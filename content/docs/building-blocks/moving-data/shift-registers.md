---
title: "Shift Registers"
weight: 10
---

# Shift Registers

A shift register is a row of [flip-flops]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}}) wired so that each one's output feeds the next one's input. On every clock edge the whole row shifts its contents one position along. Where a plain [register]({{< relref "/docs/building-blocks/storage/registers" >}}) holds a word still, a shift register makes it *move* — which is the basis for nearly every way hardware moves data on a small number of wires.

## Serial and Parallel, in Four Combinations

The value of a shift register is converting between serial and parallel form, and parts are named for how data enters and leaves:

- **SIPO** (serial-in, parallel-out) — bits are clocked in one wire at a time, then read out all at once. This is the [74HC595]({{< relref "/docs/glue-logic-toolbox/more-outputs" >}}), the standard way to turn a few pins into many outputs.
- **PISO** (parallel-in, serial-out) — a word is captured in parallel, then clocked out one bit at a time. This is the [74HC165]({{< relref "/docs/glue-logic-toolbox/more-inputs" >}}), the mirror for reading many inputs on a few pins.
- **SISO** (serial-in, serial-out) delays a stream by N clocks; **PIPO** with shifting, and the universal shift register (74HC194) that does any direction on command, round out the set.

Serial-to-parallel and parallel-to-serial conversion is exactly what a UART or an SPI port does at its core — a shift register clocking bits onto or off of a wire.

## Feedback Turns It Into More

Tapping a shift register's output back to its input changes what it is:

- Feed the last output straight back and it becomes a **[ring counter]({{< relref "/docs/building-blocks/counting/ring-and-johnson-counters" >}})** — a one-hot pattern circulating.
- Feed the *inverted* output back and it becomes a **Johnson counter**.
- Feed back an **[XOR]({{< relref "/docs/building-blocks/gates/xor" >}})** of a few taps and it becomes a **linear-feedback shift register (LFSR)**, cycling through a long pseudo-random sequence — the basis of scramblers, cheap noise sources, checksums, and test-pattern generators.

The same handful of flip-flops that move data in a line also, with a wire looped back, count, sequence, and generate pseudo-random patterns — which is why the shift register is one of the most reused structures in all of digital logic.
