---
title: "Transistors"
weight: 30
---

# Transistors

The transistor is the solid-state switch — the semiconductor successor to the [vacuum tube's]({{< relref "vacuum-tubes" >}}) triode, doing the same job with no heater, no vacuum, and nothing moving. A small signal on one terminal controls a much larger current between the other two, exactly as the tube's grid controlled its plate current, but now the control happens inside a sliver of doped silicon. Demonstrated at Bell Labs in 1947, it is the device every logic family and every chip in the rest of this notebook is ultimately built from. It is also the hinge of the whole story: the last switch small and cheap enough to hold in the hand, and the first one that could be replicated by the million on a single piece of silicon.

## How a Transistor Switches

Two types matter for logic, and both are three-terminal devices where one terminal controls the flow between the other two.

A **bipolar junction transistor (BJT)** is current-controlled: a small current into the base allows a much larger current to flow from collector to emitter. A **MOSFET** (metal-oxide-semiconductor field-effect transistor) is voltage-controlled: a voltage on an *insulated* gate creates or removes a conducting channel between drain and source, drawing essentially no steady current through the gate itself. That insulated gate is the detail that later makes near-zero-power logic possible.

| Device | Controlled by | "On" (conducting) when | "Off" when |
|---|---|---|---|
| **BJT** | base **current** | base driven hard (saturation) | base current ≈ 0 (cutoff) |
| **MOSFET** | gate **voltage** | gate past threshold (channel forms) | gate below threshold |

For logic, the transistor is not run as a linear amplifier but slammed between fully off (cutoff) and fully on (saturation) — the same two-state discipline used with the tube, and the same 1 and 0. The terminal mapping is direct, too: the tube's grid, plate, and cathode become the transistor's base/gate, collector/drain, and emitter/source. The concept did not change; the physics got smaller and cooler.

## Transistors as Logic

A single transistor is already a gate. Tie a transistor's output through a resistor to the supply and drive its input: a high input turns the transistor on and pulls the output low — an inverter, the NOT function, and the seed of [resistor-transistor logic (RTL)]({{< relref "/docs/implementation/rtl" >}}).

Networks of transistors form the rest. Put transistors in series and they conduct only when *all* are on (an AND condition); put them in parallel and they conduct when *any* is on (an OR condition). Wiring a pull-down network of NMOS against a complementary pull-up network of PMOS produces gates that are naturally inverting — NAND and NOR — which is why [CMOS]({{< relref "/docs/implementation/cmos" >}}) logic is built from those two [universal gates]({{< relref "/docs/building-blocks/gates" >}}) rather than bare AND and OR. And cross-coupling two inverters so each holds the other reproduces the bistable [latch]({{< relref "/docs/building-blocks/storage/sr-latch" >}}) yet again — the same flip-flop that appeared in relays as a seal-in and in tubes as the Eccles–Jordan pair, now a handful of transistors (a static memory cell is six of them). Every primitive the earlier switches could build, the transistor builds too — only now small, cool, and cheap enough to make in quantities the older devices could never approach.

## Why the Transistor Won — and Why It Changed Everything

Against the tube, the transistor wins on every axis that limited tube machines. It has no heater, so it draws far less power and needs no warm-up. It is solid — no glass envelope, no filament to burn out — so it is rugged and effectively permanent. It runs on volts rather than hundreds of volts, and it is tiny. Point for point, the transistor erased the reasons tubes could not scale.

But the decisive advantage is not any single one of those; it is that a transistor is a *pattern in silicon.* Because the device is made by doping and patterning a semiconductor surface, many transistors can be fabricated together, at once, on one wafer — and once that is true, the marginal cost of another transistor collapses. A relay is an assembly of parts; a tube is a hand-built vacuum vessel; neither can be printed. The transistor can. That is why it does not merely replace the tube but opens a door the earlier switches never could: [integration]({{< relref "why-ics-happened" >}}), and with it the entire lineage of logic families that follows.

## Where Transistors Stand Today

The transistor is not a historical device — it is the substrate of everything after it. Every gate, flip-flop, memory cell, FPGA lookup table, and processor in use today is transistors, now numbering in the billions on a single die. As a *logic* element the transistor never retreated the way the relay and the tube did; it scaled up, disappearing into the [integrated circuit]({{< relref "/docs/implementation" >}}) rather than being displaced by anything.

Discrete transistors — the individually packaged kind — still have a healthy life outside logic: MOSFETs switch power in nearly every supply and motor drive, BJTs and FETs handle analog gain, level shifting, and interfacing, and a single transistor is still the go-to for driving a load too big for a logic pin. But those are the transistor as amplifier and power switch. Its role in *logic* is exactly where this book turns: from here on, the story is no longer about a better individual switch, but about how transistors were organized into [logic families]({{< relref "/docs/implementation" >}}) and then packed together by the thousand, the million, and the billion.
