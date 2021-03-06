[cnblogs](https://www.cnblogs.com/jingzhishen/p/4433023.html)
#### 用户级线程
线程管理工作由应用程序完成，内核意识不到线程的存在。比如一个进程由10个线程，但在内核看来，这就是1个进程而已，该进程任一个线程阻qi塞都会导致该进程挂起，并且无法利用多处理器技术。
用户级线程的优点是线程切换不用内核态和用户态的转换。

#### 内核级线程
线程管理由内核完成，进程的一个线程被阻塞，该进程的其它线程仍然可以被内核调度。

#### 轻量级进程
>a LWP runs in user space on top of a single kernel thread and shares its address space and system resources with other LWPs within the same process

#### 总结
进程是资源分配的最小单位，线程是程序执行的最小单位。

进程有自己的独立地址空间，每启动一个进程，系统就会为它分配地址空间，建立数据表来维护代码段、堆栈段和数据段，这种操作非常昂贵。而线程是共享进程中的数据的，使用相同的地址空间，因此CPU切换一个线程的花费远比进程要小很多，同时创建一个线程的开销也比进程要小很多。

线程之间的通信更方便，同一进程下的线程共享全局变量、静态变量等数据，而进程之间的通信需要以通信的方式（IPC)进行。不过如何处理好同步与互斥是编写多线程程序的难点。

但是多进程程序更健壮，多线程程序只要有一个线程死掉，整个进程也死掉了，而一个进程死掉并不会对另外一个进程造成影响，因为进程有自己独立的地址空间。
