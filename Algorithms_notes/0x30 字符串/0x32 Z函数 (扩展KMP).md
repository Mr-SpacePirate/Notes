## 0x32 Z函数 (扩展KMP)

**约定**：字符串下标从 $0$ 开始。

#### 定义

对于个长度为 $n$ 的字符串 $S$。定义函数 $z[i]$ 表示 $S$ 和 $S[i, n - 1]$（即以 $S[i]$ 开头的后缀）的最长公共前缀（$LCP$）的长度。$z$ 被称为 $S$ 的 $Z$ 函数（扩展 $KMP$ ）。**特殊地**，$z[0] = 0$。

#### 代码封装

- 时间复杂度 $O(n)$

``` C++ {.line-numbers}
// z[i] = LCP(T[i,lent],T)
// extend[i] = LCP(S[i,lens],T)
struct Z
{
    int n;
    string p;
    vector<int> z;
    Z(string &s) : n(s.size() - 1), p(s), z(z_algorithm(p)) {}

    vector<int> z_algorithm(string &s)
    {
        vector<int> extend(s.size());
        extend[0] = 0;
        for (int i = 1, st = 0, ed = 0; i < s.size(); i ++ )
        {
            extend[i] = i <= ed ? min(z[i - st + 1], ed - i + 1) : 0;
            while (i + extend[i] < s.size() && extend[i] < n && s[i + extend[i]] == p[extend[i] + 1])
            {
                extend[i] ++ ;
            }
            if (i + extend[i] - 1 >= ed && i != 1)
            {
                st = i;
                ed = i + extend[i] - 1;
            }
        }
        return extend;
    }
};
```
