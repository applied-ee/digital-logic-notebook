---
title: "Buffers"
weight: 30
---

# Buffers

A buffer is a gate that computes nothing — its output simply equals its input — yet it is one of the most useful parts in the toolbox. What a buffer provides is not logic but *electrical* help: drive, isolation, and, in its three-state form, the ability to disconnect.

## The Gate That Does Nothing, Usefully

A non-inverting buffer is, at heart, two [inverters]({{< relref "/docs/building-blocks/gates/not" >}}) in series — the double inversion cancels, leaving the logic value unchanged but the signal freshly restored and able to drive a much heavier load than the original could. That buys three things:

- **Drive and fan-out** — one weak output can be buffered to drive many inputs, a long trace, or a heavy load without its levels sagging. The limit it relieves is [fan-out]({{< relref "/docs/timing/propagation-delay-and-fan-out" >}}).
- **Isolation** — a buffer separates a sensitive node from whatever it feeds, so downstream loading cannot pull the source around.
- **Restoration** — the signal comes out at full, clean logic levels; give the buffer input hysteresis (a [Schmitt trigger]({{< relref "/docs/building-blocks/gates/schmitt-trigger" >}})) and it also squares up a ragged edge.

## The Third State

The most consequential buffer is the **three-state (tri-state) buffer**, which adds an enable input. When enabled it passes its input normally; when disabled its output goes to a **high-impedance (Hi-Z)** state — not a 0 and not a 1, but *not driving at all*, electrically disconnected from whatever it is wired to.

Those three conditions — 0, 1, and Hi-Z — are what make shared wires possible. Put many three-state outputs on one line, keep all but one disabled, and only the active driver controls the line while the rest stay invisible; enabling two at once is the [bus contention]({{< relref "bus-transceivers" >}}) a bus design works to prevent. This is the mechanism behind every bus: octal three-state buffers (the 74HC244, 74HC241) drive address and data lines, [transceivers]({{< relref "bus-transceivers" >}}) are pairs of them facing opposite directions, and even the outputs of [latches]({{< relref "/docs/building-blocks/storage/d-latch" >}}) and registers are often three-stated so they can join a bus. A part that computes nothing turns out to be what lets everything share a wire.
