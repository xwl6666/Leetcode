## 剑指 Offer II 084. 含有重复元素集合的全排列

LeetCode：[剑指 Offer II 084. 含有重复元素集合的全排列](https://leetcode.cn/problems/7p8L0Z/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector< vector<int> > res;
        do {
            if(res.empty() || nums != res.back()) {
                res.push_back(nums);
            }
        } while (next_permutation(nums.begin(), nums.end()));
        return res;
    }
};
```



---



### 题目

给定一个可包含重复数字的整数集合 `nums` ，**按任意顺序** 返回它所有不重复的全排列。

 

**示例 1：**

```
输入：nums = [1,1,2]
输出：
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

**示例 2：**

```
输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

 

**提示：**

- `1 <= nums.length <= 8`
- `-10 <= nums[i] <= 10`

 

注意：本题与 47 题[47. 全排列 II](https://leetcode-cn.com/problems/permutations-ii/)相同


