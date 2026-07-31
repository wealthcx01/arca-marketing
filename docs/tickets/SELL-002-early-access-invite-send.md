# SELL-002 — Send the early-access invitation to the waiting list

**Status:** Todo · **Owner:** lane · **Gate:** activegraph

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
- [ ] The draft exists in `library/campaigns/`, and cites the positioning rather than re-inventing it.
- [ ] An unsubscribe path is in the copy, not assumed.
- [ ] The compliance facts are recorded with the draft, not left implicit.
- [ ] A proposal is raised for the founder's approval, and **nothing is sent** by the lane.
