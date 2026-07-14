---
title: "XNOR"
weight: 70
---

# XNOR

XNOR is the complement of [XOR]({{< relref "xor" >}}): its output is high when its inputs *match* and low when they differ. If XOR is the difference detector, XNOR is the **equality detector**.

| A | B | A XNOR B |
|---|---|----------|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

## Equality in One Gate

XNOR answers "are these two bits the same?" directly — a single gate that is high precisely when A equals B. Because it is XOR inverted, it shares XOR's cost and its complementary identities: **A XNOR 0 = NOT A** and **A XNOR 1 = A**, so it too can act as a controlled inverter, just with the opposite sense to XOR.

## Where It's Used

The equality behavior makes XNOR the natural per-bit building block of a **comparator**: a [magnitude comparator]({{< relref "/docs/building-blocks/arithmetic/magnitude-comparators" >}}) decides that two words are equal by XNOR-ing them bit for bit and requiring every result to be high (a wide AND of XNORs). It also appears in **even-[parity]({{< relref "/docs/building-blocks/arithmetic/parity-and-error-detection" >}})** logic, where a chain of XNORs computes the complement of the XOR-based odd parity. In practice XNOR is used less often than XOR only because so many circuits are framed around detecting *change* rather than *sameness* — the two are the same gate wearing opposite bubbles.
