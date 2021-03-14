## ArrayList和LinkedList



## ArrayList

### Arraylist的基本构造

ArrayList内部是由Object对象组成的elementData数组，所以是一块连续的内存空间。同时也有当前元素长度modCount、总容量size属性。

### 对Arraylist做初始化操作时应该如何赋值？

ArrayList在初始化时如果长度可以确定，应当赋值初始长度为需求的长度，以免多次扩容。默认长度在第一次赋值时会变为10。

### Arraylist新增元素的扩容机制是什么？

ArrayList在初始并没有长度，当添加第一个元素时，数组会初始化为10。后面当元素超过10的时候（元素数大于容量），会再次触发扩容，ArrayList使用Arrays.copyOf重新设置为一个之前大小1.5倍的数组并将地址重新赋给elementData

### ArrayList移除元素的逻辑是什么

获取移除的元素后面元素的个数，后直接在elementData做System.arrayCopy的原地拷贝，后长度-1.

### 为什么ArrayList的对象数组 elementData 使用了transient修饰？

因为elementData在序列化时可能会有空值，所以ArrayList自身再次实现了readObject反序列化/writeObject序列化 私有方法



## LinkedList

### LinkedList的基本构造

LinkedList是由Node元素组成的双向链表，Node包含item，prev、next。LinkedList存在first和last节点对象方便数据插入。

### LinkedList的添加元素的过程

LinkedList默认将元素添加到链表的末尾，先是获取last节点，然后将新元素包装为Node并设置为tail，然后将last的next节点为设置为新元素的tail

### LinkedList移除元素的过程

- 移除位置：LinkedList会从first向last遍历，然后做一个unlink操作：比如要删除x节点，就把x节点的前驱的后继设置为x节点的后继，然后将x后继的前驱设置为x的前驱。只移除最低位置索引的元素。

- 直接移除对象：调用removeFirst从头遍历

### 可以用for循环遍历LinkedList吗

不推荐。因为每次LinkedList获取元素都要循环判断元素在链表前后半段，我们在for循遍历时每一次循环都会遍历半个List。所以推荐用iterator去直接拿到我们的元素。

### LinkedList在遍历时怎么确定元素在链表的前段还是后段

LinkedList在get一个指定索引的元素时，是会根据传入的索引值去遍历整个链表的，然后再据size >>1 再决定从first还是last元素还是遍历。

### ArrayList和LinkedList插入性能对比

LinkedList插入到头部或者中部效率是要比同样长度的ArrayList高的。

但是在不扩容的时候，插入元素到ArrayList的尾部肯定是效率更高的，因为省去了LinkedList链接和实例化新Node和连接新节点的过程。



## 其他

### 说下java.util.Iterator

Iterator是访问集合的方式，可以用它来迭代ArrayList和HashSet。next()/hasNext()/remove()/forEachRemaining()

Collection继承的Iterable内含Iterator.

LinkedList的iterator内即为链表遍历（实现方式为 lastReturned和next两个Node）

### ArrayList内实现Iterator的方式

设立2个索引，一个是当前被遍历的元素的位置的索引‘cursor’（调用next()会返回的那个索引，同时增加1），另一个是上次调用next返回的索引‘lastRet’。所以lastRet往往比cursor少1，即使在forEachRemaining()中。但是在调用remove()时，cursor需要相应的-1之外，不应当可以再次删除，所以lastRet会被赋值为-1;

#### 代码是否会报错

```java
private class Demo1 {
    
    public void run() {
        ArrayList<String> list = new ArrayList<String>();
        list.add("a");
        list.add("b");
        list.add("c");
        list.add("d");
        list.add("e");
    
        for (String item : list) {
            if (item.equals("d")) {
                list.remove(item);
            }
        }
    }
    
}

```

可能你会觉得会报ConcurrentModificationException，实际上不会报错。

首先ArrayList的for循环在本质上就是Iterator循环。

比如存在“f”，那么如上错误应当发生在第5次循环“e”时，iterator在调用next()时会先检查迭代器内部的expectedModCount是否和ArrayList本身的modCount相等。但是因为调用的是list的remove(),所以不会去改变迭代器的expectedModCount，所以会在检查时报错。

然鹅，因为你删除的是倒数第二个元素，迭代器在判断hasNext就因为cursor和size不一致，就已经返回了false，也就没机会去校验modCount了。





