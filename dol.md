#DOL实例分析&编程
##一.实验要求
*修改example1，使其输出三次方数

*修改example2，让3个square模块变成2个
##二.实验过程
###1.修改example1
####①.代码
*使其输出三次方数

![](http://i.imgur.com/UAImp2W.png)

由上图（square.c)可以看出，square模块所做工作就是将从端口的值读到变量i中后再对i做平方运算，然后将计算结果写到端口中。因此，要想输出三次方数，只需要将中间的运算操作改为立方即可。

*将模块名由square改为cube
对模块名的修改需要在xml文件中进行，具体细节如下:

-进程定义块

![](http://i.imgur.com/oZFK6Kl.png)

-连接定义块

![](http://i.imgur.com/RYHaVme.png)

需要注意的是，如果只在进程定义块中做相应修改并不会生效，必须连同连接定义块一同修改。

####②.运行截图
![](http://i.imgur.com/AANt0at.png)
####③.dot图
![](http://i.imgur.com/PuR5Afo.png)

###2.修改example2
####①.代码
*修改进程中的模块数

![](http://i.imgur.com/ZTsa6b5.png)

想要将进程中的模块数由3个变为2个，只需要将N的值由3改为2，因为N被用来控制进程定义块、通道定义块以及连接定义快中所用迭代器的迭代次数（如下图所示）

-进程定义块

![](http://i.imgur.com/Fbk3aQn.png)

因此，N值改为2后该进程中就将只有2个square模块。

-通道定义块

![](http://i.imgur.com/FeQVPmw.png)

因此，N值改为2后该进程就将只有3个通道用于连接生产者模块、消费者模块以及2个square模块。

-连接定义块

![](http://i.imgur.com/QKehQmH.png)

因此，N值改为2后就将只建立生产者模块、消费者模块以及2个square模块之间的连接。


####②.运行截图
![](http://i.imgur.com/SdxDWhF.png)
####③.dot图
![](http://i.imgur.com/KK6s896.png)


##三.实验感想与总结

1.实验中遇到的问题及解决

①.在dol/build/bin/main目录下的c文件和xml文件都不允许修改
解决方法：该目录下的example文件夹都是编译运行生成的，所以没有修改权限。本次实验中我们要修改的文件都在dol/examples目录下，完成修改后重新编译运行（在此之前需要将之前已经生成的文件夹删除）即可得到预期结果。

2.实验心得

通过本次实验，对dol架构以及生产者进程、消费者进程和处理模块的含义有了一定了解，掌握了对该类代码的基本分析方法。



