# C++ 语法基础
## 1.1 变量 输入输出 表达式 顺序语句
### 先导
#### 1. 头文件
`#include <cstdio>`
`#include <iostream>`
包含了基础的输入输出函数 `cin cout printf scanf`
#### 2. 命名空间
`using namespace std`
常见的输入输出函数都保存在命名空间 std 中

### 变量
#### 1. 变量类型

```c
/**
    bool false/true 1B
    char 'c', '\n', ' ' 1B
    int  -2147483648 ~ 2147483647 4B
    float 1.23, 2.5, 1.23e12 6~7位有效数字  4B
    double 15~16位有效数字 8B
    
    long long -2^63 ~ 2^63-1 8B
    long double 18~19位有效数字; 12B 16B
*/ 
```


### 输入输出

#### 1. Cin, Cout 

```
cin >> a >> b;
cout << a + b << endl;
```

#### 2. Scanf(), Printf()

```
scanf("%d%d", &a, &b);
printf("a + b = %d", a + b);
```

`cin` 输入过滤空格
`scanf` 输入不会过滤空格

### 表达式



### 顺序语句




