## 剑指 Offer 38. 字符串的排列

LeetCode：[剑指 Offer 38. 字符串的排列](https://leetcode.cn/problems/zi-fu-chuan-de-pai-lie-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<string> permutation(string s) {
        sort(s.begin(), s.end());

        vector<string> res;
        do {
            res.push_back(s);
        } while(next_permutation(s.begin(), s.end()));
        return res;
    }
};
```



---



### 题目

输入一个字符串，打印出该字符串中字符的所有排列。

 

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

 

**示例:**

```
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
```

 

**限制：**

```
1 <= s 的长度 <= 8
```


