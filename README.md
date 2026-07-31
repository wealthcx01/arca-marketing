# arca-marketing — ARCA's **Sell** surface

This is where ARCA's go-to-market work lives: positioning, site and content, campaigns, and the
sequences that go out to real people. It is a normal git repo worked by the Foundry lane on ARCA's
venture box, under the same discipline as the product repo — **one ticket = one branch = one PR**.

It is the *Sell* department declared in `ventures/arca.yaml` in the Foundry Studio. The studio renders
this queue on ARCA's board.

## How work gets done here

1. **A ticket lands in `docs/tickets/`** — filed by the founder through the studio composer, or by
   hand. `**Status:** Todo` is the signal that the lane may pick it up.
2. **The lane works it** — research (from `context/` and the venture brain) → plan → implement →
   review and test its own work → open a PR. A human merges.
3. **Nothing goes out to a real person without a recorded approval.** That is the difference between
   this repo and the product repo, and it is not a convention — it is enforced elsewhere:

## The gate (why a lane can draft a campaign but never send it)

The Sell department's gate is `activegraph`. Drafting, editing and reviewing content is ordinary
work: it happens in a PR. **Sending** is not. When a ticket asks for an external action — an email
sequence, an outreach send, anything that reaches a person outside the company — the lane does not
perform it. It writes a **proposal** to the venture's approvals record, and the studio shows it to the
founder as something to approve. Only a human approval, signed by the studio, lets the separate
gated executor act.

The lane box holds no send credentials at all, so this is structural rather than a promise.

## Layout

| Path | What lives there |
| --- | --- |
| `docs/tickets/` | The work queue. One markdown file per ticket, in the house format. |
| `context/` | Durable background the lane should know: positioning, ICP, voice, competitors. |
| `library/` | Outputs and artefacts — drafts, campaign copy, briefs, published assets. |

Heavy binaries (video, large images) belong in object storage with a pointer here, not committed.

## Ticket format

```markdown
# SELL-001 — A short, plain title

**Status:** Todo · **Owner:** lane

## Why this matters
One paragraph a non-technical founder would recognise as their own problem.

## Scope
- What to do, concretely.

## Acceptance criteria
- [ ] How we will know it is done.
```

`Status` is one of `Todo`, `Ready`, `In progress`, `Blocked`, `Shipped`, `Planned`. The lane only ever
picks up `Todo` and `Ready` — a `Planned` backlog is safe from it.
