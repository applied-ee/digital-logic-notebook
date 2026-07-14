---
title: "Bus Transceivers"
weight: 20
---

# Bus Transceivers

A bus transceiver is a bidirectional [buffer]({{< relref "buffers" >}}) with direction control — the part that lets a device drive a shared bus, receive from it, and get out of the way when it is not its turn. It exists because a bus is a set of wires many devices share, and sharing wires safely is harder than it looks.

## The Problem of a Shared Bus

On a bus, several devices connect to the same lines, but only **one** may drive them at any instant. If two devices drive the same wire to opposite levels, they fight — a low-impedance path from supply to ground that corrupts the data and can damage the drivers. This is **bus contention**, and avoiding it is the whole discipline of bus design: every device must present a **three-state** output that can go high-impedance (electrically disconnected) whenever it is not the active driver.

A transceiver packages this for a bidirectional bus. It is two sets of three-state buffers back to back — one pointing each way — with a **direction (DIR)** input selecting which set is active and an **output-enable (OE)** input that tri-states both. The classic part is the [74HC245]({{< relref "/docs/obsolete" >}}) octal transceiver: DIR chooses A→B or B→A, OE connects or disconnects the whole device from the bus.

## Where It's Used

The archetypal use is between a processor's data bus and its memory or peripherals: DIR follows read-versus-write, and OE asserts only when this device is selected, so the shared lines have exactly one driver at a time. Transceivers also **buffer and isolate** a bus — adding drive strength for a long or heavily loaded backplane, and protecting one side from the other — and, because the two sides can run at different supplies, they double as domain crossings, which is why bus-transceiver-style parts appear in the toolbox's [level-shifting]({{< relref "/docs/glue-logic-toolbox/level-shifting" >}}) options. Underneath every one of them is the three-state output, which the [Buffers]({{< relref "buffers" >}}) page covers directly.
