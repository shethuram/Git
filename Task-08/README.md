### GIT-08 · Using Git Hooks for Automated Checks

**🎯 Objective:** Set up a Git hook to run scripts (like linters or tests) before commits are finalised.

---

**📋 Requirements:**

* Create a `pre-commit` hook in the `.git/hooks` directory
* Write a simple script (shell) to validate code
* Abort commit if validation fails
* Demonstrate outputs

---

## 🧠 Key Concepts

### 🔹 Linter

A **linter** is a tool that analyzes your code and detects:

* Syntax errors
* Bad practices
* Code style issues

👉 Example:

```js
console.log("debug")   // ❌ unwanted debug
var x = 10             // ❌ use let/const instead
```

✔️ Linters help enforce clean and consistent code.

---

### 🔹 Unit test

A **unit test** checks whether a small part of your code works correctly.

👉 Example:

```js
function add(a, b) {
  return a + b;
}
```

Unit test:

```js
add(2, 3) === 5  // ✅ pass
add(2, 2) === 5  // ❌ fail
```

✔️ Helps catch logical errors early.

---

## 🛠️ Steps Performed (VS Code + PowerShell)

---

### 1️⃣ Initial Setup

➡️ Create `index.html`

```html
<!DOCTYPE html>
<html>
<head>
  <title>Git Hooks Demo</title>
</head>
<body>
  <h1>Hello World</h1>
</body>
</html>
```

```bash
git add .
git commit -m "HTML-08 : Base version"
```

---

### 2️⃣ Create Pre-Commit Hook

➡️ Navigate to:

```
.git/hooks/
```

➡️ Create file:

```
pre-commit
```

---

### 3️⃣ Add Hook Script

```bash
#!/bin/sh

# Custom check
if grep -q "console.log" index.html; then
  echo "❌ Commit blocked: console.log found in index.html"
  exit 1
fi

echo "✅ Pre-commit checks passed"
exit 0
```

---

### 4️⃣ Make Hook Executable (Optional)

```bash
chmod +x .git/hooks/pre-commit
```

---

## 🧪 Adding ESLint (Linter Integration)

### 🧠 Understanding Rule Format 

ESLint rules follow this pattern:

```json
"rule-name": ["severity", options]
```

### 🔹 Severity Levels

| Value   | Meaning            | Effect                               |
| ------- | ------------------ | ------------------------------------ |
| "off"   | rule disabled      | no checks                            |
| "warn"  | warning only       | shows message, does NOT block commit |
| "error" | strict enforcement | ❌ fails lint → blocks commit        |

👉 In pre-commit hooks, using **"error"** ensures bad code stops the commit.

---


### 🔧 Common Linting Rules Added

* Enforced semicolons (`semi`)
* Enforced double quotes (`quotes`)
* Enforced consistent indentation (`indent`)
* Prevent unused variables (`no-unused-vars`)
* Enforced spacing before function parentheses

👉 These rules ensure clean, readable, and consistent code across the project.

### Step 1: Install ESLint

```bash
npm init -y
npm install eslint --save-dev
```

---

### Step 2: Initialize Config

```bash
npx eslint --init
```

---

### Step 3: Configure Rule

```json
{
  "rules": {
    "no-console": ["error", "always"],
    "indent": ["error", 2],
    "no-tabs": "error",
    "semi": ["error", "always"],
    "quotes": ["error", "double"],
    "no-trailing-spaces": "error",
    "space-before-function-paren": ["error", "always"]
  }
}
```

---

### Step 4: Update Hook with Linter

```bash
#!/bin/sh

echo "🔍 Running Linter..."

npx eslint .

if [ $? -ne 0 ]; then
  echo "❌ Linting failed. Fix errors before committing."
  exit 1
fi

# Additional custom check
if grep -q "console.log" index.html; then
  echo "❌ Commit blocked: console.log found"
  exit 1
fi

echo "✅ All checks passed"
exit 0
```

---

### 5️⃣ Test Failure Case

➡️ Add:

```html
<script>
console.log("debug");
</script>
```

```bash
git add .
git commit -m "HTML-08 : Added debug log"
```

❌ Commit blocked

---

### 6️⃣ Fix and Commit

➡️ Remove error and commit again

```bash
git add .
git commit -m "HTML-08 : Clean code"
```

✅ Commit successful

---

## 🏆 Why Git Hooks Matter

* Prevent bad code from entering repository
* Automatically enforce coding standards
* Catch issues early before pushing
* Maintain consistency across team

---

## Task output

![](screenshots/output.png)

---

## ⚙️ How It Works

```
Developer → git commit
        ↓
   pre-commit hook runs
        ↓
   Linter + checks execute
        ↓
   ❌ Fail → commit blocked
   ✅ Pass → commit allowed
```

---

## ⚠️ Notes

* Hooks are local (not pushed to GitHub)
* Must be named exactly `pre-commit`
* Exit code determines success/failure

---

## 🚀 Conclusion

Git hooks act as a safety net by enforcing rules before code enters the repository, ensuring better code quality and reducing bugs in collaborative environments.
