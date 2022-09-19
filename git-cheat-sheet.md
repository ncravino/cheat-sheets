# Git Cheat Sheet

## Branches

### Create branch
- `git branch new-branch` create branch but don't change current branch
- `git branch -M new-branch` create new-branch and move to new-branch
- `git checkout -b new-branch` using the current HEAD as source
- `git checkout -b new-branch another-branch` using another-branch as source

### Delete branch
- `git branch -d branch-to-delete` removes only if mergeable state is ok
- `git branch -D branch-to-delete` removes anyway

### Rename branch

After `git checkout branch-to-rename`:
- `git branch -m branch-to-rename` rename branch

## Squash multiple commits

1) `git checkout the-branch`
2) `git log`
3) find the SHA of the commit previous to the one you want
4) `git rebase -i SHA-sha-sha`
5) change from pick to squash
6) modify the messages if you want
6) `git rebase --continue`

## Divide a commit into multiple commits

1) `git checkout the-branch`
2) `git log`
3) find the commit SHA
4) `git rebase -i the-commit-sha`
5) replace `pick` with `edit`
6) `git reset HEAD~` 
7) the modified files are now waiting to be commited, so do it
8) `git rebase --continue`
9) force push the branch

## Change previous commit

1) `git checkout the-branch`
2) `git reset head~`
3) do your changes
4) commit the final change with:
`git commit --amend --no-edit`

(remove `--no-edit` to allow for a new message)
