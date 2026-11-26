# 4. Zotero, Better BibTeX and the Zotero MCP server

Rule of thumb: **if it is not in Zotero, it is not in the paper.**

## 4.1 Zotero 10

- Download: https://www.zotero.org/download/ (current version on 26 Nov 2026: Zotero 10).
- Install the **Zotero Connector** for your browser from the same page (Chrome, Firefox, Edge;
  for Safari it comes with Zotero). It saves a paper and its PDF in one click.
- Citing in Word, LibreOffice or Google Docs: the Zotero word processor plugin.
  https://www.zotero.org/support/word_processor_integration

## 4.1b Chinese papers: CNKI (知网), Wanfang (万方), CQVIP (维普), Baidu Scholar (百度学术)

The official Zotero Connector does not save CNKI items. The Zotero Chinese community fills the gap:

- **Jasminum (茉莉花)** plugin: CNKI metadata, matching PDF and CAJ files, Chinese name splitting, and it
  updates the Chinese translators. Needs **Zotero 9.0.3 or later**. Licence AGPL-3.0. https://github.com/l0o0/jasminum
- **Chinese translators** (CNKI, Wanfang, CQVIP, Baidu Scholar): https://github.com/l0o0/translators_CN
- Step-by-step guide in Chinese: https://zotero-chinese.com/user-guide/faqs/update-translators.html
  In short: install Jasminum; in its settings, update the Chinese translators (立即更新); then in your
  browser's Zotero Connector options → Advanced → "Reset Translators", and restart the browser.
- Zotero's interface can be switched to Simplified Chinese: Settings → Advanced → Language.

## 4.2 Better BibTeX (stable cite keys, automatic .bib export)

Site: https://retorque.re/zotero-better-bibtex/ · Licence: MIT

1. Go to the latest release: https://github.com/retorquere/zotero-better-bibtex/releases/latest
   and download the `.xpi` file. In Firefox, right-click the link and choose "Save link as"
   (clicking it would try to install it into Firefox).
2. In Zotero: **Tools → Plugins**, click the **gear** icon, choose **Install Plugin From File…**, pick the `.xpi`.
3. Restart Zotero if asked. Better BibTeX updates itself after that.

Installation guide: https://retorque.re/zotero-better-bibtex/installation/

**Automatic export to your project:**

1. In Zotero's left pane, right-click your library or the project's collection and choose
   **Export Library…** or **Export Collection…**
2. Format: **Better BibTeX**. Tick **Keep updated**.
3. Save as `references/library.bib` inside your project folder.

From now on the file updates itself when the library changes.
https://retorque.re/zotero-better-bibtex/exporting/auto/

## 4.3 Let other applications talk to Zotero

Zotero → **Settings → Advanced** → tick **"Allow other applications on this computer to communicate with Zotero"**.
Zotero must be running when the assistant uses it.
https://www.zotero.org/support/dev/web_api/v3/local_api

## 4.4 The Zotero MCP server — which one, and why

We checked the main open-source options on 26 Nov 2026:

| Project | Licence | Activity | Can it change your library? | Notes |
|---|---|---|---|---|
| **54yyyu/zotero-mcp** (recommended) | MIT (server); its separate Zotero plugin is AGPL-3.0 | ~6,000 stars; five releases in November 2026 | Yes: adds items by DOI, tags, notes; Zotero 10 asks you to approve writes | Reads your local library; PyPI package `zotero-mcp-server` |
| kujenga/zotero-mcp | MIT | ~160 stars | No: search, metadata and full text only | PyPI package `zotero-mcp`; a good read-only choice |
| cookjohn/zotero-mcp | MIT | ~1,300 stars | Yes (can be switched off) | A Zotero plugin with its own server |

Why 54yyyu: the most used, actively maintained, open licence, and local-first. It has a single
main maintainer, so check its page now and then.

**Careful:** the command `uvx zotero-mcp` runs **kujenga's** package, not 54yyyu's. Use the commands below.

Install and connect (54yyyu):

```
uv tool install zotero-mcp-server
claude mcp add zotero -e ZOTERO_LOCAL=true -- zotero-mcp
```

Or rely on the template, which already has the `zotero` entry for Claude (`.mcp.json`) and Codex (`.codex/config.toml`).
For Codex by command: `codex mcp add zotero --env ZOTERO_LOCAL=true -- zotero-mcp`
The project's README also describes a `zotero-mcp setup` command and other options; read it there.

- Repository: https://github.com/54yyyu/zotero-mcp
- Package: https://pypi.org/project/zotero-mcp-server/

## 4.5 Good habits

- Save every paper you read to Zotero with the Connector, from the publisher's page (better metadata).
- Put PDFs you download for the project in `references/pdfs/` only if you need them there; git ignores it.
- Never let the assistant "fix" a reference by guessing. If metadata looks wrong, open the DOI and correct it in Zotero.
