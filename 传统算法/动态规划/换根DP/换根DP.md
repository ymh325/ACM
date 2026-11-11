---
author: HAOer
data: 2026-09-29
tags:
related:
---
前置知识：
- 无


> [!NOTE] 换根DP
> 树上的某些问题，需要知道以不同的节点做根的情况下，答案是多少


思考重点：
- 如果已经得到父节点做根的答案，怎么加工得到子节点做根的答案
- 为了达到换根这个目标，可能需要设置若干额外的信息来帮助计算


换根dp的过程：
1. 先以节点1为头进行树的遍历，收集信息，dfs1过程
2. 得到 `1` 节点做根的答案，然后从 `1` 节点开始再进行树的遍历，求解每个节点做根的答案，dfs2过程核心在于换根时，答案如何转移




# 例题


[Problem - 1187E - Codeforces](https://codeforces.com/problemset/problem/1187/E)

[Problem - 219D - Codeforces](https://codeforces.com/problemset/problem/219/D)

[P3047 [USACO12FEB] Nearby Cows G - 洛谷](https://www.luogu.com.cn/problem/P3047)

https://www.luogu.com.cn/problem/CF708C

https://www.luogu.com.cn/problem/P6419
