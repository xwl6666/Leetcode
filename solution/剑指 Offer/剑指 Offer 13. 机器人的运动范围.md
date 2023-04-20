## 剑指 Offer 13. 机器人的运动范围

LeetCode：[剑指 Offer 13. 机器人的运动范围](https://leetcode.cn/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    bool bk[102][102];
    int res;
    int n, m, k;
    int nextt[4][2] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};

    bool judge(int x, int y) {
        int sum = 0;
        while(x) {
            sum += x % 10, x /= 10;
        }
        while(y) {
            sum += y % 10, y /= 10;
        }
        return sum <= k;
    }

    void dfs(int x, int y) {
        for(int i = 0, tx, ty; i < 4; i++) {
            tx = x + nextt[i][0];
            ty = y + nextt[i][1];
            if(tx < 0 || tx >= m || ty < 0 || ty >= n || bk[tx][ty]) {
                continue;
            }
            bk[tx][ty] = true;
            if(judge(tx, ty)) {
                res ++;
                dfs(tx, ty);
            }
        }
    }

    int movingCount(int m, int n, int k) {
        this -> m = m, this -> n = n, this -> k = k;
        bk[0][0] = true;
        res = 1;

        dfs(0, 0);

        return res;
    }
};
```



---



### 题目

地上有一个m行n列的方格，从坐标 `[0,0]` 到坐标 `[m-1,n-1]` 。一个机器人从坐标 `[0, 0] `的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

 

**示例 1：**

```
输入：m = 2, n = 3, k = 1
输出：3
```

**示例 2：**

```
输入：m = 3, n = 1, k = 0
输出：1
```

**提示：**

- `1 <= n,m <= 100`
- `0 <= k <= 20`


