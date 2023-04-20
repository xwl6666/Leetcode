## 剑指 Offer II 004. 只出现一次的数字 

LeetCode：[剑指 Offer II 004. 只出现一次的数字 ](https://leetcode.cn/problems/WGki4K/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int res = 0;
        for(int i = 0, s; i < 32; i++) {
            s = 0;
            for(int j : nums) {
                s += j >> i & 1;
            }
            if(s % 3 == 1) {
                res += 1 << i;
            }
        }
        return res;
    }
};
```



---



### 题目

给你一个整数数组 `nums` ，除某个元素仅出现 **一次** 外，其余每个元素都恰出现 **三次 。**请你找出并返回那个只出现了一次的元素。

 

**示例 1：**

```
输入：nums = [2,2,3,2]
输出：3
```

**示例 2：**

```
输入：nums = [0,1,0,1,0,1,100]
输出：100
```

 

**提示：**

- `1 <= nums.length <= 3 * 10^4`
- `-2^31 <= nums[i] <= 2^31 - 1`
- `nums` 中，除某个元素仅出现 **一次** 外，其余每个元素都恰出现 **三次**

 

**进阶：**你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

 

注意：本题与 137 题[137. 只出现一次的数字 II](https://leetcode-cn.com/problems/single-number-ii/)相同


