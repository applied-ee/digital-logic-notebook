---
title: "Storage"
weight: 40
bookCollapseSection: true
---

# Storage

**Gates remember.**

Cross-couple a pair of gates so each drives the other, and the arrangement will hold a state after the input that set it is removed. That feedback is the origin of memory in digital hardware. Latches are level-sensitive; flip-flops add a clock so state changes only at a defined edge — the discipline that makes large synchronous systems predictable.

## Sections

- **[SR Latch]({{< relref "sr-latch" >}})** — The basic set/reset feedback cell.
- **[D Latch]({{< relref "d-latch" >}})** — Transparent when enabled; captures one data line.
- **[D Flip-Flop]({{< relref "d-flip-flop" >}})** — Edge-triggered capture: the standard register bit.
- **[JK Flip-Flop]({{< relref "jk-flip-flop" >}})** — The historically general-purpose flip-flop, including toggle.
- **[T Flip-Flop]({{< relref "t-flip-flop" >}})** — Toggle on each clock: the building block of counters.
- **[Registers]({{< relref "registers" >}})** — A row of flip-flops clocked together to hold a word.
