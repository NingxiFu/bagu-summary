<a name="c8had"></a>
# 集合分类
<a name="iJT0F"></a>
## Java 集合有哪些？
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685870846034-4ad7b962-dc97-41d1-bd66-a70d00cbbfc3.png#averageHue=%23fcfaf7&clientId=u450a2fbd-dcf5-4&from=paste&height=288&id=u22f1ddf9&originHeight=576&originWidth=1472&originalType=binary&ratio=2&rotation=0&showTitle=false&size=279975&status=done&style=none&taskId=u80e317ee-b059-4126-a88c-3bed45ad541&title=&width=736)

- 集合相关类和接口都在java.util中，主要分为3种：List（列表）、Map（映射）、Set(集)。
- Collection 是集合List、Set的父接口：
   - List：存储的元素有序，可重复。
   - Set：存储的元素不无序，不可重复。
- Map 是另外的接口，是键值对映射结构的集合。
<a name="Xf67z"></a>
## <br />
Java 集合， 也叫作容器，主要是由两大接口派生而来：一个是 Collection接口，主要用于存放单一元素；另一个是 Map 接口，主要用于存放键值对。对于Collection 接口，下面又有三个主要的子接口：List、Set 和 Queue。<br />Java 集合框架如下图所示：<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1687088986973-d4387db9-495d-4f06-adb0-81f36357d952.png#averageHue=%23fdfdfd&clientId=u4ee7cad7-5c67-4&from=paste&id=u3c109e33&originHeight=862&originWidth=1612&originalType=url&ratio=2&rotation=0&showTitle=false&size=87065&status=done&style=none&taskId=u23dabc13-9d51-4d16-ab1b-dc22a968d0e&title=)<br />Java 集合框架概览<br />注：图中只列举了主要的继承派生关系，并没有列举所有关系。比方省略了AbstractList, NavigableSet等抽象类以及其他的一些辅助类，如想深入了解，可自行查看源码。
<a name="Lm6Ju"></a>
## 说说 List, Set, Queue, Map 四者的区别？

- List(对付顺序的好帮手): 存储的元素是有序的、可重复的。
- Set(注重独一无二的性质): 存储的元素是无序的、不可重复的。
- Queue(实现排队功能的叫号机): 按特定的排队规则来确定先后顺序，存储的元素是有序的、可重复的。
- Map(用 key 来搜索的专家): 使用键值对（key-value）存储，类似于数学上的函数 y=f(x)，"x" 代表 key，"y" 代表 value，key 是无序的、不可重复的，value 是无序的、可重复的，每个键最多映射到一个值。
<a name="OT9tT"></a>
## 集合框架底层数据结构总结
先来看一下 Collection 接口下面的集合。
<a name="WvvOg"></a>
### List

- ArrayList：Object[] 数组
- Vector：Object[] 数组
- LinkedList：双向链表(JDK1.6 之前为循环链表，JDK1.7 取消了循环)
<a name="n352k"></a>
### Set

- HashSet(无序，唯一): 基于 HashMap 实现的，底层采用 HashMap 来保存元素
- LinkedHashSet: LinkedHashSet 是 HashSet 的子类，并且其内部是通过 LinkedHashMap 来实现的。有点类似于我们之前说的 LinkedHashMap 其内部是基于 HashMap 实现一样，不过还是有一点点区别的
- TreeSet(有序，唯一): 红黑树(自平衡的排序二叉树)
<a name="MnEY3"></a>
### Queue

- PriorityQueue: Object[] 数组来实现二叉堆
- ArrayQueue: Object[] 数组 + 双指针

再来看看 Map 接口下面的集合。
<a name="XbxlT"></a>
### Map

- HashMap：JDK1.8 之前 HashMap 由数组+链表组成的，数组是 HashMap 的主体，链表则是主要为了解决哈希冲突而存在的（“拉链法”解决冲突）。JDK1.8 以后在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为 8）（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树）时，将链表转化为红黑树，以减少搜索时间
- LinkedHashMap：LinkedHashMap 继承自 HashMap，所以它的底层仍然是基于拉链式散列结构即由数组和链表或红黑树组成。另外，LinkedHashMap 在上面结构的基础上，增加了一条双向链表，使得上面的结构可以保持键值对的插入顺序。同时通过对链表进行相应的操作，实现了访问顺序相关逻辑。详细可以查看：[《LinkedHashMap 源码详细分析（JDK1.8）》open in new window](https://www.imooc.com/article/22931)
- Hashtable：数组+链表组成的，数组是 Hashtable 的主体，链表则是主要为了解决哈希冲突而存在的
- TreeMap：红黑树（自平衡的排序二叉树）
<a name="PCPEs"></a>
# List
<a name="Ka5qt"></a>
## ArrayList 和 Array（数组）的区别？
ArrayList 内部基于动态数组实现，比 Array（静态数组） 使用起来更加灵活：

- ArrayList会根据实际存储的元素动态地扩容或缩容，而 Array 被创建之后就不能改变它的长度了。
- ArrayList 允许你使用泛型来确保类型安全，Array 则不可以。
- ArrayList 中只能存储对象。对于基本类型数据，需要使用其对应的包装类（如 Integer、Double 等）。Array 可以直接存储基本类型数据，也可以存储对象。
- ArrayList 支持插入、删除、遍历等常见操作，并且提供了丰富的 API 操作方法，比如 add()、remove()等。Array 只是一个固定长度的数组，只能按照下标访问其中的元素，不具备动态添加、删除元素的能力。
- ArrayList创建时不需要指定大小，而Array创建时必须指定大小。
<a name="tQCta"></a>
## ArrayList 和 Vector 的区别?（了解即可）

- **ArrayList** 是 List 的主要实现类，底层使用 Object[]存储，适用于频繁的查找工作，**线程不安全**。
- **Vector** 是 List 的古老实现类，底层使用Object[] 存储，**线程安全**。
<a name="jIgNd"></a>
## Vector 和 Stack 的区别?（了解即可）

- Vector 和 Stack 两者都是线程安全的，都是使用 synchronized 关键字进行同步处理。
- Stack 继承自 Vector，是一个后进先出的栈，而 Vector 是一个列表。

随着 Java 并发编程的发展，**Vector 和 Stack 已经被淘汰，推荐使用并发集合类（例如 ConcurrentHashMap、CopyOnWriteArrayList 等）或者手动实现线程安全来提供安全的多线程操作支持。**
<a name="dCh4T"></a>
## ArrayList 和 LinkedList 有什么区别？
快速背诵版

- ArrayList
   - 基于数组实现，需要连续的内存
   - 随机访问快（指根据下标访问）
   - 尾部插入、删除性能可以，其它部分插入、删除都会移动数据，因此性能会低
   - 可以利用Cpu缓存，局部性原理
- Linkedlist
   - 基于双向链表实现，不需要连续内存
   - 随机访问慢（要沿着链表遍历）
   - 头尾插入删除性能高
   - 占用内存多

> 理解版
> - 数据结构不同。ArrayList和LinkedList都实现了List接口，但他们底层实现是不一样的。
>    - ArrayList 基于数组
>    - LinkedList 基于双向链表
> 
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1685972954596-1693c40d-2b4d-423e-a632-82cf0deda3d7.png#averageHue=%23fdfdfc&clientId=uc3534c1f-e147-4&from=paste&height=190&id=u606ef03d&originHeight=427&originWidth=1042&originalType=binary&ratio=2&rotation=0&showTitle=false&size=43595&status=done&style=none&taskId=u4d8ebcb9-b605-4a23-8450-bf59abab966&title=&width=463)
> - ArrayList更利于查找，LinkedList更利于增删（插入，删除，查找访问三种情况）
>    - 查找时，ArrayList 直接用下标获取，LinkedList 需要遍历链表。
>    - 增删时，ArrayList 若要插入中间的位置，就要把后面的元素都向前/向后移动，还有可能触发扩容，而 LinkedList 的插入和删除只需要改变几个相关节点的指向就行了。
> - 是否支持随机访问
>    - ArrayList 基于数组，所以可以用下标查找，支持随机访问，它也实现了RandomAccess 接口，这个接口只是用来标识是否支持随机访问。
>    - LinkedList基于链表，所以它没法根据序号直接获取元素，它没有实现RandomAccess 接口，标记不支持随机访问。
> - 内存占用，ArrayList基于数组，是一块连续的内存空间，LinkedList基于链表，内存空间不连续，它们在空间占用上都有一些额外的消耗：
>    - ArrayList是预先定义好的数组，可能会有空的内存空间，存在一定空间浪费
>    - LinkedList每个节点，需要存储前驱和后继，所以每个节点会占用更多的空间

- **是否保证线程安全：**ArrayList 和 LinkedList 都是不同步的，也就是不保证线程安全；
- **底层数据结构：**ArrayList 底层使用的是 **Object 数组**；LinkedList 底层使用的是 **双向链表** 数据结构（JDK1.6 之前为循环链表，JDK1.7 取消了循环。注意双向链表和双向循环链表的区别，下面有介绍到！）
- **插入和删除是否受元素位置的影响：**
   - ArrayList 采用数组存储，所以插入和删除元素的时间复杂度受元素位置的影响。 比如：执行add(E e)方法的时候， ArrayList 会默认在将指定的元素追加到此列表的末尾，这种情况时间复杂度就是 O(1)。但是如果要在指定位置 i 插入和删除元素的话（add(int index, E element)），时间复杂度就为 O(n)。因为在进行上述操作的时候集合中第 i 和第 i 个元素之后的(n-i)个元素都要执行向后位/向前移一位的操作。
   - LinkedList 采用链表存储，所以在头尾插入或者删除元素不受元素位置的影响（add(E e)、addFirst(E e)、addLast(E e)、removeFirst()、 removeLast()），时间复杂度为 O(1)，如果是要在指定位置 i 插入和删除元素的话（add(int index, E element)，remove(Object o),remove(int index)）， 时间复杂度为 O(n) ，因为需要先移动到指定位置再插入和删除。
- **是否支持快速随机访问：**LinkedList 不支持高效的随机元素访问，而 ArrayList（实现了 RandomAccess 接口） 支持。快速随机访问就是通过元素的序号快速获取元素对象(对应于get(int index)方法)。
- **内存空间占用：**ArrayList 的空间浪费主要体现在在 list 列表的结尾会预留一定的容量空间，而 LinkedList 的空间花费则体现在它的每一个元素都需要消耗比 ArrayList 更多的空间（因为要存放直接后继和直接前驱以及数据）。

我们在项目中一般是不会使用到 LinkedList 的，需要用到 LinkedList 的场景几乎都可以使用 ArrayList 来代替，并且，性能通常会更好！就连 LinkedList 的作者约书亚 · 布洛克（Josh Bloch）自己都说从来不会使用 LinkedList 。

更多理解
> ArrayList和LinkedList都实现了List接口，他们有以下的不同点：
> 
> ArrayList是基于索引的数据接口，它的底层是数组。它可以以O(1)时间复杂度对元素进行随机访问。与此对应， LinkedList是以元素列表的形式存储它的数据，每一个元素都和它的前一个和后一个元素链接在一起，在这种情况下，查找某个元素的时间复杂度是O(n)。
> 
> 相对于ArrayList， LinkedList的插入，添加，删除操作速度更快，因为当元素被添加到集合任意位置的时候，不需要像数组那样重新计算大小或者是更新索引。
> 
> LinkedListtArrayList更占内存，因为LinkedList为每一个节点存储了两个引用，一个指向前一个元素，一个指向下一个元素。
> 
> 也可以参考ArrayList vs。 LinkedList。
> 
> 1)因为 Array是基于索引(index) 的数据结构，它使用索引！在数组中搜索和读取数据是很快的。Array 获取数据的时间复杂度是O(1)， 但是要删除数据却是开销很大的，因为这需要重排数组中的所有数据。
> 
> 2)相对于 ArrayList ， LinkedList 插入是更快的。因为 LinkedList 不像 ArrayList 一样，不需要改变数组的大小， 也不需要在数组装满的时候要将所有的数据重新装入一个新的数组，这是 ArrayList 最坏的一种情况，时间复杂度是O(n)，而LinkedList 中插入或删除的时间复杂度仅为 0(1)。ArrayList 在插入数据时还需要更新索引（除了插入数组的尾部）。
> 
> 3) 类似于插入数据，删除数据时，LinkedList 也优于 ArrayList。
> 
> 4) LinkedList 需要更多的内存，因为 ArrayList 的每个索引的位置是实际的数据，而 LinkedList 中的每个节点中存储的是实际的数据和前后节点的位置（一个 LinkedList 实例存储了两个值：Node<E>first 和 Node<E>last 分别表示链表的其实节点和尾节点，每个 Node 实例存储了三个值：Eitem，Node next，Node pre)。
> 
> 什么场景下更适宜使用 LinkedList， 而不用ArrayList
> 
> 1)你的应用不会随机访问数据。因为如果你需要LinkedList中的第n个元素的时候，你需要从第一个元素顺序数到第n个数据，然后读取数据。
> 
> 2)你的应用更多的插入和删除元素，更少的读取数据。因为插入和删除元素不涉及重排数据，所以它要比 ArrayList要快。

<a name="J7ge2"></a>
### 补充内容:RandomAccess 接口
```java
public interface RandomAccess {
}
```
查看源码我们发现实际上 RandomAccess 接口中什么都没有定义。所以，在我看来 RandomAccess 接口不过是一个标识罢了。标识什么？ 标识实现这个接口的类具有随机访问功能。<br />在 binarySearch（) 方法中，它要判断传入的 list 是否 RandomAccess 的实例，如果是，调用indexedBinarySearch()方法，如果不是，那么调用iteratorBinarySearch()方法
```java
public static <T>
    int binarySearch(List<? extends Comparable<? super T>> list, T key) {
        if (list instanceof RandomAccess || list.size()<BINARYSEARCH_THRESHOLD)
            return Collections.indexedBinarySearch(list, key);
        else
            return Collections.iteratorBinarySearch(list, key);
    }
```
ArrayList 实现了 RandomAccess 接口， 而 LinkedList 没有实现。为什么呢？我觉得还是和底层数据结构有关！ArrayList 底层是数组，而 LinkedList 底层是链表。数组天然支持随机访问，时间复杂度为 O(1)，所以称为快速随机访问。链表需要遍历到特定位置才能访问特定位置的元素，时间复杂度为 O(n)，所以不支持快速随机访问。ArrayList 实现了 RandomAccess 接口，就表明了他具有快速随机访问功能。 RandomAccess 接口只是标识，并不是说 ArrayList 实现 RandomAccess 接口才具有快速随机访问功能的！
<a name="UtfuR"></a>
## ArrayList的扩容机制了解吗？
ArrayList是基于数组的集合，数组的容量是在定义的时候确定的，如果数组满了，再插入，就会数组溢出。所以在插入时候，会先检查是否需要扩容，如果当前容量+1超过数组长度，就会进行扩容。<br />ArrayList的扩容是创建一个**1.5倍**的新数组，然后把原数组的值拷贝过去。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1687097601387-103ce876-130a-444c-ba05-6f5c597abee2.png#averageHue=%23f8f8f0&clientId=u4ee7cad7-5c67-4&from=paste&id=u2aa4dad4&originHeight=440&originWidth=895&originalType=url&ratio=2&rotation=0&showTitle=false&size=60414&status=done&style=none&taskId=u1f03495f-4a69-4cf9-b072-af74af1745f&title=)<br />ArrayList扩容
<a name="IxfSf"></a>
## ArrayList 是怎么序列化的？ 为什么用 transient 修饰数组？
ArrayList的序列化不太一样，它使用transient修饰存储元素的elementData的数组，transient关键字的作用是让被修饰的成员属性不被序列化。
<a name="K4xKJ"></a>
### 为什么 ArrayList 不直接序列化元素数组呢？
出于效率的考虑，数组可能长度100，但实际只用了50，剩下的50不用其实不用序列化，这样可以提高序列化和反序列化的效率，还可以节省内存空间。
<a name="KFu6E"></a>
### 那 ArrayList 怎么序列化呢？
ArrayList通过两个方法**readObject、writeObject**自定义序列化和反序列化策略，实际直接使用两个流ObjectOutputStream和ObjectInputStream来进行序列化和反序列化。<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1687097609270-e5c2ca8a-4e24-44c3-9556-6623060f18ef.png#averageHue=%232f485f&clientId=u4ee7cad7-5c67-4&from=paste&height=1981&id=u73b9f9b5&originHeight=2308&originWidth=1660&originalType=url&ratio=2&rotation=0&showTitle=false&size=256029&status=done&style=none&taskId=u1d8ca7b3-30e1-4709-8802-91bb676e44a&title=&width=1425)<br />ArrayList自定义序列化
<a name="RpJZs"></a>
## 快速失败(fail-fast)和安全失败(fail-safe)了解吗？
**快速失败（fail—fast）**：快速失败是Java集合的一种错误检测机制

- 在用迭代器遍历一个集合对象时，如果线程A遍历过程中，线程B对集合对象的内容进行了修改（增加、删除、修改），则会抛出Concurrent Modification Exception。
- 原理：迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果内容发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。
- 注意：这里异常的抛出条件是检测到 modCount != expectedmodCount 这个条件。如果集合发生变化时修改modCount值刚好又设置为了expectedmodCount值，则异常不会抛出。因此，不能依赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的bug。
- 场景：java.util包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修改），比如ArrayList 类。

**安全失败（fail—safe）**

- 采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有集合内容，在拷贝的集合上进行遍历。
- 原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发Concurrent Modification Exception。
- 缺点：基于拷贝内容的优点是避免了Concurrent Modification Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。
- 场景：java.util.concurrent包下的容器都是安全失败，可以在多线程下并发使用，并发修改，比如CopyOnWriteArrayList类。
<a name="jgR2s"></a>
## 有哪几种实现ArrayList线程安全的方法？
fail-fast是一种可能触发的机制，实际上，ArrayList的线程安全仍然没有保证，一般，保证ArrayList的线程安全可以通过这些方案：

- ~~使用 Vector 代替 ArrayList。（不推荐，Vector是一个历史遗留类~~）
- 使用 Collections.synchronizedList 包装 ArrayList，然后操作包装后的 list。
- 使用 CopyOnWriteArrayList 代替 ArrayList。
- 在使用 ArrayList 时，应用程序通过同步机制去控制 ArrayList 的读写。
<a name="gDwQg"></a>
## CopyOnWriteArrayList是什么？如何读写？
CopyOnWriteArrayList 就是 线程安全版本的ArrayList，写时复制，采用读写分离的并发策略。

- CopyOnWriteArrayList容器 允许并发读，读操作是无锁的，性能较高。
- 写操作，比如向容器中添加一个元素，则先将当前容器复制一份，然后在新副本上执行写操作，结束之后再将原容器的引用指向新容器。

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688180367427-28cae4be-14a3-45e5-923e-0de1fa069cbb.png#averageHue=%23fdfdfc&clientId=u4956fc02-454b-4&from=paste&id=u23bbd19b&originHeight=619&originWidth=1140&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ue42585a9-fad5-4fe8-af0a-ad11b7866a0&title=)<br />CopyOnWriteArrayList原理
<a name="bZC2c"></a>
# Map
<a name="tUHda"></a>
## 能说一下HashMap的数据结构吗？
JDK1.7的数据结构是数组+链表。<br />JDK1.8的数据结构是数组+链表+红黑树。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688181585336-6c6e479c-3b46-493f-9abe-be006305ba4a.png#averageHue=%23fcf9f5&clientId=u4956fc02-454b-4&from=paste&id=u20c2810b&originHeight=593&originWidth=1116&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u60b2c7ac-c831-4d67-8574-26326610331&title=)<br />jdk1.8 hashmap数据结构示意图<br />桶数组 存储数据元素，链表 解决冲突，红黑树 提高查询的效率。

- 数据元素通过映射关系，也就是散列函数，映射到桶数组对应索引的位置
- 如果发生冲突，从冲突的位置拉一个链表，插入冲突的元素
- 如果链表长度>8 & 数组大小>=64，链表转为红黑树，以减少搜索时间。（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树）
- 如果红黑树节点个数<6 ，转为链表
<a name="rL4a2"></a>
## 你对红黑树了解多少？为什么不用二叉树/平衡树呢？
简单来说红黑树就是为了解决二叉查找树的缺陷，因为二叉查找树在某些情况下会退化成一个线性结构。详细了解可以查看 [漫画：什么是红黑树？](https://juejin.im/post/5a27c6946fb9a04509096248#comment)<br />红黑树本质上是一种二叉查找树，为了保持平衡，它又在二叉查找树的基础上增加了一些规则：

1. 每个节点要么是红色，要么是黑色；
2. 根节点永远是黑色的；
3. 所有的叶子节点都是是黑色的（注意这里说叶子节点其实是图中的 NULL 节点）；
4. 每个红色节点的两个子节点一定都是黑色；
5. 从任一节点到其子树中每个叶子节点的路径都包含相同数量的黑色节点；

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688181692118-28ac437c-25a5-4d8b-a9d4-5f8dfac67578.png#averageHue=%23ece5e4&clientId=u4956fc02-454b-4&from=paste&id=u73f52029&originHeight=406&originWidth=734&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=udbb53939-ebdf-4046-af8d-7e0c84da57d&title=)<br />红黑树<br />之所以不用二叉树：<br />红黑树是一种平衡的二叉树，插入、删除、查找的最坏时间复杂度都为 O(logn)，避免了二叉树最坏情况下的O(n)时间复杂度。<br />之所以不用平衡二叉树：<br />平衡二叉树是比红黑树更严格的平衡树，为了保持保持平衡，需要旋转的次数更多，也就是说平衡二叉树保持平衡的效率更低，所以平衡二叉树插入和删除的效率比红黑树要低。
<a name="Qs9lm"></a>
## 红黑树怎么保持平衡的知道吗？
红黑树插入的新节点默认是红色。这个规定有以下原因：

1. 最小影响原则：插入红色节点相比于插入黑色节点，对红黑树的性质破坏程度更小。插入红色节点时，只会破坏性质4（红色节点的两个子节点必须都是黑色），而插入黑色节点可能会破坏性质5（从任意节点到其每个叶子节点的所有路径中，包含相同数量的黑色节点）。
2. 修复方便：插入红色节点后，我们可以通过局部调整（颜色翻转和旋转操作）来恢复红黑树的性质。这些操作相对简单且高效。
3. 平衡性：将新插入的节点设置为红色有助于保持红黑树的高度平衡。因为插入红色节点时，黑色高度不会发生变化，我们只需要关注红色节点连续出现的情况。<br />因此，在红黑树中新插入的节点默认是红色，这有助于保持树的高度平衡并降低维护成本。

红黑树有两种方式保持平衡：旋转和染色。

- 旋转：旋转分为两种，左旋和右旋

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688181451287-8ba29190-ebec-4995-b468-20809ca95a96.png#averageHue=%23f8eeee&clientId=u4956fc02-454b-4&from=paste&id=u9b644933&originHeight=271&originWidth=700&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u5e5793e8-bb5f-4ab4-b7f7-1bc406bcda2&title=)<br />左旋<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688181451281-f31ccf2c-4fae-4c65-a410-ee231e77d90a.png#averageHue=%23f9efef&clientId=u4956fc02-454b-4&from=paste&id=u4bce5f1e&originHeight=298&originWidth=701&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u06c0888b-ea54-432b-baa7-e29b129818a&title=)<br />右旋

- 染⾊：

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688181451249-a4ba139a-9d73-4410-ab7b-903df3a39855.png#averageHue=%23f6efef&clientId=u4956fc02-454b-4&from=paste&id=u1421d683&originHeight=339&originWidth=811&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u4583dad3-78d1-4a8f-8746-92b56a46bf4&title=)<br />染色
<a name="iCaWh"></a>
## HashMap put 新元素的流程？
![](https://cdn.nlark.com/yuque/0/2023/jpeg/25962088/1688197488115-92b1ec75-8a67-42c8-b510-4d03dea11076.jpeg#averageHue=%23f7f5ef&clientId=u4956fc02-454b-4&from=paste&id=u7cf8a6f9&originHeight=1416&originWidth=1346&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u44f5a816-fad9-4a16-bca3-57980319874&title=)<br />HashMap插入数据流程图<br />**思路：数组是否为空需要扩容 -> 数组对应下标处是否为空 -> key是否相同 -> 是否是树节点 -> 如果是链表则判断是否已经存在相同key -> 是否达到树化阈值**

1. 首先进行哈希值的扰动，获取一个新的哈希值。(key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
2. 判断tab是否位空或者长度为0，如果是则进行扩容操作。
```java
if ((tab = table) == null || (n = tab.length) == 0)
    n = (tab = resize()).length;
```

3. 根据哈希值计算下标，如果对应小标正好没有存放数据，则直接插入即可否则需要覆盖。tab[i = (n - 1) & hash])
4. 判断tab[i]是否为树节点，否则向链表中插入数据，是则向树中插入节点。
5. 如果链表中插入节点的时候，链表长度大于等于8，则需要把链表转换为红黑树。treeifyBin(tab, hash);
6. 最后所有元素处理完成后，判断是否超过阈值；threshold，超过则扩容。
<a name="ZTWeR"></a>
## HashMap怎么查找元素？
![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688198920719-dd8c5a36-a075-427b-88da-427dcb6ef198.png#averageHue=%23faf5f4&clientId=u4956fc02-454b-4&from=paste&height=603&id=uace5d672&originHeight=741&originWidth=600&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u36f19e77-f61b-4301-80a1-870ea85177a&title=&width=488)<br />HashMap查找流程图<br />HashMap的查找就简单很多：

1. 使用扰动函数，获取新的哈希值
2. 计算数组下标，获取节点
3. 当前节点和key匹配，直接返回
4. 否则，当前节点是否为树节点，查找红黑树
5. 否则，遍历链表查找
<a name="Bp0dF"></a>
## HashMap的哈希/扰动函数是怎么设计的?
HashMap的哈希函数是**先拿到 key 的hashcode**，是一个32位的int类型的数值，**然后让hashcode的高16位和低16位进行异或^操作**。
```java
static final int hash(Object key) {
        int h;
        // key的hashCode和key的hashCode右移16位做异或运算
        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
    }
```
这么设计是为了降低哈希碰撞的概率，也就是用于优化散列效果。
<a name="IYqIq"></a>
## 为什么哈希/扰动函数能降hash碰撞？
因为 key.hashCode() 函数调用的是 key 键值类型自带的哈希函数，返回 int 型哈希值（也叫散列值）。int 值范围为 **-2147483648~2147483647**，加起来大概 40 亿的映射空间。<br />只要哈希函数映射得比较均匀松散，一般应用是很难出现碰撞的。但问题是一个 40 亿长度的数组，内存是放不下的。<br />假如 HashMap 数组的初始大小才 16，就需要用之前需要**对数组的长度取模运算，得到的余数才能用来访问数组下标。**<br />源码中模运算就是把哈希值和 (数组长度 - 1) 做一个 "&" 与操作，位运算比取余 % 运算要快。
```java
bucketIndex = indexFor(hash, table.length);

static int indexFor(int h, int length) {
     return h & (length-1);
}
```
顺便说一下，这也正好解释了为什么 HashMap 的数组长度要取 2 的整数幂。因为这样**（数组长度 - 1）正好相当于一个 “低位掩码”（n = 0...010...0, n - 1 = 0...001...1，只有右侧几位全是1）**。与 操作的结果就是**散列值的高位全部归零，只保留低位值，用来做数组下标访问**。以初始长度 16 为例，16-1=15。2 进制表示是 0000 0000 0000 0000 0000 0000 0000 1111。和某个散列值做 与 操作如下，结果就是截取了最低的四位值。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688199787099-bd628df4-bb7f-42bb-b2b0-75f9160939cd.png#averageHue=%23c6df85&clientId=u4956fc02-454b-4&from=paste&id=uce930314&originHeight=320&originWidth=1456&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=uec04150f-bd2c-448b-bd65-f9e6e354639&title=)<br />哈希&运算<br />这样是要快捷一些，但是新的问题来了，就算散列值分布再松散，要是只取最后几位的话，碰撞也会很严重。如果散列本身做得不好，分布上成等差数列的漏洞，如果正好让最后几个低位呈现规律性重复，那就更难搞了。<br />这时候 **扰动函数 的价值**就体现出来了，看一下扰动函数的示意图：<br />![](https://cdn.nlark.com/yuque/0/2023/jpeg/25962088/1688199787055-79f94485-d1b1-451f-8370-2ca26cbb7cfb.jpeg#averageHue=%23f7f0e3&clientId=u4956fc02-454b-4&from=paste&id=u0ddfa463&originHeight=2019&originWidth=6261&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u9f603ddc-083c-48d7-9e2e-501386ecd97&title=)<br />**扰动函数示意图（完整的哈希过程，重要）**<br />右移 16 位，正好是 32bit 的一半，自己的高半区和低半区做异或，就是为了**混合原始哈希码的高位和低位，以此来加大低位的随机性**。而且**混合后的低位掺杂了高位的部分特征，这样高位的信息也被变相保留下来。**
<a name="BaE6y"></a>
## 为什么HashMap的容量是2的倍数呢？
第一个原因是为了方便哈希取余：

- 将元素放在table数组上面，是**用 hash值%数组大小 定位位置**，而HashMap是用hash值&(数组大小-1)，去和%达到一样的效果。
- 这就是**需要HashMap的大小是2的倍数，这样（n-1是0**01***11这样形式的）通过&运算，才可以得到和%一样的效果**。
- 这样进行位运算时，能和%运算达到一样的充分的散列，使得添加的元素均匀分布在HashMap的每个位置上，减少hash碰撞，**而位运算比%的效率高得多**。

第二个方面是在扩容时，利用扩容后的大小也是2的倍数，将已经产生hash碰撞的元素完美的转移到新的table中去。

- HashMap的扩容机制，元素在超过 负载因子*HashMap大小 时就会扩容。
- ![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688202818549-49c0521b-7789-47bf-8603-d6fafb55ec53.png#averageHue=%23363e46&clientId=ua8c6265c-e348-4&from=paste&id=ub1cf3fb1&originHeight=143&originWidth=792&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ua1efd9ae-ecfc-4aab-9dae-2c0340320fe&title=)

put中的扩容
<a name="WquoV"></a>
## 如果初始化HashMap，传一个17的值new HashMap<>，它会怎么处理？
简单来说，就是初始化时，传的不是2的倍数时，HashMap会向上寻找离得最近的2的倍数，所以传入17，但HashMap的实际容量是32。<br />我们来看看详情，在HashMap的初始化中，有这样⼀段⽅法；
```java
public HashMap(int initialCapacity, float loadFactor) {
 ...
 this.loadFactor = loadFactor;
 this.threshold = tableSizeFor(initialCapacity);
}
```

- 阀值 threshold ，通过⽅法 tableSizeFor 进⾏计算，是根据初始化传的参数来计算的。
- 同时，这个⽅法也要要寻找⽐初始值⼤的，最⼩的那个2进制数值。⽐如传了17，我应该找到的是32。
```java
static final int tableSizeFor(int cap) {
 int n = cap - 1;
 n |= n >>> 1;
 n |= n >>> 2;
 n |= n >>> 4;
 n |= n >>> 8;
 n |= n >>> 16;
 return (n < 0) ? 1 : (n >= MAXIMUM_CAPACITY) ? MAXIMUM_CAPACITY : n + 1; }
```

- MAXIMUM_CAPACITY = 1 << 30，这个是临界范围，也就是最⼤的Map集合。
- 计算过程是向右移位1、2、4、8、16，和原来的数做|运算，这主要是为了把⼆进制的各个位置都填上1，当⼆进制的各个位置都是1以后，就是⼀个标准的2的倍数减1了，最后把结果加1再返回即可。

以17为例，看一下初始化计算table容量的过程：<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265174361-688df451-08c3-4c3d-8f58-dbcdf05b0ea5.png#averageHue=%23fbfaf9&clientId=ua8c6265c-e348-4&from=paste&id=uee6d0965&originHeight=400&originWidth=774&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u1fad29cf-1c0d-4e76-b170-2947b56ee9a&title=)<br />容量计算
<a name="pH7sN"></a>
## 还有哪些哈希函数的构造方法呢？
**HashMap里**哈希构造函数的方法叫：

- **除留取余法**：H（key)=key%p（p<=N）,关键字除以一个不大于哈希表长度的正整数p，所得余数为地址，当然HashMap里进行了优化改造，效率更高，散列也更均衡。

除此之外，**还有**这几种常见的哈希函数构造方法：

- **直接定址法**直接根据key来映射到对应的数组位置，例如1232放到下标1232的位置。
- **数字分析法**取key的某些数字（例如十位和百位）作为映射的位置
- **平方取中法**取key平方的中间几位作为映射的位置
- **折叠法**将key分割成位数相同的几段，然后把它们的叠加和作为映射的位置

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265329655-234f6c46-dba1-413d-aaf3-0534c536de6d.png#averageHue=%23fdf9f7&clientId=ua8c6265c-e348-4&from=paste&id=ud41f5d59&originHeight=452&originWidth=993&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ubc3e902d-919c-40dc-954c-891eb6162f1&title=)<br />散列函数构造
<a name="r0QTx"></a>
## 解决哈希冲突有哪些方法呢？
我们到现在已经知道，HashMap使用链表的原因为了处理哈希冲突，这种方法就是所谓的：

- **链地址法**：在冲突的位置拉一个链表，直接把冲突的元素放进去。

除此之外，还有一些常见的解决冲突的办法：

- **开放定址法**：开放定址法就是从冲突的位置再接着往下找，给冲突元素找个空位。找到空闲位置的方法也有很多种：
   - 线行探查法: 从冲突的位置开始，依次判断下一个位置是否空闲，直至找到空闲位置
   - 平方探查法: 从冲突的位置x开始，第一次增加1^2个位置，第二次增加2^2…，直至找到空闲的位置
   - ……

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265329704-463398b5-bc7c-41de-bdb7-d5275ecee750.png#averageHue=%23f7f6f5&clientId=ua8c6265c-e348-4&from=paste&id=u69c754d8&originHeight=554&originWidth=1263&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ua70f2a3f-0fbf-4d78-9ce7-94be6508eef&title=)<br />开放定址法

- **再哈希法**：换种哈希函数，重新计算冲突元素的地址。
- **建立公共溢出区**：再建一个数组，把冲突的元素放进去。
<a name="RYSXO"></a>
## 为什么HashMap链表转红黑树的阈值为8呢？
树化发生在table数组的长度大于64，且链表的长度大于8的时候。<br />为什么是8呢？源码的注释也给出了答案。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265522237-d82d0b29-720c-48ad-bcd0-6204ba3607a3.png#averageHue=%23365370&clientId=ua8c6265c-e348-4&from=paste&id=u4af2b59b&originHeight=1340&originWidth=1420&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ub969ea8a-725c-4cb3-84be-f97a8fdb44e&title=)<br />源码注释<br />**红黑树节点的大小大概是普通节点的两倍，**所以**转红黑树，牺牲了空间换时间，更多的是一种兜底的策略，保证极端情况下的查找效率。所以平常尽量不让它转红黑树。**<br />阈值为什么要选8呢？和统计学有关。理想情况下，使用随机哈希码，链表里的节点符合泊松分布，出现节点个数的概率是递减的，**节点个数为8的情况，发生概率仅为0.00000006，即为我们想定义的极端情况。**
<a name="dOXkD"></a>
### 红黑树转回链表的阈值为什么是6，而不是8？
是因为如果这个阈值也设置成8，假如发生碰撞，节点增减刚好在8附近，会发生链表和红黑树的不断转换，导致资源浪费。
<a name="dGWxc"></a>
## Hashmap什么时候会扩容？为什么负载因子是0.75？
为了减少哈希冲突发生的概率，当当前HashMap的元素个数达到一个临界值的时候，就会触发扩容，把所有元素rehash之后再放在扩容后的容器中，这是一个相当耗时的操作。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265718516-15522bba-b80a-4f1f-ae7d-a87abf8d3d88.png#averageHue=%23353d45&clientId=ua8c6265c-e348-4&from=paste&id=ub97fd059&originHeight=63&originWidth=612&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u7cbc4ea5-4b3e-4eed-934f-9c27003c8e9&title=)<br />put时，扩容<br />而这个临界值threshold就是由负载因子和当前容器的容量大小来确定的，假如采用默认的构造方法：<br />_临界值（threshold ）= 默认容量（DEFAULT_INITIAL_CAPACITY） * 默认负载因子（DEFAULT_LOAD_FACTOR）_<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265718537-936e3863-a087-4024-b82e-33d91f07c114.png#averageHue=%23373d48&clientId=ua8c6265c-e348-4&from=paste&id=ud2cfe638&originHeight=289&originWidth=807&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ue6d309b7-7a91-4ea0-b349-a5af2a74044&title=)<br />threshold计算<br />那就是大于16x0.75=12时，就会触发扩容操作。
<a name="Xtc6s"></a>
### 那么为什么选了0.75作为HashMap的默认负载因子load factor呢？
简单来说，这是**对空间成本和时间成本平衡**的考虑。<br />在HashMap中有这样一段注释：<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688265718653-7e3efa4a-11d9-405a-aaa7-f1d6b748e7b6.png#averageHue=%233a5c7f&clientId=ua8c6265c-e348-4&from=paste&id=u141287a8&originHeight=836&originWidth=1404&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u312cd0c5-e46f-4c51-af7f-7fa6386e144&title=)<br />关于默认负载因子的注释<br />我们都知道，HashMap的散列构造方式是Hash取余，负载因子决定元素个数达到多少时候扩容。

- 若负载因子较大，元素较多，空位较少的时候才扩容，那哈希冲突的概率会增加，查找时间就增加了。
- 若负载因子较小，元素较少，空位比较多的时候就扩容了，哈希碰撞的概率会降低，查找时间成本降低，但是就需要更多的空间去存储元素，空间成本会增加。
<a name="VD1ET"></a>
## Hashmap扩容机制了解吗？
HashMap是基于数组+链表和红黑树实现的，但用于存放key值的桶数组的长度是固定的，由初始化参数确定。<br />那么，随着数据的插入数量增加以及负载因子的作用下，就需要扩容来存放更多的数据。**而扩容中有一个非常重要的点，就是jdk1.8中的优化操作，可以不需要再重新计算每一个元素的哈希值。**<br />因为HashMap的初始容量是2的次幂，扩容之后的长度是原来的二倍，新的容量也是2的次幂，所以，元素，要么在原位置，要么在原位置再移动2的次幂。<br />看下这张图，n为table的长度，图a表示扩容前的key1和key2两种key确定索引的位置，图b表示扩容后key1和key2两种key确定索引位置。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688268701668-5d5b5c74-22d6-4314-8617-c59379091eeb.png#averageHue=%23fdfcfc&clientId=ua8c6265c-e348-4&from=paste&id=u32a3a636&originHeight=446&originWidth=1632&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u65cea6d7-13ca-43b0-9ffa-218a6c4306e&title=)<br />扩容之后的索引计算<br />元素在重新计算hash之后，因为n变为2倍，那么n-1的mask范围在高位多1bit(红色)，因此新的index就会发生这样的变化：<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688268701661-3b27ca03-0ab1-4b62-bd46-30c9ee2644e4.png#averageHue=%23fcfcfb&clientId=ua8c6265c-e348-4&from=paste&id=u67fb8fb3&originHeight=219&originWidth=876&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u4980ec69-d65d-4cd1-ae80-06f5d6f7998&title=)<br />扩容位置变化<br />所以在扩容时，只需要看原来的hash值新增的那一位是0还是1就行了，是0的话索引没变，是1的化变成原索引+oldCap，看看如16扩容为32的示意图：<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688268701659-374431ff-c23a-459a-85ae-29184e8b09f8.png#averageHue=%23f5f5e6&clientId=ua8c6265c-e348-4&from=paste&id=u386662c0&originHeight=568&originWidth=1179&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ubf9bd5e7-4a8b-4f74-bf25-719c2b10016&title=)<br />扩容节点迁移示意图<br />扩容节点迁移主要逻辑：<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688268701664-166ec716-5b34-45c2-a164-a8ea0cdebacb.png#averageHue=%23324f6b&clientId=ua8c6265c-e348-4&from=paste&id=ub49d82d8&originHeight=1882&originWidth=1164&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u4e4f599e-af7c-46c6-aebd-70aa61f945f&title=)<br />扩容主要逻辑
<a name="NvxYU"></a>
## jdk1.8对HashMap主要做了哪些优化呢？为什么？
jdk1.8 的HashMap主要有五点优化：

1. **数据结构**：数组 + 链表改成了数组 + 链表或红黑树原因：发生 hash 冲突，元素会存入链表，链表过长转为红黑树，将时间复杂度由O(n)降为O(logn)
2. **链表插入方式**：链表的插入方式从头插法改成了尾插法简单说就是插入时，如果数组位置上已经有元素，1.7 将新元素放到数组中，原始节点作为新节点的后继节点，1.8 遍历链表，将元素放置到链表的最后。原因：因为 1.7 头插法扩容时，头插法会使链表发生反转，多线程环境下会产生环。
3. **扩容rehash**：扩容的时候 1.7 需要对原数组中的元素进行重新 hash 定位在新数组的位置，1.8 采用更简单的判断逻辑，不需要重新通过哈希函数计算位置，新的位置不变或索引 + 新增容量大小。原因：提高扩容的效率，更快地扩容。
4. **扩容时机**：在插入时，1.7 先判断是否需要扩容，再插入，1.8 先进行插入，插入完成再判断是否需要扩容；
5. **散列函数**：1.7 做了四次移位和四次异或，jdk1.8只做一次。原因：做 4 次的话，边际效用也不大，改为一次，提升效率。
<a name="w0cme"></a>
## 你能自己设计实现一个HashMap吗？
这道题**快手**常考。<br />不要慌，红黑树版咱们多半是写不出来，但是数组+链表版还是问题不大的，也就是类似jdk1.7版本的hashmap，详细可见： [手写HashMap，快手面试官直呼内行！open in new window](https://mp.weixin.qq.com/s/Z9yoRZW5itrtgbS-cj0bUg)。<br />整体的设计：

- 散列函数：hashCode()+除留余数法
- 冲突解决：链地址法
- 扩容：节点重新hash获取位置

![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688279729722-a742e189-4445-4212-a14d-3419255e9c40.png#averageHue=%23fcfcf6&clientId=ua8c6265c-e348-4&from=paste&id=ue6e31410&originHeight=374&originWidth=1102&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u7090f112-6911-400c-9198-f2476cbf065&title=)<br />自定义HashMap整体结构<br />完整代码：<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688279729696-f5152720-6c6e-4b22-a898-bc0c84aa2e39.png#averageHue=%233c484f&clientId=ua8c6265c-e348-4&from=paste&id=u95cc4fae&originHeight=7298&originWidth=1430&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=uf1aceb81-9981-4886-be6a-7c026df15bc&title=)<br />完整代码
<a name="AuQ1L"></a>
## HashMap 是线程安全的吗？多线程时会有什么问题？
**HashMap不是线程安全**的，可能会发生这些问题：

- **多线程下扩容死循环。**JDK1.7 中的 HashMap 使用头插法插入元素，在多线程的环境下，扩容的时候有可能导致环形链表的出现，形成死循环。因此，JDK1.8 使用尾插法插入元素，在扩容时会保持链表元素原本的顺序，不会再出现环形链表的问题。（但还是不建议在多线程下使用 HashMap，因为多线程下使用 HashMap 还是会存在下面的数据覆盖的问题。并发环境下，推荐使用 ConcurrentHashMap 。）
- **多线程的 put 可能导致数据覆盖丢失。**多线程同时执行 put 操作，如果计算出的索引是相同的，前一个 key 会被后一个 key 覆盖，从而导致元素丢失。此问题在JDK 1.8 中仍存在。
- **put 和 get 并发时，可能导致 get 为 null。**线程 1 执行 put 时，因为元素个数超出 threshold 而导致 rehash，线程 2 此时执行 get，有可能导致这个问题。此问题在JDK 1.8 中仍存在。
<a name="i298X"></a>
### 详细举例 HashMap 为什么线程不安全？
JDK1.7 及之前版本，在多线程环境下，HashMap 扩容时会造成死循环和数据丢失的问题。<br />数据丢失这个在 JDK1.7 和 JDK 1.8 中都存在，这里以 JDK 1.8 为例进行介绍。<br />JDK 1.8 后，在 HashMap 中，多个键值对可能会被分配到同一个桶（bucket），并以链表或红黑树的形式存储。多个线程对 HashMap 的 put 操作会导致线程不安全，具体来说会有**数据覆盖**的风险。<br />举个例子：

- 两个线程 1,2 同时进行 put 操作，并且发生了哈希冲突（hash 函数计算出的插入下标是相同的）。
- 不同的线程可能在不同的时间片获得 CPU 执行的机会，当前线程 1 执行完哈希冲突判断后，由于时间片耗尽挂起。线程 2 先完成了插入操作。
- 随后，线程 1 获得时间片，由于之前已经进行过 hash 碰撞的判断，所有此时会直接进行插入，这就导致线程 2 插入的数据被线程 1 覆盖了。
```java
public V put(K key, V value) {
    return putVal(hash(key), key, value, false, true);
}

final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
    // ...
    // 判断是否出现 hash 碰撞
    // (n - 1) & hash 确定元素存放在哪个桶中，桶为空，新生成结点放入桶中(此时，这个结点是放在数组中)
    if ((p = tab[i = (n - 1) & hash]) == null)
        tab[i] = newNode(hash, key, value, null);
    // 桶中已经存在元素（处理hash冲突）
    else {
    // ...
}
```
还有一种情况是这两个线程同时 put 操作导致 size 的值不正确，进而导致数据覆盖的问题：

1. 线程 1 执行 if(++size > threshold) 判断时，假设获得 size 的值为 10，由于时间片耗尽挂起。
2. 线程 2 也执行 if(++size > threshold) 判断，获得 size 的值也为 10，并将元素插入到该桶位中，并将 size 的值更新为 11。
3. 随后，线程 1 获得时间片，它也将元素放入桶位中，并将 size 的值更新为 11。
4. 线程 1、2 都执行了一次 put 操作，但是 size 的值只增加了 1，也就导致实际上只有一个元素被添加到了 HashMap 中。
```java
public V put(K key, V value) {
    return putVal(hash(key), key, value, false, true);
}

final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
    // ...
    // 实际大小大于阈值则扩容
    if (++size > threshold)
        resize();
    // 插入后回调
    afterNodeInsertion(evict);
    return null;
}
```
<a name="PuPvN"></a>
## 有什么办法能解决HashMap线程不安全的问题呢？
Java 中有 HashTable、Collections.synchronizedMap、以及 ConcurrentHashMap 可以实现线程安全的 Map。

- **HashTable** 是直接在**操作方法上加 synchronized 关键字**，**锁住整个table数组**，粒度比较大；
- **Collections.synchronizedMap** 是使**用 Collections 集合工具的内部类**，通过**传入 Map 封装出一个 SynchronizedMap 对象**，内部定义了一个**对象锁**，方法内通过对象锁实现；
- **ConcurrentHashMap** 在**jdk1.7中使用分段锁**，在**jdk1.8中使用CAS（乐观锁）+synchronized（悲观锁）**。
<a name="khbEL"></a>
## ConcurrentHashmap 线程安全具体怎么实现的？
ConcurrentHashmap线程安全在**jdk1.7**版本是基于**分段锁**实现，在**jdk1.8**是基于**CAS+synchronized**实现。
<a name="VeAWN"></a>
### jdk1.7 分段锁
首先将数据分为一段一段（这个“段”就是 Segment）的存储，然后给每一段数据配一把锁。<br />**ConcurrentHashMap 是由 Segment 数组结构和 HashEntry 数组+链表结构组成**。<br />Segment 继承了 ReentrantLock,所以 Segment 是一种可重入锁，扮演锁的角色。HashEntry 用于存储键值对数据。
```java
static class Segment<K,V> extends ReentrantLock implements Serializable {
}
```
一个 ConcurrentHashMap 里包含一个 Segment 数组，Segment 的个数一旦**初始化就不能改变**。 Segment 数组的大小默认是 16，也就是说默认可以同时支持 16 个线程并发写。<br />Segment 类似 HashMap，是数组+链表结构，每个 Segment 对应一个 HashEntry 数组，当对 HashEntry 数组的数据进行修改时，必须首先获得对应的 Segment 的锁。也就是说，对同一 Segment 的并发写入会被阻塞，不同 Segment 的写入是可以并发执行的。<br />实际上就是相当于每个Segment都是一个HashMap，默认的Segment长度是16，也就是支持16个线程的并发写，Segment之间相互不会受到影响。<br />**理解：相当于减小了Hashmap上加锁的粒度大小，从而减少了并发带来的冲突。**<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688285499813-8a01657c-9cfa-4eeb-9b3b-04e4abd5c25f.png#averageHue=%23fbf8f4&clientId=u17aefc5c-1ff8-4&from=paste&height=273&id=u9025de22&originHeight=351&originWidth=736&originalType=binary&ratio=2&rotation=0&showTitle=false&size=25022&status=done&style=none&taskId=ubfb25c2c-c06c-4dc9-a644-eb11632ca5d&title=&width=573)<br />**put流程**<br />整个流程和HashMap非常类似，只不过是先定位到具体的Segment，然后通过ReentrantLock去操作而已，后面的流程，就和HashMap基本上是一样的。

1. 计算hash，定位到segment，segment如果是空就先初始化
2. 使用ReentrantLock加锁，如果获取锁失败则尝试自旋，自旋超过次数就阻塞获取，保证一定获取锁成功
3. 遍历HashEntry，就是和HashMap一样，数组中key和hash一样就直接替换，不存在就再插入链表，链表同样操作

![](https://cdn.nlark.com/yuque/0/2023/jpeg/25962088/1688280791215-d30b03ae-3e5e-4d2a-88df-71d528ff8c77.jpeg#averageHue=%23fbf8f4&clientId=ua8c6265c-e348-4&from=paste&height=804&id=u32bd6495&originHeight=1667&originWidth=1045&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u991ede6b-d69d-4c43-b78f-35b5fd31fbd&title=&width=504)<br />**get流程**<br />get也很简单，key通过hash定位到segment，再遍历链表定位到具体的元素上，需要注意的是value是volatile的，所以get是不需要加锁的。
<a name="cXJ7q"></a>
### jdk1.8 CAS+synchronized
ConcurrentHashMap 取消了 Segment 分段锁，采用 Node + CAS + synchronized 来保证并发安全。数据结构跟 HashMap 1.8 的结构类似，数组+链表/红黑二叉树。Java 8 在链表长度超过一定阈值（8）时将链表（寻址时间复杂度为 O(N)）转换为红黑树（寻址时间复杂度为 O(log(N))）。<br />Java 8 中，**锁粒度更细，synchronized 只锁定当前链表或红黑二叉树的首节点，这样只要 hash 不冲突，就不会产生并发，就不会影响其他 Node 的读写，效率大幅提升。**<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688285403401-d6180504-6837-48c7-a52e-002228f9b9bf.png#averageHue=%23f1efee&clientId=u17aefc5c-1ff8-4&from=paste&height=295&id=u233321ac&originHeight=371&originWidth=663&originalType=binary&ratio=2&rotation=0&showTitle=false&size=24037&status=done&style=none&taskId=u4a89527b-443a-4be3-b268-e65f93c8d0c&title=&width=527.5)<br />**jdk1.8**实现线程安全不是在数据结构上下功夫，它的数据结构和HashMap是一样的，数组+链表+红黑树。它**实现线程安全的关键点在于put流程**。<br />**put流程**

1. 首先计算hash，遍历node数组，如果node是空的话，就通过CAS+自旋的方式初始化
```java
tab = initTable();
```
node数组初始化：
```java
private final Node<K,V>[] initTable() {
    Node<K,V>[] tab; int sc;
    while ((tab = table) == null || tab.length == 0) {
        //如果正在初始化或者扩容
        if ((sc = sizeCtl) < 0)
            //等待
            Thread.yield(); // lost initialization race; just spin
        else if (U.compareAndSwapInt(this, SIZECTL, sc, -1)) {   //CAS操作
            try {
                if ((tab = table) == null || tab.length == 0) {
                    int n = (sc > 0) ? sc : DEFAULT_CAPACITY;
                    @SuppressWarnings("unchecked")
                    Node<K,V>[] nt = (Node<K,V>[])new Node<?,?>[n];
                    table = tab = nt;
                    sc = n - (n >>> 2);
                }
            } finally {
                sizeCtl = sc;
            }
            break;
        }
    }
    return tab;
}
```

2. 如果当前数组位置是空则直接通过CAS自旋写入数据
```java
static final <K,V> boolean casTabAt(Node<K,V>[] tab, int i,
                                    Node<K,V> c, Node<K,V> v) {
    return U.compareAndSwapObject(tab, ((long)i << ASHIFT) + ABASE, c, v);
}
```

3. 如果hash==MOVED，说明需要扩容，执行扩容
```java
else if ((fh = f.hash) == MOVED)
                tab = helpTransfer(tab, f);
```
```java
final Node<K,V>[] helpTransfer(Node<K,V>[] tab, Node<K,V> f) {
    Node<K,V>[] nextTab; int sc;
    if (tab != null && (f instanceof ForwardingNode) &&
        (nextTab = ((ForwardingNode<K,V>)f).nextTable) != null) {
        int rs = resizeStamp(tab.length);
        while (nextTab == nextTable && table == tab &&
               (sc = sizeCtl) < 0) {
            if ((sc >>> RESIZE_STAMP_SHIFT) != rs || sc == rs + 1 ||
                sc == rs + MAX_RESIZERS || transferIndex <= 0)
                break;
            if (U.compareAndSwapInt(this, SIZECTL, sc, sc + 1)) {
                transfer(tab, nextTab);
                break;
            }
        }
        return nextTab;
    }
    return table;
}
```

4. 如果都不满足，就使用synchronized写入数据，写入数据同样判断链表、红黑树，链表写入和HashMap的方式一样，key hash一样就覆盖，反之就尾插法，链表长度超过8就转换成红黑树	
```java
synchronized (f){
     ……
 }
```
![](https://cdn.nlark.com/yuque/0/2023/jpeg/25962088/1688280791109-7444e09a-b17f-499a-a782-ab43de76b661.jpeg#averageHue=%23faf7f4&clientId=ua8c6265c-e348-4&from=paste&height=657&id=u2f7aa85c&originHeight=734&originWidth=784&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ua8812699-2283-400b-ab9a-944a9291a13&title=&width=702)<br />ConcurrentHashmap jdk1.8put流程<br />**get查询**<br />get很简单，和HashMap基本相同，通过key计算位置，table该位置key相同就返回，如果是红黑树按照红黑树获取，否则就遍历链表获取。
<a name="xsni2"></a>
### JDK 1.7 和 JDK 1.8 的 ConcurrentHashMap 实现有什么不同？

- **线程安全实现方式**：
   - JDK 1.7 用 Segment 分段锁来保证安全， Segment 是继承自 ReentrantLock。
   - JDK 1.8 放弃了 Segment 分段锁的设计，采用 Node + CAS + synchronized 保证线程安全，锁粒度更细，synchronized 只锁定当前链表或红黑二叉树的首节点。
- **Hash 碰撞解决方法** : 
   - JDK 1.7 采用拉链法。
   - JDK 1.8 采用拉链法结合红黑树（链表长度超过一定阈值时，将链表转换为红黑树）。
- **并发度**：
   - JDK 1.7 最大并发度是 Segment 的个数，默认是 16。
   - JDK 1.8 最大并发度是 Node 数组的大小，并发度更大。
<a name="ceFZ9"></a>
## HashMap 内部节点是有序的吗？
HashMap是无序的，根据 hash 值随机插入。如果想使用有序的Map，可以使用LinkedHashMap 或者 TreeMap。
<a name="jOsnN"></a>
## LinkedHashMap 怎么实现有序的？
LinkedHashMap维护了一个双向链表，有头尾节点。<br />并在正常HashMap的每个节点里加入了前后节点的信息：LinkedHashMap 节点 Entry 内部除了继承 HashMap 的 Node 属性，还有 before 和 after 用于标识前置节点和后置节点。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688286257654-9049fe35-c7a7-43a5-95f2-7cc900a5b424.png#averageHue=%23f9f1e4&clientId=u17aefc5c-1ff8-4&from=paste&id=u465b8333&originHeight=309&originWidth=634&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u35ffc1eb-9f7a-4880-a14a-9f3b83586f5&title=)<br />Entry节点<br />可以实现**按插入的顺序或访问顺序排序**。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688286258099-4e1245ac-b1e1-49d6-b9f1-24a1a6e4b0cd.png#averageHue=%23fdfaf9&clientId=u17aefc5c-1ff8-4&from=paste&id=uc056ecfa&originHeight=499&originWidth=727&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u19eaa939-8e81-4965-9d9b-46b39053ba5&title=)<br />LinkedHashMap实现原理
<a name="LuDsE"></a>
### p.s. 对应的Python里的是OrderedDict
Python3.7里普通Dict就是和OrderedDict一样**按照插入顺序**来排序的。<br />OrderedDict的用法<br />[https://www.geeksforgeeks.org/ordereddict-in-python/](https://www.geeksforgeeks.org/ordereddict-in-python/)<br />但OrderedDict 和一般dict仍然有的区别<br />[https://stackoverflow.com/questions/50872498/will-ordereddict-become-redundant-in-python-3-7](https://stackoverflow.com/questions/50872498/will-ordereddict-become-redundant-in-python-3-7)<br />下面是用法：
```python
# A Python program to demonstrate working of deletion
# re-insertion in OrderedDict
from collections import OrderedDict

print("Before deleting:\n")
od = OrderedDict()  # {} normal dict
od['a'] = 1
od['b'] = 2
od['c'] = 3
od['d'] = 4

for key, value in od.items():
    print(key, value)

print("\nAfter deleting:\n")
od.pop('c')
for key, value in od.items():
    print(key, value)

print("\nAfter re-inserting:\n")
od['c'] = 3
for key, value in od.items():
    print(key, value)
print(od.keys())
print(od.values())
```
```python
Before deleting:

a 1
b 2
c 3
d 4

After deleting:

a 1
b 2
d 4

After re-inserting:

a 1
b 2
d 4
c 3
odict_keys(['a', 'b', 'd', 'c'])
odict_values([1, 2, 4, 3])
```
<a name="i7q0O"></a>
## TreeMap 怎么实现有序的？
TreeMap 是**h**，内部是通过红黑树来实现。所以要么 key 所属的类实现 Comparable 接口，或者自定义一个实现了 Comparator 接口的比较器，传给 TreeMap 用于 key 的比较。<br />![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688286257632-1a885b5b-2976-424f-8bc5-e9045e4b2965.png#averageHue=%23f6f6f5&clientId=u17aefc5c-1ff8-4&from=paste&id=u02e2d57a&originHeight=548&originWidth=1231&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=ua3f91150-54ae-42b8-af64-6cc63852404&title=)<br />TreeMap
<a name="vMpAq"></a>
# Set
<a name="th1i2"></a>
## 讲讲HashSet的底层实现？
HashSet 底层就是**基于 HashMap 实现**的。（ HashSet 的源码⾮常⾮常少，因为除了 clone() 、 writeObject() 、 readObject() 是 HashSet⾃⼰不得不实现之外，其他⽅法都是直接调⽤ HashMap 中的⽅法。<br />HashSet的add方法，直接调用HashMap的put方法，将添加的元素作为key，new一个Object作为value，直接调用HashMap的put方法，它会根据返回值是否为空来判断是否插入元素成功。
```java
public boolean add(E e) {
    return map.put(e, PRESENT)==null;
}
```
![](https://cdn.nlark.com/yuque/0/2023/png/25962088/1688289307733-e30e1ac1-eba9-4c20-8320-46497ac47a22.png#averageHue=%23cae688&clientId=u17aefc5c-1ff8-4&from=paste&height=218&id=ucaf23774&originHeight=286&originWidth=449&originalType=url&ratio=2&rotation=0&showTitle=false&status=done&style=none&taskId=u5f691233-033e-402a-9b0c-e636252f639&title=&width=343)<br />HashSet套娃<br />而在HashMap的put方法中，进行了一系列判断，最后的结果是，只有在key在table数组中不存在的时候，才会返回插入的值。所以如果put方法返回为空说明table里已存在该元素。
```java
if (e != null) { // existing mapping for key
    V oldValue = e.value;
    if (!onlyIfAbsent || oldValue == null)
        e.value = value;
    afterNodeAccess(e);
    return oldValue;
}
```
