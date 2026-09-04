# BUILD-NOTES — Enterprise for OpenBao support landing

The audience is teams ALREADY running OpenBao who are weighing enterprise
support. It is deliberately the opposite psychology to openbao_campaign_1
(Vault migrators): no competitor comparison, no renewal urgency. The sell
is cover, evidence, and a name for the auditor's report.

## Content source of truth

All product facts come from the cpsales customer-success layer
(`src/data/solutions/openbao/customerSuccess.ts`), which carries the
sourcing: LTS releases with vulnerability patching, rapid CVE remediation
with a signed VEX statement per assessment, supply-chain assurance,
optional FIPS 140-3 compliant edition (Level 1, via CMVP Certificate
#5247 — always "compliant", never "validated" or "certified"), named
Technical Account Architect + Customer Success programme, support on the
hardened build or pure upstream, plugin-type scoping (distinct plugin
types, not clusters or client identities; thirteen core plugins standard;
non-core/community supportable as additional scope; all plugins under
contract get the same support levels; NEVER call core plugins
proprietary). Adopters wording is the verified line from
openbao_campaign_1 BUILD-NOTES (resolution logged there 2026-08-21), with
the kicker adapted to this audience ("You are in good company." instead
of "So can you." — this reader already picked OpenBao).

## House rules

- Product name: "Enterprise for OpenBao", never "Enterprise Support for
  OpenBao".
- Support copy stays generic: no SLA or severity tables, no response-time
  promises (nothing about 24/7 or "3am" — unsanctioned).
- No pricing figures. The scoping section describes the model, not
  numbers.
- CVE attribution (Phil, 2026-08-26): never cite the upstream CVE
  count or imply ControlPlane's role in disclosures — 2025 OpenBao
  CVEs were responsibly disclosed by EXTERNAL researchers; ControlPlane
  sits on the patching side. The cp-website FAQ's "5 CVEs" figure is
  also stale (registries show at least six). Our claimable ground is
  the VEX statement and the named response, nothing more.
- British spelling; no em-dashes in rendered copy; no crutch words.
- DEVIATION (Phil, 2026-08-26): the community-is-enough concession is
  FULLY REMOVED from this page family on Phil's instruction — first the
  main-page honesty section, then the thanks-page soft line. Unlike the
  campaign family, this page carries no staying-put concession anywhere;
  reps should still say it in conversation where true, but the page
  no longer volunteers it.

## Open items

- **Naming RESOLVED (Phil, 2026-08-26): the close is "Ready when you
  are"** — a deliberate inversion of the family's "X when ready" motif
  (those pages ask the reader to act; a support page promises the vendor
  stands ready). Closer names the maintainers, not "a company".
- **Hero graphic is borrowed** from openbao_landing (the unseal motif).
  Works, but a support-specific motif (e.g. the seal held closed) would
  differentiate the two pages if the ads ever run side by side.
- **noindex is on** (family default). If this page is meant to be found
  organically rather than fed by ads/outbound, remove it deliberately.
- **Netlify**: site not yet created/wired (Phil-side, like the
  siblings). After first deploy: set the form notification email for
  form `openbao-support`.
- The product-page link in the fine print goes to
  control-plane.io/enterprise-for-openbao/ — verify the URL is still
  live at launch.

## Ad-matched hero (added 2026-09-04)

The hero swaps on `?v=` to match the campaign 2 awareness ads, the same
mechanism as openbao_campaign_1. Default copy lives in the HTML (so no-JS
and crawlers see it); a script at the foot of the page replaces the
eyebrow, h1, strap and pitch when `v` is one of:

- `source` (ad 4, maintainer): "Support from the source".
- `page` (ad 5, pager): "Open source secrets. Covered." The strap asks
  "when it seals, who picks up?" with no clock time and no 24/7, per the
  house rule above. The ad itself says 2am; the page does not.
- `audit` (ad 6, auditor): "The last box on the audit".
- anything else, or nothing: the default "cover" hero.

The form captures `variant` and `utm_source`, `utm_medium`, `utm_campaign`,
`utm_content` as hidden fields, and submit pushes `openbao_support_submit`
with the variant to `dataLayer` (and fires the LinkedIn conversion when
`LINKEDIN_CONVERSION_ID` and the Insight Tag partial exist; neither is on
this page yet). A honeypot field `company-website` is now on the form.

Ad links for campaign 2 should use `utm_campaign=openbao-support` and the
matching `v` so the metrics stay separate from campaign 1.

## Mechanics

- Buildless static: index.html + thanks.html, publish root
  (netlify.toml). Netlify Forms, form name `openbao-support`, fields:
  name, email, company, stage (dropdown), message. No honeypot yet —
  add one if spam arrives.
- Local dev: python http.server via cpsales `.claude/launch.json` entry
  "openbao-enterprise" (port 6002).
