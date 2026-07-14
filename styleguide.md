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

## Page Structure — Inline Topic Flow

Pages are organized by **their own subject, not a fixed template.** Use `##` sections that follow the natural arc of the topic, and let observations, limitations, and practical notes flow inline where they belong rather than being collected into standard closing buckets.

There is **no required Tips / Caveats / In Practice trio.** That structure belongs to the bench-oriented *EE Notebook*, where it maps to hands-on troubleshooting; this book is explanatory and narrative, so forcing every page into those three buckets fights the material. Content that would once have gone there is re-homed:

- **How something works and behaves** — its own section(s), titled for the subject (*How a Relay Works*, *The Idea*, *Behavior*).
- **Limitations, failure modes, and tradeoffs** — folded into the narrative where they matter, most often in the "why it emerged / why it was replaced" discussion. A limitation is usually *part of the story*, not an appendix to it.
- **Practical guidance and mental models** — placed next to the thing they clarify.
- **Where it stands today / what persisted** — a genuine section when the subject earns one, since showing what carried forward is central to the book's thesis. Title it plainly (*Where Relays Stand Today*, *In Modern Use*).

A common arc for an era- or device-page is: what it is → how it does logic → why it emerged and what it replaced (limits folded in) → where it stands today. Building-block pages follow their own shape: what it is → how it behaves → variants → how it is used. Neither is mandatory — the subject decides.

Two habits survive from the older structure and still apply everywhere:

- **Lead a bulleted point with a bold phrase** capturing its key idea, then the explanation: `- **Bold lead-in** — the rest.` Use bullets where a list genuinely helps; prefer flowing prose otherwise.
- **Keep a paragraph to one idea.** Don't stack unrelated observations into a wall of text.

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

## Consistent Terminology

Section headings are chosen per page (see *Page Structure — Inline Topic Flow*), so there are no canonical section names to enforce. What must stay consistent is **concept terminology**: use the same name for the same idea across pages (a *flip-flop* is always a flip-flop, *propagation delay* always that), and prefer the term the glossary defines so the tooltip auto-linking resolves. Consistency beats cleverness.

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
