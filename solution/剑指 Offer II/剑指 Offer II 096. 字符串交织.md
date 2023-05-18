## 剑指 Offer II 096. 字符串交织

LeetCode：[剑指 Offer II 096. 字符串交织](https://leetcode.cn/problems/IY6buf/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    bool f[105][105];

    bool isInterleave(string s1, string s2, string s3) {
        int len1 = (int)s1.size(), len2 = (int)s2.size(), len = (int)s3.size();
        if(len1 + len2 != len) {
            return false;
        }

        f[0][0] = true;
        for(int i = 0; i <= len1; i++) {
            for(int j = 0, to; j <= len2; j++) {
                to = i + j - 1;
                if(i > 0) {
                    f[i][j] |= (f[i - 1][j] && s1[i - 1] == s3[to]);
                }
                if(j > 0) {
                    f[i][j] |= (f[i][j - 1] && s2[j - 1] == s3[to]);
                }
            }
        }
        return f[len1][len2];
    }
};
```



---



### 题目

给定三个字符串 `s1`、`s2`、`s3`，请判断 `s3` 能不能由 `s1` 和 `s2` **交织（交错）** 组成。

两个字符串 `s` 和 `t` **交织** 的定义与过程如下，其中每个字符串都会被分割成若干 **非空** 子字符串：

- `s = s1 + s2 + ... + sn`
- `t = t1 + t2 + ... + tm`
- `|n - m| <= 1`
- **交织** 是 `s1 + t1 + s2 + t2 + s3 + t3 + ...` 或者 `t1 + s1 + t2 + s2 + t3 + s3 + ...`

**提示：**`a + b` 意味着字符串 `a` 和 `b` 连接。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII096-interleave.jpg)

```
输入：s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"
输出：true
```

**示例 2：**

```
输入：s1 = "aabcc", s2 = "dbbca", s3 = "aadbbbaccc"
输出：false
```

**示例 3：**

```
输入：s1 = "", s2 = "", s3 = ""
输出：true
```

 

**提示：**

- `0 <= s1.length, s2.length <= 100`
- `0 <= s3.length <= 200`
- `s1`、`s2`、和 `s3` 都由小写英文字母组成

 

注意：本题与 97 题[97. 交错字符串](https://leetcode-cn.com/problems/interleaving-string/)相同

