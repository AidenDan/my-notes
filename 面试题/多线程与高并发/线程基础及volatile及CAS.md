## volatile

### volatile

1. 保证可见
2. 不保证原子
3. 禁止指令重排

### volatile原理

编译为字节码后增加 Lock前缀指令，其做2件事：

1. 将当前缓存行的数据立即写回主内存

2. 写回主内存使其他工作内存里缓存了该共享变量地址的数据无效（缓存一致性协议）。

3. 内存屏障。确保指令重排序后顺序。loadload，loadstore...

   

### 指令重排序



## CAS

解决volatile不具有的原子性。

### CPU/CAS如何实现原子操作

CPU通过**缓存锁定**实现原子操作。因为内存相对CPU速度非常慢，所以每个CPU核心内部存在L1-3级别高速缓存，频繁使用的数据会存入其中，用来加快读取效率。单核心不会出现问题，但是当多核心的情况，可能会造成不同核心的高速缓存的数据不一致。

缓存锁定机制：当某个处理器对缓存中的共享变量进行了操作，会通知其他CPU当期存储该共享资源或重新读取该共享资源。

CAS是调用CPU底层指令实现的原子操作. 在**循环内得到原始值，然后CAS**(this, old, new)

### CAS ABA问题会造成什么影响

- 比如一个队列元素 A/B/A，如果数据没有变就修改A为C，可能造成第一个线程获取的是最后一个A，但是却以为自己获取的是第一个A，导致最后改成C。
- 比如存钱，两个操作重复了，都是100->50,一个操作是50->100

### CAS ABA问题如何处理

1. 版本号验证，每次版本号+1：

   在循环里判断版本/时间戳 是否合法，版本号是否正常，正常再走CAS

   AtomicMarkableReference，在pair内用bool标识版本进行compareAndSwapObject，感觉不靠谱。

   AtomicStampedReference。

2. 时间戳。StampedLock：

   



### CAS的性能问题

CAS操作的实质是**循环重试**，如AtomicInteger，每次循环获取当前值后，尝试将当前值改为目标值。

所以当处于**写多读少**的情况下，可能会造成长时间的循环。

### CAS性能优化

降低操作共享变量的并发数，分摊对单一共享变量压力。

如使用LongAdder，其由base和cell[]组成，单一线程仅CAS操作cell，当发生线程竞争，其余线程会将修改的值写入cell[],最后将cell[]和base累加即可。

但因为虽然最终会返回准确值，但操作后数值不一定当时准确，对实时性要求不高可用。



## 线程基础

### JAVA线程的实现

基于native方法调用操作系统 pthread实现，和系统线程是1：1的



### 如何理解线程上下文切换

当一个线程的时间片用完或被迫暂停，另一个线程或进程的线程被操作系统选中，来占用CPU的过程就是上下文切换（Context Switch）

![thread](./image/thread_1.jpg)

### 线程的状态

JAVA将 NEW/READY/RUNNING/WAITING/DEAD

映射为：

NEW -- NEW

READY -- RUNNABLE

RUNNING -- RUNNABLE

WAITING -- BLOCKED/WAITING/TIMED_WAITING

DEAD  -- TERMINATED





### 看个题目锻炼下思维，找找问题

```java
void lock(int lockval) {
	//trylock是用户级的自旋锁
	while(!trylock(lockval)) {
		wait();//**释放cpu，并将当期线程加入等待队列，是系统调用
	}
}

boolean trylock(int lockval){
	int i=0; 
	//localval=1代表上锁成功
	while(!compareAndSet(lockval,0,1)){
		if(++i>10){
			return false;
		}
	}
	return true;
}

void unlock(int lockval) {
	 compareAndSet(lockval,1,0);
	 notify();
}
```







### 不加synchronized也能运行Object.wait的话会存在什么问题？

eg：

```java
Object condObj=new Object();
voilate int flag = 0;
public void waitTest(){
	if(flag == 0){
		condObj.wait();
	}
}
public void notifyTest(){
	flag=1;
	condObj.notify();
}

```

### mutex和cond锁不同之处

`pthread_cond_timedwait`用于阻塞线程，实现线程等待，底层为futex



### 条件变量等待时传入的互斥锁，有何用意？

原子性



### futex原理

FUTEX_WAKE：
