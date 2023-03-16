## 剑指 Offer 10- II. 青蛙跳台阶问题

LeetCode：[剑指 Offer 10- II. 青蛙跳台阶问题](https://leetcode.cn/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:

    const int mod = 1e9 + 7;
    
    int numWays(int n) {
        if(n <= 1) {
            return 1;
        }
        vector<int> f(n + 1, 0);
        f[0] = 1, f[1] = 1;
        for(int i = 2; i <= n; i++) {
            f[i] = (f[i - 1] + f[i - 2]) % mod;
        }
        return f[n];
    }
    
};
```



---



### 题目

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 `n` 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

**示例 1：**

```
输入：n = 2
输出：2
```

**示例 2：**

```
输入：n = 7
输出：21
```

**示例 3：**

```
输入：n = 0
输出：1
```

**提示：**

- `0 <= n <= 100`

注意：本题与 70 题[70. 爬楼梯](https://leetcode.cn/problems/climbing-stairs/)相同


