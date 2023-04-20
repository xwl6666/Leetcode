## 剑指 Offer II 001. 整数除法

LeetCode：[剑指 Offer II 001. 整数除法](https://leetcode.cn/problems/xoh6Oh/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:

    #define ll long long

    ll qpow(ll a, ll k) {
        ll ans = 0;
        while (k > 0) {
            if (k & 1) {
                ans += a;
            }
            k >>= 1;
            a <<= 1;
        }
        return ans;
    }

    bool judge(ll mid, ll divisor, ll dividend) {
        return qpow(mid, divisor) <= dividend;
    }

    int divide(int dividend, int divisor) {
        if(divisor == 1) {
            return dividend;
        }
        int mi = - (1LL << 31), mx = (1LL << 31) - 1;
        if(dividend == mi && divisor == -1) {
            return mx;
        }

        int flag = -1;
        if( (divisor > 0 && dividend > 0) || (divisor < 0 && dividend < 0) ) {
            flag = 1;
        } 
        
        ll y = abs(dividend), x = abs(divisor);

        ll left = 0, right = mx, mid, ans = -1;
        while(left <= right) {
            mid = (left + right) >> 1;
            if(judge(mid, x, y)) {
                ans = max(ans, mid);
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return ans * flag;
    }
};
```



---



### 题目

给定两个整数 `a` 和 `b` ，求它们的除法的商 `a/b` ，要求不得使用乘号 `'*'`、除号 `'/'` 以及求余符号 `'%'` 。

 

**注意：**

- 整数除法的结果应当截去（`truncate`）其小数部分，例如：`truncate(8.345) = 8` 以及 `truncate(-2.7335) = -2`
- 假设我们的环境只能存储 32 位有符号整数，其数值范围是 `[−231, 231−1]`。本题中，如果除法结果溢出，则返回 `231 − 1`

 

**示例 1：**

```
输入：a = 15, b = 2
输出：7
解释：15/2 = truncate(7.5) = 7
```

**示例 2：**

```
输入：a = 7, b = -3
输出：-2
解释：7/-3 = truncate(-2.33333..) = -2
```

**示例 3：**

```
输入：a = 0, b = 1
输出：0
```

**示例 4：**

```
输入：a = 1, b = 1
输出：1
```

 

**提示:**

- `-2^31 <= a, b <= 2^31 - 1`
- `b != 0`

 

注意：本题与 29 题[29. 两数相除](https://leetcode-cn.com/problems/divide-two-integers/)相同


