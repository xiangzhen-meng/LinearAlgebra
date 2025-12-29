# Q 线性子空间表示为矩阵的零空间

### 问题

>[!question] 问题
>给定线性空间 $\mathbb{R}^n$，是否其任意线性子空间 $V_{1}$，总能写成某个矩阵 $\mathbf{A}$ 的零空间？也即是否成立：$$\exists \mathbf{A},s.t. V_{1}=\ker (\mathbf{A})$$

### 方法一：正交补的视角

>[!note] 定义：正交补
>给定线性空间 $\mathbb{V}$ 和其线性子空间 $V_{1}$。$V_{1}$ 的正交补定义为：$$V^\perp_1=\{x \ \vert\ \forall y\in V_{1},(v,x)=0\}$$

首先选定 $V_{1}$ 的一组基：$e_{1},e_{2},e_{3},\dots,e_s$. 

再取 $V^\perp_{1}$ 的基 $e_{s+1},e_{s+2},\dots ,e_{n}$，显然这两组基是正交的。

>[!attention] 注意
>这两组基不一定需要是单位正交基，只要保证两组基之间相互正交即可

于是可以取矩阵 $A$ 形式如下：
$$
A=\begin{pmatrix}
e_{s+1} \\
e_{s+2} \\
\vdots \\
e_n
\end{pmatrix}
$$
首先验证：线性空间 $V_{1}$ 中的所有向量都在 $A$ 的零空间中，也即向量右乘 $A$ 得到零向量
$$
\forall a\in V_{1},a=\lambda_{1}e_{1}+\lambda_{2}e_{2}+\dots+\lambda_se_s
$$
于是由正交补的定义可以知道：
$$
Aa=A(\lambda_{1}e_{1}+\lambda_{2}e_{2}+\dots+\lambda_se_s)=\mathbf{0}
$$
于是有：$V_{1}\subset \ker(A)$ 

反过来，验证：$A$ 的零空间的所有向量都在 $V_{1}$ 中
$$
\forall x\in\ker(A),Ax=0
$$
这也就意味着，
$$
\forall x\in\ker(A),\forall y\in V_{1}^\perp,(x,y)=0
$$
于是：
$$
x\in (V_{1}^\perp)^\perp=V_{1}
$$
也即：$\ker(A)\subset V_{1}$ 

综上所述，$V_{1}=\ker(A)$ 

>[!example] 例子 
>这个思路是从哪里来的呢？不妨考虑一下三维空间中过原点的二维平面。想要确定二维平面，必然要两个方程，而这两个方程可以由：$$\begin{align}(n,a)=0\\(n,b)=0
\end{align}$$给出，也即由法向量点乘面内的两个线性无关向量形成方程组。

### 方法二：构造神奇的矩阵

老唐的神奇小方法，我也不知道他是怎么想出来这么麻烦的证明的，并且居然是对的呃呃呃啊啊啊，可能之后可以问一问他

取出线性空间 $V_{1}$ 的一组基：$a_{1},a_{2},\dots,a_s$，将此线性空间作为一个矩阵的列空间，有：
$$
A=\begin{pmatrix}
a_{1},a_{2},\dots,a_s
\end{pmatrix}=\begin{pmatrix}
a_{11}&a_{21}&\dots&a_{s1} \\
a_{12}&a_{22}&\dots&a_{s2}  \\
\vdots&\vdots&&\vdots \\
a_{1n}&a_{2n}&\dots&a_{sn} 
\end{pmatrix}
$$
显然这个矩阵有 $\text{rank}(A)=s$，则不妨有前 $s$ 行组成的方阵非奇异，于是有：
$$
\begin{vmatrix}
a_{11}&\dots&a_{s1} \\
\vdots&&\vdots \\
a_{1s}&\dots&a_{ss} 
\end{vmatrix}\neq 0
$$
任意线性空间 $V_{1}$ 中的向量都可以被列向量线性表出，于是有：
$$
\forall x\in V_{1},x=\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_n
\end{pmatrix}=\begin{pmatrix}
a_{11}&a_{21}&\dots&a_{s1} \\
a_{12}&a_{22}&\dots&a_{s2}  \\
\vdots&\vdots&&\vdots \\
a_{1n}&a_{2n}&\dots&a_{sn} 
\end{pmatrix}\begin{pmatrix}
\lambda_{1} \\
\lambda_{2} \\
\vdots \\
\lambda_s
\end{pmatrix}
$$
另一方面，注意到：
$$
\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_s
\end{pmatrix}=\begin{pmatrix}
a_{11}&\dots&a_{s1} \\
\vdots&&\vdots \\
a_{1s}&\dots&a_{ss} 
\end{pmatrix}\begin{pmatrix}
\lambda_{1} \\
\lambda_{2} \\
\vdots \\
\lambda_s
\end{pmatrix}
$$
于是可以写成如下形式：
$$
\begin{align}

x&=\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_n
\end{pmatrix}=\begin{pmatrix}
a_{11}&a_{21}&\dots&a_{s1} \\
a_{12}&a_{22}&\dots&a_{s2}  \\
\vdots&\vdots&&\vdots \\
a_{1n}&a_{2n}&\dots&a_{sn} 
\end{pmatrix}\begin{pmatrix}
\lambda_{1} \\
\lambda_{2} \\
\vdots \\
\lambda_s
\end{pmatrix} \\
&=\begin{pmatrix}
a_{11}&a_{21}&\dots&a_{s1} \\
a_{12}&a_{22}&\dots&a_{s2}  \\
\vdots&\vdots&&\vdots \\
a_{1n}&a_{2n}&\dots&a_{sn} 
\end{pmatrix}\begin{pmatrix}
a_{11}&\dots&a_{s1} \\
\vdots&&\vdots \\
a_{1s}&\dots&a_{ss} 
\end{pmatrix}^{-1}\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_s
\end{pmatrix}
\end{align}
$$
将左边的两个矩阵乘起来，令为 B，并且补充上足够多的 0 ，得到：
$$
\begin{align}

x&=\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_n
\end{pmatrix}=\begin{pmatrix}
b_{11}&b_{21}&\dots&b_{s1} &0&\dots&0\\
b_{12}&b_{22}&\dots&b_{s2} &0&\dots&0 \\
\vdots&\vdots&&\vdots &\vdots&&\vdots\\
b_{1n}&b_{2n}&\dots&b_{sn}&0&\dots&0 
\end{pmatrix}\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_n
\end{pmatrix}
\end{align}
$$
于是可以构造出如下的矩阵：
$$
\left[\begin{pmatrix}
b_{11}&b_{21}&\dots&b_{s1} &0&\dots&0\\
b_{12}&b_{22}&\dots&b_{s2} &0&\dots&0 \\
\vdots&\vdots&&\vdots &\vdots&&\vdots\\
b_{1n}&b_{2n}&\dots&b_{sn}&0&\dots&0 
\end{pmatrix}-I_{n\times n}\right]\begin{pmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_n
\end{pmatrix}=\mathbf{0}
$$
这即是该矩阵的零空间

### 问题：共同的性质

#### 问题

>[!question] 问题
>这样的表示是唯一的吗？如果不是的话，所有可以选择的矩阵 $A$ 有什么共同的性质吗？

方法一相当于是证明了：如果 $A$ 的行空间是 $V_{1}^\perp$，则 $\ker(A)=V_{1}$ 

想要找到矩阵 $A$ 共同的性质，只需要证明逆命题，即：
$$
V_{1}=\ker(A) \implies Row(A)=V_{1}^\perp
$$
#### 引理

此时需要引理：

>[!note] 引理
>$$Row(A)=\ker(A)^\perp$$

考察 $A$ 的任一行向量 $r$，若 $Ax=0$，则必有：
$$
rx=0
$$
此时有：
$$
Row(A)\subset \ker(A)^\perp
$$
而由维数定理，知道：
$$
\dim(\ker(A)^\perp)=n-\dim(\ker(A))=n-(n-\text{rank}(A))=\text{rank}(A)=\dim(Row(A))
$$
于是此时有：
$$
Row(A)=\ker(A)^\perp
$$
引理证毕

这个引理有非常好的直观理解。矩阵的零空间必定跟其行空间正交，于是零空间的正交补必定是行空间

#### 定理的证明

而由引理可知：
$$
V_{1}=\ker(A)=Row(A)^\perp
$$
两边同时取正交补，得到：
$$
Row(A)=V_{1}^\perp
$$
定理证毕

### 总结

在有限维实内积空间 $\mathbb R^n$ 中，配备标准内积时，对任意矩阵 $A$，其行空间等于零空间的正交补。这也就意味着：若要把一个**线性空间的子空间** $V_{1}$ 写成某个矩阵的**零空间**，也即让线性空间的子空间等于**某个行空间的正交补**。而 $(V_{1}^\perp)^\perp=V_{1}$，于是行空间取成该子空间的正交补即可。

这个结论非常的优雅！