# zh-codebase-to-course

A Codex skill package for Chinese-first, paged code courses built on the `codebase-to-course` base skill.

Point it at a repo. Get back a stunning, self-contained course that teaches how the code works — with scroll-based navigation, animated visualizations, embedded quizzes, and Chinese explanations that keep key English terms intact.

## Who is this for?

**"Vibe coders"** — people who build software by instructing AI coding tools in natural language, without a traditional CS education.

You've built something (or found something cool on GitHub). It works. But you don't really understand *how* it works under the hood. This skill generates a course that teaches you — not by lecturing, but by tracing what happens when you actually use the app.

**Your goals are practical, not academic:**
- Steer AI coding tools better (make smarter architectural decisions)
- Detect when AI is wrong (spot hallucinations, catch bad patterns)
- Debug when AI gets stuck (break out of bug loops)
- Talk to engineers without feeling lost

You're not trying to become a software engineer. You want coding as a superpower.

## What the course looks like

The output is a **single HTML file** — no dependencies, no setup, works offline. It includes:

- **Scroll-based modules** with progress tracking and keyboard navigation
- **Code ↔ 中文 explanations** — real code on the left, what it means in Chinese on the right, with key English terms preserved
<img width="720" alt="Code translation block" src="https://github.com/user-attachments/assets/fb9e7fac-05c1-4f98-b80c-46543ef81afc" />

- **Animated visualizations** — data flow animations, group chat between components, architecture diagrams
<img width="720" alt="Animated data flow" src="https://github.com/user-attachments/assets/20fb403e-7dfd-4a47-989b-bbae86ca8041" />

- **Interactive quizzes** that test *application* not memorization ("You want to add favorites — which files change?")
<img width="720" alt="Interactive quiz" src="https://github.com/user-attachments/assets/57706496-9fa8-457a-8450-3da22789951c" />

- **Glossary tooltips** — hover any technical term for a Chinese definition, with the original English term kept when useful
<img width="720" alt="Glossary tooltip" src="https://github.com/user-attachments/assets/ac2f160a-d73f-4779-97b2-a06fdb5f3227" />

  
- **Warm, distinctive design** — not the typical purple-gradient AI look

## How to use

### As a Codex skill

1. Copy the `zh-codebase-to-course` folder into `~/.codex/skills/`
2. Open any project in Codex
3. Say one of these:
   - *"Turn this codebase into an interactive course"*
   - *"Use codebase-to-course on this repo"*
   - *"Make this project into a course"*
   - *"Explain this codebase interactively"*

If you're already inside the project you want to teach, you can also just say:
*"Turn this into a course."*

### Profiles

The base skill stays the base. If you want the Chinese paged code-course presentation layer that was tuned in this session, activate the **`zh-paged-report-course`** profile explicitly.

This profile is a **forced template**, not just a visual preference. When it is active, the workflow skips generic style-discovery questions and uses the fixed Chinese code-course structure instead.
The profile is backed by shared public-layer files under `tokens/`, `templates/`, `presets/`, `checklists/`, and `references/`.
The shell stays fixed while content density can expand or shrink with the codebase; sparse projects should stay calm and lighter, not grow filler sections.
The page schema is explicit, so the generator knows whether it is rendering an opener, framing page, structure map, code lesson, exercise, or recap.

Use it when you want:

- Chinese-first code-course pages instead of poster-like English presentation pages
- True pagination with page-internal scrolling for long content
- Light fade + small translate page transitions
- Lecture-scale title hierarchy and weak auxiliary kicker text
- A fixed teaching path: conclusion -> structure -> data flow -> boundary / risk / next step
- A homepage that opens like a lecture page, not a branded project cover
- An execution contract that includes thesis-first lessons, snippet metadata, learn lists, and exercise pages

Trigger examples:

- "Use zh-paged-report-course"
- "Make this a Chinese paged code course"
- "Use the Chinese paged report template"
- "Turn this into a paged report course"
- "Use the strict Chinese paged report profile"

### Trigger phrases

- "Turn this into a course"
- "Use codebase-to-course on this repo"
- "Make this project into a course"
- "Explain this codebase interactively"
- "Teach me how this code works"
- "Interactive tutorial from this code"
- "Generate a course from this codebase"

## Design philosophy

### Build first, understand later

This inverts traditional CS education. The old way: memorize concepts for years → eventually build something → finally see the point (most people quit before step 3). This way: **build something → experience it working → now understand how it works.**

### Show, don't tell

Every screen is at least 50% visual. Max 2-3 sentences per text block. If something can be a diagram, animation, or interactive element — it shouldn't be a paragraph. Write the course body in Chinese by default, but keep important English technical terms alongside the Chinese explanation.

### Quizzes test doing, not knowing

No "What does API stand for?" Instead: "A user reports stale data after switching pages. Where would you look first?" Quizzes should be written in Chinese, while preserving technical terms like `API`, `DOM`, or `callback` when they matter for accuracy. The goal is to test whether you can *use* what you learned to solve a new problem.

### No recycled metaphors

Each concept gets a metaphor that fits *that specific idea*. A database is a library with a card catalog. Auth is a bouncer checking IDs. API rate limiting is a nightclub with a capacity limit. Never the same metaphor twice.

### Original code only

Code snippets are exact copies from the real codebase — never modified or simplified. The learner should be able to open the actual file and see the same code they learned from.

## Skill structure

```
zh-codebase-to-course/
├── SKILL.md                          # Main skill instructions
├── README.md                         # User-facing usage guide
├── tokens/
│   └── zh-paged-report-course.css    # Shared token layer for the profile
├── templates/
│   ├── zh-paged-report-course-shell.html  # Shared page shell / builder scaffold
│   └── zh-paged-report-course-pages.md    # Shared page recipe for the elastic page flow
├── presets/
│   └── zh-paged-report-course-motion.css  # Shared motion preset
├── checklists/
│   └── zh-paged-report-course.md     # Shared preflight / QA gate
└── references/
    ├── design-system.md              # CSS tokens, typography, colors, layout
    └── interactive-elements.md       # Quiz, animation, and visualization patterns
└── profiles/
    └── zh-paged-report-course.md     # Chinese paged code course profile
```

### Profile preflight

When the `zh-paged-report-course` profile is active, the generator should confirm these four items before writing the HTML:

1. `profile:`
2. `首页模板逻辑:`
3. `拆解顺序:`
4. `本次不会再出现的通用提问:`

If these do not line up, correct them first. Do not fall back to generic discovery questions.

The page count is elastic: the same four anchors stay in order, but dense codebases may split anchors across more pages and sparse codebases may merge adjacent anchors if the shell stays calm and readable.
The generated pages should map to a fixed archetype vocabulary (`opener-page`, `framing-page`, `structure-map-page`, `code-lesson-page`, `exercise-page`, `recap-page`) rather than inventing a new shell per project.


---

Built by [Zara](https://x.com/zarazhangrui).
