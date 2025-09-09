
## 📜 Contribution Guidelines

This document outlines the step-by-step process for contributing to any project at Scadable. Following these guidelines helps us maintain a smooth workflow and high-quality codebase.

### The Core Workflow

All work at Scadable follows a simple principle: **Every change starts with an issue and ends with a pull request.** This ensures our work is tracked, documented, and properly reviewed.

#### **Step 1: Find or Create an Issue**

All tasks, features, and bug fixes must be tracked in a GitHub Issue.
* **Project Board**: Check the **GitHub Project board** to find issues ready for development. If you don't have access, please ask a supervisor to grant it.
* **Documentation is Key**: All conversations, questions, and problem-solving related to a task **must be documented** in the comments of its corresponding issue. This creates a searchable history for future decisions.

#### **Step 2: Create a Branch**

Once you've been assigned an issue, create a new branch from `main`.
* **Branch Naming Convention**: Your branch name must follow the format: `issue-number/short-description`.
    * Example: If you are working on issue #42, which is about creating a login form, your branch name would be `42/create-login-form`.

#### **Step 3: Make Commits**

We use **Conventional Commits** to create a clear and readable commit history. You will be prompted to follow this format automatically when you commit.
* **Commit Regularly**: Don't save all your work for one big commit at the end of the day. Make small, logical commits frequently. This makes your changes easier to review.
* **Commit Message Format**: Use the interactive tool to select the type of change you are making. Here are the standard types and their meanings:

| Type | Description |
| :--- | :--- |
| `feat` | A new feature. |
| `fix` | A bug fix. |
| `docs` | Documentation only changes. |
| `style` | Changes that do not affect the meaning of the code (e.g., white-space, formatting, missing semi-colons). |
| `refactor` | A code change that neither fixes a bug nor adds a feature. |
| `perf` | A code change that improves performance. |
| `test` | Adding missing tests or correcting existing tests. |
| `chore`| Changes to the build process, auxiliary tools, or libraries. |

#### **Step 4: Create a Pull Request (PR)**

Once your code is ready for review, open a Pull Request (PR) against the `main` branch.
* **Make PRs Regularly**: Don't wait a full week to create a PR. Smaller, more frequent PRs are easier and faster to review.
* **Link to the Issue**: In the PR description, you **must** include a keyword to automatically link and close the issue upon merging. Example: `Fixes #42` or `Closes #42`.
* **Automated Checks (CI)**: When you create a PR, our CI pipeline will automatically run. This includes:
    * Running all tests.
    * Linting the code for style errors.
    * Performing an AI code health check.
    All checks must pass before the PR can be merged.

#### **Step 5: Code Review**

Your code must be reviewed and approved by at least **one other developer** before it can be merged.
* Handle feedback by pushing new commits to the same branch.
* Once your PR is approved and all CI checks are passing, it can be merged into `main`.

#### **Step 6: Deployment (CD)**

After your PR is merged into `main`, our Continuous Deployment (CD) pipeline will automatically build a new image and push it to our container registry.
