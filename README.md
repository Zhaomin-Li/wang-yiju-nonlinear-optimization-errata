# 非线性优化理论 王宜举 凸集分离定理勘误

## 勘误对象

课本中“推论 2.3.1”的证明大意为：设 $S_1,S_2\subset \mathbb{R}^n$ 为非空闭凸集，且

$$
S_1\cap S_2=\varnothing .
$$

令

$$
S=S_1-S_2=\{x-y:x\in S_1,\ y\in S_2\}.
$$

课本证明中使用了如下说法：

> 由 $S_1,S_2$ 的闭凸性知，$S$ 为闭凸集。

这一说法有误。虽然 $S_1-S_2$ 一定是凸集，但它未必是闭集。因此后续直接对 $S_1-S_2$ 使用需要闭性的凸集分离定理是不严谨的。

## 问题所在

闭凸集的 Minkowski 差未必闭。一个典型反例是

$$
S_1=\{(x,y)\in\mathbb{R}^2:y\ge e^x\},\qquad
S_2=\{(x,0):x\in\mathbb{R}\}.
$$

其中 $S_1,S_2$ 都是非空闭凸集，并且

$$
S_1\cap S_2=\varnothing .
$$

但

$$
S_1-S_2=\mathbb{R}\times(0,+\infty),
$$

它不是闭集。

所以，课本证明中从“$S_1,S_2$ 闭凸”推出“$S_1-S_2$ 闭凸”的步骤不成立。

## 正确结论

在仅假设 $S_1,S_2$ 为非空凸集且

$$
S_1\cap S_2=\varnothing
$$

时，可以推出弱分离：

存在 $p\ne 0$ 与 $\alpha\in\mathbb{R}$，使得

$$
p^Tx\ge \alpha \ge p^Ty,\qquad \forall x\in S_1,\ \forall y\in S_2.
$$

也就是说，超平面

$$
H=\{z\in\mathbb{R}^n:p^Tz=\alpha\}
$$

弱分离 $S_1$ 与 $S_2$。

若要得到严格分离

$$
p^Tx>\alpha>p^Ty,\qquad \forall x\in S_1,\ \forall y\in S_2,
$$

通常还需要附加条件，例如

$$
\operatorname{dist}(S_1,S_2)>0
$$

或等价地保证分离方向上存在正间隔。仅由闭凸且不相交，不能推出严格分离。

上面的反例中，取 $p=(0,1)^T$ 时有

$$
\inf_{x\in S_1}p^Tx=0,\qquad \sup_{y\in S_2}p^Ty=0,
$$

二者之间没有正间隔，因此不能选取 $\alpha$ 使得严格分离成立。

## 修正证明：弱分离

下面给出一个不需要 $S_1-S_2$ 闭性的证明。

### 引理 1：最佳逼近的刻画

设 $C$ 是内积空间 $\mathcal{H}$ 中的闭凸子集，$y\in\mathcal{H}$。则 $x_0\in C$ 是 $y$ 在 $C$ 上的最佳逼近元，当且仅当

$$
\operatorname{Re}\langle y-x_0,\ x_0-x\rangle\ge 0,\qquad \forall x\in C.
$$

在 $\mathbb{R}^n$ 中，上式即为

$$
(y-x_0)^T(x_0-x)\ge 0,\qquad \forall x\in C.
$$

### 引理 2：有限维凸集的支撑向量

设 $C\subset\mathbb{R}^n$ 为凸集，且 $0\notin C$。则存在 $p\ne 0$，使得

$$
p^Tz\ge 0,\qquad \forall z\in C.
$$

证明：反设结论不成立。则对任意 $p\ne 0$，都存在 $z\in C$，使得

$$
p^Tz<0.
$$

令欧氏单位球面为

$$
S^{n-1}=\{p\in\mathbb{R}^n:\|p\|_2=1\}.
$$

对每个 $z\in C$，定义开集

$$
U_z=\{p\in S^{n-1}:p^Tz<0\}.
$$

由反设，$\{U_z\}_{z\in C}$ 覆盖 $S^{n-1}$。由于 $S^{n-1}$ 紧，存在有限子覆盖

$$
S^{n-1}\subset \bigcup_{i=1}^k U_{z_i},\qquad z_1,\ldots,z_k\in C.
$$

记

$$
K=\operatorname{conv}\{z_1,\ldots,z_k\}.
$$

由于 $C$ 为凸集，故 $K\subset C$。又 $K$ 是有限个点的凸包，因此 $K$ 是紧凸集。

若 $0\notin K$，则 $0$ 在 $K$ 上存在唯一最佳逼近元 $u\in K$，并且 $u\ne 0$。由引理 1，取 $y=0,x_0=u$，得到

$$
(-u)^T(u-x)\ge 0,\qquad \forall x\in K.
$$

于是

$$
u^Tx\ge \|u\|^2>0,\qquad \forall x\in K.
$$

特别地，

$$
u^Tz_i>0,\qquad i=1,\ldots,k.
$$

令

$$
p=\frac{u}{\|u\|_2}\in S^{n-1}.
$$

则

$$
p^Tz_i>0,\qquad i=1,\ldots,k,
$$

所以 $p\notin U_{z_i}$ 对所有 $i=1,\ldots,k$ 成立，这与

$$
S^{n-1}\subset \bigcup_{i=1}^k U_{z_i}
$$

矛盾。因此只能有 $0\in K$。但 $K\subset C$，于是 $0\in C$，又与假设 $0\notin C$ 矛盾。

故反设不成立，引理得证。

### 推论：非空凸集的弱分离

设 $S_1,S_2\subset\mathbb{R}^n$ 为非空凸集，且

$$
S_1\cap S_2=\varnothing .
$$

令

$$
C=S_1-S_2=\{x-y:x\in S_1,\ y\in S_2\}.
$$

则 $C$ 是凸集。又因为 $S_1\cap S_2=\varnothing$，所以

$$
0\notin C.
$$

由引理 2，存在 $p\ne 0$，使得

$$
p^Tz\ge 0,\qquad \forall z\in C.
$$

于是对任意 $x\in S_1,\ y\in S_2$，有 $x-y\in C$，从而

$$
p^T(x-y)\ge 0.
$$

即

$$
p^Tx\ge p^Ty,\qquad \forall x\in S_1,\ \forall y\in S_2.
$$

因此

$$
\sup_{y\in S_2}p^Ty\le \inf_{x\in S_1}p^Tx.
$$

由于 $S_1,S_2$ 非空，上式两端均为有限实数。任取

$$
\alpha\in\left[\sup_{y\in S_2}p^Ty,\ \inf_{x\in S_1}p^Tx\right],
$$

便得到

$$
p^Tx\ge \alpha\ge p^Ty,\qquad \forall x\in S_1,\ \forall y\in S_2.
$$

故超平面

$$
H=\{z\in\mathbb{R}^n:p^Tz=\alpha\}
$$

弱分离 $S_1$ 与 $S_2$。

## 建议修改

1. 将“$S_1,S_2$ 为闭凸集且不相交，则可严格分离”改为“$S_1,S_2$ 为非空凸集且不相交，则可弱分离”。
2. 删除或修改“由 $S_1,S_2$ 的闭凸性知，$S_1-S_2$ 为闭凸集”这一错误表述。
3. 若保留严格分离结论，应额外加入保证正间隔的条件，例如 $\operatorname{dist}(S_1,S_2)>0$。
