---
title: "One of Eight Sensors"
weight: 60
---

# One of Eight Sensors

A design has one ADC input but eight analog sensors to read (or one signal path that must select among eight sources). Rather than eight converters, route each sensor to the single ADC in turn.

## The Part

The standard part is the **4051**, an 8-channel analog [multiplexer]({{< relref "/docs/building-blocks/selection/multiplexer" >}})/demultiplexer. Three address lines select which of the eight channels connects to the common pin, and because it is built from [transmission gates]({{< relref "/docs/building-blocks/analog-helpers/analog-switches" >}}) it passes analog voltages in either direction — so the same part can gather eight inputs to one ADC or fan one source out to eight destinations. Its relatives cover other groupings: the **4052** is a dual 4-channel mux, the **4053** a triple 2-channel. The 74HC4051 is the faster high-speed-CMOS version.

## Using It Well

- **Let the signal settle after switching** — the channel's on-resistance and the ADC's sampling capacitor form an RC; give it time to settle before converting, or successive readings bleed into each other.
- **Keep signals within the rails**, as with any analog switch — the mux cannot pass a voltage outside its supply.
- **Mind the on-resistance** into a low-impedance load, since it adds to the source impedance the ADC sees.

This is the analog counterpart to the digital [selection]({{< relref "/docs/building-blocks/selection" >}}) primitives: where a 74151 multiplexes *logic* signals, the 4051 multiplexes *analog* ones. For reading many *digital* inputs instead, the [74HC165]({{< relref "more-inputs" >}}) is the better fit.
