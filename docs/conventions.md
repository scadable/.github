## 💻 Development Conventions

This document lists the technical standards and rules that all code and projects at Scadable must adhere to.

### Branch Protection
* **No Direct Commits to `main`**: All changes to the `main` branch **must** go through a Pull Request. Direct commits are blocked. This is our most important rule to ensure code quality and stability.

### Code Quality & Testing
* **100% Test Coverage**: All new code and logic **must be fully covered by automated tests**. If you add a new feature or fix a bug, you must also write the tests to prove it works correctly and protect it from future regressions. PRs that lower the overall test coverage will not be approved.

### Project Management
* **Single Source of Truth**: GitHub Projects is our official tool for project management and tracking work. All active development tasks must be represented on the project board.
* **Document Everything**: As mentioned in the contribution guidelines, all technical discussions and decisions must be recorded in the relevant GitHub Issue. Avoid making decisions in private chats where they can be lost.
