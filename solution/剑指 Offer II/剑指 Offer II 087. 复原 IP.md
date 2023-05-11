## 剑指 Offer II 087. 复原 IP

LeetCode：[剑指 Offer II 087. 复原 IP](https://leetcode.cn/problems/0on3uN/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    bool judge(string str) {
        if((int)str.size() > 3) {
            return false;
        }
        int num = stoi(str);
        if(num < 0 || num > 255) {
            return false;
        }
        return to_string(num) == str;
    }

    vector<string> restoreIpAddresses(string s) {
        int len = (int)s.size();
        if(len > 12) {
            return {};
        }
        int to = 1 << len;

        vector<string> res, v;
        for(int i = 0; i < to; i++) {
            v.clear();
            string pre = "";
            bool flag = true;
            for(int j = 0, now; j < len; j++) {
                now = i >> j & 1;
                if(j == 0 && now == 1) {
                    break;
                }
                if(now == 0) {
                    if(!pre.empty()) {
                        if(judge(pre)) {
                            v.push_back(pre);
                            if((int)v.size() > 4) {
                                flag = false;
                                break;
                            }
                            pre = "";
                            pre += s[j];
                        } else {
                            flag = false;
                            break;
                        }
                    } else {
                        pre += s[j];
                    }
                } else {
                    pre += s[j];
                }
            }
            if(!pre.empty()) {
                if(judge(pre)) {
                    v.push_back(pre);
                    if((int)v.size() > 4) {
                        flag = false;
                    }
                } else {
                    flag = false;
                }
            }
            if(flag && !v.empty() && (int)v.size() == 4) {
                res.push_back(v[0] + '.' + v[1] + '.' + v[2] + '.' + v[3]);
            }
        }
        return res;
    }
};
```



---



### 题目

给定一个只包含数字的字符串 `s` ，用以表示一个 IP 地址，返回所有可能从 `s` 获得的 **有效 IP 地址** 。你可以按任何顺序返回答案。

**有效 IP 地址** 正好由四个整数（每个整数位于 0 到 255 之间组成，且不能含有前导 `0`），整数之间用 `'.'` 分隔。

例如："0.1.2.201" 和 "192.168.1.1" 是 **有效** IP 地址，但是 "0.011.255.245"、"192.168.1.312" 和 "192.168@1.1" 是 **无效** IP 地址。

 

**示例 1：**

```
输入：s = "25525511135"
输出：["255.255.11.135","255.255.111.35"]
```

**示例 2：**

```
输入：s = "0000"
输出：["0.0.0.0"]
```

**示例 3：**

```
输入：s = "1111"
输出：["1.1.1.1"]
```

**示例 4：**

```
输入：s = "010010"
输出：["0.10.0.10","0.100.1.0"]
```

**示例 5：**

```
输入：s = "10203040"
输出：["10.20.30.40","102.0.30.40","10.203.0.40"]
```

 

**提示：**

- `0 <= s.length <= 3000`
- `s` 仅由数字组成

 

注意：本题与 93 题[93. 复原 IP 地址](https://leetcode-cn.com/problems/restore-ip-addresses/)相同


