---
title: "Moore vs. Mealy"
weight: 20
---

# Moore vs. Mealy

The two classic styles of [state machine]({{< relref "fsm-concepts" >}}) differ in one respect: what the outputs depend on. It is the first design decision after deciding a machine is needed, and it trades response speed against clean, predictable timing.

## The Distinction

- A **Moore** machine's outputs depend **only on the current state**. The output logic looks at the state register and nothing else, so outputs change only *after* a clock edge moves the machine to a new state.
- A **Mealy** machine's outputs depend on the **current state and the current inputs together**. An input change can ripple straight to an output within the same state, without waiting for a clock edge.

## The Trade-off

Because a Moore output is a function of the registered state alone, it is **clean and glitch-free** — it changes synchronously, once per transition, and never twitches in response to a noisy input. The cost is a step of latency (the machine must clock into a new state before the output reflects an input) and sometimes more states, since distinctions that a Mealy machine draws with inputs must become separate states.

A Mealy machine is **faster and often smaller**: it can react within the current cycle and frequently needs fewer states to express the same behavior. The cost is that its outputs are combinationally tied to the inputs, so they can change at any time and can **glitch** as inputs settle — outputs that are no longer safely synchronous to the clock.

## In Practice

Real designs mix the two, and the common remedy for Mealy's timing hazard is to **register the outputs** — pass them through a [flip-flop]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}}) — which restores clean, synchronous edges at the price of the same one-cycle latency a Moore machine has. The rule of thumb: prefer Moore (or registered) outputs when other logic samples them and timing must be clean; reach for Mealy when a fast, same-cycle response matters and the output's consumer can tolerate its timing. The choice also shows up in how the machine is drawn — Moore outputs are written inside the [state bubbles, Mealy outputs on the transitions]({{< relref "state-diagrams" >}}).
