>### 1 变量的声明和定义有什么区别
>>变量的定义为变量分配地址和存储空间，但变量的声明不分配地址。一个变量可以在多个地方声明，但是只在一个地方定义，加入extern修饰的是变量的声明，说明此变量在文件以外或文件后面部分定义。

```
int main() 
{
 extern int A;   //这是个声明而不是定义，声明A是一个已经定义了的外部变量。声明时可以把变量类型去掉。
 dosth(); //执行函数
}
int A; //是定义，定义了A为整型的外部变量
```
 简述#ifdef、#else、#endif和#ifndef的作用
 
 
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
