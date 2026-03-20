# CertiK Skills for AI Agents

**Bring blockchain security intelligence directly into your AI coding agent.**

This repository provides a collection of production-ready skills that connect AI agents — such as [Claude Code](https://claude.ai), [Codex](https://openai.com), and [Cursor](https://cursor.com) — to [CertiK](https://www.certik.com)'s security infrastructure. Each skill is self-contained, requires no external dependencies beyond Python 3.10+, and is designed to be invoked by AI agents as part of natural-language workflows.

---

## Table of Contents

- [Skills Overview](#skills-overview)
- [Quick Start](#quick-start)
- [Repository Structure](#repository-structure)
- [Requirements](#requirements)
- [License](#license)

---

## Skills Overview

| Skill | Description | Auth Required |
|-------|-------------|:---:|
| [**Skynet Score**](./skills/skynet-score/README.md) | Project-level security ratings and score breakdowns from CertiK Skynet | No |
| [**SkyInsights**](./skills/skyinsights/README.md) | Address & transaction risk scoring, AML compliance screening, entity attribution | Yes |
| [**Skylens**](./skills/skylens/README.md) | Deep EVM transaction investigation — execution traces, balance & state changes, source code | No |
| [**Token Scan**](./skills/token-scan/README.md) | Token contract security analysis — risk alerts, tax detection, holder concentration, LP locks | No |

---

## Quick Start

### Install via CLI

```bash
npx skills add certikdev/skills
```

### Manual Installation

Clone this repository and copy the skill folders you need into your agent's skill directory:

```bash
git clone https://github.com/certikdev/skills.git
cp -R skills/skills/skyinsights ~/.claude/skills/   # Claude Code
cp -R skills/skills/skylens     ~/.codex/skills/     # Codex
cp -R skills/skills/token-scan  ~/.cursor/skills/    # Cursor
```

| Agent | Skill Directory |
|-------|-----------------|
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| Cursor | `~/.cursor/skills/` |

---

## Repository Structure

```text
.
├── LICENSE
├── README.md
└── skills/
    ├── skyinsights/              # Address & transaction risk intelligence
    │   ├── README.md             # Human-oriented documentation
    │   ├── SKILL.md              # Agent-oriented skill definition
    │   ├── agents/
    │   │   └── openai.yaml       # OpenAI agent integration config
    │   ├── reference/
    │   │   ├── error-codes.md
    │   │   ├── risk-factors.md
    │   │   └── supported-chains.md
    │   └── scripts/
    │       └── skyinsights.py    # CLI wrapper (authenticated API)
    ├── skylens/                  # EVM transaction forensics
    │   ├── README.md
    │   ├── SKILL.md
    │   └── scripts/
    │       └── skylens.py        # CLI wrapper (public API)
    ├── skynet-score/             # Project security ratings
    │   ├── README.md
    │   ├── SKILL.md
    │   └── scripts/
    │       └── skynet_score.py   # CLI wrapper (public API)
    └── token-scan/               # Token contract security analysis
        ├── README.md
        ├── SKILL.md
        └── scripts/
            └── token_scan.py     # CLI wrapper (public API)
```

Each skill is self-contained:

- **`SKILL.md`** — Structured definition that AI agents use to understand when and how to invoke the skill.
- **`README.md`** — Human-readable documentation (content consolidated into this central README).
- **`scripts/`** — Standalone CLI tools with no external dependencies beyond the Python standard library.
- **`agents/`** — Optional agent-specific integration config (currently used by SkyInsights).
- **`reference/`** — Supporting reference material (SkyInsights only).

---

## Requirements

| Requirement | Details |
|-------------|---------|
| **Python** | 3.10 or later |
| **Dependencies** | Standard library only (`urllib`, `json`, `argparse`) — no pip install needed |
| **zstandard** | Required for Skylens only (`pip install zstandard`, or Python 3.14+ built-in) |
| **Network** | Outbound HTTPS to CertiK API endpoints |
| **Credentials** | Required for SkyInsights only (`SKYINSIGHTS_API_KEY`, `SKYINSIGHTS_API_SECRET`) |

---

## License

This project is licensed under the [MIT License](LICENSE).

---

Built by [CertiK](https://www.certik.com) — the largest blockchain security auditor, trusted to secure over $600B in digital assets.
