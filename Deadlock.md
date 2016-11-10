#死锁
##一.实验原理
###死锁产生的四个必要条件
1.互斥条件：一个资源只能被一个进程使用。

2.请求与保持条件：一个进程因请求资源而阻塞时，不释放已获得的资源。

3.不剥夺条件：进程已获得的资源在它使用完之前不能被强行剥夺。

4.循环等待条件：若干进程之间可以形成一种头尾相接的循环等待资源关系。

##二.实验验证
###*代码
1.Deadlock.java

![](http://i.imgur.com/sxSvZdM.png)

用命令javac Deadlock.java进行编译

2.Deadlock.sh

![](http://i.imgur.com/aCUUhiA.png)

用命令sh Deadlock.sh 运行

###*死锁产生的截图
![](http://i.imgur.com/Pt210vK.png)
###*对上述现象的解释
![](http://i.imgur.com/6cdzLQY.png)

当调度到线程t时，跑run()里面的代码，即调用B类对象b的methodB()方法，在该方法中调用作为参数传入的A类对象a的last()方法，等待一定时间后（用count控制的循环），线程t被阻塞，调用a的methodA()方法，在这个方法中调用作为参数传入的B类对象b的last()方法。如果此时线程t没有结束对methodB()方法的方法，那么runnable对b的last()方法的访问也会被阻塞，于是就产生了死锁。因此，为了跑出死锁的效果，可以适当调整变量count和c（执行次数）的值。
