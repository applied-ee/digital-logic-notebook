---
title: "SR Latch"
weight: 10
---

# SR Latch

The SR (set-reset) latch is the simplest memory element, and it is the seed from which every latch, flip-flop, and register grows. Cross-couple two gates so that each one's output feeds back into the other's input, and the pair becomes **bistable**: it has two stable states and will rest in whichever one it was last driven into, holding that state after the driving input is removed. That feedback loop is what "remembering" means in hardware.

## Two Gates, Two Forms

An SR latch is built from a cross-coupled pair of [NOR]({{< relref "/docs/building-blocks/gates/nor" >}}) gates (active-high inputs) or a cross-coupled pair of [NAND]({{< relref "/docs/building-blocks/gates/nand" >}}) gates (active-low inputs). The NOR version is the easier to read:

| S | R | Q (next) |
|---|---|----------|
| 0 | 0 | Q — hold |
| 1 | 0 | 1 — set |
| 0 | 1 | 0 — reset |
| 1 | 1 | invalid |

A pulse on **Set** drives Q high; a pulse on **Reset** drives it low; with both inputs inactive the latch **holds** its last value. Asserting both at once is forbidden — it forces the outputs into an inconsistent state, and when the inputs are released together the latch settles unpredictably. Which input "wins" when both are asserted is the meaning of *set-dominant* versus *reset-dominant*, and it is decided by which gate the priority signal drives.

## The Oldest Circuit in the Book

The SR latch is not one invention but a recurring one. It is the **seal-in [relay]({{< relref "/docs/before-the-ic/relays" >}})** whose own contact holds its coil energized; it is the **Eccles–Jordan pair** of cross-coupled [triodes]({{< relref "/docs/before-the-ic/vacuum-tubes" >}}) from 1918; it is two cross-coupled CMOS inverters in a static memory cell. Different switches, identical topology — the clearest example in this notebook of an idea that survived every change of technology.

## Where It Fits

On its own the SR latch is level-sensitive and asynchronous — it reacts to its inputs whenever they change, with no notion of a clock. That is enough for simple jobs like switch [debounce]({{< relref "/docs/glue-logic-toolbox/debounce" >}}), but it is too unruly for large synchronous systems. Adding an enable and eliminating the forbidden state gives the [D latch]({{< relref "d-latch" >}}); adding a clock edge gives the [D flip-flop]({{< relref "d-flip-flop" >}}). Everything sequential is a refinement of this loop.
