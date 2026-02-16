# Git

+ [Install](#install)
+ [Using Git](#using-git)
+ [View History](#view-history)
+ [Branches](#branches)

## Install
`Git` is a distributed `version control system (VCS)` — a tool that tracks changes to files (especially code) over time. To install `Git`, for `Windows` and `macOS`, open [https://git-scm.com/](https://git-scm.com/) and select the installation required. Once installed, check the version of `Git` that is installed on the system. To check the version of `Git` installed:

```shell
$ git --version
```

When using `Linux` to install `Git`:

```shell
$ sudo apt update
$ sudo apt install git
```

Once installed set the configuration:

```shell
$ git config --global user.name "Your Name"
$ git config --global user.email "you@example.com"
```

## Using Git
When creating a project, this project folder can be created into a `Git` project using the `init` command. This will create a hidden `.git` folder. That folder is the entire history database. The `.git` hidden folder can be viewed using the keyboard shortcut of: `Command` + `Shift` + `.` on macOS.

```shell
# Create an empty folder
$ mkdir my-project
$ cd my-project

# Turn the folder into a Git project
$ git init
# Set the name for the default branch e.g main: $ git config --global init.defaultBranch <name>
$ git config --global init.defaultBranch main
```

If a file is added to this folder, a snapshot of the change, can be made using the `add` command. This means: `"I want Git to track this change."`.

```shell
$ git add file.txt

# Or, all files that have changes:
$ git add .
```

The changes can then be committed to version control using the `commit` command followed by `-m` to add a commit message:

```shell
$ git commit -m "First version"
```

To check the status:

```shell
$ git status
```

To push the changes to an online repository, like `GitHub`, for collaboration and working within a team, the `git push origin` command can be used. This basically means: `"Upload my local commits to the online repository"`. Usually that online place is `GitHub` (but could also be `GitLab`, `Bitbucket`, etc.).

```shell
$ git push origin
```

So the full process to commit a change:

```shell
$ git status
$ git add .
$ git commit -m "This is an example commit message"
$ git push origin
```

When you connect your project to a remote repo, `Git` saves its address and calls it `origin` (a nickname). After creating a repo online, you link it once. Now `Git` knows where to upload.:

```shell
$ git remote add origin https://github.com/username/myproject.git
```

The `push` command to the `main` branch:

```shell
$ git push origin main

# Or, push to current branch (e.g. feature branch):
$ git push origin
```

So this means: `"Send my local main timeline to the server"`.

It is important on the first ever push:

```shell
$ git push -u origin main
```

The `-u` flag means: `Remember this connection so future pushes only need git push`. After this, `git push` is enough to push the changes to `origin`.

+ `commit` = save on your computer
+ `push` = save on the internet

## View History
To view the history of a project in version control, use the `log` command. This will be the timeline of the project:

```shell
$ git log
```

## Branches
A `branch` allows a copy of the `main` branch to be created so changes and updates can be made in isolation and then merged back into the main codebase when required/completed. To create a new branch, the `checkout` and `-b` flag is used:

```shell
$ git checkout -b "feature/branch-name-here"
```

This will create a new branch named: `feature/branch-name-here` and switch to this branch. Using `git status` will show the current branch we are on.

Once changes are completed, the branch can be merged back into the main code base using `git merge`. This joins another branch into your current branch. So we would checkout the `main` branch and then use `git merge` to merge the changes in.

```shell
# Checkout the main branch
$ git checkout main
# Get any recent changes on the main branch
$ git pull
# Merge changes from the feature branch into the main branch. The feature/branch-name-here branch is now inside main
$ git merge feature/branch-name-here

# Delete the feature/branch-name-here branch
$ git branch -D feature/branch-name-here
```
