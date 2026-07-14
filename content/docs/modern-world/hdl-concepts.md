---
title: "HDL Concepts"
weight: 40
---

# HDL Concepts

A hardware description language — Verilog or VHDL — is how logic is actually specified once there is too much of it to draw. Nobody schematics a million gates; instead they *describe* the intended behavior in an HDL, and a synthesis tool turns that description into real gates and flip-flops, whether for an [FPGA]({{< relref "fpgas" >}})'s fabric or an [ASIC]({{< relref "asics" >}})'s cells.

## It Describes Hardware, It Does Not Run

The single most important idea — and the one that trips up newcomers from software — is that **an HDL describes hardware that all exists at once; it is not a program that executes line by line.** When a Verilog file says one signal is the AND of two others and, elsewhere, that a third is the OR of two more, both pieces of logic are built and both operate concurrently, forever. There is no "first this, then that." Order of appearance is irrelevant; everything is simultaneous, because it is describing wires and gates, not instructions.

Within that model, the description maps straight onto the primitives of this book. Write `a & b` and synthesis instantiates an [AND]({{< relref "/docs/building-blocks/gates/and" >}}). Describe logic that depends only on its current inputs and you get [combinational]({{< relref "/docs/building-blocks/gates" >}}) gates; describe logic that updates on a clock edge and you get [flip-flops]({{< relref "/docs/building-blocks/storage" >}}). Describe a set of states and the transitions between them and you get exactly the [state machine]({{< relref "/docs/building-blocks/state-machines" >}}) from Part II. This level of description — logic between registers, updated on clocks — is called register-transfer level (RTL), and it is how essentially all modern digital design is entered.

## Why It Matters Here

HDL is the bridge that makes the rest of this notebook practical at scale. The gates, latches, counters, and comparators do not go away when a design has millions of them — they simply stop being drawn and start being *described*, then rebuilt automatically by the tools. The same HDL source can target an FPGA today and an ASIC tomorrow, which is why learning the primitives as behaviors, not part numbers, pays off exactly here: an HDL is those behaviors, written down.
