# Dijkstra(迪杰斯特拉)算法

> **注意事项**：**不能处理负边权**

是基于**贪心思想**的**单源最短路算法**

------



- **e[u]** 存节点 **u** 的所有出边的终点和边权
- **d[u] **存 **u** 到源点 **s** 的最小距离，**vis[u]** 标记 **u** 是否出圈



1. 初始时，所有点都在圈 (集合) 内 **vis = 0**, **d[s]=0**, **d[其他点]=+无穷**
2. 从圈内选一个距离最小的点 **u** ，打标记出圈
3. 对u的所有出边执行**松弛操作**（即尝试更新邻点 v 的最小距离）
4. 重复2,3步操作，直到圈内为空



# 堆优化后的Dijkstra

> 时间复杂度O(mlogm)，m 为边数

创建一个pair类型的大根堆**q { -距离，点}**，把距离取负值，距离最小的元素最大，一定在堆顶



1.初始化，**{0,s}** 入队，**d[s]=0**,  **d[其它点]=+无穷**

2.从队头弹出距离最小的点山，若山扩展过则跳过否则打标记

3.对 **u** 的所有出边执行**松弛操作**，把{-d[v],v}压入队尾；

4.重复2,3步操直到列为空

```c++
struct edge{int v,w;}; //v表示所指向的点，w表示边权
const int N = 1e5+5;
vector<edge> e[N];
int d[N],vis[N];
priority_queue<pair<int,int>> q;

void Dijkstra(int s){
    for(int i=0;i<=n;i++)d[i] = 1e9;
    d[s]=0;q.push({0,s});
    while(q.size()){
        //离源点最近的点会被优先提出
        auto t=q.top();q.pop();
        //提取节点
        int u=t.second;
        if(vis[u])continue;
        vis[u]=1;
        //循环节点的出边
        for(auto ed:e[u]){
            int v=ed.v,w=ed.w;
            if(d[v]>d[u]+w){
                d[v]=d[u]+w;
                q.push({-d[v],v});
            }
        }
    }
}
```



### 最短路径的记录与递归输出

- **记录**

```c++
if(d[v]>d[u]+w){
    d[v]=d[u]+w;
    per[v]=u;//!!!此处记录一下
    q.push({-d[v],v});
}
```

- **递归输出**

```c++
void dfs_path(int u){
    if(u==s){
        cout<<u<<" ";
        return;
    }
    dfs_path(pre[u]);
    cout<<u<<" ";
}
```



## 一些理解

​	在堆优化的代码中，每一次 节点被取出代表着出圈，那么意义就是：**源点到节点的最短路径已经被确定了，不会再被更改**





# 暴力式的Dijkstra



## 代码 $O(n^2)$

```c++
struct edge{int v,w;};
vector<edge> e[N];
int d[N],vis[N];

void Dijkstra(int s){
    for(int i=1;i<=n;i++)d[i] = INF;
    d[s] = 0;
    for(int i = 1;i < n;i++){ // 一个点最多被松弛 n-1 次
        int u = 0;
        for(int j = 1;j <=n; i++){
            if(!vis[i]&&d[j]<d[u])u = j;
        }
        vis[u] = 1; // 标记 u 已出圈
        for(edge ed:e[u]){
            int v = ed.v,w = ed.w;
            if(d[v]>d[u]+w){
                d[v] = d[u]+w;
            }
        }
    }
}
int main(){
    cin>>n>>m>>s;
    for(int i=1;i<=n;i++){
        cin>>a>>b>>c;
        e[a].push_back({b,c});
    }
    Dijkstra(s);
}
```

