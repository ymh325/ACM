

[E - Digit Circus](https://atcoder.jp/contests/abc465/tasks/abc465_e)

数位DP

```cpp
#include <bits/stdc++.h>
using namespace std;
#define OFF ios::sync_with_stdio(0),cin.tie(0);
#define int long long
// const int N = 1e5 + 5;
void so(){
    // int n;cin>>n;
    string s ;cin>>s;
    int dp[1<<10][3][2];
    int ndp[1<<10][3][2];

    memset(dp, 0, sizeof(dp));

    dp[0][0][0] = 1;

    int len = s.size();

    for(int i = 0; i < len;i ++){
        memset(ndp, 0, sizeof(ndp));
        for(int mask = 0;mask< (1<<10);mask++){
            for(int mod= 0;mod<3;mod++){
                for(int less = 0;less<2;less++){
                    if(dp[mask][mod][less] == 0){
                        continue;
                    }
                    int mx = less == 0? s[i]-'0' : 9;

                    for(int d=0;d<=mx;d++){
                        int nmask,nmod,nless;
                        if(mask == 0 && d==0){
                            nmask = 0;
                        }
                        else {
                            nmask = mask | (1<<d);
                        }
                        nmod = (mod*10 + d)%3;
                        nless = less || (d<(s[i]-'0'));
                        ndp[nmask][nmod][nless] = (ndp[nmask][nmod][nless] + dp[mask][mod][less] )%(998244353);
                    }
                }
            }
        }
        memcpy(dp, ndp, sizeof(dp));

    }
    int ans=0;
    for(int mask = 1;mask < (1<<10);mask++){
        for(int mod= 0;mod<3;mod++){
            for(int less = 0;less<2;less++){
                int num = dp[mask][mod][less];
                int cnt = 0 ;
                if(__builtin_popcount(mask) == 3)cnt++;
                if(mod == 0)cnt++;
                if(mask & (1<<3))cnt++;
                if(cnt==1){
                    ans  = (ans + num)%(998244353);
                }
            }
        }
    }
    cout<<ans;

}

signed main(){
    int _;
    _ = 1;
    // cin>>_;
    while(_--){
        so();
    }

    return 0;
}

```