---
title: "TTL"
weight: 30
---

# TTL

Transistor-Transistor Logic was the family that made integrated logic ubiquitous. For roughly two decades it was simply what "a logic chip" meant, and although [CMOS]({{< relref "cmos" >}}) has replaced it in almost every new design, TTL's conventions — its part numbers and its voltage levels — are so deeply embedded that they still govern logic built today.

## How It's Built

TTL took [DTL]({{< relref "dtl" >}}) and replaced its two weak spots. The string of input diodes became a single **multi-emitter transistor**: each emitter is an input, and the transistor actively sweeps charge out of the following stage, switching far faster than passive diodes could. The passive pull-up became a **totem-pole output** — a stacked pair of transistors that actively drives the output both high and low, giving fast edges and real drive strength. The signature gate is the 7400 quad two-input [NAND]({{< relref "/docs/building-blocks/gates/nand" >}}).

Because TTL is built from bipolar transistors, it draws current whenever it is powered, switching or not. That static power consumption is fine for a handful of chips but becomes the ceiling that stops bipolar logic from scaling to [large-scale integration]({{< relref "/docs/before-the-ic/integration-scales" >}}).

## Speed vs. Power, in a Dozen Flavors

TTL was never one thing; it was a spectrum of sub-families trading speed against power, all sharing the 74xx numbering:

| Sub-family | Prefix | Character |
|---|---|---|
| Standard | 74 | the original |
| Low-power | 74L | slower, less power |
| Schottky | 74S | faster (Schottky clamps prevent saturation) |
| Low-power Schottky | 74LS | the popular all-round balance |
| Advanced Schottky / FAST | 74AS, 74ALS, 74F | fastest bipolar TTL |

Schottky clamping — keeping the transistors out of deep saturation so they turn off quickly — was the key trick that made the later families fast.

## The Conventions That Outlived the Technology

TTL's lasting legacy is not its circuitry but its *interfaces*. Two things in particular became de facto standards:

- **The 74xx part-numbering scheme** — 7400, 7404, 74138, 74595 — carried forward unchanged into every CMOS family that followed (74HC00, 74LVC138). A part's number still tells you its function regardless of the technology inside.
- **TTL logic levels** — an output guaranteed above 2.4 V for a high and below 0.4 V for a low, with inputs recognizing above 2.0 V and below 0.8 V — became the reference that later families had to interoperate with. It is exactly why a "T"-suffixed CMOS part ([74HCT]({{< relref "hc-hct" >}})) exists: to accept those levels.

## Where It Stands Today

New designs rarely specify bipolar TTL — it is slower and far hungrier than modern CMOS — but it is not a museum piece. Its numbering and levels are everywhere, its schematics are the ones found in decades of industrial equipment, and it is central to retrocomputing and to reading vintage designs. TTL is best understood as *mostly replaced in silicon but permanently present in convention*.
