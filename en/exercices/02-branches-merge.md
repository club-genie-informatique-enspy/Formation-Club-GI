# Exercise 2: Life in Branches

**Objective:** To master the basic workflow with branches: creating, switching, and merging.

---

### Context

You are going to add a new feature to your `my-git-project` project from the previous exercise. The work will be done on a dedicated branch so as not to impact the main branch (`master`).

### Steps to complete

1.  **Start from the `my-git-project` project** from exercise 1. Make sure you are on the `master` branch.

2.  **Create a new branch** named `feature/skills`.
    <details>
      <summary>Command</summary>
      <pre><code>git checkout -b feature/skills</code></pre>
    </details>

3.  **Create a new file** named `skills.txt`.

4.  **Add some skills** to this file, one per line. For example:
    -   HTML
    -   CSS
    -   JavaScript

5.  **Add and commit** this new file on your `feature/skills` branch. Choose a clear commit message.

6.  **Go back to the `master` branch**.
    <details>
      <summary>Command</summary>
      <pre><code>git checkout master</code></pre>
    </details>

7.  Has the `skills.txt` file disappeared? (This is normal!). **Modify the `biography.txt` file** to add a line, for example: "My goal: to become a Git expert."

8.  **Add and commit** this change on the `master` branch.

9.  Your new feature is ready. **Merge** the `feature/skills` branch into `master`.
    <details>
      <summary>Command</summary>
      <pre><code>git merge feature/skills</code></pre>
    </details>

10. **Check the status of your project**. You should now see both the `skills.txt` file and the latest version of `biography.txt`.

11. **(Optional) Clean up your repository** by deleting the `feature/skills` branch, which is no longer needed.
    <details>
      <summary>Command</summary>
      <pre><code>git branch -d feature/skills</code></pre>
    </details>

---

**Congratulations!** You have isolated the development of a feature in a branch and integrated it cleanly into the main project.
