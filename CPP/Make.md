---
author: HAOer（银mh）
data: 2026-02-12
tags:
  - 构建工具
related:
---


> [!important] 
> 前置知识：[[CPP/编译|编译]]

# 简介

> [!NOTE] 
> Makefile，一个为 `C/C++` 设计的自动化构建脚本，实际上是一个通用的构建工具，可以用来构建任何类型的项目，但主要还是用在 `C/C++`的项目中。

# 基础规则

Makefile 定义了一系列的规则来指定哪些文件需要先编译，哪些文件需要后编译，哪些文件需要重新编译，甚至于进行更复杂的功能操作。

# 生成目标

规则的基本格式如下：
```text
目标文件: 依赖文件
	要执行的命令
	......
```

- 目标文件：就是我们要生成的文件
	
- 依赖文件：就是生成这个文件所需要的文件
	
- 命令：就是生成这个文件的具体步骤（**注意：命令前必须有一个 Tab 键，不能是空格**）


以一个简单的例子：

```makefile
hello: main.c message.c
	gcc main.c message.c -o hello
```

意思是：如果要生成 `hello` 这个可执行文件的话，会先找到 `main.c` 和 `message.c` ，而后再执行下面的命令，从而生成可执行文件 `hello`；


# 执行规则

默认情况下，如果在命令行中只输入 `make`，`Makefile` **只会执行第一个规则**（也就是默认目标）；

```bash
make 
```

如果想要执行特定的规则，可以在 `make` 后面加上特定的目标名：

```bash
make hello
```

# 变量配置

为了使 Makefile 更加灵活和易于维护，常常会定义和使用变量来替代重复的编译器名称或编译选项：

```makefile
CC = gcc
CFLAGS = -Wall -g
TARGET = hello

$(TARGET): main.c message.c
	$(CC) $(CFLAGS) main.c message.c -o $(TARGET)
```

# 伪目标

伪目标不代表真正的文件名，在执行 make 时可以指定这个目标来执行其所在规则定义的命令。最常见的伪目标是用于清理编译产物的 `clean` 项目。使用 `.PHONY` 声明。

```makefile
.PHONY: clean

clean:
	rm -f *.o hello
```

# 自动化变量

Makefile 提供了一些内置的快速变量来化简命令编写，常用的自动化变量有：

- `$@`：表示规则中的目标文件集。
- `$<`：表示依赖目标中的第一个目标名字。
- `$^`：表示所有的依赖目标集合，以空格分隔。

利用自动化变量，规则可以进一步简写为：

```makefile
hello: main.c message.c
	gcc $^ -o $@
```


