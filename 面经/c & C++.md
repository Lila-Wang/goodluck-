>### 面试题1：变量的声明和定义有什么区别
>>变量的定义为变量分配地址和存储空间，但变量的声明不分配地址。一个变量可以在多个地方声明，但是只在一个地方定义，加入extern修饰的是变量的声明，说明此变量在文件以外或文件后面部分定义。

```
int main() 
{
 extern int A;   //这是个声明而不是定义，声明A是一个已经定义了的外部变量。声明时可以把变量类型去掉。
 dosth(); //执行函数
}
int A; //是定义，定义了A为整型的外部变量
```

>### 面试题2：写出 bool 、int、 float、指针变量与“零值”比较的 if 语句
```
//bool 
if(flag)
{A;}
else
{B;}

//int
if(0 != flag)
{A;}
else
{B;}

//指针型
if(NULL == flag)
{A;}
else
{B;}

//float
if ( ( flag >= -NORM ) && ( flag <= NORM ) ) 
{A;} 


flag通常用来作为一个指示变化的变量的名称，c语言中一般设置一个变量flag。当一种情况时，置flag为1，另外一种情况，置flag为2.

例：设置标志，如：A事件和B事件

A事件正在发生 flag=1, A事件没有发生 flag=0;

B检测flag，如果flag=1,说明A正在执行，B就不执行; B检测flag，如果flag=0,说明A没有执行，B就执行

常用于同时访问共享内存，或者同一块儿变量，互斥。
```
>### 面试题3：sizeof 和 strlen区别
>> 1 sizeof 是操作符，参数可以是数据类型，也可以是变量。strlen 是库函数，只能以结尾为'\0'的字符串作参数。
>> 2 编译器在编译时就计算出sizeof 的结果，但strlen函数必须在运行时才能计算出来。sizeof计算的是数据类型占内存的大小，strlen计算的是字符串实际的长度。
>> 3 数组做sizeof的参数不退化，传递给strlen就退化为指针。
 



面试题 4：C 语言的关键字 static 和 C++ 的关键字 static 有什么区别
在 C 中 static 用来修饰局部静态变量和外部静态变量、函数。而 C++中除了上述功能外，还用来定义类的成员变量和函数。即静态成员和静态成员函数。
注意：编程时 static 的记忆性，和全局性的特点可以让在不同时期调用的函数进行通信，传递信息，而 C++的静态成员则可以在多个对象实例间进行通信，传递信息。



指针和引用的区别

引用是被引用对象的一个别名，其只能在定义的时候初始化，并且其值不能改变不能为空

指针可以在任何时候给其赋值，并且其可以为nullptr

sizeof引用为其引用对象的大小，sizeof指针为指针本身的大小

对引用取地址为其引用对象的地址






谈谈对Cpp内存的理解

1、栈区（stack）― 由编译器自动分配释放 ，存放函数的参数值，局部变量的值等。其操作方式类似于数据结构中的栈。

2、堆区（heap）― 一般由程序员分配释放， 若程序员不释放，程序结束时可能由OS回收 。注意它与数据结构中的堆是两回事，分配方式倒是类似于链表。

3、全局区（静态区）（static）― 全局变量和静态变量的存储是放在一块的，初始化的全局变量和静态变量在一块区域， 未初始化的全局变量和未初始化的静态变量在相邻的另一块区域。 - 程序结束后有系统释放

4、文字常量区 ― 常量字符串就是放在这里的。 程序结束后由系统释放

5、程序代码区 ― 存放函数体的二进制代码。






谈谈new、delete、malloc、free

1.malloc与free是C++/C语言的标准库函数，new/delete是C++的运算符。它们都可用于申请动态内存和释放内存。

2.对于非内部数据类型的对象而言，光用maloc/free无法满足动态对象的要求。对象在创建的同时要自动执行构造函数，对象在消亡之前要自动执行析构函数。由于malloc/free是库函数而不是运算符，不在编译器控制权限之内，不能够把执行构造函数和析构函数的任务强加于malloc/free。

3.因此C++语言需要一个能完成动态内存分配和初始化工作的运算符new，以一个能完成清理与释放内存工作的运算符delete。注意new/delete不是库函数







const关键字

1.const 修饰类的成员变量，表示成员常量，不能被修改。

2.const修饰函数承诺在本函数内部不会修改类内的数据成员，不会调用其它非 const 成员函数。

3.如果 const 构成函数重载，const 对象只能调用 const 函数，非 const 对象优先调用非 const 函数。

4.const 函数只能调用 const 函数。非 const 函数可以调用 const 函数。

5.类体外定义的 const 成员函数，在定义和声明处都需要 const 修饰符。。

int const *p / const int *p; //value是常数

int * const p; //常指针

int *const p const; //常指针、value值也是常数






一个文件从源码到可执行文件所经历的过程

1.预处理，产生.ii文件

2.编译，产生汇编文件(.s文件)

3.汇编，产生目标文件(.o或.obj文件)

4.链接,产生可执行文件(.out或.exe文件)


 
 
 
 
 
 进程的状态

运行状态：进程正在处理器上运行，在单处理器环境下，每一时刻最多只有一个进程处于运行状态。

就绪状态：进程已处于准备运行的状态，即进程获得了除处理器之外的一切所需要的资源，一旦得到处理器即可运行。

阻塞状态：又称为等待状态，进程正在等待某一事件而暂停运行。如等待某资源为可用（不包括处理器）或等待输入/输出完成。即使处理器空闲，该进程也不能运行。

创建状态：进程正在被创建，尚未转到就绪状态。

结束状态：进程正从系统中消失。可能是进程正常结束或其它原因中断退出运行。







 
C 存储类

auto 存储所有局部变量默认的存储类

```c
{
  int mount;
  auto int month;
}
```

register 存储类用于定义存储在寄存器中的局部变量，意味着变量的最大尺寸等于寄存器的大小。
```
{
  register int miles;
}
```

static 指编译器在程序的生命周期内保持局部变量的存在，不需要在每次它进入和离开作用域时进行创建和销毁。
也可以应用于全局变量。
```
#include <stdio.h>
void func1(void);
static int count = 10;

int main()
{
 while (count--){
  func1();
}
 return 0;
}

void func1(void)
{
 static int thingy = 5;
 thingy++;
 printf("thingy 为 %d, count 为 %d\n", thingy, count);
}
```

extern




1.引用和指针的区别？

2.从汇编层去解释一下引用

3.C++中的指针参数传递和引用参数传递

4.形参与实参的区别？

5.static的用法和作用？

6.静态变量什么时候初始化

7. const?

8.const成员函数的理解和应用？

9.指针和const的用法

10.mutable

11.extern用法？

12.int转字符串字符串转int?strcat,strcpy,strncpy,memset,memcpy的内部实现？

13.深拷贝与浅拷贝？

14.C++模板是什么，底层怎么实现的？

15.C语言struct和C++struct区别

16.虚函数可以声明为inline吗?

17.类成员初始化方式？构造函数的执行顺序 ？为什么用成员初始化列表会快一些？

18.成员列表初始化？

19.构造函数为什么不能为虚函数？析构函数为什么要虚函数？

20.析构函数的作用，如何起作用？

21.构造函数和析构函数可以调用虚函数吗，为什么

22.构造函数的执行顺序？析构函数的执行顺序？构造函数内部干了啥？拷贝构造干了啥？

23.虚析构函数的作用，父类的析构函数是否要设置为虚函数？

24.构造函数析构函数可以调用虚函数吗？

25.构造函数析构函数可否抛出异常

26.类如何实现只能静态分配和只能动态分配

27.如果想将某个类用作基类，为什么该类必须定义而非声明？

28.什么情况会自动生成默认构造函数？

29.什么是类的继承？

30.什么是组合？

31.抽象基类为什么不能创建对象？

32.类什么时候会析构？

33.为什么友元函数必须在类内部声明？

34.介绍一下C++里面的多态？

35. 用C语言实现C++的继承

36.继承机制中对象之间如何转换？指针和引用之间如何转换？

37.组合与继承优缺点？

38.左值右值

39.移动构造函数

40.C语言的编译链接过程？

41.vector与list的区别与应用？怎么找某vector或者list的倒数第二个元素

42.STL vector的实现，删除其中的元素，迭代器如何变化？为什么是两倍扩容？释放空间？

43.容器内部删除一个元素

44.STL迭代器如何实现

45.set与hash_set的区别

46.hashmap与map的区别

47.map、set是怎么实现的，红黑树是怎么能够同时实现这两种容器？ 为什么使用红黑树？

48.如何在共享内存上使用stl标准库？

49.map插入方式有几种？

50.STL中unordered_map(hash_map)和map的区别，hash_map如何解决冲突以及扩容

51.vector越界访问下标，map越界访问下标？vector删除元素时会不会释放空间？

52.map[]与find的区别？

53.STL中list与queue之间的区别

54.STL中的allocator,deallocator

55.STL中hash_map扩容发生什么？

56.map如何创建？

57.vector的增加删除都是怎么做的？为什么是1.5倍？

58.函数指针？

59.说说你对c和c++的看法，c和c++的区别？

60.c/c++的内存分配，详细说一下栈、堆、静态存储区？

61.堆与栈的区别？

62.野指针是什么？如何检测内存泄漏？

63.悬空指针和野指针有什么区别？

64.内存泄漏

65.new和malloc的区别？

66.delete p;与delete[]p，allocator

67.new和delete的实现原理， delete是如何知道释放内存的大小的额？

68.malloc申请的存储空间能用delete释放吗

69.malloc与free的实现原理？

70.malloc、realloc、calloc的区别

71.__stdcall和__cdecl的区别？

72.使用智能指针管理内存资源，RAII

73.手写实现智能指针类

74.内存对齐？位域？

75.结构体变量比较是否相等

76.位运算

77.为什么内存对齐

78.函数调用过程栈的变化，返回值和参数变量哪个先入栈？

79.怎样判断两个浮点数是否相等？

80.宏定义一个取两个数中较大值的功能

81.define、const、typedef、inline使用方法？

82.printf实现原理？

83.#include 的顺序以及尖叫括号和双引号的区别

84.lambda函数

85. hello world 程序开始到打印到屏幕上的全过程?


86.模板类和模板函数的区别是什么？

87.为什么模板类一般都是放在一个h文件中

88.C++中类成员的访问权限和继承权限问题。

89.cout和printf有什么区别？

90.重载运算符？

91.函数重载函数匹配原则

92.定义和声明的区别

93.C++类型转换有四种

94.全局变量和static变量的区别

95.静态成员与普通成员的区别

96.说一下理解 ifdef endif

97.隐式转换，如何消除隐式转换？

98.虚函数的内存结构，那菱形继承的虚函数内存结构呢

99.多继承的优缺点，作为一个开发者怎么看待多继承

100.迭代器++it,it++哪个好，为什么

101.C++如何处理多个异常的？

102.模板和实现可不可以不写在一个文件里面？为什么？

103.在成员函数中调用delete this会出现什么问题？对象还可以使用吗？

104.智能指针的作用；

105.auto_ptr作用

106.class、union、struct的区别

107.动态联编与静态联编

108.动态编译与静态编译

109.动态链接和静态链接区别

110.在不使用额外空间的情况下，交换两个数？

111.strcpy和memcpy的区别

112.执行int main(int argc, char *argv[])时的内存结构

113.volatile关键字的作用？

114.讲讲大端小端，如何检测（三种方法）

115.查看内存的方法

116.空类会默认添加哪些东西？怎么写？

117.标准库是什么？

119.new、delete、operator new、operator delete、placement new、placement delete

120.为什么拷贝构造函数必须传引用不能传值？

121.空类的大小是多少？为什么？

122.你什么情况用指针当参数，什么时候用引用，为什么？

123.大内存申请时候选用哪种？C++变量存在哪？变量的大小存在哪？符号表存在哪？

124.为什么会有大端小端，htol这一类函数的作用

125.静态函数能定义为虚函数吗？常函数?

126.this指针调用成员变量时，堆栈会发生什么变化？

127.静态绑定和动态绑定的介绍

128.设计一个类计算子类的个数

129.怎么快速定位错误出现的地方

130.虚函数的代价？

131.类对象的大小

132.移动构造函数

133.何时需要合成构造函数

134.何时需要合成复制构造函数

135.何时需要成员初始化列表？过程是什么？

136.程序员定义的析构函数被扩展的过程？

137.构造函数的执行算法？

138.构造函数的扩展过程？

139.哪些函数不能是虚函数

140.sizeof 和strlen 的区别

141.简述strcpy、sprintf与memcpy的区别

142.编码实现某一变量某位清0或置1

143.将“引用”作为函数参数有哪些特点？

144.分别写出BOOL,int,float,指针类型的变量a 与“零”的比较语句。

145.局部变量全局变量的问题？

146.数组和指针的区别？

147.C++如何阻止一个类被实例化？一般在什么时候将构造函数声明为private？

148.如何禁止自动生成拷贝构造函数？

149.assert与NDEBUGE

150.Denug和release的区别

151.main函数有没有返回值

152.写一个比较大小的模板函数

153.c++怎么实现一个函数先于main函数运行

154.虚函数与纯虚函数的区别在于

155.智能指针怎么用？智能指针出现循环引用怎么解决？

156.strcpy函数和strncpy函数的区别？哪个函数更安全？

157.为什么要用static_cast转换而不用c语言中的转换？

158.成员函数里memset(this,0,sizeof(*this))会发生什么

159.方法调用的原理（栈，汇编）

160.MFC消息处理如何封装的？

161.回调函数的作用

162.随机数的生成
