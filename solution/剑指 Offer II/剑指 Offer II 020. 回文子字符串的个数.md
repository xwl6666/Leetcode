## 剑指 Offer II 020. 回文子字符串的个数

LeetCode：[剑指 Offer II 020. 回文子字符串的个数](https://leetcode.cn/problems/a7VOhD/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int countSubstrings(string s) {
        int len = (int)s.size(), res = 0;

        for(int i = 0, j; i < len - 1; i++) {
            res ++;
            j = i + 1;
            if(s[i] == s[j]) {
                res ++;
                for(int l = i - 1, r = j + 1; ; l -- , r++) {
                    if(l < 0 || r >= len) {
                        break;
                    }
                    if(s[l] == s[r]) {
                        res ++;
                    } else {
                        break;
                    }
                }
            }
            j = i;
            for(int l = i - 1, r = j + 1; ; l -- , r++) {
                if(l < 0 || r >= len) {
                    break;
                }
                if(s[l] == s[r]) {
                    res ++;
                } else {
                    break;
                }
            }
        }

        return res + 1;
    }
};
```



---



### 题目

给定一个字符串 `s` ，请计算这个字符串中有多少个回文子字符串。

具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被视作不同的子串。

 

**示例 1：**

```
输入：s = "abc"
输出：3
解释：三个回文子串: "a", "b", "c"
```

**示例 2：**

```
输入：s = "aaa"
输出：6
解释：6个回文子串: "a", "a", "a", "aa", "aa", "aaa"
```

 

**提示：**

- `1 <= s.length <= 1000`
- `s` 由小写英文字母组成

 

注意：本题与 647 题[647. 回文子串](https://leetcode-cn.com/problems/palindromic-substrings/)相同


