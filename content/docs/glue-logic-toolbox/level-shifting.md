---
title: "Level Shifting"
weight: 70
---

# Level Shifting

Modern boards are rarely a single voltage. A 3.3 V microcontroller must talk to a 5 V sensor, a 1.8 V memory, or an I²C bus shared across domains, and connecting mismatched levels directly either fails to register a logic high or over-volts an input. Level shifting moves a signal safely from one voltage domain to another — and the right part depends entirely on the *direction* and the *drive type*.

## Match the Part to the Signal

- **One-way, into a tolerant input** — an [74LVC]({{< relref "/docs/implementation/lvc-ahc" >}}) buffer with 5 V-tolerant inputs shifts a 5 V signal down to 3.3 V logic simply by being powered from 3.3 V; the tolerant input accepts the higher level. The single-gate 74LVC1T45 adds a direction pin for a push-pull line.
- **Bidirectional open-drain buses (I²C)** — the **TXS0102 / TXS0108** are designed for this: they auto-sense direction and work with the open-drain, pulled-up signaling that I²C uses. Do not use a push-pull translator on I²C.
- **Bidirectional push-pull** — the **TXB0104 / TXB0108** translate driven (push-pull) signals in either direction, for buses like SPI where both ends actively drive. They are *not* suitable for open-drain lines.
- **A single line, cheaply** — a lone N-channel MOSFET (the BSS138 circuit) level-shifts one bidirectional open-drain line; a resistor divider works for a slow, one-way down-shift where speed is not critical.

## The One Rule

Get the two questions right before picking a part: **which direction** does the signal travel, and is it **push-pull or open-drain**? Nearly every level-shifting failure comes from using a push-pull translator on an open-drain bus, or assuming a resistor divider can keep up with a fast edge. These families come straight out of the [low-voltage logic]({{< relref "/docs/implementation/lvc-ahc" >}}) era, where mixed-voltage design became the normal case rather than the exception.
