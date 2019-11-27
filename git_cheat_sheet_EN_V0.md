# GIT CHEAT SHEET

## CREATE

Clone an existing repository

```sh
$ git clone ssh://user@domain.com/repo.git

```

Create a new local repository

```sh
# git init
```

## Local Changes

Changed files in your working directory

```sh
git status
```

Changes to tracked files

```sh
$ git diff
```

Add all current changes to the next commit

```sh
$ git add .
```

Add some changes in <file> to the next commit

```sh
$ git add -p <file>
```

Commit all local changes in tracked files

```sh
$ git commit -a
```

Commit previously staged changes

```sh
$ git commit
```

Change the last commit<br>

> Don't amend published commits!

```sh
$ git commit --amend
```

## COMMIT HISTORY

Show all commits, starting with newest

```sh
$ git log
```

Show changes over time for a specific file

```sh
$ git log -p <file>
```

Who changed what and when in <file>

```sh
$ git blame <file>
```

## BRANCHES & TAGS


List all existing branches

```sh
$ git branch -av
```

Switch HEAD branch

```sh
$ git checkout <branch>
```

Create a new branch based on your current head

```sh
$ git branch <new-branch>
```

Create a new tracking branch based on a remote branch

```sh
$ git checkout --track <remote/branch>
```

Delete a local branch

```sh
$ git branch -d <branch>
```

Mark the current commit with a tag

```sh
$ git tag <tag-name>
```

## UPDATE & PUBLISH

List all currently configured remotes

```sh
$ git remote -v
```

Show information about a remote

```sh
$ git remote show <remote>
```

Add new remote repository, named <remote>

```sh
$ git remote add <shortname> <url>
```

Download all changes from <remote>, but don't integrate into HEAD

```sh
$ git fetch <remote>
```

Download changes and directly merge/integrate into HEAD

```sh
$ git pull <remote> <branch>
```

Publish local changes on a remote

```sh
$ git push <remote> <branch>
```

Delete a branch on the remote

```sh
$ git branch -dr <remmote/branch>
```

Publish your tags

```sh
$ git push --tags
```

## MERGE & REBASE

Merge <branch> into your current HEAD

```sh
$ git merge <branch>
```

Rebase your current HEAD onto <branch>

> Don't rebase published commits!

```sh
$ git rebase <branch>
```

Abort a rebase

```sh
$ git rebase --abort
```

Continue a rebase after resolving conflicts

```sh
$ git rebase --continue
```

Use your configured merge tool to solve confilicts

```sh
$ git mergetool
```

Use your editor to manually solve conflicts and (after resolving) mark files as resolved

```sh
$ git add <resolved-file>
$ git rm <resolved-file>
```

## UNDO

Discard all local changes in your working directory

```sh
$ git reset --hard HEAD
```

Discard local changes in a specific file

```sh
$ git checkout HEAD <file>
```

Revert a commit (by producing a new commit with contrary changes)

```sh
$ git revert <commit>
```

Reset your HEAD pointer to a previous commit...and discard all changes since then

```sh
$ git reset --hard <commit>
```

...and preserve all changes as unstaged changes

```sh
$ git git reset <commit>
```

...and preserve uncommitted local changes

```sh
$ git reset --keep <commit>
```
