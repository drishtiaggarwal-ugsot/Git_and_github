# 🐙 GitHub — Complete Beginner's Notes

> **GitHub is a web-based platform built on top of Git.** It hosts your repositories online and adds tools for collaboration: pull requests, issues, project boards, code review, automation, and a huge open-source community.

---

## 📑 Table of Contents

1. [What Is GitHub?](#1-what-is-github)
2. [Git vs. GitHub](#2-git-vs-github)
3. [A Tiny Bit of History](#3-a-tiny-bit-of-history)
4. [GitHub Essentials](#4-github-essentials)
5. [The GitHub Workflow](#5-the-github-workflow)
6. [Forking vs. Cloning vs. Branching](#6-forking-vs-cloning-vs-branching)
7. [Pull Requests in Depth](#7-pull-requests-in-depth)
8. [Issues & Projects](#8-issues--projects)
9. [Authentication (HTTPS, SSH, Tokens)](#9-authentication-https-ssh-tokens)
10. [Other Useful Features](#10-other-useful-features)
11. [Writing Good Markdown](#11-writing-good-markdown)
12. [Common Misconceptions](#12-common-misconceptions)
13. [Common Mistakes & Fixes](#13-common-mistakes--fixes)
14. [Best Practices](#14-best-practices)
15. [Student Contributions](#15-student-contributions)

---

## 1. What Is GitHub?

GitHub is a website (and company) where you can:

- ☁️ **Host** Git repositories in the cloud
- 🤝 **Collaborate** with others through forks and pull requests
- 🐛 **Track** bugs, tasks, and ideas with Issues
- 📋 **Manage** work with Project boards
- 🌍 **Showcase** your work. Your profile works like a developer portfolio
- 🌱 **Join** the open-source community and contribute to real projects

---

## 2. Git vs. GitHub

| | **Git** | **GitHub** |
|---|---------|-----------|
| What it is | A version-control **tool** | A **website / service** that hosts Git repos |
| Where it runs | On your computer | In the cloud (github.com) |
| Needs internet? | No | Yes |
| Made by | Linus Torvalds (2005) | GitHub, Inc. (2008), owned by Microsoft since 2018 |
| Main job | Track changes & history | Share, collaborate, review, manage |
| Alternatives | Mercurial, SVN | GitLab, Bitbucket, Gitea, Codeberg |

> 🧠 **Analogy:** Git is like a camera that takes snapshots of your work. GitHub is like an online photo album where you share them and others can comment.

---

## 3. A Tiny Bit of History

- Launched in **2008**.
- Quickly became the home of open-source software.
- Acquired by **Microsoft** in **2018**.
- Now hosts hundreds of millions of repositories and is the largest code host in the world.

---

## 4. GitHub Essentials

| Feature | What it is |
|---------|------------|
| **Repository (Repo)** | A project folder where your code/files and their full history are stored. |
| **Fork** | A copy of someone else's repo under **your** account. You can change it freely. |
| **Pull Request (PR)** | A request to merge your changes into another branch or repository, with discussion and review. |
| **Issues** | Track bugs, tasks, questions, or feature requests. |
| **Projects** | Organize tasks using boards, lists, and cards (like a Kanban board). |
| **Stars ⭐** | Bookmark/like a repo. Also signals popularity. |
| **Watch 👀** | Get notifications about a repo's activity. |
| **README.md** | The front page of a repo. Shown automatically on the repo's homepage. |
| **Contributors** | People whose commits are part of the repo. |
| **Discussions** | A forum-style space for Q&A and ideas, separate from Issues. |

---

## 5. The GitHub Workflow

```
 1. Clone / Fork ──▶ 2. Make Changes ──▶ 3. Add ──▶ 4. Commit
                                                        │
                                                        ▼
 8. Merge & Improve ◀── 7. Pull Updates ◀── 6. Review ◀── 5. Push to GitHub
```

In commands:

```bash
git clone <url>                    # 1. Get the repo
git switch -c my-change            #    Make a branch
# ...edit files...                 # 2. Make changes
git add .                          # 3. Stage
git commit -m "Explain change"     # 4. Commit
git push -u origin my-change       # 5. Push
# 6. Open a Pull Request on GitHub → teammates review & discuss
# 7. After merge: git switch main && git pull
# 8. Repeat!
```

---

## 6. Forking vs. Cloning vs. Branching

These three confuse almost everyone at first.

| | **Fork** | **Clone** | **Branch** |
|---|----------|-----------|------------|
| Where does it happen? | On GitHub (server side) | Your computer | Inside a repo |
| What does it create? | A new repo under your account | A local copy of a repo | A new line of work in the same repo |
| When to use it | You **don't** have write access to the original repo | You want to work on a repo locally | You want to work on a change without touching `main` |
| Is it Git or GitHub? | GitHub feature | Git command | Git feature |

**Typical open-source flow (like this repo!):**

```
Original repo ──Fork──▶ Your fork (GitHub) ──Clone──▶ Your computer ──Branch──▶ Make changes
                                                                                    │
Original repo ◀──────── Pull Request ◀──── Your fork ◀────────── Push ◀────────────┘
```

---

## 7. Pull Requests in Depth

A **Pull Request** says: *"Here are my changes. Please review them and pull them into your project."*

### What a PR contains

- The **source** branch (your changes) and the **target** branch (where they'll go)
- A title and description
- The list of commits and a line-by-line **diff**
- A conversation thread and review comments
- Status checks (automated tests, if set up)

### Lifecycle

1. **Open** the PR.
2. **Review:** maintainers comment, approve, or request changes.
3. **Update:** push more commits to the same branch. The PR updates automatically.
4. **Merge** (or close if not accepted).

### Merge options on GitHub

| Option | Result |
|--------|--------|
| **Create a merge commit** | Keeps all commits + adds a merge commit |
| **Squash and merge** | Combines all PR commits into one clean commit |
| **Rebase and merge** | Replays commits onto the target branch, no merge commit |

### Writing a good PR

- Clear title: `"Add section on merge conflicts to git.md"`
- Description: **what** you changed and **why**
- Link related issues: `Closes #12` (auto-closes the issue when merged)
- Keep it small and focused

---

## 8. Issues & Projects

### Issues

Use issues to report bugs, suggest ideas, or ask questions. Good issues include:

- A clear title
- Steps to reproduce (for bugs)
- What you expected vs. what happened
- Screenshots if helpful

Useful features: **labels** (`bug`, `good first issue`, `documentation`), **assignees**, **milestones**, and linking from commits or PRs with `#issue-number`.

### Projects

GitHub Projects are boards/tables for planning work. Columns like **To Do → In Progress → Done**, with issues and PRs as cards.

---

## 9. Authentication (HTTPS, SSH, Tokens)

⚠️ GitHub **no longer accepts your account password** for `git push` over HTTPS. Use one of these:

### Option A: HTTPS + Personal Access Token (PAT)

1. GitHub → **Settings → Developer settings → Personal access tokens**
2. Generate a token with repo access.
3. When Git asks for a password, paste the **token**.
4. Credential managers (installed with Git for Windows / macOS Keychain) will remember it.

### Option B: SSH keys

```bash
ssh-keygen -t ed25519 -C "you@example.com"   # create a key (press Enter for defaults)
cat ~/.ssh/id_ed25519.pub                    # copy the output
```

Then paste it into GitHub → **Settings → SSH and GPG keys → New SSH key**. Test:

```bash
ssh -T git@github.com
```

Clone using the SSH URL (`git@github.com:user/repo.git`).

### Option C: GitHub CLI or GitHub Desktop

`gh auth login` (GitHub CLI) or the **GitHub Desktop** app handle authentication for you.

---

## 10. Other Useful Features

| Feature | What it does |
|---------|--------------|
| **GitHub Pages** | Free static website hosting straight from a repo |
| **GitHub Actions** | Automation/CI: run tests, checks, or deployments on every push or PR |
| **Releases & Tags** | Package and publish versions of your project |
| **Gists** | Share small snippets or single files |
| **Profile README** | Make a repo named exactly like your username to customize your profile page |
| **Codespaces** | A full development environment in the browser |
| **Branch protection** | Prevent direct pushes to `main`, require reviews |
| **`.github/` folder** | Holds templates for issues and PRs, workflows, etc. |
| **Web editor** | Press `.` on any repo page to open it in a browser-based VS Code |
| **Licenses** | Add a `LICENSE` file so others know how they can use your work |

---

## 11. Writing Good Markdown

Since this repo is all `.md` files, here's a quick reference:

````markdown
# Heading 1
## Heading 2
### Heading 3

**bold**, *italic*, `inline code`

- bullet item
1. numbered item

[link text](https://example.com)

> a quote / callout

| Column | Column |
|--------|--------|
| cell   | cell   |

```bash
git status
```

- [ ] task not done
- [x] task done
````

---

## 12. Common Misconceptions

### ❌ "GitHub is Git."
✅ GitHub is a **service** that uses Git. Git works fine without GitHub, and GitHub isn't the only host (GitLab, Bitbucket, etc.).

### ❌ "I need GitHub to use version control."
✅ Git alone gives you full version control on your machine. GitHub adds sharing and collaboration.

### ❌ "Forking and cloning are the same."
✅ A **fork** is a copy on GitHub under your account. A **clone** is a copy on your computer. You usually fork *then* clone.

### ❌ "My fork updates automatically when the original changes."
✅ It does **not**. You must sync it yourself (the **Sync fork** button, or `git pull upstream main`).

### ❌ "Pushing to my fork changes the original repo."
✅ Your fork is separate. Changes only reach the original through a **Pull Request** that someone accepts.

### ❌ "A Pull Request means I'm pulling something."
✅ The name is from the maintainer's point of view: you're asking *them* to **pull** your changes. GitLab calls the same thing a "Merge Request", which is arguably clearer.

### ❌ "Private repos are totally secret, so it's okay to commit passwords there."
✅ Never commit secrets anywhere. Repos get made public, shared, forked, or leaked. Use `.env` files + `.gitignore`.

### ❌ "Deleting a file on GitHub removes it completely."
✅ It's still in the commit history. Leaked secrets must be **revoked/rotated**, not just deleted.

### ❌ "If it's public on GitHub, I can use it however I want."
✅ Public ≠ free to use. Check the repo's **LICENSE**. No license generally means all rights reserved.

### ❌ "GitHub is only for professional programmers."
✅ Students, writers, designers, researchers, and hobbyists all use it. You're using it right now for notes!

### ❌ "Stars and green contribution squares are what matter."
✅ They're nice, but meaningful projects, clear READMEs, and good collaboration habits matter much more.

### ❌ "I need to be an expert before I can contribute to open source."
✅ Many projects welcome beginners. Look for issues labeled **`good first issue`**. Fixing docs and typos counts!

---

## 13. Common Mistakes & Fixes

| Mistake | Fix |
|---------|-----|
| Push asks for password and rejects it | Use a Personal Access Token or SSH, not your account password |
| Opened a PR against the wrong branch | Click **Edit** next to the PR title and change the base branch |
| PR has merge conflicts | Pull the target branch into yours locally, resolve conflicts, push again |
| Pushed directly to `main` of your fork | Not a disaster. Next time branch first. Your PR can still come from `main`, it's just messier |
| Fork is far behind the original | **Sync fork** on GitHub, then `git pull` locally |
| Cloned the original instead of your fork, push fails | `git remote set-url origin <your-fork-url>` |
| Accidentally made a repo public | **Settings → Danger Zone → Change visibility** (and rotate any secrets) |

---

## 14. Best Practices

- 📝 **Every repo gets a README** explaining what it is and how to use it.
- 📜 **Add a LICENSE** if you want others to use your work.
- 🌿 **Use branches + PRs**, even on solo projects. It builds the habit.
- 🔍 **Review PRs kindly and specifically.** Suggest, don't just criticize.
- 🔗 **Link issues and PRs** (`Closes #5`) to keep work traceable.
- 🛡️ **Enable 2FA** on your account.
- 🙈 **Use `.gitignore`** and never commit secrets.
- 🔄 **Keep your fork in sync** before starting new work.
- 🏷️ **Use labels** to organize issues.
- ⭐ **Star useful repos** so you can find them later.

---

## 15. Student Contributions

> Add your own notes below! Keep them under a heading with your topic. Example:
>
> ### How I set up SSH on Windows (by @your-username)
> Your explanation here...

<!-- Add new sections below this line -->

### How I set up SSH on Windows (by @DevdattaRane)

To set up SSH on Windows, you must first install the OpenSSH components, which are available as optional features in Windows 10 and Windows 11.

Installation and Configuration Steps

1.Install OpenSSH: Open PowerShell as Administrator and run the following commands to install both the client and server:

Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

2.Start the Service: Enable the SSH server service and set it to start automatically:

Start-Service sshd
Set-Service -Name sshd -StartupType Automatic

3.Configure Firewall: Ensure the firewall allows inbound SSH traffic on port 22:

New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH SSH Server' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22

