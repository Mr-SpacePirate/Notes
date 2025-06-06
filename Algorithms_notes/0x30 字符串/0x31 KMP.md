## 0x31 KMP

#### Border

如果字符串 $S$ 的同长度的前后缀完全相同，则称此前缀（后缀）为一个 $border$。

#### 周期

对于字符串 $S$ 和正整数 $p$，如果有 $S[i] = S[i - p]$，对于 $p < i \leq \vert S \vert$ 成立，则称 $p$ 为字符串 $S$ 的一个周期。**特殊地**，$p = \vert S \vert$ 一定是 $S$ 的周期。

- 形如 $acaca$ 中 ac 是一个合法周期

#### 循环节

若字符串 $S$ 的周期 $p$ 满足 $p | \vert S \vert$，则称 $p$ 为 $S$ 的一个循环节。**特殊地**，$p = \vert S \vert$ 一定是 $S$ 的循环节。

- 形如 $acac$ 中 $ac$、$acac$ 是循环节，$aca$ 不是

#### 性质

$p$ 是 $S$ 的周期 $\Leftrightarrow \vert S \vert - p$ 是 $S$ 的 $border$。

#### 代码封装

- 时间复杂度 $O(n + m)$

```C++ {.line-numbers}
template <typename T>
struct KMP
{
    int n;
    T p;
    vector<int> ne;
    KMP(T &s) : n(s.size() - 1), p(s), ne(n + 1)
    {
        for (int i = 2, j = 0; i <= n; i ++ )
        {
            while (j && p[i] != p[j + 1]) j = ne[j];
            if (p[i] == p[j + 1]) j ++ ;
            ne[i] = j;
        }
    }

    int boarder(int x) { return ne[x]; }
    // 求所有在s串中的start_pos，如果first_only设置为true，则只返回第一个位置
    vector<int> match(T &s, bool first_only = false)
    {
        vector<int> start_pos;
        for (int i = 1, j = 0; i < s.size(); i ++ )
        {
            while (j && s[i] != p[j + 1]) j = ne[j];
            if (s[i] == p[j + 1]) j ++ ;
            if (j == n)
            {
                start_pos.push_back(i - j + 1);
                if (first_only) return start_pos;
                j = ne[j];
            }
        }
        return start_pos;
    }
    // 循环周期 形如 acaca 中 ac 是一个合法周期
    vector<int> periodic()
    {
        vector<int> ret;
        int now = n;
        while (now)
        {
            now = ne[now];
            ret.push_back(n - now);
        }
        return ret;
    }
    // 循环节 形如 acac 中ac、acac是循环节，aca不是
    vector<int> periodic_loop()
    {
        vector<int> ret;
        for (int x : periodic())
        {
            if (n % x == 0) ret.push_back(x);
        }
        return ret;
    }
    int min_periodic_loop() { return periodic_loop()[0]; }
};
```
