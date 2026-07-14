---
title: "LVC / AHC"
weight: 60
---

# LVC / AHC

As supply voltages fell — 5 V giving way to 3.3 V, then 1.8 V and below, for both power savings and speed — logic families followed them down. LVC, AHC, and their many siblings are **today's** discrete logic: the parts actually specified in current designs, where [HC/HCT]({{< relref "hc-hct" >}}) is increasingly the legacy 5 V choice.

## Today's Low-Voltage CMOS

These are all [CMOS]({{< relref "cmos" >}}), refined for lower voltages, higher speed, and mixed-voltage systems:

- **LVC** (Low-Voltage CMOS) — runs at roughly 1.65–3.6 V, switches fast, drives hard, and — crucially — has **5 V-tolerant inputs**, so a 3.3 V LVC part can safely accept signals from a 5 V device. This tolerance makes LVC a workhorse at the boundary between old and new voltage domains.
- **AHC / AHCT** (Advanced High-speed CMOS) — an evolution of HC, several times faster, pin- and function-compatible with the HC catalog, with AHCT keeping the TTL-compatible inputs for the same interfacing reason HCT does.
- **AC/ACT, ALVC, AUC, AUP, …** — the broader modern zoo, trading among speed, drive, voltage, and power for specific needs (AUP, for instance, targets ultra-low-power portable designs).

## Why This Is Where Designs Live Now

A modern board rarely runs at a single 5 V rail; it is a patchwork of 3.3 V, 1.8 V, and lower domains around an MCU, FPGA, or SoC. Logic has to run at those voltages and, just as often, has to **move signals between them** — which is why level translation is a routine concern and why families with 5 V-tolerant I/O and dedicated translators exist. The [level-shifting]({{< relref "/docs/glue-logic-toolbox/level-shifting" >}}) entry in the glue-logic toolbox is built around exactly these parts: 74LVC for tolerant buffering, and the TXS/TXB translators for bidirectional domain crossing.

## Where It Stands Today

This is current production logic — what a new design's glue and interfacing is drawn from. The trend it embodies (lower voltage, higher speed, smaller packages, mixed-domain interfacing) also points directly at the next step, where the package shrinks all the way down to a single gate: [tiny logic]({{< relref "tiny-logic" >}}).
