---
title: 树状数组
date: 2021-11-24 23:41:42
tags: [Data Structure, Fenwick]
---
> 仅记录了树状数组一些操作。
>
> 参考https://oi-wiki.org/ds/fenwick/

## 操作

获取$c_i$管理的数组$a$中的数的个数。

``` c++
int lowbit(int x) {
  return x & -x; //x + 1 = -x
}
```

## 单点修改

``` c++
void add(int x, int v) {
  while (x <= n) {
    tr[x] += v;
    x += bowbit(x);
  }
}
```

## 单点查询

``` c++
int getPrefix(int x) {
  int ans = 0;
  while (x) {
    ans += tr[x];
    x -= lowbit(x);
  }
  return ans;
}
```

## 区间修改

``` c++
void update(int l, int r, int v) {
  add(l, v); 			//l及之后的父节点都加上v
  add(r + 1, -v); //(r + 1)及之后的父节点都减去v
}
```

## 区间查询

设$b$是维护序列$a$的差分数组，由差分数组的定义，有：$\displaystyle a_i=\sum_{i=1}^{r}b_i$,

有以下推导：
$$
\begin{eqnarray}
\displaystyle
\sum_{i=1}^{r}a_i&=&\sum_{i=1}^{r}\sum_{j=1}^{i}b_j \\
&=&\sum_{i=1}^{r}b_i\times(r-i+1) \\
&=&\sum_{i=1}^{r}b_i\times(r+1)-\sum_{i=1}^{r}b_i\times i
\end{eqnarray}
$$

``` c++
int b[MAXN], ib[MAXN]; //上述两个的数组（差分数组和数组i*bi）
int getPrefix(int* nums, int x) {
  int sum = 0, v = x + 1;
  while (x) {
    sum += v * b[x] - ib[x];
    x -= lowbit(x);
  }
  return sum;
}

int getSum(int x) {
  int ans = 0;
  while (x) {
    ans += getSum(nums, r) - getSum(nums, l - 1);
    x -= bowbit(x);
  }
  return ans;
}
```

## 构造树

``` c++
int tr[MAXN];
void initBIT() {
  for (int i = 1; i <= n; i++) {
    tr[i] += a[i];						//构造前缀和
    b[i] += a[i] - a[i - 1];	//构造差分数组
    int j = i + lowbit(i);
    if (j <= n) tr[j] += tr[i];
  }
}
```

## 组合形式

### 1.单点修改，单点查询

### 2.单点修改，区间查询

### 3.区间修改，单点查询

### 4.区间修改，区间查询

