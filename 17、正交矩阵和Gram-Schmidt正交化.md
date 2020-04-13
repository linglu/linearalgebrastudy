#### 正交矩阵和Gram-Schmidt正交化



参考：https://www.jianshu.com/p/fd59f2471d61



**标准正交矩阵性质：**

设 $Q$ 是标准正交矩阵（由标准正交向量构成的矩阵），则有 $Q^TQ = I$

当 $Q$ 是方阵时，$Q^T=Q^{-1}$

**标准正交向量实例：**

1、旋转矩阵
$$
Q = \begin{bmatrix}
\cos\theta&-\sin\theta \\
\sin\theta&\cos\theta
\end{bmatrix}
$$
2、置换矩阵
$$
Q = \begin{bmatrix}
0&0&1\\
1&0&0\\
0&1&0
\end{bmatrix}
$$


3、镜像矩阵：$Q = I - 2uu^T$，其中 $u$ 是任意单位向量



以上矩阵的性质：
$$
Q^TQ=I
$$
只有当 Q 是方阵时，$Q^T = Q^{-1}$



**正交矩阵的投影：**
$$
P=A(A^TA)^{-1}A^T=Q(Q^TQ)^{-1}Q^T=QI^{-1}Q^T=QQ^T
$$
所以向量 $b$ 的投影为 $Pb=QQ^Tb$，当 $Q$ 为方阵时，$Q^T=Q^{-1}$，所以 $Pb=QQ^Tb=QQ^{-1}b=b$，即向量 $b$ 的投影为其自身。

反过来看，可以得到
$$
\begin{aligned}
b &= QQ^Tb\\
&=Q(Q^Tb)\\
&=q_1(q_1^Tb)+q_2(q_2^Tb)+...+q_n(q_n^Tb)
\end{aligned}
$$
即 向量$b$ 可以被分解成正交的小片，将这些小片加起来后可以得到向量 $b$

> 按：当矩阵A 为一般方阵时，可以运用正交化算法，将矩阵 A 的列空间的基正交化，得到表示有相同列空间的正交矩阵 Q。即 $C(A)=C(Q)$，前者的基不是正交的，后者的基是正交的。



**Gram-Schemidt 正交化算法**

假设我们有三个**不相关**的向量 a，b，c，目标是构造出三个正交的向量 A，B，C，然后再除以他们的长度

算法：

1、令 $A = q_1 = \frac{a}{|a|}$

2、令 $B^\prime$ = b - b在A上的投影 = $b-(q_1 \cdot b) q_1= b - q_1^Tbq_1$

3、$B = q_2 = \frac{B^\prime}{|B^\prime|}$

4、令 $C^\prime$ = c - c在A上的投影 - c 在 B 上的投影 = $c-(q_1 \cdot c)q_1-(q_2 \cdot c)q_2$

5、$C = q_3 = \frac{C^\prime}{|C^\prime|}$

如果有更多的向量，以此类推







