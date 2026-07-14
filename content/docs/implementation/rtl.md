---
title: "RTL"
weight: 10
---

# RTL

Resistor-Transistor Logic was the first practical way to build logic gates inside an integrated circuit. Its name is its schematic: resistors at the inputs, a [transistor]({{< relref "/docs/before-the-ic/transistors" >}}) doing the switching. It is obsolete now, but it is where the family tree starts, and every weakness of RTL is the reason the next family exists.

## How It's Built

The basic RTL gate is a [NOR]({{< relref "/docs/building-blocks/gates/nor" >}}). Each input drives the base of its own transistor through a resistor; all the transistors share a single collector resistor to the supply. If *any* input is high, its transistor conducts and pulls the shared output low — low-when-any-input-is-high is exactly NOR. Adding transistors in parallel adds inputs; that is the entire trick.

The appeal in the early 1960s was simplicity. A gate is just resistors and transistors — no diodes, few components, easy to fabricate on the young planar process — which is why RTL was the first logic anyone could integrate and sell.

## Why It Gave Way

Simplicity came at a cost on every axis that matters for logic. The input resistors and transistor capacitances form slow RC time constants, so RTL is sluggish. The shared collector resistor can only source so much current, so **fan-out is poor** — a gate can drive only a few others before its high level sags. And the switching thresholds sit uncomfortably close to the noise on the rails, giving a **thin noise margin**. Pushing an RTL system larger made all three worse at once.

The fix was to stop using resistors for the input logic and use diodes instead, which is precisely what [DTL]({{< relref "dtl" >}}) did — trading RTL's resistor networks for diode logic to buy back noise margin and fan-out.

## What Was Built With It

- **The Apollo Guidance Computer** — around 2,800 Fairchild RTL three-input [NOR gates]({{< relref "/docs/building-blocks/gates/nor" >}}), flying to the Moon on the simplest logic family there was.
- **Aerospace and military electronics** — missile and satellite guidance, telemetry, and instrumentation, the buyers who could justify first-generation ICs while they were still expensive.
- **Early digital instruments** — counters and test gear among the first commercial products to adopt integrated logic.

## Where It Stands Today

RTL is genuinely obsolete; nothing new is designed with it. It is worth knowing not as a family to use but as the baseline the rest of the lineage improved on — the starting point every later family defined itself against.
