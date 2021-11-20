
diweb.sh使用方法：
======

由于mindevdesk直接托管在gitee.com/minlearn/mindevdesk公开仓库下，脚本，debian镜像,系统镜像一体，最方便讲解（这也正是前述diweb.sh的优点体现之一），mindevdesk也是diweb.sh默认支持的系统，所以先讲。
稍后讲其它自定义镜像安装，最后讲打包一个镜像集成到仓库的方法

利用diweb.sh安装mindevdesk
------

首先，系统要求debian<=18.06，不能centos
1，进入这台云主机的vnc，打开命令行，2，或者直接在ssh下操作，稍后打开vnc，3，或者干脆不开vnc，仅在ssh下全程操作等待
（以上三种场景都可以，但如果有条件还是选择1更为直观，这里默认以1为例继续讲解）

进入命令后先下载mindevdesk公开仓库的diweb.sh脚本
(以下可在任意目录下进行，最好在本用户HOME目录或HOME子目录下，diweb.sh需要高级权限，所以必须要使用root或能sudo的帐户)：
```
1,以root用户进行: 
wget https://gitee.com/minlearn/mindevdesk/raw/master/diweb.sh
chmod +x ./diweb.sh
2,以sudo用户进行: 
sudo wget https://gitee.com/minlearn/mindevdesk/raw/master/diweb.sh
sudo chmod +x ./diweb.sh
```

然后执行脚本,对于mindevdesk就是一个t参数：
(以下讲解到的后续命令形式默认以root用户呈现，sudo一般只需要前面加个sudo）

diweb.sh -t mindevdesk


```
实际上 -t 是target的意思，mindevdesk是简化的镜像托管在仓库的地址，脚本做了简化处理，因此可以这样的方式调用。实际镜像在https://gitee.com/minlearn/mindevdesk/raw/master/_build/mindevdesk/mindevdesk_000到999之内的镜像分片文件组合而成的整体上。

具体的调用简化在diweb.sh开头的参数和开关判断处。

你可以在脚本执行前，wget一下https://gitee.com/minlearn/mindevdesk/raw/master/_build/mindevdesk/mindevdesk_中某个文件，测试一下速度以防机器网络对这些源下载过慢（对于其它http/https直链镜像也是一样的道理），对于国外主机你也可以转到wget https://github.com/minlearn/mindevdesk/raw/master/diweb.sh，然后


> (切换国外镜像：)  
> sudo ./diweb.sh -m https://github.com/minlearn/mindevdesk/raw/master -t mindevdesk


```

![](/p/wiki/diwebusage/rundiwebsh.jpg)

脚本会在开始处判断部署时的依赖，一般云主机带diweb.sh运行所需全部依赖，如果有必要的依赖这台机器不满足，会出现脚本错误并在相应的依赖框处提示no，并在不远处提示please apt-get install xxx in debian的字样，
比如对于curl，就是apt-get install curl

如果你的云主机无法apt-get install curl可能包缓存过时了，apt-get update即可，如果apt-get update不能进行，nano /etc/apt/sources.list，把坏掉的源替换，一般只需要替换第一条即可，如mirrors.xxx.com/debian，换成mirrors.aliyun.com/debian，ctl+x保存，再apt-get update，apt-get install curl

再次diweb.sh -t mindevdesk





