---
title: "De Morgan's Theorems"
weight: 30
---
{{< katex >}}{{< /katex >}}

# De Morgan's Theorems

De Morgan's theorems are the two most-used identities in all of digital logic. They describe what happens when the output of an AND or an OR is inverted:

$$ (A \cdot B)' = A' + B' $$

$$ (A + B)' = A' \cdot B' $$

In words: inverting the output of a gate is the same as **swapping the gate type (AND ↔ OR) and inverting every input**. The theorems extend to any number of inputs — the complement of a whole product is the sum of the complemented terms, and vice versa.

## Bubbles: One Gate, Two Faces

The practical consequence is that every gate has an equivalent "other" form, reached by moving the inversion bubbles:

| This gate | is identical to |
|---|---|
| [NAND]({{< relref "/docs/building-blocks/gates/nand" >}}) — (A·B)′ | an [OR]({{< relref "/docs/building-blocks/gates/or" >}}) with both inputs inverted — A′ + B′ |
| [NOR]({{< relref "/docs/building-blocks/gates/nor" >}}) — (A+B)′ | an [AND]({{< relref "/docs/building-blocks/gates/and" >}}) with both inputs inverted — A′·B′ |

A NAND *is* a bubbled-input OR; a NOR *is* a bubbled-input AND. Reading a schematic full of mixed gate symbols becomes straightforward once each bubble is accounted for: two bubbles meeting across a wire cancel, and a gate can always be redrawn in whichever form makes the logic clearest.

## Why It Is So Central

De Morgan is the reason NAND and NOR are [universal]({{< relref "/docs/building-blocks/gates/nand" >}}). Because any AND/OR/NOT expression can be rewritten with the inversions pushed onto the inputs, any function can be converted into all-NAND or all-NOR form — which is exactly what lets a design be built from a single gate type, and what makes the natural inverting gates of a CMOS process sufficient to build everything. "Bubble pushing" — sliding inversions through a circuit using these two rules — is the everyday technique for converting a design between representations and matching it to the gates actually available.
