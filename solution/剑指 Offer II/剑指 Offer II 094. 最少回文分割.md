## 剑指 Offer II 094. 最少回文分割

LeetCode：[剑指 Offer II 094. 最少回文分割](https://leetcode.cn/problems/omKAoA/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:
    int minCut(string s) {
        int len = (int)s.size();
        vector< vector<bool> > f(len, vector<bool>(len, false));
        for(int i = 0; i < len; i++) {
            for(int j = 0; j <= i; j++) {
                if(s[i] == s[j] && (i - j <= 1 || f[j + 1][i - 1])) {
                    f[j][i] = true;
                }
            }
        }

        vector<int> dp(len);
        for(int i = 0; i < len; i++) {
            if(f[0][i]) {
                dp[i] = 0;
            } else {
                dp[i] = i;
                for(int j = 1; j <= i; j++) {
                    if(f[j][i]) {
                        dp[i] = min(dp[i], dp[j - 1] + 1);
                    }
                }
            }
        }
        return dp[len - 1];
    }
};
```



---



### 题目

给定一个字符串 `s`，请将 `s` 分割成一些子串，使每个子串都是回文串。

返回符合要求的 **最少分割次数** 。

 

**示例 1：**

```
输入：s = "aab"
输出：1
解释：只需一次分割就可将 s 分割成 ["aa","b"] 这样两个回文子串。
```

**示例 2：**

```
输入：s = "a"
输出：0
```

**示例 3：**

```
输入：s = "ab"
输出：1
```

 

**提示：**

- `1 <= s.length <= 2000`
- `s` 仅由小写英文字母组成

 

注意：本题与 132 题[132. 分割回文串 II](https://leetcode-cn.com/problems/palindrome-partitioning-ii/)相同


