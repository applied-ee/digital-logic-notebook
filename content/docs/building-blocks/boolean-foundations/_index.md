---
title: "Boolean Foundations"
weight: 20
bookCollapseSection: true
---

# Boolean Foundations

**Gates obey algebra.**

Every combinational circuit is a Boolean expression in disguise, and every Boolean expression can be drawn as gates. That equivalence is the most useful lever in digital design: a function can be written as a truth table, reduced with algebra or a Karnaugh map, and only then committed to hardware — trading gates for speed, or speed for gates, on purpose rather than by accident. This is also where the difference between the *intended* logic and the *momentary* glitches a real circuit produces first shows up.

## Sections

- **[Truth Tables]({{< relref "truth-tables" >}})** — The exhaustive specification every combinational function starts from.
- **[Boolean Algebra]({{< relref "boolean-algebra" >}})** — Identities and laws for manipulating logic expressions.
- **[De Morgan's Theorems]({{< relref "demorgans-theorems" >}})** — Why NAND and NOR are interchangeable with everything else.
- **[Canonical Forms (SOP & POS)]({{< relref "canonical-forms" >}})** — Minterms, maxterms, and the standard ways to write a function.
- **[Karnaugh Maps]({{< relref "karnaugh-maps" >}})** — Visual minimization: fewer gates, fewer surprises.
- **[Hazards & Glitches]({{< relref "hazards-and-glitches" >}})** — The transient outputs a correct truth table doesn't predict.
