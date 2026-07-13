---
title: "🔬 The Technology"
weight: 3
bookCollapseSection: true
---

# The Technology

The building blocks in **Primitive Building Blocks** are behaviors. This section is about the *implementations* — the successive logic families that built those behaviors from real transistors, each trading away the weaknesses of the one before. The progression is the classic lineage of digital electronics, and it is where references like the *TTL Cookbook* and *CMOS Sourcebook* live.

Each family is worth understanding for a different reason:

- **[RTL]({{< relref "rtl" >}})** — Obsolete. Worth knowing for the history: the first practical IC logic.
- **[DTL]({{< relref "dtl" >}})** — Obsolete. Worth understanding for *why TTL replaced it*.
- **[TTL]({{< relref "ttl" >}})** — Historically enormous and mostly replaced, but still worth understanding for the 74xx numbering scheme, the schematics, industrial equipment, and retrocomputing.
- **[CMOS]({{< relref "cmos" >}})** — A milestone. Negligible static power, and still everywhere.
- **[HC / HCT Families]({{< relref "hc-hct" >}})** — Probably the modern baseline for discrete logic.
- **[LVC / AHC]({{< relref "lvc-ahc" >}})** — Today's logic: low voltage, fast, widely stocked.
- **[Tiny Logic (74LVC1Gxx)]({{< relref "tiny-logic" >}})** — Very modern: one gate per package, for surgical fixes and glue.

The through-line: the *function* of a gate barely changed across fifty years. What changed was the transistor technology, the supply voltage, the speed, and the package.
