---
title: "HC / HCT Families"
weight: 50
---

# HC / HCT Families

The 74HC and 74HCT families are where [CMOS]({{< relref "cmos" >}}) became the *practical default* for board-level logic. They pair CMOS power consumption with speed comparable to the popular [74LS TTL]({{< relref "ttl" >}}) of their day, wrapped in the familiar 74xx part numbers — which is why, for a great deal of discrete digital design, "HC" is simply the logic reached for first.

## High-Speed CMOS

74**HC** ("High-speed CMOS") is silicon-gate CMOS built to be fast enough to replace LS-TTL while keeping CMOS's near-zero static power, its wide 2–6 V supply range, and its high, rail-to-rail noise margin (thresholds near half the supply). Functionally it carries the entire 74xx catalog forward: a 74HC00 is the CMOS quad NAND, a 74HC595 the CMOS shift register, and so on.

## The "T" Is About Talking to TTL

The one place plain HC is awkward is interfacing with older 5 V [TTL]({{< relref "ttl" >}}) outputs. A TTL output only guarantees about 2.4 V for a logic high, but an HC input wants to see something near half its supply — around 2.5 V at 5 V — so a valid TTL high can fall in HC's undefined region.

74**HCT** solves exactly this: it is the same high-speed CMOS with its input thresholds shifted to be **TTL-compatible** (recognizing a high above 2.0 V), so it accepts TTL levels directly. The rule of thumb is simple — use HC in an all-CMOS design, and reach for HCT only when something is feeding it genuine TTL-level signals. It is the clearest small example of a family created purely to honor an [interface convention]({{< relref "ttl" >}}) that outlived the technology that set it.

## What Was Built With It

- **1980s–90s personal computers and peripherals** — the glue logic around the processor on motherboards and expansion cards.
- **Consumer electronics** — VCRs, CD players, and similar gear leaned heavily on jellybean HC parts.
- **Early microcontroller products** — the interfacing and glue bridging an MCU to the rest of a board.

## Where It Stands Today

For 5 V (and often 3.3 V) discrete logic, 74HC/HCT is the modern baseline — cheap, universally stocked, robust, and well understood. It is no coincidence that most of the parts in the [glue-logic toolbox]({{< relref "/docs/glue-logic-toolbox" >}}) are HC: the 74HC595 for [more outputs]({{< relref "/docs/glue-logic-toolbox/more-outputs" >}}), the 74HC165 for [more inputs]({{< relref "/docs/glue-logic-toolbox/more-inputs" >}}), the 74HC14 Schmitt inverter for [debounce]({{< relref "/docs/glue-logic-toolbox/debounce" >}}). When a design just needs a gate or a function and voltage is not exotic, HC is the safe default; the [low-voltage families]({{< relref "lvc-ahc" >}}) take over when the supply drops below its range.
