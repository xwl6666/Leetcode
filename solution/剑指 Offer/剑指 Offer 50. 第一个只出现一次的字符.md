## 剑指 Offer 50. 第一个只出现一次的字符

LeetCode：[剑指 Offer 50. 第一个只出现一次的字符](https://leetcode.cn/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    char firstUniqChar(string s) {
        unordered_map<int, int> bk;
        for(int i : s) {
            bk[i] ++;
        }
        for(int i : s) {
            if(bk[i] == 1) {
                return i;
            }
        }
        return ' ';
    }
};
```



---



### 题目

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

**示例 1:**

```
输入：s = "abaccdeff"
输出：'b'
```

**示例 2:**

```
输入：s = "" 
输出：' '
```

 

**限制：**

`0 <= s 的长度 <= 50000`

