## 剑指 Offer II 044. 二叉树每层的最大值

LeetCode：[剑指 Offer II 044. 二叉树每层的最大值](https://leetcode.cn/problems/hPov7L/)，难度：中等。

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

    int mx;
    vector<int> res;

    void dfs(TreeNode* root, int cur) {
        int to = cur + 1;
        if(to > mx) {
            mx = to;
        }

        res[cur] = max(res[cur], root -> val);
        if(root -> left) {
            dfs(root -> left, to);
        }
        if(root -> right) {
            dfs(root -> right, to);
        }
    }

    vector<int> largestValues(TreeNode* root) {
        if(root == nullptr) {
            return {};
        }
        mx = 0;
        res.resize(100000, INT_MIN);
        dfs(root, 0);
        res.resize(mx);
        return res;
    }
};
```



---



### 题目

给定一棵二叉树的根节点 `root` ，请找出该二叉树中每一层的最大值。

 

**示例1：**

```
输入: root = [1,3,2,5,3,null,9]
输出: [1,3,9]
解释:
          1
         / \
        3   2
       / \   \  
      5   3   9 
```

**示例2：**

```
输入: root = [1,2,3]
输出: [1,3]
解释:
          1
         / \
        2   3
```

**示例3：**

```
输入: root = [1]
输出: [1]
```

**示例4：**

```
输入: root = [1,null,2]
输出: [1,2]
解释:      
           1 
            \
             2     
```

**示例5：**

```
输入: root = []
输出: []
```

 

**提示：**

- 二叉树的节点个数的范围是 `[0,10^4]`
- `-2^31 <= Node.val <= 2^31 - 1`

 

注意：本题与 515 题[515. 在每个树行中找最大值](https://leetcode-cn.com/problems/find-largest-value-in-each-tree-row/)相同


