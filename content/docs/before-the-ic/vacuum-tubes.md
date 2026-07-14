---
title: "Vacuum Tubes"
weight: 20
---

# Vacuum Tubes

The vacuum tube was the first device to switch *electronically* — with no moving parts. Where a [relay]({{< relref "relays" >}}) throws a metal armature to make or break a circuit, a tube controls a stream of electrons flying through a vacuum. Nothing mechanical moves, so switching happens at the speed of electron flow rather than the speed of a spring. That single change took switching from milliseconds to microseconds, and it is what made genuinely fast computation possible.

## How a Vacuum Tube Works

A tube works by thermionic emission. A heated cathode boils electrons off its surface; a positively charged plate (anode) across an evacuated envelope attracts them, and current flows. With just those two electrodes the device is a diode — it conducts in one direction only, which is why the earliest tubes were rectifiers.

The breakthrough was adding a third electrode. In a **triode**, a wire mesh **control grid** sits between cathode and plate, and a small voltage on the grid throttles the electron stream — a slightly negative grid repels electrons and reduces plate current; a more negative grid cuts it off entirely. Because a tiny grid voltage controls a large plate current, the triode amplifies. Later tubes (tetrodes, pentodes) added further grids to improve gain and reduce unwanted capacitance, but the principle never changed: **a small input voltage controls a much larger output current.** That is transconductance, and it is the same idea that carries directly into the transistor, so the mental model transfers rather than being discarded.

## Vacuum Tubes as Logic

For logic, the tube is not used as a linear amplifier but slammed between two extremes: the grid is driven below cutoff (plate current off) or hard into conduction (plate current on). Those two states are the 1 and 0, switched electronically in microseconds; the linear region in between is for analog amplifiers, and a gate deliberately avoids resting there.

Combinational gates were built by pairing diodes with tubes: diode networks form AND and OR by steering current through whichever path is enabled, and a triode or pentode stage inverts and restores the signal level so gates can be cascaded without the levels decaying — the same division of labor that later became [DTL]({{< relref "/docs/implementation/dtl" >}}).

The more consequential invention was memory. In 1918 the **Eccles–Jordan** circuit cross-coupled two triodes so that each held the other in place: the pair rests in one of two stable states and stays there until a pulse flips it. That bistable circuit is the **flip-flop** — electronic memory, invented in tubes, decades before the transistor. Sequential logic became electronic here. The first electronic computers counted and stored numbers in banks of these tube flip-flops; ENIAC's decade counters, for instance, were [ring counters]({{< relref "/docs/building-blocks/counting/ring-and-johnson-counters" >}}) of ten flip-flops each. Spotting two cross-coupled active devices that feed back to hold each other is spotting one bit of storage — a topology identical whether the devices are triodes, bipolar transistors, or CMOS.

## Why Tubes Replaced Relays — and Why the Transistor Replaced Tubes

Tubes displaced relays for computing for one reason: speed. A relay switches in milliseconds and wears out mechanically; a tube switches in microseconds with nothing moving to wear, a thousand-fold speedup that turned automatic calculation into something fast enough to be genuinely useful. For about a decade a tube was simply what an electronic switch *was*, and the first generation of electronic computers was built on them — Colossus (1943–44) for codebreaking, ENIAC (1945, roughly 18,000 tubes), and their successors.

What tubes gave up drove the search for something better. Every tube has a heater that burns power continuously whether or not it is switching, so thousands of them dissipate kilowatts and demand serious cooling — a limit that alone capped how large tube machines could grow. They are bulky and fragile, glass envelopes with filaments that fail like light bulbs, so in a system of thousands the mean time between failures is dominated by burned-out filaments and a single dead tube can halt the whole machine. Their logic levels are plate swings of hundreds of volts, a world away from the sub-5-volt logic that followed, and they need warm-up time and are microphonic — mechanical vibration modulates the electrodes. The [transistor]({{< relref "transistors" >}}), demonstrated in 1947, did the same switching job solid-state: cool, tiny, rugged, and low-voltage. It made the tube obsolete for logic almost as soon as it could be manufactured in quantity — and the mapping was direct, since the triode's grid, plate, and cathode become the transistor's gate/base, drain/collector, and source/emitter. The three-terminal "small input controls large output" device is the same concept in both eras, which is why tube-era circuit topologies, and the word *gate* itself, carried straight across into semiconductors.

## Where Vacuum Tubes Stand Today

The tube's *logic* role ended completely with the transistor, but two threads survive. As a device, the vacuum tube still wins where power and frequency are extreme: high-power RF and microwave transmitters, and the magnetron in every microwave oven, are vacuum tubes, because solid-state does not yet fully match certain very-high-power, high-frequency, high-voltage regimes. This is physics, not nostalgia — but it is generating and switching power, not computing. And in audio, guitar and hi-fi amplifiers still use tubes for the soft-clipping character of their overload, which is the tube as a linear amplifier, not a switch.

What actually persisted from the tube era into modern logic is not the tube but the *idea* it first made electronic: the cross-coupled Eccles–Jordan bistable is functionally the same latch drawn today in CMOS. The storage primitive behind every register and [flip-flop]({{< relref "/docs/building-blocks/storage" >}}) predates the transistor entirely; only the switching device underneath it changed.
