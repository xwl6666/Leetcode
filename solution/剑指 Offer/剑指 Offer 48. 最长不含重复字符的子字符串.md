## 剑指 Offer 48. 最长不含重复字符的子字符串

LeetCode：[剑指 Offer 48. 最长不含重复字符的子字符串](https://leetcode.cn/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int len = (int)s.size(), mx = 0;

        unordered_set<int> bk;
        for(int l = 0, r = 0; l < len; l++) {
            while(r < len && !bk.count(s[r])) {
                bk.insert(s[r]);
                r ++;
            }
            mx = max(mx, r - l);
            if(r == len) {
                break;
            }
            bk.erase(s[l]);
        }

        return mx;
    }
};
```



---



### 题目

请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

 

**示例 1:**

```
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

**示例 2:**

```
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3:**

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

 

提示：

- `s.length <= 40000`

注意：本题与 3 题[3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/)相同


