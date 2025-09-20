java中String、StringBuffer、StringBuilder是编程中经常使用的字符串类

-   可变与不可变
    String类中使用字符数组保存字符串，如下就是，因为有“final”修饰符，所以可以知道string对象是不可变的。

`private final char value[];`

StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数组保存字符串，如下就是，可知这两种对象都是可变的。

`char[] value;`

String 类型和StringBuffer的主要性能区别：String是不可变的对象, 因此在每次对String 类型进行改变的时候，都会生成一个新的 String 对象，然后将指针指向新的 String 对象。

```java
// 初始化abc对象，新建一个efghti对象，将str指针指向新的efghti，完成重新赋值。abc由gc进行回收。
String str = "abc";
str = "efghti对象，";
```

-   是否多线程安全

String中的对象是不可变的，也就可以理解为常量，`显然线程安全`。  
AbstractStringBuilder是StringBuilder与StringBuffer的公共父类，定义了一些字符串的基本操作，如expandCapacity、append、insert、indexOf等公共方法。  
StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以是`线程安全的`。看如下源码：  

```java
public synchronized StringBuffer reverse() {
    super.reverse();
    return this;
}

public int indexOf(String str) {
    return indexOf(str, 0);        //存在 public synchronized int indexOf(String str, int fromIndex) 方法
}
```

StringBuilder并没有对方法进行加同步锁，所以是`非线程安全`的。

-   StringBuilder与StringBuffer共同点
    StringBuilder与StringBuffer有公共父类AbstractStringBuilder(抽象类)。  
    抽象类与接口的其中一个区别是：抽象类中可以定义一些子类的公共方法，子类只需要增加新的功能，不需要重复写已经存在的方法；而接口中只是对方法的申明和常量的定义。  
    StringBuilder、StringBuffer的方法都会调用AbstractStringBuilder中的公共方法，如super.append(...)。只是StringBuffer会在方法上加synchronized关键字，进行同步。  

`基本原则1：如果要操作少量的数据，用String ；单线程操作大量数据，用StringBuilder ；多线程操作大量数据，用StringBuffer。`

`基本原则2：不要使用String类的"+"来进行频繁的拼接，因为那样的性能极差的，应该使用StringBuffer或StringBuilder类`

使用以下代码来测试String和StringBuffer在时间和空间使用上的差别。

```java
public class Test {  
    public static void main(String args[]) {  
          
        String str = "abc";  
        StringBuffer sb = new StringBuffer("abc");  
        Runtime runtime = Runtime.getRuntime();  
        long start = System.currentTimeMillis();  
        long startFreememory = runtime.freeMemory();  
        for (int i = 0; i < 10000; i++) {  
            str += i;  
            //测试StringBuffer时候把注释打开  
            //sb.append(i);  
        }  
        long endFreememory = runtime.freeMemory();  
        long end = System.currentTimeMillis();  
        System.out.println("操作耗时:" + (end - start) + "ms," + "内存消耗:"  
                + (startFreememory - endFreememory)/1024 + "KB");  
    }  
} 
```

测试结果：  
使用String做10000次向一字符串后添加字符串  
操作耗时:1872ms,内存消耗:1301KB  

使用StringBuffer做10000次向一字符串后添加字符串  
操作耗时:15ms,内存消耗:162KB  
**差别显著！**  
