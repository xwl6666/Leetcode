## 剑指 Offer 34. 二叉树中和为某一值的路径

LeetCode：[剑指 Offer 34. 二叉树中和为某一值的路径](https://leetcode.cn/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)，难度：中等。

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

    vector< vector<int> > res;

    vector<int> v;
    int target;

    void dfs(TreeNode* cur, int sum) {
        if(sum == target && cur -> left == nullptr && cur -> right == nullptr) {
            res.push_back(v);
            return ;
        }

        if(cur -> left != nullptr) {
            v.push_back(cur -> left -> val);
            dfs(cur -> left, sum + cur -> left -> val);
            v.pop_back();
        }
        if(cur -> right != nullptr) {
            v.push_back(cur -> right -> val);
            dfs(cur -> right, sum + cur -> right -> val);
            v.pop_back();
        }
    }

    vector<vector<int>> pathSum(TreeNode* root, int target) {
        if(root == nullptr) {
            return {};
        }
        this -> target = target;

        v.push_back(root -> val);
        dfs(root, root -> val);

        return res;
    }
};
```



---



### 题目

给你二叉树的根节点 `root` 和一个整数目标和 `targetSum` ，找出所有 **从根节点到叶子节点** 路径总和等于给定目标和的路径。

**叶子节点** 是指没有子节点的节点。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOffer34-pathsumii1.jpg)

```
输入：root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
输出：[[5,4,11,2],[5,8,4,5]]
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOffer34-pathsum2.jpg)

```
输入：root = [1,2,3], targetSum = 5
输出：[]
```

**示例 3：**

```
输入：root = [1,2], targetSum = 0
输出：[]
```

 

**提示：**

- 树中节点总数在范围 `[0, 5000]` 内
- `-1000 <= Node.val <= 1000`
- `-1000 <= targetSum <= 1000`

注意：本题与 113 题[113. 路径总和 II](https://leetcode.cn/problems/path-sum-ii/)相同


