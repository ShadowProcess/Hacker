所谓的密码字典主要是配合密码破解软件所使用，密码字典里包括许多人们习惯性设置的密码。这样可以提高密码破解软件的密码破解成功率和命中率，
缩短密码破解的时间。当然，如果一个人密码设置没有规律或很复杂，未包含在密码字典里，这个字典就没有用了，甚至会延长密码破解所需要的时间。
在Linux中有Crunch和rtgen两个工具，可以来创建密码字典。为方便用户的使用，本节将介绍这两个工具的使用方法。


###Crunch（压碎，咬碎）工具
Crunch是一种创建密码字典工具，该字典通常用于暴力破解。使用Crunch工具生成的密码可以发送到终端、文件或另一个程序。下面将介绍使用Crunch工具创建密码字典。

使用Crunch生成字典。具体操作步骤如下所示。

（1）启动crunch命令。执行命令如下所示。
```shell script
crunch
```

执行以上命令后，将输出如下所示的信息：
```text
crunch version 3.4
Crunch can create a wordlist based on criteria you specify. The outout from crunch can be sent to the screen, file, or to another program.
Usage: crunch <min> <max> [options]
where min and max are numbers
Please refer to the man page for instructions and examples on how to use crunch.
```
输出的信息显示了crunch命令的版本及语法格式。其中，使用crunch命令生成密码的语法格式如下所示：
> crunch [minimum length] [maximum length] [character set] [options]


crunch命令常用的选项如下所示。
-o：用于指定输出字典文件的位置。
-b：指定写入文件最大的字节数。该大小可以指定KB、MB或GB，但是必须与-o START选项一起使用。
-t：设置使用的特殊格式。
-l：该选项用于当-t选项指定@、%或^时，用来识别占位符的一些字符。

（2）创建一个密码列表文件，并保存在桌面上。其中，生成密码列表的最小长度为8，最大长度为10，并使用ABCDEFGabcdefg0123456789为字符集。执行命令如下所示：
[root@kali]:~# crunch 8 10 ABCDEFGabcdefg0123456789 –o /root/Desktop/ generatedCrunch.txt

```text
Notice: Detected unicode characters. If you are piping crunch output
to another program such as john or aircrack please make sure that program
can handle unicode input.
Do you want to continue? [Y/n] y
Crunch will now generate the following amount of data: 724845943848960 bytes
691266960 MB
675065 GB
659 TB
0 PB
Crunch will now generate the following number of lines: 66155263819776
AAAAAAAA
AAAAAAAB
AAAAAAAC
...
AAAAS
```

从以上输出的信息中，可以看到将生成659TB大的文件，总共有66155263819776行。以上命令执行完成后，
将在桌面上生成一个名为generatedCrunch.txt的字典文件。由于组合生成的密码较多，所以需要很长的时间。

（3）以上密码字典文件生成后，使用Nano命令打开。执行命令如下所示：
[root@kali]:~# nano /root/Desktop/generatedCrunch.txt

执行以上命令后，将会打开generatedCrunch.txt文件。该文件中保存了使用crunch命令生成的所有密码。