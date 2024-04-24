### 一、问题分析：

通常在非 Mac App Store下载的软件都会提示“xxx已损坏，打不开。您应将它移到废纸篓”或者“打不开 xxx，因为它来自身份不明的开发者”。
### 二、原因：

Mac电脑启用了安全机制，默认只信任Mac App Store下载的软件以及拥有开发者 ID 签名的软件，但是同时也阻止了没有开发者签名的 “老实软件”
### 三、解决方法：

```
macOS Mojave 10.14及以下系统：
打开「终端」，输入sudo spctl --master-disable并回车，输入开机密码回车
```

```
macOS Catalina 10.15系统：
打开「终端」，输入以下命令并回车，输入开机密码回车
```

软件路径快速获取方法：
将软件拖入「终端」即可获得路径

```
sudo xattr -rd com.apple.quarantine 空格 软件路径
例：Xmind.app
sudo xattr -rd com.apple.quarantine /Applications/Xmind.app
```

