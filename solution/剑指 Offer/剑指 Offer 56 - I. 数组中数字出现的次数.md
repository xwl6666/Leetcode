## 剑指 Offer 56 - I. 数组中数字出现的次数

LeetCode：[剑指 Offer 56 - I. 数组中数字出现的次数](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<int> singleNumbers(vector<int>& nums) {
        int s = 0;
        for(int i : nums) {
            s ^= i;
        }
        int idx = -1;
        for(int i = 0; i < 16; i++) {
            if(s >> i & 1) {
                idx = i;
                break;
            }
        }

        int x = 0, y = 0;
        for(int i : nums) {
            if(i >> idx & 1) {
                x ^= i;
            } else {
                y ^= i;
            }
        }
        return {x, y};
    }
};
```



---



### 题目

一个整型数组 `nums` 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

 

**示例 1：**

```
输入：nums = [4,1,4,6]
输出：[1,6] 或 [6,1]
```

**示例 2：**

```
输入：nums = [1,2,10,4,1,4,3,3]
输出：[2,10] 或 [10,2]
```

 

**限制：**

- `2 <= nums.length <= 10000`


