# Changelog

All notable changes to **grokrec** will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [CIAO](https://github.com/cloudgen/ciao) principles.

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
