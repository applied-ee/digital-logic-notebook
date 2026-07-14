---
title: "♻️ What Became Obsolete?"
weight: 6
bookCollapseSection: true
---

# What Became Obsolete?

The most useful question to ask about any classic part is not "how does it work?" but "would I still design it in today, and if not, what replaced it?" This table is the honest answer. It is deliberately blunt: some parts are genuinely dead, some are quietly immortal, and the difference is worth knowing before reaching for either.

| Part | Description | Still useful? | Modern replacement |
|---|---|---|---|
| 7490 | Decade (÷10) ripple counter | Mostly no | MCU timer |
| 74161 | 4-bit synchronous binary counter | Sometimes | FPGA / MCU |
| 74138 | 3-to-8 line decoder / demultiplexer | Yes | Often still used |
| 74HC595 | 8-bit serial-in, parallel-out shift register | Absolutely | Still common |
| 74HC14 | Hex Schmitt-trigger inverter | Absolutely | Still common |
| 74HC245 | Octal bus transceiver (direction-controlled) | Absolutely | Still common |
| 4066 | Quad bilateral (analog) switch | Absolutely | Still common |
| 555 | Timer / oscillator IC (astable & monostable) | Surprisingly yes | MCU timer or dedicated timer IC |
| EPROM | UV-erasable programmable ROM | Mostly hobby / retro | Flash |
| PAL | Programmable Array Logic (fuse-programmed) | Mostly obsolete | CPLD |
| GAL | Generic Array Logic (reprogrammable PAL) | Mostly obsolete | CPLD |

The pattern is not "old is dead." It is that *counting and sequencing* migrated into microcontrollers and programmable logic, while *interfacing, buffering, level translation, and analog switching* stayed discrete because they still solve a physical problem no processor can absorb.
