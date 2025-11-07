# 拉普拉斯展开定理 (Laplace expansion)
## 概述
$$
|A|=\sum_{1\leq s_{1} <\dots<s_p \leq n} (-1)^{s_{1}+s_{2}+\dots+s_p+t_1+t_{2}+\dots+t_p}
\left| \mathbf{A} \begin{pmatrix} t_{1},\cdots,t_p \\ s_1,\cdots,s_p \end{pmatrix} \right| \left| \mathbf{A} \begin{pmatrix} t_{p+1},\cdots,t_n\\ s_{p+1},\cdots,s_n \end{pmatrix} \right|.
$$
也即：选定 p 行，方阵的行列式等于这 p 行内的**所有** **p 阶子式**乘以该子式的**代数余子式**

注意，符号并不是将所有的角标求和（这样做一定是偶数），而是将所有的选定的行指标和选定的列指标求和
## 证明
### 证明一：对列指标分类求和
#### 引理：两段序列拼在一起后的逆序数

这段引理在：[[矩阵的分块#对角分块的行列式计算]] 中曾经使用过类似情形
同样的，这段引理在 [[行列式的按一行展开]] 中使用过一段序列退化为长度为 1 的情形

任意选定 $p$ 列，列指标为 $s_1 < \cdots < s_p$ ，其余列指标依大小为 $s_{p+1} < \cdots < s_n$ 
取：$(j_{1},j_{2}, \dots,j_p) 为 (s_{1},s_{2},\dots,s_p)的排列$ 
取：$(j_{p+1},j_{p+2}, \dots,j_n) 为 (s_{p+1},s_{p+2},\dots,s_n)的排列$ 
则有：
$$
\begin{align}
\tau(j_{1}, j_{2},\dots,j_n) =& \tau(j_{1},j_{2},\dots,j_p) + \tau(j_{p+1},j_{p+2},\dots ,j_n) \\
 &+ (s_{1}-1) + (s_{2}-2)+\dots+(s_p-p)
\end{align}
$$
#### 引理的证明：

将 n 个数分为两段，则可以将整个序列的逆序数分为三类：
第一类是第一段中的逆序数；
第二类是第二段中的逆序数；
第三类是第一段中的数与第二段中的数之间产生的逆序数：考察第一段中的 $s_k$ ，他与第二段内所有比他小的数都会组成逆序数，但是第一段内有 k - 1 个比他小的数，所以在第二段内有 $(s_k -1) - (k-1)=s_k-k$ 个比他小的数，求和即可
#### 定理的证明

选定 $p$ 行，行指标为 $t_1 < \cdots < t_p$ ，其余行指标依大小为 $t_{p+1} < \cdots < t_n$ 

任选 $p$ 列，列指标为 $s_1 < \cdots < s_p$ ，其余列指标依大小为 $s_{p+1} < \cdots < s_n$ 
取：$(j_{1},j_{2}, \dots,j_p) 为 (s_{1},s_{2},\dots,s_p)的排列$ 
取：$(j_{p+1},j_{p+2}, \dots,j_n) 为 (s_{p+1},s_{p+2},\dots,s_n)的排列$ 

考察每一个出现在行列式按定义展开式中的单项：
注意：这里的 t1 ~ tn 不是自然序，所以需要统计逆序数并参与正负号的讨论
参看：[[转置#观点：行列式中，行与列地位上相等]] 对于同时将行和列统计逆序数的描述
$$
(-1)^{\tau(j_{1},j_{2},\dots,j_n)+\tau(t_{1},t_{2},\dots,t_n)}a_{t_1j_{1}}a_{t_{2}j_{2}}\dots a_{t_nj_n}
$$
**一重求和**：
将这样的单项分为 p! 组，使得每一组的 $(j_{1},j_{2}, \dots,j_p)$ 都是相同的，将其作为公因式提取
**二重求和**：
而在每一组中，有 (n-p)! 项，使得每一项都是 $(j_{p+1},j_{p+2}, \dots,j_n)$ 的一个排列

而这两个分组操作之间相互独立，因此上述两重求和可以换序和提公因式

**三重求和**：
考虑到：任选的 p 列选法是不一定的，所以需要对所有的列的选法求和，共有 $C_n^p$ 种

**统计数目**：
对于 det(A) 的定义式展开，共有 n! 项
对于上述求和过程使用乘法原理，得到共有 $C_n^p\cdot p!\cdot (n-p)! = n!$ 项
可以知道数目是正确的

因此有：
$$
\begin{align} 

|A|&= \sum_{(j_{1},j_{2},\dots,j_n)}(-1)^{\tau(j_{1},j_{2},\dots,j_n)+\tau(t_{1},t_{2},\dots,t_n)}a_{t_1j_{1}}a_{t_{2}j_{2}}\dots a_{t_nj_n} \\ \\


&=\sum_{1\leq s_{1}<\dots<s_p\leq n} \sum_{(j_{1},j_{2},\dots j_p)}\sum_{(j_{p+1},j_{p+2},\dots ,j_n)} (-1)^{\tau(j_{1},j_{2},\dots,j_n)+\tau(t_{1},t_{2},\dots,t_n)}a_{t_1j_{1}}a_{t_{2}j_{2}}\dots a_{t_nj_n} \\
 \\
&=\sum_{1\leq s_{1}<\dots<s_p\leq n}  
\sum_{(j_{1},j_{2},\dots j_p)}  
a_{t_1j_{1}}a_{t_{2}j_{2}}\dots a_{t_pj_p}
\sum_{(j_{p+1},j_{p+2},\dots ,j_n)} (-1)^{\tau(j_{1},j_{2},\dots,j_n)+\tau(t_{1},t_{2},\dots,t_n)} 
a_{t_{p+1}j_{p+1}}a_{t_{p+2}j_{p+2}}\dots a_{t_nj_n}
\end{align}

$$
由引理，将 $\tau$ 展开，首先考察其中的符号项：
考察 $\tau(t_{1},\dots ,t_n)$ ：
$$
\begin{align}
\tau(t_{1},\dots ,t_n) =& \tau(t_{1},t_{2},\dots,t_p) + \tau(t_{p+1},t_{p+2},\dots ,t_n) \\
 &+ (t_{1}-1) + (t_{2}-2)+\dots+(t_p-p) \\
=& (t_{1}+t_{2}+\dots+t_n) + \frac{p(p+1)}{2}
\end{align}
$$
由于 $(t_{1},t_{2},\dots,t_p), (t_{p+1},t_{p+2},\dots ,t_n)$ 都被规定为自然序，所以逆序数等于零
故而：
$$
\begin{align}
&\ \ \ \ (-1)^{\tau(j_{1},\dots,j_p)+\tau(j_{p+1},\dots,j_n)+(s_{1}+\dots+s_{p})-\frac{(1+p)p}{2}+\tau(t_{1},\dots,t_n)}  \\
&=(-1)^{\tau(j_{1},\dots,j_p)+\tau(j_{p+1},\dots,j_n)+(s_{1}+\dots+s_{p})+(t_{1}+\dots+t_{p})-(1+p)p} \\
&=(-1)^{\tau(j_{1},\dots,j_p)+\tau(j_{p+1},\dots,j_n)+(s_{1}+\dots+s_{p})+(t_{1}+\dots+t_{p})}
\end{align}
$$
由于：p(p+1) 一定为偶数，所以抹去

因此，上式经过提公因式得到：
$$
\begin{align}
&=\sum_{1\leq s_{1}<\dots<s_p\leq n}  
\sum_{(j_{1},j_{2},\dots j_p)}  
a_{t_1j_{1}}a_{t_{2}j_{2}}\dots a_{t_pj_p}
\sum_{(j_{p+1},j_{p+2},\dots ,j_n)} (-1)^{\tau(j_{1},\dots,j_p)+\tau(j_{p+1},\dots,j_n)+(s_{1}+\dots+s_{p})+(t_{1}+\dots+t_{p})} 
a_{t_{p+1}j_{p+1}}a_{t_{p+2}j_{p+2}}\dots a_{t_nj_n} \\
 \\
&=\sum_{1\leq s_{1}<\dots<s_p\leq n} (-1)^{(s_{1}+\dots+s_{p})+(t_{1}+\dots+t_{p})} 
\sum_{(j_{1},j_{2},\dots j_p)} (-1)^{\tau(j_{1},\dots,j_p)} 
a_{t_1j_{1}}a_{t_{2}j_{2}}\dots a_{t_pj_p}
\sum_{(j_{p+1},j_{p+2},\dots ,j_n)} (-1)^{\tau(j_{p+1},\dots,j_n)} 
a_{t_{p+1}j_{p+1}}a_{t_{p+2}j_{p+2}}\dots a_{t_nj_n} \\
 \\
&=\sum_{1\leq s_{1} <\dots<s_p \leq n} (-1)^{(s_{1}+s_{2}+\dots+s_p)+(t_1+t_{2}+\dots+t_p)}
\left| \mathbf{A} \begin{pmatrix} t_{1},\cdots,t_p \\ s_1,\cdots,s_p \end{pmatrix} \right| \left| \mathbf{A} \begin{pmatrix} t_{p+1},\cdots,t_n\\ s_{p+1},\cdots,s_n \end{pmatrix} \right|.
\end{align}
$$
证毕
### 证明二：使用特殊情况并推广

（参看王萼芳高等代数）
下面使用与证明一同样的符号系统

首先考察选定了最上面 p 行，最左面 p 列的情况（称为情形一），考察是否该项同样位于行列式的定义式展开中，显然是符合的

下面推广，如果不是最左面 p 列，只需要经过一系列的相邻 [[对换]] 即可将这种情况变为情形一。对换的次数应该等于：
$$
s_{1}-1+s_{2}-2+\dots+s_p - p=\sum_{h=1}^ps_h - \frac{p(p+1)}{2}
$$
同理，由行列对称性，如果不是最上面 p 列，只需经过如下次对换即可将这种情形变为情形一解决
$$
\sum_{h=1}^pt_h - \frac{p(p+1)}{2}
$$
因此，Laplace expansion 中的每一单项的绝对值都对应等于行列式的定义式展开某单项的绝对值，符号项由
$$
(-1)^{(s_{1}+\dots+s_p)+(t_{1}+\dots +t_p)} 
$$
决定

接下来只要考察两边项数是否相等即可，由证明一的 **统计数目** 部分，显然相等

证毕