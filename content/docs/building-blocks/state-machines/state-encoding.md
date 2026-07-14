---
title: "State Encoding"
weight: 40
---

# State Encoding

Once a [state machine]({{< relref "fsm-concepts" >}})'s behavior is captured, each state has to be assigned a bit pattern in the [state register]({{< relref "/docs/building-blocks/storage/registers" >}}). The behavior is identical whatever the assignment, but the *encoding* strongly affects how much logic the machine costs, how fast it runs, and how safely it fails — so it is a real design choice, not a formality.

## Three Common Schemes

- **Binary (sequential)** — number the states 0, 1, 2, … and store the number in ⌈log₂ N⌉ flip-flops. This uses the **fewest flip-flops**, which mattered when flip-flops were expensive discrete parts. The cost is more complex next-state and output logic, and several bits can change on one transition — a source of decoding glitches.
- **Gray code** — order the state codes so that **adjacent states differ by a single bit**. Only one flip-flop changes per step, which reduces simultaneous switching and makes decoded outputs cleaner. It is most useful for machines that march through states in order, and for values that cross clock domains.
- **One-hot** — give **each state its own flip-flop**, with exactly one set at a time. It spends the most flip-flops (N of them for N states) but makes the next-state and output logic trivial and fast: "am I in state X" is just one flip-flop's output, with no decoding. A one-hot machine is essentially a [ring counter]({{< relref "/docs/building-blocks/counting/ring-and-johnson-counters" >}}) following the state diagram.

## Choosing One

The trade is flip-flops against logic. In the discrete and early-integrated eras, flip-flops were the scarce resource, so **binary** encoding dominated. In an [FPGA]({{< relref "/docs/modern-world/fpgas" >}}), flip-flops come essentially free with every logic block while wide combinational logic is what's precious — so **one-hot** is frequently the default, trading spare flip-flops for smaller, faster logic and glitch-free decoding.

Encoding also has a safety dimension. Both binary and one-hot leave **unused codes** (states the machine should never occupy), and a glitch or an upset can land it there. A *safe* or *self-correcting* FSM explicitly defines transitions from every illegal code back to a known state (usually reset), so a machine that is knocked out of its intended set of states recovers rather than hanging — a real concern for anything that must run unattended.
