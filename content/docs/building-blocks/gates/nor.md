---
title: "NOR"
weight: 50
---

# NOR

NOR is OR followed by inversion: the output is high only when *all* inputs are low, and low if any input is high. Like [NAND]({{< relref "nand" >}}), it is a universal gate — and it holds a special place in the history of the field.

| A | B | A NOR B |
|---|---|---------|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

## Universal, and the Mirror of NAND

NOR is **functionally complete**: an inverter is a NOR with its inputs tied together, and every other gate follows. It is the [De Morgan]({{< relref "/docs/building-blocks/boolean-foundations/demorgans-theorems" >}}) dual of NAND — a NOR behaves as an AND with inverted inputs — so a design can be built entirely from NOR just as it can be built entirely from NAND. In [CMOS]({{< relref "/docs/implementation/cmos" >}}) it is equally native and cheap: four transistors for a two-input gate, where a true [OR]({{< relref "or" >}}) needs six.

## A Whole Computer From One Gate

The clearest demonstration of universality is historical: the Apollo Guidance Computer was built almost entirely from a single part — a three-input NOR gate — around 2,800 of them. One gate type, chosen for exactly the completeness described above, was enough to implement an entire flight computer. It is the sharpest illustration of what "functionally complete" really means, and a recurring theme of this book that [integration]({{< relref "/docs/before-the-ic/why-ics-happened" >}}) simply packed more of such gates onto less silicon.

## Beyond Combinational

Cross-couple two NOR gates and the result is an [SR latch]({{< relref "/docs/building-blocks/storage/sr-latch" >}}) with active-high set and reset — the complement of the NAND latch, and the more intuitive of the two to read, since a high on Set sets and a high on Reset resets. Memory, like every gate, falls out of NOR alone.
