## 剑指 Offer 29. 顺时针打印矩阵

LeetCode：[剑指 Offer 29. 顺时针打印矩阵](https://leetcode.cn/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        if(matrix.empty()) {
            return {};
        }
        int u = 0, d = (int)matrix.size() - 1, l = 0, r = (int)matrix[0].size() - 1;
        vector<int> res;

        while(true) {
            for(int i = l; i <= r; i++) {
                res.push_back(matrix[u][i]);
            }
            if(u + 1 > d) {
                break;
            }
            for(int j = u + 1; j <= d; j++) {
                res.push_back(matrix[j][r]);
            }
            if(r - 1 < l) {
                break;
            }
            for(int i = r - 1; i >= l; i--) {
                res.push_back(matrix[d][i]);
            }
            if(d - 1 < u + 1) {
                break;
            }
            for(int j = d - 1; j >= u + 1; j--) {
                res.push_back(matrix[j][l]);
            }
            if(l + 1 > r - 1) {
                break;
            }
            u ++, d --, l ++, r --;
        }

        return res;
    }
};
```



---



### 题目

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

 

**示例 1：**

```
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
```

**示例 2：**

```
输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]
```

 

**限制：**

- `0 <= matrix.length <= 100`
- `0 <= matrix[i].length <= 100`

注意：本题与 54 题[54. 螺旋矩阵](https://leetcode-cn.com/problems/spiral-matrix/)相同


