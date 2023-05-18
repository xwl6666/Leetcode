## 剑指 Offer II 105. 岛屿的最大面积

LeetCode：[剑指 Offer II 105. 岛屿的最大面积](https://leetcode.cn/problems/ZL6zAn/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    int nextt[4][2] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
    int n, m;

    int mx, cnt;

    void dfs(int sx, int sy, vector<vector<int>>& grid) {
        if(grid[sx][sy] == 1) {
            cnt ++;
            grid[sx][sy] = 0;

            for(int i = 0, x, y; i < 4; i++) {
                x = sx + nextt[i][0], y = sy + nextt[i][1];
                if(x < 0 || x >= n || y < 0 || y >= m) {
                    continue;
                }
                dfs(x, y, grid);
            }
        }
        return ;
    }


    int maxAreaOfIsland(vector<vector<int>>& grid) {
        n = (int)grid.size(), m = (int)grid[0].size();

        mx = 0;
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < m; j++) {
                if(grid[i][j] == 0) {
                    continue;
                }
                cnt = 0;
                dfs(i, j, grid);
                if(cnt > mx) {
                    mx = cnt;
                }
            }
        }
        return mx;
    }
};
```



---



### 题目

给定一个由 `0` 和 `1` 组成的非空二维数组 `grid` ，用来表示海洋岛屿地图。

一个 **岛屿** 是由一些相邻的 `1` (代表土地) 构成的组合，这里的「相邻」要求两个 `1` 必须在水平或者竖直方向上相邻。你可以假设 `grid` 的四个边缘都被 `0`（代表水）包围着。

找到给定的二维数组中最大的岛屿面积。如果没有岛屿，则返回面积为 `0` 。

 

**示例 1:**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII105-1626667010-nSGPXz-image.png)

```
输入: grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
输出: 6
解释: 对于上面这个给定矩阵应返回 6。注意答案不应该是 11 ，因为岛屿只能包含水平或垂直的四个方向的 1 。
```

**示例 2:**

```
输入: grid = [[0,0,0,0,0,0,0,0]]
输出: 0
```

 

**提示：**

- `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 50`
- `grid[i][j] is either 0 or 1`

 

注意：本题与 695 题[695. 岛屿的最大面积](https://leetcode-cn.com/problems/max-area-of-island/)相同

