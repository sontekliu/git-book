# Git 使用前的配置

工欲善其事，必先利其器，作为分布式版本控制系统，Git 觉得可以称得上是利器，但是使用利器之前，必须对其进行打磨（配置）。

Git 使用 `git config` 命令来进行对 Git 的基本配置。Git 的配置内容主要存储在如下三个文件中：

1. /etc/gitconfig 或者 /usr/local/etc/gitconfig 文件，此文件是整个系统的配置信息，使用 `git config --system` 则会从此文件中读写配置信息。
2. ~/.gitconfig 文件，只是针对当前用户的配置，使用 `git config --global` 则会从此文件中读写配置信息。
3. repo/.git/config 文件，只是针对当前版本库的配置，`git config --local` 则会从此文件中读写配置信息。

> 版本库的配置信会覆盖用户级别的配置，用户级别的配置会覆盖系统级别的配置。即，以最内层的配置为主

以下是 Git 的一些基本配置：

1. 向仓库提交代码时，需要有用户名和邮箱（**重要**）

```git
    git config --global user.name "zhangsan"
    git config --global user.email "zhangsan@example.com"
```

2. 对终端显示的配置，给文字添加颜色，更易于阅读

```git
    git config --global color.diff auto
    git config --global color.ui  true
    git config --global color.status auto
    git config --global color.branch auto
```

3. Git编辑和差异化比较工具设置

```git
    git config --global core.editor vim
    git config --global merge.tool vimdiff
```

4. 配置命令别名

```git
    git config --global alias.ci commit
    git config --global alias.br branch
    git config --global alias.st status
    git config --global alias.co checkout
```

5. 配置信息查看

```git
    git config --list    # 查看所有配置
    git config user.name # 单个别名信息查看
```

6. 删除配置信息

```git
 git config [--system, --global, --local]--unset user.name
```

### 小结

本小节主要讲了 Git 的基本配置，Git 主要有三种配置级别，系统级，用户级和版本库级。最后说了 Git 配置的添加，查看和删除，这对 Git 的使用做了基本的铺垫。
下一节，将开始 Git 的基本使用。

