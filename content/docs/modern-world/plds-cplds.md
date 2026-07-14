---
title: "PLDs & CPLDs"
weight: 20
---

# PLDs & CPLDs

Programmable logic devices are the step between fixed-function chips and the [FPGA]({{< relref "fpgas" >}}): user-defined logic without custom silicon. They exist to answer a specific frustration — a board covered in 74xx glue that has to be redesigned every time the logic changes — by putting that glue into a single part whose function is programmed, not wired.

## From PAL to GAL to CPLD

The original **PLDs** implemented logic as a programmable **sum-of-products** array: a grid of AND terms feeding OR terms, with fuses (PAL) or reprogrammable cells (GAL) selecting which connections are made. Because any Boolean function can be written in [sum-of-products form]({{< relref "/docs/building-blocks/boolean-foundations/canonical-forms" >}}), that one structure can implement a wide range of combinational logic — and with a flip-flop on each output, small state machines too. A single GAL could swallow a fistful of gates, decoders, and latches.

A **CPLD** (Complex PLD) scales that up: several PAL-like blocks of macrocells joined by a central programmable interconnect. It is non-volatile — the configuration lives in on-chip flash, so it works the instant power is applied — and its timing is fixed and predictable, since signals pass through a known, small number of stages. That makes CPLDs well suited to address decoding, bus glue, interface logic, and modest state machines.

## Where They Sit, and Where They Stand

A CPLD occupies the middle ground: more than a few gates' worth of logic, less than an FPGA's fabric, with instant-on operation and deterministic timing that an SRAM-based FPGA cannot match. That niche is real but narrow, and it is squeezed from both sides — by cheap [microcontrollers]({{< relref "microcontrollers" >}}) below and small FPGAs above.

The older parts have largely aged out: PAL and GAL sit in the [obsolete]({{< relref "/docs/obsolete" >}}) column with "CPLD" as their replacement, and the whole category is a smaller part of new designs than it once was. But the idea they introduced — reconfigurable logic defined by a stored pattern rather than by wiring — is exactly what the FPGA generalized.
