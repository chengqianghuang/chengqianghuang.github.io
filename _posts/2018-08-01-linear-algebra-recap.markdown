---
layout: post
title:  "Essence of Linear Algebra - My Understanding"
date:   2018-08-01 10:15:14 +00:00
categories: math basics
---
Linear algebra is very fundamental and critical in machine learning and data mining research.
[Essence of Linear Algebra][essence] gives a very good description of the basic concepts.
Here in this article, I added some comments and thoughts.
This is mainly for helping myself understand and memorise the details better.
<br>

Linear Transformation of a Coordinate System:
======
<iframe width="700" height="400" src="https://www.youtube.com/embed/kYB8IZa5AuE?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&amp;ecver=1" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<br>
What I would like to add concerning linear transformation is another explanation of how 
the linear transformation matrix comes.
Typically, for a coordinate system, the basis vectors are known, e.g., 
<a href="https://www.codecogs.com/eqnedit.php?latex=\left&space;(&space;x_1,&space;x_2,&space;\cdots,&space;x_n&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left&space;(&space;x_1,&space;x_2,&space;\cdots,&space;x_n&space;\right&space;)" title="\left ( x_1, x_2, \cdots, x_n \right )" /></a>,
where each <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img
src="https://latex.codecogs.com/gif.latex?x" title="x" /></a>
is a basis vector and <a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a>
is the number of basis vectors and also the number of dimensions usually.
This basis vector set defines the coordinate system and any vector in this coordinate
system can be expressed using:

<a href="https://www.codecogs.com/eqnedit.php?latex=(x_1,&space;x_2,&space;\cdots,&space;x_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x_1,&space;x_2,&space;\cdots,&space;x_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}" title="(x_1, x_2, \cdots, x_n) \begin{bmatrix} \xi_1\\ \xi_2\\ \cdots\\ \xi_n \end{bmatrix}" /></a>,

in which the column vector with all
<a href="https://www.codecogs.com/eqnedit.php?latex=\xi" target="_blank"><img
src="https://latex.codecogs.com/gif.latex?\xi" title="\xi" /></a>
is the coordinate for the given vector.

A linear transformation of a coordinate system can also be considered as the linear transformation
of the basis vectors in the coordinate system, which transforms the original set of basis vectors,
e.g., 
<a href="https://www.codecogs.com/eqnedit.php?latex=\left&space;(&space;x_1,&space;x_2,&space;\cdots,&space;x_n&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left&space;(&space;x_1,&space;x_2,&space;\cdots,&space;x_n&space;\right&space;)" title="\left ( x_1, x_2, \cdots, x_n \right )" /></a>,
into another set, e.g., <a href="https://www.codecogs.com/eqnedit.php?latex=(y_1,&space;y_2,&space;\cdots,&space;y_n)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(y_1,&space;y_2,&space;\cdots,&space;y_n)" title="(y_1, y_2, \cdots, y_n)" /></a>,
defining a new coordinate system. And the relationship between these two sets could be formalised
as:

<a href="https://www.codecogs.com/eqnedit.php?latex=(y_1,&space;y_2,&space;\cdots,&space;y_n)&space;=&space;(x_1,&space;x_2,&space;\cdots,&space;x_n)\begin{bmatrix}&space;a_{11}&space;&&space;a_{21}&space;&&space;\cdots&space;&&space;a_{n1}&space;\\&space;a_{12}&space;&&space;a_{22}&space;&&space;\cdots&space;&&space;a_{n2}&space;\\&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;\\&space;a_{1n}&space;&&space;a_{2n}&space;&&space;\cdots&space;&&space;a_{nn}&space;\end{bmatrix}" target="_blank"><img
src="https://latex.codecogs.com/gif.latex?(y_1,&space;y_2,&space;\cdots,&space;y_n)&space;=&space;(x_1,&space;x_2,&space;\cdots,&space;x_n)\begin{bmatrix}&space;a_{11}&space;&&space;a_{21}&space;&&space;\cdots&space;&&space;a_{n1}&space;\\&space;a_{12}&space;&&space;a_{22}&space;&&space;\cdots&space;&&space;a_{n2}&space;\\&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;\\&space;a_{1n}&space;&&space;a_{2n}&space;&&space;\cdots&space;&&space;a_{nn}&space;\end{bmatrix}" title="(y_1, y_2, \cdots, y_n) = (x_1, x_2, \cdots, x_n)\begin{bmatrix} a_{11} & a_{21} & \cdots & a_{n1} \\ a_{12} & a_{22} & \cdots & a_{n2} \\ \cdots & \cdots & \cdots & \cdots \\ a_{1n} & a_{2n} & \cdots & a_{nn} \end{bmatrix}" /></a>,

where one can see that a new basis vector is a linear combination of the original basis vectors.
With the linear transformation of the whole space, the coordinate for a vector in the original space

will also be transformed such that:

<a href="https://www.codecogs.com/eqnedit.php?latex=(x_1,&space;x_2,&space;\cdots,&space;x_n)\begin{bmatrix}&space;a_{11}&space;&&space;a_{21}&space;&&space;\cdots&space;&&space;a_{n1}&space;\\&space;a_{12}&space;&&space;a_{22}&space;&&space;\cdots&space;&&space;a_{n2}&space;\\&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;\\&space;a_{1n}&space;&&space;a_{2n}&space;&&space;\cdots&space;&&space;a_{nn}&space;\end{bmatrix}&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}&space;=&space;(x_1,&space;x_2,&space;\cdots,&space;x_n)\begin{bmatrix}&space;\eta_1\\&space;\eta_2\\&space;\cdots\\&space;\eta_n&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x_1,&space;x_2,&space;\cdots,&space;x_n)\begin{bmatrix}&space;a_{11}&space;&&space;a_{21}&space;&&space;\cdots&space;&&space;a_{n1}&space;\\&space;a_{12}&space;&&space;a_{22}&space;&&space;\cdots&space;&&space;a_{n2}&space;\\&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;&&space;\cdots&space;\\&space;a_{1n}&space;&&space;a_{2n}&space;&&space;\cdots&space;&&space;a_{nn}&space;\end{bmatrix}&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}&space;=&space;(x_1,&space;x_2,&space;\cdots,&space;x_n)\begin{bmatrix}&space;\eta_1\\&space;\eta_2\\&space;\cdots\\&space;\eta_n&space;\end{bmatrix}" title="(x_1, x_2, \cdots, x_n)\begin{bmatrix} a_{11} & a_{21} & \cdots & a_{n1} \\ a_{12} & a_{22} & \cdots & a_{n2} \\ \cdots & \cdots & \cdots & \cdots \\ a_{1n} & a_{2n} & \cdots & a_{nn} \end{bmatrix} \begin{bmatrix} \xi_1\\ \xi_2\\ \cdots\\ \xi_n \end{bmatrix} = (x_1, x_2, \cdots, x_n)\begin{bmatrix} \eta_1\\ \eta_2\\ \cdots\\ \eta_n \end{bmatrix}" /></a>,

showing that the new coordinate <a href="https://www.codecogs.com/eqnedit.php?latex=\eta"
target="_blank"><img src="https://latex.codecogs.com/gif.latex?\eta" title="\eta" /></a>
(from the perspective of the original space) of a vector is equal to the linear transformation
matrix <a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img
src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>
(the matrix with all <a href="https://www.codecogs.com/eqnedit.php?latex=a" target="_blank"><img
src="https://latex.codecogs.com/gif.latex?a" title="a" /></a>s) times the original coordinate <a
href="https://www.codecogs.com/eqnedit.php?latex=\xi" target="_blank"><img
src="https://latex.codecogs.com/gif.latex?\xi" title="\xi" /></a>: (in matrix form)

<a href="https://www.codecogs.com/eqnedit.php?latex=\eta&space;=&space;A&space;\xi"
target="_blank"><img src="https://latex.codecogs.com/gif.latex?\eta&space;=&space;A&space;\xi"
title="\eta = A \xi" /></a>.

Note that this explanation does not apply well when the linear transformation matrix is non-square. Therefore, the intuition provided by the video shown above may be a better way to memorise linear transformation, in which:
* each column vector in the linear transformation matrix is the target vector into which the corresponding original basis vector are transforming. More formally, this could be interprete as directly changing the basis vectors into another set of basis vectors of the same number:\\
<a href="https://www.codecogs.com/eqnedit.php?latex=(x_1,&space;x_2,&space;\cdots,&space;x_n)&space;\Rightarrow&space;(x'_1,&space;x'_2,&space;\cdots,&space;x'_n)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x_1,&space;x_2,&space;\cdots,&space;x_n)&space;\Rightarrow&space;(x'_1,&space;x'_2,&space;\cdots,&space;x'_n)" title="(x_1, x_2, \cdots, x_n) \Rightarrow (x'_1, x'_2, \cdots, x'_n)" /></a>,\\
such that we have:\\
<a href="https://www.codecogs.com/eqnedit.php?latex=(x_1,&space;x_2,&space;\cdots,&space;x_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}&space;\Rightarrow&space;(x'_1,&space;x'_2,&space;\cdots,&space;x'_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x_1,&space;x_2,&space;\cdots,&space;x_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}&space;\Rightarrow&space;(x'_1,&space;x'_2,&space;\cdots,&space;x'_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}" title="(x_1, x_2, \cdots, x_n) \begin{bmatrix} \xi_1\\ \xi_2\\ \cdots\\ \xi_n \end{bmatrix} \Rightarrow (x'_1, x'_2, \cdots, x'_n) \begin{bmatrix} \xi_1\\ \xi_2\\ \cdots\\ \xi_n \end{bmatrix}" /></a>.\\
The new basis vectors could be of a different dimension and the coordinate of the original vector
after transformation becomes:\\
<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;\xi'_1\\&space;\xi'_2\\&space;\cdots\\&space;\xi'_n&space;\end{bmatrix}&space;=&space;(x'_1,&space;x'_2,&space;\cdots,&space;x'_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;\xi'_1\\&space;\xi'_2\\&space;\cdots\\&space;\xi'_n&space;\end{bmatrix}&space;=&space;(x'_1,&space;x'_2,&space;\cdots,&space;x'_n)&space;\begin{bmatrix}&space;\xi_1\\&space;\xi_2\\&space;\cdots\\&space;\xi_n&space;\end{bmatrix}" title="\begin{bmatrix} \xi'_1\\ \xi'_2\\ \cdots\\ \xi'_n \end{bmatrix} = (x'_1, x'_2, \cdots, x'_n) \begin{bmatrix} \xi_1\\ \xi_2\\ \cdots\\ \xi_n \end{bmatrix}" /></a>,\\
i.e., **the direct multiplication of the transformed basis vectors and the original coordinates.**

* the new coordinate of a vector (from the perspective of the original space) after transformation
is simply the transformation matrix times the original coordinate.
<br>


[essence]: https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab