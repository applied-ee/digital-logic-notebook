---
title: "More Outputs"
weight: 30
---

# More Outputs

A microcontroller or FPGA has run out of pins, but the design still needs to drive many things — a bank of LEDs, seven-segment digits, relays, or status lines. The trick is to trade a few pins and a little time for as many outputs as needed.

## The Part

The workhorse is the **74HC595**, an 8-bit serial-in, parallel-out [shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}) with a latched output. Three signals — data, shift clock, and latch — feed eight bits in serially, and the latch then presents all eight at the outputs at once (so they change cleanly together rather than rippling). Its serial-output pin feeds the next '595's input, so devices **daisy-chain**: three pins can drive 8, 16, 24, or more outputs, limited mainly by how long the shifting takes.

## How It Fits Together

The '595 is a shift register plus an output [register]({{< relref "/docs/building-blocks/storage/registers" >}}) — exactly the [moving-data]({{< relref "/docs/building-blocks/moving-data" >}}) primitive, packaged for this job. Clock the bits in, pulse the latch, and the new pattern appears. Its mirror image, the [74HC165]({{< relref "more-inputs" >}}), solves the opposite problem of too few *inputs*.

## Alternatives

- **An I²C or SPI GPIO expander** (MCP23017, PCF8574) — adds a block of addressable pins on a bus, convenient when several are already on it.
- **A dedicated LED driver** (TLC5940, WS2812 strings) when the outputs are specifically LEDs needing constant-current or per-pixel control.
- **Just use more pins** — if a larger package or a second device frees enough I/O, the simplest answer is no expansion chip at all.
