## 剑指 Offer II 053. 二叉搜索树中的中序后继

LeetCode：[剑指 Offer II 053. 二叉搜索树中的中序后继](https://leetcode.cn/problems/P5rCT8/)，难度：中等。

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

    TreeNode *p, *pre, *res;

    void dfs(TreeNode* root) {
        if(root == nullptr || res != nullptr) {
            return ;
        }
        if(root -> left) {
            dfs(root -> left);
        }
        if(pre == p) {
            res = root;
        }
        pre = root;
        if(root -> right) {
            dfs(root -> right);
        }
    }

    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        this -> p = p;
        res = nullptr;
        dfs(root);
        return res;
    }
};
```



---



### 题目

给定一棵二叉搜索树和其中的一个节点 `p` ，找到该节点在树中的中序后继。如果节点没有中序后继，请返回 `null` 。

节点 `p` 的后继是值比 `p.val` 大的节点中键值最小的节点，即按中序遍历的顺序节点 `p` 的下一个节点。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII053-285_example_1.PNG)

```
输入：root = [2,1,3], p = 1
输出：2
解释：这里 1 的中序后继是 2。请注意 p 和返回值都应是 TreeNode 类型。
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII053-285_example_2.PNG)

```
输入：root = [5,3,6,2,4,null,null,1], p = 6
输出：null
解释：因为给出的节点没有中序后继，所以答案就返回 null 了。
```

 

**提示：**

- 树中节点的数目在范围 `[1, 10^4]` 内。
- `-10^5 <= Node.val <= 10^5`
- 树中各节点的值均保证唯一。

 

注意：本题与 285 题[285. 二叉搜索树中的中序后继](https://leetcode-cn.com/problems/inorder-successor-in-bst/)相同


