# ThreadPoolExecutor

## 主体结构

![图1 ThreadPoolExecutor UML类图](https://p1.meituan.net/travelcube/912883e51327e0c7a9d753d11896326511272.png)

图1 ThreadPoolExecutor UML类图



### Executor

ThreadPoolExecutor实现的顶层接口是Executor，顶层接口Executor提供了一种思想：将任务提交和任务执行进行解耦。用户无需关注如何创建线程，如何调度线程来执行任务，用户只需提供Runnable对象，将任务的运行逻辑提交到执行器(Executor)中，由Executor框架完成线程的调配和任务的执行部分。



### ExecutorService

ExecutorService接口增加了一些能力：（1）扩充执行任务的能力，补充可以为一个或一批异步任务生成Future的方法；（2）提供了管控线程池的方法，比如停止线程池的运行。

其中invokeAny 的意义为输入一组任务，当有一个非异常结束后其他任务全体撤销;

 invokeAll则会完成所有任务并返回一个Future的集合。



### AbstractExecutorService

AbstractExecutorService则是上层的抽象类，将执行任务的流程串联了起来，保证下层的实现只需关注一个执行任务的方法即可。



### ThreadPoolExecutor

最下层的实现类ThreadPoolExecutor实现最复杂的运行部分，ThreadPoolExecutor将会一方面维护自身的生命周期，另一方面同时管理线程和任务，使两者良好的结合从而执行并行任务。



## 实现原理

### ctl

```java
    private final AtomicInteger ctl = new AtomicInteger(ctlOf(RUNNING, 0));

    private static int runStateOf(int c)     { return c & ~CAPACITY; }// 获取运行状态
    private static int workerCountOf(int c)  { return c & CAPACITY; }// 获取当前工作线程数
    private static int ctlOf(int rs, int wc) { return rs | wc; }// 获取ctl
```

`ctl`这个AtomicInteger类型，是对线程池的运行状态和线程池中有效线程的数量进行控制的一个字段， 它同时包含两部分的信息：线程池的运行状态 (runState) 和线程池内有效线程的数量 (workerCount)，高3位保存runState，低29位保存workerCount，两个变量之间互不干扰。用一个变量去存储两个值，可避免在做相关决策时，出现不一致的情况，不必为了维护两者的一致，而占用锁资源。通过阅读线程池源代码也可以发现，**经常出现要同时判断线程池运行状态和线程数量的情况**。线程池也提供了若干方法去供用户获得线程池当前的运行状态、线程个数。这里都使用的是位运算的方式，相比于基本运算，速度也会快很多。



### execute

所有任务的调度都是由execute方法完成的，这部分完成的工作是：检查现在线程池的运行状态、运行线程数、运行策略，决定接下来执行的流程，是直接申请线程执行，或是缓冲到队列中执行，亦或是直接拒绝该任务。其执行过程如下：

1. 首先检测线程池运行状态，如果不是RUNNING，则直接拒绝，线程池要保证在RUNNING的状态下执行任务。
2. 如果workerCount < corePoolSize，则创建并启动一个线程来执行新提交的任务。
3. 如果workerCount >= corePoolSize，且线程池内的阻塞队列未满，则将任务添加到该阻塞队列中。
4. 如果workerCount >= corePoolSize && workerCount < maximumPoolSize，且线程池内的阻塞队列已满，则创建并启动一个线程来执行新提交的任务。
5. 如果workerCount >= maximumPoolSize，并且线程池内的阻塞队列已满, 则根据拒绝策略来处理该任务, 默认的处理方式是直接抛异常。

![图4 任务调度流程](https://p0.meituan.net/travelcube/31bad766983e212431077ca8da92762050214.png)

```java
public void execute(Runnable command) {
        if (command == null)
            throw new NullPointerException();
        /*
         * Proceed in 3 steps:
         *
         * 1. If fewer than corePoolSize threads are running, try to
         * start a new thread with the given command as its first
         * task.  The call to addWorker atomically checks runState and
         * workerCount, and so prevents false alarms that would add
         * threads when it shouldn't, by returning false.
         *
         * 2. If a task can be successfully queued, then we still need
         * to double-check whether we should have added a thread
         * (because existing ones died since last checking) or that
         * the pool shut down since entry into this method. So we
         * recheck state and if necessary roll back the enqueuing if
         * stopped, or start a new thread if there are none.
         *
         * 3. If we cannot queue task, then we try to add a new
         * thread.  If it fails, we know we are shut down or saturated
         * and so reject the task.
         */
        int c = ctl.get();
        if (workerCountOf(c) < corePoolSize) {
            if (addWorker(command, true))
                return;
            c = ctl.get();
        }
        if (isRunning(c) && workQueue.offer(command)) {
            int recheck = ctl.get();
            if (! isRunning(recheck) && remove(command))
                reject(command);
            else if (workerCountOf(recheck) == 0)
                addWorker(null, false);
        }
        else if (!addWorker(command, false))
            reject(command);
    }
```

### 缓冲队列

线程池的本质是对任务和线程的管理，而做到这一点最关键的思想就是将任务和线程两者解耦，不让两者直接关联，才可以做后续的分配工作。线程池中是以生产者消费者模式，通过一个阻塞队列来实现的。阻塞队列缓存任务，工作线程从阻塞队列中获取任务。

阻塞队列(BlockingQueue)是一个支持两个附加操作的队列。这两个附加的操作是：在队列为空时，获取元素的线程会等待队列变为非空。当队列满时，存储元素的线程会等待队列可用。阻塞队列常用于生产者和消费者的场景，生产者是往队列里添加元素的线程，消费者是从队列里拿元素的线程。阻塞队列就是生产者存放元素的容器，而消费者也只从容器里拿元素。

- ArrayBlockingQueue

  一个用数组实现的有界阻塞队列，遵循先进先出（FIFO）原则，支持公平和非公平锁

- LinkedBlockingQueue

  一个由链表组成的有界队列，遵循先进先出（FIFO）原则，默认长度为Integer.MAX_VALUE ，所以默认创业该队列有容量危险。

- PriorityBlockingQueue

  一个支持线程优先级排序的无界队列，默认自然排序，可以自定义实现#compareTo指定元素排序顺序，不能保证同优先级元素顺序

- DelayQueue

  一个实现PriorityBlockingQueue实现延迟获取的无界队列，创建元素时，可以指定多久才能从队列中获取当前元素。只有延时期慢才能从队列中获取元素

- SynchronousQueue

  一个不存储元素的阻塞队列，每一个put操作必须等待take操作，否则不能添加元素。支持公平和非公平锁。SynchronousQueue的一个使用场景在线程池里。Executors.newCachedThreadPool就使用了SynchronousQueue。这个线程根据需要（新任务到来时）创建新的线程，如果有空闲线程则会重复使用，线程空闲了60s会回收。（LIFO TransferStack）

  如果我们采用 SynchronousQueue 作为 ThreadPoolExecuto 的缓冲队列时，在没有线程执行 poll 时 ( 即存在等待线程 ) ，则 workQueue.offer(command) 返回 false, 这时 ThreadPoolExecutor就会增加线程，最快地达到最大线程数。

  Java 5中的SynchronousQueue使用两个队列（一个用于正在等待的生产者、另一个用于正在等待的消费者）和一个用来保护两个队列的锁。

- LinkedTransferQueue

  一个由链表结构组成的无界阻塞队列，相比其他队列，LinkedTransferQueue多了transfer和tryTransfer方法。#transfer(e)作用为：若当前存在一个正在等待获取的消费者线程，则立即移交e，否则，会将e插入队列尾部并且 等待 ，直到有消费者取走该元素。#tryTransfer省略了等待过程，直接返回false。其判断是否有等待的消费者原理是通过？？
  保留与完成。比如消费者线程从一个队列中取元素，发现队列为空，他就生成一个空元素放入队列 , 所谓空元素就是数据项字段为空。然后消费者线程在这个字段上旅转等待。这叫保留。直到一个生产者线程意欲向队例中放入一个元素，这里他发现最前面的元素的数据项字段为 NULL，他就直接把自已数据填充到这个元素中，即完成了元素的传送。大体是这个意思，这种方式优美了完成了线程之间的高效协作。

- LinkedBlockingDeque

  一个由链表结构组成的双向阻塞队列，队列头部和尾部都可以添加移除元素，多线程并发时，可以将锁的竞争最多降低至一半

  

  

  

  

  

  
  
  

使用ReentrantLock mainLock 来保证多线程入workers 并发。

一个boolean参数就区分了是入core还是max

## 获取任务getTask

1.while循环不断地通过getTask()方法获取任务。 2.getTask()方法从阻塞队列中取任务。 3.如果线程池正在停止，那么要保证当前线程是中断状态，否则要保证当前线程不是中断状态。 4.执行任务。 5.如果getTask结果为null则跳出循环，执行processWorkerExit()方法，销毁线程。



![图6 获取任务流程图](https://p0.meituan.net/travelcube/49d8041f8480aba5ef59079fcc7143b996706.png)



## 拒绝策略

如下已经存在的：

- ThreadPoolExecutor.AbortPolicy

  默认。丢弃并抛出RejectedExecutionException

- ThreadPoolExecutor.DIscardPolicy

  静默丢弃

- ThreadPoolExecutor.DiscardOldestPolicy

  丢弃队列最前面的任务，重新提交当前被拒绝的任务

- ThreadPoolExecutor.CallerRunsPolicy

  由调用线程（提交任务的线程）处理该任务×



## Worker

增加线程是通过线程池中的 addWorker 方法，该方法的功能就是增加一个线程，该方法不考虑线程池是在哪个阶段增加的该线程，这个分配线程的策略是在上个步骤完成的，该步骤仅仅完成增加线程，并使它运行，最后返回是否成功这个结果。addWorker方法有两个参数：firstTask、core。firstTask参数用于指定新增的线程执行的第一个任务，该参数可以为空；core参数为true表示在新增线程时会判断当前活动线程数是否少于corePoolSize，false表示新增线程前需要判断当前活动线程数是否少于maximumPoolSize，其执行流程如下图所示：

![图9 申请线程执行流程图](https://p0.meituan.net/travelcube/49527b1bb385f0f43529e57b614f59ae145454.png)







### 工作

```java
final void runWorker(Worker w) {
        Thread wt = Thread.currentThread();
    	// 获取当前worker内的任务
        Runnable task = w.firstTask;
        w.firstTask = null;
        w.unlock(); // allow interrupts
        boolean completedAbruptly = true;
        try {
            // 如果当前worker内任务不为空 或 可以从workQueue 获取一个任务（获取不到默认阻塞）
            while (task != null || (task = getTask()) != null) {
                w.lock();
                // If pool is stopping, ensure thread is interrupted;
                // if not, ensure thread is not interrupted.  This
                // requires a recheck in second case to deal with
                // shutdownNow race while clearing interrupt
                if ((runStateAtLeast(ctl.get(), STOP) ||
                     (Thread.interrupted() &&
                      runStateAtLeast(ctl.get(), STOP))) &&
                    !wt.isInterrupted())
                    wt.interrupt();
                try {
                    beforeExecute(wt, task);
                    Throwable thrown = null;
                    try {
                        // 执行任务
                        task.run();
                    } catch (RuntimeException x) {
                        thrown = x; throw x;
                    } catch (Error x) {
                        thrown = x; throw x;
                    } catch (Throwable x) {
                        thrown = x; throw new Error(x);
                    } finally {
                        afterExecute(task, thrown);
                    }
                } finally {
                    task = null;
                    w.completedTasks++;
                    w.unlock();
                }
            }
            completedAbruptly = false;
        } finally {
            processWorkerExit(w, completedAbruptly);
        }
    }
```



### 回收

**Worker线程回收**

线程回收的工作是在processWorkerExit方法完成的。

线程池中线程的销毁依赖JVM自动的回收，线程池做的工作是根据当前线程池的状态维护一定数量的线程引用，防止这部分线程被JVM回收，当线程池决定哪些线程需要回收时，只需要将其引用消除即可。Worker被创建出来后，就会不断地进行轮询，然后获取任务去执行，核心线程可以无限等待获取任务，非核心线程要限时获取任务。当Worker无法获取到任务，也就是获取的任务为空时，循环会结束，Worker会主动消除自身在线程池内的引用。

线程池在执行shutdown方法或tryTerminate方法时会调用interruptIdleWorkers方法来中断空闲的线程，interruptIdleWorkers方法会使用tryLock方法来判断线程池中的线程是否是空闲状态；如果线程是空闲状态则可以安全回收。

而所谓的销毁，即是在 processWorkerExit 方法中，调用HashSet<Worker> workers 的remove方法移除了对当前worker的引用。 

### 保持核心线程

每一个Worker都会在#run内执行#runWorker方法，在#runWorker内又会while调用#getTask，#getTask中有两行重要代码，在真正的任务执行前，对核心线程、非核心线程、可回收线程都作出不同的操作。





线程池使用一张Hash表去持有线程的引用，这样可以通过添加引用、移除引用这样的操作来控制线程的生命周期。这个时候重要的就是如何判断线程是否在运行。







### 总结

Worker 类 实现了Runnable接口,并继承了AQS;

因为重写了AQS，所以线程池可以锁指定某个Worker对象。

Worker的run方法又会调用线程池runWorker方法，然后runWorker会调用这个Worker对象内部线程（即业务线程）的run方法。





## 为毛submit可以返回结果

