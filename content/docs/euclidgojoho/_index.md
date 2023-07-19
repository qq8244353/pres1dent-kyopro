---
title: ユークリッドの互除法
type: docs
---
# ユークリッドの互除法

## 概要
{{< katex display >}}
x = y \times d + m と表せるとき, gcd(x, y) = gcd(y, m)
{{< /katex >}}
## 例題 (ユークリッドの互除法で和を分解)
[ABC254 F - Rectangle GCD](https://atcoder.jp/contests/abc254/tasks/abc254_f)  
{{< katex >}} (i,j) {{< /katex >}} の値が{{< katex >}}A_i + B_j{{< /katex >}}であるとき,
{{< katex >}}1 \leq h_1, h_2, \leq H,  1 \leq w_1, w_2 \leq W {{< /katex >}}で囲われる短形領域のgcdを求めよ.  
簡単のために{{< katex >}}h_1 = 1, h_2 = H, w_1 = 1, w_2 = W{{< /katex >}}とする.  
求めるものは, 
{{< katex display >}}
gcd\Biggr(
\begin{array}{c}
gcd(A_1 + B_1, A_1 + B_2, \cdots, A_1 + B_W), \\ 
gcd( A_2 + B_1, A_2 + B_2, \cdots, A_2 + B_W), \\
\vdots \\
gcd( A_H + B_1, A_H + B_2, \cdots, A_H + B_W) \\
\end{array}
\Biggr) \quad (1)
{{< /katex >}}
{{< katex >}} A_i + B_j =  (A_i + B_{j + 1}) \times 1 + B_j - B_{j+1} {{< /katex >}}  
なのでユークリッドの互除法より,  
{{< katex >}} gcd(A_i + B_j, A_i + B_{j + 1}) = gcd(B_i - B_{j + 1}, A_i + B_{j + 1}) {{< /katex >}}  
よって, 

{{< katex display >}}
\begin{array}{rl}
gcd(A_i + B_1, A_i + B_2, \cdots, A_i + B_W) & = gcd(B_1 - B_2, A_i + B_2, \cdots, A_i + B_W) \\
& \vdots \\
& = gcd(B_1 - B_2, B_2 - B_3, \cdots, A_i + B_W) \\
\end{array}
{{< /katex >}}
同様にして,  
{{< katex display >}}
\begin{array}{rl}
gcd(A_1 + B_W, A_2 + B_W, \cdots, A_H + B_W) & = gcd(A_1 - A_2, A_2 + B_W, \cdots, A_H + B_W) \\
& \vdots \\
& = gcd(A_1 - A_2, A_2 - A_3, \cdots, A_H + B_W) \\
\end{array}
{{< /katex >}}
なので,
{{< katex display >}}
(1) = gcd(A_1 - A_2, \cdots, A_{H-1} - A_H, B_1 - B_2, \cdots, B_{W-1} - B_W, A_H + B_W)
{{< /katex >}}
これはAとBの区間和なので, セグ木に乗せれば各クエリO(log(H) + log(W) + 1)で解ける
