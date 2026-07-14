---
title: "XOR"
weight: 60
---

# XOR

The exclusive-OR gate outputs high when its inputs *differ* and low when they match. Where OR asks "is any input high?", XOR asks "is exactly an odd number of inputs high?" — for two inputs, "are they different?"

| A | B | A XOR B |
|---|---|---------|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

## The Difference Detector

XOR is fundamentally a **difference detector**, and two identities make it far more useful than that description suggests:

- **A XOR 0 = A** — the signal passes through unchanged.
- **A XOR 1 = NOT A** — the signal is inverted.

So one input of an XOR acts as a **controlled inverter**: hold it low and the other input passes; hold it high and it inverts. That single trick underlies a surprising amount of hardware.

Unlike AND and OR, XOR is not a simple series/parallel switch network — it needs both a signal and its complement — so it costs noticeably more silicon, often around a dozen transistors versus four for a [NAND]({{< relref "nand" >}}). XOR is genuinely more expensive than the basic gates, which matters in circuits that use a lot of it.

## Where It's Used

XOR shows up wherever difference, addition, or parity is involved:

- **Arithmetic** — the sum bit of a [half or full adder]({{< relref "/docs/building-blocks/arithmetic/half-and-full-adders" >}}) is A XOR B; all binary addition is built on it.
- **Parity and error detection** — XOR-ing every bit of a word together produces its [parity]({{< relref "/docs/building-blocks/arithmetic/parity-and-error-detection" >}}), the cheapest integrity check there is.
- **Comparison** — XOR is high exactly when two bits differ, so it is the per-bit inequality test (and its complement, [XNOR]({{< relref "xnor" >}}), the equality test).
- **Controlled inversion** — from two's-complement negation to scramblers and linear-feedback shift registers, "invert this only when told to" is an XOR.
