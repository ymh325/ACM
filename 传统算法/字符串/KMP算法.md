### KMP算法

问题：给定一个模式窜 P 和 一个主串 S，求模式串 P 在 主串 S 中出现的位置。

字符串的下标从 0 开始

此算法不细谈，详细思想请看

[KMP算法]: https://www.bilibili.com/video/BV1AY4y157yL/?share_source=copy_web&amp;vd_source=1854db80aed1ed72ec492affb3b8acd4



```c++
#include <bits/stdc++.h>
using namespace std;
// #define ll long long
const int N = 1e6 + 5;
int nex[N];
string P,S;
// S为主串，P为模式串
void create(){
    // O(n) n为模式串长度
    for(int i = 2,j = 0; i < P.size(); i++){
        while(j && P[i]!=P[j+1]) j = nex[j];
        if(P[i] == P[j+1])j++;
        nex[i] = j ;
    }
}
int main(){
   	cin>>S>>P;
    S='-'+S;P = '-'+P;
    create();
    // O(m) m为主串长度
    for(int i = 1,j = 0;i<S.size();i++){
        while(j && S[i]!=P[j+1])j = nex[j];
        if(S[i] == P[j+1])j++;
        if(j == P.size()-1)printf("%d",i-P.size()+2);
    }
    
    // 可以输出nex数组
    for(int i=0;i<s2.size();i++){
        cout<<nex[i]<<" ";
    }
    return 0;
}
```

[[AC自动机]]