## 剑指 Offer II 025. 链表中的两数相加

LeetCode：[剑指 Offer II 025. 链表中的两数相加](https://leetcode.cn/problems/lMSNwu/)，难度：中等。

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

    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        l1 = rev(l1), l2 = rev(l2);

        ListNode *index = new ListNode(-1), *temp = index;

        int jinwei = 0, sum;
        while(l1 != nullptr || l2 != nullptr) {
            sum = jinwei;
            if(l1 != nullptr) {
                sum += l1 -> val;
                l1 = l1 -> next;
            }
            if(l2 != nullptr) {
                sum += l2 -> val;
                l2 = l2 -> next;
            }
            jinwei = sum / 10;
            temp -> next = new ListNode(sum % 10);
            temp = temp -> next;
        }
        if(jinwei) {
            temp -> next = new ListNode(jinwei);
        }

        return rev(index -> next);
    }
};
```



---



### 题目

给定两个 **非空链表** `l1`和 `l2` 来代表两个非负整数。数字最高位位于链表开始位置。它们的每个节点只存储一位数字。将这两数相加会返回一个新的链表。

可以假设除了数字 0 之外，这两个数字都不会以零开头。

 

**示例1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII025-1626420025-fZfzMX-image.png)

```
输入：l1 = [7,2,4,3], l2 = [5,6,4]
输出：[7,8,0,7]
```

**示例2：**

```
输入：l1 = [2,4,3], l2 = [5,6,4]
输出：[8,0,7]
```

**示例3：**

```
输入：l1 = [0], l2 = [0]
输出：[0]
```

 

**提示：**

- 链表的长度范围为` [1, 100]`
- `0 <= node.val <= 9`
- 输入数据保证链表代表的数字无前导 0

 

**进阶：**如果输入链表不能修改该如何处理？换句话说，不能对列表中的节点进行翻转。

 

注意：本题与 445 题[445. 两数相加 II](https://leetcode-cn.com/problems/add-two-numbers-ii/)相同


