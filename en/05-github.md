# Lesson 5: Working with Remote Repositories (GitHub)

So far, all our work has been local, on our own machine. This is useful, but the real power of Git is revealed when you collaborate and share your code. This is the role of platforms like GitHub, GitLab, or Bitbucket.

A remote repository is simply a version of your project that is hosted on a server, usually on the Internet.

## The workflow with a remote repository

The work cycle is enhanced with a few commands to synchronize your local work with the remote repository.

### 1. Create a repository on GitHub

Before you can send your code, you need a place to put it.

1.  Log in to your GitHub account.
2.  Click on the `+` in the top right and choose "New repository".
3.  Give it a name (e.g., `git-course-demo`), a description, and choose whether it should be public or private.
4.  **Important**: DO NOT check the "Initialize this repository with a README" box. We already have a local project, we want an empty repository to push our code to.
5.  Click "Create repository".

### 2. `git remote add`

Once the repository is created, GitHub will give you a URL (in HTTPS or SSH). This URL is the address of your remote repository. You now need to link your local repository to this remote repository.

The `git remote add` command creates this connection. We give it a name (by convention, `origin`) and the URL.

```bash
# Syntax: git remote add <remote-name> <remote-url>
git remote add origin https://github.com/YOUR_USERNAME/git-course-demo.git
```

### 3. `git push`

Now that the link is made, you can "push" your local work to the remote repository. The `git push` command sends your commits to `origin`.

The first time you push, you need to specify the local branch you want to send and what it should be called on the remote.

```bash
# Syntax: git push -u <remote> <local-branch>
git push -u origin master
```

-   `-u` (or `--set-upstream`) creates a link between your local `master` branch and the `master` branch on `origin`. Thanks to this, the next times, you will only have to type `git push`.

### 4. `git pull`

If changes have been made to the remote repository (by a colleague, for example), you need to retrieve them on your local machine. This is the role of `git pull`.

This command fetches the changes from the remote repository and merges them directly into your current local branch.

```bash
# Fetches changes from the remote and merges them
git pull origin master
```

### 5. `git clone`

What if you want to start working on a project that already exists on GitHub? You are not going to start with `git init`. You are going to "clone" it.

The `git clone` command does two things:
1.  It downloads the entire project and its history from a remote repository.
2.  It automatically configures the link to the `origin` remote for you.

```bash
# Clone a project from GitHub
git clone https://github.com/someone/another-project.git
```

This will create an `another-project` folder on your machine, and you will be ready to work.

## Summary of commands

-   `git remote add origin <url>`: Link a local repository to a remote repository.
-   `git push`: Send your commits to the remote.
-   `git pull`: Retrieve commits from the remote and merge them.
-   `git clone <url>`: Download an existing remote repository to start working on it.

In the last lesson, we will discuss collaboration in more detail with Pull Requests.
