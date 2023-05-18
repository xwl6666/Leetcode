## 剑指 Offer II 114. 外星文字典

LeetCode：[剑指 Offer II 114. 外星文字典](https://leetcode.cn/problems/Jf1JuT/)，难度：困难。

### 题解

#### 代码

```c++
class Solution {
public:

    vector<int> edge[200];
    int in[200];

    string alienOrder(vector<string>& words) {
        int len = (int)words.size();

        unordered_set<int> s;
        for(int i = 0; i < len; i++) {
            for(int k : words[i]) {
                s.insert(k);
            }
            for(int j = i + 1, mi; j < len; j++) {
                mi = min((int)words[i].size(), (int)words[j].size());
                if((int)words[i].size() > mi && words[i].find(words[j]) == 0) {
                    return "";
                }
                for(int k = 0; k < mi; k++) {
                    if(words[i][k] == words[j][k]) {
                        continue;
                    }
                    edge[words[i][k]].push_back(words[j][k]); // words[i][k] < words[j][k]
                    in[words[j][k]] ++;
                    break;
                }
            }
        }

        queue<int> q;
        for(int i : s) {
            if(in[i] == 0) {
                q.push(i);
            }
        }

        string res = "";
        int now;
        while(!q.empty()) {
            now = q.front(), q.pop();
            res += now;
            for(int to : edge[now]) {
                if(-- in[to] == 0) {
                    q.push(to);
                }
            }
        }

        if((int)res.size() == (int)s.size()) {
            return res;
        }
        return "";
    }
};
```



---



### 题目

现有一种使用英语字母的外星文语言，这门语言的字母顺序与英语顺序不同。

给定一个字符串列表 `words` ，作为这门语言的词典，`words` 中的字符串已经 **按这门新语言的字母顺序进行了排序** 。

请你根据该词典还原出此语言中已知的字母顺序，并 **按字母递增顺序** 排列。若不存在合法字母顺序，返回 `""` 。若存在多种可能的合法字母顺序，返回其中 **任意一种** 顺序即可。

字符串 `s` **字典顺序小于** 字符串 `t` 有两种情况：

- 在第一个不同字母处，如果 `s` 中的字母在这门外星语言的字母顺序中位于 `t` 中字母之前，那么 `s` 的字典顺序小于 `t` 。
- 如果前面 `min(s.length, t.length)` 字母都相同，那么 `s.length < t.length` 时，`s` 的字典顺序也小于 `t` 。

 

**示例 1：**

```
输入：words = ["wrt","wrf","er","ett","rftt"]
输出："wertf"
```

**示例 2：**

```
输入：words = ["z","x"]
输出："zx"
```

**示例 3：**

```
输入：words = ["z","x","z"]
输出：""
解释：不存在合法字母顺序，因此返回 "" 。
```

 

**提示：**

- `1 <= words.length <= 100`
- `1 <= words[i].length <= 100`
- `words[i]` 仅由小写英文字母组成

 

注意：本题与 269 题[269. 火星词典](https://leetcode-cn.com/problems/alien-dictionary/)相同


