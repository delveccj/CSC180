Here's a **simple tutorial on Git**, focusing on the basics of how Git works, how to use commits, and how to leverage Git’s history to find changes. This will give learners a strong foundation to understand the core concepts and power of version control with Git.

---

## **Git Basics Tutorial**

### 1. **What is Git?**
- **Git** is a **distributed version control system** that allows multiple people to collaborate on a project by tracking changes, creating a history of changes, and enabling easy collaboration.
- In Git, every time you save your work (by making a **commit**), you create a **snapshot** of your project at that moment in time. These snapshots can be revisited, compared, and even restored.

---

### 2. **Core Concepts**
Here are some basic concepts that will guide our understanding:

- **Repository (repo)**: A Git repository is where your project’s files and its history (commits) are stored.
- **Commit**: A commit is a snapshot of the changes you made to your files at a specific point in time.
- **Branch**: A branch is a separate line of development in a Git repository. The default branch in Git is called `main` or `master`.
- **HEAD**: This is a reference to the most recent commit on the current branch.

---

### 3. **Basic Git Workflow**

Let’s walk through a basic Git workflow, focusing on how to create a repository, make commits, and view the history.

#### **Step 1: Initialize a Git Repository**
To start tracking changes, you need to initialize Git in your project.

1. Create a new directory for your project:
   ```bash
   mkdir my-git-project
   cd my-git-project
   ```

2. Initialize a new Git repository:
   ```bash
   git init
   ```
   This creates a `.git` folder inside your project, which tracks all your changes.

#### **Step 2: Make Changes and Commit**
Now, let's make some changes and commit them to the repository.

1. Create a new file called `hello.txt`:
   ```bash
   echo "Hello, World!" > hello.txt
   ```

2. Check the status of your repository:
   ```bash
   git status
   ```
   You’ll see that `hello.txt` is an **untracked file**.

3. Add the file to Git's tracking system:
   ```bash
   git add hello.txt
   ```

4. Commit the change:
   ```bash
   git commit -m "Added hello.txt with Hello, World!"
   ```
   - **`-m`** allows you to add a commit message describing the change.
   - You just took a snapshot of the project at this point in time.

#### **Step 3: View Git History**
You can view all previous commits and changes using `git log`.

1. View the commit history:
   ```bash
   git log
   ```

   You'll see something like this:
   ```
   commit eeb3f8a3213d3fe16bb13af57f1f4d3b5e85b9b7 (HEAD -> main)
   Author: Your Name <you@example.com>
   Date:   Tue Sep 7 12:34:56 2023 +0000

       Added hello.txt with Hello, World!
   ```

---

### 4. **Making More Changes**
Let’s make another change and see how Git tracks the difference.

1. Edit `hello.txt`:
   ```bash
   echo "Hello, Git!" >> hello.txt
   ```

2. Check the status again:
   ```bash
   git status
   ```
   You’ll see that Git recognizes a change in `hello.txt`.

3. Commit the change:
   ```bash
   git add hello.txt
   git commit -m "Updated hello.txt to include a greeting for Git"
   ```

---

### 5. **Finding and Viewing Changes**
Here’s where Git’s history becomes useful. Let’s say you want to see all the changes made to `hello.txt`.

1. **View the history of changes for a specific file**:
   ```bash
   git log -- hello.txt
   ```
   This shows the history of all commits that affected `hello.txt`.

2. **View differences between commits**:
   You can see exactly what changed between commits using the `git diff` command.

   - View changes in the working directory (before commit):
     ```bash
     git diff
     ```

   - View changes between two commits:
     ```bash
     git diff HEAD^ HEAD
     ```

   This shows the difference between the latest commit (`HEAD`) and the one before it (`HEAD^`).

---

### 6. **Recovering Things You Thought Were Gone**
Git allows you to **recover "deleted" work** by going back in history and retrieving old snapshots (commits). This is one of Git's greatest strengths.

#### Example: Recovering a Deleted File
1. Let’s delete `hello.txt`:
   ```bash
   rm hello.txt
   ```

2. Check the status:
   ```bash
   git status
   ```
   Git will show that `hello.txt` has been deleted.

3. To recover `hello.txt`, use:
   ```bash
   git checkout HEAD -- hello.txt
   ```

   This command restores the last committed version of `hello.txt` from Git’s history.

#### Example: Reverting to a Previous Commit
If you made a mistake and want to go back to an earlier version of your project:

1. First, find the commit hash of the version you want to revert to:
   ```bash
   git log
   ```

2. Once you have the hash, you can reset your repository to that point:
   ```bash
   git reset --hard <commit-hash>
   ```

   This resets your project to the exact state it was in at that commit.

---

### 7. **Conclusion: Key Git Takeaways**
- **Commits are snapshots**: Every commit is a snapshot of your project at a specific point in time.
- **Nothing is truly lost**: Changes can always be recovered by going back through Git's history, even if files are deleted or overwritten.
- **Git tracks everything**: Git makes it easy to view, compare, and recover changes made over time, making it an invaluable tool for collaborative and personal projects.

---

### Additional Commands:
- **View a single commit in detail**:
  ```bash
  git show <commit-hash>
  ```

- **Create a new branch**:
  ```bash
  git checkout -b <branch-name>
  ```

- **Merge a branch into the main branch**:
  ```bash
  git checkout main
  git merge <branch-name>
  ```

---

This tutorial should give your students a solid understanding of Git’s core concepts, especially how **commits** work and how to **leverage history** to recover or view changes.

Git is dangerous.  There have been several instances where sensitive information was **accidentally committed to a Git repository**, deleted later, but still exposed through **Git history**. This happens because even if a file is removed or modified in a later commit, **Git retains all changes in its commit history**, allowing someone to retrieve the original content unless the history is explicitly rewritten.  Imagine if you store this information on your companie's internal github because, of course, its safe.

### **Example 1: GitHub API Key Exposure in Git History (2018)**

#### **What Happened:**
- In 2018, a software developer working on a project accidentally committed **GitHub API keys** to a private repository.
- The keys were removed in a subsequent commit, but because Git keeps a record of all previous versions of a file, the keys remained in the **commit history**.
- Hackers scanning public GitHub repositories for exposed API keys found the keys in the **Git history**, despite the developer having "removed" them in the current version of the repository.

#### **Impact:**
- The attackers used the API keys to access the developer's GitHub account and repositories, potentially gaining access to other sensitive code, intellectual property, or other private data.
- This is a common vulnerability when developers unknowingly expose sensitive information like API keys, database passwords, or AWS credentials.

#### **Prevention**:
- **GitHub’s Secret Scanning**: GitHub has since added **automated secret scanning** that alerts repository owners when they commit sensitive information like API keys.
- **`git filter-branch` and `BFG Repo-Cleaner`**: To completely remove sensitive data from Git history, tools like `git filter-branch` or **BFG Repo-Cleaner** can be used to rewrite Git history and permanently remove sensitive data from all commits.

---

### **Example 2: Uber's AWS Keys Exposed in Git History**

#### **What Happened**:
- In the **Uber 2016 breach** mentioned earlier, Uber initially **removed** the AWS credentials from the public repository after realizing the mistake.
- However, the credentials were still **accessible in the Git history** of the repository. Hackers used this fact to retrieve the AWS credentials, gaining access to Uber’s sensitive data.

#### **Impact**:
- The hackers gained access to Uber’s **Amazon S3 buckets**, which contained sensitive data on **57 million users** and **600,000 drivers**.
- The exposure happened even after Uber’s attempt to remove the credentials, simply because they existed in the history of the repository.

#### **Lessons Learned**:
- Even if sensitive information is deleted in the current version of the repository, **Git’s history keeps everything** unless explicitly rewritten.
- The correct approach would have been to use **history rewriting tools** like `git filter-branch` or BFG to scrub the entire history and force-push the cleaned version.

---

### **Example 3: Slack Tokens Exposed in Git History**

#### **What Happened**:
- In 2017, a developer accidentally committed a file containing **Slack API tokens** into a Git repository.
- After realizing the mistake, the developer quickly removed the file and committed the changes.
- However, the original commit containing the API token still existed in the **Git history**, making it possible for anyone with access to the repository to retrieve the sensitive token from earlier commits.

#### **Impact**:
- The token was used by unauthorized users to gain access to Slack's internal communication, potentially exposing sensitive messages and files.

#### **How It Could Have Been Prevented**:
- After realizing that sensitive information has been committed, it’s important to **rewrite the Git history** to **permanently remove the sensitive data**, not just remove it in a later commit.
- Tools like **BFG Repo-Cleaner** can help clean the Git history, and **revoking and rotating API keys** or tokens is necessary immediately after such exposure.

---

### **How to Prevent Sensitive Data in Git History:**

1. **Git Pre-Commit Hooks**: 
   - Use pre-commit hooks to automatically **prevent sensitive data from being committed** in the first place. Tools like **`pre-commit`**, **`git-secrets`**, or **`talisman`** can be used to block commits containing sensitive information like API keys, passwords, and other credentials.

2. **Remove Sensitive Data from Git History**:
   - If sensitive information has been committed, use tools like **`git filter-branch`** or **BFG Repo-Cleaner** to scrub it from the entire Git history.
   
   **Example**:
   ```bash
   # Using BFG to remove a file from history
   bfg --delete-files 'file_with_secrets.txt'
   
   # Clean Git history
   git reflog expire --expire=now --all && git gc --prune=now --aggressive
   ```

3. **Rotate Keys and Secrets**: 
   - If any sensitive information is exposed, immediately **revoke and rotate** the keys (e.g., API keys, AWS credentials) and ensure new keys are properly secured.

4. **Use Environment Variables**:
   - Instead of hardcoding secrets in the source code, use environment variables or secret management tools like **AWS Secrets Manager**, **Vault**, or **GitHub Secrets**.

---

### **Conclusion:**
These examples show how **critical information** like API keys and credentials can be accidentally committed to a Git repository and later exposed through **Git history**, even after the sensitive information is deleted in subsequent commits. To ensure sensitive data is properly removed, developers must rewrite the Git history and use tools that can prevent accidental exposure.
