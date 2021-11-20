

什么是diweb.sh及它与mindevdesk ci.sh的关系
=============


什么是diweb.sh
-------


diweb.sh是mindevdesk的recovery。类似winpe与windows的关系，它负责在线安装和恢复mindevdesk（基于一键DD原理），同时提供一些小工具在已安装的mindevdesk上进行一些维护工作，如一键清空数据区，扩展存储区等等

```
一键DD原理：

这是一种不同于ipxe网启方案的网络安装方案，通常用于给KVM的VPS装机

包括moeclub（V佬，全名请百度）和其它演化增强版在内的一键DD脚本原理，其实都是基于debian系的debian installer或centos的ks，一般有如下几个过程：
1，一键脚本在开始运行时根据目标机器收集网卡磁盘信息，并允许用户设定密码自定义网卡信息等，动态制造出一个类似PE的东西（也就是debian installer的内核和rootfs组成的live环境）这里存在一个部署过程（因为它被部署在了具体机器硬件上,debian installer rootfs中有驱动可以驱动目标机器）。  
2，然后重启引导目标机器进入这个”PE“，一般debian installer用的是newton界面前端，vnc环境下可以看到这个界面。然后根据preseed.cfg或ks.cfg文件读取部署方案（这被称为privison）进行网络安装或DD，你的VPS要支持dhcp，（不少机型卡在这个问题上用不一键DD，需要在preseed中配置或界面中手动设置）。  
3，preseed.cfg，如果是安装原生debian，属安装过程，不涉及到partman/earlycommand等自定义命令。如果是DD一个网络上托管的镜像，会运行一段wget -qO- url|gunzip -dc|dd of=/dev/你的第一个硬盘的脚本（或者使用tar zOx），脚本返回后会重启完成DD。  
```

diweb.sh也是上述原理脚本的演化和增强，它的不同点在于：

> diweb.sh特点：

> 它支持添加更多驱动和固件，这些逻辑在diweb.sh的update_kernelmodules函数中。linux驱动一般就是内核module，部分驱动除了modules还有firmware。能添加驱动就让diweb.sh支持更多机型，如hyperv机型和PD虚拟机。  
> 它支持将仓库保存到公有免费git平台，如gitee,github等。而一般DD自定义包只支持一个整体式打包直的链，diweb.sh的更灵活，更好用。这需要涉及到突破gitee从外网只能wget到1m文件大小的限制。需要对debianinstaller进行patch，脚本源码的patchdi函数中可见。而且脚本，debian镜像和系统镜像可以做到一起，不失联。  
> 它支持进度显示，而一般DD脚本没有进度显示。diweb.sh更直观，这段脚本被放在了mindevdesk ci.sh的patchpreseedanddiaddons函数中。  
> 它支持U盘安装和DD，本机实机安装，grube efi固件生成。  
> 更多...  

除了这些，diweb.sh最大的特点是它与mindevdesk的结合性。这导致它有点“专用”，比如它不支持centos，它也不支持直接安装debian,centos等（虽然这些也容易实现），但diweb.sh也支持自定义tar cvpzf打包的gz包镜像。你需要把你的包转成raw格式，然后tar cvpzf打包起来即可与diweb.sh配合使用

diweb.sh与mindevdesk ci.sh的关系：
-------

mindevdeskbuild源码是总体上的构建源码，它包含ci.sh和近1G的整理良好分门别类的项目资源，源码有github actions支持，workflow文件在.github/workflows下，可使用免费的github actions一个月200小时？的额度构建出mindevdesk和diweb.sh。（这样，构建仓库和目标仓库可以在同一个平台上）

基本上你可以这样理解：mindevdeskbuild + ci.sh 生成 mindevdesk + diweb.sh，后者是前者的构建结果。前者是私有的，后者是公开的
因此，diweb.sh是ci.sh经过构建的结果，它是一个去除了构建逻辑，仅面向DD使用者使用的ci精简版，此时它不叫ci了叫diweb.sh

(如果你是付费用户，拥有mindevdeskbuild源码，就能清楚发现：diweb.sh几乎是p/diweb/builder/*.sh汇合产生的，这部分有60多K。而p/mindevdesk/builder/*.sh是构建时的脚本，这部分有120多K)









