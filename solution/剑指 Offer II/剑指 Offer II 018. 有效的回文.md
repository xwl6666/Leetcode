## 剑指 Offer II 018. 有效的回文

LeetCode：[剑指 Offer II 018. 有效的回文](https://leetcode.cn/problems/XltzEq/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    bool isPalindrome(string s) {
        string ss = "";
        for(int i : s) {
            if((i >= '0' && i <= '9') || (i >= 'a' && i <= 'z')) {
                ss += i;
            } else if(i >= 'A' && i <= 'Z') {
                ss += (i - 'A' + 'a');
            }
        }
        int len = (int)ss.size(), mid = len >> 1;
        for(int i = 0; i < mid; i++) {
            if(ss[i] != ss[len - i - 1]) {
                return false;
            }
        }
        return true;
    }
};
```



---



### 题目

给定一个字符串 `s` ，验证 `s` 是否是 **回文串** ，只考虑字母和数字字符，可以忽略字母的大小写。

本题中，将空字符串定义为有效的 **回文串** 。

 

**示例 1:**

```
输入: s = "A man, a plan, a canal: Panama"
输出: true
解释："amanaplanacanalpanama" 是回文串
```

**示例 2:**

```
输入: s = "race a car"
输出: false
解释："raceacar" 不是回文串
```

 

**提示：**

- `1 <= s.length <= 2 * 10^5`
- 字符串 `s` 由 ASCII 字符组成

 

注意：本题与 125 题[125. 验证回文串](https://leetcode-cn.com/problems/valid-palindrome/)相同 


