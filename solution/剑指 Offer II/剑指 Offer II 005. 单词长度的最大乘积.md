## 剑指 Offer II 005. 单词长度的最大乘积

LeetCode：[剑指 Offer II 005. 单词长度的最大乘积](https://leetcode.cn/problems/aseY1I/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int maxProduct(vector<string>& words) {
        bitset<26> bs[1000];
        for(int i = 0; i < words.size(); i++) {
            for(int j = 0, to; j < words[i].size(); j++) {
                bs[i][words[i][j] - 'a'] = 1;
            }
        }
        int mx = 0;
        for(int i = 0; i < words.size(); i++) {
            for(int j = i + 1; j < words.size(); j++) {
                if((bs[i] & bs[j]).none()) {
                    mx = max(mx, (int)(words[i].size() * words[j].size()));
                }
            }
        }
        return mx;
    }
};
```



---



### 题目

给定一个字符串数组 `words`，请计算当两个字符串 `words[i]` 和 `words[j]` 不包含相同字符时，它们长度的乘积的最大值。假设字符串中只包含英语的小写字母。如果没有不包含相同字符的一对字符串，返回 0。

 

**示例 1:**

```
输入: words = ["abcw","baz","foo","bar","fxyz","abcdef"]
输出: 16 
解释: 这两个单词为 "abcw", "fxyz"。它们不包含相同字符，且长度的乘积最大。
```

**示例 2:**

```
输入: words = ["a","ab","abc","d","cd","bcd","abcd"]
输出: 4 
解释: 这两个单词为 "ab", "cd"。
```

**示例 3:**

```
输入: words = ["a","aa","aaa","aaaa"]
输出: 0 
解释: 不存在这样的两个单词。
```

 

**提示：**

- `2 <= words.length <= 1000`
- `1 <= words[i].length <= 1000`
- `words[i]` 仅包含小写字母

 

注意：本题与 318 题[318. 最大单词长度乘积](https://leetcode-cn.com/problems/maximum-product-of-word-lengths/)相同


