DMitry工具是用来查询IP或域名WHOIS信息的。
WHOIS是用来查询域名是否已经被注册及已经注册域名的详细信息的数据库（如域名所有人和域名注册商）。
使用该工具可以查到域名的注册商和过期时间等。下面将使用DMitry工具收集rzchina.net域名的信息。执行命令如下所示：

```shell script
┌──(root💀kali)-[~]
└─# dmitry -wnpb rzchina.net
Deepmagic Information Gathering Tool
"There be some deep magic going on"

HostIP:180.178.61.83
HostName:rzchina.net

Gathered(收集) TCP Port information for 180.178.61.83
---------------------------------
 Port           State
135/tcp         open
...
```

输出的信息显示了rzchina.net域名的IP地址、WHOIS信息及开放的端口号等。
执行以上命令后输出的信息很多，但是由于篇幅的原因，部分内容使用省略号（……）代替。

虽然使用DMitry工具可以查看到IP或域名信息，但还是不能判断出这个网络范围。
因为一般的路由器和防火墙等并不支持IP地址范围的方式，所以工作中经常要把IP地址转换成子网掩码的格式、
CIDR格式和思科反向子网掩码格式等。在Linux中，netmask工具可以在IP范围、子网掩码、CIDR和Cisco等格式中互相转换，
并且提供了IP地址的点分十进制、十六进制、八进制和二进制之间的互相转换。
使用netmask工具将域名rzchina.net转换成标准的子网掩码格式。执行命令如下所示：
```shell script
┌──(root💀kali)-[~]
└─# netmask -s rzchina.net                                                                                        139 ⨯
  180.178.61.83/255.255.255.255
```
输出的信息显示了rzchina.net域名的IP地址和子网掩码值。