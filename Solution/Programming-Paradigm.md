# 编程范式

### 命令式编程

主要思想是关注计算机执行的步骤，即**一步一步告诉计算机先做什么再做什么**。比如：如果你想在一个数字集合 collection(变量名) 中筛选大于 5 的数字，你需要这样告诉计算机：
* 第一步，创建一个存储结果的集合变量 results；
* 第二步，遍历这个数字集合 collection；
* 第三步：一个一个地判断每个数字是不是大于 5，如果是就将这个数字添加到结果集合变量 results 中。

代码实现如下：
```
List<int> results = new List<int>();
foreach(var num in collection)
{
    if (num > 5)
          results.Add(num);
}
```
 很明显，不管你用的是 C, C++ 还是 C#, Java, Javascript, BASIC, Python, Ruby 等等，你都可以以这个方式写。
 
#### 面向过程  

另一个经典例子：把大象放在冰箱分为几步？
* 第一步：把冰箱打开
* 第二步：把大象装进去
* 第三步：把冰箱门关上

#### 面向对象

面向对象编程（OOP：Object Oriented Programming）把对象作为程序的基本单元，一个对象包含了数据和操作数据的函数，它最早由 Alan Kay 在 1966 年或 1967 年在研究生期间提出。

与面向过程编程不同，在面向过程编程中，数据和处理数据的函数彼此独立，我们需要先将数据处理成函数能接受的格式，然后调用相关函数。而在在面向对象中，数据和处理数据的函数都在一个类中，通过初始化实例传递数据。

现如今，当谈及面向对象时，下意识的就会联想出它的三个特性：封装、继承与多态。
![1709ac3a2cfff15f](https://cdn.jsdelivr.net/gh/stelalae/oss@master/files/2020/05/14/LZpKjP.jpg)


用面向对象的方式来解释「把大象关进冰箱」：
* 1、冰箱.开门()
* 2、冰箱.放入(大象)
* 3、冰箱.关门()

无论是面向过程还是面向对象，两种编程方式都要对程序进行模块化，都需要调用过程或者方法来改变程序的数据，所以在某种程度上，它们的本质是一样的，这也是为什么它们都同属于命令式语言的原因。

只不过从形式上，面向对象编程语言具有更高的抽象能力，程序员可以更容易的实现一些常用的设计模式，比如封装、继承、多态等等。

### 声明式编程

以数据结构的形式来表达程序执行的逻辑。它的主要思想是**告诉计算机应该做什么，但不指定具体要怎么做**。SQL 语句就是最明显的一种声明式编程的例子，例如：
```
SELECT * FROM collection WHERE num > 5
```
网页编程中用到的 HTML 和 CSS 也都属于声明式编程。

通过观察声明式编程的代码我们可以发现，它有一个特点是它不需要创建变量用来存储数据，另一个特点是它不包含循环控制的代码如 for， while。

### 函数式编程

函数式编程和声明式编程是有所关联的，因为他们思想是一致的：即只关注做什么而不是怎么做。但函数式编程不仅仅局限于声明式编程。函数式编程最重要的特点是 **“函数第一位”，即函数可以出现在任何地方，比如你可以把函数作为参数传递给另一个函数，不仅如此你还可以将函数作为返回值**。大部分常见的编程语言一半都已经提供了对这种编程方式的支持，比如 JavaScript，再有 C# 中的 LINQ 和 Java 中的 Lambda 和闭包的概念。

### 响应式编程

**响应式编程是一种面向数据流和变化传播的编程范式**。这意味着可以在编程语言中很方便地表达静态或动态的数据流，而相关的计算模型会自动将变化的值通过数据流进行传播。即监听数据变化或事件，然后再做下一步，这种逻辑往往都是异步的。

### 函数响应式编程

函数响应式结合了函数式和响应式的优点，把函数范式里的一套思路和响应式编程合起来就是函数响应式编程。

传统的面向对象编程通过抽象出的对象关系来解决问题。函数式编程通过function的组合来解决问题，响应式编程通过函数式编程的方式来解决回调地狱的问题。用传统的面向对象来处理异步事件不是很直观，处理并发也是件麻烦的事情，所以才产生了函数响应式编程。


* [编程范式粗讲](https://juejin.im/post/5d59425a5188252700773da7)
* [声明式？命令式？面向对象？函数式？](https://blog.csdn.net/wozaixiaoximen/article/details/103490819)
* [编程范式：命令式编程(Imperative)、声明式编程(Declarative)和函数式编程(Functional)](https://www.cnblogs.com/sirkevin/p/8283110.html)
* [响应式和函数式，两个容易混淆的概念](https://www.jianshu.com/p/0c8a692a0c7f)
* [编程范式 （Programming paradigm）](https://www.jianshu.com/p/848abe46da99)