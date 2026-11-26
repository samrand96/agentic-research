# Configuration examples

## Which file is which

| File | Used by | Holds keys? |
|---|---|---|
| `.mcp.json` (top folder of this repository) | Claude Code (terminal, editor, and the desktop app's **Code** tab), for one project | **No.** It reads keys from environment variables with `${NAME}` |
| `.codex/config.toml` (top folder of this repository) | Codex, for one project (once the folder is trusted) | **No.** `env_vars` passes keys in from your environment |
| `codex-config.example.toml` (here) | Codex, for **all** your projects: copy into `~/.codex/config.toml` | **No** |
| `claude_desktop_config.example.json` (here) | The Claude desktop app's **chat** | Only placeholders here. The real file on your computer would hold keys, so never share it |

## Using the desktop example

1. In the Claude desktop app: **Settings → Developer → Edit Config**. This opens (or creates)
   `claude_desktop_config.json`:
   - Windows: `%APPDATA%\Claude\claude_desktop_config.json`
   - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Linux: `~/.config/Claude/claude_desktop_config.json`
2. Copy the `mcpServers` block from the example into it. Replace each `PASTE-...` value, or delete
   lines you do not need. Keep the file on your own computer only.
3. Save and restart the app.
4. If a server fails with "command not found", put the full path to `uvx` or `zotero-mcp` in
   `"command"` (find it with `where uvx` on Windows or `which uvx` on macOS/Linux).

Source: https://modelcontextprotocol.io/docs/develop/connect-local-servers

The desktop app also installs reviewed **extensions** from Settings, which may be easier than editing
this file: https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop

## Not configured in a file

- **Browser**: Claude in Chrome (`claude --chrome`), or the desktop app's built-in browser.
- **Google Drive, Gmail, Google Calendar**: in a Claude chat, **+ → Connectors**.
- **Scheduled tasks**: built into Claude Code and the desktop app.

See `setup-guides/03-mcp-servers.md` and `setup-guides/06-connectors-and-scheduled-tasks.md`.
