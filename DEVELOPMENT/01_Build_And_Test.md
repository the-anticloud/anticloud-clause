# Build and Test

**Project:** `CLAUSE`
**Upstream:** https://github.com/nicedoc/clause
**License:** Apache 2.0

## Quick Start

```bash
git clone https://github.com/nicedoc/clause
cd clause
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local contract analysis and clause extraction — air-gapped
2. AIOSS tamper-evident document version chain (eDiscovery-ready)
3. AES-256 encryption for all client documents and privileged communications
4. Single-binary legal tool for secure client networks
5. Zero-cloud: all NLP analysis and search run locally
6. GPU/CPU equalizer: large document analysis on GPU or CPU
7. Zero-telemetry: removes all usage reporting
8. Open format: exports to LEDES billing and EDGAR submission formats

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
