# Students — CLAUSE

**Project:** CLAUSE  
**Category:** LEGAL_TECH  
**Upstream:** see BENCH.json  
**Pinned commit:** `f96b823e4228252b2927cce3effa550c16b558a5`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `db03c0ec8eb1afc85922c34d6e83133ae2a0bb82ab7a998dfd71e0f2aeb3bdd4`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `f96b823e4228252b2927cce3effa550c16b558a5`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `db03c0ec8eb1afc85922c34d6e83133ae2a0bb82ab7a998dfd71e0f2aeb3bdd4`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
