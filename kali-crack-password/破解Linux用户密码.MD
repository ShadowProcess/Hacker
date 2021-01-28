破解Linux的密码基本上和破解Windows密码的方法非常类似，在该过程中只有一点不同。
Linux系统没有使用SAM文件夹来保存密码散列。
Linux系统将加密的密码散列包含在一个叫做shadow的文件里，该文件的绝对路径为/etc/shadow。

不过，在使用John the Ripper破解/etc/shadow文件之前，
还需要/etc/passwd文件。这和提取Windows密码散列需要system文件和SAM文件是一样的道理。
John the Ripper自带了一个功能，它可以将shadow和passwd文件结合在一起，
这样就可以使用该工具破解Linux系统的用户密码。本小节将介绍破解Linux用户密码的方法。

使用John the Ripper工具破解Linux用户密码。具体操作步骤如下所示。

（1）使用unshadow提取密码散列。执行命令如下所示：
```shell script
[root@kali]: unshadow /etc/passwd /etc/shadow > /tmp/linux_hashes.txt
```
执行以上命令后，会将/etc/passwd/文件与/etc/shadow/文件结合在一起，生成一个叫做linux_hashes.txt的文件，保存在/tmp/目录中。

（2）破解Linux用户密码。执行命令如下所示：
```shell script
[root@kali]: john --format=crypt --show /tmp/linux_hashes.txt

root:123456:0:0:root:/root:/bin/bash
bob:123456:1000:1001::/home/bob:/bin/sh
alice:123456:1001:1002::/home/alice:/bin/sh
3 password hashes cracked, 0 left
```
从输出的结果中，可以看到当前系统中共有三个用户，其密码都为123456。

注意：使用John the Ripper开始破解Linux密码之前，需要使用支持破解不同类型密码散列的John the Ripper版本。
如果用错版本或者使用未打补丁的John the Ripper，程序将返回错误信息No password hashes loaded（没有价值密码散列）。
大多数现代Linux系统都使用SHA散列加密算法保存密码。