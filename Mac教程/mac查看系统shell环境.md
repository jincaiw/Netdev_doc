Mac查看与修改系统默认shell

#### 1. 查看Mac系统所有shell

```
cat /etc/shells
```

输出：

```
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

#### 2. 查看当前窗口使用的shell版本

> 这个变量并不一定指向你当前使用的 shell。例如，即使你在终端中调用不同的 shell，$SHELL 也保持不变

```
echo $SHELL
```


输出：

```
/bin/bash
```

#### 3. 查看系统用户默认shell

```
cat /etc/passwd | grep sh
```

输出：

表示root账户用的是sh，其他用的是bash

```
root:*:0:0:System Administrator:/var/root:/bin/sh
_sshd:*:75:75:sshd Privilege separation:/var/empty:/usr/bin/false
_update_sharing:*:95:-2:Update Sharing:/var/empty:/usr/bin/false
_mbsetupuser:*:248:248:Setup User:/var/setup:/bin/bash
```

#### 4. 输出当前使用的shell

```
echo $0
```

输出：

```
-zsh
```

#### 5. 修改系统默认shell为bash

```
chsh -s /bin/bash
```

**修改完之后重启终端后生效响应的配置！**

