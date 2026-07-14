---
title: "Metastability & Synchronizers"
weight: 40
---

# Metastability & Synchronizers

When a [flip-flop]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}})'s [setup or hold]({{< relref "setup-and-hold" >}}) window is violated — its data changes right at the clock edge — it may not cleanly capture a 0 or a 1. Instead it can enter **metastability**: an unstable in-between condition where the output hovers at an invalid level, or oscillates, before eventually settling to one value or the other. This is the sharpest way the digital abstraction breaks, and it cannot be designed away — only managed.

## Why It Happens

A flip-flop stores its bit in a [cross-coupled feedback loop]({{< relref "/docs/building-blocks/storage/sr-latch" >}}), which has two stable states — but also a **metastable equilibrium** balanced exactly between them, like a ball resting on a knife edge. A clean input pushes the loop firmly toward one stable state. A marginal capture, right at the edge, can instead leave it balanced at that midpoint, and it stays there until circuit noise nudges it off. Crucially, **how long that takes is unbounded** — usually picoseconds, but with no hard ceiling.

## You Cannot Eliminate It, Only Make It Rare

Because resolution time has no fixed limit, metastability is a matter of *probability*, described by a mean time between failures (MTBF): the odds that a flip-flop is still undecided after a given settling time fall off exponentially the more time it is allowed. The design goal is never "prevent metastability" — that is impossible whenever an input can change asynchronously to the clock — but to push the MTBF out to centuries or millennia, so a failure is effectively never seen.

## The Synchronizer

The standard tool is the **two-flip-flop synchronizer**: a signal entering a clock domain is passed through two flip-flops in series before the logic uses it. The first flip-flop is the one exposed to a possible setup/hold violation and may go metastable — but it is then given a **full clock cycle** to resolve before the second flip-flop samples it. By the time the second captures the value, the odds of it still being metastable are astronomically small, so what reaches the logic is a clean, resolved bit. More flip-flops buy still more margin at very high clock rates.

Every asynchronous input needs this treatment — a button press, a signal from another board, or, most importantly, anything arriving from a different [clock domain]({{< relref "clock-domain-crossing" >}}), which is where synchronizers do their most important work.
