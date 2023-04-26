## 剑指 Offer II 027. 回文链表

LeetCode：[剑指 Offer II 027. 回文链表](https://leetcode.cn/problems/aMhZSa/)，难度：简单。

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

    ListNode* findMid(ListNode* head) {
        ListNode *fast = head, *low = head;

        while(fast -> next != nullptr && fast -> next -> next != nullptr) {
            low = low -> next;
            fast = fast -> next -> next;
        }
        return low;
    }

    ListNode* rev(ListNode* head) {
        if(head == nullptr || head -> next == nullptr) {
            return head;
        }
        ListNode *idx = new ListNode(-1), *p;
        while(head != nullptr) {
            p = head -> next;
            head -> next = idx -> next;
            idx -> next = head;
            head = p;
        }
        return idx -> next;
    }

    bool judge(ListNode* l, ListNode* r) {
        while(l != nullptr && r != nullptr) {
            if(l -> val != r -> val) {
                return false;
            }
            l = l -> next, r = r -> next;
        }
        return true;
    }

    bool isPalindrome(ListNode* head) {
        if(head == nullptr || head -> next == nullptr) {
            return true;
        }

        ListNode *mid = findMid(head);
        ListNode *l = head, *r = mid -> next;
        mid -> next = nullptr;
        r = rev(r);

        return judge(l, r);
    }
};
```



---



### 题目

给定一个链表的 **头节点** `head` **，**请判断其是否为回文链表。

如果一个链表是回文，那么链表节点序列从前往后看和从后往前看是相同的。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII027-1626421737-LjXceN-image.png)

```
输入: head = [1,2,3,3,2,1]
输出: true
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII027-1626422231-wgvnWh-image.png)

```
输入: head = [1,2]
输出: false
```

 

**提示：**

- 链表 L 的长度范围为 `[1, 10^5]`
- `0 <= node.val <= 9`

 

**进阶：**能否用 O(n) 时间复杂度和 O(1) 空间复杂度解决此题？

 

注意：本题与 234 题[234. 回文链表](https://leetcode-cn.com/problems/palindrome-linked-list/)相同


