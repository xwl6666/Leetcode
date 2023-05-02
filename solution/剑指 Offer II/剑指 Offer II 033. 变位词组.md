## 剑指 Offer II 033. 变位词组

LeetCode：[剑指 Offer II 033. 变位词组](https://leetcode.cn/problems/sfvd7V/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<string> > bk;
        string ss;
        for(int i = 0; i < strs.size(); i++) {
            ss = strs[i];
            sort(ss.begin(), ss.end());
            bk[ss].push_back(strs[i]);
        }
        
        vector< vector<string> > res;
        for(auto it = bk.begin(); it != bk.end(); it ++) {
            res.push_back(it -> second);
        }
        return res;
    }
};
```



---



### 题目

给定一个字符串数组 `strs` ，将 **变位词** 组合在一起。 可以按任意顺序返回结果列表。

**注意：**若两个字符串中每个字符出现的次数都相同，则称它们互为变位词。

 

**示例 1:**

```
输入: strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
输出: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

**示例 2:**

```
输入: strs = [""]
输出: [[""]]
```

**示例 3:**

```
输入: strs = ["a"]
输出: [["a"]]
```

 

**提示：**

- `1 <= strs.length <= 10^4`
- `0 <= strs[i].length <= 100`
- `strs[i]` 仅包含小写字母

 

注意：本题与 49 题[49. 字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/)相同


