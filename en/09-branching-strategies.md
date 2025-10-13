# Lesson 9: Branching Strategies (Workflows)

Knowing how to create branches is good. Knowing how to organize them into a coherent workflow for an entire team is better. A branching strategy (or workflow) is a set of rules and conventions that a team follows to use Git. This avoids chaos and makes the project easier to maintain.

We will look at two of the most popular strategies.

## 1. GitHub Flow (The simplest and most common)

Popularized by GitHub, this workflow is extremely simple and effective, especially for web projects or applications that are deployed continuously.

### Key principles:

1.  **Everything in the `main` (or `master`) branch is deployable.** This is the golden rule. The `main` branch must always be stable and ready to be put into production.

2.  **To work on something new, create a descriptive branch from `main`.** The branch name should be explicit (e.g., `feature/add-login-page`, `fix/wrong-color-button`).

3.  **Push your branch to the remote repository regularly.** This saves your work and makes it visible to others.

4.  **Open a Pull Request (PR) when you need feedback or your work is ready.** The PR is the central tool for code review and discussion.

5.  **Merge the PR into `main` only after its approval.**

6.  **Once merged, the branch is immediately deployed to production.**

This workflow is very flexible and is based on rapid cycles of development, review, and deployment.

## 2. GitFlow (The most structured)

GitFlow is an older and much stricter model. It is well suited for projects that have planned release cycles (for example, a mobile application that releases a new version every month) rather than continuous deployment.

### The main branches:

-   `main` (or `master`): Contains the history of official versions (releases). You never commit directly to it. Each commit on `main` is a version number (tag).
-   `develop`: This is the main integration branch. All new features are merged into it. This is the state of the next upcoming version.

### The support branches:

-   **`feature/*`**: They are created from `develop`. This is where developers work on their new features. Once finished, they are merged into `develop`.
    -   Example: `feature/user-profile`

-   **`release/*`**: When the `develop` branch contains enough features for a new version, a `release` branch is created from `develop`. on this branch, only minor bug fixes are made and the release is prepared (updating the version number, etc.).
    -   Example: `release/v1.2.0`

-   **`hotfix/*`**: If a critical bug is discovered in production (on `main`), a `hotfix` branch is created from `main`. The bug is fixed, then this branch is merged into both `main` (to update production) AND `develop` (so that the fix is included in the next version).
    -   Example: `hotfix/critical-login-bug`

### Comparison

| Aspect | GitHub Flow | GitFlow |
|---|---|---|
| **Complexity** | Very simple | Complex |
| **Main branch** | `main` | `main` and `develop` |
| **Ideal for** | Continuous deployment, web projects | Planned releases, mobile/desktop applications |
| **Pace** | Fast and flexible | Structured and controlled |

For most modern projects, **GitHub Flow is an excellent starting point**. Only complicate your life with GitFlow if your project really requires it.
