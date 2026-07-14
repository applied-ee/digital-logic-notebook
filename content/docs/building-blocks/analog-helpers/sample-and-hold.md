---
title: "Sample & Hold"
weight: 30
---

# Sample & Hold

A sample-and-hold captures an analog voltage at a chosen instant and holds it steady long enough to be measured. It exists because measurement takes time: an analog-to-digital converter needs its input to stay constant while it works out the digital value, and a signal that moves during the conversion produces a wrong reading. Sample-and-hold freezes the signal at a defined moment so the converter has something still to look at.

## Switch, Capacitor, Buffer

The circuit is three parts working together. An [analog switch]({{< relref "analog-switches" >}}) connects the input to a **hold capacitor**; a high-impedance buffer (an [op-amp]({{< relref "op-amps" >}}) follower) reads the capacitor's voltage without draining it.

- **Sample (track):** close the switch and the capacitor charges to follow the input.
- **Hold:** open the switch at the sampling instant, and the capacitor keeps that voltage while the buffer presents it to the ADC.

The moment the switch opens *is* the sampling instant, which is why the sample-and-hold defines *when* a signal is measured, not just what value comes out.

## The Imperfections That Matter

Every part of that simple circuit contributes an error worth knowing:

- **Acquisition time** — the capacitor needs time to charge to the input during the sample phase; sample too briefly and it never reaches the true value.
- **Droop** — during hold, leakage and the buffer's bias current slowly discharge the capacitor, so the held value drifts if held too long.
- **Charge injection** — the switch dumps a little charge onto the capacitor as it opens, adding a small offset to the captured value.
- **Aperture uncertainty** — the switch does not open at a perfectly precise instant, and that jitter in the sampling moment limits accuracy on fast-changing signals.

In practice a discrete sample-and-hold is rare today because most converters build it in: a SAR ADC's front end is a **track-and-hold** stage doing exactly this. It is the quiet bridge between the continuous [comparator]({{< relref "comparators" >}})-and-conversion world and the discrete numbers the digital side works with — and the reason an ADC needs its input to [settle before a reading]({{< relref "/docs/glue-logic-toolbox/one-of-eight-sensors" >}}).
