# Q 矩阵的交换子结构定理

>[!note] 定理
>方阵 $A\in M_n(\mathbb K)$，若 $A$ 的最小多项式次数为 $n$，则与方阵可交换的方阵构成的线性空间满足：$$\mathcal{C}(A)=\{X|AX=XA\}=\text{span} (I, A, \dots, A^{n-1})$$

这个定理的证明好复杂好复杂，下面给出能够使用这个定理的简要判别手段

1. 任取向量 $v$，通常不妨：$v=(1,0,0,\dots,0)^\top$ 
2. 验证向量组：$(v, Av, A^2v, \dots,A^{n-1}v)$ 是否线性无关
   若线性无关，则可以使用上述定理，通常这时已经算出来了
   若线性相关，则不可以使用上述定理，上面的活就白干了

### 定理：相似矩阵的交换子空间

>[!note] 相似矩阵的交换子空间
>$A, B$ 都是域 $\mathbb{F}$ 上的 $n$ 级矩阵，若 $A\sim B$，则有 $C(A)\cong C(B)$，则有 $\dim(C(A)) = \dim(C(B))$ 

由相似，可知存在可逆矩阵 $P$，$s.t.B=P^{-1}AP$ 
$$
\begin{align}
X\in C(A) &\iff XA=AX \\
&\iff XPBP^{-1}=PBP^{-1}X \\
&\iff (P^{-1}XP)B=B(P^{-1}XP) \\
&\iff P^{-1}XP\in C(B)
\end{align}
$$
也即这样建立了一个映射：
$$
\begin{align}
\sigma:C(A)&\to C(B) \\
X&\to P^{-1}XP
\end{align}
$$
显然这样的映射是双射，并且满足线性性，于是是同构，于是：
$$
C(A)\cong C(B)\implies \dim(C(A)) = \dim(C(B))
$$
证毕

