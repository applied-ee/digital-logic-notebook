---
title: "Half & Full Adders"
weight: 10
---

# Half & Full Adders

Binary addition is just a combinational function, and it is built from one small cell repeated. That cell is the adder, and understanding it is understanding how gates do arithmetic.

## The Half Adder

A half adder adds two bits and produces a sum and a carry. The sum is 1 when the inputs differ, and the carry is 1 only when both are 1 — which is to say the sum is an [XOR]({{< relref "/docs/building-blocks/gates/xor" >}}) and the carry is an [AND]({{< relref "/docs/building-blocks/gates/and" >}}):

| A | B | Sum | Carry |
|---|---|-----|-------|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

Sum = A ⊕ B, Carry = A · B. It is called *half* because it has no way to accept a carry coming in from a lower position — so it can only add the least-significant bit of a larger number.

## The Full Adder

A full adder fixes that by taking a third input, the **carry-in** from the stage below. It adds three bits and produces a sum and a carry-out:

| A | B | Cin | Sum | Cout |
|---|---|-----|-----|------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

The sum is A ⊕ B ⊕ Cin, and the carry-out is 1 whenever at least two of the three inputs are 1 (a majority function, AB + Cin(A ⊕ B)).

## Building a Word-Wide Adder

Chain N full adders, each stage's carry-out feeding the next stage's carry-in, and the result adds two N-bit numbers. This **ripple-carry adder** is simple but carries the same flaw as the [ripple counter]({{< relref "/docs/building-blocks/counting/ripple-counters" >}}): the carry has to propagate through every stage before the top bits are valid, so the [delay]({{< relref "/docs/timing/propagation-delay-and-fan-out" >}}) grows with word width. Faster adders attack this with **carry-lookahead**, computing the carries in parallel from the inputs rather than waiting for them to ripple — the trick behind fast arithmetic parts like the 74283. Either way, the adder is the foundation the [subtractor]({{< relref "subtractors" >}}) and the [ALU]({{< relref "alu" >}}) are built on.
