---
title: Changing Git Commit Message
comments: true
---

Git, as all we know, best practice for code versioning system. For me it became a lifesaving system. I want to share one of my particular experience about git.
You can change your git commit message if your message contains unclear, incorrect, or insensitive information. You can amend it locally and push a new commit with a new message to GitHub.

## If the commit only exists in your local repository:

– You can change the most recent commit message using the  git commit --amend command.


## Amending the message of older or multiple commit messages:

– Use the git rebase -i HEAD~n command to display a list of the last n commits in your default text editor.

```javascript
git rebase -i HEAD~3 # Displays a list of the last 3 commits on the current branch
```
It should look something like that:

```javascript
pick e499d89 First commit message
pick 0c39034 Second commit message
pick f7fde4a Change the commit message but push the same commit.

# Rebase 9fdb3bd..f7fde4a onto 9fdb3bd
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```
Replace pick with reword before each commit message you want to change.

```javascript
pick e499d89 first commit message
reword 0c39034 Better second commit
reword f7fde4a Changed commit message but push the same commit.
```

Save and close the commit list file.
Force-push the amended commits.

```javascript
git push --force
```