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
- Keep contrast high between background and foreground, and between neighboring visual elements.
- Keep fonts large enough for people sitting far from the screen.
- Prefer visuals over words whenever a concept can be shown instead of narrated.
- Keep code snippets minimal: include only the lines needed to understand the point.
- Break the deck into sections. End every section with micro-conclusions. End the whole deck with overall conclusions.
- Build each section from short stories. One story should usually cover one concept or example in 4-10 slides.

## Recommended workflow

1. Start with a deck outline.
2. Split the deck into sections.
3. Inside each section, define short stories:
   - one story = one concept, mechanism, example, or comparison
   - typical story length = 4-10 slides
   - slides inside the story should reveal the idea step by step
4. End each section with a short micro-conclusion slide.
5. End the deck with overall conclusions.

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
- If the snippet is still too tall or dense, split it across slides or replace part of it with a diagram or diff-style comparison.

## Viewport and readability check

Before finishing presentation work, review every changed slide with these questions:

1. Does everything fit on the viewport without feeling cramped?
2. Is the font size large enough for an audience at the back of the room?
3. Is the visual contrast strong enough at a glance?
4. Can the audience understand the slide quickly, or is there too much to read?
5. Would two slides communicate this better than one?

If the answer is poor on any of these checks, fix the slide before considering the work done.

If tooling is available, preview or build the deck after substantial edits. Even with preview, do not accept borderline density.

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
