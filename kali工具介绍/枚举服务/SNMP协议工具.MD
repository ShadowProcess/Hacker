#==========================SNMP枚举工具Snmpwalk==================================-===========================
Snmpwalk是一个SNMP应用程序。它使用SNMP的GETNEXT请求，查询指定的所有OID（SNMP协议中的对象标识）树信息，并显示给用户。本小节将演示Snmpwalk工具的使用。

使用Snmpwalk命令测试Windows主机。执行命令如下所示：
```shell script
snmpwalk -c public 192.168.41.138 -v 2c   #该命令将返回无响应  因为我的是win家庭版，没有Snmp服务，也装不上，需要win专业版
```

```text
iso.3.6.1.2.1.1.1.0 = STRING: "Hardware: x86 Family 6 Model 42 Stepping 7 AT/AT COMPATIBLE - Software: Windows Version 6.1 (Build 7601 Multiprocessor Free)"
iso.3.6.1.2.1.1.2.0 = OID: iso.3.6.1.4.1.311.1.1.3.1.1
iso.3.6.1.2.1.1.3.0 = Timeticks: (49046) 0:08:10.46
iso.3.6.1.2.1.1.4.0 = ""
iso.3.6.1.2.1.1.5.0 = STRING: "WIN-RKPKQFBLG6C"
iso.3.6.1.2.1.1.6.0 = ""
iso.3.6.1.2.1.1.7.0 = INTEGER: 76
iso.3.6.1.2.1.2.1.0 = INTEGER: 19
```
以上输出的信息显示了Windows主机192.168.41.138上的所有信息。


使用Snmpwalk工具也可以枚举目标主机上打开的TCP端口。执行命令如下所示：
```shell script
[email protected]:~# snmpwalk -c public 192.168.41.138 -v 1 | grep tcpConnState | cut -d "." -f6 | sort -nu
21
25
80
443
```
输出信息显示了192.168.41.138主机打开的端口。如21、25、80和443，总共打开了4个端口号。



#==========================SNMP枚举工具Snmpcheck==================================-===========================
Snmpcheck工具允许用户枚举SNMP设备的同时将结果以可读的方式输出。下面将演示该工具的使用。
使用Snmpcheck工具通过SNMP协议获取192.168.41.138主机信息。执行命令如下所示：

如果使用该命令出现以下错误：
```text
Can't locate Tk.pm in @INC (you may need to install the Tk module) 
(@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.30.0 
/usr/local/share/perl/5.30.0 /usr/lib/x86_64-linux-gnu/perl5/5.30 
/usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.30 /usr/share/perl/5.30 
/usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) 
at /usr/bin/snmpcheck line 652.
BEGIN failed--compilation aborted at /usr/bin/snmpcheck line 652.
```
那么需要安装TK模块：
```shell script
sudo apt-get install perl-tk
```


```shell script
snmpcheck -t <ip地址>
```

可以获取该ip对应主机的信息：
（1）获取系统信息，如主机名、操作系统类型及架构
（2）获取设备信息，如设备ID号、类型和状态等
（3）获取存储信息，如设备id、设备类型和文件系统类型等。
（4）获取用户账户信息
（5）获取进程信息，如进程ID、进程名和进程类型等。
（6）获取网络信息，如TTL值、TCP段和数据元。
（7）获取网络接口信息，如接口状态、速率、IP地址和子网掩码等。
（8）获取路由信息，如目标地址、下一跳地址、子网掩码和路径长度值。
（9）获取网络服务信息，如分布式组件对象模型服务、DHCP客户端和DNS客户端等。
（10）获取监听的TCP端口，如监听的TCP端口号有135、495149513和139等
（11）获取监听UDP端口信息，如监听的UDP端口有123、161、4500、500和5355等。
（12）获取软件组件信息，如Visual C++ 2008。
（13）获取Web服务信息，如发送的字节数、文件数和当前匿名用户等。
以上信息显示了关于Web服务的信息。最后显示了枚举主机192.168.41.138共用的时间


#==========================SNMP枚举工具smtp-user-enum==================================-===========================
```shell script
smtp-user-enum -M VRFY -U /tmp/users.txt -t 192.168.41.138
```
smtp-user-enum是针对SMTP服务器的25端口，进行用户名枚举的工具，
用以探测服务器已存在的邮箱账户。在SMTP服务上启动用户的SMTP枚举

输出的信息显示了扫描192.168.41.138主机的详细信息，包括模式、运行进程、用户名文件、用户数和TCP端口等。