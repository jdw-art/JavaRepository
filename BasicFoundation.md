# 一、集合

## 1.1、Java 中的几种基本数据类型是什么

| 简单类型 | boolean | byte | char      | short | Int     | long | float | double |
| -------- | ------- | ---- | --------- | ----- | ------- | ---- | ----- | ------ |
| bit位数  | 1       | 8    | 16        | 16    | 32      | 64   | 32    | 64     |
| 包装类   | Boolean | Byte | Character | Short | Integer | Long | Float | Double |

java10中可以用`var`关键字来定义局部变量。var相当于一种动态类型，在定义局部变量时，任意什么类型都可以用var定义变量的类型会根据所赋的值来判断。

## 1.2、对应的包装类型是什么

**Java是一种面向对象语言，很多地方都需要使用对象而不是基本数据类型。\**比如，在集合类中，我们是无法将 int 、double 等类型放进去的。因为\**集合的容器要求元素是 Object 类型**。

为了让基本类型也具有对象的属性，就出现了包装类型。相当于**将基本数据类型包装起来，使其具有对象的性质，并为其添加属性和方法，丰富了对基本数据类型的操作**。

| 原始类型 | 包装类型  |
| -------- | --------- |
| boolean  | Boolean   |
| byte     | Byte      |
| char     | Character |
| float    | Float     |
| int      | Integer   |
| long     | Long      |
| short    | Short     |
| double   | Double    |

- **装箱：** 将基本类型转化成包装类型。
- **拆箱：** 将包装类型转化为基本类型。

**当基础类型和它们的包装类出现一下几种情况时，编译器会自动装箱或拆箱。**

- 赋值操作（装箱或拆箱）
- 进行加减乘除等混合操作时（拆箱）
- 进行>、<、==比较运算时（拆箱）
- 使用equals进行比较（装箱）
- **ArrayList、HashMap等集合类型添加基础类型数据时**（装箱）

## 1.3、String、 StringBuffer 和StringBuilder的区别是什么

- 可变性：
  - Strnig不可变。
  - StringBuffer、StringBuilder可变。
- 线程安全：
  - String不可变，因此是线程安全的。
  - **StringBuffer是线程安全的，内部使用synchronized进行同步**。
  - StringBuilder不是线程安全的。

## 1.4、String为什么是不可变的?

**如果一个对象在创建完后，不能再改变它的状态，那么该对象就是不可变的。\**不能改变状态的意思是：不能改变对象内的成员变量，包括\**基本数据类型的值不能改变，引用类型的变量不能指向其他对象，引用类型指向的对象的状态也不能改变**。

```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final char value[];

    /** Cache the hash code for the string */
    private int hash; // Default to 0
}
```

从String的源码中可以看出，**字符串的存储实际上是一个个字符存储在value数组中的结果，同时value被final修饰，被final修饰的变量，值不能被修改**。因此value不能指向其他对象。并且，**String类中的所有字段都被private修饰，也就是说String没有对外提供修改内部状态的方法**，因此String是不可变的。

***String为什么设计成不可变：***

- **线程安全**：同一个字符串可以被多个线程共享。由于字符串不可变，本身就是线程安全的。
- **支持Hash映射和缓存**：String的Hash值经常会被使用，比如作为Map的键，由于String不可变，因此Hash值也是不可变的，不需要重新计算。
- **出于安全考虑**：网络地址URL、文件地址、密码通常情况下都是使用String类型存储的，如果String不是固定不变的，将会引起各种安全隐患。
- **字符串常量池优化**：String对象创建后，会缓存到字符串常量池中，下次需要创建同样的对象时，可以直接返回缓存的引用。

**当使用`substring`、`replace`、`replaceAll`方法操作String时并没有改变String对象，而是在堆内存中创建一个新的对象，然后value数组引用指向不同的对象。**

## 1.5、new String("zifuchaun")会创建几个对象

使用这种方式会创建两个字符串对象（前提是字符串常量池中没有 "zifuchuan" 这个字符串对象）。

- "zifuchaun" 属于字符串字面量（字符串字面量就是两个双引号之间的字符序列），因此编译时期会在**字符串常量池**中创建一个字符串对象，指向这个"zifuchuan" 字符串字面量；
- 使用 new 的方式会**在堆中创建一个字符串对象**。

## 1.6、equals和==

- 对于基本数据类型，比较的是它们的值，**基本数据类型没有equals方法**。
- 对于**复合数据类型，比较的是它们的存放地址（是否是同一个对象）**。equals()默认比较地址值。

## 1.7、equals和hashCode

equals和hashCode的关系：

- 两个对象调用equals返回true，那么它们的hashCode不一定相同。
- 两个对象的hashCode相同，它们并不一定相同。

**hashCode的主要作用是用来提升对象之间的比较效率**。*先进行hashCode比较，如果不相同，就没有必要再进行equals比较，这样大大减少了equals的比较次数， 当比较对象的数量很大时可以提升一定效率。*

之所以要重写equals()的同时重写hashCode()，是为了保证equals()方法返回true的情况下hashCode的值也相同，如果重写了equals()，没有重写hashCode()，就会出现两个对象相等但是hashCode()不相等的情况。这样当其中一个对象当作键存储在hashMap、hashTable或hashSet中时，再对另一个对象作为键值查询时，就会查找失败。

## 1.8、包装类型的缓存机制了解么

Java 基本数据类型的包装类型的大部分都用到了缓存机制来提升性能。

`Byte`,`Short`,`Integer`,`Long` 这 4 种包装类默认创建了数值 **[-128，127]** 的相应类型的缓存数据，`Character` 创建了数值在 **[0,127]** 范围的缓存数据，`Boolean` 直接返回 `True` or `False`。

## 1.9、深拷贝和浅拷贝

**浅拷贝：** 拷贝对象和原始对象的引用类型引用同一个对象。

- 对于基本数据类型的成员变量，浅拷贝直接进行值传递，也就是将属性值复制了一份给新的成员变量
- 对于引用数据类型的成员变量，比如成员变量是数组、某个类的对象等，浅拷贝就是引用的传递，也就是将成员变量的引用（内存地址）复制了一份给新的成员变量，他们指向的是同一个事例。在一个对象修改成员变量的值，会影响到另一个对象中成员变量的值。

```java
public class Cat implements Cloneable {
    private String name;
    private Person owner;

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }

    public static void main(String[] args) throws CloneNotSupportedException {
        Cat c = new Cat();
        Person p = new Person(18, "程序员大彬");
        c.owner = p;

        Cat cloneCat = (Cat) c.clone();
        p.setName("大彬");
        System.out.println(cloneCat.owner.getName());
    }
    //output
    //大彬
}
```

**深拷贝：** 拷贝对象和原始对象的引用类型引用不同的对象。

- 对于基本数据类型，深拷贝复制所有基本数据类型的成员变量的值
- 对于引用数据类型的成员变量，深拷贝申请新的存储空间，并复制该引用对象所引用的对象，也就是将整个对象复制下来。所以在一个对象修改成员变量的值，不会影响到另一个对象成员变量的值。

**clone函数不仅调用了super.clone，而且还调用了Person对象的clone方法，从而实现了深拷贝**。拷贝对象的值不会受到原对象的影响。

```java
public class Cat implements Cloneable {
    private String name;
    private Person owner;

    @Override
    protected Object clone() throws CloneNotSupportedException {
        Cat c = null;
        c = (Cat) super.clone();
        c.owner = (Person) owner.clone();//拷贝Person对象
        return c;
    }

    public static void main(String[] args) throws CloneNotSupportedException {
        Cat c = new Cat();
        Person p = new Person(18, "程序员大彬");
        c.owner = p;

        Cat cloneCat = (Cat) c.clone();
        p.setName("大彬");
        System.out.println(cloneCat.owner.getName());
    }
    //output
    //程序员大彬
}
```

## 1.10、Java注解

`Annotation` （注解） 是 Java5 开始引入的新特性，可以看作是一种特殊的注释，主要用于修饰类、方法或者变量，提供某些信息供程序在编译或者运行时使用。

注解本质是一个继承了`Annotation` 的特殊接口：

```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.SOURCE)
public @interface Override {

}

public interface Override extends Annotation{

}
```

JDK 提供了很多内置的注解（比如 `@Override`、`@Deprecated`），同时，我们还可以自定义注解。

### 注解的解析方法有哪几种？

注解只有被解析之后才会生效，常见的解析方法有两种：

- **编译期直接扫描**：编译器在编译 Java 代码的时候扫描对应的注解并处理，比如某个方法使用`@Override` 注解，编译器在编译的时候就会检测当前的方法是否重写了父类对应的方法。
- **运行期通过反射处理**：像框架中自带的注解(比如 Spring 框架的 `@Value`、`@Component`)都是通过反射来进行处理的。

## 1.11、Java异常体系

Java异常类层次结构图：

![img](http://110.41.141.141:9000/weblog/4cb93960ec8e457ca9be296ca4c05657.png)

Java的异常体系主要基于两大类：Throwable类及其子类。Throwable有两个重要的子类：Error和Exception，它们分别代表了不同类型的异常情况。

- Error（错误）：表示运行时环境的错误。错误是程序无法处理的严重问题，如系统崩溃、虚拟机错误、动态链接失败等。通常，程序不应该尝试捕获这类错误。例如，OutOfMemoryError、StackOverflowError等。
- Exception（异常）：表示程序本身可以处理的异常条件。异常分为两大类：
  - 非运行时异常：这类异常在编译时期就必须被捕获或者声明抛出。它们通常是外部错误，如文件不存在（FileNotFoundException）、类未找到（ClassNotFoundException）等。非运行时异常强制程序员处理这些可能出现的问题，增强了程序的健壮性。
  - 运行时异常：这类异常包括运行时异常（RuntimeException）和错误（Error）。运行时异常由程序错误导致，如空指针访问（NullPointerException）、数组越界（ArrayIndexOutOfBoundsException）等。运行时异常是不需要在编译时强制捕获或声明的。

## 1.12、泛型

**允许在定义类和接口时使用类型参数**。声明的类型参数在使用时用具体的类型替换。

允许定义类，接口时通过一个标识表示某个属性的类型或者是某个方法的返回值或者是参数类型，参数类型在具体使用的时候确定，在使用之前对类型进行检查。

**泛型的最大好处是可以提高代码的复用性**。以List接口为例，我们可以将String、 Integer等类型放⼊List中， 如不⽤泛型， 存放String类型要写⼀个List接口， 存放Integer要写另外⼀个List接口， 泛型可以很好的解决这个问题。

## 1.13、类型擦除

类型擦除机制是Java语言处理泛型的一种方式，它保证了泛型代码的向后兼容性，即能在没有泛型的老版本Java环境中运行。简而言之，类型擦除意味着在编译时期，所有关于泛型类型参数的信息都会被擦除，实际生成的字节码中并不包含这些类型参数，而是统一替换为对应的原始类型（如 List<String> 被擦除为 List）。尽管如此，编译器仍然会进行类型检查，确保类型安全，同时在必要时插入类型转换代码。

如何有效运用类型擦除机制
1. 理解类型擦除的局限
* 避免运行时类型检查：认识到无法直接通过反射获取确切的泛型类型参数，因此设计时应尽量减少对运行时类型信息的需求。
* 使用通配符和界限：合理利用 ? extends T 和 ? super T 通配符，以及泛型的上下界，可以使代码更加灵活且类型安全。
2. 利用超类型令牌（Super Type Tokens）
* 当确实需要在运行时知道泛型类型信息时，可以使用超类型令牌技术。这是一个绕过类型擦除，获取泛型类型信息的技巧。示例：

```java
public class Example {
    public static <T> void printListType(List<T> list, Class<T> clazz) {
        System.out.println("List contains elements of type: " + clazz.getName());
    }
 
    public static void main(String[] args) {
        List<String> stringList = new ArrayList<>();
        printListType(stringList, String.class); // 传递类型参数的Class对象
    }
}
```

在这个例子中，通过传递 String.class 参数，我们能够在运行时确定列表元素的确切类型。

3. 注意泛型数组的创建
* 由于类型擦除，直接创建泛型数组会导致类型不安全，可以采用如下方式规避：

```java
public static <T> T[] newArray(Class<T> clazz, int size) {
    return (T[]) Array.newInstance(clazz, size);
}
 
List<String>[] stringLists = newArray(List.class, 10); // 需要注意类型转换的安全性
```

4. 利用泛型方法
* 泛型方法可以提供灵活性，避免了由于擦除导致的类型不匹配问题，例如：

```java
public static <T> T getFirst(List<T> list) {
    if (!list.isEmpty()) {
        return list.get(0);
    }
    return null;
}
```

## 1.14、BIO、NIO和AIO的区别

- **同步阻塞IO（BIO）：** 用户进程发起一个IO操作后，必须等待IO操作真正完成后，才能继续运行。
- **同步非阻塞IO（NIO）：\**客户端和服务器\**通过channel连接**，采用**多路复用轮询注册的channel**。提高吞吐量和可靠性。用户发起一个IO操作后可以做其他事情，但是**用户进程需要轮询IO操作是否完成，这样会造成不必要的cpu资源浪费。**
- **异步非阻塞IO（AIO）：\**非异步阻塞通讯模式，NIO的升级版，采用\**异步通道实现异步通信**，其write和read均为异步方法。用户进程发起一个IO操作，然后立即返回，等IO操作真正完成后，应用程序会得到一个IO操作完成的通知。类似于多线程中的future模式。

# 二、集合

## 2.1、List、Map、Set的区别

- List 以索引来存取元素，有序的，元素是允许重复的，可以插入多个null；
- Set 不能存放重复元素，无序的，只允许一个null；
- Map 保存键值对映射；
- List的底层实现有**数组和链表**两种方式，Set和Map有基于**哈希存储和红黑树**两种方式。
- Set基于Map实现，**Set里的值就是Map的键值**。

## 2.2、有哪些集合是线程不安全的

- 线程安全的集合：

  - Vector，比ArrayList多了同步机制。
  - HashTable
  - ConcurrentHashMap：一种高效且线程安全的集合。
  - Stack：栈也是线程安全的，基于Vector。

- 线程不安全的集合

  ：

  - HashMap
  - ArrayDeque
  - ArrayList
  - LinkedList
  - HashSet
  - TreeSet
  - TreeMap

## 2.3、HashSet、LinkedHashSet和TreeSet的区别

- **HashSet是接口Set的实现类，底层是HashMap**，是线程不安全的，可以存储Null值。
- **LinkedHashSet是HashSet的子类**，能够按照添加元素的顺序进行遍历。
- **TreeSet底层是红黑树**，能够根据添加元素的顺序进行遍历，排序的方式可以自定义。

## 2.4、HashMap和HashTable的区别

- **HashMap中允许为null的key和value**，key为null的键值对放在下标为0的头结点的链表中，而HashTable则不行。
- **HashMap是非线程安全的**，而HashTable是线程安全的。在jdk1.5中提供了ConcurrentHashMap作为HashTable的替代品。
- **HashTable有很多方法是同步的，在单线程环境下它比HashMap要慢。**
- Hash值的使用不同，**HashTable直接使用对象的HashCode**，而HashMap需要重新计算Hash值。

## 2.5、HashMap的底层实现

**HashMap使用数组+链表+红黑树实现**。链表长度大于`8`时，会把链表转换为红黑树。红黑树的节点小于`6`时，才会把红黑树转换为链表，防止频繁的转化。

### 扩容过程

- **java1.7扩容机制：\**新节点采用的头插法，因此在线程进行扩容迁移元素时，会\**改变元素顺序，导致两个线程中出现的元素的相互指向而形成循环链表**， 1.8采用了尾插法，避免了这种情况。
- **java1.8扩容机制：\**当元素个数大于threshold时，会进行扩容，使用\**2倍容量**的数组替代原有数组。采用**尾插法**将原数组的元素拷贝到新数组中。**1.8扩容之后元素的相对位置不会发生改变**，1.7扩容之后元素的位置会发生倒置。

### put方法的流程

- 如果table没有初始化就进行初始化过程。
- 使用hash算法计算key的索引。
- 判断索引处有没有存在元素，如果没有则直接插入。
- 如果索引处存在元素，则遍历插入。
  - 如果是链表形式就直接遍历到尾端插入。
  - 如果是红黑树就按照红黑树结构插入。
- 链表的数量大于阈值8，就要转换成红黑树的结构。
- **添加成功后会检查是否需要扩容。**

## 2.6、HashMap的长度为什么是2的幂次方

Hash值的范围值比较大，使用之前需要对数组的长度进行取模运算，得到的余数才是元素存放的位置也就是对应的数组下标。这个下标的计算方式是`(n - 1) & hash`。将**HashMap的长度定为2的幂次方，这样就可以使用`(n - 1) & hash`位运算代替`%`运算，提高性能**。（**使用位运算代替取余运算**）

## 2.7、hashtable 和concurrentHashMap有什么区别

- 底层数据结构：
  - jdk7之前的ConcurrentHashMap底层采用的是**分段的数组+链表**实现，jdk8之后采用的是**数组+链表/红黑树；**
  - HashTable采用的是**数组+链表，** 数组是主体，链表是解决hash冲突存在的。
- 实现线程安全的方式：
  - Hashtable是通过使用synchronized修饰方法的方式来实现多线程同步，因此，Hashtable的同步会锁住整个数组。在高并发的情况下，性能会非常差。ConcurrentHashMap会使用更细粒度的锁提高在并发时的效率。synchronized容器（并发容器）也是通过synchronized关键字来实现线程安全，在使用时会对所有的数据加锁。

## 2.8、HashMap和ConcurrentHashMap的区别

HashMap 不是线程安全的，ConcurrentHashMap是线程安全的。

> HashMap 底层实现

- 在 **JDK 1.7** 版本之前， HashMap 数据结构是**数组和链表**，HashMap通过哈希算法将元素的键（Key）映射到数组中的槽位（Bucket）。如果多个键映射到同一个槽位，它们会以链表的形式存储在同一个槽位上，因为链表的查询时间是O(n)，所以冲突很严重，一个索引上的链表非常长，效率就很低了。

  ![img](http://110.41.141.141:9000/weblog/weblog/ec6030f30bf44a82b81b839ab106910b.png)

- 所以在 **JDK 1.8** 版本的时候做了优化，当一个链表的长度超过8的时候就转换数据结构，不再使用链表存储，而是使用**红黑树**，查找时使用红黑树，时间复杂度O（log n），可以提高查询性能，但是在数量较少时，即数量小于6时，会将红黑树转换回链表。

  ![img](http://110.41.141.141:9000/weblog/weblog/60a7f297893047989e20eb29c407888f.png)

> ConcurrentHashMap 底层实现

- 在 **JDK 1.7** 中它使用的是数组加链表的形式实现的，而数组又分为：大数组 Segment 和小数组 HashEntry。Segment 是一种可重入锁（ReentrantLock），在 ConcurrentHashMap 里扮演锁的角色；HashEntry 则用于存储键值对数据。一个 ConcurrentHashMap 里包含一个 Segment 数组，一个 Segment 里包含一个 HashEntry 数组，每个 HashEntry 是一个链表结构的元素。简单理解就是，ConcurrentHashMap 是一个 Segment 数组，Segment 通过继承 ReentrantLock 来进行加锁，所以每次需要加锁的操作锁住的是一个 segment，这样只要保证每个 Segment 是线程安全的，也就实现了全局的线程安全。

  ![img](http://110.41.141.141:9000/weblog/weblog/bcf4b4875a1043648b55cf80a043c776.png)

- **JDK 1.8** 也引入了红黑树，优化了之前的固定链表，那么当数据量比较大的时候，查询性能也得到了很大的提升，从之前的 O(n) 优化到了 O(logn) 的时间复杂度。ConcurrentHashMap 主要通过 volatile + CAS 或者 synchronized 来实现的线程安全的，ConcurrentHashMap通过对头结点加锁来保证线程安全的，锁的粒度相比 Segment 来说更小了，发生冲突和加锁的频率降低了，并发操作的性能就提高了。

  ![img](http://110.41.141.141:9000/weblog/weblog/b418bbe1d7fd4f85ac94fa907da8c70d.png)