---
title: "🧰 The Glue Logic Toolbox"
weight: 5
bookCollapseSection: true
---

# The Glue Logic Toolbox

This is the section that most books leave out. Instead of organizing by chip — here is the 74HC595, here is what it does — it organizes by *problem*. A working engineer rarely thinks "I want a shift register"; they think "I need more outputs than my microcontroller has pins." This part maps the problem to the part that solves it.

## Quick reference

| I need to… | Reach for |
|---|---|
| [one inverter]({{< relref "one-inverter" >}}) | 74HC04, or 74LVC1G04 (single-gate) |
| [debounce a signal]({{< relref "debounce" >}}) | 74HC14 (Schmitt inverter) |
| [more outputs]({{< relref "more-outputs" >}}) | 74HC595 (serial-in, parallel-out) |
| [more inputs]({{< relref "more-inputs" >}}) | 74HC165 (parallel-in, serial-out) |
| [switch analog signals]({{< relref "switch-analog-signals" >}}) | 4066 (quad analog switch) |
| [one of eight sensors]({{< relref "one-of-eight-sensors" >}}) | 4051 (8-channel analog mux) |
| [level shifting]({{< relref "level-shifting" >}}) | 74LVC, TXS, TXB |
| [a reset delay]({{< relref "reset-delay" >}}) | 555, an RC network, or a supervisor IC |

Each entry expands into its own page with the reasoning, alternatives, and gotchas.
