---
title: "♻️ What Became Obsolete?"
weight: 6
bookCollapseSection: true
---

# What Became Obsolete?

The most useful question to ask about any classic part is not "how does it work?" but "would I still design it in today, and if not, what replaced it?" This table is the honest answer. It is deliberately blunt: some parts are genuinely dead, some are quietly immortal, and the difference is worth knowing before reaching for either.

| Technology | Still useful? | Modern replacement |
|---|---|---|
| 7490 counter | Mostly no | MCU timer |
| 74161 counter | Sometimes | FPGA / MCU |
| 74138 decoder | Yes | Often still used |
| 74HC595 | Absolutely | Still common |
| 74HC14 | Absolutely | Still common |
| 74HC245 | Absolutely | Still common |
| 4066 | Absolutely | Still common |
| 555 | Surprisingly yes | MCU timer or dedicated timer IC |
| EPROM | Mostly hobby / retro | Flash |
| PAL | Mostly obsolete | CPLD |
| GAL | Mostly obsolete | CPLD |

The pattern is not "old is dead." It is that *counting and sequencing* migrated into microcontrollers and programmable logic, while *interfacing, buffering, level translation, and analog switching* stayed discrete because they still solve a physical problem no processor can absorb.
