## 剑指 Offer II 022. 链表中环的入口节点

LeetCode：[剑指 Offer II 022. 链表中环的入口节点](https://leetcode.cn/problems/c32eOV/)，难度：中等。

### 题解

#### 代码

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        unordered_set<ListNode*> st;

        while(head != nullptr) {
            if(st.count(head)) {
                return head;
            }
            st.insert(head);
            head = head -> next;
        }
        return nullptr;
    }
};
```



---



### 题目

给定一个链表，返回链表开始入环的第一个节点。 从链表的头节点开始沿着 `next` 指针进入环的第一个节点为环的入口节点。如果链表无环，则返回 `null`。

为了表示给定链表中的环，我们使用整数 `pos` 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 `pos` 是 `-1`，则在该链表中没有环。**注意，`pos` 仅仅是用于标识环的情况，并不会作为参数传递到函数中。**

**说明：**不允许修改给定的链表。



 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII022-circularlinkedlist.png)

```
输入：head = [3,2,0,-4], pos = 1
输出：返回索引为 1 的链表节点
解释：链表中有一个环，其尾部连接到第二个节点。
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII022-circularlinkedlist_test2.png)

```
输入：head = [1,2], pos = 0
输出：返回索引为 0 的链表节点
解释：链表中有一个环，其尾部连接到第一个节点。
```

**示例 3：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII022-circularlinkedlist_test3.png)

```
输入：head = [1], pos = -1
输出：返回 null
解释：链表中没有环。
```

 

**提示：**

- 链表中节点的数目范围在范围 `[0, 10^4]` 内
- `-10^5 <= Node.val <= 10^5`
- `pos` 的值为 `-1` 或者链表中的一个有效索引

 

**进阶：**是否可以使用 `O(1)` 空间解决此题？

 

注意：本题与 142 题[142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)相同


