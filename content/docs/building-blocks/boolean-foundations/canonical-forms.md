---
title: "Canonical Forms (SOP & POS)"
weight: 40
---

# Canonical Forms (SOP & POS)

A canonical form is a systematic, mechanical way to write down a function straight from its [truth table]({{< relref "truth-tables" >}}) — no cleverness required. There are two, and they are duals of each other: sum of products, built from the rows where the output is 1, and product of sums, built from the rows where it is 0.

## Sum of Products (from the 1s)

For each row where the output is **1**, write a **minterm**: the [AND]({{< relref "/docs/building-blocks/gates/and" >}}) of every input variable, taken true where the variable is 1 and complemented where it is 0. OR all those minterms together and the result is the **sum-of-products (SOP)** form — it is 1 for exactly the input combinations that should give 1, and nothing else. For a function that is 1 on rows 3 and 5 of three variables, F = A′BC + AB′C, often written compactly as Σm(3, 5).

SOP is the more common of the two because it maps directly onto two levels of logic — a bank of AND gates feeding one [OR]({{< relref "/docs/building-blocks/gates/or" >}}) gate — which is exactly the structure of a [decoder]({{< relref "/docs/building-blocks/selection/decoder" >}}) (all minterms) with an OR, and of the programmable AND-OR array inside a [PAL or CPLD]({{< relref "/docs/modern-world/plds-cplds" >}}).

## Product of Sums (from the 0s)

The dual approach uses the rows where the output is **0**. For each, write a **maxterm** — the OR of every variable, complemented where it is 1 — and AND all the maxterms together. This **product-of-sums (POS)** form is 0 for exactly the rows that should be 0. It maps to the mirror structure, OR gates feeding an AND, and is the natural choice when a function is mostly 1s with a few 0s.

## Canonical Versus Minimal

Both forms are *canonical*: every term names every variable, so they are complete and unique but usually far from the smallest expression. They are the systematic starting point, not the finished design. Reducing a canonical form to a minimal one is the job of [Boolean algebra]({{< relref "boolean-algebra" >}}) and [Karnaugh maps]({{< relref "karnaugh-maps" >}}) — the canonical form guarantees a correct expression, and minimization makes it a cheap one.
