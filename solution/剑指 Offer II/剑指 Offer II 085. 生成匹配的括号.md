## 剑指 Offer II 085. 生成匹配的括号

LeetCode：[剑指 Offer II 085. 生成匹配的括号](https://leetcode.cn/problems/IDBivT/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        int len = n << 1, to = 1 << len;

        vector<string> res;
        string ss;
        for(int i = 0, cnt; i < to; i++) {
            ss = "";
            cnt = 0;
            for(int j = len - 1, now; j >= 0; j--) {
                now = i >> j & 1;
                if(now == 0) {
                    cnt ++;
                    ss += '('; 
                } else {
                    cnt --;
                    if(cnt < 0) { // illegal
                        break;
                    }
                    ss += ')';
                }
            }
            if(cnt == 0) {
                res.push_back(ss);
            }
        }
        return res;
    }
};
```



---



### 题目

正整数 `n` 代表生成括号的对数，请设计一个函数，用于能够生成所有可能的并且 **有效的** 括号组合。

 

**示例 1：**

```
输入：n = 3
输出：["((()))","(()())","(())()","()(())","()()()"]
```

**示例 2：**

```
输入：n = 1
输出：["()"]
```

 

**提示：**

- `1 <= n <= 8`

 

注意：本题与 22 题[22. 括号生成](https://leetcode-cn.com/problems/generate-parentheses/)相同


