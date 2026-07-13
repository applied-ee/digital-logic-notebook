---
title: "State Machines"
weight: 60
bookCollapseSection: true
---

# State Machines

**Hardware follows a plan.**

Combine storage with combinational logic that decides the *next* state from the current state and the inputs, and the result is a finite state machine — the general form of every sequential circuit. A counter is a trivial state machine; a bus controller or a traffic-light sequencer is a deliberate one. The whole discipline is choosing the states, the transitions, and the encoding so the machine does what is intended and nothing dangerous when it doesn't.

## Sections

- **[What Is a State Machine?]({{< relref "fsm-concepts" >}})** — State, transition, and the next-state/output structure common to all of them.
- **[Moore vs. Mealy]({{< relref "moore-vs-mealy" >}})** — Whether outputs depend on state alone or on state and input together.
- **[State Diagrams]({{< relref "state-diagrams" >}})** — Capturing behavior as states and labeled transitions before touching gates.
- **[State Encoding]({{< relref "state-encoding" >}})** — Binary, Gray, and one-hot — and why the choice affects speed and safety.
- **[Sequencers]({{< relref "sequencers" >}})** — Counter- and shift-register-based machines that step through a fixed order.
