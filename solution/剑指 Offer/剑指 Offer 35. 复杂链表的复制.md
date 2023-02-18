## 剑指 Offer 35. 复杂链表的复制

LeetCode：[剑指 Offer 35. 复杂链表的复制](https://leetcode.cn/problems/fu-za-lian-biao-de-fu-zhi-lcof/)，难度：中等。

### 题解

#### 代码

```c++
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/
class Solution {
public:

    map<Node*, Node*> bk;

    Node* copyRandomList(Node* head) {
        if(head == nullptr) {
            return nullptr;
        }
        if(!bk.count(head)) {
            Node* now = new Node(head -> val);
            bk[head] = now;
            now -> next = copyRandomList(head -> next);
            now -> random = copyRandomList(head -> random);
        }
        return bk[head];
    }
    
};
```



---



### 题目

请实现 `copyRandomList` 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 `next` 指针指向下一个节点，还有一个 `random` 指针指向链表中的任意节点或者 `null`。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianzhi Offer 35-e1.png)

```
输入：head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
输出：[[7,null],[13,0],[11,4],[10,2],[1,0]]
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianzhi Offer 35-e2.png)

```
输入：head = [[1,1],[2,1]]
输出：[[1,1],[2,1]]
```

**示例 3：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianzhi Offer 35-e3.png)

```
输入：head = [[3,null],[3,0],[3,null]]
输出：[[3,null],[3,0],[3,null]]
```

**示例 4：**

```
输入：head = []
输出：[]
解释：给定的链表为空（空指针），因此返回 null。
```

 

**提示：**

- `-10000 <= Node.val <= 10000`
- `Node.random` 为空（null）或指向链表中的节点。
- 节点数目不超过 1000 。

 

**注意：**本题与 138 题[138. 复制带随机指针的链表](https://leetcode.cn/problems/copy-list-with-random-pointer/)相同

