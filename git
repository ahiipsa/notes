
# Revert merge after *git pull*

```
git reset --merge
```

# Undo local changes


If you want to revert changes made to your working copy, do this:

```
git checkout .
```

If you want to revert changes made to the index (i.e., that you have added), do this. Warning this will reset all of your unpushed commits to master!:

```
git reset
```

Revert a change that you have committed, do this:

```
git revert ...
```

Untracked files:

```
git clean -f 
```

Untracked directories:

```
git clean -d
```

# Helpers

Get current tags:

```
git tag --contains
```

Get list of tag sorted by version (reverse):
```
git tag -l --sort="-version:refname"
```

Get list no-merged remote branches 
```
git branch -r --no-merged origin/master
```

Get list branch with "owner"
```
git for-each-ref --sort=-committerdate --format='%(committerdate)%09%(refname)%09%(authorname)' refs/remotes/origin/ | grep -e ".$@"
```

Is branch merged to master
```
git co master && git branch --merge | grep "branch-name"
```

Prune local tracking branches that do not exist on remote anymore
```
git remote prune origin
```

Remove all your local branches
```
git branch | grep -v "master" | xargs git branch -D 
```

Remove all remote-tracking branchs
```
git branch -r | grep -v "master" | xargs git branch -rd
```

Remove all merged branches from origin
```
git branch -r --merged | grep -v 'master' | sed 's/origin\///g' | xargs git push --delete origin
```
