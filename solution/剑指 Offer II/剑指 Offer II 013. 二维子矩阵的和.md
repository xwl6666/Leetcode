## 剑指 Offer II 013. 二维子矩阵的和

LeetCode：[剑指 Offer II 013. 二维子矩阵的和](https://leetcode.cn/problems/O4NDxx/)，难度：中等。

### 题解

#### 代码

```c++
class NumMatrix {
public:

    vector< vector<int> > dp;

    NumMatrix(vector<vector<int>>& mat) {
        int n = (int)mat.size(), m = (int)mat[0].size();
        dp = mat;
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < m; j++) {
                if(i == 0 && j == 0) {
                    // dp[i][j] = mat[i][j];
                    continue;
                } else if(i == 0) {
                    dp[i][j] += dp[i][j - 1];
                } else if(j == 0) {
                    dp[i][j] += dp[i - 1][j];
                } else {
                    dp[i][j] += dp[i][j - 1] + dp[i - 1][j] - dp[i -1][j - 1];
                }
            }
        }
    }
    
    int sumRegion(int x1, int y1, int x2, int y2) {
        int res = dp[x2][y2];
        bool f1 = x1 - 1 >= 0, f2 = y1 - 1 >= 0;
        if(f1) {
            res -= dp[x1 - 1][y2];
        }
        if(f2) {
            res -= dp[x2][y1 - 1];
        }
        if(f1 && f2) {
            res += dp[x1 - 1][y1 - 1];
        }
        return res;
    }
};

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix* obj = new NumMatrix(matrix);
 * int param_1 = obj->sumRegion(row1,col1,row2,col2);
 */
```



---



### 题目

给定一个二维矩阵 `matrix`，以下类型的多个请求：

- 计算其子矩形范围内元素的总和，该子矩阵的左上角为 `(row1, col1)` ，右下角为 `(row2, col2)` 。

实现 `NumMatrix` 类：

- `NumMatrix(int[][] matrix)` 给定整数矩阵 `matrix` 进行初始化
- `int sumRegion(int row1, int col1, int row2, int col2)` 返回左上角 `(row1, col1)` 、右下角 `(row2, col2)` 的子矩阵的元素总和。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII 013-1626332422-wUpUHT-image.png)

```
输入: 
["NumMatrix","sumRegion","sumRegion","sumRegion"]
[[[[3,0,1,4,2],[5,6,3,2,1],[1,2,0,1,5],[4,1,0,1,7],[1,0,3,0,5]]],[2,1,4,3],[1,1,2,2],[1,2,2,4]]
输出: 
[null, 8, 11, 12]

解释:
NumMatrix numMatrix = new NumMatrix([[3,0,1,4,2],[5,6,3,2,1],[1,2,0,1,5],[4,1,0,1,7],[1,0,3,0,5]]]);
numMatrix.sumRegion(2, 1, 4, 3); // return 8 (红色矩形框的元素总和)
numMatrix.sumRegion(1, 1, 2, 2); // return 11 (绿色矩形框的元素总和)
numMatrix.sumRegion(1, 2, 2, 4); // return 12 (蓝色矩形框的元素总和)
```

 

**提示：**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 200`
- `-105 <= matrix[i][j] <= 10^5`
- `0 <= row1 <= row2 < m`
- `0 <= col1 <= col2 < n`
- 最多调用 `10^4` 次 `sumRegion` 方法

 

注意：本题与 304 题[304. 二维区域和检索 - 矩阵不可变](https://leetcode-cn.com/problems/range-sum-query-2d-immutable/)相同


