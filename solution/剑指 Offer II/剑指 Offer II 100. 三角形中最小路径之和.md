## 剑指 Offer II 100. 三角形中最小路径之和

LeetCode：[剑指 Offer II 100. 三角形中最小路径之和](https://leetcode.cn/problems/IlPe0q/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        int n = (int)triangle.size();
        if(n == 1) {
            return triangle[0][0];
        }
        vector< vector<int> > dp(n, vector<int>(201, 1e9));

        int mi = INT_MAX;
        for(int i = 0, m; i < n; i++) {
            m = (int)triangle[i].size();
            for(int j = 0; j < m; j++) {
                if(i == 0) {
                    dp[i][j] = triangle[i][j];
                    continue;
                }
                if(j == 0) {
                    dp[i][j] = dp[i - 1][j] + triangle[i][j];
                } else if(j == m - 1) {
                    dp[i][j] = dp[i - 1][j - 1] + triangle[i][j];
                } else {
                    dp[i][j] = min(dp[i - 1][j - 1], dp[i - 1][j]) + triangle[i][j];
                }

                if(i == n - 1) {
                    mi = min(mi, dp[i][j]);
                }
            }
        }
        return mi;
    }
};
```



---



### 题目

给定一个三角形 `triangle` ，找出自顶向下的最小路径和。

每一步只能移动到下一行中相邻的结点上。**相邻的结点** 在这里指的是 **下标** 与 **上一层结点下标** 相同或者等于 **上一层结点下标 + 1** 的两个结点。也就是说，如果正位于当前行的下标 `i` ，那么下一步可以移动到下一行的下标 `i` 或 `i + 1` 。

 

**示例 1：**

```
输入：triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]
输出：11
解释：如下面简图所示：
   2
  3 4
 6 5 7
4 1 8 3
自顶向下的最小路径和为 11（即，2 + 3 + 5 + 1 = 11）。
```

**示例 2：**

```
输入：triangle = [[-10]]
输出：-10
```

 

**提示：**

- `1 <= triangle.length <= 200`
- `triangle[0].length == 1`
- `triangle[i].length == triangle[i - 1].length + 1`
- `-10^4 <= triangle[i][j] <= 10^4`

 

**进阶：**

- 你可以只使用 `O(n)` 的额外空间（`n` 为三角形的总行数）来解决这个问题吗？

 

注意：本题与 120 题[120. 三角形最小路径和](https://leetcode-cn.com/problems/triangle/)相同


