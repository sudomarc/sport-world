# Information Architecture — GUINEASKET Tournament 3X3

## Navigation Model

**Primary Navigation (Persistent Header):**
- Home
- Tournament
- Partnership
- Teams
- Programme
- Gallery
- Contact

**Mobile:** Hamburger menu with same items, plus WhatsApp CTA button
**Desktop:** Horizontal nav, WhatsApp CTA in header actions

**Footer Navigation:**
- Legal: Privacy, Terms
- Social: Instagram, Facebook, Twitter/X, YouTube
- Organizer: Contact, About
- Sponsor tier logos (horizontal scroll)

---

## Page/Route Model

### 1. Home (`/`)
**Type:** Page
**Purpose:** Event discovery, sponsor CTA, key info snapshot
**Sections:**
- Hero: Event name, date, venue, primary CTA "Become a Partner"
- Value Proposition: Why sponsor? (audience, visibility, community)
- Key Info Bar: Format, Venue, Dates, Organizer (icon + text)
- Sponsor Showcase: Tier logos (marquee or grid)
- Programme Preview: Next 3 matches / key dates
- Team Count: "X teams registered" + CTA
- Social Proof: Instagram feed / hashtag
- Footer CTA: Partnership + WhatsApp

### 2. Tournament (`/tournament`)
**Type:** Page (or section on Home if content light)
**Purpose:** Complete event details
**Sections:**
- Format: 3X3 rules, FIBA endorsement, categories
- Venue: Palais des Sports du 28 Septembre — map, access, parking
- Dates: Full schedule (start, end, key dates)
- Organizer: Name, logo, mission, contact
- Status: Upcoming / Live / Completed badge
- FAQ: Accordion (registration, rules, spectators, parking)

### 3. Partnership (`/partnership`)
**Type:** Page — **Primary Conversion Surface**
**Purpose:** Sponsor conversion
**Sections:**
- Hero: "Partner with GUINEASKET" + value summary
- Audience Metrics: Expected attendees, social reach, demographics (when known)
- Sponsor Tiers: Cards — Title, Benefits, Logo Placement, Price (when known)
  - Tier 1: Title Partner (exclusive)
  - Tier 2: Official Partner
  - Tier 3: Supporting Partner
  - Tier 4: Friend of the Tournament
- Custom Activations: Court branding, jersey, digital, hospitality
- Inquiry Form: Organization, Contact, Email, Phone, Interest, Message
- WhatsApp CTA: "Talk directly on WhatsApp"
- Existing Partners: Logo wall with tier badges

### 4. Teams (`/teams`)
**Type:** Page (or section)
**Purpose:** Team directory + registration entry
**Sections:**
- Registered Teams: Grid of Team Cards (logo, name, category, status)
- Filters: Category (Men/Women/U18), Search
- Empty State: "No teams registered yet" + registration CTA
- Registration: Process, requirements, deadlines, fees
- CTA: "Register Your Team" → Form or WhatsApp
- Captain Resources: Rules, roster limits, check-in info

### 5. Programme / Results (`/programme`)
**Type:** Page
**Purpose:** Schedule, live results, brackets
**Sections:**
- Day Tabs: Day 1, Day 2, Finals
- Match Cards: Time, Court, Team A vs Team B, Score, Status
- Bracket View: Visual bracket (SVG/CSS) — knockout stages
- Standings: Pool tables (when pool play)
- Live Indicator: "LIVE" badge on active matches
- Past Results: Archive link (future)

### 6. Gallery (`/gallery`)
**Type:** Page
**Purpose:** Media showcase, press assets
**Sections:**
- Hero: Featured image/video
- Grid: Masonry or uniform — images + videos
- Filters: Photos / Videos / Highlights / Press Kit
- Lightbox: Full-screen view, caption, download (press)
- Rights Notice: "Images for editorial use only. Contact organizer for commercial use."
- Press Kit Link: ZIP download (logos, photos, fact sheet)

### 7. Contact (`/contact`)
**Type:** Page
**Purpose:** Organizer contact, general inquiries
**Sections:**
- Organizer Card: Name, logo, address, email, phone
- WhatsApp Button: Primary contact method
- General Inquiry Form: Name, Email, Subject, Message
- Map: Palais des Sports embed (OpenStreetMap/Leaflet)
- Office Hours / Response Time
- Social Links

---

## CTA Hierarchy

| Priority | CTA | Location | Style |
|---|---|---|---|
| **P0** | Become a Partner | Home hero, Partnership hero, Header (desktop) | Primary Button |
| **P0** | WhatsApp Contact | Header (mobile), Home, Partnership, Contact, Teams | Ghost + Icon |
| **P1** | Register Team | Teams page, Home team section | Secondary Button |
| **P1** | View Programme | Home, Tournament | Secondary Button |
| **P2** | View Gallery | Home, Programme | Ghost Button |
| **P2** | Follow/Share | Home, Gallery, Match cards | Icon Buttons |

**CTA States:** Default → Hover → Focus → Active → Loading → Disabled

---

## User Flows

### Flow 1: Sponsor Inquiry (Primary)
```
Entry: Any page (social, search, direct)
→ Home (or direct to Partnership)
→ Partnership page (scroll tiers)
→ Click "Become a Partner" (P0 CTA)
→ Form modal or page section
→ Fill: Org, Contact, Email, Phone, Tier Interest, Message
→ Submit → Loading → Success
→ Success State: "Thank you! We'll contact within 24h." + WhatsApp button
→ Organizer receives email lead
```

### Flow 2: Team Registration (Secondary)
```
Entry: Home → Teams or direct /teams
→ Teams page (view registered)
→ Click "Register Team" (P1 CTA)
→ Registration form or WhatsApp pre-filled
→ Submit → Success: "Registration received. Captain will receive confirmation."
→ Organizer receives lead
```

### Flow 3: Spectator Programme Check
```
Entry: Home or direct /programme
→ Programme page
→ Filter by Day / Stage
→ View match cards
→ Click team name → Teams page (future)
→ Share match (native share API)
```

### Flow 4: Media/Press Access
```
Entry: Gallery page or direct link
→ Gallery → Press Kit filter
→ Download press kit (ZIP)
→ Or: View individual assets in lightbox
→ Copy caption/credit
```

---

## Content Hierarchy (Per Page)

### Home
```
h1: GUINEASKET 3X3 — [Date] · [Venue]
  h2: Why Partner with GUINEASKET
    h3: Audience Reach
    h3: Brand Visibility
    h3: Community Impact
  h2: Tournament at a Glance
    h3: Format
    h3: Venue
    h3: Dates
  h2: Our Partners
  h2: Upcoming Matches
  h2: Teams Registered
```

### Partnership
```
h1: Become a Partner
  h2: Audience & Reach
  h2: Partnership Tiers
    h3: Title Partner
    h3: Official Partner
    h3: Supporting Partner
    h3: Friend of the Tournament
  h2: Custom Activations
  h2: Become a Partner (Form)
    h3: Contact Information
    h3: Partnership Interest
```

### Tournament
```
h1: Tournament Information
  h2: Format & Rules
  h2: Venue & Access
  h2: Dates & Schedule
  h2: Organizer
  h2: Frequently Asked Questions
```

### Teams
```
h1: Teams
  h2: Registered Teams (grid)
  h2: Register Your Team
    h3: Process
    h3: Requirements
    h3: Deadlines
```

### Programme
```
h1: Programme & Results
  h2: Day 1 — [Date]
    h3: Pool A
    h3: Pool B
  h2: Day 2 — [Date]
  h2: Finals — [Date]
  h2: Standings
```

### Gallery
```
h1: Gallery
  h2: Featured
  h2: All Media (filterable)
  h2: Press Kit
```

### Contact
```
h1: Contact Us
  h2: Organizer Information
  h2: WhatsApp (Primary)
  h2: General Inquiry
  h2: Location
```