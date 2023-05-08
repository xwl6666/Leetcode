## 剑指 Offer II 064. 神奇的字典

LeetCode：[剑指 Offer II 064. 神奇的字典](https://leetcode.cn/problems/US1pGT/)，难度：中等。

### 题解

#### 代码

```c++
class MagicDictionary {
public:
    /** Initialize your data structure here. */

    int trie[26][50005];
    bool flag[50005];
    int total;

    void insert(string word) {
        int root = 0;
        for(int i = 0, to; i < word.size(); i++) {
            to = word[i] - 'a';
            if(!trie[to][root]) {
                trie[to][root] = ++total;
                root = trie[to][root];
            } else {
                root = trie[to][root];
            }
        }
        flag[root] = true;
    }

    MagicDictionary() {
        total = 0;
        memset(trie, 0, sizeof(trie));
        memset(flag, false, sizeof(flag));
    }
    
    void buildDict(vector<string> dictionary) {
        for(string ss : dictionary) {
            insert(ss);
        }
    }

    bool search(string word) {
        int root = 0;
        for(int i = 0, to; i < word.size(); i++) {
            to = word[i] - 'a';
            if(!trie[to][root]) {
                for(int j = 0; j < 26; j++) {
                    if(j == to) {
                        continue;
                    }
                    if(trie[j][root] && judge(trie[j][root], word.substr(i + 1))) {
                        return true;
                    }
                }
                return false;
            } else {
                for(int j = 0; j < 26; j++) {
                    if(j == to) {
                        continue;
                    }
                    if(trie[j][root] && judge(trie[j][root], word.substr(i + 1))) {
                        return true;
                    }
                }
            }
            root = trie[to][root];
        }
        return false;
    }
    
    bool judge(int root, string word) {
        for(int i = 0, to; i < word.size(); i++) {
            to = word[i] - 'a';
            if(!trie[to][root]) {
                return false;
            }
            root = trie[to][root];
        }
        return flag[root];
    }

};

/**
 * Your MagicDictionary object will be instantiated and called as such:
 * MagicDictionary* obj = new MagicDictionary();
 * obj->buildDict(dictionary);
 * bool param_2 = obj->search(searchWord);
 */
```



---



### 题目

设计一个使用单词列表进行初始化的数据结构，单词列表中的单词 **互不相同** 。 如果给出一个单词，请判定能否只将这个单词中**一个**字母换成另一个字母，使得所形成的新单词存在于已构建的神奇字典中。

实现 `MagicDictionary` 类：

- `MagicDictionary()` 初始化对象
- `void buildDict(String[] dictionary)` 使用字符串数组 `dictionary` 设定该数据结构，`dictionary` 中的字符串互不相同
- `bool search(String searchWord)` 给定一个字符串 `searchWord` ，判定能否只将字符串中 **一个** 字母换成另一个字母，使得所形成的新字符串能够与字典中的任一字符串匹配。如果可以，返回 `true` ；否则，返回 `false` 。

 

**示例：**

```
输入
inputs = ["MagicDictionary", "buildDict", "search", "search", "search", "search"]
inputs = [[], [["hello", "leetcode"]], ["hello"], ["hhllo"], ["hell"], ["leetcoded"]]
输出
[null, null, false, true, false, false]

解释
MagicDictionary magicDictionary = new MagicDictionary();
magicDictionary.buildDict(["hello", "leetcode"]);
magicDictionary.search("hello"); // 返回 False
magicDictionary.search("hhllo"); // 将第二个 'h' 替换为 'e' 可以匹配 "hello" ，所以返回 True
magicDictionary.search("hell"); // 返回 False
magicDictionary.search("leetcoded"); // 返回 False
```

 

**提示：**

- `1 <= dictionary.length <= 100`
- `1 <= dictionary[i].length <= 100`
- `dictionary[i]` 仅由小写英文字母组成
- `dictionary` 中的所有字符串 **互不相同**
- `1 <= searchWord.length <= 100`
- `searchWord` 仅由小写英文字母组成
- `buildDict` 仅在 `search` 之前调用一次
- 最多调用 `100` 次 `search`

 

注意：本题与 676 题[676. 实现一个魔法字典](https://leetcode-cn.com/problems/implement-magic-dictionary/)相同


