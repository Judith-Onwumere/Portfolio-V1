# Judith Onwumere portfolio: full handover

Everything built and decided in the "Career" project chat, written so a new chat can pick it up cold. Treat this file as the source of truth for the content, the design system, the layout rules and Judith's preferences. The finished site files (index.html and the img folder) are delivered alongside it in a zip.

Last updated: 9 Nov 2026.

---

## 1. How to use this file in a new chat

1. Upload this file and the zip (or tell the new chat to read this file only).
2. State the goal, for example: "Build a second portfolio from this content, in a different style" or "Add a new case study using the same format".
3. Tell the new chat: use the content in section 8 and the appendices as the facts, obey section 9 (content integrity) and section 10 (preferences), and never invent metrics.

Suggested opening prompt for the new chat:

> I'm Judith, a product designer. Read the attached handover file fully. I want to build a new portfolio using the same content and the same standards (honest claims, AI-use story, side-by-side layout, mobile-first). Ask me up to three questions, then plan the build in batches so it doesn't time out.

---

## 2. Who Judith is and what the portfolio is for

- Name: Judith Onwumere. Product designer, based in Nigeria. Also does freelance frontend design for clients in the Nigerian market.
- Goal: win senior product design roles with product-led teams, remote, on site or with relocation. The site's contact line says exactly that.
- Positioning line (hero): "Hi, I'm Judith. I design apps people enjoy." Hero subtext (her wording, translated into all six languages): "A designer who turns complicated, multi-layered problems into useful products people enjoy using. I take a feature from first research and requirement, through motion, to a handoff developers can build without guessing."
- Tagline/marquee: "✦ EFFORT MAKES YOU ✦". Hero tag: "Product designer and craft lover". Personality: bubbly, curious, logical, loves pastel, crochets (TikTok crochet account).
- Contact: onwumerejudith@gmail.com. Behance: https://www.behance.net/onwumerejudith. LinkedIn: https://www.linkedin.com/in/judithonwumere/. CV download link is a Google Drive export link (id 1A3wY-a1-qHTSksrui2rUJGQMhQ7QmbQn). Confirm the LinkedIn and Behance URLs are the live ones before publishing anywhere new.
- Education and certificates shown on the site: B.Sc. Computer Science, University of Nigeria (2024); Anthropic "AI Fluency: Framework and Foundations"; Cambridge International Qualifications "Basics of Information Security" (2026); OpenLearn Create "Introduction to Generative Engine Optimisation (GEO)" (2026). Each has a certificate image.

### Work history shown
| Dates | Company | Role |
|---|---|---|
| Mar 2025 – Oct 2026 | KEYS (PropTech and community management) | Product Designer |
| Oct 2024 | Quebit Group (Canadian team, short contract) | Product Designer |
| Feb – May 2024 | RateAm | Freelance Product Designer |
| Feb 2023 – Jan 2024 | SwiftAlly (SwiftVote, SwiftReview, SwiftPoll) | UI/UX Designer |

---

## 3. What exists now

- Live preview (private to Judith unless she shares it): https://claude.ai/artifact/XeaDwrMqXTVmdtsm6L3CTm
- Single self-contained HTML page. For her own hosting she deploys `index.html` plus the `img/` folder (Vercel; an older deployment was judith-onwumere-portfolio.vercel.app). The hosted preview version inlines every image as base64.
- Six interface languages (English, French, Spanish, Chinese, Korean, Thai) via a language switcher. The older case studies (RateAm, AdQua, Petrol Advisory) have translations. KEYS and Lazy Stash, and all newly added diagrams, are English only (a note appears in other languages).
- A hidden game ("My toolbox: match it to win": sticker-matching, 45 seconds) that unlocks a "secret diary" overlay with personal taste (games, series, music, Spotify work playlist).

- Browser tab: title is "Judith Onwumere - Product designer". The favicon is a face-centred crop of the hero photo (img/photo.webp), embedded as base64 PNG icons (96px and 180px apple-touch icon) in the page head; standalone copies are favicon.png and apple-touch-icon.png in the zip. The claude.ai preview shows its own emoji favicon in the tab, so the photo icon shows only when the site is hosted on her own domain.

### Home page sections, in order
Nav (brand text "Judith O."; links: Case studies, Experience, Certificates, About, Side quests, Contact) → Hero (photo, tagline, Download CV) → Marquee → Case studies cards → Experience accordion → Certificates carousel → Toolbox game → About → How I work → Side quests → Contact (email, Behance) → footer "Made by Judith, with love and lots of coffee ✿🍵".

---

## 4. Architecture (for anyone editing the code)

- One `index.html`. Large inline CSS (about 540 lines plus additions), then one big script. Case studies live in a JS array `CASES`. Each entry: `{ti, slug, img, title, tag, sub, blurb, ...}` plus either:
  - classic fields: `facts` (white cards), `stats` (big-number cards), `note`, `secs` (heading/body sections), `slots` (inserted after a given section index), `shots` (two bottom images), `link`; or
  - a `body` HTML string (used by KEYS and Lazy Stash) that replaces the whole classic layout, so links/buttons must be inside `body`.
- `slots` entries are `[sectionIndex, label, description, size, html]`. If `html` (index 4) exists the `slot()` function renders it instead of the grey "Image slot" placeholder. All former placeholders now carry diagrams or real screens.
- Card covers come from `IMG` (a key to file map) via the `img` field on each case (`keys_cover`, `lazy_cover`, and the existing covers).
- Translations: `TR` (UI strings by language) and `TE` (case text keyed by the first 20 characters of a text node) plus `ZF` for Chinese. Changing English text invalidates its translation silently (falls back to English).
- A small script at the end of the page (`fit`) sizes the screenshots in text-and-image rows to match the text height (see appendix C).
- Safe-area and phone-first CSS: viewport-fit=cover, safe-area padding, scroll containers for wide content.
- Editing approach used in the chat: Python build scripts regenerate the case studies from a pristine backup of the page, then Playwright renders the page at 1440, 1100, 900, 768 and 390px wide to check overflow and errors before publishing.

### Image inventory (img folder)
- `img/about.webp` — 1100×1216px, 72 KB
- `img/adqua_1.webp` — 1181×707px, 22 KB
- `img/adqua_2.webp` — 1171×593px, 39 KB
- `img/adqua_cover.webp` — 1293×809px, 54 KB
- `img/aq_cart.webp` — 786×1701px, 45 KB
- `img/aq_cart_s.webp` — 440×952px, 17 KB
- `img/aq_hero.webp` — 1600×1000px, 144 KB
- `img/aq_home.webp` — 786×1701px, 87 KB
- `img/aq_home_s.webp` — 440×952px, 33 KB
- `img/aq_notif.webp` — 786×1701px, 77 KB
- `img/aq_pd.webp` — 786×1701px, 68 KB
- `img/aq_pd_s.webp` — 440×952px, 25 KB
- `img/aq_prof.webp` — 786×1701px, 82 KB
- `img/aq_search.webp` — 786×1701px, 112 KB
- `img/aq_subs.webp` — 780×1688px, 67 KB
- `img/aq_subs_s.webp` — 440×952px, 24 KB
- `img/briefs.webp` — 450×300px, 8 KB
- `img/btn.webp` — 1516×868px, 36 KB
- `img/cert_aif.webp` — 1600×1236px, 34 KB
- `img/cert_bsc.webp` — 1378×2048px, 347 KB
- `img/cert_ciq.webp` — 1600×1141px, 96 KB
- `img/cert_geo.webp` — 1448×2048px, 210 KB
- `img/d10.webp` — 810×1080px, 127 KB
- `img/d11.webp` — 1400×788px, 83 KB
- `img/d12.webp` — 1100×1467px, 399 KB
- `img/d13.webp` — 1080×1332px, 117 KB
- `img/d14.webp` — 1100×1467px, 439 KB
- `img/d2.webp` — 1100×1467px, 158 KB
- `img/d4.webp` — 1100×1467px, 208 KB
- `img/d5.webp` — 1100×1467px, 190 KB
- `img/d6.webp` — 1100×1467px, 84 KB
- `img/d7.webp` — 1100×1467px, 62 KB
- `img/d9.webp` — 1100×1467px, 123 KB
- `img/keys_cover.webp` — 1024×768px, 66 KB
- `img/lazy_cover.webp` — 1200×900px, 86 KB
- `img/ls_counter.webp` — 440×978px, 21 KB
- `img/ls_d_dash.webp` — 1200×675px, 33 KB
- `img/ls_d_patterns.webp` — 1200×675px, 88 KB
- `img/ls_dash.webp` — 440×978px, 25 KB
- `img/ls_home.webp` — 440×978px, 26 KB
- `img/ls_notes.webp` — 440×978px, 17 KB
- `img/ls_pattern.webp` — 440×978px, 40 KB
- `img/ls_patterns.webp` — 440×978px, 46 KB
- `img/ls_pdf.webp` — 440×978px, 26 KB
- `img/ls_projects.webp` — 440×978px, 30 KB
- `img/ls_settings.webp` — 440×978px, 29 KB
- `img/ls_supplies.webp` — 440×978px, 35 KB
- `img/ls_video.webp` — 440×978px, 27 KB
- `img/ls_yarn.webp` — 440×978px, 34 KB
- `img/pa_1.webp` — 1170×811px, 38 KB
- `img/pa_2.webp` — 1171×724px, 28 KB
- `img/pa_checkin.webp` — 750×1624px, 39 KB
- `img/pa_cover.webp` — 1293×809px, 40 KB
- `img/pa_emergency.webp` — 750×1624px, 75 KB
- `img/pa_explore.webp` — 750×1624px, 110 KB
- `img/pa_explore_s.webp` — 440×953px, 37 KB
- `img/pa_hero.webp` — 1600×1000px, 130 KB
- `img/pa_home.webp` — 750×1624px, 46 KB
- `img/pa_home_s.webp` — 440×953px, 19 KB
- `img/pa_redeem.webp` — 750×1624px, 50 KB
- `img/pa_redeem_s.webp` — 440×953px, 22 KB
- `img/pa_rewards.webp` — 750×1624px, 69 KB
- `img/pa_station.webp` — 750×1624px, 73 KB
- `img/pa_tank.webp` — 750×1624px, 39 KB
- `img/pa_tank_s.webp` — 440×953px, 17 KB
- `img/pencrib.webp` — 450×300px, 16 KB
- `img/photo.webp` — 1200×1537px, 93 KB
- `img/rateam_1.webp` — 1177×870px, 53 KB
- `img/rateam_2.webp` — 1178×842px, 55 KB
- `img/rateam_cover.webp` — 1293×809px, 71 KB
- `img/sm.webp` — 450×300px, 15 KB
- `img/w3s.webp` — 450×300px, 11 KB
- `img/yhacker.webp` — 450×300px, 12 KB

---

## 5. Design system

Style name: pastel brutalism. Thick ink borders (3px), hard offset shadows (6px 6px 0), rounded corners, dot-grid cream background, hand-written Caveat accents.

- Colour tokens: `--bg:#fffaf3; --ink:#1b1b1b; --card:#fff; --pink:#ffb3d1; --lilac:#d4c2ff; --mint:#b5f0d0; --butter:#fff09e; --peach:#ffd0aa; --sh:6px 6px 0 var(--ink)`.
- Extra tints used by newer components: lilac panel `#ebe3ff`, butter tint `#fff6c2`, mint tint `#daf8e8`.
- Fonts: Bricolage Grotesque (400/600/800, headings tight at line-height 1.02 and letter-spacing -.03em) and Caveat 700 for handwritten notes. Body 18px / 1.55.
- Headings: h2 `clamp(2rem,6vw,3.6rem)` with a pink underline highlight.
- Components (class names): `.box` card, `.facts` (four white cards), `.stats` (coloured big-number cards), `.note` (pink left-bar paragraph), `.cover` (16:8 hero image), `.kh/.khg/.khr` (the old yellow header box, now unused), `.kchips`, `.kd` decision card with `.kdh/.kdn/.kdl/.kq/.kopts/.ko/.ko.ch/.kdp`, `.kt` tables, `.kv/.kvs` SVG figure with `.nda` tag pill (now used only for "Process diagram", "Simplified recreation" and similar labels), `.btn` and `.btn.mint`.
- Newer components: `.lsec` section wrapper, `.lss.t / .lss.d` text-and-media rows, `.stg/.stgi/.ph/.pill` lilac stage panel with phone screenshots, `.dg` white diagram card, `.cmp/.cmpc` before-after columns, `.stp` step card with arrows, `.hflow`, `.brow/.btrack/.bfill` bar charts, `.call` callout, `.cols3/.cc` cards, `.mp` map tiles, `.bw` browser wireframe.

---

## 6. Case study format ("decision-led")

Opening, in this order: **four white fact cards** (Role, Scope, Timeline, Industry) → cover image → **four coloured stat cards** → pink note (status, read time, invitation to discuss in interview). Then sections in this shape:

1. Context / the problem.
2. My role (what I owned, what I shaped, reporting line, tools).
3. Timeline at a glance (KEYS only).
4. Three decisions, each as a card: the question, option A vs option B (chosen marked), why, the cost. Each decision paired with a visual.
5. "Not every call went my way": honest trade-offs and cut features.
6. The solution (key screens).
7. Working with AI (KEYS and Lazy Stash): a table of task, tool and how it was used.
8. How I'd measure success: a table of feature, what success looks like, signal.
9. Reflection.
10. End buttons (KEYS: Google Play and contact; Lazy Stash: Try Lazy Stash).

Judith loves the depth and structure of the KEYS case study and wants every case study brought to that level, one case at a time ("work in batches to avoid timing out").

### Per-case status
- **KEYS**: complete, includes 7 custom SVG visuals, AI section, reflection, Play Store and "Ask KEYS about working with me" buttons.
- **Lazy Stash**: complete in the new format with real screenshots (see section 8).
- **RateAm, AdQua, Petrol Advisory**: placeholders replaced with contextual diagrams and real app screens, but they still use the older, shorter format. They have NOT yet been expanded to KEYS depth (no decisions, trade-offs, AI section, success measures). Judith has not yet answered the questions asked for RateAm (see section 11).

---

## 7. Layout rules that were learned the hard way

Judith's feedback shaped these. Follow them in any rebuild.

1. Pair text and images side by side where it fits, otherwise stack. Never leave one tall phone screenshot floating next to three lines of text.
2. Put screenshots in a framed "stage" panel (lilac, ink border) so they read as intentional. Use labelled pills (Before, After, 1 Buy…).
3. For text rows: text column about 420px, screenshots on the right, and the screenshot height is computed to match the text block height plus about 6% (never a huge mismatch). Needs the fit script in appendix C. At 1020px and below, stack text above panel.
4. For decision cards: stack the card on top and the screenshots below in a full-width panel, phones up to 300px each so they are very visible.
5. Spacing: more space between adjacent elements (cover, header cards, chips, notes, paragraphs, figures and captions, decision card internals), with only a moderate gap between sections. Her words: spacing between "these elements", not between sections.
6. Wide diagrams need a vertical version on phones (switch with a class pair `vd`/`vm`). HTML/CSS diagrams (flows, bars, cards) reflow by themselves and are preferred where possible.
7. Check every layout at desktop, tablet (768 to 1024) and phone. Her words: a recruiter reading it must not be thrown off. Act as an experienced UX designer, review alignment critically, and say honestly what still looks imperfect.
8. Use real screenshots wherever they exist, and diagrams for conceptual content.

---

## 8. Content facts, by case study

Everything below was either written on the page or stated by Judith. Anything not listed was not verified and must not be asserted.

### KEYS
- Community platform for residential estates (UK and Europe, US market also researched). Residents use it for news, clubs, events, voting and booking local services; committees run their estate; developers and landlords manage properties. Mobile app on iOS and Android plus a responsive web platform. Two apps (resident and service provider), 3 platforms, 8 user types, 11 PRDs authored.
- Role: Product Designer, one of several, each owning separate features. Owned services marketplace, community projects, property-owner tools; wrote the PRDs engineering built from. Reported to the design team lead and the project manager. Tools: Figma, Jitter, Claude (plus Figma Make, Figma Agent, Google Flow).
- Timeline: Mar 2025 – Oct 2026, 19 months. The page currently says "In build", although a Google Play listing exists (ask Judith whether it is live and update the wording).
- No launch metrics. The "How I'd measure success" table lists signals only.
- AI use (stated by Judith): Figma Make and Figma Agent for design edits and low-fi screen generation, with the design library and reference images loaded so output matches the style; Claude to turn her screen-by-screen notes, written in her own words, into professional PRDs; Figma Agent for layer renaming, padding fixes and desktop and tablet versions of mobile screens; Google Flow for illustrations, which "saved a LOT of time". No time-saved numbers were given and none must be invented.
- Design system claim: the earlier "cut cycle by 30%" was a placeholder and was removed. Current line: components, spacing tokens and interaction states so designers and developers worked from the same building blocks. Check the CV for the old 30% claim too.
- Reflection (written by Judith, polished): enjoyed it; solves a real everyday problem; very user-centred; many user types served so every feature needed rules that worked for everyone.
- Links: Google Play https://play.google.com/store/apps/details?id=com.keys.community&hl=en. Contact button emails gerard.pambu@keyscommunity.co.uk (supplied by Judith as the person at KEYS to ask about her work) with the subject "Question about working with Judith Onwumere". Button label: "Ask KEYS about working with me".
- The "View on LinkedIn" button under the KEYS entry in the Experience section was removed at her request (do not re-add). The navbar shows "Judith O.".
- All NDA wording was removed at her request (tag, note, diagram labels). Do not reintroduce.

### Lazy Stash
- Personal project: a PWA craft inventory for crocheters and knitters, built in Google AI Studio by prompting. Judith is the product designer and prompter: she specified the design, the data model, the themes and the behaviour; the AI wrote the code. AI Studio's model needed very precise prompts.
- Took 14 days because of AI Studio's 24-hour reset window. She is the only user so far, nobody else has tested it, so there are NO usage metrics. The earlier invented results (14 min to under 3, minus 82%, 41% to 69%, load times) were deleted and must not return. Her own stash currently holds 100+ balls of yarn and 100+ patterns.
- AI problem she solved: PDF text extraction (used to fill the new-pattern form) kept reading the text wrongly and putting wrong text in fields. Fix: a prompt containing a list of keywords and what each means, for example "hook: 3.5mm and 5mm" means select the 3.5mm hook and the 5mm hook.
- Cuts: (1) online database sync, because the AI struggled to implement it with Firebase Studio on her plan, so users export and import data manually; (2) video patterns stored on the device, because videos were being imported (duplicated in two places) instead of read from device storage, which a PWA cannot do, so patterns stay written and PDF with YouTube links.
- Three decisions on the page: a dashboard answering "what do I own?" (totals, low stock, shopping list, quick add), a counter built for busy hands (large +1 Row button, −1, +5, reset, segments such as Main Body and Brim, screen-awake toggle, haptic feedback), and pattern, tutorial and materials in one place (hook, ply, yarn needed, materials, PDF viewer with Extract button, in-app YouTube).
- Screens used: notes-app "before" shot (caption "Before: my patterns lived in a notes app" is an inference, confirm), home, dashboard, yarn list, projects, patterns, pattern detail, PDF viewer, video, counter, settings and supplies, plus desktop dashboard and patterns library. The screenshots contain her naira stash value, her photo and a project thumbnail with her face. Ask whether to blur.
- Link button: https://lazy-stash.ai.studio ("Try Lazy Stash"). The timeline has no calendar dates (none supplied).

### RateAm (Feb – May 2024, freelance)
- Rating flow, network map, shared design language. Mobile-first, low-bandwidth. Survey: 74% of surveyed users hit network issues regularly; about ₦3,500 average monthly mobile spend per user in 2024 (above ₦5,000 by 2025 per MTN and Airtel ARPU reports); 68% would check network quality before moving; ratings take under 10 seconds. The rating step names in the flow diagram are inferred and unconfirmed. Survey sample size not stated anywhere.

### AdQua
- Bottled water as a mobile advertising medium: consumer app (ordering, points-based recycling rewards, water-intake tracker), partner website, three dashboards (manufacturer, brand, retailer). Research: 63% of consumers prefer brands with visible sustainability efforts; 72% of manufacturers want advertising partnerships; ₦938.6bn Nigerian bottled water sales in 2016 (Euromonitor). No rewards or tracker screens exist yet to show.

### Petrol Advisory
- Virtual fuel storage, delivery or pickup, tow truck and mechanic requests, partner station dashboard. Research: desk research plus in-person interviews at fuel stations; 68% interested in delivery to avoid queues; 73% prioritise tow truck and mechanic add-ons; 400+ vehicles a day at an average urban station is an estimate, not an official figure. No live-tracking screen exists.

### Other work referenced
Quebit Group (Oct 2024), SwiftVote redesign, SwiftReview CMS, SwiftPoll, and side quests on Behance: Hacker News homepage redesign, W3Schools course page redesign, Practice Briefs app (first solo project), 3D social media icons pack (Figma Community), PenCrib landing page. Other personal projects in her notes: Yarn Nest (crochet stash and project tracker), a custom gallery app and a daily to-do app with streaks (not on the portfolio).

---

## 9. Content integrity rules

- Never fabricate metrics, research, interviews, tools or timings. If a number was not given, leave it out or label it as an estimate.
- AI work is described honestly: Lazy Stash was AI-built with Judith as the prompter; KEYS used AI for PRD formatting, screen drafts, clean-up and illustrations, while decisions stayed hers.
- Label recreations honestly ("Simplified recreation", "Illustrative map", "Simplified flow").
- Remove claims that cannot be defended in an interview.
- No NDA language anywhere.

---

## 10. Judith's preferences and working style (from this chat)

- Wants to proceed step by step and in batches so nothing times out; invites questions.
- Wants depth, structure and visuals like the KEYS case study everywhere, and AI-use stories on KEYS and Lazy Stash.
- Gives precise layout feedback and notices small errors. When corrected, own the mistake and fix it. She once found the wrong button removed, so confirm which instance when an instruction is ambiguous.
- Wants an experienced-UX-designer standard: self-review alignment honestly.
- Uses comments on the published artifact to request changes ("Stack this as well", "Remove this from here"). The comment's anchor says which element.
- Prefers a warm, collaborative tone when describing declined proposals or trade-offs (the KEYS section was softened; the "What I took from it" paragraph is approved as written). The KEYS Reflection has no "What's next" line.
- Prefers short, direct answers; British spelling in content ("behaviour", "colour"); typographic apostrophes.
- Likes: pastel palette, handwritten accents, playful microcopy (diary, sticker game).

---

## 11. Open items and questions still unanswered

1. RateAm batch: who she worked with and her process; where the survey figures came from and the sample size; what options she considered and rejected for the rating flow and the map; anything changed after feedback; whether she used AI.
2. AdQua and Petrol Advisory: need the same depth (decisions, trade-offs, AI use if any, success signals).
3. KEYS: is the app live (status wording "In build")?
4. Lazy Stash: calendar dates for the 14 days; confirm the notes-app caption; blur personal details in screenshots?
5. Replace the raw Figma board images at the bottom of RateAm, AdQua and Petrol Advisory with captioned figures.
6. Verify the LinkedIn and Behance URLs, and check the CV for the removed 30% claim.
7. Translations for the new content (KEYS, Lazy Stash, new diagrams) if multilingual matters.
8. Possible extras offered but not done: swipeable phone gallery on desktop, pull-quote or fact box to fill space beside short text.

---

## Appendix A. Home page text (English, as rendered)

```text
Hi, I’m Judith. I design apps people enjoy. 
A designer who turns complicated, multi-layered problems into useful products people enjoy using. I take a feature from first research and requirement, through motion, to a handoff developers can build without guessing.
Download CV

Product designer and craft lover
✦ EFFORT MAKES YOU ✦

Case studiesProduct design · In buildKEYSKEYS is a community platform for residential estates. I owned the design of its services marketplace end to end, plus community projects and tools for property owners, and wrote the PRDs engineering builds from.Read the case studyPersonal product · Mobile-first web appLazy StashDesigning and building an all-in-one stash, pattern and project companion for knitters and crocheters.Read the case studyFreelance · Mobile app and websiteRateAmTurning technical ISP performance data into a 10-second rating flow and a colour-coded network map.Read the case studyProduct design · App, website and dashboardsAdQuaOne platform connecting brands, manufacturers, retailers and consumers across a consumer app and three dashboards.Read the case studyProduct design · App and station dashboardPetrol AdvisoryA fuel delivery and roadside assistance platform that builds trust in a brand-new behaviour.Read the case study

Where I’ve worked

Mar 2025 – Oct 2026KEYS · Product Designer+

What it wasA PropTech and community management ecosystem connecting residents, vendors, property owners and administrators.
What I owned
Services and marketplace. Service recommendations (including AI-driven), vendor onboarding, services homepages for customers and vendors, and communal services.
Community and engagement. Events, clubs, stories and LIVE, chat, comments and reactions, blogs, feeds, news and polls, plus public web pages for events, clubs and vendors.
Finance and administration. Wallet, budget, sink fund, committee board, projects, car parking and voting.
Property owner operations. Onboarding and dashboards for developers, landlords and self-managed committees, plus staff modules.
How I worked
Product and design, together. I worked across UI/UX and product management: designing mobile and web interfaces while writing PRDs for service recommendations, projects and car parking, mapping flowcharts, and defining the logic behind voting and AI recommendations.
Design system. I built and maintained the Figma design system: components, spacing tokens and interaction states. That meant designers and developers worked from the same building blocks.
Mobile to web. I built and refined iOS and Android features through 2025, then architected and expanded the full web platform in 2026, including onboarding, feeds, news, projects and AI services.
Leadership. I onboarded new teammates, ran design syncs and prepared thorough cleanups and handovers.
The system
One platform, many roles. Residents, vendors, property owners (developers, landlords and self-managed committees) and staff, across mobile and web, with public links for non-users.
Three core modules. Governance and operations (projects, committee boards, car parking, sink funds, budgets), social and interactive (chat, events, clubs, blogs, stories, LIVE, feeds), and commerce and services (service matching, AI recommendations, wallets, vendor onboarding).
View on LinkedIn

Oct 2024Quebit Group · Product Designer+

The jobLed UI/UX for web and mobile applications on a short contract with a Canadian team.
What I didDefined scope with stakeholders, validated concepts and iterated quickly, keeping cross-platform consistency and accessibility.

Feb – May 2024RateAm · Freelance Product Designer+

The jobDesigned a marketing website and companion mobile app to turn mobile web visitors into app downloads.
What I didCreated responsive, mobile-first designs optimised for low-bandwidth connections.

Feb 2023 – Jan 2024SwiftAlly · UI/UX Designer+

SwiftVoteLed the full website redesign, with clearer information architecture and visual hierarchy around the core voting features.
SwiftReviewDesigned a CMS interface for editor efficiency and clear task flows for non-technical content teams.
SwiftPollDesigned a survey tool alongside the other two products.
HandoffRan iterative reviews with developers to keep visual fidelity through launch.

Certificates
My academic and professional training, backing up my hands-on product design work: a computer science degree, plus recent short courses in different fields.

AI Fluency: Framework & FoundationsAnthropicUnroll ↓
B.Sc. in Computer ScienceUniversity of Nigeria · 2024Unroll ↓
Basics of Information SecurityCambridge International Qualifications · 2026Unroll ↓
Introduction to Generative Engine Optimisation (GEO)OpenLearn Create · 2026Unroll ↓

←→

The person behind the pixels

Bubbly, curious and logical. I love people, and it shows in my research: I ask a lot of questions, then turn the answers into clear requirements.
I’m confident in my work because I can explain every decision. I learn new tools quickly (I now make illustrations with AI and build element animations in Jitter), and I will always choose a pastel.

How I work

1ResearchTalk to users, audit competitors, test usability.
2Write the PRDTurn findings into requirements everyone signs off.
3Design and animateFlows, UI, systems and motion, mobile first.
4Hand offSpecs and states developers can build without guessing.

Side questsY Hacker News Home Page RedesignA cleaner, more intuitive homepage with simpler navigation and better content accessibility, keeping the features people rely on.View on BehanceW3Schools Course Page RedesignA UX case study adding a sandbox with live previews, so students can practise without a separate code editor.View on BehancePractice BriefsA mobile app giving designers quick access to practice briefs. My first solo project, designed end to end as the UI/UX designer.View on Behance3D Social Media Icons PackOver 20 high-quality icons designed in Adobe Illustrator, free on the Figma Community.Get it on FigmaPenCrib Landing PageA landing page for a web app that organises and structures documents, so nobody has to sort them by hand.View on BehanceJelly Design System v1.0Versatile button components built with Auto Layout in Figma, free on the Figma Community.Get it on Figma

Y Hacker News Home Page Redesign

A cleaner, more intuitive homepage with simpler navigation and better content accessibility, keeping the features people rely on.

View on Behance
W3Schools Course Page Redesign

A UX case study adding a sandbox with live previews, so students can practise without a separate code editor.

View on Behance
Practice Briefs

A mobile app giving designers quick access to practice briefs. My first solo project, designed end to end as the UI/UX designer.

View on Behance
3D Social Media Icons Pack

Over 20 high-quality icons designed in Adobe Illustrator, free on the Figma Community.

Get it on Figma
PenCrib Landing Page

A landing page for a web app that organises and structures documents, so nobody has to sort them by hand.

View on Behance
Jelly Design System v1.0

Versatile button components built with Auto Layout in Figma, free on the Figma Community.

Get it on Figma

Let’s build something together.
Product-led teams hiring remotely, on site or with relocation: say hello.
onwumerejudith@gmail.com

Bē
```

Diary overlay (shown after winning the game):

```text
Close
✿♥★♪✦♡✿♥★♪✦♡✿♥★♪
Judith’s secret diary ✿
You beat the board, so you get the good stuff. Welcome to my world.
Hello, you
Helllllllllllo, Judith here ✿ I debated including this section because this is a professional portfolio, but I think it helps to know the kind of person I am before working with me. My portfolio is not just a reflection of my work but also an embodiment of me as a person. This is who Judith is when she’s not behind a computer screen for work, hehe ^_^
Games I likeTemple Run 2 (girl just likes to run, don’t judge)Strategy games of any kind
On my screenSeries: At 25:00, In Akasaka
In my earsFavourite artist: BTSFavourite genre: Everything
My work playlist♪♫♬✿NOW SPINNINGJudith’s work playlistThe songs I design to.▶ Play on Spotify
More of me
```

---

## Appendix B. Case study text (English)

### KEYS (`keys`)
- Card tag: Product design · In build
- Subtitle: Turning a residential community into a local economy
- Card blurb: KEYS is a community platform for residential estates. I owned the design of its services marketplace end to end, plus community projects and tools for property owners, and wrote the PRDs engineering builds from.

Full rendered English text (headings, cards, captions and diagram labels as the visitor reads them):

```text
← All case studies
Product design · In build
KEYS

Turning a residential community into a local economy

Role
Product Designer, one of several on the team, each owning separate features
Scope
Services marketplace, community projects and property-owner tools, across mobile and responsive web, with the PRDs for each
Timeline
Mar 2025 – Oct 2026 · 19 months · In build
Industry
PropTech and community management
11
PRDs authored
3
platforms: iOS, Android and responsive web
8
user types
2
apps: resident and service provider

KEYS is in build, so there are no launch metrics yet. This study focuses on decisions and how I’d measure success. It’s about a 6-minute read, and I’m happy to walk through the work in more depth in an interview.

Context

KEYS is a community and services platform for residential estates, being tailored for the UK and European markets (the US market was also researched). Residents use it for community news, clubs and events, voting and booking local services. Committees use it to run their estate, and developers and landlords use it to manage their properties. The core product is a mobile app on iOS and Android, with a responsive web platform added for people who prefer a browser.

Communities were full of needs, skills and spare space, but nothing connected them
Residents had no trusted, quick way to find a local cleaner, repairer or childminder.
Local businesses, many not yet on KEYS, couldn’t see demand on an estate or reach residents.
Committees could propose estate projects but had no structured way to approve, fund, staff and track them.
Residents with a spare parking space had no safe way to rent it to neighbours.

What made it hard: every feature served several user types with different permissions and incentives, across two apps (resident and service provider) and later the web. Money, trust and governance were involved, so the rules had to be firm without making the experience feel heavy.

My role
I owned: design and PRDs for Service Recommendations, Services Home (customer, business and SME vendor), Car Parking, Projects, Property Owner Onboarding and the Developer Dashboard. I also made the Projects and Services flowcharts and the notification and email logic for my features.
I shaped: Team Management for property owners and a later Service Recommendations revision (both co-written), brand email sign-off, and onboarding new designers to the team.
Reporting and tools: I reported to the design team lead and the project manager, and worked in Figma, Jitter and Claude.
Every feature served two sides that wanted different things
Feature
Side A wants
Side B wants
The tension
Service Recommendations
Residents: a trusted provider, fast, at a fair price
Vendors (on KEYS or not): more jobs, with little effort to join
Trust needs checks, but checks slow down someone who needs help now
Car Parking
Renters: a flexible daily spot, or a reliable monthly one
Listers: steady income and protection for their space
Daily and monthly renters compete for the same spot
Projects
Committee members: control, accountability, approved budgets
Residents: a voice, and a way to donate or volunteer
Open participation versus financial governance
Property owners
Developers: portfolio-scale tools
Landlords and self-managed committees: a simple setup
One front door for three very different organisations

I organised every PRD by role (“resident as requester”, “resident as referrer”, “applicant”) so engineering always knew whose problem each rule solved.

19 months at a glance

Services ran through all 19 months; web and property owners came last.

2025
2026
M
A
M
J
J
A
S
O
N
D
J
F
M
A
M
J
J
A
S
O
COMMUNITY
Documents
Events and Clubs
Notifications, chat, budget, posts
Comments, committee board, blog, sink fund
Stories and LIVE
SERVICES
Service Recommendations V1
Services home and wallet
Vendor onboarding
Recommendations PRD and revision
Services Home and PRDs
Car Parking and PRD
PROJECTS
Projects, flowcharts, PRD
WEB PLATFORM
Feed, projects, services, AI recommendations
Share pages and loading states
PROPERTY OWNERS
Onboarding, dashboard, team
Design handover
Services is the thread through the whole period. Community work shows range early on; property owners show the move into B2B web tools.
Three decisions
Decision 1
STRATEGIC
Every service request became a way to grow the vendor side

The question. When a resident asks for help, who should they see if the best local providers aren’t on KEYS yet?

AShow only KEYS vendors

Simple and trusted, but results are thin while the marketplace is young.

BLink out to search results

Useful to residents, but KEYS loses both the booking and the vendor.

C
CHOSEN
Blend several sources in one place

Neighbours’ recommendations, platform-ranked suggestions and direct applications from vendors, with off-platform vendors invited in.

Why. Neighbours’ picks build trust, ranked suggestions give a fallback when no one has answered, and applications give vendors a reason to keep checking. When a resident contacts a provider who isn’t on KEYS yet, that provider is invited to join, so each request also helps grow the marketplace.

The cost. More onboarding paths for vendors arriving from outside the app. I kept this manageable by designing a lightweight web entry point that lets a new vendor see the request and then moves them into the app to do the work.

How I would measure it. Response rate within the window · share of invited vendors who join · requests that end in a booking

What I changed in the revision

I doubled the vendor response window, so vendors had enough time to actually engage with a message, and widened the search radius, so vendors could reach a larger pool of customers.

New request
Category
Send
Request detail
Neighbours
Suggested
Applied
Vendor A
Vendor B
Chat
Book
1 Ask
2 Compare three sources
3 Talk and book
One request, three sources of trust
Decision 2
STRUCTURAL
Money changes the rules, so free projects move fast and funded ones need more checks

The question. How do you let any resident propose an estate project without letting community money move unchecked?

AOne flow, approval on everything

Safe, but slow for something as simple as a litter-pick.

B
CHOSEN
Split the flow by funding

Free projects launch right after approval. Funded projects carry extra checks at every step.

Why. The risk sits in the money, not in the project, so the guardrails sit there too. Funded projects need a broader committee, can draw only a limited share of community funds, and return donations if they don’t reach their target. Changing a project’s funding sends it back for approval, and stepping away from a funded project needs sign-off.

The cost. More project states to design and explain. I kept them manageable with one card pattern whose status and main action change by state and by the viewer’s role.

How I would measure it. Proposals that reach launch · time from proposal to approval · share of funded projects that hit their target

Proposal
Vote
Approved
Launched
Completed
Crowdfunding
Launched
Completed
Free
Funded
funding changed
One card pattern, three states
Vote
Vote
Crowdfunding
Donate
Launched
View
One card pattern carries every project state
Decision 3
DETAIL
Hybrid parking by default, with a booking limit that protects monthly renters

The question. Should a parking spot be rented by the day or by the month?

AMonthly only

Steady income, but spots stay empty when no one commits.

BDaily only

Flexible, but income is unpredictable.

C
CHOSEN
Hybrid by default

Listers can still choose monthly only or daily only.

Why. Hybrid gives listers the most use of their space without extra work. A lister sets one price and the other is worked out for them.

The cost. Daily bookers could take dates a monthly renter needs. I limited how far ahead one-off bookings can be made on hybrid spots, so recurring renters keep priority.

Details. Readable spot names are generated from the spot type plus the lister’s own label. Form fields appear only when they apply to the spot type. Listers prove ownership before a spot goes live.

How I would measure it. Occupancy per spot · share of hybrid listings · renter disputes over dates

New listing
Rental type
Hybrid
Monthly
Daily
Price
£—
Save
One-off booking
M
T
W
T
F
S
S
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
Open to book
Not yet open
One price, two ways to rent, and a calendar that protects monthly renters
Not every call went my way

Some of my proposals weren’t taken forward at the time. That’s a natural part of working in a team that is balancing many priorities and constraints. In a few cases, the problems those proposals were meant to address came up again months later, and we revisited the idea together.

What I took from it: I now write the risk and the reasoning into the PRD, not just the solution, so a declined idea can be picked up quickly when the problem shows up. I also try to back proposals with a quick prototype or test early.

The solution

Each flow is shown as an abstract recreation, captioned with the decision it answers.

Customer
Vendor
Upcoming booking
Recommended
Requests
Quick actions
One marketplace, two homepages
What type of property owner are you?
Developer
Landlord
Self-managed
committee
Dashboard
Setup progress
Three breakpoints
Desktop
Tablet
Mobile
Three organisations, one front door
Empty comments
Locked comments
Loading (web)
Try instead
Expired request
Empty dashboard
Confirmation
The states most portfolios skip
Built to be handed over
11 PRDs, each organised by user role, with state tables, permissions, notification triggers and user stories.
Flowcharts for Projects and Services, made before the high-fidelity designs.
Notification and email logic for Service Recommendations and Projects.
Onboarded new designers to the team in January 2026.
Synchronised and cleaned up the design files for handover in September 2026.
Overview
Roles
Flows by role
States
Permissions
Notifications
User stories
Every PRD followed the same role-first structure
Beyond the app
Responsive web: onboarding, feed, updates, news, polls, projects, community, Services Home and AI service recommendations. Property-owner tools were designed for desktop, tablet and mobile.
Shareable web pages for events, clubs and vendor profiles, so links shared outside the app work for people who don’t use KEYS.
Brand email sign-off.
Working with AI to move faster

I used AI on KEYS wherever it removed repetitive work, and kept the thinking and the decisions mine.

Task
Tool
How I used it
PRDs
Claude
I write each feature screen by screen in my own words, explaining every interaction. Claude turns it into a professional document.
Screen drafts
Figma Make and Figma Agent
I gave them the design library and reference images so the low-fi screens it generated matched the KEYS style.
Design clean-up
Figma Agent
Renaming layers and fixing padding in one prompt instead of by hand.
Desktop and tablet
Figma Agent
Desktop and tablet versions of the mobile screens, made faster.
Illustrations
Google Flow
Custom illustrations, which saved a lot of time.

The interaction logic and every decision above are mine. AI handled the formatting and the repetitive production, which left more time for the thinking.

How I’d measure success

KEYS is still in build, so these are the signals I designed each feature to move.

Feature
What success looks like
Signal
Service Recommendations
Residents find help, and new vendors join
Response rate · invited vendors who join · requests that end in a booking
Services Home
Vendors come back daily and post
Daily vendor visits · posts per vendor · booking conversion
Projects
Ideas become delivered projects
Proposals that launch · funded projects that hit target
Car Parking
Spare spots get used
Occupancy per spot · repeat renters
Property owners
Owners finish setup on their own
Setup completion rate · time to first community linked
Reflection

KEYS is a product I genuinely enjoyed working on. It solves a real, everyday problem: how people who live near each other find trusted help, share resources and run their community together. It also called for properly user-centred design. Residents, vendors, committees and property owners each want different things, so every feature needed rules that worked for all of them without favouring one side.

Design for every side at once. Writing down the tension between user groups early made later decisions about permissions, incentives and notifications easier to make and to defend.

Get KEYS on Google Play
Ask KEYS about working with me

←
Previous case study
Petrol Advisory
Next case study
Lazy Stash
Read it
```

### Lazy Stash (`lazy-stash`)
- Card tag: Personal product · Mobile-first web app
- Subtitle: A craft room in your pocket: one calm place for yarn, tools, patterns and works in progress.
- Card blurb: Designing and building an all-in-one stash, pattern and project companion for knitters and crocheters.

Full rendered English text (headings, cards, captions and diagram labels as the visitor reads them):

```text
← All case studies
Personal product · Mobile-first web app
Lazy Stash

A craft room in your pocket: one calm place for yarn, tools, patterns and works in progress.

Role
Product designer and prompter: I wrote the specs, the AI wrote the code
Scope
The whole product: design, data model, themes and behaviour, built in Google AI Studio
Timeline
14 days, paced by AI Studio’s 24-hour reset window
Industry
Crafts and hobbies (crochet and knitting)
14 days
to build in Google AI Studio
PWA
a progressive web app, so no app store
100+
balls of yarn and 100+ patterns in my own stash
1 user
so far, me, so there are no usage metrics

Lazy Stash is a personal project and a working PWA you can try. Everything here is about decisions and how I directed the AI, not user results.

Crafters’ stash lives in too many places

Fibre artists run their hobby across storage bins, printouts, notes and memory. Yarn gets bought twice, row counts get lost, and gauge details go missing.

Two principles shaped everything I specified. First, crafters’ hands are busy, so the product has to work without looking at it. Second, a stash is only useful if you can see what you own before you buy more.

BEFORE
AFTER
From scattered notes to one place for the whole stash.
Directing an AI build

AI Studio’s model needed very precise instructions, so I wrote prompts the way I write PRDs: exact behaviour, exact data fields and the exact look I wanted. Because of AI Studio’s 24-hour reset window, the build took 14 days.

1 · I write the spec
Design, data model,
themes and behaviour
in exact detail
2 · AI Studio builds
It generates the app
from my prompts
(a PWA)
3 · I test it
Run it, find what
the AI got wrong
4 · I correct
A sharper, more
specific prompt,
then rebuild
Repeat until it behaves
14 days to build: AI Studio’s 24-hour reset window set the pace
1
2
3
4
5
6
7
8
9
10
11
12
13
14
How the build worked: I specified, AI Studio generated, and I corrected.
PROCESS DIAGRAM
The PDF import problem

The clearest example was PDF pattern import. The app extracts text from a pattern PDF to fill in the new-pattern form, and the AI kept reading that text wrongly and putting the wrong words in the wrong fields.

Pattern PDFs describe hook sizes, yarn and materials in free text, so the model had to decide which words belonged in which field.

I fixed it by giving the model a list of keywords and what each one means.

The lesson carried through the whole build: when the AI misreads something, the answer is a more precise instruction, not a longer one.

The PDF pattern says
Hook: 3.5mm and 5mm
Text extracted from the PDF
to fill in the new-pattern form
First attempt
Field
wrong text ✕
Field
wrong text ✕
The AI misread the extracted text
After my keyword rules
Field
Hook: 3.5mm ✓
Field
Hook: 5mm ✓
Both hooks selected correctly
My fix: a prompt with a list
of keywords and what each
one means. For example,
“hook: 3.5mm and 5mm” = select
the 3.5mm hook and the 5mm hook.
The pattern viewer with its Extract button, and how the keyword rules fixed the misreading.
Three decisions
Decision 1
STRUCTURE
A dashboard that answers “what do I own?”

The question. What should a crafter see first when they open the app?

AA plain list of yarn

Everything is there, but you have to scroll and count to know what you have.

B
CHOSEN
A dashboard of totals

Total balls, yarn weight, hooks and needles, supplies, projects, a Low Stock card and a shopping list, with four quick-add actions above.

Why. The original problem was buying yarn twice, so the first screen answers “what do I already have?” before anything else.

The cost. The totals are only as good as the data, so adding something had to stay one tap away.

The dashboard, and the yarn list it leads to.
Decision 2
INTERACTION
A counter built for busy hands

The question. How do you count rows when your hands are holding hooks and yarn?

AStandard-sized controls

Fine at a desk, easy to miss mid-row.

B
CHOSEN
One big target

A large +1 Row button, with −1, +5 and Reset beneath it, a segment for each part of a pattern (Main Body, Brim), a screen-awake toggle and haptic feedback.

Why. The product has to work without looking at it.

The cost. Less information fits on screen, so everything secondary sits behind a small control.

The row counter, connected to a project.
Decision 3
STRUCTURE
Pattern, tutorial and materials in one place

The question. Should the pattern live inside the app or stay a separate file?

AKeep PDFs and videos outside the app

Simple to build, but crafters switch apps mid-project.

B
CHOSEN
A built-in pattern library

Recommended hook, yarn ply and yarn needed, the materials list, the PDF and an in-app YouTube player on one screen.

Why. Hook size, yarn and the tutorial stay in context, so a project can be picked up again without hunting for notes.

The cost. A PDF reader is a lot of surface to build, and it is where I hit the text-extraction problem above.

A pattern with its materials, PDF and tutorial video.
Not every call went my way

Two features were cut because of limits in the tools, not because the ideas were wrong.

1Online sync, cut

The AI struggled to implement database sync with Firebase Studio on my current plan.

→
INSTEAD
Export and import

Users export their data and import it manually, so nothing depends on a server.

2Video patterns, cut

Videos were being imported into the app instead of read from the device, so one video sat in two places on the user’s device. As a PWA, the app can’t read them in place.

→
INSTEAD
Written and PDF patterns, plus YouTube links

Patterns stay in one place and the user’s storage isn’t doubled. Tutorials play from YouTube instead.

The solution

Lazy Stash on a phone and on desktop: stash, projects, patterns, supplies and settings.

The core screens on a phone: projects, patterns, supplies and settings.
DASHBOARD
PATTERNS LIBRARY
The same app on desktop.
How I’d measure success

I’m the only user so far, so these are the signals I’ll track once other crafters try it.

Feature
What success looks like
Signal
Dashboard
Crafters know what they own before they buy
Duplicate yarn bought (self-reported) · Low Stock cards acted on
Adding items
Adding something feels effortless
Time to add a yarn or supply
Counter
Makers trust it mid-row
Counter use per project · lost-count reports
Pattern reader
Patterns stay in one place
Projects started from a saved pattern
Reflection
Physical hobbies demand physical-first design. A big thumb target and a screen that stays awake matter more than extra detail.
Weaker tools need sharper specs. Writing prompts like requirements, with exact behaviour and keyword lists, is what made AI Studio build what I meant.
Constraints are design material. Cutting sync and video kept the scope honest and the app simple.
What’s next: put it in front of other crafters and replace these hypotheses with real numbers.

Try Lazy Stash

←
Previous case study
KEYS
Next case study
RateAm
Read it
```

### RateAm (`rateam`)
- Card tag: Freelance · Mobile app and website
- Subtitle: Making ISP performance visible, so people can choose providers and places with reliable connectivity.
- Card blurb: Turning technical ISP performance data into a 10-second rating flow and a colour-coded network map.

Full rendered English text (headings, cards, captions and diagram labels as the visitor reads them):

```text
← All case studies
Freelance · Mobile app and website
RateAm

Making ISP performance visible, so people can choose providers and places with reliable connectivity.

My role
Product designer (freelance), Feb – May 2024
Scope
Mobile app and marketing website
Focus
Rating flow, network map, shared design language
Constraint
Low-bandwidth, mobile-first
74%
of surveyed users hit network issues regularly
~₦3,500
average monthly mobile spend per user in 2024 (above ₦5,000 by 2025)
68%
would check network quality before moving
Under 10 sec
to submit a rating

Survey percentages come from my own user research. The ₦3,500 figure reflects 2024 spending; by 2025, average monthly spend per user had passed ₦5,000 (MTN and Airtel ARPU reports).

The problem

Internet users in Nigeria pay for connectivity they cannot judge in advance. RateAm lets people rate ISPs on call quality and data speed, and view a network map that shows where service is dependable.

Without RateAm
Pick a provider or a place to live
Nothing shows how reliable the network is there
Pay for the connection
About ₦3,500 a month per user in 2024
Find out the hard way
74% of surveyed users hit network issues regularly
With RateAm
People rate their provider
Call quality and data speed, in under 10 seconds
Ratings become a colour-coded map
Quality by area, readable at a glance
Choose with evidence
68% would check network quality before moving
Paying for connectivity you cannot judge in advance, and what RateAm changes.
PROBLEM MAP
Research and insight

Survey data showed regular network problems for most users and a clear appetite for transparency. The roughly ₦3,500 average monthly spend (a 2024 figure) made the cost of a poor choice obvious, and two thirds of users said they would use the app to assess an area before relocating.

Regularly hit network issues
74%
Would check network quality before moving
68%
Average monthly mobile spend per user
₦3,500 → ₦5,000+
2024
2025
The three survey findings behind the product.
SURVEY DATA
Key design decisions
Rating in under 10 seconds. A short, forgiving flow, because a rating nobody finishes is no data at all.
Colour-coded network map. Technical performance metrics become an instantly readable picture of quality by area.
One design language, two platforms. A shared system unified the app and the website, and the mobile-first, low-bandwidth approach drove the website’s conversion path to app downloads.
Under 10 seconds, start to finish
Choose your provider
Rate call quality
Rate data speed
Submit
The rating flow, kept short and forgiving so people finish it.
SIMPLIFIED FLOW
Dependable
Mixed
Weak
Technical performance metrics become a picture of quality by area.
ILLUSTRATIVE MAP
Impact

Users could make informed choices about providers and places. ISPs received data-driven feedback, and communities gained evidence to argue for better infrastructure.

What I learned

Data transparency changes behaviour only when it is legible. The design work was translation: turning technical signals into something anyone can act on.

←
Previous case study
Lazy Stash
Next case study
AdQua
Read it
```

### AdQua (`adqua`)
- Card tag: Product design · App, website and dashboards
- Subtitle: Turning bottled water into a mobile advertising medium, with ordering, recycling rewards and partner dashboards.
- Card blurb: One platform connecting brands, manufacturers, retailers and consumers across a consumer app and three dashboards.

Full rendered English text (headings, cards, captions and diagram labels as the visitor reads them):

```text
← All case studies
Product design · App, website and dashboards
AdQua

Turning bottled water into a mobile advertising medium, with ordering, recycling rewards and partner dashboards.

My role
Product designer
Scope
Consumer app, partner website, dashboards
Users
Consumers, manufacturers, brands, retailers
Research
Nigerian bottled water market analysis
₦938.6bn
Nigerian bottled water sales in 2016 (Euromonitor); far larger today
63%
prefer brands with visible sustainability efforts
72%
of manufacturers want advertising partnerships
3
dashboards for three distinct workflows

Survey percentages come from my own research. ₦938.6bn is the 2016 off-trade bottled water total reported by Euromonitor, the latest naira total I could verify; the market is far larger today.

The problem

AdQua connects brands with water manufacturers so bottles become a mobile advertising medium, while consumers and retailers buy and recycle through the same platform. The challenge was serving four audiences with different goals without building four disconnected products.

One platform, four audiences
Brands
Run campaigns
Manufacturers
Inventory and sales
Consumers
Order, recycle, earn points
Retailers
Restock at direct prices
Ad campaigns
Distribution insight
Direct orders
Recycled bottles
Stock at manufacturer-direct prices
Bottles
Who pays, who gains and what moves between the four audiences.
ECOSYSTEM DIAGRAM
Research and insight

I analysed sales volumes and pricing trends in the Nigerian bottled water industry. Consumers favoured brands with visible sustainability initiatives, and most manufacturers were keen to offset production costs through advertising partnerships. Together these shaped both the rewards system and the partner proposition.

Consumers who prefer brands with visible sustainability efforts
63%
Manufacturers who want advertising partnerships
72%
₦938.6bn
Nigerian bottled water sales in 2016 (Euromonitor), and the market is far larger today.
The research behind the rewards system and the partner proposition.
MARKET RESEARCH
Key design decisions
Consumer app. Ordering direct from manufacturers or retailers, points-based recycling rewards, and a water intake tracker that adds a healthy habit.
Role-specific dashboards. Manufacturers manage inventory, campaigns and sales trends. Brands run campaigns with real-time distribution insight. Retailers restock at manufacturer-direct prices.
Sustainability built in. Recycling is part of the core loop, not a bolt-on.
A website that sells the idea. Interactive feature demonstrations help prospective partners understand the model quickly.
BROWSE
CHOOSE
ORDER
SUBSCRIBE
Ordering in the consumer app: browse, choose, order and subscribe.
Manufacturer
Inventory
Campaigns
Sales trends
Brand
Run campaigns
Real-time distribution insight
Retailer
Restock at manufacturer-direct prices
Three dashboards for three distinct workflows.
SIMPLIFIED WIREFRAME
See how it works
Ordering
Recycling rewards
Dashboards
Interactive feature demonstrations help prospective partners understand the model quickly.
SIMPLIFIED WIREFRAME
Impact

Brands gain an affordable way to reach diverse audiences. Consumers get affordable water and a gamified way to recycle. Retailers restock more cheaply, and manufacturers earn through ad partnerships and direct sales.

What I learned

Good platform design balances function and emotion. Pairing practicality with sustainability made the product more than a service.

←
Previous case study
RateAm
Next case study
Petrol Advisory
Read it
```

### Petrol Advisory (`petrol-advisory`)
- Card tag: Product design · App and station dashboard
- Subtitle: Bringing fuel to people: virtual fuel storage, delivery or pickup, and roadside help, with a dashboard for partner stations.
- Card blurb: A fuel delivery and roadside assistance platform that builds trust in a brand-new behaviour.

Full rendered English text (headings, cards, captions and diagram labels as the visitor reads them):

```text
← All case studies
Product design · App and station dashboard
Petrol Advisory

Bringing fuel to people: virtual fuel storage, delivery or pickup, and roadside help, with a dashboard for partner stations.

My role
Product designer
Scope
User app and partner station dashboard
Research
Online research and in-person interviews
Challenge
Trust in a new service category
68%
interested in fuel delivery to avoid queues
400+
vehicles a day at an average urban station (my estimate)
73%
prioritise tow truck and mechanic add-ons

Percentages come from my own survey and interviews. The 400+ vehicles figure is an estimate from station research, not an official statistic.

The problem

Traditional fuelling means long queues and lost time. Petrol Advisory lets people buy fuel in advance, store it virtually, and have it delivered or collect it, while giving stations the tools to run the operation.

What I did
Online research
In-person interviews at fuel stations
What I learned
Queues and lost time drive interest in delivery
Emergency add-ons matter almost as much
A new service means trust is the problem
What I designed
Virtual tank, delivery or pickup
Tow truck and mechanic requests
Trust through transparency
From station research to product decisions.
RESEARCH TO DESIGN
Research and insight

I combined desk research with in-person interviews at fuel stations. Queues and time pressure drove interest in delivery, and users valued emergency add-ons such as tow trucks and mechanics almost as much. Because fuel delivery is new, trust became the central design problem.

Interested in fuel delivery to avoid queues
68%
Prioritise tow truck and mechanic add-ons
73%
400+
vehicles a day at an average urban station (my estimate, not an official statistic).
The three findings that shaped the product.
RESEARCH FINDINGS
Key design decisions
Virtual tank. Buy fuel in advance, store it securely and redeem it when needed, explained step by step for first-time users.
Service requests. Tow truck and mechanic ordering with real-time tracking and status updates.
Delivery or pickup. Flexible fulfilment with clear pricing and time estimates.
Trust through transparency. Live delivery tracking and a clean, professional interface with subtle credibility cues.
Station dashboard. Order management, live fuel stock monitoring and analytics on sales, delivery efficiency and customer satisfaction.
1 · BUY
2 · STORE
3 · FIND
4 · REDEEM
The virtual tank journey for a first-time user: buy, store, find a station and redeem.
In the app
Live delivery tracking
Tow truck and mechanic requests
Real-time tracking and status updates
Clear pricing and time estimates
On the station dashboard
Order management
Live fuel stock monitoring
Analytics
Sales, delivery efficiency and customer satisfaction
Both sides of the delivery: what the customer sees and what the station runs.
SIMPLIFIED WIREFRAME
Impact

Users get faster fuelling and dependable roadside help. Stations run more efficiently and sell more, and fewer idling vehicles in queues means lower emissions.

What I learned

Logistics-heavy products succeed when complexity stays behind the screen. Research and a deliberate trust strategy shaped every flow.

←
Previous case study
AdQua
Next case study
KEYS
Read it
```


---

## Appendix C. Key code to reuse

### C1. Layout and component CSS added during this chat

```css
.lsec{margin-top:clamp(48px,6vw,72px)}.lsec .txt>h2:first-child{margin-top:0}.lsec .txt h2{margin-bottom:18px}.lsec .txt p{margin:0 0 16px}.lsec .lsh{font-size:1.35rem;margin:0 0 14px}.lsx{height:clamp(34px,5vw,48px)}.lsx.s{height:22px}.case .cover{margin:0 0 32px}.case .kh{margin:0 0 30px}.case .kh .khg{gap:26px 36px}.case .kchips{margin:0 0 30px;gap:12px}.case .note{margin:0 0 4px}.lss{display:grid;gap:clamp(28px,4.5vw,56px);align-items:center}.lss .lsm{min-width:0}.lss .lsm .txt{max-width:none}.lss.t{grid-template-columns:minmax(0,5fr) minmax(0,7fr)}.lss.d{grid-template-columns:1fr;align-items:start;gap:clamp(22px,3vw,32px)}.lss.d .stgi{grid-template-columns:repeat(var(--n),minmax(0,300px));justify-content:center;gap:clamp(18px,4vw,48px)}.lss.d .stg .ph{max-width:300px}.stg{margin:0;background:#ebe3ff;border:3px solid var(--ink);border-radius:18px;padding:clamp(18px,3vw,30px);display:flex;flex-direction:column;justify-content:center;gap:20px;min-width:0}.stgi{display:grid;grid-template-columns:repeat(var(--n),minmax(0,1fr));gap:clamp(14px,2.4vw,26px);justify-items:center;align-items:center}.stgi.pdf{grid-template-columns:minmax(0,.85fr) minmax(0,1fr)}.stg .ph{display:flex;flex-direction:column;align-items:center;width:100%;max-width:240px}.stg .ph.dk{max-width:none}.stg .ph img{display:block;width:100%;height:auto;border:3px solid var(--ink);border-radius:14px;box-shadow:var(--sh);background:#1b1032}.stg figcaption{margin:0;font-weight:700;font-size:.92rem;text-align:center}.pill{display:inline-block;margin:0 0 10px;padding:3px 12px;border:2px solid var(--ink);border-radius:999px;background:#fff09e;font-weight:800;font-size:.74rem;text-transform:uppercase;letter-spacing:.05em}.dgc{width:100%;max-width:300px;background:#fff;border:3px solid var(--ink);border-radius:14px;box-shadow:var(--sh);padding:12px}.dgc svg{display:block;width:100%;height:auto;min-width:0}.lsd{display:grid;gap:clamp(40px,5vw,60px);margin-top:30px}.lsd .kd{margin:0}.lsec .kd h3{margin:12px 0 16px}.lsec .kd .kq{margin:0 0 22px}.lsec .kd .kdh{margin-bottom:14px}.lsec .kd .kopts{gap:20px;margin:0 0 28px}.lsec .kd .kdp p{margin:0 0 14px}.lsec .kopts{gap:20px}.lsec .kt{margin:26px 0 0}.kv svg.vm{display:none}.stg .dgc svg.vm{display:block}.lss.t.fit{grid-template-columns:minmax(0,420px) auto;justify-content:space-between}.lss.t.fit .stgi{grid-template-columns:repeat(var(--n),auto)}.lss.t.fit .stg .ph{width:auto;max-width:none}.lss.t.fit .stg .ph img{height:var(--ph);width:auto;max-width:none}.lss.t.fit .stg .dgc{width:auto;max-width:none}.lss.t.fit .stg .dgc svg{height:var(--ph);width:auto;max-width:none}@media(max-width:1020px){.lss.t,.lss.d,.lss.d.n1{grid-template-columns:1fr}.lss.d{align-items:center}.stg .ph{max-width:220px}.stg .ph.dk{max-width:none}}@media(max-width:700px){.stgi.g4{grid-template-columns:repeat(2,minmax(0,1fr))}.stgi.g2{grid-template-columns:1fr}.stgi.pdf{grid-template-columns:1fr}.stg .ph{max-width:230px}.kv svg.vd{display:none}.kv svg.vm{display:block;min-width:0;max-width:400px}}
.dg{margin:34px 0;background:#fff;border:3px solid var(--ink);border-radius:16px;box-shadow:var(--sh);padding:clamp(18px,3vw,28px)}.dg figcaption{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap;margin:22px 0 0;font-weight:700;font-size:.95rem}.dgt{border:2px dashed var(--ink);background:#fff09e;border-radius:999px;padding:2px 12px;font-size:.7rem;font-weight:800;text-transform:uppercase;letter-spacing:.05em;white-space:nowrap}.dg h4{margin:0 0 14px;font-size:1.05rem}.cmp{display:grid;grid-template-columns:1fr 1fr;gap:20px}.cmpc{border:3px solid var(--ink);border-radius:14px;padding:18px}.cmpc.a{background:#fff6c2}.cmpc.b{background:#daf8e8}.cmpc h4{margin:0 0 16px}.stp{background:#fff;border:2px solid var(--ink);border-radius:12px;padding:10px 14px;font-weight:700;line-height:1.35;position:relative}.stp small{display:block;font-weight:500;margin-top:3px;opacity:.85}.stack .stp+.stp{margin-top:26px}.stack .stp+.stp::before{content:'↓';position:absolute;left:50%;top:-24px;transform:translateX(-50%);font-weight:900}.hflow>div{position:relative}.hflow>div+div::before{content:'→';position:absolute;left:-26px;top:50%;transform:translateY(-50%);font-weight:900}.hflow{display:grid;grid-template-columns:repeat(var(--n),minmax(0,1fr));gap:34px}.hflow>.stp+.stp::before{content:'→';position:absolute;left:-26px;top:50%;transform:translateY(-50%);font-weight:900}.tlb{margin:0 0 18px;padding:8px 18px;border:3px solid var(--ink);border-radius:999px;background:#b5f0d0;text-align:center;font-weight:800}.brow{margin:0 0 20px}.brow>div:first-child{display:flex;justify-content:space-between;gap:14px;font-weight:700;margin:0 0 7px}.btrack{height:28px;background:#f1f1f1;border:2px solid var(--ink);border-radius:999px;overflow:hidden}.bfill{height:100%;border-right:2px solid var(--ink)}.bsplit{display:grid;grid-template-columns:1fr 1fr;gap:16px}.bsplit span{display:block;font-weight:700;font-size:.85rem;margin:0 0 5px}.call{margin-top:8px;display:flex;gap:16px;align-items:center;border:2px dashed var(--ink);border-radius:12px;padding:12px 16px;background:#fff6c2;font-weight:600}.call strong{font-size:1.5rem;white-space:nowrap}.cols3{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:18px}.cc{border:3px solid var(--ink);border-radius:14px;overflow:hidden;background:#fff}.cc h4{margin:0;padding:10px 14px;border-bottom:3px solid var(--ink);font-size:1rem}.cc ul{margin:0;padding:14px 14px 6px 32px}.cc li{margin:0 0 8px}.mp{display:grid;grid-template-columns:repeat(10,1fr);gap:5px}.mp i{aspect-ratio:1.6;border-radius:8px;border:2px solid var(--ink)}.mp .g{background:#7fe0a8}.mp .y{background:#ffe066}.mp .r{background:#ff8fa3}.lg{display:flex;gap:20px;flex-wrap:wrap;margin-top:16px;font-weight:700}.lg span::before{content:'';display:inline-block;width:14px;height:14px;border-radius:4px;border:2px solid var(--ink);margin-right:8px;vertical-align:-2px}.lg .g::before{background:#7fe0a8}.lg .y::before{background:#ffe066}.lg .r::before{background:#ff8fa3}.bw{border:3px solid var(--ink);border-radius:12px;overflow:hidden;background:#fff}.bwh{display:flex;gap:7px;padding:9px 12px;background:#f1f1f1;border-bottom:3px solid var(--ink)}.bwh i{width:12px;height:12px;border-radius:50%;border:2px solid var(--ink);background:#fff09e}.bwb{padding:clamp(16px,3vw,28px)}.bl{height:14px;border-radius:7px;background:#d9d9d9;margin:0 0 10px}.bl.w60{width:60%;height:20px;background:#bdbdbd}.bl.w40{width:40%}.bbtn{display:inline-block;margin:8px 0 22px;padding:8px 18px;border:3px solid var(--ink);border-radius:999px;background:#ffb3d1;font-weight:800}.bt{display:flex;gap:10px;flex-wrap:wrap;margin:0 0 14px}.bt span{padding:5px 14px;border:2px solid var(--ink);border-radius:999px;font-weight:700;background:#fff}.bt .on{background:#b5f0d0}.bpanel{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}.bpanel div{height:90px;border:2px solid var(--ink);border-radius:10px;background:#ebe3ff}.ecom{display:none}.ecom .stp{margin:0 0 10px}@media(max-width:700px){.cmp,.cols3{grid-template-columns:1fr}.hflow{grid-template-columns:1fr;gap:28px}.hflow>.stp+.stp::before,.hflow>div+div::before{content:'↓';left:50%;top:-26px;transform:translateX(-50%)}.ecod{display:none}.ecom{display:block}.bpanel div{height:60px}.call{flex-direction:column;align-items:flex-start;gap:4px}}

```

### C2. Script that fits screenshot height to text height

```html
<script>(function(){function fitRow(r){var m=r.querySelector('.lsm'),s=r.querySelector('.stg');if(!m||!s)return;if(window.innerWidth<=1020){r.classList.remove('fit');s.style.removeProperty('--ph');return}r.classList.add('fit');var H=m.getBoundingClientRect().height,cs=getComputedStyle(s),pad=parseFloat(cs.paddingTop)+parseFloat(cs.paddingBottom),cap=s.querySelector('figcaption'),ch=cap?cap.getBoundingClientRect().height:0,gap=parseFloat(cs.rowGap)||20,pl=s.querySelector('.pill'),plh=pl?pl.getBoundingClientRect().height+10:0,ph=Math.round(Math.min(520,Math.max(220,H*1.06-pad-ch-gap-plh)));s.style.setProperty('--ph',ph+'px')}function fit(){var rows=document.querySelectorAll('#case .lss.t');rows.forEach(fitRow);rows.forEach(fitRow)}var c=document.getElementById('case');if(c)new MutationObserver(fit).observe(c,{childList:true});window.addEventListener('resize',fit);window.addEventListener('load',fit);if(document.fonts&&document.fonts.ready)document.fonts.ready.then(fit)})()</script>
```

### C3. SVG diagram conventions used on the page
- Ink stroke 3px, pastel fills (#ffb3d1, #d4c2ff, #b5f0d0, #fff09e), rounded rects (rx 10 to 12), arrowheads via a marker per figure with a unique id, font Bricolage Grotesque, text 13 to 18px.
- Wide figures sit in `.kv` with `min-width:640px`; phones get a second vertical SVG (`svg.vd` desktop / `svg.vm` mobile, switched at 700px).
- Figure caption row: `<figcaption><span>caption</span><span class="nda">Tag</span></figcaption>`.

---

## Appendix D. Build and QA process that worked
1. Keep a pristine backup of the page and regenerate the changed section from a script each time, so repeated edits never double up.
2. After each change: syntax-check the main script (node --check), render with Playwright at 1440, 1100, 900, 768 and 390 wide, assert no horizontal overflow and no page errors, then screenshot and review sections.
3. Publish the single-file version with images inlined as base64, then reply to any artifact comments in their thread (do not resolve threads unless asked).
