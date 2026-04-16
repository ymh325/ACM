# Bell-Ford1

> **能够处理负边权的情况，但无法处理存在负权回路的情况**

**单源最短路径算法，时间复杂度：$O(NE)$**，`N` 是顶点数，`E` 是边数

****

## 核心思想：

​	以**边为主体**，而 `Dijkstra` 是以点为主体



## 操作：

​	`e[u]` 存 `u` 点的出边的邻点和边权，`d[u]` 存 `u` 点到源点的距离。

1. 初始化，`d[s] = 0` ，`d[其他点] = +∞`  ；
2. 执行多轮循环。每轮循环，对 **所有边** 都尝试进行一次松弛操作；
3. 当每一轮中没有成功的松弛操作时，算法停止。



## 代码展示

```c++
#include <iostream>
#include <vector>
#include <cstring>
#define OFF ios::sync_with_stdio(false); cin.tie(0); cout.tie(0);
using namespace std;
const int N = 2e3 + 5;
struct edge{int v,w;};
vector<edge> e[N];
int d[N];
int n,m,inf;
int ford(int s){
    memset(d,0x3f,sizeof(d));
    inf = d[0];
    d[s]=0;
    int flg = 0;
    for(int i=1;i<=n;i++){
        flg = 0;
        for(int u=1;u<=n;u++){
            if(d[u]==inf)continue;
            for(edge ed:e[u]){
                int v = ed.v , w =ed.w;
                if(d[v]>d[u]+w){
                    d[v] = d[u]+w;
                    flg=1;
                }
            }
        }
        if(!flg)break;//* 没有任何松弛操作,跳出
    }
    return flg;//* flg = 1 则有负环
}
int main(){
    return 0;
}
```





# SPFA

**SPFA是Bell-Ford算法的一种队列实现，减少了不必要的冗余计算**

**时间复杂度：O(KE)**，E是边数，K是常数，平均值为2



**只有本轮被更新的点，其出边才有可能起下一轮的松弛操作**，因此用队列来维护被更新的点的集合

`vis[u]` 标记 `u` 点是否在队内，`cnt[u]`记录边数，判负环。

1. 初始化，`s` 入队，标记 `s` 在队内，`d[s]=0`，`d[其它点]=+∞`

2. 从队头弹出 `u` 点，标记 `u` 不在队内；

3. 枚举 `u` 的所有出边，执行松弛操作。记录从 `s` 走到 `v` 的边数并判负环。

   如果 `v` 不在队内则把 `v` 压入队尾，并打上标记；

4. 重复2,3步操作，直到队列为空。



## 代码展示

```C++
#include <iostream>
#include <vector>
#include <cstring>
#include <queue>
#define OFF ios::sync_with_stdio(false); cin.tie(0); cout.tie(0);
using namespace std;
const int N = 2e3 + 5;
struct edge{int v,w;};
vector<edge> e[N];
queue<int> q;
int d[N],cnt[N],vis[N];
int n,m,inf;
int spfa(int s){
    memset(d,0x3f,sizeof(d));
    d[s]=0;q.push(s);vis[s]=1;
    while(q.size()){
        int u = q.front();q.pop();
        vis[u] = 0; //* 标记不在队列中
        for(edge ed:e[u]){
            int v = ed.v ,w = ed.w;
            if(d[v]>d[u]+w){
                d[v] = d[u]+w;
                cnt[v] = cnt[u] + 1;
                if(cnt[v]>=n)return 1;//* 有负环
                if(!vis[v])q.push(v),vis[v]=1;
            }
        }
    }
    return 0;//* 无负环
}
int main(){
    return 0;
}
```



## 提醒：

​	以上只是判断以图中某一结点为起点，能否走到负环

若要判断整个图是否有负环，那么需要添加一个超级源点 `P` ，让 `P` 能连接到所有的节点，并且 边权为 0

一般，我们都会添加一个 0 节点为超级源点，具体可以根据题目来
