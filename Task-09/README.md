# GIT-09 · Working with Remote Repositories and Collaboration

## 🎯 Objective

Learn how to connect a local repository to a remote repository, work with branches, and collaborate using Pull Requests.

---

## 📋 Requirements

* Create a local repository and push it to a remote
* Create a feature branch and commit changes
* Push branch to remote
* Create Pull Request
* Merge changes and sync locally

---

## 🛠️ Steps Performed

---

### 1️⃣ Initialize Local Repository

```bash
# Create project folder
mkdir git-09-demo
cd git-09-demo

# Initialize git
git init
```

---

### 2️⃣ Create Demo File

```bash
# Create index.html
echo "<h1>GIT-09 Demo</h1>" > index.html

# Stage and commit
git add .
git commit -m "HTML-09 : Initial commit"
```

📌 Output:

```
[main (root-commit) abc123] HTML-09 : Initial commit
 1 file changed, 1 insertion(+)
```

---

### 3️⃣ Connect to Remote Repository

```bash
# Add remote (replace with your repo URL)
git remote add origin https://github.com/your-username/git-09-demo.git

# Push to remote
git push -u origin main
```

📌 Output:

```
Branch 'main' set up to track 'origin/main'
```

---

### 4️⃣ Create Feature Branch

```bash
# Create and switch branch
git checkout -b feature/git-09-collab
```

📌 Output:

```
Switched to a new branch 'feature/git-09-collab'
```

---

### 5️⃣ Make Changes

```bash
# Update file
echo "<p>Feature added</p>" >> index.html

# Stage and commit
git add .
git commit -m "HTML-09 : Added feature content"
```

📌 Output:

```
[feature/git-09-collab def456] HTML-09 : Added feature content
 1 file changed, 1 insertion(+)
```

---

### 6️⃣ Push Feature Branch

```bash
git push -u origin feature/git-09-collab
```

📌 Output:

```
Branch 'feature/git-09-collab' set up to track 'origin/feature/git-09-collab'
```

---

### 7️⃣ Create Pull Request (GitHub UI)

* Go to repository
* Click "Compare & Pull Request"
* Add title and description
* Submit PR

---

### 8️⃣ Merge Pull Request

* Review changes
* Click "Merge Pull Request"
* Confirm merge

---

### 9️⃣ Pull Latest Changes Locally

```bash
# Switch to main
git checkout main

# Pull latest changes
git pull origin main
```

📌 Output:

```
Updating abc123..def456
Fast-forward
 index.html | 1 +
```

---

## ✅ Final Result

* Local repo connected to remote
* Feature branch created and pushed
* Pull Request created and merged
* Local main updated with remote changes

---

## 📚 Key Learnings

* `git remote` connects local to GitHub
* Feature branches isolate work
* Pull Requests enable collaboration and review
* Always sync local after merge

