# TxLINE Integration Evidence

- Devnet wallet: `ALMpoj9rW5Tsfv61rQMmTr1PLVraaNgdgbsRn9b7LiU5`
- Subscription transaction: `31reS5HQNCMPvC3npDATxHoZkx84FGfVzcLNhhmJ5QTCpdj1nqqpGoKuEKVTBncajtKigLNnQCVPU5baofZusvES`
- TxLINE program: `6pW64gN1s2uqjHkn1unFeEjAwJkPGHoppGvS715wyP2J`

The deployed serverless adapter uses TxLINE Devnet credentials stored only in the hosting environment. It reads fixtures, odds, and scores through the official snapshot endpoints. During development, the feed returned seven live fixtures; score observations were available for fixtures including `18257739` and `18257865`.

ResolveKit deliberately distinguishes source evidence from proof. Its settlement receipt is deterministic and source-bound, but it does not claim Merkle or on-chain verification that the current build does not execute.
