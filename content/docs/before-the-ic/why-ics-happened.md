---
title: "Why Integrated Circuits Happened"
weight: 40
---

# Why Integrated Circuits Happened

The [transistor]({{< relref "transistors" >}}) made a single switch cheap, small, and reliable. That solved the *device* problem — but it exposed a new one. As designs grew from dozens of transistors to thousands, the limiting factor stopped being the transistors and became the wiring between them. The integrated circuit exists to solve that second problem, and understanding which problem it solved is the key to why every later chapter looks the way it does.

## The Tyranny of Numbers

A discrete circuit is an assembly. Every transistor, resistor, and capacitor is manufactured separately, placed, and soldered by hand or machine, and every one of those connections is a unit of cost, a unit of size, and — worst of all — a point of failure. A circuit with a thousand devices has several thousand joints; a machine with a hundred thousand devices has an interconnect problem that no amount of care fully tames. Reliability falls as joint count rises, assembly time and cost climb, and the whole thing grows heavier and hotter.

Engineers of the late 1950s named this the **tyranny of numbers**: past a certain complexity, a system's feasibility was governed not by whether the components existed but by whether they could all be *connected* reliably and affordably. The transistor had removed the ceiling on how many switches were available; it had done nothing about the ceiling on how many could be wired together. That was the wall the ambitions of the era kept hitting.

## One Piece of Silicon Instead of a Thousand Parts

The escape was to stop treating a circuit as an assembly of parts at all. If transistors and resistors are already made by patterning a semiconductor surface, then the *connections between them* can be made the same way, in the same process, on the same piece of material — the entire circuit fabricated monolithically, with no discrete pieces to place and no joints to solder.

Jack Kilby at Texas Instruments demonstrated the idea in 1958 with a working circuit built on a single sliver of germanium. Robert Noyce at Fairchild made it manufacturable a year later, using the **planar process** (Jean Hoerni's method of building devices under a protective oxide layer) to lay the interconnecting metal down as a printed pattern on top of the silicon. Noyce's monolithic silicon IC is essentially the form still used today: devices and wiring, defined together by light and chemistry rather than by assembly. The interconnect that had been the enemy became just another patterned layer — made once, inside the chip, not soldered a thousand times outside it.

## Why Integration Paid for Itself

Solving the tyranny of numbers made large systems *possible*; photolithography made integration *inevitable*. Because a whole wafer is patterned in one set of steps, the cost of fabricating a chip barely depends on how many transistors it contains — a chip with ten thousand devices costs about what a chip with a hundred costs to make. So the cost *per function* falls as density rises, and each generation of denser chips is not only more capable but cheaper per gate than the last. Gordon Moore turned that observation into a forecast in 1965: transistor counts per chip would keep doubling on a regular cadence, because the economics rewarded exactly that. Integration was self-funding — denser chips paid for the tooling that made the next, denser generation.

It needed a first customer willing to pay the early premium, and that was aerospace and defense. Minuteman missile guidance and the Apollo Guidance Computer bought integrated circuits when they were still expensive, because size, weight, and reliability mattered more than price — the Apollo computer was built almost entirely from a single type of three-input NOR gate. Those programs bootstrapped the volume that drove prices down for everyone else, and the industry never looked back.

## What Integration Opened

It is worth being precise about *why* this could happen with the transistor and not before. A [relay]({{< relref "relays" >}}) is an assembly of moving parts and a [vacuum tube]({{< relref "vacuum-tubes" >}}) is a hand-built vacuum vessel; neither can be printed. Only the transistor is a pattern in silicon, so only the transistor could carry its interconnect and its neighbors into the same monolithic process. The integrated circuit is the direct payoff of that one property.

With whole circuits now fabricable at once, the design question inverted. It was no longer "how do we wire these devices together" but "how much should we put on a single chip" — and the answer grew relentlessly, from a few gates to a few thousand to a few billion. That progression is the subject of the next page, [SSI, MSI, LSI & VLSI]({{< relref "integration-scales" >}}), and the first things anyone put on those chips — the [logic families]({{< relref "/docs/implementation" >}}) — are where the rest of the notebook begins.
