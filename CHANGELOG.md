# Changelog

All notable changes to ZHIXI will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-07-28

### Added

- **Four-stage thinking framework**: 知己 (Self-Knowledge) → 问己 (Self-Questioning) → 明需 (Requirement Clarity) → 洞意 (Insight & Execution)
- **Knowledge Capture system**: Structured knowledge slots and fragments with confidence scoring
- **Agent handoff protocol**: Full context propagation for multi-agent workflows
- **GitHub repo search funnel**: 7-step capability source discovery process
- **Safety rules**: Credential protection and source verification requirements
- **Bilingual support**: Chinese and English trigger words and documentation

### Design Decisions

- Zero external dependencies: runs entirely within host session
- Knowledge fragments default to confidence ≤ 0.6 when unverified
- Original user request always preserved verbatim
- Facts, inferences, and suggestions strictly separated
