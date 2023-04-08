## 剑指 Offer 57 - II. 和为s的连续正数序列

LeetCode：[剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode.cn/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<vector<int>> findContinuousSequence(int target) {
        vector< vector<int> > res;
        unordered_set<int> st;
        vector<int> temp;

        target <<= 1;
        for(int i = 1, s1, s2, a, b; i * i <= target; i++) {
            if(target % i == 0) {
                s1 = i, s2 = target / i;
                if((s1 + s2) % 2 == 0) {
                    continue;
                }

                b = (s1 + s2 - 1) / 2, a = s1 - b;
                if(a > b) {
                    swap(a, b);
                }
                if(a > 0 && a != b) {
                    if(!st.count(a)) {
                        st.insert(a);
                        temp = {a};
                        for(int j = a + 1; j <= b; j++) {
                            temp.push_back(j);
                        }
                        res.push_back(temp);
                    }
                }


                s1 = target / i, s2 = i;
                b = (s1 + s2 - 1) / 2, a = s1 - b;
                if(a > b) {
                    swap(a, b);
                }
                if(a > 0 && a != b) {
                    if(!st.count(a)) {
                        st.insert(a);
                        temp = {a};
                        for(int j = a + 1; j <= b; j++) {
                            temp.push_back(j);
                        }
                        res.push_back(temp);
                    }
                }
            }
        }

        sort(res.begin(), res.end(), [](const vector<int> &a, const vector<int> &b) {
            return a[0] < b[0];
        });

        return res;
    }
};
```



---



### 题目

输入一个正整数 `target` ，输出所有和为 `target` 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

 

**示例 1：**

```
输入：target = 9
输出：[[2,3,4],[4,5]]
```

**示例 2：**

```
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

 

**限制：**

- `1 <= target <= 10^5`

 