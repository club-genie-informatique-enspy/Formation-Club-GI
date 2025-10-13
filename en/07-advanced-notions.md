# Lesson 7: Advanced Concepts and Best Practices

Now that you have mastered the basic workflow, let's explore more advanced commands and concepts that will make you even more productive and professional.

## `git rebase`: Rewriting history cleanly

When you merge a branch with `git merge`, it creates a "merge commit". This is fine, but sometimes it can make the history difficult to read, with many intersecting branches.

`git rebase` is an alternative. Instead of creating a merge commit, it takes the commits from your feature branch and replays them *on top* of the latest changes in the `master` branch. The result is a **linear** and much cleaner history.

```bash
# From your feature branch
git rebase master
```

```
BEFORE REBASE (identical to a merge):

      C3---C4---C5   <-- feature
     /
C1---C2---C6---C7   <-- master

AFTER REBASE:

                     C3'--C4'--C5'  <-- feature
                    /
C1---C2---C6---C7   <-- master
```
The commits from the `feature` branch have been re-created (C3', C4', C5') and placed after `master`.

**Warning**: Only use `git rebase` on branches that you have not yet shared with others. Rewriting the history of a collaborative branch can cause complex problems.

## `git stash`: Putting your work aside

Imagine: you are in the middle of a feature, and you are asked to fix an urgent bug. Your changes are not ready to be committed. What do you do?

`git stash` puts your uncommitted changes aside in a temporary "stash" and cleans your working directory.

```bash
# Stash the changes
git stash

# (Now you can switch branches and fix the urgent bug)

# Once finished, come back to your branch and retrieve your work
git stash pop
```

## `git tag`: Marking versions

When your project reaches a stable version (e.g., 1.0, 2.5), you can mark it with a "tag". This is a permanent pointer to a specific commit, which makes it easier to consult the published versions.

```bash
# Create a "lightweight" tag
git tag v1.0.0

# Push the tags to the remote repository (they are not sent by default)
git push origin --tags
```

## The `.gitignore` file

Your project often contains files that should never be tracked by Git: dependencies (`node_modules`), your editor's configuration files (`.vscode`), logs, etc.

Create a file named `.gitignore` at the root of your project and list the files or folders to ignore. Each line corresponds to a pattern.

**Example of `.gitignore`**:
```
# Dependencies
node_modules/

# Log files
*.log

# macOS system files
.DS_Store
```

## The `.gitattributes` file

Less known than `.gitignore`, the `.gitattributes` file allows you to declare specific attributes for paths (files or folders). It is a powerful tool to dictate to Git how it should treat certain files.

Create a `.gitattributes` file at the root of your project.

### Use case 1: Managing line endings (EOL)

The classic problem: Windows uses `CRLF` for line endings, while Linux and macOS use `LF`. This can create unnecessary "differences" in the files. `.gitattributes` solves this problem.

```
# Force Git to always use LF (Linux/Mac) line endings in the repository,
# but to convert them to the user's native system line endings on checkout.
* text=auto
```

### Use case 2: Git LFS (Large File Storage)

Git is not made for versioning large binary files (HD images, videos, audio files). Git LFS is an extension that solves this problem by storing pointers in the Git repository, while the large files themselves are stored on a dedicated server.

`.gitattributes` is used to tell Git LFS which files it should handle.

```
# Tell Git LFS to handle all .psd (Photoshop) files
*.psd filter=lfs diff=lfs merge=lfs -text
```

## GitHub Actions: Automating your workflow

GitHub Actions is a CI/CD (Continuous Integration / Continuous Deployment) tool integrated into GitHub. It allows you to automate actions in response to events on your repository (like a `push` or a `Pull Request`).

Create a `.github/workflows` folder in your project, and inside it, a YAML file (e.g., `main.yml`).

**Simple example**: Run tests on each push to `master`.
```yaml
name: CI
on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run tests
      run: npm test # or your project's test command
```

## GitHub Pages: Hosting your static site

GitHub Pages is a free service that takes the HTML, CSS, and JavaScript files from your repository and publishes them as a website.

1.  Go to the **Settings** of your GitHub repository.
2.  In the **Pages** section, choose the branch you want to publish (often `master` or a `gh-pages` branch).
3.  GitHub will give you the URL of your site (e.g., `https://YOUR_NAME.github.io/YOUR_REPO/`).

It's a great way to put a portfolio, documentation, or a project's presentation page online.
