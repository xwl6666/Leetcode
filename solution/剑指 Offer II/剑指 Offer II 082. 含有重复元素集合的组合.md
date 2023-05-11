## 剑指 Offer II 082. 含有重复元素集合的组合

LeetCode：[剑指 Offer II 082. 含有重复元素集合的组合](https://leetcode.cn/problems/4sjJUc/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    vector<int> num;
    int limit;
    map<int, int> bk;

    vector< vector<int> > res;
    vector<int> v;

    void dfs(int index, int sum) {
        if(sum > limit) {
            return ;
        }
        if(sum == limit) {
            res.push_back(v);
            return ;
        }
        if(index >= (int)num.size() || sum + num[index] > limit) {
            return ;
        }

        for(int i = 1; i <= bk[num[index]]; i++) {
            for(int j = 0; j < i; j++) {
                v.push_back(num[index]);
            }
            dfs(index + 1, sum + num[index] * i);
            for(int j = 0; j < i; j++) {
                v.pop_back();
            }
        }
        
        dfs(index + 1, sum);
    }

    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        for(int i : candidates) {
            bk[i] ++;
        }
        for(auto it = bk.begin(); it != bk.end(); it++) {
            num.push_back(it -> first);
        }

        limit = target;
        dfs(0, 0);
        return res;
    }
};
```



---



### 题目

给定一个可能有重复数字的整数数组 `candidates` 和一个目标数 `target` ，找出 `candidates` 中所有可以使数字和为 `target` 的组合。

`candidates` 中的每个数字在每个组合中只能使用一次，解集不能包含重复的组合。 

 

**示例 1:**

```
输入: candidates = [10,1,2,7,6,1,5], target = 8,
输出:
[
    [1,1,6],
    [1,2,5],
    [1,7],
    [2,6]
]
```

**示例 2:**

```
输入: candidates = [2,5,2,1,2], target = 5,
输出:
[
    [1,2,2],
    [5]
]
```

 

**提示:**

- `1 <= candidates.length <= 100`
- `1 <= candidates[i] <= 50`
- `1 <= target <= 30`

 

注意：本题与 40 题[40. 组合总和 II](https://leetcode-cn.com/problems/combination-sum-ii/)相同


