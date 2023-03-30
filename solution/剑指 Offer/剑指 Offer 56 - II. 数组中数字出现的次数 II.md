## 剑指 Offer 56 - II. 数组中数字出现的次数 II

LeetCode：[剑指 Offer 56 - II. 数组中数字出现的次数 II](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        vector<int> bk(32, 0);
        for(int i : nums) {
            for(int j = 0; j < 31; j++) {
                bk[j] += i >> j & 1;
            }
        }

        int res = 0, bas = 1;
        for(int i = 0; i < 31; i++) {
            bk[i] %= 3;
            if(bk[i]) {
                res += bas;
            }
            bas <<= 1;
        }
        return res;
    }
};
```



---



### 题目

在一个数组 `nums` 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。

 

**示例 1：**

```
输入：nums = [3,4,3,3]
输出：4
```

**示例 2：**

```
输入：nums = [9,1,7,9,7,9,7]
输出：1
```

 

**限制：**

- `1 <= nums.length <= 10000`
- `1 <= nums[i] < 2^31`


