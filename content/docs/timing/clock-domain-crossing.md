---
title: "Clock Domain Crossing"
weight: 50
---

# Clock Domain Crossing

A modern chip does not run on one clock. A processor core, a memory interface, a radio, and a USB port each have their own, and signals constantly have to pass between them. Whenever a signal generated in one clock domain is sampled by another whose clock is unrelated, it is a **clock domain crossing (CDC)** — and it is where [metastability]({{< relref "metastability-and-synchronizers" >}}) stops being a curiosity and becomes a design discipline.

## Why Crossings Are Dangerous

Because the two clocks bear no fixed relationship, a signal arriving from domain A can change at *any* time relative to domain B's clock edge — including right in the [setup/hold]({{< relref "setup-and-hold" >}}) window, causing metastability. Worse, a **multi-bit** value crossing the boundary can be sampled mid-transition, catching some bits already updated and others not, and delivering a value that was never actually valid on either side. A CDC bug is the classic intermittent failure: rare, timing-dependent, and nearly impossible to reproduce on the bench.

## Crossing Safely

The techniques depend on what is crossing:

- **A single control bit or flag** — pass it through a [two-flip-flop synchronizer]({{< relref "metastability-and-synchronizers" >}}). This is the everyday case and the everyday fix.
- **A multi-bit value** — never synchronize each bit independently, since they would resolve on possibly different cycles and briefly form a wrong number. Instead, keep only one bit changing at a time by using a **[Gray-code]({{< relref "/docs/building-blocks/state-machines/state-encoding" >}})** representation (so at most one bit is ever uncertain), or move the whole word atomically with a **handshake** (a request/acknowledge pair, each synchronized) or an **asynchronous FIFO** — a dual-clock buffer, built from a memory and Gray-coded read/write pointers synchronized across the boundary, which is the standard way to stream data between domains.

The one rule underneath all of them: a raw multi-bit bus must never cross unsynchronized.

## Where the Abstraction Comes Full Circle

Clock domain crossing is the deepest point at which "it is all just logic" stops being true. Here a designer cannot reason in 0s and 1s alone; they must reason about *probability* and *physics* — the odds a flip-flop resolves in time, the analog reality of an edge arriving at the wrong instant. It is a fitting place to end.

This notebook began with switches that were unmistakably physical — [relays]({{< relref "/docs/before-the-ic/relays" >}}) and [tubes]({{< relref "/docs/before-the-ic/vacuum-tubes" >}}) — and watched the digital abstraction get built up on top of them, layer by layer, until whole systems disappeared onto a single die. Timing is where that abstraction, pushed to its limits, quietly hands the reins back to the analog world it was built on. The gates never stopped being circuits; the 0s and 1s were always voltages agreeing to behave. Understanding when they don't — a slow carry, a violated setup window, a metastable flip-flop between two clocks — is the difference between logic that works in a diagram and logic that works on real hardware. That, from the first relay to the last synchronizer, has been the whole point.
