# Git Cheat Sheet

Further reference documentation:

https://git-scm.com/docs

## Git Checkout

`git checkout -b new_branch` - Checkout of a new branch

`git checkout master -- path/to/file` - Checkout of file on master

`git checkout -` - Git checkout the previous branch again

`git checkout <commitid>` - Git checkout specific commit id

## Git Commit

`git commit --amend` - Git commit ammend

`git commit --amend --no-edit -a` - Git commit ammend without editing the comment

## Git Stage

`git add` - Stage files: 

`git add -p` - Interactively stage files

## Git Stash

`git stash` - Creates a stash

`git stash --all` - Adds all untracked files

`git stash list` - List all stashes

`git stash apply` - Applies the latest stash

`git stash apply stash@{0}` - Applies a specific stash

`git stash pop stash@{0}` - Pops a specific stash

`git stash pop` - Pops the last stash

`git stash show` - Shows the last stash

`git stash show -p` - Shows the content of the last stash

`git stash show -p stash@{0}` - Shows the content of a specific stash

`git stash branch new_branch stash@{2}` - Creates a branch from a stash

`git stash show --name-only` - Shows the modified files of a stash

`git stash -s stash@{0} -- <filename>` - Applies a stashed change from a particular file

`git restore -s stash@{1} -- src/main/java/Whateverfile.java` - Unstash a specific file from the stash

`git stash clear` - Deletes all stash entries

`git stash drop` - Drops the last stash entry

`git stash drop stash@{2}` - Drops a specific stash entry

## Git Push

`git push -f` - Does a force push

`git push --force-with-lease` - Checks the remote branch for changes before force push

## Git Reset

`git checkout HEAD -- my-file.txt` - Reset a single file

`git reset --hard head` - Reset branch to head

`git reset --hard origin/master` - Reset branch to master from origin

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
