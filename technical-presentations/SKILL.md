---
name: slidev-technical-presentations
description: Write and revise Slidev-based technical presentations with progressive disclosure, story-driven sections, viewport-safe layouts, high-contrast visuals, large readable typography, concise code snippets, visual-first explanations, section micro-conclusions, and final conclusions. Use whenever the user asks to create, improve, review, or restructure a lecture deck, conference talk, workshop slides, `slides.md`, or any technical presentation content.
---

# Slidev Technical Presentations

Use this skill when authoring or revising technical presentations.

## Core principles

- Build the presentation with Slidev unless the user explicitly asks for another format.
- Prefer progressive disclosure both across slides and inside slides.
- Treat viewport overflow and tiny text as bugs. If a slide feels crowded, split it.
- Treat scrollable text or code on slides as a design failure in most cases. Avoid it whenever possible.
- Keep contrast high between background and foreground, and between neighboring visual elements.
- Keep fonts large enough for people sitting far from the screen.
- Prefer visuals over words whenever a concept can be shown instead of narrated.
- Keep code snippets minimal: include only the lines needed to understand the point.
- Break the deck into sections. End every section with micro-conclusions. End the whole deck with overall conclusions.
- Build each section from short stories. One story should usually cover one concept or example in 4-10 slides.

## Recommended workflow

1. Scan `package.json` or the equivalent project file first to understand how this Slidev project is built, previewed, or validated.
2. Start with a deck outline.
3. Split the deck into sections.
4. Inside each section, define short stories:
   - one story = one concept, mechanism, example, or comparison
   - typical story length = 4-10 slides
   - slides inside the story should reveal the idea step by step
5. End each section with a short micro-conclusion slide.
6. End the deck with overall conclusions.
7. After making changes, run the project's real build or validation command and make sure it succeeds.

## Story pattern

Use a simple narrative shape for each story:

1. Set up the problem, question, or context.
2. Show the baseline, misconception, or starting point.
3. Reveal the explanation progressively.
4. Show the result, consequence, or comparison.
5. Close with the takeaway that the audience should remember.

Not every story needs all five beats, but the audience should always feel guided from setup to takeaway.

## Slide authoring rules

- Give each slide one job. If a slide tries to explain two ideas, split it.
- Use progressive disclosure with Slidev primitives such as `v-click` when it helps the audience follow the logic.
- Prefer multiple simple slides over one dense slide.
- Keep bullets short. If bullet text becomes sentence-like, convert it into multiple reveals or multiple slides.
- Use diagrams, tables, mermaid blocks, visual comparisons, step flows, and before/after layouts when they explain faster than prose.
- Use standard Slidev layouts and markdown first. Reach for custom Vue components only when the default toolbox is not enough.
- If the deck already exists, preserve its voice and theme where practical, but improve clarity and pacing.

## Code snippets

- Include only the code that is strictly necessary for the teaching point.
- Omit imports, getters/setters, boilerplate, and unrelated branches unless they matter for the explanation.
- Shorten names and surrounding context only if the meaning stays clear.
- Prefer one focused snippet per slide.
- If the snippet is still too tall or dense, first remove non-essential lines. Then reformat it so it fits the viewport cleanly if possible.
- If it still does not fit, split it across slides or replace part of it with a diagram or diff-style comparison instead of making the slide scroll.

**Highlightable code in Slidev:** When you write code samples for Slidev, structure them so a person (or a later edit, including by an assistant) can attach highlighting or emphasis to **specific** fragments—lines, tokens, or regions—not only to the whole block. A single fenced markdown block (e.g. opening with ` ```java `) is one opaque unit and is awkward to annotate inside. Prefer HTML structure instead: normal elements such as `<div>`, `<span>`, `<pre>`, or other markup the project already uses for slides, so individual parts can be wrapped, class-tagged, or paired with Slidev/Vue directives for stepwise reveals and syntax or emphasis highlights.

## Viewport and readability check

Before finishing presentation work, review every changed slide with these questions:

1. Does everything fit on the viewport without feeling cramped?
2. Is the font size large enough for an audience at the back of the room?
3. Is the visual contrast strong enough at a glance?
4. Can the audience understand the slide quickly, or is there too much to read?
5. Is any slide relying on scrollable text or code that should be trimmed, reformatted, or split instead?
6. Would two slides communicate this better than one?

If the answer is poor on any of these checks, fix the slide before considering the work done.

Do not guess the build command. Read `package.json` or the equivalent project file and use the project's actual build or validation command.

After substantial edits, run that build or validation command and make sure it succeeds. Previewing the deck is helpful, but it does not replace a successful build check. Even with preview, do not accept borderline density.

## Quality bar

Before wrapping up, make sure the deck has:

- Slidev-based structure
- progressive disclosure
- sections made of short stories
- a micro-conclusion at the end of each section
- overall conclusions at the end
- high contrast
- readable font sizes
- minimal code snippets
- visuals preferred over text where possible
- no overcrowded slides
- the project's build command was identified from `package.json` or an equivalent file
- the deck builds successfully after the changes
