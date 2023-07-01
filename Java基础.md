<a name="MbP8B"></a>
# Java概述
<a name="u4Vxs"></a>
## Java 语言的特点？

- 面对对象：封装、继承、多态。
- 跨平台性：“一次编写，到处运行（Write Once，Run Anywhere）”，由JVM实现
- 支持多线程（C++ 语言没有内置的多线程机制，因此必须调用操作系统的多线程功能来进行多线程）
- 编译 和 解释 并存
- 可靠性？？
- 安全性？？
- 支持网络编程，并且很方便（ Java 语言诞生本身就是为简化网络编程设计的）？？
<a name="jGMv9"></a>
### 什么是跨平台性？
只要该系统可以安装相应的 Java 虚拟机，该系统就可以运行 java 程序。
<a name="aecTo"></a>
### 为什么说 Java “编译与解释并存”？

- 编译型语言：一次性编译成机器码，再执行。编译器针对特定操作系统，把源代码一次性全部翻译成可被该平台执行的机器码。
- 解释型语言：边解释边执行。解释器把源程序逐行解释成特定平台的机器码，并立即执行。

因为 Java 程序要经过先编译，后解释两个步骤。

- 先编译，生成字节码（.class 文件）
- 而字节码必须由 Java 解释器来解释执行。
<a name="odUUE"></a>
## JVM、JDK、JRE 的区别？
JVM < JRE < JDK

- **JVM (Java Virtual Machine)**
   - Java 虚拟机，Java 程序运行在 Java 虚拟机上。针对不同系统的实现不同的 JVM，所以实现了跨平台。
- **JRE (Java Runtime Environment)**
   - Java 运⾏时环境。是运⾏ 已编译 Java 程序 所需的所有内容的集合，包括 JVM，Java 类库，Java 命令和其他基础构件。只能运行程序，不能编译或创建程序。
- **JDK (Java Development Kit)**
   - 功能⻬全的 Java SDK。它包含 JRE，还有编译器（javac）和⼯具（如 javadoc 和 jdb）。能创建和编译程序。

![](https://cdn.nlark.com/yuque/0/2023/jpeg/25962088/1680799504394-238eb1ad-4ded-49d2-89a7-c672846554e3.jpeg)
<a name="UezRu"></a>
## 什么是字节码？采用字节码的好处是什么?

- Java程序编译后生成的`.class`文件就是字节码。字节码可以被 JVM 识别理解。它不面向任何特定的处理器，只面向虚拟机。
- 好处：字节码，在一定程度上解决了传统解释型语言执行效率低的问题，又保留了解释型语言可移植的特点。所以 Java 程序运行相对高效。
<a name="N2sBc"></a>
### Java程序运行步骤？
**Java** 程序从源代码到运行主要有三步：

- **编译**：将我们的代码（.java）编译成虚拟机可以识别理解的字节码(.class)
- **解释**：虚拟机执行 Java 字节码，将字节码翻译成机器能识别的机器码
- **执行**：对应的机器执行二进制机器码

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1680799912052-3a84ac0c-3236-433a-b3df-92a5d971112c.png#averageHue=%23f5f1e4&clientId=ucd898b60-aa10-4&from=paste&height=291&id=ufa6fe12c&originHeight=388&originWidth=393&originalType=binary&ratio=2&rotation=0&showTitle=false&size=29884&status=done&style=none&taskId=u7486b516-6820-4959-b2d9-8f2cafe67da&title=&width=294.5)
<a name="b5SfB"></a>
## Java 和 C++ 的区别?
虽然，Java 和 C++ 都是面向对象的语言，都支持封装、继承和多态，但是，它们还是有挺多不相同的地方：

- Java 不提供指针来直接访问内存，程序内存更加安全
- Java 的类是单继承的，C++ 支持多重继承；虽然 Java 的类不可以多继承，但是接口可以多继承。
- Java 有自动内存管理垃圾回收机制(GC)，不需要程序员手动释放无用内存。
- C++ 同时支持方法重载和操作符重载，但是 Java 只支持方法重载（操作符重载增加了复杂性，这与 Java 最初的设计思想不符）。
<a name="UFDXy"></a>
## Java 和 Python 的区别？？


<a name="kaOHO"></a>
# Java基础语法
<a name="ce7ae847"></a>
## Java 有哪些语言关键字？
| 分类 | 关键字 |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 访问控制 | private | protected | public |  |  |  |  |
| 类，方法，变量修饰符 | abstract | class | extends | final | implements | interface | native |
|  | new | static | strictfp | synchronized | transient | volatile | enum |
| 程序控制 | break | continue | return | do | while | if | else |
|  | for | instanceof | switch | case | default | assert |  |
| 错误处理 | try | catch | throw | throws | finally |  |  |
| 包相关 | import | package |  |  |  |  |  |
| 基本类型 | boolean | byte | char | double | float | int | long |
|  | short |  |  |  |  |  |  |
| 变量引用 | super | this | void |  |  |  |  |
| 保留字 | goto | const |  |  |  |  |  |

> `default` 这个关键字很特殊，既属于程序控制，也属于类，方法和变量修饰符，还属于访问控制。
> - 在程序控制中，当在 `switch` 中匹配不到任何情况时，可以使用 `default` 来编写默认匹配的情况。
> - 在类，方法和变量修饰符中，从 JDK8 开始引入了默认方法，可以使用 `default` 关键字来定义一个方法的默认实现。
> - 在访问控制中，如果一个方法前没有任何修饰符，则默认会有一个修饰符 `default`，但是这个修饰符加上了就会报错。<br />⚠️ 注意 ：虽然 `true`, `false`, 和 `null` 看起来像关键字但实际上他们是字面值，同时你也不可以作为标识符来使用。

<a name="n1l7Y"></a>
## Java 有哪些数据类型？
![](https://cdn.nlark.com/yuque/0/2023/jpeg/25962088/1682601151847-fbc7cdcd-2783-44d0-b032-a9b136c8516d.jpeg)
<a name="vLqe6"></a>
### 八个基本类型的性质？
| 基本类型 | 位数 | 字节 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- |
| byte | 8 | 1 | 0 | -128 ~ 127 |
| short | 16 | 2 | 0 | -32768 ~ 32767 |
| int | 32 | 4 | 0 | -2147483648 ~ 2147483647 |
| long | 64 | 8 | 0L | -9223372036854775808 ~ 9223372036854775807 |
| float | 32 | 4 | 0f | 1.4E-45 ~ 3.4028235E38 |
| double | 64 | 8 | 0d | 4.9E-324 ~ 1.7976931348623157E308 |
| char | 16 | 2 | 'u0000' | 0 ~ 65535 |
| boolean | 1 |  | false | true、false |

- 对于 boolean，官方文档未明确定义，它依赖于 JVM 厂商的具体实现。逻辑上理解是占用 1 位，但是实际中会考虑计算机高效存储因素。
<a name="QsC6h"></a>
## 自动类型转换、强制类型转换？
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1682601402747-771bf90c-3a5b-46f1-b00f-3f7f1c23824a.png#averageHue=%23fcfcfb&clientId=u18fc352f-d6d4-4&from=paste&height=153&id=u164ec17f&originHeight=226&originWidth=823&originalType=binary&ratio=2&rotation=0&showTitle=false&size=27697&status=done&style=none&taskId=uc9debc46-a822-4c36-9aa9-2b727c20399&title=&width=555.5)

- 从左到右赋值，是会自动类型转换。
- 从右到左赋值，需要强制类型转换。
   - 比如`float f = 3.4`不行，3.4 是double，会有精度损失。
      - 需要强制类型转换`float f =(float)3.4`;或者写成`float f =3.4F`
<a name="TQYNj"></a>
### `short s1 = 1; s1 = s1 + 1；`对吗？`short s1 = 1; s1 += 1;`对吗？

- 对于 short s1 = 1; s1 = s1 + 1;编译出错，由于 1 是 int 类型，因此 s1+1 运算结果也是 int 型，需要强制转换类型才能赋值给 short 型。
- 而 short s1 = 1; s1 += 1;可以正确编译，因为 s1+= 1;相当于 s1 = (short(s1 + 1);其中有隐含的强制类型转换。
<a name="d35Jq"></a>
## 为什么浮点数运算的时候会有精度丢失的风险？

- 浮点数没有办法用二进制精确表示。计算机在表示一个数字时，宽度是有限的，无限循环的小数存储在计算机时，只能被截断，所以就会导致小数精度发生损失的情况。
```java
float a = 2.0f - 1.9f;
float b = 1.8f - 1.7f;
System.out.println(a);// 0.100000024
System.out.println(b);// 0.099999905
System.out.println(a == b);// false
```
<a name="fsLQs"></a>
### 如何解决浮点数运算的精度丢失问题？

- [BigDecimal](https://javaguide.cn/java/basis/bigdecimal.html#bigdecimal-%E5%B8%B8%E8%A7%81%E6%96%B9%E6%B3%95) 可以实现对浮点数的运算，不会造成精度丢失。
- 大部分需要浮点数精确运算结果的业务场景（比如涉及到钱的场景）都是通过 BigDecimal 来做的。
<a name="yuoWe"></a>
## 超过 long 整型的数据应该如何表示？

- Java 里 64 位 long 整型是最大的整数类型，如果超过 long 可以表示的最大范围就有数值溢出的风险。溢出如下：
```java
long l = Long.MAX_VALUE;
System.out.println(l + 1); // -9223372036854775808
System.out.println(l + 1 == Long.MIN_VALUE); // true
```

- 超过 long 的，用 BigInteger。
- BigInteger 内部使用 int[] 数组来存储任意大小的整形数据。
   - 相对于常规整数类型的运算来说，BigInteger 运算的效率会相对较低。
<a name="KBY7M"></a>
## 什么是自动拆箱/封箱？
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1682601847753-1ab0128d-7813-4a98-b6a1-7efd906a7500.png#averageHue=%23f6d593&clientId=u18fc352f-d6d4-4&from=paste&height=236&id=u1b6be513&originHeight=472&originWidth=945&originalType=binary&ratio=2&rotation=0&showTitle=false&size=64601&status=done&style=none&taskId=ua3bfb6f5-f72e-419c-bccb-6f370840dea&title=&width=472.5)

- **装箱**：将基本类型用它们对应的引用类型包装起来；
- **拆箱**：将包装类型转换为基本数据类型；
- Java 可以**自动**对**基本数据类型**和它们的包装类进行装箱和拆箱。
```java
Integer i = 10;  //装箱
int n = i;   //拆箱
```

- 装箱其实就是调用了 包装类的valueOf()方法，拆箱其实就是调用了 xxxValue()方法。所以：
   - `Integer i = 10` = `Integer i = Integer.valueOf(10)`
   - `int n = i` = `int n = i.intValue();`
<a name="iJqit"></a>
## &和&&有什么区别？

- &：逻辑与
- &&：短路与
- 虽然二者都要求运算符左右两端的布尔值都是 true 整个表达式的值才是 true，但区别是右侧表达式会不会被运算。
   - &一定会都运算，而&&在左侧false时会直接短路右边所有，也就是不接着运算右边的了。
- 很多时候我们可能都需要用&&而不是&。
   - 例如在验证用户登录时判定用户名不是 null 而且不是空字符串，应当写为username != null &&!username.equals("")，二者的顺序不能交换，更不能用&运算符，因为第一个条件如果不成立，根本不能进行字符串的 equals 比较，否则会产生 NullPointerException 异常。
- **注意**：逻辑或（|）和短路或（||）的差别也是如此。
<a name="eVUoX"></a>
## switch 是否能作用在 byte/long/String 上？

- switch(expr) 中的 expr 支持什么数据类型：
   - Java5 以前，只能是 byte、short、char、int。
   - 从 Java 5 开始，Java 中引入了枚举类型，可以是 enum 类型。
   - 从 Java 7 开始，还可以是字符串(String)。
   - 但是长整型(long)在目前所有的版本中都是不可以的。
<a name="vwVCK"></a>
## break, continue, return 的区别及作用？

- break 跳出整个循环，不再执行循环(**结束当前的循环体**)
- continue 跳出本次循环，继续执行下次循环(**结束正在执行的循环 进入下一个循环条件**)
- return 程序返回，不再执行下面的代码(**结束当前的方法 直接返回**)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1682603574761-d1382784-4656-4964-ba12-28a47addc56f.png#averageHue=%23f9f6ed&clientId=u18fc352f-d6d4-4&from=paste&height=272&id=u7f23ea1f&originHeight=543&originWidth=500&originalType=binary&ratio=2&rotation=0&showTitle=false&size=38139&status=done&style=none&taskId=ua8d719c2-72a0-456d-9f34-abbf8bf43fa&title=&width=250)
<a name="vSirR"></a>
## 自增自减运算符？

- 当运算符放在变量之前时(前缀)，先自增/减，再赋值；当运算符放在变量之后时(后缀)，先赋值，再自增/减。
   - 例如，当 b = ++a 时，先自增（自己增加 1），再赋值（赋值给 b）；
   - 当 b = a++ 时，先赋值(赋值给 b)，再自增（自己增加 1）。也就是，++a 输出的是 a+1 的值，a++输出的是 a 值。
- 用一句口诀就是：“符号在前就先加/减，符号在后就后加/减”。

这段代码会输出什么？
```java
int i  = 1;
i = i++;
System.out.println(i);
```

- 答案是 1。
- 对于 JVM 而言，它对自增运算的处理，是会先定义一个临时变量来接收 i 的值，然后进行自增运算，最后又将临时变量赋给了值为 2 的 i，所以最后的结果为 1。
- 相当于这样的代码：
```java
int i = 1；
int temp = i;
i++；
i = temp;
System.out.println(i);
```
这段代码会输出什么？
```java
int count = 0;
for(int i = 0;i < 100;i++)
{
    count = count++;
}
System.out.println("count = "+count);
```

- 答案是 0。
- 和上面的题目一样的道理，同样是用了临时变量，count 实际是等于临时变量的值。
```java
int autoAdd(int count)
{
    int temp = count;
    count = coutn + 1;
    return temp;
}
```
<a name="LdUFQ"></a>
## 移位运算符？

- 移位运算符在各种框架以及 JDK 自身的源码中使用还是挺广泛的，HashMap（JDK1.8） 中的 hash 方法的源码就用到了移位运算符：
```java
static final int hash(Object key) {
    int h;
    // key.hashCode()：返回散列值也就是hashcode
    // ^ ：按位异或
    // >>>:无符号右移，忽略符号位，空位都以0补齐
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
  }
```

- Java 中有三种移位运算符：
   - `<<` :左移运算符，向左移若干位，高位丢弃，低位补零。x << 1,相当于 x 乘以 2(不溢出的情况下)。
   - `>>` :带符号右移，向右移若干位，高位补符号位，低位丢弃。正数高位补 0,负数高位补 1。x >> 1, 相当于 x 除以 2。
   - `>>>` :无符号右移，忽略符号位，空位都以 0 补齐。
- 由于 double，float 在二进制中的表现比较特殊，因此不能来进行移位操作。
- 移位操作符实际上支持的类型只有 int 和 long，编译器在对short、byte、char类型进行移位前，都会将其转换为int类型再操作。
<a name="Vso98"></a>
### 如果移位的位数超过数值所占有的位数会怎样？

- 当 int 类型左移/右移位数大于等于 32 位操作时，会先求余（%）后再进行左移/右移操作。
- 当 long 类型进行左移/右移操作时，由于 long 对应的二进制是 64 位，因此求余操作的基数也变成了 64。
- 也就是说：`x<<42`=`x<<10`，`x>>42`=`x>>10`，`x >>>42`=`x >>> 10`。
<a name="YcUvf"></a>
# 面向对象
<a name="zsI8W"></a>
## ⾯向对象 和 ⾯向过程 的区别?

- 面向过程把解决问题的过程拆成一个个方法，使用的时候再一个一个的调用就可以。
- 面向对象会先抽象出对象，为了描述某个事件在解决整个问题的过程所发生的行为。然后用对象执行方法的方式解决问题。
   - 面向对象开发的程序一般更易维护、易复用、易扩展。
- 用一个比喻：面向过程是编年体；面向对象是纪传体。
- [面向过程 ：面向过程性能比面向对象高？](https://github.com/Snailclimb/JavaGuide/issues/431)![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1682604679266-31d50d10-dc96-4779-a99a-62abdfc3ca51.png#averageHue=%23fefefe&clientId=u18fc352f-d6d4-4&from=paste&height=373&id=ubb5cbcd4&originHeight=746&originWidth=1620&originalType=binary&ratio=2&rotation=0&showTitle=false&size=231402&status=done&style=none&taskId=uf1982f27-9d28-4153-9c61-d6cb74017dc&title=&width=810)
<a name="ZBCWh"></a>
## 面向对象有哪三个特性？

- **封装**
   - 封装把⼀个对象的属性私有化，同时提供⼀些可以被外界访问的属性的⽅法。
- **继承**
   - 继承是使⽤已存在的类的定义作为基础创建新的类，新类的定义可以增加新的属性或新的方法，也可以继承父类的属性和方法。通过继承，可以快速创建新的类，提高代码的重用性，程序的可维护性，节省大量创建新类的时间 ，提高开发效率。
   - 三个要点：
      - ⼦类拥有⽗类对象所有的属性和⽅法（包括私有属性和私有⽅法），但是⽗类中的私有属性和⽅法⼦类是⽆法访问，只是拥有。
      - ⼦类可以拥有⾃⼰属性和⽅法，即⼦类可以对⽗类进⾏扩展。
      - ⼦类可以⽤⾃⼰的⽅式实现⽗类的⽅法。
- **多态**
   - 多态，表示一个对象具有多种的状态，具体表现为，父类的引用 指向 子类的实例。
      - ⼀个引⽤变量到底会指向哪个类的实例对象，该引⽤变量发出的⽅法调⽤到底是哪个类中实现的⽅法，必须在由程序运⾏期间才能决定。
   - 在 Java 中有两种形式可以实现多态：
      - 继承（多个⼦类对同⼀⽅法的重写）
      - 接⼝（实现接⼝并覆盖接⼝中同⼀⽅法）
   - **多态的特点:**
      - 对象类型和引用类型之间具有 继承（类）/ 实现（接口）的关系；
      - 引用类型变量发出的方法调用的到底是哪个类中的方法，必须在程序运行期间才能确定；
      - 多态不能调用“只在子类存在但在父类不存在”的方法；
      - 如果子类重写了父类的方法，会执行子类覆盖的方法，否则，执行父类的方法。
<a name="HxY3g"></a>
## 重载（overload）和重写（override）的区别？
| 区别点 | 重载overload | 重写override |
| --- | --- | --- |
| 发生范围 | 同一个类 | 子类 |
| 参数列表 | 必须修改 | 一定不能修改 |
| 返回类型 | 可修改 | 子类方法返回值类型应比父类方法返回值类型更小或相等 |
| 异常 | 可修改 | 子类方法声明抛出的异常类应比父类方法声明抛出的异常类更小或相等； |
| 访问修饰符 | 可修改 | 一定不能做更严格的限制（可以降低限制） |
| 发生阶段 | 编译期 | 运行期 |

- 重载和重写都是实现多态的方式，前者实现的是编译时的多态性，而后者实现的是运行时的多态性。
- **重载 (overload)** 就是在**同一个类中，有多个同名方法，他们的参数列表不同，所以调用这个方法时会根据不同的传参来执行不同的逻辑处理**。
   - Java 允许重载任何方法， 而不只是构造器方法。
   - 重载的规则：
      1. 方法名一致，参数列表中参数的顺序，类型，个数不同。
      2. 重载与方法的返回值无关，存在于父类和子类，同类中。
      3. 可以抛出不同的异常，可以有不同修饰符。
- **重写 (override) 发生在运行期，是子类对父类的允许访问的方法（方法名、参数列表必须相同）的实现过程进行重新编写。**
   - 重写的规则
      1. 方法名、参数列表必须相同，子类方法返回值类型应比父类方法返回值类型更小或相等，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类。
      2. 如果父类方法访问修饰符为 private/final/static 则子类就不能重写该方法，但是被 static 修饰的方法能够被再次声明。
      3. 构造方法无法被重写
   - 关于 **重写的返回值类型** 这里需要额外多说明一下：如果方法的返回类型是 void 和基本数据类型，则返回值重写时不可修改。但是如果方法的返回值是引用类型，重写时是可以返回该引用类型的子类的。
```java
public class Hero {
    public String name() {
        return "超级英雄";
    }
}
public class SuperMan extends Hero{
    @Override
    public String name() {
        return "超人";
    }
    public Hero hero() {
        return new Hero();
    }
}

public class SuperSuperMan extends SuperMan {
    public String name() {
        return "超级超级英雄";
    }

    @Override
    public SuperMan hero() {
        return new SuperMan();
    }
}
```
<a name="a4Vq3"></a>
## 什么是可变长参数？

- 从 Java5 开始，Java 支持定义可变长参数，所谓可变长参数就是允许在调用方法时传入不定长度的参数。就比如下面的这个 printVariable 方法就可以接受 0 个或者多个参数。
```java
public static void method1(String... args) {
   //......
}
```

- 另外，可变参数只能作为函数的最后一个参数，但其前面可以有也可以没有任何其他参数。
```java
public static void method2(String arg1, String... args) {
   //......
}
```
<a name="G1cvi"></a>
### 遇到方法重载的情况怎么办呢？会优先匹配固定参数还是可变参数的方法呢？

- 会优先匹配固定参数的方法，因为固定参数的方法匹配度更高。
<a name="Q1k2I"></a>
## 访问修饰符 public、private、protected、以及不写（默认）时的区别？
Java 支持 4 种不同的访问权限。

- **default** (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。可以修饰在类、接口、变量、方法。
- **private** : 在同一类内可见。可以修饰变量、方法。**注意：不能修饰类（外部类）**
- **public** : 对所有类可见。可以修饰类、接口、变量、方法
- **protected** : 对同一包内的类和所有子类可见。可以修饰变量、方法。**注意：不能修饰类（外部类）**。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1682607899374-8c413e5d-861f-4491-95ba-f659bdc12ab2.png#averageHue=%23eff7da&clientId=u18fc352f-d6d4-4&from=paste&height=274&id=udaa9f2ff&originHeight=327&originWidth=840&originalType=binary&ratio=2&rotation=0&showTitle=false&size=45223&status=done&style=none&taskId=u559012bb-2249-492d-98e0-d5e2daa97b9&title=&width=704)
<a name="mxcS1"></a>
## this 关键字？

- this 是自身的一个对象，代表对象本身，可以理解为：**指向对象本身的一个指针**。
- 3 种用法：
   - 普通的直接引用，this 相当于是指向当前对象本身
   - 形参与成员变量名字重名，用 this 来区分：
```java
public Person(String name,int age){
    this.name=name;
    this.age=age;
}
```

   - 引用本类的构造函数
<a name="tKz5u"></a>
## 抽象类(abstract class)和接口(interface)有什么区别？

1. 接⼝的⽅法默认是 public ，所有⽅法在接⼝中不能有实现(Java 8 开始接⼝⽅法可以有默认实现），⽽抽象类可以有⾮抽象的⽅法。
2. 接⼝中除了 static 、 final 变量，不能有其他变量，⽽抽象类中则不⼀定。
3. ⼀个类可以实现多个接⼝，但只能实现⼀个抽象类。接⼝⾃⼰本身可以通过 extends 关键字扩展多个接⼝。
4. 接⼝⽅法默认修饰符是 public ，抽象⽅法可以有 public 、 protected 和 default 这些修饰符（抽象⽅法就是为了被重写所以不能使⽤ private 关键字修饰！）。
5. 从设计层⾯来说，抽象是对类的抽象，是⼀种模板设计，⽽接⼝是对⾏为的抽象，是⼀种⾏为的规范。
   1. 在 JDK8 中，接⼝也可以定义静态⽅法，可以直接⽤接⼝名调⽤。实现类和实现是不可以调⽤的。如果同时实现两个接⼝，接⼝中定义了⼀样的默认⽅法，则必须重写，不然会报错。
   2. jdk9 的接⼝被允许定义私有⽅法 。
- 总结⼀下 jdk7~jdk9 Java 中接⼝的变化：
   1. 在 jdk 7 或更早版本中，接⼝⾥⾯只能有常量变量和抽象⽅法。这些接⼝⽅法必须由选择实现接⼝的类实现。
   2. jdk 8 的时候接⼝可以有默认⽅法和静态⽅法功能。
   3. jdk 9 在接⼝中引⼊了私有⽅法和私有静态⽅法。
<a name="pj48r"></a>
## 成员变量与局部变量的区别有哪些？

1. 从**语法形式**上看：成员变量是属于类的，⽽局部变量是在⽅法中定义的变量或是⽅法的参数；成员变量可以被 public , private , static 等修饰符所修饰，⽽局部变量不能被访问控制修饰符及 static 所修饰；但是，成员变量和局部变量都能被 final 所修饰。
2. 从变量在内存中的**存储⽅式**来看：如果成员变量是使⽤ static 修饰的，那么这个成员变量是属于类的，如果没有使⽤ static 修饰，这个成员变量是属于实例的。对象存于堆内存，如果局部变量类型为基本数据类型，那么存储在栈内存，如果为引⽤数据类型，那存放的是指向堆内存对象的引⽤或者是指向常量池中的地址。
3. 从变量在内存中的**⽣存时间**上看：成员变量是对象的⼀部分，它随着对象的创建⽽存在，⽽局部变量随着⽅法的调⽤⽽⾃动消失。
4. 是否有**默认值**：成员变量若没被赋初始值，则会⾃动以类型的默认值⽽赋值（⼀种情况例外:被 final 修饰的成员变量也必须显式地赋值），⽽局部变量则不会⾃动赋值。

成员变量与局部变量代码示例：
```java
public class VariableExample {

    // 成员变量
    private String name;
    private int age;

    // 方法中的局部变量
    public void method() {
        int num1 = 10; // 栈中分配的局部变量
        String str = "Hello, world!"; // 栈中分配的局部变量
        System.out.println(num1);
        System.out.println(str);
    }

    // 带参数的方法中的局部变量
    public void method2(int num2) {
        int sum = num2 + 10; // 栈中分配的局部变量
        System.out.println(sum);
    }

    // 构造方法中的局部变量
    public VariableExample(String name, int age) {
        this.name = name; // 对成员变量进行赋值
        this.age = age; // 对成员变量进行赋值
        int num3 = 20; // 栈中分配的局部变量
        String str2 = "Hello, " + this.name + "!"; // 栈中分配的局部变量
        System.out.println(num3);
        System.out.println(str2);
    }
}
```
<a name="muEXG"></a>
## 静态变量和实例变量的区别？
**静态变量:** 是被 static 修饰符修饰的变量，也称为类变量，它属于类，不属于类的任何一个对象，一个类不管创建多少个对象，静态变量在内存中有且仅有一个副本。<br />**实例变量:** 必须依存于某一实例，需要先创建对象然后通过对象才能访问到它。静态变量可以实现让多个对象共享内存。
<a name="oAy1S"></a>
## 静态⽅法和实例⽅法的区别?
类似地。<br />**静态方法**：static 修饰的方法，也被称为类方法。在外部调⽤静态⽅法时，可以使⽤"**类名.⽅法名**"的⽅式，也可以使⽤"**对象名.⽅法名**"的⽅式。静态方法里不能访问类的非静态成员变量和方法。<br />**实例⽅法**：依存于类的实例，需要使用"**对象名.⽅法名**"的⽅式调用；可以访问类的所有成员变量和方法。
<a name="GS1d1"></a>
## final 关键字有什么作用？
final 表示不可变的意思，可用于修饰类、属性和方法：

- 被 final 修饰的**类不可以被继承**
- 被 final 修饰的**方法不可以被重写**
- 被 final 修饰的**变量不可变**，被 final 修饰的变量必须被显式第指定初始值。注意这里不可变指的是**变量的引用不可变，不是引用指向的内容的不可变**。例如：
```java
final StringBuilder sb = new StringBuilder("abc");
sb.append("d");
System.out.println(sb);  //abcd
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1682950341709-8cac8516-f672-4849-83af-6124efff2d26.png#averageHue=%23f0f5dc&clientId=ue4afb669-0e3a-4&from=paste&height=207&id=u88f96506&originHeight=341&originWidth=849&originalType=binary&ratio=2&rotation=0&showTitle=false&size=39498&status=done&style=none&taskId=u8e3cff26-eacc-4b7f-98a3-2fdb53ee993&title=&width=516.5)
<a name="OaJjl"></a>
## final、finally、finalize 区别？

- **final** 用于**修饰变量、方法和类**：final 修饰的类不可被继承；修饰的方法不可被重写；修饰的变量不可变。
- **finally **作为**异常处理**的一部分，它只能在 try/catch 语句中，并且附带一个语句块表示这段语句最终一定被执行（无论是否抛出异常），经常被用在需要释放资源的情况下，System.exit (0) 可以阻断 finally 执行。
- **finalize** 是在 java.lang.Object 里定义的方法，也就是说每一个对象都有这么个方法，这个方法在 gc 启动，该**对象被回收的时候被调用**。一个对象的 finalize 方法只会被调用一次，finalize 被调用不一定会立即回收该对象，所以有可能调用 finalize 后，该对象又不需要被回收了，然后到了真正要被回收的时候，因为前面调用过一次，所以不会再次调用 finalize 了，进而产生问题，因此不推荐使用 finalize 方法。
<a name="QTlem"></a>
## == 、equals 区别？

- **== **: 
   - 它的作⽤是判断两个对象的**地址**是不是相等。即，判断两个对象是不是同⼀个对象。
   - 基本数据类型 **==** 比较的是值，引⽤数据类型 **==** 比较的是内存地址。
- **equals()** : 它的作⽤也是判断两个**对象**是否相等。但是这个“相等”一般也分两种情况：
   - **默认**情况：类没有覆盖 equals() ⽅法。则通过 equals() 比较该类的两个对象时，等价于通过“ **==** ”比较这两个对象，还是相当于比较**两个对象的内存地址**。
   - **自定义**情况：类覆盖了 equals() ⽅法。我们平时覆盖的 equals()方法一般是比较**两个对象的内容**是否相同，自定义了一个相等的标准，也就是两个对象的值是否相等。
      - 举个自定义的例⼦，Person，我们认为两个人的编号和姓名相同，就是一个人：
```java
public class Person {
    private String no;
    private String name;

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Person)) return false;
        Person person = (Person) o;
        return Objects.equals(no, person.no) &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(no, name);
    }
}
```
<a name="rlO0G"></a>
## hashCode 与 equals?
“你重写过 hashcode 和 equals 么，为什么重写 equals 时必须重写 hashCode ⽅法？”
<a name="orTlp"></a>
### 什么是 HashCode？
hashCode() 的作⽤是获取哈希码，也称为散列码；它实际上是返回⼀个 int 整数，定义在 Object 类中， 是一个本地⽅法，将对象的内存地址转换为整数之后返回。
```java
public native int hashCode();
```
哈希码主要在哈希表这类集合映射的时候用到，哈希表存储的是键值对(key-value)，它的特点是：能根据“键”快速的映射到对应的“值”。这其中就利⽤到了哈希码！
<a name="yipVn"></a>
### 为什么要有 hashCode？
上面已经讲了，主要是在哈希表这种结构中用的到。<br />例如 HashMap 怎么把 key 映射到对应的 value 上呢？用的就是哈希取余法，也就是拿哈希码和存储元素的数组的长度取余，获取 key 对应的 value 所在的下标位置。
<a name="LUi66"></a>
### 为什么重写 equals 时必须重写 hashCode ⽅法？
如果两个对象相等，则 hashcode ⼀定也是相同的。两个对象相等，对两个对象分别调⽤ equals ⽅法都返回 true。反之，两个对象有相同的 hashcode 值，它们也不⼀定是相等的 。因此，**equals** ⽅法被覆盖过，则 **hashCode** ⽅法也必须被覆盖。<br />hashCode() 的默认⾏为是对堆上的对象产⽣独特值。如果没有重写 hashCode() ，则该 class 的两个对象⽆论如何都不会相等（即使这两个对象指向相同的数据）
<a name="aqPG8"></a>
### 为什么两个对象有相同的 hashcode 值，它们也不⼀定是相等的？
因为可能会**碰撞**， hashCode() 所使⽤的散列算法也许刚好会让多个对象传回相同的散列值。越糟糕的散列算法越容易碰撞，但这也与数据值域分布的特性有关（所谓碰撞也就是指的是不同的对象得到相同的 hashCode ）。
<a name="ypIS3"></a>
## Java 是值传递，还是引用传递？
**值传递**。<br />Java 语言的**方法调用**只支持参数的值传递。当一个对象实例作为参数被传递到方法里时，参数的值就是对该对象的引用。对象的属性可以在被调用过程中被改变，但对对象引用的改变是不会影响到调用者的。<br />JVM 的内存分为 堆和栈，其中栈里存了基本数据类型&引用数据类型实例的地址，也就是对象地址。<br />而对象所占的空间是在堆中开辟的，所以传递的时候可以理解为把变量存储的对象地址给传递过去，因此引用类型也是值传递。
<a name="X6v31"></a>
## 深拷贝和浅拷贝?

- **浅拷贝**：仅拷贝被拷贝对象的成员变量的值，也就是基本数据类型变量的值，和引用数据类型变量的地址值，而对于引用类型变量指向的堆中的对象不会拷贝。
- **深拷贝**：完全拷贝一个对象，拷贝被拷贝对象的成员变量的值，堆中的对象也会拷贝一份。

例如现在有一个 order 对象，里面有一个 products 列表，它的浅拷贝和深拷贝的示意图：<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1683041234436-58bcfc48-9f5f-433b-bc4c-df5477f23193.png#averageHue=%23f5f7e3&clientId=u93913cc4-e730-4&from=paste&id=ud2b9b370&originHeight=515&originWidth=1127&originalType=url&ratio=2&rotation=0&showTitle=false&size=63894&status=done&style=none&taskId=u7ee2636c-66d0-4dd6-9fd6-126b2a217f4&title=)<br />浅拷贝和深拷贝示意图<br />因此深拷贝是安全的，浅拷贝的话如果有引用类型，那么拷贝后对象，引用类型变量修改，会影响原对象。
<a name="i5gRA"></a>
### 浅拷贝如何实现？
Object 类提供的 clone()方法可以非常简单地实现对象的浅拷贝。
<a name="NH7ji"></a>
### 深拷贝如何实现？

- 重写克隆方法：重写克隆方法，引用类型变量单独克隆，这里可能会涉及多层递归。
- 序列化：可以先将原对象序列化，再反序列化成拷贝对象。
<a name="b4bfu"></a>
## Java 创建对象有哪几种方式？

- new 创建新对象
- 通过反射机制
- 采用 clone 机制（需要注意浅拷贝和深拷贝的区别）
- 通过序列化机制（可以通过实现 Externalizable 或者 Serializable）

前两者都需要**显式地调用构造方法**。对于 clone 机制,需要注意浅拷贝和深拷贝的区别，对于序列化机制需要明确其实现原理，在 Java 中序列化可以通过实现 Externalizable 或者 Serializable 来实现。
<a name="UdyUU"></a>
# String
<a name="XuCQ3"></a>
## String 是 Java 基本数据类型吗？
不是。Java 中的基本数据类型只有 8 个：byte、short、int、long、float、double、char、boolean；其他都是引用类型（reference type）。<br />String 是特殊的引用数据类型。<br />字符串使用 final 声明的话，可以让编译器当做常量来处理，作为优化。如果编译器在运行时才能知道其确切值的话，就无法对其优化。所以就算是 final 也仍需要是确切值。
```java
final String str1 = "str";
final String str2 = "ing";
// 下面两个表达式其实是等价的
String c = "str" + "ing";// 常量池中的对象
String d = str1 + str2; // 常量池中的对象
System.out.println(c == d);// true
```
```java
final String str1 = "str";
final String str2 = getStr();
String c = "str" + "ing";// 常量池中的对象
String d = str1 + str2; // 在堆上创建的新的对象
System.out.println(c == d);// false
public static String getStr() {
      return "ing";
}
```
<a name="heXEy"></a>
## String 类可以被继承吗？
不行。String 类使用 final 修饰，是所谓的不可变类，无法被继承。
<a name="mAQz7"></a>
## String 和 StringBuilder、StringBuffer 的区别？

- String：String 被创建后不能修改，任何修改都会引发新的 String 对象的生成。
- StringBuffer：跟 String 类似，但是值可以被修改，使用 synchronized 来保证线程安全。
- StringBuilder：StringBuffer 的非线程安全版本，性能上更高一些。
<a name="KvKrP"></a>
## 字符串常量池是？
**字符串常量池** 是 JVM 为了提升性能和减少内存消耗针对字符串（String 类）专门开辟的一块区域，主要目的是为了避免字符串的重复创建。字符串常量池里相同的字符串只会有一个，没有重复的。
<a name="vDvjr"></a>
## `String s1 = new String("abc")`和`String s2 = "abc"`区别？

- `String s2 = "abc"`，创建一个常量池里的（看是否已经存在，有就不用）。
- `String s1 = new String("abc")`，创建一个常量池里的（看是否已经存在，有就不用）和一个堆上的对象实例。

下面是解释：字符串常量池里相同的字符串只会有一个，没有重复的。<br />所以`String s2 = "abc"`看常量池有没有，若有就直接用，若没有就在常量池中创建 “abc” 对象。<br />而`String s1 = new String("abc")`，也是先看常量池有没有。

- 若字符串常量池已经有“abc”，则只在堆创建一个 "abc" 字符串对象实例。
- 若字符串常量池还没有 “abc”，此时会创建如下两个对象：
   - 一个是字符串字面量 "abc" 所对应的、字符串常量池中的实例
   - 另一个是通过 new String() 在堆里创建的一个 "abc" 字符串对象实例。
<a name="d8YZy"></a>
## String 不是不可变类吗？字符串拼接是如何实现的？
是不可变的。“**+**”的拼接操作，其实是生成新对象。<br />在**jdk1.8 之前**，a 和 b 初始化时位于字符串常量池，ab 拼接后的对象位于堆中。经过拼接新生成了 String 对象。如果拼接多次，那么会生成多个中间对象。<br />在 **Java8 时 **JDK 对“+”号拼接进行了优化，在编译期基于 StringBuilder 的 append 方法对“+”号进行处理。但循环里拼接还是建议用 StringBuilder，因为循环一次就会创建一个新的 StringBuilder 对象。
<a name="jc59U"></a>
## intern 方法的作用？
String.intern() 是一个 native（本地）方法，作用是把 指定的字符串对象的引用 保存在 字符串常量池：

- 如果字符串常量池中保存了对应的字符串对象的引用，就直接返回该引用。
- 如果字符串常量池中没有保存了对应的字符串对象的引用，那就在常量池中创建一个指向该字符串对象的引用并返回。
```java
// 在堆中创建字符串对象”Java“
// 将字符串对象”Java“的引用保存在字符串常量池中
String s1 = "Java";
// 直接返回字符串常量池中字符串对象”Java“对应的引用
String s2 = s1.intern();
// 会在堆中在单独创建一个字符串对象
String s3 = new String("Java");
// 直接返回字符串常量池中字符串对象”Java“对应的引用
String s4 = s3.intern();

// s1 和 s2 指向的是堆中的同一个对象
System.out.println(s1 == s2); // true
// s3 和 s4 指向的是堆中不同的对象
System.out.println(s3 == s4); // false
// s1 和 s4 指向的是堆中的同一个对象
System.out.println(s1 == s4); //true
```
<a name="R7zC0"></a>
# Integer
<a name="bFUob"></a>
## Integer a= 127，Integer b = 127；Integer c= 128，Integer d = 128；，相等吗?
a 和 b 相等，c 和 d 不相等。原因是：

- 对于基本数据类型==比较的是值
- 对于引用数据类型==比较的是地址

Int 自动装箱的机制：自动装箱时会去缓存池里取 Integer 对象，没取到才会创建新对象。<br />如果整型字面量的值在 -128 到 127 之间，那么自动装箱时不会 new 新的 Integer 对象，而是直接引用缓存池中的 Integer 对象，超过范围 a1==b1 的结果是 false。
<a name="G6MsR"></a>
## IntegerCache是？
一个静态内部类，默认范围是 -128 到 127。可以设置 AutoBoxCacheMax 来修改缓存最大值，最小值改不了。int 在自动装箱的时候会调用 Integer.valueOf，而 valueOf 用到了 IntegerCache，就是判断值是否在缓存范围内，若在就去 IntegerCache 中取，不在就创建一个新的 Integer 对象。
<a name="erttv"></a>
## String 怎么转成 Integer 的？原理？

- Integer.parseInt(String s)
- Integer.valueOf(String s)

这俩最后都是调用 Integer 类内中的parseInt(String s, int radix)方法。
<a name="H7yAv"></a>
# Object
<a name="TaAAx"></a>
## Object 类的常见方法?
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684242257851-1ec025d2-75d2-44fd-9f2a-4112a9e4c113.png#averageHue=%23fdefe3&clientId=uafd271d6-e9be-4&from=paste&height=540&id=ua83f5018&originHeight=800&originWidth=1006&originalType=binary&ratio=2&rotation=0&showTitle=false&size=90204&status=done&style=none&taskId=ubb167eda-a6e6-4e52-bcc6-baa1e347131&title=&width=679)<br />**对象比较**：

- public native int hashCode() ：native 方法，用于返回对象的哈希码，主要使用在哈希表中，比如 JDK 中的 HashMap。
- public boolean equals(Object obj)：用于比较对象的内存地址是否相等，String 类对这个方法进行了重写用户比较字符串的值是否相等。

**对象拷贝**：

- protected native Object clone() throws CloneNotSupportedException：native 方法，用于创建并返回当前对象的一份拷贝。一般情况下，对于任何对象 x，表达式 x.clone() != x 为 true，x.clone().getClass() == x.getClass() 为 true。Object 本身没有实现 Cloneable 接口，所以不重写 clone 方法并且进行调用的话会发生 CloneNotSupportedException 异常。

**对象转字符串：**

- public String toString()：返回类的名字@实例的哈希码的 16 进制的字符串。建议 Object 所有的子类都重写这个方法。

**多线程调度：**

- public final native void notify()：native 方法，并且不能重写。唤醒一个在此对象监视器上等待的线程(监视器相当于就是锁的概念)。如果有多个线程在等待只会任意唤醒一个。
- public final native void notifyAll()：native 方法，并且不能重写。跟 notify 一样，唯一的区别就是会唤醒在此对象监视器上等待的所有线程，而不是一个线程。
- public final native void wait(long timeout) throws InterruptedException：native 方法，并且不能重写。暂停线程的执行。注意：sleep 方法没有释放锁，而 wait 方法释放了锁 。timeout 是等待时间。
- public final void wait(long timeout, int nanos) throws InterruptedException：多了 nanos 参数，这个参数表示额外时间（以毫微秒为单位，范围是 0-999999）。 所以超时的时间还需要加上 nanos 毫秒。
- public final void wait() throws InterruptedException：跟之前的 2 个 wait 方法一样，只不过该方法一直等待，没有超时时间这个概念

**反射：**

- public final native Class<?> getClass()：native 方法，用于返回当前运行时对象的 Class 对象，使用了 final 关键字修饰，故不允许子类重写。

**垃圾回收：**

- protected void finalize() throws Throwable ：通知垃圾收集器回收对象。
<a name="PrUcm"></a>
# 异常处理
<a name="paEWf"></a>
## Java 中异常处理体系?
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684243422141-4fa330b2-b2a8-4c3b-9b98-f075c02f9012.png#averageHue=%23fceee9&clientId=uafd271d6-e9be-4&from=paste&height=354&id=u8e78d7b0&originHeight=707&originWidth=1290&originalType=binary&ratio=2&rotation=0&showTitle=false&size=87772&status=done&style=none&taskId=u38eb786e-f126-4d6b-9e1a-7738c390868&title=&width=645)<br />Throwable是 Java 语言中所有错误或异常的基类。 Throwable 又分为Error和Exception，其中 Error 是系统内部错误，比如虚拟机异常，是程序无法处理的。Exception是程序问题导致的异常，又分为两种：

- CheckedException 受检异常：编译器会强制检查并要求处理的异常。
- RuntimeException 运行时异常：程序运行中出现异常，比如我们熟悉的空指针、数组下标越界等等
<a name="ytoUq"></a>
## Throwable 类常用方法有哪些？

- String getMessage(): 返回异常发生时的简要描述
- String toString(): 返回异常发生时的详细信息
- String getLocalizedMessage(): 返回异常对象的本地化信息。使用 Throwable 的子类覆盖这个方法，可以生成本地化信息。如果子类没有覆盖该方法，则该方法返回的信息与 getMessage()返回的结果相同
- void printStackTrace(): 在控制台上打印 Throwable 对象封装的异常信息
<a name="VSulW"></a>
## 异常的处理方式？
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684243594558-baf71522-f61b-48b7-90db-c3d4cdaf9395.png#averageHue=%23fefefe&clientId=uafd271d6-e9be-4&from=paste&height=204&id=uc3c37ac3&originHeight=329&originWidth=819&originalType=binary&ratio=2&rotation=0&showTitle=false&size=32225&status=done&style=none&taskId=u23c1a61b-d0d9-44c8-b4c5-37c905e315d&title=&width=508.5)<br />**遇到异常不进行具体处理，而是继续抛给调用者 （throw，throws）**<br />抛出异常有三种形式，一是 throw,一个 throws，还有一种系统自动抛异常。

- throws 用在方法上，后面跟的是异常类，可以跟多个
- throw 用在方法内，后面跟的是异常对象。
<a name="TZiIs"></a>
## try-catch-finally？

- try块：用于捕获异常。其后可接零个或多个 catch 块，如果没有 catch 块，则必须跟一个 finally 块。
- catch块：用于处理 try 捕获到的异常。
- finally 块：无论是否捕获或处理异常，finally 块里的语句都会被执行。当在 try 块或 catch 块中遇到 return 语句时，finally 语句块将在方法返回之前被执行。

**注意：不要在 finally 语句块中使用 return!** 当 try 语句和 finally 语句中都有 return 语句时，try 语句块中的 return 语句会被忽略。这是因为 try 语句中的 return 返回值会先被暂存在一个本地变量中，当执行到 finally 语句中的 return 之后，这个本地变量的值就变为了 finally 语句中的 return 返回值。
```java
try {
    //包含可能会出现异常的代码以及声明异常的方法
}
catch(Exception e) {
    //捕获异常并进行处理
}
finally {                                                       
    //可选，不管是否有问题，都一定会再返回之前执行的代码
}
```
<a name="YmnN9"></a>
### finally 中的代码一定会执行吗？
不一定！在某些情况，finally 中的代码不会被执行。<br />比如 finally 之前虚拟机被终止运行/ 程序所在的线程死亡/ 关闭 CPU。
<a name="J3Nuy"></a>
## 三道经典异常处理代码题

- 题目 1
```java
public class TryDemo {
    public static void main(String[] args) {
        System.out.println(test());
    }
    public static int test() {
        try {
            return 1;
        } catch (Exception e) {
            return 2;
        } finally {
            System.out.print("3");
        }
    }
}
```
执行结果：31。<br />try、catch。finally 的基础用法，在 return 前会先执行 finally 语句块，所以是先输出 finally 里的 3，再输出 return 的 1。

- 题目 2
```java
public class TryDemo {
    public static void main(String[] args) {
        System.out.println(test1());
    }
    public static int test1() {
        try {
            return 2;
        } finally {
            return 3;
        }
    }
}
```
执行结果：3。<br />try 返回前先执行 finally，结果 finally 里不按套路出牌，直接 return 了，自然也就走不到 try 里面的 return 了。<br />finally 里面使用 return 仅存在于面试题中，实际开发这么写要挨吊的。

- 题目 3
```java
public class TryDemo {
    public static void main(String[] args) {
        System.out.println(test1());
    }
    public static int test1() {
        int i = 0;
        try {
            i = 2;
            return i;
        } finally {
            i = 3;
        }
    }
}
```
执行结果：2。<br />大家可能会以为结果应该是 3，因为在 return 前会执行 finally，而 i 在 finally 中被修改为 3 了，那最终返回 i 不是应该为 3 吗？<br />但其实，在执行 finally 之前，JVM 会先将 i 的结果暂存起来，然后 finally 执行完毕后，会返回之前暂存的结果，而不是返回 i，所以即使 i 已经被修改为 3，最终返回的还是之前暂存起来的结果 2。
<a name="mHePF"></a>
## 如何使用 try-with-resources 代替 try-catch-finally？

- **适用范围（资源的定义）：** 任何实现 java.lang.AutoCloseable或者 java.io.Closeable 的对象
- **关闭资源和 finally 块的执行顺序：** 在 try-with-resources 语句中，任何 catch 或 finally 块在声明的资源关闭后运行
- [具体](https://javaguide.cn/java/basis/java-basic-questions-03.html#%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-try-with-resources-%E4%BB%A3%E6%9B%BFtry-catch-finally)
<a name="DcCn4"></a>
## 异常使用有哪些需要注意的地方？

- 不要把异常定义为静态变量，因为这样会导致异常栈信息错乱。每次手动抛出异常，我们都需要手动 new 一个异常对象抛出。
- 抛出的异常信息一定要有意义。
- 建议抛出更加具体的异常比如字符串转换为数字格式错误的时候应该抛出NumberFormatException而不是其父类IllegalArgumentException。
- 使用日志打印异常之后就不要再抛出异常了（两者不要同时存在一段代码逻辑中）。
- ......
<a name="Z7rd6"></a>
# I/O
<a name="y6ac3"></a>
## Java 中 IO 流分为几种?
分类方式：

- 按 流的流向：**输入流** **输出流**
- 按 操作单元：**字节流** **字符流**
- 按 流的角色：**节点流** **处理流**

IO 流的 40 多个类都是从这 4 个抽象类基类里派生出来的：

- 输入流的基类
   - InputStream: 字节输入流
   - Reader: 字符输入流
- 输出流的基类
   - OutputStream: 字节输出流
   - Writer: 字符输出流

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684244877753-10957f01-4b8c-44e8-8e55-e8696407cc45.png#averageHue=%23fcfbf6&clientId=uafd271d6-e9be-4&from=paste&height=917&id=u17218c8a&originHeight=1080&originWidth=720&originalType=binary&ratio=2&rotation=0&showTitle=false&size=426453&status=done&style=none&taskId=u94ad4923-057b-46a9-b5ec-3350d587b80&title=&width=611)
<a name="FMhjB"></a>
## 既然有了字节流,为什么还要有字符流?
问题本质想问：**不管是文件读写还是网络发送接收，信息的最小存储单元都是字节，那为什么 I/O 流操作要分为字节流操作和字符流操作呢？**

- 因为字节流转换成字符流，过程很耗时。 如果你必须要使用字符流，但你只得到了字节流，就要经历这个转换，其中编码也容易出问题。 
- 所以 I/O 流干脆提供了一个直接操作字符的接口，从而提高使用字符流的效率。
- 如果**涉及到字符**的话用**字符流**更好，如果是**音频文件、图片等媒体文件**用**字节流**更好。
<a name="l0A8O"></a>
## IO 流用到了什么设计模式？（待补充 [具体可看](https://javaguide.cn/java/io/io-design-patterns.html)）
**装饰器模式**。<br />InputStream 相关的部分类图如下。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684244944400-85ff28dc-d1e6-47c6-883f-19e76e586ad6.png#averageHue=%23fcfbf4&clientId=uafd271d6-e9be-4&from=paste&height=307&id=u005a769c&originHeight=455&originWidth=1015&originalType=binary&ratio=2&rotation=0&showTitle=false&size=40389&status=done&style=none&taskId=u92e9005e-c83a-415d-8b24-6e648ee1993&title=&width=685.5)<br />**装饰器模式** 更侧重于动态地增强原始类的功能，装饰器类需要跟原始类继承相同的抽象类或者实现相同的接口。并且，装饰器模式支持对原始类嵌套使用多个装饰器。
<a name="OWblv"></a>
## BIO、NIO、AIO？（[具体可看](https://javaguide.cn/java/io/io-model.html#java-%E4%B8%AD-3-%E7%A7%8D%E5%B8%B8%E8%A7%81-io-%E6%A8%A1%E5%9E%8B)）
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684674810616-d306c297-75e6-4579-b8ea-e3b16dad4712.png#averageHue=%23d7d5d5&clientId=u12878bdb-6efd-4&from=paste&height=562&id=u2d29fb4e&originHeight=1124&originWidth=1184&originalType=binary&ratio=2&rotation=0&showTitle=false&size=98612&status=done&style=none&taskId=u2837ebbb-85f4-4a69-9ecf-e052163b05e&title=&width=592)<br />**BIO**(blocking I/O) ： 就是传统的 IO，同步阻塞，服务器实现模式为一个连接一个线程，即**客户端有连接请求时服务器端就需要启动一个线程进行处理**，如果这个连接不做任何事情会造成不必要的线程开销，可以通过连接池机制改善(实现多个客户连接服务器)。<br />BIO 方式适用于连接数目比较小且固定的架构，这种方式对服务器资源要求比较高，并发局限于应用中，JDK1.4 以前的唯一选择，程序简单易理解。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684245860995-d0d26889-76fc-4769-83ed-916ec4092815.png#averageHue=%23f5b785&clientId=uafd271d6-e9be-4&from=paste&height=151&id=ub1813f89&originHeight=464&originWidth=546&originalType=binary&ratio=2&rotation=0&showTitle=false&size=100753&status=done&style=none&taskId=ucd68b4cc-6792-415d-9cae-8854300e843&title=&width=178)![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684245957921-ef84fe95-8aa4-4cb9-84d6-c79cc0ec785c.png#averageHue=%23b9e386&clientId=uafd271d6-e9be-4&from=paste&height=233&id=u2d426898&originHeight=347&originWidth=705&originalType=binary&ratio=2&rotation=0&showTitle=false&size=30052&status=done&style=none&taskId=ub38a1cfe-af36-4692-af0c-56e68a96c5c&title=&width=473)<br />**NIO** ：全称 java non-blocking IO，是指 JDK 提供的新 API。从 JDK1.4 开始，Java 提供了一系列改进的输入/输出的新特性，被统称为 NIO(即 New IO)。<br />NIO 是**同步非阻塞**的，服务器端用一个线程处理多个连接，客户端发送的连接请求会注册到多路复用器上，多路复用器轮询到连接有 IO 请求就进行处理：<br />NIO 的数据是面向**缓冲区 Buffer**的，必须从 Buffer 中读取或写入。<br />NIO 的运行机制：

- 每个 Channel 对应一个 Buffer。
- Selector 对应一个线程，一个线程对应多个 Channel。
- Selector 会根据不同的事件，在各个通道上切换。
- Buffer 是内存块，底层是数据。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684245871295-5a0f1bf9-d4a0-4f4a-a405-447188e65486.png#averageHue=%23e6f3ed&clientId=uafd271d6-e9be-4&from=paste&height=115&id=ud087ab23&originHeight=356&originWidth=548&originalType=binary&ratio=2&rotation=0&showTitle=false&size=76783&status=done&style=none&taskId=u04945f4a-35ee-4317-9562-78314d44fd5&title=&width=177)![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684245987483-8549667e-8b50-485a-b94c-8661ce3ee0c1.png#averageHue=%23fcf9f8&clientId=uafd271d6-e9be-4&from=paste&height=204&id=u682fb806&originHeight=326&originWidth=871&originalType=binary&ratio=2&rotation=0&showTitle=false&size=41945&status=done&style=none&taskId=u7c194bb2-b73f-4e17-ac7c-56fcc2e5629&title=&width=544)<br />**AIO**：JDK 7 引入了 Asynchronous I/O，是**异步不阻塞**的 IO。在进行 I/O 编程中，常用到两种模式：Reactor 和 Proactor。Java 的 NIO 就是 Reactor，当有事件触发时，服务器端得到通知，进行相应的处理，完成后才通知服务端程序启动线程去处理，一般适用于连接数较多且连接时间较长的应用。<br />异步 IO 是基于事件和回调机制实现的，也就是应用操作之后会直接返回，不会堵塞在那里，当后台处理完成，操作系统会通知相应的线程进行后续的操作。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684245886761-4aa61140-a8d0-41a9-8d6f-2daec3cf981a.png#averageHue=%23a8cafa&clientId=uafd271d6-e9be-4&from=paste&height=135&id=u794e1c71&originHeight=400&originWidth=542&originalType=binary&ratio=2&rotation=0&showTitle=false&size=78649&status=done&style=none&taskId=u982589da-2b0d-49da-a94a-65ab9ff3f34&title=&width=183)
<a name="Syf0R"></a>
# 序列化
<a name="XgG4s"></a>
## 什么是序列化？什么是反序列化？
如果我们需要持久化 Java 对象比如将 Java 对象保存在文件中，或者在网络传输 Java 对象，这些场景都需要用到序列化。类比我们生活中一些大件物品的运输，运输的时候把它拆了打包，用的时候再拆包组装。**序列化的主要目的是通过网络传输对象或者说是将对象存储到文件系统、数据库、内存中。**<br />**序列化**：**把 Java 对象转为二进制流**，方便存储和传输。<br />**反序列化：把二进制流恢复成对象**。<br />常见应用场景：

- 对象在进行网络传输（比如远程方法调用 RPC 的时候）之前需要先被序列化，接收到序列化的对象之后需要再进行反序列化；
- 将对象存储到文件之前需要进行序列化，将对象从文件中读取出来需要进行反序列化；
- 将对象存储到数据库（如 Redis）之前需要用到序列化，将对象从缓存数据库中读取出来需要反序列化；
- 将对象存储到内存之前需要进行序列化，从内存中读取出来之后需要进行反序列化。
<a name="lLSKh"></a>
### Serializable 接口有什么用？
这个接口只是一个标记，没有具体的作用，但是如果不实现这个接口，在有些序列化场景会报错，所以一般建议，创建的 JavaBean 类都实现 Serializable。
<a name="dFOAV"></a>
### serialVersionUID 又有什么用？
serialVersionUID 就是起验证作用。
```java
private static final long serialVersionUID = 1L;
```
我们经常会看到这样的代码，这个 ID 其实就是用来验证序列化的对象和反序列化对应的对象 ID 是否一致。<br />这个 ID 的数字其实不重要，无论是 1L 还是 IDE 自动生成的，只要序列化和反序列化的时候，对象的 serialVersionUID 相同就行。<br />如果没有显示指定 serialVersionUID ，则编译器会根据**类的相关信息**自动生成一个，可以认为是一个指纹。<br />所以如果你没有定义一个 serialVersionUID， 结果序列化一个对象之后，在反序列化之前把对象的类的结构改了，比如增加了一个成员变量，那反序列化就会失败。因为类的结构变了，所以 serialVersionUID 就不一致。
<a name="JgtNp"></a>
### Java 序列化不包含静态变量？
序列化的时候是不包含静态变量的。
<a name="jIYNw"></a>
### 如果有些变量不想序列化，怎么办？
对于不想进行序列化的变量，使用 **transient** 关键字修饰。<br />transient 关键字的作用是：阻止实例中那些用此关键字修饰的的变量序列化；当对象被反序列化时，被 transient 修饰的变量值不会被持久化和恢复。transient 只能修饰变量，不能修饰类和方法。
<a name="bD9eK"></a>
## 序列化协议对应于 TCP/IP 4 层模型的哪一层？
我们知道网络通信的双方必须要采用和遵守相同的协议。TCP/IP 四层模型是下面这样的，序列化协议属于哪一层呢？

- TCP/IP 四层模型
   1. 应用层 ✅
   2. 传输层
   3. 网络层
   4. 网络接口层
- **OSI 七层**协议模型

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1684677990991-414c82b4-a731-45bb-8f7f-c573bf608682.png#averageHue=%23f5f4f3&clientId=u12878bdb-6efd-4&from=paste&id=ubaade632&originHeight=469&originWidth=818&originalType=url&ratio=2&rotation=0&showTitle=false&size=77997&status=done&style=none&taskId=u8f7aaecb-262f-465e-9f70-326a282ff8b&title=)<br />**OSI 七层**协议模型中，**表示层✅ **做的事情主要就是对应用层的用户数据进行处理转换为二进制流。反过来的话，就是将二进制流转换成应用层的用户数据。这不就对应的是序列化和反序列化么？<br />因为，OSI 七层协议模型中的应用层、表示层和会话层对应的都是 TCP/IP 四层模型中的应用层，所以序列化协议属于**TCP/IP 四层**模型的**应用层**。
<a name="W223Q"></a>
## 序列化方式有哪几种？

- **Java 对象序列化**：Java 原生序列化方法即通过 Java 原生流（InputStream 和 OutputStream 之间的转化）的方式进行转化，一般是对象输出流 ObjectOutputStream 和对象输入流 ObjectInputStream。
- **Json 序列化**：这个可能是我们最常用的序列化方式，Json 序列化的选择很多，一般会使用 jackson 包，通过 ObjectMapper 类来进行一些操作，比如将对象转化为 byte 数组或者将 json 串转化为对象。
- **ProtoBuff 序列化**：ProtocolBuffer 是一种轻便高效的结构化数据存储格式，ProtoBuff 序列化对象可以很大程度上将其压缩，可以大大减少数据传输大小，提高系统性能。
<a name="Hu9Cn"></a>
# 泛型
<a name="BBYkB"></a>
## Java 泛型是？
**Java 泛型（Generics）**可以增强代码的可读性以及稳定性，是 JDK 5 中引入的新特性。<br />编译器可以对 泛型参数 进行检测，并且通过 泛型参数 可指定传入对象的类型。比如 ArrayList<Person> persons = new ArrayList<Person>() 这行代码就指明了该 ArrayList 对象只能传入 Person 对象，如果传入其他类型的对象就会报错。
```java
ArrayList<E> extends AbstractList<E>
```
并且，原生 List 返回类型是 Object ，需要手动转换类型才能使用，使用泛型后编译器会自动转换。
<a name="M5qUF"></a>
## 泛型有哪几种使用方式？
有三种: **泛型类**、**泛型接口**、**泛型方法**。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685113607040-99b141c6-ca5f-41a7-91e7-eb3f8e35cfb7.png#averageHue=%23ecdf8e&clientId=ufe80384a-fda5-4&from=paste&height=327&id=uab7812fc&originHeight=410&originWidth=795&originalType=binary&ratio=2&rotation=0&showTitle=false&size=33242&status=done&style=none&taskId=ueef6b8d6-2f15-4ba9-81ac-8b052ff2cd8&title=&width=633.5)<br />**1.泛型类**：
```java
//此处T可以随便写为任意标识，常见的如T、E、K、V等形式的参数常用于表示泛型
//在实例化泛型类时，必须指定T的具体类型
public class Generic<T>{

    private T key;

    public Generic(T key) {
        this.key = key;
    }

    public T getKey(){
        return key;
    }
}
```
如何实例化泛型类：
```java
Generic<Integer> genericInteger = new Generic<Integer>(123456);
```
**2.泛型接口**：
```java
public interface Generator<T> {
    public T method();
}
```
实现泛型接口，不指定类型：
```java
class GeneratorImpl<T> implements Generator<T>{
    @Override
    public T method() {
        return null;
    }
}
```
实现泛型接口，指定类型：
```java
class GeneratorImpl<T> implements Generator<String>{
    @Override
    public String method() {
        return "hello";
    }
}
```
**3.泛型方法**：
```java
public static< E > void printArray( E[] inputArray )
   {
         for ( E element : inputArray ){
            System.out.printf( "%s ", element );
         }
         System.out.println();
    }
```
使用：
```java
// 创建不同类型数组：Integer, Double 和 Character
Integer[] intArray = { 1, 2, 3 };
String[] stringArray = { "Hello", "World" };
printArray( intArray  );
printArray( stringArray  );
```

注意: `public static < E > void printArray( E[] inputArray )` 是静态泛型方法。<br />在 java 中泛型只是一个占位符，必须在传递类型后才能使用。泛型类在实例化时才能真正的传递类型参数，但静态方法的加载先于类的实例化，所以静态泛型方法会在泛型类传递真正的类型参数前就加载完。<br />所以静态泛型方法是没有办法使用类上声明的泛型的，只能使用自己声明的 <E>。
<a name="ZDhSP"></a>
## 什么是泛型擦除/类型擦除？为什么要泛型擦除？
Java 的泛型是伪泛型，这是因为 Java 在编译期间，就会擦掉所有的类型信息，等到运行的时候是没有泛型的。<br />是为了向下兼容，因为 JDK5 之前是没有泛型的，为了让 JVM 保持向下兼容，就出了类型擦除这个策略。<br />例如这段代码，往一群猫里放条狗：
```java
LinkedList<Cat> cats = new LinkedList<Cat>();
LinkedList list = cats;  // 注意我在这里把范型去掉了，但是list和cats是同一个链表！
list.add(new Dog());  // 完全没问题！
```
因为 Java 的范型只存在于源码里，编译时会静态地检查一下泛型类型是否正确，而到运行时就不检查了。所以上面这段代码在 JRE（Java**运行**环境）看来和下面这段没区别：
```java
LinkedList cats = new LinkedList();  // 注意：没有范型！
LinkedList list = cats;
list.add(new Dog());
```
<a name="ePNM1"></a>
## 泛型常用的通配符有哪些？

- `？` 表示不确定的 java 类型
- `T (type)` 表示具体的一个 java 类型
- `K` `V (key value)` 分别代表 java 键值中的 Key Value
- `E (element)` 代表 Element
<a name="HmGVK"></a>
# 注解 Annotation
<a name="afRYG"></a>
## 注解是什么？
注解本质上是一个标记，可以标记在类上、方法上、属性上等。<br />是 Java 提供的一种对元程序中元素关联信息和元数据(metadata)的途径和方法。<br />Annatation(注解)是一个接口，程序可以通过反射来获取指定程序中元素的 Annotation对象，然后通过该 Annotation 对象来获取注解中的 metadata 信息。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685790867718-ff56982d-d05b-4872-bbcf-e4b7b1beb2d4.png#averageHue=%23eeeeee&clientId=ub5de2078-286b-4&from=paste&height=663&id=udea60d57&originHeight=1326&originWidth=1340&originalType=binary&ratio=2&rotation=0&showTitle=false&size=569329&status=done&style=none&taskId=u78b26f24-3583-42d0-b0c3-480b257d880&title=&width=670)
<a name="bNiB9"></a>
## 注解的解析方法有哪几种？
注解只有被解析之后才会生效，常见的解析方法有两种：

- **编译期直接扫描**：编译器在编译 Java 代码的时候扫描对应的注解并处理，比如某个方法使用@Override 注解，编译器在编译的时候就会检测当前的方法是否重写了父类对应的方法，检查没问题就 over 了，class 文件里面不会有 Override 这个标记。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685791745979-c228a7d8-d1d2-4a57-83d5-9ca439c7c9d7.png#averageHue=%23343e48&clientId=ub5de2078-286b-4&from=paste&height=100&id=uf8763328&originHeight=164&originWidth=439&originalType=binary&ratio=2&rotation=0&showTitle=false&size=66414&status=done&style=none&taskId=ud041db65-3879-434c-89c8-f3e868b2a28&title=&width=268.5)

- **运行期 runtime 通过反射处理**：像框架中自带的注解(比如 Spring 框架的 @Value、@Component)都是通过反射来进行处理的。比如 Spring 常见的 Autowired ，就是 RUNTIME 的，所以**在运行的时候可以通过反射得到注解的信息**，还能拿到标记的值 required 。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685791726273-965eb0ef-2a74-48d5-9870-8b177398b3f7.png#averageHue=%23363b49&clientId=ub5de2078-286b-4&from=paste&height=109&id=u602acaf7&originHeight=215&originWidth=1401&originalType=binary&ratio=2&rotation=0&showTitle=false&size=218958&status=done&style=none&taskId=u187f751d-08ad-4721-a1e4-cf5cf02f230&title=&width=712.5)
<a name="d0bAy"></a>
# 反射
<a name="VyItE"></a>
## 什么是反射？
想动态地获取类信息、创建类实例、调用类方法这时候就要用到**反射**。<br />通过反射，可以获取任意一个类的所有属性和方法，你还可以调用这些方法和属性。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685791916892-604ea8eb-2d52-4bed-adc2-c187725fd8dd.png#averageHue=%23f9f7f5&clientId=ub5de2078-286b-4&from=paste&height=478&id=u3efe4dc6&originHeight=956&originWidth=1564&originalType=binary&ratio=2&rotation=0&showTitle=false&size=268055&status=done&style=none&taskId=ue60394d7-c044-427a-9aaf-425ea1f25a0&title=&width=782)
<a name="w8zpo"></a>
## 反射的优缺点？
反射可以让我们的代码更加灵活、为各种框架提供开箱即用的功能提供了便利。<br />不过，反射让我们在运行时有了分析操作类的能力的同时，也增加了安全问题，比如可以无视泛型参数的安全检查（泛型参数的安全检查发生在编译时）。另外，反射的性能也要稍差点，不过，对于框架来说实际是影响不大的。<br />相关阅读：[Java Reflection: Why is it so slow?open in new window](https://stackoverflow.com/questions/1392351/java-reflection-why-is-it-so-slow) 。
<a name="PIC9g"></a>
## 反射的应用场景？

- 正是因为反射，你才能这么轻松地使用各种框架。像 Spring/Spring Boot、MyBatis 等等框架中都大量使用了反射机制。像 Spring 里的很多 **注解** ，它真正的功能实现就是利用反射。
- 就像为什么我们使用 Spring 的时候 ，一个@Component注解就声明了一个类为 Spring Bean 呢？为什么通过一个 @Value注解就读取到配置文件中的值呢？究竟是怎么起作用的呢？
- 这些都是因为我们可以基于反射操作类，然后获取到类/属性/方法/方法的参数上的注解，注解这里就有两个作用
   - 一是标记，我们对注解标记的类/属性/方法进行对应的处理；
   - 二是注解本身有一些信息，可以参与到处理的逻辑中。
<a name="QsgNv"></a>
## 反射的原理？
Java 程序编译之后会生成字节码(.class)文件，JVM 进行类加载的时候，会加载字节码文件，将类型相关的所有信息加载进方法区，反射就是去获取这些信息，然后进行各种操作。
<a name="zU0VK"></a>
## JDK1.8 新特性
<a name="QiqPB"></a>
## JDK1.8 都有哪些新特性？
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685792943954-01ab137d-bcd4-4470-b01d-cd9d99587010.png#averageHue=%23fe8b15&clientId=ub5de2078-286b-4&from=paste&height=261&id=u4ce8b7e8&originHeight=521&originWidth=807&originalType=binary&ratio=2&rotation=0&showTitle=false&size=47517&status=done&style=none&taskId=ud1e2ad81-1fd0-479c-b8a7-0aee9c5beef&title=&width=403.5)

- **接口默认方法**：Java 8 允许我们给接口添加一个非抽象的方法实现，只需要使用 default 关键字修饰即可
- **Lambda 表达式和函数式接口**：Lambda 表达式本质上是一段匿名内部类，也可以是一段可以传递的代码。Lambda 允许把函数作为一个方法的参数（函数作为参数传递到方法中），使用 Lambda 表达式使代码更加简洁，但是也不要滥用，否则会有可读性等问题，《Effective Java》作者 Josh Bloch 建议使用 Lambda 表达式最好不要超过 3 行。
- **Stream API**：用函数式编程方式在集合类上进行复杂操作的工具，配合 Lambda 表达式可以方便的对集合进行处理。Java8 中处理集合的关键抽象概念，它可以指定你希望对集合进行的操作，可以执行非常复杂的查找、过滤和映射数据等操作。使用 Stream API 对集合数据进行操作，就类似于使用 SQL 执行的数据库查询。也可以使用 Stream API 来并行执行操作。简而言之，Stream API 提供了一种高效且易于使用的处理数据的方式。
- **日期时间 API**：Java 8 引入了新的日期时间 API 改进了日期时间的管理。
- **Optional 类**：用来解决空指针异常的问题。很久以前 Google Guava 项目引入了 Optional 作为解决空指针异常的一种方式，不赞成代码被 null 检查的代码污染，期望程序员写整洁的代码。受 Google Guava 的鼓励，Optional 现在是 Java 8 库的一部分。
<a name="aqMjv"></a>
###