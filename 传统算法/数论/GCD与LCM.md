## 📕$GCD$  (最大公约数) 

### 求解方法

​	质因数分解法，辗转相除法(欧几里得算法)



#### 😂辗转相除法

​	**方法**：用较大数除以较小数，再将除数作为被除数、余数作为除数，重复此过程，直到余数为 $0$，此时的除数即为最大公约数。

**数学符号表述**：   

对正整数 $a, b\;(a \geq b)$，定义递推关系   $$ \begin{cases}  a = bq_1 + r_1, & 0 \leq r_1 < b, \\  b = r_1 q_2 + r_2, & 0 \leq r_2 < r_1, \\  \vdots & \vdots \\  r_{k-1} = r_k q_{k+1} + r_{k+1}, & 0 \leq r_{k+1} < r_k, \\  \vdots & \vdots \\  r_{n-1} = r_n q_{n+1}, & r_n = 0,  \end{cases} $$   

则 $\gcd(a, b) = r_{n-1}$。  



##### 😎$CODE SHOW$

**时间复杂度均为：$O (\,log (\;min (a, b)\;)\,)$**

- **递归实现**

```C++
int GCD(int a,int b){
    return b==0? a : GCD(b,a%b);
}
```



- **迭代实现**

  ```C++
  int GCD(int a, int b) {
      while (b != 0) {       // 当b非0时持续辗转相除
          int temp = a % b;  // 计算余数
          a = b;             // 替换a为原来的b
          b = temp;          // 替换b为余数
      }
      return a;              // b为0时，a就是GCD
  }
  ```



- **鲁棒版(处理负数)**

  ```c++
  int GCD(int a, int b) {
      a = abs(a);  // 转为非负数
      b = abs(b);
      while (b != 0) {
          int temp = a % b;
          a = b;
          b = temp;
      }
      return a;
  }
  ```



##### *证明：

 **1. 基本定义与符号**

​	设 $a, b \in \mathbb{N}^*且 (a \geq b$)，定义余数 $(r = a \bmod b)$

​	即唯一存在 $(q \in \mathbb{Z})$ 满足：$(a = bq + r, \quad 0 \leq r < b.)$

​	记  $\gcd(a, b)$  为 $(a, b)$ 的最大公约数。

**2. 核心引理：$\gcd (a, b) = \gcd (b, r)$**



​	**证明**：需证 $(\{d \mid a \land d \mid b\} = \{d \mid b \land d \mid r\})$。

​	$(d\,|\,a)$  表示  $a$  能被  $b$  整除



**(1) 若 $(d \mid a) 且 (d \mid b)$，则 $(d \mid b) 且 (d \mid r)$**

​	由 $(d \mid a)$ 和$ (d \mid b)$，存在 $(m, n \in \mathbb{Z})$ 使得：$(a = dm, \quad b = dn.)$ 代入 $(a = bq + r)$ 得：$\;(dm = dnq + r \implies r = d(m - nq) \implies d \mid r.)$ ，故 $(d \in \{d \mid b \land d \mid r\})$。

**(2) 若 $(d \mid b)$ 且 $(d \mid r)$，则 $(d \mid a)$ 且 $(d \mid b)$**

​	由 $(d \mid b)$ 和 $(d \mid r)$，存在 $(p, q \in \mathbb{Z})$ 使得：$(b = dp, \quad r = dq.)$ 代入 $(a = bq + r)$ 得：$(a = dpq + dq = d(pq + q) \implies d \mid a.)$ 故 $(d \in \{d \mid a \land d \mid b\})$。



由 (1)(2)，两集合相等，故：$\gcd(a, b) = \gcd(b, a \bmod b)$



#### 🤣质因数分解法















## 📘$LCM$(最小公倍数)

lcm (最小公倍数)

```C++
int lcm(int a,int b){
    reture a*b/gcd(a,b);
}
```

