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
  numbers; "we will help you find out before anything is quoted".
- British spelling; no em-dashes in rendered copy; no crutch words.
- The honesty section ("When the community edition is all you need") is
  the family's trust play — do not cut it without recording a deviation.

## Open items

- **Naming: the close motif is "Covered when ready"** (family pattern:
  Merge / Reconcile / Unseal when ready). Provisional — Phil to confirm
  or rename.
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

## Mechanics

- Buildless static: index.html + thanks.html, publish root
  (netlify.toml). Netlify Forms, form name `openbao-support`, fields:
  name, email, company, stage (dropdown), message. No honeypot yet —
  add one if spam arrives.
- Local dev: python http.server via cpsales `.claude/launch.json` entry
  "openbao-enterprise" (port 6002).
