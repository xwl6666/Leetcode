## 剑指 Offer 45. 把数组排成最小的数

LeetCode：[剑指 Offer 45. 把数组排成最小的数](https://leetcode.cn/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    string minNumber(vector<int>& nums) {
        vector<string> v;
        for(int i : nums) {
            v.push_back(to_string(i));
        }
        sort(v.begin(), v.end(), [](const string &a, const string &b) {
            return a + b < b + a;
        });

        string res = "";
        for(string s : v) {
            res += s;
        }
        return res;
    }
};
```



---



### 题目

输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

 

**示例 1:**

```
输入: [10,2]
输出: "102"
```

**示例 2:**

```
输入: [3,30,34,5,9]
输出: "3033459"
```

 

**提示:**

- `0 < nums.length <= 100`

**说明:**

- 输出结果可能非常大，所以你需要返回一个字符串而不是整数
- 拼接起来的数字可能会有前导 0，最后结果不需要去掉前导 0


