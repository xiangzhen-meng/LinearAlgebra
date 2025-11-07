# 克莱姆法则 (Cramer's Rule)
## 定理内容
### 理解

克莱姆法则给出了有唯一解的线性方程组的解
有唯一解 $\iff$ 系数矩阵行列式为零
### 内容

若线性方程组
$$
\begin{cases}
a_{11}x_{1} + \cdots + a_{1n}x_{n} = b_{1}, \\
\vdots \\
a_{n1}x_{1} + \cdots + a_{nn}x_{n} = b_{n}
\end{cases}
$$
的系数矩阵
$$
\boldsymbol{A} = \begin{pmatrix}
a_{11} & \cdots & a_{1n} \\
\vdots & \ddots & \vdots \\
a_{n1} & \cdots & a_{nn}
\end{pmatrix}
$$

的行列式非0，
则有唯一解：
$$
x_{1} = \frac{d_{1}}{d}, \cdots, x_{n} = \frac{d_{n}}{d},
$$
其中
$$
d = \det(\boldsymbol{A}) = \begin{vmatrix}
a_{11} & \cdots & a_{1n} \\
\vdots & \ddots & \vdots \\
a_{n1} & \cdots & a_{nn}
\end{vmatrix},
$$
$$
d_{j} = \begin{vmatrix}
a_{11} & \cdots & a_{1,j-1} & b_{1} & a_{1,j+1} & \cdots & a_{1n} \\
\vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\
a_{n1} & \cdots & a_{n,j-1} & b_{n} & a_{n,j+1} & \cdots & a_{nn}
\end{vmatrix} \quad (j=1,\cdots,n).
$$

## 证明
### 先证是原方程组的解

将 $x_{1},\cdots,x_{n}$ 的表达式代入第 $p$ 个方程
$$
\begin{align*}
\sum_{j=1}^{n}a_{pj}x_{j}&=\frac{1}{d}\sum_{j=1}^{n}a_{pj}\sum_{i=1}^{n}b_{i}A_{ij}\\
&=\frac{1}{d}\sum_{i=1}^{n}b_{i}\delta_{pi}d\\
&=b_{p}
\end{align*}
$$

这里涉及到一个换序技巧：由于 i 和 j 无关，因此可以将内部含有 j 的先做求和
而且求和还涉及到了 [[行列式的按一行展开#某项乘以另一项的代数余子式]] 中克罗涅克德尔塔符号的问题，显然只有一项即 i = j 时有非零项
### 再证原方程组的解唯一

方程组的 n 个方程依次乘以 $A_{1j},\cdots,A_{nj}$ 并求和可得
$$
\sum_{i=1}^n\sum_{k=1}^n a_{ik}A_{ij}x_k = \sum_{i=1}^n b_i A_{ij},
$$
左式为
$$
d\sum_{k=1}^{n}\delta_{jk}x_{k}=dx_{j},
$$
右式即$d_{j}$，故方程组若有解，必定为定理给出的 $x_{1},\cdots,x_{n}$ 的表达式

## 与 [[矩阵的逆 (方阵的逆)]] 的联系

下述解法给出了所有系数阵为可逆方阵的通解，形式比 Cramer's Rule 简洁许多

给出一个系数阵为方阵的线性方程组：
$$
Ax=b
$$
如果这个方阵可逆，也即满秩，也即非奇异，也即行列式非零，则可以进行如下操作：

两侧同时左乘以 $A^{-1}$，得到：
$$
\begin{align}
& LHS=A^{-1}Ax=(A^{-1}A)x=Ix=xn \\
& RHS=A^{-1}b
\end{align}
$$
也即有线性方程组的解：
$$
x=A^{-1}b
$$
显然这是唯一解

另一方面，若方阵不可逆，则不满秩，则需要按之前的解法解决了
