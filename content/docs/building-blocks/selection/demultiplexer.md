---
title: "Demultiplexer"
weight: 40
---

# Demultiplexer

A demultiplexer (demux) is the reverse of a [multiplexer]({{< relref "multiplexer" >}}): it takes a single input and routes it to one of many outputs, chosen by the select lines. One source, many destinations, and a control that decides which destination receives the signal while the others stay idle.

## The Same Hardware as a Decoder

A demux is not a distinct circuit — it is a [decoder]({{< relref "decoder" >}}) with its enable input used as the data input. The decoder already activates exactly the one output named by the select lines; feed data into its enable and that selected output follows the data instead of simply going active. This is why a part like the 74138 is sold as a "decoder/demultiplexer": the two functions are one piece of silicon addressed two ways. When the input is held permanently active it is a decoder; when the input carries data it is a demux.

## Multiplexer and Demultiplexer as a Pair

The natural partner of a demux is a mux, and together they form a routing link. A multiplexer at the source collapses many signals onto one line; a demultiplexer at the far end fans that one line back out to many destinations, with both ends' select lines stepped in step. Sharing a single wire this way — each source getting the line for a slice of time — is **time-division multiplexing**, the classic method behind everything from telephone trunk lines to serializing many signals down a single connection.

On its own a demux also does plain distribution and addressing: sending a strobe or a data bit to one selected register, channel, or device. And scanned with a counter it performs **serial-to-parallel** distribution — routing a stream of values out to a row of destinations one at a time — the mirror of the parallel-to-serial job a mux does at the source, and a close cousin of the [shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}) approach to the same problem.
