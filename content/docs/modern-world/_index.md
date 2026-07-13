---
title: "🚀 Part VI — The Modern World"
weight: 6
bookCollapseSection: true
---

# Part VI — The Modern World

Microcontrollers, FPGAs, ASICs, and SoCs are where most digital functionality lives today. It is tempting to read them as the end of discrete logic — but that is the wrong lesson.

> Microcontrollers → FPGAs → ASICs → SoCs

They didn't *replace* logic. They **absorbed** some of it. A timer/counter peripheral inside an MCU is a 7490 that moved onto the die. An FPGA fabric is gates and flip-flops made configurable. An ASIC is millions of the Part II primitives, fixed in silicon. And even so, there are still millions of discrete NAND gates, buffers, multiplexers, comparators, and analog switches designed into products every year — because integration moved the *common* functions inward and left the *edge* functions where they always were.

## Sections

- **[Microcontrollers]({{< relref "microcontrollers" >}})** — Logic plus a program: where counting and sequencing went.
- **[FPGAs]({{< relref "fpgas" >}})** — Configurable fabric: gates and flip-flops you define after manufacture.
- **[ASICs]({{< relref "asics" >}})** — The primitives, fixed in silicon at scale.
- **[SoCs]({{< relref "socs" >}})** — Whole systems — processors, logic, and analog — on one die.
