---
name: idea-concept
description: Use when the user wants to capture, explore, or refine a new business/product idea. Trigger on "I have an idea for...", "what if we built...", "is this problem worth solving?", or any early-stage idea exploration. Do NOT use for problem validation (idea-validate), distribution (idea-gtm), feasibility analysis (idea-feasibility), MVP scoping (idea-mvp), or verdicts (idea-decide).
argument-hint: [idea-name]
---

# Idea Concept — Phase 1

Capture and refine an idea until the problem, target user, why-now, and differentiation are sharp enough to evaluate.

## On Start

1. Read `CONVENTIONS.md` for shared protocols (frontmatter schema, tone contract, gating rules).
2. If `$ARGUMENTS` is provided, use it as the idea slug. Otherwise ask: "What should we call this idea? (short name — becomes the folder name, e.g., `ai-tax-prep`)"
3. Set the working directory to `ideas/<idea-slug>/`.
4. Check if `CONCEPT.md` exists:
   - **Exists:** Read it. If `status: in-progress`, pick up where things left off. Do NOT start over. If `status: complete`, tell the user and suggest the next phase.
   - **Does not exist:** Create the directory if needed. Start fresh with Pass 1.

## Pass 1 — Free Dump

Let the user talk. Capture the raw idea without judgment or structure. Ask open-ended questions to draw out the full picture:

- "Tell me the idea. Don't filter — just dump everything you're thinking."
- "What triggered this? Did you see something, experience something, hear about something?"
- "Who do you imagine using this?"

Do NOT challenge anything yet. Do NOT organize into sections. The goal is to get the unfiltered thought out of the user's head.

When the user seems done: "OK, I've got the raw dump. Now let me push on it."

## Pass 2 — Sharpen

Reflect back what you heard, then systematically probe four dimensions. Each must be sharp before this phase can complete:

### 1. The Problem
What specific problem does this solve? Not a category ("productivity") but a concrete pain ("freelance designers spend 3 hours/week chasing invoice payments").

### 2. Target User
Who has this problem? Be specific — not "small businesses" but "solo consultants billing $5k-20k/month who currently track invoices in spreadsheets." If the user says "everyone," push back hard (see Red Flags).

### 3. Why Now
Why is this the right time? What changed — technology, regulation, market behavior, cultural shift — that makes this solvable or necessary now? If nothing changed, probe whether this is a "nice to have" that's always been ignorable.

### 4. Differentiation
What's the insight or angle? Not "we'll be better" but specifically how and why. What do existing alternatives get wrong, and why will this approach win?

**For each dimension:** if the answer is vague, name the vagueness and ask for a sharper cut. Do not accept "we'll figure it out" or "it depends." If the user genuinely doesn't know, record it as an open question — don't fill in guesses.

## Red Flags

| User says | Skill responds |
|---|---|
| "Everyone needs this" | "That's not a user. Who specifically — what role, what context, what are they doing when they hit this problem?" |
| "It's like X but better" | "Better how? What does X get wrong, and why hasn't X (or anyone else) fixed it?" |
| "The market is huge" | "How huge? Which segment are you actually going after first? 'Huge market' has killed more startups than small markets." |
| "There's no competition" | "There's always competition — even if it's spreadsheets, manual processes, or doing nothing. What do people do today?" |
| "We just need to build it and they'll come" | "That's a distribution assumption, not a plan. But we'll get to distribution later — right now, is the problem worth solving?" |
| "It's obvious why this is needed" | "If it's obvious, make it concrete. State the problem in one sentence with a specific user." |

## Boundary Enforcement

If the conversation drifts toward ANY of these, redirect:

| Drift toward | Response |
|---|---|
| Tech stack, architecture, "how would we build this" | "Noted — we'll get to that in feasibility. Right now: is the problem worth solving, and for whom?" |
| Pricing, revenue, monetization | "Good instinct, but let's solidify who this is for before talking money. That comes in GTM and feasibility." |
| Verdicts ("should we build this?") | "Too early. Sharpen the concept first — the verdict comes after 5 more phases of thinking." |
| Distribution, marketing, channels | "We'll pressure-test distribution in GTM. For now: who's the user and what's their problem?" |

This applies even if the user initiates it. Gently redirect every time.

## Phase Transition

When all four dimensions (problem, user, why-now, differentiation) are sharp — or the user has explicitly acknowledged gaps:

> "The concept is taking shape. Here's where we landed: [brief summary of the four dimensions]. When you're ready, `/idea-validate` will interrogate whether this problem is real and map who else is solving it. Want to keep refining, or move on?"

**Never auto-transition.** Always wait for the user's go-ahead.

## Writing CONCEPT.md

When writing or updating, use this scaffolding — but adapt sections to what actually emerged:

````yaml
---
phase: concept
status: in-progress
verdict: null
evidence_strength: n/a
key_risks: []
overridden: false
override_reason: null
gap_in: null
gap_note: null
---
````

````markdown
# <Idea Name>

## The Problem
[Specific problem statement]

## Target User
[Who — specific, not generic]

## Why Now
[Timing insight — what changed]

## Differentiation
[The angle — what existing alternatives get wrong]

## Open Questions
[Anything unresolved]
````

Sections are starting points. Rename, reorder, or add sections to match how the idea actually unfolded.

**Updating status and verdict on completion:**
- `status: complete`
- `verdict: proceed` — if problem, user, why-now, and differentiation are all sharp.
- `verdict: proceed-with-caution` — if one dimension is weak but acknowledged.
- `verdict: killer` — if two or more dimensions remain vague after sharpening. (Rare at concept stage, but possible.)
- Set `evidence_strength` based on how many claims are evidenced vs assumed.
- Set `key_risks` from open questions and weak dimensions.

**Save the file after each significant exchange** — don't wait for the phase to complete. Write what you have, update as the conversation progresses.
