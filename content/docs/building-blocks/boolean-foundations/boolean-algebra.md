---
title: "Boolean Algebra"
weight: 20
---

# Boolean Algebra

Boolean algebra is the algebra of two-valued logic: variables that are only ever 0 or 1, combined with three operations — AND (·), OR (+), and NOT (′). It is the lever between a [truth table]({{< relref "truth-tables" >}}) and a circuit, because it lets a logic expression be manipulated and *simplified* on paper before a single [gate]({{< relref "/docs/building-blocks/gates" >}}) is committed. Fewer terms mean fewer gates, fewer levels of logic, less delay, and less power.

## The Identities

The manipulation rests on a small set of laws. Most come in dual pairs — swap AND for OR and 0 for 1 and one identity becomes the other:

| Law | AND form | OR form |
|---|---|---|
| Identity | A · 1 = A | A + 0 = A |
| Null | A · 0 = 0 | A + 1 = 1 |
| Idempotent | A · A = A | A + A = A |
| Complement | A · A′ = 0 | A + A′ = 1 |
| Absorption | A · (A + B) = A | A + A·B = A |
| Distributive | A·(B + C) = A·B + A·C | A + B·C = (A + B)·(A + C) |

Add the obvious ones — commutative and associative ordering, and involution ((A′)′ = A) — and these are enough to transform any expression into any equivalent one. The second distributive law (A + BC = (A+B)(A+C)) is the one that surprises people, because ordinary arithmetic has no equivalent.

## Where It Fits

Algebraic simplification is the general-purpose tool: it works for any number of variables and it is what a synthesis tool does internally. By hand it is powerful but easy to get lost in, which is why two special cases get their own treatment. [De Morgan's theorems]({{< relref "demorgans-theorems" >}}) handle inversion across a whole gate and are the single most-used identities in practice, and [Karnaugh maps]({{< relref "karnaugh-maps" >}}) turn simplification of small functions from algebra into pattern-spotting. All three are doing the same job — trading a complicated expression for a simpler circuit that computes the identical truth table.
