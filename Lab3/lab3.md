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
