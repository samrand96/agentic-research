# 8. Where to get API keys for paper databases

An **API key** is like a free library card for a database: it lets the paper-search plug-in ask the
database for more results, faster. You do **not** need any key to start. The plug-in works without
keys, just more slowly, and skips Unpaywall until you give it an email address.

Checked on the official pages on **26 November 2026**.

## Quick table

| Database | Do you need it? | Where to get it | Cost / who can get it | Environment variable name |
|---|---|---|---|---|
| **Unpaywall** (free full texts) | Yes, to use Unpaywall | No sign-up. You only give an email address you choose | Free, anyone | `PAPER_SEARCH_MCP_UNPAYWALL_EMAIL` |
| **Semantic Scholar** | Recommended | https://www.semanticscholar.org/product/api → "Request an API key" form. The key arrives by email | Free | `PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY` |
| **CORE** (open-access papers) | Recommended | https://core.ac.uk/services/api → register | Free | `PAPER_SEARCH_MCP_CORE_API_KEY` |
| **OpenAlex** | Optional (10 times more requests per day) | Sign up at https://openalex.org/signup, then copy the key from https://openalex.org/settings/api-key | Free account | `PAPER_SEARCH_MCP_OPENALEX_API_KEY` (and optionally `PAPER_SEARCH_MCP_OPENALEX_EMAIL`) |
| **Web of Science** (Starter API) | Optional, only when you ask for Web of Science by name | https://developer.clarivate.com/apis/wos-starter → register an application | Free trial for anyone (50 requests a day); more if your university subscribes | `PAPER_SEARCH_MCP_WOS_API_KEY` |
| **Scopus** (Elsevier) | Optional, only when you ask for Scopus by name | https://dev.elsevier.com/apikey/manage | The key is free, but data only comes through your **university's subscription**, usually on the campus network (or with an institutional token from Elsevier) | `PAPER_SEARCH_MCP_SCOPUS_API_KEY` |
| **IEEE Xplore** | Optional | https://developer.ieee.org/member/register | Only for current IEEE customers, non-commercial research; metadata and open-access content only | `PAPER_SEARCH_MCP_IEEE_API_KEY` |
| **DOAJ** | Not needed | Keys are mainly for publishers who submit data to DOAJ | — | `PAPER_SEARCH_MCP_DOAJ_API_KEY` |
| **Zenodo** | Not needed (only for private records) | https://zenodo.org/account/settings/applications/tokens/new/ | Free account | `PAPER_SEARCH_MCP_ZENODO_ACCESS_TOKEN` |

**For most students:** set the Unpaywall email, and get Semantic Scholar, CORE and OpenAlex keys. Add Scopus or Web of Science if your university library offers them.

**Google Scholar** has no official API. The plug-in searches it, but Google may block automated searches
(it shows CAPTCHAs, which the plug-in does not solve). The other databases keep working when that happens.

**Crossref** (DOI lookups) needs no key.

## Rules from the providers worth knowing

- **Semantic Scholar:** a new key starts at 1 request per second. Commercial use needs their permission.
  https://www.semanticscholar.org/product/api
- **OpenAlex:** without a key, 10 requests per second; with a free key, 30 per second and 10 times the
  daily budget. https://help.openalex.org/how-to-use-the-api/rate-limits-and-authentication
- **IEEE:** using their content to train AI models is not allowed without IEEE's written consent.
  https://developer.ieee.org/API_Terms_of_Use2
- **Scopus:** "A key alone does not provide data or content access"; access follows your institution's
  subscription. https://dev.elsevier.com/support.html

## How to save a key (once per computer)

Never paste a key into a file in your project, a chat, a slide or an email. Save it as an
**environment variable** instead. Both Claude Code and Codex read it from there.

**Windows (PowerShell):** one line per key, then close and reopen the terminal and the apps:

```
setx PAPER_SEARCH_MCP_UNPAYWALL_EMAIL "an-email-you-choose@example.org"
setx PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY "paste-your-key-here"
setx PAPER_SEARCH_MCP_CORE_API_KEY "paste-your-key-here"
setx PAPER_SEARCH_MCP_OPENALEX_API_KEY "paste-your-key-here"
```

**macOS:** open Terminal, type `touch ~/.zshrc && open -e ~/.zshrc`, add these lines at the end, save,
then open a new Terminal window:

```
export PAPER_SEARCH_MCP_UNPAYWALL_EMAIL="an-email-you-choose@example.org"
export PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY="paste-your-key-here"
export PAPER_SEARCH_MCP_CORE_API_KEY="paste-your-key-here"
export PAPER_SEARCH_MCP_OPENALEX_API_KEY="paste-your-key-here"
```

(Linux: the same lines in `~/.bashrc`.)

**Check it worked** (new terminal): Windows `echo $env:PAPER_SEARCH_MCP_CORE_API_KEY`, Mac/Linux
`echo $PAPER_SEARCH_MCP_CORE_API_KEY`. It should print your key. Then in Claude Code or Codex type `/mcp`.

## How the assistants get the key

- **Claude Code** reads `${PAPER_SEARCH_MCP_CORE_API_KEY:-}` in the project's `.mcp.json`.
- **Codex** passes the names listed under `env_vars` in `.codex/config.toml`.

Neither file contains the key itself, so both are safe to share and to put on GitHub.
Source for the variable names: https://github.com/openags/paper-search-mcp
