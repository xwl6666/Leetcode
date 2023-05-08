## 剑指 Offer II 063. 替换单词

LeetCode：[剑指 Offer II 063. 替换单词](https://leetcode.cn/problems/UhWRSj/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:

    int trie[26][50005];
    bool flag[50005];
    int total;

    void init() {
        total = 0;
        memset(trie, 0, sizeof(trie));
        memset(flag, false, sizeof(flag));
    }

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

    int match(string prefix) {
        int root = 0;
        for(int i = 0, to; i < prefix.size(); i++) {
            to = prefix[i] - 'a';
            if(!trie[to][root]) {
                return -1;
            }
            root = trie[to][root];
            if(flag[root]) {
                return i + 1;
            }
        }
        return -1;
    }

    string replaceWords(vector<string>& dictionary, string sentence) {
        init();
        for(string ss : dictionary) {
            insert(ss);
        }

        string now = "", res = "";
        int idx;
        for(int i : sentence) {
            if(i == ' ') {
                idx = match(now);
                if(idx != -1) {
                    res += now.substr(0, idx);
                } else {
                    res += now;
                }
                res += " ";
                now = "";
            } else {
                now += i;
            }
        }

        idx = match(now);
        if(idx != -1) {
            res += now.substr(0, idx);
        } else {
            res += now;
        }
        return res;
    }
};
```



---



### 题目

在英语中，有一个叫做 `词根(root)` 的概念，它可以跟着其他一些词组成另一个较长的单词——我们称这个词为 `继承词(successor)`。例如，词根`an`，跟随着单词 `other`(其他)，可以形成新的单词 `another`(另一个)。

现在，给定一个由许多词根组成的词典和一个句子，需要将句子中的所有`继承词`用`词根`替换掉。如果`继承词`有许多可以形成它的`词根`，则用最短的词根替换它。

需要输出替换之后的句子。

 

**示例 1：**

```
输入：dictionary = ["cat","bat","rat"], sentence = "the cattle was rattled by the battery"
输出："the cat was rat by the bat"
```

**示例 2：**

```
输入：dictionary = ["a","b","c"], sentence = "aadsfasf absbs bbab cadsfafs"
输出："a a b c"
```

**示例 3：**

```
输入：dictionary = ["a", "aa", "aaa", "aaaa"], sentence = "a aa a aaaa aaa aaa aaa aaaaaa bbb baba ababa"
输出："a a a a a a a a bbb baba a"
```

**示例 4：**

```
输入：dictionary = ["catt","cat","bat","rat"], sentence = "the cattle was rattled by the battery"
输出："the cat was rat by the bat"
```

**示例 5：**

```
输入：dictionary = ["ac","ab"], sentence = "it is abnormal that this solution is accepted"
输出："it is ab that this solution is ac"
```

 

**提示：**

- `1 <= dictionary.length <= 1000`
- `1 <= dictionary[i].length <= 100`
- `dictionary[i]` 仅由小写字母组成。
- `1 <= sentence.length <= 10^6`
- `sentence` 仅由小写字母和空格组成。
- `sentence` 中单词的总量在范围 `[1, 1000]` 内。
- `sentence` 中每个单词的长度在范围 `[1, 1000]` 内。
- `sentence` 中单词之间由一个空格隔开。
- `sentence` 没有前导或尾随空格。

 

注意：本题与 648 题[648. 单词替换](https://leetcode-cn.com/problems/replace-words/)相同


