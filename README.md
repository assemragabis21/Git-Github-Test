# Lab Objectives

The main objectives of this lab were:

* Create **four commits** while modifying a Python file.
* **Delete the last two commits** from the Git history.
* **Create a new commit after deleting commits**.
* **Amend the last commit** by modifying the file and changing the commit message.
* Understand the concept of **git revert** and how it safely undoes changes.
* **Bonus:** revert commits from earlier in the history.

---

# Execution Steps

## 1. Repository Setup

First, the repository was connected to GitHub using SSH and the remote origin was added.

```
git remote add origin git@github.com:assemragabis21/Git-Github-Test.git
git push -u origin main
```

An SSH key was also generated to authenticate with GitHub.

```
ssh-keygen -t rsa -C "test@gmail.com"
```

---

# 2. File Creation and Initial Changes

A Python file named **lab1.py** was created and edited multiple times using the terminal editor.

```
nano lab1.py
```

After creating the file, it was added to the repository and committed.

```
git add lab1.py
git commit -m "initial commit"
```

---

# 3. Creating Four Commits

The file **lab1.py** was modified several times to simulate development changes.
Each modification was committed separately to build a commit history.

Example process:

```
nano lab1.py
git add lab1.py
git commit -m "First commit change"
```

Then repeated again:

```
git add lab1.py
git commit -m "Second commit change"
```

```
git add lab1.py
git commit -m "Third commit change"
```

```
git add lab1.py
git commit -m "Fourth commit change"
```

At this point the repository had **four commits in the history**.

---

# 4. Deleting the Last Two Commits

To remove the last two commits from the history, the following command was used:

```
git reset --hard HEAD~2
```

This command moves the **HEAD pointer two commits back**, effectively deleting the last two commits from the local history.

After running this command, the repository returned to the state before those two commits were created.

To confirm the result, the commit history was checked:

```
git log --oneline
```

---

# 5. Creating a New Commit After Deletion

After deleting the last two commits, the file **lab1.py** was modified again.

```
nano lab1.py
```

The changes were then staged and committed with the required message:

```
git add lab1.py
git commit -m "commit after deletion"
```

This created a **new commit on top of the shortened history**.

---

# 6. Amending the Last Commit

Next, the file was edited again and the text **"lab Done"** was added at the end of the file.

```
nano lab1.py
```

Instead of creating a new commit, the previous commit was **amended** so that the changes became part of the last commit.

```
git commit --amend -m "finish"
```

This command performs two actions:

1. Adds the new modifications to the previous commit.
2. Changes the commit message to **"finish"**.

The updated history was verified using:

```
git log --oneline
```

---

# 7. Pushing Changes to GitHub

After finishing the modifications locally, the changes were pushed to the remote repository.

```
git push origin main
```

---

# 8. Reverting Commits (Self Study)

The **git revert** command was used to undo changes from previous commits.

Example commands used:

```
git revert HEAD~1
```

Later, a specific commit was also reverted using its commit hash.

```
git revert a16841f
```

After reverting the changes, the history was checked again:

```
git log --oneline
```

---

# What is git revert?

`git revert` is a **safe method to undo changes in Git**.

Unlike `git reset`, which removes commits from the history, **git revert keeps the history intact**.

It works by:

1. Taking the changes introduced in a specific commit.
2. Creating a **new commit that reverses those changes**.

This makes it the safest method when working on **shared repositories** because it does not rewrite commit history.

---

# Bonus Task

As part of the bonus task, commits from earlier in the history were reverted to practice undoing previous changes while maintaining a consistent Git history.

---

# Git Commands Practiced in This Lab

During this lab the following Git commands were used:

* `git add`
* `git commit`
* `git commit --amend`
* `git reset --hard`
* `git revert`
* `git log`
* `git push`
* `git status`

---
