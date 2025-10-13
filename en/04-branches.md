# Lesson 4: The Power of Branches

So far, we have been working on a single timeline, the `master` (or `main`) branch. Branches are arguably the most powerful feature of Git. They allow you to diverge from the main line of development to work on a new feature, a bug fix, or an experiment in complete safety, without affecting the main project.

## What is a branch?

Think of a branch as a movable pointer to a commit. When you create a branch, you are simply creating a new pointer. It's extremely lightweight and fast.

The workflow is as follows:
1.  You are working on the main branch (`master`).
2.  You decide to develop a new feature.
3.  You create a new branch (e.g., `feature/login`).
4.  You switch to this new branch and make your changes and commits there.
5.  Meanwhile, if a critical bug appears in the main version, another developer can create a `hotfix/urgent-bug` branch from `master`, fix it, and merge their fix into `master` without your work on the feature being impacted.
6.  Once your feature is finished and tested, you "merge" it into the `master` branch.

```
      C3---C4---C5   <-- feature/login (HEAD)
     /
C1---C2---C6---C7   <-- master
```

## Commands for managing branches

### `git branch`

This command, used alone, lists all the branches in your local repository. The asterisk `*` indicates the branch you are currently on.

```bash
# List branches
git branch

# Create a new branch
git branch branch-name
```

### `git checkout`

This command allows you to "move" from one branch to another.

```bash
# Move to an existing branch
git checkout branch-name
```

You can combine creation and switching in a single command with the `-b` option.

```bash
# Create the branch AND switch to it directly
git checkout -b new-branch
```
This is the command you will use most often to start a new task.

### `git merge`

Once the work on your branch is finished, you will want to integrate it into your main branch (e.g., `master`). This is called a merge.

```bash
# 1. First, go back to the branch that will RECEIVE the changes
git checkout master

# 2. Then, start the merge with the branch you want to integrate
git merge branch-to-merge
```

Git will then attempt to combine the histories. If the changes do not conflict, the merge is done automatically.

      C3---C4---C5      <-- feature/login
     /            \
C1---C2---C6---C7---M   <-- master (HEAD)

The `M` commit is a "merge commit"; it has two parents and brings the two histories together.

### `git branch -d`


Once a branch has been merged, it is generally no longer useful. You can delete it to keep your repository clean.

```bash
# Delete a branch (only if it has been merged)
git branch -d branch-name
```

## Practical Example

1.  You are on `master`.
2.  Create and switch to a branch for a new "Contact" page:
    `git checkout -b feature/contact-page`
3.  Create the `contact.html` file and make a commit.
    `git add contact.html`
    `git commit -m "feat: add contact page"`
4.  Your feature is finished. Go back to `master`:
    `git checkout master`
5.  Merge your work:
    `git merge feature/contact-page`
6.  Clean up by deleting the branch:
    `git branch -d feature/contact-page`

Branches are an essential tool for organized and collaborative work. In the next lesson, we will see how to interact with a remote repository like GitHub.

```