# Changelog

All notable changes to ZHIXI will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.0] - 2026-07-28

### Added

- **Fallback Behavior** section in SKILL.md: guidance for when users skip stages, refuse to answer, or need quick answers
- **Templates** directory: knowledge-fragment, knowledge-slot, and full session templates for quick start
- **Two complex examples**: team process improvement under conflicting constraints, advanced knowledge fragments with multiple `kind` types
- **Expanded English section**: full English documentation covering features, workflow, quick start, FAQ
- **Idealized knowledge base vision** section in README with explicit "not yet implemented" disclaimer
- **LICENSE** file: Apache License 2.0 full text

### Changed

- SKILL.md version bumped to 1.1.0
- Knowledge base section now clearly distinguishes format specification (implemented) from tooling (aspirational)

## [1.0.1] - 2026-07-28

### Changed

- Added `status` and `confidence` field documentation to knowledge fragment specification
- Clarified confidence threshold rules: verified claims (0.7–1.0) vs. unverified (≤ 0.6)

## [1.0.0] - 2026-07-28

### Added

- **Four-stage thinking framework**: 知己 (Self-Knowledge) → 问己 (Self-Questioning) → 明需 (Requirement Clarity) → 洞意 (Insight & Execution)
- **Knowledge Capture format**: Structured knowledge slots and fragments with confidence scoring
- **Agent handoff guidelines**: Context propagation checklist for multi-agent workflows
- **GitHub repo search funnel**: 7-step capability source discovery process
- **Safety rules**: Credential protection and source verification requirements
- **Bilingual support**: Chinese and English trigger words and documentation

[Unreleased]: https://github.com/tensely0228/ZHIXI/compare/v1.1.0...HEAD
[1.1.0]: https://github.com/tensely0228/ZHIXI/compare/v1.0.1...v1.1.0
[1.0.1]: https://github.com/tensely0228/ZHIXI/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/tensely0228/ZHIXI/releases/tag/v1.0.0
