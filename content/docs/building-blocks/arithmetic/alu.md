---
title: "ALU"
weight: 50
---

# ALU

The Arithmetic Logic Unit is where the building blocks converge. It is a single combinational block that performs a *selected* operation — add, subtract, AND, OR, XOR, compare, shift — on its two operands, with function-select inputs choosing which. It is the computational core of a processor's datapath, and it is assembled almost entirely from the primitives covered elsewhere in this section.

## What It Combines

An ALU is less an invention than an arrangement:

- An **[add/subtract unit]({{< relref "subtractors" >}})** — the [adder]({{< relref "half-and-full-adders" >}}) with its controllable input inversion — provides the arithmetic.
- Banks of **[gates]({{< relref "/docs/building-blocks/gates" >}})** (AND, OR, XOR, NOT across the operands) provide the logic operations.
- A **[multiplexer]({{< relref "/docs/building-blocks/selection/multiplexer" >}})** driven by the function-select lines picks which of those results actually appears at the output.
- **Status flags** come out alongside the result: zero (the result is all 0s), carry, signed overflow, and negative/sign — the bits a program branches on.

Feed it two operands and a function code, and it produces the result and the flags in one combinational sweep. It computes nothing sequential on its own; the sequencing around it is somebody else's job.

## The 74181 and What Came After

The landmark part is the **74181**, a 4-bit ALU on a single chip offering sixteen arithmetic and sixteen logic functions selected by its mode and function inputs. It was the first complete ALU available as one [MSI]({{< relref "/docs/before-the-ic/integration-scales" >}}) package, and it sat at the center of many 1970s minicomputers — several 74181s cascaded to build a wider word.

That is exactly the through-line the book keeps returning to. The ALU is the point where the [adder]({{< relref "half-and-full-adders" >}}), the logic [gates]({{< relref "/docs/building-blocks/gates" >}}), and a [selecting]({{< relref "/docs/building-blocks/selection/multiplexer" >}}) mux come together under control; wrap it with [registers]({{< relref "/docs/building-blocks/storage/registers" >}}) to hold the operands and result and a [sequencer]({{< relref "/docs/building-blocks/state-machines/sequencers" >}}) to feed it a stream of operations, and the result is the execution core of a CPU. The ALU inside any modern [microcontroller]({{< relref "/docs/modern-world/microcontrollers" >}}) or processor is this same arrangement, no longer a chip of its own but a region of a much larger die — the [functional building blocks]({{< relref "/docs/building-blocks" >}}), doing math.
