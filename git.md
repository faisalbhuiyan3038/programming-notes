# Notes on Git

## Where is Our Code Stored in Git?

There are 4 main locations where our code lives in Git:

- Local directory: Where we actively edit files locally.
- The staging area: Temporary spot for holding changes for commiting.
- The local repository: Where we store commited changes locally.
- Remote repository: A server like Github for sharing and backing up code.

## Git Commands Explained

`git config`: Used to setup configurations like name, email id. Should be provided as soon as git is installed.

`git diff`: Shows differences between changes made on a file.

`git log`: See previous commits taken place in git project in reverse chronological order.

`git init`: Creates an empty .git folder in local working directory.

`git reset`: Used to undo the local changes that are made to the state of a git repo. Three forms: --soft, --mixed, --hard.

`git rebase`: Used to integrate changes from one branch to another.

Git commands move files across these locations.

First step is to clone a repo with `git clone`.

`git clone`: Files are copied from remote repository to local repository, complete with all its history.

`git checkout`: Files are copied from local repository to local working directory, where you edit your code.

`git add`: To stage a snapshot of the files to the staging area.

`git commit`: Takes a snapshot of the staging area and save s it to local repository.

When you are ready to collaborate with the team, you can `git push` to a remote repository in Github or Bitbucket or gitlab.

`git push -u origin master`: Here master is the branch name.

Collaboration in git is a two-way exchange. Use `git pull` to fetch changes from the remote repository and merges them to your local repository.

It combines two commands, `git fetch` which fetches the code from remote repo to local repo, and `git merge` which integrates these updates with your code.

`git status`: Can check for changes or untracked files in current working directory. Simply shows what is happening with git add and git commit.

## Switch Contexts

There are times when you need to switch context to fix a bug on another branch.

This is where you use `git checkout` or `git switch` comes in.

`git checkout master`: Means we are switching to master branch in local repo.

Allows you to switch between branches to work on specific features.

Allows to diverge from the main codebase to develop a new feature without impacting the main code.

Create a new branch with `git branch`.

`git branch vlrBranch`: Creates vlrBranch in repo.

`git branch -v`: Shows the current branch.

Switch to a branch with `git switch`.

Merge branches with `git merge` and resolving merge conflicts when changes overlap.

Branching allows isolated development and collaboration workflows.

## GUI

Some people use GUI like Github Desktop or SourceTree, which provides shortcuts and visual feedback that can help new users get familiar with git.
