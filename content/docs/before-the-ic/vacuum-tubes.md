---
title: "Vacuum Tubes"
weight: 20
---

# Vacuum Tubes

The vacuum tube was the first device to switch *electronically* — with no moving parts. Where a [relay]({{< relref "relays" >}}) throws a metal armature to make or break a circuit, a tube controls a stream of electrons flying through a vacuum. Nothing mechanical moves, so switching happens at the speed of electron flow rather than the speed of a spring. That single change took switching from milliseconds to microseconds, and it is what made genuinely fast computation possible.

## How a Vacuum Tube Works

A tube works by thermionic emission. A heated cathode boils electrons off its surface; a positively charged plate (anode) across an evacuated envelope attracts them, and current flows. With just those two electrodes the device is a diode — it conducts in one direction only, which is why the earliest tubes were rectifiers.

The breakthrough was adding a third electrode. In a **triode**, a wire mesh **control grid** sits between cathode and plate. A small voltage on the grid throttles the electron stream — a slightly negative grid repels electrons and reduces plate current; a more negative grid cuts it off entirely. Because a tiny grid voltage controls a large plate current, the triode amplifies. Later tubes (tetrodes, pentodes) added further grids to improve gain and reduce unwanted capacitance, but the principle is unchanged: **a small input voltage controls a much larger output current.**

## Vacuum Tubes as Logic

For logic, the tube is not used as a linear amplifier but slammed between two extremes: the grid is driven below cutoff (plate current off) or hard into conduction (plate current on). Those two states are the 1 and 0, switched electronically in microseconds.

Combinational gates were built by pairing diodes with tubes: diode networks form AND and OR (current steered through whichever path is enabled), and a triode or pentode stage inverts and restores the signal level so gates can be cascaded without the levels decaying — the same division of labor that later became [DTL]({{< relref "/docs/implementation/dtl" >}}).

The more consequential invention was memory. In 1918 the **Eccles–Jordan** circuit cross-coupled two triodes so that each held the other in place: the pair rests in one of two stable states and stays there until a pulse flips it. That bistable circuit is the **flip-flop** — electronic memory, invented in tubes, decades before the transistor. Sequential logic became electronic here. The first electronic computers counted and stored numbers in banks of these tube flip-flops; ENIAC's decade counters, for instance, were [ring counters]({{< relref "/docs/building-blocks/counting/ring-and-johnson-counters" >}}) of ten flip-flops each.

## Why Vacuum Tubes Emerged, and What They Replaced

Tubes displaced relays for computing for one reason: speed. A relay switches in milliseconds and wears out mechanically; a tube switches in microseconds with nothing moving to wear. That thousand-fold speedup turned "automatic calculation" into something fast enough to be genuinely useful.

The first generation of electronic computers was built on tubes — Colossus (1943–44) for codebreaking, ENIAC (1945, roughly 18,000 tubes), and their successors. For about a decade, a tube was simply what an electronic switch *was*.

What tubes gave up drove the search for something better. Every tube has a heater that burns power continuously, so thousands of them dissipate kilowatts and demand serious cooling. They are bulky and fragile — glass envelopes with filaments that fail like light bulbs — and they run on plate supplies of hundreds of volts. At the scale of a large machine, a tube is always failing somewhere, so reliability becomes a maintenance problem. The [transistor]({{< relref "transistors" >}}), demonstrated in 1947, did the same switching job solid-state: cool, tiny, rugged, and low-voltage. It made the tube obsolete for logic almost as soon as it could be manufactured in quantity.

## Tips

- **Read the tube as a voltage-controlled valve** — the grid throttles a plate current it does not itself supply. That "small input controls large output" relationship is transconductance, and it is the same idea that carries directly into the transistor, so the mental model transfers rather than being discarded.
- **Cutoff and saturation are the digital states** — logic uses the tube only at its extremes, fully off (grid below cutoff) or fully on. The linear region in between is for analog amplifiers; a gate deliberately avoids resting there.
- **The heater is a separate supply from the signal path** — like a relay's coil versus its contacts, filament/heater power is independent of the plate circuit doing the switching. Reasoning about a tube stage means keeping the two supplies distinct.
- **The Eccles–Jordan pair is the flip-flop** — spotting two cross-coupled active devices, each feeding back to hold the other, is spotting one bit of storage. The topology is identical whether the devices are triodes, bipolar transistors, or CMOS.

## Caveats

- **Tubes run hot and hungry** — heater power is dissipated continuously whether or not the tube is switching, so power and cooling scale with tube count, not with activity. This alone capped how large tube machines could practically grow.
- **Filaments burn out** — a tube is a consumable. In a system of thousands, mean time between failures is dominated by filament failure, and a dead tube anywhere can halt the whole machine until it is found and replaced.
- **Logic levels are hundreds of volts** — plate swings are large, so the "1" and "0" are high-voltage levels with all the insulation and safety concerns that implies — a world away from the sub-5-volt logic that followed.
- **Warm-up and microphonics** — a tube needs time to heat before it works, and mechanical vibration physically modulates its electrodes (microphonics). These are analog imperfections that a switch is not supposed to have.

## In Practice

- **The flip-flop was born here and never changed shape** — the cross-coupled Eccles–Jordan bistable is functionally the same latch drawn today in CMOS. The storage primitive behind every register and [flip-flop]({{< relref "/docs/building-blocks/storage" >}}) predates the transistor entirely; only the switching device underneath it changed.
- **The triode is the transistor's functional ancestor** — grid maps to base/gate, plate to collector/drain, cathode to emitter/source. The three-terminal "small input controls large output" device is the same concept in both eras, which is why tube-era circuit topologies — and the word *gate* itself — carried straight across into semiconductors.
- **Tubes survive where power and frequency are extreme** — high-power RF and microwave transmitters, and the magnetron in every microwave oven, are still vacuum tubes, because solid-state does not yet fully match certain very-high-power, high-frequency, high-voltage regimes. This is physics, not nostalgia — but it is switching and generating power, not doing logic.
- **Audio kept the tube for its analog behavior, not its digital role** — guitar and hi-fi amplifiers still use tubes for their soft-clipping overload character. That is the tube as a linear amplifier; its role as a logic and memory element ended completely with the transistor.
