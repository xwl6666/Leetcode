## 剑指 Offer II 098. 路径的数目

LeetCode：[剑指 Offer II 098. 路径的数目](https://leetcode.cn/problems/2AoeFn/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int uniquePaths(int n, int m) {
        vector< vector<int> > dp(n, vector<int>(m ,0));

        dp[0][0] = 1;
        for(int i = 1; i < m; i++) {
            dp[0][i] = dp[0][i - 1];
        }
        for(int j = 1; j < n; j++) {
            dp[j][0] = dp[j - 1][0];
        }
        for(int i = 1; i < n; i++) {
            for(int j = 1; j < m; j++) {
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
        return dp[n - 1][m - 1];
    }
};
```



---



### 题目

一个机器人位于一个 `m x n` 网格的左上角 （起始点在下图中标记为 “Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。

问总共有多少条不同的路径？

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII098-robot_maze.png)

```
输入：m = 3, n = 7
输出：28
```

**示例 2：**

```
输入：m = 3, n = 2
输出：3
解释：
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右
3. 向下 -> 向右 -> 向下
```

**示例 3：**

```
输入：m = 7, n = 3
输出：28
```

**示例 4：**

```
输入：m = 3, n = 3
输出：6
```

 

**提示：**

- `1 <= m, n <= 100`
- 题目数据保证答案小于等于 `2 * 10^9`

 

注意：本题与 62 题[62. 不同路径](https://leetcode-cn.com/problems/unique-paths/)相同


