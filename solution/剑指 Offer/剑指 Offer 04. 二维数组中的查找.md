## 剑指 Offer 04. 二维数组中的查找

LeetCode：[剑指 Offer 04. 二维数组中的查找](https://leetcode.cn/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
        int n = (int)matrix.size();
        if(n == 0) {
            return false;
        }
        int m = (int)matrix[0].size();
        int l = n - 1, r = 0;
        while(l >= 0 && r < m) {
            if(matrix[l][r] < target) {
                r ++;
            } else if(matrix[l][r] > target) {
                l --;
            } else {
                return true;
            }
        }
        return false;
    }
};
```



---



### 题目

在一个 n * m 的二维数组中，每一行都按照从左到右 **非递减** 的顺序排序，每一列都按照从上到下 **非递减** 的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

 

**示例:**

现有矩阵 matrix 如下：

```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```

给定 target = `5`，返回 `true`。

给定 target = `20`，返回 `false`。

 

**限制：**

```
0 <= n <= 1000
0 <= m <= 1000
```

 

**注意：**本题与 240 题[240. 搜索二维矩阵 II](https://leetcode.cn/problems/search-a-2d-matrix-ii/)相同

