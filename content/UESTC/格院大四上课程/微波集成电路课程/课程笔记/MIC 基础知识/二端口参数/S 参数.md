---
title: S 参数
date: 2023-11-11 11:25
modification date: 2023 十一月 11日 星期六 11:25:56
aliases:
  - Scattering parameters
  - S-parameters
  - 散射参数
tags: 
publish: "true"
---
S 参数是一种用于描述多端口网络中**信号传输和散射特性**的重要工具，是一个无量纲参数。

在射频电路中，当信号进入一个器件或网络时，由于阻抗不匹配、器件特性等因素，部分信号会被**反射**，部分信号会在器件内传输并被**透射**或**吸收**。S参数用于量化这种**散射行为**，具体描述了每个端口的输入信号如何在多个端口上被分配。其核心是通过 **S参数矩阵**来表达输入和输出信号的关系。

对于二端口网络，S 参数的定义如下，

- S11 为输入端反射系数（输入匹配）
- S12 为反向传输系数（隔离）
- S21 为正向传输系数（增益/差损）
- S22 为输出端反射系数 （输出匹配）

![[用散射参数描述二端口网络.jpeg]]

当有 N 个端口的时候，S 参数是一个 $N\times N$ 的矩阵。有，

$$
S_{ij}=\frac{b_{i}}{a_{j}}\Bigg|_{a_{k}-0},k\neq j ,\quad S_{ij}=\frac{\mathrm{V}_{i}^{-}}{\mathrm{V}_{j}^{+}}\Bigg|_{\mathrm{V}_{k}^{-}-0},k\neq j
$$
S 参数下表的第一项为响应，第二项为源。

对于一个互易网络，有
$$
\begin{bmatrix}
S
\end{bmatrix}
=
\begin{bmatrix}
S
\end{bmatrix}
^{T}
$$
对于一个无损的网络，有
$$
\begin{bmatrix}S\end{bmatrix}^{T*}\begin{bmatrix}S\end{bmatrix}=\begin{bmatrix}I\end{bmatrix}
$$
，或者写成，
$$
\begin{bmatrix}S\end{bmatrix}^{H}\begin{bmatrix}S\end{bmatrix}=\begin{bmatrix}I\end{bmatrix}
$$
即 S 参数是一个[[酉矩阵]]。

