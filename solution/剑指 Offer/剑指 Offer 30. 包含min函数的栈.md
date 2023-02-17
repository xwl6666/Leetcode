## 剑指 Offer 30. 包含min函数的栈

LeetCode：[剑指 Offer 30. 包含min函数的栈](https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class MinStack {
public:
    /** initialize your data structure here. */

    stack<int> a, mi;

    MinStack() {
        while(!a.empty()) {
            a.pop();
        }
        while(!mi.empty()) {
            mi.pop();
        }
    }
    
    void push(int x) {
        int now = mi.empty() ? x : std::min(mi.top(), x);
        a.push(x);
        mi.push(now);
    }
    
    void pop() {
        a.pop();
        mi.pop();
    }
    
    int top() {
        return a.top();
    }
    
    int min() {
        return mi.top();
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->min();
 */
```



---

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

 

**示例:**

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.
```

 

**提示：**

1. 各函数的调用总次数不超过 20000 次

 

注意：本题与155 题[155. 最小栈](https://leetcode.cn/problems/min-stack/)相同。

