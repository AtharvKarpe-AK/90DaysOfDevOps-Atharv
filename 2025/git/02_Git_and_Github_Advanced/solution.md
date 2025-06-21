# Solution: Week 4: Git & GitHub Advanced Challenge

## 1. Working on a New Feature and Creating a PR

### Step-by-step Commands:
```bash
# Step 1: Clone the forked repository
git clone <your-forked-repo-url>
cd <repo-name>

# Step 2: Create a new feature branch
git checkout -b feature-branch

# Step 3: Make changes
echo "New Feature" >> feature.txt

# Step 4: Stage and commit your changes
git add .
git commit -m "Added a new feature"

# Step 5: Push the changes to your fork
git push origin feature-branch
```
Step 6: Open a Pull Request
Go to your forked repository on GitHub.

You'll see a prompt to "Compare & pull request" — click it.

Ensure the base branch is master or main and the compare branch is your feature-branch.

Add a title and description, then click Create pull request.

Request a review if needed.

Once approved, click Merge pull request and then Delete branch (optional cleanup).

2. Steps to Create a Pull Request (PR)
Push your feature branch to your forked repository.

Navigate to the repository on GitHub.

Click Compare & pull request.

Add a meaningful title and detailed description.

Assign reviewers or team members.

Submit the PR.

Monitor and respond to any review feedback.

Merge the PR once approved.

3. Best Practices for Writing PR Descriptions
Title: Clear and concise, summarizing the change (e.g., Add login feature to user dashboard)

What: Explain what the PR does.

Why: Briefly state the reasoning or problem it solves.

How: Mention any specific implementation details, dependencies, or risks.

Extras: Link to related issues, screenshots (if UI), or docs.


###Task 2: Undoing Changes – Reset & Revert

Differences Between git reset and git revert

| Feature            | `git reset`                       | `git revert`                                  |
| ------------------ | --------------------------------- | --------------------------------------------- |
| **Action**         | Moves the branch pointer backward | Creates a new commit that undoes previous one |
| **Data Loss Risk** | Yes (especially with `--hard`)    | No                                            |
| **History**        | Rewrites history                  | Preserves history                             |
| **Usage Scope**    | Local work                        | Safe for shared/public branches               |
| **Undo Commits?**  | Yes                               | Yes                                           |
| **Undo Changes?**  | Yes (with `--mixed` or `--hard`)  | No (just reverses commit logic)               |


When to Use Each Method
✅ Use git reset when:
You’re working locally and want to clean up your commit history.

You want to remove one or more commits before pushing.

You accidentally committed files and want to undo before sharing.

You’re okay with possibly losing uncommitted changes (especially with --hard).

✅ Use git revert when:
You already pushed the commit to a shared/public branch.

You want to undo a commit without altering history.

You're working in a team environment and need a safe way to fix mistakes.

You want to preserve an audit trail of every action.



###Task 3: Stashing - Save Work Without Committing

When to Use `git stash`

`git stash` is used when you need to **temporarily set aside** your local changes (both staged and unstaged) so you can:

- Switch to a different branch to work on something urgent
- Pull the latest changes from a remote branch without committing partial work
- Perform tests or fixes without losing your ongoing work
- Experiment with something and return to your previous state later

It helps you keep your working directory clean **without committing incomplete or experimental changes**.

## Commands:

```bash
# Save uncommitted changes
git stash

# List all stashed changes
git stash list

# Reapply the most recent stash (and remove it from stash list)
git stash pop

# Reapply the most recent stash (but keep it in the stash list)
git stash apply

# Drop a specific stash entry
git stash drop stash@{0}

# Clear all stash entries
git stash clear

```

Difference Between git stash pop and git stash apply

| Command           | Behavior                                                                                |
| ----------------- | --------------------------------------------------------------------------------------- |
| `git stash apply` | Reapplies the changes from the latest (or specified) stash but **keeps it in the list** |
| `git stash pop`   | Reapplies the changes **and removes** the stash entry from the stash list               |




###Task 5: Rebasing - Keeping a Clean Commit History

Using Cherry-Picking for Bug Fixes
What is Cherry-Picking?
Cherry-picking in Git is the act of selecting specific commits from one branch and applying them to another. This is useful when you want to apply a fix or feature from a development or feature branch into a stable branch (like main or release) without merging the whole branch.

📌 When to Use It for Bug Fixes
Cherry-picking is often used to:

Backport a bug fix from main to an older release branch

Apply a fix from a feature branch to main before the whole feature is ready

Isolate important hotfixes without pulling in unrelated work

Example:
Suppose a bug was fixed in a feature branch with commit fab5c2b. Instead of merging the entire branch, you can cherry-pick just the fix:


⚠️ Risks of Cherry-Picking
While cherry-picking can be convenient, it comes with several risks:

1. Duplicate Commits / Merge Conflicts Later
Cherry-picked commits are copied with a new SHA, so Git does not recognize them as the same. When the original branch is merged later, you may get:

Merge conflicts

Duplicated changes

2. Loss of Context
Cherry-picking isolates a commit from its original context. This can:

Break dependencies between commits

Lead to confusing histories

Introduce bugs if the cherry-picked commit relies on other unseen changes

3. History Complexity
Frequent cherry-picking can clutter your Git history, making it hard to understand where fixes came from and how they relate to other work.

4. Maintenance Overhead
Teams must track what was cherry-picked where. Without proper tracking (e.g., commit messages or tags), it’s easy to lose track of what's been applied.

✅ Best Practices
Always test cherry-picked commits in their new context.

Document cherry-picked commits in messages (e.g., cherry-picked from <commit-sha>).

Avoid cherry-picking large, dependent commits.

Consider alternatives like git merge -s ours or patch-based workflows if you need more control.


