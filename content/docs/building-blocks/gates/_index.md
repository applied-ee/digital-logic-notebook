---
title: "Gates"
weight: 10
bookCollapseSection: true
---

# Gates

**Gates make decisions.**

A logic gate turns one or more input levels into an output level according to a fixed rule. From this handful of rules — invert, require all, require any, and their negations and exclusives — every combinational function can be constructed. NAND and NOR are *functionally complete*: either one alone can build all the others, which is exactly why they became the workhorse products of the logic era.

## Sections

- **[NOT]({{< relref "not" >}})** — Inversion: the simplest decision.
- **[AND]({{< relref "and" >}})** — True only when all inputs are true.
- **[OR]({{< relref "or" >}})** — True when any input is true.
- **[NAND]({{< relref "nand" >}})** — Universal gate; AND followed by inversion.
- **[NOR]({{< relref "nor" >}})** — Universal gate; OR followed by inversion.
- **[XOR]({{< relref "xor" >}})** — True when inputs differ.
- **[XNOR]({{< relref "xnor" >}})** — True when inputs match.
- **[Schmitt Trigger]({{< relref "schmitt-trigger" >}})** — A gate input with hysteresis, for clean edges from slow or noisy signals.
