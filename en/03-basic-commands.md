# Lesson 3: Basic Git Commands

In this lesson, we will cover the core of the Git workflow. These are the commands you will use 90% of the time.

## The 3-Step Workflow

Git operates with three main "areas":

1.  **The Working Directory**: This is your project folder, where you modify, create, or delete files.
2.  **The Staging Area**: This is an intermediate area. You add the changes you want to include in the next "snapshot" (commit) here. This allows you to precisely choose what will be saved.
3.  **The Repository (.git)**: This is where Git permanently stores the snapshots of your project in the form of commits.

The process is as follows: You modify your files (Working Directory), you select the changes to be saved (Staging Area), and then you save them permanently (Repository).

```
+----------------------+        +--------------------+        +----------------+
|                      |        |                    |        |                |
|  Working Directory   | git add|   Staging Area     | git    | Repository     |
|                      |------->|   (Index)          | commit | (.git)         |
|                      |        |                    |------->|                |
|                      |<-------|                    |        |                |
|                      | git    |                    |        |                |
|                      | checkout                    |        |                |
+----------------------+        +--------------------+        +----------------+
```

## Essential Commands

### `git init`

We've seen it before, but this is the command that turns a normal folder into a Git repository. It creates the hidden `.git` subfolder that contains all the repository's logic.

### `git status`

This is your best friend. This command tells you the state of your repository: which files are modified, which are in the Staging Area, etc. Run it often!

```bash
# Displays the current state of the repository
git status
```

### `git add`

This command adds changes from the working directory to the staging area.

```bash
# To add a specific file
git add file-name.txt

# To add all modified and new files in the current directory
git add .
```

### `git commit`

This is the action of saving the snapshot of your Staging Area to your repository. Each commit has a unique ID and a message that describes the changes.

The commit message is **crucial**. It should be clear and concise.

```bash
# Opens a text editor to write a commit message
git commit

# Allows you to pass the message directly (useful for small changes)
git commit -m "Explicit commit message"
```

### `git log`

This command allows you to see the commit history of your project. You will see the author, date, and message for each commit.

```bash
# Displays the full history
git log

# Displays a simplified history with one line per commit
git log --oneline
```

## Example of a Complete Workflow

Let's imagine a new project.

1.  Navigate to the project folder.
2.  Initialize the repository:
    `git init`
3.  Create an `index.html` file.
4.  Check the status:
    `git status` (Git will tell us that `index.html` is "untracked").
5.  Add it to the Staging Area:
    `git add index.html`
6.  Check the status again:
    `git status` (Git will tell us that `index.html` is ready to be committed).
7.  Save our first commit:
    `git commit -m "feat: add base index.html file"`
8.  View the history:
    `git log`

You have just completed the basic Git cycle! In the next lesson, we will explore Git's most powerful feature: branches.
