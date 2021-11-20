# diweb+mindevdesk

diweb.sh是一键DD mindevdesk的脚本，当然它也支持其它系统和自定义镜像  
mindevdesk是一套live pve系统，包括三个可云桌面的lxc os  
mindevdesk ci.sh是一体系统mindevdesk的构建脚本，同时能构建出diweb.sh  
项目地址：https://gitee.com/minlearn/mindevdesk，项目分免费和部分付费  

更多请看接下来演示和文档部分

演示
--------

diweb.sh自带仓库和脚本。
可组建你自己的仓库。支持将自定义镜像和脚本一起，打包进免费github,gitee仓库，不会安装时镜像或debian源失联
见项目地址：https://gitee.com/minlearn/mindevdesk/raw/master/_build

diweb.sh支持进度显示（视频演示：https://www.bilibili.com/video/BV1ug411N7tn/）
![](/p/index/ddprogress.png)

mindevdesk ci.sh支持生成三系统,anbox,winebox,deepin desktop
![](/p/index/lxcdesktops.png)

mindevdesk ci.sh生成的os支持显卡加速
![](/p/index/gpupassthrough.png)

项目文档与维基：
-------

+  diweb
     +  [diweb介绍：什么是diweb.sh及它与mindevdesk ci.sh的关系](/p/32.tdl/diwebintro/readme.md)
     +  [diweb使用：利用diweb.sh安装mindevdesk，安装自定义镜像，及简单制造打包镜像](/p/32.tdl/diwebusage/readme.md)
     +  [高级：利用diweb.sh安装云黑群/云黑果镜像]
     +  [高级：对接diweb.sh使用gitee,github托管镜像，建立一体仓库]
     +  [高级：扩展diweb.sh，手动加入驱动]
     +  [高级：扩展diweb.sh，加入复杂机型网络及非DHCP支持的机型支持]
+  mindevdesk
     +  [mindevdesk介绍](/p/33.mdd/mddintro/readme.md)
     +  [mindevdesk使用：跑github actions编译带进度显示支持的diweb.sh和mindevdesk](/p/33.mdd/mddusage/readme.md)
     +  [显进度diweb版本使用：利用diweb.sh安装mindevdesk，安装自定义镜像]
     +  [高级：利用mindevdesk中的pve封装制造硬盘镜像]
     +  [高级：把进度显示附加到你现在使用的其它一键DD版本]
     +  [高级：利用mindevdesk汇聚闲置机打造你的个人IDC]

服务
--------

免费
> 只提供diweb.sh，可一站式解决你DD中大部分问题，去上面仓库，一键DD即可  
> 仅拥有diweb.sh定制能力  

收费1
> 拥有完整源码拥有定制能力。省事一体解决你装机和集成应用的问题。  
> 收费50发源码和资源包mindevdesk ci.sh，可加作者个人TG：https://t.me/minlearnhhbs 获取付款码  
> 个人TG只保持联系不提供无偿技术支持  

收费2
> 拥有完整源码拥有定制能力。省事一体解决你装机和集成应用的问题。  
> 收费100发mindevdesk ci.sh源码和资源包，享受源码升级1年，并可加一个永久TG互助组及作者个人TG  
> 可加作者个人TG：https://t.me/minlearnhhbs 获取付款码加入  
> （加群获社区支持，楼主不定期会在TG互助组里面帮解决问题，个人TG只保持联系不提供无偿技术支持）  

特价服务
> 如果你DD碰到问题无法解决找我，一次付足60-100元帮忙解决(视问题大小)，并可以得到显DD进度的diweb.sh一套  
> （注意：此套餐不提供加群和全套源码服务）  


此项目关联 https://gitee.com/minlearn/minlearnprogramming/tree/master/p/diwebmindevdeskopen/

