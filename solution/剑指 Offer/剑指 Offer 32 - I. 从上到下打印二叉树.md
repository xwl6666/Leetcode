## 剑指 Offer 32 - I. 从上到下打印二叉树

LeetCode：[剑指 Offer 32 - I. 从上到下打印二叉树](https://leetcode.cn/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)，难度：中等。

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

    vector<int> levelOrder(TreeNode* root) {
        if(root == nullptr) {
            return {};
        }
        vector<int> v;

        queue<TreeNode*> q;
        q.push(root);
        v.push_back(root -> val);
        
        TreeNode* now;
        while(!q.empty()) {
            now = q.front(), q.pop();

            if(now -> left != nullptr) {
                q.push(now -> left);
                v.push_back(now -> left -> val);
            }
            if(now -> right != nullptr) {
                q.push(now -> right);
                v.push_back(now -> right -> val);
            }
        }

        return v;
    }
};
```



---



### 题目

从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

 

例如:
给定二叉树: `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

返回：

```
[3,9,20,15,7]
```

 

**提示：**

1. `节点总数 <= 1000`


