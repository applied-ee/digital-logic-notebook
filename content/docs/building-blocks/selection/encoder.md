---
title: "Encoder"
weight: 20
---

# Encoder

An encoder is the reverse of a [decoder]({{< relref "decoder" >}}): it takes 2ⁿ inputs, one of them active, and produces the *n*-bit binary code that names which one. Eight input lines become a 3-bit number, sixteen become a 4-bit number. Where a decoder expands a code into one-hot, an encoder compresses one-hot back into a code.

## The Problem of More Than One

A plain encoder assumes *exactly one* input is active. If two are high at once, the naïve output is meaningless — it is neither input's code. Real inputs do not cooperate, so the useful part is the **priority encoder**: when several inputs are active, it outputs the code of the **highest-priority** one and ignores the rest, usually flagging separately whether *any* input was active at all. The standard parts are the 74148 (8-to-3 priority) and 74147 (10-line-to-4-line BCD priority).

Structurally each output bit is an [OR]({{< relref "/docs/building-blocks/gates/or" >}}) across the input lines whose codes have that bit set, with the priority logic layered on top to suppress lower inputs when a higher one is present.

## Where It's Used

The archetypal use is **interrupt handling**: many devices each assert their own request line, and a priority encoder turns that set of lines into the binary vector of the most urgent one for the processor to service — resolving simultaneous requests by priority in the process. The same shape appears in keypad and position encoding, in finding the highest set bit of a word, and, in general, wherever a [one-hot]({{< relref "/docs/building-blocks/state-machines/state-encoding" >}}) signal has to be converted back to a compact binary index. Encoder and decoder are the round trip between "which one" as a code and "which one" as a single active line.
