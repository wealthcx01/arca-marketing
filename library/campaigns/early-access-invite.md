# Early-access invitation — waiting list

**Status:** Drafted, pending founder approval to send · **Ticket:** SELL-002

## Source

Positioning is cited from `context/positioning.md` as authored on branch
`foundry/SELL-001-positioning-one-pager` (commit `aac2241`) — that file is not yet merged to `main`,
so this draft quotes it directly rather than assuming it will land unchanged. See "Notes for review"
in `docs/tickets/SELL-002-early-access-invite-send.md` for why.

## Email copy

**Subject:** You're in — early access to ARCA is open

---

Hi {{first_name}},

You asked to hear when ARCA opened. It's open — and you're one of the first people we're telling.

ARCA is the Bloomberg Terminal for Pokemon cards — the terminal where a card collector checks price,
tracks their holdings, and decides what to buy, sell, or grade next, the same way a trader opens a
terminal for a stock position instead of piecing it together from five browser tabs.

With early access today, you get:

- **One resolved price instead of five browser tabs.** ARCA pulls pricing from six sources and
  conflates them into a single best price per card, with the source attributed per field.
- **A portfolio that knows its own P&L.** Log your buys and sells; ARCA derives your holdings,
  weighted-average cost basis, and P&L from the ledger, plus portfolio-level risk — volatility,
  Sharpe, concentration, currency exposure.
- **A real answer on whether to grade.** The ARCA Score and grading-alpha run off the same computed
  analytics, netting the graded-vs-raw price gap against real PSA, CGC, and BGS fees — so "is it
  worth grading this one" has a computed answer, not a guess.

Worth knowing up front: pricing refreshes daily, not tick-by-tick; coverage today is focused on
roughly 1,250 of the ~19,000 cataloged cards; and the trend/volatility numbers currently run on
simulated history seeded from each card's real current price, not yet on observed historical prices.
Real historical ingestion is planned but not shipped.

**[Get early access → {{EARLY_ACCESS_LINK}}]**

— The ARCA team

---

Don't want these emails? [Unsubscribe]({{UNSUBSCRIBE_LINK}}) — one click, no login required, and
we'll stop writing to you.

## Compliance

- **Recipients — who they are and how they came to be on this list:** Not established in this repo.
  No waiting-list dataset, signup form, or consent record exists in `arca-marketing` or in the venture
  context supplied to this lane. This is a gap the founder needs to close before any send — flagged
  here rather than assumed (e.g. "double opt-in signup form").
- **Lawful basis for writing to them:** Not established. The lawful basis depends on how consent was
  captured at signup (e.g. explicit opt-in vs. soft opt-in), which this repo has no record of. Flagged
  rather than guessed.
- **Suppression-list check:** Not performed, and no suppression-list mechanism exists anywhere in this
  repo or in the sending infrastructure this lane can see. Building or checking one is explicitly out
  of scope for SELL-002 ("Out of scope: ... Building the list. Any change to the sending
  infrastructure.").
- **Sending identity (from/reply-to):** Not established. No sending domain or mailbox is recorded in
  this repo.

## Send proposal

**Proposed action:** Send the email copy above to ARCA's early-access waiting list.

**Status:** Not sent. This lane holds no send credentials (see root `README.md`, "The gate"). This
section is the proposal raised to the venture's approvals record under the `activegraph` gate, for
the founder to review and approve or reject. A structured copy of this proposal is written to the
run's `proposal.json` per the studio's process; approval and sending both happen outside this repo.

**Before this can be approved and sent, the founder needs to supply or confirm:** the recipient list
and its consent basis, the lawful basis for sending, a suppression-list check against it, and the
sending identity. All four are listed as unresolved above, not guessed.
