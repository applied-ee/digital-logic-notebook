---
title: "Microcontrollers"
weight: 10
---

# Microcontrollers

A microcontroller is a whole small computer on one chip: a CPU, its memory (flash for the program, RAM for data), and a set of peripherals, all on a single die. For most small systems it is the first and most common answer to the question this chapter asks — *where did the logic go?* It went into a program running on a cheap MCU.

## Logic That Became a Program

The peripherals around an MCU's CPU are, quite literally, the [functional building blocks]({{< relref "/docs/building-blocks" >}}) of this book absorbed onto the die and made software-configurable. A timer/counter peripheral is a [counter]({{< relref "/docs/building-blocks/counting" >}}) — a 7490 that moved inside the chip. A UART or SPI block is [shift registers]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}) plus a small [state machine]({{< relref "/docs/building-blocks/state-machines" >}}). GPIO is latches and buffers. Where a 1975 design wired those functions together from 74xx parts, an MCU design configures them in firmware and wires them with lines of code.

That is the trade the microcontroller makes: instead of choosing and soldering a counter, a decoder, and a handful of gates, a designer writes a program that sets up the equivalent peripherals and sequences them. The logic is the same; the medium became software.

## What It Is Good At, and What It Is Not

The strength is flexibility and cost. One inexpensive part, reprogrammable at will, replaces a board of fixed logic — which is exactly why so many discrete parts landed in the [obsolete]({{< relref "/docs/obsolete" >}}) column with "MCU timer" as their replacement.

The limit is that a CPU is *sequential*: it executes one instruction at a time, so timing is bounded by software and interrupt latency rather than by parallel hardware. When a task needs many things to happen truly at once, or with hard nanosecond determinism, the MCU hands off to actual parallel hardware — an [FPGA]({{< relref "fpgas" >}}) or custom silicon. The firmware side of microcontrollers — clocks, peripherals, interrupts, and real-time behavior — is the subject of the *Embedded Systems* notebook; here the point is simply that the MCU is where the bulk of everyday logic quietly moved.
