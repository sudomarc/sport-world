# Phase 1 — Product Brief

## Product Objective

Build a credible, mobile-first public web presence for the **GUINEASKET Tournament 3X3** that converts social-media attention into:
1. **Primary:** Sponsor/partner inquiries
2. **Secondary:** Team registrations, WhatsApp contacts, social follows/shares

The site is the official tournament reference — not a generic sports portal.

## Target Audiences

| Audience | Primary Need | Conversion Goal |
|---|---|---|
| Sponsors / Partners | Understand event value, audience, visibility options | Submit partnership inquiry |
| Players / Teams | Event info, registration process, deadlines | Register team or contact organizer |
| Spectators / Media | Programme, results, teams, media assets | Share, follow, attend |
| Organizers | Publish official info, capture leads, showcase partners | Manage content, track inquiries |

## User Journeys

### Sponsor Journey (Primary)
```
Social post / referral
→ Home (hero + value prop)
→ Partnership (tiers, benefits, audience)
→ CTA: "Become a Partner"
→ Inquiry Form (organization, contact, interest)
→ Success: Confirmation + WhatsApp fallback
→ Organizer receives lead
```

### Team Journey (Secondary)
```
Social post / shared link
→ Home or Teams page
→ Teams (registered teams, registration info)
→ CTA: "Register Team"
→ Registration Form / WhatsApp contact
→ Success: Confirmation + next steps
```

### Spectator Journey
```
Discovery (social, search, direct)
→ Home (event essence)
→ Tournament (details, venue, dates)
→ Programme (fixtures, results, brackets)
→ Teams (who's playing)
→ Gallery (photos, highlights)
→ Share / Follow
```

### Organizer Journey
```
Content updates (event data, sponsors, programme)
→ Static JSON files (or CMS later)
→ Deploy (git push)
→ Verify (automated + manual)
→ Lead capture (form submissions)
```

## Primary Conversion

**Sponsor Inquiry Form**
- Fields: Organization, Contact Person, Email, Phone, Partnership Interest (tier/other), Message
- Submission: Formspree/Netlify Forms → email to organizer
- Confirmation: On-page success state + WhatsApp deep link
- Spam protection: Honeypot + rate limiting (Formspree handles)

## Secondary Conversions

1. **Team Registration** — Same form pattern, different fields (Team Name, Captain, Contact, Category)
2. **WhatsApp Contact** — Deep link `https://wa.me/<NUMBER>?text=...` with pre-filled message
3. **Social Follow/Share** — Native share API + meta tags for preview cards

## MVP Scope (7 Routes)

| Route | Type | Primary Content |
|---|---|---|
| **Home** | Page | Hero, value prop, sponsor CTA, key info, social proof |
| **Tournament** | Page/Section | Format, venue, dates, organizer, rules, status |
| **Partnership** | Page | Sponsor tiers, benefits, audience stats, inquiry form |
| **Teams** | Page/Section | Registered teams (cards), registration CTA |
| **Programme / Results** | Page | Fixtures, brackets, standings, live scores (static initially) |
| **Gallery** | Page | Image/video grid, captions, rights, press kit link |
| **Contact** | Page | Organizer info, WhatsApp, email, form, map |

**Navigation Model:** Single-page sections acceptable if content density supports; split pages when content warrants. No artificial page inflation.

## Non-Goals (MVP)

- Full social network / user accounts
- Native mobile app
- Complex admin dashboard / CMS
- Database / backend services
- Payment processing
- Real-time infrastructure (live scores)
- Speculative AI features
- Multi-tournament platform (Phase 5+)

## Content Requirements

### Event (Required)
- name, format, venue, date/time, organizer, short description, status

### Sponsors (Required for Partnership page)
- organization name, logo, tier/relationship, website/social, activation details

### Teams (Required for Teams page)
- team name, logo, roster summary (when authorized), registration status

### Matches (Required for Programme page)
- round, teams, date/time, score, status

### Media (Required for Gallery page)
- image/video, caption, source/rights status, alt text, publish status

### Leads (Required for conversion)
- organization, contact person, phone/email, partnership interest, consent, submission status

## Unknowns (Explicitly Not Fabricated)

| Unknown | Source | Blocked? |
|---|---|---|
| Exact tournament dates | Organizer | Blocks Programme page completeness |
| Sponsor tier names, prices, benefits | Organizer | Blocks Partnership page completeness |
| Organizer legal entity, address, registration | Organizer | Blocks Legal/Privacy pages |
| Official WhatsApp number | Organizer | Blocks WhatsApp CTA |
| Team count, rosters | Organizer | Blocks Teams page completeness |
| Programme fixtures, brackets | Organizer | Blocks Programme page completeness |
| Gallery images + rights | Organizer | Blocks Gallery page |
| Ticketing model (free/paid) | Organizer | May add ticketing CTA |

## Acceptance Criteria (Phase 1 Exit)

- [ ] Product brief approved
- [ ] Information architecture approved
- [ ] Design direction approved (with anti-vibe preflight)
- [ ] Architecture decision recorded with rationale
- [ ] Content unknowns explicitly listed with owners
- [ ] Verification strategy defined
- [ ] No production implementation started