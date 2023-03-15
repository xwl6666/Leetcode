## 剑指 Offer 32 - II. 从上到下打印二叉树 II

LeetCode：[剑指 Offer 32 - II. 从上到下打印二叉树 II](https://leetcode.cn/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)，难度：简单。

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

        int cnt;
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
            res.push_back(temp);
            temp.clear();
        }

        return res;
    }
};
```



---



### 题目

从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

 

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
  [9,20],
  [15,7]
]
```

 

**提示：**

1. `节点总数 <= 1000`

注意：本题与 102 题[102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)相同


