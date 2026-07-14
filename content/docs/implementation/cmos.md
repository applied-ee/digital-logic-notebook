---
title: "CMOS"
weight: 40
---

# CMOS

Complementary Metal-Oxide-Semiconductor logic is the milestone the whole lineage was building toward. Every other family on this list is either an ancestor of CMOS or a variety of it, and every integrated circuit in a modern device — processor, memory, FPGA, microcontroller — is CMOS underneath. It won on the one axis that ultimately mattered most: power.

## How It's Built

A CMOS gate uses two complementary networks between the output and the rails: a **PMOS** network that can pull the output high and an **NMOS** network that can pull it low, arranged so that in any stable input state *exactly one* network conducts. Because there is never a path from supply to ground in a settled state, a CMOS gate draws essentially **no static current** — it dissipates power only briefly while switching, charging and discharging capacitance.

The networks are naturally inverting, so the native gates are [NAND]({{< relref "/docs/building-blocks/gates/nand" >}}) and [NOR]({{< relref "/docs/building-blocks/gates/nor" >}}); AND and OR cost an extra inverter. This is the transistor-level reason the [universal gates]({{< relref "/docs/building-blocks/gates" >}}) are the ones real logic is built from.

## Why It Was the Breakthrough

Bipolar logic like [TTL]({{< relref "ttl" >}}) burns power continuously, whether or not it is doing anything. CMOS burns power only in proportion to how often it switches — its dynamic power is roughly C·V²·f (capacitance, supply voltage squared, switching frequency). That single property unlocked two things at once:

- **Battery-powered electronics** — logic that idles at microamps made watches, calculators, and portable devices practical.
- **Very-large-scale integration** — you cannot cool a billion always-on bipolar transistors, but you *can* cool a billion transistors that each dissipate only when they switch. CMOS is what made packing millions and then billions of gates onto one die thermally possible.

CMOS also brings a wide, forgiving supply range and high input impedance: a gate input is a capacitor, drawing no steady current, so DC fan-out is enormous and the real limit becomes how fast the driver can charge all that capacitance. The tradeoff is sensitivity — the thin gate oxide is vulnerable to static discharge, so CMOS parts need ESD care.

## Where It Stands Today

CMOS is not a historical family; it is the present and the substrate of everything. The original **4000 series** (wide supply, low speed) proved the concept, and its descendants — [HC/HCT]({{< relref "hc-hct" >}}), then [LVC and the low-voltage families]({{< relref "lvc-ahc" >}}) — are the discrete logic actually stocked and specified now. When this book says a modern chip is "just VLSI," it means it is CMOS scaled up. Everything after this page is a refinement of it.
