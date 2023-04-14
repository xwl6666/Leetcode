## 剑指 Offer 37. 序列化二叉树

LeetCode：[剑指 Offer 37. 序列化二叉树](https://leetcode.cn/problems/xu-lie-hua-er-cha-shu-lcof/)，难度：困难。

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
class Codec {
public:

    void enc(TreeNode* root, string& res) {
        if (root == nullptr) {
            res += "nullptr,";
        } else {
            res += to_string(root->val) + ",";
            enc(root -> left, res);
            enc(root -> right, res);
        }
    }

    TreeNode* dec(list<string>& array) {
        if (array.front() == "nullptr") {
            array.erase(array.begin());
            return nullptr;
        }

        TreeNode* root = new TreeNode(stoi(array.front()));
        array.erase(array.begin());
        root -> left = dec(array);
        root -> right = dec(array);
        return root;
    }

    // Encodes a tree to a single string.
    string serialize(TreeNode* root) {
        string res;
        enc(root, res);
        return res;
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        list<string> array;
        string str;
        for (int i : data) {
            if (i == ',') {
                array.push_back(str);
                str.clear();
            } else {
                str.push_back(i);
            }
        }
        if (!str.empty()) {
            array.push_back(str);
            str.clear();
        }
        return dec(array);
    }
};

// Your Codec object will be instantiated and called as such:
// Codec codec;
// codec.deserialize(codec.serialize(root));
```



---



### 题目

请实现两个函数，分别用来序列化和反序列化二叉树。

你需要设计一个算法来实现二叉树的序列化与反序列化。这里不限定你的序列 / 反序列化算法执行逻辑，你只需要保证一个二叉树可以被序列化为一个字符串并且将这个字符串反序列化为原始的树结构。

**提示：**输入输出格式与 LeetCode 目前使用的方式一致，详情请参阅 [LeetCode 序列化二叉树的格式](https://support.leetcode-cn.com/hc/kb/article/1567641/)。你并非必须采取这种方式，你也可以采用其他的方法解决这个问题。

 

**示例：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOffer37-serdeser.jpg)

```
输入：root = [1,2,3,null,null,4,5]
输出：[1,2,3,null,null,4,5]
```

 

注意：本题与 297 题[297. 二叉树的序列化与反序列化](https://leetcode-cn.com/problems/serialize-and-deserialize-binary-tree/)相同：


