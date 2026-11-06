# 🧑‍💻 Git Commands — Full Walkthrough

Every command you'll need, explained step by step.

---

## 📖 Legend

| Symbol | Meaning |
|--------|---------|
| `$`    | Run this in your terminal (PowerShell / Git Bash) |
| `#`    | Comment — don't type this part |

---

## 1️⃣ First-Time Git Setup (one time only)

```bash
# Tell Git who you are (used in commit messages)
$ git config --global user.name "Shubh Verma"
$ git config --global user.email "YOUR_EMAIL@example.com"   # use the email linked to your GitHub account
```

> **What this does:** Sets your name and email globally so every repo you create uses these by default.

---

## 2️⃣ Initialize the Repository

```bash
# Navigate to your project folder
$ cd "c:\Users\shubh\OneDrive\Desktop\github profile"

# Initialize a new Git repository in this folder
$ git init
```

> **What this does:** Creates a hidden `.git/` folder that tracks all your changes. This folder is now a Git repo.

---

## 3️⃣ Check What Files Git Sees

```bash
$ git status
```

> **What this does:** Shows you which files are new (untracked), modified, or staged. Run this often — it's your best friend.

You should see:
```
Untracked files:
  README.md
  PROFILE_CHECKLIST.md
  assets/banner.svg
  .github/workflows/snake.yml
  COMMANDS.md
```

---

## 4️⃣ Stage Files (Add Them to the Next Commit)

```bash
# Stage everything at once
$ git add .
```

> **What this does:** `git add .` tells Git "I want to include ALL new/changed files in my next commit." The `.` means "everything in the current directory."

**Or stage files individually** (useful when you only want to commit some changes):
```bash
$ git add README.md
$ git add assets/banner.svg
$ git add .github/workflows/snake.yml
$ git add PROFILE_CHECKLIST.md
$ git add COMMANDS.md
```

---

## 5️⃣ Commit (Save a Snapshot)

```bash
$ git commit -m "✨ Add GitHub profile README with Catppuccin theme"
```

> **What this does:** Creates a permanent snapshot of all staged files. The `-m` flag lets you write a short message describing what changed. Think of commits as save points in a game.

---

## 6️⃣ Create the Repo on GitHub

Before pushing, you need a repo on GitHub to push to:

1. Go to [github.com/new](https://github.com/new)
2. **Repository name:** `User8085` (must match your GitHub username exactly!)
3. **Visibility:** Public
4. **Do NOT** check "Add a README file" (you already have one)
5. Click **Create repository**

> ⚠️ **Your current repo is named `GithubProfile`.** You MUST rename it to `User8085` for the profile README to show up. Go to **Settings → General → Repository name** → change to `User8085` → click **Rename**.

---

## 7️⃣ Connect Local Repo to GitHub (Set Remote)

```bash
# Add GitHub as the "origin" remote
$ git remote add origin https://github.com/User8085/GithubProfile.git
```

> **What this does:** Tells your local repo where to push/pull from. `origin` is just a nickname for the GitHub URL. You only do this once per repo.

**Verify it worked:**
```bash
$ git remote -v
```
You should see:
```
origin  https://github.com/User8085/GithubProfile.git (fetch)
origin  https://github.com/User8085/GithubProfile.git (push)
```

---

## 8️⃣ Rename Branch to `main` (if needed)

```bash
# Rename the default branch from 'master' to 'main'
$ git branch -M main
```

> **What this does:** GitHub's default branch is called `main`. Older Git versions create `master`. This command renames it.

---

## 9️⃣ Push to GitHub

```bash
# Push your code and set 'origin main' as the default upstream
$ git push -u origin main
```

> **What this does:**
> - Uploads your commits to GitHub
> - `-u` sets `origin main` as the default, so next time you can just run `git push`
> - You may be prompted to log in (browser auth or token)

---

## 🔟 Trigger the Snake Workflow

After pushing, the snake action won't have run yet. Trigger it manually:

1. Go to your repo on GitHub: `https://github.com/User8085/GithubProfile`
2. Click the **Actions** tab
3. Click **Generate Snake** in the left sidebar
4. Click **Run workflow** → **Run workflow**
5. Wait ~30 seconds, then check your profile — the snake should appear!

> **Important:** If the workflow fails with a permissions error, go to  
> **Settings → Actions → General → Workflow permissions** → select **Read and write permissions** → **Save**  
> Then re-run the workflow.

---

## 📝 Future Changes (The Daily Loop)

Whenever you edit your README or any file:

```bash
# 1. See what changed
$ git status

# 2. See the actual line-by-line diff
$ git diff

# 3. Stage the changes
$ git add .

# 4. Commit with a descriptive message
$ git commit -m "📝 Update project descriptions"

# 5. Push to GitHub
$ git push
```

> After the first push with `-u`, you only need `git push` (no `origin main`).

---

## 🧰 Handy Commands Reference

| Command | What It Does |
|---------|-------------|
| `git status` | Show changed/staged/untracked files |
| `git log --oneline` | Show commit history (compact) |
| `git diff` | Show unstaged changes line by line |
| `git diff --staged` | Show staged changes (what's about to be committed) |
| `git add <file>` | Stage a specific file |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Commit staged changes with a message |
| `git push` | Upload commits to GitHub |
| `git pull` | Download latest changes from GitHub |
| `git remote -v` | Show connected remote URLs |
| `git branch` | List local branches |
| `git log --graph --oneline --all` | Visual branch history |

---

## ⚠️ Common Gotchas

1. **"Repository not found" on push** — Make sure the repo exists at `https://github.com/User8085/GithubProfile` and is public
2. **Authentication popup** — GitHub no longer accepts passwords; use a [Personal Access Token](https://github.com/settings/tokens) or the GitHub CLI (`gh auth login`)
3. **Snake workflow fails** — Check Actions permissions (see step 🔟 above)
4. **README doesn't show on profile** — The repo MUST be named exactly the same as your username (`User8085`), not `GithubProfile`. Rename it in **Settings → General → Repository name**

---

> 💡 **Tip:** Install the [GitHub CLI](https://cli.github.com/) (`gh`) for easier authentication:
> ```bash
> $ gh auth login    # follow the prompts — much easier than tokens
> ```

