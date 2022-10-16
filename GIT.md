#GIT

#Branch: A branch in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is master.


## The“master” branch in Git is not a special branch. It is exactly like any other branch. The only reason nearly every repository has one is that the git init command creates it by default and most people don’t bother to change it.


# How To Creating a New Branch??
```
    -$ git branch waledBranch
 ``` 
    
###It keeps a special pointer called HEAD.

## The git branch command only created a new branch — it didn’t switch to that branch. Next UP to see How Switch the branch ..


```
   -$ git checkout waledBranch
```


## the HEAD now poin at the waledBranch.


#HEAD pointing to a branch
You can easily see this by running a simple git log command that shows you where the branch pointers are pointing. This option is called --decorate.
```
    -$ git log --oneline --decorate
```





