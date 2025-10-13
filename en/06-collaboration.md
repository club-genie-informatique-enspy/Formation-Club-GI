# Lesson 6: Collaboration with Pull Requests

We now know how to work with a remote repository. But how do we collaborate cleanly and organized on a project? The answer is: **Pull Requests** (or *Merge Requests* on GitLab).

A Pull Request (PR) is a formal request to integrate the changes from one of your branches into another (usually the main `master` or `main` branch). It is a space for discussion and code review before the merge.

## The Pull Request workflow

Here is the most common scenario for a contributor on a project:

1.  **Create a branch**: You NEVER work directly on `master`. For each new feature or fix, you create a descriptive branch.
    ```bash
    git checkout -b feature/amazing-new-page
    ```

2.  **Make commits**: You work on your branch, making clear and atomic commits.

3.  **Push the branch to GitHub**: Once your work is ready (or even in progress if you want feedback), you push your branch to the remote repository `origin`.
    ```bash
    git push origin feature/amazing-new-page
    ```

4.  **Open the Pull Request**: In the GitHub interface, you will see a button appear to create a Pull Request from the branch you just pushed. Click on it.
    -   You give your PR a clear title.
    -   You write a description explaining what you did and why.
    -   You can designate "reviewers", colleagues who will have to approve your work.

5.  **Code review and discussion**: This is the heart of the process. Your colleagues can now:
    -   See all the changes you are proposing.
    -   Leave comments on specific lines of code.
    -   Request changes.

6.  **Update the PR**: If changes are requested, you simply make new commits on your local branch (`feature/amazing-new-page`) and push them again (`git push`). The Pull Request will automatically update with your new commits.

7.  **Approval and Merge**: Once everyone is satisfied and the automated tests (if any) are green, the Pull Request is approved. A project maintainer can then click the "Merge Pull Request" button directly in GitHub.
    Your branch is now merged into `master`!

8.  **Cleaning up**: Once the PR is merged, you can (and should) delete your feature branch, both on the remote (via a button in GitHub) and locally.
    ```bash
    # Get back on master and get the merged version
    git checkout master
    git pull origin master

    # Delete the local branch
    git branch -d feature/amazing-new-page
    ```

## Conflict resolution

Sometimes, while you were working on your branch, the `master` branch has evolved and the changes conflict with yours. In this case, Git cannot merge automatically.

GitHub will warn you that there are conflicts in the PR. To resolve them:

1.  Make sure your local `master` branch is up to date:
    `git checkout master`
    `git pull origin master`
2.  Go back to your feature branch:
    `git checkout feature/amazing-new-page`
3.  Try to merge `master` INTO your branch:
    `git merge master`
4.  Git will tell you which files are in conflict. Open them in your editor. You will see markers `<<<<<<<`, `=======`, `>>>>>>>`.
5.  **Modify the file** to keep only the desired final version, removing the Git markers.
6.  Once all conflicts are resolved, make a new commit:
    `git add .`
    `git commit -m "fix: merge conflict resolution"`
7.  Push your changes: `git push`. The PR will be updated and the conflicts should be gone.

## Conclusion

Congratulations! You now have all the keys to use Git and GitHub effectively, from creating a solo project to collaborating on a team project. Practice is the key, so don't hesitate to create personal projects to experiment.
