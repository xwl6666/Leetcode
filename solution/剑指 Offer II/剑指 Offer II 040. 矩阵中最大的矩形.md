## 剑指 Offer II 040. 矩阵中最大的矩形

LeetCode：[剑指 Offer II 040. 矩阵中最大的矩形](https://leetcode.cn/problems/PLYXKQ/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:
    int maximalRectangle(vector<string>& matrix) {
        if(matrix.empty()) {
            return 0;
        }

        int mx = 0;
        vector<int> heights(matrix[0].size(), 0);

        for(string row : matrix) {
            for(int i = 0; i < row.size(); i++) {
                if (row[i] == '0') {
                    heights[i] = 0;
                }
                else {
                    heights[i] ++;
                }
            }
            mx = max(mx, largestRectangleArea(heights));
        }
        return mx;
    }

    int largestRectangleArea(vector<int>& heights) {
        stack<int> stk;
        stk.push(-1);
        int mx = 0, height, width;
        for(int i = 0; i < heights.size(); ++i) {
            while(stk.top() != -1 && heights[stk.top()] >= heights[i]) {
                height = heights[stk.top()], stk.pop();
                width = i - stk.top() - 1;
                mx = max(mx, height * width);
            }
            stk.push(i);
        }

        while(stk.top() != -1) {
            height = heights[stk.top()], stk.pop();
            width = heights.size() - stk.top() - 1;
            mx = max(mx, height * width);
        }
        return mx;
    }
};
```



---



### 题目

给定一个由 `0` 和 `1` 组成的矩阵 `matrix` ，找出只包含 `1` 的最大矩形，并返回其面积。

**注意：**此题 `matrix` 输入格式为一维 `01` 字符串数组。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII040-maximal.jpg)

```
输入：matrix = ["10100","10111","11111","10010"]
输出：6
解释：最大矩形如上图所示。
```

**示例 2：**

```
输入：matrix = []
输出：0
```

**示例 3：**

```
输入：matrix = ["0"]
输出：0
```

**示例 4：**

```
输入：matrix = ["1"]
输出：1
```

**示例 5：**

```
输入：matrix = ["00"]
输出：0
```

 

**提示：**

- `rows == matrix.length`
- `cols == matrix[0].length`
- `0 <= row, cols <= 200`
- `matrix[i][j]` 为 `'0'` 或 `'1'`

 

注意：本题与 85 题[85. 最大矩形](https://leetcode-cn.com/problems/maximal-rectangle/)相同（输入参数格式不同）


