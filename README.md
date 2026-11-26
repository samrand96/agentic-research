# Agentic Research — a starter kit for AI-assisted research

**中文说明：[README.zh-CN.md](README.zh-CN.md)**

A ready-to-use starter kit for doing research with an AI assistant, **from research question to
submitted paper**, without losing control of your sources, your data or your results.
It works with **Claude Code** (by Anthropic) and **Codex** (by OpenAI): use either one, or both.

You do **not** need to be a programmer. Everything can be done with desktop apps; the commands in the
guides are optional. It is for students and researchers in any field.
Everything here was checked on the tools' official pages on **26 November 2026**.

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

## Start here (about an hour the first time)

1. **Install the apps:** the Claude desktop app and/or the ChatGPT desktop app, GitHub Desktop, Zotero 10,
   and uv (one line). See `setup-guides/01-install.md`.
2. **Sign in.** Codex is in every ChatGPT plan, even Free. Claude Code needs a paid Claude plan.
3. **Add Better BibTeX to Zotero** and allow other applications to talk to Zotero. Chinese papers: add
   Jasminum (茉莉花). See `setup-guides/04-zotero.md`.
4. **Get your own copy** for each paper: on GitHub click **Use this template** → **Create a new repository**
   (make it **private**), or click **Code → Download ZIP** and unzip it. Name it after your paper, e.g. `my-paper`.
5. **Fill in** `AGENTS.md`: your question, target journal, style and rules.
6. **Get free API keys** and save them as environment variables: `setup-guides/08-api-keys.md` (summary below).
7. **Install the Zotero plug-in once:** `uv tool install zotero-mcp-server`.
8. **Open the folder in your assistant.** Claude: Code tab → open the folder, approve the project's plug-ins.
   Codex: open the folder in the ChatGPT app; the project's plug-in settings only work once the folder is
   trusted, so say yes if Codex asks. Type `/mcp` to check the plug-ins.
9. **Switch on the safety net** with GitHub Desktop: add the folder, first commit, publish as private
   (`setup-guides/02-git-and-github.md`).
10. **Ask for your first task**, for example:
    *"Read AGENTS.md and the plan. Then use the literature-review skill to plan a search for WP1.1.
    Write the plan into the search log and stop for my approval."*

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
