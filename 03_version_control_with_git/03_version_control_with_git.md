## Setup

### Installation: Git

Before using Git, you need to install it on your system. Installation methods vary depending on your operating system. Here are the links for installation instructions on the official website.

#### macOS

[Installation instructions: macOS](https://git-scm.com/downloads/mac)

#### Linux

[Installation instructions: Linux](https://git-scm.com/downloads/linux)

#### Windows

[Installation instructions: Windows](https://git-scm.com/downloads/win)

#### Configuring Identity for Git

Before using Git on your system, the first step is to configure your Git username and email address. This ensures that Git associates your identity with every commit you make.

In the terminal, 
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

In this unit, we'll learn how to use Git to track changes, manage collaboration, and maintain a history of all modifications. Git helps researchers keep versions of their work, making it easier to collaborate and revert to previous states when needed. This unit covers essential Git commands for tracking changes, committing updates, and reverting to older versions. It also includes instructions on using Git within VS Code for an easier workflow.  

## Tracking Changes  

Git helps track changes in your project by monitoring file modifications. You can check the status of your changes, add files to be included in the temporary staging area, and unstage them if needed. This section covers the basic commands for tracking changes and how to use the VS Code interface for Git.  

The temporary staging area holds changes before they are committed (saved permanently in the repository’s history). You can stage modified files, newly created files, and deleted files.

| Code                | Description                                             | VS Code GUI |
|---|---|---|
| `git init`            | Initialize a new Git repository in the current directory | Click **Source Control (Ctrl + Shift + G)** → Click **"Initialize Repository"** |
| `git status`          | Show the status of changes in the working directory      | Click **Source Control (Ctrl + Shift + G)** → See the file changes |
| `git add file1.txt`   | Stage `file1.txt` for commit                             | Click **➕ (plus) icon** next to the file in **Source Control** |
| `git add .`          | Stage all modified and new files                         | Click **➕ (plus) icon** next to each file OR Click **"Stage All Changes"** |
| `git reset file1.txt` | Unstage `file1.txt`                                      | Click **➖ (minus) icon** next to the file to move it back to "Changes" |

**Exercises**  

1. Initializing a Git repository (Should be done only once in the beginning)
   1. Open a new folder for your project.  
   2. Initialize a Git repository in this folder.  
   3. Check the status of the repository using `git status`.  

2. Tracking files and changes (check status before and after staging)
   1. Create and stage `experiment_1.txt`. 
   2. Create `experiment_2.txt` and `experiment_3.txt`. Stage both the files together.
   3. Unstage the `experiment_3.txt` and check the status.
   4. Delete `experiment_3.txt` and check the status.

## Committing Changes and Viewing History 

The staged changes are still only temporary. To create a more permanent snapshot of your project, you need to save the staged changes using a `commit`. A commit records a snapshot of your project at a particular time described by a `commit message`. Essentially, your project will be a series of commits and the changes committed can be accessed via commit history.  

In Git, each commit has a unique **commit hash**, which is a long ID that helps track changes. Commits are saved in order, creating a history of changes in the project. You can see past commits using `git log`, which shows the commit hash, message, and time of each commit. **Typical workflow would be that you *stage* any change you make to the files in the temporary staging area and once you are happy with the changes you have made, you *commit* them**. The point where you **stage** and **commit** are up to you. This section covers committing changes, adding messages, and viewing commit history.

| Code | Description | VS Code GUI |
|---------|-------------|-------------|
| `git add f1.txt f2.txt` | Stage specific files for commit | Click **➕ (plus) icon** next to the files in **Source Control** |
| `git commit -m "Commit message"` | Commit staged files with a message | Click **✔ (checkmark) icon**, enter commit message, and press Enter |
| `git add .` | Stage modifications of all files | Click **➕ (plus) icon** next **Changes** |
| `git commit -am "Commit message"` | Stage and commit all modified files in one step | Click **"Stage All Changes"**, then **✔ (checkmark) icon** |
| `git log` | View the full commit history of the repository | **N/A** (Command-line only) |
| `git log --oneline` | View a compact version of the commit history | **N/A** (Command-line only) |
| `git log -2` | Display the last two commits | **N/A** (Command-line only) |
| `git diff` | Compare the working directory with the last commit | Click on the file in **Source Control** and check the inline diff |
| `git diff <commit-hash1> <commit-hash2>` | Compare two specific commits | **N/A** (Command-line only) |

**Exercises**  

1. Committing changes  
   1. Commit creation of `experiment_1.txt` and `experiment_2.txt` with message "create files".    
   2. Add some text into `experiment_1.txt` and commit with message "add data to exp 1".
   3. Add some text into `experiment_2.txt`, modify `experiment_1.txt` and commit the changes with a suitable commit message. 
   4. Modify both the files. Stage and commit in one step.

2. View history  
   1. View the full commit history of the repository.
   2. Check a compact version of the commit history.
   3. Display the history of the last three commits. Make a few more commits if necessary.

3. Comparing differences between commits
   1. Compare the differences between the most recent commit and the working directory.
   2. Compare two specific commits.

## Reverting to Older Versions  

Git allows you to go back to a previous version of your work if needed. There are several ways of doing this. In this section, you will use one such method where you undo the changes made in a particular commit without losing the commit history. This is where having descriptive commit messages can be useful in identifying which version you want to go back to. In this section, we cover reverting changes using Git using `revert`.  

| Code                      | Description                                         | VS Code GUI |
|---|---|---|
| `git revert HEAD`            | Creates a new commit that undoes the latest commit | NA |
| `git log --oneline`          | Shows commit history in a short format             | NA |
| `git revert <commit-hash>`   | Creates a new commit that undoes only the specified commit | NA |

**Exercises**  

1. Reverting the latest commit  
   1. Modify `experiment_1.txt` again and commit the changes.  
   2. Use `git log --oneline` to view the commit history.  
   3. Revert the latest commit using `git revert HEAD`.  
   4. Check the status and commit history to confirm the revert.  

2. (Optional) Reverting a specific commit  
   1. Modify and commit changes to `experiment.txt` a few times.  
   2. Use `git log --oneline` to identify a specific commit to undo.  
   3. Use `git revert <commit-hash>` to undo only that commit. Were you able to do this smoothly? Or did you get any conflicts? If so, why? 
   4. Check the commit history again to verify the changes.