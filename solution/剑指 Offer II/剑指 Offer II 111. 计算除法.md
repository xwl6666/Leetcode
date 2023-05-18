## 剑指 Offer II 111. 计算除法

LeetCode：[剑指 Offer II 111. 计算除法](https://leetcode.cn/problems/vlzXQL/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    vector< vector< pair<int, double> > > edge;

    bool f;
    double mul;
    vector<bool> vis;

    void dfs(int cur, int ed, double sum) {
        if(f == true) {
            return ;
        }
        if(cur == ed) {
            f = true, mul = sum;
            return ;
        }
        for(pair<int, double> to : edge[cur]) {
            if(!vis[to.first]) {
                vis[to.first] = true;
                dfs(to.first, ed, sum * to.second);
            }
        }
    }

    vector<double> calcEquation(vector<vector<string>>& equations, vector<double>& values, vector<vector<string>>& queries) {
        unordered_map<string, int> bk;
        int total = 0;
        edge.resize(40);
        for(int i = 0, x, y; i < equations.size(); i++) {
            if(!bk.count(equations[i][0])) {
                bk[equations[i][0]] = total ++;
            }
            x = bk[equations[i][0]];
            if(!bk.count(equations[i][1])) {
                bk[equations[i][1]] = total ++;
            }
            y = bk[equations[i][1]];
            edge[x].push_back({y, values[i]}); // x / y = val
            edge[y].push_back({x, 1.0 / values[i]}); // y / x = 1.0 / val
        }
        edge.resize(total);

        vector<double> res;
        for(int i = 0, x, y; i < queries.size(); i++) {
            if(!bk.count(queries[i][0]) || !bk.count(queries[i][1])) {
                res.push_back(-1.0);
                continue;
            }
            if(queries[i][0] == queries[i][1]) {
                res.push_back(1.0);
                continue;
            }
            x = bk[queries[i][0]], y = bk[queries[i][1]];
            f = false;
            vis.assign(total, false);
            vis[x] = true;
            dfs(x, y, 1.0);
            if(f == true) {
                res.push_back(mul);
                continue;
            }
            res.push_back(-1.0);
        }
        return res;
    }
};
```



---



### 题目

给定一个变量对数组 `equations` 和一个实数值数组 `values` 作为已知条件，其中 `equations[i] = [A_i, B_i]` 和 `values[i]` 共同表示等式 `A_i / B_i = values[i]` 。每个 `A_i` 或 `B_i` 是一个表示单个变量的字符串。

另有一些以数组 `queries` 表示的问题，其中 `queries[j] = [C_j, D_j]` 表示第 `j` 个问题，请你根据已知条件找出 `C_j / D_j = ?` 的结果作为答案。

返回 **所有问题的答案** 。如果存在某个无法确定的答案，则用 `-1.0` 替代这个答案。如果问题中出现了给定的已知条件中没有出现的字符串，也需要用 `-1.0` 替代这个答案。

**注意：**输入总是有效的。可以假设除法运算中不会出现除数为 0 的情况，且不存在任何矛盾的结果。

 

**示例 1：**

```
输入：equations = [["a","b"],["b","c"]], values = [2.0,3.0], queries = [["a","c"],["b","a"],["a","e"],["a","a"],["x","x"]]
输出：[6.00000,0.50000,-1.00000,1.00000,-1.00000]
解释：
条件：a / b = 2.0, b / c = 3.0
问题：a / c = ?, b / a = ?, a / e = ?, a / a = ?, x / x = ?
结果：[6.0, 0.5, -1.0, 1.0, -1.0 ]
```

**示例 2：**

```
输入：equations = [["a","b"],["b","c"],["bc","cd"]], values = [1.5,2.5,5.0], queries = [["a","c"],["c","b"],["bc","cd"],["cd","bc"]]
输出：[3.75000,0.40000,5.00000,0.20000]
```

**示例 3：**

```
输入：equations = [["a","b"]], values = [0.5], queries = [["a","b"],["b","a"],["a","c"],["x","y"]]
输出：[0.50000,2.00000,-1.00000,-1.00000]
```

 

**提示：**

- `1 <= equations.length <= 20`
- `equations[i].length == 2`
- `1 <= A_i.length, B_i.length <= 5`
- `values.length == equations.length`
- `0.0 < values[i] <= 20.0`
- `1 <= queries.length <= 20`
- `queries[i].length == 2`
- `1 <= C_j.length, D_j.length <= 5`
- `A_i, B_i, C_j, D_j` 由小写英文字母与数字组成

 

注意：本题与 399 题[399. 除法求值](https://leetcode-cn.com/problems/evaluate-division/)相同


