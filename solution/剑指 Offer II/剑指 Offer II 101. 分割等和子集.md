## 剑指 Offer II 101. 分割等和子集

LeetCode：[剑指 Offer II 101. 分割等和子集](https://leetcode.cn/problems/NUPfPr/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int sum = 0;
        for(int i : nums) {
            sum += i;
        }
        if(sum & 1) {
            return false;
        }

        const int maxn = 10005;
        int dp[maxn] = {0};

        dp[0] = 1;
        for(int i = 0; i < nums.size(); i++) {
            for(int j = maxn - 1, to; j >= 0; j--) {
                to = j + nums[i];
                if(to >= maxn) {
                    continue;
                }

                if(dp[j] > 0) {
                    dp[to] = max(dp[to], dp[j] + 1);
                }
            }
        }

        return dp[sum / 2] > 0;
    }
};
```



---



### 题目

给定一个非空的正整数数组 `nums` ，请判断能否将这些数字分成元素和相等的两部分。

 

**示例 1：**

```
输入：nums = [1,5,11,5]
输出：true
解释：nums 可以分割成 [1, 5, 5] 和 [11] 。
```

**示例 2：**

```
输入：nums = [1,2,3,5]
输出：false
解释：nums 不可以分为和相等的两部分
```

 

**提示：**

- `1 <= nums.length <= 200`
- `1 <= nums[i] <= 100`

 

注意：本题与 416 题[416. 分割等和子集](https://leetcode-cn.com/problems/partition-equal-subset-sum/)相同


