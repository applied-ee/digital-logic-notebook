---
title: "Debounce"
weight: 20
---

# Debounce

A mechanical switch or button does not make one clean transition. Its contacts — like the [relay contacts]({{< relref "/docs/before-the-ic/relays" >}}) that first exposed the problem — bounce for a few milliseconds on every closure, producing a burst of edges that a fast logic input or an interrupt reads as many presses.

## The Part

The classic answer is a **74HC14** hex [Schmitt-trigger]({{< relref "/docs/building-blocks/gates/schmitt-trigger" >}}) inverter (or the single-gate **74LVC1G14**) with a small **RC filter** on its input. The resistor and capacitor slow the signal so the bounce is smeared into a gentle ramp; the Schmitt input's hysteresis then turns that ramp into exactly one clean edge, ignoring the wobble in between.

Size the RC so its time constant is comfortably longer than the bounce — a few milliseconds is typical for a button (roughly a 10 kΩ resistor and 100 nF, adjusted to taste). Too short and bounce leaks through; too long and fast presses are missed.

## Alternatives

- **An [SR latch]({{< relref "/docs/building-blocks/storage/sr-latch" >}}) with an SPDT switch** — the textbook debounce: the switch's two throws set and reset the latch, which snaps to the first solid contact and ignores the bounce entirely. No RC tuning, but it needs a changeover switch.
- **In firmware** — sample the input on a timer and accept a change only after it has been stable for several reads. Free on a microcontroller, and the most common approach when a pin and a timer are already available.
- **A dedicated debounce IC** (MAX6816, MC14490) when several lines need clean, guaranteed debouncing without per-line RC design.
