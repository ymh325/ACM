---
author: HAOer
data: 2026-09-01
tags:
related:
---
前置知识：
- [[并查集]]
- 最小生成树 [[kruskal]]
- [[倍增算法]] ，树上倍增和LCA


> [!NOTE] 针对于原始问题
> **无向边**，`n` 个点， `m` 条带权边，`q` 次询问，每次询问：从 `x` 走到 `y` 的所有路径上最大边权的最小值


# Kruskal重构树过程

1. 图中的每个点，都是Kruskal重构树的底层叶节点，初始时认为互不连通 
2. **先考虑边权小的边**，**后考虑边权大的边**，增加连通性的边就选择，不增加连通性的边就舍弃 
3. 一条边一旦被选择，就变成Kruskal重构树的非叶节点，并且作为头节点，连接两个连通的部分
4. 考虑完所有的边，过程停止，原始图中有几个连通区域，就有几棵Kruskal重构树 
5. 每棵Kruskal重构树，都进行树上dfs，建立倍增表等信息


# Kruskal原理

先考虑边权小的边，后考虑边权大的边，所建立的最小生成树，同时也是最小瓶颈树
Kruskal 重构树，节点越往上，代表边权越大，获得的联通性也越大

任何`(x,y)` ，利用 Kruskal 重构树，查询x和y的最低公共祖先，代表x和y连通时，边权的最小瓶颈


模板：[P2245 星际导航 - 洛谷](https://www.luogu.com.cn/problem/P2245)
> [!example] 代码
```cpp
#include <bits/stdc++.h>
using namespace std;
#define OFF ios::sync_with_stdio(0),cin.tie(0);
#define int long long
const int N = 3e5 + 5;

int n,m;
struct node{
    int u,v;
    int val;
    bool operator < (const node & p) const {
        return val<p.val;
    }
};
vector<node> edge;
vector<int> fa(2*N,0); // 乘2是因为要考虑后面加的点
vector<int> w(2*N,0);
vector<int> e[2*N];
int dep[2*N];
int st[2*N][21];
int cnt;

int find(int x){
    return (fa[x]==x? x:fa[x] = find(fa[x]));
}

void bulid(){
    cnt = n;
    sort(edge.begin(),edge.end());
    for(int i=1;i<=2*n;i++){
        fa[i] = i;
    }
    for(int i=0;i<m;i++){
        int fv = find(edge[i].v);
        int fu = find(edge[i].u);
        if(fv!=fu){
            ++cnt;
            fa[fv] = cnt;
            fa[fu] = cnt;
            
            e[cnt].push_back(fv);
            e[cnt].push_back(fu);
            
            w[cnt] = edge[i].val;
        }
    }
}

void dfs(int u,int fat){
    dep[u] = dep[fat] + 1;
    st[u][0] = fat;
    for(int i=1;i<=20;i++){
        st[u][i] = st[st[u][i-1]][i-1];
    }
    for(int son:e[u]){
        if(son==fat)continue;
        dfs(son,u);
    }
}

int lca(int u,int v){
    if(dep[u]<dep[v])swap(u,v);

    for(int i=20;i>=0;i--){
        if(dep[st[u][i]]>=dep[v])u = st[u][i];
    }
    
    if(u==v)return u;
    for(int i=20;i>=0;i--){
        if(st[u][i]!=st[v][i]){
            u = st[u][i],v =st[v][i];
        }
    }
    return st[u][0];
}

signed main(){
    cin>>n>>m;
    for(int i=1;i<=m;i++){
        int a,b,l;
        cin>>a>>b>>l;
        edge.push_back({a,b,l});
    }
    
    bulid();
    for(int i=cnt;i;i--){
        if(fa[i] == i)dfs(i,0);
    }
    
    int q;cin>>q;
    for(int i=1;i<=q;i++){
        int a,b;cin>>a>>b;
        
        if(find(a)!=find(b)){
            cout<<"impossible"<<'\n';
        }
        else {
            int fat = lca(a,b);
            cout<<w[fat]<<'\n';
            // cout<<fat<<'\n';
        }
    }

    return 0;
}
```
