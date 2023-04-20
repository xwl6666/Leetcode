## 剑指 Offer II 010. 和为 k 的子数组

LeetCode：[剑指 Offer II 010. 和为 k 的子数组](https://leetcode.cn/problems/QTMn0o/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        unordered_map<int, int> bk;

        bk[0] = 1;
        int sum = 0, res = 0;
        for(int i : nums) {
            sum += i;
            if(bk.count(sum - k)) {
                res += bk[sum - k];
            }
            bk[sum] ++;
        }
        return res;
    }
};
```



---



### 题目

给定一个整数数组和一个整数 `k` **，**请找到该数组中和为 `k` 的连续子数组的个数。

 

**示例 1：**

```
输入:nums = [1,1,1], k = 2
输出: 2
解释: 此题 [1,1] 与 [1,1] 为两种不同的情况
```

**示例 2：**

```
输入:nums = [1,2,3], k = 3
输出: 2
```

 

**提示:**

- `1 <= nums.length <= 2 * 10^4`
- `-1000 <= nums[i] <= 1000`
- `-10^7 <= k <= 10^7`

 

注意：本题与 560 题[560. 和为 K 的子数组](https://leetcode-cn.com/problems/subarray-sum-equals-k/)相同


