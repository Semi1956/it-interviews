# 线程异常面试题
##Java中如何停止一个线程？

* JDK 1.0本来有一些像stop(), suspend() 和 resume()的控制方法但是由于潜在的死锁威胁因此在后续的JDK版本中他们被弃用了
	
* 当run() 或者 call() 方法执行完的时候线程会自动结束

* 可以用volatile 布尔变量来退出run()方法的循环或者是取消任务来中断线程

##一个线程运行时发生异常会怎样？

* 异常没有被捕获该线程将会停止执行

* 当一个未捕获异常将造成线程中断的时候JVM会使用Thread.getUncaughtExceptionHandler()来查询线程的UncaughtExceptionHandler并将线程和异常作为参数传递给handler的uncaughtException()方法进行处理。

##如果同步块内的线程抛出异常会发生什么？
* 无论你的同步块是正常还是异常退出的，里面的线程都会释放锁

##Java中活锁和死锁有什么区别？

* 处于活锁的线程或进程的状态是不断改变的，活锁可以认为是一种特殊的饥饿

* 进程的状态可以改变但是却不能继续执行



##怎么检测一个线程是否拥有锁？

* 在java.lang.Thread中有一个方法叫holdsLock()，它返回true如果当且仅当当前线程拥有某个具体对象的锁

