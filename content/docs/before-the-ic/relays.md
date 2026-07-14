---
title: "Relays"
weight: 10
---

# Relays

A relay is an electrically controlled switch: a coil, when energized, generates a magnetic field that pulls a movable armature, and that armature opens or closes a set of contacts. The essential feature is not the switching itself but the *separation* — the coil that does the controlling is electrically independent of the contacts being controlled. One circuit commands another.

That single property is the seed of all logic. A plain switch is thrown by a hand or a cam; a relay is thrown by *another circuit's output*. Once a switch can be operated by the same kind of signal it produces, switches can be cascaded — the output of one drives the input of the next — and cascaded switches are exactly what a logic gate is.

## How a Relay Works

A basic relay has four parts: a coil, an iron armature held by a spring, and one or more contact sets.

- **Energized** — coil current magnetizes the core, the armature is pulled in, **normally-open (NO)** contacts close and **normally-closed (NC)** contacts open.
- **De-energized** — the spring returns the armature, NO contacts open and NC contacts close again.

Contacts are described by poles (how many independent circuits are switched) and throws (how many positions each pole selects) — SPST, SPDT, DPDT, and so on. A single SPDT relay already provides both a make (NO) and a break (NC) contact from one coil.

## Relays as Logic

Contacts wired together form Boolean functions directly, with no notion of "gate" required:

| Contact arrangement | Conducts when | Logic function |
|---|---|---|
| Two NO contacts in **series** | both coils energized | **AND** |
| Two NO contacts in **parallel** | either coil energized | **OR** |
| A single **NC** contact | its coil is *de-energized* | **NOT** |

Series is [AND]({{< relref "/docs/building-blocks/gates" >}}), parallel is OR, and a normally-closed contact is the inverter. Drive one relay's coil from another relay's contacts and the functions compose — this is combinational logic built entirely from moving metal.

Feedback turns it into memory. Wire one of a relay's own NO contacts in parallel with its "start" input so that, once energized, the relay keeps itself energized until a series NC "stop" contact breaks the loop. This **seal-in** or self-holding circuit is a set/reset latch made of contacts — the mechanical ancestor of the [SR latch]({{< relref "/docs/building-blocks/storage/sr-latch" >}}). With combinational functions from contact networks and memory from seal-in loops, relays already provide both halves of digital logic.

The notation used to design these circuits — power rails on the left and right, horizontal "rungs" of series and parallel contacts driving coils — is **ladder logic**, and it outlived the relays themselves.

## Why Relays Emerged, and What They Replaced

Before the relay, control meant mechanical actuation: hand-thrown switches, cams on a rotating shaft, governors, and linkages. These could only be driven by physical motion at the point of contact. The relay decoupled the decision from the muscle — a small signal on a coil could switch a large or distant circuit, automatically and repeatably.

That capability built the first generation of automatic systems. Telephone exchanges (step-by-step and crossbar) routed calls with banks of relays. Industrial machinery gained sequenced, interlocked control. And the earliest program-controlled computers were relay machines: Zuse's Z3 (1941, ~2,000 relays, the first programmable digital computer), the Harvard Mark I, and the Bell Labs relay computers all computed by clicking contacts open and closed.

Relays were displaced for computing by the [vacuum tube]({{< relref "vacuum-tubes" >}}) — and later the transistor — for one reason above all: **speed**. A relay switches in milliseconds and wears out mechanically; a tube switches electronically in microseconds with no moving parts. What the relay proved was the *idea* — that logic and memory could be built from a controllable switch. What it could not do was run fast, small, or cool enough to scale.

## Tips

- **Read the coil side and the contact side as two independent specifications** — the coil has a voltage/current to energize it; the contacts have separate voltage and current ratings for the load. The two are electrically isolated, which is often the whole point of using a relay rather than a transistor.
- **A normally-closed contact is the inverter** — any time a function needs "active when the controlling signal is *off*," that is an NC contact, not extra logic. Much relay-logic elegance comes from choosing NO vs NC contacts deliberately.
- **A seal-in contact is one bit of stored state** — recognizing the self-holding loop as a latch makes relay ladders readable: find the coil, find its own contact feeding back, and that rung is memory rather than combinational logic.
- **Put a freewheeling diode across a DC coil** — the coil is an inductor, and interrupting its current produces a large reverse voltage spike that can destroy whatever drives it. A reverse-biased diode across the coil clamps that kickback.

## Caveats

- **Contacts bounce** — the armature and contacts are mechanical, so on every closure they make and break several times over a few milliseconds before settling. A relay output is not a clean single edge.
- **Switching is measured in milliseconds** — coil pull-in and drop-out take time, and drop-out is often slower than pull-in because the collapsing field lingers. This bounds relay logic to low speeds and rules it out of any fast datapath.
- **Contacts wear, arc, and weld** — mechanical life is finite, and switching inductive or high-current loads draws an arc that erodes the contacts or, in the worst case, welds them shut. Reliability is a materials and derating problem, not just a logic one.
- **Coil power is not free** — holding a relay energized dissipates continuous current in the coil. A wall of relays implementing logic consumes real power just to *hold* its state, independent of any switching.

## In Practice

- **Relay logic became ladder logic, and ladder logic never left** — programmable logic controllers (PLCs) are still programmed in ladder diagrams whose rungs, contacts, and coils are drawn exactly as if the relays were physical. The abstraction migrated into software while keeping its original shape.
- **Safety interlock logic is still hardwired in relays** — emergency-stop, guard-door, and light-curtain logic is routinely built from force-guided (guided-contact) safety relays, because hardwired relay logic is deterministic, fails in a predictable direction, and is straightforward to certify to functional-safety standards (ISO 13849, IEC 62061) where arguing the same case for firmware is far harder. The AND of "all guards closed and E-stop clear" is a genuine logic function, designed in relays today.
- **Railway signaling still runs on relay interlocking** — route and interlocking logic assembled from signaling relays remains in active service on many networks, kept precisely because it is non-programmable and can be independently verified rung by rung. It is being modernized to computer-based interlocking, but the relay logic persists for exactly the reason it was chosen: auditability over speed.
- **A latching relay is a bit of nonvolatile state** — a bistable/impulse relay toggles on each pulse and holds its position with no coil power, which makes the impulse relay behind stairwell and corridor lighting a [T flip-flop]({{< relref "/docs/building-blocks/storage/t-flip-flop" >}}) in the wall, and the service-disconnect relay in a utility meter a stored bit that must survive an outage. The seal-in latch that began as the flip-flop's ancestor still ships as memory — and the seal-in mental model (which contact sits in series with the loop) is still the clearest way to reason about set- versus reset-dominant behavior.
- **Contact bounce is why debounce exists** — the same millisecond-scale bounce appears on every mechanical button and switch in use today, which is exactly the problem the [Schmitt-trigger debounce]({{< relref "/docs/glue-logic-toolbox/debounce" >}}) part in the glue-logic toolbox is reached for. The relay's oldest flaw is a routine consideration on modern boards.
- **The load-switching hat moved to the solid-state relay; the logic hat did not** — where the job is purely fast, silent, high-cycle switching of an isolated load, the SSR (a triac/MOSFET device, part of the transistor lineage) has largely replaced the electromechanical relay. But nobody builds logic from SSRs, and the safety-interlock niche above specifically avoids them because an SSR tends to fail *closed* and leaks when off. Isolated power switching became solid-state; isolated decision-making and stored state stayed electromechanical.
