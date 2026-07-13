---
title: "Arithmetic"
weight: 30
bookCollapseSection: true
---

# Arithmetic

**Gates do math.**

Addition, subtraction, comparison, and parity are just particular combinational functions — truth tables large enough that nobody writes them out by hand, built instead from repeating cells. A full adder chained N times is an N-bit adder; add a mode input and it becomes the core of an ALU. These are the blocks where propagation delay stops being abstract, because a carry has to ripple across every stage before the answer is valid.

## Sections

- **[Half & Full Adders]({{< relref "half-and-full-adders" >}})** — The one-bit cell that all binary arithmetic is built from.
- **[Subtractors]({{< relref "subtractors" >}})** — Subtraction as addition of a two's-complement number.
- **[Magnitude Comparators]({{< relref "magnitude-comparators" >}})** — Deciding greater-than, less-than, or equal in hardware (distinct from the voltage comparators in Analog Helpers).
- **[Parity & Error Detection]({{< relref "parity-and-error-detection" >}})** — Cheap integrity checks built from XOR trees.
- **[ALU]({{< relref "alu" >}})** — Where arithmetic and logic functions are selected under control — the ancestor of the CPU datapath.
