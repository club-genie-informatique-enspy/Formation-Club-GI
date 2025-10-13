# Exercise 4: Interactive Rebase for a Clean History

**Objective:** To learn how to use interactive rebase (`rebase -i`) to modify, merge (squash), and reorder commits before sharing them.

---

### Context

Sometimes, when developing a feature, we tend to make a lot of small work-in-progress commits ("WIP", "fix typo", "it finally works"). Before merging this work into a main branch, it is good to "clean up" this history to make it more readable. This is the role of interactive rebase.

### Steps to complete

1.  **Start from a clean repository**, on the `master` branch (you can reuse the project from the previous exercises).

2.  **Create a new branch** for this exercise, named `feature/refactoring-bio`.
    <details>
      <summary>Command</summary>
      <pre><code>git checkout -b feature/refactoring-bio</code></pre>
    </details>

3.  Now, we are going to make a series of small "draft" commits. Modify the `biography.txt` file and make a commit **after each modification**:
    -   Add a line "Start of refactoring." -> Commit with the message `WIP: start refactoring`.
    -   Correct a spelling mistake somewhere. -> Commit with the message `fix: typo`.
    -   Delete the line "Start of refactoring." and add "Final version of the biography." -> Commit with the message `feat: final version of bio`.

4.  **View your history**. You should see these three somewhat messy commits.
    <details>
      <summary>Command</summary>
      <pre><code>git log --oneline</code></pre>
    </details>

5.  It's time to clean up! We are going to merge these last 3 commits into a single one. **Start the interactive rebase** by telling it to work on the last 3 commits from your current position (`HEAD`).
    <details>
      <summary>Command</summary>
      <pre><code>git rebase -i HEAD~3</code></pre>
    </details>

6.  **The text editor opens**. It shows you the list of commits, with the word `pick` in front of each one. `pick` means "keep this commit".
    ```
    pick 2d3f4a5 WIP: start refactoring
    pick 9a8b7c6 fix: typo
    pick 1e2d3f4 feat: final version of bio
    ```

7.  **Modify this file** to tell Git what you want to do. We are going to keep the first commit (`pick`) and merge the next two (`squash`) into it.
    -   Keep the first line with `pick`.
    -   Replace `pick` with `s` (or `squash`) for the second and third lines.
    ```
    pick 2d3f4a5 WIP: start refactoring
    s 9a8b7c6 fix: typo
    s 1e2d3f4 feat: final version of bio
    ```
    -   Save and close the file.

8.  **A new editor opens**. Git now asks you to write the **new commit message** that will combine the messages of the three old commits. Clean up this text and write a single clear and concise commit message, for example: `refactor(bio): improvement of the biography`.

9.  Save and close this second file.

10. **Check the history again**. If everything went well, your three draft commits have been replaced by a single clean and explicit commit.

---

**Congratulations!** You have used one of Git's most powerful tools to maintain a readable and professional project history. This is a highly valued skill in teamwork.
