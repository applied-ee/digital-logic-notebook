---
title: "Relays"
weight: 10
---

# Relays

A relay is an electrically controlled switch: a coil, when energized, generates a magnetic field that pulls a movable armature, and that armature opens or closes a set of contacts. The essential feature is not the switching itself but the *separation* — the coil that does the controlling is electrically independent of the contacts being controlled. One circuit commands another.

That single property is the seed of all logic. A plain switch is thrown by a hand or a cam; a relay is thrown by *another circuit's output*. Once a switch can be operated by the same kind of signal it produces, switches can be cascaded — the output of one drives the input of the next — and cascaded switches are exactly what a logic gate is.

## How a Relay Works

A basic relay has a coil, an iron armature held by a spring, and one or more contact sets. Energize the coil and its magnetic field pulls the armature in, closing **normally-open (NO)** contacts and opening **normally-closed (NC)** contacts; remove the current and the spring returns everything to rest. Contacts are described by poles (how many independent circuits are switched) and throws (how many positions each pole selects) — SPST, SPDT, DPDT — and a single SPDT relay already provides both a make (NO) and a break (NC) contact from one coil.

Two practical facts follow from the construction and matter on every schematic. The coil and the contacts are rated separately and are electrically isolated: the coil has a voltage and current to energize it, while the contacts carry an entirely different load, and that isolation is frequently the whole reason a relay is chosen over a transistor. And because the coil is an inductor, interrupting its current produces a large reverse-voltage spike — a DC coil needs a freewheeling diode across it to clamp that kickback before it destroys whatever drives the coil.

## Relays as Logic

Contacts wired together form Boolean functions directly, with no notion of "gate" required:

| Contact arrangement | Conducts when | Logic function |
|---|---|---|
| Two NO contacts in **series** | both coils energized | **AND** |
| Two NO contacts in **parallel** | either coil energized | **OR** |
| A single **NC** contact | its coil is *de-energized* | **NOT** |

Series is [AND]({{< relref "/docs/building-blocks/gates" >}}), parallel is OR, and a normally-closed contact is the inverter — so "active when the controlling signal is *off*" is a contact choice, not extra logic. Drive one relay's coil from another relay's contacts and the functions compose: this is combinational logic built entirely from moving metal.

Feedback turns it into memory. Wire one of a relay's own NO contacts in parallel with its "start" input so that, once energized, the relay keeps itself energized until a series NC "stop" contact breaks the loop. This **seal-in** or self-holding circuit is a set/reset latch made of contacts — the mechanical ancestor of the [SR latch]({{< relref "/docs/building-blocks/storage/sr-latch" >}}), and the clearest physical picture of what "set-dominant" versus "reset-dominant" means, since the priority is visible as which contact sits in series with the loop. With combinational functions from contact networks and memory from seal-in loops, relays already provide both halves of digital logic. The notation used to design these circuits — power rails on the left and right, horizontal "rungs" of series and parallel contacts driving coils — is **ladder logic**, and it outlived the relays themselves.

## Why Relays Emerged, and What They Replaced

Before the relay, control meant mechanical actuation: hand-thrown switches, cams on a rotating shaft, governors, and linkages, all driven by physical motion at the point of contact. The relay decoupled the decision from the muscle — a small signal on a coil could switch a large or distant circuit, automatically and repeatably. That capability built the first generation of automatic systems: telephone exchanges routed calls with banks of relays, industrial machinery gained sequenced and interlocked control, and the earliest program-controlled computers were relay machines — Zuse's Z3 (1941, ~2,000 relays, the first programmable digital computer), the Harvard Mark I, and the Bell Labs relay computers all computed by clicking contacts open and closed.

What ended the relay's computing career were the limits of moving metal. Contacts bounce — on every closure they make and break several times over a few milliseconds before settling, so a relay output is not a clean edge. Switching itself takes milliseconds, with drop-out often slower than pull-in as the field collapses, which rules relays out of any fast datapath. Contacts wear, arc, and can weld, especially on inductive or high-current loads, making reliability a materials problem. And holding a relay energized dissipates coil current continuously, so a wall of relays burns real power just to *hold* its state. The [vacuum tube]({{< relref "vacuum-tubes" >}}) — and later the transistor — displaced relays for one reason above all: speed. A tube switches electronically in microseconds with nothing to wear. What the relay proved was the *idea* — that logic and memory can be built from a controllable switch. What it could not do was run fast, small, or cool enough to scale.

## Where Relays Stand Today

Relays never left; they retreated to the niche where hardwired, isolated, fail-safe switching beats fast and small — and that niche is very much alive. The clearest sign is that relay logic itself persists: programmable logic controllers are still programmed in ladder diagrams whose rungs, contacts, and coils are drawn exactly as if the relays were physical, and **safety interlock logic is still built from real relays**. Emergency-stop, guard-door, and light-curtain logic uses force-guided (guided-contact) safety relays because hardwired relay logic is deterministic, fails in a predictable direction, and is straightforward to certify to functional-safety standards (ISO 13849, IEC 62061) where arguing the same case for firmware is far harder. The AND of "all guards closed and E-stop clear" is a genuine logic function, designed in relays today. For the same reason — non-programmable logic that can be verified rung by rung — a great deal of **railway signaling** still runs on relay interlocking, being modernized to computer-based interlocking only slowly.

Relays also still hold state. A bistable or **impulse relay** toggles on each pulse and keeps its position with no coil power, which makes the impulse relay behind stairwell and corridor lighting a [T flip-flop]({{< relref "/docs/building-blocks/storage/t-flip-flop" >}}) in the wall, and the service-disconnect relay in a utility meter a stored bit that must survive an outage. The seal-in latch that began as the flip-flop's ancestor still ships as memory.

Two footnotes complete the picture. The relay's oldest flaw is now a routine design consideration: the same millisecond-scale contact bounce appears on every mechanical button and switch in use today, which is exactly the problem the [Schmitt-trigger debounce]({{< relref "/docs/glue-logic-toolbox/debounce" >}}) part is reached for. And the relay's *load-switching* role — fast, silent, high-cycle switching of an isolated load — has largely moved to the solid-state relay, a triac or MOSFET device from the transistor lineage. But nobody builds logic from solid-state relays, and safety interlocks specifically avoid them because an SSR tends to fail *closed* and leaks when off. Isolated power switching went solid-state; isolated decision-making and stored state stayed electromechanical.
