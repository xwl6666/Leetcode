## 剑指 Offer II 070. 排序数组中只出现一次的数字

LeetCode：[剑指 Offer II 070. 排序数组中只出现一次的数字](https://leetcode.cn/problems/skFtm2/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int len = (int)nums.size();
        if(len == 1) {
            return nums[0];
        }

        int l = 0, r = len - 1, mid;
        while(l <= r) {
            mid = (l + r) >> 1;

            if(mid == 0) {
                if(nums[mid] != nums[mid + 1]) {
                    return nums[mid];
                }
                l = mid + 2;
            } else if(mid == len - 1) {
                if(nums[mid] != nums[mid - 1]) {
                    return nums[mid];
                }
                r = mid - 2;
            } else {
                if(nums[mid] == nums[mid + 1]) {
                    if(mid % 2 == 0) {
                        l = mid + 2;
                    } else {
                        r = mid - 1;
                    }
                } else if(nums[mid] == nums[mid - 1]) {
                    if((mid - 1) % 2 == 0) {
                        l = mid + 1;
                    } else {
                        r = mid - 2;
                    }
                } else {
                    return nums[mid];
                }
            }
        }
        return 0;
    }
};
```



---



### 题目

给定一个只包含整数的有序数组 `nums` ，每个元素都会出现两次，唯有一个数只会出现一次，请找出这个唯一的数字。

你设计的解决方案必须满足 `O(log n)` 时间复杂度和 `O(1)` 空间复杂度。

 

**示例 1:**

```
输入: nums = [1,1,2,3,3,4,4,8,8]
输出: 2
```

**示例 2:**

```
输入: nums =  [3,3,7,7,10,11,11]
输出: 10
```



**提示:**

- `1 <= nums.length <= 10^5`
- `0 <= nums[i] <= 10^5`

 

注意：本题与 540 题[540. 有序数组中的单一元素](https://leetcode-cn.com/problems/single-element-in-a-sorted-array/)相同


