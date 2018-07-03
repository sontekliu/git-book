# Git 多平台安装 

### Windows 平台

打开网址访问 `https://git-scm.com/` 下载 `Git` 并进行安装。

Git GUI 工具：

* [Git for Windows](https://gitforwindows.org/index.html) 
* [TortoiseGit](https://tortoisegit.org/) 
* [SourceTree](https://www.sourcetreeapp.com/) 

### GUN/Linux 平台

**Fedora** 平台

```shell
$ sudo yum install git
```

如果你在基于 **Debian** 的发行版上，请尝试用 apt-get： 

```shell
$ sudo apt-get install git
```

### Mac 平台

```shell
brew install git
```

### 源码安装

Linux 系统 `git` 源码下载地址是:`https://www.kernel.org/pub/software/scm/git/`,可下载最新版本.

```shell
1) tar -zxvf git-2.3.4.tar.gz # 解压缩此源码包
2) cd git-2.3.4
3) yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel
4) ./configure
5) make
6) make install
```
注意, 如果安装的是新版本,可能会出现如下错误:
```shell
 usr/bin/perl Makefile.PL PREFIX='/usr/local/git' INSTALL_BASE='' --localedir='/usr/local/git/share/locale'
 Can't locate ExtUtils/MakeMaker.pm in @INC (@INC contains: /usr/local/lib64/perl5 /usr/local/share/perl5 /usr/lib64/perl5/vendor_perl /usr/share/perl5/vendor_perl /usr/lib64/perl5 /usr/share/perl5 .) at Makefile.PL line 3.
 BEGIN failed--compilation aborted at Makefile.PL line 3.
 make[1]: *** [perl.mak] Error 2
 make: *** [perl/perl.mak] Error 2 
```

以下是解决方案:
```shell
$ sudo yum install perl-ExtUtils-MakeMaker package
```

