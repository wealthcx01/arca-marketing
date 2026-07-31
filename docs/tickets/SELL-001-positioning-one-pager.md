# SELL-001 — Write the positioning one-pager

**Status:** In progress · **Owner:** lane · **Gate:** pr

## Why this matters
Everything else in this repo — the landing page, the emails, the way we describe ARCA to a collector
— is downstream of one paragraph nobody has written down yet: who this is for, what it replaces, and
why it is better. Until that exists, every piece of copy re-invents it slightly differently and none
of them agree.

## Scope
- Read what the product actually does from the `arca` repo (`docs/`, `reference/`) and from
  `context/` here. Do not invent capabilities — describe what is built.
- Write `context/positioning.md` covering:
  - **Who it is for** — the specific collector or investor, described so a real person would
    recognise themselves. Not "card enthusiasts".
  - **What they do today instead**, and where that hurts.
  - **What ARCA is**, in one sentence, in their words.
  - **The three things it does** that matter most, each with the concrete outcome for the user.
  - **What it is not** — the boundary that stops the promise inflating.
- Flag, in the PR description, anything you could not establish from the repos rather than filling it
  in with a plausible guess.

## Out of scope
Landing page copy, emails, pricing. Those are separate tickets that will cite this one.

## Acceptance criteria
- [ ] `context/positioning.md` exists and answers all five questions above.
- [ ] Every capability claim traces to something that exists in the `arca` repo.
- [ ] Anything unresolved is listed explicitly rather than guessed.

## Notes for review
Everything in `context/positioning.md` traces to a Shipped ticket in `arca/docs/tickets/` or to a
named current limit (see the file's own "What it is not" section). Three founder-only facts could
not be established from either repo and are flagged here, per this ticket's instruction to flag
rather than guess:
- **Target price/subscription tier** — no pricing ticket or context file exists yet.
- **Named competitors** — nothing in `arca/` or `context/` names who ARCA is positioned against.
- **Brand voice/tone** — no style guide exists; the doc is written plainly, borrowing the "Bloomberg
  Terminal for Pokemon Cards" framing already present in `arca/CLAUDE.md`, but that framing is
  inferred, not a specified voice guide.
