# PRP — SELL-001-positioning-one-pager

## Intent
The founder gets one written-down page, `context/positioning.md`, that says who ARCA is for, what
they do today instead, what ARCA is, and where the promise stops — so every future piece of copy
(landing page, emails, decks) cites it instead of re-inventing it.

## Context
- `context/README.md` (this repo) — positioning belongs in `context/`, one idea per file. `context/`
  currently holds only this README: no founder-deposited ICP, voice, competitor, or pricing knowledge
  exists yet to build on or reconcile against. This ticket is the first entry.
- `docs/tickets/SELL-002-early-access-invite-send.md` — already written to cite
  `context/positioning.md` by name, confirming the filename and that a real downstream ticket is
  blocked on this one.
- `/opt/foundry/lane/arca/CLAUDE.md` — ARCA is "The Bloomberg Terminal for Pokemon Cards": Hono/Bun
  backend, React terminal-styled client (Diamond dark / Pearl light themes), 10 modules (auth, cards,
  portfolio, pricing, performance, analytics, market, news, etl, psa, watchlist).
- `/opt/foundry/lane/arca/reference/TRKD-to-ARCA-Design.md` — the product is deliberately modelled tab
  -for-tab on a Refinitiv/LSEG market-data terminal (TRKD): Overview/movers/ticker, Sets & Eras, Market
  News, Cards, Graded, Watchlist, Screener — each an explicit re-skin of an equity-terminal panel onto
  the card market.
- Shipped capabilities, verified against `/opt/foundry/lane/arca/docs/tickets/` (Status: Shipped):
  - Multi-source price conflation with per-field source attribution across 6 providers, 3 free + 3
    BYOK (ARCA-4, ARCA-5, ARCA-7) — one resolved "best price" instead of comparing listings by hand.
  - Portfolio & holdings engine derived from a BUY/SELL transaction ledger: weighted-average cost
    basis, P&L, CSV import wizard (ARCA-13); portfolio-level risk — weighted vol/Sharpe, HHI
    concentration, currency exposure (ARCA-14).
  - ARCA Score, a 0–100 composite (momentum/value/liquidity/risk-adjusted-return/scarcity) per card
    (ARCA-9, ARCA-10), and grading-alpha — graded-vs-raw ROI net of real PSA $75 / CGC $50 / BGS $100
    grading fees (ARCA-11).
  - PSA cert verification against the public API, cached 30 days (ARCA-16).
  - Watchlists with live conflated pricing (ARCA-19). Session-based email/password auth (ARCA-20).
- Material limits that must bound the claims, also from the same tickets:
  - **Analytics currently run on synthetic history.** `scripts/seed-prices.ts` fetches *real* current
    prices from TCGdex, then fabricates 30 days of price history as a random walk (`jitter()`,
    Box-Muller noise) to seed the series analytics are computed from. ARCA-27 ("Real historical price
    ingestion"), which replaces that random walk with real history, is **Planned**, not shipped. So
    today's ARCA Score, volatility, Sharpe, and trend are real formulas running on a fabricated
    series, not on observed market history — a claim like "see the real risk profile of your cards"
    would overstate what's true right now.
  - Card catalog/pricing coverage is capped at ~1,250 of ~19k cards and only refreshes held cards;
    full-catalog and non-held-card pricing is ARCA-24, **In progress**.
  - Multi-user BYOK is stubbed to one global key, not per-user (ARCA-25, **In progress**).
  - Screener rankings/grouped views and watchlist compare/export are ARCA-41 / ARCA-39, **Planned**.
  - No real-time/tick data (explicit design choice, daily refresh), no grading service, no
    marketplace/trade execution — ARCA verifies, prices and tracks; it does not grade or transact.

## Approach
Write one new file, `context/positioning.md`, following the "one idea per file" convention in
`context/README.md`. Every capability claim is sourced from the shipped tickets above; every claim
that would depend on an in-progress/planned ticket is either left out or stated as a current
boundary, not a feature. No other file changes.

Files touched:
- `context/positioning.md` (new)

## Tasks
- [ ] Draft "Who it is for" as a specific collector/investor (holds graded + raw Pokemon cards across
  multiple sources, tracks cost basis and P&L like a portfolio, cares about grading economics) rather
  than a demographic label.
- [ ] Draft "What they do today instead" — manual price-checking across scattered marketplaces,
  spreadsheets for cost basis/P&L, gut-feel on whether to grade a raw card — naming where each hurts.
- [ ] Draft the one-sentence "What ARCA is," in the audience's words, not internal module names.
- [ ] Draft the three highest-value capabilities, each tied to a shipped feature: conflated pricing
  (ARCA-4/5/7), portfolio/holdings + risk analytics (ARCA-13/14), ARCA Score + grading alpha
  (ARCA-9/10/11) — each with the concrete outcome for the user, not the mechanism.
- [ ] Draft "What it is not," explicitly excluding real-time data, full catalog coverage, grading
  services, marketplace/trade execution, multi-user BYOK — and stating plainly that current analytics
  run on seeded/synthetic history pending real historical ingestion (ARCA-27).
- [ ] Write the PR description listing every fact the founder would reasonably supply but that isn't
  establishable from either repo (target price tier, named competitors, brand voice/tone) as an open
  question, not a filled-in guess.

## Validation gates
- [ ] happy path: `context/positioning.md` exists and, read top to bottom, answers all five ticket
  bullets (who, what-instead, what-it-is, three things, what-it-is-not) without requiring another doc.
- [ ] edge cases: each of the "three things" names or clearly implies the shipped ticket it traces to
  (ARCA-4/5/7 conflation, ARCA-13/14 portfolio, ARCA-9/10/11 score/grading-alpha), and no claim rests
  on a ticket whose Status is "In progress" or "Planned" (ARCA-24, ARCA-25, ARCA-27, ARCA-39, ARCA-41)
  without being named as a present limit in "What it is not" instead.
- [ ] errors: no sentence in the file contradicts a ticket's actual scope — specifically, no claim of
  real-time pricing, no claim of analytics computed on real historical data, no claim of grading
  cards, and no claim of marketplace/trade execution; a reader cross-checking against
  `arca/docs/tickets/` and `scripts/seed-prices.ts` finds no mismatch.
- [ ] coverage: the PR description enumerates every founder-only fact that could not be sourced from
  `arca/` or `context/` (pricing tier, named competitors, brand voice) so nothing is silently guessed,
  per the ticket's explicit instruction to flag rather than invent.

<!-- foundry-ticket: 9b13f5cf47110920 -->

<!-- foundry-ticket: 9b13f5cf47110920 -->

<!-- foundry-ticket: 9b13f5cf47110920 -->
