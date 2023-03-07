# 安装

例子操作系统：[Ubuntu 22.04.1 LTS (Jammy Jellyfish)](https://www.releases.ubuntu.com/22.04/)， 最小化安装后，

安装完成后，需要做如下步骤：

1. sudo apt update

2. 安装部分基础软件，

   ```bash
   sudo apt install -y net-tools
   sudo apt install -y git vim curl jq
   # 用于远程登录
   sudo apt isntall -y openssh-server
   ```

3. 在操作系统页面中配置静态网络，也可以命令行（最好命令行，UI界面配置后没有自动生效）。

   ```bash
   # 看一下网卡情况
   # 注意，135.131是我一开始配置的网络，现在要改成其他的。
   fxy@fxy-virtual-machine:~$ ifconfig
   ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
           inet 192.168.135.131  netmask 255.255.255.0  broadcast 192.168.135.255
           inet6 fe80::ed27:cea7:6582:f44b  prefixlen 64  scopeid 0x20<link>
           ether 00:0c:29:a9:12:5d  txqueuelen 1000  (Ethernet)
           RX packets 1398  bytes 1106142 (1.1 MB)
           RX errors 0  dropped 0  overruns 0  frame 0
           TX packets 664  bytes 94435 (94.4 KB)
           TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
   
   lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
           inet 127.0.0.1  netmask 255.0.0.0
           inet6 ::1  prefixlen 128  scopeid 0x10<host>
           loop  txqueuelen 1000  (Local Loopback)
           RX packets 190  bytes 16006 (16.0 KB)
           RX errors 0  dropped 0  overruns 0  frame 0
           TX packets 190  bytes 16006 (16.0 KB)
           TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
   
   # 修改
   fxy@fxy-virtual-machine:~$ sudo vi /etc/netplan/01-network-manager-all.yaml
   # 修改为如下（ip是我的配置）：
   fxy@fxy-virtual-machine:~$ cat /etc/netplan/01-network-manager-all.yaml 
   # Let NetworkManager manage all devices on this system
   network:
     ethernets:
       ens33:
         dhcp4: false
         dhcp6: false
         addresses:
           - 192.168.135.132/24
         routes:
           - to: default
             via: 192.168.135.2
         nameservers:
           addresses:
             - 114.114.114.114
             - 8.8.8.8
     version: 2
     renderer: NetworkManager
   fxy@fxy-virtual-machine:~$ 
   # 使用如下命令使之生效：
   fxy@fxy-virtual-machine:~$ sudo netplan apply
   ```

   