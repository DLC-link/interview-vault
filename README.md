# BitSafe — AI-Assisted Engineering Task: Collateral Vault

A small, staged live build. **AI tools are allowed and expected.** Think out loud, commit as you go.

| | |
|---|---|
| **Format** | One live session, staged. Stage 1 first; we extend it once it runs. |
| **Stack** | Use whatever language and tooling you're most productive in. |
| **Core signal** | Judgment, correctness, and how you use AI — not finishing speed. |
| **Tools** | Your editor, terminal, git, AI assistants, the web. All fair game. |

> **Read this first**
>
> We care less about whether you finish and more about how you scope the problem, reason about correctness, verify what AI gives you, and adapt when we change the requirements. Please think out loud as you go.

## Stage 1 — Collateral Vault

Build a small backend service for a minimal **collateral vault** — a stripped-down version of a wrapped-asset system. A user locks a collateral asset into the vault and receives *receipt tokens* in return, one-for-one. They can later redeem receipts to get their collateral back. Single user, single collateral type; keeping state in memory is fine for this stage.

Expose a small HTTP API with roughly these operations:

- `POST /lock` — lock an amount of collateral; mint the same amount of receipts. Returns the updated balances.
- `POST /redeem` — burn an amount of receipts; release the same amount of collateral. Returns the updated balances.
- `GET /balance` — return collateral currently locked and receipts currently outstanding.

> **The one rule that must always hold**
>
> Receipts outstanding must always equal collateral locked — the vault is fully backed, 1:1, at all times. A user can never redeem more than they hold, and balances can never go negative. How you represent and update balances is up to you; correctness here matters more than anything else.

### What "done" looks like for Stage 1

- The service runs and the three operations work end-to-end.
- Invalid requests are rejected with sensible HTTP status codes (bad input vs. a disallowed operation are not the same thing).
- At least one test covering the highest-risk path — pick the one that matters most.
- Commits at sensible points. Say out loud what you're deferring and why.

## Stage 2

Once Stage 1 runs, we'll extend it together — be ready to adapt. We're interested in how you handle a shift in requirements, not in you guessing what's coming.

## Permissions & notes

- AI assistants are allowed and expected. Use them the way you normally would — we'll ask you about the code afterward.
- No authentication, no database, and no persistence are required for Stage 1.
- No real blockchain or external services are involved — this is a self-contained service.

---

*We are not measuring whether you finish the vault. We're measuring whether you can turn a small, slightly ambiguous brief into a correct, production-shaped service, use AI without losing ownership of the result, and adapt when the requirements move.*
