---
title: "Karnaugh Maps"
weight: 50
---

# Karnaugh Maps

A Karnaugh map is a [truth table]({{< relref "truth-tables" >}}) rearranged so that simplification becomes something the eye can do. The rows and columns are ordered in **Gray code** — each cell differs from its neighbors by exactly one variable — so that physically adjacent 1s can always be combined into a simpler term. It turns the algebra of [minimization]({{< relref "boolean-algebra" >}}) into pattern-spotting.

## Reading the Grid

Here is a three-variable function, F(A, B, C), with the columns in Gray order (00, 01, 11, 10):

| A \ BC | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| **0**  | 0  | 1  | 1  | 0  |
| **1**  | 0  | 1  | 1  | 0  |

The four 1s form a solid 2×2 block in the middle two columns. Those columns are exactly the ones where C = 1, and A and B take every value across the block — so A and B do not matter, and the whole function simplifies to just **F = C**. The [canonical]({{< relref "canonical-forms" >}}) sum-of-products would have listed four minterms; the map shows at a glance that they collapse to a single literal.

## The Rules of Grouping

- **Group adjacent 1s in rectangles whose size is a power of two** — 1, 2, 4, 8. Bigger groups eliminate more variables, so make each group as large as possible.
- **Adjacency wraps around** the edges of the map, top-to-bottom and left-to-right, because the Gray ordering is circular.
- **[Don't-cares]({{< relref "truth-tables" >}}) may be included** in a group when doing so enlarges it, and left out otherwise — free simplification from honestly recorded don't-cares.
- **Each group becomes one product term** naming only the variables that stay constant across it; OR the group terms together for the minimized result.

## When to Use One

Karnaugh maps are practical up to about five or six variables; beyond that the adjacencies become impossible to see and algorithmic methods (Quine–McCluskey) or a synthesis tool take over. In modern practice a designer rarely draws one — the tools minimize automatically, and an [FPGA]({{< relref "/docs/modern-world/fpgas" >}}) lookup table stores the truth table directly, so shaving the last gate matters less than it once did. But the K-map remains the fastest way to reason about small logic by hand, and it builds the intuition for *why* a function simplifies — including, as the next page shows, where a correct-looking circuit can still [glitch]({{< relref "hazards-and-glitches" >}}).
