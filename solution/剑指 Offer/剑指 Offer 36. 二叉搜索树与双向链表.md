## 剑指 Offer 36. 二叉搜索树与双向链表

LeetCode：[剑指 Offer 36. 二叉搜索树与双向链表](https://leetcode.cn/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)，难度：中等。

### 题解

#### 代码

```c++
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;

    Node() {}

    Node(int _val) {
        val = _val;
        left = NULL;
        right = NULL;
    }

    Node(int _val, Node* _left, Node* _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/
class Solution {
public:

    vector<Node*> v;

    void dfs(Node* root) {
        if(root -> left != nullptr) {
            dfs(root -> left);
        }
        v.push_back(root);
        if(root -> right != nullptr) {
            dfs(root -> right);
        }
    }

    Node* treeToDoublyList(Node* root) {
        if(root == nullptr) {
            return nullptr;
        }

        dfs(root);
        int len = (int)v.size();

        for(int i = 0; i < len - 1; i++) {
            v[i] -> right = v[i + 1];
        }
        v[len - 1] -> right = v[0];

        for(int i = 1; i < len; i++) {
            v[i] -> left = v[i - 1];
        }
        v[0] -> left = v[len - 1];

        return v[0];
    }
};
```



---



### 题目

输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。

 

为了让您更好地理解问题，以下面的二叉搜索树为例：

 

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOffer36-bstdlloriginalbst.png)

 

我们希望将这个二叉搜索树转化为双向循环链表。链表中的每个节点都有一个前驱和后继指针。对于双向循环链表，第一个节点的前驱是最后一个节点，最后一个节点的后继是第一个节点。

下图展示了上面的二叉搜索树转化成的链表。“head” 表示指向链表中有最小元素的节点。

 

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOffer36-bstdllreturndll.png)

 

特别地，我们希望可以就地完成转换操作。当转化完成以后，树中节点的左指针需要指向前驱，树中节点的右指针需要指向后继。还需要返回链表中的第一个节点的指针。

 

**注意：**本题与 [426 题](https://leetcode-cn.com/problems/convert-binary-search-tree-to-sorted-doubly-linked-list/) 相同：

**注意：**此题对比原题有改动。


