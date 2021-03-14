# String知识点



## String知识点

java9开始，string为了节约空间将内部的char数组改为byte数组，因为一个char字符占16位，2个字节，这样存储占一个字节的字符就很浪费。而byte占8位一个字节。

在字符串常量中，对象默认被放入常量池。而变量中，对象会创建在堆内存，同时在常量池中创建一个字符串对象，String对象中的char数组将引用常量池中的char数组，并返回堆内存对象引用。



String是final的。不可被更改。

保证了：

1. String对象的安全性。假设String对象可变，那么string对象可能被修改。
2. hash属性值不频繁变更。
3. 可以实现字符串常量池。创建时池里找，找不到再创建。

## String优化

1. 拼接时可能被优化为stringbuilder。

2. 每次赋值时使用String#intern方法，如果常量池中有该对象则返回引用。1.7中常量池合并到堆，所以只是会把首次遇到的字符串引用添加到常量池;如果有则返回常量池中的字符串引用。

   ```
   String a =new String("abc").intern();
   String b = new String("abc").intern();
   ```

   调用new String 会在堆内存中创建一个String对象，而对象中的char数组会引用常量池中的字符串。

   在调用intern之后，会去常量池中查找是否有相应的引用，有就返回引用。

   堆内存中的对象由于没有新的引用指向，则会被垃圾回收。

   运行时创建的String对象不会在常量池中创建。

## 题目

### 1. 在1.7版本，new String后调用intern方法之后，程序做了什么？

1. 代码编译加载时，就会在字符串常量池中创建常量。

2. new String会分配一个String对象到堆内存，然后String对象内部的char数组会引用字符串常量池中已经存在的对象。

3. 调用intern之后会得到字符串常量池中的字符串引用并返回，原先堆内存中的String对象会被GC清理。

### 2. 看程序写结果

```java
class Demo1 {
    public void run() {
        String str1= "abc";
        String str2= new String("abc");
        String str3= str2.intern();
        assertSame(str1==str2);
        assertSame(str2==str3);
        assertSame(str1==str3)
    }
    
}

```

```java
// 字面量创建，搜索字符串常量池，若不存在则创建abc到字符串常量池，并返回引用
class Demo1 {
    public void run() {
        String str1= "abc";
        // new对象，在堆中创建String对象，返回引用。并去字符串常量池创建abc对象，
        // 若存在，则直接将char数组关联到字符串常量池内对象
        String str2= new String("abc");
        // 常量池中若存在abc，则返回abc存在于常量池中的引用
        String str3= str2.intern();
        assertSame(str1==str2);
        assertSame(str2==str3);
        assertSame(str1==str3)
    }
}

```





