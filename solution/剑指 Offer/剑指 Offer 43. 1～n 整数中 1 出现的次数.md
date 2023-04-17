## 剑指 Offer 43. 1～n 整数中 1 出现的次数

LeetCode：[剑指 Offer 43. 1～n 整数中 1 出现的次数](https://leetcode.cn/problems/1nzheng-shu-zhong-1chu-xian-de-ci-shu-lcof/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:

    const static int maxn = 12;

    int a[maxn];

    int dp[maxn][maxn][2];

    int dfs(int pos, int cnt, bool limit) {
        if(pos == -1) {
            return cnt;
        }
        
        if(dp[pos][cnt][limit] != -1) {
            return dp[pos][cnt][limit];
        }
        
        int up = limit ? a[pos] : 9;
        
        int res = 0;
        for(int i = 0; i <= up; i++) {
            res += dfs(pos - 1, cnt + (i == 1), limit && i == a[pos]);
        }

        dp[pos][cnt][limit] = res;
        return res;
    }

    int solve(int x) {
        int pos = 0;
        while(x) {
            a[pos++] = x % 10;
            x /= 10;
        }
        
        return dfs(pos - 1, 0, true);
    }

    int countDigitOne(int n) {
        memset(dp, -1, sizeof(dp));

        return solve(n);
    }
};
```



---



### 题目

输入一个整数 `n` ，求1～n这n个整数的十进制表示中1出现的次数。

例如，输入12，1～12这些整数中包含1 的数字有1、10、11和12，1一共出现了5次。

 

**示例 1：**

```
输入：n = 12
输出：5
```

**示例 2：**

```
输入：n = 13
输出：6
```

 

**限制：**

- `1 <= n < 2^31`

注意：本题与 233 题[233. 数字 1 的个数](https://leetcode-cn.com/problems/number-of-digit-one/)相同


