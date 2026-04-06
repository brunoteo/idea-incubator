---
name: idea-decide
description: Use when the user wants a final verdict on an idea — "should we build this?", "go or kill?", "is this worth pursuing?". Requires prior phases to be complete. Do NOT use for brainstorming (idea-concept), validation (idea-validate), distribution (idea-gtm), feasibility (idea-feasibility), or MVP scoping (idea-mvp).
argument-hint: [idea-name]
---

# Idea Decide — Verdict

> **STUB VERSION.** This skill currently reads CONCEPT.md only. It will be upgraded to synthesize across all 5 prior artifacts once the middle phases are built.

Make a go/park/kill decision on an idea.

## On Start

1. Read `CONVENTIONS.md` for shared protocols.
2. If `$ARGUMENTS` is provided, use it as the idea slug. Otherwise ask: "Which idea? (folder name under ideas/)"
3. Set the working directory to `ideas/<idea-slug>/`.
4. **Gate check (stub):** Read `CONCEPT.md`. If missing or `status` is not `complete`, refuse:
   > "Can't decide without a solid concept. Run `/idea-concept <slug>` first."
5. Read all existing artifacts to build the full picture.

## The Decision Process

### Step 1: Steel-man both sides

Present two clear, honest arguments:

**The case FOR go:**
- Strongest arguments from the available analysis.
- What makes this worth building?
- What's the upside scenario?
- Reference specific findings from the artifacts.

**The case AGAINST go:**
- Strongest counterarguments.
- Real risks, weak evidence, unresolved questions.
- **Do NOT soften this.** If the idea has fatal flaws, say so.

### Step 2: Weigh the evidence

Read every artifact's frontmatter. Explicitly cite:
- `evidence_strength` per phase — how solid is the foundation?
- `overridden` / `override_reason` — where did the user push past a red flag?
- `gap_in` / `gap_note` — what gaps were noted and never resolved?
- `key_risks` — accumulated risk tags across all phases.

These are first-class evidence in the verdict. An override without resolution is a risk. A gap that was never addressed is a weakness.

### Step 3: Make a recommendation

State your verdict clearly:
- **Go:** What the MVP should look like (reference MVP.md if it exists) and concrete next steps.
- **Park:** What specific new information would change this to a go. Be concrete — "if X happens" not "if things change." For pivot-style parks: which insight is valid, what to sharpen, which phase to restart from.
- **Kill:** Why this isn't worth pursuing. Name the fatal flaw directly.

**Own the recommendation.** Don't hedge with "it depends on your risk tolerance" or "only you can decide." Have an opinion and defend it.

### Step 4: User decides

Wait for the user's decision. The recommendation is input, not the final word. If they disagree, that's fine — capture their reasoning in DECISION.md.

## Red Flags

| User says | Skill responds |
|---|---|
| "Let's just go for it" (without engaging with the analysis) | "Which specific finding makes you confident? The analysis surfaced [risks] — are you comfortable with those?" |
| "I don't care about the risks" | "The risks don't care about that. Which ones have you thought through, and which are you choosing to accept?" |
| "It feels right" | "Gut instinct is data, but it's not enough alone. What evidence supports the feeling?" |
| "Let's park it and come back later" (as avoidance) | "Park needs a trigger — what specific event or information would bring you back? Otherwise park is just a comfortable kill." |

## Writing DECISION.md

````yaml
---
phase: decide
status: in-progress
verdict: null
evidence_strength: null
key_risks: []
overridden: false
override_reason: null
---
````

````markdown
# <Idea Name> — Decision

## Verdict: go | park | kill

## The Case For
[Steel-manned argument for building]

## The Case Against
[Steel-manned argument against — not softened]

## Evidence Inventory
[Per-phase: evidence_strength, overrides taken, gaps noted]

## Reasoning
[Why this verdict — explicitly citing which phase findings drove it]

## What Would Change This
[For park: specific triggers. For kill: what would have to be different. For go: what could still derail this.]

## Next Steps
[For go: concrete actions. For park: revisit conditions. For kill: lessons learned.]
````

On completion:
- `status: complete`
- `verdict: go | park | kill`
- `evidence_strength` based on the overall quality of evidence across all phases.
- `key_risks` — the top risks carried forward.
