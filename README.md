# CSE 2023

Index repository for **Computer Science and Engineering** students of **Batch 2023–2027**.

Students add the projects they build during the programme as **Git submodules**, grouped by the academic year in which the project was made (`1st Year`, `2nd Year`, `3rd Year`, `4th Year`). This repo does not hold project source directly; each project lives in its own GitHub repository and is linked here so the batch has a single, year-wise catalogue.

## Repository layout

Projects are grouped by academic year. Add a submodule under the matching year folder and list it in that year’s `README.md`.

```text
CSE_2023/
├── README.md
├── 2nd Year/
│   ├── README.md             # index of 2nd-year projects
│   └── project-name_USN/     # submodule
├── 3rd Year/
│   └── README.md             # index of 3rd-year projects
└── 4th Year/
    └── README.md             # index of 4th-year projects
```

Each project folder is named **`project-name_USN`** (example: `flip-a-find_4VP23CS004`). For a group project, use **one** USN in the folder name (the submitter, or the first USN listed). List **every** author and USN in that year’s index table; do not concatenate multiple USNs in the folder name.

---

## How to add your project

Do this from your own fork. Do not push directly to the upstream `main` branch. For a group project, **one** member forks, adds the submodule, and opens the PR. The index still names the full team.

### 1. Fork

1. Open the upstream repository on GitHub.
2. Click **Fork**.
3. Keep the fork under your GitHub account.

### 2. Clone your fork

```bash
git clone https://github.com/<your-username>/CSE_2023.git
cd CSE_2023
```

If you already cloned without a fork, add the upstream remote and work on a branch of your fork instead.

### 3. Create a branch

Use a short, unique branch name:

```bash
git checkout -b add/<project-name>_<USN>
```

Example: `add/flip-a-find_4VP23CS004` (for a group, still use a single USN in the branch name).

### 4. Add the project as a submodule

Your project must already exist as a **public** GitHub repository (or one the maintainers can clone).

Pick the year folder that matches when you built the project, then add the submodule with the required folder name:

```bash
git submodule add <your-project-repo-url> "<Nth Year>/<project-name>_<USN>"
```

Examples:

```bash
git submodule add https://github.com/Adithya-1489181/flip-a-find.git "2nd Year/flip-a-find_4VP23CS004"
```

Rules:

- Folder name is **`project-name_USN`** only — no extra spaces, no extra suffixes.
- Use a lowercase, hyphenated project name when possible (`tic-tac-toe_4VP23CS039`).
- Use **one** USN in the folder name, even for group projects. Do not concatenate multiple USNs.
- That USN must be a real member of the team (prefer the person submitting the PR).
- Add the submodule **inside** the correct year folder. Do not copy project files into this repo.

### 5. Index the project in that year’s `README.md`

Open `Nth Year/README.md` and add a row for your project. Keep the table sorted (by USN, then project name) unless the year file already uses another consistent order.

Use this format. For a group project, put all authors and USNs in the same cells, separated with `<br>` tags. The folder link and submodule path still contain only one USN.

**CMD / Markdown view:**

```markdown
| Project | USNs | Authors | Repository |
| --- | --- | --- | --- |
| [flip-a-find](./flip-a-find_4VP23CS004) | 4VP23CS004 | Your Name | [github.com/you/flip-a-find](https://github.com/Adithya-1489181/flip-a-find) |
| [example-project](./example-project_4VP23CS0XX) | 4VP23CS0XX<br>4VP23CS0XY | First Author<br>Second Author | [github.com/you/example-project](https://github.com/you/example-project) |
```

**Table view:**

| Project | USNs | Authors | Repository |
| --- | --- | --- | --- |
| [flip-a-find](./flip-a-find_4VP23CS004) | 4VP23CS004 | Your Name | [github.com/you/flip-a-find](https://github.com/Adithya-1489181/flip-a-find) |
| [example-project](./example-project_4VP23CS0XX) | 4VP23CS0XX<br>4VP23CS0XY | First Author<br>Second Author | [github.com/you/example-project](https://github.com/you/example-project) |

Do **not** skip this step. A submodule without an index entry will be requested as a change in review.

### 6. Commit and push to your fork

```bash
git status
git add .gitmodules "<Nth Year>/<project-name>_<USN>" "<Nth Year>/README.md"
git commit -m "Add <project-name> (<USN>) to <Nth Year>"
git push -u origin add/<project-name>_<USN>
```

Example commit message: `Add flip-a-find (4VP23CS004) to 2nd Year`

Commit only:

- `.gitmodules`
- the new submodule gitlink
- the year `README.md` index update

Do not commit unrelated files, local IDE settings, or copies of your project source.

### 7. Open a pull request

1. Open your fork on GitHub.
2. Create a pull request from your branch into the **upstream** `main` branch.
3. Wait for review. Address comments on the same branch; do not open a second PR for the same project unless asked.

---

## Pull request hygiene

Keep one PR focused on **one project** (or one clearly related set of index fixes).

**Title**

```text
Add <project-name> (<USN>) — <Nth Year>
```

**Description** should include:

- Project name and a one-line summary of what it is
- Every author’s name and USN (for a group project)
- Year folder used and why (the year you built it)
- Link to the standalone project repository
- Confirmation that the folder is named `project-name_USN`
- Confirmation that `Nth Year/README.md` was updated

**Before you submit, check:**

- [ ] You forked first and the PR targets upstream `main`
- [ ] The project is a **submodule**, not pasted source
- [ ] Folder name is `project-name_USN`
- [ ] Group projects use one USN only in the folder and list every author and USN in the year index
- [ ] The year folder is correct
- [ ] The year `README.md` lists the project with working links
- [ ] `.gitmodules` points at the correct clone URL
- [ ] The commit message matches the change
- [ ] No unrelated files are in the diff
- [ ] The project repo is cloneable (public, or access granted to maintainers)

**During review:**

- Reply to each review comment.
- Push fixes to the **same** branch; the PR updates automatically.
- Do not force-push unless a maintainer asks you to.
- Do not mix later projects into an open PR.

PRs that skip the year index, use the wrong folder name, or dump project files instead of a submodule will be asked to update before merge.

---

## Prompt for AI agents

After cloning this repository, you may give the following prompt to an AI coding agent. Replace the values in brackets before using it.

```text
You are adding one project to the CSE_2023 repository. Complete the entire task through pushing the changes to the remote branch.

Project repository link: [PROJECT_REPOSITORY_URL]
Year completed: [1st/2nd/3rd/4th Year]
Project name: [PROJECT_NAME]
Authors and USNs:
- [AUTHOR_NAME] — [USN]
- [AUTHOR_NAME] — [USN]

Follow these rules:
1. Inspect the repository instructions and current year README before editing.
2. Work from a fork, create a branch named add/<project-name>_<one-usn>, and never push directly to upstream main.
3. Add the project as a Git submodule under the year folder for the year completed.
4. Name the project folder <project-name>_<one-usn>. Use exactly one real team member USN, preferably the submitting member's USN. Never concatenate multiple USNs in the folder name.
5. Add one index-table row to <year folder>/README.md. Include every author and every USN in the row, using <br> between multiple values when needed, and link the project repository.
6. Inspect the diff and status. Commit only .gitmodules, the new submodule gitlink, and the relevant year README update.
7. Commit with: Add <project-name> (<one-usn>) to <year folder>
8. Push the branch to origin with git push -u origin add/<project-name>_<one-usn>.
9. Report the branch name, commit hash, changed files, and pull-request target after the push. Do not create a pull request unless explicitly asked.

Before making changes, ask for any missing value above. If the project URL cannot be cloned or the remote is not a fork, stop and report the exact blocker instead of guessing.
```

---