# GIT Documentation


## Introduction 
*  Welcome, I'll explain what **git** is in the beginning before getting into the specifics. You must first be familiar with how **git** functions and the on what does it depend it has. Git operates on a version control system (VCS), which keeps track of changes made to a file or group of files over time so that you can refer to specific versions in the future. You really need this system if you're a **designer** or **developer** because it simply enables you to roll back your files or even projects to their previous iterations, allowing you to compare changes and determine who made them.


## Branch
* A branch in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is master.


* The **master** branch in Git is not a special branch. It is exactly like any other branch. The only reason nearly every repository has one is that the git init command creates it by default and most people don’t bother to change it.


## How To Creating a New Branch?
```
    -$ git branch 'Branch_name'
 ``` 
    
* It keeps a special pointer called HEAD.

* The git branch command only created a new branch — it didn’t switch to that branch. Next UP to see How Switch the branch ..


```
   -$ git checkout 'Branch_name'
```


*  the HEAD now poin at the 'Branch_name'


* HEAD now pointing to a branch
* You can easily see this by running a simple git log command that shows you where the branch pointers are pointing. This option is called --decorate.

```
    -$ git log --oneline --decorate
```

## Merge
* is Git's way of putting a forked history back together again. The git merge command lets you take the independent lines of development created by git branch and integrate them into a single branch


## Merge types

* Fast Forward Merge

![Image](https://www.delftstack.com/img/Git/fastforward%20merge.jpg?ezimgfmt=rs:372x331/rscb5/ngcb5/notWebP)

* 3-way merge

![Image](https://www.w3docs.com/uploads/media/default/0001/03/e0f0e9e14db945c07e1fc0f3b2460ac19e0f738f.png)
