## 剑指 Offer 20. 表示数值的字符串

LeetCode：[剑指 Offer 20. 表示数值的字符串](https://leetcode.cn/problems/biao-shi-shu-zhi-de-zi-fu-chuan-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    bool judgeDecimal(string str) {
        if((int)str.size() < 2) {
            return false;
        }
        if(str.front() == '+' || str.front() == '-') {
            str.erase(0, 1);
        }
        if((int)str.size() == 1 && str.front() == '.') {
            return false;
        }

        for(int i = 0; i < str.size(); i++) {
            if(str[i] == '.') {
                for(int j = i - 1; j >= 0; j--) {
                    if(str[j] < '0' || str[j] > '9') {
                        return false;
                    }
                }
                for(int j = i + 1; j < str.size(); j++) {
                    if(str[j] < '0' || str[j] > '9') {
                        return false;
                    }
                }
                return true;
            }
        }

        return false;
    }

    bool judgeInteger(string str) {
        if((int)str.size() == 0) {
            return false;
        }
        if((int)str.size() == 1) {
            return str.front() >= '0' && str.front() <= '9';
        }

        if(str.front() == '+' || str.front() == '-') {
            str.erase(0, 1);
        }
        for(int i : str) {
            if(i < '0' || i > '9') {
                return false;
            }
        }
        return true;
    }

    bool isNumber(string s) {
        while((int)s.size() > 1 && s.back() == ' ') {
            s.pop_back();
        }
        while((int)s.size() > 1 && s.front() == ' ') {
            s.erase(0, 1);
        }

        for(int i = 0; i < s.size(); i++) {
            if(s[i] == 'e' || s[i] == 'E') {
                string pre = s.substr(0, i);
                string nxt = s.substr(i + 1);
                return (judgeInteger(pre) || judgeDecimal(pre)) 
                            && judgeInteger(nxt);
            }
        }

        return judgeDecimal(s) || judgeInteger(s);
    }
};
```



---



### 题目

请实现一个函数用来判断字符串是否表示**数值**（包括整数和小数）。

**数值**（按顺序）可以分成以下几个部分：

1. 若干空格
2. 一个 **小数** 或者 **整数**
3. （可选）一个 `'e'` 或 `'E'` ，后面跟着一个 **整数**
4. 若干空格

**小数**（按顺序）可以分成以下几个部分：

1. （可选）一个符号字符（`'+'` 或 `'-'`）
2. 下述格式之一：
   1. 至少一位数字，后面跟着一个点 `'.'`
   2. 至少一位数字，后面跟着一个点 `'.'` ，后面再跟着至少一位数字
   3. 一个点 `'.'` ，后面跟着至少一位数字

**整数**（按顺序）可以分成以下几个部分：

1. （可选）一个符号字符（`'+'` 或 `'-'`）
2. 至少一位数字

部分**数值**列举如下：

- `["+100", "5e2", "-123", "3.1416", "-1E-16", "0123"]`

部分**非数值**列举如下：

- `["12e", "1a3.14", "1.2.3", "+-5", "12e+5.4"]`

 

**示例 1：**

```
输入：s = "0"
输出：true
```

**示例 2：**

```
输入：s = "e"
输出：false
```

**示例 3：**

```
输入：s = "."
输出：false
```

**示例 4：**

```
输入：s = "    .1  "
输出：true
```

 

**提示：**

- `1 <= s.length <= 20`
- `s` 仅含英文字母（大写和小写），数字（`0-9`），加号 `'+'` ，减号 `'-'` ，空格 `' '` 或者点 `'.'` 。


