## 一、介绍

> Heimdall是一种以简单的方式组织所有指向您最常用的网站和 Web 应用程序的链接的方法。简单是 Heimdall 的关键。它甚至可以使用 Google、[Bing](https://so.csdn.net/so/search?q=Bing&spm=1001.2101.3001.7020) 或 DuckDuckGo 包含一个搜索栏。

![在这里插入图片描述](https://img-blog.csdnimg.cn/c5d8ccd97b384279976b73fac042a361.png#pic_center)

## 二、安装环境

系统：CentOS Linux release 7.9.2009 (Core)
Docker：Docker version 20.10.18, build b40c2f6

## 三、支持的架构

镜像支持的架构是：

| 架构   | 可用 | 标签                  |
| ------ | ---- | --------------------- |
| x86-64 | √    | amd64-(version tag)   |
| arm64  | √    | arm64v8-(version tag) |
| armhf  | √    | arm32v7-(version tag) |

## 四、使用Docker部署Heimdall

借助Docker Compose，您可以使用 YAML 文件 来配置所有应用程序服务，这样您就可以轻松地使用单个命令启动它们。在继续之前，请确保您的系统上安装了Docker （[Linux安装Docker教程](https://www.talkmu.com/archives/linux-an-zhuang-docker-rong-qi)）。

创建挂载目录

```bash
mkdir -p /opt/docker/heimdall/config
1
```

### 方式1、[docker-compose](https://so.csdn.net/so/search?q=docker-compose&spm=1001.2101.3001.7020)（推荐）

创建docker-compose.yml

```bash
vi /opt/docker/heimdall/docker-compose.yml
1
```

添加以下内容：

```bash
version: "2.1"
services:
  heimdall:
    image: lscr.io/linuxserver/heimdall:latest
    container_name: heimdall
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Shanghai
    volumes:
      - /opt/docker/heimdall/config:/config
    ports:
      - 80:80
      - 443:443
    restart: unless-stopped
123456789101112131415
```

进入挂载目录

```bash
cd /opt/docker/heimdall
1
```

启动容器

```bash
docker-compose up -d
1
```

### 方式2、docker cli

```bash
docker run -d \
  --name=heimdall \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Asia/Shanghai \
  -p 80:80 \
  -p 443:443 \
  -v /opt/docker/heimdall/config:/config \
  --restart unless-stopped \
  lscr.io/linuxserver/heimdall:latest
12345678910
```

## 五、如何使用Heimdall

#### 1、输入网址访问服务

```bash
http://192.168.50.101:80
1
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/f0706e99cb5d40f181c0db9f680384b2.png#pic_center)

#### 2、设置语言

![![在这里插入图片描述](https://img-blog.csdnimg.cn/f0dacc9af2c24a0ab3ddd6717ac5087e.png](https://img-blog.csdnimg.cn/857b68b7b4bb4c7e9584855cec980f5c.png#pic_center)

将语言设置为简体中文

![![在这里插入图片描述](https://img-blog.csdnimg.cn/6da822f584894c3ebca3befbff78d312.png](https://img-blog.csdnimg.cn/2b6f2024d6844129b63c9fbfd2a5d81f.png#pic_center)

#### 3、添加应用

![在这里插入图片描述](https://img-blog.csdnimg.cn/7d7d721b0ec64fd390eea8071698a99c.png#pic_center)

可通过选择应用类型自动添加网站信息，也可通过输入网址自动获取网站信息
设置完成后，点击右下角保存即可

![在这里插入图片描述](https://img-blog.csdnimg.cn/d738307b63fd46bd9c9e0cd70b0603e0.png#pic_center)

#### 4、最终效果图

![在这里插入图片描述](https://img-blog.csdnimg.cn/0dd1153ec75641898625a91efa64f6d5.png#pic_center)

文章知识点与官方知识档案匹配，可进一步学习相关知识