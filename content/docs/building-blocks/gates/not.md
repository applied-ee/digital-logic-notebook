---
title: "NOT"
weight: 10
---

# NOT

The NOT gate, or inverter, is the simplest logic function: its output is the complement of its input. A high in produces a low out, and a low in produces a high out.

| A | NOT A |
|---|-------|
| 0 | 1 |
| 1 | 0 |

## How It's Built

In [CMOS]({{< relref "/docs/implementation/cmos" >}}) the inverter is the most economical gate there is — one PMOS transistor pulling the output up and one NMOS pulling it down, two transistors total. A low input turns the PMOS on and pulls the output high; a high input turns the NMOS on and pulls it low. Because exactly one of the two is on in each stable state, no current flows through from supply to ground except briefly during a switch — the reason CMOS logic burns almost no static power.

The inverter is also the seed of every other CMOS gate: a [NAND]({{< relref "nand" >}}) or [NOR]({{< relref "nor" >}}) is essentially an inverter whose single pull-up and pull-down transistors have been replaced by series/parallel networks. Learn the inverter and the rest of the family is a variation on it.

## Where It's Used

Producing a complement is the obvious job — many logic expressions need the inverse of a signal — but the inverter earns its keep in two less obvious ways. Chained or widened, inverters **restore and drive**: each stage pulls the signal cleanly back to a full rail and can drive a heavier load than its input, which is exactly what the non-inverting [buffer]({{< relref "/docs/building-blocks/moving-data/buffers" >}}) (two inverters in series) is for. And giving the inverter's input **hysteresis** turns it into a [Schmitt trigger]({{< relref "schmitt-trigger" >}}), the standard way to clean up a slow or noisy edge.

As a discrete part the inverter is everywhere, from the classic hex inverter (a package of six) to the single-gate parts reached for in the [glue-logic toolbox]({{< relref "/docs/glue-logic-toolbox/one-inverter" >}}) when a design needs exactly one.
