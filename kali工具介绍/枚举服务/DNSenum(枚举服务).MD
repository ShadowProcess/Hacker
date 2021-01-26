枚举是一类程序，它允许用户从一个网络中收集某一类的所有相关信息。本节将介绍DNS枚举和SNMP枚举技术。
DNS枚举可以收集本地所有DNS服务和相关条目。DNS枚举可以帮助用户收集目标组织的关键信息，
如用户名、计算机名和IP地址等，为了获取这些信息，用户可以使用DNSenum工具。要进行SNMP枚举，
用户需要使用SnmpEnum工具。SnmpEnum是一个强大的SNMP枚举工具，它允许用户分析一个网络内SNMP信息传输。

DNS枚举工具DNSenum
DNSenum是一款非常强大的域名信息收集工具。它能够通过谷歌或者字典文件猜测可能存在的域名，
并对一个网段进行反向查询。它不仅可以查询网站的主机地址信息、域名服务器和邮件交换记录，
还可以在域名服务器上执行axfr请求，然后通过谷歌脚本得到扩展域名信息，提取子域名并查询，
最后计算C类地址并执行whois查询，执行反向查询，把地址段写入文件。
本小节将介绍使用DNSenum工具检查DNS枚举。在终端执行如下所示的命令：

```shell script
┌──(root💀kali)-[~]
└─# dnsenum --enum baidu.com                                                                                      255 ⨯
dnsenum VERSION:1.2.6

-----   baidu.com   -----


Host's addresses:
__________________

baidu.com.                               600      IN    A        220.181.38.148
baidu.com.                               600      IN    A        39.156.69.79


Name Servers:
______________

ns3.baidu.com.                           63175    IN    A        112.80.248.64
ns7.baidu.com.                           59407    IN    A        180.76.76.92
dns.baidu.com.                           600      IN    A        110.242.68.134
ns4.baidu.com.                           51443    IN    A        14.215.178.80
ns2.baidu.com.                           57901    IN    A        220.181.33.31


Mail (MX) Servers:
___________________

mx1.baidu.com.                           300      IN    A        220.181.3.85
mx1.baidu.com.                           300      IN    A        111.202.115.85
mx.n.shifen.com.                         300      IN    A        220.181.3.85
mx.n.shifen.com.                         300      IN    A        220.181.50.185
jpmx.baidu.com.                          5343     IN    A        12.0.243.41
mx50.baidu.com.                          300      IN    A        12.0.243.41
mx.maillb.baidu.com.                     30       IN    A        220.181.3.85


Trying Zone Transfers and getting Bind Versions:
_________________________________________________


Trying Zone Transfer for baidu.com on ns3.baidu.com ...
AXFR record query failed: REFUSED

Trying Zone Transfer for baidu.com on ns7.baidu.com ...
AXFR record query failed: REFUSED

Trying Zone Transfer for baidu.com on dns.baidu.com ...

Trying Zone Transfer for baidu.com on ns4.baidu.com ...
AXFR record query failed: REFUSED

Trying Zone Transfer for baidu.com on ns2.baidu.com ...
AXFR record query failed: REFUSED
AXFR record query failed: REFUSED


Scraping baidu.com subdomains from Google:
___________________________________________

Error GETing http://www.google.com/ncr: Can't connect to www.google.com:80 (Network is unreachable) at /usr/bin/dnsenum line 971.
```

输出的信息显示了DNS服务的详细信息。其中，包括主机地址、域名服务地址和邮件服务地址。如果幸运的话，还可以看到一个区域传输。

使用DNSenum工具检查DNS枚举时，可以使用dnsenum的一些附加选项，如下所示。

--threads [number]：设置用户同时运行多个进程数。
-r：允许用户启用递归查询。
-d：允许用户设置WHOIS请求之间时间延迟数（单位为秒）。
-o：允许用户指定输出位置。
-w：允许用户启用WHOIS请求。
