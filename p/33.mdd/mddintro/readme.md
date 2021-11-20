

什么是mindevdesk ci.sh
=============

其实在diweb的介绍里就介绍过mindevdesk ci了。还介绍过它与mindevdesk的包含关系，总而言之：

概述
------

mindevdesk和mindevdesk ci.sh是：


```
mindevdesk是包含diweb.sh的源码基础codebase
源码所有的更改在mindevdesk ci.sh端所处的源码处发生，并编译成一个diweb.sh和一些target
之后,diweb.sh -t可以DD这些target
```

高级
------

这里还将介绍mindevdesk ci的源码结构：

