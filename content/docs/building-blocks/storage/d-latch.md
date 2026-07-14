---
title: "D Latch"
weight: 20
---

# D Latch

The D latch fixes the two awkward things about the raw [SR latch]({{< relref "sr-latch" >}}): its forbidden state, and its lack of any control over *when* it listens. It does this by adding a single data input **D** and an **enable**, arranged so that set and reset can never be asserted at the same time.

## Transparent When Enabled

Steering logic drives the internal set/reset from D and its complement, gated by the enable. The result is simple to state:

| Enable | D | Q (next) |
|--------|---|----------|
| 1 | 0 | 0 |
| 1 | 1 | 1 |
| 0 | X | Q — hold |

While the enable is high the latch is **transparent** — Q simply follows D, changing whenever D changes. When the enable goes low, Q **freezes** at whatever value D held at that moment and stays there. One data line in, one bit stored, and no invalid combination to avoid.

## Transparency Is the Catch

That transparency is both the feature and the hazard. Because Q tracks D the entire time the enable is high — not just at one instant — anything that ripples through D during the enable window passes straight to the output. A design has to be sure D is settled and the enable is timed correctly, or a latch will happily pass a glitch. This is exactly the weakness that the edge-triggered [D flip-flop]({{< relref "d-flip-flop" >}}) removes by capturing D only at a single clock *edge* rather than across a whole level.

## Where It's Used

Transparent latches are the right tool for holding a value behind an enable — capturing a byte off a bus, demultiplexing an address/data bus, or holding an output steady while new data is prepared. The classic parts are the octal transparent latches, the 74HC373 and 74HC573. Where a design needs clean, clock-synchronized storage instead, it reaches past the latch to the flip-flop.
