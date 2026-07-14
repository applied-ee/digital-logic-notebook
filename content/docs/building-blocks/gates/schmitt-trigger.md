---
title: "Schmitt Trigger"
weight: 80
---

# Schmitt Trigger

A Schmitt trigger is not a new logic function — it is usually just an inverter or buffer — but a special *input characteristic*: **hysteresis**. Instead of one switching threshold, it has two, and which one is active depends on which way the input is currently moving. That small change is what lets logic accept slow, noisy, or sloppy signals and still produce clean edges.

## Two Thresholds Instead of One

An ordinary gate has a single threshold, and any wobble of the input around that level produces a burst of output transitions. A Schmitt-trigger input has an **upper threshold** (V<sub>T+</sub>) and a **lower threshold** (V<sub>T−</sub>), with a gap between them:

- Rising input: the output does not switch until the input climbs past V<sub>T+</sub>.
- Falling input: the output does not switch back until the input drops below V<sub>T−</sub>.

Once switched, the input must travel all the way across that gap to switch again. Noise smaller than the gap is simply ignored, and a slow ramp produces exactly one clean transition instead of a shower of them. The width of the gap is the noise immunity, bought at the cost of a little threshold uncertainty.

## Where It's Used

The Schmitt trigger is the standard fix wherever an input is not already a clean logic edge:

- **Debouncing switches** — a mechanical contact (a button, or the bouncing [relay contacts]({{< relref "/docs/before-the-ic/relays" >}}) that first exposed the problem) rings for milliseconds; a Schmitt input with an RC filter turns that mess into one edge. This is exactly the job of the [debounce]({{< relref "/docs/glue-logic-toolbox/debounce" >}}) part in the glue-logic toolbox — classically the 74HC14 hex inverting Schmitt trigger.
- **Squaring up slow signals** — sensor outputs, RC ramps, and signals degraded over a long cable arrive with slow or ragged edges; a Schmitt input restores them to sharp logic transitions.
- **Relaxation oscillators** — a single Schmitt inverter with one resistor and one capacitor oscillates: the cap charges toward V<sub>T+</sub>, the output flips and discharges it toward V<sub>T−</sub>, and the cycle repeats. It is the cheapest clock a designer can build.

Whenever a design must accept a real-world signal that a plain gate would chatter on, giving that gate's input hysteresis is the answer — which is why the Schmitt trigger lives in the gate family even though it computes nothing new.
