# ResolveKit

ResolveKit is a TxLINE-native prediction market and deterministic settlement workbench built for the TxODDS Prediction Markets and Settlement track.

It creates winner markets from TxLINE fixtures, normalizes available 1X2 odds, accepts demo-credit positions, advances markets through `OPEN -> LOCKED -> RESOLVED -> SETTLED`, and emits a reproducible settlement receipt bound to the fixture ID, source timestamp, final score, winner, and rule.

## Product boundaries

- Demo credits only. No wallet, wagering, token transfer, or real assets.
- TxLINE is the primary fixture, odds, and score source.
- Live mode never marks a market settled without a final source observation.
- Replay Lab provides a deterministic five-frame review harness when a live fixture has not finished.
- The receipt is an application-level deterministic checksum, not a claim of cryptographic or on-chain proof.

## Run locally

Set `TXLINE_JWT`, `TXLINE_API_TOKEN`, and optionally `TXLINE_API_ORIGIN`, then serve the static root with the Netlify function runtime. The deployed application maps `/api/markets` to `netlify/functions/markets.js`.

## Settlement rule

The canonical receipt preimage is:

```
fixtureId|sourceTimestamp|participant1Score:participant2Score|winner
```

ResolveKit applies `FULL_TIME_PARTICIPANT_RESULT`: participant 1 wins when score 1 is higher, participant 2 wins when score 2 is higher, and otherwise Draw wins. The same source observation always produces the same receipt hash.

## TxLINE integration

The serverless adapter fetches `/api/fixtures/snapshot`, then concurrently fetches `/api/odds/snapshot/{fixtureId}` and `/api/scores/snapshot/{fixtureId}` for up to 12 fixtures. Secrets remain server-side.

## Review path

1. Open Replay Lab.
2. Select Japan and place a 100 CR demo position.
3. Advance frames from scheduled through live, locked, resolved, and settled.
4. Inspect the payout, source evidence, and deterministic receipt in the audit ledger.

## Responsible AI disclosure

The human participant owns this submission, selected the task, directed the product scope, authorized the account actions, and approved submission through their authenticated Superteam account. Codex was used as an AI development and browser automation tool.
