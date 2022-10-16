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


