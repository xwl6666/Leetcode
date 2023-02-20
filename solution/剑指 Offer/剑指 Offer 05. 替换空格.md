## 剑指 Offer 05. 替换空格

LeetCode：[剑指 Offer 05. 替换空格](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    string replaceSpace(string s) {
        string res = "";
        for(int i : s) {
            if(i == ' ') {
                res += "%20";
            } else {
                res += i;
            }
        }
        return res;
    }
};
```



---



### 题目

请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

 

**示例 1：**

```
输入：s = "We are happy."
输出："We%20are%20happy."
```

 

**限制：**

```
0 <= s 的长度 <= 10000
```

