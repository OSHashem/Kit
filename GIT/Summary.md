# Git Tutorial

## What is Git?

- **Definition**: Git is the most popular version control system worldwide. It records changes to code over time in a special database called a repository.
- **Benefits**: Eliminates the need for manual folder-based backups, which are slow and unscalable.
- **Types of Version Control**:
  - Centralized: All team members connect to a central server. Single point of failure if the server goes down.
  - Distributed: Every team member has a full copy of the project and its history on their machine. Allows local snapshots and direct synchronization.

## Why Git is Popular

- Free, open-source, super fast, and scalable.
- Operations like branching and merging are much faster than in other systems (e.g., Subversion, TFS).
- Used in over 90% of software projects globally.
- Essential skill for software developers.

## Ways to Use Git

### Command Line

- Fastest and often easiest method.
- Open terminal/command prompt and execute Git commands.

### Code Editors/IDEs

- Most modern editors (e.g., VS Code) have built-in Git support via source control panels.
- Extensions like GitLens provide additional features.

### Graphical User Interfaces

- Dedicated tools like GitKraken and Sourcetree.
- GitKraken is recommended for its design, cross-platform support, and integration with other tools.

## Installing and Configuring Git

### Installation

- Check installation: `git --version`
- Download from git-scm.com
- On Windows, use Git Bash instead of Command Prompt.

### Configuration

- Three levels: system, global, local.
- Set global settings: `git config --global user.name "Your Name"` and `git config --global user.email "your.email@example.com"`
- Configure end-of-line handling: `git config --global core.autocrlf true` (Windows) or `input` (Mac/Linux).

## Basic Git Workflow

### Creating a Repository

- Initialize: `git init` in project folder.
- Creates a hidden `.git` directory storing project history.

### Staging and Committing

- Modify files in working directory.
- Stage changes: `git add <file>` or `git add .`
- Commit: `git commit -m "Commit message"`
- View history: `git log`

### Staging Area (Index)

- Intermediate step between working directory and repository.
- Allows review of changes before committing.
- `git status` shows current state.

<!-- ## Branching and Merging
- Create branch: `git branch <branch-name>`
- Switch branches: `git checkout <branch-name>` or `git switch <branch-name>`
- Merge: `git merge <branch-name>`
- Resolve conflicts during merges.

## Working with Remote Repositories
- Clone: `git clone <repository-url>`
- Push changes: `git push`
- Pull changes: `git pull` -->

## Advanced Topics Covered

### Ignoring Files

- Use `.gitignore` file to exclude files/directories.
- Templates available at github.com/github/gitignore.

### Undoing Changes

- Restore from staging: `git restore --staged <file>`
- Discard local changes: `git restore <file>`
- Remove untracked files: `git clean -f`

### Viewing Changes

- `git diff`: Compare working directory with staging area.
- `git diff --staged`: Compare staging area with last commit.
- Use visual tools like VS Code for diffs.

### Commit History

- `git log`: View commit history.
- `git show <commit>`: View changes in a specific commit.

## Best Practices

- Commit often with meaningful messages.
- Use present tense verbs in commit messages.
- Keep commits focused on logically separate changes.
- Review staged changes before committing.

## Important Git Commands

Below is a list of key Git commands covered in the tutorial, along with brief explanations:

- **`git --version`**: Checks the installed version of Git on your system. Useful for verifying installation.
- **`git init`**: Initializes a new Git repository in the current directory, creating a `.git` folder to store version history.
- **`git status`**: Displays the state of the working directory and staging area, showing modified, staged, and untracked files.
- **`git add <file>`**: Stages changes in the specified file for the next commit. Use `git add .` to stage all changes.
- **`git commit -m "message"`**: Commits the staged changes to the repository with a descriptive message. Use `git commit -a` to commit all tracked changes without staging.
- **`git log`**: Shows the commit history of the repository, including commit IDs, authors, dates, and messages. Use `git log --oneline` for a concise view.
<!-- - **`git branch`**: Lists all branches in the repository. Use `git branch <name>` to create a new branch.
- **`git checkout <branch>`**: Switches to the specified branch. Use `git checkout -b <branch>` to create and switch to a new branch.
- **`git merge <branch>`**: Merges the specified branch into the current branch, combining their histories.
- **`git clone <url>`**: Creates a local copy of a remote repository from the given URL.
- **`git push`**: Uploads local commits to the remote repository. Specify branch with `git push origin <branch>`.
- **`git pull`**: Fetches and merges changes from the remote repository into the current branch. -->
- **`git config --global user.name "Name"`**: Sets the global username for commits.
- **`git config --global user.email "email"`**: Sets the global email for commits.
- **`git config --global core.editor "editor"`**: Sets the default text editor for commit messages (e.g., "code --wait" for VS Code).
- **`git diff`**: Shows differences between the working directory and the staging area.
- **`git diff --staged`**: Shows differences between the staging area and the last commit.
- **`git restore <file>`**: Discards changes in the working directory for the specified file, restoring it from the last commit.
- **`git restore --staged <file>`**: Unstages the specified file, removing it from the staging area.
- **`git clean -f`**: Removes untracked files from the working directory. Use `-d` to include directories.
- **`git show <commit>`**: Displays details of a specific commit, including changes made.
- **`git rm <file>`**: Removes the file from the working directory and stages the removal for commit.
- **`git mv <old> <new>`**: Renames or moves a file and stages the change.
- **`.gitignore`**: A file that specifies files and directories to ignore (not track) in the repository.

<!-- ## Conclusion
This tutorial provides a solid foundation for beginners to start using Git confidently. It emphasizes understanding the basic workflow and encourages learning both command-line and GUI tools. By mastering these fundamentals, developers can effectively manage code changes and collaborate on projects. -->
