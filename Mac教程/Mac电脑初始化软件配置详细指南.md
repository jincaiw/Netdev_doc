Mac电脑初始化配置详细指南

## MacOS简单设置

# **macOS系统简单设置**

**1. 触摸板设置** `SystemPreferences` → `Trackpad`

- `Point&Click` → `Tapto click`.
- `Point&Click` → `Lookup &data detectors` → `Tapwiththree fingers`

**2. 键盘设置** `SystemPreferences` → `Keyboard`

- 建议把 F1 - F12 设置为标准功能键：`Useall F1,F2,etc.keys asstandard functionkeys`
- `Shortcuts` → `Allcontrols`

**3. Dock设置** `SystemPreference` → `Dock`

- Dock只放置常用App
- Dock栏建议移动到左侧：`Positionon screen` : `left`
- 建议设置为不重复显示已打开应用：`Minimizewindows intoapplication icon`

**4. 取消自动更新**

- `AppStore` → `Preference` → `Automaticallycheck forupdates`

**5. 输入法快捷键**

- `Keyboard` → `Shortcuts` → `InputSources/Spotlight`

**6. 热区锁屏**

- `Desktop&&ScreenSaver` → `ScreenSaver` → `HotCorners`. 右下角选择：`PutDisplayto Sleep`

## 一、必装软件

### 1.homebrew

- 使用 Homebrew 安装 Apple没有预装但需要的软件、Homebrew 会将软件包安装到独立目录，并将其文件软链接至 `/usr/local`、Homebrew 不会将文件安装到它本身目录之外，所以您可将 Homebrew 安装到任意位置。

安装命令：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)
```



- Homebrew必装的软件：
  
	- 批量安装软件
	
	```bash
	brew cask install atom
	brew cask install datagrip
  brew install deno
	brew cask install discord
	brew cask install docker
	brew install emacs
	brew install golang
	brew cask install google-chrome
	brew cask install intellij-idea
	brew cask install mailmaster
	brew install micro
	brew cask install mos
	brew cask install mumble
	brew cask install neteasemusic
	brew install nginx
	brew services start nginx
	brew install node
	brew cask install adoptopenjdk8
	brew install openjdk@11
	brew cask install popo
	brew cask install postman
	brew cask install QQ
	brew cask install qqmusic
	brew install rustup-init
	brew cask install sogouinput
	brew cask install shadowsocksx-ng-r
	brew cask install telegram
	brew install telnet
	brew cask install tencent-meeting
	brew cask install terminus
	brew install tree
	brew install unrar
	brew cask install visual-studio-code
	brew cask install wechat
	brew install wget
	brew cask install youdaodict
	brew cask install aliwangwang
	```
	
	
	
	- 安装Wget命令行下载软件，安装命令：
	
	```bash
	$ brew install wget
	```
	
	- 安装oh-my-zsh终端管理界面，安装命令：
	```bash
	sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
	```
	
	- 安装git版本管理软件，安装命令：
	
	```bash
	$ brew install git
	```

- Homebrew命令使用

```bash
# 搜索软件
brew search git
brew search google-chrome

# 安装
brew install vim
brew install neteasemusic

# 重新安装
brew reinstall vim
brew reinstall neteasemusic

# 升级软件
brew upgrade curl
brew upgrade google-chrome

# 不升级软件
brew pin curl

# 卸载软件与应用
brew uninstall git
brew uninstall  QQ

# 查看软件与应用
brew info git
brew info sourcetree
brew list

# 启动软件
brew services start mariadb

# 重新启动软件
brew services restart nginx

# 关闭软件
brew services stop mariadb
```

## 笔记本软件

### 1.flomo

> 主要是随时快速记录想法、读书笔记。双向链接、随时回顾、标签及全文搜索，
>
> 年会员费比较便宜，买个会员有更多的功能，图片可以原图上床。

[下载链接](https://flomoapp.com)

### 2.typora

> 支持markdown格式记事本软件，已经开始收费了，当网上能找到版本旧的免费版本，使用基本不受影响。

### 3.妙言

> 优点：比较轻的markdown软件，使用起来特别舒服，功能比较多。
>
> 缺点：网上的教程比较少，官方支持文件较少，快捷键支持不是很好。
>
> 

## 二、编辑软件
### 1. Office软件



1. list
2. list2
3. list3

- item
  - item
    - item5

------



> 主要的日常文件、表格等处理。



### 2. WPS Office



### 3. PDF Expert





## 三、沟通软件

### 1.微信



### 2.电报



### 3.Discord



## 四、截图软件



## 五、浏览器插件

## 1.油猴插件安装



## 六、终端&命令行









