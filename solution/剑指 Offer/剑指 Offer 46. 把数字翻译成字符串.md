## 剑指 Offer 46. 把数字翻译成字符串

LeetCode：[剑指 Offer 46. 把数字翻译成字符串](https://leetcode.cn/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    int dp[12];

    bool judge(char s0, char s1) {
        if(s0 == '0') {
            return false;
        }
        return (s0 - '0') * 10 + (s1 - '0') <= 25;
    }

    int translateNum(int num) {
        string str = to_string(num);
        int len = (int)str.size();

        dp[0] = 1;
        dp[1] = dp[0] + judge(str[0], str[1]);
        for(int i = 2; i < len; i++) {
            dp[i] = dp[i - 1] + dp[i - 2] * judge(str[i - 1], str[i]);
        }

        return dp[len - 1];
    }
};
```



---



### 题目

给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

 

**示例 1:**

```
输入: 12258
输出: 5
解释: 12258有5种不同的翻译，分别是"bccfi", "bwfi", "bczi", "mcfi"和"mzi"
```

 

**提示：**

- `0 <= num < 2^31`


