该文件内创建的自定义命令，只能在当前用户使用
/~/.bashrc
该文件内创建的自定义命令，可以被所有用户使用
/etc/bash.bashrc

############################################################
修改改文件:
```shell script
vi /home/alex/.bashrc
```


在最下面添加该段:
pack() {
        dir=`pwd`
        cd target/classes
        zip -r ../target.zip templates static com config
        cd $dir
}


我们添加这段不需要执行source命令，因为我们没有并没有新加的环境变量：
(该命令解释请看：以当前Shell执行，不会新建子Shell，，让脚本中新添加的环境变量执行并生效)
以下两个命令作用相同；因为source命令，可以用 点 代替；
```shell script
source /~/.bashrc
```
```shell script
. /~/.bashrc
```

