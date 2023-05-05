## 剑指 Offer II 039. 直方图最大矩形面积

LeetCode：[剑指 Offer II 039. 直方图最大矩形面积](https://leetcode.cn/problems/largest-rectangle-in-histogram/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:
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

给定非负整数数组 `heights` ，数组中的数字用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 `1` 。

求在该柱状图中，能够勾勒出来的矩形的最大面积。

 

**示例 1:**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII039-histogram.jpg)

```
输入：heights = [2,1,5,6,2,3]
输出：10
解释：最大的矩形为图中红色区域，面积为 10
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII039-histogram-1.jpg)

```
输入： heights = [2,4]
输出： 4
```

 

**提示：**

- `1 <= heights.length <=10^5`
- `0 <= heights[i] <= 10^4`

 

注意：本题与 84 题[84. 柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)相同

