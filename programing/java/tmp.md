

## 选择结构

* if...else/switch

## 循环结构

增强 `for` 循环（主要用于数组）

```java
for(声明语句 : 表达式)
{
   //代码句子
}
```

* String
* 
局部变量是在栈上分配的。

## Java 8 新特性

* Lambda 表达式
* 方法引用
* 默认方法
* 新工具 
* Stream API
* Date Time API
* Optional 类
* ashorn, JavaScript 引擎








 
## 接口的增强
 
接口的默认方法和静态方法
 
 
 
## lambda表达式
 
lambda表达式本质是匿名方法，下面是一些lambda表达式：
 
lambda表达式：(int x, int y) -> x + y
 
解析：接收x和y这两个整形参数并返回它们的和
 
lambda表达式：() -> 42
 
解析：不接收参数，返回整数42
 
lambda表达式：(String s) -> { System.out.println(s); }
 
解析：接收一个字符串并把它打印到控制台，不返回值
 
 
 
lambda表达式的语法由参数列表、箭头符号->和函数体组成。函数体既可以是一个表达式，也可以是一个语句块：
表达式：表达式会被执行然后返回执行结果。
语句块：语句块中的语句会被依次执行，就像方法中的语句一样。
return语句会把控制权交给匿名方法的调用者
break和continue只能在循环中使用
如果函数体有返回值，那么函数体内部的每一条路径都必须返回值
 
[Java Lambda表达式入门](http://blog.csdn.net/renfufei/article/details/24600507)
 
 
 
## 相关文章
 
[JAVA8 十大新特性详解](http://www.jb51.net/article/48304.htm)
 
[Java 8 中你可能没听过的 10 个新特性](http://blog.jobbole.com/66990/)
 






 
 
Vector 和 Hashtable类被定义为线程安全（同步）类，使用效率受到一定的限制，
Stack类在设计时存在一些不恰当的方法，因此，三个类建议用新版本中的ArrayList类、Hashtable
类、和LinkedList类取代。 要获得线程安全的功能，可以使用Colections类下面的相应同步方法来
获得，如：synchronizedList()、synchronizedMap()、synchronizedSet()等。
 
 
 
Set和List对比：
Set：检索元素效率低下，删除和插入效率高，插入和删除不会引起元素位置改变。
List：和数组类似，List可以动态增长，查找元素效率高，插入删除元素效率低，因为会引起其他元素位置改变。
 
Set子接口：无序，不允许重复。
List子接口：有序，可以有重复元素。
 
 
 
HashMap和HashTable
a.HashMap去掉了HashTable的contains方法，但是加上了containsValue()和containsKey()方法。
b.HashTable同步的，而HashMap是非同步的，效率上比HashTable要高。
c.HashMap允许空键值，而HashTable不允许。
 
 
 
 
 
对于查找和删除较为频繁，且元素数量较多的应用，Set或Map是更好的选择；
 
 
 
 
 
非多线程环境：
 
 
HashSet 适用于对排序没有要求的非重复元素的存放；
 
TreeSet 适用于要排序的非重复元素的存放；
 
 
 
HashMap 适用于大部分key-value的存取场景；
 
TreeMap 适用于需排序存放的key-value场景。
 

 
Java集合类框架的最佳实践有哪些？
 
根据应用的需要正确选择要使用的集合的类型对性能非常重要，比如：假如元素的大小是固定的，而且能事先知道，我们就应该用Array而不是ArrayList。
 
有些集合类允许指定初始容量。因此，如果我们能估计出存储的元素的数目，我们可以设置初始容量来避免重新计算hash值或者是扩容。
 
为了类型安全，可读性和健壮性的原因总是要使用泛型。同时，使用泛型还可以避免运行时的ClassCastException。
 
使用JDK提供的不变类(immutable class)作为Map的键可以避免为我们自己的类实现hashCode()和equals()方法。
 
编程的时候接口优于实现。
 
底层的集合实际上是空的情况下，返回长度是0的集合或者是数组，不要返回null。
 
 
 
HashSet和TreeSet有什么区别？
 
HashSet是由一个hash表来实现的，因此，它的元素是无序的。add()，remove()，contains()方法的时间复杂度是O(1)。
 
另一方面，TreeSet是由一个树形的结构来实现的，它里面的元素是有序的。因此，add()，remove()，contains()方法的时间复杂度是O(logn)。
 
 
 
数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？
 
Array可以包含基本类型和对象类型，ArrayList只能包含对象类型。
 
Array大小是固定的，ArrayList的大小是动态变化的。
 
ArrayList提供了更多的方法和特性，比如：addAll()，removeAll()，iterator()等等。
 
对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。
 
 
 
 
 
 
 
 
 
会用模型驱动user.save()，代替dao。
少传一个参数，概念上优雅了一些。模型驱动太考验建模能力，一定要在一个范围内把所有问题想清楚再使用。建议把DDD那本书看个两三遍再说。
不过这东西看上去真的很吸引人。


能用metadata生成一堆乱七八杂的代码，这下爽多了。
metadata的解释是“描述数据的数据”，比方说数据库的表结构定义可能就算是一种metadata。在写代码过程中能正确的抽象出元数据之后，眼光会提高一个层次，至于是不是要搞生成代码的工具，因项目而异。
曾经用过一段时间的freemarker，写一些轻量级的代码生成工具还是挺好用的。

模板技术：FreeMarker























[TOC]

## 基础知识
 
### clone
 
浅克隆
实现Cloneable接口（不这样做运行时会有CloneNotSupportedException），重写clone方法（该方法来自Object类）并将访问权限限定符改为public
 
深克隆
2．Java的clone()方法
 
⑴clone方法将对象复制了一份并返回给调用者。一般而言，clone（）方法满足：
①对任何的对象x，都有x.clone() !=x//克隆对象与原对象不是同一个对象
②对任何的对象x，都有x.clone().getClass()= =x.getClass()//克隆对象与原对象的类型一样
③如果对象x的equals()方法定义恰当，那么x.clone().equals(x)应该成立。
 
⑵Java中对象的克隆
 
①为了获取对象的一份拷贝，我们可以利用Object类的clone()方法。
②在派生类中覆盖基类的clone()方法，并声明为public。
③在派生类的clone()方法中，调用super.clone()。
④在派生类中实现Cloneable接口。
 
利用串行化来做深复制（主要是为了避免重写比较复杂对象的深复制的clone（）方法，也可以程序实现断点续传等等功能）
这样做的前提是对象以及对象内部所有引用到的对象都是可串行化的，否则，就需要仔细考察那些不可串行化的对象或属性可否设成transient，从而将之排除在复制过程之外。
```java
public Object deepClone()
{
//将对象写到流里
ByteArrayOutoutStream bo=new ByteArrayOutputStream();
ObjectOutputStream oo=new ObjectOutputStream(bo);
oo.writeObject(this);
//从流里读出来
ByteArrayInputStream bi=new ByteArrayInputStream(bo.toByteArray());
ObjectInputStream oi=new ObjectInputStream(bi);
return(oi.readObject());
}
```
 
 
### Comparable
 
Comparable实现接口
 
强烈推荐（虽然不是必需的）使自然排序与 equals 一致。所谓与equals一致是指对于类 C 的每一个 e1 和 e2 来说，当且仅当 (e1.compareTo((Object)e2) == 0) 与e1.equals((Object)e2) 具有相同的布尔值时，类 C 的自然排序才叫做与 equals 一致 。
 
2.实现什么方法
 
int compareTo(T o)
比较此对象与指定对象的顺序。如果该对象小于、等于或大于指定对象，则分别返回负整数、零或正整数。
 
强烈推荐 (x.compareTo(y)==0) == (x.equals(y)) 这种做法，但不是 严格要求这样做。一般来说，任何实现 Comparable 接口和违背此条件的类都应该清楚地指出这一事实。推荐如此阐述：“注意：此类具有与 equals 不一致的自然排序。”
 
Comparator位于包java.util下，而Comparable位于包java.lang下，Comparable接口将比较代码嵌入自身类中，而后者在一个独立的类中实现比较。 如果类的设计师没有考虑到Compare的问题而没有实现Comparable接口，可以通过 Comparator来实现比较算法进行排序，并且为了使用不同的排序标准做准备，比如：升序、降序。
```java
public int compareTo(Object o) {
return this.age - ((ComparableUser) o).getAge();
}
```
选择Comparable接口还是Comparator？
一个类实现了Comparable接口则表明这个类的对象之间是可以相互比较的，这个类对象组成的集合就可以直接使用sort方法排序。
Comparator可以看成一种算法的实现，将算法和数据分离，Comparator也可以在下面两种环境下使用：
1、类的设计师没有考虑到比较问题而没有实现Comparable，可以通过Comparator来实现排序而不必改变对象本身
2、可以使用多种排序标准，比如升序、降序等。
 
### equals
 
Object类中的equals()方法等价于==
 
equals方法必须满足
自反性（x.equals(x)必须返回true）
对称性（x.equals(y)返回true时，y.equals(x)也必须返回true）
传递性（x.equals(y)和y.equals(z)都返回true时，x.equals(z)也必须返回true）
一致性（当x和y引用的对象信息没有被修改时，多次调用x.equals(y)应该得到同样的返回值）
而且对于任何非null值的引用x，x.equals(null)必须返回false。
 
实现高质量的equals方法的诀窍包括：
1. 使用==操作符检查“参数是否为这个对象的引用”；
2. 使用instanceof操作符检查“参数是否为正确的类型”；
3. 对于类中的关键属性，检查参数传入对象的属性是否与之相匹配；
4. 编写完equals方法后，问自己它是否满足对称性、传递性、一致性；
5. 重写equals时总是要重写hashCode；
6. 不要将equals方法参数中的Object对象替换为其他的类型，在重写时不要忘掉@Override注解。
 
一个非常完美的equals方法的写法：
 
```java
public boolean equals(Object otherObject)
{
// a quick test to see if the objects are identical
if (this == otherObject) return true;
// must return false if the explicit parameter is null
if (otherObject == null) return false;
// if the classes don't match, they can't be equal
if (getClass() != otherObject.getClass()) return false;
// now we know otherObject is a non-null Employee
Employee other = (Employee) otherObject;
// test whether the fields have identical values
return name.equals(other.name) && salary == other.salary && hireDay.equals(other.hireDay);
}
```
### hashCode
 
这个方法返回一个整型值（hash code value），如果两个对象被equals()方法判断为相等，那么它们就应该拥有同样的hash code。Object类的hashCode()方法为不同的对象返回不同的值，Object类的hashCode值表示的是对象的地址。
hashCode的一般性契约（需要满足的条件）如下：
1.在Java应用的一次执行过程中，如果对象用于equals比较的信息没有被修改，那么同一个对象多次调用hashCode()方法应该返回同一个整型值。应用的多次执行中，这个值不需要保持一致，即每次执行都是保持着各自不同的值。
2.如果equals()判断两个对象相等，那么它们的hashCode()方法应该返回同样的值。
3.并没有强制要求如果equals()判断两个对象不相等，那么它们的hashCode()方法就应该返回不同的值。即，两个对象用equals()方法比较返回false，它们的hashCode可以相同也可以不同。但是，应该意识到，为两个不相等的对象产生两个不同的hashCode可以改善哈希表的性能。
 
[通用的Java hashCode重写方案](http://blog.csdn.net/sunmenggmail/article/details/18660699)
 
### equals与hashCode
 
当覆写（override）了equals()方法之后，必须也覆写hashCode()方法，反之亦然。
 
(1)如果两个对象相同（equals方法返回true），那么它们的hashCode值一定要相同；
(2)如果两个对象的hashCode相同，它们并不一定相同。
 
### Serializable
 
2、当一个父类实现序列化，子类自动实现序列化，不需要显式实现Serializable接口，不过即使显
示实现了，也没有错，效果一样的；
3、当一个对象的实例变量引用其他对象，序列化该对象时也把引用对象进行序列化；否则运行时会
有异常
4并非所有的对象都可以序列化，至于为什么不可以，有很多原因了,比如：
a.安全方面的原因，比如一个对象拥有private，public等field，对于一个要传输的对象
，比如写到文件，或者进行rmi传输等等，在序列化进行传输的过程中，这个对象的private等域是
不受保护的。
b. 资源分配方面的原因，比如socket，thread类，如果可以序列化，进行传输或者保存，
也无法对他们进行重新的资源分配，而且，也是没有必要这样实现。
相关注意事项
5、反过来父类未实现Serializable，子类实现了，序列化子类实例的时候，父类的属性是直接被跳
过不保存
 
### transient
 
1）一旦变量被transient修饰，变量将不再是对象持久化的一部分，该变量内容在序列化后无法获
得访问。
 
2）transient关键字只能修饰变量，而不能修饰方法和类。注意，本地变量是不能被transient关
键字修饰的。变量如果是用户自定义类变量，则该类需要实现Serializable接口。
 
3）一个静态变量不管是否被transient修饰，均不能被序列化。
 
我们知道在Java中，对象的序列化可以通过实现两种接口来实现，若实现的是Serializable接口
，则所有的序列化将会自动进行，若实现的是Externalizable接口，则没有任何东西可以自动序列
化，需要在writeExternal方法中进行手工指定所要序列化的变量，这与是否被transient修饰无关
。因此第二个例子输出的是变量content初始化的内容，而不是null。
 
### instanceof
 
instanceof关键字用于判断一个引用类型变量所指向的对象是否是一个类（或接口、抽象类、父类）的实例。
使用instanceof在绝大多数情况下并不是推荐的做法，应当好好利用多态。
 
另外，数组类型也可以使用instanceof来比较。比如
 
String str[] = new String[2];
则str instanceof String[]将返回true。
 
### 自动装箱和拆箱
 
Integer f1 = 100, f2 = 100, f3 = 150, f4 = 150;
 
System.out.println(f1 == f2);
System.out.println(f3 == f4);
结果为true,false
 
### 多线程
 
Thread.sleep() 保持对象锁，让出CPU
 
Thread.yield()
 
让出CPU的使用权，给其他线程执行机会、让同等优先权的线程运行（但并不保证当前线程会被JVM再次调度、使该线程重新进入Running状态），如果没有同等优先权的线程，那么yield()方法将不会起作用。
 
thread.join()
 
object.wait()
 
当一个线程执行到wait()方法时，他就进入到一个和该对象相关的等待池(Waiting Pool)中，同时失去了对象的机锁—暂时的，wait后还要返还对象锁。当前线程必须拥有当前对象的锁，如果当前线程不是此锁的拥有者，会抛出IllegalMonitorStateException异常,所以wait()必须在synchronized block中调用。
 
object.notify()/notifyAll()
 
唤醒在当前对象等待池中等待的第一个线程/所有线程。notify()/notifyAll()也必须拥有相同对象锁，否则也会抛出IllegalMonitorStateException异常。
 
 
sleep() 和 wait() 有什么区别?
sleep()方法是使线程停止一段时间的方法。在sleep 时间间隔期满后，线程不一定立即恢复执行。
这是因为在那个时刻，其它线程可能正在运行而且没有被调度为放弃执行，除非(a)"醒来"的线程具
有更高的优先级
(b)正在运行的线程因为其它原因而阻塞。
wait()是线程交互时，如果线程对一个同步对象x 发出一个wait()调用，该线程会暂停执行，被调
对象进入等待状态，直到被唤醒或等待时间到。
 

[![061046391107893](http://www.chenjianhang.com/wp-content/uploads/2015/09/061046391107893.jpg)](http://www.chenjianhang.com/wp-content/uploads/2015/09/061046391107893.jpg)
 
### synchronized
 
 
synchronized关键字是不能继承的
 

 
被synchronized保护的数据应该是私有的。
 

 
再举个例子：当有多个线程读写文件时，读操作和写操作会发生冲突现象，写操作和写操作会发生冲突现象，但是读操作和读操作不会发生冲突现象。
 
但是采用synchronized关键字来实现同步的话，就会导致一个问题：
 
如果多个线程都只是进行读操作，所以当一个线程在进行读操作时，其他线程只能等待无法进行读操作。
 
因此就需要一种机制来使得多个线程都只是进行读操作时，线程之间不会发生冲突，通过Lock就可以办到。
 
另外，通过Lock可以知道线程有没有成功获取到锁。这个是synchronized无法办到的。
 
总结一下，也就是说Lock提供了比synchronized更多的功能。但是要注意以下几点：
 
1）Lock不是Java语言内置的，synchronized是Java语言的关键字，因此是内置特性。Lock是一个类，通过这个类可以实现同步访问；
 
2）Lock和synchronized有一点非常大的不同，采用synchronized不需要用户去手动释放锁，当synchronized方法或者synchronized代码块执行完之后，系统会自动让线程释放对锁的占用；而Lock则必须要用户去手动释放锁，如果没有主动释放锁，就有可能导致出现死锁现象。
lock
 
lock()、tryLock()、tryLock(long time, TimeUnit unit)和lockInterruptibly()是用来获取锁的。unLock()方法是用来释放锁的。newCondition()这个方法暂且不在此讲述，会在后面的线程协作一文中讲述。
```java
Lock lock = ...;
lock.lock();
try{
//处理任务
}catch(Exception ex){
 
}finally{
lock.unlock(); //释放锁
}
```
注意，当一个线程获取了锁之后，是不会被interrupt()方法中断的。因为本身在前面的文章中讲过单独调用interrupt()方法不能中断正在运行过程中的线程，只能中断阻塞过程中的线程。
 
2）synchronized在发生异常时，会自动释放线程占有的锁，因此不会导致死锁现象发生；而Lock在发生异常时，如果没有主动通过unLock()去释放锁，则很可能造成死锁现象，因此使用Lock时需要在finally块中释放锁；
 
### 其他
 
接口优先于抽象类：
 
 
重写要求子类被重写方法与父类被重写方法有相同的返回类型，比父类被重写方法更好访问，不能
比父类被重写方法声明更多的异常（里氏代换原则）
HashMap 类没有分类或者排序。它允许一个 null 键和多个 null 值。
Hashtable 类似于 HashMap，但是不允许 null 键和 null 值。它也比 HashMap 慢，因为它是同
步的。
 
 
异常尽量不被作为程序正常流程的一部分来使用
 
 
HashMap：无序
 
LinkedHashMap：更新保持插入顺序
 
TreeMap：按键排序
 
用enum代替int常量
 
一个内部类对象的创建不能像外部类一样创建
内部类不能定义static型成员
 
protected：同一包中的非子类可以访问
缺省：同一包内的所有类可以都可以访问，包外的不可以，即使是子类
 
 
当复制大量数据时，使用 System.arraycopy()
 
java程序在执行过程中，类，对象以及它们成员加载、初始化的顺序如下：
1、首先加载要创建对象的类及其直接与间接父类。
2、在类被加载的"同时"会将静态成员进行加载，主要包括静态成员变量的初始化，静态语句块的
执行，在加载时按代码的先后顺序进行。（程序运行期间，一个类只执行一次，在在该类（或者其子类）第一次创建对象前或者该类（或者其子类）的静态成员第一次被使用前执行）
3、需要的类加载完成后，开始创建对象，首先会加载非静态的成员，主要包括非静态成员变量的
初始化，非静态语句块的执行，在加载时按代码的先后顺序进行。
4、最后执行构造器，构造器执行完毕，对象生成。
 
 
```java
class HelloA {
 
    public HelloA() {
        System.out.println("HelloA");
    }
 
    { System.out.println("I'm A class"); }
 
    static {
 
        System.out.println("static A");
    }
 
}
 
public class HelloB extends HelloA {
    public HelloB() {
        System.out.println("HelloB");
    }
 
    { System.out.println("I'm B class"); }
 
    static {
 
        System.out.println("static B");
    }
 
    public static void main(String[] args) {
        new HelloB();
    }
 
}
 
```
运行结果：
 
static A
static B
I'm A class
HelloA
I'm B class
HelloB
 
 
```java
public class foo{
 
    public static void main (String[] args) {
 
        String s;
 
        System.out.println("s=" + s);
 
    }
 
}
```
 
译不通过
 
ArrayList list = new ArrayList(20);中的list扩充0次
 
不通过构造函数也能创建对象
解析：Java创建对象的几种方式（重要）：
(1) 用new语句创建对象，这是最常见的创建对象的方法。
(2) 运用反射手段,调用java.lang.Class或者java.lang.reflect.Constructor类的newInstance()
实例方法。
(3) 调用对象的clone()方法。
(4) 运用反序列化手段，调用java.io.ObjectInputStream对象的 readObject()方法。
(1)和(2)都会明确的或者显式的调用构造函数 ；(3)是在内存上对已有对象的影印，所以不会调用构
造函数 ；(4)是从文件中还原类的对象，也不会调用构造函数。
 
java将内存空间分成两块，栈和堆，在栈中保存基本类型和引用变量；在堆中保存对象。
 
协变返回类型指的是子类中的成员函数的返回值类型不必严格等同于父类中被重写的成员函数的返回值类型，而可以是更 "狭窄" 的类型
 

 
如果配合Java 5增加的atomic wrapper classes，对它们的increase之类的操作就不需要sychronized。

 
在java 1.5的java.util.concurrent.atomic包下提供了一些原子操作类，即对基本数据类型的 自增（加1操作），自减（减1操作）、以及加法操作（加一个数），减法操作（减一个数）进行了封装，保证这些操作是原子性操作。atomic是利用CAS来实现原子性操作的（Compare And Swap），CAS实际上是利用处理器提供的CMPXCHG指令实现的，而处理器执行CMPXCHG指令是一个原子性操作。
 
 
注意：当设计多线程应用程序的时候，一定不要依赖于线程的优先级。因为线程调度优先级操作是没有保障的，只能把线程优先级作用作为一种提高程序效率的方法，但是要保证程序不依赖这种操作。
 
sleep(long millis)和Thread.sleep(long millis, int nanos)
当睡眠时间到期，则返回到可运行状态。
 
yield()
将导致线程从运行状态转到可运行状态，但有可能没有效果。
 
join()方法还有带超时限制的重载版本。例如t.join(5000);则让线程等待5000毫秒，如果超过这个时间，则停止等待，变为可运行状态。
 
3、静态同步方法和非静态同步方法将永远不会彼此阻塞，因为静态方法锁定在Class对象上，非静态方法锁定在该类的对象上。
五、何时需要同步
 
在多个线程同时访问互斥（可交换）数据时，应该同步以保护数据，确保两个线程不会同时修改更改它。
 
对于非静态字段中可更改的数据，通常使用非静态方法访问。
 
对于静态字段中可更改的数据，通常使用静态方法访问。
 
如果需要在非静态方法中使用静态字段，或者在静态字段中调用非静态方法，问题将变得非常复杂。已经超出SJCP考试范围了。
即使是线程安全类，也应该特别小心，因为操作的线程是间仍然不一定安全。
 
 
与每个对象具有锁一样，每个对象可以有一个线程列表，他们等待来自该信号（通知）。线程通过执行对象上的wait()方法获得这个等待列表。从那时候起，它不再执行任何其他指令，直到调用对象的notify()方法为止。如果多个线程在同一个对象上等待，则将只选择一个线程（不保证以何种顺序）继续执行。如果没有线程等待，则不采取任何特殊操作。
 
http://www.cnblogs.com/riskyer/p/3263032.html
 
信号量
阻塞队列
 
Test tt = null;
tt.sta();
不会异常
 
## 其他
 


join sleep interrupte
 
Java-ODBC 桥是在 Java 没甚麼数据库连接时的过渡性产物，连 JDBC 2 都支援不全。
因此，既然现在大部分数据库都有更好的桥了，Java 8 决定把它移除。

Java 编程过程中，进行数据库连接、I/O流操作时务必小心，在使用完毕后，即使关闭以释放资源。因为对这些大对象的操作会造成系统大的开销，稍有不慎，会导致严重的后果。
 
 
 
 
使用移位操作来代替'a / b'操作或者‘a * b’，如果不是对效率要求很高的底层代码，没这个必要，影响可读性。如果用了，最好加上注释