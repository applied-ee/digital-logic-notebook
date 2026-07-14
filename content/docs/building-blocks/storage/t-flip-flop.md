---
title: "T Flip-Flop"
weight: 50
---

# T Flip-Flop

The T (toggle) flip-flop does one thing: when its T input is high, it flips state on every clock edge; when T is low, it holds. That single behavior makes it the building block of counters and frequency dividers.

| T | Q (next) |
|---|----------|
| 0 | Q — hold |
| 1 | Q̄ — toggle |

## Divide by Two

A flip-flop that toggles on each clock edge produces an output that changes half as often as its clock — a **divide-by-two**. Feed that output into the clock of a second toggle stage and it divides by two again; chain *n* stages and the result counts in binary and divides the input frequency by 2ⁿ. That is precisely how a [ripple counter]({{< relref "/docs/building-blocks/counting/ripple-counters" >}}) works, and why the T flip-flop lives at the root of the [counting]({{< relref "/docs/building-blocks/counting" >}}) primitives.

## How It's Made

There is rarely a dedicated T flip-flop today; it is built from what's available. A [D flip-flop]({{< relref "d-flip-flop" >}}) becomes a T flip-flop by feeding back D = Q [XOR]({{< relref "/docs/building-blocks/gates/xor" >}}) T — the XOR passes Q unchanged when T is 0 and inverts it when T is 1, which is exactly hold-or-toggle. A [JK flip-flop]({{< relref "jk-flip-flop" >}}) becomes one by tying J and K together to form T.

The toggle idea is old and physical, too: the bistable **impulse relay** behind stairwell lighting — one press, one flip — is a mechanical T flip-flop, the same [relay]({{< relref "/docs/before-the-ic/relays" >}}) memory that still ships today. Toggle is one of the most durable behaviors in the notebook: a single bit that changes only when told to, holding otherwise.
