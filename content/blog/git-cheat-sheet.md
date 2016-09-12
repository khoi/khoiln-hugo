+++
date = "2016-09-10T09:11:26+07:00"
draft = false
title = "Common Git Usages"

+++


### Change the last commit message

```bash
git commit --amend
#Then follow the instructions
```

### Append some changes to the last commit

```bash
git add .
git commit --amend
```

### Accidentally commited something to the wrong branch

```bash
#undo the last commit, but leave things unchaged
git reset HEAD~ --soft
git add .
git stash
#move to your correct branch
git checkout new-branch
git stash pop
git commit -am "Commit message"
```

### Undo commits

```bash
git reset --hard HEAD # Reset to the last commit and remove all changes
git reset HEAD # Undo the last commit, keep changes 

git reset --hard HEAD~2 # Undo last 2 commits, remove all changes
git reset HEAD~2 # Undo last 2 commit, keep changes

```
