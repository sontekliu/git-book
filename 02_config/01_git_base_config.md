# 使用前的基本配置

开始使用 `Git` 有必要进行一些设置，`Git` 通过 `git config`  命令来进行对 `Git` 的基本配置，配置的内容存储在如下三个不同的文件中：

1. `/usr/local/etc/gitconfig` 文件，系统每个用户的通用配置，`git config --system` 则会从此文件中读写配置信息
2. `~/.gitconfig` 文件，只针对当前用户的配置，`git config --global` 则会从此文件中读写配置信息
3. `.git/config` 文件，只针对当前仓库的配置，`git config` 则会从此文件中读写配置信息
    每个级别会覆盖上一级别的配置，所以 `.git/config` 的配置肯定会覆盖 `~/.gitconfig` 和 `/usr/local/etc/gitconfig` 中的配置变量


1. **向服务器端提交代码时，需要有用户名和邮箱（重要）**

   ```shell
   git config --global user.name "zhangsan"
   git config --global user.email "zhangsan@example.com"
   ```

2. **对终端显示的配置，给文字添加颜色，更易于阅读**

   ```shell
   git config --global color.diff auto
   git config --global color.ui  true      
   git config --global color.status auto
   git config --global color.branch auto
   ```

3. **Git编辑和差异化比较工具设置**

   ```shell
   git config --global core.editor vim
   git config --global merge.tool vimdiff
   ```

4. **别名配置**

   ```shell
   git config --global alias.ci commit	
   git config --global alias.br branch	
   git config --global alias.st status	
   git config --global alias.co checkout
   ```

5. **配置信息查看**

   ```shell
   git config --list    # 查看所有配置
   git config user.name # 单个别名信息查看
   ```