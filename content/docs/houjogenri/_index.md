---
title: 包除原理
type: docs
---
# 包除原理

<!-- f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi -->
## 概要
包除原理とは以下の性質.
{{< katex display >}}
|A_1\cup A_2 \cup \cdots \cup A_n| = \sum_{k=1}^n(-1)^{k-1} \sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |A_{i_1} \cup A_{i_2} \cup \cdots \cup A_{i_k}|
{{< /katex >}}
包助原理とド・モルガンの法則を組み合わせることで以下の式を得る.
{{< katex display >}}
\begin{array}{rl}
    |A_1\cap A_2 \cap \cdots \cap A_n| &= \overline{|\overline{A_1}\cup \overline{A_2} \cup \cdots \cup \overline{A_n}|} \\
    &= |\Omega| - |\overline{A_1}\cup \overline{A_2} \cup \cdots \cup \overline{A_n}| \\
    &= |\Omega| - \displaystyle\sum_{k=1}^n(-1)^{k-1} \displaystyle\sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |\overline{A_{i_1}} \cup \overline{A_{i_2}} \cup \cdots \cup \overline{A_{i_k}}| \\
    &= |\Omega| + \displaystyle\sum_{k=1}^n(-1)^{k} \displaystyle\sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |\overline{A_{i_1}} \cup \overline{A_{i_2}} \cup \cdots \cup \overline{A_{i_k}}| \\
\end{array} \\
{{< /katex >}}
dp配列を以下のように定義すると.  
({{< katex >}} k = 0{{< /katex >}} のとき,条件がないので全体集合になるのは直感的に正しい).  
{{< katex display >}}
dp[k] = \Biggl\{ \begin{array}{cl}
    \displaystyle\sum_{1\leq i_1 < i_2 < \cdots < i_k \leq n} |\overline{A_{i_1}} \cup \overline{A_{i_2}} \cup \cdots \cup \overline{A_{i_k}}| \quad & (k \geq 1) \\
    |\Omega| & (k = 0)
    \end{array}
{{< /katex >}}
包助原理に関するテクを得る.
{{< katex display >}}
|A_1\cap A_2 \cap \cdots \cap A_n| = \sum_{k=0}^n(-1)^k dp[k]
{{< /katex >}}
ここの行間理解するの大変だった
