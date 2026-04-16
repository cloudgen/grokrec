# Changelog

All notable changes to **grokrec** will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [CIAO](https://github.com/cloudgen/ciao) principles (Caution, Intentionality, Anti-fragility, Over-engineering).

## [Unreleased]

### Added
- Stronger defensive documentation in `main_grokrec()` explaining safe variable defaults and the exact required execution order (safe defaults → auto-install block → argument parsing → command dispatch).

### Changed
- Improved interactive mode handling reminders in `maybe_install()` (explicit TTY check before any user prompt).

---

## [2.7.2] - 2026-04-16

### Added
- **Defensive hardening of `main_grokrec()`**: Added comprehensive comments explaining the need for safe variable defaults (`: "${VAR:=default}"`) and the **exact non-negotiable execution sequence** to prevent "Illegal number" errors and broken one-liner (`curl | sh`) behavior.
- Updated `maybe_install()` comment block with clear reminder about **interactive TTY checking** (`[ -t 0 ] && [ -t 1 ]`) before calling `prompt_yes_no()`.

### Changed
- Bumped version to 2.7.2
- Further strengthened anti-AI-simplification warnings across installation and main entry point functions.
- Minor cleanup in argument parsing (`--force` now consistently sets `FORCE_REINSTALL`).

### Technical / Defensive Hardening
- Emphasized early safe variable defaults to avoid undefined variable issues in minimal POSIX shells (`dash`, `ash`, etc.).
- Made execution order explicit in comments to protect against future refactoring that could break `curl | sh` installation.

### Philosophy
- Continued reinforcement of CIAO principles with louder, more explicit guards against common AI assistant failure modes (moving blocks, removing defaults, weakening interactive checks, etc.).

---

## [2.7.0] - 2026-04-14 (CIAO Edition)

### Major Improvements
- **Accurate Tagged Commit Resolution**: Added `get_tagged_commit()` with multi-layered fallback (local git → GitHub API → `git ls-remote`). Raw GitHub URLs now correctly point to the exact tagged commit instead of HEAD. This fixes the long-standing mismatch when HEAD is ahead of the latest tag.
- **Single Source of Truth for Prompts**: `maybe_install()` now fully uses `prompt_yes_no()`. All interactive yes/no prompts are now consistently routed through the designated single source of truth.
- **Robust Version Comparison**: Added `version_gt()` — a pure POSIX semantic version comparator — and integrated it into `version_check()` and `self_update()`. This eliminates incorrect downgrade attempts when the local development version is newer than the published version.

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
- **Version handling now uses battle-field-tested pure POSIX logic** (`version_gt()`) instead of relying on `sort -V`.

### Bug Fixes
- Fixed critical downgrade bug in `self_update()`.
- Fixed non-interactive / JSON mode behavior in several edge cases.
- Corrected prompt generation to always use tagged commit for source URLs.

### Philosophy
- Continued commitment to CIAO principles. The script remains intentionally verbose and heavily guarded against future AI "cleanups" and simplification attempts.

---

## [2.6.0] - 2026-04

### Added
- Significantly improved `show_help_grokrec()` and `show_about_grokrec()` functions (modeled after `pomo`).
- Detailed diagnostic output in `about` command.
- Stronger defensive comment blocks across multiple functions.
- Explicit warnings about root vs non-root, interactive vs non-interactive modes, `--quiet` respect, etc.

### Changed
- Bumped version to 2.6.0
- Updated README.md with corrected installation URLs and improved structure.

### Fixed (Defensively)
- Reinforced protection against common AI failure modes (ignoring `--quiet`, oversimplifying installation logic, removing self-uninstall, etc.).

### Philosophy
- Strengthened CIAO guards to reduce the chance of future AI assistants introducing fragile changes.

---

## [2.5.0] - 2026-04

### Added
- Initial battle-field tested installation routines with proper root/non-root handling.
- Multi-user safe storage (`resolve_storage`).
- Tagged commit resolution.
- JSON output support.
- Self-update and self-uninstall.

**Initial public release.**

---

*Made with strict CIAO principles: Caution, Intentionality, Anti-fragility, Over-engineering.*

