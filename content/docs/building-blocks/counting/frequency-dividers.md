---
title: "Frequency Dividers"
weight: 30
---

# Frequency Dividers

A frequency divider produces a slower clock from a faster one, and a counter is already a frequency divider — the two are the same circuit viewed two ways. Every [toggle flip-flop]({{< relref "/docs/building-blocks/storage/t-flip-flop" >}}) stage halves the frequency, so an *n*-stage [counter]({{< relref "ripple-counters" >}}) divides its input by 2ⁿ while it counts. Deriving usable clocks this way is one of the most common jobs a counter does.

## Dividing by Two, by 2ⁿ, and by N

Dividing by a power of two is free: tap the output of the right stage of a binary counter. Stage 0 gives ÷2, stage 3 gives ÷16, and so on.

Dividing by an arbitrary **N** takes a **modulo-N counter** — a counter that counts up to N−1 and then resets (or reloads) to zero, so its cycle is N clocks long. A synchronous binary counter with a small decode on its outputs to trigger the reset makes any divide ratio, and programmable counters make the ratio settable at run time. This is exactly how a system turns one crystal into many clocks: prescalers for timer ticks, baud-rate generators for a UART, and the feedback divider inside a PLL are all modulo-N dividers.

## Watch the Duty Cycle

A divide-by-two from a single flip-flop gives a clean 50 % duty cycle, because the output spends one input period high and one low. Even divide ratios generally come out symmetric, but a straightforward divide-by-*odd* counter does **not** produce a 50 % duty cycle on its own — the high and low times differ by one input period. When a symmetric output is needed from an odd divide, it takes extra logic (for instance, combining edges from both clock phases). For a slow enable or tick this rarely matters; for a clock feeding other synchronous logic, the duty cycle and the cleanliness of the edge (see [Clocks & Distribution]({{< relref "/docs/timing/clocks-and-distribution" >}})) very much do.
