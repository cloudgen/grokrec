# grokrec

[![Version](https://img.shields.io/badge/Version-2.7.0-blue?style=flat-square)](https://github.com/cloudgen/grokrec)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![CIAO](https://img.shields.io/badge/Philosophy-CIAO%20(Caution%20%E2%80%A2%20Intentional%20%E2%80%A2%20Anti--fragile%20%E2%80%A2%20Over--engineered)-purple.svg)](https://github.com/cloudgen/ciao)
[![Shell](https://img.shields.io/badge/Shell-POSIX%20sh-orange?style=flat-square)]()
[![Made with CIAO](https://img.shields.io/badge/Made%20with%20❤️-CIAO-00AEEF?style=flat-square)](https://github.com/cloudgen/ciao)

**CIAO-defensive GitHub source-code review prompt generator**  
*One-file POSIX shell script. Zero dependencies except `git` + `curl` + coreutils.*

---

## What is grokrec?

`grokrec` is a **CIAO-compliant** utility that instantly generates a high-quality, structured prompt for **Grok** (built by xAI) to perform a professional code review and security inspection of your Git repository at a **specific tagged version**.

It intelligently detects the current tag, resolves the **exact tagged commit SHA** (even when `HEAD` is ahead of the tag), supports interactive or non-interactive file selection, and outputs a ready-to-paste prompt with correct `raw.githubusercontent.com` links pointing to the released version.

Built by **Cloudgen Wong** — the creator of the [CIAO philosophy](https://github.com/cloudgen/ciao).

---

## Why Obtain a Recommendation and Security Review from Grok?

Grok has proven to be an exceptionally capable, honest, and thorough code reviewer when given clean, version-accurate information.

A strong real-world example is the official Grok review of **[pomo v1.4.0](https://grok.com/share/c2hhcmQtNA_a3403f9f-2990-443c-a32e-cf1a59be6234)** (another CIAO-based shell project). Grok provided deep static analysis, identified robustness and security improvements, and delivered actionable recommendations suitable for public documentation.

**Key benefits:**

- Independent and unbiased validation
- Strong security-focused analysis (command injection, path traversal, race conditions, etc.)
- Actionable, high-signal feedback with code examples
- Professional report that can be added directly to `README.md` or `RECOMMENDATION.md`

`grokrec` + Grok creates a repeatable, high-quality review process that aligns with CIAO principles.

---

## Features

- Fully **CIAO-compliant** with loud defensive guards (`!!! DO NOT MODIFY OR SIMPLIFY !!!`)
- **Accurate Tagged Commit Resolution** (`get_tagged_commit()` with multi-layered fallback)
- **Robust Semantic Version Comparison** (`version_gt()`) — prevents incorrect downgrades during development
- Interactive file selection + fully non-interactive / JSON mode
- Self-update and self-uninstall commands (battle-field tested)
- Strict root vs non-root handling
- Volatile storage preference (`/dev/shm` → `/tmp`)
- Full respect for `--quiet` and `--json`
- Improved help and about commands

---

## Installation

```bash
# User install (recommended)
curl -fsSL https://raw.githubusercontent.com/cloudgen/grokrec/main/grokrec | sh

# System-wide install
curl -fsSL https://raw.githubusercontent.com/cloudgen/grokrec/main/grokrec | sudo sh
```

---

## Usage

```bash
cd /path/to/your/project

grokrec                    # interactive mode (recommended)
grokrec --json             # machine-readable output (for scripting)
grokrec help               # detailed help
grokrec about              # diagnostics (version, install status, shell, storage, etc.)
grokrec self-update        # update to latest version
grokrec self-uninstall     # clean removal
```

After running `grokrec`, copy the generated prompt and paste it directly into Grok.

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for detailed version history.

---

## Philosophy

`grokrec` is built strictly according to the **[CIAO](https://github.com/cloudgen/ciao)** defensive programming philosophy.

> **CIAO** = **C**aution • **I**ntentional • **A**nti-fragile • **O**ver-engineered

Every critical function contains explicit purpose, warnings, and guards against simplification — especially against common AI tendencies to ignore root/non-root differences, `--quiet` mode, battle-tested logic, and multi-user environments.

---

## Author

**Cloudgen Wong** — Creator of the [CIAO philosophy](https://github.com/cloudgen/ciao)

---

## Related Projects

- [pomo](https://github.com/Wilgat/pomo) — CIAO-based Pomodoro timer
- [SyncPrjs](https://github.com/Wilgat/SyncPrjs) — CIAO-powered project manager

---

**Made with ❤️ and strict CIAO principles.**

*Defensive by design. Anti-fragile by intention.*
