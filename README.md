# Sport World

> Sports web platform foundation. Initial pilot: the **GUINEASKET Tournament 3X3** public/sponsor-facing experience.

## Project objective

Build a credible sports web presence that turns social traffic into concrete actions:

- discover the event;
- understand the value proposition for partners and sponsors;
- view teams, programme, results and media;
- register a team or contact organisers;
- reach organisers quickly through WhatsApp and other official channels.

The first release is intentionally focused. It is not a generic sports portal yet.

## Initial product

**Pilot:** GUINEASKET Tournament 3X3

**Known input:** the supplied event announcement describes a 3X3 basketball tournament at the Palais des Sports du 28 Septembre and explicitly calls for partners, sponsors and brands to associate with the event.

## Governance

This repository is governed by `AGENTS.md`.

Every substantive coding task MUST use the project's Vibe Coding Instructions contract and MUST be decomposed across at least five independent specialist-agent roles. See:

- `AGENTS.md`
- `ROADMAP.md`
- `docs/AGENT-TEAM.md`
- `.ai/VIBE-CODING.md`

## Current status

**Phase 0 — governance and planning**

No production implementation has started yet. The next milestone is product/design architecture, followed by implementation.

## Planned technical direction

Start with the smallest stack that satisfies the product:

- public-first web UI;
- mobile-first responsive design;
- lightweight client-side runtime unless requirements justify a framework;
- Vercel-compatible deployment;
- form/WhatsApp conversion paths;
- measurable performance, accessibility, SEO and browser QA.

The exact framework choice is a Phase 1 architecture decision, not an assumption to encode during scaffolding.
