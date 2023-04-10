## 剑指 Offer 59 - I. 滑动窗口的最大值

LeetCode：[剑指 Offer 59 - I. 滑动窗口的最大值](https://leetcode.cn/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        multiset<int> st;
        for(int i = 0; i < k; i++) {
            st.insert(nums[i]);
        }
        vector<int> res = {*st.rbegin()};
        for(int i = k; i < nums.size(); i++) {
            st.insert(nums[i]);
            st.erase(st.find(nums[i - k]));
            res.push_back(*st.rbegin());
        }
        return res;
    }
};
```



---



### 题目

给定一个数组 `nums` 和滑动窗口的大小 `k`，请找出所有滑动窗口里的最大值。

**示例:**

```
输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

 

**提示：**

你可以假设 *k* 总是有效的，在输入数组 **不为空** 的情况下，`1 ≤ k ≤ nums.length`。

注意：本题与 239 题[239. 滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum/)相同


