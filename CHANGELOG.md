# Changelog

All notable changes to **grokrec** will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [CIAO](https://github.com/cloudgen/ciao) principles.

## [2.7.0] - 2026-04-14 (CIAO Edition)

### Major Improvements
- **Accurate Tagged Commit Resolution**: Added `get_tagged_commit()` with multi-layered fallback (local git → GitHub API → `git ls-remote`). Raw GitHub URLs now correctly point to the exact tagged commit instead of HEAD. This fixes the long-standing mismatch when HEAD is ahead of the latest tag.
- **Single Source of Truth for Prompts**: `maybe_install()` now fully uses `prompt_yes_no()`. All interactive yes/no prompts are now consistently routed through the designated single source of truth.
- **Robust Version Comparison**: Added `version_gt()` — a pure POSIX semantic version comparator — and integrated it into `version_check()` and `self_update()`. This eliminates incorrect downgrade attempts when the local development version is newer than the published version (e.g. 2.7.0 trying to downgrade to 2.6.0).

### Changed
- Renamed `cmd_start()` → `start_grokrec()` for better clarity.
- Improved interactive file selection flow and remaining files tracking.
- Enhanced defensive comments across multiple functions with clearer warnings about past AI failure modes.
- Better shell detection in `show_about_grokrec()`.
- Updated help text and diagnostics output.

### Technical / Defensive Hardening
- More consistent use of safe variable defaults (`: "${VAR:=default}"`).
- Strengthened anti-subshell patterns in `write_prompt_to_file()`.
- Improved JSON output handling and escaping.
- Better root vs non-root path handling and messaging.
- **Version handling now uses battle-field-tested pure POSIX logic** (`version_gt()`) instead of relying on `sort -V`, improving portability in minimal environments (Alpine, ash, busybox, etc.).

### Bug Fixes
- Fixed critical downgrade bug in `self_update()` where a newer local version would incorrectly attempt to update to an older remote version.
- Fixed non-interactive / JSON mode behavior in several edge cases.
- Corrected prompt generation to always use tagged commit for source URLs.

### Philosophy
- Continued commitment to CIAO principles (Caution, Intentionality, Anti-fragility, Over-engineering).
- The script remains intentionally verbose and heavily guarded against future AI "cleanups" and simplification attempts.
- Strengthened version awareness as a core part of the self-update safety net.

---

## [2.6.0] - 2026-04

### Added
- Significantly improved `cmd_help() --> show_help_grokrec()` and `cmd_about() --> show_about_grokrec()` functions for much better usability (modeled after `pomo`)
- Detailed diagnostic output in `about` (storage directory, clearer installation status, next-step commands)
- Stronger defensive comment blocks across multiple functions to better protect against AI simplification tendencies
- Explicit warnings about root vs non-root, interactive vs non-interactive modes, `--quiet` respect, and battle-field tested logic (especially `perform_self_install`, `is_installed`, `get_installed_version`, `version_check`, `self_update`, `self_uninstall`, `resolve_storage`)

### Changed
- Bumped version to 2.6.0
- Updated README.md with corrected installation URLs (`grokrec` instead of `gorkrec`), improved structure, and link to new CHANGELOG
- Made help and about outputs clearer and more consistent with other CIAO projects

### Fixed (Defensively)
- Reinforced protection against common AI failure modes: ignoring `--quiet`, oversimplifying installation logic, removing self-uninstall, underestimating version checking, and breaking root/non-root isolation

### Philosophy
- Strengthened CIAO guards to reduce the chance of future AI assistants introducing fragile changes

---

## [2.5.0] - 2026-04

### Added
- Initial battle-field tested installation routines with proper root/non-root handling
- Multi-user safe storage (`resolve_storage`)
- Tagged commit resolution (`get_tagged_commit`)
- JSON output support
- Self-update and self-uninstall

**Initial public release.**

---

*Made with strict CIAO principles: Caution, Intentionality, Anti-fragility, Over-engineering.*

