---
author: HAOer（银mh）
data: 2026-04-03
tags:
related:
---

> [!important] 基本情况
> 先进先出，**不提供迭代器**，不能遍历


```mermaid
graph LR
    subgraph Pipeline["队列（管道模型）"]
        direction RL
        Entry["队尾（Back）<br>入队端"]-->|入队方向| A["元素A"] --> B["元素B"] --> C["元素C"] --> |出队方向|Exit["队头（Front）<br>出队端"]
    end

    style Entry fill:#ccffcc,stroke:#00aa00,stroke-width:2px
    style Exit fill:#ffcccc,stroke:#cc0000,stroke-width:2px
    style Pipeline fill:#f0f0f0,stroke:#333,stroke-width:1px
```

# 创建

$O(1)$
```cpp
queue<T> q
```


# 插入与删除

- 队尾插入元素，$O(1)$
```cpp
q.push(val); 
```

- 队首删除元素，$O(1)$
```cpp
q.pop();
```

# 获取

- 返回队首元素的引用，$O(1)$
```cpp
q.front();
```

- 返回队尾元素引用，$O(1)$
```cpp
q.back();
```

- 获取元素个数，$O(1)$
```cpp
q.size();
```

# 交换

- 交换内容，$O(1)$
```cpp
swap(q1,q2);
```

# 清空

> [!tip] Title
> 注：`queue` 没有 `clear()` ，需逐个 `pop()` 或交换空队列
