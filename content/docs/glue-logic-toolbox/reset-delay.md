---
title: "Reset Delay"
weight: 80
---

# Reset Delay

At power-up, a chip must be held in reset until its supply is stable, then released cleanly. Do this wrong and the device wakes into a garbage state, latches up, or resets erratically as the rail sags. The need is a reset that asserts while power is coming up and releases only once the supply is good — ideally with a defined delay.

## The Right Answer: a Supervisor IC

A dedicated **reset supervisor** (MAX809, MCP100/MCP809, TPS3839, and many others) is the proper part. It watches the supply voltage against a precise threshold, holds reset asserted whenever the rail is below it, and releases after a fixed delay once the rail is good — and, crucially, re-asserts on a **brown-out** if the supply dips later. Many include a watchdog input as well. This is what production designs use, because it handles the cases a naïve delay cannot.

## The Cheap Answers, and Their Limits

- **An RC on the reset pin** — a resistor and capacitor that charge up to release reset after a delay. It is nearly free and common on simple boards, but it is crude: it delays by a time constant rather than tracking the *actual* supply voltage, gives no brown-out protection, and can release too early if the rail rises slowly. Fine for undemanding designs, risky for anything that must be robust.
- **A 555 timer as a one-shot** — configured as a monostable, it produces a single reset pulse of defined length at power-up. It gives a clean, repeatable delay but, like the RC, does not monitor the supply.

The rule of thumb: if the reset merely needs *a delay*, an RC or a 555 will do. If it needs to *guarantee* the part only runs on a good supply — which most real designs do — use a supervisor.
