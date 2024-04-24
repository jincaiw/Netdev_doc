### 一、Oh My Zsh 是什么

- **Oh My Zsh** 是一款社区驱动的命令行工具，正如它的主页上说的，**Oh My Zsh** 是一种生活方式。它基于 **zsh** 命令行，提供了主题配置，插件机制，已经内置的便捷操作。给我们一种全新的方式使用命令行。
- **Oh My Zsh** 是基于 **zsh** 命令行的一个扩展工具集，提供了丰富的扩展功能。

### 二、Zsh 是什么

- **Zsh** 是一款强大的虚拟终端，既是一个系统的虚拟终端，也可以作为一个脚本语言的交互解析器。

```bash
# 打开终端，在终端上输入: 
zsh --version 
zsh 5.8.1 (x86_64-apple-darwin22.0)
# 这个命令来查看我们的电脑上是否安装了 Zsh 
# 端查询版本为： zsh 5.8.1 (x86_64-apple-darwin22.0)
```

```bash
# 查看系统当前 shell
cat /etc/shells 
# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.

/bin/bash
/bin/csh
/bin/dash
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh 
```

### 三、安装 Oh My Zsh 方法

- curl方式安装

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- wget方式安装

```bash
sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

- 安装成功会显示如下页面：

![image-20230306213407623](/Users/jincai/Library/Application Support/typora-user-images/image-20230306213407623.png)

### 四、开启高亮语法、开启显示行号

- 在终端中依次输入以下命令：

```bash
echo 'syntax on' >> ~/.vimrc
echo 'set nu!' >> ~/.vimrc
```

### 五、安装主题

- 在终端中输入以下命令：

```bash
vim ~/.zshrc
```

找到ZSH_THEME 这行，并且将后面双引号内文字改成想要套用主题风格，按下i 键进入编辑模式，双引号内改成「agnoster」，最后按下esc 键退出编辑，并输入:wq 就可以保存退出vim 编辑模式。

![image-20230306213649957](/Users/jincai/Library/Application Support/typora-user-images/image-20230306213649957.png)

### 六、安装命令高亮插件（zsh-syntax-highlighting）

- 在终端输入以下命令：

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### 七、安装命令自动补全插件（zsh-autosuggestions）

- 在终端输入以下命令:

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### 八、配置插件

**在终端输入以下命令**:

```bash
vim ~/.zshrc
```

1. 找到plugins=(git)这行;
2. 按下i 键进入编辑模式;
3. 修改成这个样子 plugins=(git zsh-syntax-highlighting zsh-autosuggestions);
4. 最后按下esc 键退出编辑，并输入:wq 就可以保存退出vim 编辑模式。

### 九、保存修改的设置

**在终端输入以下命令**

```bash
source ~/.zshrc
```

### 十、修改终端显示名称

进入 vi ~/.oh-my-zsh/themes/agnoster.zsh-theme 这个文件，把prompt_context用#注释掉，显示的名称就可以变短。

**修改前效果**：

![image-20230306230749025](/Users/jincai/Library/Application Support/typora-user-images/image-20230306230749025.png)

**修改后效果**：

![image-20230306234231025](/Users/jincai/Library/Application Support/typora-user-images/image-20230306234231025.png)

