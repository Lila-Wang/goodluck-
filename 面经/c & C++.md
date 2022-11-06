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
