# Your first change

Your app should already be running from [the README](https://github.com/kaw393939/218_spec#readme). Keep its terminal open. Use a second terminal in the same project folder for Git.

**Before:** Note has a limit you cannot see. **After:** this sentence appears directly below the box, before typing:

> Add a short note (up to 4,000 characters).

That is **PRACTICE-001**. This small change rehearses how to guide AI and verify its work. Saving and the existing limit stay unchanged.

## 1. Agree a plan

In **ChatGPT desktop**, attach `docs/specs/practice.md` from your cloned folder (or paste its contents). Ask:

> Help me understand this task and agree a short plan. Do not code yet. Draft a short GitHub issue title and body with the feature ID, spec link, scope, and three examples to check.

Read the reply. Does it keep the task to help text below Note, connected to that field for assistive technology, with saving unchanged? Ask about anything unclear. Reject extra features. **You decide when the plan is ready.**

In **your GitHub repository → Issues → New issue → Small feature or change**, use the AI's title and paste its body into **Plan and checks**. Review it against the spec before submitting. Copy the issue URL. GitHub's issue number is separate from the feature ID PRACTICE-001.

## 2. Build with Codex

In your second terminal:

```sh
git status --short --branch
git switch -c practice-001-note-help
```

Start from a clean copy. If you already made this branch, use `git switch practice-001-note-help` instead.

In **Codex**, working locally in this same folder, paste your agreed plan, issue URL, and the app command/address that worked. Then ask:

> Read AGENTS.md and docs/specs/practice.md, then inspect the existing HTML. Flag any conflict with our plan before editing. Implement only PRACTICE-001. Update the spec's tracking row with my issue and a GitHub source link on practice-001-note-help. Run npm test and npm run docs:build; record only checks actually performed. Show the changed files. Do not commit or push.

Expect only `app/public/index.html` and `docs/specs/practice.md` to change. Read edit/command approval requests before accepting. A separate chat does not automatically have your plan: carry it into Codex yourself.

## 3. Try it and give feedback

In the app's running terminal, press **Ctrl+C** and rerun your start command. Refresh the browser at the printed address. This app needs a restart to load changed HTML.

Try three things:

- The exact sentence appears below Note before typing.
- Save a link you want to keep with a note. The saved entry appears.
- Submit that URL again with a different note. Your original note should remain.

Tests check existing saving behavior; **they do not prove the new sentence appears correctly**.

In the second terminal, inspect the before/after changes:

```sh
git diff -- app/public/index.html docs/specs/practice.md
```

Press `q` if Git opens a scrolling view. Open the files in VS Code; ask Codex to explain anything unclear, including how the help is connected to Note.

Tell Codex what you actually saw. If the result is wrong, describe the mismatch and ask for a focused fix; restart and recheck. If it is right, ask it to record your browser results in the spec's short tracking row. Keep real issue/source links and actual results; do not claim checks you skipped.

## 4. Review and keep it

In the second terminal:

```sh
git status --short
git add app/public/index.html docs/specs/practice.md
git diff --cached
```

Only those two files should be staged. If other changes appear, ask why before continuing. Read the diff, then:

```sh
git commit -m "PRACTICE-001: explain the note limit"
git push -u origin practice-001-note-help
```

In **your GitHub repository → Pull requests → New pull request**, select base `main` and compare `practice-001-note-help`. Describe what changed and what you checked. Add `Closes #N` using your issue number. You can ask Codex for a short draft; review it before posting.

Inspect **Files changed**, wait for the build to pass, then merge when it matches the spec. A skipped deployment is expected; your copy does not need GitHub Pages. Missing checks? Use [Setup help](./setup#common-fixes). Keep the branch so your spec's source link continues to work.

**Done:** your PR is merged, its issue is closed, and the spec links to your code and actual checks. Stop the app with Ctrl+C. What did you ask AI to clarify or correct? That is the conversation to bring to class.
