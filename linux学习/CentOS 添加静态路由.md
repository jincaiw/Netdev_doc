# CentOS 添加静态路由

------

在日常使用中，服务器有两个 IP 地址，两块网卡的配置，访问不同网段，这种情况很常见。但我们需要创建额外的路由条目，以确定通过正确的网关转发数据包，使 interface 能够正常通信。

以下在 CentOS 7、8 测试通过

## 一、使用 route 命令加入临时路由，重启后将失效

route 命令参数：

```
add     增加路由
del     删除路由
-net    设置到某个网段的路由
-host   设置到某台主机的路由
gw      出口网关 IP 地址
dev     出口网关 物理设备名
# 加入到主机的路由 (sysin)
route add -host 192.168.1.123 dev eth0
route add -host 192.168.1.123 gw 192.168.1.1

# 加入到网络的路由
route add -net 192.168.1.123 netmask 255.255.255.0 eth0
route add -net 192.168.1.123 netmask 255.255.255.0 gw 192.168.1.1
route add -net 192.168.1.123 netmask 255.255.255.0 gw 192.168.1.1 eth1
route add -net 192.168.1.0/24 eth1

# 加入默认网关
route add default gw 192.168.1.1

# 删除路由
route del -host 192.168.1.11 dev eth0
route del -net 192.168.1.123 netmask 255.255.255.0
# 查看路由信息
ip route
route -n
```

## 二、在 Linux 中添加永久路由的方法

### 1. 默认网关

（1）写入 ifcfg 文件（推荐）

```
vi /etc/sysconfig/network-scripts/ifcfg-eth0
```

在配置 ip 地址的时候直接将 GATEWAY 的配置写入 ifcfg 文件。形式：GATEWAY=gw-ip

适合加入默认路由

（2）在 `/etc/sysconfig/network` 里加入到文件末尾，格式例如以下：

GATEWAY=gw-ip 或者 GATEWAY=gw-dev

### 2. 写入 `/etc/rc.loacl`（不推荐）

（注意：CentOS 7 必须执行 `chmod +x /etc/rc.d/rc.local` 来确保确保这个脚本在引导时执行。）

能够将上面提到的命令写入 `/etc/rc.local` 文件里，这样在系统启动的时候会自己主动增加相关的路由设置。

只是这样的方法有一个缺点 (sysin)：假设某个系统服务，比方说是 NFS 服务，这个服务是在启动 network 服务之后，在运行 rc.local 之前，假设你设置的有自己主动挂载的 nfs。那么，这里链路的不通畅。会造成挂载的失败。另外一个就是假设你重新启动了网络 server，那么路由就失效了，这个时候你不得不又一次载入这个文件，可是假设你是远程操作的呢？所以，这种方法不推荐。

方法：

编辑 `/etc/rc.local`，使用 route 命令语法添加

```
route add -net 192.168.3.0/24 dev eth0
route add -net 192.168.2.0/24 gw 192.168.3.254
route add -net 172.16.0.0 netmask 255.255.0.0 gw 192.168.1.100 dev eth0
```

修改过的文件 `/etc/rc.d/rc.local` 文件示例

```
#!/bin/sh
#
# This script will be executed *after* all the other init scripts.
# You can put your own initialization stuff in here if you don't
# want to do the full Sys V style init stuff.
touch /var/lock/subsys/local
route add -net 192.168.3.0/24 dev eth0
route add -net 192.168.2.0/24 gw 192.168.3.254
route add -net 172.16.0.0 netmask 255.255.0.0 gw 192.168.1.100 dev eth0
```

### 3. 写入 `/etc/sysconfig/static-routes` 文件

默认在 `/etc/sysconifg` 文件夹中是没有这个文件的，须要我们手工创建。对这个文件的调用在以下：

```
cat /etc/init.d/network

    # Add non interface-specific static-routes.
    if [-f /etc/sysconfig/static-routes]; then
        if [-x /sbin/route]; then
            grep "^any" /etc/sysconfig/static-routes | while read ignore args ; do
                /sbin/route add -$args
            done
        else
            net_log $"Legacy static-route support not available: /sbin/route not found"
        fi
    fi
```

添加操作如下：

```
vi /etc/sysconfig/static-routes
any net 192.168.1.0/24 gw 192.168.1.1
any net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.1
any host 10.19.190.11/32 gw 10.19.177.10
any host 10.19.190.12 gw 10.19.177.10
```

这样的方式的话，和 rc.local 相比，比较有用。还比方 nfs，这个路由的生效时间是在网络服务 network 启动的时候生效的，而其它的一些网络相关服务都是在网络服务启动成功之后再启动的，所以可以保证网络链路的通畅。并且，假设我重新启动了网络服务，这个脚本是在网络服务启动里面的脚本调用。因此，也增加了自己主动上设置的相关路线。

> 该方式在 CentOS 8 默认安装时无效。
>
> 在 CentOS 8 中默认使用 nmcli 管理网络，可以通过 `yum install network-scripts` 来安装传统的 network.service，恢复用这种方式配置静态路由。

### 4. 创建 `/etc/sysconfig/network-scripts/route-eth0`（推荐）

```
# 在 `/etc/sysconfig/network-scripts/` 目录下创建名为 route-eth0 的文件
vi /etc/sysconfig/network-scripts/route-eth0
# 在此文件添加如下格式的内容
192.168.1.0/24 via 192.168.0.1
# 重启网络验证有效
systemctl restart network
```