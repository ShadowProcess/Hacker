rtgen工具用来生成彩虹表。彩虹表是一个庞大的和针对各种可能的字母组合预先计算好的哈希值的集合。
彩虹表不一定是针对MD5算法的，各种算法都有，有了它可以快速的破解各类密码。越是复杂的密码，
需要的彩虹表就越大，现在主流的彩虹表都是100G以上。

使用rtgen工具生成彩虹表。具体操作步骤如下所示：

（1）切换到rtgen目录。执行命令如下所示。
[root@kali]:~# cd /usr/share/rainbowcrack/

（2）使用rtgen命令生成一个基于MD5的彩虹表。执行命令如下所示：
```text
[root@kali]:/usr/share/rainbowcrack# ./rtgen md5 loweralpha-numeric 1 5 0 3800 33554432 0 rainbow table md5_loweralpha-numeric#1-5_0_3800x33554432_0.rt parameters
hash algorithm: md5
hash length:    16
charset:        abcdefghijklmnopqrstuvwxyz0123456789
charset in hex: 61 62 63 64 65 66 67 68 69 6a 6b 6c 6d 6e 6f 70 71 72 73 74 75 76 77 78 79 7a 30 31 32 33 34 35 36 37 38 39
charset length: 36
plaintext length range: 1 - 5
reduce offset: 0x00000000
plaintext total: 62193780
sequential starting point begin from 0 (0x0000000000000000)
generating…
131072 of 33554432 rainbow chains generated (0 m 42.5 s)
262144 of 33554432 rainbow chains generated (0 m 39.2 s)
393216 of 33554432 rainbow chains generated (0 m 41.6 s)
524288 of 33554432 rainbow chains generated (0 m 42.0 s)
655360 of 33554432 rainbow chains generated (0 m 39.1 s)
786432 of 33554432 rainbow chains generated (0 m 40.1 s)
917504 of 33554432 rainbow chains generated (0 m 39.9 s)
1048576 of 33554432 rainbow chains generated (0 m 38.8 s)
1179648 of 33554432 rainbow chains generated (0 m 39.2 s)
1310720 of 33554432 rainbow chains generated (0 m 38.2 s)
.....
33161216 of 33554432 rainbow chains generated (0 m 40.2 s)
33292288 of 33554432 rainbow chains generated (0 m 38.9 s)
33423360 of 33554432 rainbow chains generated (0 m 38.1 s)
33554432 of 33554432 rainbow chains generated (0 m 39.1 s)
```
以上信息显示了彩虹表的参数及生成过程。例如，生成的彩虹表文件名为md5_loweralpha-numeric#1-5_0_3800x33554432_0.rt；
该表使用MD5散列算法加密的；使用的字符集abcdefghijklmnopqrstuvwxyz0123456789等。


（3）为了容易使用生成的彩虹表，使用rtsort命令对该表进行排序。执行命令如下 所示：
[root@kali]:/usr/share/rainbowcrack# rtsort md5_loweralpha-numeric#1-5_0_3800x33554432_0.rt

md5_loweralpha-numeric#1-5_0_3800x33554432_0.rt:
1351471104 bytes memory available
loading rainbow table…
sorting rainbow table by end point…
writing sorted rainbow table…
输出以上信息表示生成的彩虹表已成功进行排序。