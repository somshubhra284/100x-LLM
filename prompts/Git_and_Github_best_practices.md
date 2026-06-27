# Git and GitHub Workflow — Instructions for Claude Code

These are the Git and GitHub rules (based on BigBinary's conventions) you MUST follow for every task in this repository. Follow the workflow in order. Do not skip steps. When a step requires a manual action in the GitHub UI that you cannot perform, stop and tell me explicitly.

---

## Workflow (follow in this order)

### 1. Create a GitHub issue for the task
- Every task MUST have a corresponding GitHub issue. If one does not exist, create it before writing any code.
- Title the issue in the **future tense**, describing what will be done.
- Command:
  ```bash
  gh issue create --title "Add Playwright tests to verify logging in to the application" --body "<short description of the task>"
  ```
- Note the issue number returned (e.g. `#2`) — you will use it for the branch name and PR.

### 2. Create a branch from up-to-date main
- Branch name format: `<issue_number>-a-short-hyphenized-description`, in the **future tense**.
- Example: `2-add-tests-to-verify-login`
- Commands:
  ```bash
  git checkout main
  git pull
  git checkout -b 2-add-tests-to-verify-login
  ```

### 3. Make atomic commits as you work
- Break the task into small logical parts. Commit after completing each part.
- NEVER bundle all changes for an issue into a single commit.
- Commit messages MUST be:
  - In the **past tense** (they describe completed work).
  - Specific and meaningful.
- Good: `Added beforeEach block for login tests`, `Fixed redundant awaits in the code`
- Bad: `Completed first part`, `Fixed review suggestion`, `WIP`
  ```bash
  git add <specific-files>
  git commit -m "Added beforeEach block for login tests"
  ```

### 4. Push frequently and open a draft PR early
- After the **first** commit, push and open a **draft** PR immediately. Keep pushing commits to it as you progress.
- The first line of the PR description MUST be `Closes #<issue-number>`.
- The PR title MUST be in the **past tense** and summarize the whole feature (e.g. `Added tests for login`).
- Commands:
  ```bash
  git push -u origin 2-add-tests-to-verify-login
  gh pr create --draft --title "Added tests for login" --body "Closes #2"
  ```
- Keep pushing as you go:
  ```bash
  git push
  ```
- Note: If a draft PR cannot be created (e.g. personal repo restrictions), create a regular PR with `gh pr create` (omit `--draft`) and tell me.

### 5. Mark ready and assign the reviewer ONLY when complete
- Do NOT assign a reviewer until the work is fully complete and functional. Assigning early spams the reviewer.
- When ready, mark the PR ready for review and **assign** the reviewer (adding them as a reviewer alone does not notify them of updates — they must be assigned).
- Commands:
  ```bash
  gh pr ready
  gh pr edit --add-assignee <reviewer-username> --add-reviewer <reviewer-username>
  ```
- If you do not know the reviewer's username, ask me before assigning.

### 6. Respond to review comments
- When changes are requested, the PR is assigned back to you.
- Address review comments BEFORE starting any new feature.
- After pushing the fixes:
  1. Re-assign the PR back to the reviewer.
  2. Post a comment stating the review comments have been fixed.
  ```bash
  git push
  gh pr edit --add-assignee <reviewer-username>
  gh pr comment --body "Fixed the review comments."
  ```

### 7. Merge only after approval
- A PR may be merged ONLY after the reviewer has fully approved it. Never merge an unapproved PR.

---

## Hard rules checklist (must always hold true)

- [ ] Every task has a GitHub issue, titled in the **future tense**.
- [ ] Branch name is `<issue_number>-short-hyphenized-description`, in the **future tense**.
- [ ] Commits are **atomic** — one logical change each, never one big commit.
- [ ] Commit messages are in the **past tense**, specific, and meaningful.
- [ ] PR description's first line is `Closes #<issue-number>`.
- [ ] PR title is in the **past tense** and summarizes the whole feature.
- [ ] A draft PR is opened after the first commit; commits are pushed frequently.
- [ ] Reviewer is assigned ONLY when the PR is fully ready.
- [ ] Reviewer is **assigned** (not just added as reviewer) so they get notified.
- [ ] Review comments are addressed before new features; PR re-assigned to reviewer with a comment.
- [ ] PR is merged ONLY after full approval.

---

## Tense quick-reference

| Item            | Tense   | Example                                            |
|-----------------|---------|----------------------------------------------------|
| Issue title     | Future  | `Add Playwright tests to verify logging in`        |
| Branch name     | Future  | `2-add-tests-to-verify-login`                      |
| Commit message  | Past    | `Added tests to verify logging into the application` |
| PR title        | Past    | `Added tests for login`                            |
