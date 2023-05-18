## 剑指 Offer II 103. 最少的硬币数目

LeetCode：[剑指 Offer II 103. 最少的硬币数目](https://leetcode.cn/problems/gaM7Ch/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    const static int maxn = 1e4 + 5;

    int coinChange(vector<int>& coins, int amount) {
        int dp[maxn];
        memset(dp, 0x3f3f3f, sizeof dp);
        int inf = dp[0];

        dp[0] = 0;
        for(int i = 0; i < coins.size(); i++) {
            for(int j = 0, to; j < maxn; j++) {
                to = j + coins[i];
                if(to >= maxn) {
                    break;
                }
                dp[to] = min(dp[to], dp[j] + 1);
            }
        }
        if(dp[amount] == inf) {
            dp[amount] = -1;
        }
        return dp[amount];
    }
};
```



---



### 题目

给定不同面额的硬币 `coins` 和一个总金额 `amount`。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 `-1`。

你可以认为每种硬币的数量是无限的。

 

**示例 1：**

```
输入：coins = [1, 2, 5], amount = 11
输出：3 
解释：11 = 5 + 5 + 1
```

**示例 2：**

```
输入：coins = [2], amount = 3
输出：-1
```

**示例 3：**

```
输入：coins = [1], amount = 0
输出：0
```

**示例 4：**

```
输入：coins = [1], amount = 1
输出：1
```

**示例 5：**

```
输入：coins = [1], amount = 2
输出：2
```

 

**提示：**

- `1 <= coins.length <= 12`
- `1 <= coins[i] <= 2^31 - 1`
- `0 <= amount <= 10^4`

 

注意：本题与 322 题[322. 零钱兑换](https://leetcode-cn.com/problems/coin-change/)相同


