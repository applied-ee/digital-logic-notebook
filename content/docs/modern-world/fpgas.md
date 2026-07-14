---
title: "FPGAs"
weight: 30
---

# FPGAs

A Field-Programmable Gate Array is the [building blocks]({{< relref "/docs/building-blocks" >}}) of this book made configurable: a fabric of logic and flip-flops whose function is defined after manufacture by loading a configuration. Where a [microcontroller]({{< relref "microcontrollers" >}}) turns logic into a sequential program, an FPGA turns it into actual parallel hardware — every part of the design runs at once, the way discrete logic always did.

## A Fabric of Lookup Tables and Flip-Flops

The fabric is made of many small configurable blocks, each holding a **lookup table (LUT)** and a **flip-flop**, tied together by a mesh of programmable interconnect and surrounded by configurable I/O.

The LUT is the elegant part. A k-input LUT is just a tiny memory that stores the output for every input combination — which is to say, it stores a [truth table]({{< relref "/docs/building-blocks/boolean-foundations/truth-tables" >}}) directly. Load one truth table and the block is an AND; load another and it is a three-input XOR; the same silicon becomes any function of its inputs. The flip-flop beside it provides [sequential state]({{< relref "/docs/building-blocks/storage" >}}), and the interconnect wires thousands of these blocks into whatever the design requires. Modern parts add hardened blocks — memory, arithmetic/DSP slices, even CPU cores — for functions too common or too demanding to build from LUTs.

## Where It Fits

The FPGA occupies the gap between a microcontroller and custom silicon. It offers genuine hardware parallelism and nanosecond determinism that a sequential CPU cannot, without the enormous cost and finality of an [ASIC]({{< relref "asics" >}}) — and, being reconfigurable, it can be revised or entirely repurposed by loading a new configuration. That makes it the tool of choice for high-throughput signal processing, custom interfaces, prototyping future ASICs, and anywhere a problem is inherently parallel.

Because the fabric holds a stored truth table rather than a fixed gate, minimizing a function to the last gate matters far less than it did with discrete logic — the synthesis tool simply fills the LUTs. The design itself is written not as a schematic but in a [hardware description language]({{< relref "hdl-concepts" >}}), which is where the next page turns.
