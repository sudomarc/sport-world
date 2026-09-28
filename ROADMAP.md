# Sport World — Roadmap

## Product

**Initial pilot:** GUINEASKET Tournament 3X3

**Primary outcome:** a professional public web presence that turns social-media attention into sponsor conversations, team registrations and audience engagement.

The roadmap deliberately separates the first event experience from a future general-purpose Sport World platform.

## Phase 0 — Governance & project setup
**Status: DONE**

- Initialize repository.
- Establish `AGENTS.md`.
- Pin Vibe Coding Instructions governance.
- Define minimum multi-agent operating model.
- Define project scope and non-goals.
- Establish this roadmap.

**Exit criteria**
- Governance is readable from the repository.
- Agent team responsibilities are explicit.
- No production implementation is started accidentally.

## Phase 1 — Product discovery & architecture
**Next**

### Product
- Validate event facts from the organizer.
- Define target audiences: sponsors/partners, players/teams, spectators/media.
- Define primary conversion: sponsor inquiry.
- Define secondary conversions: team registration, WhatsApp contact, social follow/share.
- Define information architecture and content inventory.

### Design
- Establish the GUINEASKET visual direction from organizer-owned identity/assets.
- Define typography, spacing, color, buttons, cards, sponsor/logo treatment and responsive composition.
- Produce a low-fidelity structure before detailed polish.
- Run anti-vibe preflight.

### Technical
- Decide the smallest suitable frontend architecture.
- Decide content source strategy.
- Decide form/WhatsApp strategy.
- Define deployment and asset handling.
- Define verification matrix.

**Exit criteria**
- Approved product brief.
- Approved IA.
- Approved design direction.
- Architecture decision recorded.
- Content unknowns explicitly listed.

## Phase 2 — Public MVP foundation

Build only what is required for the first useful public release.

### Core pages / surfaces
- Home / event landing
- Tournament overview
- Partnership / sponsorship
- Programme
- Teams / registration
- Gallery / media
- Contact

### Conversion
- Sponsor CTA
- Partner inquiry form
- WhatsApp CTA
- Team registration entry point

### Foundation
- shared header/footer;
- responsive layout system;
- metadata and social sharing;
- 404;
- loading/error/empty states where dynamic behavior exists;
- analytics only if actually required and legally/technically scoped.

**Exit criteria**
- End-to-end sponsor CTA works.
- Team-registration path is usable.
- No critical responsive or accessibility defects.
- Browser verification evidence exists.

## Phase 3 — Tournament operations

Add operational features only after the public MVP is stable.

- Team directory
- Player profiles where authorized and needed
- Fixtures / programme
- Live or post-event results
- Standings / bracket
- Match detail
- Announcements
- Sponsor activation modules

**Exit criteria**
- Organizer content workflow is defined.
- Data model is stable.
- Dynamic states have loading/empty/error/success handling.
- Runtime verification covers critical paths.

## Phase 4 — Media & audience growth

- Photo/video galleries
- Highlights
- Social sharing cards
- Press/media kit
- Sponsor showcase
- Search-friendly event pages
- Structured metadata where appropriate

**Exit criteria**
- Media assets are optimized and provenance/rights are documented.
- Public pages have coherent metadata.
- Performance budget remains within agreed limits.

## Phase 5 — Sport World platformization

Only after validating the pilot.

Potential reusable capabilities:
- multiple tournaments
- multiple sports
- organizer workspaces
- sponsor management
- reusable event templates
- team/player registration
- results and standings
- media management
- public event URLs
- organizer analytics

No platform abstraction should be introduced before a real repeated use case justifies it.

## Phase 6 — Launch / post-event hardening

- Production deployment verification
- Domain / HTTPS verification
- 404 and redirect verification
- robots.txt / sitemap verification
- form delivery verification
- mobile/browser verification
- accessibility pass
- performance pass
- security pass
- sponsor CTA and WhatsApp end-to-end check
- final diff/status review
- release notes and known limitations

## Non-goals for the first release

- full social network
- native mobile app
- complex admin dashboard
- unnecessary backend services
- speculative AI features
- payment processing unless an explicit requirement appears
- real-time infrastructure unless the tournament workflow requires it

## Definition of done

A phase is complete only when:
1. the intended observable behavior exists;
2. appropriate verification has been performed;
3. final scope/diff has been reviewed;
4. remaining unknowns are documented;
5. no claimed evidence is based on assumption.
