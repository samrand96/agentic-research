# 1. Install the tools

> **New to all this?** The simplest, click-by-click instructions for Windows and Mac are in the main
> [README](../README.md#install-everything-step-by-step) (中文：[README.zh-CN](../README.zh-CN.md#一步一步安装所有工具)).
> This page has more options and details.
>
> **You do not need to install Python:** uv downloads it automatically when needed.
> After installing a tool with `uv tool install`, run `uv tool update-shell` once and open a new terminal.

Checked on the official pages on **26 November 2026**. Install commands change; if one fails, open the
link next to it and use what the page says today.

You need: **an AI assistant** (Claude Code, Codex, or both), **Git** or **GitHub Desktop** (keeps every version),
**uv** (runs the plug-ins), **Zotero 10** with **Better BibTeX** (references).

## Not a programmer? Start with the apps

| App | What it gives you | Where |
|---|---|---|
| Claude desktop app | Claude Code in the **Code** tab (needs a paid Claude plan, Pro or above) | https://claude.com/download |
| ChatGPT desktop app | Codex (included in ChatGPT plans, including Free and Go) | https://learn.chatgpt.com/docs/app |
| GitHub Desktop | Git with buttons instead of commands | https://github.com/apps/desktop |
| Zotero 10 | Your reference library | https://www.zotero.org/download/ |

You still need **uv** for the plug-ins (one line, below). Everything else in this file is for people who like the terminal.

Copy one line at a time. On Windows use **PowerShell**; on a Mac use **Terminal**.

## Git — https://git-scm.com/install

| System | Command |
|---|---|
| Windows | `winget install --id Git.Git -e --source winget` |
| macOS | `xcode-select --install` (or `brew install git` if you use Homebrew) |
| Ubuntu / Debian | `sudo apt-get install git` |
| Fedora | `sudo dnf install git` |

The winget package is not maintained by the Git for Windows team and can lag a little behind.
Version on 26 Nov 2026: Git 2.56.1.

## Claude Code — https://code.claude.com/docs/en/setup

| System | Command |
|---|---|
| Windows (PowerShell) | `irm https://claude.ai/install.ps1 \| iex` |
| macOS, Linux | `curl -fsSL https://claude.ai/install.sh \| bash` |

- The native installer is the recommended one and updates itself.
- Alternatives that do **not** update themselves: `winget install Anthropic.ClaudeCode`,
  `brew install --cask claude-code`.
- You need a paid Claude plan (Pro or above). The free plan does not include Claude Code.
- Version on 26 Nov 2026: 2.1.332.

**Prefer clicking?** Install the Claude desktop app from https://claude.com/download and use its
**Code** tab. It is the same Claude Code, with panes for files, a browser and tasks.

**In a code editor?** VS Code extension: https://code.claude.com/docs/en/vs-code ·
JetBrains plugin: https://code.claude.com/docs/en/jetbrains

## Codex — https://learn.chatgpt.com/docs/codex/cli

| System | Command |
|---|---|
| Windows | `npm install -g @openai/codex` (needs Node.js from https://nodejs.org) |
| Windows (OpenAI's script) | `powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 \| iex"` |
| macOS, Linux | `curl -fsSL https://chatgpt.com/codex/install.sh \| sh` |

- Easiest: the ChatGPT desktop app, which OpenAI's quickstart marks as recommended.
- Sign in with your ChatGPT account (run `codex`, then "Sign in with ChatGPT").
- Codex runs natively on Windows. Version on 26 Nov 2026: Codex CLI 0.172.0. Source: https://github.com/openai/codex

## uv — https://docs.astral.sh/uv/getting-started/installation/

| System | Command |
|---|---|
| Windows | `winget install --id=astral-sh.uv -e` |
| macOS, Linux | `curl -LsSf https://astral.sh/uv/install.sh \| sh` |

`uvx` (comes with uv) runs a tool without installing it. The paper-search plug uses it.
Version on 26 Nov 2026: uv 0.13.10.

## Zotero 10 and Better BibTeX

See `04-zotero.md`.

## Optional

- **GitHub Desktop** (git without typing): https://github.com/apps/desktop
- **GitHub CLI** (`gh`): Windows `winget install --id GitHub.cli --source winget`, macOS `brew install gh`.
  https://cli.github.com/
- **Google Antigravity**: https://antigravity.google/download

## Check it worked

Open a **new** terminal and run:

```
git --version
claude --version     (if you installed Claude Code)
codex --version      (if you installed Codex)
uv --version
```

Each should print a version number.

## First sign-in

Claude: open the Claude desktop app, or type `claude` in a terminal, and follow the login steps in the browser.
Codex: open the ChatGPT desktop app, or type `codex` in a terminal and choose "Sign in with ChatGPT".
