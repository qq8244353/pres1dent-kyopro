---
title: 包除原理
type: docs
---
# 包除原理

<!-- f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi -->
## 概要
包除原理とは以下の性質.
{{< katex display >}}
|A_1\cup A_2 \cup \cdots \cup A_n| = \sum_{k=1}^n(-1)^{k-1} \sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |A_{i_1} \cap A_{i_2} \cap \cdots \cap A_{i_k}|
{{< /katex >}}
## 包除原理dpのテク
包助原理とド・モルガンの法則を組み合わせることで以下の式を得る.
{{< katex display >}}
\begin{array}{rl}
    |A_1\cap A_2 \cap \cdots \cap A_n| &= \overline{|\overline{A_1}\cup \overline{A_2} \cup \cdots \cup \overline{A_n}|} \\
    &= |\Omega| - |\overline{A_1}\cup \overline{A_2} \cup \cdots \cup \overline{A_n}| \\
    &= |\Omega| - \displaystyle\sum_{k=1}^n(-1)^{k-1} \displaystyle\sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |\overline{A_{i_1}} \cap \overline{A_{i_2}} \cap \cdots \cap \overline{A_{i_k}}| \\
    &= |\Omega| + \displaystyle\sum_{k=1}^n(-1)^{k} \displaystyle\sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |\overline{A_{i_1}} \cap \overline{A_{i_2}} \cap \cdots \cap \overline{A_{i_k}}| \\
\end{array} \\
{{< /katex >}}
dp配列を以下のように定義すると.  
({{< katex >}} k = 0{{< /katex >}} のとき,条件がないので全体集合になるのは直感的に正しい.)  
{{< katex display >}}
dp[k] = \Biggl\{ \begin{array}{cl}
    \displaystyle\sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |\overline{A_{i_1}} \cap \overline{A_{i_2}} \cap \cdots \cap \overline{A_{i_k}}| \quad & (k \geq 1) \\
    |\Omega| & (k = 0)
    \end{array}
{{< /katex >}}
包助原理に関するテクを得る.
{{< katex display >}}
|A_1\cap A_2 \cap \cdots \cap A_n| = \sum_{k=0}^n(-1)^k dp[k]
{{< /katex >}}
ここの行間理解するの大変だった
<!-- ## ABC309 G - Ban Permutation -->
<!-- https://atcoder.jp/contests/abc309/tasks/abc309_g   -->
<!-- **問題文**   -->
<!-- {{<katex>}}(1,2,\cdots,N){{< /katex>}} の順列{{<katex>}}P=(P_1 ,P_2 ,\cdots,P_N){{< /katex>}}のうち、以下の条件を満たすものの個数を{{<katex>}}998244353{{< /katex>}} で割ったあまりを求めてください。   -->
<!-- {{<katex>}}1≤i≤N{{< /katex>}}を満たす全ての整数{{<katex>}}i{{< /katex>}}に対して、{{<katex>}}∣P_i−i∣≥X{{< /katex>}}である。   -->
<!---->
<!-- **制約**   -->
<!-- - {{<katex>}}1≤N≤100{{</ katex>}} -->
<!-- - {{<katex>}}1≤X≤5{{</ katex>}} -->
<!-- - 入力はすべて整数   -->
<!---->
<!-- **解説**   -->
<!-- {{<katex>}}|P_i-i| < X{{</ katex>}}である{{<katex>}}i{{</ katex>}}についての情報を持ちながらDPすれば解決.   -->
<!-- {{<katex>}}dp[i][j][k] = {{</ katex>}} (i番目までみて, j個について -->
