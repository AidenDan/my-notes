2019.08.23笔记
顺序语从上往下从左往右(默认执行)
选择语句 
循环语句/发分支语句 让某个特定的代码重复执行；当执行到if时判定为true则执行语句；判定为false则跳出语句（必须先判定）
if...else if...else.只要一个条件满足，结束所有语句。
switch匹配case值，能匹配就执行语句。只执行一次就结束。
作业：今天的代码敲两边
键盘录入 Scanner scanner =new Scanner(System.in);
         System.out.println("请输入");
         int i = scanner.nextInt();
赋值时左边必须为变量    

public class Demo1 {
    public static void main(){
        Scanner scanner =new Scanner(System.in);
        System.out.println("请输入");
        int i = scanner.nextInt();
        Scanner scanner1 =new Scanner(System.in);
        System.out.println("请输入");
        int p = scanner.nextInt();
        if (i>=5000){
                        if (p<100){
                            System.out.println("我就去云南旅游");
                        }
        }
    }
}

char类型与数字进行+必需把char字符按照ASCII码转化成数字再进行+。几个char类型进行运算必须先转换为数字。
和字符串类型进行+都为拼接。
Demo34中为什么一输入小数就报错。但输入整数可以运行。
nextint()对应输入的数据为整数；nextdouble()对应输入的数据为双精度浮点数。
字符串比较值是否相等用.equals()，==比较的是字符串地址是否一样。
 找出a/b/c中三个数最大值
 a>b且a>c最大值为a
 a>b且a<c最大值为c
 a<b且a>c最大值为b
 a<b且b<c最大值为c
 a<b且a<c,b>c最大值为b
 a<b且a<c,b<c最大值为c
 在Java中判定if  a>b 再比较a,c大小;else  a<b  再比较b,c大小关系
 在while语句中，当（）条件为真时则执行{}中语句；为假则跳出while循环执行{}后面的语句；
 如果对条件的区分只有a,b两类(ture 或 false)，那么用if...else...进行分支。如果对条件的区分有a,b,c,d,...多类，
 那么用if...else if...else if......else进行分支。
 在for语句中，当boolean为真时，先执行{}中的语句，后自增。
 for语句中遇到break时跳出当前循环语句，进入另一个循环语句。遇到continue时，continent下面语句不执行，程序不跳出循环，继续自增。


 2019.08.25
 for循环嵌套为难点
 for循环体中，判断条件语句为true时执行循环体；
 每个程序都有多个代码方式，看个人喜好
求阶乘，定义一个变量ji
for中i未被定义；while中i被定义；
变量的作用域：其所在的{}内；
叠纸时，每叠一次厚度*2
do...while语句，先执行一次循环体；特点为至少执行一次；基本和while一致；
print时去ln表示不换行，加ln表示换行
for嵌套中；for内循环控制列数；for外循环控制行数
内循环分两个部分*部分和空白部分
用for循环构建图形时，*从左往右填充，若为空白则用空格填充。

int n=18311;
System.out.println("个位 "+ (n % 10));
System.out.println("十位 "+ (n / 10)%10);
System.out.println("百位 "+ (n / 100)%10);
System.out.println("千位 "+ (n /1000)%10);
万位=n/10000;


2019.08.26
有明确的循环次数时首选用for循环；没有明确的循环次数时用while循环。
用for循环对数组进行排序
上课的例题代码自己敲两遍
在语句下面加System.out.println();表示换行输出
在for语句循环嵌套语句中
for(){
for(){}...内循环体中的for执行完后必须先执行语句n才会跳到去执行外循环中的for语句
语句n;
}
当为true时，for循环内打印；当为false时，跳出for循环外打印
在打印后面加/r;/n表示换行
/t 相当与6个空格；+"/t"相当与在后面加6个空格；
53 64 74 63 73 62
 75

 2019.08.27 周二
 变量用于存储数据，同理数组也用于存储数据（一组数据类型相同的数据）
 数组是存储多个变量（元素）的东西（容器）。但数组内的数据类型必须要一致。
 数组是存储同一个数据类型多个元素的集合（容器）；可存储基本数据类型，也可存储引用数据类型
 定义;方法一：数据类型[] 数组名; int[] arr;
 数组的初始化：给变量赋值；
 数组动态初始化：只给定数组的长度，由系统给元素默认值
 数据类型[] 数组名=new 数据类型[arr.length];

 数组的静态初始化：给出每个元素的初始值，长度由系统分配；
 不确定数据类型时，整数用int，小数用double；
 数组内存地址;数组数据类型+@+16进制数；用于判定两个数组是否相等；
 所有new出来的东西都会在堆中开辟一块空间
 程序启动会调用main方法到栈中；
 数组的索引=下标
 获取数组的元素。数组名[索引值]。索引：数组在定义时，系统会为数组从左到右定义一个
 （0——数组长度-1）的值
 数组的动态赋值；

 数组的静态初始化:int[] arr =new int[] {1,2,3}; 数据类型[] 数组名 =new 数据类型[] {};
 简化版：int[] arr ={1,2,3};
 数组常见异常：数组下标越界；数组空指针异常，arr=null 数组为空;
 获取数组的长度    数组名.length
 直接system.out.println(arr)打印的为数组的地址；

 数组的使用

 增强for循环 for(元素的数据类型 变量名：数组名) arr.iter

 获取数组的最大值；用第一个元素依次与后面的元素相比。定义第一个数为max，后面的数依次与max相比

 数组中元素对调，需要一个空变量；

 数组中元素排序；冒泡排序法，相邻的两个元素进行比较大的放后面，最后一个是最大值
 最后一次比较时应该满足从小到大的顺序；（第几次比较）外循环定义排序的次数；内循环定义两两比较次数
 外循环比较arr.length-1次；内循环比较arr.length-1-i次；

 遍历一个数组中的各元素的快捷方式：for (int i:arr){
           System.out.print(i+"  ");
       }

 2019.08.28 努力过后才知道许多事情坚持坚持就过来了！
 day08-java基础语法
 数组的长度一旦确定就不可以发生改变。要改变数组长度必须创建新数组。

 Arrays类的使用。Arrays是数组操作的工具类；
 功能/方法：equals（arr1,arr2）：比较两个数组的元素内容值是否相等，顺序也必须一致；==比较的数组的地址；返回false或者true
 Arrays.sort（arr）/(arr,index,index)：对数组进行排序；默认从小到大排序；按照索引进行局部排序，包括前索引元素，不包括后索引元素。[..)无返回值
 Arrays.toString(arr):把数组的元素转成字符串；
 Arrays.fill（arr，val）：用一个新元素替代数组中的所有元素；无返回值；
 Arrays.copyOf(arr,length):复制数组；不按照索引复制，而是按照长度进行复制
 Arrays.copyOfRange(arr,index,index):用于局部复制，按照索引进行复制。包括前索引元素，不包括后索引元素。[..)
 Arrays.binarySearch(arr,val):查找元素的索引；查找索引前必须对数组进行排序；

 二维数组：其元素为数组
 定义：数据类型[][] 数组名；
 初始化方式：
 动态初始化：数据类型[][] 数组名=new 数据类型[外数组长度/盒子数][内数组长度/盒子中钥匙把数];
 静态初始化：数据类型[][] 数组名={{}，，，，}
 二维数组for循环中i表示盒子数，arr[i]表示盒子i中的钥匙把数；

 2019.08.29 周四 努力过后才知道许多事情坚持坚持就过来了！
 二维数组的遍历：每输出一个一维数组中的元素就换行；从盒子中拿钥匙，把一个盒子中的钥匙拿完再去拿另一个盒子中的钥匙
 ，同理给盒子中放钥匙时把一个盒子放满再去放另一个盒子。
 强制遍历二维数组：(只适用于每个一维数组元素相同时)for(int[] arr1:arr2){ 
            System.out.print(arr1[0]+"\t");
            System.out.print(arr1[1]+"\t");
            System.out.print(arr1[2]+"\t");
            System.out.print(arr1[3]+"\t");
            System.out.print(arr1[4]+"\t");
            System.out.print(arr1[5]+"\t");
            System.out.println(); }
            
方法的概述：方法==函数；完成特定功能的代码块；
格式：修饰符 返回值类型 方法名（参数列表）{
方法体；
return 返回值类型；} 
ruturn有结束方法的作用；

详解：
修饰符：目前先用public static
返回值类型：数据类型
方法名：方法的名称 小驼峰 见名知意

定义两个明确：返回值类型、参数列表
方法放在主方法外面；方法不能嵌套；方法不调用就不执行；

无返回值无参数方法的调用：
单独调用；jx()；  直接调用

无返回值有参数列表的调用；
jx(4,5) ;直接调用

有返回值有参数的调用；
输出调用；
赋值调用 

在调用方法时变量就初始化；形参用于接受实参；
main方法被JVM调用；为程序入口；
1.方法不调用不执行；
2.方法与方法是平行关系，不能嵌套；
3.方法调用时参数不能传递数据类型；
4.定义时每个参数都要带数据类型且用“，”隔开；
5.如果方法有明确的返回值类型时，一定要有return返回值；
6.如果方法没有明确的返回值类型，可以用return，但是不能带返回值；

方法的重载：
在同一个类中，方法名相同，参数列表不同，与返回值无关；
参数列表：个数、数据类型

参数传递：
基本数据类型作为参数传递时，值不会受方法体改变；
引用数据类型作为参数传递时，内容会随着方法体的改变而改变；  

在同一个main下定义多个方法时，用同一个方法名,但参数类型不能相同，否则重名；
Math.pow(x,y),表示求x的y次方；
int n=(int)(Math.radom()*m),表示在10中产生随机数； 

ctrl+alt+l自动对其文件格式；
 byte short int long//基本数据类型
//                float double
//                char
//                boolean*//**//**//*
//         *//* String s = "123";String属于符合引用数据类型，但是和一般的引用数据类型不同，
//         * 它new出来的数据在常量池中（常量池用来存储常量，常量池中的数据是不会改变的）;堆里面用来存放对象值/地址；new出的数据都有一个
//         * 指定地址，同一个常量公用一个地址；基本数据类型和String只有一个地址在常量池中，引用数据类型都是赋值的地址；
          String s = "123"
//        String b = s;*//*
       此时 b==s;因为在常量池中b,s的存储地址相同；
//        b ="1";*/
////        String s = "123";
////        String b = new String("123");
////        String c = new String("123");
             此时b!=c;因为栈中b,c的存储地址不一样；
////        System.out.println(s == b);
////        System.out.println(c == b);

 2019.09.01
 面向对象(OOP)：
 语法部分属于面向过程部分；
 面向对象包括：封装、继承、多态。面向过程与面向对象是相对的。
 面向过程需要我们亲力亲为（自己做），我们必须得自己实现每个细节
 面向过程对我们来说很累，面向过程关注每个步骤

 面向对象不需要我们亲力亲为，我们只需要指挥别人去干；
 面向对象我只提出要求，只关注结果
 面向对象即指挥别人（对象）做事情

 类的属性：
 类的行为：即方法
 new出来的东西代表现实中的实物
 定义在方法内的为局部变量；定义在类中但在方法的外部为成员变量，成员变量作用域为整个类
 ，因此我们可以在类中的任意位置使用；
 String的默认值为null；
 c.color，我会去找这个空间color变量；
 c.run为调用car中的run方法；
 只要我们在代码块中new几次，就会在堆中产生对应的几个对象，我们具体使用哪个对象，通过.前面的
 引用变量名来区分；
 类是对某一类事物的抽象描述，而对象用于表示现实中该类事物的个体；
 属性：体现到代码中就是成员变量；
 行为：体现到代码中就是成员方法；
 体现到具体的现实生活的人通过new来体现
 人 人= new 人();
 人.name="张三"；
 人.age= 10;
 一个{}表示一个代码块；

 万物皆对象；对象是具体到某一个事物的。
 类的举例：鱼类、车类、饮料
 对象的举例：(鲤鱼、鲫鱼、鲈鱼）大众、百事可乐

 从今天开始在类中创建的方法不写static;

 测试类：只创建对象和调用成员
 ①先创建不同的类（实现把方法放在不同的类中），那么在任何程序中都可以调用。
 ②调用main方法创建一个测试类，来调用创建的类；类自己不能运行；

 面向过程不利于维护，因为所有方法都在一个程序中。

 对象的使用：①创建对象 类名/引用名= new 类名（）；
 使用成员变量：对象名.变量名；
 使用成员方法：对象名.方法名；
 类的作用;通过创建一个个类，把一个个的属性和方法放在类中。在main方法中执行时，直接
 调用对应的类属性，类方法即可。

 成员变量在创建时系统自动赋值；

 2019.09.02
 封装指的是带有{}的语句，例如方法public void sort(int[] arr){
                                                                  方法体；}  
 其中方法体就被封装起来了。
 类也是一个封装体，封装了 属性（成员变量）和行为（成员方法）    
 封装提高的代码的复用性(效率)；隐藏细节；提高安全性；
 通过private关键字来实现封装；
 private 类型 变量名；
 private只能用在成员变量上，不能用在局部变量上；
 加私有private这个成员只能在类的内部使用，不能在类的外部使用；通过对象名.成员变量的
 方法不能够调用； 

 if语句，for语句不能写在类中；只能写在方法中；类中只能写成员变量

 this关键字；

 变量访问的就近原则，先找局部，局部有了就使用局部变量，局部变量没找到再去找成员变量；

 当局部变量和成员变量重名时，我们通过this来区分；在变量前面加个this，使用this来访问成员变量；
 this.age=age,this这边的age传递给成员变量；this区分成员变量和局部变量；
 谁调用这个方法this就指向谁,p.setAge中p调用setAge这个方法，那么·this就指向p，可理解为this=p；                                                        
 把p的地址传递给this；当访问成员变量时，虽然没有写this，隐式的也有this。

 继承：程序中，事物之间有所属关系，我们就让其中一个事物继承另外一个事物；
 继承指的是类与类之间的关系；通过extends关键字来让两个类产生关系；
 public class Teacher extends Person{
                }
 指的为Teacher类继承了Person类中的属性，方法 
 继承特点：子类（Teacher）会自动继承父类（Person）中的所有非private修饰成员（成员变量和成员方法）
 继承后子类既有自己的属性和方法也有从父类中继承过来的属性和方法；
 Java只支持单继承不支持多继承：一个类只能继承一个类。因为当父类重名时，子类无法确定继承哪一个；
 一个类可以被多次继承，一个父类可以有多个孩子；
 类B继承类A，类C继承B，那么C间接继承类A;
 JAVA中所用类（除了Object）的都直接或间接继承Ojject类；Object类是JDK中定义好的一个类；  
 public class Demo/*extends Object*/{}

 当子类与父类的变量名/方法名  相同时，遵循打印的就近原则，先找子类，子类中有就打印子类，打印子类；
 父类也叫超类（super）;要想打印父类使用super.number
 通过super来访问直接父类的非私有成员；而this访问的是本类的成员变量
 注意：
 ①继承中不会产生父类对象，因为没有new Father()，那么会将父类的成员变量以及子类的成员
 变量都放在子类对象中，通过虚线隔开；
 ②我们通过this来寻找（调用）子类的成员，通过super来寻找（调用）父类的成员；
 通过super.show()来调用父类的方法；

 Car c= new Car就像int[] arr=new int[3]在内存中存储方式一样，new出来的东西首先在堆中产生一个空间;
 像数组的大空间中分成3个小空间一样，对象也会形成小空间，只不过里面存放属性；new Car的地址就是c指向
 的地址c.color表示对象c调用Car类中color属性；调用方法入栈一定会在栈中产生一个新的空间

 方法的重写：当子类的方法名与父类的方法名一模一样叫做方法的重写，子类的方法重写了父类的方法
 应用场景：我们向基于父类的原有的功能提供更强的功能，我们考虑重写。既要保留
 父类的方法，也要在子类方法中加入新的功能。

 方法重写的条件：①必须要有继承关系，因为重写是针对子类的方法重写父类的方法
②重写要求子类的方法权限>=父类的方法权限
Java权限：public>默认>=protected>private
③重写要求子类的方法的方法名和 ，形参列表、返回值类型和被重写的父类的方法和形参列表、返回值类型 完全一致
 ④我们可以在子类的重写的方法上加上@Override（注释），要求子类强制重写父类方法。

 abstract抽象类；OOP面向对象
 抽向方法的由来：
 由于在我们的形状类中，这个形状是不确定的，因此求周长的方法体和求面积的方法体都无法写；
 因此我们就不写这两个方法的方法体，但是需要在返回值类型前面加上abstract；
 抽象类的由来：
 含有抽象方法的类一定是抽象类（在class的前面加上abstract修饰符）；
 Shape是一个抽象类，不能创建对象；
 形状是抽象的。
 在长方形类中需要重写所有的抽象方法，才能保证长方形类不是抽象类；
 抽象方法一定定义在抽象类中；抽象方法没有方法体；
 抽象类中可以定义抽象方法，也可定义非抽象方法；抽象类中可以没有抽象方法；
 abstract和private不能共存

 不用private谁都能赋值，
 private int age;将age变为私有；用private进行封装，并对外提供一个公共的访问方式；
 封装：
 概述：隐藏类的属性和实现细节，仅对外部提供公共的访问方式；
 好处：提高了安全性；提高了代码的复用性；
 原则：类的所用属性必须封装，对外提供访问方式；setAge,getAge;先设置后获取；
 private关键字：私有的，一个权限修饰符；修饰成员变量和成员方法；

 构造：
 类中默认自带一个new
 重写构造方法：给成员变量初始化的；例如：Student st=new Student();
 new Student()调用构造方法产生对象，为对象名称，为匿名对象
 当我们不给该类写构造方法时，系统给出一个默认的构造方法；构造方法是一种特殊的方法；
 当我们给出构造方法时，系统就不会给出任何的构造方法；
 构造方法可以重载；
 格式：
 修饰符 方法名（）{
 方法体；
 }
 特点：
 方法名和类名相同，没有返回值，连void都没有；

 给成员变量赋值的方法
 两种：setter；构造方法；

 类的标准写法：
 public class Student{
 private int id;
 private String name;
 private String sex;

 public Student(){"无参数构造法"
 }

 public Student(int id,String name,String sex){
 "全参构造法"}}


 ？
 public class Student {
    //成员变量
    private int id;
    private String name;
    private String sex;
    //构造方法
    //无参构造
    public Student(){
        System.out.println("无参构造方法");
    }
    public Student(int id,String name,String sex){
        this.id=id;
        this.name=name;
        this.sex=sex;
        System.out.println("全参构造方法");
    }
    //成员方法
    //id
    public void setId(int id){
        this.id=id;
    }
    public int getId(){
        return id;
    }
    //name
    public void setName(String name){
        this.name = name;
    }
    public String getName(){
        return name;
    }
    //sex
    public void setSex(String sex){
        this.sex = sex;
    }
    public String getSex(){
        return sex;
    }
}

Student st=new Student();在内存中做了哪些事情
一。加载Student.class文件进入内存；
二。在栈中加载st

static关键字：静态属性，静态方法；
特点：所有对象共有这个属性；其中一个改变所有改变；
静态成员又称为类成员；成员变量和成员方法又称之为对象成员；
静态成员在无对象下也可调用，静态成员优先于对象存在；静态成员又称之为类成员；
static可修饰成员变量和成员方法； 
类名.成员名   对象名.成员名

匿名对象:没有名字的对象Student st=new Student();
 new Student()调用构造方法产生对象，为对象名称，为匿名对象
 匿名对象只在当前行使用一次，就被垃圾回收器回收；节省空间

 代码块：{}
 {}，更具位置不同，就产生了不同的代码块
 局部代码块在调用方法时会执行局部代码块；成员代码块在每次执行构造方法之前先执行成员代码块
 ；静态代码块在类加载的时候就会被执行；

 重写构造器后就不需要在测试类中给成员变量赋值了；每创建一个类就会形成一个默认构造器；

 2019.09.03
 有的状态和行为应该属于类型，不属于对象；static修饰的资源属于类级别的，而不是成员级别；
 static修饰的成员直接属于类，不属于对象，所以可以直接使用类访问static成员；
 static成员随着类的加载而加载，优先于对象存在；
 static修饰的成员被该类型的所有的对象所拥有；
 直接用类名访问static成员；
 static方法中只能访问static成员；但非static方法可以访问static成员；
 有些状态和行为（不可能属于某一个具体对象）就属于类，不属于对象；


 继承：
 父类==基类==超类；
 格式：class子类extends父类；
 耦合性增加；
 是多态的前提；
 子类继承父类的所有非私有成员；
子类不能继承父类的构造方法；但在调用子类构造方法前
可以用super关键字访问父类构造方法；
不能因为部分功能就去继承；只有当A属于B类时才去继承；
单继承，多层继承；
当子类与父类的变量名称一致时，继承采用就近原则；
查找方法：
①先找子类，有就用，没有再找父类；
②父类有就用，没有就报错；
super关键字：
super和this的用法是一致的
继承的时候不会继承父类的构造方法，那么子类要想继承父类的构造方法，
那么在子类的构造方法中用super关键字来继承；

无参构造法的第一行默认为super（）；默认不写；
子类在
一个Java文件中只能有一个public修饰类，且这个类名与文件名相同；

父类与子类的先后执行顺序；

方法重写：子类与父类的方法申明一模一样；
方法重载：在同一个类中，方法名相同，参数列表不同，与返回值无关


final修饰关键字：
最终的，修饰类、变量、方法；
修饰类：类为最终类，此类不能被继承；
修饰变量：变量变常量；一旦有值就不能被改变；
修饰方法：方法不能被重写；父类有这个方法子类就不能有；

2019.09.04
调用子类构造方法前前必须先调用父类，一直到级别最高的父类；
类的标准写法，成员变量，构造方法，成员方法，因此在执行构造方法前必须先执行成员代码块；
在调用构造方法时，与子类参数列表相同的父类的构造方法必须先调用执行；
在执行程序时，先执行静态代码块（父类的、子类的），每个类中的静态代码块只执行一次；

匿名对象格式：new User()   每个匿名对象都会在堆中开辟一个新的存储空间；用new User()来
调用构造方法方法；例如new User(1,"jack","love").show();其实有两步操作，一是调用构造方法并给成员变量赋值，
二是调用了成员方法show();
匿名对象只用一次；

用super调用父类构造方法相当于把子类的构造方法重写了，默认的构造方法不复存在
继承是类与类之间的关系，与测试类不产生继承关系；

抽象类:无方法体，子类必须覆盖父类；抽象类必须作为父类，必须得有子类； 

2019.09.05
接口：接口属于抽象类，接口中的所有方法都是抽象的；
接口中没有构造器，不能new;
软加接口：程序代码，特殊的类；
在Java中接口表示一种约束规范，多个类共同具有的特征；  
USB也是一种规范协议，接口，此时USB插槽可以看做类的实例；完成了规范和实现的分离
USB协议只关心USB插槽是否遵循协议，并不关心USB插槽是如何制造实现的；   
层次范围：接口层次>类层次>对象层次；
接口只定义了类应当遵循的规范，却不关心这些类的内部数据和功能的实现细节；  
JDBC用来连接数据库的
面向接口编程：接口和实现类体现了真正的多态；
在Java中最小的程序单元就是类，接口是一个特殊的类。Java中接口表示规范，用于定义一组
抽象方法，表示某一类事物必须具备的功能，要求实现类必须来实现该接口并提供方法实现；
引用类型分三种：类、接口、数组；
[public] interface 接口名{}
接口中的成员：
接口中没有构造器，不能new;
接口中定义的成员变量实质是全局静态常量，默认使用public static final来修饰
定义的方法都是公共抽象的，默认使用public abstract来修饰；
public sbstract void walk();
接口中的内部类都是公共的静态的内部类，默认使用public static来修饰内部类；
public static interface Abc{}
标志接口；
常量接口；
java文件通过Javac.exe编译生成class文件，class文件通过Java.exe来执行，最后看到执行结果；
接口与接口之间只能是继承关系：使用extends来表示；
接口和实现之间只能是实现关系（继承关系），使用implements来表示：
 接口的实现者：实现类
 类实现接口的语法：一个类可以实现多个接口，从而也弥补了类的单继承问题。
 [修饰符] class 类名 (extends 父类) implements 接口1，接口2{}
 严格上成为实现关系，是一种特殊继承关系，接口是实现类的父类，现实类就是接口的子类  
接口 变量=创造实现类对象；把实现类类型变量赋值给接口类型变量//体现了多态思想；
类可以多实现接口；一个类实现多个接口

*****************************************
### **MySQL笔记：**

版本5.5-->服务名MYSQL4-->密码123456-->端口3307-->用户名root;
版本5.7-->服务名MYSQL-->密码123456-->端口3306-->用户名root;

* 数据库中一旦开启事物，那么对数据的修改操作并没有保存在磁盘上面，除非提交事物；在提交事物前可以进行回滚，撤销所有操作回到操作前的状态；没有开启事务，那么所有操作就已经保存在磁盘上面了

1.mysql数据库中create database emp character set utf8;drop database emp

### 2-->6为对表结构的修改：

2.alter table emp **add** 姓名 varchar(50);

3.alter table emp **drop** 姓名；

4.alter table emp **change** name 姓名 varchar(50);

5.alter table emp **modify** gender char(2);  

6.alter table emp **rename **(to) emp1;

------------------------------------------------------------------------------------------

### 1-->对表中数据的修改

1.insert into emp values(,,,)

2.update emp set name=name1 where id="1";

3.delete from emp where name="name1";

### **----通过创建JDBCUtils工具类来获取连接对象**

```java
package com.dan.connection;

import JDBCUtils.JDBCUtils;


import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class TestCon02 {
    public static void main(String[] args) {
        /*用JDBCUtils工具类来创建连接对象*/
        Connection con = JDBCUtils.getcon();
        /*用con创建发送sql语句对象*/
        try {
            Statement sta = con.createStatement();
            /*写sql语句*/
            /*一、查询所有员工的信息*/
            ResultSet rs1 = sta.executeQuery("select * from emp");
            /*next相当于结果集中的指针，指向每一个记录*/
            while(rs1.next()){
                System.out.println(rs1.getString("eid")+"  "+rs1.getString("ename")+"  "+rs1.getString("esex")+"  "+
                        rs1.getString("estartime")+"  "+rs1.getString("epay")+"  "+rs1.getString("did"));
            }
            String str = "select * from dept";
            /*返回dept表中的结果集，其实就是一张表；可以理解为一条记录就是一个对象，而字段就是对应的属性*/
            ResultSet rs = sta.executeQuery(str);
            while(rs.next()){
                /*如果字段为int类型，那么可以调用getint,输入对应的列数,string类型就用getString*/
                System.out.println(rs.getString("did")+"  "+ rs.getString("dname")+"  "+rs.getString("dtel"));
            }
            /*查询完毕后要断开连接，释放资源*/
            JDBCUtils.closeAll(rs,sta,con);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

```

### **---反射机制**

![](C:\Users\Administrator\Desktop\反射机制.png)

### **`---线程执行过程`**

![](C:\Users\Administrator\Desktop\线程.png)

![](C:\Users\Administrator\Desktop\线程执行过程.PNG)

### **正则表达式**

![](C:\Users\Administrator\Desktop\正则表达式.png)

------

## **JDBC**

一、创建JDBCUtils类来封装四大连接对象，通过静态方法来获取Connection对象。同时里面封装关闭连接释放资源的方法。①创建配置文件，包含四大连接对象；②创建工具类。

二、①将数据库中的表封装成java类，类中属性为字段，设置对应属性的set/get方法，无参构造，全参构造，获取表记录的实例化对象；②创建接口来约束CRUD操作；③在Dao层创建工具类来实现接口，重写增删改查方法；④在测试类中进行操作。

### 1、创建JDBC工具类

```java
package utils;

/**
 * @author LIKUS
 */

import java.sql.*;
import java.util.ResourceBundle;

/**
 * 创建一个JDBCutils工具类
 * */
public class JDBCUtils {
    /*把需要连接数据的属性，定义成变量*/
    /*驱动的全路径*/
    private static String className;
    /*数据库的路径*/
    private static String url;
    /*数据库的用户名*/
    private static String user;
    /*数据库的密码*/
    private static String pwd;

    /*把配置文件中的属性加载进来，赋值给全局的静态变量*/
    static {
        /*读取配置文件db：把文件当做java类来读取;必须在src目录下面;*/

        ResourceBundle in = ResourceBundle.getBundle("properties/db");
        /*根据配置文件的名字，获取配置文件中属性的值 调用getString的方法*/
        className = in.getString("className");
        url = in.getString("url");
        user = in.getString("user");
        pwd= in.getString("pwd");
    }
    /*把加载驱动程序写在静态代码块*/
    static {
        try {
            Class.forName(className);
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
    /*获取数据库连接对象*/
    public static Connection getcon(){
        try {
            return DriverManager.getConnection(url,user,pwd);
        } catch (SQLException e) {
            e.printStackTrace();
            /*出现了异常要处理，不然会报错!*/
            throw new RuntimeException("数据库连接失败！");
        }
    }
    /*关闭连接，释放资源*/
   public static void closeAll(ResultSet rs, Statement sta, Connection con){
       if (rs != null){
           try {
               rs.close();
           } catch (SQLException e) {
               e.printStackTrace();
           }
       }
       if (sta != null){
           try {
               sta.close();
           } catch (SQLException e) {
               e.printStackTrace();
           }
       }
       if (con !=null){
           try {
               con.close();
           } catch (SQLException e) {
               e.printStackTrace();
           }
       }
       }
     }
```

### 2、配置文件

```java
# properties�ļ�Ϊ���Ե������ļ� ����Ĵ����Ӷ���
className=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3307/employee1?characterEncoding=utf8
user=root
pwd=123456
```

### 3、获得数据库中表的实体类

```java
package domain;

import java.util.Date;

public class Emp {
    /**
     * Emp类中封装了表emp中的字段(属性)
     * */
    private int eid;
    private String ename;
    private String esex;
    private java.util.Date estartime;
    private float epay;
    private int did;

    public Emp() {
    }

    public Emp(int eid, String ename, String esex, java.util.Date estartime, float epay, int did) {
        this.eid = eid;
        this.ename = ename;
        this.esex = esex;
        this.estartime = estartime;
        this.epay = epay;
        this.did = did;
    }

    public Emp(String ename, String esex, Date estartime, float epay, int did) {
        this.ename = ename;
        this.esex = esex;
        this.estartime = estartime;
        this.epay = epay;
        this.did = did;
    }

    public int getEid() {
        return eid;
    }

    public void setEid(int eid) {
        this.eid = eid;
    }

    public String getEname() {
        return ename;
    }

    public void setEname(String ename) {
        this.ename = ename;
    }

    public String getEsex() {
        return esex;
    }

    public void setEsex(String esex) {
        this.esex = esex;
    }

    public Date getEstartime() {
        return estartime;
    }

    public void setEstartime(Date estartime) {
        this.estartime = estartime;
    }

    public float getEpay() {
        return epay;
    }

    public void setEpay(float epay) {
        this.epay = epay;
    }

    public int getDid() {
        return did;
    }

    public void setDid(int  did) {
        this.did = did;
    }

    @Override
    public String toString() {
        return "Emp{" +
                "eid=" + eid +
                ", ename='" + ename + '\'' +
                ", esex='" + esex + '\'' +
                ", estartime=" + estartime +
                ", epay=" + epay +
                ", did=" + did +
                '}';
    }
}

```

### 4、创建DAO接口

```java
package impl;

import domain.Emp;

import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.List;

public interface DaoImpl {
    /*在接口里面定义好CRUD的方法，让dao来实现，那么就可以避免方法被篡改*/
    /*第一、传入要添加的emp对象insert方法*/
    int empInsert(Emp e) throws SQLException;

    /*第二、传入要更新的emp对象update方法*/
    int empUpdate(Emp e) throws SQLException;

    /*第三、delete方法,根据员工的eid删除*/
    int empDelete(int eid) throws SQLException;

    /*第四、query方法查到所有对象*/
    List<Emp> empQuery() throws SQLException;

    /*第五、query的根据ename字段的模糊查询方法*/
    List<Emp> empQueryLike(String ename) throws SQLException;
}
```

### 5、创建工具类来实现CRUD

```java
package dao;

import domain.Emp;
import impl.DaoImpl;
import utils.JDBCUtils;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.text.SimpleDateFormat;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

/*EmpDao为工具类，提供CRUD方法,调用这个方法就可得到查询结果*/
public class EmpDao implements DaoImpl {
    /*获取java util下的date*/



    @Override
    public  int empInsert(Emp e) throws SQLException {
        /*获取emp表的对象*/

        /*获取连接对象*/
        Connection con = JDBCUtils.getcon();
        PreparedStatement ps = con.prepareStatement("insert into emp values (?,?,?,?,?,?)");
//        ps.setObject(1,emp.getEid());
        ps.setObject(1,e.getEname());
        ps.setObject(2,e.getEsex());
        ps.setObject(3,e.getEstartime());
        ps.setObject(4,e.getEpay());
        ps.setObject(5,e.getDid());
        int i = ps.executeUpdate();
        JDBCUtils.closeAll(null,ps,con);
        return i;
    }

    @Override
    public int empUpdate(Emp e) throws SQLException {
        /*一、获取连接对象*/
        Connection con = JDBCUtils.getcon();
        PreparedStatement ps = con.prepareStatement("update emp set epay=? where eid=?");
        ps.setObject(1,12000);
        ps.setObject(2,e.getEid());
        int i=  ps.executeUpdate();
        JDBCUtils.closeAll(null,ps,con);
        return i;
    }

    @Override
    public int empDelete(int eid) throws SQLException {
        /*根据eid删除对象*/
        Connection con = JDBCUtils.getcon();
        PreparedStatement ps = con.prepareStatement("delete from emp where eid=?");
        ps.setObject(1,eid);
        int i = ps.executeUpdate();
        JDBCUtils.closeAll(null,ps,con);
        return i;
    }

    @Override
    public List<Emp> empQuery() throws SQLException {
        /*全部查询，得到所有结果*/
        /*把表中的数据取出来放在，对象取出来，放在List集合中*/
        List<Emp> empList = new ArrayList<>();
        Connection con = JDBCUtils.getcon();
        PreparedStatement ps = con.prepareStatement("select * from emp");
        ResultSet rs = ps.executeQuery();

        while (rs.next()){
            Emp e = new Emp();
            e.setEid(rs.getInt(1));
            e.setEname(rs.getString(2));
            e.setEsex(rs.getString(3));
            e.setEstartime(rs.getDate(4));
            e.setEpay(rs.getFloat(5));
            e.setDid(rs.getInt(6));
            empList.add(e);
        }
        JDBCUtils.closeAll(rs,ps,con);
        return empList;
    }

    @Override
    public List<Emp> empQueryLike(String ename) throws SQLException {
        ResultSet rs =null;
        /*查询的结果放在List集合中*/
        List<Emp> empList = new ArrayList<>();
        /*获取连接对象*/
        Connection con = JDBCUtils.getcon();
        /*查到所有的结果*/
        String sql= "select * from emp where 1=1";
        if(ename !=null && !ename.isEmpty() ){
            sql = sql+ " and ename like ?";

        }
        PreparedStatement ps = con.prepareStatement(sql);
        if(ename !=null && !ename.isEmpty()){
             ps.setObject(1,"%"+ename+"%");
        }
        rs = ps.executeQuery();
        while (rs.next()){
            Emp e = new Emp();
            e.setEid(rs.getInt(1));
            e.setEname(rs.getString(2));
            e.setEsex(rs.getString(3));
            e.setEstartime(rs.getDate(4));
            e.setEpay(rs.getFloat(5));
            e.setDid(rs.getInt(6));
            empList.add(e);
        }
        JDBCUtils.closeAll(rs,ps,con);
        return empList;
    }
}
```

### 6、 创建测试类来实现操作

```java
package com.test;

import dao.EmpDao;
import domain.Emp;
import org.junit.Test;

import java.sql.SQLException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.List;
import java.util.Scanner;

public class Test01 {
    /*@test 测试单元注解，相当于主方法*/
    @Test
    public void test(){
       /* System.out.println("hello"+1234);
        Scanner scan = new Scanner(System.in);
        System.out.println("输入一个数：");
        String i = scan.nextLine();
        System.out.println(i);*/
        Scanner input = new Scanner(System.in);
        System.out.println("请输入用户名：");
        //输入一行数据
        String username = input.nextLine();
        System.out.println("username"+username);
    }

    @Test
    public void test01() throws SQLException {
        Date date1 = new Date();
        /*把utils下的date转变为sql下的date*/
        java.sql.Date date2 = new java.sql.Date(date1.getTime());

        Emp e = new Emp( "夏利", "男",date2 , 10000, 1);

        EmpDao empDao = new EmpDao();
        empDao.empInsert(e);
    }

    @Test
    public void test02() throws SQLException {
        Emp e = new Emp(103, null, null, null, 0, 0);
        EmpDao empDao = new EmpDao();
        empDao.empUpdate(e);
    }

    @Test
    public void test03() throws SQLException {
    /*    int eid= 101;*/
        EmpDao empDao = new EmpDao();
        empDao.empDelete(101);
    }

    @Test
    public void test04() throws SQLException {
        EmpDao empDao = new EmpDao();
        List<Emp> empList = empDao.empQuery();
        for (Emp emp : empList) {
            System.out.println(emp);
        }
        empList.forEach(emp -> System.out.println(emp));
    }
    
    @Test
    public void test05() throws SQLException {
        EmpDao empDao = new EmpDao();
        List<Emp> empList = empDao.empQueryLike("j");
        empList.forEach(System.out::println);
    }
}
```

##  三层架构

 ![](C:\Users\Administrator\Desktop\三层架构.jpg)     

 **把服务器分成三层

在三层架构中，DAO层只能与数据库进行数据访问，进行CRUD操作，并且一次只能执行一个操作；service层直接调用DAO层中的方法，在service层的方法中可以一次调用多个DAO层中的方法来完成一整套的业务。

------

## 反射

​    反射的本质为把一个类中各个部分（成员属性、构造方法、成员方法）封装成对象，是一种动态加载类的方式。

*通过Class对象来获取方法对象method,----->>>method.invoke(obj,....)来执行对应的方法，其中obj为实例化对象，后面的参数依次为方法的参数类型.class。通过方法对象执行方法的结果与原方法执行的结果一致。

------

## 连接池技术

1、连接池为存放多个连接的集合。解决了程序连接数据库时间长耗费资源的问题，提高了性能。

2、JavaBean就是Java的组件，也可以广泛的理解为一个类。如果一个类中含有get/set方法，那么这个类就是javabean。JavaBean主要用于传递数据信息。

## DBUtils

DBUtils是JDBC的框架，

DBUtuls中的QueryRunner核心类和ResultHandler结果集封装器配合使用。

①通过传入连接池对象参数(C3P0Utils.getDataSource)获得QueryRunner的实例对象，②然后写sql语句，③通过实例对象来执行sql语句，同时封装结果集（封装成javabean对象实例，然后放到list集合中，或者只封装成javabean对象实例不放到List集合中）。

***BeanHandler(Class type)：将结果集中的第一行数据封装到一个对应的
JavaBean实例中。

***BeanListHandler(Class type)：将结果集中的每一行数据都封装到一个对应
的JavaBean实例中，存放到List里。

***ColumnListHandler(String columnName/int columnIndex)：将结果集中
某一列的数据存放到List中。

***(了解)MapHandler()：将结果集中的第一行数据封装到一个Map里，key是列
名，value就是对应的值。

***(了解)MapListHandler()：将结果集中的每一行数据都封装到一个Map里，然后
再将所有的Map存放到List中。

***ScalarHandler(int columnIndex)：通常用来保存只有一行一列的结果集。

------

### DBUtils模糊查询

①创建一个javabean类用于封装模糊查询字段，设置setter/getter方法。②按照三层架构来写，在dao层中引入一个List集合用于接收占位符的参数。③List集合调用toArray方法转为对象数组，作为占位符的参数传递。

```java
  @Override
        public List<Emp> empAndDeptQuery1(Some some) throws SQLException {
//            Some some = new Some();
            Integer did = some.getDid();
            String dname = some.getDname();
            String dtel = some.getDtel();
            Integer eid = some.getEid();
            String ename = some.getEname();
            Float epay = some.getEpay();
            String esex = some.getEsex();
            String estartime = some.getEstartime();
            /*定义一个List集合用于接受占位符参数*/
            List params = new ArrayList();

            QueryRunner qr = new QueryRunner(C3P0Utils.getDataSource());
            String sql = "select emp.*,dept.dname,dept.dtel from emp left join dept on emp.did=dept.did where 1= 1";
            if(dname !=null && !dname.isEmpty() ){
                 sql = sql + " and dname like ?";
                 params.add("%"+some.getDname()+"%");

            }
            if(dtel !=null && !dtel.isEmpty()){
                sql= sql + " and dtel= ?";
                params.add(some.getDtel());
            }
            if(eid !=null && eid >0){
                sql= sql + " and eid=?";
                params.add(some.getEid());
            }
            if(ename !=null && !ename.isEmpty()){
                sql = sql + " and ename = ?";
                params .add(some.getEname());
            }
            if(epay != null && epay>0){
                sql = sql +" and epay =?";
                params.add(some.getEpay());
            }
            if(esex !=null && esex.isEmpty()){
                sql = sql + " and esex=?";
                params.add(some.getEsex());
            }
            if(estartime !=null && estartime.isEmpty()){
                sql = sql + " and estartime>?";
                params.add(some.getEstartime());
            }
             /*把List集合转为Object数组，传递占位符参数*/
            List<Emp> empList = qr.query(sql, new BeanListHandler<Emp>(Emp.class),params.toArray());

            return empList;
        }
```

------

### 占位符的使用

```java
 public Integer deptInsert(Dept dept) throws SQLException {
        QueryRunner qr = new QueryRunner(C3P0Utils.getDataSource());
        String sql = "insert into dept values (?,?,?)";
        /*定义一个数组封装占位符参数*/
        Object [] param =  {dept.getDid(),dept.getDname(),dept.getDetel()};
        int i = qr.update(sql, param);
        return i;
    }
```



## Tomcat服务器(容器)

项目必须部署在服务器上面，才能运行

服务器相当于你的桌子 , 你桌子上的每个东西 可以看成一个服务 , 容器可以看成是个收纳盒 , 整理你桌子上的东西。

## servlet

客户端发送请求被web.xml拦截，tomcat会找到对应的servlet来完成请求。一个类型的servlet只有一个实例化servlet对象。一个请求对应了一个servlet.

一个项目中只有一个ServletContext对象，这个对象在tomcat启动时就会被创建，在tomcat关闭时才会被销毁；web程序发布服务器上面，服务器产生一个ServletContext，服务器会为每个应用创建一个ServletContext对象。ServletContext对象的作用是在整个Web应用的动态资源之间共享数据

一、提交表单数据到服务器，然后再与数据库中的数据进行比对的思路。①把表单提交到对应的servlet;②在servlet中的post/get方法下调用service层的方法，然后调用dao层方法进行CRUD操作。

二、servlet是javaweb三大组件之一，它属于动态资源。servlet的作用是处理动态资源，服务器会把接收到的请求交给对应的servlet来处理。作用：接受请求；处理请求；响应请求。

三、servlet是Javaee技术平台的规范，只能运行在web服务器上面。通常说servlet指的是servlet接口及其实现类。

四、servlet对象在tomcat服务器启动的时候，并且第一次访问的时候被创建，servlet对象在tomcat服务器关闭和web项目被移除的时候就被销毁。而我们只需要实现servlet就行了，不需要去创建对象。实现servlet的三种方式：①实现Servlet接口；②继承GenericServlet类；③继承HttpServlet类。

HttpServlet继承了GeneriServlet类,GenericServlet实现了Servlet接口。

## JavaWeb四大域对象

​             l.  PageContext；

2.  ServletRequest；

3. HttpSession；

4. ServletContext；

一、ServletContext是Javaweb四大域对象之一，域对象都有存取数据的功能，因为域对象内部有一个Map。主要方法为，setAttribute，getAttribute，removeAttribute.

二、调用(this.)getServletContext会返回一个servletContext对象，在servlet每个方法中适用,注意了，在重写int(config)方法的时候一定要调用父类的int(config方法)。

## 数据从**表单**注册传递到**服务器**再到**数据库**思路分析

①从表单注册信息，点击submit提交，把表单数据上传到服务器上对应的servlet上面，注意当数据上传到servlet的时候，request对象调用getParameterMap()的方法获取表单中name-value对，存储在Map集合中，然后借助BeanUtils工具类populate()方法，把map中的数据存到Javabean中，采用javabean对数据进行封装，注意javabean中的成员变量应该与Map中的name值一一对应，那么此时就应经或得了一个对象，通过这个对象的成员属性值完成对数据库的操作。应该注意的是，对于select下拉框这种方法处理不了，要单独处理；对于Date类型也需要单独处理；②在servlet中调用service层的方法，那么service层会去调用dao层方法，在dao层对数据库进行CRUD操作。

## IDEA激活码

JNTWJDBF2N-eyJsaWNlbnNlSWQiOiJKTlRXSkRCRjJOIiwibGljZW5zZWVOYW1lIjoi5o6I5p2D5Luj55CG5ZWGOiB3d3cuaTkub3JnIiwiYXNzaWduZWVOYW1lIjoiIiwiYXNzaWduZWVFbWFpbCI6IiIsImxpY2Vuc2VSZXN0cmljdGlvbiI6IiIsImNoZWNrQ29uY3VycmVudFVzZSI6ZmFsc2UsInByb2R1Y3RzIjpbeyJjb2RlIjoiSUkiLCJmYWxsYmFja0RhdGUiOiIyMDE5LTA3LTIwIiwicGFpZFVwVG8iOiIyMDIwLTA3LTE5In0seyJjb2RlIjoiQUMiLCJmYWxsYmFja0RhdGUiOiIyMDE5LTA3LTIwIiwicGFpZFVwVG8iOiIyMDIwLTA3LTE5In0seyJjb2RlIjoiRFBOIiwiZmFsbGJhY2tEYXRlIjoiMjAxOS0wNy0yMCIsInBhaWRVcFRvIjoiMjAyMC0wNy0xOSJ9LHsiY29kZSI6IlBTIiwiZmFsbGJhY2tEYXRlIjoiMjAxOS0wNy0yMCIsInBhaWRVcFRvIjoiMjAyMC0wNy0xOSJ9LHsiY29kZSI6IkdPIiwiZmFsbGJhY2tEYXRlIjoiMjAxOS0wNy0yMCIsInBhaWRVcFRvIjoiMjAyMC0wNy0xOSJ9LHsiY29kZSI6IkRNIiwiZmFsbGJhY2tEYXRlIjoiMjAxOS0wNy0yMCIsInBhaWRVcFRvIjoiMjAyMC0wNy0xOSJ9LHsiY29kZSI6IkNMIiwiZmFsbGJhY2tEYXRlIjoiMjAxOS0wNy0yMCIsInBhaWRVcFRvIjoiMjAyMC0wNy0xOSJ9LHsiY29kZSI6IlJTMCIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJSQyIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJSRCIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJQQyIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJSTSIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJXUyIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJEQiIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJEQyIsImZhbGxiYWNrRGF0ZSI6IjIwMTktMDctMjAiLCJwYWlkVXBUbyI6IjIwMjAtMDctMTkifSx7ImNvZGUiOiJSU1UiLCJmYWxsYmFja0RhdGUiOiIyMDE5LTA3LTIwIiwicGFpZFVwVG8iOiIyMDIwLTA3LTE5In1dLCJoYXNoIjoiMTM3NzMzMjEvMCIsImdyYWNlUGVyaW9kRGF5cyI6NywiYXV0b1Byb2xvbmdhdGVkIjpmYWxzZSwiaXNBdXRvUHJvbG9uZ2F0ZWQiOmZhbHNlfQ==-eWdxZk0seWB55Q7nIH8z9ye3Hx6JvP1l4NWX/EPD2CTdbajon7jKqy3ZdtpN4i38MQxm22HnwV5mJCPYdj9badWrdcRazMNns+DSylt7OGpbyfHaDXUL4hosbKw9ysyEpjBpmj5CTHARbT9xezSAVWKXyn6fDhOGD/qazMxe5l1DW0JaSbn8mQjkMbJmP4xvpFW/pO9zxv3spMB8J5U1OgrQY8DKUhpDzlIMOS5K0jixY6QaLWkMbL0Fa36PPBIeJ1BinIevmiM3Mw3lWmCpBflBhyrX8ZZg1sRClvS8nXDm62TWh4aZRQJnAnXX8+cgRUXupsU3UmJdERizb/4aPA==-MIIElTCCAn2gAwIBAgIBCTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE4MTEwMTEyMjk0NloXDTIwMTEwMjEyMjk0NlowaDELMAkGA1UEBhMCQ1oxDjAMBgNVBAgMBU51c2xlMQ8wDQYDVQQHDAZQcmFndWUxGTAXBgNVBAoMEEpldEJyYWlucyBzLnIuby4xHTAbBgNVBAMMFHByb2QzeS1mcm9tLTIwMTgxMTAxMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxcQkq+zdxlR2mmRYBPzGbUNdMN6OaXiXzxIWtMEkrJMO/5oUfQJbLLuMSMK0QHFmaI37WShyxZcfRCidwXjot4zmNBKnlyHodDij/78TmVqFl8nOeD5+07B8VEaIu7c3E1N+e1doC6wht4I4+IEmtsPAdoaj5WCQVQbrI8KeT8M9VcBIWX7fD0fhexfg3ZRt0xqwMcXGNp3DdJHiO0rCdU+Itv7EmtnSVq9jBG1usMSFvMowR25mju2JcPFp1+I4ZI+FqgR8gyG8oiNDyNEoAbsR3lOpI7grUYSvkB/xVy/VoklPCK2h0f0GJxFjnye8NT1PAywoyl7RmiAVRE/EKwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQAF8uc+YJOHHwOFcPzmbjcxNDuGoOUIP+2h1R75Lecswb7ru2LWWSUMtXVKQzChLNPn/72W0k+oI056tgiwuG7M49LXp4zQVlQnFmWU1wwGvVhq5R63Rpjx1zjGUhcXgayu7+9zMUW596Lbomsg8qVve6euqsrFicYkIIuUu4zYPndJwfe0YkS5nY72SHnNdbPhEnN8wcB2Kz+OIG0lih3yz5EqFhld03bGp222ZQCIghCTVL6QBNadGsiN/lWLl4JdR3lJkZzlpFdiHijoVRdWeSWqM4y0t23c92HXKrgppoSV18XMxrWVdoSM3nuMHwxGhFyde05OdDtLpCv+jlWf5REAHHA201pAU6bJSZINyHDUTB+Beo28rRXSwSh3OUIvYwKNVeoBY+KwOJ7WnuTCUq1meE6GkKc4D/cXmgpOyW/1SmBz3XjVIi/zprZ0zf3qH5mkphtg6ksjKgKjmx1cXfZAAX6wcDBNaCL+Ortep1Dh8xDUbqbBVNBL4jbiL3i3xsfNiyJgaZ5sX7i8tmStEpLbPwvHcByuf59qJhV/bZOl8KqJBETCDJcY6O2aqhTUy+9x93ThKs1GKrRPePrWPluud7ttlgtRveit/pcBrnQcXOl1rHq7ByB8CFAxNotRUYL9IF5n3wJOgkPojMy6jetQA5Ogc8Sm7RG6vg1yow==

## FTP

ftp://192.168.2.22

## Java的三种页面跳转方法（setHeader，SendRedirect，forward）

### 重定向 / 转发

在JAVA中进行资源跳转，或者是页面跳转，从本质上来讲，有两种方式：重定向 ， 转发

这两者都可以使页面进行跳转，但是两者之间有不同的区别

其中 SendRedirect，setHeader 属于重定向方式，而 forward 属于转发方式

### 重定向（sendRedirect，setHeader）

1.重定向到指定URL，是客户端跳转

2.地址栏中的地址将会改变，变成重定向的地址

3.调用者和被调用者处于两次不同的请求。不能通过request域对象来共享数据，

如果需要传递参数，需要在 url 后加参数，如 url?id=2，或者使用ServletContext 存放全局数据，不能通过request和response方式 

4.使用重定向方式可以重定向到任意 URL

①response.sendRedirect(url);
②response.sendRedirect( "/uu ");表示相对于服务器根路径
③url 可以使用相对路径，也可以使用绝对路径

⑤//需要设置状态码 302（found），重新定位
⑥response.setStatus(302);
⑦response.setHeader("Location","url");

#### 重定向的详细过程：

Redirect 会发送一个 response（响应）给浏览器，当浏览器接收到 response 后，再发送一个request（请求）给服务器，服务器接收到后，会发送新的 response 给浏览器，而这时候，页面接收到的是从浏览器取来的新的request。

那么，在跳转之前的页面所存放在request.setAttribute中的东西就没了，如果在新页面中使用request.getAttribute 获取以前存放的元素，将会得到null。

所以在传递参数时，不能使用request和response方式。

浏览器和服务器两次请求响应。

#### 转发（forward）

1.请求转发到指定URL

2.是服务器端跳转

3.地址栏中的网址保持不变

4.只能重定向到同一个Web应用程序中的某个资源

①无法重定向至有frame的jsp文件,可以重定向至有frame的html文件,同时forward()无法在后面带参数传递,比如servlet?name=frank
②可以通过response.setAttribute("name",name)来传至下一个页面
5.采用请求转发方式，在跳转页面的时候是带着原来页面的request和response跳转的，request对象始终存在，所以可以使用域对象传递参数。

①request.getRequestDispatcher(“url”).forward(request,response);

#### 转发的详细过程：

forward() 过程 发生在服务器端, 客户端浏览器只发出一次请求，在服务器端，Servlet将用户的请求连同请求信息等内容转发给Servlet、HTML、JSP或其它信息资源，由第2个信息资源响应该请求，两个信息资源共享同一个request对象，参数自动传递。

浏览器和服务器一次请求响应。

### 总结

setHeader() 的其他几种使用方式

①一秒刷新页面一次：response.setHeader("refresh","1");
②二秒跳到其他页面：response.setHeader("refresh","2;URL=otherPagename");
③没有缓存：response.setHeader("Pragma", "No-cache");  
④response.setHeader("Cache-Control", "no-cache");

forward方法只有一次的浏览器服务器请求，只有一个Request和Response，所以调用者与被调用者之间共享Request和Response

sendRedirect方法由于两次浏览器服务器请求，所以有两个Request和Response。

如果使用 request.setAttribute 传递一些属性就需要用forward，如果想要跳转到别的应用的资源，就需要用 sendRedirect，setHeader。

PS：无论是forward方法还是sendRedirect方法调用前面都不能有PrintWriter输出到客户端。

forward方法报错： Java.lang.IllegalStateException: Cannot forward after response has been committed

sendRedirect报错：java.lang.IllegalStateException: at org.apache.catalina.connector.ResponseFacade.sendRedirect
————————————————
原文链接：https://blog.csdn.net/Annn_kk/article/details/87996777

------

## 表单注册登录：

①先写html页面，填写表单；②把表单数据提交到一个Servlet，创建一个javabean实体类来封装提交表单中name-value的属性值(这里javabean实体类中的成员变量必须和表单中name属性的值一一对应，因为BeanUtils的populate()方法会把ParamaterMap中的key值与实体类中的成员变量进行比对赋值，相同就赋值)，对于Date类型要先将表单中的String类型转换为Date.

```java
/*时间类型先把字符串类型转为date,时间转换器*/
DateConverter dc = new DateConverter();
dc.setPatterns(new String[]{"yyyy-MM-dd", "yyyy-MM-dd HH:mm:ss"});
ConvertUtils.register(dc, Date.class);
```

对复选框单独处理。

```java
/*复选框单独处理，根据标签的name属性返回所有name属性对应的value*/
String[] val = request.getParameterValues("chk");
/*然后调用set方法给javabean中对应的属性赋值*/
 user.setChk(strval);
```

```java
/*注册，用户的表单注册数据传到/as*/
@javax.servlet.annotation.WebServlet(urlPatterns = "/as")
public class AServlet extends javax.servlet.http.HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request, response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=utf-8");
        /*时间类型单独处理,把字符串类型转为date,时间转换器*/
        DateConverter dc = new DateConverter();
        dc.setPatterns(new String[]{"yyyy-MM-dd", "yyyy-MM-dd HH:mm:ss"});
        ConvertUtils.register(dc, Date.class);
        /*String birth = request.getParameter("birth");*/

        /*select下拉框单独处理，返回所有name属性对应的value*/
        String[] val = request.getParameterValues("chk");
        /*System.out.println(Arrays.toString(val));*/

        /**/
        /*获取表单中的name和value保存在map中,不包括下拉框*/
        String strval = Arrays.toString(val);
        Map<String, String[]> parameterMap = request.getParameterMap();
        /*用BeanUtils工具类来封装数据,但是复选框要单独处理，如chk*/
        UsersDemo user = new UsersDemo();
        try {
            /*把map中的值赋值给user中对应属性的值，变量名必须一一对应*/
            BeanUtils.populate(user, parameterMap);
            user.setChk(strval);
        } catch (Exception e) {
            e.printStackTrace();
        }
        /*接着调用service层，把数据插入到数据库中*/
        ServiceUser serviceUser = new ServiceUserImpl();
```

html页面跳转的时候，当要进行功能操作的时候应该跳转到servlet中进行CRUD操作，然后把结果响应给新的html页面。如果不需要进行功能操作，直接跳转到新的html页面就可以了。

### 图片下载

```java
@WebServlet(urlPatterns = "/img")
public class ImgServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request, response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=utf-8");
        /*设置响应头，告诉客户端该做什么*/
        response.setHeader("content-disposition","attachment;filename=bz.jpg");
        /*把文件作为字节输入流输入到程序*/
        InputStream in = getServletContext().getResourceAsStream("/file/bz.jpg");
        /*以字节输出流响应客户端*/
        ServletOutputStream out = response.getOutputStream();
        /*把输入流数据，写入到输出流中,响应客户端*/
        IOUtils.copy(in,out);

    }
```

## URL栏的get请求链接

```java
/*注册成功后，3秒后刷新跳转到登录页面，页面刷新就用setHeader*/
response.setHeader("refresh", "3;url=" + request.getContextPath() + "/login.html");
```

```
writer.write("<td>"+"<a href='#'>修改</a>&nbsp;&nbsp<a href="+request.getContextPath()+"/d?id="+usersDemo.getId()+">删除</a>"+"</td>");
```

## 四步创建Cookie

```java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd-HH:mm:ss");
String fdate = sdf.format(new Date());

Cookie cookie = new Cookie("last-time", fdate);
/*设置cookie存活时间*/
cookie.setMaxAge(30*60);
/*设置路径,把cookie存放在当前项目下面*/
cookie.setPath(request.getContextPath());
/*把cookie发送给客户端*/
response.addCookie(cookie);
```

## 程序员应该具备的能力

## JavaBean类封装数据

一、当把表单中的数据通过Map封装到类中时，那么类中必须包含与表单中name属性值一模一样的成员变量。

二、当把数据库表中的字段封装到类中时，那么类中必须包含与表中字段一模一样的成员变量。

## Session失效

```java
    //让session失效
    HttpSession session = request.getSession();
    //让session失效：让所有的session失效。
    //session.invalidate();

    //让保存的某个session的属性失效
    session.getAttribute("name");
    session.removeAttribute("name");
```

## idea的中文字体渲染问题

IDEA 2018.2升级到 IDEA 2019.2，中文字体渲染问题
修改一下备用字体就可以
共需要修改两处：
1、Setting -> Editor -> Font 修改 Fallback font 为 simsun
2、Setting -> Editor -> Color Scheme -> Color Scheme Font 修改 Fallback font 为 simsun

## JSP

一、三个指令（静态）page、include、taglib.每个指令又有若干个属性。

二、<jsp:forward/include/param三个常用的动态标签

三、<jsp:useBean>动态标签。在jsp中引入javabean类对象，可以给对象属性赋值、取值。

四、jsp中的标签内容可以在html页面直接显示。

五、javabean封装表单数据时，表单的name属性必须和javabean类中的成员属性一模一样。

## EL&JSTL

几个需要注意的地方：

一、标签中的变量值默认存在pageScope域中。

二、${域对象别名.属性名}获得域属性值

三、${域对象别名.javabean类.属性名}获得域对象中存的javabean类对象属性值

四、在forEach循环中添加变量map获得${map.key}、${map.value}获得map集合的key和value值

五、forEach循环遍历集合时，必须自定义一个变量来指代集合中的每一个元素

------

## JavaWeb与MVC

M-model  模型 javabean泛指所有与数据库操作相关的部分 SERVICE+DAO

V-view   视图图形化界面jsp

C-controller控制器负责页面的重定向和转发的部分 servlet

## 旅游项目案例

需要注意的点：

一、封装查询条件时，属性全部用String类型，javabean中在包含表单。

二、回显查询条件，将查询条件显示在查询框中。

```java
<body style="font-size: 10px">
<center>
    <h3>旅游景点信息列表</h3>
    <%--一定要带上cmd=list--%>
    <form action="${pageContext.request.contextPath}/ms?cmd=list" method="post">
        城市名称:<select name="cityName">
                      <option value="">==全部==</option>
        <c:forEach items="${cityList}" var="city">
            <%--citylist是查询返回的结果，searchinfo是查询的条件--%>
            <option value="${city.cityName}" <c:if test="${searchInfo.cityName eq city.cityName}">selected</c:if>> <%--value="${city.cityId}" <c:if test="${city.cityName==searchInfo.cityName}">selected</c:if> >
                      ${city.cityName}--%>
            ${city.cityName}
            </option>
        </c:forEach>
                </select>&nbsp;&nbsp;
        价格区间:<input type="text" name="startPrice" value="${searchInfo.startPrice}" style="width:50px">&nbsp;--
                <input type="text" name="endPrice" value="${searchInfo.endPrice}" style="width: 50px">&nbsp;&nbsp;
        景点介绍:<input type="text" name="intro" value="${searchInfo.intro}">&nbsp;&nbsp;
        <input type="submit" value="查找" style="font-size: 10px">
        <%----%>
        <input type="button" value="添加景点信息" onclick="addToursInfo()" style="font-size: 10px">
    </form>
    <table border="1px" cellpadding="5px" cellspacing="0" width="80%">
        <tr>
            <th>景点编号</th>
            <th>景点介绍</th>
            <th>发布时间</th>
            <th>票价</th>
            <th>城市名称</th>
            <th>删除</th>
            <th>详细</th>
            <th>修改</th>
        </tr>
        <c:forEach items="${list}" var="info">
           <tr>
               <td>${info.id}</td>
               <td>${info.introduce}</td>
               <td>${info.pubTime}</td>
               <td>${info.price}</td>
               <td>${info.cityName}</td>
               <td><a href="">删除</a></td>
               <td><a href="">详细</a></td>
               <td><a href="">修改</a></td>
           </tr>
        </c:forEach>
    </table>
</center>
</body>
```

三、将多个操作封装在一个servlet中，在方法中调用方法。

四、表单中隐藏节点<input:hidden>可以传递数据到servlet，但此节点不显示在表单上面。

```java
<input type="hidden" name="id" value="${requestScope.addInfo.id}">
```

五、在超链接里面写javascript函数。

```java
<%--超链接中在js中传递函数的写法--%>
<td><a href="javascript:toDel(${info.id})">删除</a></td>
```

```
/*删除提示*/
function toDel(id) {
    if (window.confirm("确认删除吗？")){    window.location.href="${pageContext.request.contextPath}/ms?cmd=del&id="+id;
    }
```

六、回显数据。

```java
<select name="cityId" id="">
    <%--从session中拿出城市放在下拉框--%>
    <c:forEach items="${sessionScope.cityList}" var="city">
        <%--因为表中要显示city_id,所以这里value放cityId//回显，通过id把城市名字连来了。默认的为回显City中的cityId
        现在变成了实体Addinfo中的cityId,相当于当前的cityId覆盖默认的cityId--%>
        <option value="${city.cityId}" <c:if test="${city.cityId == requestScope.addInfo.cityId}"> selected </c:if>>
        ${city.cityName}
        </option>
    </c:forEach>
</select>
```

七、跳转。①要显示数据，就先到servlet，后到jsp中显示数据；②要通过页面添加数据，就先到jsp页面然后到servlet；③在链接中传递参数。

八、在index.jsp中添加forward动态标签，当服务器打开的时候就会默认到index.jsp中并转发到servlet。

```java
<jsp:forward page="/ms?cmd=list"></jsp:forward>
```

九、合并servlet的写法，即在servlet中用if...else...语句判断参数中传递过来的方法名。

十、表单中的数据传递到servlet中后全部变为String类型（无论在表单中是什么数据类型）。如果封装的实体类中的时间类型为Date,用ConverterUtils把String类型时间

------

## 分页查询

一、service业务层根据表单查询条件condition和当前页p返回得到PageBean;service层中要调用两个dao层方法，一个为根据condition查到所有的记录数，另一个为根据condition和pb查询得到结果集。

```java
public PageBean findToursByPB(Condition condition, Integer p) throws Exception {
    //创建pageBean对象
    PageBean pb = new PageBean();
    //步骤：步骤一定不能设置错了！
    //1.查询总共有多少条记录: 得到 count
       //调用dao
    Integer count = toursInfoDao.getCount(condition);
    //2.设置每页显示多少记录  : 设置pageSize
    pb.setPageSize(5);
    //3.设置总共有多少条记录:设置count / 设置总共有多少页: 设置pageTotal
    pb.setCount(count);
    //4.设置当前是第几页：设置p
    pb.setP(p);
    System.out.println("Second:"+p);
    //5.根据条件分页查询数据 : 获取data
       //调用dao
    List<ToursInfo> toursInfoList = toursInfoDao.queryToursInfoByPB(condition, pb);
    //6.设置data
    pb.setData(toursInfoList);
    return pb;
}
```

二、数据库中原本就有数据，打开网站应该先访问数据库拿到所有的数据显示在页面上。然后再在这个页面上执行操作。

```java
public class Condition {
    //装查询条件,注意了查询条件中的属性名一定不能和实体类中的属性名相同，否则名字相同，删除就查不出来
    private Integer cid;

    public Condition() {
    }

    public Integer getCid() {
        return cid;
    }

    public void setCid(Integer cid) {
        this.cid = cid;
    }
}
```

## 批量查询

```xml
 查询编号是1,2的电脑信息

    foreach标签：循环遍历作用

    collection: 集合:list / 数组: 类型[]  = Integer[]
    item: 集合/数组的数据值
    item="接口传递的参数的名字"
    注意：这里为集合时时只能写list

    separator：分隔符

     面向接口 = 面向百度
-->
<select id="queryBatch" parameterType="list" resultType="Computers">
    select * from computers where id in
    <foreach collection="list" open="(" separator="," close=")" item="cids">
        #{cids}
    </foreach>
</select>
```

------

## mybatis

### 几个传参的注解：

①@Param将方法中参数赋值给SQL中的参数

②@RequestParam将请求中的参数赋值给方法中的参数

③@PathVariable将Restful风格请求中的参数赋给方法中的参数

一、在不使用逆向工程的前提下在mybatis框架中把数据表字段与pojo类属性进行一一对应。①引入reslutmap标签，子标签id对应主键，result标签对应普通字段，association标签对应一个类，collection标签对应一个集合。②主要目的是把查询到的结果封装到实体类中，既然是封装到实体类中那么就应该明白查到的结果只有一个，有点类似于BeanHandler<>();适用于两个表关系为一条记录对应一条记录或者一条记录对应多条记录。其实也可以把结果封装到Map中

二、使用逆向工程的话会自动形成pojo类，接口和mapper映射文件。逆向工程只会自动生成单表的信息，对于多表的查询的方法要自己写

三、注解开发  mybatis自带注解开发功能

四、打印出插入的那条记录，尤其注意打印出自增主键

```java
@Options(useGeneratedKeys = true, keyColumn = "hus_id", keyProperty = "husId")

<!--插入一条订单信息，并返回主键订单的数字-->
  <insert id="insertOneOrder" parameterType="Orders"  useGeneratedKeys="true" keyProperty="orderid" keyColumn="orderId">
    insert into orders values (null, #{remark}, #{orderno}, #{cost}, #{createtime}, #{userid})
  </insert>
```

```java
//注解开发
//查询丈夫信息封装在丈夫实体中，表中字段与实体类中的字段不一致时，添加注解对应
@Select("select * from husband where hus_id=#{id}")
@Results({
        @Result(id=true, column = "hus_id", property="husId"),
        @Result(column = "husband_name", property = "husbandName")
})
Husband queryHusbandById(Integer id);

//添加一条丈夫记录,把参数封装在Husband实体中，进行传参；并返回丈夫的id
@Insert("insert into husband values(null, #{age}, #{gender}, #{husbandName})")
@Options(useGeneratedKeys = true, keyColumn = "hus_id", keyProperty = "husId")
Integer insertOneHusband(Husband husband);

//查询所有的丈夫信息,把查到的结果封装到Husband实体中，再放到list集合中
//字段映射时，主键要加id属性
@Select("select * from husband")
@Results({
        @Result(id = true, column = "hus_id", property = "husId"),
        @Result(column = "husband_name", property = "husbandName")
})
List<Husband> queryHusbandAll();
```

五、延迟加载。只查询wife的信息时，就不去查询husband的信息了。

```java
<!--实体类类型，懒加载husband，一对一-->
<association property="husband" javaType="Husband" fetchType="lazy" column="hid"
             select= "com.mapper.HusbandMapper.queryHusbandById">
</association>
<集合类型，一对多>
 <collection property="list" ofType="Orders" column="id" select="com.mapper.OrdersMapper.queryOrdersByUsersId"
                fetchType="lazy">
    </collection>
```

六、一级缓存数据在同一个sqlSession下有效，也即是在同一个sqlSession下对数据进行增删改，可以查到更新后的数据，因为增删改清空了缓存，会重新到数据库中查找。二级缓存数据在同一个namespace下有效。

```java
//根据用户名和地址查询
@Select("select * from users where uName=#{name001} and address=#{address001}")
public List<Map<String, Object>> queryUsersByNameAndAddress(@Param("name001") String name, @Param("address001") String address);
```

七、

```java
  //动态查询所有用户
    @Select("<script>" +
            "select * from users where 1=1" +
            "<if test='uName !=null and !uName.isEmpty()'>" +
            "and uName=#{uName}" +
            "</if>" +
            "<if test='address !=null and !address.isEmpty()'>" +
            "and address=#{address}" +
            "</if>" +
            "</script>")
    List<Users> queryUsersActive(Map<String, Object> map);
    //查询用户和定单所有信息
    @Select("select * from users, orders where users.id = orders.userId order by users.id")
    List<Map<String, Object>> queryUsersAndOrders();
    //根据用户名和地址查询
    @Select("select * from users where uName=#{name001} and address=#{address001}")
    public List<Map<String, Object>> queryUsersByNameAndAddress(@Param("name001") String name, @Param("address001") String address);
}
```

八、

```java
//查询所有的历史信息
@Select("select * from history")
List<History> queryAllHistory();

//查询所有的历史信息2
@Select("select * from history")
@Results({
        @Result(id = true, column = "hid", property = "hId"),
        @Result(id = true, column = "hstarttime", property = "hStarTime"),
        @Result(id = true, column = "hendtime", property = "hEndTime"),
        @Result(id = true, column = "hcity", property = "hCity"),
        @Result(id = true, column = "hwork", property = "hWork"),
        @Result(id = true, column = "eid", property = "eId"),
})
List<History> queryAllHistory2();
```

九、

```java
//模糊查询所有的帖子
@Select("<script>select * from invitation where 1=1" +
        "<if test='the !=null and !the.isEmpty()'>" +
        "and title like \"%\"#{the}\"%\"" +
        "</if>" +
        "</script>")
List<Invitation> queryAllInvitation(@Param("the") String title);
```

十、

```java
int insert(ReplyDetail replyDetail);
注意：如果对象变量名为replyDetail，那么就不能用默认的record了
int insertSelective(ReplyDetail record);
```

## SpringMvc

```java
@RequestMapping("/list")
public ModelAndView list(@RequestParam(value = "ctitle", required = false) String title,
                                                @RequestParam(defaultValue = "1") Integer pageNum,
                                                 ModelAndView mv){
    PageInfo pageInfo = serviceInterface.findAllInvitation(title, pageNum, 3);
    mv.addObject("pageInfo", pageInfo);
    mv.addObject("title", title);
    mv.setViewName("/jsp/main.jsp");
    return mv;
```

![img](file:///C:\Users\Administrator\AppData\Roaming\Tencent\Users\1299930560\QQ\WinTemp\RichOle\KH2C_S`[0P{5JH0TW({]}PF.png)

### 内部转发：

```java
@RequestMapping("/reply/{id}")
public ModelAndView reply(@PathVariable("id") Integer invid, ModelAndView mv){
     List<ReplyDetail> allReplyDetail = serviceInterface.findAllReplyDetail(invid);
     mv.addObject("invid", invid);
     mv.addObject("allReplyDetail", allReplyDetail);
     mv.setViewName("/jsp/com.jsp");
     return mv;
 }

 @Autowired
 ReplyDetail replyDetail;
 //添加
@RequestMapping("/add")
public ModelAndView addreply(ReplyDetail replyDetail, ModelAndView mv){
    replyDetail.setCreatedate(new Date());
    boolean b = serviceInterface.addReply(replyDetail);
    if(b){
        mv.addObject("msg01", "success");
    }else{
        mv.addObject("msg01", "fail");
    }
    mv.setViewName("/main/reply/"+replyDetail.getInvid());
    return mv;
}
```

```java
@RequestMapping("/reply/{id}/{pageNum}")
public ModelAndView reply(@PathVariable("id") Integer invid,
                                                     //@RequestParam(defaultValue = "1") @PathVariable("pageNum") Integer pageNum,
注意：在参数前面不能同时用这两个注解，否则一直为默认值                          
                                                      ModelAndView mv){
    PageInfo pageInfo = serviceInterface.findAllReplyDetail(invid, pageNum, 3);
     mv.addObject("invid", invid);
     mv.addObject("pageInfo", pageInfo);
     mv.setViewName("/jsp/com.jsp");
     return mv;
 }
```

## Restful

```java
public class RestFul {

    //增加，把前台传递过来的参数给{id}
    @RequestMapping(value = "/books/{id}", method = RequestMethod.POST)
    //@PathVariable表示把请求中的参数给方法中的参数
    public String insertBook(@PathVariable("id") Integer tid){
        System.out.println("插入post:"+tid);
        return "/index.jsp";
    }
    //删除
    @RequestMapping(value = "/books/{id}/{bookname}", method = RequestMethod.DELETE)
    public String deleteBook(@PathVariable("id") Integer id,
                             @PathVariable("bookname") String bookname){
        System.out.println("删除delete："+id +"==="+ bookname);
        return "redirect:/index.jsp";
    }
    //修改
    @RequestMapping(value = "/books/{id1}/{bname}/{country}", method = RequestMethod.PUT)
    public String updateBook(@PathVariable("id1") Integer id,
                             @PathVariable("bname") String name,
                             @PathVariable("country") String country){
        System.out.println("修改操作put:"+id+"==="+name+"==="+country);
        return "redirect:/index.jsp";
    }
    //查询
    @RequestMapping(value = "/books/{id}")//把请求中的参数赋给方法中的参数
    public String findBook(@PathVariable("id") Integer id){
        System.out.println("查询get:"+id);
        return "redirect:/index.jsp";
    }
```

## JVM

一、java中的class字节码文件不是二进制文件（它是16进制文件），不是机器指令，不能直接被cpu执行，由jvm解释执行。

二、栈有深度。内存有大小,栈中每入一个方法就会产生一个栈帧

三、指令寄存器存的是当前要执行的指令；程序寄存器存的是下一条要执行的指令。

四、jvm栈内存有默认大小，1M。

------

## 锁

锁有cpu指令集支持，上锁和释放锁都是原子操作，不可再分

------

JSON

如果是数组和List集合，那么就返回一个json数组。如果是Map和pojo，那么就返回json数据格式。

```java
Model:用来封装传递数据使用。=== request作用域对象
```

## 引入jQuery时问题

```java
<script src="${pageContext.request.contextPath}/js/jquery-3.4.1.js"></script>
这么写不会出错
放的目录不要深
```

## 用easyui分页注意的问题

![1576756031758](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1576756031758.png)

## 有无thymeleaf对static和templates文件夹下html文件访问的区别

一、引入thymeleaf模板引擎后，此时html被默认存在templates下面，可以通过url地址栏直接访问static、public下的HTML文件，但不能通过url地址栏直接访问templates下的html文件。

![1577022757257](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1577022757257.png)

但是通过控制器内部转发或重定向必须写forward、redirect才能访问static下面的html文件。而此时templates下面的HTML文件是可以return就可以访问的。

![1577023180435](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1577023180435.png)

二、未引入thymeleaf时，html默认存在static文件加夹下。此时可以直接从url地址栏访问public、static下的HTML文件，但不能访问templates下的HTML文件。此时在控制器中可以return到static、public下的HTML文件，但不能到templates下的HTML文件，转发重定向也找不到。也就是使用templates必须要用thymeleaf.

![1577024625905](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1577024625905.png)

## 批量删除

```java
//批量查询，参数类型为List，list里面装的为查询的id
List<Map<String, Object>> queryBatchById(List<Integer> listId);
//数组批量查询
List<Map<String, Object>> queryBatchById02(Integer[] arrId);
//根据id删除
------
    </update>
    <!--批量查询，传参数就传一个集合，item指向接口中的变量-->
    <select id="queryBatchById" parameterType="List" resultType="Map">
         select * from books where id in
         <foreach collection="list" open="(" separator="," close=")" item="listId">
             #{listId}
         </foreach>
    </select>
    <!--数组批量查询/删除-->
    <select id="queryBatchById02" parameterType="Integer[]" resultType="Map">
        select * from books where id in
        <foreach collection="array" open="(" separator="," close=")" item="arrId">
            #{arrId}
        </foreach>
    </select>
```

## MYSQL5.7.22设置密码用户名：

set global validate_password_policy=0;
set global validate_password_mixed_case_count=0;
set global validate_password_number_count=3;
set global validate_password_special_char_count=0;
set global validate_password_length=3;
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('123456');

## 前台表单数据与实体类封装数据：

通过实体类的set方法把表单中的数据封装到实体类中，只要求表单中的name属性名称与实体类中的属性名称相同即可，

## LINUX添加配置，启动项目

<resources>
			<resource>
				<directory>${project.basedir}/src/main/resources</directory>
				<filtering>true</filtering>
			</resource>
		</resources>

github密码：

1299930560@qq.com          djy19921223

gitee密码：

%wsdjy1223%djy

## 打包时自定义maven打包工具，不用maven自带的版本

```java
<!--这里要自定义如下的maven打包工具，不用springboot自带的，不然就用不了包中的类-->
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <configuration>
        <source>1.8</source>
        <target>1.8</target>
    </configuration>
</plugin>
```

## 打包时不把test打包进去

```java
<!--打包时不编译test类-->
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.4.2</version>
    <configuration>
        <skipTests>true</skipTests>
    </configuration>
</plugin>
```

## 在启动类做一下配置，就可以直接访问静态页面了

```java
public class DdbuyConsumerWebApplication extends WebMvcConfigurationSupport {

    public static void main(String[] args) {
        SpringApplication.run(DdbuyConsumerWebApplication.class, args);
    }

    @Override
    protected void addResourceHandlers(ResourceHandlerRegistry registry) {
        registry.addResourceHandler("/**").addResourceLocations(ResourceUtils.CLASSPATH_URL_PREFIX+"/templates/");
        registry.addResourceHandler("/**").addResourceLocations(ResourceUtils.CLASSPATH_URL_PREFIX+"/static/");
        registry.addResourceHandler("/**").addResourceLocations(ResourceUtils.CLASSPATH_URL_PREFIX+"/webapp/");
        super.addResourceHandlers(registry);
    
```

## dubbo+zookeeper服务架构项目拆分：

①消费者和提供者（web工程，在服务器里面跑）、dao层工程为springboot的非web工程

②实体工程、接口工程就为maven工程

③拆分后每个工程应该独自都能完整的运行、整合后也应该完整运行



## 异步提交表单

```java
//保存
function SaveDialog(){
    //跳转到后台实现保存
    //传统:取值-->通过$.ajax方法发送异步请求实现添加
    $('#saveDialogForm').form('submit', {
        url:"/admin/addDistrict",  //提交的服务器地址
        success:function(data){ //成功的回调函数
            //data接收服务器返回值json字符串（不是json对象）
            var obj=$.parseJSON(data);
            if(obj.result>0){
                $("#AddDialog").dialog("close");  //关闭
                //alert("添加成功");
                $.messager.alert('提示框','恭喜添加成功!');
            }
            else
            {
                $.messager.alert('提示框','系统正在维护!');
            }
        }
    });
}
```

## 从客户端获取cookie

```java
<script type="text/javascript">
    //获取保存在客户浏览器cookie
    //通过js代码读取cookie
    function readCookie(name)   {
        var cookieValue = "";
        var search = name + "=";
        if(document.cookie.length > 0)
        {
            offset = document.cookie.indexOf(search);
            if (offset != -1)
            {
                offset += search.length;

                end = document.cookie.indexOf(";", offset);

                if (end == -1) end = document.cookie.length;

                cookieValue = document.cookie.substring(offset, end);
            }
        }
        return cookieValue;
    }

    jq(function () {
        var token = readCookie("token");
        //alert(token);
        //发送异步请求获取用户展示
        //异步请求正常只能访问本系统的控制器返回json数据,访问别人系统的控制器返回json(跨域)
        jq.get(
            "http://localhost:9010/loginNoFirst",
            {"token":token},
            function(data){
                if (data !=null){
                    jq("#osp").text("欢迎您："+data.userName);
                }
        },"json");
    })
</script>
```

## springboot自定义配置访问静态资源

```java
#配置访问静态资源
spring.mvc.static-path-pattern=/**
spring.resources.static-locations=classpath:/test/,classpath:/static/js/,classpath:/META-INF/resources/,classpath:/resources/,classpath:/static/,classpath:/public/
```

List集合迭代

```java
    // 创建出一个数组
    List<String> strList = Arrays.asList("YangHang", "AnXiaoHei", "LiuPengFei");

    strList.forEach(System.out::println);

、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、
    @Test
    public void testDemo2() {
        List<String> strList = Arrays.asList("YangHang", "AnXiaoHei", "LiuPengFei");

        strList.forEach(x -> {
            System.out.println(x);
        });
    }

```
![1580375457520](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1580375457520.png)

当边迭代集合边删除集合中的元素的时候只能用迭代器迭代，增强for循环引发并发修改异常

## mysql添加索引和删除索引

alter table ***toursinfo*** add index index_name ( ***price*** )

drop index index_name on ***toursinfo***

## 启动fastdfs

[root@localhost ~]# /usr/bin/fdfs_trackerd /etc/fdfs/tracker.conf restart
[root@localhost ~]# /usr/bin/fdfs_storaged /etc/fdfs/storage.conf
[root@localhost ~]# /usr/local/nginx/sbin/nginx

## **jvisualvm**

## 面试题

1、int i =1;

​      i = i++;

这个代码是怎么执行的。

①栈帧中的局部变量表中的i=1;②到第二行代码时，右边i先入操作数栈，此时值为1，然后执行++操作，局部变量表中的i的值就变成了2；③执行=赋值操作，将操作数栈中的i=1赋值给局部变量表中的i=2，那么最终i=1;

## 类的初始化与实例的初始化

一、类的初始化，先类的初始化在是实例的初始化，类的初始化在main方法执行时执行。main方法执行时，父类先初始化，此时静态属性，静态代码块按循序执行。然后子类初始化，此时静态属性，静态代码块按循序执行。

二、实例的初始化，new对象的时候执行。父类实例先初始化，此时父类非静态属性、非静态代码块，构造方法(最后执行)按顺序执行。然后子类实例初始化，此时非静态属性、非静态代码块，构造方法(最后执行)按顺序执行。

![1584970590602](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1584970590602.png)

三、如果子类继承父类，并且一个方法在子类和父类中都有，那么父类对象调用这个方法时，执行的是子类中的这个方法，多态特性。会先在子类中找方法，如果子类中有这个方法，那么就执行子类中的这个方法，没有才执行父类中的方法。

![1584971784165](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1584971784165.png)

![1584971825603](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1584971825603.png)



![1584971616510](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1584971616510.png)

![1585041596724](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1585041596724.png)

## cmd启动consul

consul agent -dev



## 程序运行卡在某一处

死锁、用jps、jstack命令排查死锁。

解决：重启服务器，停一下程序。




