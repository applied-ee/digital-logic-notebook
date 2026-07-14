---
title: "More Inputs"
weight: 40
---

# More Inputs

The mirror of the output problem: a design needs to read more switches, buttons, or digital sensors than there are pins to spare. The same shift-register trick works in reverse — sample many inputs, then clock them out over a few wires.

## The Part

The go-to is the **74HC165**, an 8-bit parallel-in, serial-out [shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}). A load pulse captures all eight inputs at once into the register; the controller then clocks those bits out serially on a single data line. Like the [74HC595]({{< relref "more-outputs" >}}) it **daisy-chains** — each '165's serial output feeds the next's input — so three pins can read 8, 16, or more inputs. The '595 for outputs and the '165 for inputs are the standard complementary pair.

## Alternatives

- **An I²C GPIO expander** (MCP23017, PCF8574) — addressable input pins on a bus, and many expanders can generate an interrupt on change so the controller need not poll.
- **A [4051 analog multiplexer]({{< relref "one-of-eight-sensors" >}})** when the "inputs" are analog voltages rather than logic levels — it routes one of several to a single ADC pin.
- **Matrix scanning** — arranging many switches into a row/column grid (as keypads and keyboards do) reads N×M switches with N+M pins, no expander required.
