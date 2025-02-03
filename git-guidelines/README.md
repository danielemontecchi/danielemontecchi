# Git Guidelines

This document provides guidelines and best practices for using Git effectively in software projects. These guidelines are opinionated and tailored to my personal workflow, but I hope they can offer useful insights and structure to others as well.

---

## **Table of Contents**
1. [Branch Naming Conventions](#branch-naming-conventions)
2. [Commit Messages](#commit-messages)
3. [Branching Strategies](#branching-strategies)
4. [Pull Request Best Practices](#pull-request-best-practices)
5. [Rebasing vs Merging](#rebasing-vs-merging)

---

## **1. Branch Naming Conventions**

Use clear and descriptive branch names to indicate the purpose of the branch. Suggested patterns:

- **feature/**: For new features.
  ```
  feature/add-user-authentication
  ```
- **fix/**: For bug fixes.
  ```
  fix/login-button-error
  ```
- **hotfix/**: For critical production fixes.
  ```
  hotfix/critical-payment-issue
  ```
- **chore/**: For non-functional changes like refactoring or updating dependencies.
  ```
  chore/update-dependencies
  ```

---

## **2. Commit Messages**

Follow the [Conventional Commits](https://www.conventionalcommits.org/) standard for clear and consistent commit messages.

**Structure:**
```
<type>: <short summary> (#<issue-number>)

[optional body explaining the change in detail]
```

**Types:**
- `feat`: A new feature.
- `fix`: A bug fix.
- `docs`: Documentation updates.
- `style`: Code style changes (formatting, no functional changes).
- `refactor`: Code refactoring without adding new features or fixing bugs.
- `test`: Adding or updating tests.

**Example:**
```
feat: add user profile page (#42)

Added a new user profile page with editable fields. Includes backend API integration.
```

When possible, always reference the related issue number to provide context and traceability.

---

## **3. Branching Strategies**

The following strategy is designed to support both development and production environments efficiently.

### **Branch Structure**
- **main**: The production branch.
- **develop**: The testing and integration branch.
- **feature/**, **fix/**, **hotfix/** branches are created from `develop`.

### **Workflow**

1. **Create Branches:**
   - Branches for features, bug fixes, and hotfixes are created from the `develop` branch.
     ```bash
     git checkout develop
     git checkout -b feature/new-feature
     ```

2. **Merge to develop:**
   - Once the work on a branch is complete, it is merged into `develop`.
     ```bash
     git checkout develop
     git merge feature/new-feature
     ```

3. **Pull Request to main:**
   - To publish changes to production, create a pull request from `develop` to `main`.
   - Ensure all tests pass and the PR is reviewed before merging.

4. **Delete Branches:**
   - After the pull request is merged, delete the feature or fix branch to keep the repository clean.
     ```bash
     git branch -d feature/new-feature
     git push origin --delete feature/new-feature
     ```

### **Benefits:**
- Clear separation between production (`main`) and testing (`develop`).
- Organized branch structure for features, fixes, and hotfixes.
- Easier collaboration with well-defined processes for merging and publishing changes.

---

## **4. Pull Request Best Practices**

- **Keep PRs Small**: Focus on a single change or feature.
- **Provide Clear Descriptions**: Explain the purpose and scope of the PR.
- **Request Reviews Early**: Share your work early to get feedback.
- **Use Checklists**: Ensure you’ve covered all necessary tasks.

Example PR description:
```
### Description
This PR adds a new feature to manage user profiles.

### Changes
- Added new profile page.
- Implemented backend API endpoints.

### Checklist
- [x] Unit tests added.
- [x] Documentation updated.
```

---

## **5. Rebasing vs Merging**

- **Rebase**: Keeps a linear commit history. Ideal for maintaining clean branches.
  ```bash
  git rebase main
  ```
- **Merge**: Preserves the full commit history but can result in more complex logs.
  ```bash
  git merge main
  ```

### **Recommendation:**
Use rebase for feature branches and merge for integrating larger branches like `develop` into `main`. Always communicate with your team to decide on a consistent approach.

---

Feel free to adapt these guidelines to your workflow. Happy coding!

