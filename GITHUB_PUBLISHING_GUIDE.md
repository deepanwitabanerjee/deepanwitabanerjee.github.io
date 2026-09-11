# Publishing Updates to GitHub Pages

Use this guide whenever you update your website files and want the changes to appear at `https://deepanwitabanerjee.github.io/`.

## The simple idea

Your website files live on your computer. Git keeps a history of changes, and GitHub stores that history online. To publish an update, you:

1. edit and check the site locally;
2. save the changed files in Git (a **commit**);
3. upload that commit to GitHub (a **push**);
4. wait a minute or two for GitHub Pages to publish it.

You only need to perform the first-time setup once. After that, use the routine in [Every future website update](#every-future-website-update).

## Before you start

You need:

- A GitHub account.
- A GitHub repository named exactly `deepanwitabanerjee.github.io`.
- Git installed on your computer. In Terminal, run:

  ```bash
  git --version
  ```

  If you see a version number, Git is installed. If not, install the Xcode Command Line Tools by running `xcode-select --install` in Terminal and following the prompts.

- A Terminal window. On a Mac: open **Terminal** from Applications → Utilities, or search for it with Spotlight.

> Important: Do not publish passwords, API keys, personal IDs, private notes, or other confidential files. This repository is public.

## First-time setup: recommended route

The safest first-time approach is to clone the GitHub repository, then copy your site files into that clone. This avoids accidentally connecting the wrong local folder to GitHub.

### 1. Check whether the repository already exists on GitHub

Visit [github.com/deepanwitabanerjee](https://github.com/deepanwitabanerjee). Look for a repository named `deepanwitabanerjee.github.io`.

If it does not exist:

1. Select **New** on GitHub.
2. Set the repository name to `deepanwitabanerjee.github.io` exactly.
3. Choose **Public**.
4. Do **not** add a README, `.gitignore`, or license during this step; your website folder already contains files.
5. Select **Create repository**.

### 2. Clone the repository to your computer

In Terminal, run these commands one at a time:

```bash
cd ~/Downloads
git clone https://github.com/deepanwitabanerjee/deepanwitabanerjee.github.io.git
```

GitHub may open a browser window and ask you to sign in. Complete that sign-in.

This creates a folder named `deepanwitabanerjee.github.io` in Downloads. It is the folder that is connected to GitHub.

### 3. Copy the current website files into the cloned folder

Your current working website folder is:

```text
/Users/deepanwitabanerjee/Downloads/deepanwitabanerjee.github.io-main
```

Open both folders in Finder:

- `deepanwitabanerjee.github.io-main` — your current website files.
- `deepanwitabanerjee.github.io` — the new GitHub-connected clone.

Copy the contents of the first folder into the second folder. When Finder asks whether to replace files, choose **Replace** only when you are intentionally copying the newer website files into the clone.

Do not copy the `.git` folder if one is visible. It is hidden by default and belongs only to the cloned GitHub folder.

### 4. Publish the first version

Run:

```bash
cd ~/Downloads/deepanwitabanerjee.github.io
git status
git add .
git commit -m "Publish portfolio website"
git push -u origin main
```

If `git push` says the branch is `master` rather than `main`, use this command instead:

```bash
git push -u origin master
```

### 5. Turn on GitHub Pages, if needed

On the repository page on GitHub:

1. Select **Settings**.
2. Select **Pages** in the left sidebar.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Choose branch **main** (or **master**, if that is what your repository uses) and folder **/(root)**.
5. Select **Save**.

GitHub will show the published URL after deployment. The first publication can take a few minutes.

## Every future website update

After the initial setup, use this routine every time.

### 1. Make your edits in the GitHub-connected folder

Edit files inside:

```text
/Users/deepanwitabanerjee/Downloads/deepanwitabanerjee.github.io
```

This matters: edits made only in `deepanwitabanerjee.github.io-main` will not be pushed unless you copy them into the connected folder first.

### 2. Check the website locally

Open `index.html` from that folder in a browser. Confirm the layout, links, images, and CV buttons work.

### 3. Upload the changes

In Terminal, run:

```bash
cd ~/Downloads/deepanwitabanerjee.github.io
git status
git add .
git commit -m "Describe your update here"
git push
```

Replace the commit message with a short description, for example:

```bash
git commit -m "Update research portfolio and publications"
```

or:

```bash
git commit -m "Add Berkeley Lab research photo"
```

### 4. Confirm it published

1. Visit your repository on GitHub. The newest commit should appear at the top of the file list.
2. Visit `https://deepanwitabanerjee.github.io/`.
3. If you do not see the update, wait 1–3 minutes, then refresh the page. On a Mac, use **Command + Shift + R** for a hard refresh.

## The four commands to remember

Once setup is complete, these are the only commands you usually need:

```bash
cd ~/Downloads/deepanwitabanerjee.github.io
git status
git add .
git commit -m "Short description of update"
git push
```

## What each Git command means

| Command | What it does |
| --- | --- |
| `git status` | Shows which files changed. Always run this first. |
| `git add .` | Selects all current changes for the next saved version. |
| `git commit -m "..."` | Saves a named checkpoint on your computer. |
| `git push` | Uploads your saved checkpoint to GitHub. |
| `git pull` | Downloads changes made on GitHub or another computer. |

## If you edit from another computer

Before starting work, run:

```bash
cd ~/Downloads/deepanwitabanerjee.github.io
git pull
```

Then edit, check, commit, and push as usual. This reduces the chance of conflicts.

## Common problems and safe fixes

### “fatal: not a git repository”

You are in the wrong folder. Run:

```bash
cd ~/Downloads/deepanwitabanerjee.github.io
git status
```

### “nothing to commit, working tree clean”

Git does not see any changes in this folder. Check that you saved your edits and that you edited the GitHub-connected folder, not `deepanwitabanerjee.github.io-main`.

### “rejected” or “fetch first” when pushing

GitHub has changes you do not have locally. Run:

```bash
git pull --rebase
git push
```

If Git reports a conflict, stop before deleting or overwriting anything. Keep the Terminal open and ask for help with the exact message.

### The GitHub website is old after pushing

First check that `git push` completed successfully. Then wait a few minutes and hard-refresh the public site with **Command + Shift + R**. If needed, check GitHub repository **Settings → Pages** for a deployment error.

### Images do not appear

Make sure the image is inside the repository, usually in `assets/`, and that the filename in `index.html` matches exactly—including uppercase/lowercase letters. Run `git status` to make sure the new image is included before committing.

## Optional: use GitHub Desktop instead of Terminal

GitHub Desktop provides buttons for the same workflow:

1. Add your repository with **File → Add Local Repository**.
2. Make website edits.
3. Open GitHub Desktop; changed files appear on the left.
4. Write a brief summary at the bottom-left.
5. Select **Commit to main**.
6. Select **Push origin**.

Use Terminal for the first-time clone/setup if GitHub Desktop reports that the folder is not a repository.

## A good habit before every push

Review this checklist:

- [ ] I checked the website locally.
- [ ] I did not add private or confidential files.
- [ ] New images and PDFs are in the correct folders.
- [ ] `git status` shows only changes I expect.
- [ ] My commit message says what changed.
- [ ] I refreshed the live site after GitHub Pages finished publishing.
