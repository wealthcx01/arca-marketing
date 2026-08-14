# Positioning

## Who it is for
A collector or small-scale investor who holds a real, multi-card portfolio of graded and raw Pokemon
cards spread across more than one source — some bought on marketplaces, some pulled and graded
themselves, some inherited from an earlier collecting phase. They already think about this the way
an investor thinks about a portfolio: they know roughly what they paid for each card, they want to
know what it's worth now, and they're the type to ask "is this card up or down, and by how much"
rather than just "is this card cool." They're comfortable deciding whether to submit a raw card for
grading, but they currently do that math in their head or not at all.

## What they do today instead
They check prices by opening several marketplace tabs and eyeballing recent sold listings, because no
single source is authoritative and listings disagree. They track what they paid and what they own in
a personal spreadsheet, updating cost basis and P&L by hand whenever they buy or sell — and the
spreadsheet drifts out of date because updating it is tedious. When they're deciding whether a raw
card is worth submitting for grading, they guess at the graded price and skip the actual grading-fee
math, so the decision is a gut call, not a number. There's no single place that shows the whole
portfolio's risk — how concentrated it is, how volatile, how exposed to one set or one card — so that
question just doesn't get asked.

## What ARCA is
ARCA is a market-data terminal for your Pokemon card portfolio — the tool that turns scattered listing
prices and a spreadsheet of purchases into one place that tells you what you hold, what it's worth,
and whether it's working.

## The three things it does
1. **One resolved price instead of five disagreeing ones.** ARCA pulls prices from six sources (three
   free, three bring-your-own-key) and conflates them into a single best price per card, with the
   source attributed per field, so the user stops manually comparing listings across tabs to decide
   what a card is actually worth right now.
2. **A portfolio that knows its own numbers.** Every buy and sell is logged to a transaction ledger,
   and ARCA derives holdings, weighted-average cost basis, and P&L from it automatically — plus
   portfolio-level risk (weighted volatility, Sharpe ratio, concentration via HHI, currency exposure)
   — so the user gets the answer their spreadsheet was always trying to produce, without maintaining
   the spreadsheet.
3. **A number for "should I grade this."** ARCA Score gives every card a 0–100 composite read
   (momentum, value, liquidity, risk-adjusted return, scarcity), and grading-alpha compares graded vs.
   raw ROI net of real PSA/CGC/BGS grading fees, so the grading decision is a comparison of two
   numbers instead of a hunch.

## What it is not
- **Not real-time.** Prices refresh daily by design; ARCA is not a tick-by-tick trading feed.
- **Not built on observed price history yet.** ARCA Score, volatility, Sharpe, and trend are real
  formulas, but today they run on a synthetic 30-day history seeded as a random walk from the current
  real price, not on real historical prices. Real historical ingestion is planned but not shipped, so
  claims about "seeing the real risk profile" would overstate what's true right now.
- **Not full-catalog.** Pricing coverage is capped at a subset of the catalog and only refreshes cards
  the user actually holds; broader coverage is in progress, not shipped.
- **Not multi-user for bring-your-own-key sources.** BYOK pricing currently runs on one shared key,
  not a key per user.
- **Not a grading service.** ARCA tells you the economics of grading a card; it does not grade cards.
- **Not a marketplace.** ARCA verifies, prices, and tracks cards; it does not execute trades or list
  cards for sale.

## Open questions for the founder
Not established from `arca/` or `context/` — flagged rather than guessed:
- Target pricing tier / whether ARCA is free, subscription, or usage-based.
- Named competitors to position against.
- Brand voice and tone for external copy (this doc describes capabilities plainly; it does not set a
  house voice).
