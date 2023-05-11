## 剑指 Offer II 072. 求平方根

LeetCode：[剑指 Offer II 072. 求平方根](https://leetcode.cn/problems/jJ0w9p/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    int mySqrt(int x) {
        int l = 0, r = x, mid, ans;
        while(l <= r) {
            mid = 1LL * l + r >> 1;
            if(1LL * mid * mid <= x) {
                ans = mid;
                l = mid + 1;
            } else {
                r = mid - 1;
            }
        }
        return ans;
    }
};
```



---



### 题目

给定一个非负整数 `x` ，计算并返回 `x` 的平方根，即实现 `int sqrt(int x)` 函数。

正数的平方根有两个，只输出其中的正数平方根。

如果平方根不是整数，输出只保留整数的部分，小数部分将被舍去。

 

**示例 1:**

```
输入: x = 4
输出: 2
```

**示例 2:**

```
输入: x = 8
输出: 2
解释: 8 的平方根是 2.82842...，由于小数部分将被舍去，所以返回 2
```

 

**提示:**

- `0 <= x <= 2^31 - 1`

 

注意：本题与 69 题[69. x 的平方根](https://leetcode-cn.com/problems/sqrtx/)相同


