### Kahn(卡恩) 算法

**时间复杂度：O(n+m)，n为顶点数，m为边数**

`e[x]` 存点 `x` 的 邻点，`tp` 存拓扑序列，`din[x]` 存点 `x` 的入度

**算法的核心：**队列维护一个入度为0的节点的集合

1.初始化，队列 `q` 压入所有入度为0的点；

2.每次从q中取出一个点 `x` 放入数组 `tp`;

3.然后将x的所有出边删除。若将边 `(x,y)` 删除后，`y` 的入度变为 `0`，则将 `y`压入 `q` 中；

4.不断重复2,3过程，直到队列 `q` 为空。

5.若 `tp` 中的元素个数等于 `n`,则有拓扑序；否则，有环。



```c++
#include <iostream>
#include <vector>
#include <queue>
using namespace std;
const int N = 1e5+5;
vector<int> e[N],tp;
int din[N];
int n,m;

bool toposort(){
	queue<int> q;
    for(int i;i<=n;i++){
        if(din[i]==0)q.push(i);
    }
    while(q.size()){
        int t=q.front();q.pop();
        tp.push_back(t);//如果需要打印拓扑序列的话，则维护tp 
        for(auto i:e[t]){//提出节点t的每个终点，进行消边
            if(--din[i]==0)q.push(i);//如果节点i的入度为0，则压入q
        }
    }
    return tp.size()==n;
}
int main(){
    cin>>n>>m;
    for(int i=0;i<m;i++){
        int a,b;cin>>a>>b;
        e[a].push_back(b);//建边
        din[b]++;//更新入度的数量
    }
    if(!toposort())cout << -1;
    else for(auto i:tp)cout << i << " ";   
    return 0;
}
```

