## 剑指 Offer 57. 和为s的两个数字

LeetCode：[剑指 Offer 57. 和为s的两个数字](https://leetcode.cn/problems/he-wei-sde-liang-ge-shu-zi-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int l = 0, r = (int)nums.size() - 1, to;
        while(l <= r) {
            to = nums[l] + nums[r];
            if(to > target) {
                r --;
            } else if(to < target) {
                l ++;
            } else {
                return {nums[l], nums[r]};
            }
        }
        return {};
    }
};
```



---



### 题目

输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

 

**示例 1：**

```
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
```

**示例 2：**

```
输入：nums = [10,26,30,31,47,60], target = 40
输出：[10,30] 或者 [30,10]
```

 

**限制：**

- `1 <= nums.length <= 10^5`
- `1 <= nums[i] <= 10^6`


