## 剑指 Offer II 049. 从根节点到叶节点的路径数字之和

LeetCode：[剑指 Offer II 049. 从根节点到叶节点的路径数字之和](https://leetcode.cn/problems/3Etpl5/)，难度：中等。

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

    int res;

    void dfs(TreeNode* root, int sum) {
        if(root -> left == nullptr && root -> right == nullptr) {
            res += sum;
            return ;
        }
        if(root -> left != nullptr) {
            dfs(root -> left, sum * 10 + root -> left -> val);
        }
        if(root -> right != nullptr) {
            dfs(root -> right, sum * 10 + root -> right -> val);
        }
    }

    int sumNumbers(TreeNode* root) {
        res = 0;
        dfs(root, root -> val);
        return res;
    }
};
```



---



### 题目

给定一个二叉树的根节点 `root` ，树中每个节点都存放有一个 `0` 到 `9` 之间的数字。

每条从根节点到叶节点的路径都代表一个数字：

- 例如，从根节点到叶节点的路径 `1 -> 2 -> 3` 表示数字 `123` 。

计算从根节点到叶节点生成的 **所有数字之和** 。

**叶节点** 是指没有子节点的节点。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII049-num1tree.jpg)

```
输入：root = [1,2,3]
输出：25
解释：
从根到叶子节点路径 1->2 代表数字 12
从根到叶子节点路径 1->3 代表数字 13
因此，数字总和 = 12 + 13 = 25
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII049-num2tree.jpg)

```
输入：root = [4,9,0,5,1]
输出：1026
解释：
从根到叶子节点路径 4->9->5 代表数字 495
从根到叶子节点路径 4->9->1 代表数字 491
从根到叶子节点路径 4->0 代表数字 40
因此，数字总和 = 495 + 491 + 40 = 1026
```

 

**提示：**

- 树中节点的数目在范围 `[1, 1000]` 内
- `0 <= Node.val <= 9`
- 树的深度不超过 `10`

 

注意：本题与 129 题[129. 求根节点到叶节点数字之和](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/)相同


