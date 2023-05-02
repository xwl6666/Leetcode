## 剑指 Offer II 035. 最小时间差

LeetCode：[剑指 Offer II 035. 最小时间差](https://leetcode.cn/problems/569nqc/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    int findMinDifference(vector<string>& timePoints) {
        int mi = INT_MAX, len = (int)timePoints.size();

        vector<int> v(len);
        for(int i = 0; i < len; i++) {
            v[i] = ((timePoints[i][0] - '0') * 10 + timePoints[i][1] - '0') * 60 + 
                        (timePoints[i][3] - '0') * 10 + timePoints[i][4] - '0';
        }
        sort(v.begin(), v.end());

        for(int i = 1, now; i < len; i++) {
            now = v[i] - v[i - 1];
            if(now < mi) {
                mi = now;
            }
        }

        v[0] += 24 * 60;
        int now = v[0] - v[len - 1];
        if(now < mi) {
            mi = now;
        }

        return mi;
    }
};
```



---



### 题目

给定一个 24 小时制（小时:分钟 **"HH:MM"**）的时间列表，找出列表中任意两个时间的最小时间差并以分钟数表示。

 

**示例 1：**

```
输入：timePoints = ["23:59","00:00"]
输出：1
```

**示例 2：**

```
输入：timePoints = ["00:00","23:59","00:00"]
输出：0
```

 

**提示：**

- `2 <= timePoints <= 2 * 10^4`
- `timePoints[i]` 格式为 **"HH:MM"**

 

注意：本题与 539 题[539. 最小时间差](https://leetcode-cn.com/problems/minimum-time-difference/)相同


