---
title: "OR"
weight: 30
---

# OR

The OR gate outputs high when *any* of its inputs is high. It is the "at least one condition met" gate, and the natural counterpart to AND.

| A | B | A OR B |
|---|---|--------|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

The physical picture is two switches in **parallel**: current reaches the output if either one is closed — the behavior built from [relay contacts in parallel]({{< relref "/docs/before-the-ic/relays" >}}).

## The Mirror of AND

Like AND, a true OR is not what a [CMOS]({{< relref "/docs/implementation/cmos" >}}) process produces on its own. The native inverting gate here is [NOR]({{< relref "nor" >}}), and an OR is a NOR followed by an inverter — again six transistors versus four. AND and OR are also mirror images of each other under [De Morgan's theorems]({{< relref "/docs/building-blocks/boolean-foundations/demorgans-theorems" >}}): inverting the inputs and output of one gives the other, which is why a design built entirely from NAND (or entirely from NOR) can still express both.

## Where It's Used

OR **combines**: it collects several independent "this happened" conditions into a single "something happened" line — any of a set of alarm inputs, error flags, or wake-up sources asserting the output. Widened, it is a "nonzero" detector, high whenever any bit of a word is set. Whenever a design needs "any of these being true is enough," it is an OR.
