## 剑指 Offer II 007. 数组中和为 0 的三个数

LeetCode：[剑指 Offer II 007. 数组中和为 0 的三个数](https://leetcode.cn/problems/1fGaJU/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int len = (int)nums.size();
        
        vector< vector<int> > res;
        vector<int> temp;
        for(int i = 0, l, r, now; i < len; i++) {
            if(nums[i] > 0) {
                continue;
            }
            if(i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            l = i + 1, r = len - 1;
            while(l < r) {
                now = nums[i] + nums[l] + nums[r];
                if(now > 0) {
                    r --;
                } else if(now < 0) {
                    l ++;
                } else {
                    temp = {nums[i], nums[l], nums[r]};
                    if(res.empty() || temp != res.back()) {
                        res.push_back(temp);
                    }
                    l ++;
                    r --;
                }
            }
        }

        return res;
    }
};
```



---



### 题目

给你一个整数数组 `nums` ，判断是否存在三元组 `[nums[i], nums[j], nums[k]]` 满足 `i != j`、`i != k` 且 `j != k` ，同时还满足 `nums[i] + nums[j] + nums[k] == 0` 。请

你返回所有和为 `0` 且不重复的三元组。

**注意：**答案中不可以包含重复的三元组。

 

 

**示例 1：**

```
输入：nums = [-1,0,1,2,-1,-4]
输出：[[-1,-1,2],[-1,0,1]]
解释：
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0 。
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0 。
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0 。
不同的三元组是 [-1,0,1] 和 [-1,-1,2] 。
注意，输出的顺序和三元组的顺序并不重要。
```

**示例 2：**

```
输入：nums = [0,1,1]
输出：[]
解释：唯一可能的三元组和不为 0 。
```

**示例 3：**

```
输入：nums = [0,0,0]
输出：[[0,0,0]]
解释：唯一可能的三元组和为 0 。
```

 

**提示：**

- `3 <= nums.length <= 3000`
- `-10^5 <= nums[i] <= 10^5`

 

注意：本题与 15 题[15. 三数之和](https://leetcode.cn/problems/3sum/)相同


