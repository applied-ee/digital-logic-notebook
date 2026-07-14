---
title: "One Inverter"
weight: 10
---

# One Inverter

The problem is small and extremely common: a design needs exactly *one* [inverter]({{< relref "/docs/building-blocks/gates/not" >}}) — to flip an active-low signal to active-high, correct a polarity, or generate a complement — and nothing else. Dropping a 14-pin hex inverter to use one-sixth of it is wasteful on a modern board.

## The Part

Reach for a **single-gate ("tiny logic") inverter**: the [74LVC1G04]({{< relref "/docs/implementation/tiny-logic" >}}) in a tiny SOT-23-5 or smaller package, running at low voltage with 5 V-tolerant inputs. On an all-5 V board the classic **74HC04** hex inverter still works if the extra five gates can be spared or reused elsewhere. If the signal is also slow or noisy, use the Schmitt-trigger version (**74LVC1G14** / 74HC14) and get [debounce]({{< relref "debounce" >}})-grade edge cleaning in the same part.

## Alternatives and Cautions

- **A spare gate you already have** — an unused NAND or NOR in an existing package makes an inverter (tie its inputs together). Free, if one is going spare.
- **A single transistor and resistor** — the [RTL]({{< relref "/docs/implementation/rtl" >}}) inverter still works for a quick discrete fix, at the cost of drive and speed.
- **The firmware, if a pin is handy** — sometimes the cheapest inverter is not inverting in hardware at all, but flipping the logic in the microcontroller.

Whichever route, tie the inputs of any *unused* gates in a package to a rail — never leave CMOS inputs floating, or they draw current and pick up noise.
