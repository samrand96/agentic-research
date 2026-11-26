# 6. Browser, Google Drive, Gmail, Calendar and scheduled tasks

These are switched on in the apps themselves. No configuration file is needed.

## Browser

**Claude in Chrome** is a browser extension that lets Claude read, click and navigate websites with you.
Useful for: reading a journal's author guidelines, opening a DOI page to check what a paper really says,
checking a conference deadline. Needs a paid Claude plan.

- Get it: https://claude.com/chrome
- From Claude Code: start with `claude --chrome`, or manage the connection with `/chrome`.
  https://code.claude.com/docs/en/chrome
- The Claude desktop app also has a built-in browser pane.
- **Codex:** the ChatGPT desktop app has a built-in browser for Codex, and Codex has web search.
  https://developers.openai.com/codex/app/browser · https://learn.chatgpt.com/docs/web-search

## Google Drive, Gmail and Google Calendar

These are **Claude's** Google Workspace connectors, available to all Claude users.

1. In a Claude chat, click **+**, then **Connectors**, and switch on the ones you want.
2. Sign in with your Google account when asked.
3. On Team or Enterprise plans, an owner must allow them first.

https://support.claude.com/en/articles/10166901-use-google-workspace-connectors

Good uses: find a survey export or a co-author's draft in Drive; find an editor's email and draft a
reply; block writing time and add submission deadlines to your calendar.

**Rule: the AI drafts, you send.** Read every email and invite before it goes out.

## Scheduled tasks

| Kind | Runs where | When it runs | How to create |
|---|---|---|---|
| Desktop scheduled task | Your computer | On a timetable, while the desktop app is open and the computer awake | In the desktop app. https://code.claude.com/docs/en/desktop-scheduled-tasks |
| Cloud scheduled task (formerly "routines") | Anthropic's cloud | On a timetable, even when your laptop is closed | `/schedule` in Claude Code, or claude.ai/code/routines. Research preview, paid plans. https://code.claude.com/docs/en/routines |
| **Codex automation** | Your computer | On a timetable, while the computer is on and the ChatGPT app is running | In the ChatGPT desktop app's **Scheduled** view (also web and mobile). https://learn.chatgpt.com/docs/automations |
| `/loop` (Claude) | The open session | Every few minutes while the session is open | `/loop 30m <what to do>`. https://code.claude.com/docs/en/scheduled-tasks |

Ideas for research:

- *Every Monday 08:00:* "Search for new papers on my topic since last week, add relevant ones to
  `docs/literature/search-log.md` with the query and counts. Do not add anything to Zotero; list DOIs for me."
- *Every Friday:* "List new papers that cite my five key sources (cite keys in `docs/literature/verified-references.md`)."
- *During data collection:* `/loop 30m check the survey export folder and summarise new responses`

**Rule:** scheduled tasks write files for you to review. They never submit, send or delete.
