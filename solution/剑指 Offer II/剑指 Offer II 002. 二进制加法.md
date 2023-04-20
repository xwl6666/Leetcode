## 剑指 Offer II 002. 二进制加法

LeetCode：[剑指 Offer II 002. 二进制加法](https://leetcode.cn/problems/JFETK5/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    string addBinary(string a, string b) {
        int x = (int)a.size() - 1, y = (int)b.size() - 1;
        
        string res = "";
        int add = 0, sum;
        while(x >= 0 || y >= 0) {
            sum = ((x >= 0) ? a[x --] - '0' : 0) + ((y >= 0) ? b[y --] - '0' : 0) + add;
            res += (sum & 1) + '0';
            add = sum >> 1;
        }
        if(add) {
            res += '1';
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```



---



### 题目

给定两个 01 字符串 `a` 和 `b` ，请计算它们的和，并以二进制字符串的形式输出。

输入为 **非空** 字符串且只包含数字 `1` 和 `0`。

 

**示例 1:**

```
输入: a = "11", b = "10"
输出: "101"
```

**示例 2:**

```
输入: a = "1010", b = "1011"
输出: "10101"
```

 

**提示：**

- 每个字符串仅由字符 `'0'` 或 `'1'` 组成。
- `1 <= a.length, b.length <= 10^4`
- 字符串如果不是 `"0"` ，就都不含前导零。

 

注意：本题与 67 题[67. 二进制求和](https://leetcode-cn.com/problems/add-binary/)相同


