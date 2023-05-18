## 剑指 Offer II 116. 省份数量

LeetCode：[剑指 Offer II 116. 省份数量](https://leetcode.cn/problems/bLyHh0/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    vector<int> f;

    void init(int len) {
        f.resize(len);
        for(int i = 0; i < len; i++) {
            f[i] = i;
        }
    }

    int getf(int x) {
        if(x == f[x]) {
            return x;
        } else {
            x = getf(f[x]);
            return x;
        }
    }

    void merge(int x, int y) {
        x = getf(f[x]), y = getf(f[y]);
        if(x != y) {
            f[y] = x;
        }
    }

    int findCircleNum(vector<vector<int>>& isConnected) {
        int len = (int)isConnected.size();
        init(len);
        for(int i = 0; i < len; i++) {
            for(int j = i + 1; j < len; j++) {
                if(isConnected[i][j]) {
                    merge(i, j);
                }
            }
        }

        unordered_set<int> st;
        for(int i = 0; i < len; i++) {
            st.insert(getf(f[i]));
        }
        return (int)st.size();
    }
};
```



---



### 题目

有 `n` 个城市，其中一些彼此相连，另一些没有相连。如果城市 `a` 与城市 `b` 直接相连，且城市 `b` 与城市 `c` 直接相连，那么城市 `a` 与城市 `c` 间接相连。

**省份** 是一组直接或间接相连的城市，组内不含其他没有相连的城市。

给你一个 `n x n` 的矩阵 `isConnected` ，其中 `isConnected[i][j] = 1` 表示第 `i` 个城市和第 `j` 个城市直接相连，而 `isConnected[i][j] = 0` 表示二者不直接相连。

返回矩阵中 **省份** 的数量。

 

**示例 1：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII116-graph1.jpg)

```
输入：isConnected = [[1,1,0],[1,1,0],[0,0,1]]
输出：2
```

**示例 2：**

![img](https://gitee.com/xwl66/leetcode/raw/master/image/jianZhiOfferII116-graph2.jpg)

```
输入：isConnected = [[1,0,0],[0,1,0],[0,0,1]]
输出：3
```

 

**提示：**

- `1 <= n <= 200`
- `n == isConnected.length`
- `n == isConnected[i].length`
- `isConnected[i][j]` 为 `1` 或 `0`
- `isConnected[i][i] == 1`
- `isConnected[i][j] == isConnected[j][i]`

 

注意：本题与 547 题[547. 省份数量](https://leetcode-cn.com/problems/number-of-provinces/)相同


