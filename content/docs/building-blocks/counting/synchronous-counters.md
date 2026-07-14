---
title: "Synchronous Counters"
weight: 20
---

# Synchronous Counters

A synchronous counter fixes the [ripple counter]({{< relref "ripple-counters" >}})'s central flaw by clocking **every flip-flop from the same clock at the same time**. There is no ripple: on each edge all stages that need to change do so together, so the count is valid all at once and the counter runs as fast as a single stage allows.

## Knowing When to Toggle

If every flip-flop shares the clock, each one needs to be told *in advance* whether to flip on the coming edge. That is the job of a little combinational logic: a stage toggles only when all the stages below it are already 1. Stage 0 toggles every edge; stage 1 toggles when bit 0 is 1; stage 2 toggles when bits 0 and 1 are both 1 — a chain of [AND gates]({{< relref "/docs/building-blocks/gates/and" >}}) feeding each [flip-flop]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}})'s toggle enable. The flip-flops still all fire on the same edge; the logic just decides which ones act.

## The Trade, and the Parts

The cost is that extra logic, and one subtler limit: the AND chain that computes the toggle enables has its own propagation time (the *carry* rippling through the enable logic, even though the flip-flops are synchronous), which caps the clock rate for wide counters. Fast counters attack this with parallel or look-ahead carry, computing the high-order enables directly rather than in a chain.

In return the count is clean and fully decodable — all bits settle together after one clock-to-output plus the enable logic, so a gate watching for a particular value sees no ripple glitches. This is why synchronous counters are the default whenever speed or reliable decoding matters: the 74161/74163 (4-bit binary), 74160/74162 (decade), and 74191/74193 (up/down) are the standard parts. A counter is also the simplest kind of synchronous [state machine]({{< relref "/docs/building-blocks/state-machines" >}}) — a fixed sequence of states advanced by one clock — which is why the same clean, all-at-once discipline underlies both.
