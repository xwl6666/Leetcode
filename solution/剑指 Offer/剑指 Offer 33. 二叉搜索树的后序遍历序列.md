## 剑指 Offer 33. 二叉搜索树的后序遍历序列

LeetCode：[剑指 Offer 33. 二叉搜索树的后序遍历序列](https://leetcode.cn/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<int> v;

    bool judge(int l, int r) {
        if(l >= r) {
            return true;
        }

        int cur = v[r], idx = -1;
        for(int i = l; i < r; i++) {
            if(v[i] <= cur) {
                continue;
            } else {
                idx = i;
                break;
            }
        }
        if(idx != -1) {
            for(int i = idx + 1; i < r; i++) {
                if(v[i] <= cur) {
                    return false;
                }
            }
            return judge(l, idx - 1) && judge(idx, r - 1);
        } else {
            return judge(l, r - 1);
        }
    }

    bool verifyPostorder(vector<int>& postorder) {
        v = postorder;
        return judge(0, (int)postorder.size() - 1);
    }
};
```



---



### 题目

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 `true`，否则返回 `false`。假设输入的数组的任意两个数字都互不相同。

 

参考以下这颗二叉搜索树：

```
     5
    / \
   2   6
  / \
 1   3
```

**示例 1：**

```
输入: [1,6,3,2,5]
输出: false
```

**示例 2：**

```
输入: [1,3,2,6,5]
输出: true
```

 

**提示：**

1. `数组长度 <= 1000`


