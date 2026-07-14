---
title: "Comparators"
weight: 10
---

# Comparators

A comparator is the doorway from the analog world into the digital one. It looks at two analog voltages and produces a single logic bit: high if the positive input is above the negative input, low otherwise. Every threshold decision a digital system makes about a continuous signal — is the battery low, has the sensor crossed a level, did the waveform cross zero — starts at a comparator.

> **Note:** this is the *analog* comparator, turning two voltages into one bit. It shares its name with the digital [magnitude comparator]({{< relref "/docs/building-blocks/arithmetic/magnitude-comparators" >}}), which compares two binary *numbers* and reports greater/equal/less. Same word, different device.

## How It Behaves

A comparator is effectively a very-high-gain differential amplifier run without feedback: the tiniest difference between its inputs is amplified until the output slams fully to one rail or the other. That makes it a one-bit analog-to-digital converter — the front end of a flash ADC is literally a bank of comparators — and the natural part for threshold and zero-crossing detection.

Two practical points dominate its use:

- **Chatter without hysteresis.** When the input hovers right at the threshold, noise pushes it back and forth and the output oscillates. Adding a little positive feedback gives the comparator two thresholds instead of one — hysteresis — which is the analog form of the [Schmitt trigger]({{< relref "/docs/building-blocks/gates/schmitt-trigger" >}}), and it cleans up the decision the same way.
- **The output stage.** Many comparators have open-collector/open-drain outputs that need a pull-up, which conveniently lets the output be set to whatever logic supply the digital side uses.

The most common place a comparator is met in digital systems is the **supply supervisor** that watches a rail against a reference and asserts [reset]({{< relref "/docs/glue-logic-toolbox/reset-delay" >}}) when it sags — a comparator with a precise threshold, doing exactly this job. The analog design details behind offset, speed, and bias belong to the *EE Notebook*; here the comparator is simply the primitive that lets logic act on a voltage.
