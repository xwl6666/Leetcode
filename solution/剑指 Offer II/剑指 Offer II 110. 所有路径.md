## 剑指 Offer II 110. 所有路径

LeetCode：[剑指 Offer II 110. 所有路径](https://leetcode.cn/problems/bP4bmD/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    vector< vector<int> > path;

    vector< vector<int> > edge;
    vector<int> v;
    int n;

    void dfs(int cur) {
        if(cur == n) {
            path.push_back(v);
            return ;
        }
        for(int to : edge[cur]) {
            v.push_back(to);
            dfs(to);
            v.pop_back();
        }
    }

    vector<vector<int>> allPathsSourceTarget(vector<vector<int>>& edge) {
        n = (int)edge.size() - 1;
        this -> edge = edge;
        v.push_back(0);
        dfs(0);
        return path;
    }
};
```



---



### 题目

给定一个有 `n` 个节点的有向无环图，用二维数组 `graph` 表示，请找到所有从 `0` 到 `n-1` 的路径并输出（不要求按顺序）。

`graph` 的第 `i` 个数组中的单元都表示有向图中 `i` 号节点所能到达的下一些结点（译者注：有向图是有方向的，即规定了 a→b 你就不能从 b→a ），若为空，就是没有下一个节点了。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII110-all_1.jpg)

```
输入：graph = [[1,2],[3],[3],[]]
输出：[[0,1,3],[0,2,3]]
解释：有两条路径 0 -> 1 -> 3 和 0 -> 2 -> 3
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII110-all_2.jpg)

```
输入：graph = [[4,3,1],[3,2,4],[3],[4],[]]
输出：[[0,4],[0,3,4],[0,1,3,4],[0,1,2,3,4],[0,1,4]]
```

**示例 3：**

```
输入：graph = [[1],[]]
输出：[[0,1]]
```

**示例 4：**

```
输入：graph = [[1,2,3],[2],[3],[]]
输出：[[0,1,2,3],[0,2,3],[0,3]]
```

**示例 5：**

```
输入：graph = [[1,3],[2],[3],[]]
输出：[[0,1,2,3],[0,3]]
```

 

**提示：**

- `n == graph.length`
- `2 <= n <= 15`
- `0 <= graph[i][j] < n`
- `graph[i][j] != i` 
- 保证输入为有向无环图 `(GAD)`

 

注意：本题与 797 题[797. 所有可能的路径](https://leetcode-cn.com/problems/all-paths-from-source-to-target/)相同


