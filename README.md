# gitflow

* [Why aren't you using git-flow?](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/)
* [git-flow considered harmful](http://endoflineblog.com/gitflow-considered-harmful)
* [comparison of using `git flow` commands versus raw `git` commands](https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac)
* [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/)

First, create a new repository on github.com (e.g. billyzkid/gitflow), then:

```
> cd code
> mkdir gitflow
> cd gitflow
> git init
Initialized empty Git repository in C:/Users/will/Code/gitflow/.git/

> git commit --allow-empty -m "Initial commit"
[master (root-commit) 9ddab04] Initial commit

> git checkout -b develop master
Switched to a new branch 'develop'

> git remote add origin https://github.com/billyzkid/gitflow.git
> git push origin develop
Counting objects: 2, done.
Writing objects: 100% (2/2), 168 bytes | 0 bytes/s, done.
Total 2 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
 * [new branch]      develop -> develop

> git push origin master
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
 * [new branch]      master -> master

> git branch
* develop
  master

> git checkout -b feature/feature-1 develop
Switched to a new branch 'feature/feature-1'

> git add .\README.md
> git commit -m "Added README"
[feature/feature-1 f04640b] Added README
 1 file changed, 39 insertions(+)
 create mode 100644 README.md

> git push origin feature/feature-1
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 829 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
 * [new branch]      feature/feature-1 -> feature/feature-1

> git checkout develop
Switched to branch 'develop'

> git merge --no-ff feature/feature-1
Merge made by the 'recursive' strategy.
 README.md | 39 +++++++++++++++++++++++++++++++++++++++
 1 file changed, 39 insertions(+)
 create mode 100644 README.md

> git branch -d feature/feature-1
Deleted branch feature/feature-1 (was f04640b).

> git push origin develop
Counting objects: 1, done.
Writing objects: 100% (1/1), 238 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
   9ddab04..0f3c661  develop -> develop
   
> git push origin :feature/feature-1
To https://github.com/billyzkid/gitflow.git
 - [deleted]         feature/feature-1
```