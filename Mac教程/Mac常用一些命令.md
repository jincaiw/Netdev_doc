## 一、修改文件夹权限命令

### 1.首先 获得核心权限，输入密码

```bash
sudo -S
```

### 2.进入到该文件夹目录

```bash
cd /Library/Ruby/Gems/2.6.0
```

### 3.列出该文件夹文件所有权限

```bash
ls -l
```

### 4.更改权限，777

```bash
chmod 777 2.6.0
```

### 5.查看文件权限是否修改成功

```bash
ls -l
```

## 二、Mac升级ruby版本

```bash
Mac自身的ruby 版本 2.x，

ruby -v #可以查看版本号。

为更新到ruby的最新版本，可通过以下命令解决：

brew update

brew install ruby

echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile

source ~/.bash_profile

执行后，查看版本后，会判断已更新到最新版本。
```



----

关于ruby升级的问题：

已用home安装过ruby，升级： brew reinstall ruby

---

