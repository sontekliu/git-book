# Git 标签

在实际的项目开发过程成中，如果项目进行到一个里程碑、一次上线、或者一次重大的变革，可能都会打上标签，代表一次历史性事件。像其他版本管理系统一样，`Git` 也同样提供了打标签的功能。

#### 1. 创建标签

`Git` 使用两种类型的标签，轻量标签和附注标签。

```shell
$ git tag v1.0  # 创建轻量标签
```

轻量标签像是一个不会改变的分支，它只是特定提交的一个引用。

```shell
$ git tag -a v1.0 -m "v1.0 版本 2018.07.06" # 创建附注标签
```

附注标签是存储在 `Git` 数据库中的一个完整对象，其中包含打标签的名字，电子邮件，日期时间，标签说明信息。通常建议创建附注标签。

你也可以对过去的某个提交打标签，该创建标签的时候忘记创建标签了，此时可以查看日志，找到对应的提交，然后再创建标签。例如历史提交如下：

 ```shell
$ git log --pretty=oneline --abbrev-commit   # --abbrev-commit 简化 commit 字串
2269ebc (HEAD -> master, origin/master, origin/HEAD) add git remote
14a4a8b add git remote
31612ca update git flow
ded51a1 Add git logog
a6b7206 update summary
15e06c2 add git pic
0bafe22 update summary
d8e5aca update doc
 ```

例如在 `a6b7206` 这次提交该创建标签，则执行如下命令

```shell
$ git tag v0.9 a6b7206                          # 轻量标签
或者
$ git tag -a v0.9 a6b7206 -m "add v0.9 version" # 附注标签
```

#### 2. 查看标签

列出所有标签

```shell
$ git tag
```

查看指定版本的标签

```shell
$ git tag -l "v1.0*"
```

查看标签的版本信息

```shell
$ git show v1.0
```

#### 3. 共享标签

默认情况下，`git push` 命令不会将标签信息推送到远程仓库的，在创建完标签之后，需要显示的将标签推送到远程仓库。

```shell
$ git push origin <标签名称>
```

如果想一次推送多个标签，则执行如下命令，它将会把所有不在远程仓库的标签全部推送到那里。

#### 4. 删除标签

```shell
$ git tag -d <标签名称>
```

以上命令可以将本地仓库的标签删除掉。但是如果已经提交到远程仓库的标签不会删除。

```shell
$ git push origin :refs/tags/v0.9
```

#### 5. 检出标签

在 `Git` 中你并不能真的检出一个标签，因为它们并不能像分支一样来回移动。 如果你想要工作目录与仓库中特定的标签版本完全一样，可以使用 `git checkout -b [branchname] [tagname]` 在特定的标签上创建一个新分支：

```shell
$ git checkout -b version2 v2.0.0
Switched to a new branch 'version2'
```

当然，如果在这之后又进行了一次提交，`version2` 分支会因为改动向前移动了，那么 `version2` 分支就会和 `v2.0.0` 标签稍微有些不同，这时就应该当心了。

