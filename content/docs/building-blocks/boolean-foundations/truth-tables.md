---
title: "Truth Tables"
weight: 10
---

# Truth Tables

A truth table is the complete, unambiguous specification of a combinational function: every possible input combination on the left, the output it must produce on the right. It says *what* a function does without saying anything about *how* it is built, which makes it the natural starting point for every design and the common ground between a specification and a circuit.

## Complete, but It Scales Badly

For *n* inputs there are 2ⁿ combinations, so a truth table has 2ⁿ rows. That is fine for the two- and three-input [gates]({{< relref "/docs/building-blocks/gates" >}}) whose behavior *is* a small truth table, but it grows explosively: four inputs give 16 rows, eight give 256, and twenty give over a million. Completeness is the strength and the weakness — nothing is left unspecified, but the table is unusable as a design tool much past a handful of variables. That is exactly why the rest of this subsection exists: [Boolean algebra]({{< relref "boolean-algebra" >}}) and [canonical forms]({{< relref "canonical-forms" >}}) compress the table into an expression, and [Karnaugh maps]({{< relref "karnaugh-maps" >}}) reorganize it to be simplified by eye.

## Don't-Cares

Not every row always matters. If an input combination can never occur, or if the output for it genuinely does not matter, its entry is marked as a **don't-care** (X) rather than a fixed 0 or 1. Don't-cares are not sloppiness — they are *freedom*. A minimizer is allowed to make each one whichever value yields simpler logic, so recording them honestly often produces a noticeably smaller circuit than pinning every output down needlessly.

## The Table Made Physical

The truth table is not only a design aid; it is a thing hardware directly implements. Store the output column in a memory addressed by the inputs and the memory *is* the function — which is precisely what a ROM does, and what a lookup table in an [FPGA]({{< relref "/docs/modern-world/fpgas" >}}) is. A [multiplexer]({{< relref "/docs/building-blocks/selection/multiplexer" >}}) with the table wired to its data inputs does the same thing with switches. "Store the answer for every input" is a legitimate, common way to build logic, and it is the truth table taken literally.
