## 剑指 Offer 06. 从尾到头打印链表

LeetCode：[剑指 Offer 06. 从尾到头打印链表](https://leetcode.cn/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)，难度：简单。

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
    vector<int> res;

    void reverse(ListNode* head) {
        if(head != NULL) {
            reverse(head -> next);
            res.push_back(head -> val);
        }
    }

    vector<int> reversePrint(ListNode* head) {
        reverse(head);
        return res;
    }
};
```



---



### 题目

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

 

**示例 1：**

```
输入：head = [1,3,2]
输出：[2,3,1]
```

 

**限制：**

```
0 <= 链表长度 <= 10000
```

