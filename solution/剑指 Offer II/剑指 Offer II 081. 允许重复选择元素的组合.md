## 剑指 Offer II 081. 允许重复选择元素的组合

LeetCode：[剑指 Offer II 081. 允许重复选择元素的组合](https://leetcode.cn/problems/Ygoe9J/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    int limit;

    vector< vector<int> > res;
    vector<int> num, temp;

    void dfs(int idx, int sum) {
        if(sum > limit) {
            return ;
        }
        if(sum == limit) {
            res.push_back(temp);
            return ;
        }
        if(idx >= (int)num.size()) {
            return ;
        }

        temp.push_back(num[idx]);
        dfs(idx, sum + num[idx]);
        temp.pop_back();

        dfs(idx + 1, sum);
    }

    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        num = candidates, limit = target;
        dfs(0, 0);
        return res;
    }
};
```



---



### 题目

给定一个**无重复元素**的正整数数组 `candidates` 和一个正整数 `target` ，找出 `candidates` 中所有可以使数字和为目标数 `target` 的唯一组合。

`candidates` 中的数字可以无限制重复被选取。如果至少一个所选数字数量不同，则两种组合是不同的。 

对于给定的输入，保证和为 `target` 的唯一组合数少于 `150` 个。

 

**示例 1：**

```
输入: candidates = [2,3,6,7], target = 7
输出: [[7],[2,2,3]]
```

**示例 2：**

```
输入: candidates = [2,3,5], target = 8
输出: [[2,2,2,2],[2,3,3],[3,5]]
```

**示例 3：**

```
输入: candidates = [2], target = 1
输出: []
```

**示例 4：**

```
输入: candidates = [1], target = 1
输出: [[1]]
```

**示例 5：**

```
输入: candidates = [1], target = 2
输出: [[1,1]]
```

 

**提示：**

- `1 <= candidates.length <= 30`
- `1 <= candidates[i] <= 200`
- `candidate` 中的每个元素都是独一无二的。
- `1 <= target <= 500`

 

注意：本题与 39 题[39. 组合总和](https://leetcode-cn.com/problems/combination-sum/)相同 


