## 剑指 Offer 11. 旋转数组的最小数字

LeetCode：[剑指 Offer 11. 旋转数组的最小数字](https://leetcode.cn/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    int minArray(vector<int>& nums) {
        int len = (int)nums.size();
        if(len == 1 || (int)nums.back() > (int)nums.front()) {
            return nums.front();
        }

        int l = 0, r = len - 1, mid;
        while(l < r) {
            mid = (l + r) >> 1;
            if(nums[mid] < nums[r]) {
                r = mid;
            } else if(nums[mid] > nums[r]) {
                l = mid + 1;
            } else {
                r --;
            }
        }

        return nums[l];
    }
};
```



---



### 题目

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。

给你一个可能存在 **重复** 元素值的数组 `numbers` ，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的**最小元素**。例如，数组 `[3,4,5,1,2]` 为 `[1,2,3,4,5]` 的一次旋转，该数组的最小值为 1。 

注意，数组 `[a[0], a[1], a[2], ..., a[n-1]]` 旋转一次 的结果为数组 `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]` 。

 

**示例 1：**

```
输入：numbers = [3,4,5,1,2]
输出：1
```

**示例 2：**

```
输入：numbers = [2,2,2,0,1]
输出：0
```

 

**提示：**

- `n == numbers.length`
- `1 <= n <= 5000`
- `-5000 <= numbers[i] <= 5000`
- `numbers` 原来是一个升序排序的数组，并进行了 `1` 至 `n` 次旋转

注意：本题与 154 题[154. 寻找旋转排序数组中的最小值 II](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array-ii/)相同


