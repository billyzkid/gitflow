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

> git checkout master
M       README.md
Switched to branch 'master'

> git log --format=oneline
bb50e2da0d8e56ef59dec5200569f472cf540a64 Merge branch 'release/0.0.1'
ba09f19bbbdec5f0b0b2cb49c0be580267108be2 Updated README
0f3c6615de04a4da8c152a1a89a9c0497a2dcd7d Merge branch 'feature/feature-1' into de
f04640bc3e745a80a669b0cd5435b2de6ad703e1 Added README
9ddab0415e37e51421228d0f3ed51b16628b86f8 Initial commit

> git checkout -b hotfix/0.0.2 bb50e2
M       README.md
Switched to a new branch 'hotfix/0.0.2'

> git add .\README.md

> git commit -m "Fixed README"
[hotfix/0.0.2 b12a912] Fixed README
 1 file changed, 70 insertions(+), 2 deletions(-)

> git checkout master
Switched to branch 'master'

> git merge --no-ff hotfix/0.0.2
Merge made by the 'recursive' strategy.
 README.md | 72 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++--
 1 file changed, 70 insertions(+), 2 deletions(-)

> git tag -a 0.0.2 -m "Tagging release 0.0.2"

> git checkout develop
Switched to branch 'develop'

> git merge --no-ff hotfix/0.0.2
Merge made by the 'recursive' strategy.
 README.md | 72 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++--
 1 file changed, 70 insertions(+), 2 deletions(-)

> git branch -d hotfix/0.0.2
Deleted branch hotfix/0.0.2 (was b12a912).

> git push origin master
Counting objects: 4, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 887 bytes | 0 bytes/s, done.
Total 4 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local objects.
To https://github.com/billyzkid/gitflow.git
   bb50e2d..80c3ff1  master -> master

> git push origin develop
Counting objects: 1, done.
Writing objects: 100% (1/1), 239 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
   9555deb..9d666ef  develop -> develop

> git push origin --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 170 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/billyzkid/gitflow.git
 * [new tag]         0.0.2 -> 0.0.2

> git log --graph --oneline --first-parent develop
* 9d666ef Merge branch 'hotfix/0.0.2' into develop
* 9555deb Merge branch 'release/0.0.1' into develop
* 0f3c661 Merge branch 'feature/feature-1' into develop
* 9ddab04 Initial commit

> git log --graph --oneline --first-parent master
* 80c3ff1 Merge branch 'hotfix/0.0.2'
* bb50e2d Merge branch 'release/0.0.1'
* 9ddab04 Initial commit
```