# Solution: Creating and Merging a Feature Branch via Pull Request

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
