# StratX Opt-In Funnel — LIVE

Built 2026-07-20 with the funnel-architect plugin (`agashic-funnel-architect`, installed at user scope).

**Canonical URL: https://stratx-checklist.onrender.com** — Render static site (same platform/account as `app.stratx.tech`, workspace "Strat-X"), deployed from `github.com/TommyAEM/stratx-checklist-funnel` (public repo, auto-deploys on push to `main`).

A second copy also lives at https://stratx-checklist.vercel.app (Vercel, `tommyaem` account) — kept as a live backup, not the one to share. Both were deployed straight from existing authenticated CLIs; no new hosting accounts were created either way.

Lead capture: form posts to `https://formsubmit.co/sales@stratx.tech` (free, no account created — email-based activation only). A test submission was made 2026-07-20 to trigger formsubmit's one-time "Activate Form" email — **check sales@stratx.tech and click the activation link before sharing this URL**, or real leads will silently not arrive.

## Pages

| File | Role |
|---|---|
| `index.html` | Squeeze page — captures email for the lead magnet |
| `thank-you.html` | Confirmation + inline checklist access + Terminal X CTA + community links (Discord + Facebook) |
| `ea-sales.html` | **EA sales page** — Gold X1 (£299), US30 X1 (£199), bundle (£399), Stripe checkout + Vantage 50% offer + community CTAs. **Deployed on Vercel only** (`stratx-checklist.vercel.app/ea-sales.html`) — this is the SALES_URL used in all outreach emails. |
| `downloads/stratx-validation-checklist.html` | The lead magnet itself (print-ready, dark + print stylesheet) |
| `assets/` | Real StratX logo files (copied from StratX-Social/assets) |

## Funnel flow

Traffic (IG/FB/X posts, community group) → squeeze page → email captured → thank-you page → app.stratx.tech wizard.

## Compliance posture (per brand-style.md §4)

- Zero performance figures anywhere in the funnel — education-only positioning, so no backtest-label obligations.
- Risk line in every footer (long form).
- No promises, no signal language ("No spam. No 'buy now' alerts" is explicit).
- UK spelling, approved taglines verbatim, real logo files (no typeset approximation).

## Redeploying after edits

Render auto-deploys on push **when its GitHub webhook is connected** (currently NOT deploying — Render serves an old snapshot; ea-sales.html 404s there. Check Render dashboard: Strat-X workspace → stratx-checklist service → deploys; reconnect the GitHub repo if needed, or re-deploy manually).

Vercel is the working production deploy — run this after every edit to `ea-sales.html` / `index.html` / `thank-you.html`:
```
cd Documents/StratX-Funnel
git add -A && git commit -m "..." && git push
vercel --prod --yes
```

## Still open (not blocking — funnel works today)

1. **Activate formsubmit** (see above) — one click in sales@stratx.tech inbox, first thing.
2. **Render auto-deploy is broken** — GitHub webhook no longer triggers deploys (verified 2026-07-31: file is on GitHub main, Render still serves old snapshot, `/ea-sales.html` → 404). Fix in Render dashboard or migrate fully to Vercel.
3. ~~Discord activation~~ **DONE 2026-08-01** — webhook wired (`discord_community.py` posts via webhook; revival announcement already posted, HTTP 204). Repost anytime: `python discord_community.py announce`.
4. **Custom domain**: currently `stratx-checklist.onrender.com`. To move to `go.stratx.tech`, add a custom domain in the Render service settings and point a CNAME at the target Render gives you — needs Tommy's DNS access wherever stratx.tech's registrar/DNS panel is (nameservers currently `apollo/athena.dns-parking.com`).
5. **Analytics**: no tracking pixel yet — add GA4/Meta pixel before running any paid traffic (plugin has an analytics-setup skill for this).
6. **Upgrade lead capture**: formsubmit.co emails each lead one at a time — fine at low volume. Move to ConvertKit/MailerLite once volume justifies a real list + welcome sequence.
7. **Traffic — this is the actual client-finding step, the funnel just converts it:**
   - Point every StratX-Social post CTA at the checklist URL instead of the bare homepage (`🌐 STRATX.TECH` → swap for the checklist link in bio/CTA)
   - Post the checklist natively in the "StratX Community" Facebook group — it's pure education, fits the group's existing register
   - Pin it in any forex/trading Discord or Skool communities Tommy is already in
   - Once a few leads come in, this is what feeds the outreach pipeline from [[project_outreach_risk_tolerance_by_stage]]

## EA fulfillment — LIVE 2026-08-01

Automated post-purchase email delivery of the EA packages (EX5 + .set files + manual + install
steps + support/Discord/Vantage offer). Flow: Stripe Payment Link → redirect to
`https://engine.stratx.tech/fulfill/?email={CUSTOMER_EMAIL}&p=<product>&k=<secret>` → VPS Flask
service emails the buyer instantly → order logged.

**TODO (needs Tommy, ~2 min, Stripe dashboard):** set the "Redirect after purchase" URL on each
of the 3 Payment Links (Gold/US30/Bundle) — exact URLs in
`Documents/EA-Marketplace-Launch/FULFILLMENT_SYSTEM.md`. Until then buyers only see the Stripe
confirmation page and no email goes out.

## A/B test ideas (from plugin's optin-funnel skill)

- Headline: problem-focused (current) vs solution-focused ("Steal the 7 validation gates…")
- Email-only (current) vs name + email
- With vs without the checklist preview card
