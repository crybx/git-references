[< Git References](README.md)

# REWRITE HISTORY

### interactive rebase

`git rebase -i HEAD~3`

Follow the prompts to wield the power to rewrite history.

### reset author for all commits in branch (SHAs will be updated, date for all commits will be changed to now)

`git rebase -r --root --exec "git commit --amend --no-edit --reset-author"`

### reset author for all commits in branch, but keep the old dates (SHAs will still be updated)

first run

`git rebase -r --root --exec "git commit --amend --no-edit --author='crybx <crybx@users.noreply.github.com>'"`

then run

`git rebase --root --committer-date-is-author-date`

then double-check your work before you force push the branch

`git show -n 13 -s --format=fuller`
