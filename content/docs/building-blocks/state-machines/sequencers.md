---
title: "Sequencers"
weight: 50
---

# Sequencers

A sequencer is a [state machine]({{< relref "fsm-concepts" >}}) in its most restricted, most common form: one that steps through a **fixed sequence of states**, mostly marching forward rather than branching on inputs. Where a general FSM asks "given where I am and what just happened, where do I go?", a sequencer mostly just asks "what is the next step?" That narrower job has simple, efficient realizations.

## How They're Built

- **Counter plus decoder** — a [synchronous counter]({{< relref "/docs/building-blocks/counting/synchronous-counters" >}}) advances through binary states and a [decoder]({{< relref "/docs/building-blocks/selection/decoder" >}}) turns the current count into one active "step" line. Compact, and the count is also directly available.
- **Ring or Johnson counter** — a [ring counter]({{< relref "/docs/building-blocks/counting/ring-and-johnson-counters" >}}) is the simplest sequencer of all: the single circulating one-hot bit *is* the current step, already decoded and glitch-free, with no separate decoder needed.
- **A small FSM** — when a few input-dependent decisions are needed (wait here until ready, skip a step under some condition), a general state machine handles the branches the pure counter forms cannot.

## Where They're Used

Sequencers run the parts of a system that must happen in a fixed order: multi-phase clock generation, memory and bus access cycles, stepper-motor phase drive, display and keypad scanning, and pattern or waveform generation. Their most consequential use is the **control unit of a processor** — a microsequencer that steps an address counter through a ROM whose contents are the control signals for each step (microcode) and the address of the next step. That is how a great many CPUs turn an instruction into an ordered series of register-transfer operations: a sequencer, a memory, and the [datapath registers]({{< relref "/docs/building-blocks/storage/registers" >}}) it steers. The counting family's pattern circulators and the state-machine family's controllers meet exactly here.
