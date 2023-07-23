---
title: 区間DP
type: docs
---
# 区間DP

<!-- f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi -->
## 概要
2つ合わせて消すみたいな操作の数え上げに使える.  
{{< katex >}}i, j(i < j){{< /katex >}}番目に対して操作するためには{{< katex >}}(j - i) = 0 (mod 2){{< /katex >}}かつ,
{{< katex >}}[i + 1, j - 1]{{< /katex >}}が削除可能であることが必要.

