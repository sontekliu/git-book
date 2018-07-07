# 分支合并与合并冲突

#### 1. 分支合并

* 快速合并

  关于合并这块，文字描述起来可能没有示例+示图的方式效果好，下面我就已示例+示图的方式讲解分支合并。

  场景：

  1. 创建本地仓库，添加 `README.md` 并提交

     ```shell
     $ git init git_branch
     $ echo "AAAA" >> README.md
     $ git add README.md
     $ git commit -m "init README.md"
     ```

  2. 创建 `dev` 分支，并切换到 `dev` 分支

     ```shell
     $ git checkout -b dev
     ```

  3. 在 `dev` 分支上修改 `README.md` 文件多次，并进行多次提交

     ```shell
     $ echo "bbbb" >> README.md
     $ git commit -a -m "update README.md add bbbb on dev branch"
     $ echo "cccc" >> README.md
     $ git commit -a -m "update README.md add cccc on dev branch"
     $ echo "cccc" >> README.md
     $ git commit -a -m "update README.md add cccc on dev branch"
     ```

  4. 切换到 `master` 分支，查看 `README.md` 文件，看是否有在 `dev` 分支上的修改

     ```shell
     $ git checkout master
     $ cat README.md
     ```

  5. 合并 `dev` 分支到 `master` 分支，并查看历史提交

     ```shell
     $ git merge dev -m "merge dev to master"
     $ git log --oneline --graph
     ```

* 普通合并

  

#### 2. 合并冲突

