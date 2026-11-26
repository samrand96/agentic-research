# Agentic Research — a starter kit for AI-assisted research

**中文说明：[README.zh-CN.md](README.zh-CN.md)**

A ready-to-use starter kit for doing research with an AI assistant, **from research question to
submitted paper**, without losing control of your sources, your data or your results.
It works with **Claude Code** (by Anthropic) and **Codex** (by OpenAI): use either one, or both.

You do **not** need to be a programmer: you install a few apps and paste three short commands, explained
step by step below. It is for students and researchers in any field.
Everything here was checked on the tools' official pages on **26 November 2026**.

**New here? Go straight to [Install everything, step by step](#install-everything-step-by-step).**

---

## The idea in one minute

You keep each paper in **one folder** on your computer. An AI assistant (Claude Code or Codex) works inside
that folder. It follows **house rules** you write once (`AGENTS.md`), uses **plug-ins** (called MCP servers)
to search 22 real paper databases and your Zotero library, and follows **recipes** (called skills) for
literature reviews, novelty checks, drafting and citation checking. **Git** keeps every version, so any
change can be undone.

Four rules keep the work publishable:

1. **Every citation opened and verified**, never from memory.
2. **A frozen protocol** (hypotheses and analysis plan) before you see any results.
3. **Plans and status files**, so you, a co-author or any AI can pick up where the last one stopped.
4. **No secrets in files**: API keys live in environment variables.

## Claude Code or Codex?

| | Claude Code | Codex |
|---|---|---|
| Easiest way in | Claude desktop app → **Code** tab | ChatGPT desktop app (Codex) |
| Plan needed | Paid Claude plan (Pro or above) | Included in ChatGPT plans, including Free and Go |
| House rules | `CLAUDE.md`, which loads `AGENTS.md` | `AGENTS.md` |
| Plug-in settings (ready in the template) | `.mcp.json` | `.codex/config.toml` |
| Skills folder (ready in the template) | `.claude/skills/` | `.agents/skills/` |
| Use a skill | `/skill-name` | `$skill-name` |

Both are already set up in this repository. You can switch any time, or ask one assistant to check the other's work.

## Install everything, step by step

Do this **once per computer**. It takes about 30–45 minutes. You do not need any programming knowledge:
you will click installers, and paste **three short commands**.

### What you will install, and why

| What | Why you need it | Needed? |
|---|---|---|
| **Claude desktop app** and/or **ChatGPT desktop app** | Your AI assistant (Claude Code is inside the Claude app; Codex is inside the ChatGPT app) | Yes, at least one |
| **Zotero 10** + **Zotero Connector** | Your reference library, and the browser button that saves papers into it | Yes |
| **Better BibTeX** (a Zotero add-on) | Gives every paper a stable citation key | Yes |
| **uv** | A small helper that runs the plug-ins. It downloads Python by itself when needed | Yes |
| **Zotero plug-in** (zotero-mcp) | Lets the assistant read your Zotero library | Yes |
| **GitHub account** + **GitHub Desktop** | Keeps every version of your work, with buttons instead of commands | Recommended |
| **Jasminum (茉莉花)** (a Zotero add-on) | Saves Chinese papers from CNKI, Wanfang and CQVIP | Only for Chinese papers |

**You do NOT need to install Python.** uv downloads it automatically when a plug-in needs it.
**You do NOT need Node.js**, unless you later want the Codex command-line version.
**The paper-search plug-in needs no install:** uv fetches it the first time the assistant uses it.

### Before you start: how to paste a command

You only need this for three commands.

- **Windows:** press the **Windows key**, type **PowerShell**, and click **Windows PowerShell**. A window with
  text appears. Copy a command from this page, **right-click** inside the window (this pastes), then press **Enter**.
- **Mac:** press **Cmd + Space**, type **Terminal**, and press **Enter**. Copy a command from this page, press
  **Cmd + V** inside the window, then press **Enter**.
- After installing something, **close the window and open a new one** before the next step.
  New programs are only found in new windows.

---

### Windows

**Step 1 — Your AI assistant app** (Windows 10 or later)

- **Claude:** go to https://claude.com/download, download the Windows version, run it, and sign in.
  Claude Code is the **Code** tab. It needs a paid Claude plan (Pro or above).
- **ChatGPT (for Codex):** install **ChatGPT** from the Microsoft Store (or see https://learn.chatgpt.com/docs/app)
  and sign in. Codex is included in ChatGPT plans, including Free.

**Step 2 — Zotero 10 and the Zotero Connector**

1. Go to https://www.zotero.org/download/, download **Zotero for Windows**, and install it.
2. On the same page, click the button to install the **Zotero Connector** for your browser (Chrome, Edge or Firefox).
3. Open Zotero → **Edit → Settings → Advanced** → tick **"Allow other applications on this computer to communicate with Zotero"**.

**Step 3 — Better BibTeX**

1. Go to https://github.com/retorquere/zotero-better-bibtex/releases/latest. Under **Assets**, download the
   file that ends in **.xpi**. (In Firefox: right-click the file → **Save Link As…**, otherwise Firefox tries to install it.)
2. In Zotero: **Tools → Plugins** → click the **gear** icon (top right) → **Install Plugin From File…** →
   choose the .xpi file → **Install**.
3. *Chinese papers:* do the same with the Jasminum .xpi from https://github.com/l0o0/jasminum/releases.
   Chinese guide: https://zotero-chinese.com

**Step 4 — uv** (command 1 of 3)

Open **PowerShell** and paste this whole line, then press Enter:

```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Close PowerShell, open a new one, and type `uv --version` then Enter. You should see a version number.

**Step 5 — The Zotero plug-in** (commands 2 and 3 of 3)

In PowerShell, paste these two lines one at a time, pressing Enter after each:

```
uv tool install zotero-mcp-server
uv tool update-shell
```

Close PowerShell and open a new one. Type `uv tool list` then Enter: you should see **zotero-mcp-server** in the list.

**Step 6 — GitHub** (recommended)

1. Create a free account at https://github.com/signup.
2. Install **GitHub Desktop** from https://github.com/apps/desktop and sign in with that account.

**Step 7 — Restart your AI app**

Quit the Claude or ChatGPT app completely and open it again, so it finds uv and the Zotero plug-in.

---

### Mac

**Step 1 — Your AI assistant app**

- **Claude:** go to https://claude.com/download, download the Mac version (macOS 13 Ventura or later),
  drag it to Applications, open it and sign in. Claude Code is the **Code** tab (paid Claude plan, Pro or above).
- **ChatGPT (for Codex):** download the Mac app from https://learn.chatgpt.com/docs/app (the download is
  for Apple Silicon Macs) and sign in. Codex is included in ChatGPT plans, including Free.

**Step 2 — Zotero 10 and the Zotero Connector**

1. Go to https://www.zotero.org/download/, download **Zotero for Mac**, open it and drag Zotero to Applications.
2. On the same page, install the **Zotero Connector** for your browser. (For Safari it comes with Zotero.)
3. Open Zotero → **Zotero → Settings → Advanced** → tick **"Allow other applications on this computer to communicate with Zotero"**.

**Step 3 — Better BibTeX**

Same as Windows step 3: download the **.xpi** from
https://github.com/retorquere/zotero-better-bibtex/releases/latest, then in Zotero
**Tools → Plugins** → **gear** → **Install Plugin From File…**. Chinese papers: same with Jasminum.

**Step 4 — uv** (command 1 of 3)

Open **Terminal** and paste this line, then press Enter:

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Close Terminal, open a new one, and type `uv --version` then Enter. You should see a version number.

**Step 5 — The Zotero plug-in** (commands 2 and 3 of 3)

```
uv tool install zotero-mcp-server
uv tool update-shell
```

Close Terminal, open a new one, type `uv tool list`: you should see **zotero-mcp-server**.

**Step 6 — GitHub** (recommended)

Create a free account at https://github.com/signup, then install **GitHub Desktop** from
https://github.com/apps/desktop (macOS 12 or later) and sign in.
If your Mac ever asks to install **"command line developer tools"**, click **Install**: that is Apple's Git.

**Step 7 — Restart your AI app**

Quit the Claude or ChatGPT app completely (Cmd + Q) and open it again.

---

### If something goes wrong

| What you see | What to do |
|---|---|
| `uv` or `zotero-mcp` "is not recognized" / "command not found" | Close the window and open a new one. Still failing? Restart the computer. |
| Windows says running scripts is disabled | Copy the **whole** uv line from step 4, including `powershell -ExecutionPolicy ByPass`. |
| The assistant cannot see Zotero | Is Zotero open? Is "Allow other applications…" ticked (step 2)? Restart the AI app. |
| Anything else | Copy the error message and ask your assistant: *"I got this error while installing. What should I do?"* |

Official pages for every step: uv https://docs.astral.sh/uv/getting-started/installation/ ·
Zotero https://www.zotero.org/download/ · Better BibTeX https://retorque.re/zotero-better-bibtex/installation/ ·
Zotero plug-in https://github.com/54yyyu/zotero-mcp · GitHub Desktop https://docs.github.com/en/desktop

## Start using it (for each new paper)

1. **Get your own copy:** on this GitHub page click **Use this template** → **Create a new repository**
   (make it **private**), then in GitHub Desktop **File → Clone repository** to put it on your computer.
   No GitHub? Click **Code → Download ZIP** and unzip it. Name it after your paper, e.g. `my-paper`.
2. **Open the folder in your assistant.** Claude: open the **Code** tab and choose the folder; approve the
   project's plug-ins when asked. Codex: open the folder in the ChatGPT app; say yes if it asks whether to
   trust the folder (the plug-ins only work in trusted folders).
3. **Check the plug-ins:** type `/mcp`. You should see **paper-search** and **zotero**.
4. **Fill in `AGENTS.md`**, easiest by asking: *"Fill in AGENTS.md with me: ask me one question at a time."*
5. **Optional: free API keys** for faster paper searches (see below).
6. **Ask for your first task**, for example:
   *"Read AGENTS.md and the plan. Then use the literature-review skill to plan a search for WP1.1.
   Write the plan into the search log and stop for my approval."*
7. **Save versions** in GitHub Desktop: write a short summary, click **Commit to main**, then **Push origin**.

## Where to get API keys (summary)

An API key is a free password that lets the paper-search plug-in ask a database for more results.
You can start without any. Full guide: `setup-guides/08-api-keys.md`.

| Database | Need it? | Where | Cost | Variable name |
|---|---|---|---|---|
| Unpaywall | Yes, for free full texts | No sign-up: an email address you choose | Free | `PAPER_SEARCH_MCP_UNPAYWALL_EMAIL` |
| Semantic Scholar | Recommended | https://www.semanticscholar.org/product/api (key by email) | Free | `PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY` |
| CORE | Recommended | https://core.ac.uk/services/api | Free | `PAPER_SEARCH_MCP_CORE_API_KEY` |
| OpenAlex | Optional | https://openalex.org/signup → Settings → API key | Free | `PAPER_SEARCH_MCP_OPENALEX_API_KEY` |
| Web of Science | Optional | https://developer.clarivate.com/apis/wos-starter | Free trial; more via university | `PAPER_SEARCH_MCP_WOS_API_KEY` |
| Scopus | Optional | https://dev.elsevier.com/apikey/manage | Needs your university's subscription | `PAPER_SEARCH_MCP_SCOPUS_API_KEY` |
| IEEE Xplore | Optional | https://developer.ieee.org | IEEE customers only | `PAPER_SEARCH_MCP_IEEE_API_KEY` |

Save a key (once per computer), never in a file:
Windows PowerShell `setx PAPER_SEARCH_MCP_CORE_API_KEY "paste-your-key-here"`, then reopen the apps.
Mac: add `export PAPER_SEARCH_MCP_CORE_API_KEY="paste-your-key-here"` to `~/.zshrc`.

## What is in this repository

This repository **is** the project template: one copy = one paper.

```
agentic-research/
├── README.md                 this guide (English)      README.zh-CN.md  中文说明
├── AGENTS.md                 house rules every assistant reads (fill in the [brackets])
├── CLAUDE.md                 loads AGENTS.md for Claude Code
├── .mcp.json                 plug-ins for Claude Code (no keys inside)
├── .codex/config.toml        plug-ins for Codex (no keys inside)
├── .claude/skills/           4 research skills for Claude Code
├── .agents/skills/           the same 4 skills for Codex
├── .gitignore  .env.example  keeps secrets and raw data out; lists the key names
├── setup-guides/             step-by-step guides 01–08, plus settings examples
├── docs/plans/  status/      the study plan and one status file per task
├── docs/protocol/            the analysis protocol you freeze before the results
├── docs/literature/          search log, verified references, novelty check
├── docs/reports/             results, each made by a script
└── paper/ data/ analysis/ references/ figures/
```

The guides are inside the project on purpose: your assistant can read them, so you can simply ask it,
for example *"Help me with step 3 of setup-guides/01-install.md"*.

Files and folders starting with a dot (`.mcp.json`, `.codex`, `.claude`, `.agents`) are hidden on some
computers. Windows File Explorer: View → Show → Hidden items. Mac Finder: press Cmd + Shift + . (full stop).

## What is a ".md" file?

Files ending in **.md** (Markdown) are ordinary text files. You do not need any special program:

- **Windows:** right-click the file → Open with → **Notepad**.
- **Mac:** right-click the file → Open With → **TextEdit**.
- **Easiest:** ask your assistant, e.g. *"Fill in AGENTS.md with me: ask me one question at a time."*

`#` at the start of a line is a heading, `-` is a bullet point, and text between `**` is bold. That is all.

## A typical research workflow

| Stage | What happens | File it leaves behind |
|---|---|---|
| 1. Question | Fill in AGENTS.md | `AGENTS.md` |
| 2. Plan | Phases and tasks (work packages) | `docs/plans/01-study-plan.md` |
| 3. Literature | Search, screen, open, file in Zotero (`literature-review`) | `docs/literature/search-log.md`, `verified-references.md` |
| 4. Novelty | Closest papers, all read (`novelty-check`) | `docs/literature/novelty-check.md` |
| 5. Protocol | Freeze hypotheses and analysis plan; commit and tag | `docs/protocol/protocol.md` |
| 6. Analysis | Scripts, never manual edits | `analysis/`, `docs/reports/results.md`, `figures/` |
| 7. Writing | Section by section (`write-section`) | `paper/` |
| 8. Submit | Check every citation (`citation-check`), final review | `docs/reports/citation-check-*.md` |

## Tools used, and where they come from

| Tool | What it is for | Official page |
|---|---|---|
| Claude Code | AI assistant (Claude desktop app, Code tab) | https://code.claude.com/docs/en/setup |
| Codex | AI assistant (ChatGPT desktop app) | https://learn.chatgpt.com/docs/quickstart |
| GitHub Desktop / Git | Versions, private online copy, review of changes | https://github.com/apps/desktop · https://git-scm.com |
| uv | Runs the plug-ins | https://docs.astral.sh/uv/ |
| paper-search-mcp | 22 scholarly databases, MIT licence | https://github.com/openags/paper-search-mcp |
| Zotero 10 | Reference library (interface also in Chinese) | https://www.zotero.org |
| Better BibTeX | Stable cite keys, automatic .bib export, MIT licence | https://retorque.re/zotero-better-bibtex/ |
| Jasminum (茉莉花) | CNKI and other Chinese databases in Zotero, AGPL-3.0 | https://github.com/l0o0/jasminum |
| zotero-mcp (54yyyu) | Lets the assistant read your Zotero library, MIT licence | https://github.com/54yyyu/zotero-mcp |
| Claude in Chrome | Browser for Claude | https://claude.com/chrome |
| Google Workspace connectors | Drive, Gmail, Calendar in Claude | https://support.claude.com/en/articles/10166901-use-google-workspace-connectors |
| Anthropic skills | Word, PowerPoint, PDF, Excel, skill-creator (Claude) | https://github.com/anthropics/skills |
| AGENTS.md | Open format for AI house rules | https://agents.md |

## Safety notes

- This toolkit contains **no real keys, tokens, emails or personal details**. Keep it that way when you share your projects.
- Before installing any plug-in, skill or extension from someone else, read its page and licence:
  it gives your assistant new abilities.
- The paper-search plug-in has a Sci-Hub option. It is off by default; leave it off.
- Anonymise interview and survey data before any AI reads it, and follow your ethics approval.
- Ask the assistant to **draft**; do the sending, submitting and deleting yourself.

## Licence of this toolkit

The guides, templates and skills in this toolkit are licensed under **Creative Commons
Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**: free to use, share and adapt for any
non-commercial purpose (study, research, teaching), with credit. https://creativecommons.org/licenses/by-nc/4.0/

The tools it points to keep their own licences (listed above).

Online home of this toolkit: https://github.com/samrand96/agentic-research
