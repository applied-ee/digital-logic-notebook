---
title: "⏱️ Timing & the Real World"
weight: 4
bookCollapseSection: true
---

# Timing & the Real World

Everything up to this point treated logic as instantaneous and ideal: a gate's output *is* its inputs' function, a flip-flop captures *at* the clock edge. Real gates take time to switch, real clocks arrive at slightly different moments in different places, and real inputs sometimes change at exactly the wrong instant. This is where the digital abstraction leaks and where most puzzling hardware failures actually live.

The rule that ties this chapter together: **as long as signals settle within the time the clock allows, the abstraction holds — the moment they don't, behavior turns nondeterministic.** Setup and hold windows, propagation delay, clock skew, and metastability are all statements about that margin.

## Sections

- **[Propagation Delay & Fan-Out]({{< relref "propagation-delay-and-fan-out" >}})** — How long a gate takes to respond, and how loading makes it worse.
- **[Setup & Hold Time]({{< relref "setup-and-hold" >}})** — The window around a clock edge in which data must be stable.
- **[Clocks & Distribution]({{< relref "clocks-and-distribution" >}})** — Sources, jitter, skew, and getting the edge everywhere at once.
- **[Metastability & Synchronizers]({{< relref "metastability-and-synchronizers" >}})** — What happens when setup/hold is violated, and the two-flip-flop fix.
- **[Clock Domain Crossing]({{< relref "clock-domain-crossing" >}})** — Moving signals safely between unrelated clocks.

## Related, in the other notebooks

This chapter stays at the logic-device level. The board- and system-level physics that these effects bleed into — **signal integrity**, **power integrity and decoupling**, **transmission-line / high-speed effects**, and **bus protocols** — are covered in the sibling notebooks rather than duplicated here:

- **EE Notebook** — *Digital Electronics → When Digital Breaks Down* and *Fundamentals* (signal integrity, power integrity, high-speed effects).
- **Embedded Systems** — *Digital Interfaces & Peripheral Patterns* (bus protocols and their firmware-side details).
