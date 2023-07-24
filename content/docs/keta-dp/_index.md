---
title: 桁DP
type: docs
---
# 桁DP
桁DPはMLEやTLEを起こしがちなので気を付ける.  
## 雛形
```cpp
int main() {
    string s; cin >> s;
    int n = s.size();
    // 問題固有な特徴量についての処理を記載する.
    // dp: 上記の量をキーとするようなdp配列の宣言を記載.
    //     dpではs未満になることが確定したものの情報をもつ.
    // now: sと一致しているものの状態の宣言を記載.
    for (int i = 0; i < n; i++) {
        // ndp: ndpの宣言を記載.
        int d = s[i] - '0';
        // 特徴量について遷移する
        for (int j = 0; j < dp.size(); j++) {
            for (int k = 0; k <= 9; k++) {
                // small to smallの遷移. dp -> ndp
            }
        }
        // same to smallの遷移. now -> ndp
        for (int k = 0; k < d; k++) {
            // 最初に0をつけるのは禁止.
            if (i | k) {
                // ndp += 1 (sと一致する数は一通り)
            }
        }
        // same to sameの遷移. now -> now

        // leading-zeroの処理
        if (i) {
            for (int k = 1; k <= 9; k++) {
                // ndp += 1
            }
        }
        swap(dp, ndp);
    }
    // nowを答えに追加する場合があることに注意する.
    return 0;
}
```

## 例題
### 問題
1 以上 K 以下の整数のうち、十進表記における各桁の数字の総和が D の倍数であるようなものは何個でしょうか？ 10^9 +7 で割った余りを求めてください。
### 解法
各桁の和のmod Dを持って桁DPする.
### 提出
https://atcoder.jp/contests/dp/submissions/43926138
```cpp
#include <iostream>
#include <vector>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using mint = modint1000000007;
int main() {
    ios::sync_with_stdio(false);
    std::cin.tie(nullptr);
    string s; cin >> s;
    int n = s.size();
    // 問題固有な特徴量についての処理を記載する.
    int D; cin >> D;
    // dp: 上記の量をキーとするようなdp配列の宣言を記載.
    //     dpではs未満になることが確定したものの情報をもつ.
    vector<mint> dp(D);
    // now: sと一致しているものの状態の宣言を記載.
    int now = 0;
    for (int i = 0; i < n; i++) {
        // ndp: ndpの宣言を記載.
        vector<mint> ndp(D);
        int d = s[i] - '0';
        // 特徴量について遷移する
        for (int j = 0; j < dp.size(); j++) {
            for (int k = 0; k <= 9; k++) {
                // small to smallの遷移. dp -> ndp
                ndp[(j + k) % D] += dp[j];
            }
        }
        // same to smallの遷移. now -> ndp
        for (int k = 0; k < d; k++) {
            // 最初に0をつけるのは禁止.
            if (i | k) {
                ndp[(now + k) % D] += 1;
            }
        }
        // same to sameの遷移. now -> now
        now = (now + d) % D;
        // leading-zeroの処理
        if (i) {
            for (int k = 1; k <= 9; k++) {
                // ndp += 1
                ndp[k % D] += 1;
            }
        }
        swap(dp, ndp);
    }
    // nowを答えに追加する場合があることに注意する.
    if (!now) { dp[0]++; }
    cout << (dp[0]).val() << endl;

    return 0;
}
```
