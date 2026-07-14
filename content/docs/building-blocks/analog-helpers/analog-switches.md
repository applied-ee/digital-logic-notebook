---
title: "Analog Switches"
weight: 20
---

# Analog Switches

An analog switch lets a *digital* signal turn an *analog* one on and off. Where a logic gate can only handle clean highs and lows, an analog switch passes whatever voltage sits on it — an audio signal, a sensor output, a reference — while a logic-level control decides whether the path is open or closed. It is the fundamental primitive for routing analog signals under digital control.

## The Transmission Gate

The building block is the **CMOS transmission gate**: an NMOS and a PMOS transistor wired in parallel, driven by complementary control signals. When enabled, the pair conducts in *either* direction and passes any voltage between the supply rails; when disabled, the path is open. Because the two transistor types cover opposite ends of the voltage range, together they pass a signal cleanly across the whole rail-to-rail span, which a single transistor could not.

This one cell is what the [glue-logic parts]({{< relref "/docs/glue-logic-toolbox/switch-analog-signals" >}}) are made of: a 4066 is four transmission gates, and an analog [multiplexer]({{< relref "/docs/building-blocks/selection/multiplexer" >}}) like the [4051]({{< relref "/docs/glue-logic-toolbox/one-of-eight-sensors" >}}) is a tree of them selected by an address. It is also the switch inside a [sample-and-hold]({{< relref "sample-and-hold" >}}).

## What Makes It Non-Ideal

An analog switch is not a perfect relay, and its imperfections shape how it is used:

- **On-resistance (Ron)** — a closed switch has tens to hundreds of ohms, and that resistance varies a little with the signal level, which can distort the signal into a low-impedance load. Feeding high-impedance loads keeps it negligible.
- **Rail limits** — it can only pass voltages between its own supplies; anything outside is clipped or conducts through the protection structures.
- **Charge injection** — opening the switch dumps a small packet of charge onto the signal, a brief offset that matters most in precision and sample-and-hold circuits.

For switching *power* rather than signals, this is the wrong tool — that is a job for a MOSFET, [relay, or solid-state relay]({{< relref "/docs/before-the-ic/relays" >}}). The analog switch's domain is small-signal routing, controlled by logic.
