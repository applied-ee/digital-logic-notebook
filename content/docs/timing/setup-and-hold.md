---
title: "Setup & Hold Time"
weight: 20
---
{{< katex >}}{{< /katex >}}

# Setup & Hold Time

A [flip-flop]({{< relref "/docs/building-blocks/storage/d-flip-flop" >}}) captures its data input at the clock edge, but only if that data is stable in a narrow window *around* the edge. **Setup time** is how long the data must be steady *before* the edge; **hold time** is how long it must remain steady *after*. Meet both and the flip-flop captures a clean value; violate either and it can go [metastable]({{< relref "metastability-and-synchronizers" >}}). These two numbers are the foundation on which all synchronous timing rests.

## The Timing Equation

For a signal launched by one flip-flop, passing through some combinational logic, and captured by the next, the clock period must be long enough for the whole trip to finish and still satisfy setup:

$$ T_{clk} \ge t_{cq} + t_{pd} + t_{su} + t_{skew} $$

The clock-to-output delay of the launching flip-flop (\(t_{cq}\)), the [propagation delay]({{< relref "propagation-delay-and-fan-out" >}}) of the logic between them (\(t_{pd}\)), the setup time of the capturing flip-flop (\(t_{su}\)), and the clock [skew]({{< relref "clocks-and-distribution" >}}) between them all eat into the period. Rearranged, this sets the maximum clock frequency — and checking it across every register-to-register path in a design is exactly what **static timing analysis** does. The path with the least margin is the critical path; the leftover margin is called **slack**, and getting every path to positive slack is **timing closure**.

## Hold Is a Different Problem

Setup violations are fixed by slowing the clock — a longer period gives the slow path time. **Hold violations cannot be**: hold is about a path being too *fast*, delivering new data to the capturing flip-flop before the old value is safely latched, and slowing the clock does not help because both edges move together. Hold is fixed instead by ensuring minimum path delays are long enough, and clock skew can push a marginal path into failure. So a design is bounded on two sides: the longest path must not violate setup, and the shortest must not violate hold.

## Why Synchronous Design Wins

This is the deeper reason the whole field builds around the clocked flip-flop. As long as every signal settles within the period and meets setup and hold, *nothing that happens between edges matters* — the [glitches and hazards]({{< relref "/docs/building-blocks/boolean-foundations/hazards-and-glitches" >}}) that plague asynchronous logic simply resolve before the next edge and are never seen. Synchronous timing turns "make every gate behave" into the single, checkable question of whether the slowest path fits inside one clock period.
