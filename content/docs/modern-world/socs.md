---
title: "SoCs"
weight: 60
---

# SoCs

A System on a Chip is integration taken to its conclusion: not just logic, and not just a processor, but a whole system on one die. Where a [microcontroller]({{< relref "microcontrollers" >}}) put a CPU, memory, and simple peripherals together, an SoC adds everything else a product needs — multiple CPU cores, a GPU, a neural accelerator, memory controllers, high-speed I/O, radios, image and signal processors — onto a single piece of silicon.

## Built From Blocks

An SoC is assembled from **IP blocks**: large, reusable [HDL]({{< relref "hdl-concepts" >}}) designs — a CPU core, a USB controller, a memory interface — licensed or reused and wired together, then fabricated as one [ASIC]({{< relref "asics" >}}) (or implemented in an SoC-class FPGA). The design effort shifts from building logic gate by gate to integrating pre-verified subsystems, but underneath every one of those blocks is the same fabric: gates, flip-flops, multiplexers, adders, and state machines, now numbering in the billions. The phone in a pocket is a handful of such SoCs.

## The Destination of the Whole Story

The SoC is where "moving functionality to higher levels of integration" finally arrives. Each chapter of this book has been one step up that ladder — a switch, a gate, a function, a subsystem, and now an entire system on one die. It is tempting to read that as the primitives disappearing into abstraction.

They did not. A modern SoC contains more [NAND gates]({{< relref "/docs/building-blocks/gates/nand" >}}), [flip-flops]({{< relref "/docs/building-blocks/storage" >}}), [multiplexers]({{< relref "/docs/building-blocks/selection" >}}), and [comparators]({{< relref "/docs/building-blocks/gates/xnor" >}}) than every relay machine and tube computer ever built, combined — it just holds them where they can no longer be seen. This is the thesis the notebook opened with: **integration absorbed the building blocks; it never erased them.** And it is why understanding a [74HC14]({{< relref "/docs/glue-logic-toolbox/debounce" >}}) or a [74HC595]({{< relref "/docs/glue-logic-toolbox/more-outputs" >}}) is not learning obsolete history — it is learning the vocabulary that, multiplied a billionfold, is still exactly what a system on a chip is made of.
