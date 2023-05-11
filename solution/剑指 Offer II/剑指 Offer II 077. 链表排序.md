## 剑指 Offer II 077. 链表排序

LeetCode：[剑指 Offer II 077. 链表排序](https://leetcode.cn/problems/7WHec2/)，难度：中等。

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
    ListNode* sortList(ListNode* head) {
        if(head == nullptr) {
            return nullptr;
        }
        vector<ListNode*> v;
        while(head != nullptr) {
            v.push_back(head);
            head = head -> next;
        }

        sort(v.begin(), v.end(), [](const ListNode* a, const ListNode* b) {
            return a -> val < b -> val;
        });
        for(int i = 1; i < v.size(); i++) {
            v[i - 1] -> next = v[i];
        }
        v.back() -> next = nullptr;
        return v.front();
    }
};
```



---



### 题目

给定链表的头结点 `head` ，请将其按 **升序** 排列并返回 **排序后的链表** 。



 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII077-sort_list_1.jpg)

```
输入：head = [4,2,1,3]
输出：[1,2,3,4]
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII077-sort_list_2.jpg)

```
输入：head = [-1,5,3,4,0]
输出：[-1,0,3,4,5]
```

**示例 3：**

```
输入：head = []
输出：[]
```

 

**提示：**

- 链表中节点的数目在范围 `[0, 5 * 10^4]` 内
- `-10^5 <= Node.val <= 10^5`

 

**进阶：**你可以在 `O(n log n)` 时间复杂度和常数级空间复杂度下，对链表进行排序吗？

 

注意：本题与 148 题[148. 排序链表](https://leetcode-cn.com/problems/sort-list/)相同


