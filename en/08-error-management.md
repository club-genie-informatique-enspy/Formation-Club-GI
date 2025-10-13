# Lesson 8: Handling Common Mistakes (The Rescue Toolkit)

Everyone makes mistakes. A good developer is not defined by their absence of errors, but by their ability to correct them cleanly. Git offers several tools to go back or fix things.

## Scenario 1: "I made a typo in my last commit message!"

This is the easiest mistake to fix, as long as you haven't pushed your commit to the remote repository yet.

### The solution: `git commit --amend`

This command allows you to "modify" the very last commit. It opens your text editor so you can change the message. You can also take the opportunity to add files you might have forgotten.

```bash
# Oops, I forgot the "style.css" file
git add style.css

# Opens the editor to correct the message of the last commit
# and include the newly added file.
git commit --amend
```

## Scenario 2: "I added a file to the Staging Area by mistake."

You did `git add .` but a sensitive or unnecessary file slipped in.

### The solution: `git reset` (for the Staging Area)

`git reset` without a specified commit acts on the Staging Area.

```bash
# To remove a specific file from the Staging Area
git reset file-name.txt

# To completely empty the Staging Area
git reset
```
Your changes in the files are not lost, they are simply removed from the staging area.

## Scenario 3: "My last local commits are bad, I want to go back."

Your work on a local branch has gone in the wrong direction. You have **not yet pushed** these commits.

### The solution: `git reset` (with a commit)

`git reset` can also reset your branch to a previous state. `HEAD` is a pointer to your current position (the last commit).

-   `git reset --soft HEAD~1`: Undoes the last commit, but keeps the changes in the Staging Area. Useful for redoing a correct commit.
-   `git reset --mixed HEAD~1` (default behavior): Undoes the last commit and leaves the changes in your working directory. You will have to `git add` them again.
-   `git reset --hard HEAD~1`: **WARNING, DANGEROUS**. Undoes the last commit AND **permanently deletes** all associated changes. Only use this if you are absolutely sure you want to throw everything away.

## Scenario 4: "I pushed a commit that contains a bug and it needs to be undone."

This is the most delicate case. The commit is public, on the remote repository. You should **NEVER** use `git reset` on a shared branch, as it rewrites history and creates chaos for your collaborators.

### The solution: `git revert`

`git revert` is the safe method to undo a public commit. Instead of deleting the commit from history, it creates a **new commit** that does the exact opposite of the changes in the problematic commit.

The history is preserved, and the undo is documented.

```bash
# Identify the hash (the identifier) of the commit to undo with `git log`
# For example: 7a8b2c9

# Creates a new commit that undoes the changes of 7a8b2c9
git revert 7a8b2c9

# All you have to do is push this new undo commit
git push
```

In summary:
-   **Local history (not pushed)?** `git commit --amend` and `git reset` are your friends.
-   **Public history (pushed)?** `git revert` is the only safe option.
