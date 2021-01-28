安装软件：  dpkg -i nessus包.deb

运行nessus启动服务命令: /bin/systemctl start nessusd.service  

访问nessus服务：https://kali:8834/



----------nessus插件下载失败解决-------------
（1）在/opt/nessus/sbin目录下，使用nessuscli命令生成挑战码。如下所示：
    	./nessuscli fetch --challenge

（2）访问https://zh-cn.tenable.com/products/nessus/nessus-essentials网站，获取激活码。然后，访问https://plugins.nessus.org/v2/offline.php网站，输入挑战码和激活码。单击Submit按钮，将跳转到插件下载页面。

（3）下载的插件软件包名为all-2.0.tar.gz，许可协议文件名文nessus.license。然后，将下载的插件文件和许可协议文件复制到Nessus的/opt/nessus/sbin目录下，在该目录执行如下命令更新插件：
	./nessuscli fetch --register-offline nessus.license
	./nessuscli update all-2.0.tar.gz

（4）插件更新完成后，重新启动Nessus服务。然后，重新访问Nessus服务，即可成功加载插件。
	/bin/systemctl restart nessusd.service