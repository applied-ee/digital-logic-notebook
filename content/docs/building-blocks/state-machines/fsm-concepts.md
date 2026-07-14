---
title: "What Is a State Machine?"
weight: 10
---

# What Is a State Machine?

A finite state machine is the most general form a sequential circuit can take. It is defined by three things: a finite set of **states**, a rule for choosing the **next state** from the current state and the inputs, and a rule for producing **outputs**. Anything that has to remember where it is and act on what happens next — a controller, a protocol handler, a vending machine — is a state machine.

## Three Pieces

Every FSM decomposes into the same three blocks: a **state register** of [flip-flops]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}}) holding the current state, **next-state logic** (combinational [gates]({{< relref "/docs/building-blocks/gates" >}})) that computes the state to move to, and **output logic** that produces the outputs. On each clock edge the register adopts the next state, and the whole thing steps forward.

{{< graphviz >}}
digraph fsm {
  rankdir=LR;
  bgcolor="transparent";
  node [shape=box, style="rounded,filled", fillcolor="#ffffff", color="#2563eb", fontcolor="#1e293b", fontname="Helvetica,Arial,sans-serif", fontsize=11, margin="0.18,0.1"];
  edge [color="#2563eb", fontcolor="#64748b", fontname="Helvetica,Arial,sans-serif", fontsize=9, arrowsize=0.7];

  in [label="Inputs", shape=plaintext, style="", fontcolor="#64748b"];
  nsl [label="Next-State\nLogic"];
  reg [label="State\nRegister"];
  outl [label="Output\nLogic"];
  out [label="Outputs", shape=plaintext, style="", fontcolor="#64748b"];

  in -> nsl;
  nsl -> reg [label="next state"];
  reg -> nsl [label="current state", constraint=false];
  reg -> outl;
  outl -> out;
}
{{< /graphviz >}}

The feedback from the state register back into the next-state logic is the whole point: the machine's behavior depends on where it already is, not just on the present input. That loop is the same cross-coupled [memory]({{< relref "/docs/building-blocks/storage/sr-latch" >}}) that underlies all sequential logic, organized here into named states.

## The Simplest One Is a Counter

A [synchronous counter]({{< relref "/docs/building-blocks/counting/synchronous-counters" >}}) is a state machine with the plainest possible rule: its next state is always the current state plus one, and it ignores its inputs. Add input-dependent branching — "advance only if the coin input is high," "jump to the error state on a fault" — and the same structure becomes a general controller. Everything from a counter to a CPU's control unit is this block diagram with a different next-state rule.

How the outputs are generated ([Moore vs. Mealy]({{< relref "moore-vs-mealy" >}})), how the behavior is captured ([state diagrams]({{< relref "state-diagrams" >}})), and how the states are assigned to bit patterns ([state encoding]({{< relref "state-encoding" >}})) are the three decisions that turn this general idea into a specific machine.
