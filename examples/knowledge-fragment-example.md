# Example: Knowledge Fragment Lifecycle

## Overview

This example shows how ZHIXI captures knowledge across a project lifecycle, building a reusable knowledge base over time.

## Scenario

You're evaluating whether to use a specific open-source library for your project.

## Stage 3: Knowledge Slot Created

During 明需 (Requirement Clarity), ZHIXI identifies a knowledge gap:

```json
{
  "id": "slot-eval-pdf-parser",
  "title": "PDF Parser Library Evaluation",
  "question": "Which Python PDF parser best handles Chinese scanned documents?",
  "kind": "verified_finding",
  "targetNodeId": "eval-pdf",
  "requiredEvidence": [
    "Benchmark results on Chinese PDFs",
    "License compatibility check",
    "Community activity metrics"
  ],
  "destinationHint": "tech-evaluation"
}
```

## Stage 4: Knowledge Fragments Generated

After actual evaluation in 洞意 (Insight & Execution), ZHIXI produces fragments:

### Fragment 1: Technical Finding

```markdown
---
type: knowledge-fragment
status: verified
privacy: sanitized
source: "benchmark script ./scripts/benchmark_pdf.py"
confidence: 0.85
tags:
  - tech/pdf-parser
  - evaluation/chinese-ocr
---

# Chinese PDF Parsing: pymupdf4llm vs pdfplumber

## 摘要 (Summary)
For Chinese scanned documents, pymupdf4llm outperforms pdfplumber
in text extraction accuracy (92% vs 78%) on mixed-layout documents.

## 事实陈述 (Facts)
- pymupdf4llm: 92% character accuracy on test corpus (50 pages)
- pdfplumber: 78% character accuracy on same corpus
- Both handle pure-text PDFs equally well (>98%)
- pymupdf4llm is 3x faster on large documents

## 推断 (Inferences)
- The accuracy gap likely comes from better CJK font handling in PyMuPDF
- Performance advantage matters for batch processing, not single-file use

## 建议 (Suggestions)
- Use pymupdf4llm as primary parser
- Keep pdfplumber as fallback for table-heavy documents

## 适用边界 (Applicability Boundaries)
- Tested on: Simplified Chinese, scanned at 300dpi
- Not tested on: Traditional Chinese, low-resolution scans, handwritten text
- Library versions: pymupdf4llm 0.15.0, pdfplumber 0.11.4

## 来源 (Sources)
- Benchmark script: ./scripts/benchmark_pdf.py
- Test corpus: internal documents (50 pages, mixed layouts)
```

### Fragment 2: Decision Rule

```markdown
---
type: knowledge-fragment
status: verified
privacy: sanitized
source: "derived from Fragment 1 benchmark results"
confidence: 0.9
tags:
  - decision/pdf-library
---

# PDF Library Selection Decision Rule

## 摘要 (Summary)
Choose the PDF parsing library based on document type and volume.

## Decision Rule
| Document Type | Volume | Recommended Library |
|---|---|---|
| Pure text PDF | Any | pdfplumber (simpler API) |
| Scanned Chinese | >10 pages/day | pymupdf4llm (faster + more accurate) |
| Table-heavy | Any | pdfplumber (better table extraction) |
| Mixed layout | Any | pymupdf4llm (better layout awareness) |

## 适用边界 (Applicability Boundaries)
- Based on 2026 library versions
- May change as libraries update

## 来源 (Sources)
- Derived from Fragment 1 benchmark results
```

## The Knowledge Accumulates

After several projects, your knowledge base grows:

```
knowledge/
├── tech-evaluation/
│   ├── pdf-parser-chinese.md        (confidence: 0.85)
│   ├── pdf-library-decision-rule.md (confidence: 0.90)
│   ├── ocr-engine-comparison.md     (confidence: 0.75)
│   └── ...
├── architecture/
│   ├── async-vs-sync-for-io.md
│   └── ...
└── process/
    ├── code-review-checklist.md
    └── ...
```

Each fragment is:
- **Self-contained** — understandable without reading others
- **Traceable** — every claim linked to evidence
- **Calibrated** — confidence scores reflect verification status
- **Bounded** — applicability limits are explicit

> **Note:** ZHIXI defines the fragment format and methodology. The directory structure, storage system, and search capabilities shown above are an example of what you *could* build — ZHIXI itself does not manage storage.
