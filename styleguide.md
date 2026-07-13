# Content Style Guide

This document defines the structure, terminology, and intent of pages in the *Digital Logic Notebook*. Its purpose is consistency — not just in formatting, but in how readers develop **applied reasoning** about digital systems and the through-line that connects each era of logic technology.

The goal is that after reading a handful of pages, a reader subconsciously knows:
- where to find the core explanation of a technology or concept
- where to look for the tradeoffs and traps
- how ideas from one era connect to the ones that followed

---

## Page Levels

The notebook is organized into three conceptual levels:

- **L0** — Major eras or domains (chapters, e.g. *Discrete Logic Families*)
- **L1** — Topic groupings within a chapter (e.g. *TTL*)
- **L2** — Individual concepts, devices, or techniques (e.g. *Totem-Pole Outputs*)

Each level has a distinct purpose and writing style.

---

## L0 Pages (Chapter Overviews)

**Purpose:**
Orient the reader. Explain *why this era exists* — what it made possible, what it replaced, and where it sits in the evolution.

**Tone:**
High-level, conceptual, motivating.

**Characteristics:**
- No schematics or gate-level detail
- No step-by-step reasoning
- Minimal examples
- Focus on scope, historical framing, and the ideas the era contributed

**Typical Structure:**
- Short conceptual introduction
- Why this era matters and what it solved
- List of child L1 sections with brief descriptions

---

## L1 Pages (Concept Groupings)

**Purpose:**
Define a family of ideas or a technology and establish the *constraints* that shaped it.

**Tone:**
Authoritative but explanatory.

**Characteristics:**
- May include brief logic or timing references (sparingly)
- Explains what always holds versus what is commonly misremembered
- No step-by-step derivations
- Very limited numeric detail

**Typical Structure:**
- Conceptual framing
- What this section covers
- Curated list of L2 pages

---

## L2 Pages (Core Learning Units)

**Purpose:**
Teach one concept, device, or technique deeply enough to understand it correctly and to see how it connects to what came before and after.

This is where theory meets the actual behavior of the hardware.

**Tone:**
Practical, grounded, historically aware.

---

## Standard L2 Section Order

Not every L2 page must contain every section, but **when a section exists, its name and intent are fixed**.

---

### 1. Core Explanation
(Title varies: *How It Works*, *The Idea*, *Circuit Basics*, etc.)

- Explains the concept or device itself
- May include logic diagrams, timing diagrams, or truth tables
- Minimal numeric detail
- Focus on correctness, not application

---

### 2. Why It Emerged / What It Replaced
(Optional but common)

- The problem the technology or idea solved
- The tradeoff it accepted to get there
- What earlier approach it displaced, and why
- Prefer **plain-language framing** over jargon

---

### 3. Tips

**Purpose:**
Enable *correct understanding and use* of the concept.

**Tips answer:**
> "What should be understood or kept in mind to reason about this correctly?"

**What goes here:**
- Rules of thumb
- Useful mental models
- Sanity checks
- Numeric guidance that teaches *scale* (logic levels, fan-out, typical delays)

**What does NOT go here:**
- Failure modes and traps
- Root-cause analysis
- Interpretive diagnosis

---

### 4. Caveats

**Purpose:**
Prevent mistakes and false confidence.

**Caveats answer:**
> "Where does this break, mislead, or quietly fail?"

**What goes here:**
- Common misconceptions
- Assumptions that don't hold across families or eras
- Situations where intuition breaks
- "This works… until it doesn't"

**What does NOT go here:**
- How the concept is applied correctly (that is Tips)
- Interpretation of observed behavior (that is In Practice)

---

### 5. In Practice

**Purpose:**
Tie the concept to **how it actually shows up** — in real circuits, in later technologies, or in the conventions that outlived it.

In Practice answers:
> "How does this concept explain what is seen in real hardware, or why later designs look the way they do?"

**What goes here:**
- How correct theory explains confusing or surprising behavior
- Conventions that persisted after the original technology was gone
- Ideas that reappear, unchanged, in a later era
- Interpretation that links multiple observations together

**Preferred framing:**
- "often shows up as…"
- "this convention survived into…"
- "the same idea reappears in…"
- "commonly appears when…"

**In Practice is not a summary — it is a bridge between the concept and how it echoes forward.**

---

## Narrative Voice

Use a neutral, observation-oriented voice.

Avoid first-person and second-person phrasing (*I*, *we*, *you*, *your*) in body pages. The goal is to describe how the technology and its ideas behave — not to address or narrate from any individual perspective. (The signed preface is the one deliberate exception.)

**Preferred framing:**
- "In practice…"
- "This shows up as…"
- "The typical approach was…"
- "Most implementations handled this by…"
- "The idea carried forward as…"

**Avoid:**
- "When you see…"
- "The first thing you reach for…"
- "We can tell that…"
- "I've found that…"

Also avoid long multi-idea paragraphs — prefer one observable idea per paragraph.

---

## Consistent Terminology (Canonical)

Use these section names verbatim across all pages:

- **Tips**
- **Caveats**
- **In Practice**

Avoid:
- "Practical Considerations"
- "Why This Matters"
- "Practice Notes" (unless a special callout)

Consistency beats cleverness.

---

## Examples and Numbers

> **If an example uses realistic values and teaches scale, keep it.
> If it only restates a definition, generalize it.**

- Concrete numbers are encouraged at L2, especially for:
  - Logic levels and noise margins
  - Fan-out and drive limits
  - Propagation delays and clock rates
  - Gate, transistor, and device counts across eras
- Avoid contrived examples that teach nothing about scale

This is an engineer's notebook, not a textbook.

---

## Tone Contract

Across all levels:

- Prefer clarity over elegance
- Prefer the reasoning behind a technology over rote description of it
- Trace the through-line: connect each idea to what preceded and followed it
- Avoid jargon unless it is explicitly being taught
- Treat historical tradeoffs as engineering decisions with reasons, not trivia

---

## Final Principle

This notebook is not about memorizing part numbers or device catalogs.

It's about building **applied reasoning** about digital systems:
- understanding what each era of logic technology solved
- understanding what it gave up to get there
- recognizing the ideas that survived into the hardware in use today

That skill is what turns a pile of historical devices into a coherent story.
