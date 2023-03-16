## 剑指 Offer 26. 树的子结构

LeetCode：[剑指 Offer 26. 树的子结构](https://leetcode.cn/problems/shu-de-zi-jie-gou-lcof/)，难度：中等。

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

    bool same(TreeNode* A, TreeNode* B) {
        if(B == nullptr) {
            return true;
        }
        if(A == nullptr || A -> val != B -> val) {
            return false;
        }
        return same(A -> left, B -> left) && same(A -> right, B -> right);
    }

    bool isSubStructure(TreeNode* A, TreeNode* B) {
        if(B == nullptr || A == nullptr) {
            return false;
        }
        return same(A, B) || isSubStructure(A -> left, B) || isSubStructure(A -> right, B);
    }
    
};
```



---



### 题目

输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。

例如:
给定的树 A:

```bash
	 3   
	/ \   
	4  5  
   / \ 
  1  2
```


给定的树 B：

```bash
  4  
 / 
1
```


返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。

**示例 1：**

```
输入：A = [1,2,3], B = [3,1]
输出：false
```

**示例 2：**

```
输入：A = [3,4,5,1,2], B = [4,1]
输出：true
```

**限制：**

```
0 <= 节点个数 <= 10000
```


