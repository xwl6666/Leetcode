## 剑指 Offer 28. 对称的二叉树

LeetCode：[剑指 Offer 28. 对称的二叉树](https://leetcode.cn/problems/dui-cheng-de-er-cha-shu-lcof/)，难度：简单。

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

    bool dfs(TreeNode* p, TreeNode* q) {
        bool f1 = p == nullptr, f2 = q == nullptr;
        if(f1 && f2) {
            return true;
        }
        if(f1 || f2) {
            return false;
        }
        if(p -> val != q -> val) {
            return false;
        }
        return dfs(p -> left, q -> right) && dfs(p -> right, q -> left);
    }

    bool isSymmetric(TreeNode* root) {
        if(root == nullptr) {
            return true;
        }
        return dfs(root, root);
    }
    
};
```



---



### 题目

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

```
    1   
   / \  
  2   2   
 / \ / \   
3  4 4  3
```

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

```
   1   
  / \  
  2  2   
   \  \   
    3   3
```

 

**示例 1：**

```
输入：root = [1,2,2,3,4,4,3]
输出：true
```

**示例 2：**

```
输入：root = [1,2,2,null,3,null,3]
输出：false
```

 

**限制：**

```
0 <= 节点个数 <= 1000
```

注意：本题与主站 101 题[101. 对称二叉树](https://leetcode.cn/problems/symmetric-tree/)相同


