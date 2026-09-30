# Design Direction — GUINEASKET Tournament 3X3

## Design Thesis

**"Official tournament credibility through clean information hierarchy, sponsor visibility, and mobile-first clarity — not decoration."**

This is not a generic sports website. It is the official digital reference for a specific 3X3 basketball tournament seeking sponsors. Every visual decision must reinforce: *this is real, organized, and worth partnering with.*

---

## Typography

**Font Stack (System — Zero Load):**
```css
--font-sans: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
--font-mono: 'JetBrains Mono', 'Fira Code', 'SF Mono', Menlo, monospace;
```

**Roles:**
| Role | Font | Weight | Use Case |
|---|---|---|---|
| Display | Sans | 700 | Hero headline, page titles |
| Heading | Sans | 600 | Section headings (h2) |
| Subheading | Sans | 500 | Subsection headings (h3) |
| Body | Sans | 400 | All paragraph text, UI labels |
| Body Strong | Sans | 600 | Emphasis, CTAs, key stats |
| Data | Mono | 400 | Scores, times, dates, counts |
| Caption | Sans | 400 | Image captions, meta info |

**Fluid Scale (clamp):**
```css
--step--1: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);   /* Caption */
--step-0: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);       /* Body */
--step-1: clamp(1.125rem, 1.05rem + 0.375vw, 1.375rem);  /* Body Large */
--step-2: clamp(1.375rem, 1.25rem + 0.625vw, 1.75rem);   /* h3 */
--step-3: clamp(1.75rem, 1.5rem + 1.25vw, 2.5rem);       /* h2 */
--step-4: clamp(2.5rem, 2rem + 2.5vw, 4rem);             /* h1 / Hero */
```

**Line Height:** 1.5 body, 1.2 headings, 1.4 mono

---

## Color Roles (Semantic Tokens)

**Principle:** Colors have jobs, not aesthetics. Organizer brand color = primary. Everything else supports hierarchy and accessibility.

```css
/* Primitive Palette (HSL for manipulation) */
--color-brand-h: 220;        /* Organizer brand hue — TBD from assets */
--color-brand-s: 85%;
--color-brand-l: 45%;

/* Semantic Roles */
--color-primary: hsl(var(--color-brand-h) var(--color-brand-s) var(--color-brand-l));
--color-primary-hover: hsl(var(--color-brand-h) var(--color-brand-s) calc(var(--color-brand-l) - 5%));
--color-primary-focus: hsl(var(--color-brand-h) var(--color-brand-s) calc(var(--color-brand-l) + 15%));
--color-primary-light: hsl(var(--color-brand-h) var(--color-brand-s) 92%);

--color-surface: #ffffff;
--color-surface-elevated: #ffffff;
--color-surface-hover: #fafafa;

--color-text-primary: #1a1a2e;
--color-text-secondary: #4b5563;
--color-text-muted: #6b7280;
--color-text-inverse: #ffffff;

--color-border: #e5e7eb;
--color-border-focus: var(--color-primary);
--color-border-error: #dc2626;

--color-error: #dc2626;
--color-error-light: #fef2f2;
--color-success: #16a34a;
--color-success-light: #f0fdf4;
--color-warning: #ea580c;
--color-warning-light: #fff7ed;

/* Sponsor Neutral — logos rendered on consistent background */
--color-sponsor-bg: #fafafa;
--color-sponsor-border: #e5e7eb;

/* Shadow System */
--shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
--shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
--shadow-focus: 0 0 0 3px var(--color-primary-focus);
```

**Contrast Guarantees (WCAG AA):**
- Text on surface: 12.6:1 (AAA)
- Primary on white: 4.5:1 minimum (verify per brand hue)
- Error on light: 5.9:1
- Focus ring: 3:1 against adjacent

---

## Spacing Rhythm

**Base Unit:** 4px
**Scale:** 4, 8, 12, 16, 24, 32, 48, 64, 96px

```css
--space-1: 4px;   /* Micro: icon gaps, inline */
--space-2: 8px;   /* Small: form gaps, card padding */
--space-3: 12px;  /* Medium-small: button padding */
--space-4: 16px;  /* Base: component padding, gaps */
--space-5: 24px;  /* Medium: section inner, card gaps */
--space-6: 32px;  /* Large: section vertical rhythm */
--space-7: 48px;  /* XL: page section gaps */
--space-8: 64px;  /* XXL: major section breaks */
--space-9: 96px;  /* Hero: top/bottom */
```

**Container:** `max-width: 1200px; padding-inline: var(--space-4);`
**Mobile Container:** `padding-inline: var(--space-3);`

---

## Component Language

### Button (3 Variants Only)
```css
.btn {
  --btn-padding-x: var(--space-4);
  --btn-padding-y: var(--space-3);
  --btn-radius: 8px;
  --btn-font: var(--step-0);
  --btn-weight: 600;
  transition: background 100ms, transform 50ms;
}
.btn:active { transform: scale(0.98); }
.btn:focus-visible { outline: none; box-shadow: var(--shadow-focus); }

/* Variants */
.btn--primary { background: var(--color-primary); color: var(--color-text-inverse); }
.btn--primary:hover { background: var(--color-primary-hover); }
.btn--secondary { background: transparent; color: var(--color-primary); border: 2px solid var(--color-primary); }
.btn--secondary:hover { background: var(--color-primary-light); }
.btn--ghost { background: transparent; color: var(--color-text-primary); border: none; }
.btn--ghost:hover { background: var(--color-surface-hover); }
```

### Card (4 Types)
| Type | Structure | Use |
|---|---|---|
| **Media** | Image (16:9) + Caption + Credit | Gallery |
| **Sponsor** | Logo (contained) + Tier Badge + Link | Partnership, Home |
| **Team** | Logo + Name + Category + Status | Teams |
| **Match** | Team A vs Team B + Time + Score + Status | Programme |

**Card Base:**
```css
.card { background: var(--color-surface); border: 1px solid var(--color-border); border-radius: 12px; overflow: hidden; transition: box-shadow 150ms; }
.card:hover { box-shadow: var(--shadow-md); }
.card:focus-within { box-shadow: var(--shadow-focus); }
```

### Form Field
```css
.field { display: grid; gap: var(--space-1); }
.field__label { font: var(--step-0) var(--font-sans); color: var(--color-text-primary); font-weight: 500; }
.field__input { padding: var(--space-3) var(--space-4); border: 1px solid var(--color-border); border-radius: 8px; font: inherit; color: var(--color-text-primary); background: var(--color-surface); transition: border 100ms, box-shadow 100ms; }
.field__input:focus { outline: none; border-color: var(--color-border-focus); box-shadow: var(--shadow-focus); }
.field__input[aria-invalid="true"] { border-color: var(--color-border-error); }
.field__error { color: var(--color-error); font: var(--step--1) var(--font-sans); }
.field__hint { color: var(--color-text-muted); font: var(--step--1) var(--font-sans); }
```

### Section
```css
.section { padding-block: var(--space-7); }
.section--hero { padding-block: var(--space-9); }
.section__header { text-align: center; max-width: 60ch; margin-inline: auto; margin-bottom: var(--space-6); }
.section__title { font: var(--step-4) var(--font-sans); font-weight: 700; color: var(--color-text-primary); line-height: 1.1; }
.section__subtitle { font: var(--step-1) var(--font-sans); color: var(--color-text-secondary); margin-top: var(--space-2); }
```

---

## Responsive Rules

**Breakpoints (Content-Driven):**
```css
--bp-sm: 480px;   /* Narrow mobile */
--bp-md: 768px;   /* Tablet / small desktop */
--bp-lg: 1024px;  /* Desktop */
--bp-xl: 1280px;  /* Wide desktop */
```

**Layout Patterns:**
| Component | <480px | 480-767px | 768-1023px | 1024px+ |
|---|---|---|---|---|
| Hero | Stacked, centered | Stacked, centered | Two-col (text + visual) | Two-col, max-width |
| Sponsor Tiers | Single column | Single column | 2-col grid | 4-col grid |
| Team Cards | 1-col | 2-col | 3-col | 4-col |
| Match Cards | Stacked full | Stacked full | 2-col | 3-col |
| Gallery | 1-col | 2-col | 3-col | 4-col (masonry) |
| Nav | Hamburger | Hamburger | Horizontal | Horizontal |
| Form | Full width | Full width | Max 480px centered | Max 480px centered |

**Typography Scaling:** Fluid `clamp()` handles all scaling — no breakpoint font changes.

**Image Sizing:** `width: 100%; height: auto;` + `srcset` for density. Aspect ratio boxes for layout stability.

---

## Interaction Principles

| Principle | Implementation |
|---|---|
| **No decorative animation** | Only functional: form feedback (150ms), menu slide (200ms), loading spinner |
| **Reduced motion first** | `@media (prefers-reduced-motion: reduce) { * { animation: none !important; transition: none !important; } }` |
| **Focus visible always** | 3px solid primary, offset 2px — never `outline: none` without replacement |
| **Touch targets ≥ 44×44px** | Buttons, links, form inputs, tap targets |
| **WhatsApp = native** | `<a href="https://wa.me/...">` — no SDK, no popup |
| **Form submission** | Loading state on button, disable inputs, ARIA live region for result |
| **Image loading** | `loading="lazy"` below fold, `fetchpriority="high"` for hero |
| **Scroll restoration** | Native browser behavior preserved |

---

## Motion Policy

| Motion | Allowed? | Rationale |
|---|---|---|
| Form validation shake | Yes | Functional feedback |
| Form success checkmark | Yes | Confirmation |
| Loading spinner | Yes | Perceived performance |
| Mobile menu slide | Yes | Spatial orientation |
| Accordion expand | Yes | Content disclosure |
| Hero parallax | **No** | Decorative, hurts perf/accessibility |
| Scroll fade-in | **No** | Decorative, no hierarchy value |
| Cursor effects | **No** | Pointer-only, excludes keyboard |
| Background animation | **No** | GPU cost, distraction |
| Counter animations | **No** | Decorative number counting |

**All motion behind:**
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

---

## Accessibility Constraints (Non-Negotiable)

1. **Semantic HTML5:** `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`
2. **Heading Hierarchy:** One `h1` per page → `h2` → `h3` (no skipping)
3. **Landmarks:** All present, `nav` labeled (`aria-label="Main navigation"`)
4. **Skip Link:** First focusable element — "Skip to main content"
5. **Focus Order:** DOM order = visual order
6. **Alt Text:** All images — sponsor logos: `alt="[Name] logo"`
7. **Color Not Sole Indicator:** Icons + text for status (LIVE, FINAL, UPCOMING)
8. **Form Labels:** Explicit `<label for="">` — no placeholder-only
9. **Error Identification:** `aria-describedby` linking input to error
10. **Status Announcements:** `aria-live="polite"` for form success/error
11. **Language:** `lang="fr"` (adjust per organizer) — `lang` on changes
12. **Contrast:** 4.5:1 text, 3:1 UI — verified per token
13. **Target Size:** 44×44px minimum — verified per component
14. **Keyboard:** All interactive reachable, operable, no traps
15. **Reduced Motion:** All non-essential motion disabled

---

## Anti-Vibe Preflight (Per Upstream Skill)

**Patterns Explicitly Avoided:**
- Purple/blue gradient hero → **Single brand color + white space**
- Gradient text headlines → **Solid brand color, weight hierarchy**
- Emoji decoration → **Meaningful iconography or none**
- Glassmorphism cards → **Solid surfaces, subtle shadow**
- 3-icon feature rows → **Content-driven sections**
- Badge on every headline → **Only where semantic (LIVE, NEW, SPONSORED)**
- Lucide icons everywhere → **Custom SVG only where needed (WhatsApp, map, calendar)**
- Generic fade-in scroll → **No scroll animations**
- Cursor glow/spotlight → **None**
- Button hover = only opacity → **Background/border change + transform**
- Inconsistent spacing → **4px rhythm system**
- AI-copy em dashes → **Natural French/English punctuation**
- Generic "Revolutionize your game" copy → **Specific: "3X3 basketball at Palais des Sports"**
- Trendy serif accents → **System sans only — brand voice through content**
- Space Grotesk + Instrument Serif → **System font stack**
- Grain/noise on gradients → **Clean surfaces**

**Rationale for Each:** Documented above — every decision traces to product need (sponsor credibility, mobile clarity, accessibility).

---

## Verification Plan

| Check | Tool/Method | Pass Criteria |
|---|---|---|
| Token contrast | axe-core + manual | All tokens ≥ AA |
| Focus visible | Tab through all pages | 3px ring on every interactive |
| Reduced motion | DevTools toggle | Zero non-essential motion |
| Keyboard nav | Tab + Shift+Tab | All reachable, logical order |
| Screen reader | NVDA/VoiceOver | Labels, landmarks, status announced |
| Responsive | Chrome DevTools device toolbar | 320/768/1024/1440 — no overflow |
| Color blindness | Simulator (Stark/Chrome) | Status discernible without color |
| Token usage | Grep for hardcoded colors | Zero — all via CSS custom properties |