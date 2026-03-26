# zh-paged-report-course Page Recipes

This file defines the canonical page archetypes and the page schema contract for the `zh-paged-report-course` profile.
Do not replace them with a branded cover or a free-form outline.
The shell is fixed; the amount of content inside each archetype is elastic and should scale with codebase complexity, not with a need to "fill" the page.

## Schema contract

Every generated page definition should carry these fields:

- `pageNum` - visible numbering for the page
- `role` - canonical anchor role
- `archetype` - one of the allowed page archetypes below
- `title` - the page headline shown in the UI
- `copy` - the short supporting lead or summary line
- `contentNodes` - the blocks that realize the page

The builder should derive the rendered page stack from this schema. The schema decides order; the shell decides layout.

## Visual contract

- Keep the visual language editorial and lecture-like, not app-card heavy.
- The page number should read as a leading layer before the page head, not as a corner stamp.
- The page shell is a calm sheet; it should not become the main visual hero.
- Pages should breathe between blocks instead of stacking every block at the same weight.
- Primary blocks should feel more substantial; secondary blocks lighter; tertiary cues quieter.
- High-value terms should expose explanations through `.term` + tooltip where they materially support the lesson.
- Tooltip coverage should follow the page's teaching role instead of appearing as random decoration.

## Allowed archetypes

Use only these archetypes when building pages:

- `opener-page`
- `framing-page`
- `structure-map-page`
- `code-lesson-page`
- `exercise-page`
- `recap-page`

These archetypes may repeat. They may be split across more pages if the codebase is dense. They must not invent a new homepage shell.

## Density rules

- Keep the same lecture-page look and motion regardless of project size.
- If the codebase is small, prefer fewer supporting cards, shorter supporting copy, and tighter code blocks.
- If the codebase is large, deepen the same archetypes with more code↔Chinese blocks or support cards, but do not change the page order.
- Never add filler sections, branded covers, or alternative opening shells to compensate for sparse content.
- If a page has only one strong block, that is acceptable as long as the shell, typography, and motion still match the reference.
- Split dense anchors into more pages when needed rather than forcing a single page to hold too many blocks.
- If a page would need sustained internal scrolling to get through multiple strong blocks, split it before shipping so downward paging never feels trapped.
- Merge adjacent anchors only when the result stays calm, readable, and still respects the canonical order.

## Canonical order

The profile follows this teaching path:

1. 先结论
2. 再结构
3. 再数据流
4. 再边界 / 风险 / 下一步

This is an order, not a hard 4-page cap.
Opener must stay first and recap must stay last.

## Archetype contracts

### `opener-page`

Purpose: tell the learner what the project is, why it matters, and what kind of system they are looking at.

Required structure:

- weak kicker
- lecture-scale headline
- short lead paragraph
- thesis-first opening line
- a secondary side rail only if it clarifies the thesis
- no branded overview shell

Allowed content:

- one-line project conclusion
- the two-system split if relevant
- a very short "what you will learn" bridge
- one weak auxiliary note after the lead
- a compact support band that previews the learning path
- 1-3 global concept tooltips for terms that will block the rest of the course if left unexplained

Forbidden content:

- topbar + brand cover
- hero-grid
- stats-grid
- project overview landing page language
- long lists of features
- extra wrapper sections whose only job is to make the page feel full

### `framing-page`

Purpose: frame the current lesson before the code dive.

Required structure:

- one short thesis or transition
- one short why-now explanation
- one compact guidance block

Allowed content:

- roadmap hints
- short reading guidance
- a small callout that reduces confusion
- tooltip definitions for reading-path concepts or section-role words

Forbidden content:

- long code walkthroughs
- extra code blocks
- filler cards that only pad space

### `structure-map-page`

Purpose: explain file roles, route roles, component roles, and how the code is divided.

Required structure:

- directory tree or route map
- one code ↔ Chinese explanation block
- one short "why this structure matters" callout

Allowed content:

- file tree
- route map
- type layer explanation
- layout / data / API separation
- tooltip definitions for role words such as `route`, `report`, `create`, `db`, `types`

Elastic slots:

- one additional compact support block if the codebase has many related roles
- a second code block only when the structure truly needs a second layer

Visual guidance:

- Prefer a responsibility map over a raw file list.
- Show how layers hand off to each other and why the next lesson page can keep the story moving.
- Use tooltip definitions on key role labels when they help a beginner understand the handoff chain.

### `code-lesson-page`

Purpose: teach one core code path in enough depth that the learner can use it when steering AI later.

Required structure:

- page thesis / judgment
- why this snippet matters now
- snippet intro
- snippet metadata:
  - file location
  - layer / role
  - what this code is for
- reading guide
- learn list with 2-3 concrete takeaways
- code ↔ Chinese explanation pairing
- one aha / callout moment
- one "revisit this when requirements change" note

Allowed content:

- parse / normalize / update / render chains
- API route or data pipeline examples
- database / local storage flow
- one quiz if it helps the lesson land
- tooltip definitions for technical blockers in the snippet, such as `state`, `API route`, `FormData`, `JSON body`, `service worker`, or equivalent project terms

Rules:

- Do not let a code lesson collapse into code plus one general summary line.
- Explain the code in four layers: role, mechanism, meaning, and action.
- Prefer snippet metadata as a compact tag row or pill row, not one undifferentiated sentence.
- Code blocks should show internal hierarchy clearly through syntax color and structural grouping so the learner can spot functions, strings, branching, and returned shape at a glance.
- Each explanation block should move beyond "this line does this" into "why this matters, how to change it, and what to look for later."
- Prefer row-based explanation beats (`exp-line`) when the page needs a stronger teacher-led cadence.
- Let the explanation side carry visible segment labels or step labels so the learner can feel the reading rhythm.
- Separate explanation beats with clear breathing room instead of letting them read like a single paragraph dump.
- Use the explanation side to pace the lesson, not just to restate the code.
- Tooltip copy should explain what the term is, what role it plays in this project, and why the learner needs it now.
- The code side and explanation side should feel logically paired: left side = structured source, right side = segmented guided reading.

### `exercise-page`

Purpose: close the loop on understanding with an active check.

Required structure:

- one question or scenario
- 2-4 answer options or a short task
- immediate feedback state
- a short learning takeaway

Allowed content:

- multiple-choice quiz
- spot-the-bug task
- scenario-based prompt
- a small number of tooltip definitions when a term is central to the judgment being checked

Rules:

- The exercise is part of the teaching rhythm, not a decorative extra.
- The feedback must say what the learner should remember next.
- The quiz should feel like a checkpoint with visible option states and a stable feedback area.
- The page should feel like a learning checkpoint, not a generic control panel.

### `recap-page`

Purpose: explain what is already working, what is still a boundary, and what should happen next.

Required structure:

- one boundary example or equivalent final code block
- one summary section for current strengths
- one summary section for current risks
- one next-step callout
- one closing quiz or recap check

Allowed content:

- persistence boundary
- mock vs real split
- tooltip definitions for boundary words, capability terms, and extension points
- scaling risk
- sync / collaboration next steps

Rules:

- Recap must end with a useful judgment, not a pile of bullets.
- If the project is small, keep the recap concise rather than manufacturing extra depth.
- The recap should read like a final verdict page: strengths, risks, and next step in an editorial summary rhythm.
- The summary area should feel lighter than a dashboard summary card.

## Page composition rules

- One page = one core expression.
- If a page needs more room, deepen that page, do not invent a new opener.
- If a page already changes topic, start the next canonical page.
- Keep the opener visually calm and horizontally readable.
