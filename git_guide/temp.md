# 临时文件整理

## 2018.10.10

git remote show origin 显示远程分支信息
git branch -av  查看分支信息

Git 合并，遵循三方合并的原则
一个 git 提交可能有两个parent和两个child

git config --global alias.unstage "reset HEAD"
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit

git config --global alias.ui '!gitk'  外部命令别名，git ui == gitk

基于某个历史提交创建 branch，该分支指向当前历史提交还是HEAD提交?

* Git refspec

git push --set-upstream origin src:dest   创建远程分之与本地分之建立追踪关系
等价于
git push -u origin dev

clone 仓库之后，假如远程有 master dev 等分支，此时本地并没有dev，可使如下命令创建
git checkout -b dev origin/dev
等价于
git checkout --track origin/dev(新)   创建本地与远程分支同名的分支

git push 的完整写法： git push origin localBranch:remoteBranch
git pull 的完整写法： git push origin remoteBranch:localBranch
删除远程分支：git push origin :dest
删除远程分支：git push origin --delete branch_name （新版本）

建议远程分支名称与本地分支名称一致，如果不一致，即使做了追踪，git push 也执行不了
重命名远程分支，只能先删除，再推送本地分支到远程

HEAD 标记：

1. HEAD 文件是一个指向你当前所在分支的引用标识符，而该文件内部并不包含 SHA-1 值，而是一个指向另外一个引用的指
2. 当执行 git commit 命令时，git 会创建一个新的 commit 对象，并且将这个新的 commit 对象的 parent 指针设置为 HEAD 所指向的引用的 SHA-1 值  
3. 我们对于 HEAD 修改的任何操作，都会被 git reflog 完整记录下来，所以不建议手工改 HEAD 文件  
4. 实际上，我们可以通过 git 底层命令 symbolic-ref 来实现对 HEAD 文件内容的修改. git symbolic-ref HEAD 读取，git symbolic-ref HEAD refs/heads/dev 写入
5. HEAD, ORIG_HEAD, FETCH_HEAD

git push origin v1.0
git push origin v1.0 v2.0
git push origin --tags
git push origin refs/tags/v3.0:refs/tags/v3.0:

git show v1.0

删除远程标签
git push origin :refs/tags/v4.0
git push origin --delete tag v4.0

* refspec

1. 在缺省的情况下，refspec会被 git remote add 命令所自动生成，Git 会获取远端上 refs/heads 下所有引用，并将他们写到本地的 refs/remotes/origin
目录下，所以如果远端上有一个 master 分支，你在本地就可以通过下面几种方式访问他们的历史记录
git log origin/master
git log remotes/origin/master
git log refs/remotes/origin/master

```git
fetch = +refs/heads/*:refs/remotes/origin/*
fetch = +本地:远程  + 可选，即使不能快进，也强制更新远程信息, 否则不更新
```

* Git 裸库

git init --bare

* submodule

git submodule add git@github.com:/aaa.git mymodule(此路径之前不能存在)
更新 submodule
到指定的 submodule 执行 git pull
到父级：git submodule foreach git pull

git clone git@parent
git submodule init
git submodule update --recursive
或者
git clone git@github.com:parent --recursive

移除 submodule

git rm --cached mysubmodule
rm -rf mysubmodule
git commit -m "delete mysubmodule"
git rm .gitmodules

* git subtree

git remote add subtree-origin git@github.com:ss/xx.git
git subtree add --prefix=subtree subtree-origin master --squash

parent 更新 child:
git subtree pull -P subtree  subtree-origin master --squash
parent 提交 child:
git subtree push --prefix subtree  subtree-origin master

* 2018.10.13  

> git cherry-pick 将提交在A分支上的提交按提交顺序应用到B分支

git cherry-pick commit id...































