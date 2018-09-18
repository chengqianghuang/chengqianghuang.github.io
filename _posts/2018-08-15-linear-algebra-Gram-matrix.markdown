---
layout: post
title:  "Essence of Linear Algebra - Gram/Kernel Matrix and Properties"
date:   2018-08-15 12:48:14 +00:00
categories: math basics
---

I. Gram Matrix and Kernel Matrix
======
Given a set of <a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a> vectors <a href="https://www.codecogs.com/eqnedit.php?latex=X=\{x_1,&space;x_2,&space;\cdots,&space;x_n\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X=\{x_1,&space;x_2,&space;\cdots,&space;x_n\}" title="X=\{x_1, x_2, \cdots, x_n\}" /></a>, the **Gram matrix** is defined as an <a href="https://www.codecogs.com/eqnedit.php?latex=n\times&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n\times&space;n" title="n\times n" /></a> matrix whose elements are <a href="https://www.codecogs.com/eqnedit.php?latex=G_{ij}=<x_i,&space;x_j>" target="_blank"><img src="https://latex.codecogs.com/gif.latex?G_{ij}=<x_i,&space;x_j>" title="G_{ij}=<x_i, x_j>" /></a>. The notation <a href="https://www.codecogs.com/eqnedit.php?latex=<\cdot,&space;\cdot>" target="_blank"><img src="https://latex.codecogs.com/gif.latex?<\cdot,&space;\cdot>" title="<\cdot, \cdot>" /></a> denotes the operation of *inner product* [1].
If a kernel function <a href="https://www.codecogs.com/eqnedit.php?latex=\kappa" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\kappa" title="\kappa" /></a> is utilised to evaluate the inner products in a feature space with feature map <a href="https://www.codecogs.com/eqnedit.php?latex=\phi" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\phi" title="\phi" /></a>, i.e., the Gram matrix has entries:

<a href="https://www.codecogs.com/eqnedit.php?latex=G_{ij}=<\phi(x_i),&space;\phi(x_j)>=\kappa(x_i,&space;x_j)=K_{ij}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?G_{ij}=<\phi(x_i),&space;\phi(x_j)>=\kappa(x_i,&space;x_j)=K_{ij}" title="G_{ij}=<\phi(x_i), \phi(x_j)>=\kappa(x_i, x_j)=K_{ij}" /></a>.

This matrix is often referred to as **Kernel Matrix** <a href="https://www.codecogs.com/eqnedit.php?latex=K" target="_blank"><img src="https://latex.codecogs.com/gif.latex?K" title="K" /></a>.

<span style="color:red">It is obvious that the Kernel Matrix is symmetric.</span>

<br>

II. Symmetric Matrix! Eigenvalues and Eigenvectors
======
#### II.1 Orthogonal

<span style="color:red">Due to the fact that the Gram/Kernel Matrix is symmetric, it could be inferred that its Eigenvectors corresponding to different Eigenvalues are orthogonal.</span> This is because, if <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda,&space;\mu" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda,&space;\mu" title="\lambda, \mu" /></a> are two different Eigenvalues corresponding to Eigenvectors <a href="https://www.codecogs.com/eqnedit.php?latex=x,&space;z" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x,&space;z" title="x, z" /></a> in <a href="https://www.codecogs.com/eqnedit.php?latex=n&space;\times&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n&space;\times&space;n" title="n \times n" /></a> symmetric matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>, we have:

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{matrix}&space;\lambda<x,z>&=&<Ax,z>\\&space;&=&(Ax)^Tz\\&space;&=&x^TA^Tz\\&space;&=&x^TAz\\&space;&=&\mu&space;<x,&space;z>&space;\end{matrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{matrix}&space;\lambda<x,z>&=&<Ax,z>\\&space;&=&(Ax)^Tz\\&space;&=&x^TA^Tz\\&space;&=&x^TAz\\&space;&=&\mu&space;<x,&space;z>&space;\end{matrix}" title="\begin{matrix} \lambda<x,z>&=&<Ax,z>\\ &=&(Ax)^Tz\\ &=&x^TA^Tz\\ &=&x^TAz\\ &=&\mu <x, z> \end{matrix}" /></a>

and therefore <a href="https://www.codecogs.com/eqnedit.php?latex=<x,&space;z>&space;=&space;x^Tz&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?<x,&space;z>&space;=&space;x^Tz&space;=&space;0" title="<x, z> = x^Tz = 0" /></a>, i.e., the two Eigenvectors are orthogonal.

<span style="color:red">For Eigenvalues that appear multiple times, one can always find an orthonormal basis (Eigenvectors) for the corresponding Eigenspace, e.g., through [Gram-Schmidt][link1].</span> Overall, since the Eigenspaces of different Eigenvalues are mutually orthogonal, all the Eigenvectors can be chosen to give an orthonormal set.

#### II.2 Deflation
With this property in mind, we are able to further explore the *deflation* of a symmetric matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>. Given an Eigenvalue and Eigenvector pair <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda,&space;x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda,&space;x" title="\lambda, x" /></a> of matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>, the deflation is a transformation:

<a href="https://www.codecogs.com/eqnedit.php?latex=A&space;\rightarrow&space;\widetilde{A}&space;=&space;A&space;-&space;\lambda&space;xx^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;\rightarrow&space;\widetilde{A}&space;=&space;A&space;-&space;\lambda&space;xx^T" title="A \rightarrow \widetilde{A} = A - \lambda xx^T" /></a>.

Note that <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> is normalised, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=x^Tx=1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x^Tx=1" title="x^Tx=1" /></a>, and therefore:

<a href="https://www.codecogs.com/eqnedit.php?latex=\widetilde{A}x&space;=&space;Ax&space;-&space;\lambda&space;xx^Tx&space;=&space;\mathbf{0}&space;=&space;0x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\widetilde{A}x&space;=&space;Ax&space;-&space;\lambda&space;xx^Tx&space;=&space;\mathbf{0}&space;=&space;0x" title="\widetilde{A}x = Ax - \lambda xx^Tx = \mathbf{0} = 0x" /></a>,

which says <span style="color:red">the deflation maintains the Eigenvector, but reduces the corresponding Eigenvalue to 0.</span>

#### II.3 Decomposition
By repeatedly finding the Eigenvector corresponding to the largest positive (or smallest negative) Eigenvalue and then deflating, we can always find an orthonormal set of Eigenvectors that helps decompose the original symmetric matrix. More formally, the eigen-decomposition of the <a href="https://www.codecogs.com/eqnedit.php?latex=n&space;\times&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n&space;\times&space;n" title="n \times n" /></a> matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> is formulated as:

<a href="https://www.codecogs.com/eqnedit.php?latex=A&space;=&space;V\Lambda&space;V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;=&space;V\Lambda&space;V^T" title="A = V\Lambda V^T" /></a>.

This is derived from the fact that <a href="https://www.codecogs.com/eqnedit.php?latex=AV&space;=&space;V\Lambda" target="_blank"><img src="https://latex.codecogs.com/gif.latex?AV&space;=&space;V\Lambda" title="AV = V\Lambda" /></a>, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=Av_i&space;=&space;\lambda_i&space;v_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Av_i&space;=&space;\lambda_i&space;v_i" title="Av_i = \lambda_i v_i" /></a>, where the columns in <a href="https://www.codecogs.com/eqnedit.php?latex=V" target="_blank"><img src="https://latex.codecogs.com/gif.latex?V" title="V" /></a> are the orthonormal Eigenvectors such that <a href="https://www.codecogs.com/eqnedit.php?latex=V^T&space;=&space;V^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?V^T&space;=&space;V^{-1}" title="V^T = V^{-1}" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=\Lambda" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" /></a> is a diagonal matrix with <a href="https://www.codecogs.com/eqnedit.php?latex=\Lambda_{ii}&space;=&space;\lambda_i,&space;i=1,2,&space;\cdots,&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\Lambda_{ii}&space;=&space;\lambda_i,&space;i=1,2,&space;\cdots,&space;n" title="\Lambda_{ii} = \lambda_i, i=1,2, \cdots, n" /></a>.
We assume that <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda_1&space;\geq&space;\lambda_2&space;\geq&space;\cdots&space;\geq&space;\lambda_n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda_1&space;\geq&space;\lambda_2&space;\geq&space;\cdots&space;\geq&space;\lambda_n" title="\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_n" /></a>. Also, it follows that:

<a href="https://www.codecogs.com/eqnedit.php?latex=A^{-1}&space;=&space;V\Lambda^{-1}V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A^{-1}&space;=&space;V\Lambda^{-1}V^T" title="A^{-1} = V\Lambda^{-1}V^T" /></a>,
and
<a href="https://www.codecogs.com/eqnedit.php?latex=A^{2}&space;=&space;V\Lambda^{2}V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A^{2}&space;=&space;V\Lambda^{2}V^T" title="A^{2} = V\Lambda^{2}V^T" /></a>.

<br>

III. Positive Semi-definite Matrix
======
Gram and kernel matrices are positive semi-definite.

<br>

IV. Determinant and Trace
======

<br>

V. Singular Matrix? 
======
If a matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> is singular, it means that there is a non-trivial solution <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> for the equation:

<a href="https://www.codecogs.com/eqnedit.php?latex=Ax&space;=&space;\mathbf{0}&space;=&space;0x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Ax&space;=&space;\mathbf{0}&space;=&space;0x" title="Ax = \mathbf{0} = 0x" /></a>.

And this shows equivalently that:
* If a matrix is singular, its column vectors are **linear dependent** and span a space of **dimension less than the number of columns**;
* If a matrix is singular, it has at **least one eigenvalue equal to 0.**

On the other hand:
* If a matrix is non-singular, its column vectors are **linear independent** and span a space of **dimension equal to the number of columns**;
* If a matrix is non-singular, due to the fact that its columns span the space of dimension equal to the number of columns, e.g., for matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> it has <a href="https://www.codecogs.com/eqnedit.php?latex=Au_i=e_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Au_i=e_i" title="Au_i=e_i" /></a> and then <a href="https://www.codecogs.com/eqnedit.php?latex=AU=I" target="_blank"><img src="https://latex.codecogs.com/gif.latex?AU=I" title="AU=I" /></a>, **we are able to find the multiplicative inverse of the matrix**, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=U=A^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?U=A^{-1}" title="U=A^{-1}" /></a>.

Note that, **we cannot conclude whether Gram Matrix and Kernel Matrix are singular or not according to their definition.** Consider a dataset that has two same data points, there will be two same columns in the Gram/Kernel Matrix such that the columns are linear dependent, i.e., singular. Therefore, singularity is an application-specific property.

<br>

[1] John Shawe-Taylor, Nello Cristianini, Kernel methods for pattern analysis, *Cambridge University Press*, 2004.

[link1]: https://www.khanacademy.org/math/linear-algebra/alternate-bases/orthonormal-basis/v/linear-algebra-gram-schmidt-example-with-3-basis-vectors