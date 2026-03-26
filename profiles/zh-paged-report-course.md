# zh-paged-report-course

> Chinese paged code course profile for `codebase-to-course`.

## Purpose

Use this profile when the user wants the course to feel like a **Chinese-first paged code course**:

- The course is still built from the codebase using Zara's `codebase-to-course` workflow.
- The output should feel like a reusable Chinese code course, not a one-off paged report.
- The presentation layer should use a fixed paged shell, canonical page archetypes, lightweight transitions, and a teaching rhythm that scales with codebase complexity.
- The output should teach in a stable sequence: judgment, why now, code intro, code metadata, code explanation, learning target, callout, and a "revisit later" cue.

## Execution priority

This profile is a **forced template**.

Once selected, it outranks the base skill's generic discovery flow for presentation and curriculum structure. Do not improvise a new homepage or ask the user to choose between presentation modes.
The profile must be backed by shared public-layer files, not just prose rules.

## Trigger

Activate this profile when the user explicitly says one of these:

- `zh-paged-report-course`
- 中文分页报告
- 中文分页报告课件
- 讲解页
- 分页讲解
- 分页课件
- 中文优先的课程页
- `use the Chinese paged report template`

If the user does not explicitly ask for this profile, stay on the base skill.

## Must-not-ask list

When this profile is active, do not ask:

- whether the user wants the whole project or one page
- what visual style they prefer
- whether they want Chinese paged report output
- whether they want this template or another template
- any 1/2/3 branching question about presentation
- any generic discovery prompt that delays generation

## Course contract

This profile is not a loose report style. It is a reusable teaching contract for code reading.

### Narrative contract

Every core code lesson page should, at minimum, move through these beats:

1. A judgment or thesis for the page
2. Why this snippet matters now
3. A snippet intro
4. Snippet metadata:
   - file location
   - layer / role
   - what this code is for
5. A clear reading guide telling the learner what to look for
6. A short learn list with 2-3 concrete takeaways
7. A code ↔ Chinese explanation pairing
8. An aha / callout moment that states why it matters
9. A "what to revisit when requirements change" note

Do not let a code lesson collapse into just code plus a one-line summary.
The explanation must cover four layers: role, mechanism, meaning, and action.

### Page archetype contract

Use only these archetypes when building pages:

- `opener-page`
- `framing-page`
- `structure-map-page`
- `code-lesson-page`
- `exercise-page`
- `recap-page`

The archetype decides the page's narrative job. The page schema decides which archetype comes next. Do not invent a new shell per project.

### Density contract

- Complex projects may use more pages.
- Simple projects may use fewer pages.
- Every code lesson page still needs enough expansion to teach, not just label.
- Structure pages must explain how files cooperate, not only list them.
- Boundary pages must explain boundary, risk, and next step, not stop at two-sentence summaries.
- Recap pages must end with a useful judgment, not a pile of bullets.
- Exercise pages are part of the teaching rhythm, not decorative extras.

### Interaction contract

- Keep wheel, keyboard, and dot navigation.
- Reveal page content progressively after the page becomes active.
- Quiz states must reflect learning, not just taps.
- Inactive pages stay hidden and non-interactive.

### Term-definition contract

- Treat `.term` + tooltip definitions as a course support layer, not a decorative extra.
- High-value terms should receive explanation entry points when they would otherwise block the learner's reading flow.
- Tooltip copy should answer three things in compact form:
  - what this term is
  - what role it plays in this project
  - why the learner needs it right now
- Do not reduce tooltip copy to a dictionary fragment.
- Do not let tooltip coverage collapse to one or two isolated terms.
- Spread the term-definition layer across the course where it helps:
  - opener: global concepts
  - framing: reading-path concepts
  - structure-map: layer and role words
  - code-lesson: technical blockers in the snippet
  - recap: boundary and capability terms
- Prefer covering terms such as `analysis`, `API route`, `state`, `manifest`, `service worker`, `types`, `FormData`, `JSON body`, and role words like `route`, `report`, `create`, `db` when they are materially relevant.

### Visual contract

- Keep the page feeling editorial and lecture-like, not like a big app card.
- Treat the page number as a leading layer that appears before the page head.
- Keep the page shell present but quiet; the lesson hierarchy should do the visual work.
- Prefer calmer surfaces and lighter elevation over a heavy frosted card shell.
- Let the page breathe between blocks instead of making every block equally heavy.
- Avoid making the whole page feel like one giant white rounded rectangle.

### Block hierarchy contract

- Primary blocks: translation, major lesson blocks, big map blocks, quiz cards.
- Secondary blocks: snippet-intro, meta, summary, panel.
- Tertiary blocks: callout, revisit, helper, feedback notes.
- Do not give every block the same shadow, border, or fill weight.
- Make the primary block read as the anchor of the page.
- Let secondary blocks support the lesson without competing with the anchor.
- Keep tertiary cues visually quieter so the page does not feel like a dashboard.

## What this profile changes

### Reference lock

- Treat [`content-factory-course.html`](/Users/mac/Desktop/content-factory-course.html) as the visual and interaction reference for this profile.
- Match its navigation, page shell, title scale, spacing rhythm, and swipe / wheel / key paging behavior.
- Do **not** replace that shell with a generic cover, bottom menu, or a different page architecture.
- The only thing that should vary per project is the amount of content inside the fixed page roles.
- Treat the reference as the canonical shell and motion source, not as a vague inspiration.
- Treat the reference as the shape of the course system, not as a single-page report design.

### Typography

- Main title should be lecture-scale, not poster-scale.
- Title should read horizontally and naturally, not as a forced vertical stack.
- Page titles should stay horizontally readable; avoid narrow widths that force three-line poster stacks.
- Use a calmer page sheet with a leading page number layer before the headline.
- Keep the hierarchy clear:
  - background page number = faint
  - kicker / auxiliary label = very weak
  - main title = strongest, but still restrained
  - lead / body copy = readable dark gray
- Chinese title rhythm should favor readability over drama:
  - moderate line height
  - controlled weight
  - no forced dense short-line stacking
- Homepage title should follow the lecture-page template:
  - weak kicker above or below the title, not a branded cover banner
  - one thesis-led headline
  - one short lead paragraph
  - no hero-grid, stats-grid, or branded overview shell

### Pagination

- Default to true paged shells with fixed page roles and page schema.
- Long content must not be hard-clipped by a fixed-height outer shell.
- Use an inner scroll area only when a page is genuinely too dense to fit comfortably.
- Page schema drives order; the shell does not invent order.
- Use a near-bottom paging threshold only when a page has its own internal overflow, so users do not get trapped on long pages.
- Keep inactive pages hidden and non-interactive.
- Reset the active section's scrollTop to the top when that section becomes active.

### Elastic density

- Keep the shell fixed and let content density vary with codebase complexity.
- Small codebases should use fewer supporting cards and shorter support copy, not a different page style.
- Larger codebases may deepen a fixed page role with more code↔Chinese blocks or support cards, but must stay inside the same page recipe.
- If a page needs more than one substantial code block plus more than one support block, split it before shipping instead of letting one page become too tall to advance comfortably.
- Never add filler sections just to make a page look full.
- Never invent a branded cover, bottom tab bar, or extra opener because the project is sparse.
- The section count itself is elastic: split dense anchors into more sections when needed, or merge sparse adjacent anchors when that keeps the shell calm and readable.
- Elasticity applies to density and section count, not to the homepage composition or navigation pattern.
- Do not let elastic density turn into a different opener shape.
- Elasticity applies to how much teaching each archetype carries, not to whether the archetype exists.

### Fixed page mapping order

Use this sequence as the canonical teaching path. It defines order, not a mandatory 4-page cap:

1. 先结论
2. 再结构
3. 再数据流
4. 再边界 / 风险 / 下一步

If additional sections are needed, they must deepen one of the four anchors above. They cannot replace the order or introduce a new opening flow. If a single anchor is too dense, split it across more sections instead of compressing it into a cramped block.
Render the profile from an explicit `pageSchema` / `pageDefs` object, not from the natural document flow.
The archetypes may repeat, but opener must stay first and recap must stay last.

### Fixed page recipe

Use the shared page recipe file as the content structure source of truth:

- [`templates/zh-paged-report-course-pages.md`](/Users/mac/.codex/skills/codebase-to-course/templates/zh-paged-report-course-pages.md)

Do not invent a new opener, a new page density pattern, or a new content layout when the profile is active. The opener, structure page, data-flow page, and boundary page each have a fixed role.
The density inside those roles is elastic, but the shell and role order are not.
Use the archetype contract in the recipe file to decide whether a page is an opener, framing page, structure map, code lesson, exercise, or recap.

### Homepage skeleton

Use the reference lecture opener pattern, not a project promo cover:

- weak kicker
- lecture-scale headline
- one short lead paragraph
- keep the opener horizontally readable and calm, not poster-like
- follow the reference composition: main lecture block first, secondary side rail only if it clarifies the thesis
- do not replace that composition with a hero-band, branded overview shell, or bottom menu
- if the project is sparse, shorten the side rail instead of inventing a new opener
- opener should begin with a judgment, not a product blurb

Do not generate:

- brand + topbar overview shells
- hero-grid / stats-grid cover layouts
- "first see results, then structure, then code" style guided cover copy
- any generic cover that feels like a product landing page

### Motion

- Use only a light fade + small translate.
- Keep the transition in the 180ms to 280ms range.
- Avoid flashes, ghosting, layout jumps, scroll bleed, or hard instant swaps.
- Reveal the page's internal content progressively after activation rather than only swapping whole pages.
- Keep quiz feedback calm but readable, so it feels like a checkpoint verdict rather than a toast.

### Page composition

- The home page should feel like the opening of a lesson, not a promotional poster.
- Module pages, code explanation pages, and summary pages should each have distinct roles.
- Organize pages by learning flow and cognitive load, not by raw length.
- Keep the same shell and motion whether a page has one block or several; density may change, but the frame should not.
- Keep the page surface calm and editorial; avoid using a heavy app-card shell to define the course.
- Use term definitions to support the page's teaching role rather than sprinkling random glossary hints.

### Validation

Before treating a profile output as finished, confirm:

1. The longest page is fully readable to the end.
2. Switching pages returns the active page to the top.
3. The first-page title is not too large or poster-like.
4. The kicker is still secondary.
5. The page transition is gentle and readable.
6. The output does not fall back to long-page anchor scrolling.
7. The output does not add filler cards or wrapper sections just to fill empty space.
8. Sparse projects still keep the same shell and typography, only with lighter density.
9. Dense projects may gain more pages, but not a new shell or a different opener.
10. Code lesson pages include thesis, why-now, snippet meta, learn list, explanation pairing, and a revisit note.
11. Quiz pages actually close the loop on understanding rather than acting as decoration.
12. High-value terms receive enough explanation coverage that the learner is not forced to infer key role words alone.
13. Tooltip copy explains project role and timing, not only dictionary meaning.

### Preflight alignment check

Before generating the HTML, first output these four items exactly:

1. `profile:`
2. `首页模板逻辑:`
3. `拆解顺序:`
4. `本次不会再出现的通用提问:`

Only after those four are aligned should generation begin.

## How this profile relates to the base skill

`codebase-to-course` remains the base skill. `zh-paged-report-course` only changes the presentation defaults and validation rules. It does **not** change the underlying course-building workflow, the requirement to read the codebase deeply, or the core teaching arc.
The profile narrows the output into a reusable Chinese code-course format, but the base skill still does the analysis and code understanding work.

## Shared public layers

This profile must resolve to these reusable files:

- `tokens/zh-paged-report-course.css`
- `templates/zh-paged-report-course-shell.html`
- `presets/zh-paged-report-course-motion.css`
- `checklists/zh-paged-report-course.md`

These are the reusable execution layer. The profile is incomplete if it only exists as prose.

The profile also expects the page schema and archetype contract to be explicit in the generated output, so future projects can reuse the same teaching rhythm without manual rewriting.
