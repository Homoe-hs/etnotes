---
aliases: []
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
![[事件跟踪#^ynnexo]]

考点就三个内容，下面简单梳理一下解题。

# 1. Microstrip line

这里必给的参数有，微带线的特征阻抗 $Z_{0}$，基底的相对介电常数 $\epsilon_{r}$，频率 $f$ 和线宽 $w$ 或者微带线到接地的高 $h$。然后按照下面的顺序逐步求解参数即可。

这里覆盖了 1-9 页的内容。

## 1.1. 计算 $\dfrac{w}{h}$

这里需要先假设情况，然后排除。一般来说不会出现两种情况都可行的情况。

![[微带线宽高比经验计算式]]

## 1.2. 计算有效参数 Effective parameters

### 1.2.1. Effective relative permittivity

再补充一个自由空间的波阻抗 $\eta_{0} = 120\pi \pu{ \Omega }=377\pu{ \Omega }$

![[自由空间波阻抗计算式]]

有了宽高比+自由空间波阻抗就能计算一系列有效参数。

![[CPW 有效相对介电常数计算式]]

这里我们用第二个公式来近似。
### 1.2.2. Effective mirostrip line width

![[有效微带线宽度计算式]]

### 1.2.3. Effective cut-off frequency

![[有效截止频率计算式]]

## 1.3. 计算导波波长

![[导波波长计算式]]

## 1.4. 计算频率依赖参数

### 1.4.1. 频率依赖的有效相对介电常数

这里有两个模型，我觉得 Getsinger 应该常用一点。

![[频率依赖的有效介电常数的基于 Getsinger 模型的简化经验计算公式]]

还是给出 Edwards 和 Owens 的

![[Edwards 和 Owens 提出的频率依赖的有效介电常数的计算式]]

### 1.4.2. 频率依赖的导波波长

![[频率依赖的导波波长计算式]]

### 1.4.3. 频率依赖的有效微带线宽度

![[频率依赖的有效微带线宽度计算式]]

### 1.4.4. 频率依赖的特征阻抗

![[频率依赖的特征阻抗计算式]]

# 2. 网络参数

这里覆盖 10-16 页的内容。

根据他的作业来看，极有可能还是从 ABCD 参数开始入手（ABCD 转其他参数比 S 转其他参数简单多了）。我们先补充两个参数，[[混合参数]]和[[第二类混合参数]]。
![[混合参数矩阵]]
![[第二类混合参数矩阵]]

然后再补充一点矩阵的知识，行列式逆矩阵的求解，

![[行列式]]

![[逆矩阵]]

## 2.1. 传输线的ABCD 参数
![[transmission line.drawio.png|400]]


对于特征阻抗 $Z_{c}$，相位常数 $\beta$ 以及长度 $l$。有 ABCD 参数为，
$$
\begin{bmatrix}A&B\\C&D\end{bmatrix}=\begin{bmatrix}\cos\beta l&jZ_c\sin\beta l\\jY_c\sin\beta l&\cos\beta l\end{bmatrix}
$$

## 2.2. ABCD 转 Z 参数

$$
\begin{bmatrix}
Z_{11} & Z_{12} \\
Z_{21} & Z_{22}
\end{bmatrix}

=

\begin{bmatrix}
\dfrac{A}{C} & \dfrac{AD-BC}{C} \\
\dfrac{1}{C} & \dfrac{D}{C}
\end{bmatrix}
$$
这里可以求一下 Z 参数矩阵的行列式，$det (Z) = \dfrac{B}{C}$

## 2.3. ABCD 转 Y 参数

这里其实也可以求 Z 参数矩阵的倒。和 ABCD 推结果一样，看你喜好。
$$
\begin{bmatrix}
Y_{11} & Y_{12} \\
Y_{21} & Y_{22}
\end{bmatrix}

=

\begin{bmatrix}
\dfrac{D}{B} & \dfrac{BC-AD}{B} \\
\dfrac{-1}{B} & \dfrac{A}{B}
\end{bmatrix}
$$

## 2.4. ABCD 转 H 参数

$$
\begin{bmatrix}
H_{11} & H_{12} \\
H_{21} & H_{22}
\end{bmatrix}

=

\begin{bmatrix}
\dfrac{B}{D} & \dfrac{AD-BC}{D} \\
\dfrac{-1}{D} & \dfrac{C}{D}
\end{bmatrix}
$$
求一下 H 参数的行列式，$det (H) = \dfrac{A}{D}$

## 2.5. ABCD 转 G 参数

$$
\begin{bmatrix}
G_{11} & G_{12} \\
G_{21} & G_{22}
\end{bmatrix}

=

\begin{bmatrix}
\dfrac{C}{A} & \dfrac{BC-AC}{A} \\
\dfrac{1}{A} & \dfrac{B}{A}
\end{bmatrix}
$$

# 3. 背景说明

这一部分的内容就多了（

# 4. 第三章的传输线 

不考也不需要史密斯圆图，但是要考传输线的内容。估计是纯手算的阻抗匹配。





