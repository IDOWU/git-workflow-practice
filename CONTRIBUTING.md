# Contributing

Use a separate branch for each task and propose changes through a pull request.

## Start a task

Check that your working tree is clean before switching branches. Commit or set
aside any existing work first. Update `main`, then create your task branch:

```bash
git status
git switch main
git pull --ff-only origin main
git switch -c docs/example-task
```

Choose a branch name that describes your task. If the pull cannot fast-forward,
inspect the branch history and resolve the divergence before continuing.

## Make and review changes

Keep changes focused on the task. Check that the dashboard still opens in a
browser if you change it, and verify any documentation instructions you update.
Review your changes and check for whitespace errors:

```bash
git status
git diff
git diff --check
```

New, untracked files do not appear in `git diff`; inspect their contents too.

## Stage and commit

Stage specific files rather than every file in the working directory. For
example, if your task changes the README:

```bash
git add readme.md
git diff --staged
git commit -m "docs: clarify dashboard setup"
```

Review the staged diff before committing. Use a message that describes the change.

## Push and open a pull request

```bash
git push -u origin docs/example-task
```

Pushing a feature or task branch uploads that branch to GitHub. It does not merge
the changes into `main`.

On GitHub, open a pull request with `main` as the **base** (destination) and your
task branch as the **compare** (source). Describe the changes and the checks you
actually performed.

Review the Files changed tab for unintended edits and resolve any conflicts.
Request a teammate's review when available and satisfy repository checks and
review requirements before merging the pull request.

## Update main and clean up

After the pull request is merged on GitHub, update your local `main`:

```bash
git switch main
git pull --ff-only origin main
```

Verify the merged changes are present, then delete the completed task branch:

```bash
git branch -d docs/example-task
git push origin --delete docs/example-task
git fetch --prune
```

Skip the remote deletion command if the branch was already deleted on GitHub.
If local deletion reports that the branch is not fully merged, inspect the
history and confirm the changes reached `main` before deciding how to proceed;
do not force deletion blindly. This can happen after a squash or rebase merge.
