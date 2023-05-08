## 剑指 Offer II 056. 二叉搜索树中两个节点之和

LeetCode：[剑指 Offer II 056. 二叉搜索树中两个节点之和](https://leetcode.cn/problems/opLdQZ/)，难度：简单。

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

    unordered_set<int> s;

    bool findTarget(TreeNode* root, int k) {
        if(root == nullptr) {
            return false;
        }
        if(s.count(k - root -> val)) {
            return true;
        }
        s.insert(root -> val);
        return findTarget(root -> left, k) || findTarget(root -> right, k);
    }
};
```



---



### 题目

给定一个二叉搜索树的 **根节点** `root` 和一个整数 `k` , 请判断该二叉搜索树中是否存在两个节点它们的值之和等于 `k` 。假设二叉搜索树中节点的值均唯一。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII056-sum_tree_1.jpg)

```
输入: root = [8,6,10,5,7,9,11], k = 12
输出: true
解释: 节点 5 和节点 7 之和等于 12
```

**示例 2：**

```
输入: root = [8,6,10,5,7,9,11], k = 22
输出: false
解释: 不存在两个节点值之和为 22 的节点
```

 

**提示：**

- 二叉树的节点个数的范围是 `[1, 10^4]`.
- `-10^4 <= Node.val <= 10^4`
- `root` 为二叉搜索树
- `-10^5 <= k <= 10^5`

 

注意：本题与 653 题[653. 两数之和 IV - 输入二叉搜索树](https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst/)相同


