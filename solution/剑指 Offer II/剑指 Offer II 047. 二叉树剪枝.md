## 剑指 Offer II 047. 二叉树剪枝

LeetCode：[剑指 Offer II 047. 二叉树剪枝](https://leetcode.cn/problems/pOCWxh/)，难度：中等。

### 题解

#### 代码

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:

    TreeNode* pruneTree(TreeNode* root) {
        if(root == nullptr) {
            return nullptr;
        }
        root -> left = pruneTree(root -> left);
        root -> right = pruneTree(root -> right);

        if(root -> val == 0 && root -> left == nullptr 
                    && root -> right == nullptr) {
            return nullptr;
        }
        return root;
    }
};
```



---



### 题目

给定一个二叉树 **根节点** `root` ，树的每个节点的值要么是 `0`，要么是 `1`。请剪除该二叉树中所有节点的值为 `0` 的子树。

节点 `node` 的子树为 `node` 本身，以及所有 `node` 的后代。

 

**示例 1:**

```
输入: [1,null,0,0,1]
输出: [1,null,0,null,1] 
解释: 
只有红色节点满足条件“所有不包含 1 的子树”。
右图为返回的答案。
```

<img src="https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII047-1028_2.png" alt="img" style="zoom:80%;" />

**示例 2:**

```
输入: [1,0,1,0,0,0,1]
输出: [1,null,1,null,1]
解释: 
```

<img src="https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII047-1028_1.png" alt="img" style="zoom:80%;" />

**示例 3:**

```
输入: [1,1,0,1,1,0,1,0]
输出: [1,1,0,1,1,null,1]
解释: 
```

 <img src="https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII047-1028.png" alt="img" style="zoom:80%;" />

**提示:**

- 二叉树的节点个数的范围是 `[1,200]`
- 二叉树节点的值只会是 `0` 或 `1`

 

注意：本题与 814 题[814. 二叉树剪枝](https://leetcode-cn.com/problems/binary-tree-pruning/)相同


