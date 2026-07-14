---
title: "D Flip-Flop"
weight: 30
---

# D Flip-Flop

The D flip-flop is the workhorse of sequential logic — the element behind essentially every register, counter, shift register, state machine, and pipeline stage in a modern design. It stores one bit, and it captures that bit at a single, well-defined instant: the clock edge.

## Edge-Triggered, Not Level-Sensitive

This is the one distinction that matters. A [D latch]({{< relref "d-latch" >}}) is transparent — its output follows D the whole time it is enabled. A D flip-flop instead samples D **only at the rising (or falling) edge of the clock** and holds that value for the entire cycle until the next edge, ignoring anything D does in between.

| Clock | D | Q (next) |
|-------|---|----------|
| ↑ (edge) | 0 | 0 |
| ↑ (edge) | 1 | 1 |
| no edge | X | Q — hold |

The usual construction is **master–slave**: two latches in series on opposite clock phases, so the input is captured by the master while the clock is one way and passed to the slave when it flips — the input can only propagate through on the transition. That single sampling instant is what makes large synchronous systems predictable: every flip-flop in a design updates together, once per clock, so the whole machine advances in lockstep.

## Setup, Hold, and the Cost of the Edge

Because capture happens at an edge, D must be stable in a narrow window around it — steady before the edge (**setup time**) and briefly after (**hold time**). Violate that window and the flip-flop can go metastable, hovering between levels. Those constraints are the price of edge-triggering and the foundation of timing analysis; they are covered in [Setup & Hold Time]({{< relref "/docs/timing/setup-and-hold" >}}).

## The Universal Storage Element

In discrete form the D flip-flop is the 7474 (dual) and the octal [registers]({{< relref "registers" >}}) built from eight of them. But its real dominance is in synthesized logic: an [FPGA]({{< relref "/docs/modern-world/fpgas" >}}) or [ASIC]({{< relref "/docs/modern-world/asics" >}}) provides D flip-flops as *the* storage primitive, and everything else — toggles, counters, the once-versatile [JK]({{< relref "jk-flip-flop" >}}) — is built from a D flip-flop plus a little logic. When an [HDL]({{< relref "/docs/modern-world/hdl-concepts" >}}) describes something updating on a clock edge, a D flip-flop is what it becomes.
