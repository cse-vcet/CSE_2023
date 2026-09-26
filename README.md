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

Each project folder is named **`project-name_USN`** (example: `flip-a-find_4VP23CS004`).

---

## How to add your project

Do this from your own fork. Do not push directly to the upstream `main` branch.

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

Example: `add/flip-a-find_4VP23CS004`

### 4. Add the project as a submodule

Your project must already exist as a **public** GitHub repository (or one the maintainers can clone).

Pick the year folder that matches when you built the project, then add the submodule with the required folder name:

```bash
git submodule add <your-project-repo-url> "<Nth Year>/<project-name>_<USN>"
```

Examples:

```bash
git submodule add https://github.com/<your-username>/flip-a-find.git "2nd Year/flip-a-find_4VP23CS004"
```

Rules:

- Folder name is **`project-name_USN`** only — no extra spaces, no extra suffixes.
- Use a lowercase, hyphenated project name when possible (`tic-tac-toe_4VP23CS039`).
- USN must match your university seat number exactly.
- Add the submodule **inside** the correct year folder. Do not copy project files into this repo.

### 5. Index the project in that year’s `README.md`

Open `Nth Year/README.md` and add a row for your project. Keep the table sorted (by USN, then project name) unless the year file already uses another consistent order.

Use this format:

```markdown
| Project | USN | Author | Repository |
| --- | --- | --- | --- |
| [flip-a-find](./flip-a-find_4VP23CS004) | 4VP23CS004 | Your Name | [github.com/you/flip-a-find](https://github.com/you/flip-a-find) |
```

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
- Your name and USN
- Year folder used and why (the year you built it)
- Link to the standalone project repository
- Confirmation that the folder is named `project-name_USN`
- Confirmation that `Nth Year/README.md` was updated

**Before you submit, check:**

- [ ] You forked first and the PR targets upstream `main`
- [ ] The project is a **submodule**, not pasted source
- [ ] Folder name is `project-name_USN`
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

## Cloning this repository (with projects)

After clone, initialise submodules so project folders are populated:

```bash
git clone --recurse-submodules https://github.com/<org-or-owner>/CSE_2023.git
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```
