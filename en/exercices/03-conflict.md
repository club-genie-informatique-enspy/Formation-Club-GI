# Exercise 3: The Inevitable Conflict

**Objective:** To learn how to identify, understand, and resolve a merge conflict.

---

### Context

Merge conflicts occur when two branches have modified the same line of the same file. Git doesn't know which version to choose and asks you to intervene. We are going to create one intentionally to practice.

### Steps to complete

1.  **Start from the `my-git-project` project** at the end of exercise 2. Make sure you are on the `master` branch.

2.  **Create a new branch** named `feature/catchy-title`.
    <details>
      <summary>Command</summary>
      <pre><code>git checkout -b feature/catchy-title</code></pre>
    </details>

3.  In this branch, **modify the very first line** of the `biography.txt` file to something like: "Title: The biography of a future Git expert".

4.  **Add and commit** this change on the `feature/catchy-title` branch.

5.  **Go back to the `master` branch**.
    <details>
      <summary>Command</summary>
      <pre><code>git checkout master</code></pre>
    </details>

6.  Here, **ALSO modify the same first line** of the `biography.txt` file, but with different text. For example: "Introduction: My journey with Git".

7.  **Add and commit** this change on the `master` branch.

8.  The moment of truth. **Try to merge** the `feature/catchy-title` branch into `master`.
    <details>
      <summary>Command</summary>
      <pre><code>git merge feature/catchy-title</code></pre>
    </details>

9.  **Conflict!** Git should stop and show you a message `CONFLICT (content): Merge conflict in biography.txt`. Open the `biography.txt` file in your editor.

10. **Analyze the file**. You will see the Git conflict markers:
    ```
    <<<<<<< HEAD
    Introduction: My journey with Git
    =======
    Title: The biography of a future Git expert
    >>>>>>> feature/catchy-title
    ```

11. **Resolve the conflict.** Modify the file to keep only the final version you want. You can choose one of the two versions, or even write a completely new sentence. **You must delete the markers** `<<<<<<<`, `=======`, and `>>>>>>>`.

12. Once the file is cleaned and saved, **add it to the Staging Area** to mark the conflict as resolved.
    <details>
      <summary>Command</summary>
      <pre><code>git add biography.txt</code></pre>
    </details>

13. **Finish the merge** by creating the merge commit. Git will offer you a default message, which you can keep.
    <details>
      <summary>Command</summary>
      <pre><code>git commit</code></pre>
    </details>

---

**Excellent!** You have survived your first merge conflict. This is a crucial skill for teamwork.
