# thearenahub.co.uk — Institutional Site
**TheArenaHub/website-couk** · Updated August 2026

Main institutional site for The Arena Hub Ltd — company, legal, pricing, compliance
pages, plus the public Paradigm research/discussion section. Static HTML/CSS/JS, no
build pipeline.

## Pages — Institutional

| File | Purpose |
|---|---|
| `index.html` | Homepage — product overview, mission, pilot CTA |
| `platform.html` | Platform feature breakdown |
| `pricing.html` | Pricing tiers |
| `compliance.html` | GDPR / ICO compliance statement |
| `company.html` | Company overview, leadership, mission |
| `dpa.html` | Data Processing Agreement (UK GDPR Art. 28) |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms & Conditions |
| `student-hub.html` | Student-facing page |
| `parent-home.html` | Parent-facing page |
| `admin-batching.html` | Performance Centre batching admin tool (separate config) |

## Pages — Paradigm (`/paradigm`)

Public research/discussion section — Observatory (live policy monitoring),
Paradigm (Arena's own research library, rewritten from Jon's published SubStack
articles), Forum (deliberately inert, no live posting). Not a promotional surface
for Arena's commercial products — see `docs/planning/Future_Work/ARENA_PARADIGM_ARCHITECTURAL_REVIEW.md`
in the main file mirror before editing this section.

14+ pages under `/paradigm/`: `index.html`, `library.html`, `document.html`,
`policy.html`, `questions.html`, `conversations.html`, `about.html`,
`observatory/index.html`, `observatory/activity.html`, `forum/index.html`,
`forum/topic.html`, plus `editorial-standards.html`, `evidence-trail.html`,
`explore.html`, `knowledge-map.html`, `publication-methodology.html`,
`roadmap.html`, `trust-centre.html`, `why-paradigm-exists.html`.

## `thearenahub/` subfolder

Separate copies of `index.html`, `login.html`, `app.html`, `success.html`,
`dpa.html`, `privacy.html`, `terms.html` with their own `vercel.json`. Purpose
relative to the main site not fully resolved — not yet wired into the dynamic
config system below. Don't assume dead; confirm before removing anything.

## Tech Stack

HTML / CSS / vanilla JS — no frameworks, no build step, no bundler
Hosting: GitHub Pages (TheArenaHub/website-couk)
Config: GAS Web App → ARENA_SITE_CONFIG Google Sheet

## Dynamic Config

Contact details, pricing, and legal identifiers are not hardcoded — they're served
by a Google Apps Script Web App backed by the `ARENA_SITE_CONFIG` Google Sheet
(`05_Websites` Shared Drive folder). `arena-config.js` fetches on page load and
injects values via `data-config` attributes. If the endpoint is unreachable, all
`data-config` elements are hidden.

**Full key registry, deployment notes, and known gaps:** see `WEBSITE_MANIFEST.md`
in this repo — kept as the single source of truth for config keys rather than
duplicated here, where it can drift out of sync.

**To update any contact detail or price:** Open the `ARENA_SITE_CONFIG` sheet →
⚡ Arena Config → Open Admin Panel → edit → Commit.

## File Inventory

| File/folder | Purpose |
|---|---|
| `arena-config.js` | Dynamic config client |
| `ARENA_SITE_CONFIG.gs` | GAS Web App source (maintained in Apps Script, mirrored here for reference) |
| `patch_html_config.py` | One-time patcher used to inject `data-config` attributes (June 2026) |
| `WEBSITE_MANIFEST.md` | Full key registry, deployment notes, pending issues — read first |
| `*.html` | Institutional pages (see table above) |
| `paradigm/` | Paradigm section — pages, `css/`, `js/`, `data/`, `observatory/`, `forum/` |
| `thearenahub/` | Separate subfolder, purpose unresolved — see above |
| Loose `.jpg` files in root | Page assets (product/pillar card images, tier icons) — not in an `images/` subfolder |

## Deployment Workflow

GitHub Pages auto-deploys from `main`. No build step.
1. Edit HTML structurally — never hardcode contact details, use `data-config` attributes.
2. Commit and push to `main`.
3. To update contact details only: edit the `ARENA_SITE_CONFIG` sheet directly, no HTML change needed.

## Company

**The Arena Hub Ltd** · Company No. 1708605 · Registered in England & Wales
