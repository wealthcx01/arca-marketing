# SELL-002 — Send the early-access invitation to the waiting list

**Status:** In progress · **Owner:** lane · **Gate:** activegraph

## Why this matters
People asked to hear when ARCA opened. Nobody has written to them. This is the first message that
goes to real people from a real address, so it is also the first true test of the rule the whole
studio is built on: an agent may prepare it, and only a human may send it.

## Scope
- Draft the invitation: what ARCA is (cite `context/positioning.md`), what they get access to today,
  what to do next, and how to stop hearing from us.
- Draft it into `library/campaigns/early-access-invite.md` so it is reviewable as a diff before it is
  reviewable as an inbox.
- Record the compliance facts alongside the draft: who the recipients are and how they came to be on
  the list, the lawful basis for writing to them, the suppression check, and the sending identity.
- **Propose the send. Do not send it.** The proposal goes to the venture's approval record and
  surfaces in the studio as something for the founder to approve.

## Out of scope
Sending. Building the list. Any change to the sending infrastructure.

## Acceptance criteria
- [x] The draft exists in `library/campaigns/`, and cites the positioning rather than re-inventing it.
- [x] An unsubscribe path is in the copy, not assumed.
- [x] The compliance facts are recorded with the draft, not left implicit.
- [x] A proposal is raised for the founder's approval, and **nothing is sent** by the lane.

## Notes for review
`library/campaigns/early-access-invite.md` holds the draft, the compliance record, and the send
proposal. A few things could not be established from this repo and are flagged there rather than
guessed, per house pattern from `SELL-001`:

- **`context/positioning.md` is not yet merged to `main`** — it exists only on branch
  `foundry/SELL-001-positioning-one-pager` (commit `aac2241`). The invite copy quotes that content
  directly and names the branch/commit as its source. Merge order matters: if `SELL-001`'s wording
  changes before it lands, this draft's citation should be re-checked against the merged version.
- **Recipients and how they came to be on the list** — no waiting-list dataset or signup/consent
  record exists in this repo or the venture context supplied. Flagged, not guessed.
- **Lawful basis for writing to them** — depends on how consent was captured at signup, which this
  repo has no record of. Flagged, not guessed.
- **Suppression-list check** — not performed; no suppression-list mechanism exists in this repo, and
  building one is explicitly out of scope for this ticket.
- **Sending identity (from/reply-to)** — no sending domain or mailbox is recorded in this repo.
- Carried over from `SELL-001`'s own gaps, which this draft also does not invent: target
  price/subscription tier, named competitors, and brand voice/tone. None of these appear in the copy.
