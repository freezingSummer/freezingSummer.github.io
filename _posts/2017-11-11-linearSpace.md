---
layout: post
tags: mathematica
title: 线性空间
---

最近忙着复习线性代数的期中考试，整整一周都没有写博客了。今天考完，来总结一下最近学到的东西。课本上都有的就不在赘述，在此记录一些独特的视角与思考。

线性代数有很多定义，不同的教科书教的内容也有所不同，基本都是从向量、矩阵入手，但线性代数远远不止于此。

# 元素并非向量的线性空间

书上介绍的线性空间一般是向量空间，其元素自然一般是向量，简单来说，在其上满足对加法与数乘的封闭性，就可以是向量空间。但是要想讲这个概念推广，就必须给出公理化的定义，本文着重介绍元素不是向量的线性空间及其应用，最后给出一些十分有趣的应用。

元素不是向量的这种推广在数学或者物理领域都有很大的应用。

### 线性空间的定义

若集合\\(V\\)满足如下十条公理，则称其为一个线性空间：

 1. （对加法封闭）\\(\forall x,y \in V, x+y \in V\\)
 2. （对数乘封闭）\\(\forall x \in V, \forall a \in R, ax \in V\\)
 3. （加法交换律) \\(x+y=y+x\\)
 4. （加法结合律) \\(x+(y+z)=(x+y)+z\\)
 5. （存在零元）\\(\exists 0 \in V, x+0=x\\)
 6. （存在加法逆元） \\(\forall x \in V, \exists(-x)\in V, x+(-x)=0\\)
 7. （数乘结合律）\\(a(bx)=(ab)x\\)
 8. （对元素加法分配率）\\(a(x+y)=ax+ay\\)
 9. （对实数加法分配率）\\((a+b)x=ax+bx\\)
 10. （存在单位元）\\(\forall x \in V, \exists 1 \in V, 1x = x\\)
 
其实我并不很喜欢套用公理，而更喜欢直观理解，但是在进行概念的推广时，总需要有据可循，这就需要严格按照公理来推广。

## 线性空间举例

实数集、复数集和一些向量的集合在此不再赘述，这里介绍一些不易想到却十分有用的线性空间。

1.多项式集

全部多项式组成的集合是一个线性空间，其中元素形式如下： 
\\[f(x)=c_0+c_1x+c_2x^2+...+c_nx^n=\sum_{i=0}^nc_ix^i\\]
其中\\(n\\)可以取任意自然数，甚至趋于无穷。这个线性空间的是无穷维的，其基即为\\(x^i\\)。

2.\\([a,b]\\)上所有连续函数的集合是一个线性空间，记为\\(C(a,b)\\)

3.齐次线性微分方程的所有解形成的集合是一个线性空间（必须是齐次的，即常数项为0），如\\(y\'\'+ay'+y=0\\)的所有解形成的集合。

### 模|x|推广到范数||x||

刚学习到线性代数内积的时候，十分不理解为啥这里向量的长度要变成双竖线，当意识到线性空间不一定是向量组成的以后，这就很好理解了。\\(\vert x \vert\\)代表向量或者复数\\(x\\)的模，但是对于任意一个线性空间，其元素不一定有“长度”这样能够直观理解的概念，所有用“范数”来描述其度量。

要定义范数，先要定义两个元素的内积。凡是具有如下四个公理的\\(V\\)上的二元运算\\((x,y)\\)，都可以被定义为内积：

 1. \\((x,y)=(y,x)\\)
 2. \\((x,y+z)=(x,y)+(x,z)\\)
 3. \\(c(x,y)=(cx,y)\\)
 4. \\((x,x)\ge 0,当且仅当x=0时取等 \\)
 
于是范数被定义为\\(\vert \vert x \vert \vert=(x,x)^{\frac{1}{2}}\\)

范数的一个典型性质是：
\\[\vert(x,y)\vert \le \vert \vert x \vert \vert \  \vert \vert y \vert \vert\\]
若定义\\(C(a,b)\\)上的内积\\((f,g)=\int_a^bf(x)g(x)dx\\)，便可以得到著名的Cauchy-Schwarz不等式：
\\[(f,g)^2=(\int_a^bf(x)g(x)dx)^2\le(\int_a^bf^2(x)dx)(\int_a^bg^2(x)dx)=\vert \vert f \vert \vert^2 \ \vert \vert g \vert \vert^2\\]

同一个线性空间中可以定义多种内积。

### 子空间、基与线性无关

子空间从名字上就可以容易理解，如果\\(V\\)的一个子集\\(W\\)本身也是一个线性空间，那么\\(W\\)就是\\(V\\)的一个子空间。

若\\(V\\)中\\(n\\)个互异元素满足：
\\[\sum_{i=1}^nc_ix_i=0,当且仅当c_1=c_2=...=c_n=0\\]
则称\\(x_1,x_2,...,x_n\\)是线性无关的。也就是说\\(x_1,x_2,...,x_n\\)中的任意一个元素都无法表示为其他元素的线性组合。

当\\(V\\)的某个子空间\\(W\\)中的每一个元素都可以表示为\\(x_1,x_2,...,x_n\\)的线性组合时，称\\(x_1,x_2,...,x_n\\)是\\(W\\)的一组基，\\(W\\)由\\(x_1,x_2,...,x_n\\)张成。张成\\(W\\)所需的线性无关元素个数\\(n\\)被称为\\(W\\)的维数，记为\\(dim(W)=n\\)

### 正交性、投影

\\(V\\)中元素\\(x,y\\)是正交的，当且仅当\\((x,y)=0\\)。从这个定义可知0与任意元素都是正交的，这和高中的定义不同，高中定义零向量平行于任意向量，而不垂直。

若一组基\\(S=\lbrace x_1,x_2,...,x_n\rbrace\\)中，任意两个元素都互相正交，则称\\(S\\)为一组正交基，又若\\(S\\)中所有元素范数为1，则称\\(S\\)为一组标准正交基。

类似向量的投影公式\\(Proj_\vec{b}\vec{a}=\frac{\vec{b} \cdot \vec{a}}{\vec{b}\cdot \vec{b}}\vec{b}\\)，我们定义\\(V\\)中\\(a\\)在\\(b\\)上的投影为\\(\frac{(a,b)}{(b,b)}b\\)。

利用对某个元素的投影，可以得到对某个子空间的投影。设\\(S=\lbrace x_1,x_2,...,x_n\rbrace\\)是\\(V\\)的子空间\\(W\\)的一组标准正交基，则\\(y\in V\\)在\\(S\\)的投影\\(p(y)=\sum_{i=1}^n(y,x_i)x_i\\)。

这里定义再一次与高中不同，高中定义的投影是一个实数，而这里投影是一个向量或者\\(V\\)中的一个元素。

## 标准正交基的构造--Gram-Schmidt方法

现在有任意一组基\\(S=\lbrace x_1,x_2,...,x_n\rbrace\\)，希望将其改造为一组标准正交基\\(R=\lbrace e_1,e_2,...,e_n\rbrace\\)，可以采用如下方法：

#### 正交化

取：

\\(y_1=x_1\\)

\\(y_2=x_2-\frac{(x_2,y_1)}{(y_1,y_1)}y_1\\)，第二项就是\\(x_2\\)在\\(y_1\\)方向的投影，即将\\(x_2\\)中平行于\\(y_1\\)的投影减掉，得到剩余的只垂直于\\(y_1\\)的部分，通过在二维情况作图可以很好理解

\\(y_3=x_3-\frac{(x_3,y_1)}{(y_1,y_1)}y_1-\frac{(x_3,y_2)}{(y_2,y_2)}y_2\\)，类似地，将\\(x_3\\)中垂直于\\(y_1,y_2\\)的分量分别减去

\\(...\\)

\\(y_n=x_n-\sum_{i=1}^{n-1}\frac{(x_n,y_i)}{(y_i,y_i)}y_i\\)

#### 标准化（单位化）

取\\(e_i=\frac{y_i}{\vert\vert y_i\vert\vert}\\)

至此，完成了对\\(S\\)的改造，使其成为标准正交基\\(R\\)。

### 最优逼近--傅里叶级数

设\\(S\\)是\\(V\\)的一个子空间\\((S\ne V)\\)，显然无法用\\(S\\)的一组标准正交基去表示\\(V\\)中的全部元素，但是我们常常只能用\\(S\\)中的元素，这就需要找到一个最接近答案的最优解。

对于\\(x\in V\\)，\\(S\\)中最接近\\(x\\)的元素，就是\\(x\\)在\\(S\\)的投影\\(p(x)\\)。

这种方法的典型应用就是最小二乘法解不相容的线性方程组，或者求回归直线。在此引入另一个令人惊奇地推导，用投影推导出傅里叶级数：

任何一个周期函数，都可以表示为有限个或无限个三角函数的线性组合，这个是傅里叶在研究热传导时得到的结论，从而开创了傅里叶级数。

我们取周期为\\([0,2\pi]\\)，通过伸缩就可以轻易地推广到周期为任意正数的函数。

考虑线性空间\\(C(0,2\pi)\\)，我们用\\(C(0,2\pi)\\)的一个三角函数子空间\\(S\\)中的元素，来逼近\\(C(0,2\pi)\\)中的任意函数。

首先我们要构造\\(S\\)的一组标准正交基。

定义内积\\((f,g)=\int_0^{2\pi}f(x)g(x)dx\\)。

则\\(S\\)中一组正交基为
\\[\lbrace 1,\sin x,\cos x,\sin 2x,\cos 2x,...,\sin nx,\cos nx \rbrace\\]

这是一组正交基因为有：
\\((1,\sin nx)=0\\)

\\((1,\cos nx)=0\\)

\\((\sin nx,\sin mx)=0(n\ne m)\\)

\\((\cos nx,\cos mx)=0(n\ne m)\\)

\\((\sin nx,\cos mx)=0\\)

证略。

下面将其变为一组标准正交基：

\\(\vert\vert 1\vert\vert=\sqrt{2\pi}\\)，（范数与模的差别，范数取决于内积如何定义）

\\(\vert\vert \cos nx\vert\vert=\vert\vert \sin nx\vert\vert=\sqrt{\pi}\\)

所以取标准正交基：
\\[\lbrace \frac{1}{\sqrt{2\pi}},\frac{\sin x}{\sqrt{\pi}},\frac{\cos x}{\sqrt{\pi}},\frac{\sin 2x}{\sqrt{\pi}},\frac{\cos 2x}{\sqrt{\pi}},...,\frac{\sin nx}{\sqrt{\pi}},\frac{\cos nx}{\sqrt{\pi}} \rbrace\\]

下面将\\(\forall f(x)\in C(0,2\pi)\\)投影到\\(S\\)上：

\\[p(f(x))=\sum_{i=0}^{2n}(f(x),\varphi_i(x))\varphi_i(x)\\]

其中\\(\varphi_0=\frac{1}{\sqrt{2\pi}},\varphi_{2k-1}(x)=\frac{\sin kx}{\sqrt{\pi}},\varphi_{2k}(x)=\frac{\cos kx}{\sqrt{\pi}},k=1,2,...,n\\)

当\\(n\rightarrow \infty\\)时，\\(S\\)成为一个无穷维的子空间，\\(S\\)将等价于\\(V\\)，便有\\(p(f(x))=f(x)\\)。

\\(p(f(x))\\)便是\\(f(x)\\)的傅里叶级数。写成三角形式即为：

\\[f(x)=p(f(x))=\sum_{i=0}^{\infty}(f(x),\varphi_i(x))\varphi_i(x)
=\frac{1}{2}a_0+b_1\sin x+a_1\cos x+...+b_n\sin nx+a_n\cos nx+...\\]


其中\\(a_k=\frac{1}{\pi}\int_0^{2\pi}f(x)\cos kxdx,b_k=\frac{1}{\pi}\int_0^{2\pi}f(x)\sin kxdx,k=0,1,2,...\\)

所以傅里叶级数其实就是函数在三角函数形成的子空间的投影。

# EOF