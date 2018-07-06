# Git 分支

#### 1. 创建分支

```shell
$ git branch <分支名称>
```

上面命令表示创建分支，但是指针并未切换到新建的分支上面。如下图：

![git_branch_02](../images/git_branch_02.png)

```shell
$ git checkout <分支名称>
```

切换到指定的分支。如下图：

![git_branch_03](../images/git_branch_03.png)

```shell
$ git checkout -b <分支名称>    # 创建并切换到指定的分支
```

#### 2. 查看分支

```shell
$ git branch               # 显示分支列表
$ git branch -r            # 查看远程分支
$ git branch -a            # 查看本地和远程分支
```

#### 3. 切换分支

#### 4. 合并分支

#### 5. 分支的其他操作

