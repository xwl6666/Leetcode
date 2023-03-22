## 剑指 Offer 07. 重建二叉树

LeetCode：[剑指 Offer 07. 重建二叉树](https://leetcode.cn/problems/zhong-jian-er-cha-shu-lcof/)，难度：中等。

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

    vector<int> preorder, inorder;
    unordered_map<int, int> idx;

    TreeNode* build(int l1, int r1, int l2, int r2) {
        if(r1 < l1 || r2 < l2) {
            return nullptr;
        }
        int lLen = idx[preorder[l1]] - l2;
        int rLen = r2 - l2 - lLen;
        return new TreeNode(preorder[l1], 
            build(l1 + 1, l1 + lLen, l2, l2 + lLen - 1),
            build(l1 + lLen + 1, r1, l2 + lLen + 1, r2));
    }

    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        this -> preorder = preorder, this -> inorder = inorder;
        
        int len = (int)inorder.size();
        for(int i = 0; i < len; i++) {
            idx[inorder[i]] = i;
        }

        return build(0, len - 1, 0, len - 1);
    }
};
```



---



### 题目

输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

 

**示例 1:**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOffer07-tree.jpg)

```
Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]
```

**示例 2:**

```
Input: preorder = [-1], inorder = [-1]
Output: [-1]
```

 

**限制：**

```
0 <= 节点个数 <= 5000
```

 

**注意**：本题与 105 题[105. 从前序与中序遍历序列构造二叉树](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)重复


