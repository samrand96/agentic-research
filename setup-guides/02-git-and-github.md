# 2. Git and GitHub

**Git** keeps a snapshot of your project every time you "commit", so any change, including a bad
AI edit, can be undone. **GitHub** keeps an off-site copy and lets you review changes before they
join the main copy.

## The easy way: GitHub Desktop (no typing)

Download: https://github.com/apps/desktop

1. **Add your paper folder:** File → Add local repository (Mac: Add Local Repository), choose the folder.
2. **Save a snapshot:** type a short summary at the bottom left, e.g. "Screening log done", and click **Commit to main**.
3. **Put it online, privately:** click **Publish repository** and keep **"Keep this code private"** ticked.
4. **After that:** click **Push origin** to send new snapshots.
5. **One task, one branch:** Current Branch → New Branch, name it (e.g. `wp-1.1-search`) → Create Branch.
   Work and commit as usual, click **Publish branch**, then **Create Pull Request**. GitHub opens in your
   browser: read every changed line, then merge.

Sources: https://docs.github.com/en/desktop

The rest of this page is the same thing with commands, for those who prefer typing.

## One-time set-up

```
git config --global user.name "Your Name"
git config --global user.email "ID+USERNAME@users.noreply.github.com"
```

Use GitHub's private **noreply** address so your real email is not written into every commit.
Find yours under GitHub → Settings → Emails ("Keep my email addresses private").
https://docs.github.com/en/account-and-profile/reference/email-addresses-reference

## Start a project

In your paper folder (your copy of this repository, if you downloaded it as a ZIP):

```
git init -b main
git add .
git commit -m "Start project from template"
```

`git init -b main` names the first branch "main". https://git-scm.com/docs/git-init

## Put it on GitHub, privately

With the GitHub CLI (https://cli.github.com/):

```
gh auth login
gh repo create my-paper --private --source=. --push
```

`gh auth login` opens a browser to sign in and stores the token in your system's credential store.
Or use GitHub Desktop: File → Add local repository, then Publish repository, with "Keep this code private" ticked.

## The daily rhythm

| You want to | Command |
|---|---|
| See what changed | `git status` and `git diff` |
| Save a snapshot | `git add .` then `git commit -m "What you did"` |
| Throw away unsaved changes since the last snapshot | `git restore .` |
| Send snapshots to GitHub | `git push` |

**Habit:** commit before you ask the AI for a big change.

## One work package = one branch = one pull request

```
git switch -c wp/1.1-search          # new branch for work package 1.1
# ... work, commit as you go ...
git push -u origin wp/1.1-search
gh pr create --fill                   # pull request, title and text from your commits
```

On GitHub, open the pull request, read every changed line ("Files changed"), then merge.
Reading that diff is how you stay the author.

- Pull requests: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests
- `gh pr create`: https://cli.github.com/manual/gh_pr_create

## Freeze the protocol with a tag

```
git add docs/protocol/protocol.md
git commit -m "Freeze protocol"
git tag protocol-v1
git push --tags
```

The tag proves when the protocol was fixed.

## What never goes into git

The template's `.gitignore` already keeps out: `.env` files and keys, raw and processed data,
downloaded PDFs, and temporary files. Check with `git status` before every commit.

- GitHub blocks known secrets in pushes to **public** repositories by default (push protection).
  Do not rely on it: keep keys out of files in the first place.
  https://docs.github.com/en/code-security/secret-scanning/introduction/about-push-protection
- GitHub refuses files over 100 MiB. For big data, use your institution's storage, not git.
  https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github
- More `.gitignore` templates: https://github.com/github/gitignore (CC0)
