# Team Playbook: GitHub, Jira, and Power BI Workflow

This playbook explains how we work together using GitHub, Jira, and Power BI.

The goal is to:
- keep the project organized,
- let each teammate keep a showcase copy on their own GitHub account,
- reduce merge conflicts,
- make work easy to review,
- and help both teammates follow the process.

---

## How we work

We use a **fork-and-PR workflow**.

That means:
- each teammate keeps their own fork of the repository on their GitHub account,
- day-to-day work happens on feature branches in that fork,
- Pull Requests (PRs) are used to review and merge changes back to the team repository,
- and Jira tracks the task status and links the work to the issue.

---

## What the main terms mean

- **Repository:** The project folder stored on GitHub.
- **Upstream repository:** The team repository where the official version lives, used to pull updates and merge finished work.
- **Fork:** Your personal copy of the repository on your own GitHub account.
- **Main branch:** The stable branch in the team repository. We do not edit it directly.
- **Feature branch:** A temporary branch for one task or one piece of work.
- **Commit:** A saved checkpoint of your work.
- **Push:** Sending your commits to GitHub.
- **Pull Request (PR):** A request to review and merge your changes.
- **Jira issue key:** The ticket identifier, like `SCRUM-16`, used to link work in GitHub back to Jira.
- **Handoff slot:** A temporary claim on the live Power BI file so only one person edits it at a time.

---

## First-time setup

### 1. Fork the repository

On GitHub, open the team repository and choose **Fork**.

Tip: the exact button position in the UI can change, but the action is still called **Fork**.

### 2. Clone your fork

```bash
git clone https://github.com/YOUR-USERNAME/agile-powerbi-scrum.git
# Downloads your personal fork to your computer.

cd agile-powerbi-scrum
# Moves you into the project folder.
```

### 3. Add the team repo as upstream

```bash
git remote add upstream https://github.com/andrew-chung-au/agile-powerbi-scrum.git
# Saves a link to the team repository.
```

### 4. Confirm your remotes

```bash
git remote -v
# Shows which repositories your local copy is connected to.
```

---

## Git workflow

Use this for documentation, scripts, notes, cleaned data, or other non-Power BI tasks.

### 1. Sync with the team repository

```bash
git fetch upstream
# Downloads the latest changes from the team repository.

git checkout main
# Switches to your local main branch.

git pull upstream main
# Updates your local main branch with the newest shared changes.
```

### 2. Create a feature branch

Use a descriptive branch name.

Examples:
- `SCRUM-15-data-cleaning`
- `SCRUM-22-docs-update`
- `SCRUM-16-dashboard-export`

```bash
git checkout -b SCRUM-15-data-cleaning
# Creates a new branch for your task.
```

Tip: include the Jira issue key in the branch name so Jira can link the work automatically.

### 3. Make your changes

Edit your files locally, then check what changed.

```bash
git status
# Shows which files changed.
```

### 4. Commit your work

```bash
git add .
# Stages your changes.

git commit -m "SCRUM-15 cleaned customer date fields"
# Saves the work and links it to the Jira issue.
```

Tip: keep the Jira key at the start of the commit message if your team uses Jira-GitHub linking.

### 5. Push to your fork

```bash
git push origin SCRUM-15-data-cleaning
# Sends your branch to your personal fork on GitHub.
```

### 6. Open a Pull Request

After you push your branch to your fork, open a Pull Request from your branch into the team repository.

Tip: include the Jira issue key in the PR title or description so Jira can link the work to the correct ticket.

Example PR title:
- `SCRUM-15 Clean customer date fields`

#### Simple steps on GitHub
1. Go to your fork on GitHub.
2. Find your recently pushed branch.
3. Open the Pull Request view.
4. Set the base repository to the team repo and the base branch to `main`.
5. Set the head repository to your fork and the compare branch to your feature branch.
6. Add a short title and description.
7. Create the Pull Request.

---

## Jira workflow

Jira is the task tracking layer. GitHub is the code collaboration layer.

Use the Jira issue key everywhere you can:
- branch name,
- commit message,
- PR title.

Example:
- Branch: `SCRUM-16-dashboard-export`
- Commit: `SCRUM-16 updated dashboard screenshots`
- PR title: `SCRUM-16 Update dashboard export assets`

Before you start a task:
- move the Jira issue to in progress,
- or assign it to yourself if your team does that.

When the PR is opened or merged:
- update the Jira issue,
- add a short comment if needed,
- and mark the task as ready for review or done based on your process.

Note: Jira and GitHub UI labels can change, so use the general actions rather than relying on a specific button name.

---

## Commit message style

Good commit messages are short and specific.

Good:
- `SCRUM-11 added sprint review notes`
- `SCRUM-15 cleaned raw sales CSV`
- `SCRUM-16 updated dashboard screenshots`
- `SCRUM-22 refined onboarding steps`

Avoid:
- `update`
- `changes`
- `stuff`
- `final`

---

## Power BI workflow

Only **one person** should edit the live Power BI file at a time.

That person holds the **handoff slot** until the work is:
- saved,
- documented,
- committed,
- pushed,
- and shared with the team.

### 1. Claim the slot

Before opening the file, post a message in the pinned Slack thread in the `agile-powerbi-scrum` channel to let the team know you are taking the slot.

Use a message like:

```text
[SLOT ACQUIRED]
Working on dashboard visuals and DAX updates for SCRUM-16.
```

If needed, also add the same update to the Jira issue so the task history stays clear.

### 2. Sync and branch

```bash
git fetch upstream
# Gets the newest shared changes.

git checkout main
# Switches to main.

git pull upstream main
# Updates main from the team repo.

git checkout -b SCRUM-16-powerbi-updates
# Creates your Power BI task branch.
```

### 3. Edit the Power BI file

Make your changes in Power BI Desktop.

Examples:
- visual updates,
- DAX changes,
- layout changes,
- KPI formatting,
- data model refinements.

Save the file when finished.

### 4. Export review assets

After editing, export at least one review file.

Examples:
- screenshot,
- PDF,
- image of the updated report page.

Save review assets in a folder in your branch, such as:

```text
visuals/dashboard-screenshots/
```

Then commit and push them through the usual fork-and-PR workflow.

This helps teammates review progress without opening Power BI Desktop.

### 5. Document the handoff

Write a short update in the Jira ticket, project note, or issue comment.

```text
Updated sales overview page, cleaned KPI labels, and revised filter layout.
Pending: stakeholder review on regional breakdown chart.
```

### 6. Commit and push

```bash
git add .
# Stages the Power BI file, screenshots, and notes.

git commit -m "SCRUM-16 updated Power BI dashboard layout"
# Saves the work with the Jira key.

git push origin SCRUM-16-powerbi-updates
# Sends the branch to your fork.
```

### 7. Open the Pull Request and release the slot

Open a Pull Request from your fork to the team repository.

Then update the Jira issue and post a short release message in the pinned Slack thread in the `agile-powerbi-scrum` channel.

```text
[SLOT RELEASED - PR OPENED]
```

or

```text
[SLOT RELEASED - PR #12]
```

If the Power BI slot is busy, do not wait idle.

Use that time for:
- documentation,
- sample data cleanup,
- sprint notes,
- screenshot organization,
- presentation prep,
- issue review,
- README improvements.

---

## If you get stuck

If Git gives you an error or something feels unclear:

1. Stop.
2. Do not force a push.
3. Take a screenshot of the error.
4. Share the error with the team.
5. Say what you were trying to do and which branch you were on.

Example:
> “I was trying to push `SCRUM-15-data-cleaning` and got an error. Can someone help?”

---

## Documentation expectations

Keep the repo easy to understand.

Update these when relevant:
- `README.md`
- `docs/team-workflow.md`
- `docs/sprint-notes/`
- `docs/decisions/`
- `visuals/`

Keep notes short, practical, and current.

---

## Quick workflow summary

### Standard task

```text
Fork -> clone -> add upstream -> sync main -> create branch -> complete task -> commit -> push to fork -> open PR
```

### Power BI task

```text
Claim slot -> sync main -> create branch -> edit Power BI file -> export visuals -> document handoff -> commit -> push to fork -> open PR -> release slot
```

---

## Final rule

When in doubt:
- do not edit the live Power BI file at the same time as someone else
- and always leave enough documentation for the next teammate to continue smoothly.