---
title: "Magnitude Comparators"
weight: 30
---

# Magnitude Comparators

A magnitude comparator decides the relationship between two binary numbers — whether A equals B, A is greater, or A is less. It answers in logic what a subtraction answers in arithmetic, and it is a distinct, common building block wherever hardware has to make a decision about a value.

> **Note:** this is the *digital* comparator, comparing multi-bit numbers. It shares its name with the analog voltage [comparator]({{< relref "/docs/building-blocks/analog-helpers/comparators" >}}) in Analog Helpers, which compares two continuous voltages and outputs a single bit — a different device for a different job.

## Equality Is a Row of XNORs

The simplest comparison is equality. Two numbers are equal exactly when they match in *every* bit, and "these two bits are the same" is precisely what an [XNOR]({{< relref "/docs/building-blocks/gates/xnor" >}}) reports. So an equality comparator is one XNOR per bit position, [AND]({{< relref "/docs/building-blocks/gates/and" >}})ed together: A = B is true only when all the per-bit XNORs are 1. This is the direct use the XNOR page points to.

## Greater and Less

Deciding *which* is larger takes an ordered look. Working from the most-significant bit down, the numbers are equal until the first bit position where they differ; at that position, whichever number has the 1 is the larger, and lower bits no longer matter. That priority-from-the-top structure is what the greater-than and less-than logic implements. Equivalently, [subtracting]({{< relref "subtractors" >}}) one from the other and inspecting the sign and borrow gives the same answer — comparison and subtraction are two views of the same operation.

## Cascading

The classic part is the 7485, a 4-bit magnitude comparator with A>B, A=B, and A<B outputs and matching *cascade inputs*. The cascade inputs let comparators be chained: a higher stage's result dominates, and its A=B output hands the decision down to the next stage only when its own bits tie. Stringing several together compares words of any width — the same "resolve from the most-significant end" rule, now spanning chips. Magnitude comparison shows up in threshold and limit checks, address-range decoding, sorting, and any control decision that hinges on one value being larger than another.
