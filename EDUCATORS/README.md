# Educators — CLAUSE

**Project:** CLAUSE  
**Category:** LEGAL_TECH  
**Upstream:** see BENCH.json  
**Pinned commit:** `f96b823e4228252b2927cce3effa550c16b558a5`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `db03c0ec8eb1afc85922c34d6e83133ae2a0bb82ab7a998dfd71e0f2aeb3bdd4`  
**Date:** October 2026

## Teaching with CLAUSE

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `db03c0ec8eb1afc85922c34d6e83133ae2a0bb82ab7a998dfd71e0f2aeb3bdd4` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
