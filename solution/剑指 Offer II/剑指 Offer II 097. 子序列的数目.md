## 剑指 Offer II 097. 子序列的数目

LeetCode：[剑指 Offer II 097. 子序列的数目](https://leetcode.cn/problems/21dk04/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:
    int numDistinct(string s, string t) {
        int len1 = (int)s.size(), len2 = (int)t.size();
        if(len1 < len2) {
            return 0;
        }

        vector< vector<unsigned int> > dp(len1 + 1, vector<unsigned int>(len2 + 1, 0));
        for(int i = 0; i <= len1; i++) {
            dp[i][0] = 1;
        }
        for(int i = 0; i < len1; i++) {
            for(int j = 0; j <= i && j < len2; j++) {
                dp[i + 1][j + 1] = dp[i][j + 1] + (s[i] == t[j] ? dp[i][j] : 0); 
            }
        }
        return dp[len1][len2];
    }
};
```



---



### 题目

给定一个字符串 `s` 和一个字符串 `t` ，计算在 `s` 的子序列中 `t` 出现的个数。

字符串的一个 **子序列** 是指，通过删除一些（也可以不删除）字符且不干扰剩余字符相对位置所组成的新字符串。（例如，`"ACE"` 是 `"ABCDE"` 的一个子序列，而 `"AEC"` 不是）

题目数据保证答案符合 32 位带符号整数范围。

 

**示例 1：**

```
输入：s = "rabbbit", t = "rabbit"
输出：3
解释：
如下图所示, 有 3 种可以从 s 中得到 "rabbit" 的方案。
rabbbit
rabbbit
rabbbit
```

**示例 2：**

```
输入：s = "babgbag", t = "bag"
输出：5
解释：
如下图所示, 有 5 种可以从 s 中得到 "bag" 的方案。 
babgbag
babgbag
babgbag
babgbag
babgbag
```

 

**提示：**

- `0 <= s.length, t.length <= 1000`
- `s` 和 `t` 由英文字母组成

 

注意：本题与 115 题[115. 不同的子序列](https://leetcode-cn.com/problems/distinct-subsequences/)相同


