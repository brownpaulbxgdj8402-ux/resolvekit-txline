# ResolveKit - Deterministic TxLINE market settlement

## Description

ResolveKit is a functional demo-credit prediction market and settlement workbench powered by TxLINE. It automatically creates winner markets from fixtures, normalizes 1X2 odds, accepts simulated positions, and advances every market through an explicit OPEN, LOCKED, RESOLVED, and SETTLED state machine.

Settlement is deterministic: a final TxLINE observation is reduced to fixture ID, source timestamp, full-time score, winner, and result rule. ResolveKit then emits a reproducible receipt and records it with every settled position in the audit ledger. Live mode never settles without a final source observation; Replay Lab provides a five-frame deterministic review flow so judges can inspect the complete lifecycle immediately.

No wallet, wagering, token transfer, or real assets are used.

## Links

- Live app: pending deployment
- Demo video: pending deployment
- Public repository: pending publication
- Documentation: pending publication

## Feedback

TxLINE's fixture IDs and separate odds/score snapshots make source-bound market generation straightforward. The largest integration friction was the sparse and variable score payload across scheduled fixtures, plus limited availability of canonical 1X2 markets in a small live window. Published TypeScript response types, explicit final-state enums, and a canonical signed settlement payload would reduce defensive parsing and help teams move from application receipts to verifiable on-chain settlement.

## Additional disclosure

The human participant owns this submission, selected the task, directed the product scope, authorized the account actions, and approved submission through their authenticated Superteam account. Codex was used as an AI development and browser automation tool. ResolveKit is a simulation and moves no real assets.
