## 剑指 Offer 14- I. 剪绳子

LeetCode：[剑指 Offer 14- I. 剪绳子](https://leetcode.cn/problems/jian-sheng-zi-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    int cuttingRope(int n) {
        if(n <= 3) {
            return n - 1;
        }
        int res = 1, yu = n % 3, div = n / 3;

        if(yu == 0) {
            ;
        } else if(yu == 1) {
            div --;
            res *= 2 * 2;
        } else if(yu == 2) {
            res *= 2;
        }
        while(div --) {
            res *= 3;
        }

        return res;
    }
};
```



---



### 题目

给你一根长度为 `n` 的绳子，请把绳子剪成整数长度的 `m` 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 `k[0],k[1]...k[m-1]` 。请问 `k[0]*k[1]*...*k[m-1]` 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

**示例 1：**

```
输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
```

**示例 2:**

```
输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36
```

**提示：**

- `2 <= n <= 58`

注意：本题与 343 题[343. 整数拆分](https://leetcode-cn.com/problems/integer-break/)相同


