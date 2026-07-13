---
title: "Digital Logic Notebook"
type: docs
---

<div class="landing-hero">
<h1>Digital Logic Notebook</h1>
</div>

Digital logic did not arrive fully formed. It was built up in layers — mechanical switches and relays giving way to vacuum tubes, tubes to discrete transistors, transistors to small-scale integrated gates, and gates to the dense programmable fabrics and processors that define modern hardware. Each layer solved the limits of the one before it, and each carried forward ideas that only make sense once the earlier layer is understood.

This notebook traces that evolution — but its central argument is not historical. It is this:

> **Digital design has evolved by moving functionality to higher levels of integration — not by making the lower levels disappear.**

That distinction matters. An engineer who understands a 74HC14, a 74HC245, or a 74HC595 is not learning obsolete technology; they are learning the vocabulary that still underpins digital hardware. The package got smaller, the supply voltage dropped, and sometimes the function moved inside a microcontroller or FPGA — but the idea stayed the same. This is **not a nostalgia project.** It is an account of the building blocks practicing hardware engineers still reach for, and *why*.

In that sense the notebook aims to be the missing bridge between two familiar reference points: *NAND to Tetris*, which teaches how digital logic can be built from first principles, and embedded systems work, which teaches how to write firmware. The question in the middle — **what are the primitives real hardware still reaches for, and why do they persist?** — is what this notebook answers.

**What lives here:**

- **The through-line** — How each generation of logic technology grew out of the constraints of the last, and which concepts carried forward unchanged.
- **Why, not just what** — Beyond how a device works, why it exists: the problem it solved, the cost it paid, and what it made possible.
- **Problems, not just parts** — A glue-logic toolbox organized by the problem in front of you ("I need more outputs") rather than by chip number.
- **Honest obsolescence** — Which classic parts are genuinely dead, which are quietly immortal, and what replaced the rest.

## How It's Organized

The notebook follows the evolution of logic technology from the physical switches that first represented discrete states, through the primitive building blocks and the logic families that industrialized them, to the programmable and integrated forms that define current practice.

{{< graphviz >}}
digraph arc {
  bgcolor="transparent";
  rankdir=TB;
  node [shape=box, style="rounded,filled", fillcolor="#ffffff", color="#2563eb", fontcolor="#1e293b", fontname="Helvetica,Arial,sans-serif", fontsize=12, margin="0.18,0.08"];
  edge [color="#2563eb", arrowsize=0.7];

  "Mechanical" -> "Relay Logic" -> "Discrete Transistors" -> "RTL / DTL" -> "TTL" -> "CMOS" -> "HC / HCT Families" -> "Glue Logic Era" -> "Microcontrollers" -> "CPLDs / FPGAs" -> "ASIC / SoC";
}
{{< /graphviz >}}

<div class="section-cards">

<div class="section-card">

### [Before the IC]({{< relref "/docs/before-the-ic" >}})

Relays, tubes, and transistors — and the pressures that drove functionality onto silicon. Why NAND gates became products.

</div>

<div class="section-card">

### [Functional Building Blocks]({{< relref "/docs/building-blocks" >}})

The heart of the notebook: gates, Boolean foundations, arithmetic, storage, counting, state machines, selection, moving data, and analog helpers — the technology-independent primitives everything is built from.

</div>

<div class="section-card">

### [Evolution of Implementation]({{< relref "/docs/implementation" >}})

The logic-family lineage — RTL, DTL, TTL, CMOS, HC/HCT, LVC/AHC, and tiny logic — and why the function survived every change of transistor.

</div>

<div class="section-card">

### [Timing & the Real World]({{< relref "/docs/timing" >}})

Where the ideal abstraction leaks: propagation delay, setup/hold, clocks, metastability, and clock-domain crossing — the source of most puzzling hardware failures.

</div>

<div class="section-card">

### [The Glue Logic Toolbox]({{< relref "/docs/glue-logic-toolbox" >}})

Organized by problem, not by chip: the part to reach for when you need one inverter, a debounce, more I/O, an analog switch, level shifting, or a reset delay.

</div>

<div class="section-card">

### [What Became Obsolete?]({{< relref "/docs/obsolete" >}})

An honest reference: which classic parts are dead, which are quietly immortal, and what replaced the rest.

</div>

<div class="section-card">

### [The Modern World]({{< relref "/docs/modern-world" >}})

Microcontrollers, FPGAs, ASICs, and SoCs — how they absorbed logic rather than replacing it, and why discrete parts persist anyway.

</div>

<div class="section-card">

### [Glossary]({{< relref "/docs/glossary" >}})

Terms and definitions used throughout this notebook. Hover over any highlighted term to see its definition inline.

</div>

</div>
