## 剑指 Offer II 019. 最多删除一个字符得到回文

LeetCode：[剑指 Offer II 019. 最多删除一个字符得到回文](https://leetcode.cn/problems/RQku0D/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:

    bool judge(string s1) {
        int len = (int)s1.size(), mid = len / 2;
        for(int i = 0; i < mid; i++) {
            if(s1[i] != s1[len - i - 1]) {
                return false;
            }
        }
        return true;
    }

    bool validPalindrome(string s) {
        int len = (int)s.size(), l = 0, r = len - 1;
        while(l < r) {
            if(s[l] == s[r]) {
                l ++;
                r --;
            } else {
                return judge(s.substr(l + 1, r - l)) || judge(s.substr(l, r - l));
            }
        }
        return true;
    }
};
```



---



### 题目

给定一个非空字符串 `s`，请判断如果 **最多** 从字符串中删除一个字符能否得到一个回文字符串。

 

**示例 1:**

```
输入: s = "aba"
输出: true
```

**示例 2:**

```
输入: s = "abca"
输出: true
解释: 可以删除 "c" 字符 或者 "b" 字符
```

**示例 3:**

```
输入: s = "abc"
输出: false
```

 

**提示:**

- `1 <= s.length <= 10^5`
- `s` 由小写英文字母组成

 

注意：本题与 680 题[680. 验证回文串 II](https://leetcode-cn.com/problems/valid-palindrome-ii/)相同


