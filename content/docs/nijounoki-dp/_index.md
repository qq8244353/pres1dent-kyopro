---
title: 二乗の木DP
type: docs
---
# 概要
ぱっと見O(N^3)のDPが実はO(N^2)というやつ.
# 記事等
- https://snuke.hatenablog.com/entry/2019/01/15/211812
# 問題例
https://atcoder.jp/contests/abc287/tasks/abc287_f
# コード
```
int main() {
    ios::sync_with_stdio(false);
    std::cin.tie(nullptr);
    int n; cin >> n;
    vector to(n, vector<int>());
    rep(i, n - 1) {
        int a, b; cin >> a >> b;
        a--, b--;    
        to[a].push_back(b);
        to[b].push_back(a);
    }
    auto dfs = [&](auto&& self, int v, int p) -> vector<vector<mint>> {
        vector dp(2, vector<mint>(2));
        dp[0][0] = 1, dp[1][1] = 1;
        for (auto u : to[v]) {
            if (u == p) { continue; }
            auto res = self(self, u, v);
            vector ndp(dp.size() + res.size(), vector<mint>(2));
            rep(i, dp.size()) rep(j, res.size()) {
                if (i + j >= ndp.size()) { break; }
                ndp[i + j][0] += dp[i][0] * (res[j][0] + res[j][1]);
                ndp[i + j][1] += dp[i][1] * res[j][0];
                if (i + j - 1 >= 0) { ndp[i + j - 1][1] += dp[i][1] * res[j][1]; }
            }
            swap(ndp, dp);
        }
        return dp;
    };
    auto res = dfs(dfs, 0, -1);
    rep(i, n) {
        if (i + 1 >= res.size()) { cout << 0 << endl; }
        else { cout << (res[i + 1][0] + res[i + 1][1]).val() << endl; }
    }
    return 0;
}
```
