# Git Cheat Sheet

Further reference documentation:

https://git-scm.com/docs

## Git Checkout

`git checkout -b new_branch` - Checkout of a new branch

`git checkout master -- path/to/file` - Checkout of file on master

`git checkout -` - Git checkout the previous branch again

## Git Commit

`git commit --amend` - Git commit ammend

`git commit --amend --no-edit -a` - Git commit ammend without editing the comment

## Git Stage

`git add` - Stage files: 

`git add -p` - Interactively stage files

## Git Reset

`git checkout HEAD -- my-file.txt` - Reset a single file

## Git Investigate

`git show branch:file` - Shows the file within the branch

`git show HEAD` - Shows the diff of the last commit

## Git Branch Manipulation

`git cherry-pick <commitid>` - Cherry picks a commit into the current branch

`git rebase -i HEAD~3` - Rebases the three previous commits of HEAD

## Git Commit Manipulation

`git rebase --interactive 'asdf1234^'`

`git commit --all --amend --no-edit`

`git rebase --continue`

## Git Working Trees

`git worktree add`

https://git-scm.com/docs/git-worktree

## Git Upstream Configuration

`git remote show origin`

## Git Bisect

`git bisect start`

`git bisect bad <commitid>`

`git bisect good`

`git bisect bad`

`git bisect reset`

`git bisect start <commitid> <commitid>`
