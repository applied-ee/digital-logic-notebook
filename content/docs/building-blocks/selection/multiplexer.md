---
title: "Multiplexer"
weight: 30
---

# Multiplexer

A multiplexer (mux) selects one of many inputs and passes it to a single output, chosen by a set of select lines. With *n* select lines it picks among 2ⁿ inputs — an 8-to-1 mux needs three. It is the fundamental **data router**: many sources, one destination, and a control that decides which source gets through.

The standard parts are the 74151 (8-to-1), 74153 (dual 4-to-1), and 74157 (quad 2-to-1). Internally a mux is a [decoder]({{< relref "decoder" >}}) on the select lines enabling one input path, all [OR]({{< relref "/docs/building-blocks/gates/or" >}})-ed together — select, gate, combine.

## A Mux Is a Lookup Table

A multiplexer has a second life that is easy to miss. Wire the *variables* of a Boolean function to the **select** lines and the function's **truth-table values** to the data inputs, and the mux outputs exactly that function: for any input combination, it selects and passes the truth-table entry for that row. A 2ⁿ-to-1 mux can therefore implement *any* function of *n* variables, with no gate design at all — the [truth table]({{< relref "/docs/building-blocks/boolean-foundations/truth-tables" >}}) is simply loaded onto its inputs.

That is not a curiosity. It is precisely what a lookup table in an [FPGA]({{< relref "/docs/modern-world/fpgas" >}}) is: a small memory of truth-table bits feeding a multiplexer driven by the logic inputs. The mux is the mechanism that makes "store the answer for every input" into working combinational logic, which is why the FPGA fabric is built from LUTs rather than fixed gates.

## Routing and Sharing

Beyond computing functions, the everyday use is selection and sharing: choosing one of several data sources onto a bus, picking between a normal and a test input, or letting several sources take turns on one line. Scanned with a counter, a mux performs **parallel-to-serial** conversion — reading a set of inputs out one at a time — the same job a [shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}) does by a different mechanism. For switching *analog* signals rather than logic levels, the analog multiplexer (the [4051]({{< relref "/docs/glue-logic-toolbox/one-of-eight-sensors" >}})) does the equivalent with transmission gates. The reverse operation — one input fanned out to one of many outputs — is the [demultiplexer]({{< relref "demultiplexer" >}}).
