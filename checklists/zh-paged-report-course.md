# zh-paged-report-course Checklist

Use this as the execution gate for the profile. Do not generate the report until the preflight passes. Do not ship if any postflight item fails.

## Preflight alignment check

Before generating HTML, confirm these four items exactly:

1. `profile:`
2. `首页模板逻辑:`
3. `拆解顺序:`
4. `本次不会再出现的通用提问:`

If any item is unclear, stop and align it first.

## Required template rules

- [ ] Homepage is a lecture opener, not a branded overview cover
- [ ] Homepage opener follows the reference composition instead of inventing a hero-band
- [ ] No topbar + brand cover shell
- [ ] No hero-grid
- [ ] No stats-grid
- [ ] Fixed page order comes from `pageSchema` / `pageDefs`
- [ ] No free-form page order invention
- [ ] Shell matches the reference course pattern, even if content density is lighter
- [ ] No filler sections or wrapper cards added just to make sparse content look full
- [ ] Opener is first and recap is last
- [ ] Middle pages may expand or contract, but they must stay inside the canonical anchors

## Required page archetype rules

- [ ] Each page maps to one of the allowed archetypes
- [ ] `opener-page` opens with a judgment, not a product blurb
- [ ] `framing-page` explains why this section is being read now
- [ ] `structure-map-page` explains how files cooperate, not just what they are called
- [ ] `code-lesson-page` includes thesis, why-now, snippet intro, snippet meta, learn list, code ↔ Chinese explanation, callout, and revisit note
- [ ] `exercise-page` closes the loop with an active check and teaching feedback
- [ ] `recap-page` ends with judgment, risk, and next step

## Required narration rules

- [ ] Code lesson pages are not just code plus a two-line summary
- [ ] Explanations go beyond "what the line does" into role, mechanism, meaning, and action
- [ ] Each core code page contains at least 3 Chinese explanation beats
- [ ] Each page says what the learner should take away from it
- [ ] Each page gives a later "where to revisit" cue when requirements change
- [ ] Quiz pages actually teach, not just decorate

## Required typography rules

- [ ] The page feels editorial and lecture-like, not like a big app card
- [ ] The page number reads as a leading layer, not as a corner decoration
- [ ] The page shell stays calm and quiet instead of relying on a heavy frosted card for identity
- [ ] Homepage title is lecture-scale, not poster-scale
- [ ] Normal page titles and recap page titles use the same token system
- [ ] Page number is a secondary layer, not a corner stamp
- [ ] Helper / kicker / lead are weaker than the page title
- [ ] Body copy stays readable and does not collapse into a dense memo
- [ ] Line width stays calm enough for Chinese reading rhythm

## Required pagination rules

- [ ] Long sections remain fully readable to the end
- [ ] Downward scrolling continues naturally through the next canonical section
- [ ] Any inner overflow, if present, is short-lived and does not trap the user
- [ ] Inactive sections do not steal focus or interaction
- [ ] Switching to a section that overflows returns it to the top
- [ ] No fallback to a different long-page architecture

## Required interaction rules

- [ ] Page switch uses light fade + small translate
- [ ] Duration stays in the light range
- [ ] No hard cut
- [ ] No large slide
- [ ] No flash, ghosting, layout jump, or scroll bleed
- [ ] Wheel, keyboard, and dot navigation remain available
- [ ] Page content reveals progressively after activation
- [ ] Quiz feedback has a visible state, not only button clicks
- [ ] Quiz options visually read like radio choices
- [ ] Selected / correct / wrong / feedback states are clearly distinguishable
- [ ] Feedback area keeps a stable slot and does not jump the page
- [ ] High-value terms have enough tooltip coverage to support the lesson across the course
- [ ] Tooltip copy explains project role and timing, not only dictionary meaning
- [ ] Term definitions appear across multiple relevant page roles rather than only one isolated page
- [ ] Tooltip click / tap opens reliably instead of immediately closing via event bubbling
- [ ] Terms remain focusable and can reveal definitions through keyboard focus as well as hover

## Required content-order rules

- [ ] Page 1 = 先结论
- [ ] Page 2 = 再结构
- [ ] Page 3 = 再数据流
- [ ] Page 4 = 再边界 / 风险 / 下一步
- [ ] The order is preserved even if the section count grows or shrinks
- [ ] The schema keeps opener first and recap last even when pages are split
- [ ] Section density scales with project complexity without changing the shell
- [ ] Sparse projects keep the same typography and motion instead of inventing extra sections
- [ ] Dense projects split sections instead of overfilling a single one
- [ ] No section is so tall that it needs multiple full viewport scrolls before the next anchor becomes accessible

## Required block hierarchy rules

- [ ] Primary blocks stay visually stronger than support blocks
- [ ] Secondary blocks stay lighter than primary lesson blocks
- [ ] Tertiary cues stay the quietest layer on the page
- [ ] Translation / major lesson / big map / quiz cards carry the primary weight
- [ ] Snippet intro / meta / summary / panel carry the secondary weight
- [ ] Callout / revisit / helper / feedback notes remain tertiary
- [ ] Not every block uses the same shadow or border weight
- [ ] The page avoids turning every block into a white elevated card
- [ ] Accent color stays restrained and does not mix multiple decorative theme colors across blocks

## Failure conditions

If any of the following appears, the run fails:

- generic discovery questions
- wrong homepage shell
- wrong page order
- schema missing page numbers, roles, titles, archetypes, copy, or content nodes
- page order is not driven by `pageSchema` / `pageDefs`
- hard-clipped content
- scrollIntoView-based page switching as the primary mechanism
- filler content created only to fill space
- a different shell invented because the project is small
- code pages that only say what the code does, without why it matters or what to do next
- quiz pages that do not close the loop on understanding
- tooltip coverage that is too thin to support the reading flow
- tooltip copy that only gives dictionary definitions and omits project role
- courses where only one isolated term is explained while other key role words are left bare
- term definitions that appear on only one page and do not form a real course support layer
- tooltip interactions that close immediately when the learner clicks the term itself
