---
title: "AND"
weight: 20
---

# AND

The AND gate outputs high only when *all* of its inputs are high. It is the "every condition met" gate: the output asserts precisely when nothing is missing.

| A | B | A AND B |
|---|---|---------|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

The physical picture is two switches in **series**: current reaches the output only when both are closed, which is exactly the behavior first built from [relay contacts in series]({{< relref "/docs/before-the-ic/relays" >}}).

## A Gate That Costs an Extra Inverter

AND is one of the first functions anyone learns, but it is not one a [CMOS]({{< relref "/docs/implementation/cmos" >}}) process builds naturally. CMOS gates are inherently inverting, so the native gate is [NAND]({{< relref "nand" >}}); a true AND is a NAND followed by an inverter — six transistors where the NAND alone is four. For that reason real logic is often designed in NAND and NOR, with AND appearing only where the non-inverted output is actually needed. Recognizing that "AND = NAND + inversion" is the first small lesson of [De Morgan's theorems]({{< relref "/docs/building-blocks/boolean-foundations/demorgans-theorems" >}}).

## Where It's Used

The AND gate's most common role is as an **enable**: feed a signal into one input and a control line into the other, and the signal passes only while the control is high — a clean way to gate a clock, qualify a pulse, or arm a path. Widened to many inputs, AND also **masks and tests**: a bit is forced to zero unless the corresponding mask bit is one, and an all-ones detector is simply a wide AND. Whenever a design needs "all of these must be true at once," it is an AND.
