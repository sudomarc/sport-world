# Architecture Decision Record — GUINEASKET Tournament 3X3 MVP

## Observed Architecture (Current State)

**Phase 0 — Governance Only**
- No source code, no build system, no deployment
- Documentation only: AGENTS.md, ROADMAP.md, PROJECT-SCOPE.md, README.md
- Local `.ai/` governance overlays (6 agent contracts)
- Upstream: Vibe Coding Instructions pinned at `a79ac4a97179f7dac00ee356722bb47f41909ac2`

---

## Candidate Architectures Evaluated

| # | Architecture | Description |
|---|---|---|
| A | **Static HTML/CSS/JS** | Hand-authored HTML per route, shared partials via build or SSI, zero framework |
| B | **Astro (Static Export)** | Component-based, zero-JS by default, MDX support, great SEO, Vercel/Netlify native |
| C | **11ty (Eleventy)** | Template-based, flexible data, zero client JS, mature ecosystem |
| D | **Next.js (Static Export)** | React components, SSG/ISR, Image optimization, Vercel native, larger bundle |
| E | **React SPA (Vite)** | Client-only rendering, component model, poor SEO without SSR, overkill |

---

## Selection: **Static HTML/CSS/JS (Option A) — with Astro (Option B) as upgrade path**

### Rationale

| Criterion | Static HTML/CSS/JS | Why It Wins |
|---|---|---|
| **SEO** | Perfect — server-rendered HTML, no hydration | Sponsor conversion depends on crawlability |
| **Performance** | Optimal — no framework overhead, minimal JS | Mobile-first on 3G; LCP < 2.5s target |
| **Operations** | Zero build, zero deps, git push deploy | No CI failures, no version drift, no lock-in |
| **Team Velocity** | Immediate start, no learning curve | Single developer, 7 pages, 2-week target |
| **Content Model** | JSON data files + HTML templates | Simple, version-controlled, no CMS needed |
| **Forms** | Formspree/Netlify Forms (serverless) | No backend, spam protection included |
| **WhatsApp** | Deep link — zero code | Native `wa.me` links |
| **Extensibility** | Can migrate to Astro/Next.js later | No architectural lock-in |

**Why Not Astro/Next.js Now?**
- 7 pages, mostly static content → framework adds complexity without ROI
- No dynamic routing, no auth, no real-time, no user accounts
- Sponsor conversion = static content + form → HTML + Formspree solves it
- Upgrade path exists: Astro can consume existing HTML/CSS/JS incrementally

---

## Trade-offs

| Trade-off | Accepted | Mitigation |
|---|---|---|
| Manual HTML duplication (header/footer) | Yes | Use build-time includes (Astro later) or simple SSI |
| No component reuse | Yes | 7 pages only; primitives via CSS classes |
| No image optimization pipeline | Yes | Manual WebP/AVIF + `srcset`; upgrade to Astro Image later |
| No type safety | Yes | JSON Schema for data files; TypeScript later |
| Form handling external | Yes | Formspree/Netlify Forms — verify ACTIVE in production |

---

## Data / Content Strategy

### MVP Content Representation

| Content | Representation | Rationale |
|---|---|---|
| Event info | `data/event.json` | Single source, typed, version-controlled |
| Sponsor tiers | `data/sponsors.json` | Array of tier objects, logo paths, benefits |
| Programme | `data/programme.json` | Matches, days, courts, status |
| Teams | `data/teams.json` | Team objects, logos, categories |
| Gallery | `data/gallery.json` | Media objects, captions, rights, alt text |
| Leads | Formspree/Netlify Forms | Serverless, no backend, spam protection |

**Static vs Dynamic Classification:**

| Content | MVP | Future |
|---|---|---|
| Event details | Static JSON | Static JSON or CMS |
| Sponsor tiers | Static JSON | CMS (organizer updates) |
| Programme | Static JSON | CMS + live scores API |
| Teams | Static JSON | CMS + registration API |
| Gallery | Static JSON | CMS + upload workflow |
| Leads | Formspree | CRM integration |

**Currently UNKNOWN (Placeholders in JSON):**
- Exact dates → `date: "TBD"`
- Sponsor prices/benefits → `price: null, benefits: []`
- WhatsApp number → `whatsapp: null`
- Team rosters → `roster: []`
- Match fixtures → `matches: []`
- Gallery images → `media: []`

---

## Deployment Strategy

**Platform:** Vercel (or Netlify) — git push deploy
**Configuration:** `vercel.json` for SPA fallback, headers, redirects
**Headers:**
```
Content-Security-Policy: default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; connect-src 'self' https://formspree.io https://api.whatsapp.com
Referrer-Policy: strict-origin-when-cross-origin
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
```

**Custom Domain:** To be configured (Phase 6)
**HTTPS:** Automatic (Vercel/Netlify)
**Cache:** Static assets — long-term; HTML — short-term or no-cache

---

## Verification Strategy

### Pre-Deploy (Local)
- [ ] HTML validation (W3C validator)
- [ ] CSS lint (stylelint)
- [ ] JS lint (ESLint)
- [ ] Accessibility: axe-core on all 7 routes
- [ ] Responsive: 320px, 768px, 1024px, 1440px
- [ ] Performance: Lighthouse CI (LCP, TBT, CLS)

### Post-Deploy (Production)
- [ ] All 7 routes return 200
- [ ] HTTPS + headers verified
- [ ] Form submission → email received
- [ ] WhatsApp deep link opens app
- [ ] Sitemap.xml + robots.txt present
- [ ] OG tags render in social preview
- [ ] 404 page works
- [ ] Mobile nav opens/closes, focus trapped

### Ongoing
- Lighthouse CI on every PR
- Monthly performance budget check
- Quarterly accessibility audit

---

## Unresolved Questions

| Question | Owner | Target Resolution |
|---|---|---|
| Exact Formspree/Netlify Forms endpoint | Organizer/Dev | Before Batch 3 |
| Official WhatsApp number | Organizer | Before Batch 3 |
| Custom domain | Organizer | Phase 6 |
| Analytics requirement (legal/technical) | Organizer/Legal | Phase 1 exit |
| Image optimization pipeline | Dev | Phase 2+ (Astro upgrade) |
| Multi-language (FR/EN) | Organizer | Phase 4+ |

---

## Implementation Batches

| Batch | Scope | Deliverable |
|---|---|---|
| **1** | Scaffold: HTML structure, CSS tokens, shared header/footer, 7 routes, JSON data stubs | Runnable static site |
| **2** | Content: Populate JSON with real data (as available), integrate into templates | Content-complete pages |
| **3** | Forms: Sponsor inquiry + Team registration → Formspree, WhatsApp deep links | Working conversions |
| **4** | Verification: Browser QA, accessibility pass, performance audit, SEO audit | Release-ready |
| **5** | Polish: Animations (reduced-motion), error states, empty states, press kit | Production MVP |

---

## Architecture Diagram (Text)

```
┌─────────────────────────────────────────────────────────────┐
│                    VERCEL / NETLIFY                         │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │ Static HTML │  │   Assets    │  │   Headers/CSP       │  │
│  │  (7 routes) │  │ (images,    │  │   Redirects         │  │
│  └──────┬──────┘  │  fonts, JS) │  └─────────────────────┘  │
│         │         └─────────────┘                            │
│         ▼                                                    │
│  ┌─────────────────────────────────────────────────────┐    │
│  │              FORMSPREE / NETLIFY FORMS               │    │
│  │  POST /sponsor-inquiry  →  Email to organizer       │    │
│  │  POST /team-registration →  Email to organizer      │    │
│  └─────────────────────────────────────────────────────┘    │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐    │
│  │              WHATSAPP DEEP LINKS                    │    │
│  │  https://wa.me/<NUMBER>?text=...                    │    │
│  └─────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────┘
                              ▲
                              │ git push
                    ┌─────────┴─────────┐
                    │   GIT REPO        │
                    │  (main branch)    │
                    │                   │
                    │ /index.html       │
                    │ /tournament.html  │
                    │ /partnership.html │
                    │ /teams.html       │
                    │ /programme.html   │
                    │ /gallery.html     │
                    │ /contact.html     │
                    │ /shared/          │
                    │ /data/*.json      │
                    │ /styles/*.css     │
                    │ /scripts/*.js     │
                    │ vercel.json       │
                    └───────────────────┘
```

---

## Decision Record

| Field | Value |
|---|---|
| **Decision** | Static HTML/CSS/JS with JSON data, Formspree forms, WhatsApp deep links |
| **Date** | 2026-09-29 |
| **Status** | Accepted |
| **Deciders** | Web Architect (upstream), Product Strategy (local) |
| **Review Date** | Phase 2 completion or when dynamic needs emerge |