---
title: "🚀 The Modern World"
weight: 7
bookCollapseSection: true
---

# The Modern World

Microcontrollers, FPGAs, ASICs, and SoCs are where most digital functionality lives today. It is tempting to read them as the end of discrete logic — but that is the wrong lesson.

> Microcontrollers → FPGAs → ASICs → SoCs

They didn't *replace* logic. They **absorbed** some of it. A timer/counter peripheral inside an MCU is a 7490 that moved onto the die. An FPGA fabric is gates and flip-flops made configurable. An ASIC is millions of those primitives, fixed in silicon. And even so, there are still millions of discrete NAND gates, buffers, multiplexers, comparators, and analog switches designed into products every year — because integration moved the *common* functions inward and left the *edge* functions where they always were.

## Sections

- **[Microcontrollers]({{< relref "microcontrollers" >}})** — Logic plus a program: where counting and sequencing went.
- **[PLDs & CPLDs]({{< relref "plds-cplds" >}})** — Programmable fixed-function logic: PAL, GAL, and CPLD, the step before the FPGA.
- **[FPGAs]({{< relref "fpgas" >}})** — Configurable fabric: gates and flip-flops you define after manufacture.
- **[HDL Concepts]({{< relref "hdl-concepts" >}})** — Describing logic in Verilog/VHDL: how programmable and custom silicon is actually designed.
- **[ASICs]({{< relref "asics" >}})** — The primitives, fixed in silicon at scale.
- **[SoCs]({{< relref "socs" >}})** — Whole systems — processors, logic, and analog — on one die.
