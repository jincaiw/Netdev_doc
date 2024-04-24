## 目录

> - 安装git
> - 创建ssh key、配置git
> - 提交本地项目到GitHub

## 一、安装git

首先通过终端查看是否安装git，终端输入：

```bash
git
```

如果已经安装，则会输出：

```bash
 ~  git
usage: git [-v | --version] [-h | --help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           [--super-prefix=<path>] [--config-env=<name>=<envvar>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add       Add file contents to the index
   mv        Move or rename a file, a directory, or a symlink
   restore   Restore working tree files
   rm        Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect    Use binary search to find the commit that introduced a bug
   diff      Show changes between commits, commit and working tree, etc
   grep      Print lines matching a pattern
   log       Show commit logs
   show      Show various types of objects
   status    Show the working tree status

grow, mark and tweak your common history
   branch    List, create, or delete branches
   commit    Record changes to the repository
   merge     Join two or more development histories together
   rebase    Reapply commits on top of another base tip
   reset     Reset current HEAD to the specified state
   switch    Switch branches
   tag       Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch     Download objects and refs from another repository
   pull      Fetch from and integrate with another repository or a local branch
   push      Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.
```

通过homebrew安装Git

安装命令如下：

```undefined
brew install git
```

## 二、创建ssh key、配置git

### 1. 设置username和email



```csharp
git config --global user.name "wenbo"
git config --global user.email "1050794513@qq.com"
```

### 2. 通过终端命令创建ssh key

```css
ssh-keygen -t rsa -C "1050794513@qq.com"
```

`1050794513@qq.com`是我的邮件名，回车会有以下输出



```ruby
Last login: Sat Jan  6 14:12:16 on ttys000
WMBdeMacBook-Pro:~ WENBO$ ssh-keygen -t rsa -C "1050794513@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/WENBO/.ssh/id_rsa): 
/Users/WENBO/.ssh/id_rsa already exists.
Overwrite (y/n)? n
WMBdeMacBook-Pro:~ WENBO$ 
```

由于这里我原来已经创建过，这里我选**n**，没有创建过的，会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在**~/**下生成.ssh文件夹，进去，打开id_rsa.pub，复制里面的key。
终端查看`.ssh/id_rsa.pub`文件



```kotlin
open .ssh/id_rsa.pub 
```

回车后，就会新弹出一个终端，然后复制里面的key。
或者用cat命令查看



```rust
cat .ssh/id_rsa.pub
```

- 3、登录GitHub（默认你已经注册了GitHub账号），添加ssh key，点击

  Settings

  ，如图

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-2c2f1120fb632c32.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

  屏幕快照 2018-01-06 下午2.40.11.png

  点击New SSH key，如图

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-b0bb4b509b243970.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

  屏幕快照 2018-01-06 下午2.57.15.png

  添加key，如图

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-a57165416146fba2.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

  屏幕快照 2018-01-06 下午2.53.07.png

- 4、链接验证



```css
ssh -T git@github.com 
```

终端输出结果



```ruby
Last login: Sat Jan  6 14:42:55 on ttys000
WMBdeMacBook-Pro:~ WENBO$ ssh -T git@github.com 
Hi wenmobo! You've successfully authenticated, but GitHub does not provide shell access.
WMBdeMacBook-Pro:~ WENBO$ 
```

说明已经链接成功。

## 三、提交本地项目到GitHub

- 1、在GitHub上新创建一个 repository或者

  Start a Project

  ，如图：

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-e3c19936a8d18c1f.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

  屏幕快照 2018-01-06 下午3.21.40.png

- 2、填写项目信息，如下图所示：

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-c8476b119008f74c.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

  屏幕快照 2018-01-06 下午3.27.27.png

  点击

  Create repository

  ,就创好一个工程了。

- 3、Clone工程到本地，首先复制ssh 地址

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-57248e2132b2085d.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

  屏幕快照 2018-01-06 下午3.32.04.png

  打开终端，这里只是测试，我想把工程克隆在桌面，首先在终端中切换路径到桌面，输入以下命令：



```bash
cd /Users/WENBO/Desktop/
```

然后克隆项目,终端输入



```bash
git clone git@github.com:wenmobo/LearnGit.git
```

`git@github.com:wenmobo/LearnGit.git`是刚刚复制的ssh路径。
终端完整输出如下：



```bash
Last login: Sat Jan  6 15:17:17 on ttys000
WMBdeMacBook-Pro:~ WENBO$ cd /Users/WENBO/Desktop/
WMBdeMacBook-Pro:Desktop WENBO$ git clone git@github.com:wenmobo/LearnGit.git
Cloning into 'LearnGit'...
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (5/5), 5.2
```

这时，工程已经被克隆到桌面了，如下图：



![img](https:////upload-images.jianshu.io/upload_images/3072214-348949fa129832c0.png?imageMogr2/auto-orient/strip|imageView2/2/w/574)

屏幕快照 2018-01-06 下午3.42.57.png

- 4、在Xcode中新创建一个工程，保存的路径为刚刚克隆下来的

  LearnGit

  文件夹下，如下图所示：

  ![img](https:////upload-images.jianshu.io/upload_images/3072214-ff179a78a18a8f54.png?imageMogr2/auto-orient/strip|imageView2/2/w/432)

  屏幕快照 2018-01-06 下午3.48.59.png

- 5、提交修改，首先切换到**LearnGit**文件路径：



```bash
cd /Users/WENBO/Desktop/LearnGit 
```

然后输入：



```csharp
//文件添加到仓库（.代表提交所有文件）
git add .
//把文件提交到仓库
git commit -m "First Commit"
//上传到github
git push
```

终端完整输出如下：



```bash
Last login: Sat Jan  6 15:49:54 on ttys000
WMBdeMacBook-Pro:~ WENBO$ cd /Users/WENBO/Desktop/LearnGit 
WMBdeMacBook-Pro:LearnGit WENBO$ git add .
WMBdeMacBook-Pro:LearnGit WENBO$ git commit -m "First Commit"
[master ae3bbe9] First Commit
 11 files changed, 649 insertions(+)
 create mode 100644 LearnGitDemo/LearnGitDemo.xcodeproj/project.pbxproj
 create mode 100644 LearnGitDemo/LearnGitDemo.xcodeproj/project.xcworkspace/contents.xcworkspacedata
 create mode 100644 LearnGitDemo/LearnGitDemo/AppDelegate.h
 create mode 100644 LearnGitDemo/LearnGitDemo/AppDelegate.m
 create mode 100644 LearnGitDemo/LearnGitDemo/Assets.xcassets/AppIcon.appiconset/Contents.json
 create mode 100644 LearnGitDemo/LearnGitDemo/Base.lproj/LaunchScreen.storyboard
 create mode 100644 LearnGitDemo/LearnGitDemo/Base.lproj/Main.storyboard
 create mode 100644 LearnGitDemo/LearnGitDemo/Info.plist
 create mode 100644 LearnGitDemo/LearnGitDemo/ViewController.h
 create mode 100644 LearnGitDemo/LearnGitDemo/ViewController.m
 create mode 100644 LearnGitDemo/LearnGitDemo/main.m
WMBdeMacBook-Pro:LearnGit WENBO$ git push
Warning: Permanently added the RSA host key for IP address '192.30.255.112' to the list of known hosts.
Counting objects: 20, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (18/18), done.
Writing objects: 100% (20/20), 6.80 KiB | 0 bytes/s, done.
Total 20 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To github.com:wenmobo/LearnGit.git
   1000218..ae3bbe9  master -> master
WMBdeMacBook-Pro:LearnGit WENBO$ 
```

查看GitHub上的项目，[LearnGit](https://github.com/wenmobo/LearnGit)已经上传成功啦，如下图所示：

![img](https:////upload-images.jianshu.io/upload_images/3072214-072b37b9b2399029.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

屏幕快照 2018-01-06 下午3.54.48.png

