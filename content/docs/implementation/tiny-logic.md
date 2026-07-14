---
title: "Tiny Logic (74LVC1Gxx)"
weight: 70
---

# Tiny Logic (74LVC1Gxx)

Tiny logic is the endpoint of discrete-logic miniaturization: **one gate per package**. Where the classic 7400 put four NAND gates in a 14-pin package, a part like the 74LVC1G00 is a single two-input NAND in a five-pin package smaller than a grain of rice. It is the most modern link in this chapter, and it exists because of what happened to logic everywhere else in the notebook.

## One Gate, One Package

Single-gate parts carry the familiar function set into the smallest possible footprint — the "1G" in the number means one gate:

- **74LVC1G04** — a single inverter (the go-to for [one inverter]({{< relref "/docs/glue-logic-toolbox/one-inverter" >}})).
- **74LVC1G00 / 1G08 / 1G32** — a single NAND / AND / OR.
- **74LVC1G14** — a single Schmitt-trigger inverter, a whole [debounce]({{< relref "/docs/glue-logic-toolbox/debounce" >}}) or edge-cleaner in one dot.

They are built on the same low-voltage [CMOS]({{< relref "lvc-ahc" >}}) processes as their full-size siblings — fast, low voltage, often 5 V-tolerant — packaged in SOT-23-5, SC-70, and even smaller outlines. The AUP1G variants push power down further still for portable designs.

## Why the Package Shrank to One Gate

This part only makes sense in light of the book's larger story. Most logic has migrated *inside* [microcontrollers and FPGAs]({{< relref "/docs/modern-world" >}}); what remains discrete on a modern board is rarely a block of logic but a **single surgical fix** — invert one signal, debounce one button, shift one line between voltage domains, add one gate a chip forgot to provide. A quad package would waste three gates and the board space to route them. A single-gate part drops exactly one function exactly where it is needed.

## Where It Stands Today

Tiny logic is thoroughly current, and it is the physical embodiment of this book's thesis. Integration absorbed the *bulk* of logic into large chips, but it did not make the primitives disappear — it left the last few gates to be sprinkled in individually, right where a design needs them. The [glue-logic toolbox]({{< relref "/docs/glue-logic-toolbox" >}}) is, in large part, a catalog of when to reach for one.
