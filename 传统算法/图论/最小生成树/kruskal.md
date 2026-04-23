# Kruskal

> 克鲁斯卡尔

利用 **并查集** 求最小生成树（MST）



- 最小生成树：在一个带边权的无向连通图中，找到一颗 **连接所有顶点**，并且**所有边的权值之和最小**的子树



# Strat

- `e[i]` 存第 `i` 条边的起点，终点与边权。
- `fa[x]` 存 `x` 点的父节点。



1. 初始化并查集，把 `n` 个点放在 `n` 个独立的集合。

2. 将所有的边按边权从小到大排序（贪心思想）。

3. 按顺序枚举每一条边。

   如果这条边连接的两个点不在同一集合，就把这条边加入最小生成树，并且合并这两个集合；

   如果这条边连接的两个点在同一集合，就跳过。

4. 重复执行3，直到选取了 `n-1` 条边为止。



**注意：能求到最小生成树的前提是整个图是连通的**



### 代码 $(mlogm)$

```c++
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;
#define OFF ios::sync_with_stdio(false),cin.tie(0), cout.tie(0);
#define int long long
const int N = 2e5 + 5;
int n,m,cnt,ans,fa[N];
struct edge{
    int u,v,w;
    bool operator < (const edge& p)const{
        return w < p.w;
    } 
};
edge e[N];
int find(int x){
    if(fa[x] == x) return x;
    return fa[x] = find(fa[x]);
}
bool krs(){
    sort(e + 1,e + m + 1 ); // O(mlogm)
    for(int i=1;i<=n;i++)fa[i] = i;
    for(int i=1;i<=m;i++){
        int u = find(e[i].u);
        int v = find(e[i].v);
        if(u!=v){
            fa[u] = v;
            ans+=e[i].w;
            cnt++;
        }
    }
    return cnt == n - 1; // 如果图不连通，则返回 0 
}
signed main(){
    OFF
    cin>>n>>m;
    for(int i=1;i<=m;i++){
        int x,y,z;cin>>x>>y>>z;
        e[i] = {x,y,z};// 按道理来说建一条边即可
    }
    if(krs()){
        cout<<ans;
    }
    else cout<<"orz";
    return 0;
}
```



## 另外的

​	我们可以利用这个算法，真正的生成 一颗树 或是 森林 出来

​	为什么？ 因为此算法能保证 所有极大连通分量 具有 **边数 = 节点数 - 1**。



我们对于这个代码片段进行修改即可

```c++
if(u!=v){
	fa[u] = v;
	ans+=e[i].w;
	cnt++;
}
```



```C++
if(u!=v){
	fa[u] = v;
	ans+=e[i].w;
    G[e[i].v].push_back({e[i].u, e[i].w});
    G[e[i].u].push_back({e[i].v, e[i].w});
	cnt++;
}
```

