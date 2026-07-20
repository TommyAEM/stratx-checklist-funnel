# StratX Opt-In Funnel — LIVE

Built 2026-07-20 with the funnel-architect plugin (`agashic-funnel-architect`, installed at user scope).
Status: **LIVE** at https://stratx-checklist.vercel.app — deployed to Tommy's existing Vercel account (tommyaem), Vercel project `stratx-checklist`.

Lead capture: form posts to `https://formsubmit.co/sales@stratx.tech` (free, no account created — email-based activation only). A test submission was made 2026-07-20 to trigger formsubmit's one-time "Activate Form" email — **check sales@stratx.tech and click the activation link before sharing this URL**, or real leads will silently not arrive.

## Pages

| File | Role |
|---|---|
| `index.html` | Squeeze page — captures email for the lead magnet |
| `thank-you.html` | Confirmation + inline checklist access + Terminal X CTA |
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

```
cd Documents/StratX-Funnel
vercel --prod --yes
```

## Still open (not blocking — funnel works today)

1. **Activate formsubmit** (see above) — one click in sales@stratx.tech inbox, first thing.
2. **Custom domain**: currently `stratx-checklist.vercel.app`. To move to `go.stratx.tech`, add the domain in the Vercel project settings and point a CNAME at Vercel — needs Tommy's DNS access at the registrar.
3. **Analytics**: no tracking pixel yet — add GA4/Meta pixel before running any paid traffic (plugin has an analytics-setup skill for this).
4. **Upgrade lead capture**: formsubmit.co emails each lead one at a time — fine at low volume. Move to ConvertKit/MailerLite once volume justifies a real list + welcome sequence.
5. **Traffic — this is the actual client-finding step, the funnel just converts it:**
   - Point every StratX-Social post CTA at this URL instead of the bare homepage (`🌐 STRATX.TECH` → swap for the checklist link in bio/CTA)
   - Post the checklist natively in the "StratX Community" Facebook group — it's pure education, fits the group's existing register
   - Pin it in any forex/trading Discord or Skool communities Tommy is already in
   - Once a few leads come in, this is what feeds the outreach pipeline from [[project_outreach_risk_tolerance_by_stage]]

## A/B test ideas (from plugin's optin-funnel skill)

- Headline: problem-focused (current) vs solution-focused ("Steal the 7 validation gates…")
- Email-only (current) vs name + email
- With vs without the checklist preview card
