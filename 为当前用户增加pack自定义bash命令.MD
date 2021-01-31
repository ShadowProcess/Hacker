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

##############################
source /~/.bashrc

举例说明:

假如在登录后对 .bash_profile 中的 EDITER 和 TERM 变量做了修改，
这时就可以用 source 命令重新执行 .bash_profile文件,使修改立即生效而不用注销并重新登录。

再比如您在一个可执行的脚本 a.sh 里写这样一行代码

export KKK=111 
 

假如您用  ./a.sh  执行该脚本，执行完毕后，在当前shell环境中运行 echo $KKK，发现没有值，
但是用 source a.sh 来执行 ，然后再 echo $KKK，就会发现 打印 111 。

原因说明

#因为调用./a.sh来执行shell是在一个子shell里运行的，所以执行后，结构并没有反应到父shell里，
#但是source不同他就是在本shell中执行的，所以能够看到结果。
