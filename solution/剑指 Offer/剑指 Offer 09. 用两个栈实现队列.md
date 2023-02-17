## 剑指 Offer 09. 用两个栈实现队列

LeetCode：[剑指 Offer 09. 用两个栈实现队列](https://leetcode.cn/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)，难度：简单。

### 题解

#### 代码

```c++
class CQueue {
public:

    stack<int> a, b;

    CQueue() {
        while(!a.empty()) {
            a.pop();
        }
        while(!b.empty()) {
            b.pop();
        }
    }
    
    void appendTail(int value) {
        while(!b.empty()) {
            a.push(b.top());
            b.pop();
        }
        a.push(value);
    }
    
    int deleteHead() {
        while(!a.empty()) {
            b.push(a.top());
            a.pop();
        }
        if(b.empty()) {
            return -1;
        }
        int now = b.top();
        b.pop();
        return now;
    }
};

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue* obj = new CQueue();
 * obj->appendTail(value);
 * int param_2 = obj->deleteHead();
 */
```



---



### 题目

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 `appendTail` 和 `deleteHead` ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，`deleteHead` 操作返回 -1 )

 

**示例 1：**

```
输入：
["CQueue","appendTail","deleteHead","deleteHead","deleteHead"]
[[],[3],[],[],[]]
输出：[null,null,3,-1,-1]
```

**示例 2：**

```
输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
```

**提示：**

- `1 <= values <= 10000`
- 最多会对` appendTail、deleteHead `进行` 10000` 次调用

