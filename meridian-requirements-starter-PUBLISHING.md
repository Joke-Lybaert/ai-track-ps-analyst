# Publishing the Meridian requirements starter repo

**Facilitator-only: do not put this file, or anything else outside
`meridian-requirements-starter/`, into what participants clone or open.**

`meridian-requirements-starter/` (sibling folder to this file) is a minimal scaffold.
`backlog.md`, `glossary.md`, `decisions.md`, `open-questions.md`, plus a `.devcontainer/` so it
opens cleanly in a GitHub Codespace with no local install. Until now the FA day had no repo at
all; participants just created files locally by hand. This exists specifically to make the
no-IDE / no-install fallback described in `ai-tooling-fallback.md` actually usable. A
Codespace needs a real repo to open.

**This is optional infrastructure, not a new requirement.** Anyone with a working local setup
can keep working from local files exactly as before; nothing about Block 1–4's content changes.
This just gives everyone else (most of the FA population, per the day's own laptop
requirements) a zero-install way to do the same work.

## One-time setup

Same pattern as the developer and QA repos: its own clean repo, no shared git history with
this internal `ai-track-ps` facilitator materials repo (which contains the Block 4 trap
writeups, engagement-manager briefing, and other facilitator-only content FA participants must
never see).

```bash
cd module-2/functional-analyst/meridian-requirements-starter
git init
git add .
git commit -m "Meridian requirements workspace - starter scaffold"
git branch -M main
git remote add origin <your-new-repo-url>
git push -u origin main
```

Verify it opens as a Codespace the way a participant would experience it: on the repo's GitHub
page, **Code → Codespaces → Create codespace on main**. It should build in under a minute (no
Java/Maven feature to install, unlike the developer and QA repos) and land in VS Code in the
browser with `backlog.md` etc. visible and editable, and the Markdown/Mermaid preview
extensions active.

> **Note on this verification:** I couldn't spin up an actual Codespace from this sandbox to
> confirm the `.devcontainer/devcontainer.json` builds clean: no browser, and Codespaces isn't
> something a headless sandbox can drive. I did validate the JSON is well-formed. Please run
> the check above for real once this is published; it's a two-minute click-through, not a build
> like the developer/QA repos need.

Update the materials checklist in `functional-analyst/facilitator-guide.md` and
`Module2-Laptop-Requirements.md` with the real repo URL once it exists.

## Important: this repo is a shared scratch workspace, not per-team

Unlike the developer and QA repos, participants here open a Codespace directly on this shared
repo rather than forking it first: there was no need for a fork, since nothing here needs to
build or run. That's fine for the Codespace itself (each participant's codespace is a fully
isolated environment; any number of people can create one from the same repo at once with zero
interference between them). It stops being fine the moment someone runs `git push` back to
`main`, that's a normal git collision if two people do it around the same time, and worse,
this repo gets reused across roughly a dozen repeat FA sessions, so one cohort's pushed content
would corrupt the starting point for the next one.

**Tell participants explicitly (also stated in the repo's own `README.md` and in
`block1-prompt-ladders.md`): this Codespace is scratch space for the day only. Don't push
changes back to origin.** Nothing in the day's exercises requires it: the deliverable is what
they show in the retro and showcase, not a git commit. If a team wants to keep their own copy
after the day, the Codespace's own "Export changes to a branch" option (via the Source Control
panel) creates a new branch under their own account rather than touching `main`, mention this
only if someone asks, it's not part of the exercise.

## Keeping it in sync later

This scaffold is deliberately minimal and shouldn't need much maintenance: it only tracks
filenames referenced in the prompt ladders (`backlog.md`, `glossary.md`, `decisions.md`,
`open-questions.md`). If a future block ladder revision expects a differently-named file,
update this scaffold to match.
