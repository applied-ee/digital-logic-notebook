---
title: "Decoder"
weight: 10
---

# Decoder

A decoder takes an *n*-bit binary code and activates exactly one of its 2ⁿ outputs — the one whose number matches the input. A 3-bit input picks one of eight outputs, a 4-bit input one of sixteen. It turns a compact binary number into a **one-hot** signal: "this specific one, and no other."

## Every Output Is a Minterm

Internally, each output is an [AND]({{< relref "/docs/building-blocks/gates/and" >}}) of the input bits in a particular true/complemented combination — output 5 of a 3-to-8 decoder is high only for the input `101`. That combination is a **minterm**, so a decoder generates *all* the minterms of its inputs at once. Because any Boolean function is a sum of the minterms where it is true (its [sum-of-products form]({{< relref "/docs/building-blocks/boolean-foundations/canonical-forms" >}})), a decoder plus a single OR gate can build any function of its input variables — which is one reason decoders show up far beyond their obvious use.

The standard parts are the 74138 (3-to-8), 74139 (dual 2-to-4), and 74154 (4-to-16), usually with active-low outputs and one or more enable inputs.

## Where It's Used

The classic job is **address decoding**: the high bits of an address bus feed a decoder whose outputs are the chip-select lines, so each memory or peripheral responds only to its own address range. Decoders also drive one-of-many selection generally — enabling one device, lighting one indicator, decoding a [sequencer]({{< relref "/docs/building-blocks/state-machines/sequencers" >}})'s step into a control line — and display drivers (BCD-to-seven-segment) are decoders with a custom output pattern. The 74138 is squarely in the "still used today" column: turning a binary selection into individual enables is a job a processor rarely absorbs cleanly.

## The Same Chip as a Demultiplexer

A decoder's enable input is the key to a second identity. Feed data into the enable and the decoder becomes a [demultiplexer]({{< relref "demultiplexer" >}}) — the addressed output follows the data while the rest stay idle. Decoder and demux are not two circuits but one, used two ways. The reverse operation — collapsing a one-hot input back to a binary code — is the [encoder]({{< relref "encoder" >}}).
