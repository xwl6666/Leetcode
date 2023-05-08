## 剑指 Offer II 059. 数据流的第 K 大数值

LeetCode：[剑指 Offer II 059. 数据流的第 K 大数值](https://leetcode.cn/problems/jBjn9C/)，难度：简单。

### 题解

#### 代码

```c++
class KthLargest {
public:

    priority_queue<int, vector<int>, greater<int> > q;
    int limit;

    KthLargest(int k, vector<int>& nums) {
        limit = k;
        while(!q.empty()) {
            q.pop();
        }
        for(int i : nums) {
            q.push(i);
            if((int)q.size() > limit) {
                q.pop();
            }
        }
    }
    
    int add(int val) {
        q.push(val);
        if((int)q.size() > limit) {
            q.pop();
        }
        return q.top();
    }
};

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest* obj = new KthLargest(k, nums);
 * int param_1 = obj->add(val);
 */
```



---



### 题目

设计一个找到数据流中第 `k` 大元素的类（class）。注意是排序后的第 `k` 大元素，不是第 `k` 个不同的元素。

请实现 `KthLargest` 类：

- `KthLargest(int k, int[] nums)` 使用整数 `k` 和整数流 `nums` 初始化对象。
- `int add(int val)` 将 `val` 插入数据流 `nums` 后，返回当前数据流中第 `k` 大的元素。

 

**示例：**

```
输入：
["KthLargest", "add", "add", "add", "add", "add"]
[[3, [4, 5, 8, 2]], [3], [5], [10], [9], [4]]
输出：
[null, 4, 5, 5, 8, 8]

解释：
KthLargest kthLargest = new KthLargest(3, [4, 5, 8, 2]);
kthLargest.add(3);   // return 4
kthLargest.add(5);   // return 5
kthLargest.add(10);  // return 5
kthLargest.add(9);   // return 8
kthLargest.add(4);   // return 8
```

 

**提示：**

- `1 <= k <= 10^4`
- `0 <= nums.length <= 10^4`
- `-10^4 <= nums[i] <= 10^4`
- `-10^4 <= val <= 10^4`
- 最多调用 `add` 方法 `10^4` 次
- 题目数据保证，在查找第 `k` 大元素时，数组中至少有 `k` 个元素

 

注意：本题与 703 题[703. 数据流中的第 K 大元素](https://leetcode-cn.com/problems/kth-largest-element-in-a-stream/)相同


