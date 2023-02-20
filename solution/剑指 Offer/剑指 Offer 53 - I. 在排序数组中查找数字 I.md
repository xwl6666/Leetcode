## 剑指 Offer 53 - I. 在排序数组中查找数字 I

LeetCode：[剑指 Offer 53 - I. 在排序数组中查找数字 I](https://leetcode.cn/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        return upper_bound(nums.begin(), nums.end(), target) 
                    - lower_bound(nums.begin(), nums.end(), target);
    }
};
```



---



### 题目

统计一个数字在排序数组中出现的次数。

 

**示例 1:**

```
输入: nums = [5,7,7,8,8,10], target = 8
输出: 2
```

**示例 2:**

```
输入: nums = [5,7,7,8,8,10], target = 6
输出: 0
```

 

**提示：**

- `0 <= nums.length <= 10^5`
- `-10^9 <= nums[i] <= 10^9`
- `nums` 是一个非递减数组
- `-10^9 <= target <= 10^9`

 

**注意：**本题与 34 题[34. 在排序数组中查找元素的第一个和最后一个位置](https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/)相同（仅返回值不同）

