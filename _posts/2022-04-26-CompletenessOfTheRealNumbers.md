---
title: 实数系的完备性
date: 2022-04-26 23:47:34
tags: 数学分析
mathjax: true
toc: true
---

## 实数系的公理、定理和性质

我们假设实数的完备性（连续性）的公理是：

0. **戴德金原理 （Dedekind completeness）**

	**Axiom** 若将实数集 $\mathbb{R} $ 分成两个子集 $S$ 和 $T$，满足：

	（1）$S \ne \varnothing$ ，$T \ne \varnothing$；

	（2）$\mathbb{R} = S \cap T$；

	（3）$\forall x \in S$，$\forall y \in T$ ，总有$x < y$.

	则 $\exists c \in \mathbb{R}$，$\forall a \in S$，$y \in T$，有 $a \leq c \leq b$，
	
	称其为实数集 $\mathbb{R}$ 的一个戴德金分割，记作$(S, T)$. 

其余7个关于连续性的基本定理：

1. **确界原理（least-upper-bound property）**

2. **单调有界定理（monotone convergence theorem）**

3. **闭区间套定理（nested convergence theorem）**

4. **有限覆盖定理（Heine-Borel theorem）**

5. **聚点定理（Bolzano-Weierstrass theorem）**

6. **致密性定理（Bolzano-Weierstrass theorem）**

7. **柯西收敛准则（Cauchy completeness）**

以及实数系的最重要性质：

8. **阿基米德性质（Archimedeasn property)**

	$\forall x,y \in \mathbb{R}$，$\exists n \in N_+$， 使得 $na > b$.

- 我们按照以下路线来证明以上诸定理的等价性：

	0.戴德金原理$\Rightarrow$1.确界原理$\Rightarrow$2.单调有界定理$\Rightarrow$3.闭区间套定理$\Rightarrow$4.有限覆盖定理$\Rightarrow$5.聚点定理$\Rightarrow$6.致密性定理$\Rightarrow$7.柯西收敛准则$\Rightarrow$1.确界原理

## 1. 戴德金原理 $\Leftrightarrow$ 确界原理

首先给出上确界的定义及确界原理的描述：

**Definition** 设 $E$ 是非空数集.若存在数 $\beta$ ，满足

1. $\forall x \in E$，有 $x \leq \beta$；

2. $\forall \varepsilon > 0$，$\exists x_0 \in E$，有 $\beta - \varepsilon < x_0$，

	则称 $\beta$ 是数集 $E$ 的**上确界**，表示为 $\beta = \sup E$.
	

**Theorem (确界原理)**  若非空数集 $E$ 有上界（下界），则数集 $E$ 存在唯一的上确界（下确界）.

**Proof** 首先，定义集合 $T = \{ a \in \mathbb{R} \vert \forall x \in E, a > x \}$ ， $S = \mathbb{R} \backslash E$，

**必要性**：

1. 因为 $E$ 有上界，所以 $\exists M \in \mathbb{R}$，$\forall x \in E$，有 $x \leq M$，令 $a = M + 1$，则 $\forall x \in E$，有 $x \leq M < M + 1 = a$， 故 $a \in T$，$T \ne \varnothing$， $S \ne \varnothing $；
2. 显然 $S \bigcup T = \mathbb{R}$；
3. 任取 $x \in S$，$ y \in T$，由 $x \in S$，$x \notin T$，所以 $\exists z \in E$，有 $z \geq x$. 又因为$z \in E$，而$y \in T$，故$z < y$，从而 $\forall x \in S$，$y \in T$，有 $x \leq z < y$，由戴德金原理，$\exists c \in \mathbb{R}$，$\forall x \in S$，$\forall y \in T$，有 $x \le c \le y$.

下面证明 $c = \sup E$：

1.  已证 $\forall x \in E$，有 $x \in S$. 所以 $\forall x \in E$，有 $x \le c$ ；

2. 因为 $\forall \varepsilon \in \mathbb{R}^+$，有 $c - \dfrac{\varepsilon}{x} < c$，所以 $c - \dfrac{\varepsilon}{2} \notin T$. 由 $T$ 的定义知，$\exists x \in E$，有 $x \ge c - \dfrac{\varepsilon}{2}$. 又因为 $c - \varepsilon < c - \dfrac{\varepsilon}{2}$ ，故 $c - \varepsilon < x$. 所以， $\forall \varepsilon \in \mathbb{R}^+$ ，$\exists x \in E$，有 $c - \varepsilon < x$；

	由上确界的定义知，$c = \sup E$ ， 即 $E$ 有上确界.  $\blacksquare$

**充分性**：

由 $T \ne \varnothing$， $S$ 有上界，有确界原理知，$S$ 有上确界. 同理，$T$ 有下确界. 设  $c_1 = \sup S$， $c_2 = \inf T$. 

下面寻找一 点 $c$ 满足 $\forall a \in S, b \in T$，有 $a \le c \le b$ . 

1. 若 $c_1 \in S$， 则取 $c = c_1$ 即可；

2. 若 $c_1 \notin S$，则 $c_1 \in T$，分如下两种情况讨论：

	（1）若 $c_2 \in T$，取 $c = c_2$ 即可；

	（2）若 $c_2 \notin T$，则 $c_2 \in S$. 又因为 $c_1 \in T$，则有 $c_2 < c_1$，$c_2 = \inf T$， 所以 $\exists y \in T$，有 $y < c_2 < x$，与条件矛盾，所以不存在该情况. 

综上，$\forall a \in S，b \in T$，总能找到 $c \in \mathbb{R}$，使得 $a \le c \le b$. $\blacksquare$

## 2. 确界原理 $\Rightarrow$ 单调有界原理

**Theorem (单调有界原理)** 单调有界数列必收敛. 

**Proof** 不妨设 $\{a_n\}$ 为单调递增数列，且有上界. 由确界原理知，$\{ a_n \}$ 存在上确界 $\beta$. 

由上确界的定义，$\forall \varepsilon > 0$， $\exists N \in \mathbb{Z}$，有 $\beta - \varepsilon < a_N$. 

对上述的 $N$，$\forall n > N$，有 $\beta - \varepsilon < a_N \le a_n < \beta + \varepsilon$，即 $\vert a_n - \beta \vert < \varepsilon $. 

所以 $\displaystyle \lim_{n \to \infty} a_n = \beta$. $\blacksquare$

## 3. 单调有界定理 $\Rightarrow$ 闭区间套定理

**Theorem (闭区间套定理)** 设有闭区间列 $\{[a_n, b_n]\}$，若：

（1）$[a_1,b_1] \supset [a_2, b_2] \supset \cdots \supset [a_n,b_n] \supset \cdots$；

（2）$\displaystyle \lim_{n \to \infty} (b_n - a_n) = 0$，

则存在唯一的 $c$ 属于所有区间，即 $\{c\} = \bigcap \limits_{n = 1}^{\infty} [a_n, b_n]$，且 $\lim \limits_{n \to \infty} a_n = \lim \limits_{n \to \infty} b_n = c$ .

**Theorem $(\ast)$** 若数列 $\{ a_n \}$ 和 $\{ b_n \}$ 满足以下两个条件：

（1） $\forall n \in \mathbb{Z}^+$，有 $a_n \le a_{n + 1} < b_{n + 1} \le b_n$；

（2 ）$\displaystyle \lim_{n \to \infty} (b_n - a_n) = 0$，

则存在唯一的 $c \in \mathbb{R}$，$\forall n \in \mathbb{Z}^+$，有 $a_n \le c \le b_n $，且 $\displaystyle \lim_{ n \to \infty } a_n = \lim_{ n \to \infty } b_n = c $ .  

**Proof** 由条件（1）知，$\{ a_n \}$ 为单调递增数列， 且有上界 $b$. 由单调有界定理，$\{a_n\}$ 收敛. $\exists c \in \mathbb{R}$，使得 $\displaystyle \lim_{n \to \infty} a_n = c$ . 同理 $\{b_n\}$ 收敛. 且有 $\displaystyle \lim_{n \to \infty} b_n =$ $\displaystyle  \lim_{n \to \infty} [(b_n - a_n) + a_n] =$ $\lim \limits_{n \to \infty} (b_n + a_n) + \lim\limits_{n \to \infty} a_n = c$.

下面证明 $ c \in \bigcap\limits_{n = 1}^{\infty}[a_n, b_n]$ 的存在性，由 $\sup \{a_n\} = \inf\{b_n\}$，由上确界的定义知， $\forall n \in \mathbb{Z}^+$，$a_n \le c \le b_n$. 

下面在证明唯一性，设 $\exists c' \ne c \in \mathbb{R}$，$\forall n \in \mathbb{Z}^+$，有 $a_n \le c' \le b_n$. 又因为 $\lim \limits_{n \to \infty} a_n = \lim\limits_{n \to \infty} b_n = c$，由夹逼定理知， $c = c'$. $\blacksquare$

## 4. 闭区间定理 $\Rightarrow$ 有限覆盖定理

**Theorem (有限覆盖定理)** 若开区间集 $\Gamma$ 覆盖了闭区间 $[a, b]$，则在 $\Gamma$ 中存在有限个开区间也覆盖了闭区间 $[a,b]$.

**Proof** 反证法，若 $\Gamma$ 中任意有限个开区间都不能覆盖闭区间 $[a,b]$ ，则将 $[a,b]$  二等分，可得到两个闭子区间 $[a. \dfrac{a + b}{2}]$，$ [\dfrac{a + b}{2}, b]$，则其中至少有一个不能被 $\Gamma$ 中的有限个开区间覆盖，记该闭区间为 $[a_1,b_1]$，再将 $[a_1,b_1]$ 二等分，得到 $[a_1, \dfrac{a_1 + b_1}{2}]$ ，$ [\dfrac{a_1 + b_1}{2}, b_1]$，则其中仍至少有一个不能被 $\Gamma$ 中的有限个开区间覆盖，记该闭区间为  $[a_2,b_2]$，如此下去，得到一个闭区间列 $\{[a_n,b_n\}$，满足：

（1）$[a_1,b_1] \supset [a_2, b_2] \supset \cdots \supset [a_n,b_n] \supset \cdots$；

（2）$\lim \limits_{ n \to \infty } ( b_n - a_n ) = \lim \limits_{ n \to \infty } \dfrac{ b - a }{ 2^n } = 0$；

（3）每个闭区间 $[a_n,b_n]$都不能被 $\Gamma $ 中的有限个开区间覆盖，

由闭区间套定理，存在唯一一个 $c \in \bigcup\limits_{n = 1}^{\infty} [a_n,b_n]$，且 $\displaystyle \lim_{n \to \infty} b_n = \lim_{n \to \infty} a_n = c$，显然 $c\in[a,b]$，则 $\exists (\alpha, \beta) \subset [a,b]$，使得 $c\in(\alpha, \beta)$，由 $\alpha < c < \beta$，且 
$$
a < \lim\limits_{n\to\infty} a_n = c = \lim\limits_{n\to\infty}b_n < \beta，
$$
由极限的保序性，$\exists n_0$ 使得 $[a_{n_0}, b_{n_0}]$ 可被 $\Gamma$ 中的开区间 $(\alpha, \beta)$ 覆盖，与（3）矛盾.

因此， $\Gamma$ 中存在有限个开区间也覆盖了闭区间 $[a,b]$. $\blacksquare$

## 5. 有限覆盖定理 $\Rightarrow$ 聚点定理

**Theorem (聚点定理)** 数轴上的任意有界无限点集 $E$ 至少有一个聚点.

**Proof** 由 $E$ 为有界点集，所以存在 $a$ , $b$ ，使得 $E \subset [a,b]$.

反证法	假若 $E$  中没有聚点，则 $\forall x \in [a, b]$， $x$ 都不是 $[a,b]$ 的聚点. 于是 $\forall \varepsilon_x > 0$，都使得 $(x - \varepsilon_x, x + \varepsilon_x)$ 中至多只有 $E$ 中有限多个点. 从而得到一个开区间集 $\Gamma =  \{(x - \varepsilon_x, x + \varepsilon_x) \vert x \in [a, b] \}$ ，其中每个开区间  $(x - \varepsilon_x, x + \varepsilon_x)$ 至多含有 $E$ 中有限多个点. 显然 $\Gamma$ 覆盖了闭区间 $[a,b]$，由有界覆盖定理，$\Gamma$ 中存在有限个开区间  $(x_1 - \varepsilon_1, x_1 + \varepsilon_1)$， $(x_2 - \varepsilon_2, x_2 + \varepsilon_2)$，$\cdots$，$(x_n - \varepsilon_n, x_n + \varepsilon_n)$   覆盖了闭区间 $[a,b]$，即
$$
E \in [a,b] \subset \bigcup \limits_{k = 1}^n (x_k - \varepsilon_k, x_k + \varepsilon_k)
$$
因为 $E$ 为无限点集，所以 $\bigcup \limits_{k = 1}^n (x_k - \varepsilon_k, x_k + \varepsilon_k)$ 中含有 $E$  中的无限多个点. 但是由 $(x_k - \varepsilon_k, x_k + \varepsilon_k) $ 中至多含有 $E$ 中的有限多个点，从而 $\bigcup \limits_{k = 1}^n (x_k - \varepsilon_k, x_k + \varepsilon_k)$  中也仅含有 $E$ 中有限多个点，得到矛盾.

所以 $E$ 中至少含有一个聚点. $\blacksquare$

## 6. 聚点定理 $\Rightarrow$ 致密性定理

**Theorem （致密性定理)**  任何有界数列$\{a_n\}$都存在收敛的子列.

**Proof**	**Case 1**：若数列 $\{a_n\}$ 中存在无限多项相等，设 $a = a_{n_1} = a_{n_2} = \cdots$  （$n_1 < n_2 < \cdots$），则 $\{a_{n_k}\}$ 为 $\{a_n\}$ 的收敛子列，即 $\lim \limits_{k \to \infty} a_{n_k} = a$ .

**Case 2**：若 $\{a_n\}$ 中没有无限多项相等，则数列 $\{a_n\}$ 在数轴上的点集 $E = \{a_n \vert n \in \mathbb{N}^+\}$ 必为有界无限点集. 由聚点定理，$E$ 中至少存在一个聚点.

对 $\varepsilon = 1$，在 $(a-1,a+1)$ 中含有点 $y_1 \in E$，则存在数列中的某项 $a_{n_1} = y_1$，从而 $a_{n_1} \in (a-1,a+1)$.

对 $\varepsilon = \dfrac{1}{2}$，在 $(a-\dfrac{1}{2},a+\dfrac{1}{2})$ 中含有 $E$ 中的无限多个点，则存在某点 $y_2 \in E \cap\{a_1,a_2,\cdots,a_{n_1}\}$，使 $y_2 = a_{n_2}$，且 $n_2 > n_1$. 依次下去，设已取到 $\{a_n\}$ 中的 $k$ 个点，满足 $n_k > \cdots > n_2 > n_1$，且 $a_i \in (a - \dfrac{1}{i}, a + \dfrac{1}{i})$，$ i=1,2,\cdots, k$ . 此时 $(a-\dfrac{1}{k+1},a+\dfrac{1}{k+1})$中仍含有 $E$ 中无限多个点，则可取到 $a_{n_{k+1}}\in (a-\dfrac{1}{k+1},a+\dfrac{1}{k+1})\cap(E \backslash\{a1,a2,\cdots,a_{n_k}\})$，使得 $y_{k+1} = a_{n_{k+1}}$，且 $n_k < n_{k+1}$，如此下去，可得到 $\{a_n\}$ 的子列 $\{a_{n_k}\}$ ，使得 $a_{n_k} \in (a-\dfrac{1}{k},a+\dfrac{1}{k})$，$k=1,2,\cdots$.

即 $\lim \limits_{k\to\infty} a_{n_k} =a$. $\blacksquare$ 

## 7. 致密性定理 $\Rightarrow$ 柯西收敛准则



## 8. 柯西收敛准则 $\Rightarrow$ 确界原理
