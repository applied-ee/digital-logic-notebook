---
title: "Subtractors"
weight: 20
---
{{< katex >}}{{< /katex >}}

# Subtractors

Hardware rarely builds a dedicated subtractor, because it does not need one. Subtraction is addition of a negative number, and in two's-complement arithmetic negating a number is nearly free — so the same [adder]({{< relref "half-and-full-adders" >}}) that adds also subtracts, with a trivial change to its inputs.

## Subtraction Is Addition in Disguise

In two's complement, a number is negated by **inverting all its bits and adding 1**. Therefore:

$$ A - B = A + (\overline{B}) + 1 $$

Read that as a recipe for the existing adder: complement every bit of B, feed the result into the adder alongside A, and set the **carry-in of the lowest stage to 1** to supply the "+1." No borrow logic, no second arithmetic unit — an ordinary ripple-carry or lookahead adder produces A − B directly.

## One Unit That Adds or Subtracts

This leads to the standard add/subtract circuit. Put an [XOR]({{< relref "/docs/building-blocks/gates/xor" >}}) gate on each B input, controlled by a single **SUB** line: with SUB = 0 the XORs pass B unchanged (and the adder adds), and with SUB = 1 they invert B (a [controlled inverter]({{< relref "/docs/building-blocks/gates/xor" >}})). Wire that same SUB line to the carry-in to add the necessary 1, and one block adds when told to add and subtracts when told to subtract. That controllable add/subtract unit is the arithmetic heart of the [ALU]({{< relref "alu" >}}).

## Borrow and Overflow

Discrete half- and full-subtractors built around *borrow* instead of carry do exist, but they are mostly a teaching device; real designs use two's-complement addition. The two things to watch are that the carry-out of a subtraction indicates borrow (inverted, depending on convention), and that **signed overflow** — a result too large to fit the word — must be detected separately, from the carry into versus out of the sign bit. Comparing two numbers is closely related: subtracting them and inspecting the result's sign is one way to build a [magnitude comparator]({{< relref "magnitude-comparators" >}}).
