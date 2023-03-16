## 剑指 Offer 25. 合并两个排序的链表

LeetCode：[剑指 Offer 25. 合并两个排序的链表](https://leetcode.cn/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)，难度：简单。

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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* head = new ListNode(-1);

        ListNode* temp = head;
        while(l1 != nullptr && l2 != nullptr) {
            if(l1 -> val <= l2 -> val) {
                temp -> next = l1;
                l1 = l1 -> next;
            } else if(l1 -> val > l2 -> val) {
                temp -> next = l2;
                l2 = l2 -> next;
            }
            temp = temp -> next;
        }

        if(l1 != nullptr) {
            temp -> next = l1;
        }
        if(l2 != nullptr) {
            temp -> next = l2;
        }

        return head -> next;
    }
};
```



---



### 题目

输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

**示例1：**

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

**限制：**

```
0 <= 链表长度 <= 1000
```

注意：本题与 21 题[21. 合并两个有序链表](https://leetcode.cn/problems/merge-two-sorted-lists/)相同


