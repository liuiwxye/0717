vconst 关键字

默认情况下， const变量仅在当前文件范围内有效

test1: (编译运行一下， 程序ok)
```C++
//main.cpp
#include <iostream>  
using namespace std;  
  
extern int n;  
  
int main()  
{  
    cout << n << endl;  
  
    return 0;  
}  

------------------------------------------------

//test.cpp
int n = 100;
``` 

test2:( 程序编译错误， 为什么呢？ <font color=ff00ff>因为const形式的n只在test.cpp中有效</font>， 那怎么解决这个问题呢？ 我们继续看。)
```C++
//main.cpp
#include <iostream>  
using namespace std;  
  
extern const int n;  
  
int main()  
{  
    cout << n << endl;  
  
    return 0;  
}  

------------------------------------------------

//test.cpp
const int n = 100;
``` 

test3: (程序编译运行ok.  <font color=ff0000>外部要能访问test.cpp中的const形式的n, 必须在test.cpp中定义的时候用extern限定</font>)
```C++
//main.cpp
#include <iostream>  
using namespace std;  
  
extern const int n;  
  
int main()  
{  
    cout << n << endl;  
  
    return 0;  
}

------------------------------------------------

//test.cpp
extern const int n = 100;
``` 

<font color=ffff00>const对象被设定为仅在文件内有效。当多个文件中出现了同名的const变量时，其实等同于在不同文件中分别定义了独立的变量</font>

```C++
//a.h
#program once
void print()
------------------------------------------------
//a.cpp
#include "a.h"
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

extern const int aNum = 20;
void print()
{
	cout << "print" << endl;
	cout << aNum << endl;
}
------------------------------------------------
//main.cpp
#include "a.h"
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

const int aNum = 66;

int main()
{
    cout<<aNum<<endl;
    print();
    return 0;
}

```

<font color=00fff0>注意：常量定义式通常放在头文件内</font>

test4:
```C++
//a.h
#program once
const int aNum=66;
void print();

------------------------------------------------

//a.cpp
#include "a.h"
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

extern const int aNum=66;
void print()
{
	cout << "print" << endl;
	cout << aNum << endl;
}

------------------------------------------------

//main.cpp
#include "a.h" 
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

int main()
{
    cout << aNum << endl;
    print();
    return 0;
}

```

<font color=00ff00>为什么这里，在`a.cpp`和`main.cpp`都引用了`a.h`,却没有报错重定义呢，原因在于`const`变量默认只在文件内有效，在`a.cpp`中，引用的`a.h`中的`aNum`与在`main.cpp`中引用的`aNum`，类似于当多个文件中出现了同名的const变量时，其实等同于在不同文件中分别定义了独立的变量，所以不会重定义</font>  

<font color=ffff00>如果在`a.h`中把`const int aNum=66`修改为`extern const int aNum66`，就有有重定义的错误。
