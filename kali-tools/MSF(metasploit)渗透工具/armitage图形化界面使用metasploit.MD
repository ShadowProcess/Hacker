#1.去官网下载Metasploitable对应的linux，是zip包，解压后用VMware打开就行
http://sourceforge.net/projects/metasploitable/files/Metasploitable2/

#2.打开该metasploitable-linux后，登录名：msfadmin 登录密码：msfadmin


[切换到kali-linux进行操作]====================================================
先执行下面三行命令：
```shell script
# Start the PostgreSQL Database
systemctl start postgresql
# Initialize the Metasploit Framework Database 
msfdb init
# Start Armitage
armitage
```

如果成功启动：kali-linux将弹一个窗口；所有选项默认即可，点击连接，连接成功会有另外一个控制多台计算机的UI窗口
输入Host: 127.0.0.1
输入Port: 55553
输入User: msf
输入Pass: 1234

