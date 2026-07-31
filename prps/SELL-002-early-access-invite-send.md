# PRP — SELL-002-early-access-invite-send

## Intent
The founder gets a reviewable, diffable draft of the early-access invitation email — grounded in
ARCA's positioning, with an unsubscribe path and its compliance facts recorded alongside it — plus a
proposal in the venture's approval record ready for the founder to approve. Nothing is sent.

## Context
- `context/positioning.md` does not exist on `main` or on this branch yet — `SELL-001` drafted it but
  only on branch `foundry/SELL-001-positioning-one-pager` (commit `aac2241`), not merged. That draft
  covers who ARCA is for, what it replaces, the one-sentence pitch ("the Bloomberg Terminal for
  Pokemon cards"), the three things it does, and what it explicitly is not — this is the source to
  cite, not re-invent. Its own review notes flag three founder-only facts it could not establish
  (price/tier, named competitors, brand voice) — the invite must not invent these either.
- `library/` currently holds only its README; `library/campaigns/` does not exist yet — this ticket
  creates it and its first file.
- No waiting-list data, suppression-list mechanism, or sending identity exists anywhere in this repo
  or in the venture knowledge supplied — those facts must come from the founder/venture brain, and if
  they cannot be established the same way `SELL-001` flagged its gaps (named explicitly in the draft,
  not guessed).
- The gate: per root `README.md`, this repo's lane holds no send credentials. "Propose the send" means
  writing a proposal to the venture's approvals record (the `activegraph` gate, enforced outside this
  repo) — there is no in-repo code path that sends mail, and none should be added.
- `scripts/check-tickets.mjs` (run by `.github/workflows/ci.yml`) validates every file in
  `docs/tickets/`: title has an `ID — Title` separator, a `**Status:**` line with a value from a fixed
  enum, and an `## Acceptance criteria` section. The ticket file at
  `docs/tickets/SELL-002-early-access-invite-send.md` already has `**Status:** In progress` (this
  branch's only change so far) and must keep parsing cleanly.
- House pattern from `SELL-001`: cite only what traces to a source; list anything unresolved
  explicitly in the PR/ticket notes rather than inventing a plausible answer.

## Approach
Smallest correct change: one new file for the draft + compliance record, no code, no send.
- Pull `context/positioning.md` from `foundry/SELL-001-positioning-one-pager` (or wait for it to land
  on `main`) so the invite has something real to cite; do not re-derive positioning from the `arca`
  product repo directly — that duplicates `SELL-001`'s job and risks disagreeing with it.
- Create `library/campaigns/early-access-invite.md` containing:
  - The invitation copy: what ARCA is (citing positioning.md's one-sentence framing and the three
    things it does), what early access grants today, a clear next step (link/CTA placeholder), and an
    unsubscribe line written into the copy itself.
  - A compliance section recording: recipient population and consent basis, lawful basis for the
    email, suppression-list check, and sending identity (from/reply-to) — filled in where sourceable,
    explicitly flagged as unresolved (not guessed) where the repo has no answer.
  - A send-proposal section: what is being proposed to whom, referencing the draft and compliance
    facts, marked as pending founder approval via the venture's approvals record — not an in-repo
    "send" of any kind.
- Update `docs/tickets/SELL-002-early-access-invite-send.md` acceptance criteria checkboxes and add a
  "Notes for review" section (mirroring `SELL-001`'s) listing what could not be established.
- Files touched: `library/campaigns/early-access-invite.md` (new), `docs/tickets/SELL-002-early-access-invite-send.md` (already modified for Status; extend with review notes and checked boxes).

## Tasks
- [ ] Confirm `context/positioning.md` content to cite (from the `SELL-001` branch, or `main` if it has landed by implementation time)
- [ ] Create `library/campaigns/` directory and write `early-access-invite.md` with the invitation copy
- [ ] Write the unsubscribe path directly into the copy (not a footer assumption)
- [ ] Record compliance facts (recipients/consent, lawful basis, suppression check, sending identity) in the same file, flagging anything unresolved instead of guessing
- [ ] Write the send-proposal section describing what is being proposed for founder approval
- [ ] Raise the proposal in the venture's approvals record via the studio's `activegraph` mechanism (outside this repo — no send credentials touched, no infra changed)
- [ ] Update the ticket's acceptance-criteria checkboxes and add "Notes for review" listing unresolved facts
- [ ] Run `node scripts/check-tickets.mjs` to confirm the ticket still parses

## Validation gates
- [ ] happy path: `library/campaigns/early-access-invite.md` exists, cites `context/positioning.md`'s wording (not a re-derived description of ARCA), contains an unsubscribe line in the copy, and has a compliance section with recipients/consent, lawful basis, suppression check, and sending identity each addressed
- [ ] edge cases: if `context/positioning.md` is still unmerged at implementation time, the draft cites the `SELL-001` branch content explicitly and the ticket notes record that the merge order matters; any compliance fact with no source in this repo is listed under "Notes for review" rather than filled with a plausible guess
- [ ] errors: no send, list-building, or sending-infrastructure code is added anywhere in the diff; the diff touches only `library/campaigns/early-access-invite.md` and `docs/tickets/SELL-002-early-access-invite-send.md`; `node scripts/check-tickets.mjs` exits 0
- [ ] coverage: each of the four ticket scope bullets (draft, compliance facts, proposal raised, nothing sent) maps to a checked acceptance-criteria box or an explicit "Notes for review" entry explaining why it can't be checked yet

<!-- foundry-ticket: 0b6674ed7fbdb031 -->
