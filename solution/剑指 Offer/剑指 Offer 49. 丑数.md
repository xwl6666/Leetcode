## 剑指 Offer 49. 丑数

LeetCode：[剑指 Offer 49. 丑数](https://leetcode.cn/problems/chou-shu-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    #define ll long long

    int nthUglyNumber(int n) {
        set<ll> st;
        st.insert(1);

        ll res = 0;
        for(ll i = 0, x, y, z; i < n; i++) {
            res = *st.begin();
            st.erase(st.begin());

            x = res * 2, y = res * 3, z = res * 5;
            st.insert(x);
            st.insert(y);
            st.insert(z);
        }

        return res;
    }
};
```



---



### 题目

我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

 

**示例:**

```
输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
```

**说明:** 

1. `1` 是丑数。
2. `n` **不超过**1690。

注意：本题与 264 题[264. 丑数 II](https://leetcode-cn.com/problems/ugly-number-ii/)相同


