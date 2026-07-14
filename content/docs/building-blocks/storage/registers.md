---
title: "Registers"
weight: 60
---

# Registers

A register is simply a row of [D flip-flops]({{< relref "d-flip-flop" >}}) sharing one clock, storing an N-bit word instead of a single bit. Where a flip-flop remembers a bit, a register remembers a *number* — and that makes it the basic unit of storage in any datapath.

## A Word, Captured on a Clock

Present a word at the register's inputs, pulse the clock, and all N bits are captured together and held until the next clock — the same edge-triggered capture as a single flip-flop, widened. Because every bit latches on the same edge, the stored word is always internally consistent; there is no moment where half the bits are old and half are new. The classic octal parts are the 74HC574 and 74HC377 (eight D flip-flops with a shared clock, the latter with a load enable).

This "parallel load and hold" is the plain storage register. Its close relative, the [shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}), is the same row of flip-flops wired so each feeds the next — trading parallel capture for the ability to move data sideways, which is why it lives among the [moving-data]({{< relref "/docs/building-blocks/moving-data" >}}) primitives rather than here.

## The Unit of the Datapath

Registers are where individual flip-flops stop being bits and become the working storage of a machine: the register file inside a CPU, the stage boundaries of a pipeline, the holding registers between one block of logic and the next. This is also why modern hardware design is described at **register-transfer level** — an [HDL]({{< relref "/docs/modern-world/hdl-concepts" >}}) design is, quite literally, a description of words moving from register to register through logic on each clock. The humble cross-coupled pair of the [SR latch]({{< relref "sr-latch" >}}), multiplied and clocked, has become the place computation keeps its state.
