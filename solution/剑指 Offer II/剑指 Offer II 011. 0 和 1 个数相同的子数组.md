## 剑指 Offer II 011. 0 和 1 个数相同的子数组

LeetCode：[剑指 Offer II 011. 0 和 1 个数相同的子数组](https://leetcode.cn/problems/A1NYOS/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int findMaxLength(vector<int>& nums) {
        unordered_map<int, int> bk;

        bk[0] = -1;
        int now = 0, res = 0;
        for(int i = 0; i < nums.size(); i++) {
            now += nums[i] == 0 ? -1 : 1;
            if(bk.count(now)) {
                res = max(res, i - bk[now]);
            } else {
                bk[now] = i;
            }
        }
        return res;
    }
};
```



---



### 题目

给定一个二进制数组 `nums` , 找到含有相同数量的 `0` 和 `1` 的最长连续子数组，并返回该子数组的长度。

 

**示例 1：**

```
输入: nums = [0,1]
输出: 2
说明: [0, 1] 是具有相同数量 0 和 1 的最长连续子数组。
```

**示例 2：**

```
输入: nums = [0,1,0]
输出: 2
说明: [0, 1] (或 [1, 0]) 是具有相同数量 0 和 1 的最长连续子数组。
```

 

**提示：**

- `1 <= nums.length <= 10^5`
- `nums[i]` 不是 `0` 就是 `1`

 

注意：本题与 525 题[525. 连续数组](https://leetcode-cn.com/problems/contiguous-array/)相同


