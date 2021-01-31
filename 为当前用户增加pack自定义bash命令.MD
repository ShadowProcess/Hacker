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

# 立即生效
source /~/.bashrc
