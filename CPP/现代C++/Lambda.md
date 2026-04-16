---
author: HAOer
data: 2026-02-12
tags:
  - 现代cpp特性
related:
---
# 基础介绍

> [!NOTE]
> Lambda 表达式是 C++11 引入的匿名函数对象，基本语法由四个核心部分组成：
> 

```text
[捕获变量] (参数列表) -> 返回类型 {
    函数体
};
```

```cpp
[OuterVar](int x,int y) -> int { // -> int 可省略
	return OuterVar + x + y;
};
```

例如：
```cpp
auto f = [](int a,int b) -> int{
	return a+b;
};
cout << f(1,2) << endl;
```


# 捕获列表



> [!NOTE] 
> 以值捕获不能修改值，引用捕获则可以


- 用于指定 Lambda 表达式**体内部可以访问的外部局部变量**。
    
- 捕获方式：
    
    - `[=]`：**以值**捕获所有外部变量
        
    - `[&]`：**以引用**捕获所有外部变量
	    
	- `[&, =N]` ：可以**指定**部分外部变量**以值**，**其他**变量按以**引用** 
		
	- `[=, &N]` ：同理
        
    - `[a, &b]`：混合捕获，a 按值，b 按引用
        
- 示例中的 `[OuterVar]` 表示以值方式捕获名为 `OuterVar` 的外部变量。

## C++14及以上
 
### 1、可在捕获框定义新变量

```cpp
void foo() { 
	int N = 100, M = 10; 
	auto g = [N, &M, K=5](int i) { 
		M = 20;
		cout << K << endl;
		return N * i;
	}; 
	cout << g(10) << endl;
	cout << M << endl;
}
```

### 2、参数列表支持 `auto`

```cpp
[](auto a, auto b){return a + b};
```




# 返回类型 `-> type`

- **尾置返回类型（trailing return type）**，C++11 引入。
    
- 用于显式指定 Lambda 返回的类型。
    
- 如果函数体仅包含一条 `return` 语句，编译器可自动推导返回类型，此时可省略。
    
- 示例：`-> int` 明确返回 `int` 类型。