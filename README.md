# grokrec

[![Version](https://img.shields.io/badge/Version-2.5.0-blue?style=flat-square)](https://github.com/cloudgen/gorkrec)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![CIAO](https://img.shields.io/badge/Philosophy-CIAO%20(Caution%20%E2%80%A2%20Intentional%20%E2%80%A2%20Anti--fragile%20%E2%80%A2%20Over--engineered)-purple.svg)](https://github.com/cloudgen/ciao)
[![Shell](https://img.shields.io/badge/Shell-POSIX%20sh-orange?style=flat-square)]()
[![Made with CIAO](https://img.shields.io/badge/Made%20with%20❤️-CIAO-00AEEF?style=flat-square)](https://github.com/cloudgen/ciao)

Official recommendation from [grok](https://grok.com/c/285af1c9-b015-45e0-85a6-bf4832f8c6f5?rid=694a559c-5444-4d93-8530-9cfc203e4c6b)

**CIAO-defensive GitHub source-code review prompt generator**  
*One-file POSIX shell script. Zero dependencies except `git` + `curl` + coreutils.*

---

## What is grokrec?

`grokrec` is a **CIAO-compliant** utility that instantly generates a high-quality, structured prompt for **Grok** (built by xAI) to perform a professional code review and security inspection of your Git repository.

It intelligently detects the current tag, resolves the **exact tagged commit** (even when your local `HEAD` is ahead), lets you select source files, and produces a ready-to-paste prompt with correct `raw.githubusercontent.com` links pointing to the released version.

Built by **Cloudgen Wong** — the creator of the [CIAO philosophy](https://github.com/cloudgen/ciao).

---

## Why Obtain a Recommendation and Security Review from Grok?

Grok has proven to be an exceptionally capable, honest, and thorough code reviewer — especially when given clean, complete, and version-accurate information.

A strong real-world example is the official Grok review of **[pomo v1.4.0](https://grok.com/share/c2hhcmQtNA_a3403f9f-2990-443c-a32e-cf1a59be6234)** (another CIAO-based shell project). In that session, Grok:

- Conducted a deep static analysis of the entire codebase
- Identified subtle robustness, POSIX compatibility, and security improvements
- Provided clear, actionable recommendations with code examples
- Confirmed the absence of common vulnerabilities (command injection, path traversal, race conditions, etc.)
- Praised the defensive CIAO patterns while suggesting even stronger anti-fragile techniques
- Produced a professional-grade report suitable for public documentation

**Benefits of using Grok for reviews:**

- **Independent & unbiased validation** — Grok has no emotional attachment to your code and will honestly point out issues you might have overlooked.
- **Security-focused mindset** — Trained to think like a security researcher, catching problems traditional linters often miss.
- **High-signal, actionable feedback** — You receive concrete suggestions (refactoring ideas, safer patterns, better error handling) that directly improve code quality and security.
- **Beautiful documentation** — The resulting review can be added directly to your `README.md` or `RECOMMENDATION.md` as an official “Grok Security & Code Review” section, giving users and contributors immediate confidence.
- **Repeatable process** — Running `grokrec` before every release turns security & code review into a fast, consistent part of your workflow.

In short, `grokrec` + Grok creates a powerful **continuous improvement loop** that aligns perfectly with CIAO principles: Caution, Intentionality, Anti-fragility, and Over-engineering.

---

## What Information Grok Needs

For Grok to deliver its best review, it requires:

- Repository URL
- Tag name + **exact tagged commit SHA** (not just current HEAD)
- The actual source files at the released version (via stable raw links)
- Clear review intent

`grokrec` automatically assembles all of this using CIAO-defensive logic, including the new `get_tagged_commit()` function.

---

## Features

- Fully **CIAO-compliant** (see [cloudgen/ciao](https://github.com/cloudgen/ciao))
- Correctly resolves tagged commit even when `HEAD` is ahead of the tag
- Interactive file selection or fully non-interactive mode
- JSON output support for scripting/CI
- Self-update command
- Volatile prompt storage (`/dev/shm` preferred)
- Zero external dependencies

---

## Installation

```bash
# User install
curl -fsSL https://raw.githubusercontent.com/cloudgen/gorkrec/main/grokrec | sh

# System-wide install
curl -fsSL https://raw.githubusercontent.com/cloudgen/gorkrec/main/grokrec | sudo sh
```

---

## Usage

```bash
cd /path/to/your/project
grokrec          # interactive mode (recommended)
grokrec --json   # machine-readable output
grokrec help
```

After running, copy the generated prompt and paste it directly into Grok.

---

## Philosophy

`grokrec` is built strictly according to the **[CIAO](https://github.com/cloudgen/ciao)** defensive programming philosophy created by Cloudgen Wong.

> **CIAO** = **C**aution • **I**ntentional • **A**nti-fragile • **O**ver-engineered

Every important function includes explicit General Purpose, reasoning, and `!!! DO NOT MODIFY OR SIMPLIFY !!!` guards. This makes the script extremely robust in minimal environments, containers, non-interactive shells, and across different POSIX implementations.

---

## Author

**Cloudgen Wong** — Creator of the [CIAO philosophy](https://github.com/cloudgen/ciao)

---

## Related Projects

- [pomo](https://github.com/wilgat/pomo) — CIAO-based Pomodoro timer
- [SyncPrjs](https://github.com/Wilgat/SyncPrjs) — CIAO-powered project manager

---

**Made with ❤️ and strict CIAO principles.**

*Defensive by design. Anti-fragile by intention.*
