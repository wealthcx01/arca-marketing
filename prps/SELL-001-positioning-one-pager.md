# PRP — SELL-001-positioning-one-pager

## Intent
The founder gets one written-down paragraph — `context/positioning.md` — that says who ARCA is for,
what it replaces, and why it's better, so every future piece of copy (landing page, emails, decks)
can cite it instead of re-deriving it.

## Context
- `context/README.md` (this repo) — positioning belongs in `context/`, one idea per file, named after
  the idea. No positioning file exists yet; `context/` currently holds only its own README, so there
  is no prior founder-deposited ICP/voice/pricing knowledge to reconcile against or contradict.
- `docs/tickets/SELL-002-early-access-invite-send.md` — already written to cite
  `context/positioning.md`, confirming the expected filename and that downstream tickets depend on
  this one existing.
- `/opt/foundry/lane/arca/CLAUDE.md` — ARCA is "The Bloomberg Terminal for Pokemon Cards": Hono/Bun
  backend, React client styled as a dense trading-terminal (Diamond/Pearl themes), BETA tag visible in
  the header (`client/src/components/Layout.tsx`).
- `/opt/foundry/lane/arca/reference/TRKD-to-ARCA-Design.md` — the product is explicitly modelled on a
  Refinitiv/LSEG market-data terminal (TRKD), mapped tab-for-tab onto card-market equivalents
  (Overview, Sets & Eras, News, Cards, Graded, Watchlist, Screener, Portfolio, Trades, Analytics).
- Shipped capabilities, verified in `/opt/foundry/lane/arca/docs/tickets/`:
  - Multi-source price conflation with per-field source attribution (ARCA-4, ARCA-5) — one resolved
    "best price" instead of comparing listings across sites by hand.
  - Portfolio & holdings engine derived from a BUY/SELL transaction ledger, weighted-average cost
    basis, P&L, CSV import (ARCA-13), plus portfolio-level risk: weighted vol/Sharpe, HHI
    concentration, currency exposure (ARCA-14).
  - ARCA Score, a 0–100 composite (momentum/value/liquidity/risk-adjusted/scarcity) per card
    (ARCA-10), and grading-alpha — graded-vs-raw ROI net of real PSA/CGC/BGS grading fees (ARCA-11).
  - PSA cert verification against the public API, cached (ARCA-16).
  - Watchlists with live conflated pricing (ARCA-19). Session-based auth, single account holds one
    portfolio view (ARCA-20).
- Material limits, also from the same tickets, that bound the claims:
  - Card catalog/pricing coverage is capped at ~1,250 of ~19k cards and currently only refreshes held
    cards; full-catalog and non-held pricing is ARCA-24, **In progress**, not shipped.
  - BYOK keys exist per ARCA-7 (shipped) but multi-user BYOK is ARCA-25, **In progress**.
  - Prices refresh daily, not real-time/tick-by-tick (explicit design choice per the TRKD mapping doc).
  - No grading service, no marketplace/trade execution — ARCA verifies and prices, it does not grade
    or transact.

## Approach
Write a single new file, `context/positioning.md`, following the "one idea per file" convention in
`context/README.md`. No other files change. Content is assembled entirely from what's cited above —
no new capability claims. Where a fact (e.g. exact target price tier, named competitor tools the
audience uses today) isn't establishable from either repo, the PRP author lists it as unresolved in
the PR description rather than inventing it.

Files touched:
- `context/positioning.md` (new)

## Tasks
- [ ] Draft "Who it is for" as a specific collector/investor persona (holds graded and raw cards,
  tracks a portfolio, currently priced across scattered sources) rather than a demographic label.
- [ ] Draft "What they do today instead" — manual comps across TCGPlayer/eBay/PriceCharting-style
  sources, spreadsheets for cost basis/P&L, gut-feel grading decisions — and name where each hurts.
- [ ] Draft the one-sentence "What ARCA is" line in the audience's own words, not internal jargon.
- [ ] Draft the three highest-value capabilities, each paired with the concrete shipped feature it
  traces to (conflated pricing, portfolio/holdings + risk analytics, ARCA Score + grading alpha).
- [ ] Draft "What it is not," explicitly excluding real-time data, full catalog coverage, marketplace/
  trade execution, grading services, and multi-user BYOK, per the in-progress/planned tickets above.
- [ ] Write the PR description flagging anything not resolvable from the repos (e.g. target price
  point, named competitors, brand voice) as open questions rather than filled in.

## Validation gates
- [ ] happy path: `context/positioning.md` exists and, read top to bottom, answers all five bullets
  from the ticket scope (who, what-instead, what-it-is, three things, what-it-is-not) without needing
  another document.
- [ ] edge cases: every capability named in the "three things" section names or implies the shipped
  ticket it traces to (ARCA-4/5 conflation, ARCA-13/14 portfolio, ARCA-10/11 score/grading-alpha), and
  no claim depends on an ARCA ticket whose Status is "In progress" or "Planned" (e.g. full catalog
  coverage, multi-user BYOK, real historical data) without being named as a current limit instead.
- [ ] errors: nothing in the file states a capability that contradicts a ticket's actual scope (e.g.
  no claim of real-time pricing, no claim of grading cards, no claim of trade execution/marketplace
  matching) — a reader cross-checking against `arca/docs/tickets/` finds no mismatch.
- [ ] coverage: the PR description lists every fact the founder would reasonably expect (pricing
  tier, named competitors, brand voice/tone) that could not be sourced from `arca/` or `context/`,
  so nothing is silently guessed.

<!-- foundry-ticket: 9b13f5cf47110920 -->
