## 剑指 Offer II 038. 每日温度

LeetCode：[剑指 Offer II 038. 每日温度](https://leetcode.cn/problems/iIQa4I/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temperatures) {
        int len = (int)temperatures.size();

        stack< pair<int, int> > stk;
        vector<int> res(len);

        for(int i = len - 1; i >= 0; i--) {
            while(!stk.empty() && stk.top().first <= temperatures[i]) {
                stk.pop();
            }
            if(stk.empty()) {
                res[i] = 0;
            } else {
                res[i] = stk.top().second - i;
            }
            stk.push(make_pair(temperatures[i], i));
        }
        return res;
    }
};
```



---



### 题目

请根据每日 `气温` 列表 `temperatures` ，重新生成一个列表，要求其对应位置的输出为：要想观测到更高的气温，至少需要等待的天数。如果气温在这之后都不会升高，请在该位置用 `0` 来代替。

 

**示例 1:**

```
输入: temperatures = [73,74,75,71,69,72,76,73]
输出: [1,1,4,2,1,1,0,0]
```

**示例 2:**

```
输入: temperatures = [30,40,50,60]
输出: [1,1,1,0]
```

**示例 3:**

```
输入: temperatures = [30,60,90]
输出: [1,1,0]
```

 

**提示：**

- `1 <= temperatures.length <= 10^5`
- `30 <= temperatures[i] <= 100`

 

注意：本题与 739 题[739. 每日温度](https://leetcode-cn.com/problems/daily-temperatures/)相同


