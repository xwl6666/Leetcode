## 剑指 Offer 42. 连续子数组的最大和

LeetCode：[剑指 Offer 42. 连续子数组的最大和](https://leetcode.cn/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int now = 0, res = -1e4;
        for(int i : nums) {
            now = max(i, now + i);
            res = max(res, now);
        }
        return res;
    }
};
```



---



### 题目

输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

 

**示例1:**

```
输入: nums = [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

 

**提示：**

- `1 <= arr.length <= 10^5`
- `-100 <= arr[i] <= 100`

注意：本题与 53 题[53. 最大子数组和](https://leetcode-cn.com/problems/maximum-subarray/)相同

