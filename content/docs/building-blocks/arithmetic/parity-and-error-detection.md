---
title: "Parity & Error Detection"
weight: 40
---

# Parity & Error Detection

Parity is the cheapest integrity check in digital logic: a single extra bit that reveals whether data has been corrupted in the simplest way. It costs almost nothing to compute, which is exactly why it has been used everywhere from memory to serial links for decades.

## One XOR Tree

The parity of a group of bits is whether the count of 1s among them is odd — and that is precisely what an [XOR]({{< relref "/docs/building-blocks/gates/xor" >}}) of all the bits computes. A **parity generator** is therefore just an XOR tree across the data. A parity bit is appended so that the total number of 1s is always even (**even parity**) or always odd (**odd parity**), as agreed in advance.

Checking is the same circuit run again: XOR all the received data bits *and* the received parity bit. If nothing was corrupted the result is 0; if it is 1, an error has occurred. The classic part is the 74180, a 9-bit parity generator/checker.

## What It Catches, and What It Misses

Parity's limits follow directly from being one bit. It detects any **odd** number of flipped bits — one, three, five — but a pair of errors cancels in the XOR and slips through undetected. And it only ever says *that* an error happened, never *where*, so it can **detect but not correct**. For many uses (a noisy UART line, a memory sanity check) catching single-bit errors cheaply is enough.

## When One Bit Is Not Enough

Stronger schemes escalate from there. A **checksum** or a **CRC** — the latter built from an XOR-tapped [linear-feedback shift register]({{< relref "/docs/building-blocks/moving-data/shift-registers" >}}) — catches far more error patterns for a modest amount of logic, and is standard on storage and communication links. **Hamming and other ECC codes** add enough redundant bits to not only detect but *correct* single-bit errors, which is what memory in servers and spacecraft relies on. All of them, parity included, rest on the same idea: spend a few extra bits, computed from the data, so that corruption has somewhere to show up.
