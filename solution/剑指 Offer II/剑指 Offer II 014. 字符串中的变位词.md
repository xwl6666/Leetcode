## 剑指 Offer II 014. 字符串中的变位词

LeetCode：[剑指 Offer II 014. 字符串中的变位词](https://leetcode.cn/problems/MPnaiL/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        int len1 = (int)s1.size(), len2 = (int)s2.size();
        if(len1 > len2) {
            return false;
        }
        unordered_map<int, int> pre;
        for(int i : s1) {
            pre[i] ++;
        }
        
        unordered_map<int, int> now;
        for(int i = 0; i < len1; i++) {
            now[s2[i]] ++;
        }
        if(now == pre) {
            return true;
        }

        for(int i = len1, p; i < len2; i++) {
            p = s2[i - len1];
            if(-- now[p] == 0) {
                now.erase(p);
            }
            now[s2[i]] ++;
            if(now == pre) {
                return true;
            }
        }
        return false;
    }
};
```



---



### 题目

给定两个字符串 `s1` 和 `s2`，写一个函数来判断 `s2` 是否包含 `s1` 的某个变位词。

换句话说，第一个字符串的排列之一是第二个字符串的 **子串** 。

 

**示例 1：**

```
输入: s1 = "ab" s2 = "eidbaooo"
输出: True
解释: s2 包含 s1 的排列之一 ("ba").
```

**示例 2：**

```
输入: s1= "ab" s2 = "eidboaoo"
输出: False
```

 

**提示：**

- `1 <= s1.length, s2.length <= 10^4`
- `s1` 和 `s2` 仅包含小写字母

 

注意：本题与 567 题[567. 字符串的排列](https://leetcode-cn.com/problems/permutation-in-string/)相同


