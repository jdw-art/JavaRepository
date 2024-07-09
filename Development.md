#  一、Java

## 1、Java特点

* **面向对象**。
* **平台独立性和移植性**。***已编译的Java程序可以在任何带有JVM的平台上运行**。*你可以在windows平台编写代码，然后拿到linux上运行。只要你在编写完代码后，将代码编译成.class文件，再把class文件打成Java包，这个jar包就可以在不同的平台上运行了。(linux部署)
* **稳健性**。
  * Java是一个强类型语言，它***允许扩展编译时检查潜在类型不匹配问题的功能***。Java***要求显式的方法声明***，它不支持C风格的隐式声明。这些严格的要求保证编译程序能捕捉调用错误，这就导致更可靠的程序。
  * ***异常处理***是Java中使得程序更稳健的另一个特征。**异常是某种类似于错误的异常条件出现的信号。**使用try/catch/finally 语句，程序员可以找到出错的处理代码，这就简化了出错处理和恢复的任务。

## 2、Java是如何实现跨平台的

**Java通过JVM实现跨平台。**

JVM可以看作是一个软件，编写的Java代码在编译后会生成一个`.class`文件（字节码文件），而**JVM的作用就是将字节码文件翻译成特定平台下的机器码，着这样才能运行。**不同平台下编译生成的字节码是一样的，但是由JVM翻译成的机器码却不一样。**只要在不同平台上安装对应的JVM，就可以运行字节码文件，运行我们编写的Java程序。**

***因此，运行Java程序必须有JVM的支持，因为编译的结果不是机器码，必须要经过JVM的翻译才能执行。***

## 3、Java与C++的区别

* Java是**面向对象**语言，所有的对象都继承自java.long.Object，而**C++不仅支持面向对象也支持面向过程**。
* Java**通过虚拟机实现跨平台特性**，而C++不支持跨平台。
* Java中**没有指针**，但*它的引用可以理解为安全指针*，而C++和C一样都有指针。
* Java**支持自动垃圾回收**，C++需要手动回收。
* Java**不支持多重继承**，它需要通过实现多个接口来达到相同目的，而C++支持多重继承。

## 4、JDK、JRE和JVM的关系

![img](http://img.topjavaer.cn/img/20220402230613.png)

* **JVM（Java Virtual Machine）**：Java虚拟机，Java通过JVM实现跨平台交互。每个Java文件都会生成一个`.class`文件，`.class`文件并不与操作系统直接交互，而是通过JVM间接和操作系统交互，JVM通过将字节码翻译成机器码解释给操作系统执行。针对不同的J操作系统有不同的JVM，比如Linux下的JVM和Windows下的JVM，不同的操作系统生成的字节码是相同的，但经过JVM生成的机器码是不同的。
* **JRE（Java Runtime Environment）**：Java运行环境，我们编写的Java程序必须要在JRE才能运行。它主要包含两个部分，JVM 和 Java 核心类库。 **JRE只是Java的运行环境，并不是开发环境，因此并不包含编译器和调试器。**
* **JDK（Java Development Kit）**：**Java开发工具包**，JDK中已经集成了JRE，因此不需要单独安装JRE。

因此：

* **JRE = JVM + Java 核心类库**
* **JDK = JRE + Java工具 + 编译器 + 调试器**

## 5、Java程序是编译执行还是解释执行

* **编译型语言**：在程序运行之前，通过编译器将源程序编译成机器码可运行的二进制，以后执行这个程序时，就不用再进行编译了。***执行速度快、效率高；依靠编译器、跨平台性差些。***
  * **优点：**编译器一般会有**预编译**的过程对代码进行优化。因为编译只做一次，运行时不需要编译，所以编译型语言的程序执行效率高，可以脱离语言环境独立运行。
  * **缺点：**编译之后如果需要修改就需要整个模块重新编译。编译的时候根据对应的运行环境生成机器码，不同的操作系统之间移植就会有问题，需要根据运行的操作系统环境编译不同的可执行文件。

* **解释型语言**：解释型语言的源代码不是直接翻译成机器码，而是**先翻译成中间代码**，再由解释器对中间代码进行解释运行。在运行的时候才将源程序翻译成机器码，翻译一句，然后执行一句，直至结束。***解释型语言执行速度慢、效率低；依靠解释器、跨平台性好。***
  * **优点：**1、有良好的平台兼容性，在任何环境中都可以运行，前提是安装了解释器（如虚拟机）。2、灵活，修改代码的时候直接修改就可以，可以快速部署，不用停机维护。
  * **缺点：**每次运行的时候都要解释一遍，性能上不如编译型语言。

对于Java语言，**它的源代码会先通过javac编译成字节码，然后通过JVM将字节码翻译成机器码**，即解释运行和编译运行配合使用，所以可以称为***混合型或半编译型***。

## 6、面向过程和面向对象

* **面向过程**是先分析解决问题所需要的步骤，然后用函数按这些步骤实现，使用的时候一次调用这些函数即可。
* **面向对象**是将**构成问题事务分解成各个对象**，分别设计这些对象，然后组装成具有完整功能的系统。

**面向过程只用函数实现，而面向对象使用类来实现各个功能模块。**

## 7、面向对象的特点

* **封装：**把类的信息隐藏在类的内部，不允许外部程序直接访问，而是**通过该类的方法实现对隐藏信息的操作和访问**。良好的封装能够减少耦合。
* **继承：** **从已有的类中派生出新的类**，新的类继承父类的属性和行为，并能扩展新的能力，大大增加了程序的重用性和可维护性。Java是单继承的，也就是说一个子类只能有一个父类。
* **多态：** **同一个行为具有不同表现形式的能力**。在不修改程序代码的前提下改变程序运行时绑定的代码。**实现多态的三要素：继承、重写、父类引用指向子类对象。**
  * **静态多态性：**相同的方法具有不同的参数列表，根据参数的不同做出不同的处理。
  * **动态多态性：**在子类中重写父类的方法。运行期间判断所引用的对象的实际类型，根据实际类型调用相应的方法。
* **抽象：**把客观事实用代码抽象出来。

## 8、面向对象编程的六大原则

* **对象单一职责**：我们设计创建的对象，必须职责明确，比如商品类，里面相关的属性和方法都必须跟商品相关，不能出现订单等不相关的内容。这里的类可以是模块、类库、程序集，而不单单指类。
* **里式替换原则**：子类能够完全替代父类，反之则不行。通常用于实现接口时运用。因为子类能够完全替代基（父）类，那么这样父类就拥有很多子类，在后续的程序扩展中就很容易进行扩展，程序完全不需要进行修改即可进行扩展。比如IA的实现为A，因为项目需求变更，现在需要新的实现，直接在容器注入处更换接口即可.
* **迪米特法则**：也叫最小原则，或者说最小耦合。通常在设计程序或开发程序的时候，尽量要高内聚，低耦合。当两个类进行交互的时候，会产生依赖。而迪米特法则就是建议这种依赖越少越好。就像构造函数注入父类对象时一样，当需要依赖某个对象时，并不在意其内部是怎么实现的，而是在容器中注入相应的实现，既符合里式替换原则，又起到了解耦的作用。
* **开闭原则**：开放扩展，封闭修改。当项目需求发生变更时，要尽可能的不去对原有的代码进行修改，而在原有的基础上进行扩展。
* **依赖倒置原则**：高层模块不应该直接依赖于底层模块的具体实现，而应该依赖于底层的抽象。接口和抽象类不应该依赖于实现类，而实现类依赖接口或抽象类。
* **接口隔离原则**：一个对象和另外一个对象交互的过程中，依赖的内容最小。也就是说在接口设计的时候，在遵循对象单一职责的情况下，尽量减少接口的内容。

精简：

* 单一职责：**对象设计要求独立，不能设计万能对象。**
* 开闭原则：**对象修改最小化。**
* 里式替换：**程序扩展中抽象被具体可以替换（接口、父类、可以被实现类对象、子类替换对象）**
* 迪米特：**高内聚，低耦合。尽量不要依赖细节。**
* 依赖倒置：**面向抽象编程。也就是参数传递，或者返回值，可以使用父类类型或者接口类型。从广义上讲：基于接口编程，提前设计好接口框架。**
* 接口隔离：**接口设计大小要适中。**过大导致污染，过小，导致调用麻烦。

## 9、数组是不是对象

*对象是根据类创建的一个实例，表示某类事物中具体的个体*

对象具有各种属性，并且具有一些特定的行为。从计算机的角度来看，对象就是内存中的一个内存块，在这个内存块中封装了一些数据，也就是类中定义的各种属性。**因此对象就是用来封装数据的。**

而Java中的数组具有对象的一些特性，比如封装了一些数据，可以调用属性也可以调用方法。

**因此可以说数组就是对象。**

```java
Class clz = int[].class;
System.out.println(clz.getSuperclass().getName());
```

**在Java中，数组类的父类就是Object，因此数组就是对象。**

## 10、Java的基本数据类型

| 简单类型 | boolean | byte |   char    | short |   Int   | long | float | double |
| :------: | :-----: | :--: | :-------: | :---: | :-----: | :--: | :---: | :----: |
| bit位数  |    1    |  8   |    16     |  16   |   32    |  64  |  32   |   64   |
|  包装类  | Boolean | Byte | Character | Short | Integer | Long | Float | Double |

java10中可以用`var`关键字来定义局部变量。var相当于一种动态类型，在定义局部变量时，任意什么类型都可以用var定义变量的类型会根据所赋的值来判断。

## 11、为什么不能用浮点数表示金额

**计算机中保存的小数实际上是十进制的小数的近似值**，并不是准确值。可以使用`BigDecimal`或者`Long`来表示金额。

## 12、什么是值传递和引用传递

* **值传递**是对**基本型**的变量而言的，**传递的是该变量的一个副本**，改变副本不会影响原变量。
* **引用传递**是一般是对于**对象型变量**而言的，**传递的是该对象地址的一个副本**，并不是原对象本身，两者指向同一片内存空间。所以**对引用对象进行操作时会改变原对象**。

## 13、什么时Java的包装类型？为什么需要包装类？

**Java是一种面向对象语言，很多地方都需要使用对象而不是基本数据类型。**比如，在集合类中，我们是无法将 int 、double 等类型放进去的。因为**集合的容器要求元素是 Object 类型**。

为了让基本类型也具有对象的属性，就出现了包装类型。相当于**将基本数据类型包装起来，使其具有对象的性质，并为其添加属性和方法，丰富了对基本数据类型的操作**。

## 14、自动装箱和拆箱

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

* **装箱：**将基本类型转化成包装类型。
* **拆箱：**将包装类型转化为基本类型。

**当基础类型和它们的包装类出现一下几种情况时，编译器会自动装箱或拆箱。**

* 赋值操作（装箱或拆箱）
* 进行加减乘除等混合操作时（拆箱）
* 进行>、<、==比较运算时（拆箱）
* 使用equals进行比较（装箱）
* **ArrayList、HashMap等集合类型添加基础类型数据时**（装箱）

例如：

```java
Integer x = 1; // 装箱 调⽤ Integer.valueOf(1)
int y = x; // 拆箱 调⽤了 X.intValue()
```

## 15、String为什么不可变

**如果一个对象在创建完后，不能再改变它的状态，那么该对象就是不可变的。**不能改变状态的意思是：不能改变对象内的成员变量，包括**基本数据类型的值不能改变，引用类型的变量不能指向其他对象，引用类型指向的对象的状态也不能改变**。

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

* **线程安全**：同一个字符串可以被多个线程共享。由于字符串不可变，本身就是线程安全的。
* **支持Hash映射和缓存**：String的Hash值经常会被使用，比如作为Map的键，由于String不可变，因此Hash值也是不可变的，不需要重新计算。
* **出于安全考虑**：网络地址URL、文件地址、密码通常情况下都是使用String类型存储的，如果String不是固定不变的，将会引起各种安全隐患。
* **字符串常量池优化**：String对象创建后，会缓存到字符串常量池中，下次需要创建同样的对象时，可以直接返回缓存的引用。

**当使用`substring`、`replace`、`replaceAll`方法操作String时并没有改变String对象，而是在堆内存中创建一个新的对象，然后value数组引用指向不同的对象。**

## 16、为什么JDK9把String的底层实现由char[]改成byte[]

主要是为了**节约String占用的内存**。

在大部分Java程序的堆内存中，String占用的空间最大，并且绝大多数String只有Latin-1字符，这些Latin-1字符只需要1个字节就够了。

而在JDK9之前，JVM因为String使用char数组存储，每个char占2个字节，所以即使字符串只需要1字节，它也要按照2字节进行分配，浪费了一半的内存空间。

到了JDK9之后，对于每个字符串，会先判断它是不是只有Latin-1字符，如果是，就按照1字节的规格进行分配内存，如果不是，就按照2字节的规格进行分配，这样便提高了内存使用率，同时GC次数也会减少，提升效率。

不过Latin-1编码集支持的字符有限，比如不支持中文字符，因此对于中文字符串，用的是UTF16编码（两个字节），所以用byte[]和char[]实现没什么区别。

## 17、String、StringBuffer、StringBuilder的区别

* 可变性：
  * Strnig不可变。
  * StringBuffer、StringBuilder可变。
* 线程安全：
  * String不可变，因此是线程安全的。
  * **StringBuffer是线程安全的，内部使用synchronized进行同步**。
  * StringBuilder不是线程安全的。

## 18、什么是StringJoiner

StringJoiner是基于StringBuilder实现，用于实现对字符串之间**通过分隔符拼接**的场景。

StringJoiner有两个构造方法，第一个构造方法要求传入分隔符、前缀和后缀。第二个构造方法只需要传入分隔符。

```java
StringJoiner(CharSequence delimiter, CharSequence prefix, CharSequence suffix)
StringJoiner(CharSequence delimiter)
```

以下是使用StringBuilder和StringJoiner的比较

```java
List<Integer> values = Arrays.asList(1, 3, 5);
StringBuilder sb = new StringBuilder("(");
for (int i = 0; i < values.size(); i++) {
sb.append(values.get(i));
if (i != values.size() -1) {
sb.append(",");
}
}
sb.append(")");
```

```java
List<Integer> values = Arrays.asList(1, 3, 5);
StringJoiner sj = new StringJoiner(",", "(", ")");
for (Integer value : values) {
sj.add(value.toString());
}
```

## 19、String类的常用方法

* **indexOf()**：返回指定字符的索引。
* **charAt()**：返回指定索引处的字符。
* **replace()**：字符串替换。
* **trim()**：去除字符串两端空白。
* **split()**：分割字符串，返回一个分割后的字符串数组。
* **getBytes()**：返回字符串的 byte 类型数组。
* **length()**：返回字符串长度。
* **toLowerCase()**：将字符串转成小写字母。
* **toUpperCase()**：将字符串转成大写字符。
* **substring()**：截取字符串。
* **equals()**：字符串比较。

## 20、new String("zifuchaun")会创建几个对象

使用这种方式会创建两个字符串对象（前提是字符串常量池中没有 "zifuchuan" 这个字符串对象）。

* "zifuchaun" 属于字符串字面量（字符串字面量就是两个双引号之间的字符序列），因此编译时期会在**字符串常量池**中创建一个字符串对象，指向这个"zifuchuan" 字符串字面量；
* 使用 new 的方式会**在堆中创建一个字符串对象**。

## 21、什么是字符串常量池

字符串常量池保存着所有的字符串字面量，这些字面量在编译时就已经确定，**字符串常量池通常位于堆内存中，专门用来存储字符串常量**。在创建一个字符串时，JVM首先会检查字符串常量池中是否存在该字符串，如果有则直接引用，否则重新创建一个字符串并存入字符串常量池中。

## 22、String的最大长度是多少

String中有一个length方法，返回值为int类型，而int的取值为`2^31 - 1`。因此理论上String的最大长度为`2^31 - 1`。

**达到最大长度需要多大的内存：**

* String内部是使用一个char数组来维护字符序列的，一个char占用两个字节。如果说String最大长度是`2^31 - 1`的话，那么最大的字符串占用内存空间约等于4GB。

**String一般存储在JVM的哪个区域：**

* String在JVM以两种形式存储，一个是String对象，存储在堆内存中，一个是字符串常量，存储在字符串常量池中。

**什么情况下字符串会存储在常量池中：**

* 当通过字面量对字符串进行声明时，比如`String s = "zifuchuan"`，该字符串在编译后会以常量的形式存储在字符串常量池中。

**常量池中字符串的最大长度为多少：**

* Java中的UTF-8编码的Unicode字符串在常量池中以CONSTANT_Utf8类型表示。

  ```java
  CONSTANT_Utf8_info {
  u1 tag;
  u2 length;
  u1 bytes[length];
  }
  ```

  length在这里就是代表字符串的长度，length的类型是u2，u2是无符号的16位整数，也就是说最大长度可以做到2^16-1 即 65535。不过javac编译器做了限制，需要length < 65535。所以字符串常量在常量池中的最大长度是65535 - 1 =**65534**。

**String在不同状态下有不同的长度限制：**

* 字符串常量池中的最大长度为65534.
* 堆内存中的最大长度为`2^32 - 1`。

## 23、Object的常用方法

* **toString()：**默认输出对象的地址。

  ```java
  public class Person {
      private int age;
      private String name;
  
      public Person(int age, String name) {
          this.age = age;
          this.name = name;
      }
  
      public static void main(String[] args) {
          System.out.println(new Person(18, "程序员大彬").toString());
      }
      //output
      //me.tyson.java.core.Person@4554617c
  }
  ```

  可以重写toString方法，按照重写逻辑输出对象值。

  ```java
  public class Person {
      private int age;
      private String name;
  
      public Person(int age, String name) {
          this.age = age;
          this.name = name;
      }
  
      @Override
      public String toString() {
          return name + ":" + age;
      }
  
      public static void main(String[] args) {
          System.out.println(new Person(18, "程序员大彬").toString());
      }
      //output
      //程序员大彬:18
  }
  ```

* **equals()：**默认比较两个引用变量是否指向同一个对象（内存地址）。

  ```java
  public class Person {
      private int age;
      private String name;
  
      public Person(int age, String name) {
         this.age = age;
         this.name = name;
      }
  
      public static void main(String[] args) {
          String name = "程序员大彬";
          Person p1 = new Person(18, name);
          Person p2 = new Person(18, name);
  
          System.out.println(p1.equals(p2));
      }
      //output
      //false
  }
  ```

  可以重写equals方法，按照age和name是否相等来判断：

  ```java
  public class Person {
      private int age;
      private String name;
  
      public Person(int age, String name) {
          this.age = age;
          this.name = name;
      }
  
      @Override
      public boolean equals(Object o) {
          if (o instanceof Person) {
              Person p = (Person) o;
              return age == p.age && name.equals(p.name);
          }
          return false;
      }
  
      public static void main(String[] args) {
          String name = "程序员大彬";
          Person p1 = new Person(18, name);
          Person p2 = new Person(18, name);
  
          System.out.println(p1.equals(p2));
      }
      //output
      //true
  }
  ```

* **hashCode()：**将与对象相关的信息映射成一个哈希值，默认的实现hashCode值是根据内存地址换算出来。

  ```java
  public class Cat {
      public static void main(String[] args) {
          System.out.println(new Cat().hashCode());
      }
      //out
      //1349277854
  }
  ```

* **clone()：**得到对象的副本，实现了对象中各个属性的复制，但它的可见范围时protected的。

  ```java
  protected native Object clone() throws CloneNotSupportedException;
  ```

  所有实体类使用clone()的前提：

  * ***实现Cloneable接口***，这是一个标记接口，自身没有方法。调用clone方法时会先判断有没有实现Cloneable接口，没有实现的话会抛出异常CloneNotSupportedException。
  * ***覆盖clone方法***，将其可见性提升为public。

  ```java
  public class Cat implements Cloneable {
      private String name;
  
      @Override
      protected Object clone() throws CloneNotSupportedException {
          return super.clone();
      }
  
      public static void main(String[] args) throws CloneNotSupportedException {
          Cat c = new Cat();
          c.name = "程序员大彬";
          Cat cloneCat = (Cat) c.clone();
          c.name = "大彬";
          System.out.println(cloneCat.name);
      }
      //output
      //程序员大彬
  }
  ```

* **getClass()：**返回此Object的运行时类，常用于java反射机制。

  ```java
  public class Person {
      private String name;
  
      public Person(String name) {
          this.name = name;
      }
  
      public static void main(String[] args) {
          Person p = new Person("程序员大彬");
          Class clz = p.getClass();
          System.out.println(clz);
          //获取类名
          System.out.println(clz.getName());
      }
      /**
       * class com.tyson.basic.Person
       * com.tyson.basic.Person
       */
  }
  ```

* **wait()：**当前线程调用对象的wait方法后，当前线程会释放对象锁，进入等待状态。等待其他线程调用此对象的notify()/notifyAll()唤醒或等待超时wait(long timeout)自动唤醒。线程需要获取obj对象锁后才能调用obj.wait()。

* **notify()：**唤醒在此对象等待的单个线程，选择是任意性的。notifyAll()唤醒在此对象上的等待的所有线程。

## 24、深拷贝和浅拷贝

**浅拷贝：**拷贝对象和原始对象的引用类型引用同一个对象。

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

**深拷贝：**拷贝对象和原始对象的引用类型引用不同的对象。

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

## 25、两个对象的hashCode()相同，则equals是否也一定相同

equals和hashCode的关系：

* 两个对象调用equals返回true，那么它们的hashCode不一定相同。
* 两个对象的hashCode相同，它们并不一定相同。

**hashCode的主要作用是用来提升对象之间的比较效率**。*先进行hashCode比较，如果不相同，就没有必要再进行equals比较，这样大大减少了equals的比较次数， 当比较对象的数量很大时可以提升一定效率。*

之所以要重写equals()的同时重写hashCode()，是为了保证equals()方法返回true的情况下hashCode的值也相同，如果重写了equals()，没有重写hashCode()，就会出现两个对象相等但是hashCode()不相等的情况。这样当其中一个对象当作键存储在hashMap、hashTable或hashSet中时，再对另一个对象作为键值查询时，就会查找失败。

## 26、Java创建对象有几种方法

* 使用**new语句**创建对象。

  ```java
  ObjectName obj = new ObjectName();
  ```

* 使用**反射**，使用**Class.newInstance()**创建对象.

  ```java
  ObjectName obj = ObjectName.class.newInstance();
  ```

* 使用反射的**Constructor类的newInstance()**方法：

  ```java
  ObjectName obj = ObjectName.class.getConstructor.newInstance();
  ```

* 调用对象的**clone()**方法。

  ```java
  ObjectName obj = obj.clone();
  ```

* 运用**反序列化**手段，调用java.io.ObjectInputStream对象的readObject()方法。

  ```java
  try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream(FILE_NAME))) {
  
              ObjectName obj = ois.readObject();
  
          }
  ```

## 27、Java中类实例化的顺序

* 静态属性、静态代码块。
* 普通属性、普通代码块。
* 构造方法。

```java
public class LifeCycle {
    // 静态属性
    private static String staticField = getStaticField();

    // 静态代码块
    static {
        System.out.println(staticField);
        System.out.println("静态代码块初始化");
    }

    // 普通属性
    private String field = getField();

    // 普通代码块
    {
        System.out.println(field);
        System.out.println("普通代码块初始化");
    }

    // 构造方法
    public LifeCycle() {
        System.out.println("构造方法初始化");
    }

    // 静态方法
    public static String getStaticField() {
        String statiFiled = "静态属性初始化";
        return statiFiled;
    }

    // 普通方法
    public String getField() {
        String filed = "普通属性初始化";
        return filed;
    }

    public static void main(String[] argc) {
        new LifeCycle();
    }

    /**
     *      静态属性初始化
     *      静态代码块初始化
     *      普通属性初始化
     *      普通代码块初始化
     *      构造方法初始化
     */
}
```

## 28、equals和==有什么区别

* 对于基本数据类型，比较的是它们的值，**基本数据类型没有equals方法**。
* 对于**复合数据类型，比较的是它们的存放地址（是否是同一个对象）**。equals()默认比较地址值。

## 29、常见的关键字有哪些

* **static：** **static变量可以修饰类的成员方法**，也可以修饰类的成员变量。

  * static变量称为静态变量。**静态变量被所有的对象所共享，在内存中只有一个副本，它当且仅当类的初次加载时，才会被初始化**（只初始化一次）。而非静态变量是对象所拥有的，在创建对象的时候被初始化，存在多个副本，各个对象拥有的副本互不影响。
  * static方法称为静态方法。静态方法不依赖于任何对象就可以进行访问，通过类名即可调用静态方法。
  * 静态代码块只在类加载时才会被执行一次。
  * 静态内部类。**在静态方法里**，使用⾮静态内部类依赖于外部类的实例，也就是说需要先创建外部类实例，才能用这个实例去创建非静态内部类。⽽静态内部类不需要。

* **final:**

  * 基本数据类型用final修饰，则不能修改，是常量；对象引用用final修饰，则该引用只能指向该对象。
  * final修饰的方法不能被子类重写。
  * final修饰的类不能被继承。

* **this:**

  * this.属性名称指访问类中的成员变量，**可以用来区分成员变量和局部变量**。
  * this.方法名称用来访问本类中的方法。

* **super:**

  * super关键字用于**在子类中访问父类的变量和方法**。

    ```java
    class A {
        protected String name = "大彬";
    
        public void getName() {
            System.out.println("父类:" + name);
        }
    }
    
    public class B extends A {
        @Override
        public void getName() {
            System.out.println(super.name);
            super.getName();
        }
    
        public static void main(String[] args) {
            B b = new B();
            b.getName();
        }
        /**
         * 大彬
         * 父类:大彬
         */
    }
    ```

    在子类B中，我们重写了父类的getName() 方法，如果在重写getName() 方法中我们要调用父类的相同方法，必须要通过super关键字显式指出。

## 30、final、finally、finalize的区别

* final用来修饰属性、方法和类，分别表示**属性不能被重新赋值、方法不可被覆盖、类不可被继承**。
* finally是异常处理语句结构的一部分，通常以**try-catch-finally**出现，finally代码块总是会被执行。
* finalize是Object类中的方法，**该方法一般由垃圾回收器调用，当调用system.gc方法时，由垃圾回收器调用finalize()方法，回收垃圾**，JVM不能保证该方法总是被调用。

## 31、final关键字的作用

* final修饰的类不能被继承。
* final修饰的方法不能被重写。
* **final修饰的变量叫做常量，常量必须被初始化，并且初始化后不能修改。**

## 32、方法重载和重写的区别

**同一个类中有多个方法具有相同的方法名称，但其参数列表不同，称之为方法重载。**参数列表包含参数的签名、类型、顺序。只要有一个不同就为不同的参数列表。

```java
public class OverrideTest {
    void setPerson() { }
    
    void setPerson(String name) {
        //set name
    }
    
    void setPerson(String name, int age) {
        //set name and age
    }
}
```

**方法的重写是针对父类和子类之间的。当父类的方法不足以满足子类的需求时，可以在子类中对方法进行重写。** *在重写时，方法名和形参列表必须相同*。

```java
public class Person {
    private String name;
    
    public void dailyTask() {
        System.out.println("work eat sleep");
    }
}


public class Student extends Person {
    @Override
    public void dailyTask() {
        System.out.println("study eat sleep");
    }
}
```

## 33、接口和抽象类的区别

**语法层面：**

* 抽象类中既可以有抽象方法也可以有普通方法，而接口中只能有抽象方法（Java 8 之后接口方法可以有默认实现）。
* 抽象类中的成员变量可以是各种类型的，而**接口中的成员变量只能是public static final类型**的。
* 接口中不能包含静态代码块和静态方法（**java8后可以有静态方法**），而抽象类中可以有静态代码块和静态方法。
* 一个类只能继承一个抽象类，而一个类可以实现多个接口。

**设计层面：**

* 抽象层次不同。抽象类是对类的整体进行抽象，包括类的属性和行为，而接口只是对类的行为进行抽象，继承是一种是不是的关系，而接口则是有没有的关系，如果一个类继承了某个抽象类，则子类必定是抽象类的种类，而接口实现则是具备不具备的关系。
* 继承抽象类的是具有相似特点的类，而实现接口的可以是不同的类。

## 34、常见的Exception

**常见的RuntimeException：**

* ClassCastException：类型转换异常
* IndexOutOfBoundsException：数组越界异常
* NullPointerException：空指针异常
* ArrayStoreException：数组存储异常
* NumberFormatException数字格式化异常
* ArithmeticException：数学运算异常

**checked Exception：**

* NoSuchFieldException：反射异常，没有相应字段
* ClassNotFoundException：类没有找到异常
* IllegalAccessException：安全权限异常，可能是反射时调用了private方法

## 35、Error和Exception的区别

* Error：JVM中无法解决的严重问题，比如**栈溢出StackOverflowError、内存溢出OOM**等。程序无法处理的错误。
* Exception：因编程错误或其他外部因素造成的一般性问题。可以在代码中处理，比如**空指针异常、数组下标越界等**。

## 36、运行时异常（RuntimeException）和非运行时异常（checkedException）的区别

Java提供了两类主要的异常:**runtime exception和checked exception**。所有的checked exception是从java.lang.Exception类衍生出来的，而runtime exception则是从java.lang.RuntimeException或java.lang.Error类衍生出

unchecked exception 包括RuntimeException 和Error 类，其他所有异常称为检查（checked）异常。

* RuntimeException：由**程序错误导致**。应该修正程序，避免这类异常发生。
* checkd Exception：由**具体的环境（读取的文件不存在、文件为空、sql异常）导致的异常**。必须进行处理，不然编译不通过，可以使用catch或throws。

## 37、throw和throws的区别

* throw：**用于抛出一个具体的异常**。
* throws：常在方法签名中使用，**用于声明该方法可能抛出的异常**。子类方法抛出的异常范围更小，或者根本不抛出异常。

## 38、NIO（同步非阻塞IO）

**BIO（同步阻塞IO）：**每次来一个请求，就放到线程池中为其分配一个线程处理，如果超过线程池的最大上限，则放到队列中等待。

![image-20231222204844543](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20231222204844543.png)

**NIO基本思想总结起来就是：分而治之，将任务拆分开来，由专门的人负责专门的任务**

**典型的NIO有三类线程：mainReactor、subReactor和worker线程。**mainReactor线程负责监听server socket，接收新连接，并将建立的socket分配给subReactor。subReator可以是一个线程，也可以是一个线程池，负责多路分离已连接的socket，读写网络数据，对于具体的业务处理功能，将其交给worker线程池完成。

**NIO+异步的方式能够让少量的线程处理大量的事，适用于很多场景，比如代理服务、api服务和长连接服务等**。不过虽然NIO+异步能提高系统吞吐量，但其并不能让一个请求的等待时间下降，相反可能会增加等待时间。

## 39、BIO、NIO和AIO的区别

* **同步阻塞IO（BIO）：**用户进程发起一个IO操作后，必须等待IO操作真正完成后，才能继续运行。
* **同步非阻塞IO（NIO）：**客户端和服务器**通过channel连接**，采用**多路复用轮询注册的channel**。提高吞吐量和可靠性。用户发起一个IO操作后可以做其他事情，但是**用户进程需要轮询IO操作是否完成，这样会造成不必要的cpu资源浪费。**
* **异步非阻塞IO（AIO）：**非异步阻塞通讯模式，NIO的升级版，采用**异步通道实现异步通信**，其write和read均为异步方法。用户进程发起一个IO操作，然后立即返回，等IO操作真正完成后，应用程序会得到一个IO操作完成的通知。类似于多线程中的future模式。

>Future模式是多线程开发中非常常见的一种设计模式。它的核心思想是异步调用。当我们需要调用一个函数方法时。如果这个函数执行很慢,那么我们就要进行等待。但有时候,我们可能并不急着要结果。因此,我们可以让被调用者立即返回,让他在后台慢慢处理这个请求。对于调用者来说,则可以先处理一些其他任务,在真正需要数据的场合再去尝试获取需要的数据。

## 40、什么是守护线程

* **守护线程是运行在后台的一种特殊进程**
* 它独立于控制终端，并**周期性的执行某些任务或等待处理某些事件的发生**
* 在java中**垃圾回收机制就是一种特殊的守护线程**

## 41、Java是否支持多继承

**类不支持多继承，但接口支持多继承。**接口的作用是扩展对象功能，当一个子接口继承了多个父接口，说明子接口扩展了多个功能。当一个类实现该接口时，就扩展了多个功能。

java不支持多继承的原因：

* 出于**安全性考虑**，如果子类继承的多个父类中存在相同的方法或属性，则子类将不知道该继承哪个。
* java**提供了接口和内部类以达到实现多继承功能**，弥补了单继承的缺陷。

## 42、如何实现对象克隆

* 实现cloneable接口，重写clone()方法。这种方式是浅拷贝，即如果类中属性有自定义引用类型，不拷贝引用指向的对象。如果**对象属性的class也实现了cloneable接口，那么在克隆对象时也会克隆属性，即深拷贝**。
* 结合序列化进行深拷贝。实现序列化接口Serializable，通过对象的序列化和反序列化实现克隆，可以实现真正的深度克隆。
* 通过org.apache.commons中的工具类BeanUtils和PropertyUtils进行对象复制。

## 43、同步和异步的区别

* 同步：**发出一个调用时，没有得到结果之前，该调用不返回**。
* 异步：**发出一个调用之后，被调者返回结果之后会通知调用者，或通过回调函数处理这个调用**。

## 44、阻塞和非阻塞的区别

阻塞和非阻塞关注的是线程的状态。

* 阻塞调用是指在调用结果返回之前，当前进程会被挂起。调用线程只有在得到结果之后才会恢复运行。
* 非阻塞调用是指在得到调用结果之前，该调用不会阻塞当前进程。

## 45、Java8新特性

* **Lambda 表达式：**Lambda允许把函数作为一个方法的参数
* **Stream API ：**新添加的Stream API（java.util.stream） 把真正的**函数式编程风格**引入到Java中
* **默认方法：**默认方法就是一个在接口里面有了一个实现的方法。
* **Optional 类 ：**Optional 类已经成为 Java 8 类库的一部分，用来**解决空指针异常**。
* **Date Time API ：**加强对日期与时间的处理。

## 46、序列化和反序列化

* 序列化：把**对象转换成字节序列**的过程称为对象的序列化
* 反序列化：把**字节序列恢复成对象**的过程称为对象的反序列化。

**序列化最重要的作用：**在传递和保存对象时，**保证对象的完整性和可传递性**。对象转换为有序[字节流](https://so.csdn.net/so/search?q=字节流&spm=1001.2101.3001.7020),以便在网络上传输或者保存在本地文件中。

 **反序列化的最重要的作用：**根据字节流中保存的对象状态及描述信息，通过反序列化重建对象。

## 47、什么时候需要用到序列化和反序列化

当在本地JVM里运行Java实例时，是不需要序列化和反序列化的，但当我们需要**将内存中的对象持久化到磁盘、数据库中**时，当我们需要**与浏览器进行交互**、当我们**需要实现RPC（远程过程调用协议）**时，这时需要进行序列化和反序列化。

**只要我们对内存中的对象进行持久化或网络传输时，就需要序列化和反序列化。**

> RPC（Remote Procedure Call）远程过程调用协议，**一种通过网络从远程计算机上请求服务，而不需要了解底层网络技术的协议。**RPC它假定某些协议的存在，例如TPC/UDP等，为通信程序之间携带信息数据。在OSI网络七层模型中，RPC跨越了传输层和应用层，RPC使得开发，包括网络分布式多程序在内的应用程序更加容易。

## 48、实现序列化和反序列化为什么要实现Serializable接口

在Java中实现了Serializable接口后，JVM在类加载的时候就会发现我们实现了这个接口，然后在初始化实例对象的时候就会自动在底层帮我们实现序列化和反序列化。**如果被写对象类型不是String、数组、Enum，并且没有实现Serializable接口，那么在序列化时就会抛出NotSerializableExceptio异常。**

理由:

服务器与浏览器交互时真的没有用到 Serializable 接口吗? **JSON 格式实际上就是将一个对象转化为字符串**，所以服务器与浏览器交互时的数据格式其实是字符串，我们来看来 String 类型的源码:

```java
public final class String
    implements java.io.Serializable，Comparable<String>，CharSequence {
    /\*\* The value is used for character storage. \*/
    private final char value\[\];

    /\*\* Cache the hash code for the string \*/
    private int hash; // Default to 0

    /\*\* use serialVersionUID from JDK 1.0.2 for interoperability \*/
    private static final long serialVersionUID = -6849794470754667710L;

    ......
}
```

String 类型实现了 Serializable 接口，并显示指定 serialVersionUID 的值.

然后我们再来看对象持久化到数据库中时的情况，Mybatis 数据库映射文件里的 insert 代码:

```java
<insert id="insertUser" parameterType="org.tyshawn.bean.User">
    INSERT INTO t\_user(name，age) VALUES (#{name}，#{age})
</insert>
```

实际上我们并不是将整个对象持久化到数据库中，而是将对象中的属性持久化到数据库中，而这些属性（如Date/String）都实现了 Serializable 接口。

## 49、实现Serializable接口之后，为什么还要指定serialVersionUID的值

如果不指定一个serialVersionUID，**JVM在序列化时就会根据属性自动生成一个serialVersionUID，然后与属性一起序列化**，在进行持久化或网络传输。**在反序列化时，JVM会再根据属性自动生成一个serialVersionUID，然后将新的serialVersionUID和旧的serialVersionUID进行比较**，如果相同则但序列化成功，否则将会报错。

如果显示指定了一个serialVersionUID，则JVM会在序列化和反序列化时同样都会生成serialVerisonUID，但值显示为指定的值，此时在反序列化时两个serialVersionUID就会相同了。

如果我们的类写完后不再修改，那么不指定serialVersionUID，不会有问题，但这在实际开发中是不可能的，我们的类会不断迭代，一旦类被修改了，那旧对象反序列化就会报错。 所以在实际开发中，我们都会显示指定一个 serialVersionUID。

## 50、static属性为什么不能被序列化

**因为序列化是针对对象而言的，而static是优先于对象的，随着类的加载而加载，所以不会被序列化。**

serialVersionUID 也被 static 修饰，为什么 serialVersionUID 会被序列化? 其实 serialVersionUID 属性并没有被序列化，JVM 在序列化对象时会自动生成一个serialVersionUID，然后将我们显示指定的 serialVersionUID 属性值赋给自动生成的 serialVersionUID.

## 51、transient关键字的作用

Java的关键字，变量的修饰词，**如果用transient声明一个实例对象，当对象存储时，它的值不需要维持**。**也就是说被transient修饰的成员变量，在序列化时会被忽略，在被反序列化后，其值会被重置为初始值**。如int类型的变为0，对象型的是null。

## 52、什么是反射

**反射机制：** **动态获取的信息以及动态调用对象的方法**的功能。

* 通过java语言中的反射机制可以操作字节码文件（可以读和修改字节码文件。）
* 通过反射机制可以操作代码片段。（class文件。）

**反射就是把Java类中的各种成分映射成一个个的Java对象**。例如：一个类有：成员变量、方法、构造方法、包等等信息，利用反射技术可以对一个类进行解剖，把一个个组成部分映射成一个个对象。

在运行状态过程中，对于**任意一个类，能够知道这个类的所有属性和方法**。对于**任意一个对象，能够调用它的任意一个属性和方法**。

通过反射实例化对象：

```java
对象.newInstance()
```

## 53、反射的应用场景

* JDBC连接数据库时使用class.forName()通过反射加载数据库的驱动程序。
* Eclispe、IDEA等开发工具利用反射动态解析对象的类型与结构，动态提示对象的属性和方法。
* Web服务器中利用反射调用了Sevlet的service 方法。
* JDK动态代理底层依赖反射实现。
* spring组件中的拦截器基于java的反射机制实现。

## 54、泛型

**允许在定义类和接口时使用类型参数**。声明的类型参数在使用时用具体的类型替换。

允许定义类，接口时通过一个标识表示某个属性的类型或者是某个方法的返回值或者是参数类型，参数类型在具体使用的时候确定，在使用之前对类型进行检查。

**泛型的最大好处是可以提高代码的复用性**。以List接口为例，我们可以将String、 Integer等类型放⼊List中， 如不⽤泛型， 存放String类型要写⼀个List接口， 存放Integer要写另外⼀个List接口， 泛型可以很好的解决这个问题。

## 55、如何停止一个正在运行的线程

* **使用线程的stop方法。**

  **使用stop方法可以强制终止线程，但已被废弃。**使用Stop方法，会一直向上传播**ThreadDeath异常**，从而使得目标线程解锁所有锁住的监视器，即释放掉所有的对象锁。**使得之前被锁住的对象得不到同步的处理**，因此可能会造成数据不一致的问题。

* **使用interrupt方法中断线程。**

  该方法只是告诉线程要中止，但何时中止取决于计算机。调用interrupt方法只是在当前线程中加了一个停止的标记，并不是真的停止线程。

  接着可以调用Thread.currentThread().isInterrupted()方法，可以判断当前线程是否被终止，通过这个判断我们可以做一些业务逻辑处理，通常如果isInterrupted返回true的话，会抛一个中断异常，然后通过try-catch捕获。

* **设置标志位。**

  设置标志位，当标识值为某个特定值时，使线程正常退出。**设置标志位用到了共享线程的方式，当线程发生阻塞时是无法完成响应的**。比如调用Thread.sleep()方法之后，线程处于不可运行状态，即便是主线程修改了共享变量的值，该线程此时根本无法检查循环标志，所以也就无法实现线程中断。

因此，**interrupt() 加上手动抛异常的方式是目前中断一个正在运行的线程最为正确的方式了。**

## 56、跨域

**跨域就是从一个域名的网页去请求另一个域名的资源**。由于有**同源策略**的限制，一般是不允许这么访问的，但是很多场景会有跨域访问的需求，比如在前后端分离的模式下，前后端的域名是不一样的，此时就会出现跨域问题。

* **同源策略**

  同源指的是”协议+域名+端口“三者相同。即便两个不同的域名指向同一个IP地址，也是非同源。

  同源策略限制以下几种行为：

  * Cookie、LocalStorage和IndexDB无法读取。
  * DOM和JS对象无法获取。
  * AJAX请求不能发送。

* **为什么要有同源策略**

  举个例子，假如你刚刚在网银输入账号密码，查看了自己的余额，然后再去访问其他不安全的网站，这个网站可以访问刚刚的网银站点，并且获取账号密码，那后果可想而知。因此，**从安全的角度来讲，同源策略是有利于保护网站信息的。**

## 57、怎么解决跨域问题

* **CORS：跨域资源共享**

  CORS（Cross-origin resource sharing），跨域资源共享。浏览器会自动进行CORS通信，它的实现主要在服务端，**通过一些HTTP Header来限制可以访问的域**。例如页面A要向服务器B访问数据，如果B服务器上声明了允许A的域名访问，那么从A到B的跨域请求就可以完成。

  想要传递`cookie`需要满足 3 个条件：

  * web请求设置`withCredentials`：这里默认情况下在跨域请求，浏览器是不带 cookie 的。但是我们可以通过设置`withCredentials`来进行传递`cookie`.
  * `Access-Control-Allow-Credentials`为`true`
  * `Access-Control-Allow-Origin`为非`*`

* **CrossOrigin注解**

  如果项目使用的是SpringBoot，可以**在Controller类上添加一个@CrossOrigin注解就可以实现对当前controller的跨域访问**，该注解也可以直接加到方法上，**或者加到入口类上对所有的接口进行跨域处理**。

* **nginx反向代理接口跨域**

  nginx反向代理跨域原理：同源策略是浏览器的安全策略，不是HTTP协议的一部分。**服务器端调用HTTP接口只是使用HTTP协议，不会执行JS脚本，不需要同源策略，也就不存在跨域问题**。

  nginx反向代理接口跨域实现思路：通过nginx实现一个代理服务器（域名和domain1相同，端口不同）做跳板机，反向代理domain2接口，并且可以顺便修改cookie中的domain信息，方便当前域cookie写入，实现跨域登录。

  ```xml
  // proxy服务器
  server {
      listen       81;
      server_name  www.domain1.com;
      location / {
          proxy_pass   http://www.domain2.com:8080;  #反向代理
          proxy_cookie_domain www.domain2.com www.domain1.com; #修改cookie里域名
          index  index.html index.htm;
          
          add_header Access-Control-Allow-Origin http://www.domain1.com;
      }
  }
  ```

  这样我们的前端代理只要访问 http:www.domain1.com:81/*就可以了。

* **通过jsonp跨域**

  通常为了减轻web服务器的负载，我们把js、css、img等静态资源分离到一台独立域名的服务器上，在html页面中再通过相应的标签从不同域名下加载静态资源，这是浏览器允许的操作，**基于此原理，我们可以动态创建script，再请求一个带参网址实现跨域。**

## 58、接口设计

* **接口参数校验。**接口必须校验参数。比如入参是否为空，入参长度是否符合预期。
* 设计接口时充分考虑**接口的可扩展性**。接口是否可复用，怎么保持接口的可扩展性。
* **串行调用考虑改并行调用。**比如设计一个商城首页接口，需要查商品信息、营销信息、用户信息等等。如果是串行一个一个查，那耗时就比较大了。这种场景是可以改为并行调用的，降低接口耗时。
* **接口是否需要防重处理。**涉及到数据库修改的需要考虑防重处理，可以使用数据库防重表，以唯一的流水号作为唯一索引。
* **日志打印全面。**入参出参，接口耗时。
* 修改旧接口时需要考虑**接口的兼容性。**
* **异常处理得当。**使用finally关闭流资源，使用log打印而不是e.printStackTrace()、不要吞异常等等。
* **是否需要考虑限流。**限流是为了保护系统，防止流量洪峰超过系统的承受能力。

## 59、过滤器和拦截器的区别

* **实现原理不同。**过滤器是基于回调函数实现，拦截器是基于Java的**反射机制**实现。一般定义的过滤器都会有一个doFilter()函数，并包含一个FilterChain参数，这个参数实际上起到的是一个回调函数的作用。
* **使用范围不同。**过滤器实现的是 javax.servlet.Filter 接口，而这个接口是在Servlet规范中定义的，也就是说**过滤器Filter的使用要依赖于Tomcat等容器**，导致它只能在web程序中使用。而拦截器是一个Spring组件，并由Spring容器管理，并不依赖Tomcat等容器，是可以单独使用的。拦截器不仅能应用在web程序中，也可以用于Application、Swing等程序中。
* **使用的场景不同。**因为拦截器更接近业务系统，所以拦截器主要用来实现项目中的业务判断的，比如：日志记录、权限判断等业务。而过滤器通常是用来实现通用功能过滤的，比如：敏感词过滤、响应数据压缩等功能。
* **触发的时机不同。**
  * 过滤器Filter是在请求进入容器后，但在进入servlet之前进行预处理，请求结束是在servlet处理完以后。
  * 拦截器 Interceptor 是在请求进入servlet后，在进入Controller之前进行预处理的，Controller 中渲染了对应的视图之后请求结束。
* **拦截的请求范围不同。**请求的执行顺序是：**请求进入容器 -> 进入过滤器 -> 进入 Servlet -> 进入拦截器 -> 执行控制器**。可以看到过滤器和拦截器的执行时机也是不同的，**过滤器会先执行，然后才会执行拦截器**，最后才会进入真正的要调用的方法。

## 60、对接接口时要注意什么

* **确定接口对接的网络协议**，https/http或自己定义的私有协议。
* **约定好数据传参、响应的格式**（如application/json），弱类型对接强语言类型时要特别注意。
* **接口安全**方面。确定身份校验方式，token校验或证书校验。
* **确认是否需要接口调用失败后的重试机制**，保证数据传输的最终一致性。
* **日志记录要全面**。接口出入参数，以及解析之后的参数值，都要用日志记录，方便定位问题。

## 61、后端接口性能优化的方法

* **优化索引。**给where条件后面的关键字段，或order by后面的排序字段，添加索引。
* **优化sql语句。**避免使用select * 、批量操作、避免深分页、提升group by的效率。
* **避免大事务。**使用@Transaction注解这种声明式事务的方式提供事务功能，容易造成大事务，引发其他问题。应该**避免在事务中一次性处理太多数据**，将一些跟事务无关的数据放在事务外面执行。
* **异步处理。**剥离主逻辑和副逻辑，**副逻辑可以异步执行，异步写库**。比如用户购买的商品发货需要短信通知，短信通知是副流程，可以异步执行，避免影响主逻辑的执行。
* **降低锁粒度。**在并发场景下，多个线程修改数据可能会造成数据不一致的情况，此时需要加锁解决。如果锁加的不好，粒度过粗，也会影响接口的性能。
* **加缓存。**如果数据量非常大，直接从数据库中查询数据，性能会非常差，可以使用Redis提升查询性能，从而提升接口性能。
* **分库分表。**当系统发展到一定阶段，用户的并发量会非常大，会有大量的数据库请求，需要占用大量数据库连接，同时会带**磁盘IO性能瓶颈问题**。或者数据库表数据非常大，即使sql查询使用索引也会非常耗时。此时可以通过分库分表解决。**分库用于解决数据库资源连接不足问题和磁盘IO性能瓶颈问题。分表是为了解决单表数据量过大，sql查询耗时问题。**
* **避免在循环中查询数据库。**循环查询数据库是一件非常耗时的事情，尽量在一次查询中获取所有的数据。

# 二、集合

## 1、常见的集合

Java集合类主要有两个接口Collection和Map派生出的。Collection有三个接口：List、Queue、Set。

![img](http://img.topjavaer.cn/img/collections.drawio.png)

![img](http://img.topjavaer.cn/img/map.png)

**List代表了有序可重复集合，可直接根据元素的索引来访问**；**Set代表无序不可重复集合，只能根据元素本身来访问**；**Queue是队列集合**。**Map代表的是存储key-value对的集合，可根据元素的key来访问value**。

> LinkedList同时实现了List接口和Dqeue接口

集合体系中常用的实现类有ArrayList、LinkedList、HashSet、TreeSet、HashMap、TreeMap 等实现类。

## 2、List、Map、Set的区别

* List 以索引来存取元素，有序的，元素是允许重复的，可以插入多个null；
* Set 不能存放重复元素，无序的，只允许一个null；
* Map 保存键值对映射；
* List的底层实现有**数组和链表**两种方式，Set和Map有基于**哈希存储和红黑树**两种方式。
* Set基于Map实现，**Set里的值就是Map的键值**。

## 3、ArrayList

ArrayList的底层是动态数组，它的**容量可以动态增长**。在添加大量元素之前可以使用**ensureCapacity**操作增加ArrayList的实际容量。ArrayLIst继承了AbstractList，并继承了LIst接口。

## 4、ArrayList的扩容机制

ArrayList的扩容机制本质上就是**计算实际的容量然后进行实例化**，并将原本的数组复制到新的数组中。默认情况下**新的容量会是原容量的1.5倍**。

```java
public boolean add(E e) {
    //判断是否可以容纳e，若能，则直接添加在末尾；若不能，则进行扩容，然后再把e添加在末尾
    ensureCapacityInternal(size + 1);  // Increments modCount!!
    //将e添加到数组末尾
    elementData[size++] = e;
    return true;
    }

// 每次在add()一个元素时，arraylist都需要对这个list的容量进行一个判断。通过ensureCapacityInternal()方法确保当前ArrayList维护的数组具有存储新元素的能力，经过处理之后将元素存储在数组elementData的尾部

private void ensureCapacityInternal(int minCapacity) {
      ensureExplicitCapacity(calculateCapacity(elementData, minCapacity));
}

private static int calculateCapacity(Object[] elementData, int minCapacity) {
        //如果传入的是个空数组则最小容量取默认容量与minCapacity之间的最大值
        if (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {
            return Math.max(DEFAULT_CAPACITY, minCapacity);
        }
        return minCapacity;
    }
    
  private void ensureExplicitCapacity(int minCapacity) {
        modCount++;
        // 若ArrayList已有的存储能力满足最低存储要求，则返回add直接添加元素；如果最低要求的存储能力>ArrayList已有的存储能力，这就表示ArrayList的存储能力不足，因此需要调用 grow();方法进行扩容
        if (minCapacity - elementData.length > 0)
            grow(minCapacity);
    }


private void grow(int minCapacity) {
        // 获取elementData数组的内存空间长度
        int oldCapacity = elementData.length;
        // 扩容至原来的1.5倍
        int newCapacity = oldCapacity + (oldCapacity >> 1);
        //校验容量是否够
        if (newCapacity - minCapacity < 0)
            newCapacity = minCapacity;
        //若预设值大于默认的最大值，检查是否溢出
        if (newCapacity - MAX_ARRAY_SIZE > 0)
            newCapacity = hugeCapacity(minCapacity);
        // 调用Arrays.copyOf方法将elementData数组指向新的内存空间
         //并将elementData的数据复制到新的内存空间
        elementData = Arrays.copyOf(elementData, newCapacity);
    }
```

## 5、怎么在遍历ArrayList时移除一个元素

foreach删除会导致快速失败问题，可以使用迭代器的 remove() 方法。

```java
Iterator itr = list.iterator();
while(itr.hasNext()) {
      if(itr.next().equals("jay") {
        itr.remove();
      }
}
```

## 6、ArrayList和Vector的区别

* **ArrayList**在容量不够时会扩容至原来的**1.5倍**。**Vector**会扩容至原来的**2倍**。
* **Vector是线程安全级的**，但大多数情况下不使用Vector，因为**Vector的操作效率比较低**。

## 7、ArrayList和LinkedLIst的区别

* ArrayList是基于动态数组实现的，LikedList是基于链表实现的。
* 对于**随机index访问的get和set方法，ArrayList的效率要比LinkedLIst高**，因为ArrayList可以直接根据下标进行访问，而LinkedList需要移动指针遍历每个元素才能找到。
* 新增和删除数组。**LInkedList新增和删除的效率要比ArrayList高**，ArrayList需要考虑是否扩容和复制数组，而LinkedList实例化对象需要时间外，只需要修改指针即可。

## 8、HashMap

**HashMap使用数组+链表+红黑树实现**。链表长度大于`8`时，会把链表转换为红黑树。红黑树的节点小于`6`时，才会把红黑树转换为链表，防止频繁的转化。

### 8.1 解决hash冲突的方法有哪些，HashMap用的哪种方法

**解决方法：开放定址法、再哈希法、链地址法。HashMap采用的是链地址法。**

* 开放定址法：如果`p = Hash(key1)`发生冲突时，就以`p`为基础再次进行hash，`p1 = Hash(p)`，`p1`发生冲突再以`p1`为基础进行hash，以此类推，直至找到一个不冲突的hash地址。因此**开放定址法所需要的hash表的长度大于所需要存放的元素的数量**。因为存在再次hash，所以只能在删除节点时做标记，不能真正删除节点。
* 再哈希法：使用多个hash函数计算hash值，当`p = hash1(key)`冲突时，计算`p = hash2(key)`，直到没有冲突为止。这样做虽然不会产生堆集，但会**增加计算时间**。
* 链地址法：**将哈希值相同的元素构成一个单链表**，并将单链表的头指针存放在hash表的第`i`个单元中。查找、删除、插入在同义词链表中进行。**链地址法适合用于经常插入和删除的情况**。

### 8.2、使用的Hash算法

Hash算法：取key的hashCode值、高位运算、取模运算。

```java
h=key.hashCode() //第一步 取hashCode值
h^(h>>>16)  //第二步 高位参与运算，减少冲突
return h&(length-1);  //第三步 取模运算
```

在JDK1.8的实现中，优化了高位运算的算法，**通过hashCode() 的高16位异或低16位实现的**：这么做可以在数组比较小的时候，也能保证考虑到高低位都参与到Hash的计算中，**可以减少冲突，同时不会有太大的开销**。

### 8.3、为什么建议设置HashMap的容量

HashMap有扩容机制，当达到扩容条件的时候就会扩容。**扩容条件就是当HashMap的元素个数超过临界值的时候就会自动扩容**（（threshold = loadFactor * capacity））（threshold代表扩容阈值）。

如果我们没有初始HashMap的容量大小，随着元素的增加，HashMap会发生多次扩容。而**HashMap每次扩容都会重建hash表，非常影响性能**。所以建议在创建HashMap的时候**指定初始化容量**。

### 8.4、扩容过程

* **java1.7扩容机制：**新节点采用的头插法，因此在线程进行扩容迁移元素时，会**改变元素顺序，导致两个线程中出现的元素的相互指向而形成循环链表**， 1.8采用了尾插法，避免了这种情况。

* **java1.8扩容机制：**当元素个数大于threshold时，会进行扩容，使用**2倍容量**的数组替代原有数组。采用**尾插法**将原数组的元素拷贝到新数组中。**1.8扩容之后元素的相对位置不会发生改变**，1.7扩容之后元素的位置会发生倒置。

原数组的元素在计算hash之后，因为数组的容量n变为2倍，**那么n-1的mask范围在高位就会多1bit**。在元素拷贝的过程中不需要重新计算元素在数组中的位置只需要检查原来的hash值新增的那个bit是1还是0，**是0的话索引没变，是1的话索引变成“原索引+oldCap”**（根据`e.hash & oldCap == 0`判断，用位运算代替取余运算）。这样可以省去重新计算hash值的时间，而且由于新增的1bit是0还是1可以认为是随机的，因此resize的过程中会均匀的把之前冲突的节点分散到新的bucket。

### 8.5、put方法的流程

* 如果table没有初始化就进行初始化过程。
* 使用hash算法计算key的索引。
* 判断索引处有没有存在元素，如果没有则直接插入。
* 如果索引处存在元素，则遍历插入。
  * 如果是链表形式就直接遍历到尾端插入。
  * 如果是红黑树就按照红黑树结构插入。
* 链表的数量大于阈值8，就要转换成红黑树的结构。
* **添加成功后会检查是否需要扩容。**

<img src="C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240313135632192.png" alt="image-20240313135632192" style="zoom:80%;" />

### 8.6、红黑树的特点

* 每个节点或者是红色，或者是黑色。
* 根节点和叶子节点（包括NULL）都是黑色。
* 如果一个节点是红色，那么它的子节点一定是黑色。
* **从一个节点到该节点的所有子孙节点的路上包含相同数量的黑色节点。**

### 8.7、在解决Hash冲突时，为什么先选择使用链表再考虑红黑树

红黑树需要进行左旋、右旋、变色这些操作来保持树的平衡，而单链表不需要。因此，当元素个数小于8时，采用单链表能够**保证查询效率**。而当元素个数大于8且数组容量大于64时，会采用红黑树结构。因为**红黑树搜索的时间复杂度是`O(logn)`，而单链表的搜索时间复杂度是`O(n)`**，因此当n比较大时，使用红黑树能够提升查询效率。

### 8.8、HashMap的长度为什么是2的幂次方

Hash值的范围值比较大，使用之前需要对数组的长度进行取模运算，得到的余数才是元素存放的位置也就是对应的数组下标。这个下标的计算方式是`(n - 1) & hash`。将**HashMap的长度定为2的幂次方，这样就可以使用`(n - 1) & hash`位运算代替`%`运算，提高性能**。（**使用位运算代替取余运算**）

### 8.9、HashMap的默认加载因子是多少，为什么是这个取值

HashMap的构造函数中的参数

```java
int threshold; // 容纳键值对的最大值
final float loadFactor; // 负载因子
int modCount;
int size;
```

HashMap的构造函数中存在一个负载因子loadFactor参数，Node[] table的初始化长度length为16，默认的loadFactor是0.75，**0.75是对空间和时间效率的一个平衡选择**，根据泊松分布，loadFactor 取0.75碰撞最小。一般不会修改，除非在时间和空间比较特殊的情况下 ：

* 如果内存空间很多而又对时间效率要求很高，可以降低负载因子Load factor的值 。
* 如果内存空间紧张而对时间效率要求不高，可以增加负载因子loadFactor的值，这个值可以大于1。

### 8.10、一般用什么作为HashMap的Key值

**一般使用Integer或String这种不可变类型当HashMap的Key**，String类比较常用。

* String是不可变的，所以**在它创建的时候`hashCode`就被缓存了，不需要重新计算**。
* 获取**对象的时候要用到equals()和hashCode()这两个方法**，而*Integer和String这些类都已经重写了equals()和hashCode()，因此不需要手动重写这些方法*。

### 8.11、HashMap为什么线程不安全

* **多线程下扩容死循环**，jdk1.7中的HashMap使用的是头插法插入元素，**在多线程的环境下，扩容的时候有可能会导致环形链表的出现，形成死循环**。
* 在jdk1.8中，多线程的环境下，会发生**数据覆盖**的情况。

### 8.12、HashMap和HashTable的区别

HashMap和HashTable都实现了Map接口。

* **HashMap中允许为null的key和value**，key为null的键值对放在下标为0的头结点的链表中，而HashTable则不行。
* **HashMap是非线程安全的**，而HashTable是线程安全的。在jdk1.5中提供了ConcurrentHashMap作为HashTable的替代品。
* **HashTable有很多方法是同步的，在单线程环境下它比HashMap要慢。**
* Hash值的使用不同，**HashTable直接使用对象的HashCode**，而HashMap需要重新计算Hash值。

## 9、LinkedHashMap的底层原理

HashMap是无序的，迭代HashMap所得到的元素的顺序并不是最初放到HashMap的顺序，即不能保证它们的插入顺序。

LinkedListHashMap继承于HashMap，是HashMap和LinkedList的结合，具备两者的特性。每次**put操作都会将entry插入双向链表的尾部**。

## 10、TreeMap

TreeMap是一个能够**比较元素大小**的Map集合，会对传入的key进行大小排序。可以使用元素的自然顺序，也可以使用集合中自定义的比较器来进行排序。

![img](http://img.topjavaer.cn/img/image-20210905215046510.png)

**TreeMap的特点：**

* TreeMap是**有序的key-value集合，通过红黑树实现**。根据键的自然顺序进行排序或根据提供的Comparator进行排序。
* TreeMap继承了AbstractMap，实现了NavigableMap接口，支持一系列导航方法，**给定具体搜索目标，可以返回最接近的匹配项**。如floorEntry()、ceilingEntry()分别返回小于等于、大于等于给定键关联的Map.Entry()对象，不存在则返回null。lowerKey()、floorKey、ceilingKey、higherKey()只返回关联的key。

## 11、HashSet的底层原理

HashSet基于HashMap实现。放入**HashSet中的元素实际上是由HashMap的key来保存**，而HashMap的**value则存储了静态的Object对象**。

```java
public class HashSet<E>
    extends AbstractSet<E>
    implements Set<E>, Cloneable, java.io.Serializable {
    static final long serialVersionUID = -5024744406713321676L;

    private transient HashMap<E,Object> map; //基于HashMap实现
    //...
}
```

## 12、HashSet、LinkedHashSet和TreeSet的区别

* **HashSet是接口Set的实现类，底层是HashMap**，是线程不安全的，可以存储Null值。
* **LinkedHashSet是HashSet的子类**，能够按照添加元素的顺序进行遍历。
* **TreeSet底层是红黑树**，能够根据添加元素的顺序进行遍历，排序的方式可以自定义。

## 13、什么是fail fast

**fail fast是Java集合的一种错误机制，当存在多个线程对同一个集合进行操作时，就有可能产生fail fast事件**。例如：当线程a正在通过iterator遍历集合时，另一个线程b修改了集合的内容，此时modCount（记录集合操作过程的修改次数）就会加1，从而不等于exceptedModCount，那么线程a访问集合时就会抛出ConcurrentModificationException，产生fail fast事件。**边遍历边修改集合也会产生fail fast事件。**

**解决方法：**

* 使用**CollectionSynchronizedList**方法或在修改集合内容的地方加上**synchronized**。但这样增加了集合内容的**同步锁会阻塞遍历操作**，影响性能。
* **使用CopyOnWriteArrayList来替换ArrayList**。在对CopyOnWriteArrayList进行修改操作时，会拷贝一个新的数组，对新的数组进行操作，操作完成后再把**引用移到新的数组**。

## 14、什么是fail safe

采用**安全失败机制**的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有的集合内容，然后在拷贝的集合上进行遍历。java.util.concurrent包下的容器都是安全失败的，**可以在多线程下并发使用、并发修改**。

* **原理：**由于迭代时是对原集合的拷贝进行遍历，所以**在遍历过程中对原集合所作的修改并不能被迭代器检测到**，所以不会触发ConcurrentModificationException。
* **缺点：**基于拷贝内容的优点是避免了ConcurrentModificationException，但同样地，**迭代器并不能访问到修改后的内容**，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。

## 15、什么是ArrayDeque

**ArrayDeque实现了双端队列，底层基于循环数组实现**，默认大小为16。

* 在两端插入、删除元素的效率较高。
* 根据元素内容查找、删除的效率较低。
* 没有索引位置的概念，不能根据索引位置进行操作。

ArrayDeque和LinkedList都实现了Deque接口，如果只需要从两端进行操作，ArrayDeque效率更高一些。如果同时需要根据索引位置进行操作，或者经常需要在中间进行插入和删除（LinkedList有相应的api，如add(int index, E e)），则应该选LinkedList。

**ArrayDeque和LinkedList都是线程不安全的**，可以使用Collection类中的sychronizedXXX方法转换成线程同步。

## 16、哪些集合是线程安全的，哪些是不安全的

* 线程安全的集合：
  * Vector，比ArrayList多了同步机制。
  * HashTable
  * ConcurrentHashMap：一种高效且线程安全的集合。
  * Stack：栈也是线程安全的，基于Vector。
* **线程不安全的集合**：
  * HashMap
  * ArrayDeque
  * ArrayList
  * LinkedList
  * HashSet
  * TreeSet
  * TreeMap

## 17、迭代器Iterator是什么

**Iterator模式使用同一种逻辑来遍历集合元素。它可以把访问逻辑从不同类型的集合类中抽象出来，不需要知道集合类的内部实现便可以遍历集合元素，统一使用Iterator提供的接口遍历元素。**特点是安全，因为它可以保证集合元素在被修改时就抛出ConcurrentModificationException异常。

```java
public interface Collection<E> extends Iterable<E> {
    Iterator<E> iterator();
}
```

主要有三个方法：**hasNext()、next()和remove()**。

例如，在遍历删除list中的元素时，使用迭代器的remove方法进行删除：

```java
List<String> list = new ArrayList<>();
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String item = iterator.next();
    if (item.startsWith("1")) {
        iterator.remove();
    }
}
```

**这种方法可以保证在删除元素的同时不会破坏迭代器的状态。**

或者，从Java 8开始，ArrayList引入了removeIf方法，这是删除元素的另一种便捷方式：

```java
list.removeIf(item -> item.startsWith("1"));
```

## 18、Iterator和ListIterator的区别

ListIterator是Iterator的增强版。

* ListIterator遍历**可以是逆向的**，因为有previous和hasPrevious方法，而Iterator不能。
* ListIterator**可以定位当前的索引位置**，因为有nextIndex和previousIndex方法，而Iterator不能。
* LIstIterator**有add方法，可以向List添加对象**，而Iterator不能。
* LIstIterator**可以通过set方法实现对象的修改**，而Iterator不能。
* ListIterator**只能对List及其子类进行遍历**，而Iterator可以对任意集合遍历。

## 19、如何能够让一个集合不能被修改

**可以通过Collections包下的unmodifiableMap/unmodifiableList/unmodifiableSet方法**，通过这些方法返回的集合是不能被修改的。如果被修改，将会抛出java.lang.UnsupportedOperationException异常。

```java
List<String> list = new ArrayList<>();
list.add("x");
Collection<String> clist = Collections.unmodifiableCollection(list);
clist.add("y"); // 运行时此行报错
System.out.println(list. size());
```

对于List/Set/Map集合，Collections包都有相应的支持。

需要注意的是，**不能使用final关键子修饰**。**final关键字如果修饰的成员变量是引用类型的话，则表示这个引用的地址值是不能被修改的，但是该引用所指向的对象的内容还是可以修改的**。而集合类都是引用类型，如果使用final修饰，则集合里面的内容还是可以被修改的。

## 20、并发容器（JUC）

JDK提供的这些容器大部分都在java.long.concurrent包中。

* **ConcurrentHashMap**：线程安全的HashMap。
* **CopyOnWriteArrayList**：线程安全的List，在读多写少的场景下性能非常好，远远好于vector。
* **ConcurrentLinkedQueue**：高效的并发队列，基于链表实现。可以看作一个LinkedList，这是一个非阻塞队列。
* **BlockingQueue**：阻塞队列接口，JDK内部通过链表、数组实现了这个接口。非常**适用于数据共享的通道**。
* **ConcurrentSkipListMap**：跳表的实现。使用跳表的数据结构进行快速查找。

### 20.1、ConcurrentHashMap

**多线程环境**下，使用HashMap进行put操作会造成死循环，应该**使用支持多线程的ConcurrentHashMap**。

JDK1.8中的ConcurrentHashMap取消了segment分段锁，而**采用CAS和synchrionized来保证并发安全**。数据结构采用数组 + 链表/红黑树。**synchronized只锁定链表或红黑树的首节点**，相比于JDK1.7锁定HashEntry数组，**锁的粒度更小，支持更高的并发量**。当链表的长度过长时，Node会变成TreeNode，提高查找效率。

#### 20.1.1 put的执行流程

ConcurrentHashMap在JDK8中进行了巨大改动**它摒弃了Segment（锁段）的概念**，而是启用了一种全新的方式实现,利用CAS和synchrionized来保证并发安全。它沿用了与它同时期的HashMap版本的思想，底层依然由“数组”+链表+红黑树的方式思想，但是为了做到并发，又增加了很多辅助的类，例如TreeBin，Traverser等对象内部类。

```java
transient volatile Node<K,V>[] table;

static class Node<K,V> implements Map.Entry<K,V> {
    volatile V val;
    volatile Node<K,V> next;
}
```

put的流程：

* **计算哈希值：**首先，根据键的哈希值来确定这个键值对应该存储在数组的哪个槽位。

* **检查数组是否初始化**：如果数组还没有初始化，那么就进行初始化。

* **检查槽位是否为空**：如果计算出的槽位为空，那么就直接在这个槽位上创建一个新的Node。

* **检查槽位是否为`ForwardingNode`**：`ForwardingNode`是一个特殊的节点，表示当前的`ConcurrentHashMap`正在进行扩容操作。如果槽位是`ForwardingNode`，那么就帮助完成扩容操作。

* **锁定槽位**：如果槽位不为空，那么就尝试使用CAS（乐观锁）操作锁定这个槽位。

  >CAS操作的就是乐观锁，每次不加锁而是假设没有冲突而去完成某项操作，如果因为冲突失败就重试，直到成功为止。

* **检查键是否已存在**：如果槽位已被锁定，那么就在链表或红黑树中查找是否有相同的键。如果有，就更新这个键的值。

* **添加新的Node**：如果链表或红黑树中没有相同的键，那么就在链表或红黑树中添加一个新的Node。

* **检查是否需要扩容**：如果链表的长度超过一定的阈值（默认为8），那么就进行扩容操作。

> 以上就是Java 8中`ConcurrentHashMap`的`put`方法的执行逻辑。需要注意的是，`ConcurrentHashMap`的设计目标是支持高并发操作，所以在`put`方法的实现中，**大量使用了无锁技术（如CAS操作）和细粒度锁（如锁定槽位而不是整个数组）**。

#### 20.1.2、怎么扩容

数组扩容**transfer方法会设置一个步长**，表示一个线程处理的数组长度，最小值为16。在一个步长范围内只有一个线程会对其进行复制移动操作。

#### 20.1.3、ConcurrentHashMap和Hashtable的区别

* Hashtable是通过**使用synchronized修饰方法的方式来实现多线程同步**，因此，Hashtable的同步会锁住整个数组。在高并发的情况下，性能会非常差。**ConcurrentHashMap会使用更细粒度的锁提高在并发时的效率**。synchronized容器（并发容器）也是通过synchronized关键字来实现线程安全，在使用时会对所有的数据加锁。
* **Hashtable的默认大小为11**，在达到阈值后，每次按照以下公式进行扩容：**newCapacity = oldCapacity * 2 + 1**。**ConcurrentHashMap的默认大小为16**，在扩容时**容量变为之前容量的两倍**。

### 20.2、CopyOnWrite

copy-on-write，写时复制。**当往容器中添加元素时，不直接往容器添加，而是先对当前容器进行复制，得到一个新容器，然后往新容器中添加元素**。添加完元素后，再将原容器的引用指向新容器。这样做的好处在于：**可以对CopyOnWrite容器进行并发的读而不需要加锁**，因为**当前容器不会被修改。**

```java
    public boolean add(E e) {
        final ReentrantLock lock = this.lock;
        lock.lock(); //add方法需要加锁
        try {
            Object[] elements = getArray();
            int len = elements.length;
            Object[] newElements = Arrays.copyOf(elements, len + 1); //复制新数组
            newElements[len] = e;
            setArray(newElements); //原容器的引用指向新容器
            return true;
        } finally {
            lock.unlock();
        }
    }
```

**缺点**：

* **内存占用问题**。CopyOnWrite的写时复制机制会使得在进行**写操作时**，**内存中会驻扎两个对象的内存。**
* CopyOnWrite操作**不能保证数据的实时一致性**，可能会读取到旧数据。

### 20.3、CopyOnWriteArrayList

CopyOnWriteArrayList是Java并发包提供的一个并发容器，**相当于线程安全的ArrayList**。CopyOnWriteArrayList具有写时复制的机制，即当有新元素add到CopyOnWriteArrayList时，先从原有的数组中拷贝一份出来，然后在新的数组做写操作，写完之后，再将原来的数组引用指向到新数组。

**CopyOnWriteArrayList在进行写操作时是需要进行加锁的**，保证同步，**避免有多个线程写的时候复制多个副本**。读的时候不需要加锁，如果读的时候有新的线程向CopyOnWriteArrayList添加元素，此时还是可以读到旧数据的。

**CopyOnWrite并发容器用于读多写少的并发场景。**

**优点：**

* **读写性能很高，因为不需要任何同步操作，比较适用于读多写少的并发场景**。Java的list在遍历时，如果中途有其他线程对list容器进行修改，则会抛出ConcurrentModificationException异常。而**CopyOnWriteArrayList由于其读写分离的性质，读和写操作是作用在不同的list容器上**的，所以在使用迭代器进行遍历时不会抛出ConcurrentModificationException异常。

**缺点：**

* **内存占用问题**。每次执行写操作时都会将原容器拷贝一份，数据量大时，对内存压力较大，可能会引起频繁GC。
* **无法保证数据的实时一致性**。Vector的读写操作均加锁同步，可以保证数据的强一致性。而CopyOnWriteArrayList由于其机制的特殊性，**读写操作是作用在两个新老容器**。在执行读写操作时，*读操作不会阻塞但读取到的时老容器的内容*。

### 20.4、ConcurrentLinkedQueue

**非阻塞队列，高效的并发队列，使用链表实现**。可以看作一个*<u>线程安全的LinkedList</u>*，通过CAS实现。

如果对队列使用**加锁的成本较高**，则适合使用<u>无锁的ConcurrentLinkedQueue</u>来替代。适合**对性能要求相对较高**，同时**有多个线程对队列进行读写操作**时的场景。

非阻塞队列的几种主要方法：

* add(E e)：将元素e插入队列末尾，如果插入成功则返回true，如果插入失败（即队列已满），则会抛出异常。
* remove()：将队首元素移出队列，如果移除成功则返回true，否则（队列为空）会抛出异常。
* offer(E e)：将元素e插入队列末尾，如果插入成功则返回true，插入失败（队列已满）返回false。
* poll()：移除并获取队首元素，获取成功则返回对应元素，否则返回会null。
* peek()：获取队首元素，若成功返回队首元素，否则返回null。

### 20.5、BlockingQueue

阻塞队列是java.util.concurrent包下的数据结构，BlockingQueue提供了线程安全的队列访问方式：**当阻塞队列进行插入数据时，如果队列已满，线程将会阻塞等待直到线程非满**；**从阻塞队列中读取数据时，如果队列为空，线程将会阻塞等待直到线程非空**。并发包下的许多高级同步类的实现都是基于BlockingQueue实现的。<u>*BlockingQueue适合作为数据共享的通道*</u>。

使用阻塞算法的队列可以用一个锁（出对和入队共用一个锁）或者两个锁（出队和入队使用不同的锁）等方法来实现。

**阻塞队列和一般队列的区别**：

* **多线程支持**，多个线程可以安全的访问队列。
* **阻塞操作**。当队列为空时，消费线程会阻塞等到队列不为空，当队列满时，生产线程会阻塞等待队列直到不满。

方法：

| 方法/处理方式 | 抛出异常  | 返回特殊值 | 一直阻塞 | 超时退出            |
| ------------- | --------- | ---------- | -------- | ------------------- |
| 插入方式      | add(e)    | offer(e)   | put(e)   | offer(e, time unit) |
| 移除方式      | remove()  | poll()     | take()   | poll(time, unit)    |
| 检查方式      | element() | peek()     | 不可用   | 不可用              |

#### 20.5.1、JDK提供的阻塞队列

* **1、ArrayBlockingQueue**

  **有界阻塞队列**，底层采用数组实现。ArrayBlockingQueue <u>一旦创建，容量不能改变</u>。其并发控制采用可重入锁来控制，*不管是插入操作还是读取操作，都需要获取到锁才能进行操作*。此队列按照**先进先出（FIFO）的原则对元素进行排序**。默认情况下不能保证线程访问队列的公平性，参数fair 可用于设置线程是否公平访问队列。为了保证公平性，通常会降低吞吐量。

  ```java
  private static ArrayBlockingQueue<Integer> blockingQueue = new
  ArrayBlockingQueue<Integer>(10,true);//fair
  ```

* **2、LinkedBlockingQueue**

  LinkedBlockingQueue 是一个用**单向链表实现的有界阻塞队列，可以当做无界队列也可以当做有界队列来使用**。通常在创建 LinkedBlockingQueue 对象时，会指定队列最大的容量。此队列的默认和最大长度为Integer.MAX_VALUE 。此队列**按照先进先出的原则对元素进行排序**。与 ArrayBlockingQueue相比起来具有更高的吞吐量。

* **3、PriorityBlockingQueue**

  支持优先级的**无界阻塞队列**。默认情况下**元素采取自然顺序升序排列**。也可以自定义类实现compareTo() 方法来指定元素排序规则，或者初始化PriorityBlockingQueue 时，指定构造参数Comparator 来进行排序。

  PriorityBlockingQueue 只能指定初始的队列大小，后面插入元素的时候，如果空间不够的话会自动扩容。

  PriorityQueue 的线程安全版本。**不可以插入 null 值**，同时，插入队列的对象必须是可比较大小的（comparable），否则报 ClassCastException 异常。它的插入操作 put 方法不会 block，因为它是无界队列（take 方法在队列为空的时候会阻塞）。

* **4、DelayQueue**

  **支持延时获取元素的无界阻塞队列**。*队列使用PriorityBlockingQueue 来实现。队列中的元素必须实现Delayed接口*，在创建元素时可以指定多久才能从队列中获取当前元素。**只有在延迟期满时才能从队列中提取元素**。

* **5、SynchronousQueue**

  **不存储元素的阻塞队列**，每一个put必须等待一个take操作，否则不能继续添加元素。支持公平访问队列。

  SynchronousQueue 可以看成是一个传球手，**负责把生产者线程处理的数据直接传递给消费者线程**。队列本身不存储任何元素，**非常适合传递性场景**。SynchronousQueue 的吞吐量高于LinkedBlockingQueue 和ArrayBlockingQueue 。

* **LinkedTransferQueue**

  由链表结构组成的无界阻塞TransferQueue队列。相对于其他阻塞队列，多tryTransfer 和transfer 方法。

  * **transfer方法**：如果当前有消费者正在等待接收元素（take或者待时间限制的poll方法），transfer可以把生产者传入的元素立刻传给消费者。如果没有消费者等待接收元素，则将元素放在队列的tail节点，并等到该元素被消费者消费了才返回。
  * **tryTransfer方法**：用来试探生产者传入的元素能否直接传给消费者。如果没有消费者在等待，则返回false。和上述方法的区别是该方法无论消费者是否接收，方法立即返回。而transfer方法是必须等到消费者消费了才返回。

#### 20.5.2、原理

JDK使用**通知模式**实现阻塞队列。所谓通知模式，就是当生产者往满的队列里添加元素时会阻塞生产者，当消费者消费了一个队列中的元素后，会通知生产者当前队列可用。

ArrayBlockingQueue使用Condition来实现：

```java
private final Condition notEmpty;
private final Condition notFull;

public ArrayBlockingQueue(int capacity, boolean fair) {
    if (capacity <= 0)
        throw new IllegalArgumentException();
    this.items = new Object[capacity];
    lock = new ReentrantLock(fair);
    notEmpty = lock.newCondition();
    notFull =  lock.newCondition();
}

public E take() throws InterruptedException {
    final ReentrantLock lock = this.lock;
    lock.lockInterruptibly();
    try {
        while (count == 0) // 队列为空时，阻塞当前消费者
            notEmpty.await();
        return dequeue();
    } finally {
        lock.unlock();
    }
}

public void put(E e) throws InterruptedException {
    checkNotNull(e);
    final ReentrantLock lock = this.lock;
    lock.lockInterruptibly();
    try {
        while (count == items.length)
            notFull.await();
        enqueue(e);
    } finally {
        lock.unlock();
    }
}

private void enqueue(E x) {
    final Object[] items = this.items;
    items[putIndex] = x;
    if (++putIndex == items.length)
          putIndex = 0;
     count++;
     notEmpty.signal(); // 队列不为空时，通知消费者获取元素
}
```

#### 20.5.3、生产者-消费者模式

两个进程A和B，它们共享一个**固定大小的缓冲区**，A进程产生数据放入缓冲区，B进程从缓冲区中取出数据进行计算，那么这里其实就是一个生产者和消费者的模式，A相当于生产者，B相当于消费者。

**特点：**

* 保证生产者不会在缓冲区满的时候继续向缓冲区放入数据，而消费者也不会在缓冲区空的时候，消耗数据。
* 当缓冲区满的时候，生产者会进入休眠状态，当下次消费者开始消耗缓冲区的数据时，生产者才会被唤醒，开始往缓冲区中添加数据；当缓冲区空的时候，消费者也会进入休眠状态，直到生产者往缓冲区中添加数据时才会被唤醒。

**优点：**

* **解耦**：将生产者类和消费者类进行解耦，消除代码之间的依赖性，简化工作负载的管理。
* 复用：通过将生产者类和消费者类独立开来，那么可以对生产者类和消费者类进行独立的复用与扩展。
* **调整并发数**：由于生产者和消费者的处理速度是不一样的，可以调整并发数，给予慢的一方多的并发数，来提高任务的处理速度。
* **异步**：对于生产者和消费者来说能够各司其职，生产者只需要关心缓冲区是否还有数据，不需要等待消费者处理完；同样的对于消费者来说，也只需要关注缓冲区的内容，不需要关注生产者，通过异步的方式支持高并发，将一个耗时的流程拆成生产和消费两个阶段，这样生产者因为执行put()的时间比较短，而支持高并发。
* **支持分布式**：生产者和消费者通过队列进行通讯，所以不需要运行在同一台机器上，在分布式环境中可以通过redis的list作为队列，而消费者只需要轮询队列中是否有数据。同时还能支持集群的伸缩性，当某台机器宕掉的时候，不会导致整个集群宕掉。

## 21、hashtable 和concurrentHashMap有什么区别

- **底层数据结构：**
  - jdk7之前的ConcurrentHashMap底层采用的是**分段的数组+链表**实现，jdk8之后采用的是**数组+链表/红黑树；**
  - HashTable采用的是**数组+链表，**数组是主体，链表是解决hash冲突存在的。
- **实现线程安全的方式：**
  - jdk8以前，ConcurrentHashMap采用分段锁，对整个数组进行了分段分割，每一把锁只锁容器里的一部分数据，多线程访问不同数据段里的数据，就不会存在锁竞争，提高了并发访问；jdk8以后，直接采用数组+链表/红黑树，并发控制使用CAS和synchronized操作，更加提高了速度。
  - HashTable：所有的方法都加了锁来保证线程安全，但是效率非常的低下，当一个线程访问同步方法，另一个线程也访问的时候，就会陷入阻塞或者轮询的状态。

## 22、HashMap和ConcurrentHashMap的区别

HashMap 不是线程安全的，ConcurrentHashMap是线程安全的。

> HashMap 底层实现

- 在 **JDK 1.7** 版本之前， HashMap 数据结构是**数组和链表**，HashMap通过哈希算法将元素的键（Key）映射到数组中的槽位（Bucket）。如果多个键映射到同一个槽位，它们会以链表的形式存储在同一个槽位上，因为链表的查询时间是O(n)，所以冲突很严重，一个索引上的链表非常长，效率就很低了。

  ![image-20240516213321842](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240516213321842.png)

- 所以在 **JDK 1.8** 版本的时候做了优化，当一个链表的长度超过8的时候就转换数据结构，不再使用链表存储，而是使用**红黑树**，查找时使用红黑树，时间复杂度O（log n），可以提高查询性能，但是在数量较少时，即数量小于6时，会将红黑树转换回链表。

  ![image-20240516213347072](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240516213347072.png)

> ConcurrentHashMap 底层实现

- 在 **JDK 1.7** 中它使用的是数组加链表的形式实现的，而数组又分为：大数组 Segment 和小数组 HashEntry。Segment 是一种可重入锁（ReentrantLock），在 ConcurrentHashMap 里扮演锁的角色；HashEntry 则用于存储键值对数据。一个 ConcurrentHashMap 里包含一个 Segment 数组，一个 Segment 里包含一个 HashEntry 数组，每个 HashEntry 是一个链表结构的元素。简单理解就是，ConcurrentHashMap 是一个 Segment 数组，Segment 通过继承 ReentrantLock 来进行加锁，所以每次需要加锁的操作锁住的是一个 segment，这样只要保证每个 Segment 是线程安全的，也就实现了全局的线程安全。

  ![image-20240516213413121](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240516213413121.png)

- **JDK 1.8** 也引入了红黑树，优化了之前的固定链表，那么当数据量比较大的时候，查询性能也得到了很大的提升，从之前的 O(n) 优化到了 O(logn) 的时间复杂度。ConcurrentHashMap 主要通过 volatile + CAS 或者 synchronized 来实现的线程安全的，ConcurrentHashMap通过对头结点加锁来保证线程安全的，锁的粒度相比 Segment 来说更小了，发生冲突和加锁的频率降低了，并发操作的性能就提高了。

  ![image-20240516213439112](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240516213439112.png)

# 三、并发

## 1、线程池

**线程池是一种利用池化技术思想来实现的线程管理技术，主要是为了复用线程、便利地管理线程和任务、并将线程的创建和任务的执行解耦开来。**

>我们可以创建线程池来复用已经创建的线程来降低频繁创建和销毁线程所带来的资源消耗。在JAVA中主要是**使用ThreadPoolExecutor类来创建线程池**，并且JDK中也提供了Executors工厂类来创建线程池（不推荐使用）。

**线程池的优点：**

* **降低资源消耗**，复用已创建的线程来降低创建和销毁线程的消耗。
* **提高响应速度**，任务到达时，可以不需要等待线程的创建立即执行。
* **提高线程的可管理性**，使用线程池能够统一的分配、调优和监控。

### 1.1、为什么平时都是使用一个线程池创建线程，而不直接new一个线程。

手动创建线程的两个缺点：

* **不受控风险。**

  系统资源有限，每个人针对不同业务都可以手动创建线程，并且**创建线程没有统一标准**，比如线程名的规范性。当系统运行时，所有线程都在抢占资源，毫无规则，混乱程度可想而知，不容易管控。

* **频繁创建开销较大。**

  new Thread() 创建一个线程和 new Object()是有区别的。

  **new Object()的过程如下：**

  * JVM分配一块内存M
  * 在内存M上初始化对象
  * 将内存M的地址赋值给引用变量obj

  **创建线程的过程：**

  * JVM为每一个**线程栈**分配内存，该栈为每一个线程方法调用保存一个**栈帧**
  * 每一个栈帧有一个**局部变量数组、返回值、操作数堆栈和常量池**组成
  * 每个线程获得一个**程序计数器**，用于记录当前虚拟机正在执行的线程指令地址
  * 系统创建一个与java线程对应的**本机线程**
  * 将与线程相关的**描述符**添加到JVM内部数据结构中
  * 线程**共享堆和方法区域**

**创建一个线程大概需要1M左右的内存空间**，可见频繁手动创建/销毁线程的代价是非常大的。

### 1.2、为什么使用线程池

* **降低资源消耗**：通过<u>*重复利用已创建的线程*</u>降低线程创建或销毁带来的消耗。
* **提高响应速度**：当任务到达时，可以<u>*不需要等待创建线程就能立刻执行*</u>。
* **提高线程的可管理性**：统一线程管理，避免系统创建大量同类线程而造成资源消耗导致内存用尽。

### 1.3、线程池的执行原理

![线程池执行流程](http://img.topjavaer.cn/img/%E7%BA%BF%E7%A8%8B%E6%B1%A0%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B.png)

* 如果线程池中存活的线程数小于核心线程数corePoolSize时，这时对于一个新提交的任务，线程池就会创建一个新的线程去处理任务。当线程池中存活的线程数小于等于corePoolSize时，线程池中的线程将会一直存活，即使空闲时间超过了KeepAliveTime，线程也不会销毁，而是一直阻塞在哪里一直等待任务队列的任务来执行。
* 当线程池中存活的线程数已经等于corePoolSize，对于新提交的任务，会被放进一个任务队列workQueue中进行排队等待。
* 当线程池中存活的线程数等于corePoolSize，并且任务队列也满了，假设maximunPoolSize>corePoolSize，表示线程池还没有满，此时如果再来新的任务，线程池就会为该任务创建一个线程，直到线程数达到maximunPoolSize，就不会再创建新的线程。
* 如果当先的线程数达到了maximunPoolSize，并且任务队列也满了，此时如果再来新的任务就会采用**拒绝策略**进行处理。默认的拒绝策略时抛出一个**RejectedExecutionException**异常。

### 1.4、线程池的参数

ThreadPoolExecution的构造函数：

```java
public ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, ThreadFactory threadFactory, RejectedExecutionHandler handler);
```

* **corePoolSize：**当有新任务时，线程池的线程数没有达到线程池的基本大小，就会创建新的线程，否则将任务放进阻塞队列。如果线程池中的线程数的大小总是超过corePoolSize，则需要考虑调大corePoolSize。

* **maximumPoolSize：**当阻塞队列没有满的时候，如果线程池中的线程数没有超过最大线程数，则会创建新的线程处理任务，否则将会采取拒绝策略处理新任务。**非核心线程类似于临时借来的资源，这些线程的空闲时间超过keepAliveTime时就应该退出，避免造成资源浪费**。

* **BlockingQueue：**阻塞队列存储等待运行的任务。

* **keepAliveTime：**非核心线程空闲后，保持存活的时间，该参数只对非核心线程有效。设置为0则表示创建的非核心线程将会被立即终止。

* **TimeUnit：**时间单位。

  ```java
  TimeUnit.DAYS
  TimeUnit.HOURS
  TimeUnit.MINUTES
  TimeUnit.SECONDS
  TimeUnit.MILLISECONDS
  TimeUnit.MICROSECONDS
  TimeUnit.NANOSECONDS
  ```

* ThreadFactory：每当线程池创建一个线程时，都是通过**线程工场**来完成的。线程工场中只包含一个newThread方法，每当线程池需要创建线程时就会调用它。

  ```java
  public class MyThreadFactory implements ThreadFactory {
      private final String poolName;
      
      public MyThreadFactory(String poolName) {
          this.poolName = poolName;
      }
      
      public Thread newThread(Runnable runnable) {
          return new MyAppThread(runnable, poolName);//将线程池名字传递给构造函数，用于区分不同线程池的线程
      }
  }
  ```

* **RejectionExecutionHandler：**当线程池和阻塞队列都满的时候，就会采取拒绝策略处理新的任务。

  ```java
  AbortPolicy：默认的策略，直接抛出RejectedExecutionException
  DiscardPolicy：不处理，直接丢弃
  DiscardOldestPolicy：将等待队列队首的任务丢弃，并执行当前任务
  CallerRunsPolicy：由调用线程处理该任务
  ```

### 1.5、线程池的大小应该怎么设置

如果线程池线程数量太少，当出现大量请求需要处理时，**系统响应比较慢**，影响用户体验，甚至会出现**任务队列大量堆积造成OOM**（内存泄漏）。

如果线程池线程数量过大，就会有**大量线程同时抢占CPU资源**，导致大量的上下文切换，从而增加了线程的执行时间，降低执行效率。

**按照以下两种情况设置：**

* **CPU密集型任务（N + 1）**：这种任务消耗的主要是CPU资源，可以将线程数设置为**N（CPU核心数） + 1**，多出来的一个线程是为了**防止某些原因（如IO操作、线程sleep、等待锁）造成的线程阻塞带来的影响**。一旦某个线程被阻塞，释放了CPU资源，多出来的这个线程就可以充分利用CPU的空闲时间。

* **I/O密集型任务（2 * N）**：系统大部分时间都在处理I/O操作，可能会造成线程阻塞，释放CPU资源，此时可以将CPU交给其他线程使用。因此**在I/O密集型任务中可以多配备一些线程**，具体的计算方法：`最佳线程数 = CPU核心数 * （1/CPU利用率）= CPU核心数 * （1 + （I/O耗时/CPU耗时））`，一般可设置为`2N`。

### 1.6、线程池的类型及其适用场景

常见的线程池有 FixedThreadPool 、SingleThreadExecutor 、CachedThreadPool 和
ScheduledThreadPool 。这几个都是 ExecutorService 线程池实例。

* **FixedThreadPool**

  **固定线程数的线程池。**任何时间都只有n个线程处于活动状态执行任务。

  ```java
  public static ExecutorService newFixedThreadPool(int nThreads) {
  	return new ThreadPoolExecutor(nThreads, nThreads, 0L, TimeUnit.MILLISECONDS, new LinkedBlockingQueue<Runnable>());
  }
  ```

  **使用无界队列LinkedBlockingQueue，运行中的线程池不会拒绝任务，即不会调用RejectedExecutionHandler.rejectedExecution()方法。**

  maximumPoolSize是无效参数，因为它和corePoolSize相同。

  keepAliveTime也是无效参数，因为线程池中的线程都是核心线程。核心线程不会被回收。

  **适用场景**：适合处理**CPU密集型任务**，确保CPU在长期被线程使用的情况下，尽可能少的分配线程，即适用于**执行长期任务**。需要注意的是，*FixedThreadPool不会拒绝任务，因此可能会造成OOM*。

* **SingleThreadExecution**

  **只有一个线程的线程池。**

  ```java
  public static ExecutionService newSingleThreadExecutor() {
  	return new ThreadPoolExecutor(1, 1, 0L, TimeUnit.MILLISECONDS, new LinkedBlockingQueue<Runnable>());
  }
  ```

  使用**无界队列LinkedBlockingQueue**。线程池中只有一个运行的线程。新来的任务放进任务队列，线程处理完任务后就循环的从任务队列中获取任务执行。保证顺序的执行各个任务。

  **适用场景**：适用于**串行执行任务**的场景，一个任务一个任务的执行，任务较多时也会造成OOM。

* **CachedThreadPool**

  **根据需要创建新线程的线程池。**

  ```java
  public static ExecutorService newCachedThreadPool() {
  	return new ThreadPoolExecutor(0, Integer.MAX_VALUE, 60L, TimeUnit.SECONDS, new SynchronousQueue<Runnable>());
  }
  ```

  主线程提交任务的速度高于线程处理任务的速度时，CachedThreadPool会不断创建新的线程，**极端情况下会导致耗尽CPU和内存资源**。

  使用**没有容量的SychronousQueue**作为线程池工作队列，当线程池有空闲时SychronousQueue.offer(Runnable task)提交的任务会被空闲线程处理，否则将会创建新的线程。

  **使用场景**：用于**并发执行大量短期的小任务**。CacheedThreadPool允许创建的线程数量为Integer.MAX_VALUE，**可能会创建大量线程导致OOM**。

* **ScheduledThreadPoolExecution**

  **在给定的延迟后运行任务，或者定期执行任务**。在实际项目中基本不会用到，因为有其他方案选择。

  使用**延迟队列DelayQueue**封装了一个PriorityQueue，PriorityQueue会对队列中的任务进行排序，时间早的任务先被执行（即ScheduledFutureTask的time变量小的先执行），如果time相同则先提交的任务将会被先执行（ScheduledFutureTask的squenceNumber变量小的先执行）。

  执行周期任务步骤：

  * 线程从 DelayQueue 中获取已到期的 ScheduledFutureTask（DelayQueue.take()） 。到期任务是指 ScheduledFutureTask 的 time 大于等于当前系统的时间；
  * 执行这个 ScheduledFutureTask ；
  * 修改 ScheduledFutureTask 的 time 变量为下次将要被执行的时间；
  * 把这个修改 time 之后的 ScheduledFutureTask 放回 DelayQueue 中（DelayQueue.add() )。

  **适用场景**：**周期性执行任务的场景，需要限制线程数量的场景。**

![img](http://img.topjavaer.cn/img/scheduled-task.jpg)

## 2、进程线程

进程是指一个内存中运行的应用程序，每个进程都有自己独立的内存空间。

线程是比进程更小的执行单位，它是**在一个进程中独立的控制流**，一个进程可以启动多个线程，**每条线程可以并行的执行不同的任务**。

### 2.1、线程的生命周期

* **初始（NEW）**：线程被构建，还没有调用start()。
* **运行（RUNNABLE）**：包括操作系统的**运行和就绪**两种状态。
* **阻塞（BLOCKED）**：一般是被动的，在**抢占资源时抢占不到**，被动的挂起在内存中，等待资源释放将其唤醒。阻塞**会释放CPU资源但不会释放内存**。
* **等待（WAITING）**：进入该状态的线程需要等待其他线程做出一些特定动作（**通知或中断**）。
* **超时等待（TIME_WAITING）**：该状态不同于WAITING，它可以在**指定时间后自行返回**。
* **终止（TERMINATED）**：表示该线程已经执行完毕。

![img](http://img.topjavaer.cn/img/image-20210909235618175.png)

### 2.2、线程中断

线程中断就是**线程在运行过程中被其他线程打断了**。和stop的区别在于，stop是系统强制终止线程运行，而线程中断是要先向中断线程发送中断信号，在中断线程没有接收中断信号并终止线程前，线程是不会被终止的，具体是否退出或执行其他逻辑取决于目标线程。

线程中断的三个重要方法：

* **java.lang.Thread#interrupt()**

  调用interrupt()方法向目标线程发送中断信号，**目标线程被打上中断标记**。

* **java.lang.Thread#isInterrupted()**

  判断目标线程是否被中断，**不会清除中断标记**。

* **java.lang.Thread#Interrupted()**

  判断目标线程是否被中断，**会清除中断标记**。

  ```java
  private static void test2() {
      Thread thread = new Thread(() -> {
          while (true) {
              Thread.yield();
  
              // 响应中断
              if (Thread.currentThread().isInterrupted()) {
                  System.out.println("Java技术栈线程被中断，程序退出。");
                  return;
              }
          }
      });
      thread.start();
      thread.interrupt();
  }
  ```

### 2.3、创建线程的方式

* **通过扩展Thread类来创建多线程。**

  >**步骤：**
  >1.创建一个继承于Thread类的子类
  >2.重写Thread类的run() --> 将此线程执行的操作声明在run()中
  >3.创建Thread类的子类的对象
  >4.通过此对象调用start()执行线程

  ```java
  public class MyThread extends Thread{
      public MyThread() {}
  	
      // run()方法是由jvm创建完操作系统级线程后回调的方法，不可以手动调用，手动调用相当于调用普通方法。
      @Override
      public void run() {
          for (int i = 0; i < 10; i++) {
              System.out.println(Thread.currentThread() + ":" + i);
          }
      }
  
      public static void main(String[] args) {
          MyThread thread1 = new MyThread();
          MyThread thread2 = new MyThread();
          MyThread thread3 = new MyThread();
  
          thread1.start();
          thread2.start();
          thread3.start();
      }
  }
  ```

* **通过实现Runnable接口来创建多线程**。

  >**步骤：**
  >1.创建一个实现了Runnable接口的类
  >2.实现类去实现Runnable中的抽象方法：run()
  >3.创建实现类的对象
  >4.将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
  >5.通过Thread类的对象调用start()
  >① 启动线程
  >②调用当前线程的run()–>调用了Runnable类型的target的run()

  ```java
  public class MyRunnable implements Runnable{
      @Override
      public void run() {
          System.out.println("当前线程：" + Thread.currentThread().getName());
      }
  }
  
  class RunnableText {
      public static void main(String[] args) {
          MyRunnable runnable = new MyRunnable();
          Thread thread = new Thread(runnable);
          thread.start();
          System.out.println("主线程：" + Thread.currentThread().getName());
      }
  }
  ```

  **实现Runnable接口比直接继承Thread具有的优势**：

  * 可以避免java中**单继承**的限制。
  * **线程池只能放入实现Runnable或Callable类的线程**，不能直接放入继承Thread的类。

* **实现Callable接口，通过FutureTask接口来创建线程**。

  >**步骤：**
  >1.创建一个实现Callable的实现类
  >2.实现call方法，将此线程需要执行的操作声明在call()中
  >3.创建Callable接口实现类的对象
  >4.将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象
  >5.将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()
  >6.获取Callable中call方法的返回值

  ```java
  public class MyCallable implements Callable<Integer> {
      @Override
      public Integer call() throws Exception {
          int sum = 0;
          for (int i = 0; i < 100; i++) {
              sum += i;
          }
          return sum;
      }
  }
  
  class CallableTest {
      public static void main(String[] args) {
          MyCallable callable = new MyCallable();
  
          // 异步计算的结果
          FutureTask<Integer> result = new FutureTask<>(callable);
  
          new Thread(result).start();
  
          try {
              // 等待任务完成，返回结果
              int sum = result.get();
              System.out.println(sum);
          } catch (Exception e) {
              e.printStackTrace();
          }
      }
  }
  ```

* **使用Executor线程池框架来创建线程池**。

  >步骤：
  >
  >1.创建一个Runable的实现类
  >
  >2.实现Runable中的run方法，将执行操作声明在run中
  >
  >3.调用Executor的newCachedThreadPool方法，创建一个ExecutorService的实例化对象
  >
  >4.调用该实例化对象的submit方法，并新建一个ExecutorThreadPool的实例化对象作为参数
  
  ```java
  public class ExecutorThreadPool implements Runnable{
      @Override
      public void run() {
          System.out.println("创建线程池");
      }
  }
  
  class ExecutorThreadPoolText {
      public static void main(String[] args) {
          //获取ExecutorService实例，生产禁用，需要手动创建线程池
          ExecutorService executorService = Executors.newCachedThreadPool();
          //提交任务
          executorService.submit(new ExecutorThreadPool());
      }
  }
  ```

### 2.4、线程死锁

线程死锁是指存在**两个或两个以上线程因争夺资源而造成的一种互相等待的现象**，若无外力作用，它们都将无法继续推进下去。

![死锁](http://img.topjavaer.cn/img/%E6%AD%BB%E9%94%81.png)

线程a持有资源1，线程b持有资源2，此时两个线程同时想申请对方的资源， 所以这两个线程都将进入互相等待从而进入死锁状态。

```java
public class ThreadLock {
    private static Object resource1 = new Object();
    private static Object resource2 = new Object();

    public static void main(String[] args) {
        new Thread(() -> {
            synchronized (resource1) {
                System.out.println(Thread.currentThread() + "get resource1");
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread() + "waiting for resource2");
                synchronized (resource2) {
                    System.out.println(Thread.currentThread() + "get resource2");
                }
            }
        }, "线程1").start();

        new Thread(() -> {
            synchronized (resource2) {
                System.out.println(Thread.currentThread() + "get resource2");
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread() + "waiting for resource1");
                synchronized (resource1) {
                    System.out.println(Thread.currentThread() + "get resource1");
                }
            }
        }, "线程2").start();
    }
}
```

线程 A 通过 synchronized (resource1) 获得 resource1 的监视器锁，然后通过Thread.sleep(1000) 。让线程 A 休眠 1s 为的是让线程 B 得到执行然后获取到 resource2 的监视器锁。线程 A 和线程 B 休眠结束了都开始企图请求获取对方的资源，然后这两个线程就会陷入互相等待的状态，这也就产生了死锁。

### 2.5、死锁是怎么产生的，怎么避免死锁

**死锁产生的四个必要条件：**

* **互斥**：每个资源只能被一个进程使用。
* **请求与保持**：一个进程因请求资源而阻塞时，不释放获得资源。
* **不可剥夺**：进程已获得的资源，在未使用前，不能强行剥夺。
* **循环等待**：进程之间循环等待着资源。

**避免死锁的方法：**

* **互斥条件不能被破坏**，因为加锁就是为了保持互斥。
* 一次性申请所有资源，避免线程占有资源而且在等待其他资源。
* 占有部分资源的线程进一步申请其他资源时，如果申请不到，主动释放它所占有的资源。
* 按序申请资源。

### 2.6、线程run和start的区别

* 当程序调用start()方法时，会创建一个新的线程去执行run()中的代码，run()就像一个普通方法一样，调用run()方法并不会创建新的线程。
* 一个线程的start()只能调用一次，多次调用会抛出java.lang.IllegalThreadStateException异常。而run()可以多次调用没有限制。

### 2.7、线程都有哪些方法

* start()：用于**启动线程**。

* getPriority()：**获取线程优先级**，默认优先级是5，如果不手动指定，那么**线程优先级具有继承性**，比如线程A启动线程B，则线程A和线程B具有相同的优先级。

* setPriority()：**设置线程优先级**，CPU会尽量将执行资源让给优先级比较高的线程。

* interrupt()：**中断线程**，具体是中断还是其他执行逻辑，由被通知的线程自己处理。

  **对一个线程调用interrupt()时，有两种情况**：

  * 如果线程处于阻塞状态（sleep、wait、join等），则该线程立即退出阻塞状态，并抛出InterruptedException异常。
  * 如果线程处于正常活动状态，那么该线程的中断标志位设置为true，标志位为true的线程可以继续正常运行，不受影响。

  interrupt()不能真正的中断线程，需要被中断线程自己进行配合才行。

* join()：**等待其他线程结束**。在当前线程调用其他线程的join()，则当前线程转入阻塞状态，直到另一个进行运行结束，当前线程再由阻塞转为就绪状态。

* yield()：**暂停当前执行的线程，将执行机会让给优先级相同或更高的线程**。

* sleep()：**使线程转入阻塞状态**。millis参数设定睡眠时间，以毫秒为单位。当睡眠结束后，线程自动转为Runnable状态。

## 3、volatile底层原理

**volatile是轻量级的同步机制，volatile保证变量对所有线程的可见性，不保证原子性。**

* 当对volatile变量进行写操作时，JVM会向处理器发送一条LOCK前缀的指令，将该变量所在的缓存行的数据写回系统内存。
* 由于**缓存一致性协议**，每个处理器通过嗅探在总线上传播的数据来检查自己的缓存是否过期了，当处理器发现自己缓存行对应的内存地址被修改时，将会将当前处理器的缓存行设置为无效状态，当处理器对这个数据进行修改操作时，会重新从系统内存中把数据读取到处理器缓存中。

>**缓存一致性协议：**
>当CPU写数据时，如果发现当前操作的变量时共享变量，即在其他CPU中也存在该变量的副本，会发出信号通知其他CPU将该变量的缓存行设置为无效状态，因此当其他CPU需要读取这个数据时，就会从内存中重新读取。

volatile关键字的两个作用：

* **保证了不同线程对共享变量进行操作的可变性**，即一个线程修改了某个变量的值，这个新的值对于其他线程来说时立即可见的。

* **禁止进行指令重排序**

  > 指令重排序是JVM为了优化指令，提高程序运行效率，在不影响单线程程序执行结果的前提下，尽可能的提高并行度。Java编译器会在生成指令序列时在适当的位置插入内存屏障指令来禁止处理器重排序。插入一个内存屏障，相当于告诉CPU和编译器，先于这个指令的必须先执行，后于这个指令的必须后执行。对于一个volatile字段进行写操作时，Java内存模型将在写操作后插入一个屏障指令，这个指令会把之前的写入值都刷新到内存中。

## 4、volatile为什么不能保证原子性

**volatile可以保证可见性和顺序性，但是它不能保证原子性**。

举个例子。一个变量i被volatile修饰，两个线程想对这个变量修改，都对其进行自增操作i++，i++的过程可以分为三步，首先获取i的值，其次对i的值进行加1，最后将得到的新值写会到缓存中。

假如i的初始值为100。线程A首先得到了i的初始值100，但是还没来得及修改，就阻塞了，这时线程B开始了，它也去取i的值，**由于i的值未被修改，即使是被volatile修饰，主存的变量还没变化**，那么线程B得到的值也是100，之后对其进行加1操作，得到101，将新值写入到缓存中，再刷入主存中。根据可见性的原则，这个主存的值可以被其他线程可见。

那么问题来了，线程A之前已经读取到了i的值为100，线程A阻塞结束后，继续将100这个值加1，得到101，再将值写到缓存，最后刷入主存。这样i经过两次自增之后，结果值只加了1，明显是有问题的。所以说**即便volatile具有可见性，也不能保证对它修饰的变量具有原子性**。

## 5、synchronized的用法有哪些

> synchronized是一个对象锁，也就是它锁的是一个对象。因此，无论使用哪一种方法，synchronized都需要有一个锁对象。

* **修饰普通方法**：synchronized修饰实例方法只需要在方法上加上synchronized关键字即可。

  ```java
  public synchronized void add(){
         i++;
  }
  ```

  此时，**synchronized加锁的对象就是这个方法所在实例的本身**。

* **修饰静态方法**：synchronized修饰静态方法的使用与实例方法并无差别，在静态方法上加上synchronized关键字即可

  ```java
  public static synchronized void add(){
         i++;
  }
  ```

  此时，**synchronized加锁的对象为当前静态方法所在类的Class对象**。

* **修饰代码块**：synchronized修饰代码块需要传入一个对象，**指定加锁对象，对给定对象加锁**，进入同步代码块之前要获得给定对象的锁。

  ```java
  public void add() {f
      synchronized (this) {
          i++;
      }
  }
  ```

  **此时synchronized加锁对象即为传入的这个对象实例**。

## 6、synchronized的作用

* **互斥性**：确保线程互斥的访问同步代码。

* **可见性**：保证共享变量的修改时及时可见的。

* **有序性**：有效解决重排序问题。

## 7、synchronized底层实现原理

### 7.1、同步代码块的实现

**synchronized同步代码块是通过monitorenter和monitorexit执行来实现的**。monitorenter指向同步代码块的开始位置，monitorexit指向同步代码块的结束位置。当执行monitorenter指令时，线程试图获取锁，也就是获取monitor的持有权（**monitor对象存在于每个Java对象的对象头中，synchronized锁便是通过这种方式获取锁的。这也就是为什么Java中任意对象都可以作为锁的原因**）。

> Monitor对象被称为管理或者监视器锁。在Java中，每一个对象实例都会关联一个Monitor对象。这个Monitor对象既可以与对象一起创建销毁，也可以在线程试图获取对象锁时自动生成。当这个Monitor对象被线程持有后，它便处于锁定状态。

其内部有一个计数器，**当计数器为0时表示可以获取，获取后计数器设为1**，相应的在执行完monitorexit指令后，计数器置为0，表示锁被释放。如果获取对象锁失败，当前线程就要阻塞等待，直到锁被另一个线程释放。

### 7.2、同步方法的实现

**synchronized修饰的方法并没有monitorenter和monitorexit指令，取而代之的时ACC_SYNCHRONIZED标识符**，该标识指明了该方法是一个同步方法，JVM**通过ACC_SYNCHRONIZED标识符来判断该方法是否为同步方法**，从而执行相应的同步调用。

## 8、volatile和synchronized的区别

* volatile只能使用在变量上，而**synchronized可以使用在变量、方法、类和代码块上**。
* volatile保证可见性，**synchronized保证原子性和可见性**。
* **volatile禁止指令重排序**，synchronized不会。
* **volatile不会造成阻塞**，synchronized会。

## 9、ReentrantLock和synchronized的区别

* 使用synchronized关键字实现同步，执行完同步代码块之后会自动释放锁，而**ReentrantLock需要手动释放**。
* **synchronized是非公平锁**，ReentrantLock可以设置为公平锁。
* **ReentrantLock主动获取锁的线程是可以中断的**，线程可以放弃等待锁，而synchronized则会无期限的等待下去直到获取锁。
* **ReentrantLock可以设置超时获取锁**，在指定的截止时间之前获取锁，如果截止时间到了还没有获取锁，则返回。
* ReentrantLock的tryLock()方法**可以尝试非阻塞的获取锁**，调用该方法后立即返回，如果获取到锁则返回true，否则返回false。

## 10、wait()和sleep()的异同

**相同：**

* 都可以使当前线程暂停运行，把机会交给其他线程。
* 任何线程在调用wait()和sleep()后，在等待期间被中断都会抛出InterruptedException异常。

**不同点：**

* wait()是Object超类中的方法，而sleep()是Thread类中的方法。
* 对锁的持有不同，wait()会释放锁，而sleep()不会释放锁。
* 唤醒方法不完全相同。wait()依靠notify/notifyAll、中断、达到指定时间来唤醒，sleep()达到指定时间就会被唤醒。
* 调用wait()方法之前需要获取对象的锁，而Thread.sleep()不需要。

## 11、Runnable和Callable的区别

* Callable的接口方法是**call()**，而Runnable的接口方法是**run()**。
* Callable接口call方法有返回值支持泛型，Runnable的接口方法run没有返回值。
* Callable接口call方法允许抛出异常，而Runnable的接口方法run不能上抛异常。

## 12、线程执行顺序怎么控制

假设有T1、T2、T3三个线程，你怎样保证T2在T1执行完后执行，T3在T2执行完后执行？

使用join()方法。比如在线程A中，调用线程B中的join方法，意思就是：线程A等待线程B执行完毕后（释放CPU执行权），再继续执行。

```java
public class SeasonThreadTask implements Runnable{

    private String name;
    public SeasonThreadTask(String name) {
        this.name = name;
    }

    @Override
    public void run() {
        for (int i = 0; i < 4; i++) {
            System.out.println(this.name + "来了" + i + "次");
            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

class SeasonThreadTaskTest {
    public static void main(String[] args) {
        Thread spring = new Thread(new SeasonThreadTask("春天"));
        Thread summer = new Thread(new SeasonThreadTask("夏天"));
        Thread autumn = new Thread(new SeasonThreadTask("秋天"));

        try {
            spring.start();
            spring.join();
            summer.start();
            summer.join();
            autumn.start();
            autumn.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

    }
}
```

## 13、守护线程

守护线程是运行在后台的一种特殊的线程。**它独立于控制终端并周期性的执行某种任务或者等待处理某些发生的事件。**Java中的垃圾回收线程就是特殊的守护线程。

## 14、线程间的通信方式

* **使用 Object 类的 wait()/notify()**。Object 类提供了线程间通信的方法：`wait()`、`notify()`、`notifyAll()`，它们是多线程通信的基础。其中，**`wait/notify` 必须配合 `synchronized` 使用**，wait 方法释放锁，notify 方法不释放锁。wait 是指在一个已经进入了同步锁的线程内，让自己暂时让出同步锁，以便其他正在等待此锁的线程可以得到同步锁并运行，notify并不释放锁，只是告诉调用过`wait()`的线程可以去参与获得锁的竞争了，但不是马上得到锁，因为锁还在别人手里，别人还没释放。当其他线程调用了`notify()`后，调用 `wait()` 的一个或多个线程就会解除 wait 状态，重新参与竞争对象锁，程序如果可以再次得到锁，就可以继续向下运行。
* **使用volatile关键字。**基于volatile关键字实现线程间的相互通信，其底层使用了**共享内存**。简单来说就是，**多个线程共同监听一个变量**，当这个变量发生变化的时候，线程能够感知变化并执行相应的业务。
* **使用JUC工具CountDownLatch。**jdk1.5 之后在java.util.concurrent 包下提供了很多并发编
  程相关的工具类，简化了并发编程开发， **CountDownLatch 基于 AQS 框架，相当于也是维护了一个线程间共享变量 state**。
* **使用LockSupport实现线程间的阻塞和唤醒。**LockSupport是一种非常灵活的实现线程阻塞和唤醒的工具，使用它不用关注是等待线程先运行还是唤醒线程先运行，但是前提是知道线程的名字。

## 15、ThreadLocal

线程本地变量。使用TreadLocal维护变量时，**ThreadLocal为每一个使用该变量的线程提供独立的变量副本**，所以每个线程都可以独立的改变自己的副本，而不会影响其他线程。

### 15.1、ThreadLocal原理

每个线程都有一个ThreadLocalMap，Map中的键为ThreadLocal，而值对应变量的副本。

![image-20240315155015894](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240315155015894.png)

ThreadLocal set赋值的时候首先会获取当前线程thread,并获取thread线程中的ThreadLocalMap属性。如果map属性不为空，则直接更新value值，如果map为空，则实例化threadLocalMap,并将value值初始化。

```java
public void set(T value) {
    Thread t = Thread.currentThread();
    ThreadLocalMap map = getMap(t);
    if (map != null)
        map.set(this, value);
    else
        createMap(t, value);
}

ThreadLocalMap getMap(Thread t) {
    return t.threadLocals;
}

void createMap(Thread t, T firstValue) {
    t.threadLocals = new ThreadLocalMap(this, firstValue);
}
```

先获取当前线程，然后获取当前线程的ThreadLocalMap，如果是数据为null，则初始化，初始化后，TheralLocalMap中存放key值为threadLocal，值为null，如果map数据不为空，则获取threalLocalMap中存储的值。

```java
public T get() {
    Thread t = Thread.currentThread();
    ThreadLocalMap map = getMap(t);
    if (map != null) {
        ThreadLocalMap.Entry e = map.getEntry(this);
        if (e != null) {
            @SuppressWarnings("unchecked")
            T result = (T)e.value;
            return result;
        }
    }
    return setInitialValue();
}
```

threadLocal类型ThreadLocalMap的键为ThreadLocal对象，因为每个线程可以有多个threadLocal变量，如longLocal和stringLocal。

```java
public class ThreadLocalDemo {

    ThreadLocal<Long> threadLocal = new ThreadLocal<>();

    public void set() {
        threadLocal.set(Thread.currentThread().getId());
    }
    public Long get() {
        return threadLocal.get();
    }

    public static void main(String[] args) throws InterruptedException{
        ThreadLocalDemo threadLocalDemo = new ThreadLocalDemo();
        threadLocalDemo.set();
        System.out.println(threadLocalDemo.get());

        Thread thread = new Thread(() -> {
            threadLocalDemo.set();
            System.out.println(threadLocalDemo.get());
        });

        thread.start();
        thread.join();

        System.out.println(threadLocalDemo.get());
    }
}
//输出：1 20 1
```

ThreadLocal 并不是用来解决共享资源的多线程访问问题，因为**每个线程中的资源只是副本**，不会共享。因此**ThreadLocal 适合作为线程上下文变量**，简化线程内传参。

### 15.2、ThreadLocal内存泄漏的原因

每个线程都有一个ThreadLocalMap属性，**其map的键为ThreadLocal，定义为弱引用，而值为强引用类型**。**垃圾回收的时候会自动回收key，而value的回收取决于Thread的生命周期**。一般会通过线程池的方式复用线程以节省资源，这样就导致了线程对象的生命周期比较长，这样就一直存在一条强引用链的关系：**Thread-->ThreadLocalMap-->Entry-->Value**。随着任务的执行，value有可能越来越多无法释放，最终导致内存泄漏。

**解决办法：** **每次使用完ThreadLocal就调用它的remove()方法**，手动的将对应的键值删除，避免造成内存泄漏。

### 15.3、 ThreadLocal的使用场景

**场景一：**

ThreadLocal 用作保存每个线程独享的对象，为每个线程都创建一个副本，这样每个线程都可以修改自己所拥有的副本, 而不会影响其他线程的副本，确保了线程安全。

这种场景适合**保存线程不安全的工具类**，典型使用的类就是**SimpleDateFormate**。

假如需求为500个线程都要用到 SimpleDateFormat，使用线程池来实现线程的复用，否则会消耗过多的内存等资源，如果我们每个任务都创建了一个 simpleDateFormat 对象，也就是说，500个任务对应500个 simpleDateFormat 对象。但是这么多对象的创建是有开销的，而且这么多对象同时存在在内存中也是一种内存的浪费。可以将simpleDateFormat 对象给提取了出来，变成静态变量，但是这样一来就会有线程不安全的问题。我们想要的效果是，既不浪费过多的内存，同时又想保证线程安全。此时，可以使用 ThreadLocal来达到这个目的，每个线程都拥有一个自己的 simpleDateFormat 对象。

**场景二：**

**ThreadLocal 用作每个线程内需要独立保存信息，以便供其他方法更方便地获取该信息的场景**。每个线程获取到的信息可能都是不一样的，前面执行的方法保存了信息后，后续方法可以通过 ThreadLocal 直接获取到，避免了传参，**类似于全局变量的概念**。

### 15.4、ThreadLocal与Synchronized的区别

* Synchronized用于线程间的**数据共享**，而ThreadLocal则用于线程间的**数据隔离**。

* Synchronized是利用锁的机制，使变量或代码块在某一时该只能被一个线程访问。而ThreadLocal为每一个线程都提供了变量的副本，使得每个线程在某一时间访问到的并不是同一个对象，这样就隔离了多个线程对数据的数据共享。而Synchronized却正好相反，它用于在多个线程间通信时能够获得数据共享。

## 16、AQS

AQS（AbstractQueuedSynchronizer）是java.util.concurrent包下的核心类，我们经常使用的ReentrantLock、CountDownLatch，都是基于**AQS抽象同步式队列**实现的。

AQS作为一个抽象类，**通常是通过继承来使用的**。它本身是没有同步接口的，只是定义了同步状态的同步获取和同步释放的方法。

**AQS是个双向链表，**JUC包下面大部分同步类，都是基于AQS的同步状态的获取与释放来实现的。

## 17、为什么AQS是双向链表而不是单向的

双向链表有两个指针，一个指针指向前置节点，一个指针指向后继节点。所以，**双向链表可以支持常量 O(1) 时间复杂度的情况下找到前驱节点**。因此，双向链表在插入和删除操作的时候，要比单向链表简单、高效。

从双向链表的特性来看，AQS 使用双向链表有2个方面的原因：

1. 没有竞争到锁的线程加入到阻塞队列，并且阻塞等待的前提是，**当前线程所在节点的前置节点是正常状态**，这样设计是为了避免链表中存在异常线程导致无法唤醒后续线程的问题。所以，**线程阻塞之前需要判断前置节点的状态**，如果没有指针指向前置节点，就需要从 Head 节点开始遍历，性能非常低。
2. 在 Lock 接口里面有一个**lockInterruptibly()方法，**这个方法表示**处于锁阻塞的线程允许被中断**。也就是说，没有竞争到锁的线程加入到同步队列等待以后，是允许外部线程通过interrupt()方法触发唤醒并中断的。这个时候，**被中断的线程的状态会修改成 CANCELLED**。而被标记为 CANCELLED 状态的线程，是不需要去竞争锁的，但是它仍然存在于双向链表里面。这就意味着**在后续的锁竞争中，需要把这个节点从链表里面移除，否则会导致锁阻塞的线程无法被正常唤醒。**在这种情况下，如果是单向链表，就需要从 Head 节点开始往下逐个遍历，找到并移除异常状态的节点。同样效率也比较低，**还会导致锁唤醒的操作和遍历操作之间的竞争**。

## 18、AQS原理

AQS，`AbstractQueuedSynchronizer`抽象队列同步器，定义了一套**多线程访问共享资源的同步器框架**，许多并发工具都依赖于它，如ReentrantLock/Semaphore/CountDownLatch。

**AQS使用一个volatile的int类型的成员变量state来表示同步状态**，通过CAS修改同步状态的值。当线程调用lock方法时，如果state=0，说明没有任何进程获取共享资源的锁，可以获得锁并将state加1，如果state不为0，说明有进程正在使用共享资源，此时其他线程必须加入同步队列进行等待。

```java
private volatile int state;//共享变量，使用volatile修饰保证线程可见性
```

**同步器依赖内部的同步队列（一个FIFO的双向队列）来完成同步状态管理**，当前线程获取同步状态失败时同步器会将当前线程以及等待状态（独占或共享）构造成一个节点，并将其加入同步队列并进行自旋，当同步状态释放时，会把首节点中的后继节点对应的线程唤醒，使其再次尝试获取同步状态。

![img](http://img.topjavaer.cn/img/aqs.png)

## 19、ReentrantLock是如何实现可重入性的

ReentrantLock内部自定义了同步器sync，在加锁的时候通过CAS算法，将线程对象放进一个双向链表中，在每次获得锁的时候，检查当前维护的那个线程ID和当前请求的线程ID是否一致，如果一致，同步状态加1，表示锁被当前线程获取了多次。

```java
final boolean nonfairTryAcquire(int acquires) {
    final Thread current = Thread.currentThread();
    int c = getState();
    if (c == 0) {
        if (compareAndSetState(0, acquires)) {
            setExclusiveOwnerThread(current);
            return true;
        }
    }
    else if (current == getExclusiveOwnerThread()) {
        int nextc = c + acquires;
        if (nextc < 0) // overflow
            throw new Error("Maximum lock count exceeded");
        setState(nextc);
        return true;
    }
    return false;
}
```

## 20、锁的分类

### 20.1、公平锁和非公平锁

* **公平锁**：获取不到锁的时候，会自动加入队列，**等待线程释放后，队列的第一个线程获取锁**。
* **非公平锁**：获取不到锁的时候，会自动加入队列，**等待线程释放锁后，所有等待的线程同时去竞争**。

按照**线程访问顺序获取**锁，**synchronized是非公平锁，Lock默认是公平锁**，可以设置为非公平锁，**公平锁会影响性能**。

```java
public ReentrantLock() {
    sync = new NonfairSync();
}
public ReentrantLock(boolean fair) {
    sync = fair ? new FairSync() : new NonfairSync();
}
```

### 20.2、共享式和独占式锁

* **独占锁**：独占锁也叫排他锁,是指**该锁一次只能被一个线程所持有**。

* **共享锁**：**共享锁是指该锁可被多个线程所持有**。

共享式和独占式的主要区别在于：**同一时刻独占式只能有一个线程可以获取同步状态，而共享式在同一时刻可以有多个线程获取同步状态**。例如在读操作时，可以有多个线程同时进行，而写操作同一时刻只能有一个线程进行，其他线程会被阻塞。

### 20.3、悲观锁和乐观锁

**悲观锁：**每次访问资源都会加锁，执行完同步代码释放锁。**synchronized和ReentrantLock都属于悲观锁**。

**乐观锁：**不会锁定资源，**所有的线程都能访问并修改同一个资源**，如果没有冲突就修改成功并退出，否则就会继续循环尝试。乐观锁最常见的实现就是CAS。

**适用场景：**

* 悲观锁适合**写操作多**的场景。
* 乐观锁适合**读操作多**的场景，不加锁可以提升读操作的性能。

## 21、乐观锁有什么问题

乐观锁**避免了悲观锁独占对象的问题，提高了并发性能**，但也有缺点：

* 乐观锁只能保证一个共享变量的操作。
* 长时间自旋可能导致开销大。假如CAS长时间不成功而一直自旋，会给CPU带来很大开销。
* ABA原理：CAS是通过**对比内存值和期望值是否一致**来判断是否被修改过，但是会有以下问题：假设内存值原来是A，被一条线程修改成了B，现在又被修改成了A，此时CAS会认为内存值并没有发生改变。可以引入版本号解决这个问题，每次变量更新都把版本号加一。

## 22、什么是CAS

CAS全称是**Compare and Swap**，比较与交换，**是乐观锁的主要实现方式**。CAS在**不使用锁的情况下实现多线程的变量同步**。ReentrantLock内部的AQS和原子类内部都使用了CAS。

CAS算法需要三个操作数：

* **需要读写的内存值V**；
* **进行比较的内存值A**；
* **要写入的新值B**；

**只有V的值等于A时，才会使用原子方式用新值B更新V的值，否则会继续重试，直到成功更新值。**

以AutomicInteger为例，AutomicInteger的getAndIncrement()方法底层就是CAS实现，关键代码是compareAndSwapInt(obj, offset, expect, update) ，其含义就是，如果obj 内的value 和expect 相等，就证明没有其他线程改变过这个变量，那么就更新它为update ，如果不相等，那就会继续重试直到成功更新值。

## 23、CAS存在的问题

* ABA问题：CAS需要在操作值的时候检查内存值是否发生变化，没有发生变化的时候才会更新内存值。但是如果内存值原来是A，后来变成了B，然后又变成了A，此时CAS就会认为值没有发生变化，但是实际上是有变化的。ABA问题的解决思路就是在变量前添加版本号，变量每更新一次版本号就加1，这样变化过程就从A-B-A变成了1A-2B-3A。
* 循环时间长，开销大。CAS操作如果长时间不成功，就会一直自旋，导致CPU开销较大。
* 只能保证一个变量的原子操作。对一个共享变量执行操作时，CAS能够保证原子操作。但是对多个共享变量操作时，CAS无法保证操作的原子性。

## 24、并发工具

在JDK的并发包里提供了几个非常有用的并发工具类。**CountDownLatch、CyclicBarrier和Semaphore工具类提供了一种并发流程控制的手段。**

### 24.1、CountDownLatch

CountDownLatch用于**某个线程等待其他线程执行完任务后再执行**，类似于Thread.join()。常见的应用场景是同时开启多个线程共同执行某个任务，等到所有线程执行完再执行特定操作，如汇总统计结果等。

```java
public class CountDownLatchDemo {
    static int N = 4;
    static CountDownLatch latch = new CountDownLatch(N);

    public static void main(String[] args) throws InterruptedException{
        for (int i = 0; i < N; i++) {
            new Thread(new MyThread()).start();

        }
        latch.await(1000, TimeUnit.MILLISECONDS);
        System.out.println("task finished");
    }

    static class MyThread implements Runnable {

        @Override
        public void run() {
            System.out.println(Thread.currentThread().getName() + "start working");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            } finally {
                latch.countDown();
            }
        }
    }
}
```

运行结果：

```java
Thread-0start working
Thread-2start working
Thread-3start working
Thread-1start working
task finished
```

### 24.2、CyclicBarrier

CyclicBarrier（**同步屏障**），用于**一组线程互相等待某个状态，然后这组线程再同时执行**。

```java
public CyclicBarrier(int parties, Runnable barrierAction) {
}
public CyclicBarrier(int parties) {
}
```

参数parties指让多少个线程或者任务等待至某个状态；参数barrierAction为当这些线程都达到某个状态时会执行的内容。**当所有的线程都到达barrier状态后，会从线程组中选择一个线程去执行Runnable**。

```java
public class CyclicBarrierDemo {
    private static final int threadCount = 10;
    private static final CyclicBarrier cyclicBarrier = new CyclicBarrier(5);

    public static void main(String[] args) throws InterruptedException{
        ExecutorService threadPool = Executors.newFixedThreadPool(10);

        for (int i = 0; i < threadCount; i++) {
            final int threadNum = i;
            Thread.sleep(1000);
            threadPool.execute(() -> {
                try {
                    test(threadNum);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (BrokenBarrierException e) {
                    e.printStackTrace();
                }
            });
        }
        threadPool.shutdown();
    }

    public static void test(int threadNum) throws InterruptedException, BrokenBarrierException {
        System.out.println("threadNum" + threadNum + "is ready");
        try {
            cyclicBarrier.await(60, TimeUnit.SECONDS);
        } catch (Exception e) {
            System.out.println("-----CyclicBarrierException------");
        }
        System.out.println("threadNum" + threadNum + "is finished");
    }
}
```

运行结果如下：

```java
threadnum:0is ready
threadnum:1is ready
threadnum:2is ready
threadnum:3is ready
threadnum:4is ready
threadnum:4is finish
threadnum:3is finish
threadnum:2is finish
threadnum:1is finish
threadnum:0is finish
threadnum:5is ready
threadnum:6is ready
...
```

**当四个线程都到达barrier状态后，会从四个线程中选择一个线程去执行Runnable**。

### 24.3、CyclicBarrier和CountDownLatch的区别

CyclicBarrier和CountDownLatch**都能实现线程间的等待**。

CountDownLatch用于某个线程等待其他线程执行完任务之后再执行，而CyclicBarrier用于一组线程互相等待达到某个状态，然后这组线程再同时执行。**CountDownLatch的计数器只能用一次，而CyclicBarrier的计数器可以使用reset进行重置**，可以用于更加的复杂的业务场景。

### 24.4、Semaphore

Semaphore类似于锁，**用于控制同时访问特定资源的线程数，控制并发线程数**。

```java
public class SemaphoreDemo {

    public static void main(String[] args) {
        final int N = 7;
        Semaphore s = new Semaphore(3);
        for (int i = 0; i < N; i++) {
            new Worker(s, i).start();
        }
    }

    static class Worker extends Thread {

        private Semaphore s;
        private int num;
        public Worker(Semaphore s, int num) {
            this.s = s;
            this.num = num;
        }

        @Override
        public void run() {
            try {
                s.acquire();
                System.out.println("worker" + num + "is using the machine");
                Thread.sleep(1000);
                System.out.println("worker" + num + "finish use the machine");
                s.release();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

运行结果如下，可以看出并非按照线程访问顺序获取资源的锁：

```java
worker0 using the machine
worker1 using the machine
worker2 using the machine
worker2 finished the task
worker0 finished the task
worker3 using the machine
worker4 using the machine
worker1 finished the task
worker6 using the machine
worker4 finished the task
worker3 finished the task
worker6 finished the task
worker5 using the machine
worker5 finished the task
```

## 25、原子类

### 25.1、基本类型原子类

**使用原子的方式更新基本类型**：

* AutomicInteger：整型原子类
* AutomicLong：长整型原子类
* AutomicBoolean：布尔型原子类

AutomicInteger的常用方法：

```java
public final int get() //获取当前的值
public final int getAndSet(int newValue)//获取当前的值，并设置新的值
public final int getAndIncrement()//获取当前的值，并自增
public final int getAndDecrement() //获取当前的值，并自减
public final int getAndAdd(int delta) //获取当前的值，并加上预期的值
boolean compareAndSet(int expect, int update) //如果输入的数值等于预期值，则以原子方式将该值设置为输入值（update）
public final void lazySet(int newValue)//最终设置为newValue,使用 lazySet 设置之后可能导致其他线程在之后的一小段时间内还是可以读到旧的值。
```

AtomicInteger 类主要利用 **CAS (compare and swap) 保证原子操作**，从而避免加锁的高开销。

### 25.2、数组类型原子类

**使用原子方式更新数组里的每个元素**：

* AutomicIntegerArray：整型数组原子类
* AutomicLongArray：长整型数组原子类
* AutomicBooleanArray：布尔型数组原子类

AutomicIntegerArray的常用方法：

```java
public final int get(int i) //获取 index=i 位置元素的值
public final int getAndSet(int i, int newValue)//返回 index=i 位置的当前的值，并将其设置为新值：newValue
public final int getAndIncrement(int i)//获取 index=i 位置元素的值，并让该位置的元素自增
public final int getAndDecrement(int i) //获取 index=i 位置元素的值，并让该位置的元素自减
public final int getAndAdd(int i, int delta) //获取 index=i 位置元素的值，并加上预期的值
boolean compareAndSet(int i, int expect, int update) //如果输入的数值等于预期值，则以原子方式将 index=i 位置的元素值设置为输入值（update）
public final void lazySet(int i, int newValue)//最终 将index=i 位置的元素设置为newValue,使用 lazySet 设置之后可能导致其他线程在之后的一小段时间内还是可以读到旧的值。
```

### 25.3、引用类型原子类

* **AutomicReference**：引用类型原子类
* **AutomicStampReference**：带有版本号的引用类型原子类。该类**将整数值和原子类型关联起来**，可用于解决原子类型的更新数据和数据的版本号，**可以解决使用CAS进行原子更新时的ABA问题**。
* **AutomicMarkableReference**：**原子更新带有标记的引用类型**，该类将boolean标记和引用关联起来。

## 26、为什么要使用Executor线程池框架

* 每次执行任务都需要new Thread()创建线程，比较消耗性能。**创建线程是一个非常耗时、耗资源的过程**。
* 调用new Thread()创建的**线程缺乏管理**，可以无限制的创建线程，线程之间的相互竞争会导致过多占用系统资源而造成系统瘫痪。
* 直接使用new Thread()启动的线程**不利于扩展**。比如定时执行、定期执行、定时定期执行、执行中断等都不好实现。

## 27、如何停止一个正在运行的线程

* **使用共享变量的方式**。共享变量可以被执行相同任务的线程用来作为是否停止的信号，通知停止线程的执行。
* **使用interrupt方法终止线程**。当一个线程被阻塞，处于不可运行状态，即使主程序将该线程的共享变量设置为true，但该线程此时根本无法检查循环标志，当然也就无法立即中断。此时可以使用Thread.interrupt()方法，虽然这个方法不会中断一个正在运行的线程，但是它可以使一个被阻塞的线程抛出中断异常，从而使线程提前结束阻塞状态。

## 28、什么是Daemon线程

后台（Daemon）线程，是**指在程序运行时在后台提供通用服务的线程**，它并不属于程序的不可或缺的部分。当所有非后台线程结束后，程序也就终止了，同时会杀死进程中所有的后台线程。反过来说就是，只要有任何非后台线程还在运行，程序就不会终止。**必须在程序启动之前调用setDaemon()才能将其设置为后台线程。**

## 29、SynchronizedMap和ConcurrentHashMap的区别

**SynchronizedMap采用锁住整张表的方式来保证线程安全**，因此每次只能有一个线程来访问map。

**ConcurrentHashMap采用CAS和synchronized共同保证并发安全**。数据结构采用数组+链表/红黑树。synchronized只锁定当前链表或红黑树的首节点，支持并发访问、修改。另外ConcurrentHashMap采用了不同的迭代方式。<u>当iterator创建后集合再发生改变，不再是抛出ConcurrentModificationException异常，而是在改变时new新的数据从而不影响其他数据，iterator完成后，在将头指针替换成新的数据，这样iterator线程可以使用旧的数据，写的操作也能够并发执行。</u>

## 30、怎么判断线程池的任务是否执行完了

* **使用线程池的原生函数isTerminated()**

  executor提供了一个原生函数isTerminated()来判断线程池中的任务是否全部完成。如果全部完成返回True，否则返回false。

* **使用重入锁，维持一个公共计数**

  所有的普通任务维持一个计数器，当任务完成时计数器加1（这里要加锁），当计数器的值等于任务数时，这是所有的任务都执行完毕了。

* **使用CountDownLatch**

  原理和第二种方法类似，给CountDownLatch一个计数值，任务执行完毕之后，调用countDown()方法将计数值减一。最后执行的任务在调用方法的开始调用await()方法，这样整个任务就会阻塞，直到这个计数值为0，才会继续执行。

  这种方式的缺点就是需要提前直到任务数。

* **submit向线程池提交任务，使用Future判断任务执行状态**

  使用submit向线程池提交任务和Executor不同，submit会有一个Future类型的返回值。通过future.isDown()判断任务是否执行完成。

## 31、什么是Future

在并发编程中，不管是继承Thread类还是实现Runnable接口，都无法获得之前的执行结果。通过实现Callable接口，并用Future可以来接收多线程的执行结果。

**Future表示一个可能但还没有完成的异步任务的执行结果，针对这个任务，可以使用Callable以便在任务执行完成或失败后执行相应的操作。**

举个例子：比如去吃早点时，点了包子和凉菜，包子需要等3分钟，凉菜只需1分钟，如果是串行的一个执行，在吃上早点的时候需要等待4分钟，但是因为你在等包子的时候，可以同时准备凉菜，所以在准备凉菜的过程中，可以同时准备包子，这样只需要等待3分钟。Future就是后面这种执行模式。

**Future接口主要包含5个方法：**

* **get()**方法可以当任务结束后返回一个结果，如果调用时，工作还没有结束，则会阻塞线程，直到任务执行完毕
* **get(long timeout,TimeUnit unit)**做多等待timeout的时间就会返回结果
* **cancel(boolean mayInterruptIfRunning)**方法可以用来停止一个任务，如果任务可以停止（通过mayInterruptIfRunning来进行判断），则可以返回true，如果任务已经完成或者已经停止，或者这个任务无法停止，则会返回false。
* **isDone()**方法判断当前方法是否完成
* **isCancel()**方法判断当前方法是否取消

# 四、JVM

## 1、JVM内存结构

Java虚拟机的内存结构分五个部分

* **程序计数器**
* **Java虚拟机栈**
* **本地方法栈**
* **堆**
* **方法区**

![jvm-memory-structure](https://camo.githubusercontent.com/4293d2412efb0751ce2d0219d38801767632a24951c00a9b7227b816ef3eb075/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6a766d2d6d656d6f72792d7374727563747572652e6a7067)

> JDK 1.8 同 JDK 1.7 比，最大的差别就是：元数据区取代了永久代。元空间的本质和永久代类似，都是对 JVM 规范中方法区的实现。不过元空间与永久代之间最大的区别在于：元数据空间并不在虚拟机中，而是使用本地内存。

### 1.1、程序计数器（PC寄存器）

程序计数器是一块较小的内存空间，是**当前线程正在执行的那条字节码指令的地址**。若当前线程正在执行的是一个本地方法，则程序计数器为undefined。

#### 1.1.1、程序计数器的作用

* 字节码解释器通过**改变程序计数器来依次读取指令**，从而实现代码的流程控制。
* 在多线程情况下，**程序计数器记录的是当前线程执行的位置**，从而当线程切换回来时就知道上次线程执行到哪了。

#### 1.1.2、程序计数器的特点

* 是一个**比较小的内存空间**。
* **线程私有**，每条线程都有一个自己的程序计数器。
* 生命周期：**随着线程的创建而创建，随着线程的结束而销毁**。
* 是**唯一一个不会出现OutOfMemoryError的内存区域**。

### 1.2、Java虚拟机栈（Java栈）

Java虚拟机栈是**描述Java方法运行过程**的内存模型。

Java虚拟机栈会为每一个即将运行的Java程序创建一个称为“栈帧”的区域，用于存放Java方法在运行过程中的一些信息，比如 

* 局部变量表
* 操作数栈
* 动态链接
* 方法出口信息
* ......

![jvm-stack](https://camo.githubusercontent.com/d589134fdf31b594493687a27792675fae0973dc444f60a6d4f147bd80deaaef/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6a766d2d737461636b2e6a7067)

#### 1.2.1、出栈入栈过程

当方法需要创建局部变量时，就**将局部变量的值存入栈帧中的局部变量表**中。

Java虚拟机栈的**栈顶是当前正在执行的活动栈**，也就是当前正在执行的方法，PC寄存器（程序计数器）也会指向这个地址。<u>只有这个活动的栈帧的本地变量可以被操作数栈使用</u>，当在这个栈中调用另一种方法，与之对应的栈帧就会被创建，新创建的栈帧压入栈顶，变成当前的活动栈帧。

方法结束后，当前栈帧被移出，栈帧的返回值变成新的活动栈中操作数栈的一个操作数。如果没有返回值，那么新的活动栈帧中操作数栈的操作数没有变化。

> 由于Java虚拟机栈是与线程对应的，数据不是线程共享的（也就是线程私有的），因此不需要考虑数据不一致的问题，也不会存在同步锁的问题。

#### 1.2.2、局部变量表

定义为一个数字数组，**主要用于存储方法参数、定义在方法体内部的局部变量，数据类型包含各种基本数据类型，对象引用以及return address类型**。

局部变量表容量大小是在编译器确定下来的。最基本的存储单元是slot，32位占用一个slot，64位（long和double）占用两个slot。

对于slot的理解：

* JVM虚拟机会**为每个局部变量表中的每个slot都分配一个访问索引**，通过这个索引即可成功的访问到局部变量表中指定的局部变量值。
* 如果当前帧是由构造方法或实例方法创建的，那么该对象引用this，会存放在index为0的slot处，其余的参数表顺序继续排列。
* 栈帧中的局部变量表中的槽位是可以重复的，如果一个局部变量过了其作用域，那么其作用域之后声明的新的局部变量就有可能**复用过期的局部变量的槽位**，从而达到节省资源的目的。

在栈帧中，**与性能调优关系最密切的部分，就是局部变量表**，方法执行时，虚拟机使用局部变量表完成方法的传递，局部变量表中的变量也是重要的垃圾回收根节点，只要被局部变量表中直接或间接引用的对象都不会回收。

#### 1.2.3、操作数栈

* **栈顶缓存技术**：由于**操作数是存储在内存中**，频繁的执行内存读写操作影响执行速度，***<u>将栈顶元素全部缓存在物理CPU的寄存器中</u>***，以此降低对内存的读写次数，提升执行引擎的执行效率。
* 每一个操作数栈都会有一个明确的栈的深度，用于存储数值，最大深度在编译时就已经定义好。32bit类型占用一个栈单位深度，64bit类型占用两个栈单位深度操作数栈。
* 并非采用索引的方式进行数据访问，而是**采用标准的入栈、出栈方式访问数据**。

#### 1.2.4、方法的调用

* **静态链接：**当一个字节码文件被装载到JVM的内部时，如果被调用方法在**编译期可知，并且在运行期间保持不变**，在这种情况下**将调用方法的符号引用转为直接引用的过程称为静态链接**。
* **动态链接：**如果被调用方法在**编译期间不可知，只能在运行期间将调用方法的符号引用转为直接引用**，这种引用转换过程具备动态性，因此称为动态链接。  
* **方法绑定**
  * **早期绑定：**被调用的目标方法在编译时可知，并且在运行期间保持不变。
  * **晚期绑定：**被调用的目标方法无法在编译期确定，只能在运行期间根据实际的类型绑定相关的方法。
* **非虚方法：**如果方法**在调用期间就确定了具体的版本，并且在运行期间保持不变**，成该方法为非虚方法。静态方法、私有方法、final方法、实例构造器、父类方法都是非虚方法，除了这些以外都是虚方法。
* **虚方法表：**在面向对象编程中，会频繁的使用动态分配，如果每次动态分配的过程都要在类的方法元数据中搜索合适的目标的话，就可能影响到执行效率，因此为了提高性能**，JVM在类的方法区建立了一个虚方法表，使用索引表来代替查出**。
  * 每个类都有一个虚方法表，表中存放着各个方法的实际入口。
  * 虚方法表会在类加载的链接阶段被建立，并开始初始化，类的变量初始值准备完成后，JVM会把该类的方法也初始化完毕。
* **方法重写的本质**
  * 找到操作数栈顶的第一个元素所执行的对象的实际类型，记作C。如果在类型C中找到与常量池中描述符和简单名称都相符的方法，则进行访问权限校验。
  * 如果通过则返回这个方法的直接引用，查找过程结束，如果不通过，则返回java.lang.IllegalAccessError异常
  * 否则，按照继承关系从下往上以此对C的各个父类进行上一步的搜索和验证过程。
  * 如果始终没有找到合适的方法，则抛出java.lang.AbstractMethodError异常。

**Java中任意一个方法都具备虚函数的特征（运行期确认、具备晚期绑定的特点）**，C++中则使用virtual关键字来显式定义。如果在Java程序中不希望某个方法具有虚函数的特征，可以使用final关键字来标记这个方法。

#### 1.2.5、Java虚拟机栈的特点

* **运行速度特别快**，仅仅次于寄存器。
* **局部变量表随着栈帧的创建而创建，它的大小在编译时确定**，创建时只需要分配事先规定的大小即可。在方法的运行过程中，局部变量表的大小不会改变。
* Java虚拟机栈会出现两种异常：StackOverFlowError和OutOfMemoryError异常。
  * **StackOverFlowError**：当Java虚拟机栈的大小不允许动态扩展，那么***当线程请求栈的深度超过当前Java虚拟机栈的最大深度***时，会抛出StackOverFlowError异常。
  * **OutOfMemoryError：**若允许动态扩展，则在线程请求扩展时内存用完了，无法再动态扩展时，此时会抛出OutOfMemoryError异常。
* **Java虚拟机栈也是线程私有的**，随着线程的创建而创建，随着线程的结束而销毁。
* 出现StackOverFlowError时，内存可能还有很多。

### 1.3、本地方法栈（C栈）

本地方法栈是**为JVM运行Native方法准备的空间**，由于Native中很多方法是用C语言写的，所有也称为C栈。它与Java虚拟机栈实现的功能类似，只不过本地方法栈是描述本地方法运行过程的内存模型。

#### 1.3.1、栈帧的变化过程

本地方法被执行时，在本地方法栈中也会创建一块栈帧，用于**存放方法的局部变量表、操作数栈、动态链接、方法出口信息**等。

方法执行结束后，相应的栈帧也会出栈，释放内存空间。也会抛出StackOverFlowError和OutOfMemoryError异常。

> 如果Java虚拟机本身不支持Native方法，或者本身不依赖于传统栈，那么可以不提供本地方法栈。如果支持本地方法栈，这个栈一般会在线程创建的时候按线程分配。

### 1.4、堆

**堆是用来存放对象的内存空间，几乎所有的对象都存储在堆中。**

![image-20240512201711474](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240512201711474.png)

#### 1.4.1、堆的特点

* **线程共享**，整个Java虚拟机中只有一个堆，所有的线程都访问同一个堆，而程序计数器、Java虚拟机栈、本地方法栈都只有一个。
* 在虚拟机**启动时创建**。
* 是**垃圾回收**的主要场所。
* 堆按内存划分可分为**新生代（Eden区、From Survivor、To Survivor）、老年代**。
* Java虚拟机规定，堆可以处于**物理上不连续**的内存空间，但在**逻辑上是连续的**。
* 关于Survivor s0、s1区：复制之后有交换，谁空谁是to。

***<u>不同的区域存放不同生命周期的对象</u>***，这样可以根据不同的区域使用不同的垃圾回收算法，更具有针对性。

堆的**大小既可以固定也可以扩展**。对于主流的虚拟机，堆的大小是可扩展的，因此当线程请求分配内存时，如果堆已满，且内存无法再扩展时，就会抛出OutOfMemoryError异常。

> Java堆所使用的内存并不需要保证是连续的。而由于堆是被所有线程所共享的，所以对它访问需要注意同步问题，方法和对应的属性都需要保持一致性。

#### 1.4.2、新生代和老年代

- 老年代比新生代生命周期长。
- 新生代与老年代空间默认比例 `1:2`：JVM 调参数，`XX:NewRatio=2`，表示新生代占 1，老年代占 2，新生代占整个堆的 1/3。
- HotSpot 中，Eden 空间和另外两个 Survivor 空间缺省所占的比例是：`8:1:1`。
- **几乎所有的 Java 对象都是在 Eden 区被 new 出来的**，Eden 放不了的大对象，就直接进入老年代了。

#### 1.4.3、对象分配过程

* new的对象先放在Eden区，大小有限制。
* 如果创建过程中Eden区满了，就会出发Minor GC，将Eden中不再被其他对象引用的对象销毁，再加载新的对象到Eden区中，特别注意的是Survivor区满之后是不会出发Minor GC的，而是Eden空间填满了，Minor GC才顺便清理Survivor区。
* 将Eden区中剩余的对象移至Survivor区。
* 再次触发垃圾回收，**将上次Survivor下来的，放在Survivor0区，如果没有回收，就会放到Survivor1区**。
* 再次经历垃圾回收，**又会将幸存者重新放回Survivor0区**，以此类推。
* **默认15次循环**，超过15次，则会将幸存区中幸存下来的转到老年区，JVM参数设置次数：-XX:MaxTenuringThreshold=N 进行设置
* 频繁在新生区收集，很少在老年区收集，几乎不在永久区/元空间收集。

#### 1.4.4、Full GC/Major GC触发条件

* 显式调用system.gc()、老年代的空间不够、方法区的空间不够等都会触发Full GC，同时对老年代和新生代回收，**Full GC的STW时间最长，应该要避免**。

  > **stop the world指的是GC事件发生过程中，会产生应用程序的停顿。**停顿产生时整个应用程序线程都会被暂停，没有任何响应, 有点像卡死的感觉，这个停顿称为STW。

* 在出现Major GC之前，会先触发Minor GC，如果老年代的空间还是不够就会触发Major GC，STW的时间长于Minor GC。

#### 1.4.5、逃逸分析

> 逃逸分析就是，**当一个对象被new出来之后，它可能被外部所调用，如果是作为参数传递到外部了**，就称之为方法逃逸。

* **当一个对象在方法中被定义后，它可能被外部方法所引用，如作为调用参数传递到其他地方中，称为`方法逃逸`。**
* **再如赋值给类变量或可以在其他线程中访问的实例变量，称为`线程逃逸`。**

* 标量替换
  * **标量即不可再分解的量**，Java中的**基本数据类型就是标量**，与之对立的是**可以再进一步分解的量，称之为聚合量**。而在Java中对象就是可以再进一步分解的聚合量。
  * 替换过程，通过逃逸分析确认对象是否可以被外部访问，并且对象可以进一步分解时，JVM不会创建该对象，而会将该对象成员变量分解若干个被这个方法使用的成员变量所替代。这些代替的成员变量在栈帧或寄存器上分配空间。
* **对象和数组并非都是在堆上分配内存的。**
* 这是一种可以**有效减少Java内存堆分配压力的分析算法**，**<u>*通过逃逸分析，Java Hotspot编译器能够分析出一个新的对象的引用的使用范围*</u>**，从而决定是否要将这个对象分配到内存上。
* 使用逃逸分析，编译器可以对代码做如下优化：
  * **同步省略：**如果一个对象被发现只能从一个线程被访问到，那么对于这个对象的操作可以不考虑同步。
  * **将堆分配转化为栈分配：**如果一个对象在子程序中被分配，要使指向该对象的引用永远不会逃逸，对象可能是栈分配的候选，而不是堆分配。
  * **分离对象或标量替换：**有的对象可能不需要作为一个连续的内存结构也能被访问到，那么对象的部分（或者全部）可以不存储在内存中，而是存储在CPU寄存器中。

```java
public static StringBuffer createStringBuffer(String s1, String s2) {

    StringBuffer s = new StringBuffer();

    s.append(s1);

    s.append(s2);

    return s;
}
```

s 是一个方法内部变量，上边的代码中直接将 s 返回，这个 StringBuffer 的对象有可能被其他方法所改变，导致它的作用域就不只是在方法内部，即使它是一个局部变量，但还是逃逸到了方法外部，称为`方法逃逸`。

还有可能被外部线程访问到，譬如**赋值给类变量或可以在其他线程中访问的实例变量**，称为`线程逃逸`。

* 在编译期间，如果 JIT 经过逃逸分析，发现有些对象没有逃逸出方法，那么有可能堆内存分配会被优化成栈内存分配。
* jvm 参数设置，`-XX:+DoEscapeAnalysis` ：开启逃逸分析 ，`-XX:-DoEscapeAnalysis` ： 关闭逃逸分析
* 从 jdk 1.7 开始已经默认开始逃逸分析。

#### 1.4.6、TLAB

* **TLAB全称是Thread Local Allocation Buffer，即线程本地分配缓存区**，是**属于Eden区**的，这是一个线程专用的内存分配区域，线程私有的，默认开启的（当然也不是绝对的，也要看那种类型的虚拟机）。
* 堆是全局共享的，在同一时间，<u>可能会有多个线程在堆上申请空间，但每次的对象分配需要同步的进行</u>（虚拟机采用 CAS 配上失败重试的方式保证更新操作的原子性）但是效率却有点下降。
* 所以<u>用 TLAB 来避免多线程冲突</u>，在**给对象分配内存时，每个线程使用自己的 TLAB，这样可以使得线程同步**，提高了对象分配的效率。
* 当然并不是所有的对象都可以在 TLAB 中分配内存成功，**如果失败了就会使用加锁的机制来保持操作的原子性**。
* `-XX:+UseTLAB `使用 TLAB，`-XX:+TLABSize` 设置 TLAB 大小。

#### 1.4.7、四种引用方式

* **强引用：** **创建一个对象并把这个对象赋给一个引用变量**，普通new出来的对象的变量引用都是强引用，**有引用变量指向的时候永远不会被垃圾回收**，JVM即使抛出OOM，可以将引用赋值给null，那么它所指向的对象将会被垃圾回收。
* **软引用：**如果一个对象具有软引用，如果内存空间够，垃圾回收器就不会回收它，如果内存空间不足，垃圾回收器就会回收这些对象的内存。**只要垃圾回收器不回收内存，这些对象就可以被程序使用**。
* **弱引用：**非必需对象，当JVM进行垃圾回收时，**无论内存空间是否充足，都会回收被弱引用关联的对象**。
* **虚引用：**虚引用并不会决定对象的生命周期，当一个对象持有虚引用时，那么它就<u>和没有引用一样</u>，**任何时候都可能被垃圾回收器回收**。

### 1.5、方法区

Java虚拟机规范中定义**方法区是堆的一个逻辑部分**。方法区存放以下信息：

* **已经被虚拟机加载的类信息。**
* **常量**
* **静态变量**
* **即时编译器编译后的代码。**

#### 1.5.1、方法区的特点

* **线程共享：**方法区和堆的逻辑一样，因此是线程共享的，整个虚拟机中只有一个方法区。
* **永久代：** **方法区中的信息一般需要长期存储的**，而且又是堆的逻辑分区，因此用堆的划分方法，把方法区称为“永久代”。
* **内存回收效率低：**方法区中的信息一般需要长期存在，回收一遍后可能只有少量信息有效。**主要回收目标是：对常量池的回收，对类型的卸载**。
* Java虚拟机规范方法对方法区的要求比较宽松，和堆一样，**允许固定大小，也允许自动扩展，同时也允许没有垃圾回收**。

#### 1.5.2、运行时常量池

**方法区中存放：类信息、常量、静态变量、即时编译器编译后的代码。**常量存放在运行时常量池中。

当类被Java虚拟机加载后，.class文件中的常量就存放在方法区的运行时常量中。而**在运行期间，可以向常量区添加新的常量**，比如String类的intern()方法就能在运行期间向常量池中添加字符串常量。

![jvm-runtime-constant-pool](https://camo.githubusercontent.com/99e3c3b90bdc79dc06f2e946c94c3e4e1db6619708d9304b10044e042bea05d9/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6a766d2d72756e74696d652d636f6e7374616e742d706f6f6c2e706e67)

### 1.6、直接内存（堆外内存）

直接内存是指**Java虚拟机之外的内存**，但也可能被Java虚拟机使用。

#### 1.6.1、操作直接内存

在NIO中引入了一种通道与缓冲的IO方式。它可以**通过调用本地方法直接调用Java虚拟机之外的内存，然后通过一个存储在堆中的DirectByteBuffer对象直接操作该内存**，而无需将外部内存中的数据复制到堆中再进行操作，从而提高数据操作的效率。

直接内存的大小不受Java虚拟机的控制，但既然是内存，当内存不足时就会抛出OutOfMemoryError异常。

#### 1.6.2、直接内存和堆内存的比较

* 直接内存申请空间**耗费更高的性能**。
* 直接内存读取IO的**性能要高于普通的堆内存**。
* 直接内存作用链：**本地IO--》直接内存--》本地IO**。
* 堆内存作用链：**本地IO--》直接内存--》非直接内存--》直接内存--》本地IO**。

> 服务器管理员在配置虚拟机参数时，会根据实际内存设置`-Xmx`等参数信息，但经常忽略直接内存，使得各个内存区域总和大于物理内存限制，从而导致动态扩展时出现`OutOfMemoryError`异常。

![jvm-off-heap-memory](https://camo.githubusercontent.com/c0285d65423494262100533bf69f76d62b85252451b6da7a359d33fe92360000/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6a766d2d6f66662d686561702d6d656d6f72792e706e67)

## 2、HotSpot 虚拟机对象

### 2.1、对象的内存分布

在HotSpot虚拟机中，对象的内存分布分为以下3块区域：

* **对象头（Header）**
* **实例数据（Instance Data）**
* **对齐填充（Padding）**

![object-memory-layout.png](https://camo.githubusercontent.com/7ed6e871a204928e453c8c7aa2d42186ebd43517d7787e2cbbfcc08bf88465de/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6f626a6563742d6d656d6f72792d6c61796f75742e706e67)

#### 2.1.1、对象头

**对象头记录了对象在运行过程中所需要使用的一些数据**。

* 哈希码
* GC分代年龄
* 锁状态标志
* 线程持有的锁
* 偏向线程ID
* 偏向时间戳

对象头可能还包含类型指针，通过该指针确定该对象属于哪一类。如果对象是一个数组，那么对象头中还包含数组长度。

#### 2.1.2、实例数据

**实例数据就是成员变量的值**，其中包括父类成员变量和本类成员变量。

#### 2.1.3、对齐填充

**用于确保对象的总长度为8字节的整数倍**。

HotSpot VM的**自动内存管理系统**规定对象的大小必须是8字节的整数倍。而对象头部分正好是8字节的整数倍（1倍或2倍），因此当对象实例数据部分没有对齐时，就需要通过对齐填充来补全。

> 对齐填充并不是必然存在，也没有特别的含义，它只是起到一个占位符的作用。

### 2.2、对象的创建过程

![new-instruction](https://camo.githubusercontent.com/89f9eb0dafc09c0eaf3ea6a88cbb30bc8447a0cb5779825928758b498afd1070/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6e65772d696e737472756374696f6e2e706e67)

* 首先检查这个指令的参数是否能在常量池中定位到一个类的符号引用

* 检查这个符号引用代表的类是否已被加载、解析和初始化过。如果没有，就先执行相应的类加载过程

* 类加载检查通过后，接下来虚拟机将为新生对象分配内存。

* 内存分配完成之后，虚拟机将分配到的内存空间（但不包括对象头）都初始化为零值。

* 接下来设置对象头，对象头里包含了对象是哪个类的实例、如何才能找到类的元数据信息、对象的哈希码、对象的 GC 分代年龄等信息。

#### 2.2.1、类加载检查

虚拟机在解析.class文件时，遇到new指令时会**首先检查常量池中是否存在这个类的符号引用**，并且检查**这个符号引用所代表的类是否已经被加载过、解析过或初始化过**。如果没有，那么必须先执行相应的类加载过程。

#### 2.2.2、为新生对象分配内存

**对象所需的内存大小在类加载完成后便可确认**，接下来从堆内存中划分一小块相应内存空间给新的对象。分配堆中内存有两种方式：

* **指针碰撞：**

  如果Java堆中内存绝对规整（说明采用的是“复制算法”或者“标记整理法”），**空闲内存和已使用内存中间存在一个指针作为分界点指示器**，那么分配内存时只需要将指针向空闲内存挪动一段和对象大小相同的距离，这种分配内存的方法称为**“指针碰撞”**。

* **空闲列表：**

  如果Java堆中内存并不规整，**空闲内存和已使用内存空间互相交错**（说明使用的是“标记-清除”法，有碎片），此时设法简单进行指针碰撞，虚拟机需要维护一个列表，记录其中哪块内存块可用。**分配之时从空闲内存块中找到一个足够大的空闲内存块划分给对象实例**。

#### 2.2.3、初始化

分配完内存后，**为对象中的成员变量赋上初始值，设置对象头信息，调用对象的构造方法进行初始化。**

#### 2.2.4、将内存的地址赋值给引用变量obj

至此，整个对象的创建过程结束。

### 2.3、对象的访问方式

对象的存储空间都是在堆中分配的，但是对象的引用却是在堆栈中分配的。也就是说创建一个对象时两个地方都分配内存，在**堆中分配的内存是建立这个对象实际的内存，在堆栈中分配的内存实际上是指向这个堆对象的引用**。根据引用存放的地址类型不同，对象有不同的访问方式。

#### 2.3.1、句柄访问方式

堆中需要有一块叫做**句柄池**的内存空间，**句柄中包含了对象实例数据和类型数据的具体地址信息。**

引用类型的变量存放的是该对象的句柄地址（reference）。访问对象时，首先需要根据引用类型的变量找到该对象的句柄，然后根据**句柄中对象的地址**找到对象。

![image-20240122220309446](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240122220309446.png)

#### 2.3.2、直接指针访问方式

**引用类型的变量直接存放对象的地址**，从而不需要句柄池，通过引用能够直接访问对象。**但对象所在的内存空间需要额外的存储策略存储对象所属的类信息的地址**。

![direct-pointer](https://camo.githubusercontent.com/d68e35ab6006108355ae9bd3b08760cb9acea1438aa0b31a9eb771d659922fba/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6469726563742d706f696e7465722e6a7067)

HotSpot采用的是第二种方式，即直接指针方式来访问对象，只需要以此寻址操作，所以在性能上比句柄式访问快一倍的速度。但它需要额外的存储策略来存储对象在方法区中类信息的地址。

## 3、垃圾收集策略与算法

程序计数器、虚拟机栈、本地方法栈随线程而生，也随线程而灭。栈帧随着方法的开始而入栈，随着线程的结束而出栈。这几个区域的内存分配和回收都具有确定性，因此不需要过多考虑回收的问题，因为在方法或者线程结束时，对应的内存也就随着被回收了。

而对于**Java堆和方法区**，我们只有在程序运行期间才能知道会创建哪些对象，这部分的内存的分配和回收都是动态的，垃圾回收器所关注的就是这部分内存。

### 3.1、判断对象是否存活

若一个对象不被任何对象或变量引用，那么它就是无效对象需要被回收。

#### 3.1.1 引用计数法

**在对象头中维护着一个count计数器**，对象被引用一次计数器+1，若引用失效计数器-1，当计数器为0时，可以认为该对象为无效对象。

引用计数算法的实现很简单，判定效率也高，大部分情况下它是一个不错的算法。但是在主流的Java虚拟机中，没有选用引用计数算法来管理内存，主要是因为它**很难解决对象之间循环引用的问题**。在多线程环境下，引用计数变更也要进行昂贵的同步操作，性能较低。（虽然循环引用可以用Recycle算法来解决，但是在多线程环境下，引用计数变更也要进行昂贵的同步操作，性能较低，早期的编程会采用此算法）

> 举个栗子 👉 对象 objA 和 objB 都有字段 instance，令 objA.instance = objB 并且 objB.instance = objA，由于它们互相引用着对方，导致它们的引用计数都不为 0，于是引用计数算法无法通知 GC 收集器回收它们。

#### 3.1.2、可达性分析法

**所有和GC Roots直接或间接关联的对象都是有效对象，和GC Roots没有关联的都是无效对象。**

GC Roots是指：

* Java虚拟机栈（栈帧中的局部变量表）中引用的对象
* 本地方法栈中引用的对象
* 方法区中常量引用的对象
* 方法区中类静态属性引用的对象

GC Roots并不包含堆中对象所引用的对象，这样就不会有循环引用问题。

### 3.2、引用的种类

判断对象是否存活与引用有关，在JDK1.2中对于引用的定义很传统。一个对象只有引用和被引用两种状态。我们希望能描述这样一类对象：当内存空间足够时，则保留在内存中。当进行完垃圾收集后，内存空间还是很紧张时，可以考虑回收这些对象。很对系统的缓存功能都符合这种应用场景。

#### 3.2.1、强引用

**创建一个对象并把这个对象赋给一个引用变量**，类似 "`Object obj = new Object()`" 这类的引用，就是强引用，**只要强引用存在，垃圾收集器永远不会回收被引用的对象**。但是，如果我们**错误地保持了强引用**，比如：赋值给了 static 变量，那么对象在很长一段时间内不会被回收，会产生内存泄漏。

#### 3.2.2、软引用

**软引用是一种相对强引用弱化一些的引用**，可以让对象豁免一些垃圾收集，只有**当 JVM 认为内存不足时，才会去试图回收软引用指向的对象**。JVM 会确保在抛出 OutOfMemoryError 之前，清理软引用指向的对象。软引用通常用来**实现内存敏感的缓存**，如果还有空闲内存，就可以暂时保留缓存，当内存不足时清理掉，这样就保证了使用缓存的同时，不会耗尽内存。

#### 3.2.3、弱引用

弱引用的**强度比软引用更弱**一些。当 JVM 进行垃圾回收时，**无论内存是否充足，都会回收**只被弱引用关联的对象。

#### 3.2.4、虚引用

虚引用也称**幽灵引用或者幻影引用**，它是**最弱**的一种引用关系。一个对象是否有虚引用的存在，完全不会对其生存时间构成影响。它仅仅是提供了一种确保对象被 finalize 以后，做某些事情的机制，比如，通常用来做所谓的 Post-Mortem 清理机制。

### 3.3、回收堆中无效对象

**对于可达性分析中不可达的对象，也并不是没有存活的可能**。

#### 3.3.1、判定finalize()是否有必要执行

![img](https://camo.githubusercontent.com/92fc29f1c6eaed8b98a163804ffd0c6425d15fb6663aa8ac0917b5ae5f0846e4/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f66696e616c697a652d6d6574686f642d70726f636573732e6a7067)

**JVM会先判断该对象是否有必要执行finalize()方法**，如果对象没有覆盖finalize()方法，并且finalize()方法已经被虚拟机调用过，则可以认为“没有必要执行”，那么对象直接被回收。

如果判定对象有必要执行finalize()方法，则对象会被放进一个F-Queue队列中，虚拟机以较低的优先级执行这些finalize()方法，但不会确保所有的finalize()方法都会执行结束。如果finalize()方法出现耗时操作，虚拟机就直接停止指向该方法，将对象清除。

#### 3.3.2、对象重生或死亡

如果在执行finalize()方法时，将this赋给某一个引用，则该对象被重生了，否则将会被垃圾收集器清除。

> 任何对象的finalize()方法只会被系统调用一次，如果对象面临下一次回收，它的finalize()方法不会被执行，想继续在finalize()中自救就失效了。

### 3.4、回收方法区内存

方法区中存放着生命周期较长的类信息、常量、静态变量，每次垃圾收集器只回收少量垃圾，回收的类型包括：

* 废弃常量
* 无用的类

#### 3.4.1、判定废弃常量

**只要常量池中的常量没有被变量或对象引用，那么该常量就会被清除**。比如一个字符串常量“bingo”进入了常量池，但是当前系统没有任何一个String对象引用常量池中的常量“bingo”，也没有其他地方引用这个字面量，那么它将会被清理出常量池。

#### 3.4.2、判定无用的类

判定一个类是否是“无用的类”，条件较为苛刻。

* **该类的对象已被清除**
* **该类的classLoader已经被回收**
* **该类的java.lang.Class对象没有在任何地方被引用，无法在任何地方通过反射访问该类的方法。**

### 3.5、垃圾收集算法

学会了如何判定**无效对象、无用类、废弃常量**之后，剩余工作就是回收这些垃圾。常见的垃圾收集算法有以下几个：

#### 3.5.1、标记-清除算法

![img](https://camo.githubusercontent.com/f522d7c2d5d1282394944a8e2a745a3dc3916826cdeb267e66548687f545c4f0/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6d61726b2d616e642d73776565702e6a7067)

**标记**的过程就是，遍历所有的GC Roots，然后将所有GC Roots不可达的对象标记成不可存活的对象。

**清除**的过程就是，遍历堆中的所有对象，将标记的对象全部清除。

**缺点：**

* **效率问题**：标记和清除两个过程的效率都不高
* **空间问题**：标记清除之后会产生大量不连续的**内存碎片**，碎片太多可能会导致以后需要分配较大的对象时，无法找到足够的连续内存而不得不提前触发一次垃圾回收动作。

#### 3.5.2、复制算法（新生代）

![img](https://camo.githubusercontent.com/63a2c263e624b35640f7f49d67b0c25556516dc17985e3b5ea344c8ff52f81dd/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6d61726b2d616e642d636f70792e6a7067)

复制算法是为了解决以上的效率问题。**它将可用内存按照容量划分成大小相等的两块**，每次只使用一块，当这一块内存用完，需要进行垃圾收集时，就将存活的对象复制到另一块上，然后将第一块内存全部清除。

* **优点**：不会有内存碎片问题
* **缺点**：内存缩小为原来的一半，浪费空间

为了解决空间利用率问题，可以将内存分为三块：**Eden、From Survivor、To Survivor**，比例是8：1：1，每次只使用Eden和其中一块Survivor。回收时，将Eden和Survivor中存活的对象一次性复制到另一块Survivor上，最后清理掉Eden和刚才的Survivor空间，这样只有10%的空间被浪费。

但我们无法保证每次只有不多于10%的对象存活，当Survivor空间不够时，需要依赖其他内存（老年代）进行分配担保。

**分配担保：**为对象分配内存空间时，*<u>如果Eden+Survivor中空闲区域无法装下该对象，会触发Minor GC进行垃圾收集</u>*。但如果Minor GC过后依然有超过10%的对象存活，这样存活的对象会直接**通过分配担保机制进入老年代**，然后再将新对象存入Eden区。

#### 3.5.3、标记-整理算法（老年代）

![image-20240123110625942](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240123110625942.png)

**标记：**第一节阶段和“标记-清除算法”一样，均是遍历GC Roots中，然后**将存活的对象标记**。

**整理**：**移动所有的存活对象，然后按照内存地址依次排列**，然后将末端内存地址以后的内存全部回收。因此第二阶段才被称为整理阶段。

这是一种老年代的垃圾收集算法。老年代的对象一般寿命比较长，因此每次垃圾回收会有大量对象存活，如果采用复制算法，每次需要复制大量存活的对象，效率很低。

#### 3.5.4、分代收集算法

**根据对象存活周期的不同，将内存划分为几块。**一般是把 Java 堆分为新生代和老年代，针对各个年代的特点采用最适当的收集算法。

* **新生代**：复制算法
* **老年代**：标记-清除法、标记-整理法

## 4、HotSpot垃圾收集器

HotSpot虚拟机是Java虚拟机的一种。如果把JVM看作是一种执行规范，那么HotSpot就是该执行规范的一个实现。

HotSpot 虚拟机提供了多种垃圾收集器，每种收集器都有各自的特点，虽然我们要对各个收集器进行比较，但并非为了挑选出一个最好的收集器。我们选择的只是对具体应用最合适的收集器。

### 4.1、新生代垃圾收集器

#### 4.1.1、Serial垃圾收集器（单线程）

**只开启一个GC线程进行垃圾回收**，<u>*并且在垃圾收集期间，停止一切用户进程*</u>，即stop the world。

一般客户端应用**所需内存较小**，不会创建太多对象，而且**堆内存不大**，因此垃圾收集器回收时间短，即使在这段时间停止一切用户进程，也不会感到明显卡顿。因此**Serial垃圾收集器适合客户端使用**。

**由于Serial收集器只使用了一条线程，避免了线程切换的开销，因此简单高效。**

![Serial](https://camo.githubusercontent.com/2d92160fd261c40b4bce0fe74be4ea3b12126862bd5cf8f74e087d61f281f26b/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f73657269616c2e706e67)

#### 4.1.2、ParNew垃圾收集器（多线程）

ParNew是Serial的多线程版本，需要**多条GC线程进行垃圾清理**，但清理过程中仍然需要stop the world。

ParNew追求“**低停顿时间**”，与Serial的区别在于使用了多线程进行垃圾收集，在多CPU环境下和Serial相比会有一定的提升，但**切换线程需要额外的开销**，因此在单CPU环境中表现不如Serial。

![ParNew](https://camo.githubusercontent.com/0bcf2fc49b4fc7a7849dc0bd5e9c6948ddf711f3c8ee67e1eef6e656f5b0f0f8/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f7061726e65772e706e67)

#### 4.1.3、Parallel Scavenge垃圾收集器（多线程）

Parallel Scavenge和ParNew一样，都是多线程、新生代垃圾收集器。但两者的不同在于：

* **Parallel Scavenge：追求CPU吞吐量**，<u>*能够在较短的时间内完成指定任务*</u>，因此**适合没有交互的后台计算**。
* **ParNew：追求降低用户停顿时间，适合交互式应用**。

**吞吐量 = 运行用户代码时间 / （运行用户代码时间 + 垃圾收集时间）**

追求高吞吐量，可以通过减少 GC 执行实际工作的时间，然而，仅仅偶尔运行 GC 意味着每当 GC 运行时将有许多工作要做，因为在此期间积累在堆中的对象数量很高。单个 GC 需要花更多的时间来完成，从而导致更高的暂停时间。而考虑到低暂停时间，最好频繁运行 GC 以便更快速完成，反过来又导致吞吐量下降。

* 通过参数 **-XX:GCTimeRadio** 设置垃圾回收时间占总 CPU 时间的百分比。
* 通过参数 **-XX:MaxGCPauseMillis** 设置垃圾处理过程最久停顿时间。
* 通过命令 **-XX:+UseAdaptiveSizePolicy** 开启自适应策略。我们只要设置好堆的大小和 MaxGCPauseMillis 或 GCTimeRadio，收集器会自动调整新生代的大小、Eden 和 Survivor 的比例、对象进入老年代的年龄，以最大程度上接近我们设置的 MaxGCPauseMillis 或 GCTimeRadio。

### 4.2、老年代垃圾收集器

#### 4.2.1、Serial Old垃圾收集器（单线程）

Serial Old是Serial的老年代版本，和Serial一样都是单线程垃圾收集器，只使用一条GC线程执行垃圾清理。不同的是，**Serial Old使用“标记-整理”算法，而Serial使用“复制”算法**。

#### 4.2.2、Parallel Old垃圾收集器（多线程）

Parallel Old是Parallel Scavange的老年代版本，**追求CPU吞吐量**。

#### 4.2.3、CMS垃圾收集器

**CMS（Concurrent Mark Sweep，并发标记清除）收集器**是以**获得最短停顿时间为目标**的收集器（**追求底停顿**），它<u>*在垃圾收集时使得用户线程和GC线程并发执行*</u>，因此在垃圾收集过程中用户也不会感到明显的卡顿。

* **初始标记**：stop the world，仅使用一条初始标记线程对所有与**GC Roots直接关联**的对象进行标记。
* **并发标记**：使用多条标记线程，与用户线程并发执行。此过程进行**可达性分析，标记出所有废弃对象**。速度很慢。
* **重新标记**：stop the world，使用多条标记线程并发执行，将刚才**并发标记过程中新出现的废弃对象标记出来**。
* **并发清除**：使用**一条GC线程**，与用户线程并发执行，**清除刚才标记的对象**。这个过程非常耗时。

**并发标记与并发清除过程耗时最长**，且可以与用户线程一起工作，因此，**总体上说**，CMS 收集器的内存回收过程是与用户线程**一起并发执行**的。

![CMS](https://camo.githubusercontent.com/67ea3e9d18d2bb6ba465cf9dcf05245e7330e85f0cd39eb6c2399bd9e38200a1/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f636d732e706e67)

**CMS的缺点：**

* **吞吐量低**
* **无法处理浮动垃圾**
* **使用“标记-清除”算法产生碎片空间，导致频繁Full GC**

对于产生碎片空间的问题，可以通过开启 **-XX:+UseCMSCompactAtFullCollection**，在每次 Full GC 完成后都会进行一次内存压缩整理，将零散在各处的对象整理到一块。设置参数 **-XX:CMSFullGCsBeforeCompaction** 告诉 CMS，经过了 N 次 Full GC 之后再进行一次内存整理。

### 4.3、G1通用垃圾收集器

**G1是面向服务器端应用的垃圾收集器**，采用的是**区域化、分布式**的垃圾收集器。它没有新生代和老年代的概念，而是**将堆划分成一块块独立的Region**。当要进行垃圾回收时，**首先估计每个Region中的垃圾的数量，然后每次都从垃圾回收价值最大的Region开始回收**，因此可以***获得最大的回收效率***。

从整体上看，G1是基于“标记-整理”算法实现的收集器，从局部看（两个Region）是基于“复制”算法实现的，这意味着**运行期间不会产生内存空间碎片**。

> 一个对象和它内部所引用的对象可能不在同一个 Region 中，那么当垃圾回收时，是否需要扫描整个堆内存才能完整地进行一次可达性分析？
>
> 并不需要，**每个Region都有一个Remembered Set**，用于**记录本区域中所有对象引用的对象所在的区域**，进行可达性分析时，只要在GC Roots中再加上Remembered Set即可防止对整个堆内存进行遍历。

如果不计算维护Remembered Set的步骤，G1收集器的工作流程分为以下几个步骤：

* 初始标记：stop the world，仅用一条初始标记线程对所有与GC Roots直接关联的对象进行标记。
* 并发标记：使用一条标记线程与用户线程并发执行。此过程进行可达性分析，速度很慢。
* **最终标记**：stop the world，使用多条标记线程并发执行。
* **筛选回收**：回收废弃对象，此时也要stop the world，使用多条筛选回收线程并发执行。

## 5、内存分配与回收策略

对象的内存分配就是在堆上进行分配（也可能经过JIT编译后被拆成标量类型并间接在栈上分配），**对象主要分配在新生代的Eden**区，少数可能直接分配在老年代中，分配规则不固定，主要取决于当前使用的垃圾收集器组合以及相关参数配置。

### 5.1、对象优先在Eden区分配

在大多数情况下，**对象会先在Eden区分配，当Eden区没有足够的内存空间进行分配时，会引起Minor GC**。

Minor GC和Major GC/Full GC的区别：

* **Minor GC：回收新生代（包括Eden区和Survivor区）**，因为Java对象大多数具备生命周期比较短的特性，因此会引起频繁的Minor GC，一般回收速度也非常快。
* **Major GC/Full GC：回收老年代**，一般出现了Major GC，经常会伴随至少一次的Minor GC，但这并不是绝对的。**Major GC的速度一般会比Minor GC慢十倍以上**。

> 在 JVM 规范中，Major GC 和 Full GC 都没有一个正式的定义，所以有人也简单地认为 **Major GC 清理老年代，而 Full GC 清理整个内存堆**。

### 5.2、大对象直接进入老年代

**大对象指的是需要大量连续内存空间的Java对象**，如很长的字符串或数据。

一个大对象能够存入Eden的概率比较小，发生分配担保的概率比较大，而分配担保需要执行大量的复制操作，就会造成效率底下。

虚拟机提供了一个 -XX:PretenureSizeThreshold 参数，令大于这个设置值的对象直接在老年代分配，这样做的目的是避免在 Eden 区及两个 Survivor 区之间发生大量的内存复制。（还记得吗，新生代采用复制算法回收垃圾）

### 5.3、长期存活的对象将进入老年代

JVM为每个对象都设置了一个**对象年龄计数器**。当**新生代经历一次Minor GC时，存活下来的对象年龄计数器加1**，当年龄超过一定值时，就将超过该值的所有对象转移到老年代中。

使用 **`-XXMaxTenuringThreshold`** 设置新生代的最大年龄，只要超过该参数的新生代对象都会被转移到老年代中去。

### 5.4、动态对象年龄判断

如果当前新生代的Survivor中，**具有相同年龄的对象的内存大小总和大于Survivor空间的一半，年龄>=该年龄的对象就可以直接进入老年代**，无需等到`MaxTenuringThreshold`中要求的最大年龄。

### 5.4、空间分配担保

* 只要**老年代的连续空间大于新生代对象总大小或者历次晋升的平均大小**，就会进行 Minor GC，否则将进行 Full GC。
* **通过清除老年代中的废弃数据来扩大老年代空闲空间，以便给新生代作担保。**

### 5.5、触发JVM引起Full GC的情况

* **调用system.gc()**：此方法的调用是建议 JVM 进行 Full GC，注意这**只是建议而非一定**，但在很多情况下它会触发 Full GC，从而增加 Full GC 的频率。通常情况下我们只需要让虚拟机自己去管理内存即可，我们可以通过 -XX:+ DisableExplicitGC 来禁止调用 `System.gc()`。
* **老年代空间不足**：老年代空间不足会触发 Full GC 操作，若进行该操作后空间依然不足，则会抛出如下错误：`java.lang.OutOfMemoryError: Java heap space`
* **永久代空间不足** JVM 规范中运行时数据区域中的方法区，在 HotSpot 虚拟机中也称为永久代（Permanet Generation），存放一些类信息、常量、静态变量等数据，当系统要加载的类、反射的类和调用的方法较多时，永久代可能会被占满，会触发 Full GC。如果经过 Full GC 仍然回收不了，那么 JVM 会抛出如下错误信息：`java.lang.OutOfMemoryError: PermGen space `
* **CMS GC 时出现 `promotion failed` 和 `concurrent mode failure`** promotion failed，就是上文所说的担保失败，而 concurrent mode failure 是在执行 CMS GC 的过程中同时有对象要放入老年代，而此时老年代空间不足造成的。
* **统计得到的 Minor GC 晋升到旧生代的平均大小大于老年代的剩余空间。**



## 6、JVM性能调优

在高性能硬件上部署程序，主要有两种方式：

* **通过64位JDK来使用大内存。**
* **通过若干个32位虚拟机建立逻辑集群来利用硬件资源。**

### 6.1、使用64位JDK管理大内存

堆内存变大后，使用**垃圾收集的频率变少**了，但是**每次垃圾收集的时间变长**了，对于用户交互性强、对停顿时间敏感的系统，可以给Java虚拟机分配超大堆内存的前提是有把握**把应用程序的Full GC的频率控制的足够低**，至少低到不会影响用户使用。

可能面临的问题：

* 内存回收导致的**长停顿时间**。
* 现阶段，**64位的JDK的性能普遍低于32位的JDK**。
* 需要**保证程序足够稳定**，因为这种应用**要是产生堆溢出几乎就无法产生堆转储快照**（因为要产生超过10GB的Dump文件），哪怕产生了快照也几乎无法进行分析。
* **相同程序在64位JDK消耗的内存一般比32位JDK要大**，这是因为<u>*指针膨胀，以及数据类型对齐补白*</u>等因素造成的。

### 6.2、使用32位JVM建立逻辑集群

**在一台物理机器上启动多个应用服务器进程，为每个服务器进程分配不同的端口，然后在前端搭建一个负载均衡器，以反向代理的方式来分配访问请求。**

考虑到在一台物理机器上建立逻辑集群的目的是为了**尽可能的利用硬件资源**，因此不需要考虑状态保留、热转移之类的高可用性性能需求，也不需要保证每个虚拟机进程有绝对的均衡负载，因此可以用**无Session复制的亲合式集群**。我们仅仅需要保障集群具备亲合性，也就是**均衡器按照一定的均衡算法（一般是根据SessionID分配）将一个固定的用户请求永远分配到固定的一个集群节点进行处理即可。**

可能遇到的问题：

* 尽量**避免节点竞争全局资源**，如磁盘竞争，各个节点如果同时访问某个磁盘文件的话，很可能导致IO异常。
* **很难高效的利用资源池**，如连接池，一般是在节点建立自己独立的连接池，这样就可能会导致一些节点的连接池满了而一些节点的连接池还有较多空余的情况。
* 各个节点**受到32位内存的限制**。
* **大量使用本地缓存的应用，在逻辑集群中会造成较大的资源浪费**，因为每个逻辑节点都有一份缓存，这时候可以考虑<u>*把本地缓存改成集中式缓存*</u>。

## 6.3、调优案例分析

### 场景描述

一个小型系统，使用 32 位 JDK，4G 内存，测试期间发现服务端不定时抛出内存溢出异常。 加入 -XX:+HeapDumpOnOutOfMemoryError（添加这个参数后，堆内存溢出时就会输出异常日志）， 但再次发生内存溢出时，没有生成相关异常日志。

### 分析

在 32 位 JDK 上，1.6G 分配给堆，还有一部分分配给 JVM 的其他内存，直接内存最大也只能在剩余的 0.4G 空间中分出一部分， 如果使用了 NIO，JVM 会在 JVM 内存之外分配内存空间，那么就要小心“直接内存”不足时发生内存溢出异常了。

### 直接内存的回收过程

直接内存虽然不是 JVM 内存空间，但它的垃圾回收也由 JVM 负责。

垃圾收集进行时，虚拟机虽然会对直接内存进行回收， 但是直接内存却不能像新生代、老年代那样，发现空间不足了就通知收集器进行垃圾回收， 它只能等老年代满了后 Full GC，然后“顺便”帮它清理掉内存的废弃对象。 否则只能一直等到抛出内存溢出异常时，先 catch 掉，再在 catch 块里大喊 “`System.gc()`”。 要是虚拟机还是不听，那就只能眼睁睁看着堆中还有许多空闲内存，自己却不得不抛出内存溢出异常了。

## 7、类文件结构

### 7.1、JVM的无关性

* **平台无关性**：任何操作系统都能运行Java代码。
* **语言无关性**：JVM能运行除Java以外的其他代码。

**Java源代码首先需要Javac编译器编译成.class文件，然后由JVM执行.class文件，从而程序开始运行。**

JVM只认识.class文件，它不关心是何种语言生成了.class文件，只要.class文件符合JVM规范就能运行。目前已经有JRudy、Jython、Scala等语言能在JVM上运行。它们由各自的语法规则，但是他们的编译器都能将源代码编译成符合JVM规范的.class文件，从而能够借助JVM运行它们。

> Java语言的各种变量、关键字和运算符号的语义最终都是由多条字节码命令组合而成的，因此字节码所能提供的语义描述能力肯定会比Java语言本身更强大。因此，有一些Java语言本身无法支持的语言特性，不代表字节码本身无法支持。

### 7.2、Class文件结构

Class文件是二进制文件，它的内容有严格的规范，文件中没有任何空格，全部都是连续的0/1。**Class文件中的所有内容被分为两种类型：无符号数、表。**

* **无符号数**：无符号数表示Class文件中的值，这些值没有任何类型，但有不同的长度。u1/u2/u4/u8分别代表1/2/4/8字节的无符号数。
* **表**：由多个无符号数或其他表作为数据项组成的复合数据类型。

Class文件具体由以下几个构成：

* **魔数**
* **版本信息**
* **常量池**
* **访问标志**
* **类索引、父类索引、接口索引集合**
* **字段表集合**
* **方法表集合**
* **属性表集合**

#### 7.2.1、魔数

**Class文件的头4个字节称为魔数**，用来**表示这个Class文件的类型**。

> 魔数相当于文件后缀名，只不过后缀名容易被修改，不安全，因此在Class文件中标识文件类型比价合适。

#### 7.2.2、版本信息

紧接着魔数的**4个字节是版本信息**，<u>*5-6字节标识次版本信息，7-8字节表示主版本信息*</u>，用来表示**当前的Class文件使用的哪个版本的JDK**。

高版本的JDK能兼容以前版本的Class文件，但不能运行以后版本的Class文件，即使文件格式未发生任何变化，虚拟机也必须拒绝执行超过其版本号的Class文件。

#### 7.2.3、常量池

**版本信息之后就是常量池，常量池中存放两种类型的常量：**

* **字面值常量**：

  字面值常量就是程序定义的字符串，被final修饰。

* **符号引用**：

  符号引用就是我们定义的各种名字：类和接口的全限定名，方法的名字和描述符，字段的名字和描述符。

**常量池的特点：**

* 常量池中的常量数量不固定，因此**常量池开头放置一个u2类型的无符号数，用来存储当前常量池的容量**。
* 常量池中的每一个常量都是一个表，**表开始的第一位是一个u1类型的标志位（tag）代表当前这个常量属于哪种类型。**

**常量池中的常量类型：**

| 类型                             | tag  | 描述                   |
| -------------------------------- | ---- | ---------------------- |
| CONSTANT_utf8_info               | 1    | UTF-8 编码的字符串     |
| CONSTANT_Integer_info            | 3    | 整型字面量             |
| CONSTANT_Float_info              | 4    | 浮点型字面量           |
| CONSTANT_Long_info               | 5    | 长整型字面量           |
| CONSTANT_Double_info             | 6    | 双精度浮点型字面量     |
| **CONSTANT_Class_info**          | 7    | **类或接口的符号引用** |
| CONSTANT_String_info             | 8    | 字符串类型字面量       |
| CONSTANT_Fieldref_info           | 9    | 字段的符号引用         |
| CONSTANT_Methodref_info          | 10   | 类中方法的符号引用     |
| CONSTANT_InterfaceMethodref_info | 11   | 接口中方法的符号引用   |
| CONSTANT_NameAndType_info        | 12   | 字段或方法的符号引用   |
| CONSTANT_MethodHandle_info       | 15   | 标识方法句柄           |
| CONSTANT_MethodType_info         | 16   | 标识方法类型           |
| CONSTANT_InvokeDynamic_info      | 18   | 标识一个动态方法调用点 |

对于CONSTANT_Class_info（此类型代表类或者接口的符号引用），它的二维表结构如下：

| 类型 | 名称       | 数量 |
| ---- | ---------- | ---- |
| u1   | tag        | 1    |
| u2   | name_index | 1    |

**tag是标志位，用于区分常量类型**，**name_index**是一个索引值，它**指向常量池中一个CONSTANT_Utf8_info类型常量，此常量代表这个类（或接口）的全限定名**，这里的name_index的值若为0x0002，也就是指向了常量池中的第二项常量。

CONSTANT_Utf8_info 型常量的结构如下：

| 类型 | 名称   | 数量   |
| ---- | ------ | ------ |
| u1   | tag    | 1      |
| u2   | length | 1      |
| u1   | bytes  | length |

#### 7.2.4、访问标志

在常量池结束之后，紧接着的**两个字节代表访问标志**，这个标志用来**识别一些类/接口层次的访问信息**，比如<u>*是类还是接口、是否是public类型、是否被final/abstract修饰*</u>。

#### 7.2.5、类索引、父类索引、接口索引集合

**类索引和父类索引都是一个u2类型的数据，而接口索引是一个u2类型的数据的集合**。***Class文件由这三类数据来确定类的继承关系***，类索引用于确定这个类的全限定名，父类索引用于确定这个类的父类的全限定名。

由于Java不允许多重继承，因此除了java.lang.Object外，其他所有类都有父类，因此*<u>除了java.lang.Object的父类索引为0外，其他所有类的父类索引都不为0</u>*。由于一个类可能实现了多个接口，因此用一个接口索引集合来描述。这个集合第一项是一个u2类型的数据，用来标识索引表的容量，接下来就是接口的名字索引。

类索引和父类索引用一个u2类型的数据表示索引值，它们各自指向一个CONSTANT_Class_info的类描述符常量，通过该常量总的索引值可以找到定义在CONSTANT_Utf8-info类型的常量中的全限定名字符串。

#### 7.2.6、字段表集合

**字段表集合存储本类涉及到的成员变量**，***包括实例变量和类变量***，但不包括方法中的局部变量。

每个字段表只表示一个成员变量，本类中的所有成员变量构成了字段表集合。字段表集合的结构如下：

| 类型 | 名称             | 数量             | 说明                                                         |
| ---- | ---------------- | ---------------- | ------------------------------------------------------------ |
| u2   | access_flags     | 1                | 字段的访问标志，与类稍有不同                                 |
| u2   | name_index       | 1                | 字段名字的索引                                               |
| u2   | descriptor_index | 1                | 描述符，用于描述字段的数据类型。 基本数据类型用大写字母表示； 对象类型用“L 对象类型的全限定名”表示。 |
| u2   | attributes_count | 1                | 属性表集合的长度                                             |
| u2   | attributes       | attributes_count | 属性表集合，用于存放属性的额外信息，如属性的值。             |

> 字段表集合中不会出现从父类（或接口）中继承而来的字段，但有可能出现原本java代码中不存在的字段，譬如在内部类中为了保持对外部类的访问性，会自动添加指向外部类的实例的字段。

#### 7.2.7、方法表集合

方法表结构与属性表类似。

volatile关键字和transient关键字不能修饰方法，所以方法表的访问标志中没有ACC_VOLATILE和ACC_TRANSIENT标志。

**方法表中的属性表集合中有一张Code属性表，用于存储当前方法经编译器编译后的字节码指令。**

#### 7.2.8、属性表集合

每个属性对应一张属性表，属性表的结构如下：

| 类型 | 名称                 | 数量             |
| ---- | -------------------- | ---------------- |
| u2   | attribute_name_index | 1                |
| u4   | attribute_length     | 1                |
| u1   | info                 | attribute_length |

## 8、类加载的时机

### 8.1、类的生命周期

类从加载到虚拟机内存开始，到卸载出内存为止，它的整个生命周期包括以下7个阶段：

* 加载
* 验证
* 准备
* 解析
* 初始化
* 使用
* 卸载

验证、准备、解析三个阶段统称为连接。

![Load Class](https://camo.githubusercontent.com/0c9ca1187ee672a0124f22925d4623b083a9af904a07e13e3af1728204a9699c/68747470733a2f2f63646e2d646f6f63732e6f73732d636e2d7368656e7a68656e2e616c6979756e63732e636f6d2f67682f646f6f63732f6a766d406d61696e2f696d616765732f6c6f6164636c6173732e706e67)

加载、验证、准备、初始化和卸载这五个阶段的顺序是确定的，类的加载过程必须按照这中顺序按部就班的开始（注意是开始而不是进行或完成），而解析阶段则不一定：它在某些阶段可以在初始化之后再开始，这是为了支持Java语言的运行时绑定。

### 8.2、类加载过程中”初始化“开始的时机

Java 虚拟机规范没有强制约束类加载过程的第一阶段（即：加载）什么时候开始，但对于“初始化”阶段，有着严格的规定。有且仅有 5 种情况必须立即对类进行“初始化”：

* 在遇到**new、putstatic、getstatic、invokestatic**字节码指令时，如果类尚未被初始化，则需要先触发初始化。
* 对类进行**反射调用**时，如果类还没有被初始化，则需要先触发其初始化。
* 初始化一个类时，如果**类的父类没有被初始化**，则需要先初始化父类。
* 虚拟机启动时，用于需要指定一个**包含main()方法的主类**，虚拟机会先初始化这个类。
* 当使用 JDK 1.7 的动态语言支持时，如果一个 java.lang.invoke.MethodHandle 实例最后的解析结果为 REF_getStatic、REF_putStatic、REF_invokeStatic 的方法句柄，并且这个方法句柄所对应的类还没初始化，则需要先触发其初始化。

这5中场景中的行为称为对一个类进行主动引用，**除此之外，其他所有引用类的方式都不会触发类的初始化，称为被动引用**。

### 8.3、demo

```java
/**
 * 被动引用 Demo1:
 * 通过子类引用父类的静态字段，不会导致子类初始化。
 *
 * @author ylb
 *
 */
class SuperClass {
    static {
        System.out.println("SuperClass init!");
    }

    public static int value = 123;
}

class SubClass extends SuperClass {
    static {
        System.out.println("SubClass init!");
    }
}

public class NotInitialization {

    public static void main(String[] args) {
        System.out.println(SubClass.value);
        // SuperClass init!
    }

}
```

**输出结果：**

```java
SuperClass init!
123
```

对于静态字段，只有直接定义这个字段的类才会被初始化，因此通过其子类来引用父类中定义的静态字段，只会触发父类的初始化而不会触发子类的初始化。

```java
/**
 * 被动引用 Demo2:
 * 通过数组定义来引用类，不会触发此类的初始化。
 *
 * @author ylb
 *
 */

public class NotInitialization {

    public static void main(String[] args) {
        SuperClass[] superClasses = new SuperClass[10];
    }

}
```

这段代码不会触发父类的初始化，但会触发“[L 全类名”这个类的初始化，它由虚拟机自动生成，直接继承自 java.lang.Object，创建动作由字节码指令 newarray 触发。

```java
/**
 * 被动引用 Demo3:
 * 常量在编译阶段会存入调用类的常量池中，本质上并没有直接引用到定义常量的类，因此不会触发定义常量的类的初始化。
 *
 * @author ylb
 *
 */
class ConstClass {
    static {
        System.out.println("ConstClass init!");
    }

    public static final String HELLO_BINGO = "Hello Bingo";

}

public class NotInitialization {

    public static void main(String[] args) {
        System.out.println(ConstClass.HELLO_BINGO);
    }

}
```

编译通过之后，常量存储到 NotInitialization 类的常量池中，NotInitialization 的 Class 文件中并没有 ConstClass 类的符号引用入口，这两个类在编译成 Class 之后就没有任何联系了。

### 8.4、接口的加载过程

接口加载过程与类加载过程稍有不同。

当一个类在初始化时，要求其父类全部都已经初始化过了，但是一个接口在初始化时，并不要求其父接口全部都完成了初始化，当真正用到父接口的时候才会初始化。

## 9、类加载过程

类加载过程包括五个阶段：加载、验证、准备、解析和初始化。

### 9.1、加载

#### 9.1.1、加载的过程

”加载“是”类加载“过程的一个阶段，两者不是同一个概念。在加载阶段，虚拟机需要完成3件事：

* 通过类的全限定名**获取该类的二进制字节流**。
* 将二进制字节流所代表的**静态结构转换为方法区的运行时数据结构**。
* 在内存中**创建一个代表该类的java.lang.Class对象**，作为方法区中这个类的各个数据的访问入口。 

#### 9.1.2、获取二进制字节流

对于Class文件，虚拟机没有指明要从哪里获取、怎么获取。除了直接从编译好的.Class文件中读取，还有以下几种方式：

* 从zip包中读取，如jar、war等。
* 从网络中获取，如Applet。
* 通过动态代理技术生成代理类的二进制字节流。
* 由JSP文件生成对应的Class类。
* 从数据库中读取，如有些中间件服务器可以选择把程序安装到数据库中来完成程序代码在集群间的分发。

#### 9.1.3、”非数组类“和”数组类“的加载比较

* 非数组类加载阶段可以使用系统提供的引导类加载器，也可以由用户自定义的类加载器完成，开发人员可以通过定义自己的类加载器控制字节流的获取方式（如重写一个类加载器的loadClass()方法）。
* 数组类本身不通过类加载器创建，它是由Java虚拟机直接创建，再由类加载器创建数组中的元素类。

#### 9.1.4、注意事项

* 虚拟机规范未规范Class对象的存储位置，对于HotSpot虚拟机而言，Class对象比较特殊，它虽然是对象，但是却存储在方法区内。
* 加载阶段和连接阶段的部分内容交叉进行，加载阶段还没结束，连接阶段可能已经开始了。但这两个阶段的开始时间任然保持着固定的前后顺序。

### 9.2、验证

#### 9.2.1、验证的重要性

验证阶段确保Class文件的字节流中包含的信息符合当前虚拟机的要求，并且不会危害当前虚拟机的安全。

#### 9.2.1、验证的过程

* 文件合适验证：验证字节流是否符合Class文件格式的规范，并且能被当前版本的虚拟机处理，验证点如下：
  * 是否以魔数0XCAFEBABE开头。
  * 主次版本号是否在当前虚拟机处理范围内。
  * 常量池中是否存在不被支持的常量类型。
  * 指向常量的索引值是否指向了不存在的常量。
  * CONSTANT_Utf8_info型的常量是否有不符合UTF8编码的数据。
  * ......
* 元数据验证：对字节码描述信息进行语义分析，确保其符合Java语法规范。
* 字节码验证：本阶段是验证过程中最复杂的一个过程，是对方法体进行语义分析，保证方法在运行时不会出现危害虚拟机的事件。
* 符号引用验证：本阶段发生在解析阶段，确保解析正常执行。

### 9.3、准备

准备阶段是正式为类变量（或称静态成员变量）分类内存并设置初始值的阶段。这些变量（不包括实例变量）所使用的内存都在方法区进行分配。

初始值通常是数据类型的零值（0、null），假设一个类变量的定位为：
```java
public static int value = 123;
```

那么变量 value 在准备阶段过后的初始值为 0 而不是 123，因为这时候尚未开始执行任何 Java 方法。

存在“特殊情况”：如果类字段的字段属性表中存在 ConstantValue 属性，那么在准备阶段 value 就会被初始化为 ConstantValue 属性所指定的值，假设上面类变量 value 的定义变为：

```java
public static final int value = 123;
```

那么在准备阶段虚拟机会根据 ConstantValue 的设置将 value 赋值为 123。

### 9.4、解析

解析阶段是虚拟机将常量池内的符号引用替换为直接引用的过程。

### 9.5、初始化

类初始化阶段是类加载过程的最后一步，**是执行类构造器 `<clinit>()` 方法的过程**。

 `<clinit>()` 方法是由编译器自动收集类中的所有类变量的赋值动作和静态语句块（static{}块）中的语句合并产生的，编译器收集的顺序是由语句在源文件中出现的顺序决定的。

静态语句块只能访问定义在静态语句块之前的变量，定义在它之后的变量，在前面的静态语句块中可以赋值，但不能被访问。如：

```java
public class Test {
    static {
        i = 0;  // 给变量赋值可以正常编译通过
        System.out.println(i);  // 这句编译器会提示“非法向前引用”
    }
    static int i = 1;
}
```

`<clinit>()` 方法不需要显式调用父类构造器，虚拟机会保证在子类的 `<clinit>()` 方法执行之前，父类的 `<clinit>()` 方法已经执行完毕。

由于父类的 `<clinit>()` 方法先执行，意味着父类中定义的静态语句块要优先于子类的变量赋值操作。如下方代码所示：

```java
static class Parent {
    public static int A = 1;
    static {
        A = 2;
    }
}
static class Sub extends Parent {
    public static int B = A;
}
public static void main(String[] args) {
    System.out.println(Sub.B); // 输出2
}
```

`<clinit>()` 方法不是必需的，如果一个类没有静态语句块，也没有对类变量的赋值操作，那么编译器可以不为这个类生成 `<clinit>()` 方法。

**接口中不能使用静态代码块，但接口也需要通过 `<clinit>()` 方法为接口中定义的静态成员变量显式初始化。**但接口与类不同，接口的 `<clinit>()` 方法不需要先执行父类的 `<clinit>()` 方法，只有当父接口中定义的变量使用时，父接口才会初始化。

虚拟机会保证一个类的 `<clinit>()` 方法在多线程环境中被正确加锁、同步。如果多个线程同时去初始化一个类，那么只会有一个线程去执行这个类的 `<clinit>()` 方法。

## 10、类加载器

### 10.1、类与类加载器

#### 10.1.1、判断类是否相等

任意一个类，都由加载它的类加载器和这个类本身一同确定其在Java虚拟机中的唯一性，每一个类加载器，都有一个独立的类名称空间。

因此，比较两个类是否相等，只有在这两个类是由同一个类加载器加载的前提下才有意义，否则，即使这两个类来自同一个Class文件，被同一个虚拟机加载，只要加载它们的类加载器不同，那么这两个类就必定不相等。

这里的“相等”，包括代表类的Class对象的`equals()`方法、`isInstance`方法的返回结果，也包括使用instanceof 关键字做对象所属关系判定等情况。

#### 10.1.2、加载器种类

系统提供了三种类加载器：

* 启动类加载器（Bootstrap ClassLoader）：负责将存放在 `<JAVA_HOME>\lib` 目录中的，并且能被虚拟机识别的类库加载到虚拟机内存中，这里仅按照文件名识别，如 rt.jar，名字不符合的类库即使放在 lib 目录中也不会被加载
* 扩展类加载器（Extension ClassLoader）：负责加载 `<JAVA_HOME>\lib\ext` 目录中的所有类库，开发者可以直接使用扩展类加载器。
* 应用程序类加载器（Application ClassLoader）：由于这个类加载器是 ClassLoader 中的 `getSystemClassLoader()` 方法的返回值，所以一般也称它为“系统类加载器”。它负责加载用户类路径（classpath）上所指定的类库，开发者可以直接使用这个类加载器，如果应用程序中没有自定义过自己的类加载器，一般情况下这个就是程序中默认的类加载器。

![image-20240201104205731](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240201104205731.png)

当然，如果有必要，还可以加入自己定义的类加载器。

### 10.2、双亲委派模式

双亲委派模型是描述类加载器之间的层次关系。它要求除了顶层的启动类加载器外，其余的类加载器都应当有自己的父类加载器。（父子关系一般不会以继承的关系实现，而是以组合关系来复用父加载器的代码）

#### 10.2.1、工作过程

如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成，每个层次的类加载器都是如此，因此，所有的类加载请求都应该传送到顶层的类加载器中，只有当父类加载器反馈自己无法完成这个加载请求（找不到所需的类）时，子加载器才会去尝试自己去加载。

在 java.lang.ClassLoader 中的 `loadClass` 方法中实现该过程。

#### 10.2.2、为什么使用双亲委派模式

像 java.lang.Object 这些存放在 rt.jar 中的类，无论使用哪个类加载器加载，最终都会委派给最顶端的启动类加载器加载，从而使得不同加载器加载的 Object 类都是同一个。

相反，如果没有使用双亲委派模型，由各个类加载器自行去加载的话，如果用户自己编写了一个称为 java.lang.Object 的类，并放在 classpath 下，那么系统将会出现多个不同的 Object 类，Java 类型体系中最基础的行为也就无法保证。

# 五、JMM

## 1、什么是Java内存模型（JMM）

JMM就是Java内存模型(java memory model)。因为在不同的硬件生产商和不同的操作系统下，内存的访问有一定的差异，所以会造成相同的代码运行在不同的系统上会出现各种问题。所以**java内存模型(JMM)屏蔽掉各种硬件和操作系统的内存访问差异，以实现让java程序在各种平台下都能达到一致的并发效果。**

Java内存模型规定**所有的变量都存储在主内存**中，包括实例变量，静态变量，但是不包括局部变量和方法参数。每个线程都有自己的工作内存，**线程的工作内存保存了该线程用到的变量和主内存的副本拷贝，线程对变量的操作都在工作内存中进行**。**线程不能直接读写主内存中的变量**。

不同的线程之间也无法访问对方工作内存中的变量。线程之间变量值的传递均需要通过主内存来完成。

![img](https://ucc.alicdn.com/images/user-upload-01/img_convert/99aa7bfed55be2763eb947ed1290616f.png)

## 2、JMM定义了什么

整个Java内存模型实际上是围绕着三个特征建立起来的。分别是：原子性，可见性，有序性。这三个特征可谓是整个Java并发的基础。



# 六、MySQL

## 1、事务的四大特性

事务特性ACID：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）。

* **原子性**：事务包含的所有操作要么全部成功，要么全部失败回滚。
* **一致性**：一个事务在执行前和执行后都必须处于一致性状态。如a和b账户共1000块，两人之间转账无论成功还是失败之后，两个账户的总和都必须是1000块。
* **隔离性**：和隔离级别相关，如`read committed`，**一个事务只能读取到已经提交的修改**。
* **持久性**：一个事务一旦被提交了，那么对于数据库中的数据的改变将是永久性的，即使在数据库系统遇到故障的情况下也不会丢失提交事务的操作。

## 2、数据库的三大范式

1. **第一范式1NF**

   **确保数据库字段的原子性。**数据库中的字段不可再分

   比如字段 userInfo : 广东省 10086' ，依照第一范式必须拆分成 userInfo : 广东省 userTel : 10086
   两个字段。

2. **第二范式2NF**

   **首先要满足第一范式，另外还要包含两个内容，一是表必须有主键，二是非主键必须完全依赖于主键，而不能依赖于主键的一部分。**

   举个例子。假定选课关系表为student_course (student_no, student_name, age, course_name,
   grade, credit)，主键为(student_no, course_name)。其中学分完全依赖于课程名称，姓名年龄完全依
   赖学号，不符合第二范式，会导致数据冗余（学生选n门课，姓名年龄有n条记录）、插入异常（插入一
   门新课，因为没有学号，无法保存新课记录）等问题。

   应该拆分成三个表：学生： student (stuent_no, student_name, 年龄)；课程：
   course (course_name, credit)；选课关系： student_course_relation (student_no, course_name,
   grade)。

3. **第三范式3NF**

   **首先要满足第二范式，另外非主键列必须直接依赖于主键，不能存在传递依赖。即不能存在：非主键列A依赖于非主键列B，非主键列B依赖于主键的情况。**

   假定学生关系表为Student(student_no, student_name, age, academy_id, academy_telephone)，主
   键为"学号"，其中学院id依赖于学号，而学院地点和学院电话依赖于学院id，存在传递依赖，不符合第三
   范式。

   可以把学生关系表分为如下两个表：学生：(student_no, student_name, age, academy_id)；学院：
   (academy_id, academy_telephone)。

**2NF和3NF的区别：**

* 2NF依据是非主键列是否完全依赖主键，还是依赖于主键的一部分。
* 3NF依据是非主键列是直接依赖于主键，还是直接依赖于非主键。

**第一范式：**1NF是对属性的**原子性约束**，要求属性具有原子性，不可再分解；
**第二范式：**2NF是对记录的**惟一性约束**，要求记录有惟一标识，即实体的惟一性；
**第三范式：**3NF是对**字段冗余性的约束**，即任何字段不能由其他字段派生出来，它要求字段没有冗余。

> 没有冗余的数据库设计可以做到。但是，没有冗余的数据库未必是最好的数据库，有时为了提高运行效率，就必须降低范式标准，适当保留冗余数据。具体做法是：在概念数据模型设计时遵守第三范式，降低范式标准的工作放到物理数据模型设计时考虑。降低范式就是增加字段，允许冗余。

## 3、事务隔离的级别有哪些

先解释一下脏读、不可重复读和幻读的概念：

* **脏读：**在一个事务处理过程中读取了另一个未提交事务中的数据。
* **不可重复读：**对于数据库中的某行记录，一个事务范围内多次查询却返回了不同的数据值，这是由于在查询间隔，另一个事务修改了数据并提交了。
* **幻读：**当某个事务在读取某个范围内的记录时，另一个事务又在该范围内插入了新的记录。对幻读的正确理解是，一个事务内的读取操作的结论不足以支撑之后业务的执行。假设事务要新增一条记录，主键为id，在新增之前执行了select，发现没有id为xxx的记录，但插入时却出现了主键冲突，这就属于幻读，读取不到的记录却发生了主键冲突，是因为记录实际上已经被其他的事务插入了，但当前事务不可见。

不可重复读和脏读的区别：**脏读时某一事务读取了另一个事务未提交的脏数据，而不可重复读则是读取了前一个事务提交的数据**。

事务隔离就是为了解决上面提到的脏读、不可重复读、幻读这几个问题。

MySQL数据库提供了四种隔离级别：

* **Serializable（串行化）**：通过强制事务排序，使之不可能相互冲突，从而解决幻读问题。
* **Repeatable read（可重复读）**：**NySQL的默认事务隔离级别，它确保同一事务的多个实例在并发读取数据时，会看到同样的数据行，解决了不可重复读的问题**。
* **Read committed（读已提交）**：一个事务只能看见已经提交事务所作的改变，可避免脏读的发生。
* **Read uncommitted（读未提交）**：所有事务都可以看见其他未提交事务的执行结果。

**查看隔离级别：**

```sq
select @@transaction_isolation;
```

**设置隔离级别：**

```sql
set session transaction isolation level read uncommitted;
```

## 4、生产环境数据库一般用的隔离级别

生产环境一般使用读已提交（RC）隔离级别。为什么不使用可重复读（RR）隔离级别？

> 可重复读(Repeatable Read)，简称为RR 读已提交(Read Commited)，简称为RC

* 在可重复读（RR）隔离级别下，存在**间隙锁**，导致出现死锁的几率比读已提交（RC）大得多。
* 在可重复读（RR）隔离级别下，**条件列未命中索引会锁表**，而在读已提交（RC）隔离级别下，只锁行。也就是说，读以提交的并发性要比可重复读高。
* 并且大部分场景下，不可重复读是可以接受的。毕竟数据都已经提交了，读出来本身没有太大问题。

## 5、编码和字符集的关系

我们平时可以在编辑器上输入各种中文英文字母，但这些都是给人读的，不是给计算机读的，其实**计算机真正保存和传输数据都是以二进制0101的格式进行的**。

那么就需要有一个规则，把中文和英文字母转化为二进制。其中d对应十六进制下的64，它可以转换为01二进制的格式。于是字母和数字就这样一一对应起来了，这就是ASCII编码格式。

它用**一个字节**，也就是`8位`来标识字符，基础符号有128个，扩展符号也是128个。也就只能表示下**英文字母和数字**。

这明显不够用。于是，为了标识**中文**，出现了**GB2312**的编码格式。为了标识**希腊语**，出现了**greek**编码格式，为了标识**俄语**，整了**cp866**编码格式。

为了统一它们，于是出现了**Unicode编码格式**，它用了2~4个字节来表示字符，这样理论上所有符号都能被收录进去，并且它还完全兼容ASCII的编码，也就是说，同样是字母d，在ASCII用64表示，在Unicode里还是用64来表示。

但**不同的地方是ASCII编码用1个字节来表示，而Unicode用则两个字节来表示。**

同样都是字母d，unicode比ascii多使用了一个字节，如下：

```\
D   ASCII:           01100100
D Unicode:  00000000 01100100
```

可以看到，上面的unicode编码，前面的都是0，其实用不上，但还占了个字节，有点浪费。如果我们能做到该隐藏时隐藏，这样就能省下不少空间，按这个思路，就是就有了**UTF-8编码**。

总结一下，**按照一定规则把符号和二进制码对应起来，这就是编码。而把n多这种已经编码的字符聚在一起，就是我们常说的字符集**。

比如utf-8字符集就是所有utf-8编码格式的字符的合集。

想看下mysql支持哪些字符集。可以执行 `show charset;`

##  6、utf8和utf8mb4的区别

上面提到utf-8是在unicode的基础上做的优化，既然unicode有办法表示所有字符，那utf-8也一样可以表示所有字符，为了避免混淆，我在后面叫它**大utf8**。

mysql支持的字符集中有utf8和utf8mb4。

先说**utf8mb4**编码，mb4就是**most bytes 4**的意思，从上图最右边的`Maxlen`可以看到，它最大支持用**4个字节**来表示字符，它几乎可以用来表示目前已知的所有的字符。

再说mysql字符集里的**utf8**，它是数据库的**默认字符集**。但注意，**此utf8非彼utf8**，我们叫它**小utf8**字符集。为什么这么说，因为从Maxlen可以看出，它最多支持用3个字节去表示字符，按utf8mb4的命名方式，准确点应该叫它**utf8mb3**。

utf8 就像是阉割版的utf8mb4，只支持部分字符。比如`emoji`表情，它就不支持。

而mysql支持的字符集里，第三列，**collation**，它是指**字符集的比较规则**。

比如，"debug"和"Debug"是同一个单词，但它们大小写不同，该不该判为同一个单词呢。

这时候就需要用到collation了。

通过`SHOW COLLATION WHERE Charset = 'utf8mb4';`可以查看到`utf8mb4`下支持什么比较规则。

![image-20240203110558621](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240203110558621.png)

如果`collation = utf8mb4_general_ci`，是指使用utf8mb4字符集的前提下，**挨个字符进行比较**（`general`），并且不区分大小写（`_ci，case insensitice`）。

这种情况下，"debug"和"Debug"是同一个单词。

如果改成`collation=utf8mb4_bin`，就是指**挨个比较二进制位大小**。

于是"debug"和"Debug"就不是同一个单词。

**那utf8mb4对比utf8有什么劣势吗？**

我们知道数据库表里，字段类型如果是`char(2)`的话，里面的`2`是指**字符个数**，也就是说**不管这张表用的是什么编码的字符集**，都能放上2个字符。

而char又是**固定长度**，为了能放下2个utf8mb4的字符，char会默认保留`2*4（maxlen=4）= 8`个字节的空间。

如果是utf8mb3，则会默认保留 `2 * 3 (maxlen=3) = 6`个字节的空间。也就是说，在这种情况下，**utf8mb4会比utf8mb3多使用一些空间。**

**对于固定长度的char类型的字符串，utf8mb4会比utf8多使用一些空间**。

## 7、索引

### 7.1、索引的定义

索引是存储引擎用于提高数据库表的访问速度的一种数据结构。

### 7.2、索引的优缺点

**优点：**

* **加快数据查找速度。**
* 为用来排序或者是分组的字段添加索引，可以**加快分组和排序的速度。**
* **加快表与表之间的连接。**

**缺点：**

* 建立索引需要**占用物理空间**。
* 会**降低表的增删改的效率**，因为每次对表记录进行增删改，需要进行动态维护索引，导致增删改的时间变长。

### 7.3、索引的作用

数据是存储在磁盘上的，查询数据时，如果没有索引，就需要加载所有的数据到内存上，一次进行检索，读取磁盘次数较多。有了索引，就不需要加载全部数据了，因为B+树的高度一般在2-4层，最多只需要读取2-4次磁盘，查询速度大大提升。

### 7.4、什么情况下需要建立索引

1. 经常用于**查询**的字段
2. 经常用于**连接**的字段建立索引，可以加快连接的速度。
3. 经常需要**排序**的字段建立索引，因为索引已经排好序，可以加快排序查询速度。

### 7.5、什么情况下不建立索引

1. **where条件中用不到的字段**不适合建立索引。
2. **表记录较少**。比如只有几百条数据，没必要加索引。
3. 需要**经常增删改**，需要评估是否适合加索引。
4. **参与列计算的列**不适合建立索引。
5. **区分度不高的字段**不适合建立索引，如性别，只有男/女/未知三个值。加了索引，查询效率也不会提高。

### 7.6、索引的数据结构

索引的数据结构主要有B+树和哈希表，对应的索引分别是**B+树索引和哈希索引**。InnoDB引擎的索引类型有B+树索引和哈希索引，默认的索引类型为B+树索引。

**B+树索引**

B+ 树是基于B 树和叶子节点顺序访问指针进行实现，它具有B树的平衡性，并且通过顺序访问指针来提高区间查询的性能。

在 B+ 树中，节点中的 `key` 从左到右递增排列，如果某个指针的左右相邻 `key` 分别是 keyi 和 keyi+1，则该指针指向节点的所有 `key` 大于等于 keyi 且小于等于 keyi+1。

![image-20240203112153409](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240203112153409.png)

进行查找操作时，首先在根节点进行二分查找，找到key 所在的指针，然后递归地在指针所指向的节点进行查找。直到查找到叶子节点，然后在叶子节点上进行二分查找，找出key 所对应的数据项。

MySQL 数据库使用最多的索引类型是BTREE 索引，底层基于B+树数据结构来实现。

```cmd
mysql> show index from blog\G;
*************************** 1. row ***************************
        Table: blog
   Non_unique: 0
     Key_name: PRIMARY
 Seq_in_index: 1
  Column_name: blog_id
    Collation: A
  Cardinality: 4
     Sub_part: NULL
       Packed: NULL
         Null:
   Index_type: BTREE
      Comment:
Index_comment:
      Visible: YES
   Expression: NULL

```

**哈希索引**

哈希索引是基于哈希表实现的，对于每一行数据，存储引擎会对索引列进行哈希计算得到哈希码，并且哈希算法要尽量保证不同的列值计算出的哈希码值是不同的，将哈希码的值作为哈希表的key值，将指向数据行的指针作为哈希表的value值。这样查找一个数据的时间复杂度就是O(1)，一般多用于精确查找。

### 7.7、Hash索引和B+树索引的区别

* 哈希索引**不支持排序**，因为哈希表是无序的。
* 哈希索引**不支持范围查找**。
* 哈希索引**不支持模糊查询**以及多列索引的最左前缀匹配。
* 因为哈希表会存在哈希冲突，所以**哈希索引的性能是不稳定的，而B+树索引的性能相对稳定**，每次查询都是从根节点到叶子节点。

### 7.8、为什么B+树比B树更适合实现数据库索引

* 由于**B+树的数据都存储在叶子节点中**，叶子节点均为索引，方便扫库，只需要扫一遍叶子节点即可，但是B树因为其分支同样存储着数据，我们要找到具体的数据，需要进行一次中序遍历按序来扫，所以B+树更适合在区间查询的情况，而在数据库中基于范围的查询是非常频繁的，所以通常使用B+树用于数据库索引。
* **B+树的节点只存储索引key值，具体信息的地址存在于叶子节点的地址中**。这就使**以页为单位的索引中可以存放更多的节点**。减少更多的I/O支出。
* **B+树的查询效率更加稳定，任何关键字的查找必须走一条从根结点到叶子结点的路**。所有关键字查询的路径长度相同，导致每一个数据的查询效率相当。

### 7.9、索引的分类

1. **主键索引**：名为primary的唯一非空索引，不允许有空值。

2. **唯一索引**：索引列的值必须是唯一的，允许有空值。主键索引和唯一索引的区别在于：唯一索引字段可以为null且可以存在多个null值，而主键索引字段不可以为null。唯一索引的用途：唯一标识数据库中的每条记录，主要用来防止重复数据插入。创建唯一索引的SQL语句为：

   ```sql
   ALTER TABLE table_name
   ADD CONSTRAINT constraint_name UNIQUE KEY(column_1,column_2,...);
   ```

3. **组合索引**：在表中的多个字段组合上创建的索引，只有在查询条件中使用了这些字段的左边字段时，索引才会被使用，使用组合索引时需遵循最左前缀原则。

4. **全文索引**：只能在CHAR 、VARCHAR 和TEXT 类型字段上使用全文索引。

5. **普通索引**：普通索引是最基本的索引，它没有任何限制，值可以为空。

### 7.10、什么是最左匹配原则

**如果 SQL 语句中用到了组合索引中的最左边的索引，那么这条 SQL 语句就可以利用这个组合索引去进行匹配。当遇到范围查询(`>`、`<`、`between`、`like`)就会停止匹配，后面的字段不会用到索引**。

对`(a,b,c)`建立索引，查询条件使用 a/ab/abc 会走索引，使用 bc 不会走索引。

对`(a,b,c,d)`建立索引，查询条件为`a = 1 and b = 2 and c > 3 and d = 4`，那么a、b和c三个字段能用到索引，而d无法使用索引。因为遇到了范围查询。

如下图，对(a, b) 建立索引，a 在索引树中是全局有序的，而 b 是全局无序，局部有序（当a相等时，会根据b进行排序）。直接执行`b = 2`这种查询条件无法使用索引。

![image-20240205213802510](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240205213802510.png)

当a的值确定的时候，b是有序的。例如`a = 1`时，b值为1，2是有序的状态。当`a = 2`时候，b的值为1，4也是有序状态。 当执行`a = 1 and b = 2`时a和b字段能用到索引。而执行`a > 1 and b = 2`时，a字段能用到索引，b字段用不到索引。因为a的值此时是一个范围，不是固定的，在这个范围内b值不是有序的，因此b字段无法使用索引。

### 7.11、什么是聚集索引

InnoDB使用**表的主键构造主键索引树**，同时叶子节点中存放的即为整张表的记录数据。聚集索引叶子节点的存储是逻辑上连续的，使用双向链表连接，叶子节点按照主键的顺序排序，因此对于主键的排序查找和范围查找速度比较快。如果表中没有显示指定主键，则会**选择表中的第一个不允许为NULL 的唯一索引**。如果没有主键也没有合适的唯一索引，那么InnoDB 内部会生成一个隐藏的主键作为聚集索引，这个隐藏的主键长度为6个字节，它的值会随着数据的插入自增。

### 7.12、什么是覆盖索引

**覆盖索引（covering index ，或称为索引覆盖）即从非主键索引中就能查到的记录，而不需要查询主键索引中的记录，避免了回表的产生减少了树的搜索次数，显著提升性能**。不是所有类型的索引都可以成为覆盖索引。覆盖索引要存储索引列的值，而哈希索引、全文索引不存储索引列的值，所以**MySQL使用b+树索引做覆盖索引**。

对于使用了覆盖索引的查询，在查询前面使用`explain`，输出的extra列会显示为`using index`。

比如`user_like` 用户点赞表，组合索引为`(user_id, blog_id)`，`user_id`和`blog_id`都不为`null`。

```sql
explain select blog_id from user_like where user_id = 13;
```

`explain`结果的`Extra`列为`Using index`，查询的列被索引覆盖，并且where筛选条件符合最左前缀原则，通过**索引查找**就能直接找到符合条件的数据，不需要回表查询数据。

```sql
explain select user_id from user_like where blog_id = 1;
```

`explain`结果的`Extra`列为`Using where; Using index`， 查询的列被索引覆盖，where筛选条件不符合最左前缀原则，无法通过索引查找找到符合条件的数据，但可以通过**索引扫描**找到符合条件的数据，也不需要回表查询数据。

![image-20240321154941037](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321154941037.png)

### 7.13、索引的设计原则

* 对于经常作为查询条件的字段，应该建立索引，以提高查询速度

* 为经常需要排序、分组和联合操作的字段建立索引

* 索引列的**区分度越高**，索引的效果越好。比如使用性别这种区分度很低的列作为索引，效果就会很差。

* 避免给"大字段"建立索引。尽量使用数据量小的字段作为索引。因为`MySQL`在维护索引的时候是会将字段值一起维护的，那这样必然会导致索引占用更多的空间，另外在排序的时候需要花费更多的时间去对比。

* 尽量使用**短索引**，对于较长的字符串进行索引时应该指定一个较短的前缀长度，因为较小的索引涉及到的磁盘I/O较少，查询速度更快。

* 索引不是越多越好，每个索引都需要额外的物理空间，维护也需要花费时间。

* 频繁增删改的字段不要建立索引。假设某个字段频繁修改，那就意味着需要频繁的重建索引，这必然影响MySQL的性能

* 利用**最左前缀原则**。

###  7.14、索引什么时候会失效

导致索引失效的情况：

- 对于组合索引，不是使用组合索引最左边的字段，则不会使用索引
- 以%开头的like查询如`%abc`，无法使用索引；非%开头的like查询如`abc%`，相当于范围查询，会使用索引
- 查询条件中列类型是字符串，没有使用引号，可能会因为类型不同发生隐式转换，使索引失效
- 判断索引列是否不等于某个值时
- 对索引列进行运算
- 查询条件使用`or`连接，也会导致索引失效

### 7.15、什么是前缀索引

有时需要在很长的字符列上创建索引，这会造成索引特别大且慢。使用前缀索引可以避免这个问题。

**前缀索引是指对文本或者字符串的前几个字符建立索引**，这样索引的长度更短，查询速度更快。

创建前缀索引的关键在于选择足够长的前缀以**保证较高的索引选择性**。索引选择性越高查询效率就越高，因为选择性高的索引可以让MySQL在查找时过滤掉更多的数据行。

建立前缀索引的方式：

```sql
// email列创建前缀索引
ALTER TABLE table_name ADD KEY(column_name(prefix_length));
```

## 8、常见的存储引擎有哪些

MySQL中常用的四种存储引擎分别是： **MyISAM**、**InnoDB**、**MEMORY**、**ARCHIVE**。MySQL 5.5版本后默认的存储引擎为`InnoDB`。

**InnoDB存储引擎**

InnoDB是MySQL**默认的事务型存储引擎**，使用最广泛，基于聚簇索引建立的。InnoDB内部做了很多优化，如能够自动在内存中创建自适应hash索引，以加速读操作。

**优点**：支持事务和崩溃修复能力；引入了行级锁和外键约束。

**缺点**：占用的数据空间相对较大。

**适用场景**：需要事务支持，并且有较高的并发读写频率。

**MyISAM存储引擎**

数据以紧密格式存储。对于只读数据，或者表比较小、可以容忍修复操作，可以使用MyISAM引擎。MyISAM会将表存储在两个文件中，数据文件`.MYD`和索引文件`.MYI`。

**优点**：访问速度快。

**缺点**：MyISAM不支持事务和行级锁，不支持崩溃后的安全恢复，也不支持外键。

**适用场景**：对事务完整性没有要求；表的数据都是只读的。

**MEMORY存储引擎**

MEMORY引擎将数据全部放在内存中，访问速度较快，但是一旦系统奔溃的话，数据都会丢失。

MEMORY引擎默认使用哈希索引，将键的哈希值和指向数据行的指针保存在哈希索引中。

**优点**：访问速度较快。

**缺点**：

1. 哈希索引数据不是按照索引值顺序存储，无法用于排序。
2. 不支持部分索引匹配查找，因为哈希索引是使用索引列的全部内容来计算哈希值的。
3. 只支持等值比较，不支持范围查询。
4. 当出现哈希冲突时，存储引擎需要遍历链表中所有的行指针，逐行进行比较，直到找到符合条件的行。

**ARCHIVE存储引擎**

ARCHIVE存储引擎非常适合存储大量独立的、作为历史记录的数据。ARCHIVE提供了压缩功能，拥有高效的插入速度，但是这种引擎不支持索引，所以查询性能较差。

##  9、MyISAM和InnoDB的区别

* **存储结构的区别**。每个MyISAM在磁盘上存储成三个文件。文件的名字以表的名字开始，扩展名指出文件类型。 .frm文件存储表定义。数据文件的扩展名为.MYD (MYData)。索引文件的扩展名是.MYI (MYIndex)。InnoDB所有的表都保存在同一个数据文件中（也可能是多个文件，或者是独立的表空间文件），InnoDB表的大小只受限于操作系统文件的大小，一般为2GB。

* **存储空间的区别**。MyISAM支持支持三种不同的存储格式：静态表(默认，但是注意数据末尾不能有空格，会被去掉)、动态表、压缩表。当表在创建之后并导入数据之后，不会再进行修改操作，可以使用压缩表，极大的减少磁盘的空间占用。InnoDB需要更多的内存和存储，它会在主内存中建立其专用的缓冲池用于高速缓冲数据和索引。
* **可移植性、备份及恢复**。MyISAM数据是以文件的形式存储，所以在跨平台的数据转移中会很方便。在备份和恢复时可单独针对某个表进行操作。对于InnoDB，可行的方案是拷贝数据文件、备份 binlog，或者用mysqldump，在数据量达到几十G的时候就相对麻烦了。
* **是否支持行级锁**。MyISAM 只支持表级锁，用户在操作myisam表时，select，update，delete，insert语句都会给表自动加锁，如果加锁以后的表满足insert并发的情况下，可以在表的尾部插入新的数据。而InnoDB 支持行级锁和表级锁，默认为行级锁。行锁大幅度提高了多用户并发操作的性能。
* **是否支持事务和崩溃后的安全恢复**。 MyISAM 不提供事务支持。而InnoDB 提供事务支持，具有事务、回滚和崩溃修复能力。
* **是否支持外键**。MyISAM不支持，而InnoDB支持。
* **是否支持MVCC**。MyISAM不支持，InnoDB支持。应对高并发事务，MVCC比单纯的加锁更高效。
* **是否支持聚集索引**。MyISAM不支持聚集索引，InnoDB支持聚集索引。
* **全文索引**。MyISAM支持 FULLTEXT类型的全文索引。InnoDB不支持FULLTEXT类型的全文索引，但是innodb可以使用sphinx插件支持全文索引，并且效果更好。
* **表主键**。MyISAM允许没有任何索引和主键的表存在，索引都是保存行的地址。对于InnoDB，如果没有设定主键或者非空唯一索引，就会自动生成一个6字节的主键(用户不可见)。
* **表的行数**。MyISAM保存有表的总行数，如果`select count(*) from table`;会直接取出该值。InnoDB没有保存表的总行数，如果使用select count(*) from table；就会遍历整个表，消耗相当大，但是在加了where条件后，MyISAM和InnoDB处理的方式都一样。

---

* **存储结构的区别**。每个MyISAM在磁盘上存储成三个文件。InnoDB所有的表都保存在同一个数据文件中（也可能是多个文件，或者是独立的表空间文件）。

* **存储空间的区别**。MyISAM支持三种不同的存储格式：静态表、动态表、压缩表。当表在创建之后并导入数据之后，不会再进行修改操作，可以使用压缩表，极大的减少磁盘的空间占用。InnoDB需要更多的内存和存储，它会在主内存中建立其专用的缓冲池用于高速缓冲数据和索引。
* **可移植性、备份及恢复**。MyISAM数据是以文件的形式存储，所以在跨平台的数据转移中会很方便。对于InnoDB，可行的方案是拷贝数据文件、备份 binlog，或者用mysqldump，在数据量达到几十G的时候就相对麻烦了。
* **是否支持行级锁**。MyISAM 只支持表级锁，而InnoDB 支持行级锁和表级锁，默认为行级锁。行锁大幅度提高了多用户并发操作的性能。
* **是否支持事务和崩溃后的安全恢复**。 MyISAM 不提供事务支持。而InnoDB 提供事务支持，具有事务、回滚和崩溃修复能力。
* **是否支持外键**。MyISAM不支持，而InnoDB支持。
* **是否支持MVCC**。MyISAM不支持，InnoDB支持。应对高并发事务，MVCC比单纯的加锁更高效。
* **是否支持聚集索引**。MyISAM不支持聚集索引，InnoDB支持聚集索引。
* **全文索引**。MyISAM支持 FULLTEXT类型的全文索引。InnoDB不支持FULLTEXT类型的全文索引，但是innodb可以使用sphinx插件支持全文索引，并且效果更好。
* **表主键**。MyISAM允许没有任何索引和主键的表存在，索引都是保存行的地址。对于InnoDB，如果没有设定主键或者非空唯一索引，就会自动生成一个6字节的主键(用户不可见)。
* **表的行数**。MyISAM保存有表的总行数，如果`select count(*) from table`;会直接取出该值。InnoDB没有保存表的总行数，如果使用select count(*) from table；就会遍历整个表，消耗相当大，但是在加了where条件后，MyISAM和InnoDB处理的方式都一样。

## 10、MySQL有哪些锁

**按锁粒度分类**，有行级锁、表级锁和页级锁。

1. 行级锁是mysql中锁定粒度最细的一种锁。表示只针对当前操作的行进行加锁。行级锁能大大减少数据库操作的冲突，其加锁粒度最小，但加锁的开销也最大。行级锁的类型主要有三类： 
   - Record Lock，记录锁，也就是仅仅把一条记录锁上；
   - Gap Lock，间隙锁，锁定一个范围，但是不包含记录本身；
   - Next-Key Lock：Record Lock + Gap Lock 的组合，锁定一个范围，并且锁定记录本身。
2. 表级锁是mysql中锁定粒度最大的一种锁，表示对当前操作的整张表加锁，它实现简单，资源消耗较少，被大部分mysql引擎支持。最常使用的MyISAM与InnoDB都支持表级锁定。
3. 页级锁是 MySQL 中锁定粒度介于行级锁和表级锁中间的一种锁。表级锁速度快，但冲突多，行级冲突少，但速度慢。因此，采取了折衷的页级锁，一次锁定相邻的一组记录。

**按锁级别分类**，有共享锁、排他锁和意向锁。

1. 共享锁又称读锁，是读取操作创建的锁。其他用户可以并发读取数据，但任何事务都不能对数据进行修改（获取数据上的排他锁），直到已释放所有共享锁。
2. 排他锁又称写锁、独占锁，如果事务T对数据A加上排他锁后，则其他事务不能再对A加任何类型的封锁。获准排他锁的事务既能读数据，又能修改数据。
3. 意向锁是表级锁，其设计目的主要是为了在一个事务中揭示下一行将要被请求锁的类型。InnoDB 中的两个表锁：
   * 意向共享锁（IS）：表示事务准备给数据行加入共享锁，也就是说一个数据行加共享锁前必须先取得该表的IS锁；
   * 意向排他锁（IX）：类似上面，表示事务准备给数据行加入排他锁，说明事务在一个数据行加排他锁前必须先取得该表的IX锁。

意向锁是 InnoDB 自动加的，不需要用户干预。

**对于INSERT、UPDATE和DELETE，InnoDB 会自动给涉及的数据加排他锁；对于一般的SELECT语句，InnoDB 不会加任何锁**，事务可以通过以下语句显式加共享锁或排他锁。

共享锁：`SELECT … LOCK IN SHARE MODE;`

排他锁：`SELECT … FOR UPDATE;`

##  11、MVCC 实现原理

MVCC(`Multiversion concurrency control`) 就是**同一份数据保留多版本的一种方式**，进而实现并发控制。在查询的时候，通过`read view`和版本链找到对应版本的数据。

作用：提升并发性能。对于高并发场景，MVCC比行级锁开销更小。

**MVCC 实现原理如下：**

MVCC 的实现依赖于版本链，版本链是通过表的三个隐藏字段实现。

- `DB_TRX_ID`：当前事务id，通过事务id的大小判断事务的时间顺序。
- `DB_ROLL_PTR`：回滚指针，指向当前行记录的上一个版本，通过这个指针将数据的多个版本连接在一起构成`undo log`版本链。
- `DB_ROW_ID`：主键，如果数据表没有主键，InnoDB会自动生成主键。

每条表记录大概是这样的：

![image-20240321194910340](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321194910340.png)

使用事务更新行记录的时候，就会生成版本链，执行过程如下：

1. 用排他锁锁住该行；
2. 将该行原本的值拷贝到`undo log`，作为旧版本用于回滚；
3. 修改当前行的值，生成一个新版本，更新事务id，使回滚指针指向旧版本的记录，这样就形成一条版本链。

下面举个例子方便大家理解。

1、初始数据如下，其中`DB_ROW_ID`和`DB_ROLL_PTR`为空。

![image-20240321194926502](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321194926502.png)

2、事务A对该行数据做了修改，将`age`修改为12，效果如下：

![image-20240321194936642](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321194936642.png)

3、之后事务B也对该行记录做了修改，将`age`修改为8，效果如下：

![image-20240321194946886](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321194946886.png)

4、此时undo log有两行记录，并且通过回滚指针连在一起。

**接下来了解下read view的概念。**

`read view`可以理解成将数据在每个时刻的状态拍成“照片”记录下来。在获取某时刻t的数据时，到t时间点拍的“照片”上取数据。

在`read view`内部维护一个活跃事务链表，表示生成`read view`的时候还在活跃的事务。这个链表包含在创建`read view`之前还未提交的事务，不包含创建`read view`之后提交的事务。

不同隔离级别创建read view的时机不同。

- read committed：每次执行select都会创建新的read_view，保证能读取到其他事务已经提交的修改。
- repeatable read：在一个事务范围内，第一次select时更新这个read_view，以后不会再更新，后续所有的select都是复用之前的read_view。这样可以保证事务范围内每次读取的内容都一样，即可重复读。

------

**read view的记录筛选方式**

**前提**：`DATA_TRX_ID` 表示每个数据行的最新的事务ID；`up_limit_id`表示当前快照中的最先开始的事务；`low_limit_id`表示当前快照中的最慢开始的事务，即最后一个事务。

![image-20240321195018031](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321195018031.png)

- 如果`DATA_TRX_ID` < `up_limit_id`：说明在创建`read view`时，修改该数据行的事务已提交，该版本的记录可被当前事务读取到。

- 如果`DATA_TRX_ID` >= `low_limit_id`：说明当前版本的记录的事务是在创建`read view`之后生成的，该版本的数据行不可以被当前事务访问。此时需要通过版本链找到上一个版本，然后重新判断该版本的记录对当前事务的可见性。

- 如果`up_limit_id` <= `DATA_TRX_ID` < `low_limit_i`

  * 需要在活跃事务链表中查找是否存在ID为`DATA_TRX_ID`的值的事务。

  * 如果存在，因为在活跃事务链表中的事务是未提交的，所以该记录是不可见的。此时需要通过版本链找到上一个版本，然后重新判断该版本的可见性。

  * 如果不存在，说明事务trx_id 已经提交了，这行记录是可见的。

**总结**：InnoDB 的`MVCC`是通过 `read view` 和版本链实现的，版本链保存有历史版本记录，通过`read view` 判断当前版本的数据是否可见，如果不可见，再从版本链中找到上一个版本，继续进行判断，直到找到一个可见的版本。

##  12、快照读和当前读

表记录有两种读取方式。

- 快照读：**读取的是快照版本**。普通的`SELECT`就是快照读。通过mvcc来进行并发控制的，不用加锁。
- 当前读：**读取的是最新版本**。`UPDATE、DELETE、INSERT、SELECT … LOCK IN SHARE MODE、SELECT … FOR UPDATE`是当前读。

快照读情况下，InnoDB通过`mvcc`机制避免了幻读现象。而`mvcc`机制无法避免当前读情况下出现的幻读现象。因为当前读每次读取的都是最新数据，这时如果两次查询中间有其它事务插入数据，就会产生幻读。

下面举个例子说明下：

1、首先，user表只有两条记录，具体如下：

![image-20240321195139043](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321195139043.png)

2、事务a和事务b同时开启事务`start transaction`；

3、事务a插入数据然后提交；

```sql
insert into user(user_name, user_password, user_mail, user_state) values('tyson', 'a', 'a', 0);
```

4、事务b执行全表的update；

```sql
update user set user_name = 'a';
```

5、事务b然后执行查询，查到了事务a中插入的数据。（下图左边是事务b，右边是事务a。事务开始之前只有两条记录，事务a插入一条数据之后，事务b查询出来是三条数据）

![image-20240321195211795](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321195211795.png)

以上就是当前读出现的幻读现象。

**那么MySQL是如何避免幻读？**

- 在快照读情况下，MySQL通过`mvcc`来避免幻读。
- 在当前读情况下，MySQL通过`next-key`来避免幻读（加行锁和间隙锁来实现的）。

next-key包括两部分：行锁和间隙锁。行锁是加在索引上的锁，间隙锁是加在索引之间的。

`Serializable`隔离级别也可以避免幻读，会锁住整张表，并发性极低，一般不会使用。

## 13、共享锁和排他锁

SELECT 的读取锁定主要分为两种方式：共享锁和排他锁。

```sql
select * from table where id<6 lock in share mode;--共享锁
select * from table where id<6 for update;--排他锁
```

这两种方式主要的不同在于`LOCK IN SHARE MODE `多个事务同时更新同一个表单时很容易造成死锁。

申请排他锁的前提是，没有线程对该结果集的任何行数据使用排它锁或者共享锁，否则申请会受到阻塞。在进行事务操作时，MySQL会对查询结果集的每行数据添加排它锁，其他线程对这些数据的更改或删除操作会被阻塞（只能读操作），直到该语句的事务被`commit`语句或`rollback`语句结束为止。

`SELECT... FOR UPDATE` 使用注意事项：

1. `for update` 仅适用于innodb，且必须在事务范围内才能生效。
2. 根据主键进行查询，查询条件为`like`或者不等于，主键字段产生**表锁**。
3. 根据非索引字段进行查询，会产生**表锁**。

## 14、bin log/redo log/undo log

MySQL日志主要包括查询日志、慢查询日志、事务日志、错误日志、二进制日志等。其中比较重要的是 `bin log`（二进制日志）和 `redo log`（重做日志）和 `undo log`（回滚日志）。

**bin log**

`bin log`是MySQL数据库级别的文件，记录对MySQL数据库执行修改的所有操作，不会记录select和show语句，主要用于恢复数据库和同步数据库。

**redo log**

`redo log`是innodb引擎级别，用来记录innodb存储引擎的事务日志，不管事务是否提交都会记录下来，用于数据恢复。当数据库发生故障，innoDB存储引擎会使用`redo log`恢复到发生故障前的时刻，以此来保证数据的完整性。将参数`innodb_flush_log_at_tx_commit`设置为1，那么在执行commit时会将`redo log`同步写到磁盘。

**undo log**

除了记录`redo log`外，当进行数据修改时还会记录`undo log`，`undo log`用于数据的撤回操作，它保留了记录修改前的内容。通过`undo log`可以实现事务回滚，并且可以根据`undo log`回溯到某个特定的版本的数据，**实现MVCC**。

## 15、bin log和redo log有什么区别

* `bin log`会记录所有日志记录，包括InnoDB、MyISAM等存储引擎的日志；`redo log`只记录innoDB自身的事务日志。

* `bin log`只在事务提交前写入到磁盘，一个事务只写一次；而在事务进行过程，会有`redo log`不断写入磁盘。

* `bin log`是逻辑日志，记录的是SQL语句的原始逻辑；`redo log`是物理日志，记录的是在某个数据页上做了什么修改。

## 16、讲一下MySQL架构

MySQL主要分为 Server 层和存储引擎层：

- **Server 层**：主要包括连接器、查询缓存、分析器、优化器、执行器等，所有跨存储引擎的功能都在这一层实现，比如存储过程、触发器、视图，函数等，还有一个通用的日志模块 binglog 日志模块。
- **存储引擎**： 主要负责数据的存储和读取。server 层通过api与存储引擎进行通信。

**Server 层基本组件**

- **连接器：** 当客户端连接 MySQL 时，server层会对其进行身份认证和权限校验。
- **查询缓存:** 执行查询语句的时候，会先查询缓存，先校验这个 sql 是否执行过，如果有缓存这个 sql，就会直接返回给客户端，如果没有命中，就会执行后续的操作。
- **分析器:** 没有命中缓存的话，SQL 语句就会经过分析器，主要分为两步，词法分析和语法分析，先看 SQL 语句要做什么，再检查 SQL 语句语法是否正确。
- **优化器：** 优化器对查询进行优化，包括重写查询、决定表的读写顺序以及选择合适的索引等，生成执行计划。
- **执行器：** 首先执行前会校验该用户有没有权限，如果没有权限，就会返回错误信息，如果有权限，就会根据执行计划去调用引擎的接口，返回结果。

## 17、分库分表

当单表的数据量达到1000W或100G以后，优化索引、添加从库等可能对数据库性能提升效果不明显，此时就要考虑对其进行切分了。切分的目的就在于减少数据库的负担，缩短查询的时间。

数据切分可以分为两种方式：垂直划分和水平划分。

**垂直划分**

垂直划分数据库是根据业务进行划分，例如购物场景，可以将库中涉及商品、订单、用户的表分别划分出成一个库，通过降低单库的大小来提高性能。同样的，分表的情况就是将一个大表根据业务功能拆分成一个个子表，例如商品基本信息和商品描述，商品基本信息一般会展示在商品列表，商品描述在商品详情页，可以将商品基本信息和商品描述拆分成两张表。

![image-20240321195424395](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321195424395.png)

**优点**：行记录变小，数据页可以存放更多记录，在查询时减少I/O次数。

**缺点**：

- 主键出现冗余，需要管理冗余列；
- 会引起表连接JOIN操作，可以通过在业务服务器上进行join来减少数据库压力；
- 依然存在单表数据量过大的问题。

**水平划分**

水平划分是根据一定规则，例如时间或id序列值等进行数据的拆分。比如根据年份来拆分不同的数据库。每个数据库结构一致，但是数据得以拆分，从而提升性能。

![image-20240321195445190](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240321195445190.png)

**优点**：单库（表）的数据量得以减少，提高性能；切分出的表结构相同，程序改动较少。

**缺点**：

- 分片事务一致性难以解决
- 跨节点`join`性能差，逻辑复杂
- 数据分片在扩容时需要迁移

## 18、什么是分区表

分区是把一张表的数据分成N多个区块。分区表是一个独立的逻辑表，但是底层由多个物理子表组成。

当查询条件的数据分布在某一个分区的时候，查询引擎只会去某一个分区查询，而不是遍历整个表。在管理层面，如果需要删除某一个分区的数据，只需要删除对应的分区即可。

分区一般都是放在单机里的，用的比较多的是时间范围分区，方便归档。只不过分库分表需要代码实现，分区则是mysql内部实现。分库分表和分区并不冲突，可以结合使用。

##  19、分区表类型

**range分区**，按照范围分区。比如按照时间范围分区

```sql
CREATE TABLE test_range_partition(
       id INT auto_increment,
       createdate DATETIME,
       primary key (id,createdate)
   ) 
   PARTITION BY RANGE (TO_DAYS(createdate) ) (
      PARTITION p201801 VALUES LESS THAN ( TO_DAYS('20180201') ),
      PARTITION p201802 VALUES LESS THAN ( TO_DAYS('20180301') ),
      PARTITION p201803 VALUES LESS THAN ( TO_DAYS('20180401') ),
      PARTITION p201804 VALUES LESS THAN ( TO_DAYS('20180501') ),
      PARTITION p201805 VALUES LESS THAN ( TO_DAYS('20180601') ),
      PARTITION p201806 VALUES LESS THAN ( TO_DAYS('20180701') ),
      PARTITION p201807 VALUES LESS THAN ( TO_DAYS('20180801') ),
      PARTITION p201808 VALUES LESS THAN ( TO_DAYS('20180901') ),
      PARTITION p201809 VALUES LESS THAN ( TO_DAYS('20181001') ),
      PARTITION p201810 VALUES LESS THAN ( TO_DAYS('20181101') ),
      PARTITION p201811 VALUES LESS THAN ( TO_DAYS('20181201') ),
      PARTITION p201812 VALUES LESS THAN ( TO_DAYS('20190101') )
   );
```

在`/var/lib/mysql/data/`可以找到对应的数据文件，每个分区表都有一个使用#分隔命名的表文件：

```sql
   -rw-r----- 1 MySQL MySQL    65 Mar 14 21:47 db.opt
   -rw-r----- 1 MySQL MySQL  8598 Mar 14 21:50 test_range_partition.frm
   -rw-r----- 1 MySQL MySQL 98304 Mar 14 21:50 test_range_partition#P#p201801.ibd
   -rw-r----- 1 MySQL MySQL 98304 Mar 14 21:50 test_range_partition#P#p201802.ibd
   -rw-r----- 1 MySQL MySQL 98304 Mar 14 21:50 test_range_partition#P#p201803.ibd
...
```

**list分区**

list分区和range分区相似，主要区别在于list是枚举值列表的集合，range是连续的区间值的集合。对于list分区，分区字段必须是已知的，如果插入的字段不在分区时的枚举值中，将无法插入。

```sql
create table test_list_partiotion
   (
       id int auto_increment,
       data_type tinyint,
       primary key(id,data_type)
   )partition by list(data_type)
   (
       partition p0 values in (0,1,2,3,4,5,6),
       partition p1 values in (7,8,9,10,11,12),
       partition p2 values in (13,14,15,16,17)
   );
```

**hash分区**

可以将数据均匀地分布到预先定义的分区中。

```sql
create table test_hash_partiotion
   (
       id int auto_increment,
       create_date datetime,
       primary key(id,create_date)
   )partition by hash(year(create_date)) partitions 10;
```

## 20、分区的问题

* 打开和锁住所有底层表的成本可能很高。当查询访问分区表时，MySQL 需要打开并锁住所有的底层表，这个操作在分区过滤之前发生，所以无法通过分区过滤来降低此开销，会影响到查询速度。可以通过批量操作来降低此类开销，比如批量插入、`LOAD DATA INFILE`和一次删除多行数据。

* 维护分区的成本可能很高。例如重组分区，会先创建一个临时分区，然后将数据复制到其中，最后再删除原分区。

* 所有分区必须使用相同的存储引擎。

##  21、查询语句执行流程

查询语句的执行流程如下：权限校验、查询缓存、分析器、优化器、权限校验、执行器、引擎。

举个例子，查询语句如下：

```sql
select * from user where id > 1 and name = '大彬';
```

* 首先检查权限，没有权限则返回错误；

* MySQL8.0以前会查询缓存，缓存命中则直接返回，没有则执行下一步；

* 词法分析和语法分析。提取表名、查询条件，检查语法是否有错误；

* 两种执行方案，先查 `id > 1` 还是 `name = '大彬'`，优化器根据自己的优化算法选择执行效率最好的方案；

* 校验权限，有权限就调用数据库引擎接口，返回引擎的执行结果。

## 22、更新语句执行过程

更新语句执行流程如下：分析器、权限校验、执行器、引擎、`redo log`（`prepare`状态）、`binlog`、`redo log`（`commit`状态）

举个例子，更新语句如下：

```sql
update user set name = '大彬' where id = 1;
```

1. 先查询到 id 为1的记录，有缓存会使用缓存。
2. 拿到查询结果，将 name 更新为大彬，然后调用引擎接口，写入更新数据，innodb 引擎将数据保存在内存中，同时记录`redo log`，此时`redo log`进入 `prepare`状态。
3. 执行器收到通知后记录`binlog`，然后调用引擎接口，提交`redo log`为`commit`状态。
4. 更新完成。

为什么记录完`redo log`，不直接提交，而是先进入`prepare`状态？

假设先写`redo log`直接提交，然后写`binlog`，写完`redo log`后，机器挂了，`binlog`日志没有被写入，那么机器重启后，这台机器会通过`redo log`恢复数据，但是这个时候`binlog`并没有记录该数据，后续进行机器备份的时候，就会丢失这一条数据，同时主从同步也会丢失这一条数据。

## 23、exist和in的区别

> ```sql
> SELECT * FROM A WHERE cc IN (SELECT cc FROM B)；
> ```
>
> ```sql
> SELECT * FROM A WHERE EXISTS (SELECT cc FROM B WHERE B.cc = A.cc)；
> ```
>
> `IN`是在A中选择一条记录，然后在B中查找该记录是否存在。`EXISTS`是在B中选择一条符合条件的记录，然后在A中查找该记录是否存在。

* **In**：确定给定的值是否与子查询或列表中的值相匹配。in在查询的时候，首先查询子查询的表，然后将内表和外表做一个笛卡尔积，然后按照条件进行筛选。所以相对内表比较小的时候，in的速度较快。
* **exists**：指定一个子查询，检测行的存在。循环遍历外表，然后看外表中的记录有没有和内表的数据一样的。匹配上就将结果放入结果集中。

**子查询的表比较大的时候**，使用`exists`可以有效减少总的循环次数来提升速度；**当外查询的表比较大的时候**，使用`in`可以有效减少对外查询表循环遍历来提升速度。

##  24、MySQL中int(10)和char(10)的区别

int(10)中的10表示的是**显示数据**的长度，而char(10)表示的是**存储数据**的长度。

## 25、truncate、delete与drop区别

**相同点：**

1. `truncate`和不带`where`子句的`delete`、以及`drop`都会删除表内的数据。
2. **`drop`、`truncate`都是`DDL`语句（数据定义语言）**，执行后会自动提交。

**不同点：**

1. truncate 和 delete 只删除数据不删除表的结构；**drop 语句将删除表的结构、被依赖的约束、触发器、索引**；
2. 一般来说，**执行速度: drop > truncate > delete**。

## 26、having和where区别？

- 二者作用的对象不同，`where`子句作用于表和视图，`having`作用于组。
- `where`在数据分组前进行过滤，`having`在数据分组后进行过滤。

## 27、什么是MySQL主从同步？

主从同步使得数据可以从一个数据库服务器复制到其他服务器上，在复制数据时，一个服务器充当主服务器（`master`），其余的服务器充当从服务器（`slave`）。

因为复制是异步进行的，所以从服务器不需要一直连接着主服务器，从服务器甚至可以通过拨号断断续续地连接主服务器。通过配置文件，可以指定复制所有的数据库，某个数据库，甚至是某个数据库上的某个表。

## 28、为什么要做主从同步？

1. **读写分离**，使数据库能支撑更大的并发。
2. **在主服务器上生成实时数据，而在从服务器上分析这些数据**，从而提高主服务器的性能。
3. **数据备份**，保证数据的安全。

## 29、乐观锁和悲观锁是什么

数据库中的并发控制是确保在多个事务同时存取数据库中同一数据时不破坏事务的隔离性和一致性以及数据库的一致性。乐观锁和悲观锁是并发控制主要采用的技术手段。

- **悲观锁**：假定会发生并发冲突，会对操作的数据进行加锁，直到提交事务，才会释放锁，其他事务才能进行修改。实现方式：使用数据库中的锁机制。
- **乐观锁**：假设不会发生并发冲突，只在提交操作时检查数据是否被修改过。给表增加`version`字段，在修改提交之前检查`version`与原来取到的`version`值是否相等，若相等，表示数据没有被修改，可以更新，否则，数据为脏数据，不能更新。实现方式：乐观锁一般使用版本号机制或`CAS`算法实现。

## 30、用过processlist吗

`show processlist` 或 `show full processlist` 可以查看当前 MySQL 是否有压力，正在运行的`SQL`，有没有慢`SQL`正在执行。返回参数如下：

1. **id**：线程ID，可以用`kill id`杀死某个线程

2. **db**：数据库名称

3. **user**：数据库用户

4. **host**：数据库实例的IP

5. **command**：当前执行的命令，比如`Sleep`，`Query`，`Connect `等

6. **time**：消耗时间，单位秒

7. state

   ：执行状态，主要有以下状态： 

   - Sleep，线程正在等待客户端发送新的请求
   - Locked，线程正在等待锁
   - Sending data，正在处理`SELECT`查询的记录，同时把结果发送给客户端
   - Kill，正在执行`kill`语句，杀死指定线程
   - Connect，一个从节点连上了主节点
   - Quit，线程正在退出
   - Sorting for group，正在为`GROUP BY`做排序
   - Sorting for order，正在为`ORDER BY`做排序

8. **info**：正在执行的`SQL`语句

## 31、MySQL查询 limit 1000,10 和limit 10 速度一样快吗

两种查询方式。对应 `limit offset, size` 和 `limit size` 两种方式。

而其实 `limit size` ，相当于 `limit 0, size`。也就是从0开始取size条数据。

也就是说，两种方式的**区别在于offset是否为0。**

先来看下limit sql的内部执行逻辑。

MySQL内部分为**server层**和**存储引擎层**。一般情况下存储引擎都用innodb。

server层有很多模块，其中需要关注的是**执行器**是用于跟存储引擎打交道的组件。

执行器可以通过调用存储引擎提供的接口，将一行行数据取出，当这些数据完全符合要求（比如满足其他where条件），则会放到**结果集**中，最后返回给调用mysql的**客户端**。

以主键索引的limit执行过程为例：

执行`select * from xxx order by id limit 0, 10;`，select后面带的是**星号**，也就是要求获得行数据的**所有字段信息。**

server层会调用innodb的接口，在innodb里的主键索引中获取到第0到10条**完整行数据**，依次返回给server层，并放到server层的结果集中，返回给客户端。

把offset搞大点，比如执行的是：`select * from xxx order by id limit 500000, 10;`

server层会调用innodb的接口，由于这次的offset=500000，会在innodb里的主键索引中获取到第0到（500000 + 10）条**完整行数据**，**返回给server层之后根据offset的值挨个抛弃，最后只留下最后面的size条**，也就是10条数据，放到server层的结果集中，返回给客户端。

可以看出，当offset非0时，server层会从引擎层获取到**很多无用的数据**，而获取的这些无用数据都是要耗时的。

因此，mysql查询中 limit 1000,10 会比 limit 10 更慢。原因是 limit 1000,10 会取出1000+10条数据，并抛弃前1000条，这部分耗时更大。

## 32、深分页怎么优化

还是以上面的SQL为空：`select * from xxx order by id limit 500000, 10;`

**方法一**：

从上面的分析可以看出，当offset非常大时，server层会从引擎层获取到很多无用的数据，而当select后面是*号时，就需要拷贝完整的行信息，**拷贝完整数据**相比**只拷贝行数据里的其中一两个列字段**更耗费时间。

因为前面的offset条数据最后都是不要的，没有必要拷贝完整字段，所以可以将sql语句修改成：

```sql
select * from xxx  where id >=(select id from xxx order by id limit 500000, 1) order by id limit 10;
```

先执行子查询 `select id from xxx by id limit 500000, 1`, 这个操作，其实也是将在innodb中的主键索引中获取到`500000+1`条数据，然后server层会抛弃前500000条，只保留最后一条数据的id。

但不同的地方在于，在返回server层的过程中，只会拷贝数据行内的id这一列，而不会拷贝数据行的所有列，当数据量较大时，这部分的耗时还是比较明显的。

在拿到了上面的id之后，假设这个id正好等于500000，那sql就变成了

```sql
select * from xxx  where id >=500000 order by id limit 10;
```

这样innodb再走一次**主键索引**，通过B+树快速定位到id=500000的行数据，时间复杂度是lg(n)，然后向后取10条数据。 

**方法二：**

将所有的数据**根据id主键进行排序**，然后分批次取，将当前批次的最大id作为下次筛选的条件进行查询。

```sql
select * from xxx where id > start_id order by id limit 10;
```

通过主键索引，每次定位到start_id的位置，然后往后遍历10个数据，这样不管数据多大，查询性能都较为稳定。

* 子查询+索引

  > 思路：通过将 select * 转变为 select id，把符合条件的 id 筛选出来后，最后通过嵌套查询的方式按顺序取出 id 对应的行。
  >
  > ```sql
  > -- 优化前
  > select *
  > from people
  > order by create_time desc
  > limit 5000000, 10;
  > 
  > -- 优化后
  > select a.*
  > from people a
  > inner join(
  >     select id
  >     from people
  >     order by create_time desc
  >     limit 5000000, 10
  > ) b ON a.id = b.id;
  > ```

* 联合索引

  > 刚才我们优化后的 SQL 语句如下，是没有 where 条件的。
  >
  > ```sql
  > select a.*
  > from people a
  > inner join(
  >     select id
  >     from people
  >     order by create_time desc
  >     limit 5000010, 10
  > ) b ON a.id = b.id;
  > ```

  > 为了更接近现实场景，假设我们要把 status = 1 的人筛出来，SQL 就要这么写：
  >
  > ```sql
  > select a.*
  > from people a
  > inner join(
  >     select id
  >     from people
  >     where status=1
  >     order by create_time desc
  >     limit 5000010, 10
  > ) b ON a.id = b.id;
  > ```

  > 为了加速这个查询，我们可以创建一个 create_time 和 status 的联合索引，对应的 SQL 语句是：
  >
  > ```sql
  > alter table people add index create_time_status(create_time, status);
  > ```

* where id > start_id

  > 将上一页的查询结果中的最大 id 作为下一页查询的 where 条件，这样可以大幅减少扫描行数，提高查询性能。
  >
  > ```sql
  > select a.*
  > from people a
  > inner join(
  >     select id
  >     from people
  >     where status=1
  >           and id > ${id}
  >     order by create_time desc
  >     limit 10
  > ) b ON a.id = b.id;
  > ```

## 33、高度为3的B+树，可以存放多少数据

InnoDB存储引擎有自己的最小储存单元——页（Page）。

查询InnoDB页大小的命令如下：

```
mysql> show global status like 'innodb_page_size';
+------------------+-------+
| Variable_name    | Value |
+------------------+-------+
| Innodb_page_size | 16384 |
+------------------+-------+
```

可以看出 **innodb 默认的一页大小为 16384B = 16384/1024 = 16kb**。

在MySQL中，B+树一个节点的大小设为一页或页的倍数最为合适。因为如果一个节点的大小 < 1页，那么读取这个节点的时候其实读取的还是一页，这样就造成了资源的浪费。

B+树中**非叶子节点存的是key + 指针**；**叶子节点存的是数据行**。

对于叶子节点，如果一行数据大小为1k，那么一页就能存16条数据。

对于非叶子节点，如果key使用的是bigint，则为8字节，指针在MySQL中为6字节，一共是14字节，则16k能存放 16 * 1024 / 14 = 1170 个索引指针。

于是可以算出，对于一颗高度为2的B+树，根节点存储索引指针节点，那么它有1170个叶子节点存储数据，每个叶子节点可以存储16条数据，一共 1170 x 16 = 18720 条数据。而对于高度为3的B+树，就可以存放 1170 x 1170 x 16 = 21902400 条数据（**两千多万条数据**），也就是对于两千多万条的数据，我们只需要**高度为3**的B+树就可以完成，通过主键查询只需要3次IO操作就能查到对应数据。

所以在 InnoDB 中B+树高度一般为3层时，就能满足千万级的数据存储。

## 34、MySQL单表多大进行分库分表

目前主流的有两种说法：

1. MySQL 单表数据量大于 2000 万行，性能会明显下降，考虑进行分库分表。
2. 阿里巴巴《Java 开发手册》提出单表行数超过 500 万行或者单表容量超过 2GB，才推荐进行分库分表。

事实上，这个数值和实际记录的条数无关，而与 MySQL 的配置以及机器的硬件有关。因为MySQL为了提高性能，会将表的索引装载到内存中。在InnoDB buffer size 足够的情况下，其能完成全加载进内存，查询不会有问题。但是，当单表数据库到达某个量级的上限时，导致内存无法存储其索引，使得之后的 SQL 查询会产生磁盘 IO，从而导致性能下降。当然，这个还有具体的表结构的设计有关，最终导致的问题都是内存限制。

因此，对于分库分表，需要结合实际需求，不宜过度设计，在项目一开始不采用分库与分表设计，而是随着业务的增长，在无法继续优化的情况下，再考虑分库与分表提高系统的性能。对此，阿里巴巴《Java 开发手册》补充到：如果预计三年后的数据量根本达不到这个级别，请不要在创建表时就分库分表。

至于MySQL单表多大进行分库分表，应当根据机器资源进行评估。

## 35、大表查询慢怎么优化

某个表有近千万数据，查询比较慢，如何优化？

当MySQL单表记录数过大时，数据库的性能会明显下降，一些常见的优化措施如下：

- **合理建立索引**。在合适的字段上建立索引，例如在WHERE和ORDER BY命令上涉及的列建立索引，可根据EXPLAIN来查看是否用了索引还是全表扫描
- **索引优化，SQL优化**。索引要符合最左匹配原则等，参考：[https://topjavaer.cn/database/mysql.html#什么是覆盖索引open in new window](https://topjavaer.cn/database/mysql.html#什么是覆盖索引)
- **建立分区**。对关键字段建立水平分区，比如时间字段，若查询条件往往通过时间范围来进行查询，能提升不少性能
- **利用缓存**。利用Redis等缓存热点数据，提高查询效率
- **限定数据的范围**。比如：用户在查询历史信息的时候，可以控制在一个月的时间范围内
- **读写分离**。经典的数据库拆分方案，主库负责写，从库负责读
- 通过**分库分表**的方式进行优化，主要有垂直拆分和水平拆分
- **数据异构到es**
- **冷热数据分离**。几个月之前不常用的数据放到冷库中，最新的数据或比较新的数据放到热库中

## 36、说说count(1)、count(*)和count(字段名)的区别

嗯，先说说count(1) and count(字段名)的区别。

两者的主要区别是

1. count(1) 会统计表中的所有的记录数，包含字段为null 的记录。
2. count(字段名) 会统计该字段在表中出现的次数，忽略字段为null 的情况。即不统计字段为null 的记录。

接下来看看三者之间的区别。

执行效果上：

- count(*)包括了所有的列，相当于行数，在统计结果的时候，**不会忽略列值为NULL**
- count(1)包括了忽略所有列，用1代表代码行，在统计结果的时候，**不会忽略列值为NULL**
- count(字段名)只包括列名那一列，在统计结果的时候，会忽略列值为空（这里的空不是只空字符串或者0，而是表示null）的计数，**即某个字段值为NULL时，不统计**。

执行效率上：

- 列名为主键，count(字段名)会比count(1)快
- 列名不为主键，count(1)会比count(列名)快
- 如果表多个列并且没有主键，则 count(1) 的执行效率优于 count(*)
- 如果有主键，则 select count(主键)的执行效率是最优的
- 如果表只有一个字段，则 select count(*)最优。

**COUNT(`*`)是SQL92定义的标准统计行数的语法，效率高，MySQL对它进行了很多优化，MyISAM中会直接把表的总行数单独记录下来供COUNT(*)查询，而InnoDB则会在扫表的时候选择最小的索引来降低成本**。

## 37、MySQL中DATETIME 和 TIMESTAMP有什么区别

嗯，`TIMESTAMP`和`DATETIME`都可以用来存储时间，它们主要有以下区别：

1.表示范围

- DATETIME：1000-01-01 00:00:00.000000 到 9999-12-31 23:59:59.999999
- TIMESTAMP：'1970-01-01 00:00:01.000000' UTC 到 '2038-01-09 03:14:07.999999' UTC

`TIMESTAMP`支持的时间范围比`DATATIME`要小，容易出现超出的情况。

2.空间占用

- TIMESTAMP ：占 4 个字节
- DATETIME：在 MySQL 5.6.4 之前，占 8 个字节 ，之后版本，占 5 个字节

3.存入时间是否会自动转换

`TIMESTAMP`类型在默认情况下，insert、update 数据时，`TIMESTAMP`列会自动以当前时间（`CURRENT_TIMESTAMP`）填充/更新。`DATETIME`则不会做任何转换，也不会检测时区，你给什么数据，它存什么数据。

4.`TIMESTAMP`比较受时区timezone的影响以及MYSQL版本和服务器的SQL MODE的影响。因为`TIMESTAMP`存的是时间戳，在不同的时区得出的时间不一致。

5.如果存进NULL，两者实际存储的值不同。

- TIMESTAMP：会自动存储当前时间 now() 。
- DATETIME：不会自动存储当前时间，会直接存入 NULL 值。

## 38、说说为什么不建议用外键

外键是一种约束，这个约束的存在，会保证表间数据的关系始终完整。外键的存在，并非全然没有优点。

外键可以保证数据的完整性和一致性，级联操作方便。而且使用外键可以将数据完整性判断托付给了数据库完成，减少了程序的代码量。

虽然外键能够保证数据的完整性，但是会给系统带来很多缺陷。

1、并发问题。在使用外键的情况下，每次修改数据都需要去另外一个表检查数据，需要获取额外的锁。若是在高并发大流量事务场景，使用外键更容易造成死锁。

2、扩展性问题。比如从`MySQL`迁移到`Oracle`，外键依赖于数据库本身的特性，做迁移可能不方便。

3、不利于分库分表。在水平拆分和分库的情况下，外键是无法生效的。将数据间关系的维护，放入应用程序中，为将来的分库分表省去很多的麻烦。

## 39、使用自增主键有什么好处

自增主键可以让主键索引尽量地保持递增顺序插入，避免了页分裂，因此索引更紧凑，在查询的时候，效率也就更高。

## 40、自增主键保存在什么地方

不同的引擎对于自增值的保存策略不同：

- **MyISAM引擎的自增值保存在数据文件中**。
- 在MySQL8.0以前，InnoDB引擎的自增值是存在内存中。MySQL重启之后内存中的这个值就丢失了，每次重启后第一次打开表的时候，会找自增值的最大值max(id)，然后将最大值加1作为这个表的自增值；MySQL8.0版本会将自增值的变更记录在redo log中，重启时依靠redo log恢复。

## 41、自增主键一定是连续的吗

不一定，有几种情况会导致自增主键不连续。

1、**唯一键冲突导致自增主键不连续**。当我们向一个自增主键的InnoDB表中插入数据的时候，如果违反表中定义的唯一索引的唯一约束，会导致插入数据失败。此时表的自增主键的键值是会向后加1滚动的。下次再次插入数据的时候，就不能再使用上次因插入数据失败而滚动生成的键值了，必须使用新滚动生成的键值。

2、**事务回滚导致自增主键不连续**。当我们向一个自增主键的InnoDB表中插入数据的时候，如果显式开启了事务，然后因为某种原因最后回滚了事务，此时表的自增值也会发生滚动，而接下里新插入的数据，也将不能使用滚动过的自增值，而是需要重新申请一个新的自增值。

3、**批量插入导致自增值不连续**。MySQL有一个批量申请自增id的策略：

- 语句执行过程中，第一次申请自增id，分配1个自增id
- 1个用完以后，第二次申请，会分配2个自增id
- 2个用完以后，第三次申请，会分配4个自增id
- 依次类推，每次申请都是上一次的两倍（最后一次申请不一定全部使用）

如果下一个事务再次插入数据的时候，则会基于上一个事务申请后的自增值基础上再申请。此时就出现自增值不连续的情况出现。

4、**自增步长不是1**，也会导致自增主键不连续。

## 42、InnoDB的自增值为什么不能回收利用

**主要为了提升插入数据的效率和并行度**。

假设有两个并行执行的事务，在申请自增值的时候，为了避免两个事务申请到相同的自增 id，肯定要加锁，然后顺序申请。

假设事务 A 申请到了 id=2， 事务 B 申请到 id=3，那么这时候表 t 的自增值是 4，之后继续执行。

事务 B 正确提交了，但事务 A 出现了唯一键冲突。

如果允许事务 A 把自增 id 回退，也就是把表 t 的当前自增值改回 2，那么就会出现这样的情况：表里面已经有 id=3 的行，而当前的自增 id 值是 2。

接下来，继续执行的其他事务就会申请到 id=2，然后再申请到 id=3。这时，就会出现插入语句报错“主键冲突”。

而为了解决这个主键冲突，有两种方法：

- 每次申请 id 之前，先判断表里面是否已经存在这个 id。如果存在，就跳过这个 id。但是，这个方法的成本很高。因为，本来申请 id 是一个很快的操作，现在还要再去主键索引树上判断 id 是否存在。
- 把自增 id 的锁范围扩大，必须等到一个事务执行完成并提交，下一个事务才能再申请自增 id。这个方法的问题，就是锁的粒度太大，系统并发能力大大下降。

可见，这两个方法都会导致性能问题。

因此，InnoDB 放弃了“允许自增 id 回退”这个设计，语句执行失败也不回退自增 id。

## 43、MySQL数据如何同步到Redis缓存

有两种方案：

1、通过MySQL自动同步刷新Redis，**MySQL触发器+UDF函数**实现。

> UDF函数：常见的函数类型，可以操作单个数据行，且产生一个数据行作为输出，大多数函数为这一类。

过程大致如下：

1. 在MySQL中对要操作的数据设置触发器Trigger，监听操作
2. 客户端向MySQL中写入数据时，触发器会被触发，触发之后调用MySQL的UDF函数
3. UDF函数可以把数据写入到Redis中，从而达到同步的效果

2、**解析MySQL的binlog**，实现将数据库中的数据同步到Redis。可以通过canal实现。canal是阿里巴巴旗下的一款开源项目，基于数据库增量日志解析，提供增量数据订阅&消费。

canal的原理如下：

1. canal模拟mysql slave的交互协议，伪装自己为mysql slave，向mysql master发送dump协议
2. mysql master收到dump请求，开始推送binary log给canal
3. canal解析binary log对象（原始为byte流），将数据同步写入Redis。

## 44、为什么阿里Java手册禁止使用存储过程

先看看什么是存储过程。

存储过程是在大型数据库系统中，一组为了完成特定功能的SQL 语句集，它存储在数据库中，一次编译后永久有效，用户通过指定存储过程的名字并给出参数（如果该存储过程带有参数）来执行它。

存储过程主要有以下几个缺点。

1. **存储过程难以调试**。存储过程的开发一直缺少有效的 IDE 环境。SQL 本身经常很长，调试时要把句子拆开分别独立执行，非常麻烦。
2. **移植性差**。存储过程的移植困难，一般业务系统总会不可避免地用到数据库独有的特性和语法，更换数据库时这部分代码就需要重写，成本较高。
3. **管理困难**。存储过程的目录是扁平的，而不是文件系统那样的树形结构，脚本少的时候还好办，一旦多起来，目录就会陷入混乱。
4. 存储过程是**只优化一次**，有的时候随着数据量的增加或者数据结构的变化，原来存储过程选择的执行计划也许并不是最优的了，所以这个时候需要手动干预或者重新编译了。

## 45、MySQL update 是锁行还是锁表？

首先，InnoDB行锁是通过给索引上的索引项加锁来实现的，只有通过索引条件检索数据，InnoDB才使用行级锁，否则，InnoDB将使用表锁。

1. 当执行update语句时，where中的过滤条件列，如果用到索引，就是锁行；如果无法用索引，就是锁表。
2. 如果两个update语句同时执行，第一个先执行触发行锁，但是第二个没有索引触发表锁，因为有个行锁住了，所以还是会等待行锁释放，才能锁表。
3. 当执行insert或者delete语句时，锁行。

## 46、select...for update会锁表还是锁行？

如果查询条件用了索引/主键，那么`select ... for update`就会加行锁。

如果是普通字段(没有索引/主键)，那么`select ..... for update`就会加表锁。

## 47、MySQL的binlog有几种格式？分别有什么区别？

有三种格式，**statement，row和mixed**。

- statement：**每一条会修改数据的sql都会记录在binlog中**。不需要记录每一行的变化，减少了binlog日志量，节约了IO，提高性能。由于sql的执行是有上下文的，因此**在保存的时候需要保存相关的信息**，同时还有一些使用了函数之类的语句无法被记录复制。
- row：**不记录sql语句上下文相关信息，仅保存哪条记录被修改**。记录单元为每一行的改动，由于很多操作，会导致大量行的改动(比如alter table)，因此这种模式的文件保存的信息太多，日志量太大。
- mixed：一种折中的方案，普通操作使用statement记录，当无法使用statement的时候使用row。

## 48、阿里手册为什么禁止使用 count(列名)或 count(常量)来替代 count(*)

先看下这几种方式的区别。

count(主键id)：InnoDB引擎会遍历整张表，把每一行id值都取出来，返给server层。server层拿到id后，判断是不可能为空的，就按行累加，不再对每个值进行NULL判断。

count(常量)：InnoDB引擎会遍历整张表，但不取值。server层对于返回的每一行，放一个常量进去，判断是不可能为空的，按行累加，不再对每个值进行NULL判断。count(常量)比count(主键id)执行的要快，因为从引擎放回id会涉及解析数据行，以及拷贝字段值的操作。

count(字段)：全表扫描，分情况讨论。

1、如果参数字段定义NOT NULL，判断是不可能为空的，按行累加，不再对每个值进行NULL判断。 2、如果参数字段定义允许为NULL，那么执行的时候，判断可能是NULL，还要把值取出来再判断一下，不是NULL才累加。

count(*)：统计所有的列，相当于行数，统计结果中会包含字段值为null的列；

**COUNT(`*`)是SQL92定义的标准统计行数的语法，效率高，MySQL对它进行了很多优化，MyISAM中会直接把表的总行数单独记录下来供COUNT(*)查询，而InnoDB则会在扫表的时候选择最小的索引来降低成本**。

所以，建议使用COUNT(*)查询表的行数！

## 49、存储MD5值应该用VARCHAR还是用CHAR？

首先说说CHAR和VARCHAR的区别：

1、存储长度：

**CHAR类型的长度是固定的**

当我们当定义CHAR(10)，输入的值是"abc"，但是它占用的空间一样是10个字节，会包含7个空字节。当输入的字符长度超过指定的数时，CHAR会截取超出的字符。而且，当存储为CHAR的时候，MySQL会自动删除输入字符串末尾的空格。

**VARCHAR的长度是可变的**

比如VARCHAR(10)，然后输入abc三个字符，那么实际存储大小为3个字节。

除此之外，**VARCHAR还会保留1个或2个额外的字节来记录字符串的实际长度**。如果定义的最大长度小于等于255个字节，那么，就会预留1个字节；如果定义的最大长度大于255个字节，那么就会预留2个字节。

2、存储效率

**CHAR类型每次修改后的数据长度不变，效率更高**。

VARCHAR每次修改的数据要更新数据长度，效率更低。

3、存储空间

CHAR存储空间是**初始的预计长度字符串再加上一个记录字符串长度的字节**，可能会存在多余的空间。

VARCHAR存储空间的时候是**实际字符串再加上一个记录字符串长度的字节**，占用空间较小。

根据以上的分析，由于**MD5是一个定长的值，所以MD5值适合使用CHAR存储**。对于固定长度的非常短的列，CHAR比VARCHAR效率也更高。

# 七、Redis

## 1、Redis是什么

Redis（`Remote Dictionary Server`）是一个使用 C 语言编写的，高性能非关系型的键值对数据库。与传统数据库不同的是，Redis 的数据是存在内存中的，所以读写速度非常快，被广泛应用于缓存方向。Redis可以将数据写入磁盘中，保证了数据的安全不丢失，而且Redis的操作是原子性的。

## 2、Redis优缺点？

> * RDB 是 Redis 默认的持久化方案。RDB持久化时会将内存中的数据写入到磁盘中，在指定目录下生成一个dump.rdb文件。Redis 重启会加载dump.rdb文件恢复数据。
>
>   RDB持久化的过程（执行SAVE命令除外）：
>
>   - 创建一个子进程；
>   - 父进程继续接收并处理客户端的请求，而子进程开始将内存中的数据写进硬盘的临时文件；
>   - 当子进程写完所有数据后会用该临时文件替换旧的RDB文件。
>
>   Redis启动时会读取RDB快照文件，将数据从硬盘载入内存。通过RDB方式的持久化，一旦Redis异常退出，就会丢失最近一次持久化以后更改的数据。
>
> * AOF（append only file）持久化：以独立日志的方式记录每次写命令，Redis重启时会重新执行AOF文件中的命令达到恢复数据的目的。AOF的主要作用是**解决了数据持久化的实时性**，目前已经是Redis持久化的主流方式。

**优点**：

1. **基于内存操作**，内存读写速度快。
2. **支持多种数据类型**，包括String、Hash、List、Set、ZSet等。
3. **支持持久化**。Redis支持RDB和AOF两种持久化机制，持久化功能可以有效地避免数据丢失问题。
4. **支持事务**。Redis的所有操作都是原子性的，同时Redis还支持对几个操作合并后的原子性执行。
5. **支持主从复制**。主节点会自动将数据同步到从节点，可以进行读写分离。
6. Redis命令的处理是**单线程**的。Redis6.0引入了多线程，需要注意的是，**多线程用于处理网络数据的读写和协议解析**，Redis命令执行还是单线程的。

**缺点**：

1. 对结构化查询的支持比较差。
2. 数据库容量受到物理内存的限制，不适合用作海量数据的高性能读写，因此**Redis适合的场景主要局限在较小数据量的操作**。
3. Redis **较难支持在线扩容**，在集群容量达到上限时在线扩容会变得很复杂。

## 3、Redis为什么这么快？

- **基于内存**：Redis是使用内存存储，没有磁盘IO上的开销。数据存在内存中，读写速度快。
- **IO多路复用模型**：Redis 采用 IO 多路复用技术。Redis 使用单线程来轮询描述符，将数据库的操作都转换成了事件，不在网络I/O上浪费过多的时间。
- **高效的数据结构**：Redis 每种数据类型底层都做了优化，目的就是为了追求更快的速度。
- **持久化机制**：尽管Redis主要是一个内存[数据库](https://cloud.tencent.com/solution/database?from_column=20065&from=20065)，但它也支持将数据持久化到磁盘。Redis提供了两种持久化选项：快照（snapshot）和日志（append-only file）。这些机制确保了即使在服务器重启时，数据也不会丢失，从而满足了一些需要持久化数据的应用场景。
- **响应式设计**：Redis的设计非常响应式，它能够以微秒级的延迟响应请求。这对于需要实时数据处理的应用程序非常关键，如实时分析、聊天应用和实时游戏等。

## 4、既然Redis那么快，为什么不用它做主数据库，只用它做缓存？

虽然Redis非常快，但它也有一些**局限性**，不能完全替代主数据库。有以下原因：

* **事务处理：**Redis只支持简单的事务处理，对于复杂的事务无能为力，比如跨多个键的事务处理。

* **数据持久化：**Redis是内存数据库，数据存储在内存中，如果服务器崩溃或断电，数据可能丢失。虽然Redis提供了数据持久化机制，但有一些限制。

* **数据处理：**Redis只支持一些简单的数据结构，比如字符串、列表、哈希表等。如果需要处理复杂的数据结构，比如关系型数据库中的表，那么Redis可能不是一个好的选择。

* **数据安全：**Redis没有提供像主数据库那样的安全机制，比如用户认证、访问控制等等。

因此，虽然Redis非常快，但它还有一些限制，不能完全替代主数据库。所以，使用Redis作为缓存是一种很好的方式，可以提高应用程序的性能，并减少数据库的负载。

## 5、讲讲Redis的线程模型？

Redis基于Reactor模式开发了网络事件处理器，这个处理器被称为文件事件处理器。它的组成结构为4部分：多个套接字、IO多路复用程序、文件事件分派器、事件处理器。因为文件事件分派器队列的消费是单线程的，所以Redis才叫单线程模型。

- 文件事件处理器使用I/O多路复用（multiplexing）程序来同时监听多个套接字， 并根据套接字目前执行的任务来为套接字关联不同的事件处理器。
- 当被监听的套接字准备好执行连接accept、read、write、close等操作时， 与操作相对应的文件事件就会产生， 这时文件事件处理器就会调用套接字之前关联好的事件处理器来处理这些事件。

虽然文件事件处理器以单线程方式运行， 但通过使用 I/O 多路复用程序来监听多个套接字， 文件事件处理器既实现了高性能的网络通信模型， 又可以很好地与 redis 服务器中其他同样以单线程方式运行的模块进行对接， 这保持了 Redis 内部单线程设计的简单性。

## 6、Redis应用场景有哪些？

1. **缓存热点数据**，缓解数据库的压力。
2. 利用 Redis 原子性的自增操作，可以实现**计数器**的功能，比如统计用户点赞数、用户访问数等。
3. **分布式锁**。在分布式场景下，无法使用单机环境下的锁来对多个节点上的进程进行同步。可以使用 Redis 自带的 SETNX 命令实现分布式锁，除此之外，还可以使用官方提供的 RedLock 分布式锁实现。
4. **简单的消息队列**，可以使用Redis自身的发布/订阅模式或者List来实现简单的消息队列，实现异步操作。
5. **限速器**，可用于限制某个用户访问某个接口的频率，比如**秒杀场景用于防止用户快速点击带来不必要的压力**。
6. **好友关系**，利用集合的一些命令，比如交集、并集、差集等，实现共同好友、共同爱好之类的功能。

## 7、Memcached和Redis的区别？

1. MemCached 数据结构单一，仅用来缓存数据，而 **Redis 支持多种数据类型**。
2. MemCached 不支持数据持久化，重启后数据会消失。**Redis 支持数据持久化**。
3. **Redis 提供主从同步机制和 cluster 集群部署能力**，能够提供高可用服务。Memcached 没有提供原生的集群模式，需要依靠客户端实现往集群中分片写入数据。
4. Redis 的速度比 Memcached 快很多。
5. Redis 使用**单线程的多路 IO 复用模型**，Memcached使用多线程的非阻塞 IO 模型。（Redis6.0引入了多线程IO，**用来处理网络数据的读写和协议解析**，但是命令的执行仍然是单线程）
6. value 值大小不同：Redis 最大可以达到 512M；memcache 只有 1mb。

## 8、为什么要用 Redis 而不用 map/guava 做缓存?

使用自带的 map 或者 guava 实现的是**本地缓存**，最主要的特点是轻量以及快速，生命周期随着 jvm 的销毁而结束，并且在多实例的情况下，每个实例都需要各自保存一份缓存，缓存不具有一致性。

使用 redis 或 memcached 之类的称为**分布式缓存**，在多实例的情况下，各实例共用一份缓存数据，缓存具有一致性。

## 9、Redis 数据类型有哪些？

**基本数据类型**：

1、**String**：最常用的一种数据类型，String类型的值可以是字符串、数字或者二进制，但值最大不能超过512MB。

2、**Hash**：Hash 是一个键值对集合。

3、**Set**：无序去重的集合。Set 提供了交集、并集等方法，对于实现共同好友、共同关注等功能特别方便。

4、**List**：有序可重复的集合，底层是依赖双向链表实现的。

5、**SortedSet**：有序Set。内部维护了一个`score`的参数来实现。适用于排行榜和带权重的消息队列等场景。

**特殊的数据类型**：

1、**Bitmap**：位图，可以认为是一个以位为单位数组，数组中的每个单元只能存0或者1，数组的下标在 Bitmap 中叫做偏移量。Bitmap的长度与集合中元素个数无关，而是与基数的上限有关。二值状态统计的场景，比如签到、判断用户登陆状态、连续签到用户总数等

2、**Hyperloglog**。HyperLogLog 是用来做基数统计的算法，其优点是，在输入元素的数量或者体积非常非常大时，计算基数所需的空间总是固定的、并且是很小的。典型的使用场景是统计独立访客。

3、**Geospatial** ：主要用于存储地理位置信息，并对存储的信息进行操作，适用场景如定位、附近的人等。

4、**Stream**：消息队列，相比于基于 List 类型实现的消息队列，有这两个特有的特性：自动生成全局唯一消息ID，支持以消费组形式消费数据。

## 10、SortedSet和List异同点？

**相同点**：

1. 都是有序的；
2. 都可以获得某个范围内的元素。

**不同点：**

1. 列表基于链表实现，获取两端元素速度快，访问中间元素速度慢；
2. 有序集合基于散列表和跳跃表实现，访问中间元素时间复杂度是OlogN；
3. 列表不能简单的调整某个元素的位置，有序列表可以（更改元素的分数）；
4. 有序集合更耗内存。

## 11、Redis的内存用完了会怎样？

如果达到设置的上限，Redis的写命令会返回错误信息（但是读命令还可以正常返回）。

也可以配置内存淘汰机制，当Redis达到内存上限时会冲刷掉旧的内容。

## 12、Redis如何做内存优化？

可以好好利用Hash,list,sorted set,set等集合类型数据，因为通常情况下很多小的Key-Value可以用更紧凑的方式存放到一起。尽可能使用散列表（hashes），散列表（是说散列表里面存储的数少）使用的内存非常小，所以你应该尽可能的将你的数据模型抽象到一个散列表里面。比如你的web系统中有一个用户对象，不要为这个用户的名称，姓氏，邮箱，密码设置单独的key，而是应该把这个用户的所有信息存储到一张散列表里面。

## 13、keys命令存在的问题？

redis的单线程的。keys指令会导致线程阻塞一段时间，直到执行完毕，服务才能恢复。scan采用渐进式遍历的方式来解决keys命令可能带来的阻塞问题，每次scan命令的时间复杂度是`O(1)`，但是要真正实现keys的功能，需要执行多次scan。

scan的缺点：在scan的过程中如果有键的变化（增加、删除、修改），遍历过程可能会有以下问题：新增的键可能没有遍历到，遍历出了重复的键等情况，也就是说scan并不能保证完整的遍历出来所有的键。

## 14、Redis事务

事务的原理是将一个事务范围内的若干命令发送给Redis，然后再让Redis依次执行这些命令。

事务的生命周期：

1. 使用MULTI开启一个事务
2. 在开启事务的时候，每次操作的命令将会被插入到一个队列中，同时这个命令并不会被真的执行
3. EXEC命令进行提交事务

![image-20240328094225158](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094225158.png)

一个事务范围内某个命令出错不会影响其他命令的执行，不保证原子性：

```java
127.0.0.1:6379> multi
OK
127.0.0.1:6379> set a 1
QUEUED
127.0.0.1:6379> set b 1 2
QUEUED
127.0.0.1:6379> set c 3
QUEUED
127.0.0.1:6379> exec
1) OK
2) (error) ERR syntax error
3) OK
```

**WATCH命令**

`WATCH`命令可以监控一个或多个键，一旦其中有一个键被修改，之后的事务就不会执行（类似于乐观锁）。执行`EXEC`命令之后，就会自动取消监控。

```java
127.0.0.1:6379> watch name
OK
127.0.0.1:6379> set name 1
OK
127.0.0.1:6379> multi
OK
127.0.0.1:6379> set name 2
QUEUED
127.0.0.1:6379> set gender 1
QUEUED
127.0.0.1:6379> exec
(nil)
127.0.0.1:6379> get gender
(nil)
```

比如上面的代码中：

1. `watch name`开启了对`name`这个`key`的监控
2. 修改`name`的值
3. 开启事务a
4. 在事务a中设置了`name`和`gender`的值
5. 使用`EXEC`命令进提交事务
6. 使用命令`get gender`发现不存在，即事务a没有执行

使用`UNWATCH`可以取消`WATCH`命令对`key`的监控，所有监控锁将会被取消。

## 15、Redis事务支持隔离性吗？

Redis 是单进程程序，并且它保证在执行事务时，不会对事务进行中断，事务可以运行直到执行完所有事务队列中的命令为止。因此，Redis 的事务是总是带有隔离性的。

## 16、Redis事务保证原子性吗，支持回滚吗？

Redis单条命令是原子性执行的，但事务不保证原子性，且没有回滚。事务中任意命令执行失败，其余的命令仍会被执行。

## 17、持久化机制

持久化就是把**内存的数据写到磁盘中**，防止服务宕机导致内存数据丢失。

Redis支持两种方式的持久化，一种是`RDB`的方式，一种是`AOF`的方式。**前者会根据指定的规则定时将内存中的数据存储在硬盘上**，而**后者在每次执行完命令后将命令记录下来**。一般将两者结合使用。

**RDB方式**

`RDB`是 Redis 默认的持久化方案。RDB持久化时会将内存中的数据写入到磁盘中，在指定目录下生成一个`dump.rdb`文件。Redis 重启会加载`dump.rdb`文件恢复数据。

`bgsave`是主流的触发 RDB 持久化的方式，执行过程如下：

![image-20240328094344166](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094344166.png)

* 执行`BGSAVE`命令
* Redis 父进程判断当前**是否存在正在执行的子进程**，如果存在，`BGSAVE`命令直接返回。
* 父进程执行`fork`操作**创建子进程**，fork操作过程中父进程会阻塞。
* 父进程`fork`完成后，**父进程继续接收并处理客户端的请求**，而**子进程开始将内存中的数据写进硬盘的临时文件**；
* 当子进程写完所有数据后会**用该临时文件替换旧的 RDB 文件**。

Redis启动时会读取RDB快照文件，将数据从硬盘载入内存。通过 RDB 方式的持久化，一旦Redis异常退出，就会丢失最近一次持久化以后更改的数据。

触发 RDB 持久化的方式：

1. **手动触发**：用户执行`SAVE`或`BGSAVE`命令。`SAVE`命令执行快照的过程会阻塞所有客户端的请求，应避免在生产环境使用此命令。`BGSAVE`命令可以在后台异步进行快照操作，快照的同时服务器还可以继续响应客户端的请求，因此需要手动执行快照时推荐使用`BGSAVE`命令。
2. **被动触发**：
   - 根据配置规则进行自动快照，如`SAVE 100 10`，100秒内至少有10个键被修改则进行快照。
   - 如果从节点执行全量复制操作，主节点会自动执行`BGSAVE`生成 RDB 文件并发送给从节点。
   - 默认情况下执行`shutdown`命令时，如果没有开启 AOF 持久化功能则自动执行·BGSAVE·。

**优点**：

1. **Redis 加载 RDB 恢复数据远远快于 AOF 的方式**。
2. 使用单独子进程来进行持久化，主进程不会进行任何 IO 操作，**保证了 Redis 的高性能**。

**缺点**：

1. **RDB方式数据无法做到实时持久化**。因为`BGSAVE`每次运行都要执行`fork`操作创建子进程，属于重量级操作，频繁执行成本比较高。
2. RDB 文件使用特定二进制格式保存，Redis 版本升级过程中有多个格式的 RDB 版本，**存在老版本 Redis 无法兼容新版 RDB 格式的问题**。

**AOF方式**

AOF（append only file）持久化：以独立日志的方式记录每次写命令，Redis重启时会重新执行AOF文件中的命令达到恢复数据的目的。AOF的主要作用是**解决了数据持久化的实时性**，AOF 是Redis持久化的主流方式。

默认情况下Redis没有开启AOF方式的持久化，可以通过`appendonly`参数启用：`appendonly yes`。开启AOF方式持久化后每执行一条写命令，Redis就会将该命令写进`aof_buf`缓冲区，AOF缓冲区根据对应的策略向硬盘做同步操作。

默认情况下系统**每30秒**会执行一次同步操作。为了防止缓冲区数据丢失，可以在Redis写入AOF文件后主动要求系统将缓冲区数据同步到硬盘上。可以通过`appendfsync`参数设置同步的时机。

```
appendfsync always //每次写入aof文件都会执行同步，最安全最慢，不建议配置
appendfsync everysec  //既保证性能也保证安全，建议配置
appendfsync no //由操作系统决定何时进行同步操作
```

接下来看一下 AOF 持久化执行流程：

![image-20240328094435610](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094435610.png)

1. 所有的写入命令会追加到 AOP 缓冲区中。
2. AOF 缓冲区根据对应的策略向硬盘同步。
3. 随着 AOF 文件越来越大，需要定期对 AOF 文件进行重写，达到压缩文件体积的目的。AOF文件重写是把Redis进程内的数据转化为写命令同步到新AOF文件的过程。
4. 当 Redis 服务器重启时，可以加载 AOF 文件进行数据恢复。

**优点**：

1. AOF可以更好的保护数据不丢失，可以配置 AOF 每秒执行一次`fsync`操作，如果Redis进程挂掉，最多丢失1秒的数据。
2. AOF以`append-only`的模式写入，所以没有磁盘寻址的开销，写入性能非常高。

**缺点**：

1. 对于同一份文件AOF文件比RDB数据快照要大。
2. 数据恢复比较慢。

## 18、RDB和AOF如何选择？

通常来说，应该同时使用两种持久化方案，以保证数据安全。

- 如果数据不敏感，且可以从其他地方重新生成，可以关闭持久化。
- 如果数据比较重要，且能够承受几分钟的数据丢失，比如缓存等，只需要使用RDB即可。
- 如果是用做内存数据，要使用Redis的持久化，建议是RDB和AOF都开启。
- 如果只用AOF，优先使用everysec的配置选择，因为它在可靠性和性能之间取了一个平衡。

当RDB与AOF两种方式都开启时，Redis会优先使用AOF恢复数据，因为AOF保存的文件比RDB文件更完整。

## 19、Redis有哪些部署方案？

**单机版**：单机部署，单机redis能够承载的 QPS 大概就在上万到几万不等。这种部署方式很少使用。存在的问题：1、内存容量有限 2、处理能力有限 3、无法高可用。

**主从模式**：一主多从，主负责写，并且将数据复制到其它的 slave 节点，从节点负责读。所有的读请求全部走从节点。这样也可以很轻松实现水平扩容，支撑读高并发。master 节点挂掉后，需要手动指定新的 master，可用性不高，基本不用。

**哨兵模式**：主从复制存在不能自动故障转移、达不到高可用的问题。哨兵模式解决了这些问题。通过哨兵机制可以自动切换主从节点。master 节点挂掉后，哨兵进程会主动选举新的 master，可用性高，但是每个节点存储的数据是一样的，浪费内存空间。数据量不是很多，集群规模不是很大，需要自动容错容灾的时候使用。	

**Redis cluster**：服务端分片技术，3.0版本开始正式提供。Redis Cluster并没有使用一致性hash，而是采用slot(槽)的概念，一共分成16384个槽。将请求发送到任意节点，接收到请求的节点会将查询请求发送到正确的节点上执行。主要是针对海量数据+高并发+高可用的场景，如果是海量数据，如果你的数据量很大，那么建议就用Redis cluster，所有主节点的容量总和就是Redis cluster可缓存的数据容量。

## 20、主从架构

单机的 redis，能够承载的 QPS 大概就在上万到几万不等。对于缓存来说，一般都是用来支撑读高并发的。因此架构做成主从(master-slave)架构，一主多从，主负责写，并且将数据复制到其它的 slave 节点，从节点负责读。所有的读请求全部走从节点。这样也可以很轻松实现水平扩容，支撑读高并发。

Redis的复制功能是支持多个数据库之间的数据同步。主数据库可以进行读写操作，当主数据库的数据发生变化时会自动将数据同步到从数据库。从数据库一般是只读的，它会接收主数据库同步过来的数据。一个主数据库可以有多个从数据库，而一个从数据库只能有一个主数据库。

**主从复制的原理？**

1. 当启动一个从节点时，它会发送一个 `PSYNC` 命令给主节点；
2. 如果是从节点初次连接到主节点，那么会触发一次全量复制。此时主节点会启动一个后台线程，开始生成一份 `RDB` 快照文件；
3. 同时还会将从客户端 client 新收到的所有写命令缓存在内存中。`RDB` 文件生成完毕后， 主节点会将`RDB`文件发送给从节点，从节点会先将`RDB`文件**写入本地磁盘，然后再从本地磁盘加载到内存中**；
4. 接着主节点会将内存中缓存的写命令发送到从节点，从节点同步这些数据；
5. 如果从节点跟主节点之间网络出现故障，连接断开了，会自动重连，连接之后主节点仅会将部分缺失的数据同步给从节点。

## 21、哨兵Sentinel

主从复制存在不能自动故障转移、达不到高可用的问题。哨兵模式解决了这些问题。通过哨兵机制可以自动切换主从节点。

客户端连接Redis的时候，先连接哨兵，哨兵会告诉客户端Redis主节点的地址，然后客户端连接上Redis并进行后续的操作。当主节点宕机的时候，哨兵监测到主节点宕机，会重新推选出某个表现良好的从节点成为新的主节点，然后通过发布订阅模式通知其他的从服务器，让它们切换主机。

![image-20240328094527966](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094527966.png)

**工作原理**

- 每个`Sentinel`以每秒钟一次的频率向它所知道的`Master`，`Slave`以及其他 `Sentinel `实例发送一个 `PING`命令。
- 如果一个实例距离最后一次有效回复 `PING` 命令的时间超过指定值， 则这个实例会被 `Sentine` 标记为主观下线。
- 如果一个`Master`被标记为主观下线，则正在监视这个`Master`的所有 `Sentinel `要以每秒一次的频率确认`Master`是否真正进入主观下线状态。
- 当有足够数量的 `Sentinel`（大于等于配置文件指定值）在指定的时间范围内确认`Master`的确进入了主观下线状态， 则`Master`会被标记为客观下线 。若没有足够数量的 `Sentinel `同意 `Master` 已经下线， `Master` 的客观下线状态就会被解除。 若 `Master`重新向 `Sentinel` 的 `PING` 命令返回有效回复， `Master` 的主观下线状态就会被移除。
- 哨兵节点会选举出哨兵 leader，负责故障转移的工作。
- 哨兵 leader 会推选出某个表现良好的从节点成为新的主节点，然后通知其他从节点更新主节点信息。

## 22、Redis cluster

哨兵模式解决了主从复制不能自动故障转移、达不到高可用的问题，但还是存在主节点的写能力、容量受限于单机配置的问题。而cluster模式实现了Redis的分布式存储，每个节点存储不同的内容，解决主节点的写能力、容量受限于单机配置的问题。

Redis cluster集群节点最小配置6个节点以上（3主3从），其中主节点提供读写操作，从节点作为备用节点，不提供请求，只作为故障转移使用。

Redis cluster采用**虚拟槽分区**，所有的键根据哈希函数映射到0～16383个整数槽内，每个节点负责维护一部分槽以及槽所映射的键值数据。

![image-20240328094550676](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094550676.png)

**工作原理：**

1. 通过哈希的方式，将数据分片，每个节点均分存储一定哈希槽(哈希值)区间的数据，默认分配了16384 个槽位
2. 每份数据分片会存储在多个互为主从的多节点上
3. 数据写入先写主节点，再同步到从节点(支持配置为阻塞同步)
4. 同一分片多个节点间的数据不保持一致性
5. 读取数据时，当客户端操作的key没有分配在该节点上时，redis会返回转向指令，指向正确的节点
6. 扩容时时需要需要把旧节点的数据迁移一部分到新节点

在 redis cluster 架构下，每个 redis 要放开两个端口号，比如一个是 6379，另外一个就是 加1w 的端口号，比如 16379。

16379 端口号是用来进行节点间通信的，也就是 cluster bus 的东西，cluster bus 的通信，用来进行故障检测、配置更新、故障转移授权。cluster bus 用了另外一种二进制的协议，`gossip` 协议，用于节点间进行高效的数据交换，占用更少的网络带宽和处理时间。

**优点：**

- 无中心架构，**支持动态扩**容；
- 数据按照`slot`存储分布在多个节点，节点间数据共享，**可动态调整数据分布**；
- **高可用性**。部分节点不可用时，集群仍可用。集群模式能够实现自动故障转移（failover），节点之间通过`gossip`协议交换状态信息，用投票机制完成`Slave`到`Master`的角色转换。

**缺点：**

- **不支持批量操作**（pipeline）。
- 数据通过异步复制，**不保证数据的强一致性**。
- **事务操作支持有限**，只支持多`key`在同一节点上的事务操作，当多个`key`分布于不同的节点上时无法使用事务功能。
- `key`作为数据分区的最小粒度，不能将一个很大的键值对象如`hash`、`list`等映射到不同的节点。
- **不支持多数据库空间**，单机下的Redis可以支持到16个数据库，集群模式下只能使用1个数据库空间。
- 只能使用0号数据库。

**哈希分区算法有哪些？**

节点取余分区。使用特定的数据，如Redis的键或用户ID，对节点数量N取余：hash（key）%N计算出哈希值，用来决定数据映射到哪一个节点上。 优点是简单性。扩容时通常采用翻倍扩容，避免数据映射全部被打乱导致全量迁移的情况。

一致性哈希分区。为系统中每个节点分配一个token，范围一般在0~232，这些token构成一个哈希环。数据读写执行节点查找操作时，先根据key计算hash值，然后顺时针找到第一个大于等于该哈希值的token节点。 这种方式相比节点取余最大的好处在于加入和删除节点只影响哈希环中相邻的节点，对其他节点无影响。

虚拟槽分区，所有的键根据哈希函数映射到0~16383整数槽内，计算公式：slot=CRC16（key）&16383。每一个节点负责维护一部分槽以及槽所映射的键值数据。**Redis Cluser采用虚拟槽分区算法。**

## 23、过期键的删除策略？

1、**被动删除**。在访问key时，如果发现key已经过期，那么会将key删除。

2、**主动删除**。定时清理key，每次清理会依次遍历所有DB，从db随机取出20个key，如果过期就删除，如果其中有5个key过期，那么就继续对这个db进行清理，否则开始清理下一个db。

3、**内存不够时清理**。Redis有最大内存的限制，通过maxmemory参数可以设置最大内存，当使用的内存超过了设置的最大内存，就要进行内存释放， 在进行内存释放的时候，会按照配置的淘汰策略清理内存。

## 24、内存淘汰策略有哪些？

当Redis的内存超过最大允许的内存之后，Redis 会触发内存淘汰策略，删除一些不常用的数据，以保证Redis服务器正常运行。

**Redisv4.0前提供 6 种数据淘汰策略**：

- **volatile-lru**：LRU（`Least Recently Used`），最近使用。利用LRU算法移除设置了过期时间的key
- **allkeys-lru**：当内存不足以容纳新写入数据时，从数据集中移除最近最少使用的key
- **volatile-ttl**：从已设置过期时间的数据集中挑选将要过期的数据淘汰
- **volatile-random**：从已设置过期时间的数据集中任意选择数据淘汰
- **allkeys-random**：从数据集中任意选择数据淘汰
- **no-eviction**：禁止删除数据，当内存不足以容纳新写入数据时，新写入操作会报错

**Redisv4.0后增加以下两种**：

- **volatile-lfu**：LFU，Least Frequently Used，最少使用，从已设置过期时间的数据集中挑选最不经常使用的数据淘汰。
- **allkeys-lfu**：当内存不足以容纳新写入数据时，从数据集中移除最不经常使用的key。

**内存淘汰策略可以通过配置文件来修改**，相应的配置项是`maxmemory-policy`，默认配置是`noeviction`。

## 25、MySQL 与 Redis 如何保证数据一致性

**缓存不一致是如何产生的**

如果数据一直没有变更，那么就不会出现缓存不一致的问题。

通常缓存不一致是发生在数据有变更的时候。 因为每次数据变更你需要同时操作数据库和缓存，而他们又属于不同的系统，无法做到同时操作成功或失败，总会有一个时间差。在并发读写的时候可能就会出现缓存不一致的问题（理论上通过分布式事务可以保证这一点，不过实际上基本上很少有人这么做）。

虽然没办法在数据有变更时，保证缓存和数据库强一致，但对缓存的更新还是有一定设计方法的，遵循这些设计方法，能够让这个不一致的影响时间和影响范围最小化。

缓存更新的设计方法大概有以下四种：

- 先删除缓存，再更新数据库（这种方法在并发下最容易出现长时间的脏数据，不可取）
- 先更新数据库，删除缓存（Cache Aside Pattern）
- 只更新缓存，由缓存自己同步更新数据库（Read/Write Through Pattern）
- 只更新缓存，由缓存自己异步更新数据库（Write Behind Cache Pattern）

**先删除缓存，再更新数据库**

这种方法在并发读写的情况下容易出现缓存不一致的问题

![image-20240328094610695](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094610695.png)

如上图所示，其可能的执行流程顺序为：

- 客户端1 触发更新数据A的逻辑
- 客户端2 触发查询数据A的逻辑
- 客户端1 删除缓存中数据A
- 客户端2 查询缓存中数据A，未命中
- 客户端2 从数据库查询数据A，并更新到缓存中
- 客户端1 更新数据库中数据A

可见，最后缓存中的数据A跟数据库中的数据A是不一致的，缓存中的数据A是旧的脏数据。

因此一般不建议使用这种方式。

**先更新数据库，再让缓存失效**

这种方法在并发读写的情况下，也可能会出现短暂缓存不一致的问题

![image-20240328094626149](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094626149.png)

如上图所示，其可能执行的流程顺序为：

- 客户端1 触发更新数据A的逻辑
- 客户端2 触发查询数据A的逻辑
- 客户端3 触发查询数据A的逻辑
- 客户端1 更新数据库中数据A
- 客户端2 查询缓存中数据A，命中返回（旧数据）
- 客户端1 让缓存中数据A失效
- 客户端3 查询缓存中数据A，未命中
- 客户端3 查询数据库中数据A，并更新到缓存中

可见，最后缓存中的数据A和数据库中的数据A是一致的，理论上可能会出现一小段时间数据不一致，不过这种概率也比较低，大部分的业务也不会有太大的问题。

**只更新缓存，由缓存自己同步更新数据库（Read/Write Through Pattern）**

这种方法相当于是业务只更新缓存，再由缓存去同步更新数据库。 一个Write Through的 例子如下：

![image-20240328094642251](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094642251.png)

如上图所示，其可能执行的流程顺序为：

- 客户端1 触发更新数据A的逻辑
- 客户端2 触发查询数据A的逻辑
- 客户端1 更新缓存中数据A，缓存同步更新数据库中数据A，再返回结果
- 客户端2 查询缓存中数据A，命中返回

Read Through 和 WriteThrough 的流程类似，只是在客户端查询数据A时，如果缓存中数据A失效了（过期或被驱逐淘汰），则缓存会同步去数据库中查询数据A，并缓存起来，再返回给客户端

这种方式缓存不一致的概率极低，只不过需要对缓存进行专门的改造。

**只更新缓存，由缓存自己异步更新数据库（Write Behind Cache Pattern）**

这种方式性详单于是业务只操作更新缓存，再由缓存异步去更新数据库，例如：

![image-20240328094658098](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240328094658098.png)

如上图所示，其可能的执行流程顺序为：

- 客户端1 触发更新数据A的逻辑
- 客户端2 触发查询数据A的逻辑
- 客户端1 更新缓存中的数据A，返回
- 客户端2 查询缓存中的数据A，命中返回
- 缓存异步更新数据A到数据库中

这种方式的优势是读写的性能都非常好，基本上只要操作完内存后就返回给客户端了，但是其是非强一致性，存在丢失数据的情况。

如果在缓存异步将数据更新到数据库中时，缓存服务挂了，此时未更新到数据库中的数据就丢失了。

## 26、缓存常见问题

### 26.1、缓存穿透

缓存穿透是指查询一个**不存在的数据**，由于缓存是不命中时被动写的，如果从DB查不到数据则不写入缓存，这将导致这个不存在的数据每次请求都要到DB去查询，失去了缓存的意义。在流量大时，可能DB就挂掉了。

怎么解决？

1. **缓存空值**，不会查数据库。
2. 采用**布隆过滤器**，将所有可能存在的数据哈希到一个足够大的`bitmap`中，查询不存在的数据会被这个`bitmap`拦截掉，从而避免了对`DB`的查询压力。

布隆过滤器的原理：当一个元素被加入集合时，通过K个哈希函数将这个元素映射成一个位数组中的K个点，把它们置为1。查询时，将元素通过哈希函数映射之后会得到k个点，如果这些点有任何一个0，则被检元素一定不在，直接返回；如果都是1，则查询元素很可能存在，就会去查询Redis和数据库。

布隆过滤器一般用于在大数据量的集合中判定某元素是否存在。

### 26.2、缓存雪崩

缓存雪崩是指在我们设置缓存时采用了相同的过期时间，**导致缓存在某一时刻同时失效**，请求全部转发到DB，DB瞬时压力过重挂掉。

解决方法：

1. 在原有的失效时间基础上**增加一个随机值**，使得过期时间分散一些。这样每一个缓存的过期时间的重复率就会降低，就很难引发集体失效的事件。
2. **加锁排队可以起到缓冲的作用**，防止大量的请求同时操作数据库，但它的缺点是**增加了系统的响应时间**，**降低了系统的吞吐量**，牺牲了一部分用户体验。当缓存未查询到时，对要请求的 key 进行加锁，只允许一个线程去数据库中查，其他线程等候排队。
3. 设置二级缓存。二级缓存指的是除了 Redis 本身的缓存，**再设置一层缓存**，当 Redis 失效之后，先去查询二级缓存。例如可以设置一个本地缓存，在 Redis 缓存失效的时候先去查询本地缓存而非查询数据库。

### 26.3、缓存击穿

缓存击穿：大量的请求同时查询一个 key 时，此时这个 key 正好失效了，就会导致大量的请求都落到数据库。**缓存击穿是查询缓存中失效的 key，而缓存穿透是查询不存在的 key。**

解决方法：

1、**加互斥锁**。在并发的多个请求中，只有第一个请求线程能拿到锁并执行数据库查询操作，其他的线程拿不到锁就阻塞等着，等到第一个线程将数据写入缓存后，直接走缓存。可以使用Redis分布式锁实现，代码如下：

```java
public String get(String key) {
    String value = redis.get(key);
    if (value == null) { //缓存值过期
        String unique_key = systemId + ":" + key;
        //设置30s的超时
        if (redis.set(unique_key, 1, 'NX', 'PX', 30000) == 1) {  //设置成功
            value = db.get(key);
            redis.set(key, value, expire_secs);
            redis.del(unique_key);
        } else {  //其他线程已经到数据库取值并回写到缓存了，可以重试获取缓存值
            sleep(50);
            get(key);  //重试
        }
    } else {
        return value;
    }
}
```

2、**热点数据不过期**。直接将缓存设置为不过期，然后由定时任务去异步加载数据，更新缓存。这种方式适用于比较极端的场景，例如流量特别特别大的场景，使用时需要考虑业务能接受数据不一致的时间，还有就是异常情况的处理，保证缓存可以定时刷新。

### 26.4、缓存预热

缓存预热就是系统上线后，将相关的缓存数据直接加载到缓存系统。这样就可以避免在用户请求的时候，先查询数据库，然后再将数据缓存的问题！用户直接查询事先被预热的缓存数据！

解决方案：

1. 直接写个缓存刷新页面，上线时手工操作一下；
2. 数据量不大，可以在项目启动的时候自动进行加载；
3. 定时刷新缓存；

### 26.5、缓存降级

当访问量剧增、服务出现问题（如响应时间慢或不响应）或非核心服务影响到核心流程的性能时，仍然需要保证服务还是可用的，即使是有损服务。系统可以根据一些关键数据进行自动降级，也可以配置开关实现人工降级。

缓存降级的最终目的是保证核心服务可用，即使是有损的。而且有些服务是无法降级的（如加入购物车、结算）。

在进行降级之前要对系统进行梳理，看看系统是不是可以丢卒保帅；从而梳理出哪些必须誓死保护，哪些可降级；比如可以参考日志级别设置预案：

1. 一般：比如有些服务偶尔因为网络抖动或者服务正在上线而超时，可以自动降级；
2. 警告：有些服务在一段时间内成功率有波动（如在95~100%之间），可以自动降级或人工降级，并发送告警；
3. 错误：比如可用率低于90%，或者数据库连接池被打爆了，或者访问量突然猛增到系统能承受的最大阀值，此时可以根据情况自动降级或者人工降级；
4. 严重错误：比如因为特殊原因数据错误了，此时需要紧急人工降级。

服务降级的目的，是为了防止Redis服务故障，导致数据库跟着一起发生雪崩问题。因此，对于不重要的缓存数据，可以采取服务降级策略，例如一个比较常见的做法就是，Redis出现问题，不去数据库查询，而是直接返回默认值给用户。

## 27、Redis 怎么实现消息队列？

使用list类型保存数据信息，rpush生产消息，lpop消费消息，当lpop没有消息时，可以sleep一段时间，然后再检查有没有信息，如果不想sleep的话，可以使用blpop, 在没有信息的时候，会一直阻塞，直到信息的到来。

```java
BLPOP queue 0  //0表示不限制等待时间
```

> BLPOP和LPOP命令相似，唯一的区别就是当列表没有元素时BLPOP命令会一直阻塞连接，直到有新元素加入。

redis可以通过pub/sub**主题订阅模式**实现一个生产者，多个消费者，当然也存在一定的缺点，当消费者下线时，生产的消息会丢失。

```java
PUBLISH channel1 hi
SUBSCRIBE channel1
UNSUBSCRIBE channel1 //退订通过SUBSCRIBE命令订阅的频道。
```

> `PSUBSCRIBE channel?*` 按照规则订阅。 `PUNSUBSCRIBE channel?*` 退订通过PSUBSCRIBE命令按照某种规则订阅的频道。其中订阅规则要进行严格的字符串匹配，`PUNSUBSCRIBE *`无法退订`channel?*`规则。

## 28、Redis 怎么实现延时队列

使用sortedset，拿时间戳作为score，消息内容作为key，调用zadd来生产消息，消费者用`zrangebyscore`指令获取N秒之前的数据轮询进行处理。

## 29、pipeline的作用？

redis客户端执行一条命令分4个过程： 发送命令、命令排队、命令执行、返回结果。使用`pipeline`可以批量请求，批量返回结果，执行速度比逐条执行要快。

使用`pipeline`组装的命令个数不能太多，不然数据量过大，增加客户端的等待时间，还可能造成网络阻塞，可以将大量命令的拆分多个小的`pipeline`命令完成。

原生批命令（mset和mget）与`pipeline`对比：

1. 原生批命令是原子性，`pipeline`是**非原子性**。pipeline命令中途异常退出，之前执行成功的命令**不会回滚**。
2. 原生批命令只有一个命令，但`pipeline`**支持多命令**。

## 30、LUA脚本

Redis 通过 LUA 脚本创建具有原子性的命令： 当lua脚本命令正在运行的时候，不会有其他脚本或 Redis 命令被执行，实现组合命令的原子操作。

在Redis中执行Lua脚本有两种方法：`eval`和`evalsha`。`eval`命令使用内置的 Lua 解释器，对 Lua 脚本进行求值。



```java
//第一个参数是lua脚本，第二个参数是键名参数个数，剩下的是键名参数和附加参数
> eval "return {KEYS[1],KEYS[2],ARGV[1],ARGV[2]}" 2 key1 key2 first second
1) "key1"
2) "key2"
3) "first"
4) "second"
```

**lua脚本作用**

1、Lua脚本在Redis中是原子执行的，执行过程中间不会插入其他命令。

2、Lua脚本可以将多条命令一次性打包，有效地减少网络开销。

**应用场景**

举例：限制接口访问频率。

在Redis维护一个接口访问次数的键值对，`key`是接口名称，`value`是访问次数。每次访问接口时，会执行以下操作：

- 通过`aop`拦截接口的请求，对接口请求进行计数，每次进来一个请求，相应的接口访问次数`count`加1，存入redis。
- 如果是第一次请求，则会设置`count=1`，并设置过期时间。因为这里`set()`和`expire()`组合操作不是原子操作，所以引入`lua`脚本，实现原子操作，避免并发访问问题。
- 如果给定时间范围内超过最大访问次数，则会抛出异常。

```java
private String buildLuaScript() {
    return "local c" +
        "\nc = redis.call('get',KEYS[1])" +
        "\nif c and tonumber(c) > tonumber(ARGV[1]) then" +
        "\nreturn c;" +
        "\nend" +
        "\nc = redis.call('incr',KEYS[1])" +
        "\nif tonumber(c) == 1 then" +
        "\nredis.call('expire',KEYS[1],ARGV[2])" +
        "\nend" +
        "\nreturn c;";
}

String luaScript = buildLuaScript();
RedisScript<Number> redisScript = new DefaultRedisScript<>(luaScript, Number.class);
Number count = redisTemplate.execute(redisScript, keys, limit.count(), limit.period());
```

PS：这种接口限流的实现方式比较简单，问题也比较多，一般不会使用，接口限流用的比较多的是令牌桶算法和漏桶算法。

## 31、什么是RedLock？

Redis 官方站提出了一种权威的基于 Redis 实现分布式锁的方式名叫 *Redlock*，此种方式比原先的单节点的方法更安全。它可以保证以下特性：

1. 安全特性：互斥访问，即永远只有一个 client 能拿到锁
2. 避免死锁：最终 client 都可能拿到锁，不会出现死锁的情况，即使原本锁住某资源的 client 挂掉了
3. 容错性：只要大部分 Redis 节点存活就可以正常提供服务

## 32、Redis大key怎么处理？

通常我们会将含有较大数据或含有大量成员、列表数的Key称之为大Key。

以下是对各个数据类型大key的描述：

- value是STRING类型，它的值超过5MB
- value是ZSET、Hash、List、Set等集合类型时，它的成员数量超过1w个

上述的定义并不绝对，主要是根据value的成员数量和大小来确定，根据业务场景确定标准。

怎么处理：

1. 当vaule是string时，可以使用序列化、压缩算法将key的大小控制在合理范围内，但是序列化和反序列化都会带来更多时间上的消耗。或者将key进行拆分，一个大key分为不同的部分，记录每个部分的key，使用multiget等操作实现事务读取。
2. 当value是list/set等集合类型时，根据预估的数据规模来进行分片，不同的元素计算后分到不同的片。

## 33、Redis常见性能问题和解决方案？

1. Master最好不要做任何持久化工作，包括内存快照和AOF日志文件，特别是不要启用内存快照做持久化。
2. 如果数据比较关键，某个Slave开启AOF备份数据，策略为每秒同步一次。
3. 为了主从复制的速度和连接的稳定性，Slave和Master最好在同一个局域网内。
4. 尽量避免在压力较大的主库上增加从库
5. Master调用BGREWRITEAOF重写AOF文件，AOF在重写的时候会占大量的CPU和内存资源，导致服务load过高，出现短暂服务暂停现象。
6. 为了Master的稳定性，主从复制不要用图状结构，用单向链表结构更稳定，即主从关系为：Master<–Slave1<–Slave2<–Slave3…，这样的结构也方便解决单点故障问题，实现Slave对Master的替换，也即，如果Master挂了，可以立马启用Slave1做Master，其他不变。

## 34、说说为什么Redis过期了为什么内存没释放？

第一种情况，可能是覆盖之前的key，导致key过期时间发生了改变。

当一个key在Redis中已经存在了，但是由于一些误操作使得key过期时间发生了改变，从而导致这个key在应该过期的时间内并没有过期，从而造成内存的占用。

第二种情况是，Redis过期key的处理策略导致内存没释放。

一般Redis对过期key的处理策略有两种：惰性删除和定时删除。

先说惰性删除的情况

当一个key已经确定设置了xx秒过期同时中间也没有修改它，xx秒之后它确实已经过期了，但是惰性删除的策略它并不会马上删除这个key，而是当再次读写这个key时它才会去检查是否过期，如果过期了就会删除这个key。也就是说，惰性删除策略下，就算key过期了，也不会立刻释放内容，要等到下一次读写这个key才会删除key。

而定时删除会在一定时间内主动淘汰一部分已经过期的数据，默认的时间是每100ms过期一次。因为定时删除策略每次只会淘汰一部分过期key，而不是所有的过期key，如果redis中数据比较多的话要是一次性全量删除对服务器的压力比较大，每一次只挑一批进行删除，所以很可能出现部分已经过期的key并没有及时的被清理掉，从而导致内存没有即时被释放。

## 35、Redis突然变慢，有哪些原因？

1. **存在bigkey**。如果Redis实例中存储了 bigkey，那么在淘汰删除 bigkey 释放内存时，也会耗时比较久。应该避免存储 bigkey，降低释放内存的耗时。

2. 如果Redis 实例**设置了内存上限 maxmemory**，有可能导致 Redis 变慢。当 Redis 内存达到 maxmemory 后，每次写入新的数据之前，Redis 必须先从实例中踢出一部分数据，让整个实例的内存维持在 maxmemory 之下，然后才能把新数据写进来。

3. **开启了内存大页**。当 Redis 在执行后台 RDB 和 AOF rewrite 时，采用 fork 子进程的方式来处理。但主进程 fork 子进程后，此时的主进程依旧是可以接收写请求的，而进来的写请求，会采用 Copy On Write（写时复制）的方式操作内存数据。

   什么是写时复制？

   这样做的好处是，父进程有任何写操作，并不会影响子进程的数据持久化。

   不过，主进程在拷贝内存数据时，会涉及到新内存的申请，如果此时操作系统开启了内存大页，那么在此期间，客户端即便只修改 10B 的数据，Redis 在申请内存时也会以 2MB 为单位向操作系统申请，申请内存的耗时变长，进而导致每个写请求的延迟增加，影响到 Redis 性能。

   解决方案就是关闭内存大页机制。

4. **使用了Swap**。操作系统为了缓解内存不足对应用程序的影响，允许把一部分内存中的数据换到磁盘上，以达到应用程序对内存使用的缓冲，这些内存数据被换到磁盘上的区域，就是 Swap。当内存中的数据被换到磁盘上后，Redis 再访问这些数据时，就需要从磁盘上读取，访问磁盘的速度要比访问内存慢几百倍。尤其是针对 Redis 这种对性能要求极高、性能极其敏感的数据库来说，这个操作延时是无法接受的。解决方案就是增加机器的内存，让 Redis 有足够的内存可以使用。或者整理内存空间，释放出足够的内存供 Redis 使用

5. **网络带宽过载**。网络带宽过载的情况下，服务器在 TCP 层和网络层就会出现数据包发送延迟、丢包等情况。Redis 的高性能，除了操作内存之外，就在于网络 IO 了，如果网络 IO 存在瓶颈，那么也会严重影响 Redis 的性能。解决方案：1、及时确认占满网络带宽 Redis 实例，如果属于正常的业务访问，那就需要及时扩容或迁移实例了，避免因为这个实例流量过大，影响这个机器的其他实例。2、运维层面，需要对 Redis 机器的各项指标增加监控，包括网络流量，在网络流量达到一定阈值时提前报警，及时确认和扩容。

6. **频繁短连接**。频繁的短连接会导致 Redis 大量时间耗费在连接的建立和释放上，TCP 的三次握手和四次挥手同样也会增加访问延迟。应用应该使用长连接操作 Redis，避免频繁的短连接。

## 36、为什么 Redis 集群的最大槽数是 16384 个？

Redis Cluster 采用数据分片机制，定义了 16384个 Slot槽位，集群中的每个Redis 实例负责维护一部分槽以及槽所映射的键值数据。

Redis每个节点之间会定期发送ping/pong消息（心跳包包含了其他节点的数据），用于交换数据信息。

Redis集群的节点会按照以下规则发ping消息：

- (1)每秒会随机选取5个节点，找出最久没有通信的节点发送ping消息
- (2)每100毫秒都会扫描本地节点列表，如果发现节点最近一次接受pong消息的时间大于cluster-node-timeout/2 则立刻发送ping消息

心跳包的消息头里面有个myslots的char数组，是一个bitmap，每一个位代表一个槽，如果该位为1，表示这个槽是属于这个节点的。

接下来，解答为什么 Redis 集群的最大槽数是 16384 个，而不是65536 个。

1、如果采用 16384 个插槽，那么心跳包的消息头占用空间 2KB （16384/8）；如果采用 65536 个插槽，那么心跳包的消息头占用空间 8KB (65536/8)。可见采用 65536 个插槽，**发送心跳信息的消息头达8k，比较浪费带宽**。

2、一般情况下一个Redis集群**不会有超过1000个master节点**，太多可能导致网络拥堵。

3、哈希槽是通过一张bitmap的形式来保存的，在传输过程中，会对bitmap进行压缩。bitmap的填充率越低，**压缩率**越高。其中bitmap 填充率 = slots / N (N表示节点数)。所以，插槽数越低， 填充率会降低，压缩率会提高。

## 37、Redis存在线程安全的问题吗

首先从Redis 服务端层面来看。

Redis Server本身是一个线程安全的K-V数据库，也就是说在Redis Server上执行的指令，不需要任何同步机制，不会存在线程安全问题。

虽然Redis 6.0里面，增加了多线程的模型，但是增加的多线程只是用来处理网络IO事件，对于指令的执行过程，仍然是由主线程来处理，所以不会存在多个线程通知执行操作指令的情况。

然后从Redis客户端层面来看。

虽然Redis Server中的指令执行是原子的，但是如果有多个Redis客户端同时执行多个指令的时候，就无法保证原子性。

假设两个redis client同时获取Redis Server上的key1， 同时进行修改和写入，因为多线程环境下的原子性无法被保障，以及多进程情况下的共享资源访问的竞争问题，使得数据的安全性无法得到保障。

对于客户端层面的线程安全性问题，解决方法有很多，比如尽可能的使用Redis里面的原子指令，或者对多个客户端的资源访问加锁，或者通过Lua脚本来实现多个指令的操作等等。

## 38、Redis遇到哈希冲突怎么办？

当有两个或以上数量的键被分配到了哈希表数组的同一个索引上面时， 我们称这些键发生了冲突（collision）。

Redis 的哈希表使用链地址法（separate chaining）来解决键冲突： 每个哈希表节点都有一个 `next` 指针， 多个哈希表节点可以用 `next` 指针构成一个单向链表， 被分配到同一个索引上的多个节点可以用这个单向链表连接起来， 这就解决了键冲突的问题。

原理跟 Java 的 HashMap 类似，都是数组+链表的结构。当发生 hash 碰撞时将会把元素追加到链表上。

# 八、RabbitMQ

## 1、什么是RabbitMQ？

**消息**指的是两个应用间传递的数据。数据的类型有很多种形式，可能只包含文本字符串，也可能包含嵌入对象。

**“消息队列(Message Queue)”是在消息的传输过程中保存消息的容器**。在消息队列中，通常有生产者和消费者两个角色。生产者只负责发送数据到消息队列。消费者只负责从消息队列中取出数据处理。

![image-20240409144143235](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240409144143235.png)

RabbitMQ是一个由erlang开发的，用于应用间异步协作的消息队列。RabbitMQ是一种遵循`AMQP`协议的分布式消息中间件。`AMQP` 全称 “Advanced Message Queuing Protocol”，高级消息队列协议。它是应用层协议的一个开发标准，为面向消息的中间件设计。

![image-20240408122017914](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240408122017914.png)

## 2、RabbitMQ的组件

* **Message**：由消息头和消息体组成。消息体是不透明的，而消息头则由一系列的可选属性组成，这些属性包括routing-key、priority、delivery-mode（是否持久性存储）等。

* **Publisher**：消息的生产者。
* **Consumer**：消息的消费者。

* **Exchange**：接收消息并将消息路由到一个或多个Queue。default exchange 是默认的直连交换机，名字为空字符串，每个新建队列都会自动绑定到默认交换机上，绑定的路由键名称与队列名称相同。

* **Binding**：通过Binding将Exchange和Queue关联，这样Exchange就知道将消息路由到哪个Queue中。

* **Queue**：存储消息，队列的特性是先进先出。一个消息可分发到一个或多个队列。

* **Virtual host**：每个 vhost 本质上就是一个 mini 版的 RabbitMQ 服务器，拥有自己的队列、交换器、绑定和权限机制。vhost 是 AMQP 概念的基础，必须在连接时指定，RabbitMQ 默认的 vhost 是 / 。当多个不同的用户使用同一个RabbitMQ server提供的服务时，可以划分出多个vhost，每个用户在自己的vhost创建exchange和queue。

* **Broker**：消息队列服务器实体。

## 3、什么时候使用MQ

对于一些不需要立即生效的操作，可以拆分出来，异步执行，使用消息队列实现。

以常见的订单系统为例，用户点击下单按钮之后的业务逻辑可能包括：扣减库存、生成相应单据、发短信通知。这种场景下就可以用 MQ 。将短信通知放到 MQ 异步执行，在下单的主流程（比如扣减库存、生成相应单据）完成之后发送一条消息到 MQ， 让主流程快速完结，而由另外的线程消费MQ的消息。

## 4、RabbitMQ的优缺点

* **优点**：有管理界面，方便使用；可靠性高；功能丰富，支持消息持久化、消息确认机制、多种消息分发机制。
* **缺点**：使用erlang实现，不利于二次开发和维护；性能较kafka差，持久化消息和ACK确认的情况下生产和消费消息单机吞吐量大约在1-2万左右，kafka单机吞吐量在十万级别。

## 5、RabbitMQ 有哪些重要的角色？

RabbitMQ 中重要的角色有：生产者、消费者和代理。

1. 生产者：消息的创建者，负责创建和推送数据到消息队列服务器；
2. 消费者：消息的接收方，用于处理数据和确认消息；
3. 代理：就是 RabbitMQ 本身，用于扮演“快递”的角色，本身不生产消息，只是扮演“快递”的角色。

## 6、Exchange 类型

Exchange分发消息时根据不同的类型使用不同的分发策略，目前共四种类型：direct、fanout、topic、headers 。headers 模式根据消息的headers进行路由，此外 headers 交换器和 direct 交换器完全一致，但性能差很多。

Exchange规则。

| 类型名称 | 类型描述                                                     |
| -------- | ------------------------------------------------------------ |
| fanout   | 把所有发送到该Exchange的消息路由到所有与它绑定的Queue中      |
| direct   | Routing Key==Binding Key                                     |
| topic    | 模糊匹配                                                     |
| headers  | Exchange不依赖于routing key与binding key的匹配规则来路由消息，而是根据发送的消息内容中的header属性进行匹配。 |

**direct**

direct交换机会将消息路由到binding key 和 routing key完全匹配的队列中。它是完全匹配、单播的模式。

**适用场景**：有优先级的任务，根据任务的优先级把消息发送到对应的队列，这样可以指派更多的资源去处理高优先级的队列。

![image-20240410103742105](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103742105.png)

**fanout**

所有发到 fanout 类型交换机的消息都会路由到所有与该交换机绑定的队列上去。fanout 类型转发消息是最快的。

![image-20240410103754835](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103754835.png)

**topic**

topic交换机使用routing key和binding key进行模糊匹配，匹配成功则将消息发送到相应的队列。符号“#”匹配一个或多个词，符号“*”只能匹配一个词。

![image-20240410103804569](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103804569.png)

**headers**

headers交换机是根据发送的消息内容中的headers属性进行路由的。在绑定Queue与Exchange时指定一组键值对；当消息发送到Exchange时，RabbitMQ会取到该消息的headers（也是一个键值对的形式），对比其中的键值对是否完全匹配Queue与Exchange绑定时指定的键值对；如果完全匹配则消息会路由到该Queue，否则不会路由到该Queue。

![image-20240410103813662](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103813662.png)

### 6.1、消息模式

* 简单模式：简单模式是最简单的消息模式，它包含一个生产者、一个消费者和一个队列。生产者向队列里发送消息，消费者从队列中获取消息并消费。

  ![image-20240410103007441](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103007441.png)

* 工作模式：工作模式是指向多个互相竞争的消费者获取消息的模式，它包含一个生产者、两个消费者和一个队列。两个消费者同时绑定到一个队列上去，当消费者获取消息处理耗时任务时，空闲的消费者从队列中获取并消费消息。

  ![image-20240410103034513](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103034513.png)

* 发布/订阅模式：发布/订阅模式是指同时向多个消费者发送消息的模式（类似广播的形式），它包含一个生产者、两个消费者、两个队列和一个交换机。两个消费者同时绑定到不同的队列上去，两个队列绑定到交换机上去，生产者通过发送消息到交换机，所有消费者接收并消费消息。

  ![image-20240410103111343](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103111343.png)

* 路由模式：路由模式是可以根据`路由键`选择性给多个消费者发送消息的模式，它包含一个生产者、两个消费者、两个队列和一个交换机。两个消费者同时绑定到不同的队列上去，两个队列通过`路由键`绑定到交换机上去，生产者发送消息到交换机，交换机通过`路由键`转发到不同队列，队列绑定的消费者接收并消费消息。

  ![image-20240410103137046](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103137046.png)

* 通配符模式：通配符模式是可以根据`路由键匹配规则`选择性给多个消费者发送消息的模式，它包含一个生产者、两个消费者、两个队列和一个交换机。两个消费者同时绑定到不同的队列上去，两个队列通过`路由键匹配规则`绑定到交换机上去，生产者发送消息到交换机，交换机通过`路由键匹配规则`转发到不同队列，队列绑定的消费者接收并消费消息。

  ![image-20240410103208942](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410103208942.png)

## 7、消息丢失

**消息丢失场景**：

* 生产者生产消息到RabbitMQ Server消息丢失
* RabbitMQ Server存储的消息丢失
* RabbitMQ Server到消费者消息丢失。

消息丢失从三个方面来解决：生产者确认机制、消费者手动确认消息和持久化。

### 7.1、生产者确认机制

生产者发送消息到队列，无法确保发送的消息成功的到达server。

解决方法：

1. 事务机制。在一条消息发送之后会使发送端阻塞，等待RabbitMQ的回应，之后才能继续发送下一条消息。性能差。
2. 开启生产者确认机制，只要消息成功发送到交换机之后，RabbitMQ就会发送一个ack给生产者（即使消息没有Queue接收，也会发送ack）。如果消息没有成功发送到交换机，就会发送一条nack消息，提示发送失败。

在 Springboot 是通过 publisher-confirms 参数来设置 confirm 模式：

```yaml
spring:
    rabbitmq:   
        ##开启 confirm 确认机制
        publisher-confirms: true
```

在生产端提供一个回调方法，当服务端确认了一条或者多条消息后，生产者会回调这个方法，根据具体的结果对消息进行后续处理，比如重新发送、记录日志等。

```java
// 消息是否成功发送到Exchange
final RabbitTemplate.ConfirmCallback confirmCallback = (CorrelationData correlationData, boolean ack, String cause) -> {
            log.info("correlationData: " + correlationData);
            log.info("ack: " + ack);
            if(!ack) {
                log.info("异常处理....");
            }
    };

rabbitTemplate.setConfirmCallback(confirmCallback);
```

### 7.2、路由不可达消息

生产者确认机制只确保消息正确到达交换机，对于从交换机路由到Queue失败的消息，会被丢弃掉，导致消息丢失。

对于不可路由的消息，有两种处理方式：Return消息机制和备份交换机。

**Return消息机制**

Return消息机制提供了回调函数 ReturnCallback，当消息从交换机路由到Queue失败才会回调这个方法。需要将`mandatory` 设置为 `true` ，才能监听到路由不可达的消息。

```yaml
spring:
    rabbitmq:
        ##触发ReturnCallback必须设置mandatory=true, 否则Exchange没有找到Queue就会丢弃掉消息, 而不会触发ReturnCallback
        template.mandatory: true
```

通过 ReturnCallback 监听路由不可达消息。

```java
    final RabbitTemplate.ReturnCallback returnCallback = (Message message, int replyCode, String replyText, String exchange, String routingKey) ->
            log.info("return exchange: " + exchange + ", routingKey: "
                    + routingKey + ", replyCode: " + replyCode + ", replyText: " + replyText);
rabbitTemplate.setReturnCallback(returnCallback);
```

当消息从交换机路由到Queue失败时，会返回 `return exchange: , routingKey: MAIL, replyCode: 312, replyText: NO_ROUTE`。

**备份交换机**

备份交换机alternate-exchange 是一个普通的exchange，当你发送消息到对应的exchange时，没有匹配到queue，就会自动转移到备份交换机对应的queue，这样消息就不会丢失。

### 7.3、消费者手动消息确认

有可能消费者收到消息还没来得及处理MQ服务就宕机了，导致消息丢失。因为消息者默认采用自动ack，一旦消费者收到消息后会通知MQ Server这条消息已经处理好了，MQ 就会移除这条消息。

解决方法：消费者设置为手动确认消息。消费者处理完逻辑之后再给broker回复ack，表示消息已经成功消费，可以从broker中删除。当消息者消费失败的时候，给broker回复nack，根据配置决定重新入队还是从broker移除，或者进入死信队列。只要没收到消费者的 acknowledgment，broker 就会一直保存着这条消息，但不会 requeue，也不会分配给其他消费者。

消费者设置手动ack：

```java
##设置消费端手动 ack
spring.rabbitmq.listener.simple.acknowledge-mode=manual
```

消息处理完，手动确认：

```java
    @RabbitListener(queues = RabbitMqConfig.MAIL_QUEUE)
    public void onMessage(Message message, Channel channel) throws IOException {

        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        long deliveryTag = message.getMessageProperties().getDeliveryTag();
        //手工ack；第二个参数是multiple，设置为true，表示deliveryTag序列号之前（包括自身）的消息都已经收到，设为false则表示收到一条消息
        channel.basicAck(deliveryTag, true);
        System.out.println("mail listener receive: " + new String(message.getBody()));
    }
```

当消息消费失败时，消费端给broker回复nack，如果consumer设置了requeue为false，则nack后broker会删除消息或者进入死信队列，否则消息会重新入队。

### 7.4、持久化

如果RabbitMQ服务异常导致重启，将会导致消息丢失。RabbitMQ提供了持久化的机制，将内存中的消息持久化到硬盘上，即使重启RabbitMQ，消息也不会丢失。

消息持久化需要满足以下条件：

1. 消息设置持久化。发布消息前，设置投递模式delivery mode为2，表示消息需要持久化。
2. Queue设置持久化。
3. 交换机设置持久化。

当发布一条消息到交换机上时，Rabbit会先把消息写入持久化日志，然后才向生产者发送响应。一旦从队列中消费了一条消息的话并且做了确认，RabbitMQ会在持久化日志中移除这条消息。在消费消息前，如果RabbitMQ重启的话，服务器会自动重建交换机和队列，加载持久化日志中的消息到相应的队列或者交换机上，保证消息不会丢失。

### 7.5、镜像队列

当MQ发生故障时，会导致服务不可用。引入RabbitMQ的镜像队列机制，将queue镜像到集群中其他的节点之上。如果集群中的一个节点失效了，能自动地切换到镜像中的另一个节点以保证服务的可用性。

通常每一个镜像队列都包含一个master和多个slave，分别对应于不同的节点。发送到镜像队列的所有消息总是被直接发送到master和所有的slave之上。除了publish外所有动作都只会向master发送，然后由master将命令执行的结果广播给slave，从镜像队列中的消费操作实际上是在master上执行的。

## 8、消息重复消费怎么处理？

> 如何保证消息不被重复消费？或者说，如何保证消息消费的幂等性？

消息重复的原因有两个：1.生产时消息重复，2.消费时消息重复。

生产者发送消息给MQ，在MQ确认的时候出现了网络波动，生产者没有收到确认，这时候生产者就会重新发送这条消息，导致MQ会接收到重复消息。

消费者消费成功后，给MQ确认的时候出现了网络波动，MQ没有接收到确认，为了保证消息不丢失，MQ就会继续给消费者投递之前的消息。这时候消费者就接收到了两条一样的消息。由于重复消息是由于网络原因造成的，无法避免。

解决方法：发送消息时让每个消息携带一个全局的唯一ID，在消费消息时先判断消息是否已经被消费过，保证消息消费逻辑的幂等性。具体消费过程为：

1. 消费者获取到消息后先根据id去查询redis/db是否存在该消息
2. 如果不存在，则正常消费，消费完毕后写入redis/db
3. 如果存在，则证明消息被消费过，直接丢弃

## 9、消费端怎么进行限流？

当 RabbitMQ 服务器积压大量消息时，队列里的消息会大量涌入消费端，可能导致消费端服务器崩溃。这种情况下需要对消费端限流。

Spring RabbitMQ 提供参数 **prefetch** 可以设置单个请求处理的消息个数。如果消费者同时处理的消息到达最大值的时候，则该消费者会阻塞，不会消费新的消息，直到有消息 ack 才会消费新的消息。

开启消费端限流：

```properties
##在单个请求中处理的消息个数，unack的最大数量
spring.rabbitmq.listener.simple.prefetch=2
```

原生 RabbitMQ 还提供 prefetchSize 和 global 两个参数。Spring RabbitMQ没有这两个参数。

```java
//单条消息大小限制，0代表不限制
//global：限制限流功能是channel级别的还是consumer级别。当设置为false，consumer级别，限流功能生效，设置为true没有了限流功能，因为channel级别尚未实现。
void basicQos(int prefetchSize, int prefetchCount, boolean global) throws IOException;
```

## 10、什么是死信队列？

消费失败的消息存放的队列。

消息消费失败的原因：

- 消息被拒绝并且消息没有重新入队（requeue=false）
- 消息超时未消费
- 达到最大队列长度

当普通队列中有死信时，RabbitMQ 就会自动的将这个消息重新发布到设置的死信交换机去，然后被路由到死信队列。可以监听死信队列中的消息做相应的处理。

设置死信队列的 exchange 和 queue，然后进行绑定：

```java
	@Bean
    public DirectExchange dlxExchange() {
        return new DirectExchange(RabbitMqConfig.DLX_EXCHANGE);
    }

    @Bean
    public Queue dlxQueue() {
        return new Queue(RabbitMqConfig.DLX_QUEUE, true);
    }

    @Bean
    public Binding bindingDeadExchange(Queue dlxQueue, DirectExchange deadExchange) {
        return BindingBuilder.bind(dlxQueue).to(deadExchange).with(RabbitMqConfig.DLX_QUEUE);
    }
```

在普通队列加上两个参数，绑定普通队列到死信队列。当消息消费失败时，消息会被路由到死信队列。

```java
    @Bean
    public Queue sendSmsQueue() {
        Map<String,Object> arguments = new HashMap<>(2);
        // 绑定该队列到私信交换机
        arguments.put("x-dead-letter-exchange", RabbitMqConfig.DLX_EXCHANGE);
        arguments.put("x-dead-letter-routing-key", RabbitMqConfig.DLX_QUEUE);
        return new Queue(RabbitMqConfig.MAIL_QUEUE, true, false, false, arguments);
    }
```

生产者完整代码：

```java
@Component
@Slf4j
public class MQProducer {

    @Autowired
    RabbitTemplate rabbitTemplate;

    @Autowired
    RandomUtil randomUtil;

    @Autowired
    UserService userService;

    final RabbitTemplate.ConfirmCallback confirmCallback = (CorrelationData correlationData, boolean ack, String cause) -> {
            log.info("correlationData: " + correlationData);
            log.info("ack: " + ack);
            if(!ack) {
                log.info("异常处理....");
            }
    };


    final RabbitTemplate.ReturnCallback returnCallback = (Message message, int replyCode, String replyText, String exchange, String routingKey) ->
            log.info("return exchange: " + exchange + ", routingKey: "
                    + routingKey + ", replyCode: " + replyCode + ", replyText: " + replyText);

    public void sendMail(String mail) {
        //貌似线程不安全 范围100000 - 999999
        Integer random = randomUtil.nextInt(100000, 999999);
        Map<String, String> map = new HashMap<>(2);
        String code = random.toString();
        map.put("mail", mail);
        map.put("code", code);

        MessageProperties mp = new MessageProperties();
        //在生产环境中这里不用Message，而是使用 fastJson 等工具将对象转换为 json 格式发送
        Message msg = new Message("tyson".getBytes(), mp);
        msg.getMessageProperties().setExpiration("3000");
        //如果消费端要设置为手工 ACK ，那么生产端发送消息的时候一定发送 correlationData ，并且全局唯一，用以唯一标识消息。
        CorrelationData correlationData = new CorrelationData("1234567890"+new Date());

        rabbitTemplate.setMandatory(true);
        rabbitTemplate.setConfirmCallback(confirmCallback);
        rabbitTemplate.setReturnCallback(returnCallback);
        rabbitTemplate.convertAndSend(RabbitMqConfig.MAIL_QUEUE, msg, correlationData);

        //存入redis
        userService.updateMailSendState(mail, code, MailConfig.MAIL_STATE_WAIT);
    }
}
```

消费者完整代码：

```java
@Slf4j
@Component
public class DeadListener {

    @RabbitListener(queues = RabbitMqConfig.DLX_QUEUE)
    public void onMessage(Message message, Channel channel) throws IOException {

        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        long deliveryTag = message.getMessageProperties().getDeliveryTag();
        //手工ack
        channel.basicAck(deliveryTag,false);
        System.out.println("receive--1: " + new String(message.getBody()));
    }
}
```

## 11、说说pull模式

pull模式主要是通过channel.basicGet方法来获取消息，示例代码如下：

```java
GetResponse response = channel.basicGet(QUEUE_NAME, false);
System.out.println(new String(response.getBody()));
channel.basicAck(response.getEnvelope().getDeliveryTag(),false);
```

## 12、怎么设置消息的过期时间？

在生产端发送消息的时候可以给消息设置过期时间，单位为毫秒(ms)

```java
Message msg = new Message("tyson".getBytes(), mp);
msg.getMessageProperties().setExpiration("3000");
```

也可以在创建队列的时候指定队列的ttl，从消息入队列开始计算，超过该时间的消息将会被移除。

## 13、为什么使用消息队列

**高并发的流量削峰：**

举个例子，假设某订单系统每秒最多能处理一万次订单，也就是最多承受的10000qps，这个处理能力应付正常时段的下单时绰绰有余，正常时段我们下单一秒后就能返回结果。但是在高峰期，如果有两万次下单操作系统是处理不了的，只能限制订单超过一万后不允许用户下单。使用消息队列做缓冲，我们可以取消这个限制，把一秒内下的订单分散成一段时间来处理，这时有些用户可能在下单十几秒后才能收到下单成功的操作，但是比不能下单的体验要好。

![image-20240410151859511](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410151859511.png)

**应用解耦：**

以电商应用为例，应用中有订单系统、库存系统、物流系统、支付系统。用户创建订单后，如果耦合调用库存系统、物流系统、支付系统，任何一个子系统出了故障，都会造成下单操作异常。当转变成基于消息队列的方式后，系统间调用的问题会减少很多，比如物流系统因为发生故障，需要几分钟来修复。在这几分钟的时间里，物流系统要处理的内存被缓存在消息队列中，用户的下单操作可以正常完成。当物流系统恢复后，继续处理订单信息即可，中单用户感受不到物流系统的故障，提升系统的可用性。

![image-20240410151917963](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410151917963.png)

 **异步处理：**

有些服务间调用是异步的，例如 A 调用 B，B 需要花费很长时间执行，但是 A 需要知道 B 什么时候可以执行完，以前一般有两种方式，A 过一段时间去调用 B 的查询 api 查询。或者 A 提供一个 callback api， B 执行完之后调用 api 通知 A 服务。这两种方式都不是很优雅，使用消息队列，可以很方便解决这个问题，A 调用 B 服务后，只需要监听 B 处理完成的消息，当 B 处理完成后，会发送一条消息给 MQ，MQ 会将此消息转发给 A 服务。这样 A 服务既不用循环调用 B 的查询 api，也不用提供 callback api。同样B 服务也不用做这些操作。A 服务还能及时的得到异步处理成功的消息。

![image-20240410151932919](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410151932919.png)





* 解耦。比如，用户下单后，订单系统需要通知库存系统，假如库存系统无法访问，则订单减库将失败，从而导致订单操作失败。订单系统与库存系统耦合，这个时候如果使用消息队列，可以返回给用户成功，先把消息持久化，等库存系统恢复后，就可以正常消费减去库存了。
* 异步。将消息写入消息队列，非必要的业务逻辑以异步的方式运行，不影响主流程业务。
* 削峰。消费端慢慢的按照数据库能处理的并发量，从消息队列中慢慢拉取消息。在生产中，这个短暂的高峰期积压是允许的。比如秒杀活动，一般会因为流量过大，从而导致流量暴增，应用挂掉。这个时候加上消息队列，服务器接收到用户的请求后，首先写入消息队列，如果消息队列长度超过最大数量，则直接抛弃用户请求或跳转到错误页面。

## 14、消息队列有哪些优缺点

优点上面已经说了，就是**在特殊场景下有其对应的好处**，**解耦**、**异步**、**削峰**。

缺点有以下几个：

- 系统可用性降低

  系统引入的外部依赖越多，越容易挂掉。本来你就是 A 系统调用 BCD 三个系统的接口就好了，ABCD 四个系统还好好的，没啥问题，你偏加个 MQ 进来，万一 MQ 挂了咋整？MQ 一挂，整套系统崩溃，你不就完了？

- 系统复杂度提高

  硬生生加个 MQ 进来，你怎么[保证消息没有重复消费](https://doocs.github.io/advanced-java/#/docs/high-concurrency/how-to-ensure-that-messages-are-not-repeatedly-consumed)？怎么[处理消息丢失的情况](https://doocs.github.io/advanced-java/#/docs/high-concurrency/how-to-ensure-the-reliable-transmission-of-messages)？怎么保证消息传递的顺序性？头大头大，问题一大堆，痛苦不已。

- 一致性问题

  A 系统处理完了直接返回成功了，人都以为你这个请求就成功了；但是问题是，要是 BCD 三个系统那里，BD 两个系统写库成功了，结果 C 系统写库失败了，咋整？你这数据就不一致了。

## 15、Kafka、ActiveMQ、RabbitMQ、RocketMQ 都有什么区别，以及适合哪些场景

| 特性                     | ActiveMQ                              | RabbitMQ                                           | RocketMQ                                                     | Kafka                                                        |
| ------------------------ | ------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 单机吞吐量               | 万级，比 RocketMQ、Kafka 低一个数量级 | 同 ActiveMQ                                        | 10 万级，支撑高吞吐                                          | 10 万级，高吞吐，一般配合大数据类的系统来进行实时数据计算、日志采集等场景 |
| topic 数量对吞吐量的影响 |                                       |                                                    | topic 可以达到几百/几千的级别，吞吐量会有较小幅度的下降，这是 RocketMQ 的一大优势，在同等机器下，可以支撑大量的 topic | topic 从几十到几百个时候，吞吐量会大幅度下降，在同等机器下，Kafka 尽量保证 topic 数量不要过多，如果要支撑大规模的 topic，需要增加更多的机器资源 |
| 时效性                   | ms 级                                 | 微秒级，这是 RabbitMQ 的一大特点，延迟最低         | ms 级                                                        | 延迟在 ms 级以内                                             |
| 可用性                   | 高，基于主从架构实现高可用            | 同 ActiveMQ                                        | 非常高，分布式架构                                           | 非常高，分布式，一个数据多个副本，少数机器宕机，不会丢失数据，不会导致不可用 |
| 消息可靠性               | 有较低的概率丢失数据                  | 基本不丢                                           | 经过参数优化配置，可以做到 0 丢失                            | 同 RocketMQ                                                  |
| 功能支持                 | MQ 领域的功能极其完备                 | 基于 erlang 开发，并发能力很强，性能极好，延时很低 | MQ 功能较为完善，还是分布式的，扩展性好                      | 功能较为简单，主要支持简单的 MQ 功能，在大数据领域的实时计算以及日志采集被大规模使用 |

RabbitMQ的时效性是微秒级的，相比较于其他MQ来说，具有更低的时延，并且基于主从架构是实现了高可用，同时丢失消息的概率比较低和较高的并发性能。

## 16、如何保证消息的高可用性

RabbitMQ 有三种模式：单机模式、普通集群模式、镜像集群模式。

#### 16.1、单机模式

单机模式，就是 Demo 级别的，一般就是你本地启动了玩玩儿的，没人生产用单机模式。

#### 16.2、普通集群模式（无高可用性）

普通集群模式，意思就是在多台机器上启动多个 RabbitMQ 实例，每台机器启动一个。你**创建的 queue，只会放在一个 RabbitMQ 实例上**，但是每个实例都同步 queue 的元数据（元数据可以认为是 queue 的一些配置信息，通过元数据，可以找到 queue 所在实例）。你消费的时候，实际上如果连接到了另外一个实例，那么那个实例会从 queue 所在实例上拉取数据过来。

![image-20240410152320513](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410152320513.png)

这种方式确实很麻烦，也不怎么好，**没做到所谓的分布式**，就是个普通集群。因为这导致你要么消费者每次随机连接一个实例然后拉取数据，要么固定连接那个 queue 所在实例消费数据，前者有**数据拉取的开销**，后者导致**单实例性能瓶颈**。

而且如果那个放 queue 的实例宕机了，会导致接下来其他实例就无法从那个实例拉取，如果你**开启了消息持久化**，让 RabbitMQ 落地存储消息的话，**消息不一定会丢**，得等这个实例恢复了，然后才可以继续从这个 queue 拉取数据。

所以这个事儿就比较尴尬了，这就**没有什么所谓的高可用性**，**这方案主要是提高吞吐量的**，就是说让集群中多个节点来服务某个 queue 的读写操作。

#### 16.3、镜像集群模式（高可用性）

这种模式，才是所谓的 RabbitMQ 的高可用模式。跟普通集群模式不一样的是，在镜像集群模式下，你创建的 queue，无论是元数据还是 queue 里的消息都会**存在于多个实例上**，就是说，每个 RabbitMQ 节点都有这个 queue 的一个**完整镜像**，包含 queue 的全部数据的意思。然后每次你写消息到 queue 的时候，都会自动把**消息同步**到多个实例的 queue 上。

![image-20240410153149954](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410153149954.png)

那么**如何开启这个镜像集群模式**呢？其实很简单，RabbitMQ 有很好的管理控制台，就是在后台新增一个策略，这个策略是**镜像集群模式的策略**，指定的时候是可以要求数据同步到所有节点的，也可以要求同步到指定数量的节点，再次创建 queue 的时候，应用这个策略，就会自动将数据同步到其他的节点上去了。

这样的话，好处在于，你任何一个机器宕机了，没事儿，其它机器（节点）还包含了这个 queue 的完整数据，别的 consumer 都可以到其它节点上去消费数据。坏处在于，第一，这个性能开销也太大了吧，消息需要同步到所有机器上，导致网络带宽压力和消耗很重！第二，这么玩儿，不是分布式的，就**没有扩展性可言**了，如果某个 queue 负载很重，你加机器，新增的机器也包含了这个 queue 的所有数据，并**没有办法线性扩展**你的 queue。你想，如果这个 queue 的数据量很大，大到这个机器上的容量无法容纳了，此时该怎么办呢？

## 17、如何保证消息的顺序性

一个 queue，多个 consumer。比如，生产者向 RabbitMQ 里发送了三条数据，顺序依次是 data1/data2/data3，压入的是 RabbitMQ 的一个内存队列。有三个消费者分别从 MQ 中消费这三条数据中的一条，结果消费者 2 先执行完操作，把 data2 存入数据库，然后是 data1/data3。这不明显乱了。

![image-20240410153239162](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410153239162.png)

**解决方案：**

拆分多个 queue，每个 queue 一个 consumer，就是多一些 queue 而已，确实是麻烦点，这样也会造成吞吐量下降，可以在消费者内部采用多线程的方式取消费。

![image-20240410153306413](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410153306413.png)

或者就一个 queue 但是对应一个 consumer，然后这个 consumer 内部用内存队列做排队，然后分发给底层不同的 worker 来处理。

注意，这里消费者不直接消费消息，而是将消息根据关键值（比如：订单 id）进行哈希，哈希值相同的消息保存到相同的内存队列里。也就是说，需要保证顺序的消息存到了相同的内存队列，然后由一个唯一的 worker 去处理。

## 18、如何解决消息队列的延时以及过期失效问题

### 18.1、提高消费并行度

绝大部分消息消费行为都属于 IO 密集型，即可能是操作数据库，或者调用 RPC，这类消费行为的消费速度在于后端数据库或者外系统的吞吐量，通过增加消费并行度，可以提高总的消费吞吐量，但是并行度增加到一定程度，反而会下降。所以，应用必须要设置合理的并行度。 如下有几种修改消费并行度的方法：

同一个 ConsumerGroup 下，通过增加 Consumer 实例数量来提高并行度（需要注意的是超过订阅队列数的 Consumer 实例无效）。可以通过加机器，或者在已有机器启动多个进程的方式。 提高单个 Consumer 的消费并行线程，通过修改参数 consumeThreadMin、consumeThreadMax 实现。

### 18.2、批量方式消费

某些业务流程如果支持批量方式消费，则可以很大程度上提高消费吞吐量，例如订单扣款类应用，一次处理一个订单耗时 1 s，一次处理 10 个订单可能也只耗时 2 s，这样即可大幅度提高消费的吞吐量，通过设置 consumer 的 consumeMessageBatchMaxSize 返个参数，默认是 1，即一次只消费一条消息，例如设置为 N，那么每次消费的消息数小于等于 N。

### 18.3、跳过非重要消息

发生消息堆积时，如果消费速度一直追不上发送速度，如果业务对数据要求不高的话，可以选择丢弃不重要的消息。例如，当某个队列的消息数堆积到 100000 条以上，则尝试丢弃部分或全部消息，这样就可以快速追上发送消息的速度。示例代码如下：

```java
public ConsumeConcurrentlyStatus consumeMessage(
            List<MessageExt> msgs,
            ConsumeConcurrentlyContext context) {
    long offset = msgs.get(0).getQueueOffset();
    String maxOffset =
            msgs.get(0).getProperty(Message.PROPERTY_MAX_OFFSET);
    long diff = Long.parseLong(maxOffset) - offset;
    if (diff > 100000) {
        // TODO 消息堆积情况的特殊处理
        return ConsumeConcurrentlyStatus.CONSUME_SUCCESS;
    }
    // TODO 正常消费过程
    return ConsumeConcurrentlyStatus.CONSUME_SUCCESS;
}
```

### 18.4、优化每条消息消费过程

举例如下，某条消息的消费过程如下：

- 根据消息从 DB 查询【数据 1】
- 根据消息从 DB 查询【数据 2】
- 复杂的业务计算
- 向 DB 插入【数据 3】
- 向 DB 插入【数据 4】

这条消息的消费过程中有 4 次与 DB 的 交互，如果按照每次 5ms 计算，那么总共耗时 20ms，假设业务计算耗时 5ms，那么总过耗时 25ms，所以如果能把 4 次 DB 交互优化为 2 次，那么总耗时就可以优化到 15ms，即总体性能提高了 40%。所以应用如果对时延敏感的话，可以把 DB 部署在 SSD 硬盘，相比于 SCSI 磁盘，前者的 RT 会小很多。

## 19、如何设计一个消息队列

消息队列系统，我们从以下几个角度来考虑一下：

- 首先这个 mq 得支持可伸缩性吧，就是需要的时候快速扩容，就可以增加吞吐量和容量，那怎么搞？设计个分布式的系统呗，参照一下 kafka 的设计理念，broker -> topic -> partition，每个 partition 放一个机器，就存一部分数据。如果现在资源不够了，简单啊，给 topic 增加 partition，然后做数据迁移，增加机器，不就可以存放更多数据，提供更高的吞吐量了？
- 其次你得考虑一下这个 mq 的数据要不要落地磁盘吧？那肯定要了，落磁盘才能保证别进程挂了数据就丢了。那落磁盘的时候怎么落啊？顺序写，这样就没有磁盘随机读写的寻址开销，磁盘顺序读写的性能是很高的，这就是 kafka 的思路。
- 其次你考虑一下你的 mq 的可用性啊？这个事儿，具体参考之前可用性那个环节讲解的 kafka 的高可用保障机制。多副本 -> leader & follower -> broker 挂了重新选举 leader 即可对外服务。
- 能不能支持数据 0 丢失啊？可以的，参考我们之前说的那个 kafka 数据零丢失方案。

mq 肯定是很复杂的，面试官问你这个问题，其实是个开放题，他就是看看你有没有从架构角度整体构思和设计的思维以及能力。确实这个问题可以刷掉一大批人，因为大部分人平时不思考这些东西。

# 九、Spring

## 1、Spring的优点

* 通过控制反转和依赖注入实现**松耦合**。

* 支持**面向切面**的编程，并且把应用业务逻辑和系统服务分开。

* 通过**切面和模板**减少样板式代码。
* **声明式事务**的支持。可以从单调冗余的事务管理代码中解脱出来，通过声明式方式灵活地进行事务的管理，提高开发效率和质量。

* 方便**集成各种优秀框架**。内部提供了对各种优秀框架的直接支持（如：Hessian、Quartz、MyBatis等）。

* 方便**程序的测试**。Spring支持Junit4，添加注解便可以测试Spring程序。

## 2、@RestController vs @Controller

**@Controller 返回⼀个⻚⾯**：

单独使用@Controller不加@ResponseBody一般使用在要返回一个视图的情况，这种情况属于比较传统的Spring MVC的应用，对应于前后端不分离的情况

![image-20240410195507918](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410195507918.png)

**@RestController 返回JSON 或 XML 形式数据**：

但@RestController只返回对象，对象数据直接以JSON或XML的形式写入HTTP响应（Response）中，这种情况属于RestFul Web服务，这也是目前日常开发所接触的最常用的情况（前后端分离）。

![image-20240410195707475](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410195707475.png)

**@Controller +@ResponseBody 返回JSON 或 XML 形式数据**：

如果需要在Spring4之前开发Restful Web服务，需要使用@Controller结合@ResponseBody注解，也就是说@Controller + @ResponseBody = @RestController（Spring4后新加的注解）

>@ResponseBody注解的作用是将Controller方法返回的对象通过适当的转换器转换成指定的格式之后，写入到HTTP响应（Response）的body中，通常用来返回JSON或XML数据，返回JSON数据的情况较多

![image-20240410200115273](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240410200115273.png)

## 3、Spring IOC & AOP

### 3.1、IoC

IoC（Inverse of Control:控制反转）是一种设计思想，就是将原本在程序中⼿动创建对象的控制权，交由Spring框架来管理。 IoC在其他语言中也有应用，并非Spring特有，IoC 容器是Spring ⽤来实现 IoC 的载体， IoC 容器实际上就是个Map（key，value）,Map 中存放的是各种对象。

将对象之间的相互依赖关系交给loC容器来管理，并由loC容器完成对象的注入。这样可以很大程度上简化应用的开发，把应用从复杂的依赖关系中解放出来。loC 容器就像是一个工厂一样，当我们需要创建一个对象的时候，只需要配置好配置文件/注解即可，完全不用考虑对象是如何被创建出来的。在实际项目中一个Service类可能有几百甚至上千个类作为它的底层，假如我们需要实例化这个Service，可能要每次都要搞清这个Service所有底层类的构造函数。如果利用loC的话，只需要配置好，然后在需要的地方引用就行了，这大大增加了项目的可维护性且降低了开发难度。

### 3.2、Spring IoC的初始化过程：

![image-20240411093337835](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240411093337835.png)

* 从XML中读取配置文件。

* 将bean标签解析成 BeanDefinition，如解析 property 元素， 并注入到 BeanDefinition 实例中。

* 将 BeanDefinition 注册到容器 BeanDefinitionMap 中。

* BeanFactory 根据 BeanDefinition 的定义信息创建实例和初始化 bean。

### 3.4、AOP

AOP（Aspect-Oriented Programming：面向切面编程）能够将那些与业务无关，却为业务模块所共同调用的逻辑或责任(例如事务处理、日志管理、权限控制等)封装起来，便于减少系统的重复代码，降低模块间的耦合度，并有利于未来的可拓展性和可维护性。

Spring AOP就是基于动态代理的，如果要代理的对象，实现了某个接口，那么Spring AOP会使用JDK Proxy，去创建代理对象，而对于没有实现接口的对象，就无法使用JDK Proxy去进行代理了，这时候Spring AOP会使用Cglib生成一个被代理对象的子类来作为代理，如下图所示：

![image-20240411102809382](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240411102809382.png)

使用AOP之后可以把一些通用功能抽象出来，在需要用到的地方直接使用即可，这样大大简化了代码量。我们需要增加新功能时也方便，这样也提高了系统扩展性。日志功能、事务管理等等场景都用到了AOP。

### 3.5、Spring AOP 和 AspectJ AOP 有什么区别

* Spring AOP属于运行时增强，而AspectJ是编译时增强。Spring AOP基于代理(Proxying)，而AspectJ基于字节码操作(Bytecode Manipulation)。

* Spring AOP已经集成了AspectJ ，AspectJ 应该算的上是Java生态系统中最完整的AOP框架了。AspectJ相比于Spring AOP功能更加强大，但是Spring AOP相对来说更简单。

* 如果切面比较少，那么两者性能差异不大。但是，当切面太多的话， 最好选择AspectJ ，它比Spring AOP快很多。

## 4、Spring通知的类型

在AOP术语中，切面的工作被称为通知。通知实际上是程序运行时要通过Spring AOP框架来触发的代码段。

Spring切面可以应用5种类型的通知：

1. **前置通知**（Before）：在目标方法被调用之前调用通知功能；
2. **后置通知**（After）：在目标方法完成之后调用通知，此时不会关心方法的输出是什么；
3. **返回通知**（After-returning ）：在目标方法成功执行之后调用通知；
4. **异常通知**（After-throwing）：在目标方法抛出异常后调用通知；
5. **环绕通知**（Around）：通知包裹了被通知的方法，在被通知的方法调用之前和调用之后执行自定义的逻辑。

## 5、Bean的生命周期

![image-20240418095011813](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240418095011813.png)

1.调用bean的构造方法创建Bean

2.通过反射调用setter方法进行属性的依赖注入

3.如果Bean实现了`BeanNameAware`接口，Spring将调用`setBeanName`()，设置 `Bean`的name（xml文件中bean标签的id）

4.如果Bean实现了`BeanFactoryAware`接口，Spring将调用`setBeanFactory()`把bean factory设置给Bean

5.如果存在`BeanPostProcessor`，Spring将调用它们的`postProcessBeforeInitialization`（预初始化）方法，在Bean初始化前对其进行处理

6.如果Bean实现了`InitializingBean`接口，Spring将调用它的`afterPropertiesSet`方法，然后调用xml定义的 init-method 方法，两个方法作用类似，都是在初始化 bean 的时候执行

7.如果存在`BeanPostProcessor`，Spring将调用它们的`postProcessAfterInitialization`（后初始化）方法，在Bean初始化后对其进行处理

8.Bean初始化完成，供应用使用，这里分两种情况：

8.1 如果Bean为单例的话，那么容器会返回Bean给用户，并存入缓存池。如果Bean实现了`DisposableBean`接口，Spring将调用它的`destory`方法，然后调用在xml中定义的 `destory-method`方法，这两个方法作用类似，都是在Bean实例销毁前执行。

8.2 如果Bean是多例的话，容器将Bean返回给用户，剩下的生命周期由用户控制。

```java
public interface BeanPostProcessor {
	@Nullable
	default Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
		return bean;
	}
	@Nullable
	default Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
		return bean;
	}
}
public interface InitializingBean {
	void afterPropertiesSet() throws Exception;
}
```

1. 调用构造方法，创建对应的Bean类。此时Bean类中的属性都是空的。
2. 将Bean所依赖的一些数据，如待注入的容器等，填充到Bean对象中。
3. 调用bean内的一些方法，如启动数据库链接等。同时将Bean填充到容器中存储起来，以方便应用程序获取使用。
4. 如果当前不再使用该Bean对象，则调用销毁方法，将当前Bean销毁。

对应着bean的生命周期：

* **实例化 Instantiation**
* **属性赋值 Populate**
* **初始化 Initialization**（这里需要注意，初始化主要负责执行一些Bean的启动、链接方法，如连接数据库等。）
* **销毁 Destruction**

![img](https://img2020.cnblogs.com/blog/1771072/202009/1771072-20200909164026351-1683760583.png)

## 6、BeanFactory和FactoryBean的区别？

**BeanFactory**：管理Bean的容器，Spring中生成的Bean都是由这个接口的实现来管理的。

**FactoryBean**：通常是用来创建比较复杂的bean，一般的bean 直接用xml配置即可，但如果一个bean的创建过程中涉及到很多其他的bean 和复杂的逻辑，直接用xml配置比较麻烦，这时可以考虑用FactoryBean，可以隐藏实例化复杂Bean的细节。

当配置文件中bean标签的class属性配置的实现类是FactoryBean时，通过 getBean()方法返回的不是FactoryBean本身，而是调用FactoryBean#getObject()方法所返回的对象，相当于FactoryBean#getObject()代理了getBean()方法。如果想得到FactoryBean必须使用 '&' + beanName 的方式获取。

Mybatis 提供了 `SqlSessionFactoryBean`，可以简化 `SqlSessionFactory`的配置：

```java
public class SqlSessionFactoryBean implements FactoryBean<SqlSessionFactory>, InitializingBean, ApplicationListener<ApplicationEvent> {
  @Override
  public void afterPropertiesSet() throws Exception {
    notNull(dataSource, "Property 'dataSource' is required");
    notNull(sqlSessionFactoryBuilder, "Property 'sqlSessionFactoryBuilder' is required");
    state((configuration == null && configLocation == null) || !(configuration != null && configLocation != null),
              "Property 'configuration' and 'configLocation' can not specified with together");
    this.sqlSessionFactory = buildSqlSessionFactory();
  }

  protected SqlSessionFactory buildSqlSessionFactory() throws IOException {
	//复杂逻辑
  }
    
  @Override
  public SqlSessionFactory getObject() throws Exception {
    if (this.sqlSessionFactory == null) {
      afterPropertiesSet();
    }
    return this.sqlSessionFactory;
  }
}
```

在 xml 配置 SqlSessionFactoryBean：

```xml
<bean id="tradeSqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataSource" ref="trade" />
    <property name="mapperLocations" value="classpath*:mapper/trade/*Mapper.xml" />
    <property name="configLocation" value="classpath:mybatis-config.xml" />
    <property name="typeAliasesPackage" value="com.bytebeats.mybatis3.domain.trade" />
</bean>
```

Spring 将会在应用启动时创建 `SqlSessionFactory`，并使用 `sqlSessionFactory` 这个名字存储起来。

## 7、BeanFactory和ApplicationContext有什么区别？

BeanFactory和ApplicationContext是Spring的两大核心接口，都可以当做Spring的容器。其中ApplicationContext是BeanFactory的子接口。

两者区别如下：

1、功能上的区别。BeanFactory是Spring里面最底层的接口，包含了各种Bean的定义，读取bean配置文档，管理bean的加载、实例化，控制bean的生命周期，维护bean之间的依赖关系。

ApplicationContext接口作为BeanFactory的派生，除了提供BeanFactory所具有的功能外，还提供了更完整的框架功能，如继承MessageSource、支持国际化、统一的资源文件访问方式、同时加载多个配置文件等功能。

2、加载方式的区别。BeanFactroy采用的是延迟加载形式来注入Bean的，即只有在使用到某个Bean时(调用getBean())，才对该Bean进行加载实例化。这样，我们就不能发现一些存在的Spring的配置问题。如果Bean的某一个属性没有注入，BeanFacotry加载后，直至第一次使用调用getBean方法才会抛出异常。

而ApplicationContext是在容器启动时，一次性创建了所有的Bean。这样，在容器启动时，我们就可以发现Spring中存在的配置错误，这样有利于检查所依赖属性是否注入。 ApplicationContext启动后预载入所有的单例Bean，那么在需要的时候，不需要等待创建bean，因为它们已经创建好了。

相对于基本的BeanFactory，ApplicationContext 唯一的不足是占用内存空间。当应用程序配置Bean较多时，程序启动较慢。

3、创建方式的区别。BeanFactory通常以编程的方式被创建，ApplicationContext还能以声明的方式创建，如使用ContextLoader。

4、注册方式的区别。BeanFactory和ApplicationContext都支持BeanPostProcessor、BeanFactoryPostProcessor的使用，但两者之间的区别是：BeanFactory需要手动注册，而ApplicationContext则是自动注册。

## 8、Bean注入容器有哪些方式？

1、**@Configuration + @Bean**

@Configuration用来声明一个配置类，然后使用 @Bean 注解，用于声明一个bean，将其加入到Spring容器中。

```java
@Configuration
public class MyConfiguration {
    @Bean
    public Person person() {
        Person person = new Person();
        person.setName("大彬");
        return person;
    }
}
```

2、**通过包扫描特定注解的方式**

@ComponentScan放置在我们的配置类上，然后可以指定一个路径，进行扫描带有特定注解的bean，然后加至容器中。

特定注解包括@Controller、@Service、@Repository、@Component

```java
@Component
public class Person {
    //...
}
 
@ComponentScan(basePackages = "com.dabin.test.*")
public class Demo1 {
    public static void main(String[] args) {
        AnnotationConfigApplicationContext applicationContext = new AnnotationConfigApplicationContext(Demo1.class);
        Person bean = applicationContext.getBean(Person.class);
        System.out.println(bean);
    }
}
```

3、**@Import注解导入**

@Import注解平时开发用的不多，但是也是非常重要的，在进行Spring扩展时经常会用到，它经常搭配自定义注解进行使用，然后往容器中导入一个配置文件。

```java
@ComponentScan
/*把用到的资源导入到当前容器中*/
@Import({Person.class})
public class App {
    public static void main(String[] args) throws Exception {
        ConfigurableApplicationContext context = SpringApplication.run(App.class, args);
        System.out.println(context.getBean(Person.class));
        context.close();
    }
}
```

4、**实现BeanDefinitionRegistryPostProcessor进行后置处理。**

在Spring容器启动的时候会执行 BeanDefinitionRegistryPostProcessor 的 postProcessBeanDefinitionRegistry 方法，就是等beanDefinition加载完毕之后，对beanDefinition进行后置处理，可以在此进行调整IOC容器中的beanDefinition，从而干扰到后面进行初始化bean。

在下面的代码中，我们手动向beanDefinitionRegistry中注册了person的BeanDefinition。最终成功将person加入到applicationContext中。

```java
public class Demo1 {
    public static void main(String[] args) {
        AnnotationConfigApplicationContext applicationContext = new AnnotationConfigApplicationContext();
        MyBeanDefinitionRegistryPostProcessor beanDefinitionRegistryPostProcessor = new MyBeanDefinitionRegistryPostProcessor();
        applicationContext.addBeanFactoryPostProcessor(beanDefinitionRegistryPostProcessor);
        applicationContext.refresh();
        Person bean = applicationContext.getBean(Person.class);
        System.out.println(bean);
    }
}
 
class MyBeanDefinitionRegistryPostProcessor implements BeanDefinitionRegistryPostProcessor {
    @Override
    public void postProcessBeanDefinitionRegistry(BeanDefinitionRegistry registry) throws BeansException {
        AbstractBeanDefinition beanDefinition = BeanDefinitionBuilder.rootBeanDefinition(Person.class).getBeanDefinition();
        registry.registerBeanDefinition("person", beanDefinition);
    }
    
    @Override
    public void postProcessBeanFactory(ConfigurableListableBeanFactory beanFactory) throws BeansException {
    }
}
```

5、**使用FactoryBean接口**

如下图代码，使用@Configuration + @Bean的方式将 PersonFactoryBean 加入到容器中，这里没有向容器中直接注入 Person，而是注入 PersonFactoryBean，然后从容器中拿Person这个类型的bean。

```java
@Configuration
public class Demo1 {
    @Bean
    public PersonFactoryBean personFactoryBean() {
        return new PersonFactoryBean();
    }
 
    public static void main(String[] args) {
        AnnotationConfigApplicationContext applicationContext = new AnnotationConfigApplicationContext(Demo1.class);
        Person bean = applicationContext.getBean(Person.class);
        System.out.println(bean);
    }
}
 
class PersonFactoryBean implements FactoryBean<Person> {
    @Override
    public Person getObject() throws Exception {
        return new Person();
    }

    @Override
    public Class<?> getObjectType() {
        return Person.class;
    }
}
```

## 9、Bean的作用域

1、**singleton**：单例，Spring中的bean默认都是单例的。

2、**prototype**：每次请求都会创建一个新的bean实例。

3、**request**：每一次HTTP请求都会产生一个新的bean，该bean仅在当前HTTP request内有效。

4、**session**：每一次HTTP请求都会产生一个新的bean，该bean仅在当前HTTP session内有效。

5、**global-session**：全局session作用域。

| 作用域            | 含义                                                         |
| ----------------- | ------------------------------------------------------------ |
| singleton（默认） | 将单个 bean 定义限定为每个 Spring IoC 容器的单个对象实例。   |
| property          | 将单个 bean 定义限定为任意数量的对象实例                     |
| request           | 每次用户请求时，只生成一个Bean对象。                         |
| session           | 每次Http会话建立到终止时，只能够生成一个对应的Bean实例。     |
| application       | 每次应用启动到终止，只维持一个对应的Bean实例对象。           |
| websocket         | 每次webSocket从建立链接到断开链接，只存在一个对应的Bean实例对象 |

从含义的解释上来看，作用域主要是解决Bean的作用范围的。以singleton和property来说，singleton在创建之后，springboot会保证整个上下文环境中都只存在一个该类型的bean。而如果是property情况，那么每次springboot发生加载的时候，都会新创建一个bean进行注入。

相似的，request、session则是在每次用户请求、每次会话建立都新创建bean进行注入。通过指定作用域，我们就可以判断出当前这个Bean对象的大致生命周期和作用范围。

## 10、Spring自动装配的方式有哪些？

* **基于xml文件的自动装配**：byType(类型），byName(名称)， constructor(根据构造函数）
* **基于注解的自动装配**：@Autowired，@Resource，@Value

Spring的自动装配有三种模式：**byType**(根据类型)，**byName**(根据名称)、**constructor**(根据构造函数)。

**byType**

找到与依赖类型相同的bean注入到另外的bean中，这个过程需要借助setter注入来完成，因此必须存在set方法，否则注入失败。

当xml文件中存在多个相同类型名称不同的实例Bean时，Spring容器依赖注入仍然会失败，因为存在多种适合的选项，Spring容器无法知道该注入那种，此时我们需要为Spring容器提供帮助，指定注入那个Bean实例。可以通过`＜bean＞`标签的autowire-candidate设置为false来过滤那些不需要注入的实例Bean

```xml
<bean id="userDao"  class="com.zejian.spring.springIoc.dao.impl.UserDaoImpl" />

<!-- autowire-candidate="false" 过滤该类型 -->
<bean id="userDao2" autowire-candidate="false" class="com.zejian.spring.springIoc.dao.impl.UserDaoImpl" />

<!-- byType 根据类型自动装配userDao-->
<bean id="userService" autowire="byType" class="com.zejian.spring.springIoc.service.impl.UserServiceImpl" />
```

**byName**

将属性名与bean名称进行匹配，如果找到则注入依赖bean。

```xml
<bean id="userDao"  class="com.zejian.spring.springIoc.dao.impl.UserDaoImpl" />
<bean id="userDao2" class="com.zejian.spring.springIoc.dao.impl.UserDaoImpl" />

<!-- byName 根据名称自动装配，找到UserServiceImpl名为 userDao属性并注入-->
<bean id="userService" autowire="byName" class="com.zejian.spring.springIoc.service.impl.UserServiceImpl" />
```

**constructor**

存在单个实例则优先按类型进行参数匹配（无论名称是否匹配），当存在多个类型相同实例时，按名称优先匹配，如果没有找到对应名称，则注入失败。

## 11、@Autowired和@Resource的区别？

Autowire是spring的注解。默认情况下@Autowired是按类型匹配的(byType)。如果需要按名称(byName)匹配的话，可以使用@Qualifier注解与@Autowired结合。@Autowired 可以传递一个`required=false`的属性，false指明当userDao实例存在就注入不存就忽略，如果为true，就必须注入，若userDao实例不存在，就抛出异常。

```java
public class UserServiceImpl implements UserService {
    //标注成员变量
    @Autowired
    @Qualifier("userDao1")
    private UserDao userDao;   
 }
```

Resource是j2ee的注解，默认按 byName模式自动注入。@Resource有两个中重要的属性：name和type。name属性指定bean的名字，type属性则指定bean的类型。因此使用name属性，则按byName模式的自动注入策略，如果使用type属性，则按 byType模式自动注入策略。倘若既不指定name也不指定type属性，Spring容器将通过反射技术默认按byName模式注入。

```java
@Resource(name="userDao")
private UserDao  userDao;//用于成员变量

//也可以用于set方法标注
@Resource(name="userDao")
public void setUserDao(UserDao userDao) {
   this.userDao= userDao;
}
```

上述两种自动装配的依赖注入并不适合简单值类型，如int、boolean、long、String以及Enum等，对于这些类型，Spring容器也提供了@Value注入的方式。

@Value和@Autowired、@Resource类似，也是用来对属性进行注入的，只不过@Value是用来从Properties文件中来获取值的，并且@Value可以解析SpEL(Spring表达式)。

比如，jdbc.properties文件如下：

```properties
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://127.0.0.1:3306/test?characterEncoding=UTF-8&allowMultiQueries=true
jdbc.username=root
jdbc.password=root
```

利用注解@Value获取jdbc.url和jdbc.username的值，实现如下：

```java
public class UserServiceImpl implements UserService {
    //占位符方式
    @Value("${jdbc.url}")
    private String url;
    //SpEL表达方式，其中代表xml配置文件中的id值configProperties
    @Value("#{configProperties['jdbc.username']}")
    private String userName;

}
```

## 12、@Qualifier 注解有什么作用

当需要创建多个相同类型的 bean 并希望仅使用属性装配其中一个 bean 时，可以使用`@Qualifier` 注解和 `@Autowired` 通过指定应该装配哪个 bean 来消除歧义。

## 13、@Bean和@Component有什么区别？

都是使用注解定义 Bean。@Bean 是使用 Java 代码装配 Bean，@Component 是自动装配 Bean。

**@Component 注解用在类上**，表明一个类会作为组件类，并告知Spring要为这个类创建bean，每个类对应一个 Bean。

**@Bean 注解用在方法上**，表示这个方法会返回一个 Bean。@Bean 需要在配置类中使用，即类上需要加上@Configuration注解。

```java
@Component
public class Student {
    private String name = "lkm";
 
    public String getName() {
        return name;
    }
}

@Configuration
public class WebSocketConfig {
    @Bean
    public Student student(){
        return new Student();
    }
}
```

@Bean 注解更加灵活。当需要将第三方类装配到 Spring 容器中，因为没办法源代码上添加@Component注解，只能使用@Bean 注解的方式，当然也可以使用 xml 的方式。

## 14、@Component、@Controller、@Repositor和@Service 的区别？

@Component：最普通的组件，可以被注入到spring容器进行管理。

@Controller：将类标记为 Spring Web MVC 控制器。

@Service：将类标记为业务层组件。

@Repository：将类标记为数据访问组件，即DAO组件。

## 15、Spring 事务实现方式有哪些？

事务就是一系列的操作原子执行。Spring事务机制主要包括声明式事务和编程式事务。

- **编程式事务**：通过编程的方式管理事务，这种方式带来了很大的灵活性，但很难维护。
- **声明式事务**：将事务管理代码从业务方法中分离出来，通过aop进行封装。Spring声明式事务使得我们不需要去处理获得连接、关闭连接、事务提交和回滚等这些操作。使用 `@Transactional` 注解开启声明式事务。

`@Transactional`相关属性如下：

| 属性                   | 类型                               | 描述                                   |
| :--------------------- | ---------------------------------- | -------------------------------------- |
| value                  | String                             | 可选的限定描述符，指定使用的事务管理器 |
| propagation            | enum: Propagation                  | 可选的事务传播行为设置                 |
| isolation              | enum: Isolation                    | 可选的事务隔离级别设置                 |
| readOnly               | boolean                            | 读写或只读事务，默认读写               |
| timeout                | int (in seconds granularity)       | 事务超时时间设置                       |
| rollbackFor            | Class对象数组，必须继承自Throwable | 导致事务回滚的异常类数组               |
| rollbackForClassName   | 类名数组，必须继承自Throwable      | 导致事务回滚的异常类名字数组           |
| noRollbackFor          | Class对象数组，必须继承自Throwable | 不会导致事务回滚的异常类数组           |
| noRollbackForClassName | 类名数组，必须继承自Throwable      | 不会导致事务回滚的异常类名字数组       |

## 16、有哪些事务传播行为？

Spring 事务的传播机制说的是，当多个事务同时存在的时候——一般指的是多个事务方法相互调用时，Spring 如何处理这些事务的行为。事务传播机制是使用简单的 ThreadLocal 实现的，所以，如果调用的方法是在新线程调用的，事务传播实际上是会失效的。

在TransactionDefinition接口中定义了七个事务传播行为：

1. `PROPAGATION_REQUIRED`如果存在一个事务，则支持当前事务。如果没有事务则开启一个新的事务。如果嵌套调用的两个方法都加了事务注解，并且运行在相同线程中，则这两个方法使用相同的事务中。如果运行在不同线程中，则会开启新的事务。
2. `PROPAGATION_SUPPORTS` 如果存在一个事务，支持当前事务。如果没有事务，则非事务的执行。
3. `PROPAGATION_MANDATORY` 如果已经存在一个事务，支持当前事务。如果不存在事务，则抛出异常`IllegalTransactionStateException`。
4. `PROPAGATION_REQUIRES_NEW` 总是开启一个新的事务。需要使用JtaTransactionManager作为事务管理器。
5. `PROPAGATION_NOT_SUPPORTED` 总是非事务地执行，并挂起任何存在的事务。需要使用JtaTransactionManager作为事务管理器。
6. `PROPAGATION_NEVER` 总是非事务地执行，如果存在一个活动事务，则抛出异常。
7. `PROPAGATION_NESTED` 如果一个活动的事务存在，则运行在一个嵌套的事务中。如果没有活动事务, 则按PROPAGATION_REQUIRED 属性执行。

**PROPAGATION_NESTED 与PROPAGATION_REQUIRES_NEW的区别:**

使用`PROPAGATION_REQUIRES_NEW`时，内层事务与外层事务是两个独立的事务。一旦内层事务进行了提交后，外层事务不能对其进行回滚。两个事务互不影响。

使用`PROPAGATION_NESTED`时，外层事务的回滚可以引起内层事务的回滚。而内层事务的异常并不会导致外层事务的回滚，它是一个真正的嵌套事务。

## 17、Spring事务在什么情况下会失效？

**1.访问权限问题**

java的访问权限主要有四种：private、default、protected、public，它们的权限从左到右，依次变大。

如果事务方法的访问权限不是定义成public，这样会导致事务失效，因为spring要求被代理方法必须是`public`的。

翻开源码，可以看到，在`AbstractFallbackTransactionAttributeSource`类的`computeTransactionAttribute`方法中有个判断，如果目标方法不是public，则返回null，即不支持事务。

```java
protected TransactionAttribute computeTransactionAttribute(Method method, @Nullable Class<?> targetClass) {
    // Don't allow no-public methods as required.
    if (allowPublicMethodsOnly() && !Modifier.isPublic(method.getModifiers())) {
      return null;
    }
	...
}
```

**2. 方法用final修饰**

如果事务方法用final修饰，将会导致事务失效。因为spring事务底层使用了aop，也就是通过jdk动态代理或者cglib，帮我们生成了代理类，在代理类中实现的事务功能。

但如果某个方法用final修饰了，那么在它的代理类中，就无法重写该方法，而添加事务功能。

> 同理，如果某个方法是static的，同样无法通过动态代理，变成事务方法。

**3.对象没有被spring管理**

使用spring事务的前提是：对象要被spring管理，需要创建bean实例。如果类没有加@Controller、@Service、@Component、@Repository等注解，即该类没有交给spring去管理，那么它的方法也不会生成事务。

**4.表不支持事务**

如果MySQL使用的存储引擎是myisam，这样的话是不支持事务的。因为myisam存储引擎不支持事务。

**5.方法内部调用**

如下代码所示，update方法上面没有加 `@Transactional` 注解，调用有 `@Transactional` 注解的 updateOrder 方法，updateOrder 方法上的事务会失效。

因为发生了自身调用，调用该类自己的方法，而没有经过 Spring 的代理类，只有在外部调用事务才会生效。

```java
@Service
public class OrderServiceImpl implements OrderService {

    public void update(Order order) {
        this.updateOrder(order);
    }

    @Transactional
    public void updateOrder(Order order) {
        // update order
    }
}
```

解决方法：

1、再声明一个service，将内部调用改为外部调用

2、使用编程式事务

3、使用AopContext.currentProxy()获取代理对象

```java
@Servcie
public class OrderServiceImpl implements OrderService {
    
   public void update(Order order) {
        ((OrderService)AopContext.currentProxy()).updateOrder(order);
   }

    @Transactional
    public void updateOrder(Order order) {
        // update order
    }
 }
```

**6.未开启事务**

如果是spring项目，则需要在配置文件中手动配置事务相关参数。如果忘了配置，事务肯定是不会生效的。

如果是springboot项目，那么不需要手动配置。因为springboot已经在`DataSourceTransactionManagerAutoConfiguration`类中帮我们开启了事务。

**7.吞了异常**

有时候事务不会回滚，有可能是在代码中手动catch了异常。因为开发者自己捕获了异常，又没有手动抛出，把异常吞掉了，这种情况下spring事务不会回滚。

如果想要spring事务能够正常回滚，必须抛出它能够处理的异常。如果没有抛异常，则spring认为程序是正常的。

## 18、Spring怎么解决循环依赖的问题？

循环依赖指的是两个类中的属性相互依赖对方：例如 A 类中有 B 属性，B 类中有 A属性，从而形成了一个依赖闭环，如下图。

![image-20240524141725011](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240524141725011.png)

循环依赖问题在Spring中主要有三种情况：

- 第一种：通过构造方法进行依赖注入时产生的循环依赖问题。
- 第二种：通过setter方法进行依赖注入且是在多例（原型）模式下产生的循环依赖问题。
- 第三种：通过setter方法进行依赖注入且是在单例模式下产生的循环依赖问题。

只有【第三种方式】的循环依赖问题被 Spring 解决了，其他两种方式在遇到循环依赖问题时，Spring都会产生异常。

Spring 解决单例模式下的setter循环依赖问题的主要方式是通过三级缓存解决循环依赖。三级缓存指的是 Spring 在创建 Bean 的过程中，通过三级缓存来缓存正在创建的 Bean，以及已经创建完成的 Bean 实例。具体步骤如下：

- **实例化 Bean**：Spring 在实例化 Bean 时，会先创建一个空的 Bean 对象，并将其放入一级缓存中。
- **属性赋值**：Spring 开始对 Bean 进行属性赋值，如果发现循环依赖，会将当前 Bean 对象提前暴露给后续需要依赖的 Bean（通过提前暴露的方式解决循环依赖）。
- **初始化 Bean**：完成属性赋值后，Spring 将 Bean 进行初始化，并将其放入二级缓存中。
- **注入依赖**：Spring 继续对 Bean 进行依赖注入，如果发现循环依赖，会从二级缓存中获取已经完成初始化的 Bean 实例。

通过三级缓存的机制，Spring 能够在处理循环依赖时，确保及时暴露正在创建的 Bean 对象，并能够正确地注入已经初始化的 Bean 实例，从而解决循环依赖问题，保证应用程序的正常运行。

## 19、Spring启动过程

1. 读取web.xml文件。
2. 创建 ServletContext，为 ioc 容器提供宿主环境。
3. 触发容器初始化事件，调用 contextLoaderListener.contextInitialized()方法，在这个方法会初始化一个应用上下文WebApplicationContext，即 Spring 的 ioc 容器。ioc 容器初始化完成之后，会被存储到 ServletContext 中。
4. 初始化web.xml中配置的Servlet。如DispatcherServlet，用于匹配、处理每个servlet请求。

## 20、Spring 的单例 Bean 是否有并发安全问题？

当多个用户同时请求一个服务时，容器会给每一个请求分配一个线程，这时多个线程会并发执行该请求对应的业务逻辑，如果业务逻辑有对单例状态的修改（体现为此单例的成员属性），则必须考虑线程安全问题。

**无状态bean和有状态bean**

- 有实例变量的bean，可以保存数据，是非线程安全的。
- 没有实例变量的bean，不能保存数据，是线程安全的。

在Spring中无状态的Bean适合用单例模式，这样可以共享实例提高性能。有状态的Bean在多线程环境下不安全，一般用`Prototype`模式或者使用`ThreadLocal`解决线程安全问题。

## 21、Spring Bean如何保证并发安全？

Spring的Bean默认都是单例的，某些情况下，单例是并发不安全的。

以 `Controller` 举例，假如我们在 `Controller` 中定义了成员变量。当多个请求来临，进入的都是同一个单例的 `Controller` 对象，并对此成员变量的值进行修改操作，因此会互相影响，会有并发安全的问题。

应该怎么解决呢？

为了让多个HTTP请求之间不互相影响，可以采取以下措施：

**1、单例变原型**

对 web 项目，可以 `Controller` 类上加注解 @`Scope("prototype")` 或 `@Scope("request")`，对非 web 项目，在 `Component` 类上添加注解 `@Scope("prototype")` 。

这种方式实现起来非常简单，但是很大程度上增大了 Bean 创建实例化销毁的服务器资源开销。

**2、尽量避免使用成员变量**

在业务允许的条件下，可以将成员变量替换为方法中的局部变量。这种方式个人认为是最恰当的。

**3、使用并发安全的类**

如果非要在单例Bean中使用成员变量，可以考虑使用并发安全的容器，如 `ConcurrentHashMap`、`ConcurrentHashSet` 等等，将我们的成员变量包装到这些并发安全的容器中进行管理即可。

**4、分布式或微服务的并发安全**

如果还要进一步考虑到微服务或分布式服务的影响，方式3便不合适了。这种情况下可以借助于可以共享某些信息的分布式缓存中间件，如Redis等。这样即可保证同一种服务的不同服务实例都拥有同一份共享信息了。

## 22、@Async注解的原理

当我们调用第三方接口或者方法的时候，我们不需要等待方法返回才去执行其它逻辑，这时如果响应时间过长，就会极大的影响程序的执行效率。所以这时就需要使用异步方法来并行执行我们的逻辑。在springboot中可以使用@Async注解实现异步操作。

使用@Async注解实现异步操作的步骤：

1.首先在启动类上添加 @EnableAsync 注解。

```java
@Configuration
@EnableAsync
public class App {
    public static void main(String[] args) {
         ApplicationContext ctx = new  
             AnnotationConfigApplicationContext(App.class);
        MyAsync service = ctx.getBean(MyAsync.class);
        System.out.println(service.getClass());
        service.async1();
        System.out.println("main thread finish...");
    }
}
```

2.在对应的方法上添加@Async注解。

```java
@Component
public class MyAsync {
    @Async
    public void asyncTest() {
        try {
            TimeUnit.SECONDS.sleep(20);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("asyncTest...");
    }
}
```

运行代码，控制台输出：

```java
main thread finish...
asyncTest...
```

证明asyncTest方法异步执行了。

原理：

我们在主启动类上贴了一个@EnableAsync注解，才能使用@Async生效。@EnableAsync的作用是通过@import导入了AsyncConfigurationSelector。在AsyncConfigurationSelector的selectImports方法将ProxyAsyncConfiguration定义为Bean注入容器。在ProxyAsyncConfiguration中通过@Bean的方式注入AsyncAnnotationBeanPostProcessor类。

![image-20240418095426641](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240418095426641.png)

代码如下：

```java
@Import(AsyncConfigurationSelector.class)
public @interface EnableAsync {
}

public class AsyncConfigurationSelector extends AdviceModeImportSelector<EnableAsync> {
	public String[] selectImports(AdviceMode adviceMode) {
		switch (adviceMode) {
			case PROXY:
				return new String[] { ProxyAsyncConfiguration.class.getName() };
			//...
		}
	}
}

public class ProxyAsyncConfiguration extends AbstractAsyncConfiguration {
    @Bean(name = TaskManagementConfigUtils.ASYNC_ANNOTATION_PROCESSOR_BEAN_NAME)
    public AsyncAnnotationBeanPostProcessor asyncAdvisor() {
        //创建postProcessor
        AsyncAnnotationBeanPostProcessor bpp = new AsyncAnnotationBeanPostProcessor();
        //...
    }
}
```

AsyncAnnotationBeanPostProcessor往往期创建了一个增强器AsyncAnnotationAdvisor。在AsyncAnnotationAdvisor的buildAdvice方法中，创建了AnnotationAsyncExecutionInterceptor。

```java
public class AsyncAnnotationBeanPostProcessor extends AbstractBeanFactoryAwareAdvisingPostProcessor {
    @Override
    public void setBeanFactory(BeanFactory beanFactory) {
        super.setBeanFactory(beanFactory);
        //创建一个增强器
        AsyncAnnotationAdvisor advisor = new AsyncAnnotationAdvisor(this.executor, this.exceptionHandler);
        //...
        advisor.setBeanFactory(beanFactory);
        this.advisor = advisor;
    }
}


public class AsyncAnnotationAdvisor extends AbstractPointcutAdvisor implements BeanFactoryAware {
    public AsyncAnnotationAdvisor(
            @Nullable Supplier<Executor> executor, @Nullable Supplier<AsyncUncaughtExceptionHandler> exceptionHandler) {
        //增强方法
        this.advice = buildAdvice(executor, exceptionHandler);
        this.pointcut = buildPointcut(asyncAnnotationTypes);
    }

    // 委托给AnnotationAsyncExecutionInterceptor拦截器
    protected Advice buildAdvice(
            @Nullable Supplier<Executor> executor, @Nullable Supplier<AsyncUncaughtExceptionHandler> exceptionHandler) {
        //拦截器
        AnnotationAsyncExecutionInterceptor interceptor = new AnnotationAsyncExecutionInterceptor(null);
        interceptor.configure(executor, exceptionHandler);
        return interceptor;
    }
}
```

AnnotationAsyncExecutionInterceptor继承自AsyncExecutionInterceptor，间接实现了MethodInterceptor。该拦截器的实现的invoke方法把原来方法的调用提交到新的线程池执行，从而实现了方法的异步。

```java
public class AsyncExecutionInterceptor extends AsyncExecutionAspectSupport implements MethodInterceptor, Ordered {
    public Object invoke(final MethodInvocation invocation) throws Throwable {
        //...
        //构建放到AsyncTaskExecutor执行Callable Task
        Callable<Object> task = () -> {
            //...
        };
        //提交到新的线程池执行
        return doSubmit(task, executor, invocation.getMethod().getReturnType());
    }
}
```

由上面分析可以看到，@Async注解其实是通过代理的方式来实现异步调用的。

那使用@Async有什么要注意的呢？

1.使用@Aysnc的时候最好配置一个线程池Executor以让线程复用节省资源，或者为SimpleAsyncTaskExecutor设置基于线程池实现的ThreadFactory，在否则会默认使用SimpleAsyncTaskExecutor，该executor会在每次调用时新建一个线程。

2.调用本类的异步方法是不会起作用的。这种方式绕过了代理而直接调用了方法，@Async注解会失效。

## 23、为什么 Spring和IDEA 都不推荐使用 @Autowired 注解？

idea 在我们经常使用的`@Autowired` 注解上添加了警告。警告内容是: `Field injection is not recommended`, 译为: **不推荐使用属性注入**。

Spring常用的注入方式有：属性注入, 构造方法注入, set 方法注入

- 构造器注入：利用构造方法的参数注入依赖
- set方法注入：调用setter的方法注入依赖
- 属性注入：在字段上使用@Autowired/Resource注解

其中，基于属性注入的方式，容易导致Spring 初始化失败。因为在Spring在初始化的时候，可能由于属性在被注入前就引用而导致空指针异常，进而导致容器初始化失败。

如果可能的话，尽量使用构造器注入。Lombok提供了一个注解`@RequiredArgsConstructor`, 可以方便我们快速进行构造注入。

@Autowired是属性注入，而且@Autowired默认是按照类型匹配（ByType），因此有可能会出现两个相同的类型bean，进而导致Spring 装配失败。

如果要使用属性注入的话，可以使用 `@Resource` 代替 `@Autowired` 注解。@Resource默认是按照名称匹配（ByName），如果找不到则是ByType注入。另外，@Autowired是Spring提供的，@Resource是JSR-250提供的，是Java标准，我们使用的IoC容器会去兼容它，这样即使更换容器，也可以正常工作。

## 24、JDK动态代理和cglib的区别

- JDK代理只能对实现接口的类生成代理；CGLib是针对类实现代理，对指定的类生成一个子类，并覆盖其中的方法，这种通过继承类的实现方式，不能代理final修饰的类。
- JDK代理使用的是反射机制实现aop的动态代理，CGLib代理使用字节码处理框架ASM，通过修改字节码生成子类。所以jdk动态代理的方式创建代理对象效率较高，执行效率较低，CGLib创建效率较低，执行效率高。
- JDK动态代理机制是委托机制，具体说动态实现接口类，在动态生成的实现类里面委托hanlder去调用原始实现类方法，CGLib则使用的继承机制，具体说被代理类和代理类是继承关系，所以代理类是可以赋值给被代理类的，如果被代理类有接口，那么代理类也可以赋值给接口。

![image-20240516212348337](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240516212348337.png)

# 十、SpringBoot

## 1、Springboot的优点

- 内置servlet容器，不需要在服务器部署 tomcat。只需要将项目打成 jar 包，使用 java -jar xxx.jar一键式启动项目
- SpringBoot提供了starter，把常用库聚合在一起，简化复杂的环境配置，快速搭建spring应用环境
- 可以快速创建独立运行的spring项目，集成主流框架
- 准生产环境的运行应用监控

## 2、Javaweb、spring、springmvc和springboot有什么区别，都是做什么用的？

JavaWeb是 Java 语言的 Web 开发技术，主要用于开发 Web 应用程序，包括基于浏览器的客户端和基于服务器的 Web 服务器。

Spring是一个轻量级的开源开发框架，主要用于管理 Java 应用程序中的组件和对象，并提供各种服务，如事务管理、安全控制、面向切面编程和远程访问等。它是一个综合性框架，可应用于所有类型的 Java 应用程序。

SpringMVC是 Spring 框架中的一个模块，用于开发 Web 应用程序并实现 MVC（模型-视图-控制器）设计模式，它将请求和响应分离，从而使得应用程序更加模块化、可扩展和易于维护。

Spring Boot是基于 Spring 框架开发的用于开发 Web 应用程序的框架，它帮助开发人员快速搭建和配置一个独立的、可执行的、基于 Spring 的应用程序，从而减少了繁琐和重复的配置工作。

综上所述，JavaWeb是基于 Java 语言的 Web 开发技术，而 Spring 是一个综合性的开发框架，SpringMVC用于开发 Web 应用程序实现 MVC 设计模式，而 Spring Boot 是基于 Spring 的 Web 应用程序开发框架。

## 3、SpringBoot 中的 starter 到底是什么 ?

starter提供了一个自动化配置类，一般命名为 XXXAutoConfiguration ，在这个配置类中通过条件注解来决定一个配置是否生效（条件注解就是 Spring 中原本就有的），然后它还会提供一系列的默认配置，也允许开发者根据实际情况自定义相关配置，然后通过类型安全的属性注入将这些配置属性注入进来，新注入的属性会代替掉默认属性。正因为如此，很多第三方框架，我们只需要引入依赖就可以直接使用了。

## 4、运行 SpringBoot 有哪几种方式？

1. 打包用命令或者者放到容器中运行
2. 用 Maven/Gradle 插件运行
3. 直接执行 main 方法运行

## 5、SpringBoot 常用的 Starter 有哪些？

1. spring-boot-starter-web ：提供 Spring MVC + 内嵌的 Tomcat 。
2. spring-boot-starter-data-jpa ：提供 Spring JPA + Hibernate 。
3. spring-boot-starter-data-Redis ：提供 Redis 。
4. mybatis-spring-boot-starter ：提供 MyBatis 。

## 6、Spring Boot 的核心注解是哪个？

启动类上面的注解是@SpringBootApplication，它也是 Spring Boot 的核心注解，主要组合包含了以下 3 个注解：

- @SpringBootConfiguration：组合了 @Configuration 注解，实现配置文件的功能。
- @EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能： @SpringBootApplication(exclude = { DataSourceAutoConfiguration.class })。
- @ComponentScan：Spring组件扫描。

## 7、实现自动配置

实现当某个类存在时，自动配置这个类的bean，并且可以在application.properties中配置bean的属性。

（1）新建Maven项目spring-boot-starter-hello，修改pom.xml如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.tyson</groupId>
    <artifactId>spring-boot-starter-hello</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-autoconfigure</artifactId>
            <version>1.3.0.M1</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>3.8.1</version>
        </dependency>
    </dependencies>

</project>
```

（2）属性配置

```java
public class HelloService {
    private String msg;

    public String getMsg() {
        return msg;
    }

    public void setMsg(String msg) {
        this.msg = msg;
    }

    public String sayHello() {
        return "hello" + msg;

    }
}


import org.springframework.boot.context.properties.ConfigurationProperties;

@ConfigurationProperties(prefix="hello")
public class HelloServiceProperties {
    private static final String MSG = "world";
    private String msg = MSG;

    public String getMsg() {
        return msg;
    }

    public void setMsg(String msg) {
        this.msg = msg;
    }
}
```

（3）自动配置类

```java
import com.tyson.service.HelloService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.autoconfigure.condition.ConditionalOnClass;
import org.springframework.boot.autoconfigure.condition.ConditionalOnMissingBean;
import org.springframework.boot.autoconfigure.condition.ConditionalOnProperty;
import org.springframework.boot.context.properties.EnableConfigurationProperties;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
@EnableConfigurationProperties(HelloServiceProperties.class) //1
@ConditionalOnClass(HelloService.class) //2
@ConditionalOnProperty(prefix="hello", value = "enabled", matchIfMissing = true) //3
public class HelloServiceAutoConfiguration {

    @Autowired
    private HelloServiceProperties helloServiceProperties;

    @Bean
    @ConditionalOnMissingBean(HelloService.class) //4
    public HelloService helloService() {
        HelloService helloService = new HelloService();
        helloService.setMsg(helloServiceProperties.getMsg());
        return helloService;
    }
}
```

1. @EnableConfigurationProperties 注解开启属性注入，将带有@ConfigurationProperties 注解的类注入为Spring 容器的 Bean。
2. 当 HelloService 在类路径的条件下。
3. 当设置 hello=enabled 的情况下，如果没有设置则默认为 true，即条件符合。
4. 当容器没有这个 Bean 的时候。

（4）注册配置

想要自动配置生效，需要注册自动配置类。在 src/main/resources 下新建 META-INF/spring.factories。添加以下内容：

```factories
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
com.tyson.config.HelloServiceAutoConfiguration
```

"\"是为了换行后仍然能读到属性。若有多个自动配置，则用逗号隔开。

（5）使用starter

在 Spring Boot 项目的 pom.xml 中添加：

```xml
<dependency>
    <groupId>com.tyson</groupId>
    <artifactId>spring-boot-starter-hello</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```

运行类如下：

```java
import com.tyson.service.HelloService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@SpringBootApplication
public class SpringbootDemoApplication {

    @Autowired
    public HelloService helloService;

    @RequestMapping("/")
    public String index() {
        return helloService.getMsg();
    }

    public static void main(String[] args) {
        SpringApplication.run(SpringbootDemoApplication.class, args);
    }

}
```

在项目中没有配置 HelloService bean，但是我们可以注入这个bean，这是通过自动配置实现的。

在 application.properties 中添加 debug 属性，运行配置类，在控制台可以看到：

```java
   HelloServiceAutoConfiguration matched:
      - @ConditionalOnClass found required class 'com.tyson.service.HelloService' (OnClassCondition)
      - @ConditionalOnProperty (hello.enabled) matched (OnPropertyCondition)

   HelloServiceAutoConfiguration#helloService matched:
      - @ConditionalOnMissingBean (types: com.tyson.service.HelloService; SearchStrategy: all) did not find any beans (OnBeanCondition)
```

可以在 application.properties 中配置 msg 的内容：

```properties
hello.msg=大彬
```

## 8、@Value注解的原理

@Value的解析就是在bean初始化阶段。BeanPostProcessor定义了bean初始化前后用户可以对bean进行操作的接口方法，它的一个重要实现类`AutowiredAnnotationBeanPostProcessor`为bean中的@Autowired和@Value注解的注入功能提供支持。

## 9、Spring Boot 需要独立的容器运行吗？

不需要，内置了 Tomcat/ Jetty 等容器。

## 10、Spring Boot 支持哪些日志框架？

Spring Boot 支持 Java Util Logging, Log4j2, Lockback 作为日志框架，如果你使用 Starters 启动器，Spring Boot 将使用 Logback 作为默认日志框架，但是不管是那种日志框架他都支持将配置文件输出到控制台或者文件中。

## 11、YAML 配置的优势在哪里 ?

YAML 配置和传统的 properties 配置相比之下，有这些优势：

- 配置有序
- 简洁明了，支持数组，数组中的元素可以是基本数据类型也可以是对象

缺点就是不支持 @PropertySource 注解导入自定义的 YAML 配置。

## 12、什么是 Spring Profiles？

在项目的开发中，有些配置文件在开发、测试或者生产等不同环境中可能是不同的，例如数据库连接、redis的配置等等。那我们如何在不同环境中自动实现配置的切换呢？Spring给我们提供了profiles机制给我们提供的就是来回切换配置文件的功能

Spring Profiles 允许用户根据配置文件（dev，test，prod 等）来注册 bean。因此，当应用程序在开发中运行时，只有某些 bean 可以加载，而在 PRODUCTION中，某些其他 bean 可以加载。假设我们的要求是 Swagger 文档仅适用于 QA 环境，并且禁用所有其他文档。这可以使用配置文件来完成。Spring Boot 使得使用配置文件非常简单。

## 13、SpringBoot多数据源事务如何管理

第一种方式是在service层的@TransactionManager中使用transactionManager指定DataSourceConfig中配置的事务。

第二种是使用jta-atomikos实现分布式事务管理。

## 14、spring-boot-starter-parent 有什么用 ?

新创建一个 Spring Boot 项目，默认都是有 parent 的，这个 parent 就是 spring-boot-starter-parent ，spring-boot-starter-parent 主要有如下作用：

1. 定义了 Java 编译版本。
2. 使用 UTF-8 格式编码。
3. 执行打包操作的配置。
4. 自动化的资源过滤。
5. 自动化的插件配置。
6. 针对 application.properties 和 application.yml 的资源过滤，包括通过 profile 定义的不同环境的配置文件，例如 application-dev.properties 和 application-dev.yml。

## 15、Spring Boot 打成的 jar 和普通的 jar 有什么区别 ?

- Spring Boot 项目最终打包成的 jar 是可执行 jar ，这种 jar 可以直接通过 `java -jar xxx.jar` 命令来运行，这种 jar 不可以作为普通的 jar 被其他项目依赖，即使依赖了也无法使用其中的类。
- Spring Boot 的 jar 无法被其他项目依赖，主要还是他和普通 jar 的结构不同。普通的 jar 包，解压后直接就是包名，包里就是我们的代码，而 Spring Boot 打包成的可执行 jar 解压后，在 `\BOOT-INF\classes` 目录下才是我们的代码，因此无法被直接引用。如果非要引用，可以在 pom.xml 文件中增加配置，将 Spring Boot 项目打包成两个 jar ，一个可执行，一个可引用。

## 16、SpringBoot多数据源拆分的思路

先在properties配置文件中配置两个数据源，创建分包mapper，使用@ConfigurationProperties读取properties中的配置，使用@MapperScan注册到对应的mapper包中 。

## 17、SpringBoot的启动流程

* 首先，SpringBoot会读取配置文件与启动类，配置文件指定了项目的各种配置信息，启动类是应用程序的入口。

* 然后，SpringBoot会使用Spring框架初始化Spring容器，包含创建bean实例、依赖注入等操作。

* 接着，SpringBoot会开启自动配置功能，扫描项目中的类，自动注册bean，以便于可以方便地使用。

* 在完成了自动配置后，SpringBoot会启动内嵌的Web服务器，比如Tomcat或Jetty，在Web服务器上部署应用程序。

* 最后，SpringBoot会启动应用程序本身，启动相应的线程进行服务处理。

## 18、讲一讲你对Spring Boot的理解，以及为什么要用Spring Boot

在使用Spring框架进行开发的过程中，需要配置很多Spring框架包的依赖，如spring-core、spring-bean、spring-context等，而这些配置通常都是重复添加的，而且需要做很多框架使用及环境参数的重复配置，如开启注解、配置日志等。

Spring Boot致力于弱化这些不必要的操作，提供默认配置，当然这些默认配置是可以按需修改的，快速搭建、开发和运行Spring应用。

Spring Boot 的主要优点：

1. **简化开发**：Spring Boot通过约定大于配置的原则和自动化配置，大大简化了Java应用程序的开发和部署过程。开发者无需处理繁琐的配置，可以快速搭建项目并专注于业务逻辑的实现。
2. **集成性强**：Spring Boot提供了大量的起步依赖，涵盖了各种常见的库、框架和组件，使得集成第三方库和服务变得更加容易。同时，Spring Boot内置了大量的功能，如内置容器、安全性、监控等，可以快速集成这些功能到项目中。
3. **独立运行**：Spring Boot应用程序可以独立运行，内嵌了常用的Web服务器，如Tomcat、Jetty等，使得部署变得简单。开发者无需额外配置Web服务器，只需执行一个可执行的JAR文件即可启动应用。
4. **微服务友好**：Spring Boot非常适合构建微服务架构，其轻量级、模块化的特性使得微服务之间的通信和部署变得更加方便。结合Spring Cloud等微服务组件，可以更好地实现微服务架构下的各种功能。

## 19、Spring Boot简化配置具体是如何简化的

Spring 虽然使Java EE轻量级框架，但由于其繁琐的配置，一度被人认为是“配置地狱”。各种XML、Annotation配置会让人眼花缭乱，而且配置多的话，如果出错了也很难找出原因。Spring Boot更多的是采用 Java Config 的方式，对 Spring 进行配置。

举个例子：我新建一个类，但是我不用 @Service注解，也就是说，它是个普通的类，那么我们如何使它也成为一个 Bean 让 Spring 去管理呢？只需要@Configuration 和@Bean两个注解即可，如下：

```
public class TestService {
    public String sayHello () {
        return "Hello Spring Boot!";
    }
}
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class JavaConfig {
    @Bean
    public TestService getTestService() {
        return new TestService();
    }
}
```

@Configuration表示该类是个配置类，@Bean表示该方法返回一个 Bean。这样就把TestService作为 Bean 让 Spring 去管理了，在其他地方，我们如果需要使用该 Bean，和原来一样，直接使用@Resource注解注入进来即可使用，非常方便。

```
@Resource
private TestService testService;
```

另外，部署配置方面，原来 Spring 有多个 xml 和 properties配置，在 Spring Boot 中只需要个 application.yml即可。

# 十一、SpringMVC

## 1、SpringMVC

SpringMVC是一种基于 Java 的实现MVC设计模型的请求驱动类型的轻量级Web框架，属于Spring框架的一个模块。

它通过一套注解，让一个简单的Java类成为处理请求的控制器，而无须实现任何接口。同时它还支持RESTful编程风格的请求。

## 2、什么是MVC模式

MVC的全名是Model View Controller ，是模型(model)－视图(view)－控制器(controller)的缩写，是一种软件设计典范。它是用一种业务逻辑、数据与界面显示分离的方法来组织代码，将众多的业务逻辑聚集到一个部件里面，在需要改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑，达到减少编码的时间。

View，视图是指用户看到并与之交互的界面。比如由html元素组成的网页界面，或者软件的客户端界面。MVC的好处之一在于它能为应用程序处理很多不同的视图。在视图中其实没有真正的处理发生，它只是作为一种输出数据并允许用户操纵的方式。model，模型是指模型表示业务规则。在MVC的三个部件中，模型拥有最多的处理任务。被模型返回的数据是中立的，模型与数据格式无关，这样一个模型能为多个视图提供数据，由于应用于模型的代码只需写一次就可以被多个视图重用，所以减少了代码的重复性。

controller，控制器是指控制器接受用户的输入并调用模型和视图去完成用户的需求，控制器本身不输出任何东西和做任何处理。它只是接收请求并决定调用哪个模型构件去处理请求，然后再确定用哪个视图来显示返回的数据。

## 3、SpringMVC 有哪些优点

1. 与 Spring 集成使用非常方便，生态好。
2. 配置简单，快速上手。
3. 支持 RESTful 风格。
4. 支持各种视图技术，支持各种请求资源映射策略。

## 4、Spring MVC和Struts的区别

1. Spring MVC是基于方法开发，Struts2是基于类开发的。
* Spring MVC会将用户请求的URL路径信息与Controller的某个方法进行映射，所有请求参数会注入到对应方法的形参上，生成Handler对象，对象中只有一个方法；
* Struts每处理一次请求都会实例一个Action，Action类的所有方法使用的请求参数都是Action
  类中的成员变量，随着方法增多，整个Action也会变得混乱。
2. Spring MVC支持单例开发模式，Struts只能使用多例
* Struts由于只能通过类的成员变量接收参数，故只能使用多例。
3. Struts2 的核心是基于一个Filter即StrutsPreparedAndExcuteFilter，Spring MVC的核心是基于一个Servlet即DispatcherServlet(前端控制器)。
4. Struts处理速度稍微比Spring MVC慢，Struts使用了Struts标签，加载数据较慢。

## 5、SpringMVC的工作原理

1. DispatcherServlet 接收用户的请求
2. 找到用于处理request的 handler 和 Interceptors，构造成 HandlerExecutionChain 执行链
3. 找到 handler 相对应的 HandlerAdapter
4. 执行所有注册拦截器的preHandler方法
5. 调用 HandlerAdapter 的 handle() 方法处理请求，返回 ModelAndView
6. 倒序执行所有注册拦截器的postHandler方法
7. 请求视图解析和视图渲染

![image-20240425145438048](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240425145438048.png)

## 6、SpringMVC的主要组件

* 前端控制器（DispatcherServlet）：接收用户请求，给用户返回结果。
* 处理器映射器（HandlerMapping）：根据请求的url路径，通过注解或者xml配置，寻找匹配的Handler。
* 处理器适配器（HandlerAdapter）：Handler 的适配器，调用 handler 的方法处理请求。
* 处理器（Handler）：执行相关的请求处理逻辑，并返回相应的数据和视图信息，将其封装到ModelAndView对象中。
* 视图解析器（ViewResolver）：将逻辑视图名解析成真正的视图View。
* 视图（View）：接口类，实现类可支持不同的View类型（JSP、FreeMarker、Excel等）。

## 7、Spring MVC的常用注解由有哪些

* @Controller：用于标识此类的实例是一个控制器。
* @RequestMapping：映射Web请求（访问路径和参数）。
* @ResponseBody：注解返回数据而不是返回页面
* @RequestBody：注解实现接收 http 请求的 json 数据，将 json 数据转换为 java 对象。
* @PathVariable：获得URL中路径变量中的值
* @RestController：@Controller+@ResponseBody
* @ExceptionHandler标识一个方法为全局异常处理的方法。

## 8、@Controller 注解有什么用

@Controller 注解标记一个类为 Spring Web MVC 控制器。Spring MVC 会将扫描到该注解的类，然后扫描这个类下面带有 @RequestMapping 注解的方法，根据注解信息，为这个方法生成一个对应的处理器对象，在上面的 HandlerMapping 和 HandlerAdapter组件中讲到过。当然，除了添加 @Controller 注解这种方式以外，你还可以实现 Spring MVC 提供的 Controller 或者 HttpRequestHandler 接口，对应的实现类也会被作为一个处理器对象

## 9、@RequestMapping 注解有什么用

@RequestMapping 注解，用于配置处理器的 HTTP 请求方法，URI等信息，这样才能将请求和方法进行映射。这个注解可以作用于类上面，也可以作用于方法上面，在类上面一般是配置这个控制器的 URI 前缀。

## 10、@RestController 和 @Controller 有什么区别

@RestController 注解，在 @Controller 基础上，增加了 @ResponseBody 注解，更加适合目前前后端分离的架构下，提供 Restful API ，返回 JSON 数据格式。

## 11、@RequestMapping 和 @GetMapping 注解有什么不同

1. @RequestMapping ：可注解在类和方法上； @GetMapping 仅可注册在方法上
2. @RequestMapping ：可进行 GET、POST、PUT、DELETE 等请求方法； @GetMapping 是@RequestMapping 的 GET 请求方法的特例。

## 12、@RequestParam 和 @PathVariable 两个注解的区别

两个注解都用于方法参数，获取参数值的方式不同， @RequestParam 注解的参数从请求携带的参数中获取，而 @PathVariable 注解从请求的 URI 中获取

## 13、@RequestBody和@RequestParam的区别

@RequestBody一般处理的是在ajax请求中声明contentType: "application/json; charset=utf-8"时候。也就是json数据或者xml数据。
@RequestParam一般就是在ajax里面没有声明contentType的时候，为默认的x-www-form-urlencoded格式时。

## 14、Spring MVC的异常处理

可以将异常抛给Spring框架，由Spring框架来处理；我们只需要配置简单的异常处理器，在异常处理器中添视图页面即可。

* 使用系统定义好的异常处理器 SimpleMappingExceptionResolver
* 使用自定义异常处理器
* 使用异常处理注解

## 15、SpringMVC 用什么对象从后台向前台传递数据的

1. 将数据绑定到 request；
2. 返回 ModelAndView；
3. 通过ModelMap对象，可以在这个对象里面调用put方法，把对象加到里面，前端就可以通过el表达式拿到；
4. 绑定数据到 Session中。

## 16、SpringMvc的Controller是不是单例模式

单例模式。在多线程访问的时候有线程安全问题，解决方案是在控制器里面不要写可变状态量，如果需要使用这些可变状态，可以使用ThreadLocal，为每个线程单独生成一份变量副本，独立操作，互不影响。

## 17、Spring MVC 拦截器

Spring MVC 拦截器对应HandlerInterceor接口，该接口位于org.springframework.web.servlet的包
中，定义了三个方法，若要实现该接口，就要实现其三个方法：
1. 前置处理（preHandle()方法）：该方法在执行控制器方法之前执行。返回值为Boolean类型，如果返回false，表示拦截请求，不再向下执行，如果返回true，表示放行，程序继续向下执行（如果后面没有其他Interceptor，就会执行controller方法）。所以此方法可对请求进行判断，决定程序是否继续执行，或者进行一些初始化操作及对请求进行预处理。
2. 后置处理（postHandle()方法）：该方法在执行控制器方法调用之后，且在返回ModelAndView之前执行。由于该方法会在DispatcherServlet进行返回视图渲染之前被调用，所以此方法多被用于处理返回的视图，可通过此方法对请求域中的模型和视图做进一步的修改。
3. 已完成处理（afterCompletion()方法）：该方法在执行完控制器之后执行，由于是在Controller方法执行完毕后执行该方法，所以该方法适合进行一些资源清理，记录日志信息等处理操作。

可以通过拦截器进行权限检验，参数校验，记录日志等操作

## 18、Spring MVC 的拦截器和 Filter 过滤器有什么差别

有以下几点：

* 功能相同：拦截器和 Filter 都能实现相应的功能
* 容器不同：拦截器构建在 Spring MVC 体系中；Filter 构建在 Servlet 容器之上
* 使用便利性不同：拦截器提供了三个方法，分别在不同的时机执行；过滤器仅提供一个方法

## 19、什么是REST

REST，英文全称，Resource Representational State Transfer，对资源的访问状态的变化通过url的变化表述出来。

* Resource：资源。资源是REST架构或者说整个网络处理的核心。
* Representational：某种表现形式，比如用JSON，XML，JPEG等。
* State Transfer：状态变化。通过HTTP method实现。
* REST描述的是在网络中client和server的一种交互形式。用大白话来说，就是通过URL就知道要什么资源通过HTTP method就知道要干什么，通过HTTP status code就知道结果如何。

举个例子：

```bash
GET /tasks 获取所有任务
POST /tasks 创建新任务
GET /tasks/{id} 通过任务id获取任务
PUT /tasks/{id} 更新任务
DELETE /tasks/{id} 删除任务
```

GET代表获取一个资源，POST代表添加一个资源，PUT代表修改一个资源，DELETE代表删除一个资源。

server提供的RESTful API中，URL中只使用名词来指定资源，原则上不使用动词。用HTTP StatusCode 传递server的状态信息。比如最常用的 200 表示成功，500 表示Server内部错误等。

## 20、使用REST有什么优势呢

第一，风格统一了，不会出现delUser/deleteUser/removeUser 各种命名的代码了。

第二，面向资源，一目了然，具有自解释性。

第三，充分利用 HTTP 协议本身语义。

# 十二、MongoDB

## 1、mongodb是什么？

MongoDB 是由 C++语言编写的，是一个基于分布式文件存储的开源数据库系统。 再高负载的情况下，添加更多的节点，可以保证服务器性能。 MongoDB 旨在给 WEB 应用提供可扩展的高性能数据存储解决方案。

MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。 MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

## 2、mongodb有哪些特点？

（1）MongoDB 是一个面向文档存储的数据库，操作起来比较简单和容易。

（2）你可以在 MongoDB 记录中设置任何属性的索引 (如： FirstName="Sameer",Address="8 Gandhi Road")来实现更快的排序。

（3）你可以通过本地或者网络创建数据镜像，这使得 MongoDB 有更强的扩展性。

（4）如果负载的增加（需要更多的存储空间和更强的处理能力） ，它可以分布在计算机网络中的其他节点上这就是所谓的分片。

（5）Mongo 支持丰富的查询表达式。查询指令使用 JSON 形式的标记，可轻易查询文档中内嵌的对象及数组。

（6）MongoDb 使用 update()命令可以实现替换完成的文档（数据）或者一些指定的数据字段 。

（7）Mongodb 中的 Map/reduce 主要是用来对数据进行批量处理和聚合操作。

（8）Map 和 Reduce。 Map 函数调用 emit(key,value)遍历集合中所有的记录，将 key 与 value 传给 Reduce 函数进行处理。

（9）Map 函数和 Reduce 函数是使用 Javascript 编写的，并可以通过 db.runCommand 或 mapreduce 命令来执行 MapReduce 操作。

（10）GridFS 是 MongoDB 中的一个内置功能，可以用于存放大量小文件。

（11） MongoDB 允许在服务端执行脚本， 可以用 Javascript 编写某个函数，直接在服务端执行，也可以把函数的定义存储在服务端，下次直接调用即可。

## 3、什么是非关系型数据库

非关系型数据库是对不同于传统关系型数据库的统称。非关系型数据库的显著特点是不使用SQL作为查询语言，数据存储不需要特定的表格模式。由于简单的设计和非常好的性能所以被用于大数据和Web Apps等

## 4、为什么用MongoDB？

- 架构简单
- 没有复杂的连接
- 深度查询能力,MongoDB支持动态查询。
- 容易调试
- 容易扩展
- 不需要转化/映射应用对象到数据库对象
- 使用内部内存作为存储工作区,以便更快的存取数据。

## 5、在哪些场景使用MongoDB

- 大数据
- 内容管理系统
- 移动端Apps
- 数据管理

## 6、MySQL与MongoDB之间最基本的差别是什么?

MySQL和MongoDB两者都是免费开源的数据库。MySQL和MongoDB有许多基本差别包括数据的表示(data representation)，查询，关系，事务，schema的设计和定义，标准化(normalization)，速度和性能。

通过比较MySQL和MongoDB，实际上我们是在比较关系型和非关系型数据库，即数据存储结构不同。

## 7、MongoDB成为最好NoSQL数据库的原因是什么?

以下特点使得MongoDB成为最好的NoSQL数据库：

- 面向文件的
- 高性能
- 高可用性
- 易扩展性
- 丰富的查询语言

## 8、journal回放在条目(entry)不完整时(比如恰巧有一个中途故障了)会遇到问题吗?

每个journal (group)的写操作都是一致的，除非它是完整的否则在恢复过程中它不会回放。

## 9、分析器在MongoDB中的作用是什么?

MongoDB中包括了一个可以显示数据库中每个操作性能特点的数据库分析器。通过这个分析器你可以找到比预期慢的查询(或写操作);利用这一信息，比如，可以确定是否需要添加索引。

## 10、名字空间(namespace)是什么?

MongoDB存储BSON对象在丛集(collection)中。数据库名字和丛集名字以句点连结起来叫做名字空间(namespace)。

## 11、允许空值null吗?

对于对象成员而言，是的。然而用户不能够添加空值(null)到数据库丛集(collection)因为空值不是对象。然而用户能够添加空对象{}。

## 12、更新操作立刻fsync到磁盘?

不会，磁盘写操作默认是延迟执行的。写操作可能在两三秒(默认在60秒内)后到达磁盘。例如，如果一秒内数据库收到一千个对一个对象递增的操作，仅刷新磁盘一次。(注意，尽管fsync选项在命令行和经过getLastError_old是有效的)

## 13、如何执行事务/加锁?

MongoDB没有使用传统的锁或者复杂的带回滚的事务，因为它设计的宗旨是轻量，快速以及可预计的高性能。可以把它类比成MySQLMylSAM的自动提交模式。通过精简对事务的支持，性能得到了提升，特别是在一个可能会穿过多个服务器的系统里。

## 14、启用备份故障恢复需要多久?

从备份数据库声明主数据库宕机到选出一个备份数据库作为新的主数据库将花费10到30秒时间。这期间在主数据库上的操作将会失败--包括

写入和强一致性读取(strong consistent read)操作。然而，你还能在第二数据库上执行最终一致性查询(eventually consistent query)(在slaveOk模式下)，即使在这段时间里。

## 15、什么是master或primary?

它是当前备份集群(replica set)中负责处理所有写入操作的主要节点/成员。在一个备份集群中，当失效备援(failover)事件发生时，一个另外的成员会变成primary。

## 16、什么是secondary或slave?

Seconday从当前的primary上复制相应的操作。它是通过跟踪复制oplog([local.oplog.rsopen in new window](http://local.oplog.rs))做到的。

## 17、应该启动一个集群分片(sharded)还是一个非集群分片的 MongoDB 环境?

为开发便捷起见，我们建议以非集群分片(unsharded)方式开始一个 MongoDB 环境，除非一台服务器不足以存放你的初始数据集。从非集群分片升级到集群分片(sharding)是无缝的，所以在你的数据集还不是很大的时候没必要考虑集群分片(sharding)。

## 18、分片(sharding)和复制(replication)是怎样工作的?

每一个分片(shard)是一个分区数据的逻辑集合。分片可能由单一服务器或者集群组成，我们推荐为每一个分片(shard)使用集群。

## 19、数据在什么时候才会扩展到多个分片(shard)里?

MongoDB 分片是基于区域(range)的。所以一个集合(collection)中的所有的对象都被存放到一个块(chunk)中。只有当存在多余一个块的时后，才会有多个分片获取数据的选项。现在，每个默认块的大小是 64Mb，所以你需要至少 64 Mb 空间才可以实施一个迁移。

## 20、如果在一个分片(shard)停止或者很慢的时候，发起一个查询会怎样?

如果一个分片(shard)停止了，除非查询设置了“Partial”选项，否则查询会返回一个错误。如果一个分片(shard)响应很慢，MongoDB则会等待它的响应。

## 21、当更新一个正在被迁移的块（Chunk）上的文档时会发生什么？

更新操作会立即发生在旧的块（Chunk）上，然后更改才会在所有权转移前复制到新的分片上。

## 22、MongoDB在A:{B,C}上建立索引，查询A:{B,C}和A:{C,B}都会使用索引吗？

不会，只会在A:{B,C}上使用索引。

## 23、如果一个分片（Shard）停止或很慢的时候，发起一个查询会怎样？

如果一个分片停止了，除非查询设置了“Partial”选项，否则查询会返回一个错误。如果一个分片响应很慢，MongoDB会等待它的响应。

## 24、MongoDB支持存储过程吗？如果支持的话，怎么用？

MongoDB支持存储过程，它是javascript写的，保存在db.system.js表中。

## 25、如何理解MongoDB中的GridFS机制，MongoDB为何使用GridFS来存储文件？

GridFS是一种将大型文件存储在MongoDB中的文件规范。使用GridFS可以将大文件分隔成多个小文档存放，这样我们能够有效的保存大文档，而且解决了BSON对象有限制的问题。

## 26、mongodb的数据结构

数据库中存储的对象设计bson，一种类似json的二进制文件，由键值对组成。

## 27、MongoDB的优势有哪些

- 面向文档的存储：以 JSON 格式的文档保存数据。
- 任何属性都可以建立索引。
- 复制以及高可扩展性。
- 自动分片。
- 丰富的查询功能。
- 快速的即时更新。
- 来自 MongoDB 的专业支持。

## 28、什么是集合

集合就是一组 MongoDB 文档。它相当于关系型数据库（RDBMS）中的表这种概念。集合位于单独的一个数据库中。一个集合内的多个文档可以有多个不同的字段。一般来说，集合中的文档都有着相同或相关的目的。

## 29、什么是文档

文档由一组key value组成。文档是动态模式,这意味着同一集合里的文档不需要有相同的字段和结构。在关系型数据库中table中的每一条记录相当于MongoDB中的一个文档。

## 30、什么是”mongod“

mongod是处理MongoDB系统的主要进程。它处理数据请求，管理数据存储，和执行后台管理操作。当我们运行mongod命令意味着正在启动MongoDB进程,并且在后台运行。

## 31、"mongod"参数有什么

- 传递数据库存储路径，默认是"/data/db"
- 端口号 默认是 "27017"

## 32、什么是"mongo"

它是一个命令行工具用于连接一个特定的mongod实例。当我们没有带参数运行mongo命令它将使用默认的端口号和localhost连接

## 33、MongoDB哪个命令可以切换数据库

MongoDB 用 use +数据库名称的方式来创建数据库。 use 会创建一个新的数据库，如果该数据库存在，则返回这个数据库。

## 34、MongoDB中的命名空间是什么意思?

MongoDB内部有预分配空间的机制，每个预分配的文件都用0进行填充。

数据文件每新分配一次，它的大小都是上一个数据文件大小的2倍，每个数据文件最大2G。

MongoDB每个集合和每个索引都对应一个命名空间，这些命名空间的元数据集中在16M的*.ns文件中，平均每个命名占用约 628 字节，也即整个数据库的命名空间的上限约为24000。

如果每个集合有一个索引（比如默认的_id索引），那么最多可以创建12000个集合。如果索引数更多，则可创建的集合数就更少了。同时，如果集合数太多，一些操作也会变慢。

要建立更多的集合的话，MongoDB 也是支持的，只需要在启动时加上“--nssize”参数，这样对应数据库的命名空间文件就可以变得更大以便保存更多的命名。这个命名空间文件（.ns文件）最大可以为 2G。

每个命名空间对应的盘区不一定是连续的。与数据文件增长相同，每个命名空间对应的盘区大小都是随分配次数不断增长的。目的是为了平衡命名空间浪费的空间与保持一个命名空间数据的连续性。

需要注意的一个命名空间freelist，这个命名空间用于记录不再使用的盘区（被删除的Collection或索引）。每当命名空间需要分配新盘区时，会先查看freelist，这个命名空间用于记录不再使用的盘区（被删除的Collection或索引）。每当命名空间需要分配新盘区时，会先查看freelist，这个命名空间用于记录不再使用的盘区（被删除的Collection或索引）。每当命名空间需要分配新盘区时，会先查看freelist是否有大小合适的盘区可以使用，如果有就回收空闲的磁盘空间。

## 35、在MongoDB中如何创建一个新的数据库

MongoDB 用 use + 数据库名称 的方式来创建数据库。 use 会创建一个新的数据库，如果该数据库存在，则返回这个数据库。

## 36、MongoDB中的分片是什么意思

分片是将数据水平切分到不同的物理节点。当应用数据越来越大的时候，数据量也会越来越大。当数据量增长时，单台机器有可能无法存储数据或可接受的读取写入吞吐量。利用分片技术可以添加更多的机器来应对数据量增加以及读写操作的要求。

## 37、什么是复制

复制是将数据同步到多个服务器的过程，通过多个数据副本存储到多个服务器上增加数据可用性。复制可以保障数据的安全性，灾难恢复，无需停机维护（如备份，重建索引，压缩），分布式读取数据。

## 38、在MongoDB中如何在集合中插入一个文档

要想将数据插入 MongoDB 集合中，需要使用 insert() 或 save() 方法。

```stylus
>db.collectionName.insert({"key":"value"})
>db.collectionName.save({"key":"value"})
```

## 39、为什么要在MongoDB中使用分析器

数据库分析工具(Database Profiler)会针对正在运行的mongod实例收集数据库命令执行的相关信息。包括增删改查的命令以及配置和管理命令。分析器(profiler)会写入所有收集的数据到 system.profile集合，一个capped集合在管理员数据库。分析器默认是关闭的你能通过per数据库或per实例开启。

## 40、MongoDB支持主键外键关系吗

默认MongoDB不支持主键和外键关系。 用Mongodb本身的API需要硬编码才能实现外键关联，不够直观且难度较大。

## 41、MongoDB支持哪些数据类型

String、Integer、Double、Boolean、Object、Object ID、Arrays、Min/Max Keys、Datetime、Code、Regular Expression等

## 42、"ObjectID"由哪些部分组成

一共有四部分组成:时间戳、客户端ID、客户进程ID、三个字节的增量计数器

_id是一个 12 字节长的十六进制数，它保证了每一个文档的唯一性。在插入文档时，需要提供 _id 。如果你不提供，那么 MongoDB 就会为每一文档提供一个唯一的 id。 _id 的头 4 个字节代表的是当前的时间戳，接着的后 3 个字节表示的是机器 id 号，接着的 2 个字节表示MongoDB 服务器进程 id，最后的 3 个字节代表递增值。

## 43、MongoDb索引

索引用于高效的执行查询。没有索引MongoDB将扫描查询整个集合中的所有文档这种扫描效率很低，需要处理大量数据。索引是一种特殊的数据结构，将一小块数据集保存为容易遍历的形式。索引能够存储某种特殊字段或字段集的值，并按照索引指定的方式将字段值进行排序。

## 44、如何添加索引

使用 db.collection.createIndex() 在集合中创建一个索引

```reasonml
>db.collectionName.createIndex({columnName:1})
```

## 45、在MongoDB中如何更新数据

update() 与 save() 方法都能用于更新集合中的文档。 update() 方法更新已有文档中的值，而 save() 方法则是用传入该方法的文档来替换已有文档。

## 46、如何删除文档

MongoDB 利用 remove() 方法 清除集合中的文档。它有 2 个可选参数：

- deletion criteria：（可选）删除文档的标准。
- justOne：（可选）如果设为 true 或 1，则只删除一个文档。

```maxima
>db.collectionName.remove({key:value})
```

## 47、在MongoDB中如何排序

MongoDB 中的文档排序是通过 sort() 方法来实现的。 sort() 方法可以通过一些参数来指定要进行排序的字段，并使用 1 和 -1 来指定排

序方式，其中 1 表示升序，而 -1 表示降序。

```stylus
>db.connectionName.find({key:value}).sort({columnName:1})
```

## 48、什么是聚合

聚合操作能够处理数据记录并返回计算结果。聚合操作能将多个文档中的值组合起来，对成组数据执行各种操作，返回单一的结果。它相当于 SQL 中的 count(*) 组合 group by。对于 MongoDB 中的聚合操作，应该使用 aggregate() 方法。

```stylus
>db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
```

## 49、在MongoDB中什么是副本集

在MongoDB中副本集由一组MongoDB实例组成，包括一个主节点多个次节点，MongoDB客户端的所有数据都写入主节点(Primary),副节点从主节点同步写入数据，以保持所有复制集内存储相同的数据，提高数据可用性。

# 十三、ElasticSearch

## 1、ES 的分布式架构原理

ElasticSearch 设计的理念就是分布式搜索引擎，底层其实还是基于 lucene 的。核心思想就是在多台机器上启动多个 ES 进程实例，组成了一个 ES 集群。

ES 中存储数据的**基本单位是索引**，比如说你现在要在 ES 中存储一些订单数据，你就应该在 ES 中创建一个索引 `order_idx` ，所有的订单数据就都写到这个索引里面去，一个索引差不多就是相当于是 mysql 里的一个数据库。

```
index -> type -> mapping -> document -> fieldCopy to clipboardErrorCopied
```

这样吧，为了做个更直白的介绍，我在这里做个类比。但是切记，不要划等号，类比只是为了便于理解。

index 相当于 mysql 数据库。而 type 没法跟 mysql 里去对比，一个 index 里可以有多个 type，每个 type 的字段都是差不多的，但是有一些略微的差别。假设有一个 index，是订单 index，里面专门是放订单数据的。就好比说你在 mysql 中建表，有些订单是实物商品的订单，比如一件衣服、一双鞋子；有些订单是虚拟商品的订单，比如游戏点卡，话费充值。就两种订单大部分字段是一样的，但是少部分字段可能有略微的一些差别。

所以就会在订单 index 里，建两个 type，一个是实物商品订单 type，一个是虚拟商品订单 type，这两个 type 大部分字段是一样的，少部分字段是不一样的。

很多情况下，一个 index 里可能就一个 type，但是确实如果说是一个 index 里有多个 type 的情况（**注意**， `mapping types` 这个概念在 ElasticSearch 7. X 已被完全移除，详细说明可以参考[官方文档](https://github.com/elastic/elasticsearch/blob/6.5/docs/reference/mapping/removal_of_types.asciidoc)），你可以认为 index 是一个类别的表，具体的每个 type 代表了 mysql 中的一个表。每个 type 有一个 mapping，如果你认为一个 type 是具体的一个表，index 就代表多个 type 同属于的一个类型，而 mapping 就是这个 type 的**表结构定义**，你在 mysql 中创建一个表，肯定是要定义表结构的，里面有哪些字段，每个字段是什么类型。实际上你往 index 里的一个 type 里面写的一条数据，叫做一条 document，一条 document 就代表了 mysql 中某个表里的一行，每个 document 有多个 field，每个 field 就代表了这个 document 中的一个字段的值。

![es-index-type-mapping-document-field](https://doocs.github.io/advanced-java/docs/high-concurrency/images/es-index-type-mapping-document-field.png)

你搞一个索引，这个索引可以拆分成多个 `shard` ，每个 shard 存储部分数据。拆分多个 shard 是有好处的，一是**支持横向扩展**，比如你数据量是 3T，3 个 shard，每个 shard 就 1T 的数据，若现在数据量增加到 4T，怎么扩展，很简单，重新建一个有 4 个 shard 的索引，将数据导进去；二是**提高性能**，数据分布在多个 shard，即多台服务器上，所有的操作，都会在多台机器上并行分布式执行，提高了吞吐量和性能。

接着就是这个 shard 的数据实际是有多个备份，就是说每个 shard 都有一个 `primary shard` ，负责写入数据，但是还有几个 `replica shard` 。 `primary shard` 写入数据之后，会将数据同步到其他几个 `replica shard` 上去。

![es-cluster](https://doocs.github.io/advanced-java/docs/high-concurrency/images/es-cluster.png)

通过这个 replica 的方案，每个 shard 的数据都有多个备份，如果某个机器宕机了，没关系啊，还有别的数据副本在别的机器上呢。高可用了吧。

ES 集群多个节点，会自动选举一个节点为 master 节点，这个 master 节点其实就是干一些管理的工作的，比如维护索引元数据、负责切换 primary shard 和 replica shard 身份等。要是 master 节点宕机了，那么会重新选举一个节点为 master 节点。

如果是非 master 节点宕机了，那么会由 master 节点，让那个宕机节点上的 primary shard 的身份转移到其他机器上的 replica shard。接着你要是修复了那个宕机机器，重启了之后，master 节点会控制将缺失的 replica shard 分配过去，同步后续修改的数据之类的，让集群恢复正常。

说得更简单一点，就是说如果某个非 master 节点宕机了。那么此节点上的 primary shard 不就没了。那好，master 会让 primary shard 对应的 replica shard（在其他机器上）切换为 primary shard。如果宕机的机器修复了，修复后的节点也不再是 primary shard，而是 replica shard。

其实上述就是 ElasticSearch 作为分布式搜索引擎最基本的一个架构设计。

## 2、ES 写入数据的工作原理

### 2.1、es 写数据过程

- 客户端选择一个 node 发送请求过去，这个 node 就是 `coordinating node` （协调节点）。
- `coordinating node` 对 document 进行**路由**，将请求转发给对应的 node（有 primary shard）。
- 实际的 node 上的 `primary shard` 处理请求，然后将数据同步到 `replica node` 。
- `coordinating node` 如果发现 `primary node` 和所有 `replica node` 都搞定之后，就返回响应结果给客户端。

![es-write](https://doocs.github.io/advanced-java/docs/high-concurrency/images/es-write.png)

### 2.2、es 读数据过程

可以通过 `doc id` 来查询，会根据 `doc id` 进行 hash，判断出来当时把 `doc id` 分配到了哪个 shard 上面去，从那个 shard 去查询。

- 客户端发送请求到**任意**一个 node，成为 `coordinate node` 。
- `coordinate node` 对 `doc id` 进行哈希路由，将请求转发到对应的 node，此时会使用 `round-robin` **随机轮询算法**，在 `primary shard` 以及其所有 replica 中随机选择一个，让读请求负载均衡。
- 接收请求的 node 返回 document 给 `coordinate node` 。
- `coordinate node` 返回 document 给客户端。

### 2.3、es 搜索数据过程

es 最强大的是做全文检索，就是比如你有三条数据：

```
java真好玩儿啊
java好难学啊
j2ee特别牛Copy to clipboardErrorCopied
```

你根据 `java` 关键词来搜索，将包含 `java` 的 `document` 给搜索出来。es 就会给你返回：java 真好玩儿啊，java 好难学啊。

- 客户端发送请求到一个 `coordinate node` 。
- 协调节点将搜索请求转发到**所有**的 shard 对应的 `primary shard` 或 `replica shard` ，都可以。
- query phase：每个 shard 将自己的搜索结果（其实就是一些 `doc id` ）返回给协调节点，由协调节点进行数据的合并、排序、分页等操作，产出最终结果。
- fetch phase：接着由协调节点根据 `doc id` 去各个节点上**拉取实际**的 `document` 数据，最终返回给客户端。

> 写请求是写入 primary shard，然后同步给所有的 replica shard；读请求可以从 primary shard 或 replica shard 读取，采用的是随机轮询算法。

### 2.4、写数据底层原理

![es-write-detail](https://doocs.github.io/advanced-java/docs/high-concurrency/images/es-write-detail.png)

先写入内存 buffer，在 buffer 里的时候数据是搜索不到的；同时将数据写入 translog 日志文件。

如果 buffer 快满了，或者到一定时间，就会将内存 buffer 数据 `refresh` 到一个新的 `segment file` 中，但是此时数据不是直接进入 `segment file` 磁盘文件，而是先进入 `os cache` 。这个过程就是 `refresh` 。

每隔 1 秒钟，es 将 buffer 中的数据写入一个**新的** `segment file` ，每秒钟会产生一个**新的磁盘文件** `segment file` ，这个 `segment file` 中就存储最近 1 秒内 buffer 中写入的数据。

但是如果 buffer 里面此时没有数据，那当然不会执行 refresh 操作，如果 buffer 里面有数据，默认 1 秒钟执行一次 refresh 操作，刷入一个新的 segment file 中。

操作系统里面，磁盘文件其实都有一个东西，叫做 `os cache` ，即操作系统缓存，就是说数据写入磁盘文件之前，会先进入 `os cache` ，先进入操作系统级别的一个内存缓存中去。只要 `buffer` 中的数据被 refresh 操作刷入 `os cache` 中，这个数据就可以被搜索到了。

为什么叫 es 是**准实时**的？ `NRT` ，全称 `near real-time` 。默认是每隔 1 秒 refresh 一次的，所以 es 是准实时的，因为写入的数据 1 秒之后才能被看到。可以通过 es 的 `restful api` 或者 `java api` ，**手动**执行一次 refresh 操作，就是手动将 buffer 中的数据刷入 `os cache` 中，让数据立马就可以被搜索到。只要数据被输入 `os cache` 中，buffer 就会被清空了，因为不需要保留 buffer 了，数据在 translog 里面已经持久化到磁盘去一份了。

重复上面的步骤，新的数据不断进入 buffer 和 translog，不断将 `buffer` 数据写入一个又一个新的 `segment file` 中去，每次 `refresh` 完 buffer 清空，translog 保留。随着这个过程推进，translog 会变得越来越大。当 translog 达到一定长度的时候，就会触发 `commit` 操作。

commit 操作发生第一步，就是将 buffer 中现有数据 `refresh` 到 `os cache` 中去，清空 buffer。然后，将一个 `commit point` 写入磁盘文件，里面标识着这个 `commit point` 对应的所有 `segment file` ，同时强行将 `os cache` 中目前所有的数据都 `fsync` 到磁盘文件中去。最后**清空** 现有 translog 日志文件，重启一个 translog，此时 commit 操作完成。

这个 commit 操作叫做 `flush` 。默认 30 分钟自动执行一次 `flush` ，但如果 translog 过大，也会触发 `flush` 。flush 操作就对应着 commit 的全过程，我们可以通过 es api，手动执行 flush 操作，手动将 os cache 中的数据 fsync 强刷到磁盘上去。

translog 日志文件的作用是什么？你执行 commit 操作之前，数据要么是停留在 buffer 中，要么是停留在 os cache 中，无论是 buffer 还是 os cache 都是内存，一旦这台机器死了，内存中的数据就全丢了。所以需要将数据对应的操作写入一个专门的日志文件 `translog` 中，一旦此时机器宕机，再次重启的时候，es 会自动读取 translog 日志文件中的数据，恢复到内存 buffer 和 os cache 中去。

translog 其实也是先写入 os cache 的，默认每隔 5 秒刷一次到磁盘中去，所以默认情况下，可能有 5 秒的数据会仅仅停留在 buffer 或者 translog 文件的 os cache 中，如果此时机器挂了，会**丢失** 5 秒钟的数据。但是这样性能比较好，最多丢 5 秒的数据。也可以将 translog 设置成每次写操作必须是直接 `fsync` 到磁盘，但是性能会差很多。

- `index.translog.sync_interval` 控制 translog 多久 fsync 到磁盘,最小为 100ms；
- `index.translog.durability` translog 是每 5 秒钟刷新一次还是每次请求都 fsync，这个参数有 2 个取值：request(每次请求都执行 fsync,es 要等 translog fsync 到磁盘后才会返回成功)和 async(默认值，translog 每隔 5 秒钟 fsync 一次)。

实际上你在这里，如果面试官没有问你 es 丢数据的问题，你可以在这里给面试官炫一把，你说，其实 es 第一是准实时的，数据写入 1 秒后可以搜索到；可能会丢失数据的。有 5 秒的数据，停留在 buffer、translog os cache、segment file os cache 中，而不在磁盘上，此时如果宕机，会导致 5 秒的**数据丢失**。

**总结一下**，数据先写入内存 buffer，然后每隔 1s，将数据 refresh 到 os cache，到了 os cache 数据就能被搜索到（所以我们才说 es 从写入到能被搜索到，中间有 1s 的延迟）。每隔 5s，将数据写入 translog 文件（这样如果机器宕机，内存数据全没，最多会有 5s 的数据丢失），translog 大到一定程度，或者默认每隔 30mins，会触发 commit 操作，将缓冲区的数据都 flush 到 segment file 磁盘文件中。

> 数据写入 segment file 之后，同时就建立好了倒排索引。

### 2.5、删除/更新数据底层原理

如果是删除操作，commit 的时候会生成一个 `.del` 文件，里面将某个 doc 标识为 `deleted` 状态，那么搜索的时候根据 `.del` 文件就知道这个 doc 是否被删除了。

如果是更新操作，就是将原来的 doc 标识为 `deleted` 状态，然后新写入一条数据。

buffer 每 refresh 一次，就会产生一个 `segment file` ，所以默认情况下是 1 秒钟一个 `segment file` ，这样下来 `segment file` 会越来越多，此时会定期执行 merge。每次 merge 的时候，会将多个 `segment file` 合并成一个，同时这里会将标识为 `deleted` 的 doc 给**物理删除掉**，然后将新的 `segment file` 写入磁盘，这里会写一个 `commit point` ，标识所有新的 `segment file` ，然后打开 `segment file` 供搜索使用，同时删除旧的 `segment file` 。

### 2.6、底层 lucene

简单来说，lucene 就是一个 jar 包，里面包含了封装好的各种建立倒排索引的算法代码。我们用 Java 开发的时候，引入 lucene jar，然后基于 lucene 的 api 去开发就可以了。

通过 lucene，我们可以将已有的数据建立索引，lucene 会在本地磁盘上面，给我们组织索引的数据结构。

### 2.7、倒排索引

在搜索引擎中，每个文档都有一个对应的文档 ID，文档内容被表示为一系列关键词的集合。例如，文档 1 经过分词，提取了 20 个关键词，每个关键词都会记录它在文档中出现的次数和出现位置。

那么，倒排索引就是**关键词到文档** ID 的映射，每个关键词都对应着一系列的文件，这些文件中都出现了关键词。

举个栗子。

有以下文档：

| DocId | Doc                                            |
| ----- | ---------------------------------------------- |
| 1     | 谷歌地图之父跳槽 Facebook                      |
| 2     | 谷歌地图之父加盟 Facebook                      |
| 3     | 谷歌地图创始人拉斯离开谷歌加盟 Facebook        |
| 4     | 谷歌地图之父跳槽 Facebook 与 Wave 项目取消有关 |
| 5     | 谷歌地图之父拉斯加盟社交网站 Facebook          |

对文档进行分词之后，得到以下**倒排索引**。

| WordId | Word     | DocIds        |
| ------ | -------- | ------------- |
| 1      | 谷歌     | 1, 2, 3, 4, 5 |
| 2      | 地图     | 1, 2, 3, 4, 5 |
| 3      | 之父     | 1, 2, 4, 5    |
| 4      | 跳槽     | 1, 4          |
| 5      | Facebook | 1, 2, 3, 4, 5 |
| 6      | 加盟     | 2, 3, 5       |
| 7      | 创始人   | 3             |
| 8      | 拉斯     | 3, 5          |
| 9      | 离开     | 3             |
| 10     | 与       | 4             |
| ..     | ..       | ..            |

另外，实用的倒排索引还可以记录更多的信息，比如文档频率信息，表示在文档集合中有多少个文档包含某个单词。

那么，有了倒排索引，搜索引擎可以很方便地响应用户的查询。比如用户输入查询 `Facebook` ，搜索系统查找倒排索引，从中读出包含这个单词的文档，这些文档就是提供给用户的搜索结果。

要注意倒排索引的两个重要细节：

- 倒排索引中的所有词项对应一个或多个文档；
- 倒排索引中的词项**根据字典顺序升序排列**

## 3、ES 在数据量很大的情况下（数十亿级别）如何提高查询效率

### 3.1、性能优化的杀手锏——filesystem cache

你往 es 里写的数据，实际上都写到磁盘文件里去了，**查询的时候**，操作系统会将磁盘文件里的数据自动缓存到 `filesystem cache` 里面去。

![es-search-process](https://doocs.github.io/advanced-java/docs/high-concurrency/images/es-search-process.png)

es 的搜索引擎严重依赖于底层的 `filesystem cache` ，你如果给 `filesystem cache` 更多的内存，尽量让内存可以容纳所有的 `idx segment file ` 索引数据文件，那么你搜索的时候就基本都是走内存的，性能会非常高。

性能差距究竟可以有多大？我们之前很多的测试和压测，如果走磁盘一般肯定上秒，搜索性能绝对是秒级别的，1 秒、5 秒、10 秒。但如果是走 `filesystem cache` ，是走纯内存的，那么一般来说性能比走磁盘要高一个数量级，基本上就是毫秒级的，从几毫秒到几百毫秒不等。

这里有个真实的案例。某个公司 es 节点有 3 台机器，每台机器看起来内存很多，64G，总内存就是 `64 * 3 = 192G` 。每台机器给 es jvm heap 是 `32G` ，那么剩下来留给 `filesystem cache` 的就是每台机器才 `32G` ，总共集群里给 `filesystem cache` 的就是 `32 * 3 = 96G` 内存。而此时，整个磁盘上索引数据文件，在 3 台机器上一共占用了 `1T` 的磁盘容量，es 数据量是 `1T` ，那么每台机器的数据量是 `300G` 。这样性能好吗？ `filesystem cache` 的内存才 100G，十分之一的数据可以放内存，其他的都在磁盘，然后你执行搜索操作，大部分操作都是走磁盘，性能肯定差。

归根结底，你要让 es 性能要好，最佳的情况下，就是你的机器的内存，至少可以容纳你的总数据量的一半。

根据我们自己的生产环境实践经验，最佳的情况下，是仅仅在 es 中就存少量的数据，就是你要**用来搜索的那些索引**，如果内存留给 `filesystem cache` 的是 100G，那么你就将索引数据控制在 `100G` 以内，这样的话，你的数据几乎全部走内存来搜索，性能非常之高，一般可以在 1 秒以内。

比如说你现在有一行数据。 `id,name,age ....` 30 个字段。但是你现在搜索，只需要根据 `id,name,age` 三个字段来搜索。如果你傻乎乎往 es 里写入一行数据所有的字段，就会导致说 `90%` 的数据是不用来搜索的，结果硬是占据了 es 机器上的 `filesystem cache` 的空间，单条数据的数据量越大，就会导致 `filesystem cahce` 能缓存的数据就越少。其实，仅仅写入 es 中要用来检索的**少数几个字段**就可以了，比如说就写入 es `id,name,age` 三个字段，然后你可以把其他的字段数据存在 mysql/hbase 里，我们一般是建议用 `es + hbase` 这么一个架构。

hbase 的特点是**适用于海量数据的在线存储**，就是对 hbase 可以写入海量数据，但是不要做复杂的搜索，做很简单的一些根据 id 或者范围进行查询的这么一个操作就可以了。从 es 中根据 name 和 age 去搜索，拿到的结果可能就 20 个 `doc id` ，然后根据 `doc id` 到 hbase 里去查询每个 `doc id` 对应的**完整的数据**，给查出来，再返回给前端。

写入 es 的数据最好小于等于，或者是略微大于 es 的 filesystem cache 的内存容量。然后你从 es 检索可能就花费 20ms，然后再根据 es 返回的 id 去 hbase 里查询，查 20 条数据，可能也就耗费个 30ms，可能你原来那么玩儿，1T 数据都放 es，会每次查询都是 5~10s，现在可能性能就会很高，每次查询就是 50ms。

### 3.2、数据预热

假如说，哪怕是你就按照上述的方案去做了，es 集群中每个机器写入的数据量还是超过了 `filesystem cache` 一倍，比如说你写入一台机器 60G 数据，结果 `filesystem cache` 就 30G，还是有 30G 数据留在了磁盘上。

其实可以做**数据预热**。

举个例子，拿微博来说，你可以把一些大 V，平时看的人很多的数据，你自己提前后台搞个系统，每隔一会儿，自己的后台系统去搜索一下热数据，刷到 `filesystem cache` 里去，后面用户实际上来看这个热数据的时候，他们就是直接从内存里搜索了，很快。

或者是电商，你可以将平时查看最多的一些商品，比如说 iphone 8，热数据提前后台搞个程序，每隔 1 分钟自己主动访问一次，刷到 `filesystem cache` 里去。

对于那些你觉得比较热的、经常会有人访问的数据，最好**做一个专门的缓存预热子系统**，就是对热数据每隔一段时间，就提前访问一下，让数据进入 `filesystem cache` 里面去。这样下次别人访问的时候，性能一定会好很多。

### 3.3、冷热分离

es 可以做类似于 mysql 的水平拆分，就是说将大量的访问很少、频率很低的数据，单独写一个索引，然后将访问很频繁的热数据单独写一个索引。最好是将**冷数据写入一个索引中，然后热数据写入另外一个索引中**，这样可以确保热数据在被预热之后，尽量都让他们留在 `filesystem os cache` 里，**别让冷数据给冲刷掉**。

你看，假设你有 6 台机器，2 个索引，一个放冷数据，一个放热数据，每个索引 3 个 shard。3 台机器放热数据 index，另外 3 台机器放冷数据 index。然后这样的话，你大量的时间是在访问热数据 index，热数据可能就占总数据量的 10%，此时数据量很少，几乎全都保留在 `filesystem cache` 里面了，就可以确保热数据的访问性能是很高的。但是对于冷数据而言，是在别的 index 里的，跟热数据 index 不在相同的机器上，大家互相之间都没什么联系了。如果有人访问冷数据，可能大量数据是在磁盘上的，此时性能差点，就 10% 的人去访问冷数据，90% 的人在访问热数据，也无所谓了。

### 3.4、document 模型设计

对于 MySQL，我们经常有一些复杂的关联查询。在 es 里该怎么玩儿，es 里面的复杂的关联查询尽量别用，一旦用了性能一般都不太好。

最好是先在 Java 系统里就完成关联，将关联好的数据直接写入 es 中。搜索的时候，就不需要利用 es 的搜索语法来完成 join 之类的关联搜索了。

document 模型设计是非常重要的，很多操作，不要在搜索的时候才想去执行各种复杂的乱七八糟的操作。es 能支持的操作就那么多，不要考虑用 es 做一些它不好操作的事情。如果真的有那种操作，尽量在 document 模型设计的时候，写入的时候就完成。另外对于一些太复杂的操作，比如 join/nested/parent-child 搜索都要尽量避免，性能都很差的。

### 3.5、分页性能优化

es 的分页是较坑的，为啥呢？举个例子吧，假如你每页是 10 条数据，你现在要查询第 100 页，实际上是会把每个 shard 上存储的前 1000 条数据都查到一个协调节点上，如果你有个 5 个 shard，那么就有 5000 条数据，接着协调节点对这 5000 条数据进行一些合并、处理，再获取到最终第 100 页的 10 条数据。

分布式的，你要查第 100 页的 10 条数据，不可能说从 5 个 shard，每个 shard 就查 2 条数据，最后到协调节点合并成 10 条数据吧？你**必须**得从每个 shard 都查 1000 条数据过来，然后根据你的需求进行排序、筛选等等操作，最后再次分页，拿到里面第 100 页的数据。你翻页的时候，翻的越深，每个 shard 返回的数据就越多，而且协调节点处理的时间越长，非常坑爹。所以用 es 做分页的时候，你会发现越翻到后面，就越是慢。

我们之前也是遇到过这个问题，用 es 作分页，前几页就几十毫秒，翻到 10 页或者几十页的时候，基本上就要 5~10 秒才能查出来一页数据了。

有什么解决方案吗？

#### 3.5.1、不允许深度分页（默认深度分页性能很差）

跟产品经理说，你系统不允许翻那么深的页，默认翻的越深，性能就越差。

#### 3.5.2、类似于 app 里的推荐商品不断下拉出来一页一页的

类似于微博中，下拉刷微博，刷出来一页一页的，你可以用 `scroll api` ，关于如何使用，自行上网搜索。

scroll 会一次性给你生成**所有数据的一个快照**，然后每次滑动向后翻页就是通过**游标** `scroll_id` 移动，获取下一页下一页这样子，性能会比上面说的那种分页性能要高很多很多，基本上都是毫秒级的。

但是，唯一的一点就是，这个适合于那种类似微博下拉翻页的，**不能随意跳到任何一页的场景**。也就是说，你不能先进入第 10 页，然后去第 120 页，然后又回到第 58 页，不能随意乱跳页。所以现在很多产品，都是不允许你随意翻页的，app，也有一些网站，做的就是你只能往下拉，一页一页的翻。

初始化时必须指定 `scroll` 参数，告诉 es 要保存此次搜索的上下文多长时间。你需要确保用户不会持续不断翻页翻几个小时，否则可能因为超时而失败。

除了用 `scroll api` ，你也可以用 `search_after` 来做， `search_after` 的思想是使用前一页的结果来帮助检索下一页的数据，显然，这种方式也不允许你随意翻页，你只能一页页往后翻。初始化时，需要使用一个唯一值的字段作为 sort 字段。

## 4、ES 生产集群的部署架构是、每个索引的数据量、每个索引的分片数量

其实这个问题没啥，如果你确实干过 es，那你肯定了解你们生产 es 集群的实际情况，部署了几台机器？有多少个索引？每个索引有多大数据量？每个索引给了多少个分片？你肯定知道！

但是如果你确实没干过，也别虚，我给你说一个基本的版本，你到时候就简单说一下就好了。

- es 生产集群我们部署了 5 台机器，每台机器是 6 核 64G 的，集群总内存是 320G。
- 我们 es 集群的日增量数据大概是 2000 万条，每天日增量数据大概是 500MB，每月增量数据大概是 6 亿，15G。目前系统已经运行了几个月，现在 es 集群里数据总量大概是 100G 左右。
- 目前线上有 5 个索引（这个结合你们自己业务来，看看自己有哪些数据可以放 es 的），每个索引的数据量大概是 20G，所以这个数据量之内，我们每个索引分配的是 8 个 shard，比默认的 5 个 shard 多了 3 个 shard。

大概就这么说一下就行了。

# 十四、计算机网络

## 1、TCP/IP 网络模型

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E7%BD%91%E7%BB%9C/tcpip%E5%8F%82%E8%80%83%E6%A8%A1%E5%9E%8B.drawio.png)

数据封装格式：

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost3@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E6%B5%AE%E7%82%B9/%E5%B0%81%E8%A3%85.png)

***网络接口层的传输单位是帧（frame），IP 层的传输单位是包（packet），TCP 层的传输单位是段（segment），HTTP 的传输单位则是消息或报文（message）。但这些名词并没有什么本质的区分，可以统称为数据包。***

### 1.1、应用层

应用层只需要专注于为用户提供应用功能，比如 HTTP、FTP、Telnet、DNS、SMTP等。当两个不同设备的应用需要通信的时候，应用就把应用数据传给下一层，也就是传输层。

### 1.2、传输层

**传输层**（*Transport Layer*）是为应用层提供网络支持的。

TCP 的全称叫传输控制协议（*Transmission Control Protocol*），大部分应用使用的正是 TCP 传输层协议，比如 HTTP 应用层协议。TCP 相比 UDP 多了很多特性，比如流量控制、超时重传、拥塞控制等，这些都是为了保证数据包能可靠地传输给对方。

UDP 相对来说就很简单，简单到只负责发送数据包，不保证数据包是否能抵达对方，但它实时性相对更好，传输效率也高。当然，UDP 也可以实现可靠传输，把 TCP 的特性在应用层上实现就可以，不过要实现一个商用的可靠 UDP 传输协议，也不是一件简单的事情。

应用需要传输的数据可能会非常大，如果直接传输就不好控制，因此当传输层的数据包大小超过 MSS（TCP 最大报文段长度） ，就要将数据包分块，这样即使中途有一个分块丢失或损坏了，只需要重新发送这一个分块，而不用重新发送整个数据包。在 TCP 协议中，我们把每个分块称为一个 **TCP 段**（*TCP Segment*）。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E7%BD%91%E7%BB%9C/https/TCP%E6%AE%B5.png)

当设备作为接收方时，传输层则要负责把数据包传给应用，但是一台设备上可能会有很多应用在接收或者传输数据，因此需要用一个编号将应用区分开来，这个编号就是**端口**。

由于传输层的报文中会携带端口号，因此接收方可以识别出该报文是发送给哪个应用。

### 1.3、网络层

网络层最常使用的是 IP 协议（*Internet Protocol*），IP 协议会将传输层的报文作为数据部分，再加上 IP 包头组装成 IP 报文，如果 IP 报文大小超过 MTU（以太网中一般为 1500 字节）就会**再次进行分片**，得到一个即将发送到网络的 IP 报文。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/12.jpg)

IP 地址：

- 一个是**网络号**，负责标识该 IP 地址是属于哪个「子网」的；
- 一个是**主机号**，负责标识同一「子网」下的不同主机；

在寻址的过程中，先匹配到相同的网络号（表示要找到同一个子网），才会去找对应的主机。

除了寻址能力， IP 协议还有另一个重要的能力就是**路由**。实际场景中，两台设备并不是用一条网线连接起来的，而是通过很多网关、路由器、交换机等众多网络设备连接起来的，那么就会形成很多条网络的路径，因此当数据包到达一个网络节点，就需要通过路由算法决定下一步走哪条路径。

路由器寻址工作中，就是要找到目标地址的子网，找到后进而把数据包转发给对应的网络内。

### 1.4、网络接口层

> 网络接口层主要为网络层提供「链路级别」传输的服务，负责在以太网、WiFi 这样的底层网络上发送原始数据包，工作在网卡这个层次，使用 MAC 地址来标识网络上的设备。

生成了 IP 头部之后，接下来要交给**网络接口层**（*Link Layer*）在 IP 头部的前面加上 MAC 头部，并封装成数据帧（Data frame）发送到网络上。

以太网就是一种在「局域网」内，把附近的设备连接起来，使它们之间可以进行通讯的技术。

以太网在判断网络包目的地时和 IP 的方式不同，因此必须采用相匹配的方式才能在以太网中将包发往目的地，而 MAC 头部就是干这个用的，所以，在以太网进行通讯要用到 MAC 地址。

MAC 头部是以太网使用的头部，它包含了接收方和发送方的 MAC 地址等信息，我们可以通过 ARP 协议获取对方的 MAC 地址。

## 2、请求网页后发生的网络过程

![image-20240522100058891](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240522100058891.png)

- 对 `URL` 进行解析，解析出域名、方法、资源等，然后生成 http 请求报文。
- 对域名进行 dns 解析，首先会看浏览器和操作系统是否有 dns 解析的缓存，如果没有的话，就会通过dns 解析，dns 解析过程：
  - 
- 建立TCP连接：浏览器使用HTTP协议通过TCP/IP建立与百度服务器的连接。它会向百度服务器发送一个SYN（同步）包，然后等待百度服务器的确认响应。
- 三次握手：百度服务器收到浏览器发送的SYN包后，会发送一个SYN+ACK（同步确认）包给浏览器，表示接受连接请求。浏览器收到百度服务器的响应后，会发送一个ACK（确认）包给服务器，完成三次握手，建立可靠的连接。
- 发送HTTP请求：浏览器向百度服务器发送一个HTTP请求，请求百度首页的HTML文档。请求中包含了请求方法、请求头和其他相关信息。
- 服务器处理请求：百度服务器接收到浏览器发送的HTTP请求后，会根据请求的内容进行处理。它可能会读取数据库、执行相关的业务逻辑，并生成响应数据。
- 发送HTTP响应：百度服务器将生成的响应数据封装成HTTP响应报文，并发送回浏览器。响应报文中包含了响应状态码、响应头和响应体等信息。
- 接收响应和渲染页面：浏览器接收到百度服务器发送的HTTP响应后，会解析响应报文，提取出HTML文档和其他相关资源。浏览器会根据HTML文档的结构和CSS样式，渲染出页面的可视化效果。
- 关闭TCP连接：当浏览器完成页面渲染后，会关闭与百度服务器的TCP连接。它会发送一个FIN（结束）包给服务器，表示关闭连接请求。百度服务器收到请求后，会发送一个ACK包给浏览器，表示接受关闭连接请求。最终，浏览器和服务器都关闭了TCP连接。

## 3、DNS域名解析

![DNS 树状结构](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/5.jpg)

域名的层级关系类似一个树状结构：

- 根 DNS 服务器（.）
- 顶级域 DNS 服务器（.com）
- 权威 DNS 服务器（server.com）

![域名解析的工作流程](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/6.jpg)

- 发起DNS查询：当用户在浏览器中输入一个域名（如www.baidu.com）后，操作系统会首先检查本地的DNS缓存，如果有对应的IP地址，则直接返回结果。如果缓存中没有对应的IP地址，操作系统会向本地DNS服务器发送一个DNS查询请求。
- 本地DNS服务器查询：本地DNS服务器收到DNS查询请求后，会先检查自己的缓存，如果有对应的IP地址，则直接返回结果给操作系统。如果本地DNS服务器没有缓存对应的IP地址，它会向根DNS服务器发送一个迭代查询请求。
- 根DNS服务器查询：根DNS服务器是顶级DNS服务器，它存储了全球顶级域名服务器的信息。当根DNS服务器收到迭代查询请求后，它会根据请求的顶级域名（如.com）返回对应的顶级域名服务器的IP地址给本地DNS服务器。
- 顶级域名服务器查询：本地DNS服务器收到根DNS服务器返回的顶级域名服务器的IP地址后，会向顶级域名服务器发送查询请求。顶级域名服务器根据请求的域名（如baidu.com）返回该域名对应的权威域名服务器的IP地址。
- 权威域名服务器查询：本地DNS服务器收到顶级域名服务器返回的权威域名服务器的IP地址后，会向权威域名服务器发送查询请求。权威域名服务器是负责管理该域名下所有主机记录的服务器，它会根据请求的域名返回对应的主机记录的IP地址。
- 返回结果：本地DNS服务器收到权威域名服务器返回的主机记录的IP地址后，会将结果返回给操作系统。操作系统将IP地址返回给浏览器，浏览器根据IP地址建立与服务器的TCP连接，并发起HTTP请求。

## 4、Http请求从客户端到服务器的过程

### 4.1、封装TCP报文

如果 HTTP 请求消息比较长，超过了 `MSS` 的长度，这时 TCP 就需要把 HTTP 的数据拆解成一块块的数据发送，而不是一次性发送所有数据。

![MTU 与 MSS](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/11.jpg)

- `MTU`：一个网络包的最大长度，以太网中一般为 `1500` 字节。
- `MSS`：除去 IP 和 TCP 头部之后，一个网络包所能容纳的 TCP 数据的最大长度。

在双方建立了连接后，TCP 报文中的数据部分就是存放 HTTP 头部 + 数据，组装好 TCP 报文之后，就需交给下面的网络层处理。

![TCP 层报文](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/13.jpg)

### 4.2、封装成IP报文

在 IP 协议里面需要有**源地址 IP** 和 **目标地址 IP**：

- 源地址IP，即是客户端输出的 IP 地址；
- 目标地址，即通过 DNS 域名解析得到的 Web 服务器 IP。

当存在多个网卡时，在填写源地址 IP 时，需要根据**路由表**规则，来判断哪一个网卡作为源地址 IP。

![IP 层报文](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/17.jpg)

### 4.3、封装成MAC报文

在 MAC 包头里需要**发送方 MAC 地址**和**接收方目标 MAC 地址**，用于**两点之间的传输**。

**发送方**的 MAC 地址在网卡生产时写入到 ROM 里的，只要将这个值读取出来写入到 MAC 头部，**接收方**的 MAC 地址需要 `ARP` 协议先找到路由器的 MAC 地址。

![ARP 广播](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/19.jpg)

ARP 协议会在以太网中以**广播**的形式，向以太网中的所有设备发出请求对应IP地址的MAC地址。在后续操作系统会把本次查询结果放到一块叫做 **ARP 缓存**的内存空间

也就是说，在发包时：

- 先查询 ARP 缓存，如果其中已经保存了对方的 MAC 地址，就不需要发送 ARP 查询，直接使用 ARP 缓存中的地址。
- 而当 ARP 缓存中不存在对方 MAC 地址时，则发送 ARP 广播查询。

![MAC 层报文](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/21.jpg)

### 4.4、报文从网卡转发

网络包只是存放在内存中的一串二进制数字信息，没有办法直接发送给对方。因此，我们需要将**数字信息转换为电信号**，才能在网线上传输，也就是说，这才是真正的数据发送过程。

负责执行这一操作的是**网卡**，要控制网卡还需要靠**网卡驱动程序**。

网卡驱动获取网络包之后，会将其**复制**到网卡内的缓存区中，接着会在其**开头加上报头和起始帧分界符，在末尾加上用于检测错误的帧校验序列**。

![数据包](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4/%E7%BD%91%E7%BB%9C/%E6%95%B0%E6%8D%AE%E5%8C%85.drawio.png)

### 4.5、报文从交换机转发

首先，电信号到达网线接口，交换机里的模块进行接收，接下来交换机里的模块将电信号转换为数字信号。然后通过包末尾的 `FCS` 校验错误，如果没问题则放到缓冲区。

计算机的网卡本身具有 MAC 地址，并通过核对收到的包的接收方 MAC 地址判断是不是发给自己的，如果不是发给自己的则丢弃；相对地，交换机的端口不核对接收方 MAC 地址，而是直接接收所有的包并存放到缓冲区中。

将包存入缓冲区后，接下来需要查询一下这个包的接收方 MAC 地址是否已经在 MAC 地址表中有记录了。

交换机的 MAC 地址表主要包含两个信息：

- 一个是设备的 MAC 地址，
- 另一个是该设备连接在交换机的哪个端口上。

***当 MAC 地址表找不到指定的 MAC 地址时，会将包转发到除了源端口之外的所有端口上，无论该设备连接在哪个端口上都能收到这个包。***

### 4.6、路由器转发

> 网络包经过交换机之后，现在到达了**路由器**，并在此被转发到下一个路由器或目标设备。当转发包时，首先路由器端口会接收发给自己的以太网包，然后**路由表**查询转发目标，再由相应的端口作为发送方将以太网包发送出去。

首先，电信号到达网线接口部分，路由器中的模块会将电信号转成数字信号，然后通过包末尾的 `FCS` 进行错误校验。如果没问题则检查 MAC 头部中的**接收方 MAC 地址**，看看是不是发给自己的包，如果是就放到接收缓冲区中，否则就丢弃这个包。完成包接收操作之后，路由器就会**去掉**包开头的 MAC 头部。

接下来，路由器会根据 MAC 头部后方的 `IP` 头部中的内容进行包的转发操作。

首先查询**路由表**判断转发目标。接下来就会进入包的**发送操作**。

* 首先，我们需要根据**路由表的网关列**判断对方的地址。
  * 如果网关是一个 IP 地址，则这个IP 地址就是我们要转发到的目标地址，**还未抵达终点**，还需继续需要路由器转发。
  * 如果网关为空，则 IP 头部中的接收方 IP 地址就是要转发到的目标地址，也是就终于找到 IP 包头里的目标地址了，说明**已抵达终点**。

* 知道对方的 IP 地址之后，接下来需要通过 `ARP` 协议根据 IP 地址查询 MAC 地址，并将查询的结果作为接收方 MAC 地址。

* 接下来是发送方 MAC 地址字段，这里填写输出端口的 MAC 地址。还有一个以太类型字段，填写 `0800` （十六进制）表示 IP 协议。

* 网络包完成后，接下来会将其转换成电信号并通过端口发送出去。

* 发送出去的网络包会通过**交换机**到达下一个路由器。由于接收方 MAC 地址就是下一个路由器的地址，所以交换机会根据这一地址将包传输到下一个路由器。

## 5、HTTP协议

**HTTP 是一个在计算机世界里专门在「两点」之间「传输」文字、图片、音频、视频等「超文本」数据的「约定和规范」。**

### 5.1、HTTP常见状态码

![ 五大类 HTTP 状态码 ](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/6-%E4%BA%94%E5%A4%A7%E7%B1%BBHTTP%E7%8A%B6%E6%80%81%E7%A0%81.png)

### 5.2、HTTP常见字段

* *Host* 字段：客户端发送请求时，用来指定服务器的域名。
* *Content-Length 字段*：服务器在返回数据时，会有 `Content-Length` 字段，表明本次回应的数据长度。
* *Connection 字段*：`Connection` 字段最常用于客户端要求服务器使用「HTTP 长连接」机制，以便其他请求复用。
* *Content-Type 字段*：`Content-Type` 字段用于服务器回应时，告诉客户端，本次数据是什么格式。
* *Content-Encoding 字段*：`Content-Encoding` 字段说明数据的压缩方法。表示服务器返回的数据使用了什么压缩格式

## 6、GET和POST

* **GET 的语义是从服务器获取指定的资源**，这个资源可以是静态的文本、页面、图片视频等。

  * GET 请求的参数位置一般是写在 URL 中，URL 规定只能支持 ASCII，所以 GET 请求的参数只允许 ASCII 字符 ，而且浏览器会对 URL 的长度有限制（HTTP协议本身对 URL长度并没有做任何规定）。

  ![GET 请求](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/12-Get%E8%AF%B7%E6%B1%82.png)

* **POST 的语义是根据请求负荷（报文body）对指定的资源做出处理**，具体的处理方式视资源类型而不同。

  * POST 请求携带数据的位置一般是写在报文 body 中，body 中的数据可以是任意格式的数据，只要客户端与服务端协商好即可，而且浏览器不会对 body 大小做限制。

  ![POST 请求](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/13-Post%E8%AF%B7%E6%B1%82.png)

### 6.1、安全和幂等性

* GET 的语义是请求获取指定的资源。GET 方法是安全、幂等、可被缓存的。

* POST 的语义是根据请求负荷（报文主体）对指定的资源做出处理，具体的处理方式视资源类型而不同。POST 不安全，不幂等，（大部分实现）不可缓存。

## 7、HTTP缓存技术

对于一些具有重复性的 HTTP 请求，比如每次请求得到的数据都一样的，我们可以把这对「请求-响应」的数据都**缓存在本地**，那么下次就直接读取本地的数据，不必在通过网络获取服务器的响应了，这样的话 HTTP/1.1 的性能肯定肉眼可见的提升。

所以，避免发送 HTTP 请求的方法就是通过**缓存技术**，HTTP 设计者早在之前就考虑到了这点，因此 HTTP 协议的头部有不少是针对缓存的字段。

HTTP 缓存有两种实现方式，分别是**强制缓存和协商缓存**。

### 7.1、强制缓存

强缓存指的是只要浏览器判断缓存没有过期，则直接使用浏览器的本地缓存，决定是否使用缓存的主动性在于浏览器这边。

强缓存是利用下面这两个 HTTP 响应头部（Response Header）字段实现的，它们都用来表示资源在客户端缓存的有效期：

- `Cache-Control`， 是一个相对时间；
- `Expires`，是一个绝对时间；

如果 HTTP 响应头部同时有 Cache-Control 和 Expires 字段的话，**Cache-Control 的优先级高于 Expires** 。

Cache-control 选项更多一些，设置更加精细，所以建议使用 Cache-Control 来实现强缓存。具体的实现流程如下：

- 当浏览器第一次请求访问服务器资源时，服务器会在返回这个资源的同时，在 Response 头部加上 Cache-Control，Cache-Control 中设置了过期时间大小；
- 浏览器再次请求访问服务器中的该资源时，会先**通过请求资源的时间与 Cache-Control 中设置的过期时间大小，来计算出该资源是否过期**，如果没有，则使用该缓存，否则重新请求服务器；
- 服务器再次收到请求后，会再次更新 Response 头部的 Cache-Control。

### 7.2、协商缓存

当我们在浏览器使用开发者工具的时候，你可能会看到过某些请求的响应码是 `304`，这个是告诉浏览器可以使用本地缓存的资源，通常这种通过服务端告知客户端是否可以使用缓存的方式被称为协商缓存。

**协商缓存就是与服务端协商之后，通过协商结果来判断是否使用本地缓存**。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/network/http/http%E7%BC%93%E5%AD%98.png)

## 8、HTTP特性（HTTP1.1）

***优点：***

* **简单**：HTTP 基本的报文格式就是 `header + body`，头部信息也是 `key-value` 简单文本的形式，**易于理解**，降低了学习和使用的门槛。
* **灵活和易于扩展**：HTTP 协议里的各类请求方法、URI/URL、状态码、头字段等每个组成要求都没有被固定死，都允许开发人员**自定义和扩充**。同时 HTTP 由于是工作在应用层（ `OSI` 第七层），则它**下层可以随意变化**
* **应用广泛和跨平台**：互联网发展至今，HTTP 的应用范围非常的广泛，从台式机的浏览器到手机上的各种 APP，从看新闻、刷贴吧到购物、理财、吃鸡，HTTP 的应用遍地开花，同时天然具有**跨平台**的优越性。

***缺点：***

* **无状态**：因为服务器不会去记忆 HTTP 的状态，所以不需要额外的资源来记录状态信息，这能减轻服务器的负担，能够把更多的 CPU 和内存用来对外提供服务。但是既然服务器没有记忆能力，它在完成有关联性的操作时会非常麻烦。

  对于无状态的问题，解法方案有很多种，其中比较简单的方式用 **Cookie** 技术。

  * `Cookie` 通过在请求和响应报文中写入 Cookie 信息来控制客户端的状态。

    ![Cookie 技术](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/14-cookie%E6%8A%80%E6%9C%AF.png)

* **明文传输**：明文意味着在传输过程中的信息，是可方便阅读的，比如 Wireshark 抓包都可以直接肉眼查看，为我们调试工作带了极大的便利性。但是这正是这样，HTTP 的所有信息都暴露在了光天化日下，相当于**信息裸奔**。在传输的漫长的过程中，信息的内容都毫无隐私可言，很容易就能被窃取，如果里面有你的账号密码信息，那**你号没了**。
* **不安全**：
  * 通信使用明文（不加密），内容可能会被窃听。
  * 不验证通信方身份，因此有可能遭遇伪装
  * 无法验证报文的完整性，有可能会被篡改

### 8.1、HTTP1.1的性能

HTTP 协议是基于 **TCP/IP**，并且使用了「**请求 - 应答**」的通信模式，所以性能的关键就在这**两点**里。

* **长连接**：只要任意一端没有明确提出断开连接，则保持 TCP 连接状态。如果某个 HTTP 长连接超过一定时间没有任何数据交互，服务端就会主动断开这个连接。
* **管道网络传输**：在同一个 TCP 连接里面，客户端可以发起多个请求，只要第一个请求发出去了，不必等其回来，就可以发第二个请求出去，可以**减少整体的响应时间。**
* **队头阻塞**：当顺序发送的请求序列中的一个请求因为某种原因被阻塞时，在后面排队的所有请求也一同被阻塞了，会招致客户端一直请求不到数据，这也就是「**队头阻塞**」

## 9、HTTP和HTTPs

### 9.1、区别

![HTTP 与 HTTPS 网络层](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/19-HTTPS%E4%B8%8EHTTP.png)

- HTTP 是超文本传输协议，信息是明文传输，存在安全风险的问题。HTTPS 则解决 HTTP 不安全的缺陷，在 TCP 和 HTTP 网络层之间加入了 SSL/TLS 安全协议，使得报文能够加密传输。
- HTTP连接建立相对简单，TCP三次握手之后便可以进行HTTP报文的传输，而HTTPs在TCP三次握手之后，还需要进行SSL/TLS的握手过程，才可以进行加密报文传输。
- 两者的默认端口不同，HTTP采用的是80端口，HTTPs采用的是443端口。
- HTTPs需要向CA（证书权威机构）申请数字证书，来保证服务器的身份是可信的。

### 9.2、HTTPs解决了HTTP中的什么问题

- **窃听风险**：HTTPs使用混合加密（对称加密和非对称加密）的方式实现了信息加密，解决了*窃听风险*
- **篡改风险**：**使用摘要算法（哈希函数）来计算出内容的哈希值**，然后同内容一起传输给对方，对方收到后，先是对内容也计算出哈希值，然后和发送方的哈希值进行对比，如果相同说明没有篡改，否则可以判断出内容已经被篡改，以此来实现校验机制，解决*篡改风险*。
- **冒充风险**：将服务器公钥放在数字证书（由数字证书认证机构颁发）中，只要证书是可信的，公钥就是可信的。以此来实现身份认证，解决*冒充风险*。

### 9.3、HTTPs的建立连接的过程

SSL/TLS 协议基本流程：

- 客户端向服务器索要并验证服务器的公钥。
- 双方协商生产「会话秘钥」。
- 双方采用「会话秘钥」进行加密通信。

TLS 的「握手阶段」涉及**四次**通信，使用不同的密钥交换算法，TLS 握手流程也会不一样的，现在常用的密钥交换算法有两种：[RSA 算法 (opens new window)](https://xiaolincoding.com/network/2_http/https_rsa.html)和 [ECDHE 算法 (opens new window)](https://xiaolincoding.com/network/2_http/https_ecdhe.html)。

![HTTPS 连接建立过程](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/23-HTTPS%E5%B7%A5%E4%BD%9C%E6%B5%81%E7%A8%8B.png)

*1. ClientHello*

首先，由客户端向服务器发起加密通信请求，也就是 `ClientHello` 请求。

在这一步，客户端主要向服务器发送以下信息：

（1）客户端支持的 TLS 协议版本，如 TLS 1.2 版本。

（2）客户端生产的随机数（`Client Random`），后面用于生成「会话秘钥」条件之一。

（3）客户端支持的密码套件列表，如 RSA 加密算法。

*2. SeverHello*

服务器收到客户端请求后，向客户端发出响应，也就是 `SeverHello`。服务器回应的内容有如下内容：

（1）确认 TLS 协议版本，如果浏览器不支持，则关闭加密通信。

（2）服务器生产的随机数（`Server Random`），也是后面用于生产「会话秘钥」条件之一。

（3）确认的密码套件列表，如 RSA 加密算法。

（4）服务器的数字证书。

*3.客户端回应*

客户端收到服务器的回应之后，首先通过浏览器或者操作系统中的 CA 公钥，确认服务器的数字证书的真实性。

如果证书没有问题，客户端会**从数字证书中取出服务器的公钥**，然后使用它加密报文，向服务器发送如下信息：

（1）一个随机数（`pre-master key`）。该随机数会被服务器公钥加密。

（2）加密通信算法改变通知，表示随后的信息都将用「会话秘钥」加密通信。

（3）客户端握手结束通知，表示客户端的握手阶段已经结束。这一项同时把之前所有内容的发生的数据做个摘要，用来供服务端校验。

**服务器和客户端有了这三个随机数（Client Random、Server Random、pre-master key），接着就用双方协商的加密算法，各自生成本次通信的「会话秘钥」**。

*4. 服务器的最后回应*

服务器收到客户端的第三个随机数（`pre-master key`）之后，通过协商的加密算法，计算出本次通信的「会话秘钥」。

然后，向客户端发送最后的信息：

（1）加密通信算法改变通知，表示随后的信息都将用「会话秘钥」加密通信。

（2）服务器握手结束通知，表示服务器的握手阶段已经结束。这一项同时把之前所有内容的发生的数据做个摘要，用来供客户端校验。

至此，整个 TLS 的握手阶段全部结束。接下来，客户端与服务器进入加密通信，就完全是使用普通的 HTTP 协议，只不过用「会话秘钥」加密内容。

### 9.4、HTTPs如何保证应用数据的数据完整性

TLS 在实现上分为**握手协议**和**记录协议**两层：

- TLS 握手协议就是我们前面说的 TLS 四次握手的过程，负责协商加密算法和生成对称密钥，后续用此密钥来保护应用程序数据（即 HTTP 数据）；
- TLS 记录协议负责保护应用程序数据并验证其完整性和来源，所以对 HTTP 数据加密是使用记录协议；

TLS 记录协议主要负责消息（HTTP 数据）的压缩，加密及数据的认证，过程如下图：

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/HTTP/%E8%AE%B0%E5%BD%95%E5%8D%8F%E8%AE%AE.png)

具体过程如下：

- 首先，消息被分割成多个较短的片段,然后分别对每个片段进行压缩。
- 接下来，经过压缩的片段会被**加上消息认证码（MAC 值，这个是通过哈希算法生成的），这是为了保证完整性，并进行数据的认证**。通过附加消息认证码的 MAC 值，可以识别出篡改。与此同时，为了防止重放攻击，在计算消息认证码时，还加上了片段的编码。
- 再接下来，经过压缩的片段再加上消息认证码会一起通过对称密码进行加密。
- 最后，上述经过加密的数据再加上由数据类型、版本号、压缩后的长度组成的报头就是最终的报文数据。

记录协议完成后，最终的报文数据将传递到传输控制协议 (TCP) 层进行传输。

## 10、HTTP1.1优化

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E7%BD%91%E7%BB%9C/http1.1%E4%BC%98%E5%8C%96/%E4%BC%98%E5%8C%96http1.1%E6%8F%90%E7%BA%B2.png)

### 10.1、避免发送HTTP请求

通过缓存技术来避免发送 HTTP 请求。客户端收到第一个请求的响应后，可以将其缓存在本地磁盘，下次请求的时候，如果缓存没过期，就直接读取本地缓存的响应数据。如果缓存过期，客户端发送请求的时候带上响应数据的摘要，服务器比对后发现资源没有变化，就发出不带包体的 304 响应，告诉客户端缓存的响应仍然有效。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E7%BD%91%E7%BB%9C/http1.1%E4%BC%98%E5%8C%96/%E7%BC%93%E5%AD%98etag.png)

### 10.2、减少HTTP请求次数

**减少重定向请求次数**：

* **问题**：服务器上的一个资源可能由于迁移、维护等原因从 url1 移至 url2 后，而客户端不知情，它还是继续请求 url1，这时服务器不能粗暴地返回错误，而是通过 `302` 响应码和 `Location` 头部，告诉客户端该资源已经迁移至 url2 了，于是客户端需要再发送 url2 请求以获得服务器的资源。

  那么，如果重定向请求越多，那么客户端就要多次发起 HTTP 请求，每一次的 HTTP 请求都得经过网络，这无疑会越降低网络性能。

* **解决方案**：将原本由客户端处理的重定向请求，交给代理服务器处理，这样可以减少重定向请求的次数；

  ![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E7%BD%91%E7%BB%9C/http1.1%E4%BC%98%E5%8C%96/%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%87%8D%E5%AE%9A%E5%90%912.png)

**合并请求**：

* 将多个小资源合并成一个大资源再传输，能够减少 HTTP 请求次数以及 头部的重复传输，再来减少 TCP 连接数量，进而省去 TCP 握手和慢启动的网络消耗；

**延迟发送请求**：

* 按需访问资源，只访问当前用户看得到/用得到的资源，当客户往下滑动，再访问接下来的资源，以此达到延迟请求，也就减少了同一时间的 HTTP 请求次数。

### 10.3、减少HTTP相应的数据大小

通过压缩响应资源，降低传输资源的大小，从而提高传输效率。

* **无损压缩**：资源经过压缩后，信息不被破坏，还能完全恢复到压缩前的原样，适合用在文本文件、程序可执行文件、程序源代码。
* **有损压缩**：有损压缩主要将次要的数据舍弃，牺牲一些质量来减少数据量、提高压缩比，这种方法经常用于压缩多媒体数据，比如音频、视频、图片。

## 11、HTTPs优化

### 11.1、性能损耗

产生性能消耗的两个环节：

- 第一个环节， TLS 协议握手过程；
- 第二个环节，握手后的对称加密报文传输。

### 11.2、硬件优化

**HTTPS 协议是计算密集型，而不是 I/O 密集型**，因此可以更换一个性能更好的CPU，因为 HTTPS 连接过程中就有大量需要计算密钥的过程，所以这样可以加速 TLS 握手过程。

另外，如果可以，应该选择可以**支持 AES-NI 特性的 CPU**，因为这种款式的 CPU 能在指令级别优化了 AES 算法，这样便加速了数据的加解密传输过程。

### 11.3、软件优化

* **软件升级**：将正在使用的软件升级到最新版本，因为最新版本不仅提供了最新的特性，也优化了以前软件的问题或性能。
* **协议优化**：如果使用的是 RSA 密钥交换算法，那么需要 4 次握手，也就是要花费 2 RTT，才可以进行应用数据的传输，而且 RSA 密钥交换算法不具备前向安全性。因此使用 **RSA 密钥交换算法的 TLS 握手过程，不仅慢，而且安全性也不高**。尽量**选用 ECDHE 密钥交换**算法替换 RSA 算法，将 **TLS 握手的消息往返由 2 RTT 减少到 1 RTT，而且安全性也高，具备前向安全性**。

### 11.4、TLS升级

如果可以，直接把 TLS 1.2 升级成 TLS 1.3，TLS 1.3 大幅度简化了握手的步骤，**完成 TLS 握手只要 1 RTT**，而且安全性更高。

### 11.5、证书优化

* **证书传输优化**：要让证书更便于传输，那必然是减少证书的大小，这样可以节约带宽，也能减少客户端的运算量。所以，**对于服务器的证书应该选择椭圆曲线（ECDSA）证书，而不是 RSA 证书，因为在相同安全强度下， ECC 密钥长度比 RSA 短的多**。
* **证书验证优化**：
  * **CRL（证书吊销列表）**：由 CA 定期更新，列表内容都是被撤销信任的证书序号，如果服务器的证书在此列表，就认为证书已经失效，不在的话，则认为证书是有效的。
  * **OCSP（在线证书状态协议）**：**向 CA 发送查询请求，让 CA 返回证书的有效状态**。
  * **OCSP Stapling**：服务器向 CA 周期性地查询证书状态，获得一个带有时间戳和签名的响应结果并缓存它。

### 11.6、会话复用

把首次 TLS 握手协商的对称加密密钥缓存起来，待下次需要建立 HTTPS 连接时，直接「复用」这个密钥。

* **Session ID**：**客户端和服务器首次 TLS 握手连接后，双方会在内存缓存会话密钥，并用唯一的 Session ID 来标识**，Session ID 和会话密钥相当于 key-value 的关系。
  * 当客户端再次连接时，hello 消息里会带上 Session ID，服务器收到后就会从内存找，如果找到就直接用该会话密钥恢复会话状态，跳过其余的过程，只用一个消息往返就可以建立安全通信。当然为了安全性，内存中的会话密钥会定期失效。
* **Session Ticket**：**服务器不再缓存每个客户端的会话密钥，而是把缓存的工作交给了客户端**，类似于 HTTP 的 Cookie。
  * 客户端与服务器首次建立连接时，服务器会加密「会话密钥」作为 Ticket 发给客户端，交给客户端缓存该 Ticket。
  * 客户端再次连接服务器时，客户端会发送 Ticket，服务器解密后就可以获取上一次的会话密钥，然后验证有效期，如果没问题，就可以恢复会话了，开始加密通信。

## 12、RPC（远程过程调用）

- 纯裸 TCP 是能收发数据，但它是个**无边界**的数据流，上层需要定义**消息格式**用于定义**消息边界**。于是就有了各种协议，HTTP 和各类 RPC 协议就是在 TCP 之上定义的应用层协议。
- **RPC 本质上不算是协议，而是一种调用方式**，而像 gRPC 和 Thrift 这样的具体实现，才是协议，它们是实现了 RPC 调用的协议。目的是希望程序员能像调用本地方法那样去调用远端的服务方法。同时 RPC 有很多种实现方式，**不一定非得基于 TCP 协议**。
- 从发展历史来说，**HTTP 主要用于 B/S 架构，而 RPC 更多用于 C/S 架构。但现在其实已经没分那么清了，B/S 和 C/S 在慢慢融合**。很多软件同时支持多端，所以对外一般用 HTTP 协议，而内部集群的微服务之间则采用 RPC 协议进行通讯。
- RPC 其实比 HTTP 出现的要早，且比目前主流的 HTTP/1.1 **性能**要更好，所以大部分公司内部都还在使用 RPC。
- **HTTP/2.0** 在 **HTTP/1.1** 的基础上做了优化，性能可能比很多 RPC 协议都要好，但由于是这几年才出来的，所以也不太可能取代掉 RPC。

***HTTP和RPC协议的区别：***

* **服务发现**：首先要向某个服务器发起请求，你得先建立连接，而建立连接的前提是，你得知道 **IP 地址和端口**。服务发现就是服务对应的 IP 端口的过程。
  * 在 **HTTP** 中，你知道服务的域名，就可以通过 **DNS 服务**去解析得到它背后的 IP 地址
  * 而 **RPC** 的话，就有些区别，一般会有专门的**中间服务**去保存服务名和IP信息，比如 **Consul 或者 Etcd，甚至是 Redis**。想要访问某个服务，就去这些中间服务去获得 IP 和端口信息。
* **底层连接形式**：
  * 以主流的 **HTTP/1.1** 协议为例，其默认在建立底层 TCP 连接之后会一直保持这个连接（**Keep Alive**），之后的请求和响应都会复用这条连接。
  *  **RPC** 协议，也跟 HTTP 类似，也是通过建立 TCP 长链接进行数据交互，但不同的地方在于，RPC 协议一般还会再建个**连接池**，在请求量大的时候，建立多条连接放在池内，要发数据的时候就从池里取一条连接出来，**用完放回去，下次再复用**。
* **传输的内容**：
  * 对于主流的 HTTP/1.1，虽然它现在叫**超文本**协议，支持音频视频，但 HTTP 设计初是用于做网页**文本**展示的，所以它传的内容以字符串为主。Header 和 Body 都是如此。在 Body 这块，它使用 **Json** 来**序列化**结构体数据。
  * 而 RPC，因为它定制化程度更高，可以采用体积更小的 Protobuf 或其他序列化协议去保存结构体数据，同时也不需要像 HTTP 那样考虑各种浏览器行为，比如 302 重定向跳转啥的。**因此性能也会更好一些，这也是在公司内部微服务中抛弃 HTTP，选择使用 RPC 的最主要原因。**

## 13、WebSocket

**服务器主动发消息给客户端**

TCP 协议本身是**全双工**的，但我们最常用的 HTTP/1.1，虽然是基于 TCP 的协议，但它是**半双工**的，对于大部分需要服务器主动推送数据到客户端的场景，都不太友好，因此我们需要使用支持全双工的 WebSocket 协议。

### 13.1、建立WebSocket连接

浏览器在 **TCP 三次握手**建立连接之后，都**统一使用 HTTP 协议**先进行一次通信。

- 如果此时是**普通的 HTTP 请求**，那后续双方就还是老样子继续用普通 HTTP 协议进行交互，这点没啥疑问。

- 如果这时候是**想建立 WebSocket 连接**，就会在 HTTP 请求里带上一些**特殊的header 头**。

- 如果服务器正好支持升级成 WebSocket 协议。就会走 WebSocket 握手流程，同时根据客户端生成的 base64 码，用某个**公开的**算法变成另一段字符串，放在 HTTP 响应的 `Sec-WebSocket-Accept` 头里，同时带上`101状态码`，发回给浏览器。

- 之后，浏览器也用同样的**公开算法**将`base64码`转成另一段字符串，如果这段字符串跟服务器传回来的**字符串一致**，那验证通过。

  ![图片](https://cdn.xiaolincoding.com//mysql/other/117eebe06cc6b35ded3216a95706f080.png)

![图片](https://cdn.xiaolincoding.com//mysql/other/f4edd3018914fe6eb38fad6aa3fd2d65.png)

### 13.2、WebSocket的使用场景

WebSocket完美继承了 TCP 协议的**全双工**能力，并且还贴心的提供了解决粘包的方案。

它适用于**需要服务器和客户端（浏览器）频繁交互**的大部分场景，比如网页/小程序游戏，网页聊天室，以及一些类似飞书这样的网页协同办公软件。

## 14、TCP

TCP 是**面向连接的、可靠的、基于字节流**的传输层通信协议。

![img](https://cdn.xiaolincoding.com//mysql/other/format,png-20230309230424714.png)

- **面向连接**：一定是「一对一」才能连接，不能像 UDP 协议可以一个主机同时向多个主机发送消息，也就是一对多是无法做到的；
- **可靠的**：无论的网络链路中出现了怎样的链路变化，TCP 都可以保证一个报文一定能够到达接收端；
- **字节流**：用户消息通过 TCP 协议传输时，消息可能会被操作系统「分组」成多个的 TCP 报文，如果接收方的程序如果不知道「消息的边界」，是无法读出一个有效的用户消息的。并且 TCP 报文是「有序的」，当「前一个」TCP 报文没有收到的时候，即使它先收到了后面的 TCP 报文，那么也不能扔给应用层去处理，同时对「重复」的 TCP 报文会自动丢弃。

### 14.1、TCP连接

![img](https://cdn.xiaolincoding.com//mysql/other/format,png-20230309230428466.png)

建立一个 TCP 连接是需要客户端与服务端达成上述三个信息的共识。

- **Socket**：由 IP 地址和端口号组成
- **序列号**：用来解决乱序问题等
- **窗口大小**：用来做流量控制

### 14.2、唯一确定一个TCP连接

TCP 四元组可以唯一的确定一个连接，四元组包括如下：

- 源地址
- 源端口
- 目的地址
- 目的端口

### 14.3、TCP最大连接数

服务端通常固定在某个本地端口上监听，等待客户端的连接请求。

因此，客户端 IP 和端口是可变的，其理论值计算公式如下:

![img](https://cdn.xiaolincoding.com//mysql/other/format,png-20230309230436594.png)



### 14.4、UDP 和 TCP 的区别

UDP 不提供复杂的控制机制，利用 IP 提供面向「无连接」的通信服务。

**TCP 和 UDP 区别：**

*1. 连接*

- TCP 是面向连接的传输层协议，传输数据前先要建立连接。
- UDP 是不需要连接，即刻传输数据。

*2. 服务对象*

- TCP 是一对一的两点服务，即一条连接只有两个端点。
- UDP 支持一对一、一对多、多对多的交互通信

*3. 可靠性*

- TCP 是可靠交付数据的，数据可以无差错、不丢失、不重复、按序到达。
- UDP 是尽最大努力交付，不保证可靠交付数据。但是我们可以基于 UDP 传输协议实现一个可靠的传输协议，比如 QUIC 协议，具体可以参见这篇文章：[如何基于 UDP 协议实现可靠传输？(opens new window)](https://xiaolincoding.com/network/3_tcp/quic.html)

*4. 拥塞控制、流量控制*

- TCP 有拥塞控制和流量控制机制，保证数据传输的安全性。
- UDP 则没有，即使网络非常拥堵了，也不会影响 UDP 的发送速率。

*5. 首部开销*

- TCP 首部长度较长，会有一定的开销，首部在没有使用「选项」字段时是 `20` 个字节，如果使用了「选项」字段则会变长的。
- UDP 首部只有 8 个字节，并且是固定不变的，开销较小。

*6. 传输方式*

- TCP 是流式传输，没有边界，但保证顺序和可靠。
- UDP 是一个包一个包的发送，是有边界的，但可能会丢包和乱序。

*7. 分片不同*

- TCP 的数据大小如果大于 MSS 大小，则会在传输层进行分片，目标主机收到后，也同样在传输层组装 TCP 数据包，如果中途丢失了一个分片，只需要传输丢失的这个分片。
- UDP 的数据大小如果大于 MTU 大小，则会在 IP 层进行分片，目标主机收到后，在 IP 层组装完数据，接着再传给传输层。

### 14.5、TCP和UDP的应用场景

由于 TCP 是面向连接，能保证数据的可靠性交付，因此经常用于：

- `FTP` 文件传输；
- HTTP / HTTPS；

由于 UDP 面向无连接，它可以随时发送数据，再加上 UDP 本身的处理既简单又高效，因此经常用于：

- 包总量较少的通信，如 `DNS` 、`SNMP` 等；
- 视频、音频等多媒体通信；
- 广播通信；

### 14.6、TCP 三次握手

![image-20240522100605845](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240522100605845.png)

- 一开始，客户端和服务端都处于 `CLOSE` 状态。先是服务端主动监听某个端口，处于 `LISTEN` 状态
- 客户端会随机初始化序号（`client_isn`），将此序号置于 TCP 首部的「序号」字段中，同时把 `SYN` 标志位置为 `1`，表示 `SYN` 报文。接着把第一个 SYN 报文发送给服务端，表示向服务端发起连接，该报文不包含应用层数据，之后客户端处于 `SYN-SENT` 状态。

- 服务端收到客户端的 `SYN` 报文后，首先服务端也随机初始化自己的序号（`server_isn`），将此序号填入 TCP 首部的「序号」字段中，其次把 TCP 首部的「确认应答号」字段填入 `client_isn + 1`, 接着把 `SYN` 和 `ACK` 标志位置为 `1`。最后把该报文发给客户端，该报文也不包含应用层数据，之后服务端处于 `SYN-RCVD` 状态。
- 客户端收到服务端报文后，还要向服务端回应最后一个应答报文，首先该应答报文 TCP 首部 `ACK` 标志位置为 `1` ，其次「确认应答号」字段填入 `server_isn + 1` ，最后把报文发送给服务端，这次报文可以携带客户到服务端的数据，之后客户端处于 `ESTABLISHED` 状态。
- 服务端收到客户端的应答报文后，也进入 `ESTABLISHED` 状态。

### 14.7、为什么是三次握手？不是两次、四次？

- **三次握手才可以阻止重复历史连接的初始化（主要原因）**，在两次握手的情况下，服务端没有中间状态给客户端来阻止历史连接，导致服务端可能建立一个历史连接，造成资源浪费。要解决这种现象，最好就是在服务端发送数据前，也就是建立连接之前，要阻止掉历史连接，这样就不会造成资源浪费，而要实现这个功能，就需要三次握手。

- **三次握手才可以同步双方的初始序列号**，两次握手只保证了一方的初始序列号能被对方成功接收，没办法保证双方的初始序列号都能被确认接收。

  **序列号的作用**：

  * 接收方可以去除重复的数据；
  * 接收方可以根据数据包的序列号按序接收；
  * 可以标识发送出去的数据包中， 哪些是已经被对方收到的（通过 ACK 报文中的序列号知道）；

- **三次握手才可以避免资源浪费**，如果客户端发送的 SYN 报文在网络中阻塞了，重复发送多次 SYN 报文，那么服务端在收到请求后就会**建立多个冗余的无效链接，造成不必要的资源浪费。**

>TCP 建立连接时，通过三次握手**能防止历史连接的建立，能减少双方不必要的资源开销，能帮助双方同步初始化序列号**。序列号能够保证数据包不重复、不丢弃和按序传输。
>
>不使用「两次握手」和「四次握手」的原因：
>
>* 「两次握手」：无法防止历史连接的建立，会造成双方资源的浪费，也无法可靠的同步双方序列号；
>* 「四次握手」：三次握手就已经理论上最少可靠连接建立，所以不需要使用更多的通信次数。

### 14.8、第一次握手丢失，会发生什么

当客户端想和服务端建立 TCP 连接的时候，首先第一个发的就是 SYN 报文，然后进入到 `SYN_SENT` 状态。如果客户端迟迟收不到服务端的 SYN-ACK 报文（第二次握手），就会触发「超时重传」机制，重传 SYN 报文，而且**重传的 SYN 报文的序列号都是一样的**。

在 Linux 里，客户端的 SYN 报文最大重传次数由 `tcp_syn_retries`内核参数控制，这个参数是可以自定义的，默认值一般是 5。**每次超时的时间是上一次的 2 倍**。

### 14.9、第二次握手丢失，会发生什么

当服务端收到客户端的第一次握手后，就会回 SYN-ACK 报文给客户端，这个就是第二次握手，此时服务端会进入 `SYN_RCVD` 状态。

第二次握手的 `SYN-ACK` 报文其实有两个目的 ：

- 第二次握手里的 ACK， 是对第一次握手的确认报文；
- 第二次握手里的 SYN，是服务端发起建立 TCP 连接的报文；

当第二次握手丢失后：

* 因为第二次握手报文里是包含对客户端的第一次握手的 ACK 确认报文，所以，如果客户端迟迟没有收到第二次握手，那么客户端就觉得可能自己的 SYN 报文（第一次握手）丢失了，于是**客户端就会触发超时重传机制，重传 SYN 报文**。
* 由于第二次握手中包含服务端的SYN，当客户端收到后，需要向服务端发送SYN-ACK（第三次握手），如果第二次握手丢失了，服务端就收不到第三次握手，于是**服务端这边会触发超时重传机制，重传 SYN-ACK 报文**。

因此，当第二次握手丢失了，客户端和服务端都会重传：

- 客户端会重传 SYN 报文，也就是第一次握手，最大重传次数由 `tcp_syn_retries`内核参数决定；
- 服务端会重传 SYN-ACK 报文，也就是第二次握手，最大重传次数由 `tcp_synack_retries` 内核参数决定。

### 14.10、第三次握手丢失，会发生什么

客户端收到服务端的 SYN-ACK 报文后，就会给服务端回一个 ACK 报文，也就是第三次握手，此时客户端状态进入到 `ESTABLISH` 状态。

因为这个第三次握手的 ACK 是对第二次握手的 SYN 的确认报文，所以当第三次握手丢失了，如果服务端那一方迟迟收不到这个确认报文，就会触发超时重传机制，重传 SYN-ACK 报文，直到收到第三次握手，或者达到最大重传次数。

### 14.11、TCP 四次挥手

![image-20240522101338387](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240522101338387.png)

- 客户端打算关闭连接，此时会发送一个 TCP 首部 `FIN` 标志位被置为 `1` 的报文，也即 `FIN` 报文，之后客户端进入 `FIN_WAIT_1` 状态。
- 服务端收到该报文后，就向客户端发送 `ACK` 应答报文，接着服务端进入 `CLOSE_WAIT` 状态。
- 客户端收到服务端的 `ACK` 应答报文后，之后进入 `FIN_WAIT_2` 状态。
- 等待服务端处理完数据后，也向客户端发送 `FIN` 报文，之后服务端进入 `LAST_ACK` 状态。
- 客户端收到服务端的 `FIN` 报文后，回一个 `ACK` 应答报文，之后进入 `TIME_WAIT` 状态
- 服务端收到了 `ACK` 应答报文后，就进入了 `CLOSE` 状态，至此服务端已经完成连接的关闭。
- 客户端在经过 `2MSL` 一段时间后，自动进入 `CLOSE` 状态，至此客户端也完成连接的关闭。

### 14.12、为什么挥手需要四次

服务器收到客户端的 FIN 报文时，内核会马上回一个 ACK 应答报文，**但是服务端应用程序可能还有数据要发送，所以并不能马上发送 FIN 报文，而是将发送 FIN 报文的控制权交给服务端应用程序**：

- 如果服务端应用程序有数据要发送的话，就发完数据后，才调用关闭连接的函数；
- 如果服务端应用程序没有数据要发送的话，可以直接调用关闭连接的函数，

从上面过程可知，是否要发送第三次挥手的控制权不在内核，而是在被动关闭方的应用程序，因为应用程序可能还有数据要发送，由应用程序决定什么时候调用关闭连接的函数，当调用了关闭连接的函数，内核就会发送 FIN 报文了，所以服务端的 ACK 和 FIN 一般都会分开发送。

### 14.13、握手丢失，会发生什么

**第一次握手丢失：**

当客户端（主动关闭方）调用 close 函数后，就会向服务端发送 FIN 报文，试图与服务端断开连接，此时客户端的连接进入到 `FIN_WAIT_1` 状态。如果第一次挥手丢失了，那么客户端迟迟收不到被动方的 ACK 的话，也就会触发超时重传机制，重传 FIN 报文，重发次数由 `tcp_orphan_retries` 参数控制。

**第二次握手丢失：**

当服务端收到客户端的第一次挥手后，就会先回一个 ACK 确认报文，此时服务端的连接进入到 `CLOSE_WAIT` 状态。由于ACK 报文是不会重传的，所以如果服务端的第二次挥手丢失了，客户端就会触发超时重传机制，重传 FIN 报文，直到收到服务端的第二次挥手，或者达到最大的重传次数。

**第三次握手丢失：**

当服务端（被动关闭方）收到客户端（主动关闭方）的 FIN 报文后，内核会自动回复 ACK，同时连接处于 `CLOSE_WAIT` 状态，顾名思义，它表示等待应用进程调用 close 函数关闭连接。服务端处于 CLOSE_WAIT 状态时，调用了 close 函数，内核就会发出 FIN 报文，同时连接进入 LAST_ACK 状态，等待客户端返回 ACK 来确认连接关闭。如果迟迟收不到这个 ACK，服务端就会重发 FIN 报文，重发次数仍然由 `tcp_orphan_retrie`s 参数控制，这与客户端重发 FIN 报文的重传次数控制方式是一样的。

**第四次握手丢失：**

当客户端收到服务端的第三次挥手的 FIN 报文后，就会回 ACK 报文，也就是第四次挥手，此时客户端连接进入 `TIME_WAIT` 状态。如果第四次挥手的 ACK 报文没有到达服务端，服务端就会重发 FIN 报文，重发次数仍然由前面介绍过的 `tcp_orphan_retries` 参数控制。

### 14.14、为什么TIME_WAIT是两倍的MSL

* `MSL` 是 Maximum Segment Lifetime，**报文最大生存时间**，它是任何报文在网络上存在的最长时间，超过这个时间报文将被丢弃。
* TTL是 IP 数据报可以经过的最大路由数，每经过一个处理他的路由器此值就减 1，当此值为 0 则数据报将被丢弃，同时发送 ICMP 报文通知源主机。

MSL 与 TTL 的区别： MSL 的单位是时间，而 TTL 是经过路由跳数。所以 **MSL 应该要大于等于 TTL 消耗为 0 的时间**，以确保报文已被自然消亡。

**TTL 的值一般是 64，Linux 将 MSL 设置为 30 秒，意味着 Linux 认为数据报文经过 64 个路由器的时间不会超过 30 秒，如果超过了，就认为报文已经消失在网络中了**。

网络中可能存在来自发送方的数据包，当这些发送方的数据包被接收方处理后又会向对方发送响应，所以**一来一回需要等待 2 倍的时间**。可以看到 **2MSL时长** 这其实是相当于**至少允许报文丢失一次**。

### 14.15、为什么需要TIME_WAIT状态

主动发起关闭连接的一方，才会有 `TIME-WAIT` 状态。

需要 TIME-WAIT 状态，主要是两个原因：

- 防止历史连接中的数据，被后面相同四元组的连接错误的接收；
- 保证「被动关闭连接」的一方，能被正确的关闭；

## 15、如果已经建立了连接，但是客户端突然出现故障了怎么办？

客户端出现故障指的是客户端的主机发生了宕机，或者断电的场景。发生这种情况的时候，如果服务端一直不会发送数据给客户端，那么服务端是永远无法感知到客户端宕机这个事件的，也就是服务端的 TCP 连接将一直处于 `ESTABLISH` 状态，占用着系统资源。

为了避免这种情况，TCP 搞了个**保活机制**：

* 定义一个时间段，在这个时间段内，如果没有任何连接相关的活动，TCP 保活机制会开始作用，每隔一个时间间隔，发送一个探测报文，该探测报文包含的数据非常少，如果连续几个探测报文都没有得到响应，则认为当前的 TCP 连接已经死亡，系统内核将错误信息通知给上层应用程序。

TCP 保活的这个机制检测的时间是有点长，我们可以自己在应用层实现一个心跳机制。

比如，web 服务软件一般都会提供 `keepalive_timeout` 参数，用来指定 HTTP 长连接的超时时间。如果设置了 HTTP 长连接的超时时间是 60 秒，web 服务软件就会**启动一个定时器**，如果客户端在完成一个 HTTP 请求后，在 60 秒内都没有再发起新的请求，**定时器的时间一到，就会触发回调函数来释放该连接。**

## 16、如果已经建立了连接，但是服务端的进程崩溃会发生什么？

TCP 的连接信息是由内核维护的，所以当服务端的进程崩溃后，内核需要回收该进程的所有 TCP 连接资源，于是内核会发送第一次挥手 FIN 报文，后续的挥手过程也都是在内核完成，并不需要进程的参与，所以即使服务端的进程退出了，还是能与客户端完成 TCP 四次挥手的过程。

## 17、Socket

![基于 TCP 协议的客户端和服务端工作](https://cdn.xiaolincoding.com//mysql/other/format,png-20230309230545997.png)

- 服务端和客户端初始化 `socket`，得到文件描述符；
- 服务端调用 `bind`，将 socket 绑定在指定的 IP 地址和端口;
- 服务端调用 `listen`，进行监听；
- 服务端调用 `accept`，等待客户端连接；
- 客户端调用 `connect`，向服务端的地址和端口发起连接请求；
- 服务端 `accept` 返回用于传输的 `socket` 的文件描述符；
- 客户端调用 `write` 写入数据；服务端调用 `read` 读取数据；
- 客户端断开连接时，会调用 `close`，那么服务端 `read` 读取数据的时候，就会读取到了 `EOF`，待处理完数据后，服务端调用 `close`，表示连接关闭。

这里需要注意的是，服务端调用 `accept` 时，连接成功了会返回一个已完成连接的 socket，后续用来传输数据。

所以，监听的 socket 和真正用来传送数据的 socket，是「两个」 socket，一个叫作**监听 socket**，一个叫作**已完成连接 socket**。

成功连接建立之后，双方开始通过 read 和 write 函数来读写数据，就像往一个文件流里面写东西一样。

### 17.1、accept 发生在三次握手的哪一步

- 客户端的协议栈向服务端发送了 SYN 包，并告诉服务端当前发送序列号 client_isn，客户端进入 SYN_SENT 状态；
- 服务端的协议栈收到这个包之后，和客户端进行 ACK 应答，应答的值为 client_isn+1，表示对 SYN 包 client_isn 的确认，同时服务端也发送一个 SYN 包，告诉客户端当前我的发送序列号为 server_isn，服务端进入 SYN_RCVD 状态；
- 客户端协议栈收到 ACK 之后，使得应用程序从 `connect` 调用返回，表示客户端到服务端的单向连接建立成功，客户端的状态为 ESTABLISHED，同时客户端协议栈也会对服务端的 SYN 包进行应答，应答数据为 server_isn+1；
- ACK 应答包到达服务端后，服务端的 TCP 连接进入 ESTABLISHED 状态，同时服务端协议栈使得 `accept` 阻塞调用返回，这个时候服务端到客户端的单向连接也建立成功。至此，客户端与服务端两个方向的连接都建立成功。

从上面的描述过程，我们可以得知**客户端 connect 成功返回是在第二次握手，服务端 accept 成功返回是在三次握手成功之后。**

### 17.2、客户端调用 close 了，连接是断开的流程是什么

![客户端调用 close 过程](https://cdn.xiaolincoding.com//mysql/other/format,png-20230309230538308.png)

- 客户端调用 `close`，表明客户端没有数据需要发送了，则此时会向服务端发送 FIN 报文，进入 FIN_WAIT_1 状态；
- 服务端接收到了 FIN 报文，TCP 协议栈会为 FIN 包插入一个文件结束符 `EOF` 到接收缓冲区中，应用程序可以通过 `read` 调用来感知这个 FIN 包。这个 `EOF` 会被**放在已排队等候的其他已接收的数据之后**，这就意味着服务端需要处理这种异常情况，因为 EOF 表示在该连接上再无额外数据到达。此时，服务端进入 CLOSE_WAIT 状态；
- 接着，当处理完数据后，自然就会读到 `EOF`，于是也调用 `close` 关闭它的套接字，这会使得服务端发出一个 FIN 包，之后处于 LAST_ACK 状态；
- 客户端接收到服务端的 FIN 包，并发送 ACK 确认包给服务端，此时客户端将进入 TIME_WAIT 状态；
- 服务端收到 ACK 确认包后，就进入了最后的 CLOSE 状态；
- 客户端经过 `2MSL` 时间之后，也进入 CLOSE 状态；

## 18、TCP重传机制

TCP 针对数据包丢失的情况，会用**重传机制**解决。

常见的重传机制：

- 超时重传
- 快速重传
- SACK
- D-SACK

### 18.1、超时重传

重传机制的其中一个方式，就是在发送数据时，设定一个定时器，当超过指定的时间后，没有收到对方的 `ACK` 确认应答报文，就会重发该数据，也就是我们常说的**超时重传**。

TCP 会在以下两种情况发生超时重传：

- 数据包丢失
- 确认应答丢失

![超时重传的两种情况](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/5.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

### 18.2、快速重传

**快速重传（Fast Retransmit）机制**，它**不以时间为驱动，而是以数据驱动重传**。

![快速重传机制](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/10.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

在上图，发送方发出了 1，2，3，4，5 份数据：

- 第一份 Seq1 先送到了，于是就 Ack 回 2；
- 结果 Seq2 因为某些原因没收到，Seq3 到达了，于是还是 Ack 回 2；
- 后面的 Seq4 和 Seq5 都到了，但还是 Ack 回 2，因为 Seq2 还是没有收到；
- **发送端收到了三个 Ack = 2 的确认，知道了 Seq2 还没有收到，就会在定时器过期之前，重传丢失的 Seq2。**
- 最后，收到了 Seq2，此时因为 Seq3，Seq4，Seq5 都收到了，于是 Ack 回 6 。

所以，***快速重传的工作方式是当收到三个相同的 ACK 报文时，会在定时器过期之前，重传丢失的报文段***。

但是当出现多个数据发生丢失时，快速重传将不知道是重传一个还是重传所有的数据。

### 18.3、SACK方法

`SACK`（ Selective Acknowledgment）， **选择性确认**。

这种方式需要在 TCP 头部「选项」字段里加一个 `SACK` 的东西，它**可以将已收到的数据的信息发送给「发送方」**，这样发送方就可以知道哪些数据收到了，哪些数据没收到，知道了这些信息，就可以**只重传丢失的数据**。

![选择性确认](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/11.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

### 18.、Duplicate SACK

Duplicate SACK 又称 `D-SACK`，其主要**使用了 SACK 来告诉「发送方」有哪些数据被重复接收了。**

## 19、滑动窗口（流量控制）

为每个数据包确认应答的缺点：数据包的**往返时间越长，通信的效率就越低**。

为解决这个问题，TCP 引入了**窗口**这个概念。即使在往返时间较长的情况下，它也不会降低网络通信的效率。窗口大小就是指**无需等待确认应答，而可以继续发送数据的最大值**。

![用滑动窗口方式并行处理](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/15.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

***通常窗口的大小是由接收方的窗口大小来决定***，TCP 头里有一个字段叫 `Window`，也就是窗口大小。**这个字段是接收端告诉发送端自己还有多少缓冲区可以接收数据。于是发送端就可以根据这个接收端的处理能力来发送数据，而不会导致接收端处理不过来。**

### 19.1、发送方的滑动窗口

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/16.jpg?)

- \#1 是已发送并收到 ACK确认的数据：1~31 字节
- \#2 是已发送但未收到 ACK确认的数据：32~45 字节
- \#3 是未发送但总大小在接收方处理范围内（接收方还有空间）：46~51字节
- \#4 是未发送但总大小超过接收方处理范围（接收方没有空间）：52字节以后

在下图，当发送方把数据「全部」都一下发送出去后，可用窗口的大小就为 0 了，表明可用窗口耗尽，在没收到 ACK 确认之前是无法继续发送数据了。

![可用窗口耗尽](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/17.jpg?)

在下图，当收到之前发送的数据 `32~36` 字节的 ACK 确认应答后，如果发送窗口的大小没有变化，则**滑动窗口往右边移动 5 个字节，因为有 5 个字节的数据被应答确认**，接下来 `52~56` 字节又变成了可用窗口，那么后续也就可以发送 `52~56` 这 5 个字节的数据了。

![32 ~ 36 字节已确认](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/18.jpg)

### 19.2、接收方的滑动窗口

- \#1 + #2 是已成功接收并确认的数据（等待应用进程读取）；
- \#3 是未收到数据但可以接收的数据；
- \#4 未收到数据并不可以接收的数据；

![接收窗口](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/20.jpg)

其中三个接收部分，使用两个指针进行划分:

- `RCV.WND`：表示接收窗口的大小，它会通告给发送方。
- `RCV.NXT`：是一个指针，它指向期望从发送方发送来的下一个数据字节的序列号，也就是 #3 的第一个字节。
- 指向 #4 的第一个字节是个相对指针，它需要 `RCV.NXT` 指针加上 `RCV.WND` 大小的偏移量，就可以指向 #4 的第一个字节了。

### 19.3、接收窗口和发送窗口的大小

接收窗口和发送窗口的大小并不是完全相等，接收窗口的大小是**约等于**发送窗口的大小的。

因为滑动窗口并不是一成不变的。比如，当接收方的应用进程读取数据的速度非常快的话，这样的话接收窗口可以很快的就空缺出来。那么新的接收窗口大小，是通过 TCP 报文中的 Windows 字段来告诉发送方。那么这个传输过程是存在时延的，所以接收窗口和发送窗口是约等于的关系。

## 20、拥塞控制

**拥塞控制**，控制的目的就是**避免「发送方」的数据填满整个网络。**

拥塞控制主要是四个算法：

- 慢启动
- 拥塞避免
- 拥塞发生
- 快速恢复

### 20.1、慢启动

慢启动的意思就是一点一点的提高发送数据包的数量，**当发送方每收到一个 ACK，拥塞窗口 cwnd 的大小就会加 1。**

![慢启动算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/27.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

慢启动算法，发包的个数是**指数性的增长**。

有一个叫慢启动门限 `ssthresh` （slow start threshold）状态变量。

- 当 `cwnd` < `ssthresh` 时，使用慢启动算法。
- 当 `cwnd` >= `ssthresh` 时，就会使用「拥塞避免算法」。

### 20.2、拥塞避免

**每当收到一个 ACK 时，cwnd 增加 1/cwnd。**

![拥塞避免](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/28.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

拥塞避免算法就是将原本慢启动算法的指数增长变成了线性增长，还是增长阶段，但是增长速度缓慢了一些。

就这么一直增长着后，网络就会慢慢进入了拥塞的状况了，于是就会出现丢包现象，这时就需要对丢失的数据包进行重传。

当触发了重传机制，也就进入了「拥塞发生算法」。

### 20.3、拥塞发生

当网络出现拥塞，也就是会发生数据包重传，重传机制主要有两种：

- 超时重传
- 快速重传

![拥塞发送 —— 超时重传](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/TCP-%E5%8F%AF%E9%9D%A0%E7%89%B9%E6%80%A7/29.jpg?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

当发生了「超时重传」，则就会使用拥塞发生算法。

这个时候，ssthresh 和 cwnd 的值会发生变化：

- `ssthresh` 设为 `cwnd/2`，
- `cwnd` 重置为 `1` （是恢复为 cwnd 初始化值，我这里假定 cwnd 初始化值 1）

### 20.4、快速恢复

进入快速恢复之前，`cwnd` 和 `ssthresh` 已被更新了：

- `cwnd = cwnd/2` ，也就是设置为原来的一半;
- `ssthresh = cwnd`;

然后，进入快速恢复算法如下：

- 拥塞窗口 `cwnd = ssthresh + 3` （ 3 的意思是确认有 3 个数据包被收到了）；
- 重传丢失的数据包；
- 如果再收到重复的 ACK，那么 cwnd 增加 1；
- 如果收到新数据的 ACK 后，把 cwnd 设置为第一步中的 ssthresh 的值，原因是该 ACK 确认了新的数据，说明从 duplicated ACK 时的数据都已收到，该恢复过程已经结束，可以回到恢复之前的状态了，也即再次进入拥塞避免状态；

![快速重传和快速恢复](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E7%BD%91%E7%BB%9C/%E6%8B%A5%E5%A1%9E%E5%8F%91%E7%94%9F-%E5%BF%AB%E9%80%9F%E9%87%8D%E4%BC%A0.drawio.png?image_process=watermark,text_5YWs5LyX5Y-377ya5bCP5p6XY29kaW5n,type_ZnpsdHpoaw,x_10,y_10,g_se,size_20,color_0000CD,t_70,fill_0)

## 21、HTTP协议状态码 500 501 502 503 504分别代表什么

状态码500：

- 服务器内部错误（Internal Server Error）：表示服务器在处理请求时遇到了意外的错误，无法完成请求。
- 场景：当服务器上的应用程序发生未处理的异常或错误时，可能会返回500状态码。例如，如果网站的后端代码出现了错误，导致无法正确处理请求，服务器可能会返回500状态码。

状态码501：

- 未实现（Not Implemented）：表示服务器不支持客户端请求的功能或方法。
- 场景：当客户端发送了一个服务器不支持的请求方法或功能时，服务器可以返回501状态码。例如，如果客户端发送了一个不被服务器支持的HTTP方法，如PROPFIND，服务器可能会返回501状态码。

状态码502：

- 错误网关（Bad Gateway）：表示服务器作为网关或代理，从上游服务器接收到的响应无效。
- 场景：当服务器作为网关或代理时，如果服务器从上游服务器接收到的响应无效，可能会返回502状态码。例如，当反向代理服务器无法访问后端服务器或后端服务器返回了无效的响应时，可能会返回502状态码。

状态码503 ：

- 服务不可用（Service Unavailable）：表示服务器暂时无法处理请求，通常是由于服务器过载或维护。
- 场景：当服务器暂时无法处理请求时，可能会返回503状态码。例如，当网站正在进行维护或升级时，服务器可以返回503状态码来告知客户端服务不可用。

状态码504 ：

- 网关超时（Gateway Timeout）：表示服务器作为网关或代理，在等待上游服务器的响应时超时。
- 场景：当服务器作为网关或代理时，在等待上游服务器的响应时超时，可能会返回504状态码。例如，如果反向代理服务器在规定的超时时间内无法从后端服务器获取响应，可能会返回504状态码。

# 十五、操作系统

## 1、内存管理

### 1.1、虚拟内存

![进程的中间层](https://cdn.xiaolincoding.com//mysql/other/298fb68e3da94d767b02f2ed81ebf2c4.png)

**操作系统会提供一种机制，将不同进程的虚拟地址和不同内存的物理地址映射起来。**

如果程序要访问虚拟地址的时候，由操作系统转换成不同的物理地址，这样不同的进程运行的时候，写入的是不同的物理地址，这样就不会冲突了。

- 我们程序所使用的内存地址叫做**虚拟内存地址**（*Virtual Memory Address*）
- 实际存在硬件里面的空间地址叫**物理内存地址**（*Physical Memory Address*）。

操作系统引入了虚拟内存，进程持有的虚拟地址会通过 CPU 芯片中的内存管理单元（MMU）的映射关系，来转换变成物理地址，然后再通过物理地址访问内存，如下图所示：

![img](https://cdn.xiaolincoding.com//mysql/other/72ab76ba697e470b8ceb14d5fc5688d9.png)

操作系统如何管理虚拟内存和物理内存：

* 内存分段
* 内存分页

### 1.2、内存分段

程序是由若干个逻辑分段组成的，如可由代码分段、数据分段、栈段、堆段组成。**不同的段是有不同的属性的，所以就用分段（\*Segmentation\*）的形式把这些段分离出来。**

分段机制下的虚拟地址由两部分组成，**段选择因子**和**段内偏移量**。

![img](https://cdn.xiaolincoding.com//mysql/other/a9ed979e2ed8414f9828767592aadc21.png)

段选择因子和段内偏移量：

- **段选择子**就保存在段寄存器里面。段选择子里面最重要的是**段号**，用作段表的索引。**段表**里面保存的是这个**段的基地址、段的界限和特权等级**等。
- 虚拟地址中的**段内偏移量**应该位于 0 和段界限之间，如果段内偏移量是合法的，就将段基地址加上段内偏移量得到物理内存地址。

在上面，知道了虚拟地址是通过**段表**与物理地址进行映射的，分段机制会把程序的虚拟地址分成 4 个段，每个段在段表中有一个项，在这一项找到段的基地址，再加上偏移量，于是就能找到物理内存中的地址，如下图：

![img](https://cdn.xiaolincoding.com//mysql/other/c5e2ab63e6ee4c8db575f3c7c9c85962.png)

分段的办法很好，解决了程序本身不需要关心具体的物理内存地址的问题，但它也有一些不足之处：

- 第一个就是**内存碎片**的问题。
- 第二个就是**内存交换的效率低**的问题。

#### 1.2.1、内存碎片

内存碎片主要分为，内部内存碎片和外部内存碎片。

内存分段管理可以做到段根据实际需求分配内存，所以有多少需求就分配多大的段，所以**不会出现内部内存碎片**。

但是由于每个段的长度不固定，所以多个段未必能恰好使用所有的内存空间，会产生了多个不连续的小物理内存，导致新的程序无法被装载，所以**会出现外部内存碎片**的问题。

解决「外部内存碎片」的问题就是**内存交换**。

#### 1.2.2、内存交换的效率低

对于多进程的系统来说，用分段的方式，外部内存碎片是很容易产生的，产生了外部内存碎片，那不得不重新 `Swap` 内存区域，这个过程会产生性能瓶颈。

因为硬盘的访问速度要比内存慢太多了，每一次内存交换，我们都需要把一大段连续的内存数据写到硬盘上。

所以，**如果内存交换的时候，交换的是一个占内存空间很大的程序，这样整个机器都会显得卡顿。**

为了解决内存分段的「外部内存碎片和内存交换效率低」的问题，就出现了内存分页。

### 1.3、内存分页

**分页是把整个虚拟和物理内存空间切成一段段固定尺寸的大小**。这样一个连续并且尺寸固定的内存空间，我们叫**页**（*Page*）。在 Linux 下，每一页的大小为 `4KB`。

虚拟地址与物理地址之间通过**页表**来映射，如下图：

![img](https://cdn.xiaolincoding.com//mysql/other/08a8e315fedc4a858060db5cb4a654af.png)

页表是存储在内存里的，**内存管理单元** （*MMU*）就做将虚拟内存地址转换成物理地址的工作。

**采用了分页，页与页之间是紧密排列的，所以不会有外部碎片。**

但是，因为内存分页机制分配内存的最小单位是一页，即使程序不足一页大小，我们最少只能分配一个页，所以页内会出现内存浪费，所以针对**内存分页机制会有内部内存碎片**的现象。

如果内存空间不够，操作系统会把其他正在运行的进程中的「最近没被使用」的内存页面给释放掉，也就是暂时写在硬盘上，称为**换出**（*Swap Out*）。一旦需要的时候，再加载进来，称为**换入**（*Swap In*）。所以，一次性写入磁盘的也只有少数的一个页或者几个页，不会花太多时间，**内存交换的效率就相对比较高。**

![img](https://cdn.xiaolincoding.com//mysql/other/388a29f45fe947e5a49240e4eff13538-20230309234651917.png)

在分页机制下，虚拟地址分为两部分，**页号**和**页内偏移**。页号作为页表的索引，**页表**包含物理页每页所在**物理内存的基地址**，这个基地址与页内偏移的组合就形成了物理内存地址，见下图。

![img](https://cdn.xiaolincoding.com//mysql/other/7884f4d8db4949f7a5bb4bbd0f452609.png)

对于一个内存地址转换，其实就是这样三个步骤：

- 把虚拟内存地址，切分成页号和偏移量；
- 根据页号，从页表里面，查询对应的物理页号；
- 直接拿物理页号，加上前面的偏移量，就得到了物理内存地址。

#### 1.3.1、多级页表

对于单页表的实现方式，在 32 位和页大小 `4KB` 的环境下，一个进程的页表需要装下 100 多万个「页表项」，并且每个页表项是占用 4 字节大小的，于是相当于每个页表需占用 4MB 大小的空间。

我们把这个 100 多万个「页表项」的单级页表再分页，将页表（一级页表）分为 `1024` 个页表（二级页表），每个表（二级页表）中包含 `1024` 个「页表项」，形成**二级分页**。如下图所示：

![img](https://cdn.xiaolincoding.com//mysql/other/19296e249b2240c29f9c52be70f611d5.png)

我们把二级分页再推广到多级页表，就会发现页表占用的内存空间更少了，这一切都要归功于对局部性原理的充分应用。

对于 64 位的系统，两级分页肯定不够了，就变成了四级目录，分别是：

- 全局页目录项 PGD（*Page Global Directory*）；
- 上层页目录项 PUD（*Page Upper Directory*）；
- 中间页目录项 PMD（*Page Middle Directory*）；
- 页表项 PTE（*Page Table Entry*）；

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E5%86%85%E5%AD%98%E7%AE%A1%E7%90%86/%E5%9B%9B%E7%BA%A7%E5%88%86%E9%A1%B5.png)

#### 1.3.2、TLAB

多级页表虽然解决了空间上的问题，但是虚拟地址到物理地址的转换就多了几道转换的工序，这显然就降低了这俩地址转换的速度，也就是带来了时间上的开销。

程序是有局部性的，即在一段时间内，整个程序的执行仅限于程序中的某一部分。相应地，执行所访问的存储空间也局限于某个内存区域。

我们就可以利用这一特性，把最常访问的几个页表项存储到访问速度更快的硬件，于是计算机科学家们，就在 CPU 芯片中，加入了一个专门存放程序最常访问的页表项的 Cache，这个 Cache 就是 TLB（*Translation Lookaside Buffer*） ，通常称为页表缓存、转址旁路缓存、快表等。

![img](https://cdn.xiaolincoding.com//mysql/other/a3cdf27646b24614a64cfc5d7ccffa35.png)

有了 TLB 后，那么 CPU 在寻址时，会先查 TLB，如果没找到，才会继续查常规的页表。

### 1.4、段页式内存管理

内存分段和内存分页并不是对立的，它们是可以组合起来在同一个系统中使用的，那么组合起来后，通常称为**段页式内存管理**。

![img](https://cdn.xiaolincoding.com//mysql/other/f19ebd6f70f84083b0d87cc5e9dea8e3.png)

段页式内存管理实现的方式：

- 先将程序划分为多个有逻辑意义的段，也就是前面提到的分段机制；
- 接着再把每个段划分为多个页，也就是对分段划分出来的连续空间，再划分固定大小的页；

这样，地址结构就由**段号、段内页号和页内位移**三部分组成。

用于段页式地址变换的数据结构是每一个程序一张段表，每个段又建立一张页表，段表中的地址是页表的起始地址，而页表中的地址则为某页的物理页号，如图所示：

![img](https://cdn.xiaolincoding.com//mysql/other/8904fb89ae0c49c4b0f2f7b5a0a7b099.png)

段页式地址变换中要得到物理地址须经过三次内存访问：

- 第一次访问段表，得到页表起始地址；
- 第二次访问页表，得到物理页号；
- 第三次将物理页号与页内位移组合，得到物理地址。

>为了在多进程环境下，使得进程之间的内存地址不受影响，相互隔离，于是操作系统就为每个进程独立分配一套**虚拟地址空间**，每个程序只关心自己的虚拟地址就可以，实际上大家的虚拟地址都是一样的，但分布到物理地址内存是不一样的。作为程序，也不用关心物理地址的事情。
>
>每个进程都有自己的虚拟空间，而物理内存只有一个，所以当启用了大量的进程，物理内存必然会很紧张，于是操作系统会通过**内存交换**技术，把不常使用的内存暂时存放到硬盘（换出），在需要的时候再装载回物理内存（换入）。
>
>那既然有了虚拟地址空间，那必然要把虚拟地址「映射」到物理地址，这个事情通常由操作系统来维护。
>
>那么对于虚拟地址与物理地址的映射关系，可以有**分段**和**分页**的方式，同时两者结合都是可以的。
>
>内存分段是根据程序的逻辑角度，分成了栈段、堆段、数据段、代码段等，这样可以分离出不同属性的段，同时是一块连续的空间。但是每个段的大小都不是统一的，这就会导致外部内存碎片和内存交换效率低的问题。
>
>于是，就出现了内存分页，把虚拟空间和物理空间分成大小固定的页，如在 Linux 系统中，每一页的大小为 `4KB`。由于分了页后，就不会产生细小的内存碎片，解决了内存分段的外部内存碎片问题。同时在内存交换的时候，写入硬盘也就一个页或几个页，这就大大提高了内存交换的效率。
>
>再来，为了解决简单分页产生的页表过大的问题，就有了**多级页表**，它解决了空间上的问题，但这就会导致 CPU 在寻址的过程中，需要有很多层表参与，加大了时间上的开销。于是根据程序的**局部性原理**，在 CPU 芯片中加入了 **TLB**，负责缓存最近常被访问的页表项，大大提高了地址的转换速度。
>
>**Linux 系统主要采用了分页管理，但是由于 Intel 处理器的发展史，Linux 系统无法避免分段管理**。于是 Linux 就把所有段的基地址设为 `0`，也就意味着所有程序的地址空间都是线性地址空间（虚拟地址），相当于屏蔽了 CPU 逻辑地址的概念，所以段只被用于访问控制和内存保护。
>
>另外，Linux 系统中虚拟空间分布可分为**用户态**和**内核态**两部分，其中用户态的分布：代码段、全局变量、BSS、函数栈、堆内存、映射区。

### 1.5、虚拟内存的作用

- 第一，虚拟内存可以使得进程对运行内存超过物理内存大小，因为程序运行符合局部性原理，CPU 访问内存会有很明显的重复访问的倾向性，对于那些没有被经常使用到的内存，我们可以把它换出到物理内存之外，比如硬盘上的 swap 区域。
- 第二，由于每个进程都有自己的页表，所以每个进程的虚拟内存空间就是相互独立的。进程也没有办法访问其他进程的页表，所以这些页表是私有的，这就解决了多进程之间地址冲突的问题。
- 第三，页表里的页表项中除了物理地址之外，还有一些标记属性的比特，比如控制一个页的读写权限，标记该页是否存在等。在内存访问方面，操作系统提供了更好的安全性。

### 1.6、内存紧张时，会发生什么

应用程序通过 malloc 函数申请内存的时候，实际上申请的是虚拟内存，此时并不会分配物理内存。

当应用程序读写了这块虚拟内存，CPU 就会去访问这个虚拟内存， 这时会发现这个虚拟内存没有映射到物理内存， CPU 就会产生**缺页中断**，进程会从用户态切换到内核态，并将缺页中断交给内核的 Page Fault Handler （缺页中断函数）处理。

缺页中断处理函数会看是否有空闲的物理内存，如果有，就直接分配物理内存，并建立虚拟内存与物理内存之间的映射关系。

如果没有空闲的物理内存，那么内核就会开始进行**回收内存**的工作，回收的方式主要是两种：直接内存回收和后台内存回收。

- **后台内存回收**（kswapd）：在物理内存紧张的时候，会唤醒 kswapd 内核线程来回收内存，这个回收内存的过程**异步**的，不会阻塞进程的执行。
- **直接内存回收**（direct reclaim）：如果后台异步回收跟不上进程内存申请的速度，就会开始直接回收，这个回收内存的过程是**同步**的，会阻塞进程的执行。

如果直接内存回收后，空闲的物理内存仍然无法满足此次物理内存的申请，那么内核就会放最后的大招了 ——**触发 OOM （Out of Memory）机制**。

![img](https://cdn.xiaolincoding.com//mysql/other/2f61b0822b3c4a359f99770231981b07.png)



### 1.7、在 4GB 物理内存的机器上，申请 8G 内存会怎么样？

当申请内存时，如果发生内存紧张会执行如1.6的操作。

在32位和64位的操作系统中：

* 在 32 位操作系统，因为进程理论上最大能申请 3 GB 大小的虚拟内存，所以直接申请 8G 内存，会申请失败。
* 在 64位 位操作系统，因为进程理论上最大能申请 128 TB 大小的虚拟内存，即使物理内存只有 4GB，申请 8G 内存也是没问题，因为申请的内存是虚拟内存。如果这块虚拟内存被访问了，要看系统有没有 Swap 分区：
  - 如果没有 Swap 分区，因为物理空间不够，进程会被操作系统杀掉，原因是 OOM（内存溢出）；
  - 如果有 Swap 分区，即使物理内存只有 4GB，程序也能正常使用 8GB 的内存，进程可以正常运行；

### 1.8、Swap机制

当系统的物理内存不够用的时候，就需要将物理内存中的一部分空间释放出来，以供当前运行的程序使用。那些被释放的空间可能来自一些很长时间没有什么操作的程序，这些被释放的空间会被临时保存到磁盘，等到那些程序要运行时，再从磁盘中恢复保存的数据到内存中。

另外，当内存使用存在压力的时候，会开始触发内存回收行为，会把这些不常访问的内存先写到磁盘中，然后释放这些内存，给其他更需要的进程使用。再次访问这些内存时，重新从磁盘读入内存就可以了。

这种，将内存数据换出磁盘，又从磁盘中恢复数据到内存的过程，就是 Swap 机制负责的。

Swap 就是把一块磁盘空间或者本地文件，当成内存来使用，它包含换出和换入两个过程：

- **换出（Swap Out）** ，是把进程暂时不用的内存数据存储到磁盘中，并释放这些数据占用的内存；
- **换入（Swap In）**，是在进程再次访问这些内存的时候，把它们从磁盘读到内存中来；

![img](https://cdn.xiaolincoding.com//mysql/other/388a29f45fe947e5a49240e4eff13538.png)

> 使用 Swap 机制优点是，应用程序实际可以使用的内存空间将远远超过系统的物理内存。由于硬盘空间的价格远比内存要低，因此这种方式无疑是经济实惠的。当然，频繁地读写硬盘，会显著降低操作系统的运行速率，这也是 Swap 的弊端。

Linux 中的 Swap 机制会在内存不足和内存闲置的场景下触发：

- **内存不足**：当系统需要的内存超过了可用的物理内存时，内核会将内存中不常使用的内存页交换到磁盘上为当前进程让出内存，保证正在执行的进程的可用性，这个内存回收的过程是强制的直接内存回收（Direct Page Reclaim）。直接内存回收是同步的过程，会阻塞当前申请内存的进程。
- **内存闲置**：应用程序在启动阶段使用的大量内存在启动后往往都不会使用，通过后台运行的守护进程（kSwapd），我们可以将这部分只使用一次的内存交换到磁盘上为其他内存的申请预留空间。kSwapd 是 Linux 负责页面置换（Page replacement）的守护进程，它也是负责交换闲置内存的主要进程，它会在[空闲内存低于一定水位 (opens new window)](https://xiaolincoding.com/os/3_memory/mem_reclaim.html#尽早触发-kSwapd-内核线程异步回收内存)时，回收内存页中的空闲内存保证系统中的其他进程可以尽快获得申请的内存。kSwapd 是后台进程，所以回收内存的过程是异步的，不会阻塞当前申请内存的进程。

### 1.9、预读失效和缓存污染

>* 操作系统在读磁盘的时候会额外多读一些到内存中，但是最后这些数据也没用到，针对这一问题的改进。
>  * **「预读失效」导致缓存命中率下降**
>* 批量读取数据时，可能会把热点数据挤出去，针对该问题的改进
>  * **「缓存污染」导致缓存命中率下降**

* Redis 的缓存淘汰算法则是通过**实现 LFU 算法**来避免「缓存污染」而导致缓存命中率下降的问题（Redis 没有预读机制）。

* MySQL 和 Linux 操作系统是通过**改进 LRU 算法**来避免「预读失效和缓存污染」而导致缓存命中率下降的问题。

#### 1.9.1、Linux的缓存

在应用程序读取文件的数据的时候，Linux 操作系统是会对读取的文件数据进行缓存的，会缓存在文件系统中的 **Page Cache**（如下图中的页缓存）。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E6%96%87%E4%BB%B6%E7%B3%BB%E7%BB%9F/%E8%99%9A%E6%8B%9F%E6%96%87%E4%BB%B6%E7%B3%BB%E7%BB%9F.png)

Page Cache 属于内存空间里的数据，由于内存访问比磁盘访问快很多，在下一次访问相同的数据就不需要通过磁盘 I/O 了，命中缓存就直接返回数据即可。

#### 1.9.2、MySQL的缓存

MySQL 的数据是存储在磁盘里的，为了提升数据库的读写性能，Innodb 存储引擎设计了一个**缓冲池**（Buffer Pool），Buffer Pool 属于内存空间里的数据。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/mysql/innodb/%E7%BC%93%E5%86%B2%E6%B1%A0.drawio.png)

有了缓冲池后：

- 当读取数据时，如果数据存在于 Buffer Pool 中，客户端就会直接读取 Buffer Pool 中的数据，否则再去磁盘中读取。
- 当修改数据时，首先是修改 Buffer Pool 中数据所在的页，然后将其页设置为脏页，最后由后台线程将脏页写入到磁盘。

#### 1.9.3、传统的管理内存数据的LUR算法

LRU 算法一般是用「链表」作为数据结构来实现的，链表头部的数据是最近使用的，而链表末尾的数据是最久没被使用的。那么，当空间不够了，就淘汰最久没被使用的节点，也就是链表末尾的数据，从而腾出内存空间。

> 因为 Linux 的 Page Cache 和 MySQL 的 Buffer Pool 缓存的**基本数据单位都是页（Page）单位**，所以**后续以「页」名称代替「数据」**。

- 当访问的页在内存里，就直接把该页对应的 LRU 链表节点移动到链表的头部。
- 当访问的页不在内存里，除了要把该页放入到 LRU 链表的头部，还要淘汰 LRU 链表末尾的页。

传统的 LRU 算法并没有被 Linux 和 MySQL 使用，因为传统的 LRU 算法无法避免下面这两个问题：

- 预读失效导致缓存命中率下降；
- 缓存污染导致缓存命中率下降；

#### 1.9.4、预读机制

- 应用程序只想读取磁盘上文件 A 的 offset 为 0-3KB 范围内的数据，由于磁盘的基本读写单位为 block（4KB），于是操作系统至少会读 0-4KB 的内容，这恰好可以在一个 page 中装下。
- 但是操作系统出于空间局部性原理（靠近当前被访问数据的数据，在未来很大概率会被访问到），会选择将磁盘块 offset [4KB,8KB)、[8KB,12KB) 以及 [12KB,16KB) 都加载到内存，于是额外在内存中申请了 3 个 page；

![img](https://cdn.xiaolincoding.com//mysql/other/ae8252378169c8c14b8b9907983f7d8b.png)

因此，预读机制带来的好处就是**减少了 磁盘 I/O 次数，提高系统磁盘 I/O 吞吐量**。

MySQL Innodb 存储引擎的 Buffer Pool 也有类似的预读机制，MySQL 从磁盘加载页时，会提前把它相邻的页一并加载进来，目的是为了减少磁盘 IO。

**缺点：**

如果**这些被提前加载进来的页，并没有被访问**，相当于这个预读工作是白做了，这个就是**预读失效**。

如果使用传统的 LRU 算法，就会把「预读页」放到 LRU 链表头部，而当内存空间不够的时候，还需要把末尾的页淘汰掉。

如果这些「预读页」如果一直不会被访问到，就会出现一个很奇怪的问题，**不会被访问的预读页却占用了 LRU 链表前排的位置，而末尾淘汰的页，可能是热点数据，这样就大大降低了缓存命中率** 。

**解决方案：**

**让预读页停留在内存里的时间要尽可能的短，让真正被访问的页才移动到 LRU 链表的头部，从而保证真正被读取的热数据留在内存里的时间尽可能长**。

Linux 操作系统和 MySQL Innodb 通过改进传统 LRU 链表来避免预读失效带来的影响，具体的改进分别如下：

- Linux 操作系统实现两个了 LRU 链表：**活跃 LRU 链表（active_list）和非活跃 LRU 链表（inactive_list）**；
- MySQL 的 Innodb 存储引擎是在一个 LRU 链表上划分来 2 个区域：**young 区域 和 old 区域**。

这两个改进方式，设计思想都是类似的，**都是将数据分为了冷数据和热数据，然后分别进行 LRU 算法**。不再像传统的 LRU 算法那样，所有数据都只用一个 LRU 算法管理。

#### 1.9.5、Linux避免预读失效

Linux 操作系统实现两个了 LRU 链表：**活跃 LRU 链表（active_list）和非活跃 LRU 链表（inactive_list）**。

- **active list** 活跃内存页链表，这里存放的是最近被访问过（活跃）的内存页；
- **inactive list** 不活跃内存页链表，这里存放的是很少被访问（非活跃）的内存页；

有了这两个 LRU 链表后，**预读页就只需要加入到 inactive list 区域的头部，当页被真正访问的时候，才将页插入 active list 的头部**。如果预读的页一直没有被访问，就会从 inactive list 移除，这样就不会影响 active list 中的热点数据。

#### 1.9.6、MySQL避免预读失效

MySQL 的 Innodb 存储引擎是在一个 LRU 链表上划分来 2 个区域，**young 区域 和 old 区域**。

young 区域在 LRU 链表的前半部分，old 区域则是在后半部分，这两个区域都有各自的头和尾节点，如下图：

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/mysql/innodb/young%2Bold.png)

**划分这两个区域后，预读的页就只需要加入到 old 区域的头部，当页被真正访问的时候，才将页插入 young 区域的头部**。如果预读的页一直没有被访问，就会从 old 区域移除，这样就不会影响 young 区域中的热点数据。

#### 1.9.7、缓存污染

虽然 Linux （实现两个 LRU 链表）和 MySQL （划分两个区域）通过改进传统的 LRU 数据结构，避免了预读失效带来的影响。

但是如果还是使用「只要数据被访问一次，就将数据加入到活跃 LRU 链表头部（或者 young 区域）」这种方式的话，那么**还存在缓存污染的问题**。

当我们在批量读取数据的时候，由于数据被访问了一次，这些大量数据都会被加入到「活跃 LRU 链表」里，然后之前缓存在活跃 LRU 链表（或者 young 区域）里的热点数据全部都被淘汰了，**如果这些大量的数据在很长一段时间都不会被访问的话，那么整个活跃 LRU 链表（或者 young 区域）就被污染了**。

#### 1.9.8、避免缓存污染

**提高进入到活跃 LRU 链表（或者 young 区域）的门槛，就能有效地保证活跃 LRU 链表（或者 young 区域）里的热点数据不会被轻易替换掉**。

Linux 操作系统和 MySQL Innodb 存储引擎分别是这样提高门槛的：

- **Linux 操作系统**：在内存页被访问**第二次**的时候，才将页从 inactive list 升级到 active list 里。

- MySQL Innodb：在内存页被访问

  第二次

  的时候，并不会马上将该页从 old 区域升级到 young 区域，因为还要进行

  停留在 old 区域的时间判断：

  - 如果第二次的访问时间与第一次访问的时间**在 1 秒内**（默认值），那么该页就**不会**被从 old 区域升级到 young 区域；
  - 如果第二次的访问时间与第一次访问的时间**超过 1 秒**，那么该页就**会**从 old 区域升级到 young 区域；

在批量读取数据时候，**如果这些大量数据只会被访问一次，那么它们就不会进入到活跃 LRU 链表（或者 young 区域）**，也就不会把热点数据淘汰，只会待在非活跃 LRU 链表（或者 old 区域）中，后续很快也会被淘汰。

>传统的 LRU 算法法无法避免下面这两个问题：
>
>- 预读失效导致缓存命中率下降；
>- 缓存污染导致缓存命中率下降；
>
>为了避免「预读失效」造成的影响，Linux 和 MySQL 对传统的 LRU 链表做了改进：
>
>- Linux 操作系统实现两个了 LRU 链表：**活跃 LRU 链表（active list）和非活跃 LRU 链表（inactive list）**。
>- MySQL Innodb 存储引擎是在一个 LRU 链表上划分来 2 个区域：**young 区域 和 old 区域**。
>
>但是如果还是使用「只要数据被访问一次，就将数据加入到活跃 LRU 链表头部（或者 young 区域）」这种方式的话，那么**还存在缓存污染的问题**。
>
>为了避免「缓存污染」造成的影响，Linux 操作系统和 MySQL Innodb 存储引擎分别提高了升级为热点数据的门槛：
>
>- Linux 操作系统：在内存页被访问**第二次**的时候，才将页从 inactive list 升级到 active list 里。
>
>- MySQL Innodb：在内存页被访问
>
>  第二次
>
>  的时候，并不会马上将该页从 old 区域升级到 young 区域，因为还要进行
>
>  停留在 old 区域的时间判断
>
>  ：
>
>  - 如果第二次的访问时间与第一次访问的时间**在 1 秒内**（默认值），那么该页就**不会**被从 old 区域升级到 young 区域；
>  - 如果第二次的访问时间与第一次访问的时间**超过 1 秒**，那么该页就**会**从 old 区域升级到 young 区域；

## 2、进程管理

### 2.1、进程、线程和协程

- 进程（Process）：进程是操作系统中的一个执行实例，它拥有独立的内存空间和资源。每个进程都是独立运行的，拥有自己的地址空间、文件句柄、环境变量等。进程间通信需要通过特定的机制，如管道、消息队列、共享内存等。
- 线程（Thread）：线程是进程的一部分，是在同一进程内并发执行的执行单元。不同线程共享同一进程的内存空间和资源，包括全局变量、堆、文件描述符等。线程可以更轻量级地创建、切换和销毁，相对于进程而言，线程间的切换开销较小。线程之间可以通过共享内存等机制进行通信。
- 协程（Coroutine）：协程是一种用户级的轻量级线程。协程由用户控制，而不是由操作系统内核控制。在协程中，执行流可以在不同协程之间进行切换，切换由程序员手动控制，而不需要内核介入。协程可以在一个线程内实现并发，但无法利用多核心处理器。协程通常用于实现高效的异步编程和协作任务。

### 2.2、并行和并发

![并发与并行](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/5-%E5%B9%B6%E5%8F%91%E4%B8%8E%E5%B9%B6%E8%A1%8C.jpg)

### 2.3、进程的状态

![七种状态变迁](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/10-%E8%BF%9B%E7%A8%8B%E4%B8%83%E4%B8%AD%E7%8A%B6%E6%80%81.jpg)

- 创建状态（*new*）：进程正在被创建时的状态；
- 运行状态（*Running*）：该时刻进程占用 CPU；
- 就绪状态（*Ready*）：可运行，由于其他进程处于运行状态而暂时停止运行；
- 阻塞状态（*Blocked*）：该进程正在等待某一事件发生（如等待输入/输出操作的完成）而暂时停止运行，这时，即使给它CPU控制权，它也无法运行；
- 阻塞挂起状态：进程在外存（硬盘）并等待某个事件的出现；
- 就绪挂起状态：进程在外存（硬盘），但只要进入内存，即刻立刻运行；
- 结束状态（*Exit*）：进程正在从系统中消失时的状态；

### 2.4、PCB（进程控制块）

**PCB 是进程存在的唯一标识**，这意味着一个进程的存在，必然会有一个 PCB，如果进程消失了，那么 PCB 也会随之消失。

PCB中包含：

* 进程描述信息
* 进程控制和管理信息
* 资源分配清单
* CPU相关信息

PCB通过**链表**的方式进行组织，把具有**相同状态的进程链在一起，组成各种队列**。比如：

- 将所有处于就绪状态的进程链在一起，称为**就绪队列**；
- 把所有因等待某事件而处于等待状态的进程链在一起就组成各种**阻塞队列**；
- 另外，对于运行队列在单核 CPU 系统中则只有一个运行指针了，因为单核 CPU 在某个时间，只能运行一个程序。

就绪队列和阻塞队列链表的组织形式如下图：

![就绪队列和阻塞队列](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/12-PCB%E7%8A%B6%E6%80%81%E9%93%BE%E8%A1%A8%E7%BB%84%E7%BB%87.jpg)

一般会选择链表，因为可能面临进程创建，销毁等调度导致进程状态发生变化，所以链表能够更加灵活的插入和删除。

### 2.4、线程

**线程是进程当中的一条执行流程。**

同一个进程内多个线程之间可以共享代码段、数据段、打开的文件等资源，但每个线程各自都有一套独立的寄存器和栈，这样可以确保线程的控制流是相对独立的。

![多线程](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/16-%E5%A4%9A%E7%BA%BF%E7%A8%8B%E5%86%85%E5%AD%98%E7%BB%93%E6%9E%84.jpg)

#### 2.4.1、线程和进程的区别

线程与进程的比较如下：

- 进程是资源（包括内存、打开的文件等）分配的单位，线程是 CPU 调度的单位；
- 进程拥有一个完整的资源平台，而线程只独享必不可少的资源，如寄存器和栈；
- 线程同样具有就绪、阻塞、执行三种基本状态，同样具有状态之间的转换关系；
- 线程能减少并发执行的时间和空间开销；

对于，线程相比进程能减少开销，体现在：

- 线程的创建时间比进程快，因为进程在创建的过程中，还需要资源管理信息，比如内存管理信息、文件管理信息，而线程在创建的过程中，不会涉及这些资源管理信息，而是共享它们；
- 线程的终止时间比进程快，因为线程释放的资源相比进程少很多；
- 同一个进程内的线程切换比进程切换快，因为线程具有相同的地址空间（虚拟内存共享），这意味着同一个进程的线程都具有同一个页表，那么在切换的时候不需要切换页表。而对于进程之间的切换，切换的时候要把页表给切换掉，而页表的切换过程开销是比较大的；
- 由于同一进程的各线程间共享内存和文件资源，那么在线程之间数据传递的时候，就不需要经过内核了，这就使得线程之间的数据交互效率更高了；

所以，不管是时间效率，还是空间效率线程比进程都要高。

#### 2.4.2、线程的实现方式

主要有三种线程的实现方式：

- **用户线程（\*User Thread\*）**：在用户空间实现的线程，不是由内核管理的线程，是由用户态的线程库来完成线程的管理；
- **内核线程（\*Kernel Thread\*）**：在内核中实现的线程，是由内核管理的线程；
- **轻量级进程（\*LightWeight Process\*）**：在内核中来支持用户线程；

### 2.5、进程调度

进程都希望自己能够占用 CPU 进行工作，那么这涉及到前面说过的进程上下文切换。

一旦操作系统把进程切换到运行状态，也就意味着该进程占用着 CPU 在执行，但是当操作系统把进程切换到其他状态时，那就不能在 CPU 中执行了，于是操作系统会选择下一个要运行的进程。

选择一个进程运行这一功能是在操作系统中完成的，通常称为**调度程序**（*scheduler*）。

#### 2.5.1、调度时机

在进程的生命周期中，当进程从一个运行状态到另外一状态变化的时候，其实会触发一次调度。

>比如，以下状态的变化都会触发操作系统的调度：
>
>* *从就绪态 -> 运行态*：当进程被创建时，会进入到就绪队列，操作系统会从就绪队列选择一个进程运行；
>* *从运行态 -> 阻塞态*：当进程发生 I/O 事件而阻塞时，操作系统必须选择另外一个进程运行；
>* *从运行态 -> 结束态*：当进程退出结束后，操作系统得从就绪队列选择另外一个进程运行；

因为，这些状态变化的时候，操作系统需要考虑是否要让新的进程给 CPU 运行，或者是否让当前进程从 CPU 上退出来而换另一个进程运行。

另外，如果硬件时钟提供某个频率的周期性中断，那么可以根据如何处理时钟中断 ，把调度算法分为两类：

- **非抢占式调度算法**挑选一个进程，然后让该进程运行直到被阻塞，或者直到该进程退出，才会调用另外一个进程，也就是说不会理时钟中断这个事情。
- **抢占式调度算法**挑选一个进程，然后让该进程只运行某段时间，如果在该时段结束时，该进程仍然在运行时，则会把它挂起，接着调度程序从就绪队列挑选另外一个进程。这种抢占式调度处理，需要在时间间隔的末端发生**时钟中断**，以便把 CPU 控制返回给调度程序进行调度，也就是常说的**时间片机制**。

#### 2.5.2、调度原则

- **CPU 利用率**：调度程序应确保 CPU 是始终匆忙的状态，这可提高 CPU 的利用率；
- **系统吞吐量**：吞吐量表示的是单位时间内 CPU 完成进程的数量，长作业的进程会占用较长的 CPU 资源，因此会降低吞吐量，相反，短作业的进程会提升系统吞吐量；
- **周转时间**：周转时间是进程运行+阻塞时间+等待时间的总和，一个进程的周转时间越小越好；
- **等待时间**：这个等待时间不是阻塞状态的时间，而是进程处于就绪队列的时间，等待的时间越长，用户越不满意；
- **响应时间**：用户提交请求到系统第一次产生响应所花费的时间，在交互式系统中，响应时间是衡量调度算法好坏的主要标准。

### 2.6、进程调度算法

#### 2.6.1、先来先服务调度算法（First Come First Serve, FCFS）

![FCFS 调度算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/24-%E5%85%88%E6%9D%A5%E5%85%88%E6%9C%8D%E5%8A%A1.jpg)

**每次从就绪队列选择最先进入队列的进程，然后一直运行，直到进程退出或被阻塞，才会继续从队列中选择第一个进程接着运行。**

**适用场景**：FCFS 对长作业有利，适用于 CPU 繁忙型作业的系统，而不适用于 I/O 繁忙型作业的系统。

#### 2.6.2、最短作业优先调度算法（Shortest Job First, SJF）

![SJF 调度算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/25-%E6%9C%80%E7%9F%AD%E4%BD%9C%E4%B8%9A%E4%BC%98%E5%85%88%E7%AE%97%E6%B3%95.jpg)

**优先选择运行时间最短的进程来运行**

#### 2.6.3、高响应比优先调度算法（Highest Response Ratio Next, HRRN）

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/26-%E5%93%8D%E5%BA%94%E6%AF%94%E5%85%AC%E5%BC%8F.jpg)

**高响应比优先 （\*Highest Response Ratio Next, HRRN\*）调度算法**主要是权衡了短作业和长作业。

**每次进行进程调度时，先计算「响应比优先级」，然后把「响应比优先级」最高的进程投入运行**

#### 2.6.4、时间片轮转调度算法（Round Robin, RR）

![RR 调度算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/27-%E6%97%B6%E9%97%B4%E7%89%87%E8%BD%AE%E8%AF%A2.jpg)

**每个进程被分配一个时间段，称为时间片（\*Quantum\*），即允许该进程在该时间段中运行。**

- 如果时间片用完，进程还在运行，那么将会把此进程从 CPU 释放出来，并把 CPU 分配给另外一个进程；
- 如果该进程在时间片结束前阻塞或结束，则 CPU 立即进行切换；

#### 2.6.5、最高优先级调度算法（Highest Priority First，HPF）

**从就绪队列中选择最高优先级的进程进行运行**

进程的优先级可以分为，静态优先级和动态优先级：

- 静态优先级：创建进程时候，就已经确定了优先级了，然后整个运行时间优先级都不会变化；
- 动态优先级：根据进程的动态变化调整优先级，比如如果进程运行时间增加，则降低其优先级，如果进程等待时间（就绪队列的等待时间）增加，则升高其优先级，也就是**随着时间的推移增加等待进程的优先级**。

该算法也有两种处理优先级高的方法，非抢占式和抢占式：

- 非抢占式：当就绪队列中出现优先级高的进程，运行完当前进程，再选择优先级高的进程。
- 抢占式：当就绪队列中出现优先级高的进程，当前进程挂起，调度优先级高的进程运行。

#### 2.6.6、多级反馈队列调度算法（Multilevel Feedback Queue）

**多级反馈队列（\*Multilevel Feedback Queue\*）调度算法**是「时间片轮转算法」和「最高优先级算法」的综合和发展。

- 「多级」表示有多个队列，每个队列优先级从高到低，同时优先级越高时间片越短。
- 「反馈」表示如果有新的进程加入优先级高的队列时，立刻停止当前正在运行的进程，转而去运行优先级高的队列；

![多级反馈队列](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E5%92%8C%E7%BA%BF%E7%A8%8B/28-%E5%A4%9A%E7%BA%A7%E9%98%9F%E5%88%97.jpg)

### 2.7、进程间通信

- 管道（Pipe）：管道是一种半双工的通信方式，可以在具有亲缘关系的进程之间进行通信。它可以分为匿名管道和命名管道。匿名管道只能在具有共同祖先的进程之间使用，而命名管道可以在不具有亲缘关系的进程之间使用。
  - 优点：简单易用，无需额外的系统调用和复杂的设置。
  - 缺点：只能在具有亲缘关系的进程之间进行通信，且只能实现单向通信。
- 信号（Signal）：信号是一种异步的通信方式，用于通知进程发生了某种事件。一个进程可以向另一个进程发送信号，接收信号的进程可以选择采取相应的行动。
  - 优点：简单、快速，适用于简单的通信需求。
  - 缺点：信号的发送和接收是异步的，无法传递大量数据，且不支持双向通信。
- 共享内存（Shared Memory）：共享内存是一种高效的通信方式，多个进程可以将同一块内存空间映射到各自的地址空间中，从而实现共享数据。
  - 优点：传输效率高，适用于大量数据的共享。
  - 缺点：需要额外的同步机制来保证数据的一致性和互斥访问，容易造成数据竞争和死锁。
- 信号量（Semaphore）：信号量是一种用于进程间同步的机制，可以用来保护共享资源的互斥访问。
  - 优点：可以用于进程间的同步和互斥。
  - 缺点：只提供了同步和互斥的功能，无法传递大量数据。
- 消息队列：消息队列是一种消息传递的机制，可以在不同进程之间传递特定格式的消息。
  - 优点：支持多对多的进程通信，每个消息都有特定的格式。
  - 缺点：消息的发送和接收是同步的，且不支持实时性要求较高的通信。
- 套接字（Socket）：套接字是一种通用的进程间通信机制，可以在不同主机上的进程之间进行通信。
  - 优点：支持网络通信，可以在不同主机上的进程之间进行通信。
  - 缺点：相对于其他IPC方式，套接字的使用和编程复杂度较高。

#### 2.7.1、管道

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E9%97%B4%E9%80%9A%E4%BF%A1/8-%E7%AE%A1%E9%81%93-pipe-shell.jpg)

* **匿名管道**顾名思义，它没有名字标识，匿名管道是特殊文件只存在于内存，没有存在于文件系统中，shell 命令中的「`|`」竖线就是匿名管道，通信的数据是**无格式的流并且大小受限**，通信的方式是**单向**的，数据只能在一个方向上流动，如果要双向通信，需要创建两个管道，再来**匿名管道是只能用于存在父子关系的进程间通信**，匿名管道的生命周期随着进程创建而建立，随着进程终止而消失。
* **命名管道**突破了匿名管道只能在亲缘关系进程间的通信限制，因为使用命名管道的前提，需要在文件系统创建一个类型为 p 的设备文件，那么毫无关系的进程就可以通过这个设备文件进行通信。另外，不管是匿名管道还是命名管道，进程写入的数据都是**缓存在内核**中，另一个进程读取数据时候自然也是从内核中获取，同时通信数据都遵循**先进先出**原则，不支持 lseek 之类的文件定位操作。

#### 2.7.2、消息队列

**消息队列**克服了管道通信的数据是无格式的字节流的问题，消息队列实际上是保存在内核的「消息链表」，消息队列的消息体是可以用户自定义的数据类型，发送数据时，会被分成一个一个独立的消息体，当然接收数据时，也要与发送方发送的消息体的数据类型保持一致，这样才能保证读取的数据是正确的。消息队列通信的速度不是最及时的，毕竟**每次数据的写入和读取都需要经过用户态与内核态之间的拷贝过程。**

#### 2.7.3、共享内存

**共享内存**可以解决消息队列通信中用户态与内核态之间数据拷贝过程带来的开销。

在操作系统中，每个进程都有自己独立的虚拟内存空间，不同进程的虚拟内存映射到不同的物理内存中。

共享内存就是拿出一块虚拟地址空间，映射到相同的物理内存中。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%BF%9B%E7%A8%8B%E9%97%B4%E9%80%9A%E4%BF%A1/9-%E5%85%B1%E4%BA%AB%E5%86%85%E5%AD%98.jpg)

这样**每个进程都可以直接访问这个共享内存**，就像访问进程自己的空间一样快捷方便，不需要陷入内核态或者系统调用，大大提高了通信的速度，享有**最快**的进程间通信方式之名。但是便捷高效的共享内存通信，**带来新的问题，多进程竞争同个共享资源会造成数据的错乱。**

#### 2.7.4、信号量

信号量是为了防止多进程竞争共享资源，而造成的数据错乱。

使用**信号量**来保护共享资源，以确保任何时刻只能有一个进程访问共享资源，这种方式就是互斥访问。**信号量不仅可以实现访问的互斥性，还可以实现进程间的同步**，信号量其实是一个计数器，表示的是资源个数，其值可以通过两个原子操作来控制，分别是 **P 操作和 V 操作**。

- 一个是 **P 操作**，这个操作会把信号量减去 1，相减后如果信号量 < 0，则表明资源已被占用，进程需阻塞等待；相减后如果信号量 >= 0，则表明还有资源可使用，进程可正常继续执行。
- 另一个是 **V 操作**，这个操作会把信号量加上 1，相加后如果信号量 <= 0，则表明当前有阻塞中的进程，于是会将该进程唤醒运行；相加后如果信号量 > 0，则表明当前没有阻塞中的进程；

#### 2.7.5、信号

信号是**异步通信机制**，信号可以在应用进程和内核之间直接交互，内核也可以利用信号来通知用户空间的进程发生了哪些系统事件，信号事件的来源主要有硬件来源（如键盘 Cltr+C ）和软件来源（如 kill 命令），一旦有信号发生，**进程有三种方式响应信号 1. 执行默认操作、2. 捕捉信号、3. 忽略信号**。有两个信号是应用进程无法捕捉和忽略的，即 `SIGKILL` 和 `SIGSTOP`，这是为了方便我们能在任何时候结束或停止某个进程。

#### 2.7.6、Socket

前面说到的通信机制，都是工作于同一台主机，如果**要与不同主机的进程间通信，那么就需要 Socket 通信了**。

**特点**：跨主机通信

Socket 实际上不仅用于不同的主机进程间通信，还可以用于本地主机进程间通信，可根据创建 Socket 的类型不同，分为三种常见的通信方式：

* 基于 TCP 协议的通信方式
* 基于 UDP 协议的通信方式
* 本地进程间通信方式。

### 2.8、进程死锁

#### 2.8.1、死锁条件

死锁只有**同时满足**以下四个条件才会发生：

- 互斥条件：是指**多个线程不能同时使用同一个资源**。

  ![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E6%AD%BB%E9%94%81/%E4%BA%92%E6%96%A5%E6%9D%A1%E4%BB%B6.png)

- 请求保持条件：指当线程 A 已经持有了资源 1，又想申请资源 2，而资源 2 已经被线程 C 持有了，所以线程 A 就会处于等待状态，但是**线程 A 在等待资源 2 的同时并不会释放自己已经持有的资源 1**。

  ![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E6%AD%BB%E9%94%81/%E6%8C%81%E6%9C%89%E5%B9%B6%E7%AD%89%E5%BE%85%E6%9D%A1%E4%BB%B6.png)

- 不可剥夺条件：指当线程已经持有了资源 ，**在自己使用完之前不能被其他线程获取**，线程 B 如果也想使用此资源，则只能在线程 A 使用完并释放后才能获取。

  ![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E6%AD%BB%E9%94%81/%E4%B8%8D%E5%8F%AF%E5%89%A5%E5%A4%BA%E6%9D%A1%E4%BB%B6.png)

- 循环等待条件：指的是在死锁发生的时候，**两个线程获取资源的顺序构成了环形链**。

  ![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E6%AD%BB%E9%94%81/%E7%8E%AF%E8%B7%AF%E7%AD%89%E5%BE%85%E6%9D%A1%E4%BB%B6.png)

#### 2.8.2、死锁的解决方法

避免死锁问题就只需要破环四个必要条件的其中一个条件就可以，最常见的并且可行的就是**使用资源有序分配法，来破环环路等待条件**。

**资源有序分配法**：

线程 A 和 线程 B 获取资源的顺序要一样，当线程 A 是先尝试获取资源 A，然后尝试获取资源 B 的时候，线程 B 同样也是先尝试获取资源 A，然后尝试获取资源 B。也就是说，线程 A 和 线程 B 总是以相同的顺序申请自己想要的资源。

我们使用资源有序分配法的方式来修改前面发生死锁的代码，我们可以不改动线程 A 的代码。

我们先要清楚线程 A 获取资源的顺序，它是先获取互斥锁 A，然后获取互斥锁 B。

所以我们只需将线程 B 改成以相同顺序的获取资源，就可以打破死锁了。

![image-20240522102035311](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240522102035311.png)

## 3、调度算法

### 3.1、页面置换算法

当内存不足时，就需要使用「**页面置换算法**」选择一个物理页，如果该物理页有被修改过（脏页），则把它换出到磁盘，然后把该被置换出去的页表项的状态改成「无效的」，最后把正在访问的页面装入到这个物理页中。

#### 3.1.1、最佳页面置换算法

**置换在「未来」最长时间不访问的页面**。

![最佳页面置换算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E6%9C%80%E4%BC%98%E7%BD%AE%E6%8D%A2%E7%AE%97%E6%B3%95.png)

#### 3.1.2、先进先出页面置换算法

**选择在内存驻留时间很长的页面进行中置换**。

![先进先出置换算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/FIFO%E7%BD%AE%E6%8D%A2%E7%AE%97%E6%B3%95.png)

#### 3.1.3、最近最久未使用（LRU）页面置换算法

发生缺页时，**选择最长时间没有被访问的页面进行置换**。

![最近最久未使用的置换算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/LRU%E7%BD%AE%E6%8D%A2%E7%AE%97%E6%B3%95.png)

#### 3.1.4、时钟页面置换算法

把所有的页面都保存在一个类似钟面的「环形链表」中，一个表针指向最老的页面。

当发生缺页中断时，算法首先检查表针指向的页面：

- 如果它的访问位位是 0 就淘汰该页面，并把新的页面插入这个位置，然后把表针前移一个位置；
- 如果访问位是 1 就清除访问位，并把表针前移一个位置，重复这个过程直到找到了一个访问位为 0 的页面为止；

![时钟页面置换算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E6%97%B6%E9%92%9F%E7%BD%AE%E6%8D%A2%E7%AE%97%E6%B3%95.png)

#### 3.1.5、最不常用页面置换（LFU）算法

**当发生缺页中断时，选择「访问次数」最少的那个页面，并将其淘汰**。

它的实现方式是，对每个页面设置一个「访问计数器」，每当一个页面被访问时，该页面的访问计数器就累加 1。在发生缺页中断时，淘汰计数器值最小的那个页面。

## 3.2、磁盘调度算法

### 3.2.1、先来先服务（*First-Come，First-Served，FCFS*）

**先到来的请求，先被服务。**

![先来先服务](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E7%A3%81%E7%9B%98%E8%B0%83%E5%BA%A6-%E5%85%88%E6%9D%A5%E5%85%88%E6%9C%8D%E5%8A%A1.png)

### 3.2.2、最短寻道时间优先（*Shortest Seek First，SSF*）

**优先选择从当前磁头位置所需寻道时间最短的请求**

![最短寻道时间优先](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E7%A3%81%E7%9B%98%E8%B0%83%E5%BA%A6-%E6%9C%80%E7%9F%AD%E5%AF%BB%E9%81%93%E6%97%B6%E9%97%B4%E4%BC%98%E5%85%88.png)

### 3.2.3、扫描算法（*Scan*）

**磁头在一个方向上移动，访问所有未完成的请求，直到磁头到达该方向上的最后的磁道，才调换方向，这就是扫描（\*Scan\*）算法**

![扫描算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E7%A3%81%E7%9B%98%E8%B0%83%E5%BA%A6-%E6%89%AB%E6%8F%8F%E7%AE%97%E6%B3%95.png)

### 3.2.4、循环扫描算法（*Circular Scan, CSCAN*）

只有磁头朝某个特定方向移动时，才处理磁道访问请求，而返回时直接快速移动至最靠边缘的磁道，也就是复位磁头，这个过程是很快的，并且**返回中途不处理任何请求**，该算法的特点，就是**磁道只响应一个方向上的请求**。

![循环扫描算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E7%A3%81%E7%9B%98%E8%B0%83%E5%BA%A6-C-SCAN%E7%AE%97%E6%B3%95.png)

### 3.2.5、LOOK 与 C-LOOK算法

**磁头在移动到「最远的请求」位置，然后立即反向移动。**

* **针对SCAN算法的优化->LOOK算法**：磁头在每个方向上仅仅移动到最远的请求位置，然后立即反向移动，而不需要移动到磁盘的最始端或最末端，**反向移动的途中会响应请求**。

  ![LOOK 算法](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost2/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E8%B0%83%E5%BA%A6%E7%AE%97%E6%B3%95/%E7%A3%81%E7%9B%98%E8%B0%83%E5%BA%A6-LOOK%E7%AE%97%E6%B3%95.png)

* **针对C-SCAN算法的优化->C-LOOK算法**：磁头在每个方向上仅仅移动到最远的请求位置，然后立即反向移动，而不需要移动到磁盘的最始端或最末端，**反向移动的途中不会响应请求**。

## 4、I/O多路复用：select/poll/epoll

最基础的 TCP 的 Socket 编程，它是阻塞 I/O 模型，基本上只能一对一通信，那为了服务更多的客户端，我们需要改进网络 I/O 模型。

比较传统的方式是使用多进程/线程模型，每来一个客户端连接，就分配一个进程/线程，然后后续的读写都在对应的进程/线程，这种方式处理 100 个客户端没问题，但是当客户端增大到 10000 个时，10000 个进程/线程的调度、上下文切换以及它们占用的内存，都会成为瓶颈。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E5%A4%9A%E8%B7%AF%E5%A4%8D%E7%94%A8/%E5%A4%9A%E8%B7%AF%E5%A4%8D%E7%94%A8.png)

为了解决上面这个问题，就出现了 I/O 的多路复用，可以只在一个进程里处理多个文件的 I/O，Linux 下有三种提供 I/O 多路复用的 API，分别是：select、poll、epoll。这三种方式可以使得**进程可以通过一个系统调用函数从内核中获取多个事件**。

select 和 poll 并没有本质区别，它们内部都是使用「线性结构」来存储进程关注的 Socket 集合。

在使用的时候，首先需要把关注的 Socket 集合通过 select/poll 系统调用从用户态拷贝到内核态，然后由内核检测事件，当有网络事件产生时，内核需要遍历进程关注 Socket 集合，找到对应的 Socket，并设置其状态为可读/可写，然后把整个 Socket 集合从内核态拷贝到用户态，用户态还要继续遍历整个 Socket 集合找到可读/可写的 Socket，然后对其处理。

很明显发现，select 和 poll 的缺陷在于，当客户端越多，也就是 Socket 集合越大，Socket 集合的遍历和拷贝会带来很大的开销，因此也很难应对 C10K。

epoll 是解决 C10K 问题的利器，通过两个方面解决了 select/poll 的问题。

- epoll 在内核里使用「红黑树」来关注进程所有待检测的 Socket，红黑树是个高效的数据结构，增删改一般时间复杂度是 O(logn)，通过对这棵黑红树的管理，不需要像 select/poll 在每次操作时都传入整个 Socket 集合，减少了内核和用户空间大量的数据拷贝和内存分配。
- epoll 使用事件驱动的机制，内核里维护了一个「链表」来记录就绪事件，只将有事件发生的 Socket 集合传递给应用程序，不需要像 select/poll 那样轮询扫描整个集合（包含有和无事件的 Socket ），大大提高了检测的效率。

![img](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost4@main/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F/%E5%A4%9A%E8%B7%AF%E5%A4%8D%E7%94%A8/epoll.png)

# 十六、E-Commerce

>**项目简介**：E-Commerce项目是一个融合了后台管理和前台商城功能的全方位电商解决方案。利用Spring Boot和Vue构建的前后端分离架构，提供了一个高效的电子商务平台。管理员可以轻松管理商品、订单、会员和营销活动，而用户则享受到了丰富的购物功能，包括个性化推荐、快捷搜索、便利的购物车和流畅的订单流程。
>
>**核心技术**：SpringBoot、MyBatis、SpringSecurity、RabbitMQ、Redis、MongoDB、Elasticsearch、MinIO、Docker
>
>**技术要点**：
>
>* 基于Spring Security实现用户认证授权和动态权限，同时使用AOP+Redis优化了权限管理功能，提高了系统的灵活性和安全性。
>* 基于Redis消息中间件，实现了购物车、秒杀活动等高并发访问场景的开发，保证了系统的性能和可伸缩性。
>* 基于RabbitMQ开源消息中间件，实现项目中的延迟消息业务场景，完善了订单流程，包括从前台商城下单或取消到后台发货到交易完成，同时集成支付宝支付接口实现在线支付功能。
>* 使用Elasticsearch实现综合商品搜索、相关商品推荐及聚合商品信息，并整合ELK实现日志收集系统，同时对调试日志、业务日志、错误日志、接口访问日志分场景收集日志，方便系统运维和性能分析。
>* 使用MongoDB实现前台商城用户大数据量的存储。同时利用MinIO实现了文件存储功能，满足了系统对文件的存储和管理需求
>* 项目采用Docker容器化部署，简化了部署过程，提高了系统的可维护性和可靠性。


>在E-Commerce项目中，构建了一个高效的前后端分离电商系统。业务上，实现了完整的订单流程，首先用户在移动端查看商品，并将感兴趣的商品加入到购物车中，结算时查看购物车并选中指定商品创建订单，添加订单信息，包括收货地址、优惠券、使用积分折扣等，填写完成后提交订单并支付，订单生成后用户可在我的订单中查看相关订单信息。后台管理系统收到订单后，审核完信息后将订单发货，管理员确认发货后，用户可在移动端商城中的我的订单中实时查看订单流程，用户收到商品后确认订单，此次交易完成。管理员和用户可在各自的系统上查看此次订单的详细信息。
>
>此外，针对项目的使用和优化上，首先基于SpringSecurity实现了用户认证和动态权限，结合AOP和Redis优化了权限管理，提升了系统的安全性和性能。并基于Redis实现了高并发访问场景的开发，确保系统稳定运行。同时，利用RabbitMQ实现了订单流程中的延迟消息处理，完善了订单从下单到交易完成的整个流程。此外，还实现了商品搜索和文件存储功能，最后，通过Docker进行容器化部署，提高了系统的可维护性。这个项目使我在高并发、数据处理以及系统运维方面积累了丰富的经验。

## 1、模块组成：

* 前台商城系统：首页门户、商品推荐、商品搜索、商品展示、商品分类、购物车、订单流程、会员中心等模块
* 后台管理系统：商品管理、订单管理、营销管理、权限管理四大模块。
  * 商品管理：商品列表、添加商品、商品分类、商品类型、品牌管理
  * 订单管理：订单列表、订单设置、退货申请处理、退货原因设置
  * 营销管理：秒杀活动列表、优惠券列表、品牌推荐、新品推荐、人气推荐、专题推荐、广告列表
  * 权限管理：用户列表、角色列表、菜单列表、资源列表

## 2、整体业务流程：

![image-20240424103519785](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424103519785.png)

* 前台：移动端商城查看商品，然后将商品加入购物车，结算时查看购物车并选中指定商品创建订单，添加订单信息，包括收获地址、优惠券、积分抵扣等，选择完成后提交订单并支付，订单生成后用户可在我的订单中查看相关订单信息。
* 后台：后台管理系统受到订单后，审核完信息后将订单发货，管理员确认发货后，用户可在移动端商城中的我的订单中实时查看订单流程，用户收到商品后确认订单，此次交易完成。管理员和用户可在各自的系统上查看此次订单的详细信息。

## 3、数据表分析

共涉及77张数据表，分别对应于：权限、商品、订单、营销、会员、专题。

### 3.1、后台管理系统

涉及四个模块的数据表：权限模块、商品模块、订单模块和营销模块。

* 权限模块：9张数据表，ums_admin、ums_admin_login_log、ums_admin_role、ums_admin_resource、ums_menu、ums_admin_role_relation、ums_role_resource_relation、ums_resource_category、ums_role_menu_relation
* 商品模块：18张数据表，pms_album、pms_album_pic、pms_brand、pms_comment、pms_comment_replay
  、pms_feight_template、pms_member_price、pms_product、pms_product_attribute、pms_product_attribute_category、pms_product_attribute_value、pms_product_category、pms_product_category_attribute_relation、pms_product_full_reduction、pms_product_ladder、pms_product_operate_log、pms_product_vertify_record、pms_sku_stock
* 订单模块：8张数据表，oms_cart_item、oms_company_address、oms_order、oms_order_item、oms_order_operate_history、oms_order_return_apply、oms_order_return_reason、oms_order_setting
* 营销模块：13张数据表：sms_coupon、sms_coupon_history、sms_coupon_product_category_relation、sms_coupon_product_relation、sms_flash_promotion、sms_flash_promotion_log、sms_flash_promotion_product_relation、sms_flash_promotion_session、sms_home_advertise、sms_home_brand、sms_home_new_product、sms_home_recommend_product、sms_home_recommend_subject

### 3.2、前台商城系统

主要涉及用户相关的数据表，共设计13张数据表：ums_growth_change_history、ums_integration_change_history、ums_integration_consume_setting、ums_member、ums_member_level、ums_member_login_log、ums_member_member_tag_relation、ums_member_product_category_relation、ums_member_receive_address、ums_member_rule_setting、ums_member_statistics_info、ums_member_tag、ums_member_task

## 4、模块业务分析

### 4.1、权限模块

* 用户列表：筛选搜索、数据列表、添加、编辑、删除、分配角色
* 角色列表：筛选搜索、数据列表、添加、编辑、删除、分配菜单、分配资源
* 菜单列表：数据列表、添加、编辑、删除
* 资源列表：筛选搜索、数据列表、资源分类（数据列表、添加、编辑、删除）、添加、编辑、删除

### 4.2、商品模块

* 商品列表：筛选搜索、数据列表、操作（查看、编辑、日志、删除）、批量操作（上下架、推荐、新品、转移分类）
* 添加商品：填写商品信息（商品分类、商品名称、副标题、商品品牌、商品介绍、商品货号、商品价格、商品库存）、填写商品促销（积分、成长值、上下架状态、商品标签、服务保证、商品详细页内容、优惠方式【特惠促销、会员价格、接替架构、满减价格】）、填写商品属性（属性类型、商品规格【SKU属性、价格、库存】、属性图片、商品参数、商品相册、商品详情）、选择商品关联（关联专题、关联优选）
* 商品分类：数据列表、设置、操作、添加分类
* 商品类型：数据列表、设置（属性或属性列表、添加属性或参数）、编辑、删除、添加类型
* 品牌管理：筛选搜索、数据列表、批量操作（显示、隐藏）、添加品牌

### 4.3、订单模块

* 订单列表：筛选搜索、数据列表、操作（查看订单、订单关闭、发货、跟踪、删除）、查看订单、批量操作（发货、关闭、删除）
* 订单设置：秒杀订单自动自动关闭时间、正常订单自动关闭时间、发货超过时间自动完成、订单完成多少天自动结束，不能申请售后、订单完成多少天自动五星好评
* 退货申请处理：筛选搜索、数据列表、查看详情（退货商品、服务单信息、操作【确认退货 、确认收货、拒绝退货】）
* 退货原因设置：数据列表、添加、编辑、删除

### 4.4、营销模块

![image-20240424155255377](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155255377.png)

![image-20240424155307063](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155307063.png)

![image-20240424155315062](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155315062.png)

![image-20240424155325875](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155325875.png)

![image-20240424155339689](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155339689.png)

![image-20240424155348934](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155348934.png)

![image-20240424155358031](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240424155358031.png)

## 5、技术点分析

### 5.1、跨域问题

**跨域就是从一个域名的网页去请求另一个域名的资源**。由于有**同源策略**的限制，一般是不允许这么访问的，但是很多场景会有跨域访问的需求，比如在前后端分离的模式下，前后端的域名是不一样的，此时就会出现跨域问题。

#### 5.1.1、解决方案:

* **CORS：跨域资源共享**

  CORS（Cross-origin resource sharing），跨域资源共享。浏览器会自动进行CORS通信，它的实现主要在服务端，**通过一些HTTP Header来限制可以访问的域**。例如页面A要向服务器B访问数据，如果B服务器上声明了允许A的域名访问，那么从A到B的跨域请求就可以完成。

  想要传递`cookie`需要满足 3 个条件：

  * web请求设置`withCredentials`：这里默认情况下在跨域请求，浏览器是不带 cookie 的。但是我们可以通过设置`withCredentials`来进行传递`cookie`.
  * `Access-Control-Allow-Credentials`为`true`
  * `Access-Control-Allow-Origin`为非`*`

* **CrossOrigin注解**

  如果项目使用的是SpringBoot，可以**在Controller类上添加一个@CrossOrigin注解就可以实现对当前controller的跨域访问**，该注解也可以直接加到方法上，**或者加到入口类上对所有的接口进行跨域处理**。

* **nginx反向代理接口跨域**

  nginx反向代理跨域原理：同源策略是浏览器的安全策略，不是HTTP协议的一部分。**服务器端调用HTTP接口只是使用HTTP协议，不会执行JS脚本，不需要同源策略，也就不存在跨域问题**。

  nginx反向代理接口跨域实现思路：通过nginx实现一个代理服务器（域名和domain1相同，端口不同）做跳板机，反向代理domain2接口，并且可以顺便修改cookie中的domain信息，方便当前域cookie写入，实现跨域登录。

  ```xml
  // proxy服务器
  server {
      listen       81;
      server_name  www.domain1.com;
      location / {
          proxy_pass   http://www.domain2.com:8080;  #反向代理
          proxy_cookie_domain www.domain2.com www.domain1.com; #修改cookie里域名
          index  index.html index.htm;
          
          add_header Access-Control-Allow-Origin http://www.domain1.com;
      }
  }
  ```

  这样我们的前端代理只要访问 http:www.domain1.com:81/*就可以了。

* **通过jsonp跨域**

  通常为了减轻web服务器的负载，我们把js、css、img等静态资源分离到一台独立域名的服务器上，在html页面中再通过相应的标签从不同域名下加载静态资源，这是浏览器允许的操作，**基于此原理，我们可以动态创建script，再请求一个带参网址实现跨域。**

#### 5.1.2、项目采用的解决方案

> CORS全称Cross-Origin Resource Sharing，意为跨域资源共享。当一个资源去访问另一个不同域名或者同域名不同端口的资源时，就会发出跨域请求。如果此时另一个资源不允许其进行跨域资源访问，那么访问的那个资源就会遇到跨域问题。

##### 第一步：添加GlobalCorsConfig配置文件来允许跨域访问：

```java
@Configuration
public class GlobalCorsConfig {
    /**
     * 允许跨域调用的过滤器
     */
    @Bean
    public CorsFilter corsFilter() {
        CorsConfiguration config = new CorsConfiguration();
        //允许所有域名进行跨域调用
        config.addAllowedOriginPattern("*");
        //允许跨越发送cookie
        config.setAllowCredentials(true);
        //放行全部原始头信息
        config.addAllowedHeader("*");
        //允许所有请求方法跨域调用
        config.addAllowedMethod("*");
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", config);
        return new CorsFilter(source);
    }
}
```

> 创建了一个CorsConfiguration对象，并设置其属性，包括允许所有域名跨域调用、允许跨越发送cookie、放行全部原始头信息和允许所有请求方法跨域调用。然后，它创建了一个UrlBasedCorsConfigurationSource对象，并将CorsConfiguration对象注册到其中。最后，它返回一个新的CorsFilter对象，该对象使用UrlBasedCorsConfigurationSource对象作为其配置源。

##### 第二步：设置SpringSecurity允许OPTIONS请求访问

> 在自定义的SecurityConfig类关于SecurityFilterChain的配置方法中添加如下代码：

```java
//允许跨域请求的OPTIONS请求
registry.antMatchers(HttpMethod.OPTIONS)
        .permitAll();
```

首先，在自定义的全局跨域配置类中，声明一个corsFilter的bean配置，在其中进行如下配置：包括允许所有的域名进行跨域调用，允许在跨域是携带cookie，放行全部的原始头信息，允许所有的请求方法进行跨域调用，然后将这些配置注册在根路径下，覆盖所有的节点，这样后端就能够允许所有的前端请求进行跨域调用，最后还要在Spring Security的配置文件中配置允许所有的 HTTP OPTIONS 请求。这样就完成了前后端的跨域问题。

### 5.2、基于Spring Security实现用户认证授权和动态权限

#### 5.2.1、传统的权限控制

> 采用Spring Security的默认机制实现

1. 在需要权限的接口上使用`@PreAuthorize`注解定义好需要的权限。
2. 然后将该权限值存入到权限表中，当用户登录时，将其所拥有的权限查询出来；
3. 之后Spring Security把用户拥有的权限值和接口上注解定义的权限值进行比对，如果包含则可以访问，反之就不可以访问；

> 但是这样做会带来一些问题，我们需要在每个接口上都定义好访问该接口的权限值，而且只能挨个控制接口的权限，无法批量控制。其实每个接口都可以由它的访问路径唯一确定，我们可以使用基于路径的动态权限控制来解决这些问题。 

#### 5.2.1、项目采用的权限控制

> 使用Spring Security实现基于路径的动态权限

* 首先我们需要**创建一个过滤器，用于实现动态权限控制**，这里需要注意的是`doFilter`方法，对于OPTIONS请求直接放行，否则前端调用会出现跨域问题。对于配置在`IgnoreUrlsConfig`中的白名单路径我也需要直接放行，所有的鉴权操作都会在`super.beforeInvocation(fi)`中进行。

* 在DynamicSecurityFilter中调用super.beforeInvocation(fi)方法时会调用AccessDecisionManager中的decide方法用于鉴权操作，而decide方法中的configAttributes参数会通过SecurityMetadataSource中的getAttributes方法来获取。
* 然后需要实现SecurityMetadataSource接口的getAttributes方法，用于获取当前访问路径所需资源。通过FilterInvocation对象获取当前访问的路径，使用AntPathMatcher匹配器匹配路径与配置的安全资源模式，如果匹配成功，则将对应的安全资源添加到configAttributes列表中
* 由于我们的后台资源规则被缓存在了一个Map对象之中，所以当后台资源发生变化时，我们需要清空缓存的数据，然后下次查询时就会被重新加载进来。
* 之后我们需要实现AccessDecisionManager接口来实现权限校验，对于没有配置资源的接口我们直接允许访问，对于配置了资源的接口，我们把访问所需资源和用户拥有的资源进行比对，如果匹配则允许访问。
* 接下来需要修改Spring Security的配置类SecurityConfig，当有动态权限业务类时在FilterSecurityInterceptor过滤器前添加我们的动态权限过滤器。
* 需要注意的是，当前端跨域访问没有权限的接口时，会出现跨域问题，只需要在没有权限访问的处理类RestfulAccessDeniedHandler中添加允许跨域访问的响应头即可。

### 5.3、使用AOP+Redis优化了权限管理功能

#### 5.3.1、权限管理优化

> 当用户登录后，请求会带着token经过过滤器，过滤器会根据用户携带的token进行类似免密登录的操作，其中有一步会从数据库中查询登录用户信息，如果没有任何优化操作，当我们登录后访问任意接口时，从数据库中查询用户信息和用户所拥有的资源信息，每次访问接口都触发这种操作，有的时候会带来一定的性能问题。

对于上面的问题，项目的优化思路大体就是把用户信息和用户资源信息存入到Redis中去，避免频繁查询数据库。

业务中主要是获取用户信息和获取用户的资源信息这两个操作，因此需要给这两个操作添加缓存操作，这里使用的是RedisTemple的操作方式。当查询数据时，先去Redis缓存中查询，如果Redis中没有，再从数据库查询，查询到以后在把数据存储到Redis中去。使用RedisTemple是因为作为缓存，我们所希望的是，如果Redis宕机了，我们的业务逻辑不会有影响，而使用Spring Cache来实现的话，当Redis宕机以后，用户的登录等种种操作就会都无法进行了。

#### 5.3.2、使用AOP处理缓存操作异常

> 为什么要用AOP来解决这个问题呢？因为我们的缓存业务类`UmsAdminCacheService`已经写好了，要保证缓存业务类中的方法执行不影响正常的业务逻辑，就需要在所有方法中添加`try catch`逻辑。使用AOP，我们可以在一个地方写上`try catch`逻辑，然后应用到所有方法上去。试想下，我们如果又多了几个缓存业务类，只要配置下切面即可，这波操作多方便！

* 首先我们先定义一个切面，在相关缓存业务类上面应用，在它的环绕通知中直接处理掉异常，保障后续操作能执行。
* 不过并不是所有的方法都需要处理异常的，比如我们的验证码存储，如果我们的Redis宕机了，我们的验证码存储接口需要的是报错，而不是返回执行成功。
* 对于上面这种需求我们可以通过自定义注解来完成，首先我们自定义一个CacheException注解，如果方法上面有这个注解，发生异常则直接抛出。
* 接下来我们需要把`@CacheException`注解应用到存储和获取验证码的方法上去，这里需要注意的是要应用在实现类上而不是接口上，因为`isAnnotationPresent`方法只能获取到当前方法上的注解，而不能获取到它实现接口方法上的注解。

### 5.4、参数校验逻辑

> 项目中提供两种处理校验逻辑的方式。一种是使用Hibernate Validator来处理，另一种是使用全局异常来处理。

#### 5.4.1、Hibernate Validator

**常用注解**：

- @Null：被注释的属性必须为null；
- @NotNull：被注释的属性不能为null；
- @AssertTrue：被注释的属性必须为true；
- @AssertFalse：被注释的属性必须为false；
- @Min：被注释的属性必须大于等于其value值；
- @Max：被注释的属性必须小于等于其value值；
- @Size：被注释的属性必须在其min和max值之间；
- @Pattern：被注释的属性必须符合其regexp所定义的正则表达式；
- @NotBlank：被注释的字符串不能为空字符串；
- @NotEmpty：被注释的属性不能为空；
- @Email：被注释的属性必须符合邮箱格式。

**处理流程**：

* 需要先在需要校验的参数中添加校验注解，用于确定属性的校验规则及校验失败后需要返回的信息；
* 然后在接口中添加@Validated注解，并注入一个BindingResult参数；
* 然后在整个Controller层创建一个切面，在其环绕通知中获取到注入的BindingResult对象，通过hasErrors方法判断校验是否通过，如果有错误信息直接返回错误信息，验证通过则放行；

* 使用切面的话，由于每个校验方法中都需要注入`BindingResult`对象，这样会导致很多重复工作，其实当校验失败时，SpringBoot默认会抛出`MethodArgumentNotValidException`或`BindException`异常，我们只要全局处理该异常依然可以得到校验失败信息。

> **优缺点：**这种方式的优点是可以使用注解来实现参数校验，不需要一些重复的校验逻辑，但是也有一些缺点，比如需要在Controller的方法中额外注入一个BindingResult对象，只支持一些简单的校验，涉及到要查询数据库的校验就无法满足了。

#### 5.4.2、全局异常处理

> 使用全局异常处理来处理校验逻辑的思路很简单，首先我们需要通过@ControllerAdvice注解定义一个全局异常的处理类，然后自定义一个校验异常，当我们在Controller中校验失败时，直接抛出该异常，这样就可以达到校验失败返回错误信息的目的了。

**使用到的注解**：

* **@ControllerAdvice**：类似于@Component注解，可以指定一个组件，这个组件主要用于增强@Controller注解修饰的类的功能，比如说进行全局异常处理。

* **@ExceptionHandler**：用来修饰全局异常处理的方法，可以指定异常的类型。

**使用方式**：

* 首先我们需要自定义一个异常类`ApiException`，当我们校验失败时抛出该异常。
* 然后创建一个断言处理类`Asserts`，用于抛出各种`ApiException`；
* 然后再创建我们的全局异常处理类`GlobalExceptionHandler`，用于处理全局异常，并返回封装好的CommonResult对象；

>**优缺点：**使用全局异常来处理校验逻辑的优点是比较灵活，可以处理复杂的校验逻辑。缺点是我们需要重复编写校验代码，不像使用Hibernate Validator那样只要使用注解就可以了。不过我们可以在上面的`Asserts`类中添加一些工具方法来增强它的功能，比如判断是否为空和判断长度等都可以自己实现。

我们可以两种方法一起结合使用，比如简单的参数校验使用Hibernate Validator来实现，而一些涉及到数据库操作的复杂校验使用全局异常处理的方式来实现。

### 5.5、基于Redis实现高并发访问场景的开发

#### 5.5.1、Redis存储JSON格式数据

> 让Redis存储的标准的JSON格式数据有利于我们接下来的数据处理，由于不设置过期时间容易产生很多不必要的缓存数据，所以我们还需要设置一定的过期时间。

* 我们可以通过给RedisTemplate设置JSON格式的序列化器，并通过配置RedisCacheConfiguration设置超时时间，此时别忘了去除启动类上的@EnableCaching注解。

#### 5.5.2、Redis连接池

##### Jedis vs Lettuce

* Jedis在实现上是直连Redis服务，多线程环境下非线程安全，除非使用连接池，为每个 RedisConnection 实例增加物理连接。

* Lettuce是一种可伸缩，线程安全，完全非阻塞的Redis客户端，多个线程可以共享一个RedisConnection，它利用Netty NIO框架来高效地管理多个连接，从而提供了异步和同步数据访问方式，用于构建非阻塞的反应性应用程序。

#### 5.5.3、自由操作Redis

> Spring Cache给我们提供了操作Redis缓存的便捷方法，但是也有很多局限性。比如说我们想单独设置一个缓存值的有效期怎么办？我们并不想缓存方法的返回值，我们想缓存方法中产生的中间值怎么办？此时我们就需要用到RedisTemplate这个类了，接下来我们来讲下如何通过RedisTemplate来自由操作Redis中的缓存。

### 5.6、基于RabbitMQ实现延迟消息业务场景

#### 5.6.1、业务场景：

- 用户进行下单操作（会有锁定商品库存、使用优惠券、积分一系列的操作）；
- 生成订单，获取订单的id；
- 获取到设置的订单超时时间（假设设置的为60分钟不支付取消订单）；
- 按订单超时时间发送一个延迟消息给RabbitMQ，让它在订单超时后触发取消订单的操作；
- 如果用户没有支付，进行取消订单操作（释放锁定商品库存、返还优惠券、返回积分一系列操作）。

用户在进行下单操作时，会伴随着锁定商品库存、使用优惠券、使用积分抵扣等操作，下单完成后，获取到订单id和设置的订单超时时间，然后按照订单超时时间向rabbitmq发送一条延迟消息，让其在超时后触发自动取消订单操作，如果用户没有在指定时间内支付，就会执行释放锁定商品库存、返还优惠券、返还积分等一系列取消订单的操作。

#### 5.6.2、实现流程

* 添加消息队列的枚举配置类QueueEnum，用于延迟消息队列及处理取消订单消息队列的常量定义，包括交换机名称、队列名称、路由键名称；
* 添加RabbitMQ的Java配置，用于配置交换机、队列及队列与交换机的绑定关系；
* 交换机及队列说明如下： 
  * mall.order.direct（取消订单消息队列所绑定的交换机）:绑定的队列为`mall.order.cancel`，一旦有消息以`mall.order.cancel`为路由键发过来，会发送到此队列。
  * mall.order.direct.ttl（订单延迟消息队列所绑定的交换机）:绑定的队列为`mall.order.cancel.ttl`，一旦有消息以`mall.order.cancel.ttl`为路由键发送过来，会转发到此队列，并在此队列保存一定时间，等到超时后会自动将消息发送到`mall.order.cancel`（取消订单消息消费队列）。
* 添加延迟消息的发送者CancelOrderSender，用于向订单延迟消息队列（mall.order.cancel.ttl）里发送消息； 
* 添加取消订单消息的接收者CancelOrderReceiver，用于从取消订单的消息队列（mall.order.cancel）里接收消息；

首先配置消息队列的枚举配置类，配置延迟消息队列和取消消息队列中的常量定义，包括交换机的名称、队列的名称和路由键的名称，然后配置rabbitmq的配置类，定义队列和交换机的绑定关系，项目中使用了两个direct类型的交换机和两个消息队列，一个是和延迟消息队列绑定的交换机，当消息以对应的路由键发送过来时，会被存储到延迟消息队列中，另一个时和取消订单消息队列绑定的交换机，当消息以对应的路由键发送过来时，会被存储到取消订单消息队列中。此外还需要定义一个用于向延迟消息队列发送延迟消息的发送者和一个用于从取消订单消息队列中接收消息的接收者，最后系统需要定时扫描用户 超时未支付的订单，然后进行取消操作。

### 5.7、Elasticsearch和ELK

#### 5.7.1、Elasticsearch

> Spring Data Elasticsearch是Spring提供的一种以Spring Data风格来操作数据存储的方式，它可以避免编写大量的样板代码。

**常用的注解类型：**

| 注解名称       | 作用                                              | 参数说明                                                     |
| -------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| [@Document ]() | 用于标识映射到Elasticsearch文档上的领域对象       | indexName：索引库的名字，MySQL中数据库的概念                 |
| [@Setting ]()  | ES的配置注解                                      | shards：默认分片数 replicas：默认副本数量                    |
| @Id            | 用于标识文档的ID，文档可以认为是MySQL中表行的概念 | 无参数                                                       |
| [@Field ]()    | 用于标识文档中的字段，可以认为是MySQL中列的概念   | type：文档中字段的类型 index：是否建立倒排索引 store：是否进行存储 analyzer：分词器的名称 |

**Spring Data方式的数据操作：**

* 继承ElasticsearchRepository接口可以获得常用的数据操作方法

* 可以使用衍生查询，在接口中直接指定查询方法名称便可查询，无需进行实现，如商品表中有商品名称、标题和关键字，直接定义以下查询，就可以对这三个字段进行全文搜索。

  ```java
  /**
   * @auther macrozheng
   * @description 商品ES操作类
   * @date 2018/6/19
   * @github https://github.com/macrozheng
   */
  public interface EsProductRepository extends ElasticsearchRepository<EsProduct, Long> {
      /**
       * 搜索查询
       *
       * @param name              商品名称
       * @param subTitle          商品标题
       * @param keywords          商品关键字
       * @param page              分页信息
       * @return
       */
      Page<EsProduct> findByNameOrSubTitleOrKeywords(String name, String subTitle, String keywords, Pageable page);
  }
  ```

* 通过`@Query`注解可以使用Elasticsearch的原生DSL语句进行查询

#### 5.7.2、实现流程

以商品搜索为例：

* 添加商品文档对象`EsProduct`，不需要中文分词的字段设置成`Keyword`类型，需要中文分词的设置成`Text`类型，并设置分词器为`ik_max_word`；
* 继承ElasticsearchRepository接口，这样就拥有了一些基本的Elasticsearch数据操作方法，同时定义了一个衍生查询方法（根据商品名称、商品标题和商品关键字进行衍生查询）；
* 在进行查询之前，首先需要将数据导入到ES中，然后才能进行查询操作

#### 5.7.3、ELK日志收集

日志收集系统的原理是这样的，首先应用集成了Logstash插件，通过TCP向Logstash传输日志。Logstash接收到日志后根据日志类型将日志存储到Elasticsearch的不同索引上去，Kibana从Elasticsearch中读取日志，然后我们就可以在Kibana中进行可视化日志分析了，具体流程图如下。

![image-20240425144254857](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240425144254857.png)

这里把日志分成了如下四种类型，方便查看：

- 调试日志（mall-debug）：所有的DEBUG级别以上日志。
- 错误日志（mall-error）：所有的ERROR级别日志。
- 业务日志（mall-business）：`com.macro.mall`包下的所有DEBUG级别以上日志，包含MyBatis打印的SQL日志。
- 记录日志（mall-record）：`com.macro.mall.tiny.component.WebLogAspect`类下所有DEBUG级别以上日志，该类是统计接口访问信息的AOP切面类。

### 5.8、使用MongoDB实现前台商城用户大数据量的存储

> 和Spring Data Elasticsearch类似，Spring Data Mongodb是Spring提供的一种以Spring Data风格来操作数据存储的方式，它可以避免编写大量的样板代码。

#### 5.8.1、MongoDB

**常用注解：**

| 名称           | 作用                              |
| -------------- | --------------------------------- |
| [@Document ]() | 标示映射到MongoDB文档上的领域对象 |
| @Id            | 标示某个字段为ID域                |
| [@Indexed ]()  | 标示某个字段为MongoDB的索引字段   |

**Spring Data方式的数据操作：**

* 可以使用衍生查询，在接口中直接指定查询方法名称，无需进行实现即可查询
* 在编写衍生查询方法时，IDEA会提示对应字段，更多关键字可以参考`衍生查询关键字对照表`；
* 使用`@Query`注解可以用MongoDB的JSON查询语句进行查询。

#### 5.8.2、实现流程

**项目中涉及到适用MongoDB存储数据的业务：**

* 会员品牌关注
* 会员商品收藏
* 会员浏览记录

以存储用户浏览记录为例：

- 添加会员浏览记录文档对象MemberReadHistory，文档对象的ID域添加@Id注解，需要检索的字段添加@Indexed注解；
- 添加MemberReadHistoryRepository接口用于操作MongoDB，继承MongoRepository接口，这样就拥有了一些基本的数据操作方法，同时定义了一个衍生查询方法（根据会员id按时间倒序获取浏览记录）；

### 5.9、MinIO文件存储

#### 5.9.1、MinIO

> MinIO 是一个开源的对象存储服务器。这意味着它允许你在互联网上存储大量数据，比如文件、图片、视频等，而不需要依赖传统的文件系统。MinIO 的特点在于它非常灵活、易于使用，同时也非常强大，可以在你的应用程序中方便地集成。

**MinIO的优势：**

- **可伸缩性和性能：** MinIO 允许你在需要时轻松地扩展存储容量，无需中断服务。它具有出色的性能，可以处理大量的并发读取和写入请求。
- **开源和自由：** MinIO 是开源软件，遵循 Apache License 2.0 许可证，这意味着你可以自由地使用、修改和分发它。
- **容器化部署：** MinIO 提供了容器化部署的支持，可以在各种平台上快速部署和运行，包括本地开发机、云服务器和容器编排环境（如 Docker）。
- **兼容性：** MinIO 提供了 S3 兼容的 API，这意味着它可以与任何兼容 Amazon S3 的应用程序无缝集成，为你的应用程序提供强大的对象存储能力。
- **易用性：** MinIO 的配置和管理非常简单，它提供了直观的Web控制台和命令行工具，帮助你方便地管理存储桶和对象。

#### 5.9.2、实现流程

**文件上传流程：**

![image-20240425152104689](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240425152104689.png)

首先，前端vue应用上传文件至SpringBoot应用中，然后SpringBoot应用接收文件，并判断存储桶是否存在，如果存在，则按照日期+文件名的格式设置存储对象的名称，否则需要线创建存储桶并为存储桶设置只读权限，设置完存储对象名称之后，再将文件存储到MinIO服务中。

- 修改`application.yml`配置文件，在SpringBoot中开启文件上传功能，并添加MinIO客户端配置。

  ```yml
  spring:
    servlet:
      multipart:
        enabled: true #开 启文件上传
        max-file-size: 10MB # 限制文件上传大小为10M
  minio:
    endpoint: http://localhost:9000 # MinIO服务所在地址
    bucketName: mall # 存储桶名称
    accessKey: minioadmin # 访问的key
    secretKey: minioadmin # 访问的秘钥
  ```

### 5.10、Docker容器化部署

#### 5.10.1、docker基础命令

```bash
systemctl start docker启动docker
systemctl stop docker关闭docker
systemctl restart docker重启docker
systemctl enable dockerdocker设置随服务启动而自启动
systemctl status docker查看docker 运行状态
docker version
docker info查看docker 版本号信息
docker --help docker 帮助命令
```

#### 5.10.2、docker镜像命令

```bash
docker search 镜像id或name：在Docker Hub（或其他镜像仓库如阿里镜像）仓库中搜索关键字的镜像
docker pull 镜像id或name：从仓库中下载镜像，若要指定版本，则要在冒号后指定
docker images：列出已经下载的镜像，查看镜像
docker rmi 镜像id或name：删除本地镜像
docker rmi -f 镜像id或name: 删除镜像
docker build：构建镜像
```

#### 5.10.3、docker容器命令

```shell
docker ps：列出运行中的容器
docker ps -a ： 查看所有容器，包括未运行
docker stop 容器id或name：停止容器
docker kill 容器id：强制停止容器
docker start 容器id或name：启动已停止的容器
docker inspect 容器id：查看容器的所有信息
docker container logs 容器id：查看容器日志
docker top 容器id：查看容器里的进程
docker exec -it 容器id /bin/bash：进入容器
exit：退出容器
docker rm 容器id或name：删除已停止的容器
docker rm -f 容器id：删除正在运行的容器
docker exec -it 容器ID sh :进入容器
```

首页门户中查询推荐商品、秒杀商品、热门商品等，商品模块，需要查询商品的详情以及各种优惠券，查询时可以将接口中的串行调用改为并行调用

在新增订单、修改订单、查询订单等操作。然后因为订单是不能重复的，所以当时在新增订单的时候做了幂等性校验，做法就是在新增订单记录之前，先通过 `select ... for update` 语句查询订单是否存在，如果不存在才插入订单记录。

而正是因为这样的操作，当业务量很大的时候，就可能会出现死锁。

# 十七、WebLog

>**项目简介**：WebLog博客系统，不仅为用户提供了优质的阅读体验，还为博主提供了便捷的文章管理和博客设置功能。无论是在前台浏览博客、查找感兴趣的文章，还是在后台管理系统中编辑和管理博客内容，用户都能够享受到简洁高效的操作界面和流畅的使用体验。
>
>**核心技术**：SpringBoot、MyBatisPlus、SpringSecurity、Guava、Elasticsearch、MinIO
>
>**业务描述**：
>
>* 文章管理：整合MarkDown编辑器实现文章发布和更新，用户可以发布、编辑和删除文章，并且可以对文章进行分类和标签。
>* 分类与标签：文章可以根据内容进行分类和打标签，便于用户快速查找文章。管理员负责对现有的分类和标签进行编辑和删除。
>* 知识库：除了普通的文章，网站还提供了知识库模块，用户可以在这里分享知识、技巧、经验等内容，形成一个共享的学习资源池。
>* 评论功能：用户可以对文章提出自己的看法和观点并进行讨论。评论功能可以促进用户之间的交流和互动，增强网站的社区氛围。

>WebLog博客系统项目，为用户提供了优质的阅读体验，同时为博主提供了便捷的文章管理和博客设置功能。项目采用SpringBoot、MyBatisPlus等核心技术。前台用户可以通过简洁高效的界面浏览博客和查找感兴趣的文章，后台博主可以进行文章的发布、编辑、删除和分类标签管理。此外，还实现了知识库和评论功能，方便用户分享知识和技巧。项目同样也支持搜索和文件存储功能，并通过Guava优化系统性能。这两个项目让我在前后端开发和系统性能提升方面积累了丰富经验。

## 1、模块组成

* 前台博客系统：首页文章展示、文章分类、文章标签、文章归档、系统知识库

* 后台管理系统：
  * 系统仪表盘：文章数、分类数、标签数、总浏览量、近半年文章发布热点图、一周PV访问量
  * 文章管理：文章查询、文章编辑、文章删除、文章发布
  * 分类管理：分类查询、分类新增、分类删除
  * 标签管理：标签查询、标签新增、标签删除
  * 知识库管理：知识库查询、知识库编辑、知识库删除、知识库发布
  * 评论管理：评论查询、评论删除
  * 博客设置：基础信息设置

## 2、数据表分析

共13张数据表。

* t_article：文章表
* t_article_category_rel：文章所属分类关联表
* t_article_content：文章内容表
* t_article_tag_rel：文章对应标签关联表
* t_blog_settings：博客设置表
* t_category：文章分类表
* t_comment：评论表
* t_statistics_article_pv：统计表：文章PV访问量
* t_tag：文章标签表
* t_user：用户表
* t_user_role：用户角色表
* t_wiki：知识库表
* t_wiki_catalog：知识库目录表

## 3、业务分析



## 4、技术要点分析

### 4.1、SpringSecurity整合JWT

#### 4.1.1、SpringSecurity

> Spring Security 是一个广泛应用于 Java 应用程序的安全框架，旨在保护应用程序免受潜在的安全威胁和攻击。作为 Spring 框架的一部分，Spring Security 提供了强大的功能，帮助开发人员实现身份认证、授权、会话管理以及其他与安全相关的任务。

**为什么要使用 Spring Security？**

- **应用程序保护：** 在当今互联网时代，应用程序安全性至关重要。Spring Security 提供了一系列的安全特性，帮助您保护应用程序免受恶意攻击，确保数据和功能不会被未经授权的用户访问。
- **一站式解决方案：** Spring Security 提供了一个集中的框架来处理各种安全性问题。从用户认证、授权到会话管理，Spring Security 提供了一个一站式的解决方案，使开发人员能够更容易地处理安全问题。
- **多样的认证和授权方式：** Spring Security 允许您以多种方式进行用户认证，包括基本认证、表单认证、OAuth 等。此外，您还可以定义精细的授权规则，确保只有经过授权的用户才能访问特定资源。
- **与 Spring 集成：** Spring Security 可与其他 Spring 项目无缝集成，如 Spring Boot、Spring MVC 等。这使得您可以轻松地将安全性集成到现有的 Spring 应用程序中。
- **高度可定制：** Spring Security 允许您根据应用程序的特定需求进行定制。您可以创建自定义的认证提供者、访问决策器、过滤器等，以适应不同的安全性要求。
- **丰富的社区和文档：** Spring Security 拥有活跃的社区和丰富的文档。您可以在社区中找到许多教程、示例代码和解决方案，以帮助您解决各种安全性问题。
- **符合标准：** Spring Security 符合各种安全性标准和最佳实践，确保您的应用程序满足行业和法规的要求。

**整合SpringSecurity：**

要更好地控制 Spring Security 的行为，你可以创建一个自定义的 `SecurityConfig` 类，继承自 `WebSecurityConfigurerAdapter`。通过覆盖方法，您可以配置认证、授权规则、自定义登录页面、注销等。本项目中创建一个WebSecurityConfig配置类来自定义SpringSecurity配置。

#### 4.1.2、Spring Security 整合 JWT ：实现身份认证

> JWT（JSON Web Token）是一种用于在不同应用之间安全传输信息的开放标准（RFC 7519）。它是一种基于 JSON 的轻量级令牌，由三部分组成：头部（Header）、载荷（Payload）和签名（Signature）。JWT 被广泛用于实现身份验证和授权，**特别适用于前后端分离的应用程序**。

**为什么要使用 JWT？**

JWT 提供了一种在客户端和服务器之间传输安全信息的简单方法，具有以下优点：

- **无状态性（Stateless）**：JWT 本身包含了所有必要的信息，无需在服务器端存储会话信息，每个请求都可以独立验证。
- **灵活性**：JWT 可以存储任意格式的数据，使其成为传递用户信息、权限、角色等的理想选择。
- **安全性**：JWT 使用签名进行验证，确保信息在传输过程中不被篡改。
- **跨平台和跨语言**：由于 JWT 使用 JSON 格式，它在不同的编程语言和平台之间都可以轻松传递。

**JWT实现认证和授权的原理：**

-  用户调用登录接口，登录成功后获取到JWT的token； 
-  之后用户每次调用接口都在http的header中添加一个叫Authorization的头，值为JWT的token； 
-  后台程序通过对Authorization头中信息的解码及数字签名校验来获取其中的用户信息，从而实现认证和授权。 

**实现流程：**

* 修改配置文件`application.yml`，添加JWT相关配置。包括请求头、加密密钥、过期时间和JWT负载中的开头

* 添加JWT token的工具类，用于生成和解析JWT token的工具类。

* 然后整合SpringSecurity，添加SpringSecurity的配置类；

  配置中相关方法及依赖说明如下： 

  - **filterChain(HttpSecurity httpSecurity)**：用于配置SecurityFilterChain实例，SpringSecurity的核心配置类，可以SpringSecurity进行路径授权配置、过滤器配置等；
  - **RestfulAccessDeniedHandler**：当用户没有访问权限时的处理器，用于返回JSON格式的处理结果；
  - **RestAuthenticationEntryPoint**：当未登录或token失效时，返回JSON格式的结果；
  - **UserDetailsService**：SpringSecurity定义的核心接口，用于根据用户名获取用户信息，需要自行实现；
  - **UserDetails**：SpringSecurity定义用于封装用户信息的类（主要是用户信息和权限），需要自行实现；
  - **PasswordEncoder**：SpringSecurity定义的用于对密码进行编码及比对的接口，目前使用的是BCryptPasswordEncoder；
  - JwtAuthenticationTokenFilter：在用户名和密码校验前添加的过滤器，如果有jwt的token，会自行根据token信息进行登录。

### 4.2、@Scheduled 定时任务 + 事件发布订阅，统计当日 PV 访问量

> Spring Boot 定时任务是一种机制，允许您在应用程序中执行预定的任务或操作，而无需手动触发。这些任务可以是周期性的、定时的，或者基于特定的触发条件执行。Spring Boot 内部提供了`@Scheduled`注解，使得创建和管理定时任务变得非常简单。

**为什么需要定时任务？**

1. **自动化任务执行：** 定时任务允许您在预定的时间间隔内执行任务，而无需手动触发。这对于需要按照规律执行某些操作的场景非常有用，例如定期清理日志、生成报告等。
2. **定时数据处理：** 在某些应用中，需要定期处理数据，例如更新缓存、同步数据等。定时任务可以确保这些处理在规定的时间内自动完成。
3. **后台任务处理：** 有些任务可能是一些较为耗时的后台操作，例如数据备份、邮件发送等。通过定时任务，您可以将这些操作分散到不同的时间段，避免影响应用程序的实时性能。
4. **周期性报告生成：** 如果您的应用需要生成周期性报告，例如每日、每周或每月的报告，定时任务是一个很好的选择。

实现流程：

* 开启 Spring Boot 内置提供的定时任务，仅需添加在启动类上添加 `@EnableScheduling` 注解即可。
* 创建`InitPVRecordScheduledTask` 初始化次日文章访问量记录的任务类：
  * 通过 `@Scheduled(cron = "0 0 23 * * ?")` 注解来指定定时任务的 `cron` 执行表达式，`0 0 23 * * ?` 代表每晚 23 点执行一次定时任务，逻辑也比较简单，拿到当天的日期，并通过 `plusDays(1)` 方法获取第二天的日期，然后组装 `DO` 实体类，执行 `insert()` 方法插入 `pv_date` 字段为次日的记录。
* 统计表中有了记录后，还需要在 `StatisticsArticlePVMapper` 接口中，封装一个 *对指定日期的文章 PV 访问量进行 +1* 的方法，方便后续业务中直接调用。
* 前置工作都完成后，我们对文章阅读事件进行消费，编辑 `ReadArticleSubscriber` 事件订阅类，在逻辑代码的最后，添加对*当日文章 PV 访问量 +1*的逻辑代码。

### 4.3、前后端分离解决跨域问题

> 这里采用的是在前端采用的跨域解决方案

在`vite.config.js`中添加：

```js
export default defineConfig({
  server: {
    proxy: {
      '/api': {
        target: 'http://localhost:8080',
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, ''),
      },
    }
  },
})
```

在target中声明后端的域名，然后开启changeOrigin，假如前端发起请求的baseUrl应该是`http://localhost:5173/api`，那么当前端请求后端`http://localhost:8080`时，那么你发起的请求应该是下面的样子：

```url
http://localhost:5173/api/userlist
```

这样前端就是从相同的host 并且相同的port发起的请求，代理通过前缀"/api"匹配的你要转发的请求，转发到`http://localhost:8080`真正的后端服务，并且把多余的前缀给你替换掉。

# 十八、设计模式

## 1、单例模式

单例模式（Singleton），目的是为了保证在一个进程中，某个类有且仅有一个实例。

由于这个类只有一个实例，所以不能让调用方使用`new Xxx()`来创建实例。所以，单例的构造方法必须是`private`，这样就防止了调用方自己创建实例。

单例模式的实现需要**三个必要的条件**：

1. 单例类的**构造函数**必须是**私有的**，这样才能将类的创建权控制在类的内部，从而使得类的外部不能创建类的实例。
2. 单例类通过一个**私有的静态变量**来存储其唯一实例。
3. 单例类通过提供一个**公开的静态方法**，使得外部使用者可以访问类的唯一实例。

另外，实现单例类时，还需要考虑三个问题：

- 创建单例对象时，是否**线程安全**。
- 单例对象的创建，是否**延时加载**。
- 获取单例对象时，是否需要**加锁**。

### 1.1、饿汉模式

JVM在类的初始化阶段，会执行类的静态方法。在执行类的初始化期间，JVM会去获取Class对象的锁。这个锁可以同步多个线程对同一个类的初始化。

饿汉模式只在类加载的时候创建一次实例，没有多线程同步的问题。单例没有用到也会被创建，而且在类加载之后就被创建，内存就被浪费了。

```java
public class Singleton {  
    private static Singleton instance = new Singleton();  
    private Singleton() {}  
    public static Singleton newInstance() {
        return instance;  
    }  
}
```

饿汉式单例的**优点**：

- 单例对象的创建是**线程安全**的；
- 获取单例对象时**不需要加锁**。

饿汉式单例的**缺点**：单例对象的创建，不是**延时加载**。

### 1.2、懒汉式

与饿汉式思想不同，懒汉式支持延时加载，将对象的创建延迟到了获取对象的时候。不过为了线程安全，在获取对象的操作需要加锁，这就导致了低性能。

```java
public class Singleton { 
  private static final Singleton instance;
  
  private Singleton () {}
  
  public static synchronized Singleton getInstance() {    
    if (instance == null) {      
      instance = new Singleton();    
    }    

    return instance;  
  }
}
```

上述代码加的锁只有在第一次创建对象时有用，而之后每次获取对象，其实是不需要加锁的（双重检查锁定优化了这个问题）。

懒汉式单例**优点**：

- 对象的创建是线程安全的。
- 支持延时加载。

懒汉式单例**缺点**：

- 获取对象的操作被加上了锁，影响了并发性能。

### 1.3、双重检查锁定

双重检查锁定将懒汉式中的 `synchronized` 方法改成了 `synchronized` 代码块。如下：

```text
public class Singleton {  
    private static volatile Singleton instance = null;  //volatile
    private Singleton(){}  
    public static Singleton getInstance() {  
        if (instance == null) {  
            synchronized (Singleton.class) {  
                if (instance == null) {
                    instance = new Singleton();  
                }  
            }  
        }  
        return instance;  
    }  
}  
```

双重校验锁先判断 instance 是否已经被实例化，如果没有被实例化，那么才对实例化语句进行加锁。

instance使用static修饰的原因：getInstance为静态方法，因为静态方法的内部不能直接使用非静态变量，只有静态成员才能在没有创建对象时进行初始化，所以返回的这个实例必须是静态的。

为什么两次判断`instance == null`：

| Time | Thread A             | Thread B             |
| ---- | -------------------- | -------------------- |
| T1   | 检查到`instance`为空 |                      |
| T2   |                      | 检查到`instance`为空 |
| T3   |                      | 初始化对象`A`        |
| T4   |                      | 返回对象`A`          |
| T5   | 初始化对象`B`        |                      |
| T6   | 返回对象`B`          |                      |

`new Singleton()`会执行三个动作：分配内存空间、初始化对象和对象引用指向内存地址。

```java
memory = allocate();　　// 1：分配对象的内存空间
ctorInstance(memory);　 // 2：初始化对象
instance = memory;　　  // 3：设置instance指向刚分配的内存地址
```

由于指令重排优化的存在，导致初始化对象和将对象引用指向内存地址的顺序是不确定的。在某个线程创建单例对象时，会为该对象分配了内存空间并将对象的字段设置为默认值。此时就可以将分配的内存地址赋值给instance字段了，然而该对象可能还没有初始化。若紧接着另外一个线程来调用getInstance，取到的是未初始化的对象，程序就会出错。volatile 可以禁止指令重排序，保证了先初始化对象再赋值给instance变量。

| Time | Thread A                 | Thread B                                 |
| :--- | :----------------------- | :--------------------------------------- |
| T1   | 检查到`instance`为空     |                                          |
| T2   | 获取锁                   |                                          |
| T3   | 再次检查到`instance`为空 |                                          |
| T4   | 为`instance`分配内存空间 |                                          |
| T5   | 将`instance`指向内存空间 |                                          |
| T6   |                          | 检查到`instance`不为空                   |
| T7   |                          | 访问`instance`（此时对象还未完成初始化） |
| T8   | 初始化`instance`         |                                          |

双重检查锁定单例**优点**：

- 对象的创建是线程安全的。
- 支持延时加载。
- 获取对象时不需要加锁。

### 1.4、静态内部类

它与饿汉模式一样，也是利用了类初始化机制，因此不存在多线程并发的问题。不一样的是，它是在内部类里面去创建对象实例。这样的话，只要应用中不使用内部类，JVM就不会去加载这个单例类，也就不会创建单例对象，从而实现懒汉式的延迟加载。也就是说这种方式可以同时保证延迟加载和线程安全。

基于类初始化的方案的实现代码更简洁。

```text
public class Instance {
    private static class InstanceHolder {
        public static Instance instance = new Instance();
    }
    private Instance() {}
    public static Instance getInstance() {
        return InstanceHolder.instance ;　　// 这里将导致InstanceHolder类被初始化
    }
}
```

如上述代码，`InstanceHolder` 是一个静态内部类，当外部类 `Instance` 被加载的时候，并不会创建 `InstanceHolder` 实例对象。

只有当调用 `getInstance()` 方法时，`InstanceHolder` 才会被加载，这个时候才会创建 `Instance`。`Instance` 的唯一性、创建过程的线程安全性，都由 JVM 来保证。

静态内部类单例**优点**：

- 对象的创建是线程安全的。
- 支持延时加载。
- 获取对象时不需要加锁。

### 1.5、枚举

用枚举来实现单例，是最简单的方式。这种实现方式通过 **Java 枚举**类型本身的特性，保证了实例创建的线程安全性和实例的唯一性。

```java
public enum Singleton {
  INSTANCE; // 该对象全局唯一
}
```

## 2、工厂模式

工厂模式是用来封装对象的创建。工厂模式有三种，它们分别是简单工厂模式，工厂方法模式以及抽象工厂模式，通常我们所说的工厂模式指的是工厂方法模式。

下面分别介绍下这三种工厂模式。

### 2.1、简单工厂模式

简单工厂模式的定义：定义一个工厂类，根据传入的参数不同返回不同的实例，被创建的实例具有共同的父类或接口。

由于只有一个工厂类，所以工厂类中创建的对象不能太多，否则工厂类的业务逻辑就太复杂了，其次由于工厂类封装了对象的创建过程，所以客户端应该不关心对象的创建。

适用场景：

（1）需要创建的对象较少。

（2）客户端不关心对象的创建过程。

下面看一个具体的实例。

创建一个可以绘制不同形状的绘图工具，可以绘制圆形，正方形，三角形，每个图形都会有一个draw()方法用于绘图。

```java
public interface Shape {
    void draw();
}
```

编写具体的图形，每种图形都实现Shape 接口。

```java
public class CircleShape implements Shape {

    public CircleShape() {
        System.out.println(  "CircleShape: created");
    }

    @Override
    public void draw() {
        System.out.println(  "draw: CircleShape");
    }

}

public class RectShape implements Shape {
    public RectShape() {
       System.out.println(  "RectShape: created");
    }

    @Override
    public void draw() {
       System.out.println(  "draw: RectShape");
    }

}
...
```

工厂类的具体实现：

```java
 public class ShapeFactory {
          public static final String TAG = "ShapeFactory";
          public static Shape getShape(String type) {
              Shape shape = null;
              if (type.equalsIgnoreCase("circle")) {
                  shape = new CircleShape();
              } else if (type.equalsIgnoreCase("rect")) {
                  shape = new RectShape();
              } else if (type.equalsIgnoreCase("triangle")) {
                  shape = new TriangleShape();
              }
              return shape;
          }
   }
```

在这个工厂类中通过传入不同的type可以new不同的形状，返回结果为Shape 类型，这个就是简单工厂核心的地方了。

客户端使用：

```java
Shape shape= ShapeFactory.getShape("circle");
shape.draw();
```

通过给ShapeFactory传入不同的参数就实现了各种形状的绘制。

简单工厂模式的**优点**：只需要一个工厂创建对象，代码量少。

简单工厂模式的**缺点**：系统扩展困难，新增产品需要修改工厂逻辑，当产品较多时，会造成工厂逻辑过于复杂，不利于系统扩展和维护。

### 2.2、工厂方法模式

工厂方法模式是简单工厂的仅一步深化， 在工厂方法模式中，我们不再提供一个统一的工厂类来创建所有的对象，而是针对不同的对象提供不同的工厂。每个对象都有一个与之对应的工厂。

下面看一个具体的实例。

设计一个这样的图片加载类，它具有多个图片加载器，用来加载jpg，png，gif格式的图片，每个加载器都有一个read方法，用于读取图片。

首先完成图片加载器的设计，编写一个加载器的公共接口。

```java
public interface Reader {
    void read();
}
```

各个图片加载器的实现如下：

```java
public class JpgReader implements Reader {
    @Override
    public void read() {
        System.out.print("read jpg");
    }
}

public class PngReader implements Reader {
    @Override
    public void read() {
        System.out.print("read png");
    }
}
```

定义一个抽象的工厂接口ReaderFactory，通过getReader()方法返回我们的Reader 类。

```java
public interface ReaderFactory {
    Reader getReader();
}
```

为每个图片加载器都提供一个工厂类，这些工厂类实现了ReaderFactory 。

```java
public class JpgReaderFactory implements ReaderFactory {
    @Override
    public Reader getReader() {
        return new JpgReader();
    }
}

public class PngReaderFactory implements ReaderFactory {
    @Override
    public Reader getReader() {
        return new PngReader();
    }
}

public class GifReaderFactory implements ReaderFactory {
    @Override
    public Reader getReader() {
        return new GifReader();
    }
}
```

客户端通过子类来指定创建对应的对象。

```java
ReaderFactory factory=new JpgReaderFactory();
Reader  reader=factory.getReader();
reader.read();
```

和简单工厂对比一下，最根本的区别在于，简单工厂只有一个统一的工厂类，而工厂方法是针对每个要创建的对象都会提供一个工厂类，这些工厂类都实现了一个工厂基类（本例中的ReaderFactory ）。

优点：增加新的产品类时无须修改现有系统，只需增加新产品和对应的工厂类即可。

### 2.3、抽象工厂模式

抽象工厂模式创建的是对象家族，也就是很多对象而不是一个对象，并且这些对象是相关的，也就是说必须一起创建出来。而工厂方法模式只是用于创建一个对象，这和抽象工厂模式有很大不同。

下面举一个实例帮助大家理解。

现在需要做一款跨平台的游戏，需要兼容Android，IOS两个移动操作系统，该游戏针对每个系统都设计了一套操作控制器（OperationController）和界面控制器（UIController），下面通过抽象工厂模式完成这款游戏的架构设计。

新建两个抽象产品接口。

```java
//抽象操作控制器
public interface OperationController {
    void control();
}

//抽象界面控制器
public interface UIController {
    void display();
}
```

然后完成这两个系统平台的具体操作控制器和界面控制器。

```java
//Android
public class AndroidOperationController implements OperationController {
    @Override
    public void control() {
        System.out.println("AndroidOperationController");
    }
}

public class AndroidUIController implements UIController {
    @Override
    public void display() {
        System.out.println("AndroidInterfaceController");
    }
}


//IOS
public class IosOperationController implements OperationController {
    @Override
    public void control() {
        System.out.println("IosOperationController");
    }
}

public class IosUIController implements UIController {
    @Override
    public void display() {
        System.out.println("IosInterfaceController");
    }
}
```

下面定义一个抽象工厂，该工厂需要可以创建OperationController和UIController

```java
public interface SystemFactory {
    public OperationController createOperationController();
    public UIController createInterfaceController();
}
```

在各平台具体的工厂类中完成操作控制器和界面控制器的创建过程。

```java
//android
public class AndroidFactory implements SystemFactory {
    @Override
    public OperationController createOperationController() {
        return new AndroidOperationController();
    }

    @Override
    public UIController createInterfaceController() {
        return new AndroidUIController();
    }
}

//IOS
public class IosFactory implements SystemFactory {
    @Override
    public OperationController createOperationController() {
        return new IosOperationController();
    }

    @Override
    public UIController createInterfaceController() {
        return new IosUIController();
    }
}
```

客户端调用如下：

```java
SystemFactory mFactory;
UIController interfaceController;
OperationController operationController;

//Android
mFactory=new AndroidFactory();
//IOS
//mFactory=new IosFactory();

interfaceController=mFactory.createInterfaceController();
operationController=mFactory.createOperationController();
interfaceController.display();
operationController.control();
```

针对不同平台只通过创建不同的工厂对象就完成了操作和UI控制器的创建。

**适用场景：**

（1）和工厂方法一样客户端不需要知道它所创建的对象的类。

（2）需要一组对象共同完成某种功能时。并且可能存在多组对象完成不同功能的情况。

（3）系统结构稳定，不会频繁的增加对象。（因为一旦增加就需要修改原有代码，不符合开闭原则）

## 3、模板方法设计模式

模板模式：一个抽象类公开定义了执行它的方法的方式/模板。它的子类可以按需要重写方法实现，但调用将以抽象类中定义的方式进行。 这种类型的设计模式属于行为型模式。定义一个操作中的算法的骨架，而将一些步骤延迟到子类中。

**模板模式**主要由抽象模板(Abstract Template)角色和具体模板(Concrete Template)角色组成。

- 抽象模板(Abstract Template): 定义了一个或多个抽象操作，以便让子类实现。这些抽象操作叫做基本操作，它们是一个顶级逻辑的组成步骤;定义并实现了一个模板方法。这个模板方法一般是一个具体方法，它给出了一个顶级逻辑的骨架，而逻辑的组成步骤在相应的抽象操作中，推迟到子类实现。顶级逻辑也有可能调用一些具体方法。
- 具体模板(Concrete Template): 实现父类所定义的一个或多个抽象方法，它们是一个顶级逻辑的组成步骤;每一个抽象模板角色都可以有任意多个具体模板角色与之对应，而每一个具体模板角色都可以给出这些抽象方法（也就是顶级逻辑的组成步骤）的不同实现，从而使得顶级逻辑的实现各不相同。

![image-20240611212643857](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240611212643857.png)

以游戏为例。创建一个抽象类，它的模板方法被设置为 final，这样它就不会被重写。



```java
public abstract class Game {
   abstract void initialize();
   abstract void startPlay();
   abstract void endPlay();
 
   //模板
   public final void play(){
      //初始化游戏
      initialize();
 
      //开始游戏
      startPlay();
 
      //结束游戏
      endPlay();
   }
}
```

Football类：

```java
public class Football extends Game {
 
   @Override
   void endPlay() {
      System.out.println("Football Game Finished!");
   }
 
   @Override
   void initialize() {
      System.out.println("Football Game Initialized! Start playing.");
   }
 
   @Override
   void startPlay() {
      System.out.println("Football Game Started. Enjoy the game!");
   }
}
```

使用Game的模板方法 play() 来演示游戏的定义方式。

```java
public class TemplatePatternDemo {
   public static void main(String[] args) {
 
      Game game = new Cricket();
      game.play();
      System.out.println();
      game = new Football();
      game.play();      
   }
}
```

**模板模式优点** ：

1. 封装不变部分，扩展可变部分。
2. 提取公共代码，便于维护。
3. 行为由父类控制，子类实现。

**模板模式缺点**：

- 每一个不同的实现都需要一个子类来实现，导致类的个数增加，使得系统更加庞大。

## 4、策略模式

策略模式（Strategy Pattern）属于对象的行为模式。其用意是针对一组算法，将每一个算法封装到具有共同接口的独立的类中，从而使得它们可以相互替换。策略模式使得算法可以在不影响到客户端的情况下发生变化。

其主要目的是通过定义相似的算法，替换if else 语句写法，并且可以随时相互替换。

**策略模式**主要由这三个角色组成，环境角色(Context)、抽象策略角色(Strategy)和具体策略角色(ConcreteStrategy)。

- **环境角色**(Context)：持有一个策略类的引用，提供给客户端使用。
- **抽象策略角色**(Strategy)：这是一个抽象角色，通常由一个接口或抽象类实现。此角色给出所有的具体策略类所需的接口。
- **具体策略角色**(ConcreteStrategy)：包装了相关的算法或行为。

示例图如下:

![image-20240611212810059](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240611212810059.png)

以计算器为例，如果我们想得到两个数字相加的和，我们需要用到“+”符号，得到相减的差，需要用到“-”符号等等。虽然我们可以通过字符串比较使用if/else写成通用方法，但是计算的符号每次增加，我们就不得不加在原先的方法中进行增加相应的代码，如果后续计算方法增加、修改或删除，那么会使后续的维护变得困难。

但是在这些方法中，我们发现其基本方法是固定的，这时我们就可以通过策略模式来进行开发，可以有效避免通过if/else来进行判断，即使后续增加其他的计算规则也可灵活进行调整。

首先定义一个抽象策略角色，并拥有一个计算的方法。

```java
interface CalculateStrategy {
   int doOperation(int num1, int num2);
}
```

然后再定义加减乘除这些具体策略角色并实现方法。代码如下:

```java
class OperationAdd implements CalculateStrategy {
   @Override
   public int doOperation(int num1, int num2) {
   	return num1 + num2;
   }
}

class OperationSub implements CalculateStrategy {
   @Override
   public int doOperation(int num1, int num2) {
   	return num1 - num2;
   }
}

class OperationMul implements CalculateStrategy {
   @Override
   public int doOperation(int num1, int num2) {
   	return num1 * num2;
   }
}

class OperationDiv implements CalculateStrategy {
   @Override
   public int doOperation(int num1, int num2) {
   	return num1 / num2;
   }
}
```

最后在定义一个环境角色，提供一个计算的接口供客户端使用。代码如下:

```java
class  CalculatorContext {
	private CalculateStrategy strategy;

	public CalculatorContext(CalculateStrategy strategy) {
		this.strategy = strategy;
	}

	public int executeStrategy(int num1, int num2) {
		return strategy.doOperation(num1, num2);
	}
}
```

测试代码如下:

```java
public static void main(String[] args) {
  		   int a=4,b=2;
		  CalculatorContext context = new CalculatorContext(new OperationAdd());    
	      System.out.println("a + b = "+context.executeStrategy(a, b));
	 
	      CalculatorContext context2 = new CalculatorContext(new OperationSub());      
	      System.out.println("a - b = "+context2.executeStrategy(a, b));
	 
	      CalculatorContext context3 = new CalculatorContext(new OperationMul());    
	      System.out.println("a * b = "+context3.executeStrategy(a, b));
	
	      CalculatorContext context4 = new CalculatorContext(new OperationDiv());    
	      System.out.println("a / b = "+context4.executeStrategy(a, b));
}
```

**策略模式优点：**

- 扩展性好，可以在不修改对象结构的情况下，为新的算法进行添加新的类进行实现；
- 灵活性好，可以对算法进行自由切换；

**策略模式缺点：**

- 使用策略类变多，会增加系统的复杂度。；
- 客户端必须知道所有的策略类才能进行调用；

**使用场景：**

- 如果在一个系统里面有许多类，它们之间的区别仅在于它们的行为，那么使用策略模式可以动态地让一个对象在许多行为中选择一种行为； 一个系统需要动态地在几种算法中选择一种;
- 如果一个对象有很多的行为，如果不用恰当的模式，这些行为就只好使用多重的条件选择语句来实现;

## 5、责任链模式

为了避免请求发送者与多个请求处理者耦合在一起，于是将所有请求的处理者通过前一对象记住其下一个对象的引用而连成一条链；当有请求发生时，可将请求沿着这条链传递，直到有对象处理它为止。

在责任链模式中，客户只需要将请求发送到责任链上即可，无须关心请求的处理细节和请求的传递过程，请求会自动进行传递。所以责任链将请求的发送者和请求的处理者解耦了。

### 5.1、优点

**责任链模式是一种对象行为型模式，其主要优点如下。**

1. 降低了对象之间的耦合度。该模式使得一个对象无须知道到底是哪一个对象处理其请求以及链的结构，发送者和接收者也无须拥有对方的明确信息。
2. 增强了系统的可扩展性。可以根据需要增加新的请求处理类，满足开闭原则。
3. 增强了给对象指派职责的灵活性。当工作流程发生变化，可以动态地改变链内的成员或者调动它们的次序，也可动态地新增或者删除责任。
4. 责任链简化了对象之间的连接。每个对象只需保持一个指向其后继者的引用，不需保持其他所有处理者的引用，这避免了使用众多的 if 或者 if···else 语句。
5. 责任分担。每个类只需要处理自己该处理的工作，不该处理的传递给下一个对象完成，明确各类的责任范围，符合类的单一职责原则。

### 5.2、缺点

1. 不能保证每个请求一定被处理。由于一个请求没有明确的接收者，所以不能保证它一定会被处理，该请求可能一直传到链的末端都得不到处理。
2. 对比较长的职责链，请求的处理可能涉及多个处理对象，系统性能将受到一定影响。
3. 职责链建立的合理性要靠客户端来保证，增加了客户端的复杂性，可能会由于职责链的错误设置而导致系统出错，如可能会造成循环调用。

### 5.3、责任链模式的结构

1. 抽象处理者（Handler）角色：定义一个处理请求的接口，包含抽象处理方法和一个后继连接。
2. 具体处理者（Concrete Handler）角色：实现抽象处理者的处理方法，判断能否处理本次请求，如果可以处理请求则处理，否则将该请求转给它的后继者。
3. 客户类（Client）角色：创建处理链，并向链头的具体处理者对象提交请求，它不关心处理细节和请求的传递过程。

### 5.4、代码实现

比如要开发一个请假流程控制系统。请假一天以下的假只需要小组长同意即可；请假1天到3天的假还需要部门经理同意；请求3天到7天还需要总经理同意才行。

代码实现如下：

请假条类

```java
public class LeaveRequest {
    //姓名
    private String name;
    // 请假天数
    private int num;
    // 请假内容
    private String content;

    public LeaveRequest(String name, int num, String content) {
        this.name = name;
        this.num = num;
        this.content = content;
    }

    public String getName() {
        return name;
    }

    public int getNum() {
        return num;
    }

    public String getContent() {
        return content;
    }

}
```

处理类

```java
public abstract class Handler {
    protected final static int NUM_ONE = 1;
    protected final static int NUM_THREE = 3;
    protected final static int NUM_SEVEN = 7;

    //该领导处理的请假天数区间
    private int numStart;
    private int numEnd;


    //领导上还有领导
    private Handler nextHandler;

    //设置请假天数范围
    public Handler(int numStart) {
        this.numStart = numStart;
    }

    //设置请假天数范围
    public Handler(int numStart, int numEnd) {
        this.numStart = numStart;
        this.numEnd = numEnd;
    }

    //设置上级领导
    public void setNextHandler(Handler nextHandler) {
        this.nextHandler = nextHandler;
    }

    //提交请假条
    public final void submit(LeaveRequest leaveRequest) {
        if (this.numStart == 0) {
            return;
        }
        //请假天数达到领导处理要求
        if (leaveRequest.getNum() >= this.numStart) {
            this.handleLeave(leaveRequest);

            //如果还有上级 并且请假天数超过当前领导的处理范围
            if (this.nextHandler != null && leaveRequest.getNum() > numEnd) {
                //继续提交
                this.nextHandler.submit(leaveRequest);
            } else {
                System.out.println("流程结束！！！");
            }
        }
    }

    //各级领导处理请假条方法
    protected abstract void handleLeave(LeaveRequest leave);

}
```

小组长类

```java
public class GroupLeader extends Handler {
    //1-3天的假
    public GroupLeader() {
        super(Handler.NUM_ONE, Handler.NUM_THREE);
    }

    @Override
    protected void handleLeave(LeaveRequest leave) {
        System.out.println(leave.getName() + "请假" + leave.getNum() + "天，" + leave.getContent() + "!");
        System.out.println("小组长审批通过：同意！");
    }
}
```

部门经理类

```java
public class Manager extends Handler {
    //3-7天的假
    public Manager() {
        super(Handler.NUM_THREE, Handler.NUM_SEVEN);
    }

    @Override
    protected void handleLeave(LeaveRequest leave) {
        System.out.println(leave.getName() + "请假" + leave.getNum() + "天，" + leave.getContent() + "!");
        System.out.println("部门经理审批通过：同意！");
    }
}
```

总经理类

```java
public class GeneralManager extends Handler{
    //7天以上的假
    public GeneralManager() {
        super(Handler.NUM_THREE, Handler.NUM_SEVEN);
    }

    @Override
    protected void handleLeave(LeaveRequest leave) {
        System.out.println(leave.getName() + "请假" + leave.getNum() + "天，" + leave.getContent() + "!");
        System.out.println("总经理审批通过：同意！");
    }
}
```

测试类

```java
public class Client {
    public static void main(String[] args) {
        //请假条
        LeaveRequest leave = new LeaveRequest("小庄", 3, "出去旅游");

        //各位领导
        Manager manager = new Manager();
        GroupLeader groupLeader = new GroupLeader();
        GeneralManager generalManager = new GeneralManager();

        /*
         * 小组长上司是经理 经理上司是总经理
         */
        groupLeader.setNextHandler(manager);
        manager.setNextHandler(generalManager);

        //提交
        groupLeader.submit(leave);

    }
}
```

输出结果：

```java
小庄请假3天，出去旅游!
小组长审批通过: 同意!
流程结束!!!
```

### 5.5、应用场景

1. 多个对象可以处理一个请求，但具体由哪个对象处理该请求在运行时自动确定。
2. 可动态指定一组对象处理请求，或添加新的处理者。
3. 需要在不明确指定请求处理者的情况下，向多个处理者中的一个提交请求。

## 6、迭代器模式

提供一种方法顺序访问一个聚合对象中的各个元素, 而又不暴露其内部的表示。

把在元素之间游走的责任交给迭代器，而不是聚合对象。

**应用实例：**JAVA 中的 iterator。

**优点：** 1、它支持以不同的方式遍历一个聚合对象。 2、迭代器简化了聚合类。 3、在同一个聚合上可以有多个遍历。 4、在迭代器模式中，增加新的聚合类和迭代器类都很方便，无须修改原有代码。

**缺点：**由于迭代器模式将存储数据和遍历数据的职责分离，增加新的聚合类需要对应增加新的迭代器类，类的个数成对增加，这在一定程度上增加了系统的复杂性。

**使用场景：** 1、访问一个聚合对象的内容而无须暴露它的内部表示。 2、需要为聚合对象提供多种遍历方式。 3、为遍历不同的聚合结构提供一个统一的接口。

**迭代器模式在JDK中的应用**

ArrayList的遍历：

```java
Iterator<Integer> iter = null;

System.out.println("ArrayList：");
iter = arrayList.iterator();
while (iter.hasNext()) {
    System.out.print(iter.next() + "\t");
}
```

## 7、装饰器模式

装饰者模式(decorator pattern)：动态地将责任附加到对象上, 若要扩展功能, 装饰者提供了比继承更有弹性的替代方案。

装饰模式以对客户端透明的方式拓展对象的功能，客户端并不会觉得对象在装饰前和装饰后有什么不同。装饰模式可以在不创造更多子类的情况下，将对象的功能加以扩展。

比如设置FileInputStream，先用BufferedInputStream装饰它，再用自己写的LowerCaseInputStream过滤器去装饰它。

```text
InputStream in = new LowerCaseInputStream(new BufferedInputStream(new FileInputStream("test.txt")));
```

在装饰模式中的角色有：

- **抽象组件**(Component)角色：给出一个抽象接口，以规范准备接收附加责任的对象。
- **具体组件**(ConcreteComponent)角色：定义一个将要接收附加责任的类。
- **抽象装饰**(Decorator)角色：持有一个组件(Component)对象的实例，并定义一个与抽象组件接口一致的接口。
- **具体装饰**(ConcreteDecorator)角色：负责给构件对象“贴上”附加的责任。

**代码实例**

LOL、王者荣耀等类Dota游戏中，每次英雄升级都会附加一个额外技能点学习技能，这个就类似装饰模式为已有类动态附加额外的功能。

具体的英雄就是ConcreteComponent，技能栏就是装饰器Decorator，每个技能就是ConcreteDecorator。

新建一个接口：

```java
public interface Hero {
    //学习技能
    void learnSkills();
}
```

创建接口的实现类（具体英雄盲僧）：

```java
//ConcreteComponent 具体英雄盲僧
public class BlindMonk implements Hero {
    
    private String name;
    
    public BlindMonk(String name) {
        this.name = name;
    }

    @Override
    public void learnSkills() {
        System.out.println(name + "学习了以上技能！");
    }
}
```

装饰角色：

```java
//Decorator 技能栏
public abstract class Skills implements Hero {
    
    //持有一个英雄对象接口
    private Hero hero;
    
    public Skills(Hero hero) {
        this.hero = hero;
    }

    @Override
    public void learnSkills() {
        if(hero != null)
            hero.learnSkills();
    }    
}
```

具体装饰角色：

```java
//ConreteDecorator 技能：Q
public class Skill_Q extends Skills{
    
    private String skillName;

    public Skill_Q(Hero hero,String skillName) {
        super(hero);
        this.skillName = skillName;
    }

    @Override
    public void learnSkills() {
        System.out.println("学习了技能Q:" +skillName);
        super.learnSkills();
    }
}

//ConreteDecorator 技能：W
public class Skill_W extends Skills{

    private String skillName;

    public Skill_W(Hero hero,String skillName) {
        super(hero);
        this.skillName = skillName;
    }

    @Override
    public void learnSkills() {
        System.out.println("学习了技能W:" + skillName);
        super.learnSkills();
    }
}
//ConreteDecorator 技能：E
public class Skill_E extends Skills{
    
    private String skillName;
    
    public Skill_E(Hero hero,String skillName) {
        super(hero);
        this.skillName = skillName;
    }

    @Override
    public void learnSkills() {
        System.out.println("学习了技能E:"+skillName);
        super.learnSkills();
    }
}
//ConreteDecorator 技能：R
public class Skill_R extends Skills{    
    
    private String skillName;
    
    public Skill_R(Hero hero,String skillName) {
        super(hero);
        this.skillName = skillName;
    }
    
    @Override
    public void learnSkills() {
        System.out.println("学习了技能R:" +skillName );
        super.learnSkills();
    }
}
```

客户端：

```java
//客户端：召唤师
public class Player {
    public static void main(String[] args) {
        //选择英雄
        Hero hero = new BlindMonk("李青");
        
        Skills skills = new Skills(hero);
        Skills r = new Skill_R(skills,"猛龙摆尾");
        Skills e = new Skill_E(r,"天雷破/摧筋断骨");
        Skills w = new Skill_W(e,"金钟罩/铁布衫");
        Skills q = new Skill_Q(w,"天音波/回音击");
        //学习技能
        q.learnSkills();
    }
}
```

输出：

```java
学习了技能Q:天音波/回音击
学习了技能W:金钟罩/铁布衫
学习了技能E:天雷破/摧筋断骨
学习了技能R:猛龙摆尾
李青学习了以上技能！
```

## 8、适配器模式

适配器模式将现成的对象通过适配变成我们需要的接口。 适配器让原本接口不兼容的类可以合作。

适配器模式有类的适配器模式和对象的适配器模式两种不同的形式。

对象适配器模式通过组合对象进行适配。

![image-20240611214453364](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240611214453364.png)

类适配器通过继承来完成适配。

![image-20240611214504294](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240611214504294.png)

适配器模式的**优点**：

1. 更好的复用性。系统需要使用现有的类，而此类的接口不符合系统的需要。那么通过适配器模式就可以让这些功能得到更好的复用。
2. 更好的扩展性。在实现适配器功能的时候，可以调用自己开发的功能，从而自然地扩展系统的功能。

## 9、观察者模式

**观察者模式（Observer）**，又叫**发布-订阅模式（Publish/Subscribe）**，定义对象间一种一对多的依赖关系，使得每当一个对象改变状态，则所有依赖于它的对象都会得到通知并自动更新。UML结构图如下：

![image-20240611214537329](C:\Users\姜文武\AppData\Roaming\Typora\typora-user-images\image-20240611214537329.png)

其中，Subject类是主题，它把所有对观察者对象的引用文件存在了一个聚集里，每个主题都可以有任何数量的观察者。抽象主题提供了一个接口，可以增加和删除观察者对象；Observer类是抽象观察者，为所有的具体观察者定义一个接口，在得到主题的通知时更新自己；ConcreteSubject类是具体主题，将有关状态存入具体观察者对象，在具体主题内部状态改变时，给所有登记过的观察者发出通知；ConcreteObserver是具体观察者，实现抽象观察者角色所要求的更新接口，以便使本身的状态与主题的状态相协同。

### 9.1、主题Subject

首先定义一个观察者数组，并实现增、删及通知操作。它的职责很简单，就是定义谁能观察，谁不能观察，用Vector是线程同步的，比较安全，也可以使用ArrayList，是线程异步的，但不安全。

```java
public class Subject {

    //观察者数组
    private Vector<Observer> oVector = new Vector<>();

    //增加一个观察者
    public void addObserver(Observer observer) {
        this.oVector.add(observer);
    }

    //删除一个观察者
    public void deleteObserver(Observer observer) {
        this.oVector.remove(observer);
    }

    //通知所有观察者
    public void notifyObserver() {
        for(Observer observer : this.oVector) {
            observer.update();
        }
    }

}
```

### 9.2、抽象观察者Observer

观察者一般是一个接口，每一个实现该接口的实现类都是具体观察者。

```java
public interface Observer {
    //更新
    public void update();
}
```

### 9.3、具体主题

继承Subject类，在这里实现具体业务，在具体项目中，该类会有很多变种。

```java
public class ConcreteSubject extends Subject {

    //具体业务
    public void doSomething() {
        //...
        super.notifyObserver();
    }

}
```

### 9.4、具体观察者

实现Observer接口。

```java
public class ConcreteObserver implements Observer {

    @Override
    public void update() {
        System.out.println("收到消息，进行处理");
    }

}
```

### 9.5、Client客户端

首先创建一个被观察者，然后定义一个观察者，将该被观察者添加到该观察者的观察者数组中，进行测试。

```java
public class Client {

    public static void main(String[] args) {
        //创建一个主题
        ConcreteSubject subject = new ConcreteSubject();
        //定义一个观察者
        Observer observer = new ConcreteObserver();
        //观察
        subject.addObserver(observer);
        //开始活动
        subject.doSomething();
    }

}
```

运行结果如下：

```java
收到消息，进行处理
```

### 9.6、观察者模式的优点

- 观察者和被观察者是抽象耦合的
- 建立了一套触发机制

### 9.7、观察者模式的缺点

- 如果一个被观察者对象有很多的直接和间接的观察者的话，将所有的观察者都通知到会花费很多时间
- 如果观察者和观察目标间有循环依赖，可能导致系统崩溃
- 没有相应的机制让观察者知道所观察的目标对象是怎么发生变化的

### 9.8、观察者模式的使用场景

- 关联行为场景
- 事件多级触发场景
- 跨系统的消息变换场景，如消息队列的处理机制

## 10、代理模式

代理模式使用代理对象完成用户请求，屏蔽用户对真实对象的访问。

代理模式一般有三种角色：

- 抽象（Subject）角色，该角色是真实主题和代理主题的共同接口，以便在任何可以使用真实主题的地方都可以使用代理主题。
- 代理（Proxy Subject）角色，也叫做委托类、代理类，该角色负责控制对真实主题的引用，负责在需要的时候创建或删除真实主题对象，并且在真实主题角色处理完毕前后做预处理和善后处理工作。
- 真实（Real Subject）角色：该角色也叫做被委托角色、被代理角色，是业务逻辑的具体执行者。

### 10.1、静态代理

静态代理：代理类在编译阶段生成，程序运行前就已经存在，在编译阶段将通知织入Java字节码中。

以租房为例，我们一般用租房软件、找中介或者找房东。这里的中介就是代理者。

首先定义一个提供了租房方法的接口。

```java
public interface IRentHouse {
    void rentHouse();
}
```

定义租房的实现类

```java
public class RentHouse implements IRentHouse {
    @Override
    public void rentHouse() {
        System.out.println("租了一间房子。。。");
    }
}
```

我要租房，房源都在中介手中，所以找中介

```java
public class IntermediaryProxy implements IRentHouse {

    private IRentHouse rentHouse;

    public IntermediaryProxy(IRentHouse irentHouse){
        rentHouse = irentHouse;
    }

    @Override
    public void rentHouse() {
        System.out.println("交中介费");
        rentHouse.rentHouse();
        System.out.println("中介负责维修管理");
    }
}
```

这里中介也实现了租房的接口。

再main方法中测试

```java
public class Main {

    public static void main(String[] args){
        //定义租房
        IRentHouse rentHouse = new RentHouse();
        //定义中介
        IRentHouse intermediary = new IntermediaryProxy(rentHouse);
        //中介租房
        intermediary.rentHouse();
    }
}
```

返回信息

```text
交中介费
租了一间房子。。。
中介负责维修管理
```

这就是静态代理，因为中介这个代理类已经事先写好了，只负责代理租房业务。

缺点：因为代理对象需要与目标对象实现一样的接口，所以会有很多代理类。同时，一旦接口增加方法，目标对象与代理对象都要维护。

### 10.2、动态代理

动态代理：代理类在程序运行时创建，在内存中临时生成一个代理对象，在运行期间对业务方法进行增强。

**JDK动态代理**

JDK实现代理只需要使用newProxyInstance方法：

```java
static Object newProxyInstance(ClassLoader loader, Class<?>[] interfaces,   InvocationHandler h )
```

三个入参：

- ClassLoader loader：指定当前目标对象使用的类加载器
- Class<?>[] interfaces：目标对象实现的接口的类型
- InvocationHandler：当代理对象调用目标对象的方法时，会触发事件处理器的invoke方法()

还是以租房为例。

现在的中介不仅仅是有租房业务，同时还有卖房、家政、维修等得业务，只是我们就不能对每一个业务都增加一个代理，就要提供通用的代理方法，这就要通过动态代理来实现了。

中介的代理方法做了一下修改：

```java
public class IntermediaryProxy implements InvocationHandler {


    private Object obj;

    public IntermediaryProxy(Object object){
        obj = object;
    }

    /**
     * 调用被代理的方法
     * @param proxy
     * @param method
     * @param args
     * @return
     * @throws Throwable
     */
    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        Object result = method.invoke(this.obj, args);
        return result;
    }

}
```

在这里实现InvocationHandler接口，此接口是JDK提供的动态代理接口，对被代理的方法提供代理。其中invoke方法是接口InvocationHandler定义必须实现的， 它完成对真实方法的调用。动态代理是根据被代理的接口生成所有的方法，也就是说给定一个接口，动态代理就会实现接口下所有的方法。通过 InvocationHandler接口， 所有方法都由该Handler来进行处理， 即所有被代理的方法都由 InvocationHandler接管实际的处理任务。

这里增加一个卖房的业务，代码和租房代码类似。

main方法测试：

```java
public static void main(String[] args){

    IRentHouse rentHouse = new RentHouse();
    //定义一个handler
    InvocationHandler handler = new IntermediaryProxy(rentHouse);
    //获得类的class loader
    ClassLoader cl = rentHouse.getClass().getClassLoader();
    //动态产生一个代理者
    IRentHouse proxy = (IRentHouse) Proxy.newProxyInstance(cl, new Class[]{IRentHouse.class}, handler);
    proxy.rentHouse();

    ISellHouse sellHouse = new SellHouse();
    InvocationHandler handler1 = new IntermediaryProxy(sellHouse);
    ClassLoader classLoader = sellHouse.getClass().getClassLoader();
    ISellHouse proxy1 = (ISellHouse) Proxy.newProxyInstance(classLoader, new Class[]{ISellHouse.class}, handler1);
    proxy1.sellHouse();

}
```

在main方法中我们用到了Proxy这个类的方法，

```java
public static Object newProxyInstance(ClassLoader loader,
                                          Class<?>[] interfaces,
                                          InvocationHandler h)
```

InvocationHandler 是一个接口，每个代理的实例都有一个与之关联的 InvocationHandler 实现类，如果代理的方法被调用，那么代理便会通知和转发给内部的 InvocationHandler 实现类，由它决定处理。

```java
public interface InvocationHandler {

    public Object invoke(Object proxy, Method method, Object[] args)
        throws Throwable;
}
```

InvocationHandler 内部只是一个 invoke() 方法，正是这个方法决定了怎么样处理代理传递过来的方法调用。

因为，Proxy 动态产生的代理会调用 InvocationHandler 实现类，所以 InvocationHandler 是实际执行者。

### 10.3、总结

1. 静态代理，代理类需要自己编写代码写成。
2. 动态代理，代理类通过 Proxy.newInstance() 方法生成。
3. JDK实现的代理中不管是静态代理还是动态代理，代理与被代理者都要实现两样接口，它们的实质是面向接口编程。CGLib可以不需要接口。
4. 动态代理通过 Proxy 动态生成 proxy class，但是它也指定了一个 InvocationHandler 的实现类。

## 11、建造者模式

Builder 模式中文叫作建造者模式，又叫生成器模式，它属于对象创建型模式，是将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。建造者模式是一步一步创建一个复杂的对象，它允许用户只通过指定复杂对象的类型和内容就可以构建它们，用户不需要知道内部的具体构建细节。

在建造者模式中，有如下４种角色：

- Product：产品角色
- Builder：抽象建造者，定义产品接口
- ConcreteBuilder：具体建造者，实现Builder定义的接口，并且返回组装好的产品
- Director：指挥者，属于这里面的老大，你需要生产什么产品都直接找它。

### 11.1、建造者模式应用举例

### 家装

家装不管是精装还是简装，它的流程都相对固定，所以它适用于建造者模式。我们就以家装为例，一起来学习了解一下建造者模式。下图是家装建造者模式简单的 UML 图。

#### 11.1.1、家装对象类

```java
/**
 * 家装对象类
 */
public class House {
    // 买家电
    private String jiadian;

    // 买地板
    private String diban;
    // 买油漆
    private String youqi;

    public String getJiadian() {
        return jiadian;
    }

    public void setJiadian(String jiadian) {
        this.jiadian = jiadian;
    }

    public String getDiban() {
        return diban;
    }

    public void setDiban(String diban) {
        this.diban = diban;
    }

    public String getYouqi() {
        return youqi;
    }

    public void setYouqi(String youqi) {
        this.youqi = youqi;
    }

    @Override
    public String toString() {
        return "House{" +
                "jiadian='" + jiadian + '\'' +
                ", diban='" + diban + '\'' +
                ", youqi='" + youqi + '\'' +
                '}';
    }
}
```

#### 11.1.2、抽象建造者 Builder 类

```java
/**
 * 抽象建造者
 */
public interface HouseBuilder {
    // 买家电
    void doJiadian();
    // 买地板
    void doDiBan();
    // 买油漆
    void doYouqi();

    House getHouse();
}
```

#### 11.1.3、具体建造者－简装建造者类

```java
/**
 * 简装创建者
 */
public class JianzhuangBuilder implements HouseBuilder {

    private House house = new House();

    @Override
    public void doJiadian() {
        house.setJiadian("简单家电就好");
    }

    @Override
    public void doDiBan() {
        house.setDiban("普通地板");
    }

    @Override
    public void doYouqi() {
        house.setYouqi("污染较小的油漆就行");
    }

    @Override
    public House getHouse() {
        return house;
    }
}
```

#### 11.1.4、具体建造者－精装建造者类

```text
/**
 * 精装创建者
 */
public class jingzhuangBuilder implements HouseBuilder {

    private House house = new House();

    @Override
    public void doJiadian() {
        house.setJiadian("二话不说，最好的");
    }

    @Override
    public void doDiBan() {
        house.setDiban("二话不说，实木地板");
    }

    @Override
    public void doYouqi() {
        house.setYouqi("二话不说，给我来0污染的");
    }

    @Override
    public House getHouse() {
        return house;
    }
}
```

#### 11.1.5、指挥官－家装公司类

```java
/**
 * 家装公司，值需要告诉他精装还是简装
 */
public class HouseDirector {

    public House builder(HouseBuilder houseBuilder){
        houseBuilder.doDiBan();
        houseBuilder.doJiadian();
        houseBuilder.doYouqi();
        return houseBuilder.getHouse();
    }
}
```

#### 11.1.6、测试

```java
public class App {
    public static void main(String[] args) {
        house();
    }

    public static void house(){
        HouseDirector houseDirector = new HouseDirector();
        // 简装
        JianzhuangBuilder jianzhuangBuilder = new JianzhuangBuilder();
        System.out.println("我要简装");
        System.out.println(houseDirector.builder(jianzhuangBuilder));

        // 精装
        jingzhuangBuilder jingzhuangBuilder = new jingzhuangBuilder();
        System.out.println("我要精装");
        System.out.println(houseDirector.builder(jingzhuangBuilder));

    }
}
```

输出结果

```java
我要简装
House{jiadian="简单家电就好"，diban='普通地板 ，youqi= 污染较小的油漆就行'
我要精装
House{jiadian='二话不说，最好的'，diban='二话不说，实木地板，yougi='二话不说，给我来0污染的'}
```

我们以家装为例，实现了两个具体的建造者，一个简装建造者、一个精装建造者。我们只需要告诉家装公司，我是需要简装还是精装，他会去帮我们安排，我不需要知道里面具体的细节。

### 11.2、对象构建

在日常开发中，你是不是会经常看到下面这种代码:

```java
return new Docket(DocumentationType.SWAGGER_2)
        .apiInfo(apiInfo())
        .select()
        .apis(RequestHandlerSelectors.basePackage("com.curry.springbootswagger.controller"))
        .paths(PathSelectors.any())
        .build();
```

是不是很优美？学会了 Builder 模式之后，你也可以通过这种方式进行对象构建。它是通过变种的 Builder 模式实现的。先不解释了，我们先用 Builder 模式来实现跟上述的对象构建，使用学生类为例。

学生对象代码：

```java
public class Student {

    private String name;

    private int age;

    private int num;

    private String email;

    // 提供一个静态builder方法
    public static Student.Builder builder() {
        return new Student.Builder();
    }
    // 外部调用builder类的属性接口进行设值。
    public static class Builder{
        private String name;

        private int age;

        private int num;

        private String email;

        public Builder name(String name) {
            this.name = name;
            return this;
        }

        public Builder age(int age) {
            this.age = age;
            return this;
        }

        public Builder num(int num) {
            this.num = num;
            return this;
        }

        public Builder email(String email) {
            this.email = email;
            return this;
        }

        public Student build() {
            // 将builder对象传入到学生构造函数
            return new Student(this);
        }
    }
    // 私有化构造器
    private Student(Builder builder) {
        name = builder.name;
        age = builder.age;
        num = builder.num;
        email = builder.email;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", num=" + num +
                ", email='" + email + '\'' +
                '}';
    }
}
```

调用代码：

```java
public static void student(){
        Student student = Student.builder().name("平头哥").num(1).age(18).email("平头哥@163.com").build();
        System.out.println(student);
    }
```

可以看到，变种 Builder 模式包括以下内容：

- 在要构建的类内部创建一个静态内部类 Builder
- 静态内部类的参数与构建类一致
- 构建类的构造参数是 静态内部类，使用静态内部类的变量一一赋值给构建类
- 静态内部类提供参数的 setter 方法，并且返回值是当前 Builder 对象
- 最终提供一个 build 方法构建一个构建类的对象，参数是当前 Builder 对象

可能你会说，这种写法实现太麻烦了，确实需要我们写很多额外的代码，好在前辈们已经开发出了`lombok`来拯救我们，我们只需要引入`lombok`插件，然后在实体类上添加`@Builder`注解，你就可以使用 Builder 模式构建对象了。

### 11.3、建造者模式的优缺点

### 优点

- 在建造者模式中， 客户端不必知道产品内部组成的细节，将产品本身与产品的创建过程解耦，使得相同的创建过程可以创建不同的产品对象
- 每一个具体建造者都相对独立，而与其他的具体建造者无关，因此可以很方便地替换具体建造者或增加新的具体建造者， 用户使用不同的具体建造者即可得到不同的产品对象
- 可以更加精细地控制产品的创建过程 。将复杂产品的创建步骤分解在不同的方法中，使得创建过程更加清晰，也更方便使用程序来控制创建过程
- 增加新的具体建造者无须修改原有类库的代码，指挥者类针对抽象建造者类编程，系统扩展方便，符合“开闭原则”

### 缺点

- 建造者模式所创建的产品一般具有较多的共同点，其组成部分相似，如果产品之间的差异性很大，则不适合使用建造者模式，因此其使用范围受到一定的限制。
- 如果产品的内部变化复杂，可能会导致需要定义很多具体建造者类来实现这种变化，导致系统变得很庞大。

# 十九、SpringCloud

微服务 (Microservices) 是一种软件架构风格，起源于Peter Rodgers博士于 2005 年度云端运算博览会提出的微 Web 服务 (Micro-Web-Service) 。微服务主旨是将一个原本独立的系统 拆分成多个小型服务，这些小型服务都在各自独立的进程中运行，服务之间通过基于HTTP的RESTful API进行通信协作。下图展示了单体应用和微服务之间的区别：

![micro-deployment.png](https://mrbird.cc/img/micro-deployment.png)

在微服务的架构下，单体应用的各个业务模块被拆分为一个个单独的服务并部署在单独的进程里，每个服务都可以单独的部署和升级。这种去中心化的模式使得后期维护和开发变得更加灵活和方便。由于各个服务单独部署，所以可以使用不同的语句来开发各个业务服务模块。

[Spring Cloud](https://projects.spring.io/spring-cloud/)是一个基于Spring Boot实现的微服务架构开发工具。它为微服务架构中涉及的配置管理、服务治理、断路器、智能路由、微代理、控制总线、全局锁、决策竞选、分布式会话和集群状态管理等操作提供了一种简单的开发方式。Spring Cloud的诞生并不是为了解决微服务中的某一个问题，而是提供了一套解决微服务架构实施的综合性解决方案。

## 1、什么是SpringCloud
* Spring Cloud是一个微服务系统架构的一站式解决方案，提供的全套的分布式系统解决方案。
* Spring Cloud对微服务基础框架Netflix的多个开源组件进行了封装，又实现了和Spring Boot开发框架以及云端平台的集成。
* Spring Cloud为微服务架构开发涉及的配置管理，服务治理，熔断机制，智能路由，微代理，控制总线，一次性token，全局一致性锁，leader选举，分布式session，集群状态管理等操作提供了一种简单的开发方式。（贼多，记住几个就行）
* Spring Cloud 为开发者提供了快速构建分布式系统的工具，开发者可以快速的启动服务或构建应用、同时能够快速和云平台资源进行对接。
  白话文：Spring Cloud是一个微服务架构全家桶

## 2、什么是微服务？
是一个分布式系统，它是将单体应用划分成小的服务单元，微服务之间使用HTTP的API进行访问操作。每个微服务都独自运行在自己的进程中独立部署，而且每个微服务可以使用单独的语言开发以及不同的数据库存储。

## 3、微服务的优点
* 服务的独立部署：每个服务都是一个独立的项目，可以独立部署，不依赖于其他服务，耦合性低。
* 服务的快速启动：拆分之后服务启动的速度必然要比拆分之前快很多，因为依赖的库少了，代码量也少了。
* 更加适合敏捷开发：敏捷开发以用户的需求进化为核心，采用迭代、循序渐进的方法进行。服务拆分可以快速发布新版本，修改哪个服务只需要发布对应的服务即可，不用整体重新发布。（啥是敏捷开发？）
* 服务可以动态按需扩容：当某个服务的访问量较大时，我们只需要将这个服务扩容即可。
* 服务的数据库独立：分库分表，正因为与单体架构一样都在一个数据库里面就会给数据库造成压力最好的办法及时分库分表。
* 分布式服务集中化管理（说的就是注册中心）。
  服务的管理中心对微服务集中化管理，Eureka和Zookeeper和Consul。
* 熔断机制
  微服务之间相互依赖，一个服务A不可用（超时或者网络延迟），导致调用服务A的其他服务也不可用，导致系统瘫痪（雪崩效应），为了解决这一问题采用“熔断机制”。

## 3、微服务的缺点
* 服务间调用的问题：有网络问题、延迟开销、容错、带宽、安全等问题
* 独立的数据库，分布式事务问题：每个微服务都有自己的数据库，这就是所谓的去中心化的数据管理。这种模式的优点在于不同的服务，可以选择适合自身业务的数据，比如订单服务可以用 MySQL、评论服务可以用 Mongodb、商品搜索服务可以用 Elasticsearch。

> 目前最理想的解决方案就是柔性事务中的最终一致性

* 测试的难度增加：服务和服务之间通过接口来交互，当接口有改变的时候，对所有的调用方都是有影响的，这时自动化测试就显得非常重要了，如果要靠人工一个个接口去测试，那工作量就太大了。这里要强调一点，就是 API 文档的管理尤为重要。

* 运维的难度增加：在采用传统的单体应用时，我们可能只需要关注一个 Tomcat 的集群、一个 MySQL 的集群就可以了，但这在微服务架构下是行不通的。当业务增加时，服务也将越来越多，服务的部署、监控将变得非常复杂，这个时候对于运维的要求就高了。

## 4、SpringCloud有什么优势？
使用SpringBoot开发分布式微服务时,我们面临以下问题：

* 与分布式系统相关的复杂性：这种开销包括网络问题,延迟开销,带宽问题,安全问题。
* 服务发现：服务发现工具管理群集中的流程和服务如何查找和互相交谈。它涉及一个服务目录,在该目录中注册服务,然后能够查找并连接到该目录中的服务。
* 冗余：分布式系统中的冗余问题。
* 负载平衡：负载平衡改善跨多个计算资源的工作负荷,诸如计算机,计算机集群,网络链路,中央处理单元,或磁盘驱动器的分布。
* 性能问题：由于各种运营开销导致的性能问题。
* 部署复杂性：Devops技能的要求。

## 5、什么是服务熔断？什么是服务降级？
### 5.1、熔断机制（微服务链路保护机制）

* 熔断机制是应对雪崩效应的一种微服务链路保护机制。当扇出链路的某个微服务不可用或者响应时间太长时，会进行服务降级，进而熔断该节点微服务的调用，**快速返回“错误”的响应信息**。当检测到该节点微服务调用响应正常后恢复调用链路。

* 在SpringCloud框架里熔断机制通过Hystrix实现，Hystrix会监控微服务间调用的状况，当失败的调用到一定阈值，缺省是5秒内调用20次，如果失败，就会启动熔断机制。熔断机制的注解@HystrixCommand。

### 5.2、服务降级
服务降级，一般是从整体负荷考虑。就是当某个服务熔断之后，服务器将不再被调用，此时客户端可以自己准备一个本地的fallback回调，返回一个缺省值。这样做，虽然水平下降，但好歹可用，比直接挂掉强。

## 6、Eureka和zookeeper都可以提供服务注册与发现的功能，请说说两个的区别?
### 6.1、zookeeper
zookeeper 是CP原则（强一致性和分区容错性）。 zookeeper当主节点Master故障时，zk会在剩余节点重新选择主节点，耗时过长，虽然最终能够恢复，但是选取Master节点期间会导致服务不可用，这是不能容忍的。

### 6.2、Eureka
eureka是AP原则（可用性和分区容错性）。 eureka各个节点是平等的，一个节点挂掉，其他节点仍会正常保证服务。

## 7、SpringBoot和SpringCloud的区别

* SpringBoot只是一个快速开发框架
* SpringCloud是一系列框架的集合（每一个框架可以认为是一个SpringBoot）
* SpringBoot可以离开SpringCloud单独使用,而SpringCloud离不开SpringBoot

## 8、负载均衡的意义是什么？
在计算中，负载均衡可以改善计算机，计算机集群，网络连接，中央处理器单元或者磁盘驱动琪等多种计算资源和工作负载分布。负载均衡就是优化资源使用，最大吞吐量，最小化响应时间并且避免任何单一资源的过载。使用多个组件进行负载均衡，而不是单个组件可能会通过冗余来提高可靠性和可用性。负载均衡通常涉及专用软件或者硬件，例如多层交换机或者域名系统服务器进程。

## 9、什么是hystrix,如何实现容错

### 9.1、hystrix

Hystrix是Netflix针对微服务分布式系统采用的熔断保护中间件，相当于电路中的保险丝。 在微服务架构下，很多服务都相互依赖，如果不能对依赖的服务进行隔离，那么服务本身也有可能发生故障，Hystrix 通过HystrixCommand对调用进行隔离，这样可以阻止故障的连锁反应，能够让接口调用快速失败并迅速恢复正常，或者回退并优雅降级。

> tips小知识：hystrix是基于线程池隔离调用，基于熔断器快速失败

### 9.2、如何实现容错

Hystrix是由Netflix开源的一个延迟和容错库，用于隔离访问远程系统、服务或者第三方库，防止级联失败

* 包裹请求
* 跳闸机制：当服务错误率达到一定阈值时，自动跳闸或者手动跳闸
* 资源隔离：Hystrix为每个依赖都维护了一个小型的线程池，当线程池已满，会立即拒绝该依赖的请求，加速失败判定。
* 监控
* 回退机制：发生错误时，执行回退机制fallback，类似缺省值；
* 自我修复：断路器打开后的自动恢复机制

> 检测调用失败频率太高的时候，直接打开断路器，快速失败，保护资源，之后尝试关闭断路器

断路器逻辑：
1、正常情况下，断路器关闭，可正常访问；
2、在一段时间内请求失败率达到阈值，断路器打开；
3、打开后进入“半开”状态。此时可允许一个请求访问依赖的服务，若成功则关闭断路器，若失败则继续保持打开状态。

## 10、说说RPC的实现原理（非常重要）

![在这里插入图片描述](https://img-blog.csdnimg.cn/984eeff559844990b631c9e1afb7bfb8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA54ix5ZCD6bG86aW855qE54yr,size_13,color_FFFFFF,t_70,g_se,x_16)

### 10.1、建立通信

首先要解决通讯的问题：即A机器想要调用B机器，首先得建立起通信连接。

* 主要是通过在客户端和服务器之间建立TCP连接，远程过程调用的所有交换的数据都在这个连接里传输。连接可以是按需连接，调用结束后就断掉，也可以是长连接，多个远程过程调用共享同一个连接。

* 通常这个连接可以是按需连接（需要调用的时候就先建立连接，调用结束后就立马断掉），也可以是长连接（客户端和服务器建立起连接之后保持长期持有，不管此时有无数据包的发送，可以配合心跳检测机制定期检测建立的连接是否存活有效），多个远程过程调用共享同一个连接。

### 10.2、服务寻址

要解决寻址的问题，也就是说，A服务器上的应用怎么告诉底层的RPC框架，如何连接到B服务器（如主机或IP地址）以及特定的端口，方法的名称名称是什么。

* 通常情况下我们需要提供B机器（主机名或IP地址）以及特定的端口，然后指定调用的方法或者函数的名称以及入参出参等信息，这样才能完成服务的一个调用。

* 可靠的寻址方式（注册中心）是RPC的实现基石，比如可以采用Redis或者Zookeeper来注册服务等等。

#### 10.2.1 从服务提供者的角度看：

当服务提供者启动的时候，需要将自己提供的服务注册到指定的注册中心，以便服务消费者能够通过服务注册中心进行查找；

当服务提供者由于各种原因致使提供的服务停止时，需要向注册中心注销停止的服务；

服务的提供者需要定期向服务注册中心发送心跳检测，服务注册中心如果一段时间未收到来自服务提供者的心跳后，认为该服务提供者已经停止服务，则将该服务从注册中心上去掉

#### 10.2.2 从调用者的角度看：

服务的调用者启动的时候根据自己订阅的服务向服务注册中心查找服务提供者的地址等信息；

当服务调用者消费的服务上线或者下线的时候，注册中心会告知该服务的调用者；

服务调用者下线的时候，则取消订阅。

### 10.3、网络传输

#### 10.3.1 序列化

当A机器上的应用发起一个RPC调用时，调用方法和其入参等信息需要通过底层的网络协议如TCP传输到B机器，由于网络协议是基于二进制的，所有我们传输的参数数据都需要先进行序列化（Serialize）或者编组（marshal）成二进制的形式才能在网络中进行传输。然后通过寻址操作和网络传输将序列化或者编组之后的二进制数据发送给B机器。

#### 10.3.2 反序列化

当B机器接收到A机器的应用发来的请求之后，又需要对接收到的参数等信息进行反序列化操作（序列化的逆操作），即将二进制信息恢复为内存中的表达方式，然后再找到对应的方法（寻址的一部分）进行本地调用（一般是通过生成代理Proxy去调用,
通常会有JDK动态代理、CGLIB动态代理、Javassist生成字节码技术等），之后得到调用的返回值。

### 10.4、服务调用

B机器进行本地调用（通过代理Proxy和反射调用）之后得到了返回值，此时还需要再把返回值发送回A机器，同样也需要经过序列化操作，然后再经过网络传输将二进制数据发送回A机器，而当A机器接收到这些返回值之后，则再次进行反序列化操作，恢复为内存中的表达方式，最后再交给A机器上的应用进行相关处理，一般是业务逻辑处理操作。

## 11、Eureka的自我保护机制

Eureka Server 在运行期间会去统计心跳失败比例在 15 分钟之内是否低于 85%，如果低于 85%，Eureka Server 会将这些实例保护起来，让这些实例不会过期，但是在保护期内如果刚好这个服务提供者非正常下线了，此时服务消费者就会拿到一个无效的服务实例，此时会调用失败，对于这个问题需要服务消费者端要有一些容错机制，如重试，断路器等。

## 12、自我保护机制的意义

它不会从注册列表中剔除因长时间没收到心跳导致租期过期的服务，而是等待修复，直到心跳恢复正常之后，它自动退出自我保护模式。这种模式旨在避免因网络分区故障导致服务不可用的问题。例如，两个客户端实例 C1 和 C2 的连通性是良好的，但是由于网络故障，C2 未能及时向 Eureka 发送心跳续约，这时候 Eureka 不能简单的将 C2 从注册表中剔除。因为如果剔除了，C1 就无法从 Eureka 服务器中获取 C2 注册的服务，但是这时候 C2 服务是可用的。

## 13、什么是Ribbon
Ribbon是一个有负载均衡功能的http客户端（基于HTTP和TCP），它不像 spring cloud 服务注册中心、配置中心、API 网关那样独立部署，但是它几乎存在于每个 spring cloud 微服务中。包括 feign 提供的声明式服务调用也是基于该 Ribbon实现的。（feign内置了ribbon）

## 14、Ribbon的负载均衡算法

ribbon 默认提供很多种负载均衡算法，例如 轮询、随机 等等。甚至包含自定义的负载均衡算法。

## 15、什么是Feign

Feign 运行在消费者端的，使用 Ribbon 进行负载均衡，所以 Feign 直接内置了 Ribbon

Feign是Spring Cloud组件中的一个轻量级RESTful的HTTP服务客户端

Feign内置了Ribbon，用来做客户端负载均衡，去调用服务注册中心的服务。

Feign的使用方式是：使用Feign的注解定义接口，调用这个接口，就可以调用服务注册中心的服务

Feign本身不支持Spring MVC的注解，它有一套自己的注解（和OpenFeign的区别）

## 16、什么是OpenFeign

OpenFeign在Feign的基础上支持了Spring MVC的注解，如@RequesMapping等等。OpenFeign的@FeignClient可以解析SpringMVC的@RequestMapping注解下的接口，并通过动态代理的方式产生实现类，实现类中做负载均衡并调用其他服务。

## 17、Ribbon和Feign的区别

* 调用方式不同
  Ribbon 和 Feign 都是用于调用其他服务的，但调用方式不同，Feign 则是在 Ribbon 的基础上进行了一次改进，采用接口的方式，将需要调用的其他服务的方法定义成抽象方法即可，不需要自己构建 http 请求。不过要注意的是抽象方法的注解、方法签名要和提供服务的方法完全一致；Ribbon需要自己构建 http 请求，模拟 http 请求然后使用RestTemplate 发送给其他服务

---



## 1、什么是Spring Cloud ？

Spring cloud 流应用程序启动器是基于 Spring Boot 的 Spring 集成应用程序，提供与外部系统的集成。Spring cloud Task，一个生命周期短暂的微服务框架，用于快速构建执行有限数据处理的应用程序。

## 2、什么是微服务？

微服务架构是一种架构模式或者说是一种架构风格，它提倡将单一应用程序划分为一组小的服务，每个服务运行在其独立的自己的进程中，服务之间相互协调、互相配合，为用户提供最终价值。服务之间采用轻量级的通信机制互相沟通（通常是基于HTTP的RESTful API）,每个服务都围绕着具体的业务进行构建，并且能够被独立的构建在生产环境、类生产环境等。另外，应避免统一的、集中式的服务管理机制，对具体的一个服务而言，应根据业务上下文，选择合适的语言、工具对其进行构建，可以有一个非常轻量级的集中式管理来协调这些服务，可以使用不同的语言来编写服务，也可以使用不同的数据存储。[************](https://gw-c.nowcoder.com/api/sparta/jump/link?link=https%3A%2F%2Ftopjavaer.cn)

通俗地来讲：

微服务就是一个独立的职责单一的服务应用程序。在 intellij idea 工具里面就是用maven开发的一个个独立的module，具体就是使用springboot 开发的一个小的模块，处理单一专业的业务逻辑，一个模块只做一个事情。

微服务强调的是服务大小，关注的是某一个点，具体解决某一个问题/落地对应的一个服务应用，可以看做是idea 里面一个 module。

## 3、Spring Cloud有什么优势

使用 Spring Boot 开发分布式微服务时，我们面临以下问题

- 与分布式系统相关的复杂性-这种开销包括网络问题，延迟开销，带宽问题，安全问题。
- 服务发现-服务发现工具管理群集中的流程和服务如何查找和互相交谈。它涉及一个服务目录，在该目录中注册服务，然后能够查找并连接到该目录中的服务。
- 冗余-分布式系统中的冗余问题。
- 负载平衡 --负载平衡改善跨多个计算资源的工作负荷，诸如计算机，计算机集群，网络链路，中央处理单元，或磁盘驱动器的分布。
- 性能-问题 由于各种运营开销导致的性能问题。
- 部署复杂性-Devops 技能的要求。

## 4、微服务之间如何独立通讯的?

同步通信：dobbo通过 RPC 远程过程调用、springcloud通过 REST  接口json调用等。

异步：消息队列，如：`RabbitMq`、`ActiveM`、`Kafka`等消息队列。

## 5、 **什么是服务熔断？什么是服务降级？**

熔断机制是应对雪崩效应的一种微服务链路保护机制。当某个微服务不可用或者响应时间太长时，会进行服务降级，进而熔断该节点微服务的调用，快速返回“错误”的响应信息。当检测到该节点微服务调用响应正常后恢复调用链路。在Spring Cloud框架里熔断机制通过Hystrix实现，Hystrix会监控微服务间调用的状况，当失败的调用到一定阈值，缺省是5秒内调用20次，如果失败，就会启动熔断机制。

服务降级，一般是从整体负荷考虑。就是当某个服务熔断之后，服务器将不再被调用，此时客户端可以自己准备一个本地的fallback回调，返回一个缺省值。这样做，虽然水平下降，但好歹可用，比直接挂掉强。

`Hystrix`相关注解`@EnableHystrix`：开启熔断 `@HystrixCommand(fallbackMethod=”XXX”)`，声明一个失败回滚处理函数`XXX`，当被注解的方法执行超时（默认是1000毫秒），就会执行`fallback`函数，返回错误提示。

## 6、 请说说Eureka和zookeeper 的区别？

Zookeeper保证了CP，Eureka保证了AP。

> A：高可用
>
> C：一致性
>
> P：分区容错性

1.当向注册中心查询服务列表时，我们可以容忍注册中心返回的是几分钟以前的信息，但不能容忍直接down掉不可用。也就是说，服务注册功能对高可用性要求比较高，但zk会出现这样一种情况，当master节点因为网络故障与其他节点失去联系时，剩余节点会重新选leader。问题在于，选取leader时间过长，30 ~ 120s，且选取期间zk集群都不可用，这样就会导致选取期间注册服务瘫痪。在云部署的环境下，因网络问题使得zk集群失去master节点是较大概率会发生的事，虽然服务能够恢复，但是漫长的选取时间导致的注册长期不可用是不能容忍的。

2.Eureka保证了可用性，Eureka各个节点是平等的，几个节点挂掉不会影响正常节点的工作，剩余的节点仍然可以提供注册和查询服务。而Eureka的客户端向某个Eureka注册或发现时发生连接失败，则会自动切换到其他节点，只要有一台Eureka还在，就能保证注册服务可用，只是查到的信息可能不是最新的。除此之外，Eureka还有自我保护机制，如果在15分钟内超过85%的节点没有正常的心跳，那么Eureka就认为客户端与注册中心发生了网络故障，此时会出现以下几种情况：

①、Eureka不在从注册列表中移除因为长时间没有收到心跳而应该过期的服务。

②、Eureka仍然能够接受新服务的注册和查询请求，但是不会被同步到其他节点上（即保证当前节点仍然可用）

③、当网络稳定时，当前实例新的注册信息会被同步到其他节点。

因此，Eureka可以很好地应对因网络故障导致部分节点失去联系的情况，而不会像Zookeeper那样使整个微服务瘫痪

## 7、SpringBoot和SpringCloud的区别？

SpringBoot专注于快速方便得开发单个个体微服务。

SpringCloud是关注全局的微服务协调整理治理框架，它将SpringBoot开发的一个个单体微服务整合并管理起来，

为各个微服务之间提供，配置管理、服务发现、断路器、路由、微代理、事件总线、全局锁、决策竞选、分布式会话等等集成服务

SpringBoot可以离开SpringCloud独立使用开发项目， 但是SpringCloud离不开SpringBoot ，属于依赖的关系.

SpringBoot专注于快速、方便得开发单个微服务个体，SpringCloud关注全局的服务治理框架。

## 8、负载平衡的意义什么？

在计算中，负载平衡可以改善跨计算机，计算机集群，网络链接，中央处理单元或磁盘驱动器等多种计算资源的工作负载分布。负载平衡旨在优化资源使用，最大化吞吐量，最小化响应时间并避免任何单一资源 的过载。使用多个组件进行负载平衡而不是单个组件可能会通过冗余来提高可靠性和可用性。负载平衡通常涉及专用软件或硬件，例如多层交换机或域名系统服务器进程。

## 9、什么是Hystrix？它如何实现容错？

Hystrix是一个延迟和容错库，旨在隔离远程系统，服务和第三方库的访问点，当出现故障是不可避免的故障时，停止级联故障并在复杂的分布式系统中实现弹性。

通常对于使用微服务架构开发的系统，涉及到许多微服务。这些微服务彼此协作。

思考一下微服务：

![img](http://img.topjavaer.cn/img/springcloud-microservice.png)

假设如果上图中的微服务9失败了，那么使用传统方法我们将传播一个异常。但这仍然会导致整个系统崩溃。

随着微服务数量的增加，这个问题变得更加复杂。微服务的数量可以高达1000.这是hystrix出现的地方 我们将使用Hystrix在这种情况下的Fallback方法功能。我们有两个服务employee-consumer使用由employee-consumer公开的服务。

简化图如下所示

![img](http://img.topjavaer.cn/img/springcloud2.png)

现在假设由于某种原因，employee-producer公开的服务会抛出异常。我们在这种情况下使用Hystrix定义了一个回退方法。这种后备方法应该具有与公开服务相同的返回类型。如果暴露服务中出现异常，则回退方法将返回一些值。

## 10、什么是Hystrix断路器？我们需要它吗？

由于某些原因，employee-consumer公开服务会引发异常。在这种情况下使用Hystrix我们定义了一个回退方法。如果在公开服务中发生异常，则回退方法返回一些默认值。

![img](http://img.topjavaer.cn/img/springcloud3.png)

如果firstPage method() 中的异常继续发生，则Hystrix电路将中断，并且员工使用者将一起跳过firtsPage方法，并直接调用回退方法。断路器的目的是给第一页方法或第一页方法可能调用的其他方法留出时间，并导致异常恢复。可能发生的情况是，在负载较小的情况下，导致异常的问题有更好的恢复机会 。

## 11、说说 RPC 的实现原理

首先需要有处理网络连接通讯的模块，负责连接建立、管理和消息的传输。其次需要有编 解码的模块，因为网络通讯都是传输的字节码，需要将我们使用的对象序列化和反序列化。剩下的就是客户端和服务器端的部分，服务器端暴露要开放的服务接口，客户调用服 务接口的一个代理实现，这个代理实现负责收集数据、编码并传输给服务器然后等待结果返回。

## 12，eureka自我保护机制是什么?

当Eureka Server 节点在短时间内丢失了过多实例的连接时（比如网络故障或频繁启动关闭客户端）节点会进入自我保护模式，保护注册信息，不再删除注册数据，故障恢复时，自动退出自我保护模式。

## 13，什么是Ribbon？

ribbon是一个负载均衡客户端，可以很好地控制htt和tcp的一些行为。`feign默认集成了ribbon`。

## 14，什么是 Netflix Feign？它的优点是什么？

Feign 是受到 Retrofit，JAXRS-2.0 和 WebSocket 启发的 java 客户端联编程序。

Feign 的第一个目标是将约束分母的复杂性统一到 http apis，而不考虑其稳定性。

特点：

- Feign 采用的是基于接口的注解
- Feign 整合了ribbon，具有负载均衡的能力
- 整合了Hystrix，具有熔断的能力

使用方式

- 添加pom依赖。
- 启动类添加`@EnableFeignClients`
- 定义一个接口`@FeignClient(name=“xxx”)`指定调用哪个服务

## 15， Ribbon和Feign的区别？

1.**启动类注解不同**，Ribbon是@RibbonClient feign的是@EnableFeignClients；2.**服务指定的位置不同**，Ribbon是在@RibbonClient注解上声明，Feign则是在定义抽象方法的接口中使用@FeignClient声明；3.**调用方式不同**，Ribbon需要自己构建http请求，模拟http请求。

## 16、Spring Cloud 的核心组件有哪些？

- Eureka：服务注册于发现。
- Feign：基于动态代理机制，根据注解和选择的机器，拼接请求 url 地址，发起请求。
- Ribbon：实现负载均衡，从一个服务的多台机器中选择一台。
- Hystrix：提供线程池，不同的服务走不同的线程池，实现了不同服务调用的隔离，避免了服务雪崩的问题。
- Zuul：网关管理，由 Zuul 网关转发请求给对应的服务。

## 17、说说Spring Boot和Spring Cloud的关系

Spring Boot是Spring推出用于解决传统框架配置文件冗余,装配组件繁杂的基于Maven的解决方案,旨在快速搭建单个微服务而Spring Cloud专注于解决各个微服务之间的协调与配置,服务之间的通信,熔断,负载均衡等技术维度并相同,并且Spring Cloud是依赖于Spring Boot的,而Spring Boot并不是依赖与Spring Cloud,甚至还可以和Dubbo进行优秀的整合开发

总结

- SpringBoot专注于快速方便的开发单个个体的微服务
- SpringCloud是关注全局的微服务协调整理治理框架,整合并管理各个微服务,为各个微服务之间提供,配置管理,服务发现,断路器,路由,事件总线等集成服务
- Spring Boot不依赖于Spring Cloud，Spring Cloud依赖于Spring Boot,属于依赖关系
- Spring Boot专注于快速,方便的开发单个的微服务个体,Spring Cloud关注全局的服务治理框架

## 18、说说微服务之间是如何独立通讯的？

**远程过程调用（Remote Procedure Invocation）**

也就是我们常说的服务的注册与发现，直接通过远程过程调用来访问别的service。

**优点**：简单，常见,因为没有中间件代理，系统更简单

**缺点**：只支持请求/响应的模式，不支持别的，比如通知、请求/异步响应、发布/订阅、发布/异步响应，降低了可用性，因为客户端和服务端在请求过程中必须都是可用的。

**消息**

使用异步消息来做服务间通信。服务间通过消息管道来交换消息，从而通信。

**优点**：把客户端和服务端解耦，更松耦合，提高可用性，因为消息中间件缓存了消息，直到消费者可以消费，    支持很多通信机制比如通知、请求/异步响应、发布/订阅、发布/异步响应。

**缺点**：消息中间件有额外的复杂。

## 19、Spring Cloud如何实现服务的注册?

服务发布时，指定对应的服务名，将服务注册到 注册中心(`Eureka 、Zookeeper)`。

注册中心加`@EnableEurekaServer`，服务用`@EnableDiscoveryClient`，然后用ribbon或feign进行服务直接的调用发现。

## 20、什么是服务熔断？

在复杂的分布式系统中,微服务之间的相互调用,有可能出现各种各样的原因导致服务的阻塞,在高并发场景下,服务的阻塞意味着线程的阻塞,导致当前线程不可用,服务器的线程全部阻塞,导致服务器崩溃,由于服务之间的调用关系是同步的,会对整个微服务系统造成服务雪崩

为了解决某个微服务的调用响应时间过长或者不可用进而占用越来越多的系统资源引起雪崩效应就需要进行服务熔断和服务降级处理。

所谓的服务熔断指的是某个服务故障或异常一起类似显示世界中的“保险丝"当某个异常条件被触发就直接熔断整个服务，而不是一直等到此服务超时。

服务熔断就是相当于我们电闸的保险丝,一旦发生服务雪崩的,就会熔断整个服务,通过维护一个自己的线程池,当线程达到阈值的时候就启动服务降级,如果其他请求继续访问就直接返回fallback的默认值

## 21、了解Eureka自我保护机制吗？

当Eureka Server 节点在短时间内丢失了过多实例的连接时（比如网络故障或频繁启动关闭客户端）节点会进入自我保护模式，保护注册信息，不再删除注册数据，故障恢复时，自动退出自我保护模式。

## 22、熟悉 Spring Cloud Bus 吗?

spring cloud bus 将分布式的节点用轻量的消息代理连接起来，它可以用于广播配置文件的更改或者服务直接的通讯，也可用于监控。如果修改了配置文件，发送一次请求，所有的客户端便会重新读取配置文件。

## 23、Spring Cloud 断路器有什么作用?

当一个服务调用另一个服务由于网络原因或自身原因出现问题，调用者就会等待被调用者的响应，当更多的服务请求到这些资源导致更多的请求等待，发生连锁效应（雪崩效应）。一段时间内 达到一定的次数无法调用 并且多次监测没有恢复的迹象，这时候断路器完全打开 那么下次请求就不会请求到该服务。

半开：短时间内 有恢复迹象 断路器会将部分请求发给该服务，正常调用时 断路器关闭。关闭：当服务一直处于正常状态 能正常调用。

## 24、了解Spring Cloud Config 吗?

在分布式系统中，由于服务数量巨多，为了方便服务配置文件统一管理，实时更新，所以需要分布式配置中心组件。在Spring Cloud中，有分布式配置中心组件`Spring Cloud Config`，它支持配置服务放在配置服务的内存中（即本地），也支持放在远程Git仓库中。

在`Spring Cloud Config` 组件中，分两个角色，一是config server，二是config client。

使用方式：

- 添加pom依赖
- 配置文件添加相关配置
- 启动类添加注解@EnableConfigServer

## 25、说说你对Spring Cloud Gateway的理解

Spring Cloud Gateway是Spring Cloud官方推出的第二代网关框架，取代Zuul网关。网关作为流量的，在微服务系统中有着非常作用，网关常见的功能有路由转发、权限校验、限流控制等作用。

使用了一个RouteLocatorBuilder的bean去创建路由，除了创建路由RouteLocatorBuilder可以让你添加各种predicates和filters，predicates断言的意思，顾名思义就是根据具体的请求的规则，由具体的route去处理，filters是各种过滤器，用来对请求做各种判断和修改。

## 26、Spring Cloud各个微服务之间为什么要用http交互？难道不慢吗？

Spring Cloud是一个为分布式微服务架构构建应用程序的开发工具箱，是Spring Boot的扩展，通过各种微服务组件的集成，极大地简化了微服务应用程序的构建和开发。在分布式系统中，各个微服务之间的通信是非常重要的，而HTTP作为通信协议具有普遍性和可扩展性，是Spring Cloud微服务架构中主流的通信方式。

尽管使用HTTP作为微服务之间的通信协议存在一定的网络开销，但是这种不可避免的网络开销远低于我们所能得到的好处。使用HTTP通信可以实现松耦合和异步通信，微服务之间可以彼此独立地进行开发和测试，单个微服务的故障不会影响整个系统的运行，也可以支持各种不同的技术栈之间的互操作性。

另外，使用HTTP作为通信协议还具有优秀的可扩展性。HTTP协议定义了不同的请求方法（例如 GET、POST、DELETE 等），不同请求方法的扩展格式也很灵活，可以用来传递各种类型的数据和格式，同时HTTP协议支持缓存，减少重复性的数据传输和带宽开销。

当然，为了提高微服务之间的通信效率，我们也可以通过一些优化手段来减少HTTP协议的网络开销。例如，使用数据压缩和缓存技术来压缩和缓存请求和响应，减少网络数据传输量和响应时间；使用负载均衡技术来合理地分配请求和响应，避免单个微服务出现性能瓶颈；使用高速缓存技术来缓存请求和响应，避免重复的请求和响应等等。

因此，Spring Cloud各个微服务之间使用HTTP交互是一个比较成熟的选择。虽然它可能存在一些网络开销，但是在实际应用中，这种开销是可以优化和控制的，甚至可以提高系统的可扩展性和可靠性。

# 二十、微服务

## 1、什么是微服务？

微服务是将一个原本独立的系统拆分成多个小型服务，这些小型服务都在各自独立的进程中运行，服务和服务之间采用轻量级的通信机制进行协作。每个服务可以被独立的部署到生产环境。

[从单体应用到微服务open in new window](https://www.zhihu.com/question/65502802/answer/802678798)

单体系统的缺点：

1. 修改一个小功能，就需要将整个系统重新部署上线，影响其他功能的运行；
2. 功能模块互相依赖，强耦合，扩展困难。如果出现性能瓶颈，需要对整体应用进行升级，虽然影响性能的可能只是其中一个小模块；

单体系统的优点：

1. 容易部署，程序单一，不存在分布式集群的复杂部署环境；
2. 容易测试，没有复杂的服务调用关系。

微服务的**优点**：

1. 不同的服务可以使用不同的技术；
2. 隔离性。一个服务不可用不会导致其他服务不可用；
3. 可扩展性。某个服务出现性能瓶颈，只需对此服务进行升级即可；
4. 简化部署。服务的部署是独立的，哪个服务出现问题，只需对此服务进行修改重新部署；

微服务的**缺点**：

1. 网络调用频繁。性能相对函数调用较差。
2. 运维成本增加。系统由多个独立运行的微服务构成，需要设计一个良好的监控系统对各个微服务的运行状态进行监控。

## 2、分布式和微服务的区别

微服务解决的是系统复杂度问题，一般来说是业务问题，即在一个系统中承担职责太多了，需要打散，便于理解和维护，进而提升系统的开发效率和运行效率，微服务一般来说是针对应用层面的。

分布式解决的是系统性能问题，即解决系统部署上单点的问题，尽量让组成系统的子系统分散在不同的机器上进而提高系统的吞吐能力。

两者概念层面也是不一样的，微服务是设计层面的东西，一般考虑如何将系统从逻辑上进行拆分，也就是垂直拆分；

而分布式是部署层面的东西，即强调物理层面的组成，即系统的各子系统部署在不同计算机上。

微服务可以是分布式的，即可以将不同服务部署在不同计算机上，当然如果量小也可以部署在单机上。

一句话概括：分布式：分散部署；微服务：分散能力。

## 3、服务怎么划分？

横向拆分：按照不同的业务域进行拆分，例如订单、营销、风控、积分资源等。形成独立的业务领域微服务集群。

纵向拆分：把一个业务功能里的不同模块或者组件进行拆分。例如把公共组件拆分成独立的原子服务，下沉到底层，形成相对独立的原子服务层。这样一纵一横，就可以实现业务的服务化拆分。

要做好微服务的分层：梳理和抽取核心应用、公共应用，作为独立的服务下沉到核心和公共能力层，逐渐形成稳定的服务中心，使前端应用能更快速的响应多变的市场需求

总之，微服务的设计一定要 **渐进式** 的，总的原则是 **服务内部高内聚，服务之间低耦合。**

## 4、微服务设计原则

**单一职责原则**

意思是每个微服务只需要实现自己的业务逻辑就可以了，比如订单管理模块，它只需要处理订单的业务逻辑就可以了，其它的不必考虑。

**服务自治原则**

意思是每个微服务从开发、测试、运维等都是独立的，包括存储的数据库也都是独立的，自己就有一套完整的流程，我们完全可以把它当成一个项目来对待。不必依赖于其它模块。

**轻量级通信原则**

首先是通信的语言非常的轻量，第二，该通信方式需要是跨语言、跨平台的，之所以要跨平台、跨语言就是为了让每个微服务都有足够的独立性，可以不受技术的钳制。

**接口明确原则**

由于微服务之间可能存在着调用关系，为了尽量避免以后由于某个微服务的接口变化而导致其它微服务都做调整，在设计之初就要考虑到所有情况，让接口尽量做的更通用，更灵活，从而尽量避免其它模块也做调整。

## 5、微服务之间是如何通讯的？

**1、RPC**

远程过程调用，简单的理解是一个节点请求另一个节点提供的服务。

优点：简单，常见。因为没有中间件代理，系统更简单

缺点：

1. 只支持请求/响应的模式，不支持别的，比如通知、发布/订阅
2. 降低了可用性，因为客户端和服务端在请求过程中必须都是可用的

**2、消息队列**

除了标准的基于RPC通信的微服务架构，还有基于消息队列通信的微服务架构，这种架构下的微服务采用发送消息（Publish Message）与监听消息（Subscribe Message）的方式来实现彼此之间的交互。

网易的蜂巢平台就采用了基于消息队列的微服务架构设计思路，如下图所示，微服务之间通过RabbitMQ传递消息，实现通信。

与上面几种微服务架构相比，基于消息队列的微服务架构并不多，案例也相对较少，更多地体现为一种与业务相关的设计经验，各家有各家的实现方式，缺乏公认的设计思路与参考架构，也没有形成一个知名的开源平台。因此，如果需要实施这种微服务架构，则基本上需要项目组自己从零开始去设计实现一个微服务架构基础平台，其代价是成本高、风险大。

**优点**:

- 把客户端和服务端解耦，更松耦合提高可用性，因为消息中间件缓存了消息，直到消费者可以消费
- 支持很多通信机制比如通知、发布/订阅等

**缺点**：

- 缺乏公认的设计思路与参考架构，也没有形成一个知名的开源平台
- 成本高、风险大

## 6、熔断器

雪崩效应：假如存在这样的调用链路，a服务->b服务->c服务，当c服务挂了的时候，b服务调用c服务会等待超时，a服务调用b服务也会等待超时，调用方长时间等不到相应而占用线程，如果有大量的请求过来，就会造成线程池打满，导致整个链路的服务奔溃。

为了解决分布式系统的雪崩效应，分布式系统引进了**熔断器机制** 。

当一个服务的处理用户请求的失败次数在一定时间内小于设定的阀值时，熔断器出于关闭状态，服务正常。

当服务处理用户请求失败次数在一定时间内大于设定的阀值时，说明服务出现故障，打开熔断器，这时所有的请求会快速返回失败的错误信息，不执行业务逻辑，从而防止故障的蔓延。

当处于打开状态的熔断器时，一段时间后出于半打开状态，并执行一定数量的请求，剩余的请求会执行快速失败，若执行请求失败了，则继续打开熔断器，若成功了，则将熔断器关闭。

## 7、服务网关

### 7.1、何为网关？

通俗一点的讲：网关就是要去别的网络的时候，把报文首先发送到的那台设备。稍微专业一点的术语，网关就是当前主机的默认路由。

网关一般就是一台路由器，有点像“一个小区中的一个邮局”，小区里面的住户互相是知道怎么走，但是要向外地投递东西就不知道了，怎么办？把地址写好送到本小区的邮局就好了。

那么，怎么区分是“本小区”和“外地小区”的呢？根据IP地址 + 掩码。如果是在一个范围内的，就是本小区（局域网内部），如果掩不住的，就是外地的。

例如，你的机器的IP地址是：192.168.0.2/24，网关是192.168.0.1

如果机器访问的IP地址范围是：192.168.0.1~192.168.0.254的，说明是一个小区的邻居，你的机器就直接发送了（和网关没任何关系）。如果你访问的IP地址不是这个范围的，则就投递到192.168.0.1上，让这台设备来转发。

参考：[https://www.zhihu.com/question/362842680/answer/951412213open in new window](https://www.zhihu.com/question/362842680/answer/951412213)

### 7.2、何为API网关

假设你正在开发一个电商网站，那么这里会涉及到很多后端的微服务，比如会员、商品、推荐服务等等。

那么这里就会遇到一个问题，APP/Browser怎么去访问这些后端的服务? 如果业务比较简单的话，可以给每个业务都分配一个独立的域名(`https://service.api.company.com`)，但这种方式会有几个问题:

- 每个业务都会需要鉴权、限流、权限校验等逻辑，如果每个业务都各自为战，自己造轮子实现一遍，会很蛋疼，完全可以抽出来，放到一个统一的地方去做。
- 如果业务量比较简单的话，这种方式前期不会有什么问题，但随着业务越来越复杂，比如淘宝、亚马逊打开一个页面可能会涉及到数百个微服务协同工作，如果每一个微服务都分配一个域名的话，一方面客户端代码会很难维护，涉及到数百个域名
- 每上线一个新的服务，都需要运维参与，申请域名、配置Nginx等，当上线、下线服务器时，同样也需要运维参与，另外采用域名这种方式，对于环境的隔离也不太友好，调用者需要自己根据域名自己进行判断。
- 另外还有一个问题，后端每个微服务可能采用了不同的协议，比如HTTP、AMQP、自定义TCP协议等，但是你不可能要求客户端去适配这么多种协议，这是一项非常有挑战的工作，项目会变的非常复杂且很难维护。

更好的方式是采用API网关（也叫做服务网关），实现一个API网关**接管所有的入口流量**，类似Nginx的作用，将所有用户的请求转发给后端的服务器，但网关做的不仅仅只是简单的转发，也会针对流量做一些扩展，比如鉴权、限流、权限、熔断、协议转换、错误码统一、缓存、日志、监控、告警等，这样将通用的逻辑抽出来，由网关统一去做，业务方也能够更专注于业务逻辑，提升迭代的效率。

![img](http://img.topjavaer.cn/img/20220508185101.jpg)

通过引入API网关，客户端只需要与API网关交互，而不用与各个业务方的接口分别通讯，但多引入一个组件就多引入了一个潜在的故障点，因此要实现一个高性能、稳定的网关，也会涉及到很多点。

网关层通常以集群的形式存在。并在服务网关层前通常会加上Nginx 用来负载均衡。

**服务网关基本功能**：

![img](http://img.topjavaer.cn/img/20220508120340.png)

- 智能路由：接收**外部**一切请求，并转发到后端的对外服务。注意：我们只转发外部请求，服务之间的请求不走网关，这就表示全链路追踪、内部服务API监控、内部服务之间调用的容错、智能路由不能在网关完成；当然，也可以将所有的服务调用都走网关，那么几乎所有的功能都可以集成到网关中，但是这样的话，网关的压力会很大，不堪重负。
- 权限校验：网关可以做一些用户身份认证，权限认证，防止非法请求操作API 接口，对内部服务起到保护作用
- API监控：监控经过网关的请求，以及网关本身的一些性能指标（gc等）
- 限流：与监控配合，进行限流操作
- API日志统一收集：类似于一个aspect切面，记录接口的进入和出去时的相关日志

当然，网关实现这些功能，需要做高可用，否则网关很可能成为架构的瓶颈，最常用的网关组件Zuul、Nginx

## 8、服务配置统一管理

在微服务架构中，需要有统一管理配置文件的组件，例如：SpringCloud Config组件、阿里的Diamond、百度的Disconf、携程的Apollo等

## 9、服务链路追踪

在微服务架构中，必须实现分布式链路追踪，去跟进一个请求到底有哪些服务参与、参与顺序，是每个请求链路清晰可见，便于问题快速定位。

常用链路追踪组件有Google的Dapper、Twitter 的Zipkin，以及阿里Eagleeye。

## 10、微服务框架

市面常用微服务框架有：Spring Cloud 、Dubbo 、kubernetes

- 从功能模块上考虑，Dubbo缺少很多功能模块，例如网关、链路追踪等
- 从学习成本上考虑，Dubbo 版本趋于稳定，稳定完善、可以即学即用，难度简单，Spring cloud 基于Spring Boot，需要先掌握Spring Boot ，例外Spring cloud 大多为英文文档，要求学习者有一定的英文阅读能力
- 从开发风格考虑，Dubbo倾向于xml的配置方式，Spring cloud 基于Spring Boot ，采用基于注解和JavaBean配置方式的敏捷开发
- 从开发速度上考虑，Spring cloud 具有更高的开发和部署速度
- 从通信方式上考虑，Spring cloud 基于HTTP Restful 风格，服务于服务之间完全无关、无耦合。Dubbo 基于远程调用，对接口、平台和语言有强依赖性，如果需要实现跨平台，需要有额外的中间件。

所以Dubbo专注于服务治理；Spring Cloud关注于微服务架构生态。
