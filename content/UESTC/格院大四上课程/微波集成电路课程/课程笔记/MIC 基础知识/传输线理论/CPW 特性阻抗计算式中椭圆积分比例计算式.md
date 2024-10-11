---
title: CPW 特性阻抗计算式中椭圆积分比例计算式
date: 2023-12-27 15:20
aliases: 
tags: 
publish: "true"
---
$$
\begin{aligned}
\frac{K(k)}{K'(k)}&\approx\frac{1}{\pi}\mathrm{ln}\bigg(2\frac{1+\sqrt{k}}{1-\sqrt{k}}\bigg) ~ 0\leq k\leq0.707\\\\
\frac{K'(k)}{K(k)}&\approx\frac{1}{\pi}\mathrm{ln}\bigg(2\frac{1+\sqrt{k'}}{1-\sqrt{k'}}\bigg) ~ 0.707<k\leq1
\end{aligned}
$$
$k$ 为 [[CPW 有效相对介电常数参数 k 计算式|CPW 有效相对介电常数计算式中的参数]]；$k'=\sqrt{ (1-k^{2}) }$