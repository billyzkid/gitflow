# gitflow

* [Why aren't you using git-flow?](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/)
* [git-flow considered harmful](http://endoflineblog.com/gitflow-considered-harmful)
* [comparison of using `git flow` commands versus raw `git` commands](https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac)
* [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/)

First, create a new repository on github.com (e.g. billyzkid/gitflow), then on your local machine:

```
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

> git checkout -b release/0.0.1 develop
M       README.md
Switched to a new branch 'release/0.0.1'

> git add .\README.md
PS C:\Users\will\code\gitflow> git commit -m "Updated README"
[release/0.0.1 ba09f19] Updated README
 1 file changed, 41 insertions(+)

> git push origin release/0.0.1
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 1.10 KiB | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
 * [new branch]      release/0.0.1 -> release/0.0.1

> git checkout master
Switched to branch 'master'

> git merge --no-ff release/0.0.1
Merge made by the 'recursive' strategy.
 README.md | 80 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
  1 file changed, 80 insertions(+)
 create mode 100644 README.md

> git tag -a 0.0.1 -m "Tagging release 0.0.1"

> git checkout develop
Switched to branch 'develop'

> git merge --no-ff release/0.0.1
Merge made by the 'recursive' strategy.
 README.md | 41 +++++++++++++++++++++++++++++++++++++++++
 1 file changed, 41 insertions(+)

> git branch -d release/0.0.1
Deleted branch release/0.0.1 (was ba09f19).

> git push origin master
Counting objects: 1, done.
Writing objects: 100% (1/1), 228 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
   9ddab04..bb50e2d  master -> master

> git push origin develop
Counting objects: 1, done.
Writing objects: 100% (1/1), 236 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
   0f3c661..9555deb  develop -> develop

> git push origin --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 169 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
 * [new tag]         0.0.1 -> 0.0.1

> git push origin :release/0.0.1
To https://github.com/billyzkid/gitflow.git
 - [deleted]         release/0.0.1
```