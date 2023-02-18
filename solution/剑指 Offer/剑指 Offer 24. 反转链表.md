## 剑指 Offer 24. 反转链表

LeetCode：[剑指 Offer 24. 反转链表](https://leetcode.cn/problems/fan-zhuan-lian-biao-lcof/)，难度：简单。

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
    ListNode* reverseList(ListNode* head) {
        ListNode *idx = new ListNode(-1), *p;

        while(head != nullptr) {
            p = head -> next;
            head -> next = idx -> next;
            idx -> next = head;
            head = p;
        }

        return idx -> next;
    }
};
```



---



### 题目

定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

 

**示例:**

```
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

 

**限制：**

```
0 <= 节点个数 <= 5000
```

 

**注意**：本题与 206 题[206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/)相同

