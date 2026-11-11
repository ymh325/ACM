---
tags:
  - ACM
  - ICPC
  - 题单
date: 2026-09-20
---

# ICPC 铜牌专题题单

[返回训练路线](README.md) · [混合盲测](混合盲测.md) · [复盘记录模板](复盘记录模板.md)

共 **72 题 = 12 基础 + 48 主线 + 12 补强**。完成列可填写 `独立 AC / 提示 AC / 题解 AC / 待重做`。下面的知识点会提示方向；要测真实选算法能力，请先做不带标签的盲测。

难度为编排判断：**基础**检查常见技巧；**主线**练习中档建模与算法应用；**补强**增加综合性或实现要求。各区难度会有重叠，不代表官方评级。

## A. 基础诊断（12 题）

目标：能从题意得到简单模型，正确处理边界，避免依赖复杂模板。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| A01 | [CF 1352C · K-th Not Divisible by n](https://codeforces.com/problemset/problem/1352/C) | 整除分组、位置映射 | |
| A02 | [CF 1520D · Same Differences](https://codeforces.com/problemset/problem/1520/D) | 等式变形、频次计数 | |
| A03 | [CF 1374C · Move Brackets](https://codeforces.com/problemset/problem/1374/C) | 括号匹配、扫描不变量 | |
| A04 | [CF 1472D · Even-Odd Game](https://codeforces.com/problemset/problem/1472/D) | 排序、模拟决策 | |
| A05 | [ABC127 D · Integer Cards](https://atcoder.jp/contests/abc127/tasks/abc127_d) | 贪心替换、批量选择 | |
| A06 | [ABC212 C · Min Difference](https://atcoder.jp/contests/abc212/tasks/abc212_c) | 排序、双指针或二分查找 | |
| A07 | [ABC182 D · Wandering](https://atcoder.jp/contests/abc182/tasks/abc182_d) | 前缀和、过程中的最大值 | |
| A08 | [ABC183 D · Water Heater](https://atcoder.jp/contests/abc183/tasks/abc183_d) | 差分、区间端点语义 | |
| A09 | [ABC229 D · Longest X](https://atcoder.jp/contests/abc229/tasks/abc229_d) | 双指针、窗口可行性 | |
| A10 | [ABC183 C · Travel](https://atcoder.jp/contests/abc183/tasks/abc183_c) | 全排列枚举、避免重复计数 | |
| A11 | [ABC167 C · Skill Up](https://atcoder.jp/contests/abc167/tasks/abc167_c) | 子集枚举、可行性判断 | |
| A12 | [ABC218 D · Rectangles](https://atcoder.jp/contests/abc218/tasks/abc218_d) | 平面点集、枚举与查找、计数去重 | |

**验收：** 能估算枚举次数，知道什么时候使用 `long long`，能解释每个计数对象被统计了几次。

## B. 主线：贪心、构造与思维（8 题）

这部分优先级很高。先找性质、写证明，再编码，不要靠样例猜结论。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| B01 | [CF 1367C · Social Distance](https://codeforces.com/problemset/problem/1367/C) | 间隔安排、两端边界 | |
| B02 | [CF 1497B · M-arrays](https://codeforces.com/problemset/problem/1497/B) | 余数分类、配对与构造 | |
| B03 | [CF 1520E · Arranging The Sheep](https://codeforces.com/problemset/problem/1520/E) | 去除位置偏移、中位数 | |
| B04 | [CF 1690E · Price Maximization](https://codeforces.com/problemset/problem/1690/E) | 商与余数拆分、配对贪心 | |
| B05 | [ABC187 D · Choose Me](https://atcoder.jp/contests/abc187/tasks/abc187_d) | 净收益建模、排序依据 | |
| B06 | [ABC195 D · Shipping Center](https://atcoder.jp/contests/abc195/tasks/abc195_d) | 重复询问下的选择贪心 | |
| B07 | [CF 1627C · Not Assigning](https://codeforces.com/problemset/problem/1627/C) | 从约束识别图形结构、构造合法方案 | |
| B08 | [CF 1624D · Palindromes Coloring](https://codeforces.com/problemset/problem/1624/D) | 字符资源分配、奇偶与回文构造 | |

**验收：** 能证明排序或配对策略；构造题同时说明“何时无解”和“方案为什么始终合法”。

## C. 主线：二分、前缀和与计数（8 题）

先辨别单调性、区间含义和计数等式，再选择二分、双指针或维护频次。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| C01 | [CF 1613C · Poisoned Dagger](https://codeforces.com/problemset/problem/1613/C) | 二分答案、贡献重叠、溢出 | |
| C02 | [CF 371C · Hamburgers](https://codeforces.com/problemset/problem/371/C) | 单调判定、成本计算、上界选择 | |
| C03 | [CF 1538C · Number of Pairs](https://codeforces.com/problemset/problem/1538/C) | 数对范围计数、上下界差分 | |
| C04 | [CF 1398C · Good Subarrays](https://codeforces.com/problemset/problem/1398/C) | 前缀和变形、相同状态计数 | |
| C05 | [ABC174 E · Logs](https://atcoder.jp/contests/abc174/tasks/abc174_e) | 二分答案、整除边界 | |
| C06 | [ABC194 E · Mex Min](https://atcoder.jp/contests/abc194/tasks/abc194_e) | 定长窗口、频次与缺失元素 | |
| C07 | [CF 165B · Burning Midnight Oil](https://codeforces.com/problemset/problem/165/B) | 二分判定、逐次整除 | |
| C08 | [ABC146 E · Rem of Sum is Num](https://atcoder.jp/contests/abc146/tasks/abc146_e) | 前缀同余、长度约束、滑动计数 | |

**验收：** `check` 的单调方向能说清；计数题能解释插入和删除状态的顺序，以及为何没有算上空区间。

## D. 主线：动态规划（8 题）

先写出“状态代表什么”，再写转移。DP 专场前几题用于模型校准，后半部分练状态设计与组合建模。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| D01 | [DP C · Vacation](https://atcoder.jp/contests/dp/tasks/dp_c) | 有限状态线性 DP | |
| D02 | [DP D · Knapsack 1](https://atcoder.jp/contests/dp/tasks/dp_d) | 0/1 背包、容量维度、更新顺序 | |
| D03 | [DP E · Knapsack 2](https://atcoder.jp/contests/dp/tasks/dp_e) | 根据数据范围交换状态维度 | |
| D04 | [DP F · LCS](https://atcoder.jp/contests/dp/tasks/dp_f) | 二维 DP、还原方案 | |
| D05 | [CF 1389B · Array Walk](https://codeforces.com/problemset/problem/1389/B) | 操作限制、状态压缩或等价枚举 | |
| D06 | [DP G · Longest Path](https://atcoder.jp/contests/dp/tasks/dp_g) | DAG 上 DP、拓扑序 | |
| D07 | [CF 1633D · Make Them Equal](https://codeforces.com/problemset/problem/1633/D) | 预处理操作代价、转化为背包 | |
| D08 | [DP N · Slimes](https://atcoder.jp/contests/dp/tasks/dp_n) | 区间 DP、合并代价、枚举分割点 | |

**验收：** 能独立给出状态、边界、转移、遍历顺序和复杂度；能区分“方案数”和“最优值”的初始化。

## E. 主线：图论建模（8 题）

建议先掌握 BFS、Dijkstra、并查集/Kruskal、拓扑排序；遇到 0/1 边权时补 0-1 BFS。题目中“状态”不一定只是原图顶点。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| E01 | [ABC168 D · .. (Double Dots)](https://atcoder.jp/contests/abc168/tasks/abc168_d) | BFS、记录父节点、输出构造 | |
| E02 | [ABC223 D · Restricted Permutation](https://atcoder.jp/contests/abc223/tasks/abc223_d) | 拓扑排序、字典序最小方案 | |
| E03 | [ABC218 E · Destruction](https://atcoder.jp/contests/abc218/tasks/abc218_e) | 保持连通、负权边、生成树思想 | |
| E04 | [ABC176 D · Wizard in Maze](https://atcoder.jp/contests/abc176/tasks/abc176_d) | 网格建图、0-1 BFS | |
| E05 | [ABC192 E · Train](https://atcoder.jp/contests/abc192/tasks/abc192_e) | 带发车周期的最短路、等待时间 | |
| E06 | [CF 1611E1 · Escape The Maze (easy version)](https://codeforces.com/problemset/problem/1611/E1) | 多源距离、树上逃生条件 | |
| E07 | [ABC277 E · Crystal Switches](https://atcoder.jp/contests/abc277/tasks/abc277_e) | 状态扩展、切换状态与最短路 | |
| E08 | [ABC191 E · Come Back Quickly](https://atcoder.jp/contests/abc191/tasks/abc191_e) | 有向图最短环、多次最短路、自环 | |

**验收：** 能解释节点、边和权值的实际意义；知道 BFS 和 Dijkstra 的适用条件，不把负边权直接塞给 Dijkstra。

## F. 主线：数据结构与树（8 题）

重点是把需求转成可维护的信息。基础线段树、树状数组、并查集、DFS 序优先，不必先追求可持久化或复杂树链剖分。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| F01 | [CF 580C · Kefa and Park](https://codeforces.com/problemset/problem/580/C) | 树上 DFS、连续状态、叶子判断 | |
| F02 | [ABC185 F · Range Xor Query](https://atcoder.jp/contests/abc185/tasks/abc185_f) | 树状数组或线段树、异或性质 | |
| F03 | [ABC157 E · Simple String Queries](https://atcoder.jp/contests/abc157/tasks/abc157_e) | 单点修改、区间字符集合、位掩码 | |
| F04 | [ABC183 F · Confluence](https://atcoder.jp/contests/abc183/tasks/abc183_f) | 并查集、集合信息、小并大 | |
| F05 | [ABC214 D · Sum of Maximum Weights](https://atcoder.jp/contests/abc214/tasks/abc214_d) | 按边权合并、连通块贡献计数 | |
| F06 | [ABC202 E · Count Descendants](https://atcoder.jp/contests/abc202/tasks/abc202_e) | DFS 序、深度分组、二分统计 | |
| F07 | [ABC239 E · Subtree K-th Max](https://atcoder.jp/contests/abc239/tasks/abc239_e) | 利用小 K、子树信息合并 | |
| F08 | [ABC267 E · Erasing Vertices 2](https://atcoder.jp/contests/abc267/tasks/abc267_e) | 删点过程、堆维护或二分判定 | |

**验收：** 先说明维护量及合并规则，再选数据结构；能利用询问范围简化模型，不机械套高级模板。

## G. 主线：基础数学与字符串（8 题）

数论先练 GCD、质因数分解、快速幂、组合数与逆元；字符串先练前缀函数/KMP、基础哈希或等价 DP。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| G01 | [ABC125 C · GCD on Blackboard](https://atcoder.jp/contests/abc125/tasks/abc125_c) | 前后缀 GCD、删除一个元素 | |
| G02 | [ABC172 D · Sum of Divisors](https://atcoder.jp/contests/abc172/tasks/abc172_d) | 交换枚举顺序、约数贡献 | |
| G03 | [ABC145 D · Knight](https://atcoder.jp/contests/abc145/tasks/abc145_d) | 方程建模、合法性、组合计数 | |
| G04 | [ABC152 E · Flatten](https://atcoder.jp/contests/abc152/tasks/abc152_e) | LCM 的质因数表示、模逆元 | |
| G05 | [CF 1514C · Product 1 Modulo N](https://codeforces.com/problemset/problem/1514/C) | 互质、模乘积、构造与证明 | |
| G06 | [CF 126B · Password](https://codeforces.com/problemset/problem/126/B) | 前后缀匹配、出现位置限制 | |
| G07 | [CF 1200E · Compress Words](https://codeforces.com/problemset/problem/1200/E) | 前后缀重叠、匹配范围与总复杂度；本区较难，可最后做 | |
| G08 | [ABC141 E · Who Says a Pun?](https://atcoder.jp/contests/abc141/tasks/abc141_e) | 最长重复子串、不重叠约束；可用 DP/Z 等 | |

**验收：** 能说明逆元存在条件，避免在取模后直接做普通除法；字符串题能解释重叠与边界，不只背模板。

## H. 进阶补强（12 题，按短板选做）

这些题用于扩大中档题覆盖面，其中部分明显更费思考。主线做不稳时不要强行按顺序啃完，也不要求把下面所有算法都作为拿铜前置条件。

| 编号 | 题目直达链接 | 训练重点 | 完成 |
| --- | --- | --- | --- |
| H01 | [CF 1701C · Schedule Management](https://codeforces.com/problemset/problem/1701/C) | 二分答案、生产能力与剩余任务平衡 | |
| H02 | [CF 1490G · Old Floppy Drive](https://codeforces.com/problemset/problem/1490/G) | 循环序列、前缀最大值、分类与二分 | |
| H03 | [CF 1542C · Strange Function](https://codeforces.com/problemset/problem/1542/C) | 整除计数、LCM 增长、贡献拆分 | |
| H04 | [CF 706D · Vasiliy's Multiset](https://codeforces.com/problemset/problem/706/D) | 01 Trie、插入删除、最大异或 | |
| H05 | [ABC184 F · Programming Contest](https://atcoder.jp/contests/abc184/tasks/abc184_f) | 折半搜索、子集和合并 | |
| H06 | [ABC190 E · Magical Ornament](https://atcoder.jp/contests/abc190/tasks/abc190_e) | BFS 预处理、关键点压缩、状压 DP | |
| H07 | [DP O · Matching](https://atcoder.jp/contests/dp/tasks/dp_o) | 集合状态、匹配方案计数 | |
| H08 | [DP P · Independent Set](https://atcoder.jp/contests/dp/tasks/dp_p) | 树形 DP、状态间组合 | |
| H09 | [DP M · Candies](https://atcoder.jp/contests/dp/tasks/dp_m) | 计数 DP、前缀和优化 | |
| H10 | [ABC235 E · MST + 1](https://atcoder.jp/contests/abc235/tasks/abc235_e) | 离线询问、Kruskal、相同权值的处理 | |
| H11 | [ABC222 F · Expensive Expense](https://atcoder.jp/contests/abc222/tasks/abc222_f) | 换根 DP 或树上距离建模 | |
| H12 | [ABC266 F · Well-defined Path Queries on a Namori](https://atcoder.jp/contests/abc266/tasks/abc266_f) | 基环树、剥叶找环、连通分组 | |

## 暂时不作为主线的内容

网络流、后缀数组/后缀自动机、FFT/NTT、复杂计算几何、可持久化结构、莫比乌斯反演等可以后续补。这不是说区域赛不会出现它们，而是当前更值得先把常见思维题、基础算法应用和队伍配合练稳定。

若后续实战暴露出特定短板，再加对应专题。不要把“笔记里学过”直接当成“限时能独立做出”。
