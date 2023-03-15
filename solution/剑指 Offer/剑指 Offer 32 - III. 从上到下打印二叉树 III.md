## 剑指 Offer 32 - III. 从上到下打印二叉树 III

LeetCode：[剑指 Offer 32 - III. 从上到下打印二叉树 III](https://leetcode.cn/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)，难度：中等。

### 题解

#### 代码

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(root == nullptr) {
            return {};
        }

        vector< vector<int> > res;

        queue<TreeNode*> q;
        q.push(root);

        int cnt, cur = 0;
        vector<int> temp;
        TreeNode* now;
        while(!q.empty()) {
            cnt = (int)q.size();
            
            for(int i = 0; i < cnt; i++) {
                now = q.front(), q.pop();
                temp.push_back(now -> val);
                if(now -> left != nullptr) {
                    q.push(now -> left);
                }
                if(now -> right != nullptr) {
                    q.push(now -> right);
                }
            }
            if(cur & 1) {
                reverse(temp.begin(), temp.end());
            }
            cur ++;
            res.push_back(temp);
            temp.clear();
        }

        return res;
    }
};
```



---



### 题目

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

 

例如:
给定二叉树: `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```
[
  [3],
  [20,9],
  [15,7]
]
```

 

**提示：**

1. `节点总数 <= 1000`


