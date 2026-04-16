---
author: HAOer（银mh）
data: 2026-04-03
tags:
related:
---

> [!important] KNOWLEGDE
> 头文件：`#include <queue>`
> 大根堆（默认）或者小根堆，元素按优先级顺序访问> 


# 创建

## 大根堆

> 大根堆依赖 `<` 规则排序，较大的元素上浮

```cpp
priority_queue<T> maxHeap;
```

## 小根堆

> 小根堆依赖 `>` 规则排序，较小的元素上浮

- 标准定义
```cpp
priority_queue<T , vector<T> , greater<T>> minHeap;
```

# 插入与删除

- 插入元素，$O(\log{n})$ 
```cpp
pq.push(val);
```

- 删除堆顶，$O(\log{n})$
```cpp
pq.pop();
```

# 获取

## 堆顶元素

```cpp
pq.top();
```

## 元素个数

```cpp
pq.size()
```

## 是否为空

```cpp
pq.empty();
```

# 交换内容

```cpp
swap(pq.1,pq.2)
```


# 使用细节 ※

如果我们需要每次获取最小的元素，那么可以直接创建 **小根堆** ，但是可能写起来比较麻烦。**对于一些情况** ， 我们可以**直接创建大根堆来获取 ”最小值“**

## 1、有符号数

比如，`int` ，`long long` 之类的，我们完全可以把相反数放在大根堆里；
例如，要放 $3$，$2$，$1$，$5$ ，可以将 $-3$, $-2$，$-1$，$-5$ 放在 **大根堆** 中，这样原来较小的数会因为取了相反数的缘故而上浮。

```cpp
#include <iostream>
using namespace std;
int main(){
	int s = 1;
	
}
```