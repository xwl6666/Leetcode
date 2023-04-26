## 剑指 Offer II 024. 反转链表

LeetCode：[剑指 Offer II 024. 反转链表](https://leetcode.cn/problems/UHnkqh/)，难度：简单。

### 题解

#### 代码

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
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

给定单链表的头节点 `head` ，请反转链表，并返回反转后的链表的头节点。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII024-rev1ex1.jpg)

```
输入：head = [1,2,3,4,5]
输出：[5,4,3,2,1]
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII024-rev1ex2.jpg)

```
输入：head = [1,2]
输出：[2,1]
```

**示例 3：**

```
输入：head = []
输出：[]
```

 

**提示：**

- 链表中节点的数目范围是 `[0, 5000]`
- `-5000 <= Node.val <= 5000`

 

**进阶：**链表可以选用迭代或递归方式完成反转。你能否用两种方法解决这道题？

 

注意：本题与 206 题[206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)相同


