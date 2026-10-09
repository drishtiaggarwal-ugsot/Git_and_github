# 📘 Git & GitHub Notes — A Learn-by-Doing Repo

Welcome! This repository is a **shared notebook about Git and GitHub**, and also the place where you'll *practice* using them.

The idea is simple: you learn Git by reading the notes, and you learn GitHub by **forking this repo, adding your own notes, and sending a Pull Request**. By the time your first PR is merged, you've already used almost everything described in these files.

---

## 📂 What's Inside

```
.
├── README.md     ← You are here: what this repo is and how to set it up
├── git.md        ← Everything about Git: concepts, commands, workflow, misconceptions
└── github.md     ← Everything about GitHub: repos, forks, PRs, issues, misconceptions
```

This repo intentionally contains **only text / Markdown files**. No code, no build steps, nothing to install except Git itself.

---

## 🧭 Who Is This For?

- Students who have never used Git before
- People who've used Git a little but get confused by branches, staging, or merge conflicts
- Anyone who wants a clean, beginner-friendly reference they can keep and extend

---

## 🛠️ Step 1 — Install & Configure Git

### Install

| OS | How |
|----|-----|
| **Windows** | Download from [git-scm.com](https://git-scm.com/downloads) and run the installer (defaults are fine). This also installs **Git Bash**. |
| **macOS** | Run `git --version` in Terminal. If it's missing, macOS will offer to install it. Or use `brew install git`. |
| **Linux** | `sudo apt install git` (Debian/Ubuntu) or `sudo dnf install git` (Fedora) |

Check that it worked:

```bash
git --version
```

### Configure (one-time setup)

Tell Git who you are. This name and email get attached to every commit you make.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

> 💡 Use the **same email** you use on GitHub so your commits are linked to your profile.

Verify:

```bash
git config --list
```

---

## 🌐 Step 2 — Create a GitHub Account

1. Go to [github.com](https://github.com) and sign up.
2. Verify your email.
3. (Recommended) Turn on two-factor authentication in **Settings → Password and authentication**.

---

## 🍴 Step 3 — Fork This Repository

A **fork** is your own personal copy of this repo, under your GitHub account.

1. Click the **Fork** button at the top-right of this page.
2. Keep the default settings and click **Create fork**.
3. You'll now be on `github.com/<your-username>/<this-repo-name>`.

---

## 💻 Step 4 — Clone Your Fork to Your Computer

On **your fork's** page, click the green **Code** button and copy the HTTPS URL. Then:

```bash
git clone https://github.com/<your-username>/<this-repo-name>.git
cd <this-repo-name>
```

Connect your copy to the original repo so you can pull future updates:

```bash
git remote add upstream https://github.com/<original-owner>/<this-repo-name>.git
git remote -v
```

You should see two remotes:
- `origin` → your fork
- `upstream` → the original repo

---

## 🌿 Step 5 — Create a Branch

Never work directly on `main`. Make a branch for your changes:

```bash
git switch -c add-my-notes
```

(Older equivalent: `git checkout -b add-my-notes`)

---

## ✍️ Step 6 — Add Your Notes

Open `git.md` or `github.md` in any text editor (VS Code, Notepad, etc.) and add something useful:

- A concept explained in your own words
- A command that confused you and how you figured it out
- A misconception you had
- A helpful analogy or diagram (ASCII is fine!)
- A mistake you made and how you fixed it

Then save the file.

---

## ✅ Step 7 — Stage, Commit, Push

```bash
git status                       # see what changed
git add git.md                   # stage the file(s) you edited
git commit -m "Add notes on git stash to git.md"
git push -u origin add-my-notes  # upload your branch to YOUR fork
```

---

## 🔁 Step 8 — Open a Pull Request

1. Go to your fork on GitHub. You'll see a banner: **"Compare & pull request"**. Click it.
2. Make sure the PR goes **from** `your-username/add-my-notes` **into** `original-owner/main`.
3. Write a short title and description of what you added.
4. Click **Create pull request**.

A maintainer will review it, maybe leave comments, and merge it. 🎉 That's your first open-source contribution.

---

## 🔄 Keeping Your Fork Up to Date

Other students' notes will get merged over time. To get them into your fork:

```bash
git switch main
git pull upstream main
git push origin main
```

Or click **Sync fork** on your fork's GitHub page, then run `git pull` locally.

---

## 📏 Contribution Guidelines

To keep the notes clean and useful for everyone:

1. **Add to the right file.** Git concepts → `git.md`. GitHub features → `github.md`.
2. **Put it under the right heading.** If no heading fits, create a new one.
3. **Don't delete other people's notes.** Improve or clarify them instead.
4. **Keep it beginner-friendly.** Explain jargon the first time you use it.
5. **Test your commands.** If you add a command, make sure it actually works.
6. **One topic per PR.** Small PRs are easier to review and less likely to conflict.
7. **Write a meaningful commit message.** `"Add explanation of git rebase"` ✅ — `"update"` ❌
8. **Use Markdown properly.** Commands go in code blocks using triple backticks.

---

## 🆘 Stuck?

- Run `git status`. It almost always tells you what's going on and what to do next.
- Open an **Issue** in this repo describing your problem.
- Check the "Common Mistakes" sections in `git.md` and `github.md`.

---

## 🧠 Remember

> **Code. Commit. Contribute. Repeat.**
>
> The more you use Git & GitHub, the more confident you'll become.

Happy learning! 🚀