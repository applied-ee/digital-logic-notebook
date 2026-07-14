---
title: "ASICs"
weight: 50
---

# ASICs

An Application-Specific Integrated Circuit is custom silicon: the logic of a design fixed permanently into a chip made for one purpose. It is the [building blocks]({{< relref "/docs/building-blocks" >}}) of this book laid out in silicon at scale — millions or billions of gates and flip-flops, placed once and never changed.

## The Primitives, Fixed in Silicon

Most ASICs are built from a **standard-cell library**: a catalog of pre-designed, pre-characterized layouts for each primitive — a NAND cell, a NOR cell, a D [flip-flop]({{< relref "/docs/building-blocks/storage" >}}) cell, a full-adder cell, and so on. That library is nothing more than the [gates]({{< relref "/docs/building-blocks/gates" >}}) of Part II rendered as physical geometry. A designer writes the logic in an [HDL]({{< relref "hdl-concepts" >}}), synthesis maps it onto those cells, and place-and-route tools arrange and wire millions of them across the die. (Gate arrays and full-custom design are the other, less common points on the spectrum, trading flexibility for effort.)

## The Tradeoff Against the FPGA

An ASIC and an [FPGA]({{< relref "fpgas" >}}) solve the same problem — custom parallel hardware — with opposite economics. An FPGA is reconfigurable and available immediately, but each unit is larger, costlier, and hungrier because it carries all that programmable overhead. An ASIC bakes the design in, so each chip is as fast, small, and power-efficient as the process allows and cheap in volume — but it carries an enormous up-front cost (mask sets and design effort running into millions at advanced nodes) and it cannot be changed after fabrication. The rule of thumb follows directly: FPGAs for lower volumes, evolving designs, and prototyping; ASICs when the volume is high enough to amortize the up-front cost and the performance or power target demands it.

## Where It Stands

ASICs are current and everywhere high volume meets high performance — the processors, radios, and accelerators inside phones, networking gear, and consumer electronics. They are also the point where the [very-large-scale integration]({{< relref "/docs/before-the-ic/integration-scales" >}}) story arrives at its destination: whole designs, built from the same primitives that started as single relays and tubes, now committed permanently to one piece of silicon — and increasingly combined into a whole [system on a chip]({{< relref "socs" >}}).
