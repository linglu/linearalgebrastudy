#### 微分方程和exp(At)



---

2020-4-11 笔记：

一阶方程、一阶导数、常系数线性方程，转化为 线性代数的问题，关键思路是：常系数线性方程的解是指数形式的

如果在找一个指数形式，需要确定 指数是多少，系数是多少

纯指数形式是上次讲的纯幂形式在微分方程中的类似体

奇异矩阵 的 其中一个特征值 $\lambda_1=0$ 



假设 $V_{t+1} = AV_t$ ，那么 $V_t$ 的解形式是：$V_t = \sum\limits_{i}^{n} c_i\lambda_i^tx_i$，其中 $n$ 是矩阵$A$ 的特征值个数，$\lambda_i$ 是矩阵 $A$ 的第 $i$ 个特征值，$x_i$ 是矩阵 $A$ 的第 $i$ 个特征向量，有 $Ax_i=\lambda_ix_i$

证明：

$V_{t+1} = \sum\limits_{i}^{n} c_i\lambda_i^{t+1}x_i=\sum\limits_{i}^{n} c_i\lambda_i^t(\lambda_ix_i)=\sum\limits_{i}^{n} c_i\lambda_i^tAx_i=A\sum\limits_{i}^{n} c_i\lambda_i^tx_i=AV_t$



假设  $\frac{dV}{dt} = AV$，那么 $V$ 的解的形式是：$V=\sum\limits_{i}^{n} c_ie^{\lambda_it}x_i$，其中 $n$ 是矩阵$A$ 的特征值个数，$\lambda_i$ 是矩阵 $A$ 的第 $i$ 个特征值，$x_i$ 是矩阵 $A$ 的第 $i$ 个特征向量，有 $Ax_i=\lambda_ix_i$

证明：
$$
\frac{dV}{dt}=\sum\limits_{i}^{n} c_i\lambda_ie^{\lambda_it}x_i=\sum\limits_{i}^{n} c_ie^{\lambda_it}\lambda_ix_i=\sum\limits_{i}^{n} c_ie^{\lambda_it}Ax_i=A\sum\limits_{i}^{n} c_ie^{\lambda_it}x_i=AV
$$


| 假设                 | 解的一般形式                                   | 解的矩阵形式          |
| -------------------- | ---------------------------------------------- | --------------------- |
| $V_{t+1} = AV_t$     | $V_t = \sum\limits_{i}^{n} c_i\lambda_i^tx_i$  | $V_t=S\Lambda^tc$     |
| $\frac{dV}{dt} = AV$ | $V_t=\sum\limits_{i}^{n} c_ie^{\lambda_it}x_i$ | $V_t=Se^{\Lambda t}c$ |



按：对角矩阵 $D$ 的特征向量矩阵为 单位矩阵 $I$



新的假设：
$$
\frac{dU}{dt} = AU \\
U=SV
$$
其中 $S$ 为矩阵 $A$ 的特性向量矩阵。

则有
$$
\frac{\mathbb{d}U}{\mathbb{d}t}=\frac{\mathbb{d}SV}{\mathbb{d}t}=S\frac{\mathbb{d}V}{\mathbb{d}t}=ASV
$$
所以
$$
\frac{\mathbb{d}V}{\mathbb{d}t}=S^{-1}ASV = \Lambda V
$$
由上面表格中的假设可以得到 $V$ 的矩阵表达形式为（$\Lambda$ 的特性向量矩阵为单位矩阵 $I$，$V_0=Ic $）：
$$
V=e^{\Lambda t}c=e^{\Lambda t}V_0
$$
所以（$U_0=SV_0 \rightarrow V_0=S^{-1}U_0$）
$$
U=SV=Se^{\Lambda t}S^{-1}U_0=e^{At}U_0
$$


$e^{At}=Se^{\Lambda t}S^{-1}$ 由泰勒展开得到



当矩阵 $A$ 的所有特征值实部 $Re(\lambda) < 0 $ 时，$e^{\lambda t} \rightarrow 0$，最终结果收敛于 0

当矩阵 $A$ 中有特征值 $\lambda = 0$，其余特征值的实部 $Re(\lambda) < 0$ 时，$e^{0t} \rightarrow 1$，其余收敛于 0，于是最终结果收敛于某个稳定状态

---



**差分 和 微分 的含义**

已知 $V_0$ 和 $V_{t+1} = AV_t$，求 $V(t)$。

> 有点像数学归纳法

表示已知 初始值 和 相邻两个时刻之间的差分（difference），可以推知被观察的整条曲线 $V(t)$

$V(t) = A^tV_0 =S\Lambda^tS^{-1}V_0= S\Lambda^tc$

其中 $S$ 是由 $A$ 的**特征向量**作为列向量构成的矩阵，$\Lambda$ 是矩阵 $A$ 的**特征值**作为主对角线的矩阵，c 是初始值用矩阵A 的特征向量表示时的系数，$Sc=V_0$。



已知 $V_0$ 和 $\frac{dV}{dt} = AV$，求 $V(t)$。

表示已知在每个时刻的导数（微分），可以推知被观察的整条曲线 $V(t)$

$V(t) = Se^{\Lambda t}c=Se^{\Lambda t}S^{-1}V_0$

其中$S$ 为由 $A$ 的**特征向量** 作为列向量构成的矩阵， $e$ 为自然对数，$\Lambda$ 为矩阵 $A$ 的**特征值**作为主对角线的矩阵，c 是初始值用矩阵A 的特征向量表示时的系数，$Sc=V_0$ 。



特征值 和 特征向量 的作用是 解耦，又称对角化

$\frac{du}{dt} = Au$，矩阵$A$ 表明 $u_1$，$u_2$ 耦合，关键是如何解耦。

set $u = Sv$，用 特征向量矩阵 解耦它，所谓解耦，就是对角化。

$\frac{du}{dt}=\frac{dSv}{dt}=S\frac{dv}{dt}=Au=ASv$，$S$ 是常数矩阵，所以 $\frac{dv}{dt}=S^{-1}ASv=\Lambda v$，关键在于，以特征向量为基，将 $u$ 表示成 $Sv$，然后得到关于 $v$ 的对角化方程组



于是有
$$
\frac{\mathrm{d}u}{\mathrm{d}t}=Au=S\Lambda S^{-1}u=S\Lambda S^{-1}Sv=S\Lambda v\quad\mbox{其中}\frac{\mathrm{d}v}{\mathrm{d}t}=\Lambda v
$$




矩阵指数：$e^{At}$

指数的泰勒展开

$$
e^x=\sum\limits_{n=0}^\infin {\frac{e^0}{n!}x^n} = 1 + x + \frac{x^2}{2}+ \frac{x^3}{6} + ... + \frac{x^n}{n!}
$$
所以 
$$
\begin{equation}
\begin{aligned}
e^{At}&=I + At + \frac{(At)^2}{2}+ \frac{(At)^3}{6} + ... + \frac{(At)^n}{n!} \\
&=
SS^{-1}+S\Lambda S^{-1}t+\frac{S\Lambda^2S^{-1}t^2}{2}+\frac{S\Lambda^3S^{-1}t^3}{6}+ ...  +\frac{S\Lambda^nS^{-1}t^n}{n!}\\
&= S(I + \Lambda t + \frac{(\Lambda t)^2}{2}+ \frac{(\Lambda t)^3}{6} + ... + \frac{(\Lambda t)^n}{n!})S^{-1}\\
&=Se^{\Lambda t}S^{-1}
\end{aligned}
\end{equation}
$$






















