## 剑指 Offer 41. 数据流中的中位数

LeetCode：[剑指 Offer 41. 数据流中的中位数](https://leetcode.cn/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/)，难度：困难。

### 题解

#### 代码

```c++
class MedianFinder {
public:
    /** initialize your data structure here. */
    priority_queue<int> mx; 
    priority_queue<int, vector<int>, greater<int> > mi;
    int cnt;

    MedianFinder() {
        while(!mx.empty()) {
            mx.pop();
        }
        while(!mi.empty()) {
            mi.pop();
        }
        cnt = 0;
    }
    
    void addNum(int num) {
        if(cnt % 2 == 0) {
            mi.push(num);
            mx.push(mi.top());
            mi.pop();
        } else {
            mx.push(num);
            mi.push(mx.top());
            mx.pop();
        }
        cnt ++;
    }
    
    double findMedian() {
        if(cnt & 1) {
            return (double)mx.top();
        } else {
            return (mx.top() + mi.top()) / 2.0;
        }
    }
};

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder* obj = new MedianFinder();
 * obj->addNum(num);
 * double param_2 = obj->findMedian();
 */
```



---



### 题目

如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。

例如，

[2,3,4] 的中位数是 3

[2,3] 的中位数是 (2 + 3) / 2 = 2.5

设计一个支持以下两种操作的数据结构：

- void addNum(int num) - 从数据流中添加一个整数到数据结构中。
- double findMedian() - 返回目前所有元素的中位数。

**示例 1：**

```
输入：
["MedianFinder","addNum","addNum","findMedian","addNum","findMedian"]
[[],[1],[2],[],[3],[]]
输出：[null,null,null,1.50000,null,2.00000]
```

**示例 2：**

```
输入：
["MedianFinder","addNum","findMedian","addNum","findMedian"]
[[],[2],[],[3],[]]
输出：[null,null,2.00000,null,2.50000]
```

 

**限制：**

- 最多会对 `addNum、findMedian` 进行 `50000` 次调用。

注意：本题与 295 题[295. 数据流的中位数](https://leetcode-cn.com/problems/find-median-from-data-stream/)相同


