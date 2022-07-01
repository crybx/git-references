

----------------------------------------------------
## UNCOMMON BUT USEFUL COMMANDS


### interactive rebase

`git rebase -i HEAD~3`

Follow the prompts to wield the power to rewrite history.


### throw away changes that aren't checked in.

Warning! You can lose code doing this.

`git reset --hard`


### create a patch

`git format-patch <branch_name> --stdout > ~/a-handy-patch-name.patch`

### reset author for all commits in branch (SHAs will be updated, date for all commits will be changed to now)

`git rebase -r --root --exec "git commit --amend --no-edit --reset-author"`

### reset author for all commits in branch, but keep the old dates (SHAs will still be updated)

`git rebase -r --root --exec "git commit --amend --no-edit --author='crybx <crybx@users.noreply.github.com>'"`

then

`git rebase --root --committer-date-is-author-date`

----------------------------------------------------
## BRANCH HYGIENE


### push a local only branch remote

`git push --set-upstream <remote> <branch_name>`


### delete a local branch

`git branch -D <branchName>`


### delete a remote branch

`git push origin --delete <branch_name>`

Don't use the prefix `origin/` within `<branch_name>`.


### clean up local list of available remote branches

`git remote prune origin`


### set an upstream branch

`git branch -u <remote>/<branch_name>`


### force a local branch to match a remote branch after diverging:

Warning! You can lose code doing this.

```
git fetch origin
git reset --hard origin/<branch_name>
```

### force remote commit history to match your local history:

**!!! Very destructive !!!**

Relevant if you're interested in [removing sensitive data from a repository](https://docs.github.com/en/github/authenticating-to-github/removing-sensitive-data-from-a-repository).

```
git push origin --force --all
```

----------------------------------------------------
## DEALING WITH REMOTE URLS


### show all remote destinations and their URLs

`git remote -v`


### add a remote

`git remote add <remote_name> <url>`

Example 1 (this git-references repository):

`git remote add origin git@github.com:crybx/git-references.git`

Example 2 (foo.git on a Linux server):

`git remote add origin ssh://<username>@<serverurl>/foo.git`


### remove a remote

`git remote rm <remote_name>`


### update an existing remote's url

`git remote set-url origin <new_origin_url>`
