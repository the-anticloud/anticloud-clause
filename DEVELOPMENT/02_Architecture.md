# Technical Architecture — CLAUSE

**Upstream:** [https://github.com/nicedoc/clause](https://github.com/nicedoc/clause)
**License:** Apache 2.0
**Category:** LEGAL_TECH
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

Smart contract authoring and execution

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local contract analysis and clause extraction — air-gapped
2. AIOSS tamper-evident document version chain (eDiscovery-ready)
3. AES-256 encryption for all client documents and privileged communications
4. Single-binary legal tool for secure client networks
5. Zero-cloud: all NLP analysis and search run locally
6. GPU/CPU equalizer: large document analysis on GPU or CPU
7. Zero-telemetry: removes all usage reporting
8. Open format: exports to LEDES billing and EDGAR submission formats

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_clause.spec` or `go build -o clause`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |