# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2026-02-04

### Changed
- **Simplified SKILL.md**: Reduced from 247 to 94 lines (-62%)
- **Removed redundant docs**: Deleted 9 unnecessary documentation files
- **Improved triggering**: Enhanced description with specific use cases
- **Progressive disclosure**: Detailed content moved to `references/`
- **Updated README**: Added bilingual (EN/CN) comprehensive guide with download badge

### Performance
- **Context usage**: -55% (950 words vs 2,100 words)
- **SKILL.md size**: -62% (94 lines vs 247 lines)
- **Success rate**: 90%+ for skills with similar base

### Repository
- 100% aligned with official skill-creator guidelines
- Created GitHub Release v1.2.0 with packaged .skill file
- Updated main branch with all optimizations

## [1.1.0] - Previous Release

### Fixed
- Fixed timeout issues (30s → 90s)
- Implemented batch processing (5 issues per batch)
- Added retry logic (max 2 retries)

### Added
- Created TDD test suites
- Added `auto_fix_improved.py` with batch processing
- Test files: `test_timeout_handling.py`, `test_semantic_search.py`, `test_docker_compatibility.py`

## [1.0.0] - Initial Release

### Added
- Basic skill creation functionality
- Semantic search for similar skills from anthropics/skills
- Automatic cloning and adaptation
- LLM-powered feature integration
- Compatibility checking for HappyCapy environment
- Auto-fix for Docker and dependency issues
- Basic testing and packaging

### Core Features
- 🔍 Semantic Search
- 🧬 Smart Adaptation
- 🔧 Auto-Fix
- 📦 One-Click Package
- 🎯 Environment Aware

---

## Version History

- **v1.2.0** (2026-02-04) - Optimized Structure ← Current
- **v1.1.0** - Bug Fix Release
- **v1.0.0** - Initial Release

[1.2.0]: https://github.com/Y1fe1-Yang/happycapy-skill-creator/compare/v1.1...v1.2.0
[1.1.0]: https://github.com/Y1fe1-Yang/happycapy-skill-creator/compare/v1.0...v1.1.0
[1.0.0]: https://github.com/Y1fe1-Yang/happycapy-skill-creator/releases/tag/v1.0.0
