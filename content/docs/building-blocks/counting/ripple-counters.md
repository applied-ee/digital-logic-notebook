---
title: "Ripple Counters"
weight: 10
---

# Ripple Counters

A ripple counter is the simplest way to count in hardware: a chain of [toggle flip-flops]({{< relref "/docs/building-blocks/storage/t-flip-flop" >}}) in which each stage's output clocks the next. The first stage toggles on the input clock, dividing it by two; its output clocks the second stage, dividing by two again; and so on. With *n* stages the chain counts from 0 to 2ⁿ−1 in binary and divides the input frequency by 2ⁿ — all from flip-flops and a wire, no logic gates and no software.

## Why "Ripple"

The name is the catch. The stages are **asynchronous**: only the first sees the real clock, and each later stage is triggered by the one before it. So a clock edge does not update the whole counter at once — it toggles stage 0, which after its [propagation delay]({{< relref "/docs/timing/propagation-delay-and-fan-out" >}}) toggles stage 1, which toggles stage 2, and the change *ripples* down the chain.

Two consequences follow. First, the counter's outputs are not all valid at the same instant; for a brief moment after each edge the count passes through transient wrong values as the ripple propagates. Anything decoding the count during that window — a gate watching for a particular value — sees short spurious pulses (**decoding glitches**). Second, the counter is not fully settled until the edge has travelled through every stage, so the maximum usable clock rate is limited by the *total* ripple delay, which grows with the number of stages.

## Where It's Fine

For plain [frequency division]({{< relref "frequency-dividers" >}}) and slow, low-stakes counting where nothing decodes the intermediate bits, a ripple counter's simplicity is a virtue — it is cheap and needs no design effort. The classic parts are the 7490 decade counter and the long binary ripple counters like the 4020 and 4040. When speed or clean, glitch-free decoding matters, though, the ripple is exactly the problem, and the fix is to clock every stage together — the [synchronous counter]({{< relref "synchronous-counters" >}}).
