---
title: "State Diagrams"
weight: 30
---

# State Diagrams

A state diagram is how a [state machine]({{< relref "fsm-concepts" >}}) is designed before any gates exist. States are drawn as bubbles and transitions as arrows labeled with the input condition that causes them. It is the specification the machine is reasoned about — the logic is *derived from* the diagram, not the other way around.

## A Worked Example

The canonical example is a turnstile. It has two states — **Locked** and **Unlocked** — and two inputs: inserting a **coin** and **pushing** the arm.

{{< graphviz >}}
digraph turnstile {
  rankdir=LR;
  bgcolor="transparent";
  node [shape=circle, style="filled", fillcolor="#ffffff", color="#2563eb", fontcolor="#1e293b", fontname="Helvetica,Arial,sans-serif", fontsize=11, width=0.9, fixedsize=true];
  edge [color="#2563eb", fontcolor="#64748b", fontname="Helvetica,Arial,sans-serif", fontsize=9, arrowsize=0.7];

  Locked -> Unlocked [label="coin"];
  Unlocked -> Locked [label="push"];
  Locked -> Locked [label="push"];
  Unlocked -> Unlocked [label="coin"];
}
{{< /graphviz >}}

The diagram says everything about the behavior at a glance: a coin unlocks a locked turnstile; a push through an unlocked one locks it again; pushing while locked or paying while already unlocked does nothing. Reading the arrows is reading the machine.

## From Diagram to Logic

The diagram drives a repeatable design flow:

1. **Enumerate the states** and identify the reset state the machine powers up in.
2. **Define every transition** — critically, for *every* input combination out of *every* state, so there are no unspecified cases where the machine's behavior is undefined.
3. **Place the outputs**: in a [Moore]({{< relref "moore-vs-mealy" >}}) machine they are written inside the state bubbles (the output is a property of the state); in a Mealy machine they are written on the transition arrows (the output depends on the input taken).
4. **Encode and build**: assign each state a bit pattern ([state encoding]({{< relref "state-encoding" >}})) and derive the next-state and output [logic]({{< relref "/docs/building-blocks/gates" >}}) — or, in modern practice, transcribe the diagram into an [HDL]({{< relref "/docs/modern-world/hdl-concepts" >}}) `case` statement and let synthesis build the gates.

Whether the target is a handful of TTL parts or a block inside an ASIC, the state diagram is the human-readable source of truth, and most FSM bugs are visible in it — an unhandled input, a missing transition, a state with no way out — long before they reach silicon.
