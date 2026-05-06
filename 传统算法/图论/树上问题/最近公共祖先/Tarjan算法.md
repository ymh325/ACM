# Tarjan

> 塔扬算法

是一种 **离线算法** ，巧妙利用 **并查集** 维护祖先节点。

**离线算法：**需要预先知道所有数据



- `e[u]` 存树边，`e[1] = 5` ，`e[5] = 1` 。
- `query[u]` 存查询，例如 `query[3] = {4,1}` ，`query[4] = {3,1}`。  
- `fa[u]` 存父节点，`fa[5] = 1` ，`fa[2] = 5`。
- `vis[u]` 打标记，`vis[5] = true`。
- `ans[i]` 存查询结果，`ans[1] = 1`，`ans[2] = 5`。



1. 从根开始深搜遍历，入 `u` 时打标记。

2. 枚举 `u` 的儿子  `v` ,遍历完 `v` 的子树，回 `u` 时把 `v` 指向 `u` 。

3. 遍历完 `u` 的儿子们，离 `u` 时枚举以 `u` 为起点的查询，若终点 `v` 被搜过

   则查找 `v` 的根，即 `u,v` 的 `LCA`,答案记入 `ans`。

4. 递归遍历完整颗树，得到全部查询答案。



```c++
#include <iostream>
#include <vector>
#define OFF ios::sync_with_stdio(false),cin.tie(0),cout.tie(0);
using namespace std;
const int N = 5e5 + 5;
vector<int> e[N];
vector<pair<int ,int>> que[N];//* 查询
int ans[N];
int fa[N],vis[N],n,m,s;
int find(int x){
    if(x == fa[x])return x;
    return fa[x] = find(fa[x]);
}
void Tarjan(int u){
    vis[u] = 1;
    for(int v:e[u]){
        if(vis[v])continue;
        Tarjan(v);
        fa[v] = u;
    }
    for(auto t : que[u]){
        int v = t.first, i = t.second;
        if(vis[v])ans[i] = find(v);
    }
}
int main(){
    OFF;
    cin>>n>>m>>s;
    for(int i=1;i<=n;i++)fa[i]=i;
    for(int i=1;i<n;i++){
        int u,v;cin>>u>>v;
        e[u].emplace_back(v);
        e[v].emplace_back(u);
    }
    for(int i=1;i<=m;i++){
        int u,v;cin>>u>>v;
        que[u].emplace_back(v,i);
        que[v].emplace_back(u,i);
    }
    Tarjan(s);
    for(int i=1;i<=m;i++){
        cout<<ans[i]<<"\n";
    }
    return 0;
}
```

