---
title: "JK Flip-Flop"
weight: 40
---

# JK Flip-Flop

The JK flip-flop is the [SR latch]({{< relref "sr-latch" >}})'s clocked, well-behaved descendant — and, for the discrete-logic era, its most versatile one. It takes SR's set and reset inputs (here called J and K) but replaces the forbidden "both asserted" combination with something useful: **toggle**.

| J | K | Q (next) |
|---|---|----------|
| 0 | 0 | Q — hold |
| 1 | 0 | 1 — set |
| 0 | 1 | 0 — reset |
| 1 | 1 | Q̄ — toggle |

With J and K both high, each clock edge flips the output. That closes the one gap SR left open and makes a single flip-flop able to hold, set, reset, or toggle depending only on how its inputs are wired.

## Why It Mattered, and Why It Faded

That flexibility was the point. In the [TTL]({{< relref "/docs/implementation/ttl" >}}) era a designer bought flip-flops as physical parts (the 7473, 7476, 74LS109), and one JK could be configured as an SR, a [D]({{< relref "d-flip-flop" >}}), or a [T]({{< relref "t-flip-flop" >}}) flip-flop as the circuit required — a single stock part that covered every case, which simplified building counters and state machines from a bin of chips.

That advantage evaporated once logic stopped being assembled from parts and started being **synthesized**. In an [FPGA]({{< relref "/docs/modern-world/fpgas" >}}) or [ASIC]({{< relref "/docs/modern-world/asics" >}}), the D flip-flop is the native storage element and the tools build toggle, hold, and everything else from D plus a little logic — so there is nothing to gain from a more complicated flip-flop primitive. The JK is worth understanding for reading older schematics and for the clean way it completes the SR truth table, but it is rarely the flip-flop a new design actually instantiates.
