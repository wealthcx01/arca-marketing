# Positioning

## Who it is for

A collector who holds a real, multi-card position in Pokemon cards — raw and PSA/CGC/BGS-graded,
bought across eBay, TCGplayer, local shops, and shows over months or years — and who thinks about
that position the way an investor thinks about a portfolio: what did I pay, what's it worth now,
what's my P&L, is it worth paying to grade this raw card. Not a kid with a binder, and not someone
buying one card to flip next week — someone with enough of a position that "what is this actually
worth, all together" is a real question they currently can't answer without doing the math by hand.

## What they do today instead

- **Price-checking**: tabbing between eBay sold listings, TCGplayer, and marketplace apps for every
  card, by hand, because no source is authoritative on its own — and the number changes by the time
  they act on it.
- **Cost basis and P&L**: a spreadsheet they built and maintain themselves, updated manually, that
  drifts out of date the moment they stop keeping up with it.
- **Grade-or-don't**: a gut call on whether a raw card is worth sending to PSA/CGC/BGS, because
  running the real math — grading fee against the actual graded-vs-raw price gap — is tedious enough
  that most people don't do it consistently.

Each of these is a place where the collector is doing, by hand, something that has a real answer if
someone bothered to compute it from the actual market data.

## What ARCA is

ARCA is the Bloomberg Terminal for Pokemon cards — the terminal where a card collector checks price,
tracks their holdings, and decides what to buy, sell, or grade next, the same way a trader opens a
terminal for a stock position instead of piecing it together from five browser tabs.

## The three things it does

1. **One resolved price instead of five browser tabs.** ARCA pulls pricing from six sources (three
   free, three bring-your-own-key) and conflates them into a single best price per card, with the
   source attributed per field — so the collector gets one number they can act on instead of
   reconciling listings themselves.
2. **A portfolio that knows its own P&L.** Log buys and sells as transactions; ARCA derives holdings,
   weighted-average cost basis, and P&L from the ledger, plus portfolio-level risk — volatility,
   Sharpe, concentration (HHI), currency exposure — so the collector sees where the risk actually sits
   instead of eyeballing it.
3. **A real answer on whether to grade.** The ARCA Score (a 0–100 composite of momentum, value,
   liquidity, risk-adjusted return, and scarcity) and grading-alpha both run off the same computed
   analytics — grading-alpha nets the graded-vs-raw price gap against real PSA ($75), CGC ($50), and
   BGS ($100) fees, so "is it worth grading this one" has a computed answer, not a guess.

## What it is not

- **Not real-time.** Pricing refreshes daily by design, not tick-by-tick — this is a terminal for
  decisions, not a live order book.
- **Not built on observed price history yet.** The ARCA Score, volatility, Sharpe, and trend
  calculations are real formulas, but today they run on synthetic history — 30 days of simulated
  price movement seeded from each card's real current price, not on real historical prices. Genuine
  historical ingestion is planned but not shipped; until it lands, treat these as correct math on a
  placeholder series, not a track record.
- **Not full-catalog yet.** Pricing coverage is capped at roughly 1,250 of the ~19,000 cataloged
  cards, focused on held cards; broader coverage is in progress, not live.
- **Not multi-user on BYOK yet.** Bring-your-own-key pricing currently runs on one shared key, not a
  key per user; that's in progress.
- **Not a grading service.** ARCA tells you whether grading is worth it — it does not grade cards.
- **Not a marketplace.** ARCA verifies, prices, and tracks a collection — it does not list, buy, sell,
  or execute trades on the collector's behalf.
