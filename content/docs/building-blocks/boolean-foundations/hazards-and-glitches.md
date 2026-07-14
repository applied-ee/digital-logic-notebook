---
title: "Hazards & Glitches"
weight: 60
---

# Hazards & Glitches

A [truth table]({{< relref "truth-tables" >}}) describes what a function settles to, not the momentary values it passes through on the way. Real gates take time to switch, and different signal paths through a circuit take *different* amounts of time — so when an input changes, the output can briefly show a wrong value before settling to the right one. That transient is a **glitch**, and the circuit property that permits it is a **hazard**. The logic is correct; the timing is not.

## Why It Happens

A hazard arises whenever an input reaches the output by two or more paths of unequal [delay]({{< relref "/docs/timing/propagation-delay-and-fan-out" >}}). Consider a signal that feeds one gate directly and another through an inverter: when it changes, the two paths update at slightly different times, and for the moment in between, the downstream logic sees a combination that should not exist.

The usual classification:

- **Static-1 hazard** — the output should stay at 1 as an input changes, but it dips briefly to 0.
- **Static-0 hazard** — the output should stay at 0 but blips to 1.
- **Dynamic hazard** — the output should change once (say 0→1) but bounces, 0→1→0→1, before settling.

None of these appears anywhere in the truth table, because they are artifacts of the *implementation's* delays, not of the function.

## Fixing It, or Living With It

There are two responses, and which one is right depends on how the signal is used.

The classic **fix** is a redundant term. On a [Karnaugh map]({{< relref "karnaugh-maps" >}}), a static-1 hazard occurs where a transition moves between two adjacent groups that share no common product term; adding a **consensus** term that covers the overlap bridges the gap, so some gate holds the output steady throughout the change. It costs an "unnecessary" gate that a pure minimization would have removed — redundancy deliberately kept for timing's sake.

The other response is to **not care**, and it is what synchronous design does. If a combinational output is only ever sampled by a [flip-flop]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}}) on a clock edge, any glitch that settles before the edge is invisible — the [setup/hold]({{< relref "/docs/timing/setup-and-hold" >}}) window is all that matters. This is why most modern logic ignores combinational hazards entirely. Glitches become dangerous only when a signal is used **asynchronously**: as a clock, a reset, a latch enable, or a decoded control line. That is exactly the situation behind a [ripple counter]({{< relref "/docs/building-blocks/counting/ripple-counters" >}})'s decoding spikes and a [Mealy machine]({{< relref "/docs/building-blocks/state-machines/moore-vs-mealy" >}})'s output glitches — a correct function, momentarily wrong, feeding something that cannot wait for it to settle.
