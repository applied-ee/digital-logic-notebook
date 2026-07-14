---
title: "Clocks & Distribution"
weight: 30
---

# Clocks & Distribution

The clock is the heartbeat that keeps a synchronous system in step: every [flip-flop]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}}) updates on its edge, so the whole machine advances together. That only works if a clean edge reaches every flip-flop at very nearly the same instant — which is harder than it sounds, and where a surprising amount of real-world timing trouble lives.

## Where Clocks Come From

A clock starts at an oscillator. A **crystal oscillator** gives an accurate, stable frequency and is the reference for anything that must keep real time or talk to the outside world. Cheaper **RC or ring oscillators** are built from an inverter and a delay, trading precision for cost — the [Schmitt-trigger relaxation oscillator]({{< relref "/docs/building-blocks/gates/schmitt-trigger" >}}) is the simplest example. A **PLL** multiplies or divides a reference to synthesize the several frequencies a modern chip needs, and simple [frequency dividers]({{< relref "/docs/building-blocks/counting/frequency-dividers" >}}) derive slower clocks from a fast one.

## The Two Enemies: Jitter and Skew

Even a good clock is not perfect, and two imperfections directly erode timing margin:

- **Jitter** is cycle-to-cycle variation in *when* the edge arrives — the period is not exactly constant. It subtracts from the [timing budget]({{< relref "setup-and-hold" >}}), because a design must work even on the short cycles, and it matters most at high speed and when sampling analog signals.
- **Skew** is the *same* edge reaching different flip-flops at different times, because the clock travels different distances through different buffers to get to each one. Skew adds directly to the setup/hold equation — a little skew in the wrong direction can turn a passing path into a failing one, and it is a common cause of hold violations.

## Getting the Edge Everywhere at Once

A clock is the most heavily loaded and most timing-critical net on a chip, fanning out to thousands or millions of flip-flops. Delivering it with low skew takes a dedicated **clock distribution network** — balanced structures like H-trees and buffered clock trees engineered so every endpoint sees nearly the same delay. And because the clock edge is ultimately a real, fast analog signal, its rise time, ringing, and integrity are as much a physical concern as a logical one; the board- and chip-level signal-integrity side of that belongs to the *EE Notebook*. Here the point is that the clean, simultaneous edge synchronous logic assumes is something a design has to actively build — and its imperfections, jitter and skew, are where the assumption starts to fray, especially once a system has [more than one clock]({{< relref "clock-domain-crossing" >}}).
