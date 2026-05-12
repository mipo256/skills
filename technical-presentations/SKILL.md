---
name: slidev-technical-presentations
description: >-
  Guides authoring and revision of Slidev-based technical decks: progressive disclosure,
  story-driven sections, viewport-safe layouts, high-contrast readable typography,
  concise syntax-highlighted code, visual-first explanations, section micro-conclusions,
  and closing synthesis.
  Use when the user creates, reviews, or restructures lecture slides, conference or meetup
  talks, workshops, `slides.md`, Slidev layouts/themes, or embedded diagrams and snippets
  in a Slidev project.
---

# Slidev technical presentations

Use this skill when authoring or revising **live technical presentations** (talks, lectures, workshops) built with **Slidev**. For prose documentation such as READMEs or runbooks, use a technical writing / documentation skill instead.

## Core principles

- Build the presentation with Slidev unless the user explicitly asks for another format.
- Prefer progressive disclosure both across slides and inside slides—but **each reveal should earn its place**. Too many `v-click` steps on one slide feels like a stutter; split into slides or merge low-value clicks. **Progressive disclosure applies to code too:** for a medium-sized listing, the same snippet can unfold in narrative beats (what gets called first, what wraps it, what happens last) instead of showing the whole block at once.
- Treat viewport overflow and tiny text as bugs. If a slide feels crowded, split it.
- Treat scrollable text or code on slides as a design failure in most cases. Avoid it whenever possible.
- Keep contrast high between background and foreground, and between neighboring visual elements. **Do not rely on color alone** for meaning (labels, icons, or patterns help colorblind viewers and cheap projectors).
- Keep fonts large enough for people sitting far from the screen.
- Prefer visuals over words whenever a concept can be shown instead of narrated.
- Keep code snippets minimal: include only the lines needed to understand the point.
- Break the deck into sections. End every section with micro-conclusions. End the whole deck with overall conclusions.
- Build each section from short stories. One story should usually cover one concept or example in roughly **4–10 slides** (adjust for talk length; a 20-minute slot needs fewer beats than a tutorial block).

## Recommended workflow

1. Read **`package.json`** (or the monorepo equivalent) for dev, build, export, and lint scripts. If present, skim **`slidev.config.ts`** / **`slidev.config.js`**, theme entry, and any shared slide components so new slides match project conventions.
2. Start with a deck outline: audience, goal, and time budget. Put the **promise of the talk** early (why listen, what they can do after).
3. Split the deck into sections.
4. Inside each section, define short stories:
   - one story = one concept, mechanism, example, or comparison
   - typical story length = 4–10 slides
   - slides inside the story should reveal the idea step by step
5. End each section with a short micro-conclusion slide.
6. End the deck with overall conclusions.
7. After making changes, run the project’s **real** build or validation command from `package.json` (or equivalent) and fix failures. Do not guess the command.

## Story pattern

Use a simple narrative shape for each story:

1. Set up the problem, question, or context.
2. Show the baseline, misconception, or starting point.
3. Reveal the explanation progressively.
4. Show the result, consequence, or comparison.
5. Close with the takeaway the audience should remember.

Not every story needs all five beats, but the audience should always feel guided from setup to takeaway.

## Slide authoring rules

- Give each slide **one job**. The title line should telegraph that job; if the slide tries to explain two ideas, split it.
- Use progressive disclosure with Slidev primitives such as `v-click` when it helps the audience follow the logic.
- Prefer multiple simple slides over one dense slide.
- Keep bullets short. If bullet text becomes sentence-like, convert it into multiple reveals or multiple slides.
- Use diagrams, tables, mermaid blocks, visual comparisons, step flows, and before/after layouts when they explain faster than prose. **Keep mermaid and other diagrams shallow** for slides: fewer nodes, shorter labels; if the graph is huge, split across slides or show a zoomed region.
- Use standard Slidev layouts and markdown first. Reach for custom Vue components only when the default toolbox is not enough.
- If the deck already exists, preserve its voice and theme where practical, but improve clarity and pacing.
- **Presenter notes:** When timing, demos, or caveats do not belong on the slide, use the project’s usual pattern (for example Slidev **`notes`** in slide frontmatter, or whatever the repo already uses). Do not cram speaker-only detail onto the canvas.

## Code snippets

**Syntax highlighting is mandatory.** Every real source listing must render with proper language grammar: use a **correct language tag** on markdown fences (e.g. ` ```typescript `, not a bare ` ``` ` or a vague `text` tag for code). If the deck uses HTML, Vue, or a Slidev code component instead of fences, configure it so Shiki (or the project’s highlighter) still applies to that block. Plain monospace without token colors is not acceptable for teaching code—fix the fence, component, or theme integration before shipping the slide.

- Include only the code that is strictly necessary for the teaching point.
- Omit imports, getters/setters, boilerplate, and unrelated branches unless they matter for the explanation.
- Shorten names and surrounding context only if the meaning stays clear.
- Prefer one focused snippet per slide.
- If the snippet is still too tall or dense, first remove non-essential lines. Then reformat it so it fits the viewport cleanly if possible.
- If it still does not fit, split it across slides or replace part of it with a diagram or diff-style comparison instead of making the slide scroll.

**Progressive disclosure inside one snippet:** When a listing is **medium-sized**—too much to absorb in one glance but still one coherent story—reveal it in **steps on a single slide** (or a tight sequence) so the speaker can narrate a path through the code. Example beats: “here we call this service,” “this runs inside the transactional method,” “finally we publish the message to Kafka.” The audience sees **one** logical code sample; each beat adds context or the next lines using Slidev primitives (`v-click`, line-level highlights, or patterns the repo already uses). Match the number of steps to the talk: fewer clicks for a fast section, more for a deep dive, but keep each step meaningful.

**Highlightable, stepwise code in Slidev:** A single fenced markdown block is one opaque unit, which makes **per-line or per-fragment** reveals awkward. When you need emphasis or click-by-click disclosure **inside** the listing, use structured markup or Slidev/Vue patterns the project already employs (`<span>`/`v-click` wrappers, line highlighting, split fences under one `v-click` group, etc.) so **syntax highlighting is preserved**—do not fall back to unhighlighted text just to get clicks. If the project has no pattern yet, introduce the smallest structure that keeps both highlighting and reveals.

## Viewport and readability check

Before finishing presentation work, review every changed slide:

1. Does everything fit on the viewport without feeling cramped?
2. Is the font size large enough for an audience at the back of the room?
3. Is the visual contrast strong enough at a glance, and is meaning clear **without** depending solely on color?
4. Can the audience understand the slide quickly, or is there too much to read?
5. Is any slide relying on scrollable text or code that should be trimmed, reformatted, or split instead?
6. Would two slides communicate this better than one?
7. Are click/reveal sequences smooth rather than tedious?
8. Does every code listing use a **correct language** (or equivalent) so **syntax highlighting** actually appears in the built deck?

If the answer is poor on any of these checks, fix the slide before considering the work done.

Previewing the deck is helpful but does not replace a successful **build** (or the project’s chosen validation). After substantial edits, run that command and fix failures. Even with preview, do not accept borderline density.

## Quality bar

Before wrapping up, confirm:

- Slidev-based structure and project build succeeds after changes
- Progressive disclosure used with restraint
- Sections made of short stories, each with a micro-conclusion
- Overall conclusions (and next steps if useful) at the end
- High contrast, readable type, minimal code on slides, **all code syntax-highlighted**
- Visuals preferred over text where they shorten time-to-understanding
- No overcrowded slides; no guessed scripts—commands taken from `package.json` or equivalent
