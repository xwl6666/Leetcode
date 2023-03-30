## 剑指 Offer 39. 数组中出现次数超过一半的数字

LeetCode：[剑指 Offer 39. 数组中出现次数超过一半的数字](https://leetcode.cn/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int num, cnt = 0;
        for(int i : nums) {
            if(cnt == 0) {
                num = i;
                cnt ++;
            } else {
                if(num == i) {
                    cnt ++;
                } else {
                    cnt --;
                }
            }
        }
        return num;
    }
};
```



---



### 题目

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

 

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

 

**示例 1:**

```
输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2
```

 

**限制：**

```
1 <= 数组长度 <= 50000
```

 

注意：本题与 169 题[169. 多数元素](https://leetcode-cn.com/problems/majority-element/)相同


