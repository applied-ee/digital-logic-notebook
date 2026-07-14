---
title: "NAND"
weight: 40
---

# NAND

NAND is AND followed by inversion: the output is low only when *all* inputs are high, and high otherwise. That small change — putting a bubble on the AND — turns out to be one of the most important facts in digital logic, because NAND can build everything else.

| A | B | A NAND B |
|---|---|----------|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

## Why NAND Is Universal

NAND is **functionally complete**: any Boolean function whatsoever can be built from NAND gates alone. An inverter is a NAND with its inputs tied together; an AND is a NAND followed by that inverter; an OR is a NAND with both inputs inverted — which, by [De Morgan's theorems]({{< relref "/docs/building-blocks/boolean-foundations/demorgans-theorems" >}}), a NAND *already is* when its inputs are read as inverted. From those, every other gate and every larger function follows. A designer given nothing but NAND gates is not missing anything.

## Why It Became the Workhorse

Universality would be a curiosity if NAND were expensive, but the opposite is true. In [CMOS]({{< relref "/docs/implementation/cmos" >}}) the inverting gates are the *native* ones: a two-input NAND is four transistors, while a true [AND]({{< relref "and" >}}) needs six (the NAND plus an inverter). NAND is therefore both the cheapest useful gate and a complete logic set — so standard-cell libraries and hand-built logic alike lean on it heavily. It is no accident that the archetypal first [TTL]({{< relref "/docs/implementation/ttl" >}}) part, the 7400, is a quad two-input NAND, or that so much fixed logic is designed in NAND with bubbles pushed around by De Morgan.

## Beyond Combinational

Cross-couple two NAND gates — each feeding the other — and the pair becomes bistable: an [SR latch]({{< relref "/docs/building-blocks/storage/sr-latch" >}}) with active-low set and reset inputs. The same universality that lets NAND build any combinational function also lets it build memory, which is why a bin of NAND gates is, in principle, a complete logic kit.
