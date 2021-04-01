---
title: JVM
---

## 1 JVM Stacks
线程私有。
栈帧（stack frame）：栈中元素。每一个方法从调用直至执行完成的过程，就对应着一个栈帧在虚拟机栈中入栈到出栈的过程。
栈帧由操作数栈，局部变量数组和一个Class引用组成（指向当前方法在运行时常量池中对应的Class）。
2  类加载机制
2.1 类加载阶段
加载 Loading：找Class文件
验证 Verification：验证格式、依赖
准备 Preparation：静态字段、方法表
解析 Resolution：符号解析为引用
初始化 Initialization：构造器、静态变量赋值、静态代码块
使用 Using
卸载 Unloading
2.2 加载、初始化时机
2.3 类加载器
BootstrapClassLoader
ExtClassLoader
AppClassLoader
    如何避免重复加载？
双亲委派：当一个类加载器负责加载某个 Class 时，先让父类加载器试图加载该 Class ，只有在父类加载器 无法加载该类时才尝试从自己的类路径中加载该类
全盘负责：当一个类加载器负责加载某个 Class 时，该 Class 所依赖的和引用的其他 Class 也将由该类加载 器负责载入，除非显示使用另外一个类加载器来载入
缓存加载：保证所有加载过的 Class 都会被缓存，当程序需要使用某个 Class 对象时，类加载器先从缓存区中搜 索该 Class
3. Java Memory Model
堆内存与线程栈
每个线程都只能访问自己的线程栈。
所有原生类型的局部变量都存储在线程栈中，因此对其它线程不可见。
线程间可以传输原生变量值的副本，但不能共享原生局部变量本身。

堆内存中包含了Java代码中创建的所有对象。
对象引用，则引用地址存在栈中的局部变量槽位中，实际的对象内容在堆中。
对象的成员变量与对象本身一起存储在堆中，不论成员变量的类型是原生数值，还是对象引用。
类的静态变量和类定义一样都保存在堆中。
JVM内存整体结构


堆内存

堆内存是所有线程共用的内存空间，JVM 将 Heap 内存分为年轻代（Young generation）和 老年代（Old generation, 也叫 Tenured）两部分。 
年轻代还划分为 3 个内存池，新生代（Eden space）和存活区（Survivor space）, 在大部分 GC 算法中有 2 个存活区（S0, S1），在我们可 以观察到的任何时刻，S0 和 S1 总有一个是空的, 但一般较小，也不浪费多少空间。
 Non-Heap 本质上还是 Heap，只是一般不归 GC 管理，里面划分为 3 个内存池。
 Metaspace, 以前叫持久代（永久代, Permanent generation）, Java8 换了个名字叫 Metaspace. 
CCS, Compressed Class Space, 存放 class 信息的，和 Metaspace 有交叉。 
Code Cache, 存放 JIT 编译器编译后的本地机器 代码。
JVM启动参数

-开头，标准参数，所有JVM都要实现，并且向后兼容
-D，系统参数
-X，非标准参数，也是主流使用最多的参数，基本都是传给JVM的。不保证所有JVM实现或兼容，可以使用java -X命令查看
-XX，非稳定参数，专门控制JVM行为，如GC等。随时可能下个版本取消。
-XX, +-Flags，是对布尔值进行开关
-XX，key=value形式，指定某个选项的值
