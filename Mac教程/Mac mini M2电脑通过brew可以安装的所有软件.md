### homebrew安装记录

homebrew安装命令

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

安装完成后一定要设备zsh变量，才能执行具体命令，具体操作如下





PS: 终端类型根据执行命令`echo $SHELL`显示的结果：

- `/bin/bash` => `bash` => `.bash_profile`
- `/bin/zsh` => `zsh` => `.zprofile`

**如果遇到环境变量无效问题，建议回过头来查看终端类型，再做正确的设置。**

从`macOS Catalina`(10.15.x) 版开始，`Mac`使用`zsh`作为默认`Shell`，使用`.zprofile`，所以对应命令：

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

```
打开文件时提示【文件已损坏，请移至废纸篓】
打开文件时提示【文件来自身份不明的开发者】
请按以下图示操作
```

A. 系统是OS Sierra(10.12)以上，需要⽤用终端打开『允许任何来源』。

打开launchpad——其他——终端。在命令⾏行行⾏行行⾏行行⾥里里⾥里里⾥里里输⼊入⼊入:sudo spctl --master-disable 然后输⼊入您的管理理员密码(开机密码)，并回⻋车(注:输⼊入过程中密码不不可⻅见)



Cellar/wget/1.16.1

```bash
Cellar/wget/1.16.1
```

```bash
Cellar/wget/1.16.1
```

```

```

```bash
Cellar/wget/1.16.1
```

```bash
Cellar/wget/1.16.1
```