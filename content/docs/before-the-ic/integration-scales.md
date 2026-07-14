---
title: "SSI, MSI, LSI & VLSI"
weight: 50
---

# SSI, MSI, LSI & VLSI

Once whole circuits could be [fabricated at once]({{< relref "why-ics-happened" >}}), the only open question was how many devices to put on a single die. The answer grew by orders of magnitude over two decades, and the industry named the rungs of that climb: small-, medium-, large-, and very-large-scale integration. The names are worth knowing not as trivia but because each rung sold a *different level of abstraction* as a product — and that progression is exactly how the rest of this notebook is organized.

## The Scales

The boundaries were always fuzzy and quoted differently by everyone, but the orders of magnitude are the point:

| Scale | Devices per chip (rough) | Era | What fit on one chip | Examples |
|---|---|---|---|---|
| **SSI** — small-scale | a few gates (tens of transistors) | early 1960s | individual gates, a flip-flop or two | 7400 quad NAND, 7474 dual D flip-flop |
| **MSI** — medium-scale | tens to a few hundred gates | late 1960s | a whole function | 74138 decoder, 74151 multiplexer, 74161 counter, 74181 ALU |
| **LSI** — large-scale | thousands of gates | early–mid 1970s | a subsystem | Intel 4004 CPU (~2,300 transistors), early RAM/ROM |
| **VLSI** — very-large-scale | tens of thousands to millions+ | late 1970s onward | a whole system | Motorola 68000 (~68,000), modern processors |

Read down the "what fit on one chip" column and the story is clear. SSI put the primitives themselves in a package — a chip *was* a few gates. MSI put a complete function in a package — a counter, a decoder, a multiplexer, an arithmetic-logic unit. LSI put a subsystem in a package — a processor or a memory. VLSI put an entire system on one die.

## Same Primitives, More Per Package

Nothing about the *logic* changed as chips climbed this ladder. A gate on a VLSI processor is the same gate that was a whole SSI package in 1965; a flip-flop is a flip-flop. What improved was fabrication — how finely and reliably photolithography could pattern silicon — and [Moore's Law]({{< relref "why-ics-happened" >}}) is simply the name for how fast that improved. Each rung is the same transistors and the same primitives, just more of them per die.

What actually rose, rung by rung, was the level of abstraction being sold. The buyer of an SSI chip wired [gates]({{< relref "/docs/building-blocks/gates" >}}) into functions. The buyer of an MSI chip bought the function already built — the [arithmetic]({{< relref "/docs/building-blocks/arithmetic/alu" >}}), [selection]({{< relref "/docs/building-blocks/selection" >}}), and [counting]({{< relref "/docs/building-blocks/counting" >}}) blocks of this book each became a single MSI part. The buyer of an LSI or VLSI chip bought the subsystem or the system. Integration did not invent new logic; it kept absorbing more of the wiring that used to be the designer's job.

## Scale and Family Are Different Axes

It is easy to conflate the integration scale with the logic technology, but they are independent. *Scale* answers "how many devices on the chip"; *family* answers "how each gate is built from transistors." A 7400 is TTL **and** SSI; a 74HC161 is CMOS **and** MSI; a modern processor is CMOS **and** VLSI. The same integration scale appears in many families, and the same family spans every scale.

This page has covered the scale axis. The other axis — how the gates themselves were implemented, from RTL through TTL to CMOS — is the subject of the next chapter, [Evolution of Implementation]({{< relref "/docs/implementation" >}}).

## Where the Ladder Went

The naming stopped at VLSI. "ULSI" (ultra-large-scale) was coined for millions of transistors and never really caught on, because once every chip was VLSI the distinction stopped being useful. Modern dies hold *billions* of transistors and are still, technically, just VLSI — the industry gave up adding prefixes and went back to counting transistors directly.

The ladder also maps cleanly onto the rest of this notebook, which is a good way to close the run-up to the integrated circuit:

- **SSI** is [Functional Building Blocks]({{< relref "/docs/building-blocks" >}}) sold one primitive per package — and those SSI and MSI parts never disappeared; the [glue-logic toolbox]({{< relref "/docs/glue-logic-toolbox" >}}) is where they are still reached for today.
- **MSI** is the functional blocks — counters, decoders, multiplexers, ALUs — packaged as single parts.
- **LSI and VLSI** are the [modern world]({{< relref "/docs/modern-world" >}}): microcontrollers, FPGAs, ASICs, and SoCs, where whole systems live on one chip.

Everything from here forward is built on these scales. What remains is to see how the gates were actually implemented, how the primitives behave, and what became of them as integration absorbed more and more of the design.
