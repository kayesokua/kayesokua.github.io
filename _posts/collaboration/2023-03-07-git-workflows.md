---
layout: post
title: Git Workflow Practices
summary: A summary of different git workflow practices and example commands for initializing a repository, updating a local repository, working on a new or existing feature, merging the feature branch into the main branch, and resolving conflicts
tag: collaboration
---

Git workflows offer a framework and set of principles for overseeing modifications to code, promoting collaboration, and enhancing code quality. Here is a brief explanation of how it appears on your terminal:

* TOC
{:toc}

## Centralized Workflow

The centralized workflow involves having a single, central repository that serves as the authoritative source of code. Developers clone this repository to their local machines to make changes, and push their changes back up to the central repository when they are ready to share them with others. [^1] [^2]

To initialize a new repository:

```terminal
$ git init
Initialized empty Git repository in /path/to/repo/.git/
$ git add .
$ git commit -m "Initial commit"
[master (root-commit) 99fa7d4] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
$ git push origin main
```

To update your local repository from the main:

```terminal
$ git pull
...
From https://github.com/your-repo
   5b5a8e6..bbf6a47  main       -> origin/main
Updating 5b5a8e6..bbf6a47
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

To update your local repository with the latest changes without merging:

```terminal
$ git fetch
remote: Enumerating objects: 12, done.
...
Unpacking objects: 100% (6/6), 580 bytes | 193.00 KiB/s, done.
From https://github.com/your-repo
   5b5a8e6..bbf6a47  main       -> origin/main
```

To work on a new or exisiting feature:

```terminal
$ git branch feature-branch
Switched to branch 'feature-branch'
$ git add myfile.txt
$ git commit -m "added new file"
$ git push origin feature-branch
...
# Go to github to create a pull request or:
$ hub pull-request -b develop -h feature-branch
...
$ git checkout feature-branch
```

To merge the feature branch into the main branch:

```terminal
$ git merge feature-branch
Updating f173d9d..6488e54
Fast-forward
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
```

Resolving conflicts through `git diff`

```terminal
$ git merge feature-branch
Auto-merging feature.txt
CONFLICT (content): Merge conflict in feature.txt
Automatic merge failed; fix conflicts and then commit the result.

$ git status
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   feature.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git diff feature.txt
<<<<<<< HEAD
This is the main branch.
=======
This is the feature branch.
>>>>>>> feature-branch

$ nano feature.txt  # Edit the file to resolve the conflict

$ git add feature.txt
$ git commit -m "Merge conflict resolution"
```

## Feature Branching using Gitflow

Feature branching is a strategy for managing code changes within a Git repository. It involves creating separate branches for each new feature or bug fix, making changes on those branches, and then merging them back into the main branch when they are ready.

To set-up the workflow (must install gitflow first, ex. `brew install git-flow`)

```terminal
$ git flow init
..
Which branch should be used for bringing forth production releases?
   - develop
   - main
Branch name for production releases: [main]

Which branch should be used for integration of the "next release"?
   - develop
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
```

To work on a feature from beginning to end:

```terminal
$ git flow feature start <feature-name>
Switched to branch '<feature-name>'
..
$ git add <files-to-change>
$ git commit -m "a description of changes"
$ git flow feature publish '<feature-name>'
...
$ git flow feature finish <feature-name>
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
Deleted branch feature-branch (was abc1234).
```

To release means deploying a bundle of features or fixes that have been thorougly tested:

```terminal
$ git checkout develop
$ git flow release start -F v 1.2.3
...
$ git add <files-to-commit>
$ git commit -m "description of changes"
...
$ git flow release finish <version-number>
$ git push origin master
$ git push origin develop
```

## Trunk-based Development

Trunk Based Development is a software development practice that emphasizes working on a single, shared branch of a Git repository. This approach is designed to minimize code integration problems. [^3]

```terminal
$ git clone <repository-url>
$ cd <repository-name>
..
$ git checkout -b develop
$ git push -u origin develop
```

To work on a feature from beginning to end:

```terminal
$ git checkout -b feature/<feature-name>
...
$ git add <files-to-change>
$ git commit -m "a description of changes"
$ git push -u origin feature/<feature-name>
$ git checkout develop
...
# Go to Github to create PR
...
$ git merge --no-ff feature/<feature-name>
$ git push origin develop
```

## Other Notes

A summary of other git commands I often use.[^4]

* `git fetch` to check the status of the remote repository
* `git rebase origin` to update local branch with changes from the remote repository
* `git revert` to create a new commit that undoes the changes made in a previous commit
* `git revert <commit-id>` to create a new commit that undoes the changes made in a previous commit
* `git reset`: to move all changes made after that commit back to unstaged
* `git reset --hard`: to discard all changes made after the commit
* `git stash` to temporarily save changes that are not ready to be committed
* `git stash apply n` to retrieve the most recent stash
* `git stash list` to get a list of stashes
* `git cherry-pick` to apply a specific commit from one branch to another

## Resources

[^1]: Atlassian. "Comparing Workflows". Atlassian Git Tutorials. Accessed on 2023-03-07.[https://www.atlassian.com/git/tutorials/comparing-workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/)
[^2]: Koch, Sam. "With GitFlow." Git Workflow. Accessed on 2023-03-07. [https://skoch.github.io/Git-Workflow/with-gitflow.html.](https://skoch.github.io/Git-Workflow/with-gitflow.html)
[^3]: Hammant, Paul. Trunk-Based Development Website. Accessed on 2023-03-07. [https://trunkbaseddevelopment.com](https://trunkbaseddevelopment.com)
[^4]: Atlassian. Atlassian Git Tutorials. Accessed on 2023-03-07.[https://www.atlassian.com/git](https://www.atlassian.com/git)
