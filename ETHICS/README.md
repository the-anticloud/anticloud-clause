# Ethics — CLAUSE

**Project:** CLAUSE  
**Category:** LEGAL_TECH  
**Upstream:** see BENCH.json  
**Pinned commit:** `f96b823e4228252b2927cce3effa550c16b558a5`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `db03c0ec8eb1afc85922c34d6e83133ae2a0bb82ab7a998dfd71e0f2aeb3bdd4`  
**Date:** October 2026

## Position

CLAUSE is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
