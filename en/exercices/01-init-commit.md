# Exercise 1: My First Repository

**Objective:** To become familiar with initializing a repository, creating commits, and viewing the history.

---

### Steps to complete

1.  **Create a new folder** for this exercise. Name it `my-git-project`.

2.  **Open a terminal** and navigate inside this new folder.

3.  **Initialize a Git repository** here.
    <details>
      <summary>Command</summary>
      <pre><code>git init</code></pre>
    </details>

4.  **Create a file** named `biography.txt`.

5.  **Write a line** in this file, for example: "My name is [Your Name]".

6.  **Check the status** of your repository. What does Git tell you about this new file?
    <details>
      <summary>Command</summary>
      <pre><code>git status</code></pre>
    </details>

7.  **Add the `biography.txt` file** to the staging area.
    <details>
      <summary>Command</summary>
      <pre><code>git add biography.txt</code></pre>
    </details>

8.  **Check the status** of the repository again. What is the difference?

9.  **Create your first commit.** Give it a clear message, for example: "Initial commit: add biography".
    <details>
      <summary>Command</summary>
      <pre><code>git commit -m "Initial commit: add biography"</code></pre>
    </details>

10. **Modify the `biography.txt` file** by adding a new line, for example: "I am learning to use Git."

11. **Add and commit** these new changes in a single command (or in two if you prefer).

12. **View the history** of your project to see your two commits.
    <details>
      <summary>Command</summary>
      <pre><code>git log --oneline</code></pre>
    </details>

---

**Congratulations!** You have created your first local Git repository and made several commits.
