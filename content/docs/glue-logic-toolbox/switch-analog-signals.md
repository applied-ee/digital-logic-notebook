---
title: "Switch Analog Signals"
weight: 50
---

# Switch Analog Signals

A logic gate cannot pass an analog signal, and a relay is bulky and slow for routing a small voltage. The need here is to steer an analog signal — an audio line, a sensor voltage, a reference — on and off, or from one path to another, under *digital* control.

## The Part

The classic answer is the **4066**, a quad bilateral (analog) switch. Each switch is a CMOS [transmission gate]({{< relref "/docs/building-blocks/analog-helpers/analog-switches" >}}) — an NMOS and a PMOS transistor in parallel — that, when its control input is high, conducts in *either* direction and passes whatever analog voltage sits between the supply rails. When the control is low, the path is open. It is a genuine switch for signals, controlled by a logic level.

## What to Watch

Analog switches come with constraints that logic gates do not have:

- **Signals must stay within the supply rails** — the switch can only pass voltages between its Vss and Vdd; anything outside is clipped or conducts through the protection diodes.
- **On-resistance is not zero** — a closed switch has tens to a couple hundred ohms of Ron, which forms a divider with the load and varies a little with signal level; feed high-impedance loads to keep it negligible.
- **Charge injection** — switching couples a small charge spike onto the signal, which matters for sample-and-hold and precision paths.

For *selecting* one of several analog sources rather than just gating one, use an analog multiplexer such as the [4051]({{< relref "one-of-eight-sensors" >}}). And for switching real *power* rather than signals, this is the wrong tool — that is a job for a MOSFET, a [relay, or a solid-state relay]({{< relref "/docs/before-the-ic/relays" >}}).
