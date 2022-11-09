---
title: $\LaTeX$ 笔记（更新中）
date: 2022-03-26
tags: [LaTeX]
mathjax: true
---
> 本笔记仅为本人自学时为便于自己的理解和记忆而做的笔记，可能存在概念不准确的地方。
>
> 推荐使用<a href="https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes#What_is_LaTeX.3F">Overleaf</a>，<a href="http://zynd.net/doku.php?id=wiki:latex_mathematics">参考网站</a>。

## 基础

在$\LaTeX$中，所有的命令都以 `\`开头。一般形式如下：

``` LaTeX
\命令[参数]{参数}
```

一个$\LaTeX$文档简单的结构为：

``` LaTeX
\documentclass[utf-8]{article}
\usepackage{}


\title{This is a Title}
\auther{The name of the auther}
\date{\today}

\begin{document}

\maketitle

The body of the article.
\end{document}
```

1. 文档通常以`\documentclass{}`开头，它申明的文档的类型

``` LaTeX
\documentclass[utf-8]{article}
```

2. `\usepackage`为文档需要导入的宏包，类似C++中利用include导入头文件。
3. 在`\begin{document}`前的内容都成为前言（Preamble），通常内容为：

```` LaTeX
\title{标题}
\author{作者}
\date{\today}
````

3. `\maketitle`会在该位置生成2即前言。
4. 文章的内容为：

``` LaTeX
\begin{document}
	文章内容。
\end{document}
```

## 文档的类

### 基本格式

``` LaTex
\documentclass[<option>]{<class>}
```

### 使用中文

替换编译器为XeLaTeX或LuaLaTeX，参考<a href="https://jdhao.github.io/2018/03/29/latex-chinese.zh/">博客</a>。

1. 使用ctexart类文档

	``` LaTeX
	\documentclass[utf8]{ctexart}
	```

2. 使用ctex宏包

	``` LaTeX
	\usepackage[utf8]{ctex}
	```

## 常用排版格式

``` LaTeX
\textbf{加粗}
\textit{斜体}
\underline{下划线}
\emph{强调}

\begin{itemize}
	\item 第一项
	\item 第二项
\end{itemize}

\begin{enumerate}
	\item 枚举1
	\item 枚举2
\end{enumerate}

行插入公式输入：
$...$ = \(...\) = \begin{math}...\end{math}
ps: \displaystyle

独行插入公式：
\[...\] = \begin{equation}...\end{equation} = \begin{displaymath}...\end{displaymath}
ps: $$...$$is discouraged as it can give inconsistent spacing, and may not work well with some math packages.

\newline 或 \\ %换行
```

## 数学公式

<a href="https://www.caam.rice.edu/~heinken/latex/symbols.pdf">参考</a>

$\LaTeX$需要知道文档的哪些内容表示为文本，哪些内容表示为数学公式，因此需要先声明数学公式的特殊环境，可以分为以下两类：

- `text`为文本公式，即行内公式，显示在行内。

- `displaystyle`为显示公式，即行间公式，显示在独立的一行。

	数学环境及其快捷方式如下表：
	
|         类型         | 行内公式  |   行间公式   |
| :---------------: | :-------: | :----------: |
|       **环境**     |   math  | displaystyle |
| **$\LaTeX$快捷方式** | <code>\(…\) </code> |  <code>\[…\]</code>   |
|  **$\TeX$快捷方式**  |  <code>$…$</code>  | <code>$…$</code>  |

一些符号比如$\lim_{i \to \infty}$，会被压缩，可以在其之间加上`\displaystyle`使其在行内美观展现，其效果为：$\displaystyle \lim_{i \to \infty}$。

### 普通符号和特殊符号

#### 普通符号

在数学公式中，这些符号可以直接输入：+-=!/()[]<>|':*，而其他符号则需要通过公式实现输入。

#### 特殊符号

在数学公式中，如`#，%，$，{，}，~，\\，_，^`在公式中有特殊的用途，需要在其前面加上`\`来转译。

### 运算符

需要注意的是，在$\LaTeX$中，$sin$和$\sin$是有所不同的。下表为同类运算符的各例，同类中其他符号与示例类似。

|        公式        |         符号         |
| :----------------: | :------------------: |
|        \sin        |        $\sin$        |
|       \sinh        |       $\sinh$        |
|      \arcsin       |      $\arcsin$       |
|      \log_2 x      |      $\log_2 x$      |
|       \exp A       |       $\exp A$       |
|       \bmod        |       $\bmod$        |
| a \equiv 1 \pmod b | $ a\equiv 1 \pmod b$ |

### 希腊字母表

- 大写字母只需将公式首字母换为大写即可

|           公式            |             字母              |       公式        |         字母          |
| :-----------------------: | :---------------------------: | :---------------: | :-------------------: |
|       \alpha<br />A       |       $\alpha$<br />$A$       |        \nu        |         $\nu$         |
|       \beta<br />B        |       $\beta$<br />$B$        |        \xi        |         $\xi$         |
|    \gamma<br />\Gamma     |    $\gamma$<br />$\Gamma$     |     \omicron      |      $\omicron$       |
|    \delta<br />\Delta     |    $\delta$<br />$\Delta$     |        \pi        |         $\pi$         |
| \epsilon<br />\varepsilon | $\epsilon$<br />$\varepsilon$ | \rho<br />\varrho | $\rho$<br />$\varrho$ |
|           \zeta           |            $\zeta$            |      \sigma       |       $\sigma$        |
|           \eta            |            $\eta$             |       \tau        |        $\tau$         |
|   \theta<br />\vartheta   |   $\theta$<br />$\vartheta$   |     \upsilon      |      $\upsilon$       |
|           \lota           |            $\iota$            | \phi<br />\varphi | $\phi$<br />$\varphi$ |
|          \kappa           |           $\kappa$            |       \chi        |        $\chi$         |
|          \lambda          |           $\lambda$           |       \psi        |        $\psi$         |
|            \mu            |             $\mu$             |      \omega       |       $\omega$        |

### 角标

角标分为上下、上下和左右组合的角标

#### 组合角标

| 公式 | 符号  |
| :--: | :---: |
| a^b  | $a^b$ |
| a_b  | $a_b$ |
| ^ba  | $^ba$ |
| _ba  | $_ba$ |

#### 上标和下标

|   公式    |    符号     |
| :-------: | :---------: |
|  \bar{a}  |  $\bar{a}$  |
| \acute{b} | $\acute{b}$ |
| \check{c} | $\check{c}$ |
| \breve{d} | $\breve{d}$ |
| \grave{e} | $\grave{e}$ |
|  \dot{f}  |  $\dot{f}$  |
|  \hat{g}  |  $\hat{g}$  |
| \tilde{h} | $\tilde{h}$ |

### 分数、二项式和根

分数的公式为：`\frac{}{}`，二项式的公式为：`\binom{}{}`。

例如：

|        公式         |         符号          |
| :-----------------: | :-------------------: |
| \frac{n!}{k!(n-k)!} | $\frac{n!}{k!(n-k)!}$ |
|    \binom{n}{k}     |    $\binom{n}{k}$     |

分数可层层嵌套，例如：`\frac{1}{1+\frac{1}{1+\frac{1}{1+x}}}`输出为：
$$
\frac{1}{1+\frac{1}{1+\frac{1}{1+x}}}
$$
由于多层分数嵌套或行内分数会使字符越来越小，可以使用`\tfrac{}{}`或`\dfrac{}{}`强制使用`\textstyle`或`\displaystyle`，同理二项式也有`\tbinom{}{}` 和`\dbinom{}{}`。

例如：`\dfrac{1}{1+\dfrac{1}{1+\dfrac{1}{1+x}}}`输出为：
$$
\dfrac{1}{1+\dfrac{1}{1+\dfrac{1}{1+x}}}
$$

#### 繁分数

对于繁分数，可以使用`\cfrac`命令。例如：

``` LaTeX
\begin{equation}
a = a_0 + \cfrac{1}{a_1
		+ \cfrac{1}{a_2
		+ \cfrac{1}{a_3}}}
\end{equation} 
```

输出如下：
$$
\begin{equation}
a = a_0 + \cfrac{1}{a_1
		+ \cfrac{1}{a_2
		+ \cfrac{1}{a_3}}}
\end{equation}
$$

#### 根式

根式使用`\sqrt[]{}`来表示，其中`[]`的内容为可选选项，对于二次根式可以省略。例如：

|    公式     |     输出      |
| :---------: | :-----------: |
|  \sqrt{x}   |  $\sqrt{x}$   |
| \sqrt[3]{x} | $\sqrt[3]{x}$ |

### 累加、累乘和积分

累加符号和累乘符号的命令分别为：`\sum`、`\prod`，`^`和`_`分别指示上下限。例如：

$\sum_{i=1}^{n}a_i$、$\prod_{i=1}^{n}a_i$，使用`\displaystyle`防止压缩。
$$
\sum_{i=1}^{n}a_i \\ \prod_{i=1}^{n}a_i
$$
