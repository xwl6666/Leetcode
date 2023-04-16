## 剑指 Offer 60. n个骰子的点数

LeetCode：[剑指 Offer 60. n个骰子的点数](https://leetcode.cn/problems/nge-tou-zi-de-dian-shu-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<double> dicesProbability(int n) {
        vector< vector< double > > dp(n + 1, vector<double>(75));

        dp[1][1] = 1.0 / 6; // 1 / 6
        for(int i = 2; i <= 6; i++) {
            dp[1][i] = dp[1][i - 1];
        }

        for(int i = 2; i <= n; i++) {
            // 第 i - 1 轮丢出骰子的点数
            for(int j = (i - 1); j <= (i - 1) * 6; j++) {
                for(int k = 1; k <= 6; k++) {
                    dp[i][j + k] += dp[i - 1][j] / 6.0;
                }
            }
        }

        vector<double> res;
        for(int i = n; i <= n * 6; i++) {
            res.push_back(dp[n][i]);
        }
        return res;
    }
};
```



---



### 题目

把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。

 

你需要用一个浮点数数组返回答案，其中第 i 个元素代表这 n 个骰子所能掷出的点数集合中第 i 小的那个的概率。

 

**示例 1:**

```
输入: 1
输出: [0.16667,0.16667,0.16667,0.16667,0.16667,0.16667]
```

**示例 2:**

```
输入: 2
输出: [0.02778,0.05556,0.08333,0.11111,0.13889,0.16667,0.13889,0.11111,0.08333,0.05556,0.02778]
```

 

**限制：**

```
1 <= n <= 11
```


