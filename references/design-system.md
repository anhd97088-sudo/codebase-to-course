# Design System Reference

Complete CSS design tokens for the course. Copy this entire `:root` block into the course HTML and adapt the accent color to suit the project's personality.

## Table of Contents
1. [Color Palette](#color-palette)
2. [Typography](#typography)
3. [Spacing & Layout](#spacing--layout)
4. [Shadows & Depth](#shadows--depth)
5. [Animations & Transitions](#animations--transitions)
6. [Navigation & Progress](#navigation--progress)
7. [Module Structure](#module-structure)
8. [Responsive Breakpoints](#responsive-breakpoints)
9. [Scrollbar & Background](#scrollbar--background)

---

## Color Palette

```css
:root {
  /* --- BACKGROUNDS --- */
  --color-bg:             #FAF7F2;       /* warm off-white, like aged paper */
  --color-bg-warm:        #F5F0E8;       /* slightly warmer for alternating modules */
  --color-bg-code:        #1E1E2E;       /* deep indigo-charcoal for code blocks */
  --color-text:           #2C2A28;       /* dark charcoal, easy on eyes */
  --color-text-secondary: #6B6560;       /* warm gray for secondary text */
  --color-text-muted:     #9E9790;       /* muted for timestamps, labels */
  --color-border:         #E5DFD6;       /* subtle warm border */
  --color-border-light:   #EEEBE5;       /* even lighter border */
  --color-surface:        #FFFFFF;       /* card surfaces */
  --color-surface-warm:   #FDF9F3;       /* warm card surface */

  /* --- ACCENT (adapt per project — pick ONE bold color) ---
     Default: vermillion. Alternatives: coral (#E06B56), teal (#2A7B9B),
     amber (#D4A843), forest (#2D8B55). Avoid purple gradients. */
  --color-accent:         #D94F30;
  --color-accent-hover:   #C4432A;
  --color-accent-light:   #FDEEE9;
  --color-accent-muted:   #E8836C;

  /* --- SEMANTIC --- */
  --color-success:        #2D8B55;
  --color-success-light:  #E8F5EE;
  --color-error:          #C93B3B;
  --color-error-light:    #FDE8E8;
  --color-info:           #2A7B9B;
  --color-info-light:     #E4F2F7;

  /* --- ACTOR COLORS (assign to main components) ---
     Each major "character" in the codebase gets a distinct color
     for chat bubbles, diagrams, and highlights */
  --color-actor-1:        #D94F30;       /* vermillion */
  --color-actor-2:        #2A7B9B;       /* teal */
  --color-actor-3:        #7B6DAA;       /* muted plum */
  --color-actor-4:        #D4A843;       /* golden */
  --color-actor-5:        #2D8B55;       /* forest */
}
```

**Rules:**
- Even-numbered modules use `--color-bg`, odd-numbered use `--color-bg-warm` (alternating backgrounds create visual rhythm)
- Actor colors should be visually distinct from each other and from the accent
- Code blocks always use `--color-bg-code` with light text
- Lecture-style page titles should remain horizontally readable: widen the title area before forcing extra line breaks, and keep titles restrained enough that they do not become poster stacks.

---

## Typography

```css
:root {
  /* --- FONTS ---
     Display: bold, geometric, personality-driven. NOT Inter/Roboto/Arial.
     Body: readable with character. NOT system fonts.
     Mono: developer-friendly with clear character distinction. */
  --font-display:  'Bricolage Grotesque', Georgia, serif;
  --font-body:     'DM Sans', -apple-system, sans-serif;
  --font-mono:     'JetBrains Mono', 'Fira Code', 'Consolas', monospace;

  /* --- TYPE SCALE (1.25 ratio) --- */
  --text-xs:   0.75rem;    /* 12px — labels, badges */
  --text-sm:   0.875rem;   /* 14px — secondary text, code */
  --text-base: 1rem;       /* 16px — body text */
  --text-lg:   1.125rem;   /* 18px — lead paragraphs */
  --text-xl:   1.25rem;    /* 20px — screen headings */
  --text-2xl:  1.5rem;     /* 24px — sub-module titles */
  --text-3xl:  1.875rem;   /* 30px — module subtitles */
  --text-4xl:  2.25rem;    /* 36px — module titles */
  --text-5xl:  3rem;       /* 48px — hero text */
  --text-6xl:  3.75rem;    /* 60px — module numbers */

  /* --- LINE HEIGHTS --- */
  --leading-tight:  1.15;  /* headings */
  --leading-snug:   1.3;   /* subheadings */
  --leading-normal: 1.6;   /* body text */
  --leading-loose:  1.8;   /* relaxed reading */
}
```

**Google Fonts link (put in `<head>`):**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,400;12..96,600;12..96,700;12..96,800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,400;1,9..40,500&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

**Rules:**
- Module numbers: `--text-6xl`, font-display, weight 800, `--color-accent` with 15% opacity
- Module titles: `--text-4xl`, font-display, weight 700
- Screen headings: `--text-xl` or `--text-2xl`, font-display, weight 600
- Body text: `--text-base` or `--text-lg`, font-body, `--leading-normal`
- Code: `--text-sm`, font-mono
- Labels/badges: `--text-xs`, font-mono, uppercase, letter-spacing 0.05em

## Profile Override: `zh-paged-report-course`

The Chinese paged code course should feel like an editorial lesson sheet, not a glossy app card.
Keep the main page calm and light, with the page number as a leading layer before the page head.
The page shell should be present but quiet; the lesson hierarchy should do the visual work.

### Editorial page contract

- Use a calm sheet surface rather than a heavy frosted app card.
- Treat the page number as a separate leading layer, not as a decorative corner stamp.
- Keep the page head, page body, and feedback area visually distinct.
- Make the main lesson block feel stable and readable, not over-elevated.
- Let the support blocks be lighter than the core lesson block.

### Token guidance

- `--zh-course-page-sheet-surface` should stay soft and translucent, not opaque and heavy.
- `--zh-course-page-card-shadow` should be minimal or none; the page should not rely on deep shadow for identity.
- `--zh-course-page-leading-gap` should create air between the number layer and the page head.
- `--zh-course-page-number-size` should remain a clear leading element, but the color should stay faint.
- `--zh-course-block-primary-*` should be reserved for translation, major lesson blocks, big maps, and quiz cards.
- `--zh-course-block-secondary-*` should be used for meta, snippet intro, summary, and mid-weight support panels.
- `--zh-course-block-tertiary-*` should be used for callout, revisit, helper, and feedback notes.
- `meta-box` should prefer a compact tag row or pill row so file location, layer, and purpose read as three separate ideas instead of one long sentence.
- Code blocks should expose internal logic with restrained syntax color, not as flat monochrome text.
- Explanation rows (`exp-line`) should visibly segment the reading so the code side and explanation side feel paired.
- The accent system should stay mostly blue; green should only appear where semantic success or boundary state is truly needed.
- Avoid decorative gradients that make helper or callout blocks feel like a separate visual theme.
- `.term` should feel like a lightweight reading aid: subtle underline, a clear deep-blue text treatment, and tooltip tone that supports the lesson without stealing the page.

---

## Spacing & Layout

```css
:root {
  --space-1:  0.25rem;   /* 4px */
  --space-2:  0.5rem;    /* 8px */
  --space-3:  0.75rem;   /* 12px */
  --space-4:  1rem;      /* 16px */
  --space-5:  1.25rem;   /* 20px */
  --space-6:  1.5rem;    /* 24px */
  --space-8:  2rem;      /* 32px */
  --space-10: 2.5rem;    /* 40px */
  --space-12: 3rem;      /* 48px */
  --space-16: 4rem;      /* 64px */
  --space-20: 5rem;      /* 80px */
  --space-24: 6rem;      /* 96px */

  --content-width:     800px;   /* standard reading width */
  --content-width-wide: 1000px; /* for side-by-side layouts */
  --nav-height:        50px;
  --radius-sm:  8px;
  --radius-md:  12px;
  --radius-lg:  16px;
  --radius-full: 9999px;
}
```

**Module layout:**
```css
.module {
  min-height: 100dvh;       /* fallback: 100vh */
  scroll-snap-align: start;
  padding: var(--space-16) var(--space-6);
  padding-top: calc(var(--nav-height) + var(--space-12));
}
.module-content {
  max-width: var(--content-width);
  margin: 0 auto;
}
```

---

## Shadows & Depth

```css
:root {
  --shadow-sm:  0 1px 2px rgba(44, 42, 40, 0.05);
  --shadow-md:  0 4px 12px rgba(44, 42, 40, 0.08);
  --shadow-lg:  0 8px 24px rgba(44, 42, 40, 0.1);
  --shadow-xl:  0 16px 48px rgba(44, 42, 40, 0.12);
}
```

Use warm-tinted RGBA (44, 42, 40) — never pure black shadows.

---

## Animations & Transitions

```css
:root {
  --ease-out:    cubic-bezier(0.16, 1, 0.3, 1);
  --ease-in-out: cubic-bezier(0.65, 0, 0.35, 1);
  --duration-fast:   150ms;
  --duration-normal: 300ms;
  --duration-slow:   500ms;
  --stagger-delay:   120ms;
}
```

**Scroll-triggered reveal pattern:**
```css
.animate-in {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity var(--duration-slow) var(--ease-out),
              transform var(--duration-slow) var(--ease-out);
}
.animate-in.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger children */
.stagger-children > .animate-in {
  transition-delay: calc(var(--stagger-index, 0) * var(--stagger-delay));
}
```

**JS setup for stagger:**
```javascript
document.querySelectorAll('.stagger-children').forEach(parent => {
  Array.from(parent.children).forEach((child, i) => {
    child.style.setProperty('--stagger-index', i);
  });
});
```

**Intersection Observer (trigger reveals):**
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      observer.unobserve(entry.target); // animate only once
    }
  });
}, { rootMargin: '0px 0px -10% 0px', threshold: 0.1 });

document.querySelectorAll('.animate-in').forEach(el => observer.observe(el));
```

---

## Navigation & Progress

**HTML structure:**
```html
<nav class="nav">
  <div class="progress-bar" role="progressbar" aria-valuenow="0"></div>
  <div class="nav-inner">
    <span class="nav-title">Course Title</span>
    <div class="nav-dots">
      <button class="nav-dot" data-target="module-1" data-tooltip="Module 1 Name"
              role="tab" aria-label="Module 1"></button>
      <!-- one per module -->
    </div>
  </div>
</nav>
```

**Progress bar (CSS-only where possible, JS fallback):**
```javascript
function updateProgressBar() {
  const scrollTop = window.scrollY;
  const scrollHeight = document.documentElement.scrollHeight - window.innerHeight;
  const progress = (scrollTop / scrollHeight) * 100;
  progressBar.style.width = progress + '%';
}
window.addEventListener('scroll', () => {
  requestAnimationFrame(updateProgressBar);
}, { passive: true });
```

**Nav dot states:**
- Default: `border: 2px solid var(--color-text-muted)`, empty center
- Current: `border-color: var(--color-accent)`, filled center, subtle glow shadow
- Visited: `background: var(--color-accent)`, filled solid

**Keyboard navigation:**
```javascript
document.addEventListener('keydown', (e) => {
  if (['INPUT', 'TEXTAREA'].includes(e.target.tagName)) return;
  if (e.key === 'ArrowDown' || e.key === 'ArrowRight') { nextModule(); e.preventDefault(); }
  if (e.key === 'ArrowUp' || e.key === 'ArrowLeft') { prevModule(); e.preventDefault(); }
});
```

---

## Module Structure

**HTML template for each module:**
```html
<section class="module" id="module-N" style="background: var(--color-bg or --color-bg-warm)">
  <div class="module-content">
    <header class="module-header animate-in">
      <span class="module-number">0N</span>
      <h1 class="module-title">Module Title</h1>
      <p class="module-subtitle">One-line description of what this module teaches</p>
    </header>

    <div class="module-body">
      <section class="screen animate-in">
        <h2 class="screen-heading">Screen Title</h2>
        <p>Content...</p>
        <!-- Interactive elements, code translations, etc. -->
      </section>

      <section class="screen animate-in">
        <!-- Next screen -->
      </section>
    </div>
  </div>
</section>
```

---

## Responsive Breakpoints

```css
/* Tablet */
@media (max-width: 768px) {
  :root {
    --text-4xl: 1.875rem;
    --text-5xl: 2.25rem;
    --text-6xl: 3rem;
  }
  .translation-block { grid-template-columns: 1fr; } /* stack code/english */
  .pattern-cards { grid-template-columns: 1fr 1fr; }
}

/* Mobile */
@media (max-width: 480px) {
  :root {
    --text-4xl: 1.5rem;
    --text-5xl: 1.875rem;
    --text-6xl: 2.25rem;
  }
  .module { padding: var(--space-8) var(--space-4); }
  .pattern-cards { grid-template-columns: 1fr; }
  .flow-steps { flex-direction: column; }
  .flow-arrow { transform: rotate(90deg); }
}
```

---

## Scrollbar & Background

```css
/* Custom scrollbar */
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb {
  background: var(--color-border);
  border-radius: var(--radius-full);
}

/* Subtle atmospheric background */
body {
  background: var(--color-bg);
  background-image: radial-gradient(
    ellipse at 20% 50%,
    rgba(217, 79, 48, 0.03) 0%,
    transparent 50%
  );
}

/* Page scroll setup */
html {
  scroll-snap-type: y proximity;
  scroll-behavior: smooth;
}
```

---

## Code Block Globals

All code blocks in the course — whether inside translation blocks, standalone snippets, or quiz challenges — must wrap text and never show a horizontal scrollbar. This is a teaching tool, not an IDE.

```css
pre, code {
  white-space: pre-wrap;       /* wrap long lines */
  word-break: break-word;      /* break mid-word if absolutely needed */
  overflow-x: hidden;          /* no horizontal scrollbar — ever */
}
/* Hide scrollbars on code containers */
.translation-code::-webkit-scrollbar,
pre::-webkit-scrollbar {
  display: none;
}
```

Code snippets must be **exact copies** from the real codebase — never modified, trimmed, or simplified. Instead, choose naturally short (5-10 line) sections from the code that illustrate the concept well. If a longer block is needed, show it all — the wrapping CSS will handle readability.

---

## Syntax Highlighting (Catppuccin-inspired)

For code blocks on the dark `--color-bg-code` background:

```css
.code-keyword  { color: #CBA6F7; }  /* purple — if, else, return, function */
.code-string   { color: #A6E3A1; }  /* green — "strings" */
.code-function { color: #89B4FA; }  /* blue — function names */
.code-comment  { color: #6C7086; }  /* muted gray — // comments */
.code-number   { color: #FAB387; }  /* peach — numbers */
.code-property { color: #F9E2AF; }  /* yellow — object keys */
.code-operator { color: #94E2D5; }  /* teal — =, =>, +, etc. */
.code-tag      { color: #F38BA8; }  /* pink — HTML tags */
.code-attr     { color: #F9E2AF; }  /* yellow — HTML attributes */
.code-value    { color: #A6E3A1; }  /* green — attribute values */
```

---

## Profile Override: `zh-paged-report-course`

Use this override when the output should feel like a **Chinese paged code course**, not a poster-like English demo page or a one-off paged report.

### Typography contract

```css
:root {
  /* Chinese-first lecture pages */
  --font-display: 'SF Pro Display', 'PingFang SC', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-body:    'SF Pro Text', 'PingFang SC', -apple-system, BlinkMacSystemFont, sans-serif;

  /* Lecture-scale title stack */
  --zh-course-hero-title-size:   clamp(26px, 2.8vw, 34px);
  --zh-course-hero-title-line:   1.16;
  --zh-course-hero-title-weight: 560;
  --zh-course-hero-title-width:   16ch;

  --zh-course-page-title-size:    clamp(22px, 2.8vw, 34px);
  --zh-course-page-title-line:    1.12;
  --zh-course-page-title-weight:  620;
  --zh-course-page-title-width:    22ch;

  --zh-course-body-size:          16px;
  --zh-course-body-line:          1.68;
  --zh-course-body-weight:        400;
  --zh-course-body-color:         rgba(29, 29, 31, 0.68);
  --zh-course-body-width:         52ch;

  --zh-course-lead-size:          17px;
  --zh-course-lead-line:          1.72;
  --zh-course-lead-weight:        400;
  --zh-course-lead-color:         rgba(29, 29, 31, 0.72);
  --zh-course-lead-width:         52ch;

  --zh-course-helper-size:        10px;
  --zh-course-helper-line:        1.45;
  --zh-course-helper-weight:      600;
  --zh-course-helper-color:       rgba(29, 29, 31, 0.34);
  --zh-course-helper-width:       38ch;

  --zh-course-snippet-intro-size: 17px;
  --zh-course-snippet-intro-line: 1.68;
  --zh-course-snippet-intro-weight: 400;
  --zh-course-snippet-intro-color: rgba(29, 29, 31, 0.72);
  --zh-course-snippet-intro-width: 54ch;

  --zh-course-snippet-meta-size: 11px;
  --zh-course-snippet-meta-line: 1.45;
  --zh-course-snippet-meta-weight: 600;
  --zh-course-snippet-meta-color: rgba(29, 29, 31, 0.48);

  --zh-course-callout-title-size: 18px;
  --zh-course-callout-title-line: 1.18;
  --zh-course-callout-title-weight: 650;
  --zh-course-callout-title-color: rgba(29, 29, 31, 0.88);

  --zh-course-callout-body-size: 15px;
  --zh-course-callout-body-line: 1.62;
  --zh-course-callout-body-weight: 400;
  --zh-course-callout-body-color: rgba(29, 29, 31, 0.68);

  --zh-course-learn-list-size: 15px;
  --zh-course-learn-list-line: 1.62;
  --zh-course-learn-list-weight: 400;
  --zh-course-learn-list-color: rgba(29, 29, 31, 0.70);

  --zh-course-exp-line-size:      14px;
  --zh-course-exp-line-height:    1.56;
  --zh-course-exp-line-color:     rgba(29, 29, 31, 0.64);
  --zh-course-exp-line-width:     50ch;

  --zh-course-page-number-size:   clamp(34px, 4vw, 56px);
  --zh-course-page-number-weight: 700;
  --zh-course-page-number-color:  rgba(29, 29, 31, 0.10);
}
```

**Typography rules:**
- Title width should be generous enough to read horizontally; avoid forcing many short lines.
- Main title should feel like a lecture headline, not a poster headline.
- Page title, homepage title, and recap title should share the same hierarchy system; only their role changes.
- Page number is decorative and faint, never the main read.
- Kicker / auxiliary label stays weak and secondary.
- Lead and body copy should feel like course prose, not memo text.
- Explain the page with balanced line lengths, not with a dense document column.

### Pagination contract

```css
.course-pages {
  height: calc(100dvh - var(--nav-h));
  overflow: hidden;
}

.course-page {
  position: absolute;
  inset: 0;
  opacity: 0;
  visibility: hidden;
  pointer-events: none;
  transform: translateY(10px);
  transition:
    opacity 220ms ease,
    transform 220ms ease,
    visibility 0s linear 220ms;
}

.course-page.active {
  opacity: 1;
  visibility: visible;
  pointer-events: auto;
  transform: translateY(0);
}

.page-inner {
  height: 100%;
  overflow: auto;
  overscroll-behavior: contain;
}
```

**Rules:**
- Default to page-based navigation, not long-page anchor scrolling.
- Let long pages scroll inside the active page only.
- Reset the active page's internal scroll to top on every page switch.
- Do not let inactive pages remain scrollable or clickable.
- The shell must stay fixed even when page density changes.

### Narrative contract

The profile should read like a **Chinese paged code course**:

- opener first, recap last
- judgments before details
- code lesson pages explain why now before what the code does
- every serious code page includes snippet intro, metadata, learn list, explanation pairing, callout, and revisit cue
- exercise pages close the loop and turn explanation into memory
- recap pages end with a useful judgment, not a pile of bullets

### Motion contract

```css
.course-page {
  transition:
    opacity 220ms ease,
    transform 220ms ease;
}
```

**Rules:**
- Use light fade + small translate only.
- Keep the transition in the 180ms to 280ms range.
- Never add flash, ghosting, layout jump, or scroll-through behavior.
- Reveal page content progressively after activation rather than only swapping whole pages.

### Validation contract

Use this checklist for the profile before shipping:

1. Longest page is fully readable to the end.
2. Switching pages resets the inner scroll to the top.
3. First-page title reads horizontally and does not feel poster-like.
4. Auxiliary kicker stays weak and secondary.
5. Page transitions feel gentle, not abrupt.
6. The course never falls back to long-page anchor scrolling.
7. Code lesson pages contain thesis, why-now, snippet meta, learn list, explanation pairing, and revisit cue.
8. Quiz pages close the loop on understanding instead of acting as decoration.

### Homepage skeleton contract

For the `zh-paged-report-course` profile, keep the homepage in lecture-page form:

- weak kicker
- lecture-scale headline
- short lead paragraph
- optional secondary side rail if it clarifies the opening thesis
- no branded overview shell
- no hero-grid / stats-grid cover layout

This is a presentation rule, not a content rule: the page still teaches the codebase, but it opens like a lecture instead of a promo page.

### Public layer files

For the `zh-paged-report-course` profile, these files are the reusable source of truth:

- [`tokens/zh-paged-report-course.css`](/Users/mac/.codex/skills/codebase-to-course/tokens/zh-paged-report-course.css)
- [`templates/zh-paged-report-course-shell.html`](/Users/mac/.codex/skills/codebase-to-course/templates/zh-paged-report-course-shell.html)
- [`templates/zh-paged-report-course-pages.md`](/Users/mac/.codex/skills/codebase-to-course/templates/zh-paged-report-course-pages.md)
- [`presets/zh-paged-report-course-motion.css`](/Users/mac/.codex/skills/codebase-to-course/presets/zh-paged-report-course-motion.css)
- [`checklists/zh-paged-report-course.md`](/Users/mac/.codex/skills/codebase-to-course/checklists/zh-paged-report-course.md)

The profile should reference these instead of inventing new typography, shell, page recipe, or motion values per project.
The visual shell is fixed to the reference course; only the content density may scale up or down with project complexity.
The opener may grow a compact supporting band, but it should still read as a lecture opener rather than a promo cover.
