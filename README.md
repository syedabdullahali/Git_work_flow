# 🚀 Git Flow Guidelines

This document defines the **Git workflow** for our team to ensure clean, consistent, and conflict-free development.

---

## 🧭 Branch Structure

We follow a **standard Git Flow** model:

| Branch | Purpose |
|--------|----------|
| `main` | Stable production-ready code |
| `develop` | Integration branch for completed features |
| `feature/*` | For developing individual features or tasks |
| `release/*` | For final testing and version preparation |
| `hotfix/*` | For critical production fixes |

---

## 🪄 Branch Naming Convention

Use **lowercase**, separate words with **hyphens (-)**.

Examples:
```

feature/user-upload-fix
feature/add-notification-api
release/v1.0.0
hotfix/login-crash

````

---

## 🧩 Workflow Steps

1. **Create a feature branch**
   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/your-feature-name


2. **Commit changes**

   ```bash
   git add .
   git commit -m "feat: short description of change"
   ```

3. **Push your branch**

   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create a Pull Request (PR)**

   * Base branch → `develop`
   * Reviewer required before merge
   * Squash commits if needed

5. **Merge into `develop`**

   * After testing and review approval

6. **Prepare release**

   ```bash
   git checkout develop
   git checkout -b release/v1.0.0
   # Final testing, version bump
   git push origin release/v1.0.0
   ```

7. **Merge to `main`**

   ```bash
   git checkout main
   git merge release/v1.0.0
   git tag -a v1.0.0 -m "Release v1.0.0"
   git push origin main --tags
   ```

8. **Merge release back to develop**

   ```bash
   git checkout develop
   git merge release/v1.0.0
   git push origin develop
   ```

---

## 🧠 Commit Message Convention

Follow this format:

```
<type>(<scope>): <short description>
```

### Common Types

| Type       | Meaning                                  |
| ---------- | ---------------------------------------- |
| `feat`     | New feature                              |
| `fix`      | Bug fix                                  |
| `chore`    | Maintenance or tooling                   |
| `docs`     | Documentation update                     |
| `refactor` | Code improvement (no feature/bug change) |
| `style`    | Formatting, spacing, etc.                |
| `test`     | Adding or updating tests                 |

Example:

```
feat(upload): allow batch upload up to 500 users
fix(api): handle missing user data
chore(deps): update express version
```

---

## 🧯 Hotfix Process

For production issues:

```bash
git checkout main
git pull origin main
git checkout -b hotfix/fix-login-error
# fix the issue
git commit -m "fix(login): resolve crash on invalid token"
git push origin hotfix/fix-login-error
```

* Create PR → `main`
* Tag and deploy once merged
* Merge back into `develop`

---

## 🧭 Visual Git Flow Diagram

```
          +--------------------+           
          |     main (prod)    |  ←←←←←←←←←←←←←←←←←←←←←←←
          +---------▲----------+                        |
                    |                                   |
           +--------+---------+                         |
           |     release/*    | (testing & staging)     |
           +--------▲---------+                         |
                    |                                   |
           +--------+---------+                         |
           |     develop      | ←────────────── merge from feature/*
           +--------▲---------+
                    |
          +---------+----------+
          |     feature/*      |  (new features / tasks)
          +--------------------+

  Hotfixes (from main):
  main → hotfix/* → main → develop
```

---

## ✅ Summary

**Main rules:**

* Never commit directly to `main` or `develop`
* Always create PRs for merges
* Keep commits small and descriptive
* Tag every release version

---

### 💡 Example Flow

```
feature/user-upload-fix → develop → release/v1.0.0 → main
```

---

**Author:** Team
**Version:** 1.0
**Last Updated:** 2025-10-14

```

---

Would you like me to make this Markdown look **GitHub-styled with emojis and color badges (for better presentation in README format)**? It’ll look great if you plan to show it to your manager or team tomorrow.
```
