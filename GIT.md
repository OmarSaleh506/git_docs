# GIT

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

By default, any tag that points into the histories being fetched is also fetched; the effect is to fetch tags that point at branches that you are interested in. This default behavior can be changed by using the --tags or --no-tags options or by configuring remote.<name>.tagOpt. By using a refspec that fetches tags explicitly, you can fetch tags that do not point into branches you are interested in as well.

git fetch can fetch from either a single named repository or URL, or from several repositories at once if <group> is given and there is a remotes.<group> entry in the configuration file. 

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

Default values for <repository> and <branch> are read from the "remote" and "merge" configuration for the current branch as set by ```git-branch --track.```

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

