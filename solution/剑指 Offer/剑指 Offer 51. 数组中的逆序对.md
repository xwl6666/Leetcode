## 剑指 Offer 51. 数组中的逆序对

LeetCode：[剑指 Offer 51. 数组中的逆序对](https://leetcode.cn/problems/shu-zu-zhong-de-ni-xu-dui-lcof/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:
    int res;

    void merge(vector<int> &nums, int left, int mid, int right, vector<int> &temp) {
        for(int i = left; i <= right; i++) {
            temp[i] = nums[i];
        }
        int headL = left, headR = mid + 1;
        int head = left;

        while(headL <= mid && headR <= right) {
            if(temp[headL] <= temp[headR]) {
                nums[head ++] = temp[headL ++];
            } else {
                // 只在右指针移动时计算贡献度，贡献度为左数组里左指针以后的元素个数
                res += mid - headL + 1;
                nums[head ++] = temp[headR ++];
            }
        }

        while(headL <= mid) {
            nums[head ++] = temp[headL ++];
        }
        while(headR <= right) {
            nums[head ++] = temp[headR ++];
        }
    }

    void mergeSort(vector<int> &nums, int left, int right, vector<int> &temp) {
        if(left >= right) {
            return ;
        }
        int mid = left + right >> 1;
        mergeSort(nums, left, mid, temp);
        mergeSort(nums, mid + 1, right, temp);
        merge(nums, left, mid, right, temp);
    }

    int reversePairs(vector<int>& nums) {
        vector<int> temp((int)nums.size());
        res = 0;
        mergeSort(nums, 0, nums.size() - 1, temp);
        return res;
    }
};
```



---



### 题目

在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。

 

**示例 1:**

```
输入: [7,5,6,4]
输出: 5
```

 

**限制：**

```
0 <= 数组长度 <= 50000
```


