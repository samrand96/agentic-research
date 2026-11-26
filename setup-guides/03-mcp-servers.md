# 3. MCP servers: plug the assistant into papers, Zotero, a browser and your Google account

**MCP** (Model Context Protocol) is a standard plug-in. An MCP server gives the assistant new tools:
search 22 paper databases, read your Zotero library, and so on. The same plug-ins work in **Claude Code and Codex**;
only the settings file differs.

| | Claude Code | Codex |
|---|---|---|
| Project settings file (in the toolkit) | `.mcp.json` | `.codex/config.toml` (used once you mark the folder as trusted) |
| Settings for all projects | `claude mcp add --scope user ...` | `~/.codex/config.toml` |
| How keys get in | `${NAME}` in the file | names listed under `env_vars` |
| Check | `/mcp` | `/mcp` or `codex mcp list` |

## What you get, and where each one comes from

| What | How you connect it | Configured in a file? |
|---|---|---|
| **Paper search**: arXiv, Semantic Scholar, OpenAlex, Crossref, PubMed, Google Scholar, SSRN and 15 more | MCP server `paper-search-mcp` | Yes: `.mcp.json` |
| **Zotero**: your library, notes, full text | MCP server `zotero-mcp` | Yes: `.mcp.json` |
| **Browser** | Claude in Chrome (extension), or the desktop app's built-in browser | No: `claude --chrome` or `/chrome` |
| **Google Drive, Gmail, Google Calendar** | Claude connectors | No: in Claude, **+** → **Connectors** |
| **Scheduled tasks** | Built into Claude Code and the desktop app | No: see `06-connectors-and-scheduled-tasks.md` |

## Step 1 — keys go in environment variables, never in files

Some sources work better with a free key. **Where to get each key: `08-api-keys.md`.** Set them once, as environment variables:

**Windows (PowerShell)**: one line per key, then open a **new** terminal:

```
setx PAPER_SEARCH_MCP_UNPAYWALL_EMAIL "an-email-you-choose@example.org"
setx PAPER_SEARCH_MCP_CORE_API_KEY "paste-your-key-here"
```

`setx` makes the value available in future terminal windows, not the current one.
https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/setx

**macOS / Linux**: add lines like these to `~/.zshrc` (Mac) or `~/.bashrc` (Linux), then open a new terminal:

```
export PAPER_SEARCH_MCP_UNPAYWALL_EMAIL="an-email-you-choose@example.org"
export PAPER_SEARCH_MCP_CORE_API_KEY="paste-your-key-here"
```

The full list is in `.env.example` in your project folder (names only, no values).

| Variable | Needed? | Where to get it |
|---|---|---|
| `PAPER_SEARCH_MCP_UNPAYWALL_EMAIL` | Required for the Unpaywall source | An email address you choose to use |
| `PAPER_SEARCH_MCP_CORE_API_KEY` | Recommended | https://core.ac.uk |
| `PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY` | Optional | https://www.semanticscholar.org/product/api |
| `PAPER_SEARCH_MCP_OPENALEX_API_KEY` | Optional (raises the speed limit) | https://openalex.org |

## Step 2 — the project's `.mcp.json` (already in the template)

```json
{
  "mcpServers": {
    "paper-search": {
      "command": "uvx",
      "args": ["paper-search-mcp"],
      "env": {
        "PAPER_SEARCH_MCP_UNPAYWALL_EMAIL": "${PAPER_SEARCH_MCP_UNPAYWALL_EMAIL:-}",
        "PAPER_SEARCH_MCP_CORE_API_KEY": "${PAPER_SEARCH_MCP_CORE_API_KEY:-}"
      }
    },
    "zotero": {
      "command": "zotero-mcp",
      "args": [],
      "env": { "ZOTERO_LOCAL": "true" }
    }
  }
}
```

- `${NAME}` is replaced by the environment variable when Claude Code starts. `${NAME:-}` means
  "empty if not set". So the file contains **no keys** and is safe to commit and share.
- The first time you open the project, Claude Code asks you to approve these project servers.
- Type `/mcp` inside Claude Code to see each server and whether it is connected.

Docs: https://code.claude.com/docs/en/mcp

## Step 2b — the same for Codex: `.codex/config.toml` (already in the template)

```toml
[mcp_servers.paper-search]
command = "uvx"
args = ["paper-search-mcp"]
env_vars = ["PAPER_SEARCH_MCP_UNPAYWALL_EMAIL", "PAPER_SEARCH_MCP_CORE_API_KEY"]

[mcp_servers.zotero]
command = "zotero-mcp"
args = []

[mcp_servers.zotero.env]
ZOTERO_LOCAL = "true"
```

- `env_vars` passes the variables in from your environment, so the file holds **no keys**.
- Codex uses a project's `.codex/config.toml` only when the project is **trusted**. To use the plug-ins in
  every project instead, copy the same blocks into `~/.codex/config.toml` (see `setup-guides/settings-examples/codex-config.example.toml`).

Docs: https://learn.chatgpt.com/docs/extend/mcp

## Or add them by command (instead of the files)

```
uv tool install zotero-mcp-server

claude mcp add paper-search -- uvx paper-search-mcp
claude mcp add zotero -e ZOTERO_LOCAL=true -- zotero-mcp

codex mcp add paper-search -- uvx paper-search-mcp
codex mcp add zotero --env ZOTERO_LOCAL=true -- zotero-mcp
```

For Claude, add `--scope user` to make a server available in all your projects. `codex mcp add` writes to
`~/.codex/config.toml`, which applies to all your projects.

## About each server

**paper-search-mcp** — https://github.com/openags/paper-search-mcp
- MIT licence, about 3,200 GitHub stars when checked (26 Nov 2026). PyPI: `paper-search-mcp`.
- Sources: arXiv, PubMed, bioRxiv, medRxiv, Google Scholar, IACR, Semantic Scholar, Crossref, OpenAlex,
  PubMed Central, CORE, Europe PMC, dblp, OpenAIRE, CiteSeerX, DOAJ, BASE, Zenodo, HAL, SSRN,
  OpenReview, Unpaywall. IEEE Xplore, Web of Science and Scopus need your own institutional keys.
- It has a Sci-Hub download option, off by default. **Leave it off.**

**zotero-mcp** — see `04-zotero.md`.

**Paper-Preflight** (optional, for LaTeX papers) — https://github.com/amos689/paper-preflight
- MIT licence, a small and newer project. It checks every reference of a LaTeX paper against real
  records before submission. Read its README and decide yourself before relying on it.

## The Claude desktop app's chat (not the Code tab)

The Code tab uses the project's `.mcp.json`. The desktop app's **chat** uses a separate settings file,
`claude_desktop_config.json`. An example is in `setup-guides/settings-examples/`. That file does not read environment
variables, so a key would have to be typed into it: keep it on your own computer and never share it.
