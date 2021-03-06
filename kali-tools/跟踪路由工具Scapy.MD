Scapy是一款强大的交互式数据包处理工具、数据包生成器、网络扫描器、网络发现工具和包嗅探工具。
它提供多种类别的交互式生成数据包或数据包集合、对数据包进行操作、发送数据包、包嗅探、应答和反馈匹配等功能。
下面将介绍Scapy工具的使用。

使用Scapy实现多行并行跟踪路由功能。具体操作步骤如下所示。

（1）启动Scapy工具。执行命令如下所示。
```shell script
┌──(root💀kali)-[~]
└─# scapy
INFO: Can't import PyX. Won't be able to use psdump() or pdfdump().

                     aSPY//YASa
             apyyyyCY//////////YCa       |
            sY//////YSpcs  scpCY//Pp     | Welcome to Scapy
 ayp ayyyyyyySCP//Pp           syY//C    | Version 2.4.4
 AYAsAYYYYYYYY///Ps              cY//S   |
         pCCCCY//p          cSSps y//Y   | https://github.com/secdev/scapy
         SPPPP///a          pP///AC//Y   |
              A//A            cyP////C   | Have fun!
              p///Ac            sC///a   |
              P////YCpc           A//A   | Craft packets like I craft my beer.
       scccccp///pSP///p          p//Y   |               -- Jean De Clerck
      sY/////////y  caa           S//P   |
       cayCyayP//Ya              pY/Ya
        sY/PsY////YCc          aC//Yp
         sc  sccaCY//PCypaapyCP//YSs
                  spCPY//////YPSps
                       ccaacs
                                       using IPython 7.19.0
>>>
```
看到>>>提示符，表示scapy命令登录成功。


（2）使用sr()函数实现发送和接收数据包。执行命令如下所示：
```shell script
>>> ans,unans=sr(IP(dst="www.rzchina.net/30",ttl=(1,6))/TCP())  点击确定

Begin emission:
Finished sending 24 packets.
..*************..****.*.**..................................................................................................................................................................................................................................................................................WARNING: DNS RR prematured end (ofs=500, len=500)
..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Received 1818 packets, got 20 answers, remaining 4 packets
>>>
```

执行以上命令后，会自动与www.rzchina.net建立连接。执行几分钟后，使用Ctrl+C终止接收数据包。
从输出的信息中可以看到收到70个数据包，得到19个响应包及保留了5个包。

（3）以表的形式查看数据包发送情况。执行命令如下所示：
>>> ans.make_table(lambda(s,r):(s.dst,s.ttl,r.src))

执行以上命令后，输出如下所示的信息：
输出的信息显示了该网络中的所有IP地址。



```text
emission /ɪˈmɪʃn/ 
n. （光、热等的）发射，散发；喷射；发行
n. (Emission)人名；(英)埃米申
```
