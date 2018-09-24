---
layout: post
title:  "Essence of Linear Algebra - Gram/Kernel Matrix and Properties"
date:   2018-08-15 12:48:14 +00:00
categories: math basics
---

0.Conclusion
======
To conclude with, Gram and Kernel matrices are both symmetric matrices so that they are eligible to Eigen-decomposition, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=A&space;=&space;V\Lambda&space;V^T&space;=&space;\sum_i&space;\lambda_iv_iv_i^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;=&space;V\Lambda&space;V^T&space;=&space;\sum_i&space;\lambda_iv_iv_i^T" title="A = V\Lambda V^T = \sum_i \lambda_iv_iv_i^T" /></a>, where <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda_i" title="\lambda_i" /></a> is a Eigenvalue and <a href="https://www.codecogs.com/eqnedit.php?latex=v_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v_i" title="v_i" /></a> is its Eigenvector, <a href="https://www.codecogs.com/eqnedit.php?latex=VV^T&space;=&space;I" target="_blank"><img src="https://latex.codecogs.com/gif.latex?VV^T&space;=&space;I" title="VV^T = I" /></a>, and <a href="https://www.codecogs.com/eqnedit.php?latex=V^{-1}&space;=&space;V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?V^{-1}&space;=&space;V^T" title="V^{-1} = V^T" /></a>. They are positive semi-definite matrices, which means <a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;i,&space;\lambda_i&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;i,&space;\lambda_i&space;\geq&space;0" title="\forall i, \lambda_i \geq 0" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=v^TAv&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v^TAv&space;\geq&space;0" title="v^TAv \geq 0" /></a>. If they are not singular, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=\not&space;\exists&space;i,&space;\lambda_i&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\not&space;\exists&space;i,&space;\lambda_i&space;=&space;0" title="\not \exists i, \lambda_i = 0" /></a>, they are positive definite.

<br>

1.Gram Matrix and Kernel Matrix
======
Given a set of <a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a> vectors <a href="https://www.codecogs.com/eqnedit.php?latex=X=\{x_1,&space;x_2,&space;\cdots,&space;x_n\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X=\{x_1,&space;x_2,&space;\cdots,&space;x_n\}" title="X=\{x_1, x_2, \cdots, x_n\}" /></a>, the **Gram matrix** is defined as an <a href="https://www.codecogs.com/eqnedit.php?latex=n\times&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n\times&space;n" title="n\times n" /></a> matrix whose elements are <a href="https://www.codecogs.com/eqnedit.php?latex=G_{ij}=<x_i,&space;x_j>" target="_blank"><img src="https://latex.codecogs.com/gif.latex?G_{ij}=<x_i,&space;x_j>" title="G_{ij}=<x_i, x_j>" /></a>. The notation <a href="https://www.codecogs.com/eqnedit.php?latex=<\cdot,&space;\cdot>" target="_blank"><img src="https://latex.codecogs.com/gif.latex?<\cdot,&space;\cdot>" title="<\cdot, \cdot>" /></a> denotes the operation of *inner product* [1].
If a kernel function <a href="https://www.codecogs.com/eqnedit.php?latex=\kappa" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\kappa" title="\kappa" /></a> is utilised to evaluate the inner products in a feature space with feature map <a href="https://www.codecogs.com/eqnedit.php?latex=\phi" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\phi" title="\phi" /></a>, i.e., the Gram matrix has entries:

<a href="https://www.codecogs.com/eqnedit.php?latex=G_{ij}=<\phi(x_i),&space;\phi(x_j)>=\kappa(x_i,&space;x_j)=K_{ij}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?G_{ij}=<\phi(x_i),&space;\phi(x_j)>=\kappa(x_i,&space;x_j)=K_{ij}" title="G_{ij}=<\phi(x_i), \phi(x_j)>=\kappa(x_i, x_j)=K_{ij}" /></a>.

This matrix is often referred to as **Kernel matrix** <a href="https://www.codecogs.com/eqnedit.php?latex=K" target="_blank"><img src="https://latex.codecogs.com/gif.latex?K" title="K" /></a>.

<span style="color:red">It is obvious that the Kernel matrix is symmetric.</span>

<br>

2.Symmetric Matrix! Eigenvalues and Eigenvectors
======
#### 2.1 Orthogonal

<span style="color:red">Due to the fact that the Gram/Kernel matrix is symmetric, it could be inferred that its Eigenvectors corresponding to different Eigenvalues are orthogonal.</span> This is because, if <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda,&space;\mu" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda,&space;\mu" title="\lambda, \mu" /></a> are two different Eigenvalues corresponding to Eigenvectors <a href="https://www.codecogs.com/eqnedit.php?latex=x,&space;z" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x,&space;z" title="x, z" /></a> in <a href="https://www.codecogs.com/eqnedit.php?latex=n&space;\times&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n&space;\times&space;n" title="n \times n" /></a> symmetric matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>, we have:

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{matrix}&space;\lambda<x,z>&=&<Ax,z>\\&space;&=&(Ax)^Tz\\&space;&=&x^TA^Tz\\&space;&=&x^TAz\\&space;&=&\mu&space;<x,&space;z>&space;\end{matrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{matrix}&space;\lambda<x,z>&=&<Ax,z>\\&space;&=&(Ax)^Tz\\&space;&=&x^TA^Tz\\&space;&=&x^TAz\\&space;&=&\mu&space;<x,&space;z>&space;\end{matrix}" title="\begin{matrix} \lambda<x,z>&=&<Ax,z>\\ &=&(Ax)^Tz\\ &=&x^TA^Tz\\ &=&x^TAz\\ &=&\mu <x, z> \end{matrix}" /></a>

and therefore <a href="https://www.codecogs.com/eqnedit.php?latex=<x,&space;z>&space;=&space;x^Tz&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?<x,&space;z>&space;=&space;x^Tz&space;=&space;0" title="<x, z> = x^Tz = 0" /></a>, i.e., the two Eigenvectors are orthogonal.

<span style="color:red">For Eigenvalues that appear multiple times, one can always find an orthonormal basis (Eigenvectors) for the corresponding Eigenspace, e.g., through [Gram-Schmidt][link1].</span> Overall, since the Eigenspaces of different Eigenvalues are mutually orthogonal, all the Eigenvectors can be chosen to give an orthonormal set.

#### 2.2 Deflation
With this property in mind, we are able to further explore the *deflation* of a symmetric matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>. Given an Eigenvalue and Eigenvector pair <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda,&space;x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda,&space;x" title="\lambda, x" /></a> of matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>, the deflation is a transformation:

<a href="https://www.codecogs.com/eqnedit.php?latex=A&space;\rightarrow&space;\widetilde{A}&space;=&space;A&space;-&space;\lambda&space;xx^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;\rightarrow&space;\widetilde{A}&space;=&space;A&space;-&space;\lambda&space;xx^T" title="A \rightarrow \widetilde{A} = A - \lambda xx^T" /></a>.

Note that <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> is normalised, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=x^Tx=1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x^Tx=1" title="x^Tx=1" /></a>, and therefore:

<a href="https://www.codecogs.com/eqnedit.php?latex=\widetilde{A}x&space;=&space;Ax&space;-&space;\lambda&space;xx^Tx&space;=&space;\mathbf{0}&space;=&space;0x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\widetilde{A}x&space;=&space;Ax&space;-&space;\lambda&space;xx^Tx&space;=&space;\mathbf{0}&space;=&space;0x" title="\widetilde{A}x = Ax - \lambda xx^Tx = \mathbf{0} = 0x" /></a>,

which says <span style="color:red">the deflation maintains the Eigenvector, but reduces the corresponding Eigenvalue to 0.</span>

#### 2.3 Decomposition
<span style="color:red">By repeatedly finding the Eigenvector corresponding to the largest positive (or smallest negative) Eigenvalue and then deflating, we can always find an orthonormal set of Eigenvectors that helps decompose the original symmetric matrix.</span> More formally, the eigen-decomposition of the <a href="https://www.codecogs.com/eqnedit.php?latex=n&space;\times&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n&space;\times&space;n" title="n \times n" /></a> matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> is formulated as:

<a href="https://www.codecogs.com/eqnedit.php?latex=A&space;=&space;V\Lambda&space;V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;=&space;V\Lambda&space;V^T" title="A = V\Lambda V^T" /></a>.

This is derived from the fact that <a href="https://www.codecogs.com/eqnedit.php?latex=AV&space;=&space;V\Lambda" target="_blank"><img src="https://latex.codecogs.com/gif.latex?AV&space;=&space;V\Lambda" title="AV = V\Lambda" /></a>, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=Av_i&space;=&space;\lambda_i&space;v_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Av_i&space;=&space;\lambda_i&space;v_i" title="Av_i = \lambda_i v_i" /></a>, where the columns in <a href="https://www.codecogs.com/eqnedit.php?latex=V" target="_blank"><img src="https://latex.codecogs.com/gif.latex?V" title="V" /></a> are the orthonormal Eigenvectors such that <a href="https://www.codecogs.com/eqnedit.php?latex=V^T&space;=&space;V^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?V^T&space;=&space;V^{-1}" title="V^T = V^{-1}" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=\Lambda" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" /></a> is a diagonal matrix with <a href="https://www.codecogs.com/eqnedit.php?latex=\Lambda_{ii}&space;=&space;\lambda_i,&space;i=1,2,&space;\cdots,&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\Lambda_{ii}&space;=&space;\lambda_i,&space;i=1,2,&space;\cdots,&space;n" title="\Lambda_{ii} = \lambda_i, i=1,2, \cdots, n" /></a>.
We assume that <a href="https://www.codecogs.com/eqnedit.php?latex=\lambda_1&space;\geq&space;\lambda_2&space;\geq&space;\cdots&space;\geq&space;\lambda_n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\lambda_1&space;\geq&space;\lambda_2&space;\geq&space;\cdots&space;\geq&space;\lambda_n" title="\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_n" /></a>. Also, it follows that:

<a href="https://www.codecogs.com/eqnedit.php?latex=A^{-1}&space;=&space;V\Lambda^{-1}V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A^{-1}&space;=&space;V\Lambda^{-1}V^T" title="A^{-1} = V\Lambda^{-1}V^T" /></a>,
and
<a href="https://www.codecogs.com/eqnedit.php?latex=A^{2}&space;=&space;V\Lambda^{2}V^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A^{2}&space;=&space;V\Lambda^{2}V^T" title="A^{2} = V\Lambda^{2}V^T" /></a>.

<br>

3.Positive Semi-definite Matrix!
======
A matrix is *positive semi-definite* if its Eigenvalues are all non-negative. A symmetric matrix is not necessarily a positive semi-definite matrix. <span style="color:red">However, gram and kernel matrices are positive semi-definite (it's not because of they are symmetric).</span>

Another way of saying a matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> is semi-definite is <a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;v" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;v" title="\forall v" /></a>, it has:
<a href="https://www.codecogs.com/eqnedit.php?latex=v^TAv&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v^TAv&space;\geq&space;0" title="v^TAv > 0" /></a>.

To prove Gram and Kernel matrices are positive semi-definite, for a general case of kernel matrix:

<a href="https://www.codecogs.com/eqnedit.php?latex=K_{ij}&space;=&space;\kappa(x_i,&space;x_j)&space;=&space;<\phi(x_i),&space;\phi(x_j)>" target="_blank"><img src="https://latex.codecogs.com/gif.latex?K_{ij}&space;=&space;\kappa(x_i,&space;x_j)&space;=&space;<\phi(x_i),&space;\phi(x_j)>" title="K_{ij} = \kappa(x_i, x_j) = <\phi(x_i), \phi(x_j)>" /></a> for <a href="https://www.codecogs.com/eqnedit.php?latex=i,j&space;=&space;1,&space;2,&space;\cdots,&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?i,j&space;=&space;1,&space;2,&space;\cdots,&space;n" title="i,j = 1, 2, \cdots, n" /></a>.

Therefore, for any vector <a href="https://www.codecogs.com/eqnedit.php?latex=v" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v" title="v" /></a>, we have:

<a href="https://www.codecogs.com/eqnedit.php?latex=v^TKv&space;\\&space;=&space;\sum_{i,j=1}^{n}v_iv_jK_{ij}&space;\\&space;=&space;\sum_{i,j=1}^{n}v_iv_j<\phi(x_i),&space;\phi(x_j)>\\&space;=&space;<\sum_i^n&space;v_i\phi(x_i),&space;\sum_j^n&space;v_j\phi(x_j)>\\&space;=&space;\Vert&space;\sum_i^n&space;v_i\phi(x_i)&space;\Vert^2&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v^TKv&space;\\&space;=&space;\sum_{i,j=1}^{n}v_iv_jK_{ij}&space;\\&space;=&space;\sum_{i,j=1}^{n}v_iv_j<\phi(x_i),&space;\phi(x_j)>\\&space;=&space;<\sum_i^n&space;v_i\phi(x_i),&space;\sum_j^n&space;v_j\phi(x_j)>\\&space;=&space;\Vert&space;\sum_i^n&space;v_i\phi(x_i)&space;\Vert^2&space;\geq&space;0" title="v^TKv \\ = \sum_{i,j=1}^{n}v_iv_jK_{ij} \\ = \sum_{i,j=1}^{n}v_iv_j<\phi(x_i), \phi(x_j)>\\ = <\sum_i^n v_i\phi(x_i), \sum_j^n v_j\phi(x_j)>\\ = \Vert \sum_i^n v_i\phi(x_i) \Vert^2 \geq 0" /></a>

We also have the proposition that, a matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> is positive semi-definite if and only if <a href="https://www.codecogs.com/eqnedit.php?latex=A&space;=&space;B^TB" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;=&space;B^TB" title="A = B^TB" /></a> for some real matrix <a href="https://www.codecogs.com/eqnedit.php?latex=B" target="_blank"><img src="https://latex.codecogs.com/gif.latex?B" title="B" /></a>, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=v^TAv&space;=&space;v^TB^TBv&space;=&space;\Vert&space;Bv\Vert^2&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v^TAv&space;=&space;v^TB^TBv&space;=&space;\Vert&space;Bv\Vert^2&space;\geq&space;0" title="v^TAv = v^TB^TBv = \Vert Bv\Vert^2 \geq 0" /></a>.

<br>

4.Determinant and Trace
======
#### 4.1 About the Determinant
<span style="color:red">The determinant of a symmetric matrix <a href="https://www.codecogs.com/eqnedit.php?latex=\mathrm{det}(A)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathrm{det}(A)" title="\mathrm{det}(A)" /></a> is the product of the Eigenvalues of the matrix <a href="https://www.codecogs.com/eqnedit.php?latex=\prod_{i=1}^n&space;\lambda_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\prod_{i=1}^n&space;\lambda_i" title="\prod_{i=1}^n \lambda_i" /></a>. If the matrix is positive definite, the determinant would be strictly positive. If the matrix is positive semi-definite, the determinant could be zero when the matrix is a singular matrix.</span>

It also has: <a href="https://www.codecogs.com/eqnedit.php?latex=\mathrm{det}(AB)&space;=&space;\mathrm{det}(A)\mathrm{det}(B)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathrm{det}(AB)&space;=&space;\mathrm{det}(A)\mathrm{det}(B)" title="\mathrm{det}(AB) = \mathrm{det}(A)\mathrm{det}(B)" /></a>

#### 4.2 About the Trace
For the trace of a symmetric matrix, we have <a href="https://www.codecogs.com/eqnedit.php?latex=\mathrm{tr}(AB)&space;=&space;\mathrm{tr}(BA)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathrm{tr}(AB)&space;=&space;\mathrm{tr}(BA)" title="\mathrm{tr}(AB) = \mathrm{tr}(BA)" /></a>. In other words, for gram and kernel matrices, it has:

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathrm{tr}(V^TAV)&space;=&space;\mathrm{tr}(AVV^T)&space;=&space;\mathrm{tr}(A)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathrm{tr}(V^TAV)&space;=&space;\mathrm{tr}(AVV^T)&space;=&space;\mathrm{tr}(A)" title="\mathrm{tr}(V^TAV) = \mathrm{tr}(AVV^T) = \mathrm{tr}(A)" /></a>,

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathrm{tr}(V^TAV)&space;=&space;\mathrm{tr}(V^TV\Lambda&space;V^TV)&space;=&space;\mathrm{tr}(\Lambda)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathrm{tr}(V^TAV)&space;=&space;\mathrm{tr}(V^TV\Lambda&space;V^TV)&space;=&space;\mathrm{tr}(\Lambda)" title="\mathrm{tr}(V^TAV) = \mathrm{tr}(V^TV\Lambda V^TV) = \mathrm{tr}(\Lambda)" /></a>.

<br>

5.Singular Matrix? 
======
If a matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> is singular, it means that there is a non-trivial solution <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> for the equation:

<a href="https://www.codecogs.com/eqnedit.php?latex=Ax&space;=&space;\mathbf{0}&space;=&space;0x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Ax&space;=&space;\mathbf{0}&space;=&space;0x" title="Ax = \mathbf{0} = 0x" /></a>.

And this shows equivalently that:
* If a matrix is singular, its column vectors are **linear dependent** and span a space of **dimension less than the number of columns**;
* If a matrix is singular, it has at **least one eigenvalue equal to 0.**

On the other hand:
* If a matrix is non-singular, its column vectors are **linear independent** and span a space of **dimension equal to the number of columns**;
* If a matrix is non-singular, due to the fact that its columns span the space of dimension equal to the number of columns, e.g., for matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a> it has <a href="https://www.codecogs.com/eqnedit.php?latex=Au_i=e_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Au_i=e_i" title="Au_i=e_i" /></a> and then <a href="https://www.codecogs.com/eqnedit.php?latex=AU=I" target="_blank"><img src="https://latex.codecogs.com/gif.latex?AU=I" title="AU=I" /></a>, **we are able to find the multiplicative inverse of the matrix**, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=U=A^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?U=A^{-1}" title="U=A^{-1}" /></a>.

Note that, **we cannot conclude whether Gram matrix and Kernel matrix are singular or not according to their definition.** Consider a dataset that has two same data points, there will be two same columns in the Gram/Kernel Matrix such that the columns are linear dependent, i.e., singular. Therefore, singularity is an application-specific property.

<br>

[1] John Shawe-Taylor, Nello Cristianini, Kernel methods for pattern analysis, *Cambridge University Press*, 2004.

[link1]: https://www.khanacademy.org/math/linear-algebra/alternate-bases/orthonormal-basis/v/linear-algebra-gram-schmidt-example-with-3-basis-vectors