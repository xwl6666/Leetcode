## 剑指 Offer 44. 数字序列中某一位的数字

LeetCode：[剑指 Offer 44. 数字序列中某一位的数字](https://leetcode.cn/problems/shu-zi-xu-lie-zhong-mou-yi-wei-de-shu-zi-lcof/)，难度：中等。

### 题解

#### 代码

```c++
class Solution {
public:
    #define ll long long

    ll get(ll x) { // 求 1 到 x ，连接字符串有几位
        ll res = 0, bas = 1;

        while(true) {
            ll pre = pow(10, bas - 1), now = 9 * pre;
            ll index = 10 * pre - 1;

            if(x >= index) {
                res += now * bas;
            } else {
                if(x < pre) {
                    break;
                }
                int cnt = (x - pre + 1);
                res += cnt * bas;
                break;
            }
            bas ++;
        }
        return res;
    }

    int findNthDigit(int n) {
        // 1 ~ 9       9
        // 10 ~ 99     90
        // 100 ~ 999     900
        // 1000 ~ 9999    9000

        ll left = 1, right = 1e11, mid, ans, to;

        while(left <= right) {
            mid = (left + right) / 2;
            to = get(mid);
            if(get(mid - 1) < n && to >= n) {
                ans = mid;
                break;
            } 
            if(to < n) {
                left = mid + 1;
            } else if(get(mid - 1) >= n) {
                right = mid - 1;
            }
        }
        n -= get(ans - 1);
        return to_string(ans)[n - 1] - '0';
    }
};
```



---



### 题目

数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从下标0开始计数）是5，第13位是1，第19位是4，等等。

请写一个函数，求任意第n位对应的数字。

 

**示例 1：**

```
输入：n = 3
输出：3
```

**示例 2：**

```
输入：n = 11
输出：0
```

 

**限制：**

- `0 <= n < 2^31`

注意：本题与 400 题[400. 第 N 位数字](https://leetcode-cn.com/problems/nth-digit/)相同


