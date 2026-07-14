---
title: "Propagation Delay & Fan-Out"
weight: 10
---

# Propagation Delay & Fan-Out

The first crack in the ideal picture is that a gate does not respond instantly. **Propagation delay** is the time between an input changing and the output following — a few nanoseconds for ordinary logic, but never zero. Every timing limit in a digital system traces back to this one fact.

## Delay Accumulates Along a Path

Delays add up along a chain of gates. A signal passing through five gates arrives roughly five gate-delays late, and the **critical path** — the slowest route from one register to the next — sets how fast the whole circuit can run. This is why a [ripple counter]({{< relref "/docs/building-blocks/counting/ripple-counters" >}}) and a ripple-carry [adder]({{< relref "/docs/building-blocks/arithmetic/half-and-full-adders" >}}) slow down as they get wider: the carry has to propagate stage by stage, and nothing downstream is valid until it arrives. It is also why [hazards and glitches]({{< relref "/docs/building-blocks/boolean-foundations/hazards-and-glitches" >}}) exist at all — two paths of unequal delay reconverging produce a transient wrong value. Shortening the critical path, by using fewer levels of logic or faster carry schemes, is how a design is made to run faster.

## Fan-Out: Delay Depends on Load

Fan-out is the number of inputs a single output drives, and it feeds straight back into delay. In [CMOS]({{< relref "/docs/implementation/cmos" >}}) a gate input is essentially a small capacitor that draws no steady current, so the *DC* fan-out is enormous — one output can hold many inputs at valid levels indefinitely. The real limit is *dynamic*: every input added, and every inch of trace, adds capacitance the driver must charge and discharge, which slows the edges and lengthens the propagation delay. Load a gate heavily and it gets slower, not wrong.

The fix is a [buffer]({{< relref "/docs/building-blocks/moving-data/buffers" >}}) — a stage sized to drive the load with fast edges, restoring the signal and isolating the source. Clock nets, which fan out to thousands of flip-flops, are the extreme case and get their own buffered [distribution networks]({{< relref "clocks-and-distribution" >}}). Propagation delay through the critical path and the loading that lengthens it are the two quantities every timing budget is built from — and the budget itself is the subject of [setup and hold]({{< relref "setup-and-hold" >}}).
