# GIT Documentation

## Introduction 
*  Welcome, I'll explain what **git** is in the beginning before getting into the specifics. You must first be familiar with how **git** functions and the on what does it depend it has. Git operates on a version control system (VCS), which keeps track of changes made to a file or group of files over time so that you can refer to specific versions in the future. You really need this system if you're a **designer** or **developer** because it simply enables you to roll back your files or even projects to their previous iterations, allowing you to compare changes and determine who made them.

#### Installing on macOS 

 There are several ways to install Git on a Mac. The easiest is probably to install the Xcode Command Line Tools. On Mavericks (10.9) or above you can do this simply by trying to run git from the Terminal the very first time.

    ```$ git --version```

If you don’t have it installed already, it will prompt you to install it.
If you want a more up to date version, you can also install it via a binary installer. A macOS Git installer is maintained and available for download at the Git website, at [download on mac](https://git-scm.com/download/mac.)

## Getting a Git Repository

##### You typically obtain a Git repository in one of two ways:
1. You can take a local directory that is currently not under version control, and turn it into a Git repository, or
2. You can clone an existing Git repository from elsewhere.

* In either case, you end up with a Git repository on your local machine, ready for work.

##### Initializing a Repository in an Existing Directory
* If you have a project directory that is currently not under version control and you want to start controlling it with Git, you first need to go to that project’s directory. If you’ve never done this, it looks a little different depending on which system you’re running:

```$ cd /Users/user/my_project```

#### and type:

```$ git init```

* This creates a new subdirectory named .git that contains all of your necessary repository files — a Git repository skeleton. At this point, nothing in your project is tracked yet. See Git Internals for more information about exactly what files are contained in the .git directory you just created.

* If you want to start version-controlling existing files (as opposed to an empty directory), you should probably begin tracking those files and do an initial commit. You can accomplish that with a few git add commands that specify the files you want to track, followed by a git commit:
```
$ git add *.c
$ git add LICENSE
$ git commit -m 'Initial project version'
```
* We’ll go over what these commands do in just a minute. At this point, you have a Git repository with tracked files and an initial commit.

## Sharing and Updating Projects


### git fetch

##### Name
git-fetch - Download objects and refs from another repository



#### SYNOPSIS
```
git fetch [<options>] [<repository> [<refspec>…​]]
git fetch [<options>] <group>
git fetch --multiple [<options>] [(<repository> | <group>)…​]
git fetch --all [<options>]
```
### DESCRIPTION 
Fetch branches and/or tags (collectively, "refs") from one or more other repositories, along with the objects necessary to complete their histories. Remote-tracking branches are updated.

By default, any tag that points into the histories being fetched is also fetched; the effect is to fetch tags that point at branches that you are interested in. This default behavior can be changed by using the --tags or --no-tags options or by configuring remote.```<name>```.tagOpt. By using a refspec that fetches tags explicitly, you can fetch tags that do not point into branches you are interested in as well.

git fetch can fetch from either a single named repository or URL, or from several repositories at once if ```<group>``` is given and there is a remotes.```<group>``` entry in the configuration file. 

When no remote is specified, by default the origin remote will be used, unless there’s an upstream branch configured for the current branch.

The names of refs that are fetched, together with the object names they point at, are written to .git/FETCH_HEAD. This information may be used by scripts or other git commands, such as git-pull.

### git pull

##### Name
git-pull - Fetch from and integrate with another repository or a local branch

#### SYNOPSIS
```
git pull [<options>] [<repository> [<refspec>…​]]
```
### DESCRIPTION 
Incorporates changes from a remote repository into the current branch. If the current branch is behind the remote, then by default it will fast-forward the current branch to match the remote. If the current branch and the remote have diverged, the user needs to specify how to reconcile the divergent branches with --rebase or --no-rebase (or the corresponding configuration option in pull.rebase).

More precisely, git pull runs git fetch with the given parameters and then depending on configuration options or command line flags, will call either git rebase or git merge to reconcile diverging branches.

repository should be the name of a remote repository as passed to git-fetch. refspec can name an arbitrary remote ref (for example, the name of a tag) or even a collection of refs with corresponding remote-tracking branches (e.g., refs/heads/*:refs/remotes/origin/*), but usually it is the name of a branch in the remote repository.

Default values for ```<repository>``` and ```<branch>``` are read from the "remote" and "merge" configuration for the current branch as set by ```git-branch --track.```

##### Name
git-push - Update remote refs along with associated objects

#### SYNOPSIS

```
git push [--all | --mirror | --tags] [--follow-tags] [--atomic] [-n | --dry-run] [--receive-pack=<git-receive-pack>]
       [--repo=<repository>] [-f | --force] [-d | --delete] [--prune] [-v | --verbose]
       [-u | --set-upstream] [-o <string> | --push-option=<string>]
       [--[no-]signed|--signed=(true|false|if-asked)]
       [--force-with-lease[=<refname>[:<expect>]] [--force-if-includes]]
       [--no-verify] [<repository> [<refspec>…​]]
```
### DESCRIPTION 

Updates remote refs using local refs, while sending objects necessary to complete the given refs.
You can make interesting things happen to a repository every time you push into it, by setting up hooks there. See documentation for git-receive-pack.

When the command line does not specify where to push with the ```<repository>``` ```</repository> ```argument, branch.*.remote configuration for the current branch is consulted to determine where to push. If the configuration is missing, it defaults to origin.

When the command line does not specify what to push with``` <refspec>```... arguments or --all, --mirror, --tags options, the command finds the default ```<refspec> ```by consulting remote.*.push configuration, and if it is not found, honors push.default configuration to decide what to push (See git-config[1] for the meaning of push.default).

When neither the command-line nor the configuration specify what to push, the default behavior is used, which corresponds to the ```simple``` value for ```push.default```: the current branch is pushed to the corresponding upstream branch, but as a safety measure, the push is aborted if the upstream branch does not have the same name as the local one.

##### Name
git-remote - Manage set of tracked repositories

#### SYNOPSIS
```
git remote [-v | --verbose]
git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=(fetch|push)] <name> <URL>
git remote rename [--[no-]progress] <old> <new>
git remote remove <name>
git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
git remote set-branches [--add] <name> <branch>…​
git remote get-url [--push] [--all] <name>
git remote set-url [--push] <name> <newurl> [<oldurl>]
git remote set-url --add [--push] <name> <newurl>
git remote set-url --delete [--push] <name> <URL>
git remote [-v | --verbose] show [-n] <name>…​
git remote prune [-n | --dry-run] <name>…​
git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)…​]
```

### DESCRIPTION 

Manage the set of repositories ("remotes") whose branches you track.

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

### Fast Forward Merge:
##### merge can occur when there is a linear path from the current branch tip to the target branch. 

![Image](https://www.delftstack.com/img/Git/fastforward%20merge.jpg?ezimgfmt=rs:372x331/rscb5/ngcb5/notWebP)

## 3-way merge:
#### is where two changesets to one base file are merged as they are applied, as opposed to applying one, then merging the result with the other.

![Image](https://www.w3docs.com/uploads/media/default/0001/03/e0f0e9e14db945c07e1fc0f3b2460ac19e0f738f.png)

## command git marge:
```
$ git checkout master
$ git merge Feature
$ $ git branch -d Feature
```