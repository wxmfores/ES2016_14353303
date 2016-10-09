#DOL框架描述
###分布式操作层(DOL)是一个软件开发框架程序并行应用程序。DOL允许指定基于卡恩过程网络计算模型的应用程序，以基于SystemC的模拟引擎为特色。此外,DOL提供了一个基于xml的规范格式来描述在一个多处理器系统上并行应用程序的实现,包括绑定和映射。
***

#DOL安装笔记
##安装必要环境
`$ sudo apt-get update ` 

`$ sudo apt-get install ant`  

`$ sudo apt-get install openjdk-7-jdk`  

`$ sudo apt-get install unzip`

##下载文件
`sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`  

`sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`

##解压文件
###1.新建dol的文件夹
`$	mkdir dol`
###2.将dolethz.zip解压到 dol文件夹中
`$	unzip dol_ethz.zip -d dol`
###3.解压systemc
`$	tar -zxvf systemc-2.3.1.tgz`

##编译systemc
###1.解压后进入systemc-2.3.1的目录下
`$ cd systemc-2.3.1`
###2.新建一个临时文件夹objdir
`$	mkdir objdir`
###3.进入该文件夹objdir
`$	cd objdir`
###4.运行configure(能根据系统的环境设置一下参数，用于编译)
`$	../configure CXX=g++ --disable-async-updates`
###5.编译
`$ sudo make install`
###6.记录当前的工作路径(之后会用到）
`$ pwd`

##编译dol
###1.进入刚刚dol的文件夹,修改build_zip.xml文件
`$	cd ../dol`
###找到下面这段话，就是说上面编译的systemc位置在哪里，
`<property name="systemc.inc" value="YYY/include"/>`  

`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
###把YYY改成上页pwd的结果（注意，对于64位 系统的机器，lib-linux要改成lib-linux64）
###2.编译
`$	ant -f build_zip.xml all`
###若成功会显示build successful
###3.运行第一个例子
`$ cd build/bin/main`  

`$ sudo ant -f runexample.xml -Dnumber=1`
***

#遇到的问题及解决
###1.最后一步build failed
###解决方法:注释或删除在dol/build/bin/main 下 的 runexample.xml 215-217行，具体方法如下：
找到
    `<tstamp> 
    <format property="touch.time"
              pattern="MM/dd/yyyy hh:mm aa"
              offset="-5" unit="second"/>
    </tstamp>
    <touch datetime="${touch.time}">
      <fileset dir="example${number}"/>
    </touch>`



修改为：
    `<!--     <tstamp>   
    <format property="touch.time"
              pattern="MM/dd/yyyy hh:mm aa"
              offset="-5" unit="second"/>
    </tstamp>
    <touch datetime="${touch.time}">
      <fileset dir="example${number}"/>
    </touch> -->`

















# ES2016_14353303
