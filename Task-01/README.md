# 📘 GIT-01 – Initialize, Commit, and Branch Basics

## 🎯 Objective

The objective of this task is to understand and implement the fundamental Git workflow, including:

* Initializing a Git repository
* Creating and committing files (index.html)
* Working with branches
* Merging changes back into the main branch
* Connecting to GitHub and pushing code
* Verifying commit history

---

## 🛠️ Steps Performed

### 1. Initialize Repository

A new Git repository was initialized using:

```bash
git init
```

The default branch was renamed to `main`:

```bash
git branch -M main
```

---

### 2. Add Remote Repository

Connected the local repository to your GitHub repository:

```bash
git remote add origin https://github.com/your-username/your-repo.git
```

---

### 3. Create and Commit Files

* Created a sample project file (`index.html`) manually in the project folder

Example content of `index.html`:

```html
<html>
  <body>
    <h1>GIT-01</h1>
  </body>
</html>
```

* Added files to staging:

```bash
git add .
```

* Committed changes:

```bash
git commit -m "GIT-01: Initial commit with index.html"
```

---

### 4. Create and Work on a New Branch

A new branch `feature-update` was created and switched to:

```bash
git checkout -b feature-update
```

* Modified `index.html` (added new content manually)

Updated `index.html`:

```html
<html>
  <body>
    <h1>GIT-01</h1>
    <p>Feature added</p>
  </body>
</html>
```

* Verified changes using:

```bash
git diff
```

* Staged and committed updates:

```bash
git add .
git commit -m "GIT-01: Updated index.html in feature branch"
```

---

### 5. Push Branch to Remote

Pushed the new branch to GitHub:

```bash
git push -u origin feature-update
```

---

### 6. Merge Branch into Main

* Switched back to the main branch:

```bash
git checkout main
```

* Merged the feature branch into main:

```bash
git merge feature-update
```

* Pushed updated main branch:

```bash
git push origin main
```

---

### 7. Verify Commit History

Commit history was verified using:

```bash
git log --oneline --graph --all
```

This confirms:

* Initial commit
* Changes in feature branch
* Successful merge into main

---

📸 Output:

![Initial Commit](./assets/git-01-1.png)

![Branch Merge](./assets/git-01-2.png)

---

## ✅ Outcome

* Successfully initialized a Git repository
* Created and committed `index.html`
* Implemented branching workflow
* Merged changes from feature branch into main
* Connected and pushed code to GitHub

---

## 🧠 Key Learnings

* Real-world Git workflow using actual project files
* Importance of branching for safe development
* Difference between staging and committing
* How merging integrates changes
* Understanding Git history and tracking

---

## 🚀 Conclusion

This task demonstrates the foundational Git workflow used in real-world development environments. Mastering these basics is essential for collaboration, version control, and maintaining a clean project history.

---
