## Future模式

### Future和FutureTask

futureTask是future的实现类，主要场景用于异步多线程获取数据，然后阻塞等待全部结果返回。

简单来说Future模式实现是：

1. Future接口内定了get方法;get方法目的是同步等待结果执行完毕。
2. FutureTask实现了Future，其内部：设立一个lock锁 和 一个类变量result作为结果值
   - get方法：拿到lock就去判断任务是否结束，没结束就lock.wait, 结束了就返回result
   - finish方法：接收传参的结果，拿到lock后把接到的传参赋值给result，任务状态结束。
3. TaskService的submit方法接收一个Callable接口（即为task）并将新建的FutureTask返回，开启线程去执行这个Callable的内容，线程结束前调用FutureTask的finish方法。
4. 这样，外部通过submit的返回值可以拿到Future，调用get方法就能等待Callable执行固定的方法完毕再返回结果了。

以上就是最小实现方案，实际JUC的实现和上面的区别在于：

1. state设定了多种任务状态
2. JUC的FutureTask同时实现了Runnable接口，核心的执行方法run在FutureTask内部修改状态，设定返回值。
3. 用AQS实现get中的阻塞操作，因为否则没法实现超时等待。比如第一次get，wait了，第二次又要wait，最后都完事了notifyAll得。没完事就凉了。

### AQS

AQS实际上封装了对一个双向队列的操作

### forkjoin代码是否正确



### AtomicInteger