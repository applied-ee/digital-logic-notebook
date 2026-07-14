---
title: "Ring & Johnson Counters"
weight: 40
---

# Ring & Johnson Counters

Ring and Johnson counters count differently from a binary counter: instead of incrementing a number, they **circulate a pattern** around a [shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}). They trade code efficiency for something valuable — outputs that are already decoded and free of glitches.

## Ring Counter

A ring counter is a shift register with its last output fed straight back to its first input. Seed it with a single `1` and that one bit walks around the loop: `1000 → 0100 → 0010 → 0001 → 1000`. With N flip-flops it has N states, and exactly **one output is active at a time** — a **one-hot** sequence. Because each output *is* a decoded state, no decoding logic is needed and there are none of the [ripple-counter]({{< relref "ripple-counters" >}}) decoding glitches: the outputs are already clean, one-per-step control signals. That makes ring counters ideal for sequencers, stepper-motor phase drives, and LED chasers.

## Johnson Counter

A Johnson counter (also called a twisted-ring or switch-tail counter) feeds back the *inverted* last output instead. That doubles the sequence: N flip-flops now cycle through **2N** states — `000 → 100 → 110 → 111 → 011 → 001 → 000`. Its useful property is that **only one bit changes per step** (a Gray-code-like sequence), so decoding any state takes just a two-input gate and, because no two bits race, the decoded outputs are glitch-free.

## The Trade

The cost is efficiency. A binary counter gets 2ᴺ states from N flip-flops; a ring counter gets only N and a Johnson counter only 2N. Spending flip-flops so lavishly to represent a count would be wasteful — but that is the wrong way to see them. What they buy is **decoded, glitch-free outputs with almost no logic and very high speed**, which is exactly what a sequencer or phase generator wants. They are the counting family's link to one-hot [state encoding]({{< relref "/docs/building-blocks/state-machines/state-encoding" >}}) and simple [sequencers]({{< relref "/docs/building-blocks/state-machines/sequencers" >}}), where "which step are we on" matters more than "what number is this."
