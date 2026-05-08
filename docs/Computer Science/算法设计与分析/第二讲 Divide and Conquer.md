**分治（Divide and Conquer）**

---

**最大子序列（Maximum subarray）**

预先计算数组的前缀和$S[1,\cdots,n]$

$\text{Maxsub}A[1,\cdots,n]$

- 对$L,R,mid$

- 递归求解 $\text{Maxsub}(A[L,\cdots,mid])\to s_2$


- 递归求解 $\text{Maxsub}(A[mid+1,\cdots,R])\to s_3$
- 现求解跨越中点部分的最大值，找到$A[k_1,mid]$的最大值，即求$S[mid]-S[k_1-1],k_1:mid\to L$的最大值，同理，求出$A[mid+1,k_2]$的最大值，将二者相加得到$s_1$
- 返回 $\max\{s_1,s_2,s_3\}$ 

正确性证明：**利用数学归纳法证明**：$T(n)\leqslant c_1n\log n$

 $T(n)=2T(n/2)+O(n)=O(n\log n)$

此问题求解的最佳时间复杂度为$O(n)$

证明：不存在比$O(n)$更快的算法解决此问题。

---

**归并算法（Merge Sort）**

若$n=1$，$A[1,\cdots,n]\to S[1,\cdots,n]$

否则

（1）$\text{MergeSort}(A[1,\cdots,n/2])\to S_2[1,\cdots,n/2]$

（2）$\text{MergeSort}(A[n/2+1,\cdots,n])\to S_2[n/2+1,\cdots,n]$

（3）$\text{Merge}(S_1,S_2)\to S[1,\cdots,n]$

Return $S$

**使用数学归纳法证明算法正确性。**

递归树深度为$\log n$，每层时间复杂度为$O(n)$。

---

**逆序对计数（Inversion counting）**

利用归并排序辅助计数

---

**整数乘法（Integer Multiplication）**

考虑将数$x,y$分为两部分$2^{n/2}\cdot x_L,x_R,2^{n/2}\cdot y_L,y_R$

$xy=2^n x_Ly_L+2^{n/2}(x_Ly_R+x_Ry_L)+x_Ry_R$

时间复杂度为$T(n)=4T(n/2)+O(n)=O(n^2)$

考虑减少一次调用次数，由于$(x_L+x_R)(y_L+y_R)=(x_Ly_R+x_Ry_L)+(x_Ly_L+x_Ry_R)$

求解$(x_Ly_R+x_Ry_L)$可调用计算$(x_L+x_R)(y_L+y_R)-x_Ly_L-x_Ry_R$，仅需调用1次，此时

$T(n)=3T(n/2)+O(n)=O(n^{\log_23})=O(n^{1.59})$

优化后步骤：

（1）$x=2^{n/2} x_L+x_R,y=2^{n/2}y_L+y_R$

（2）$\text{IntMul}(x_L,x_R)\to t_1$

（3）$\text{IntMul}(y_L,y_R)\to t_2$

（4）$\text{IntMul}(x_L+x_R,y_L+y_R)\to t_3$

（5）return $2^n t_1+2^{n/2}(t_3-t_1-t_2)+t_2$

**三分法（Toom—3）**

1. **将两个大整数分别拆成3部分**；
2. 通过在特定位置进行多项式插值，将大整数乘法转化成在少数点上的多项式乘法问题；
3. 计算插值点的乘积，再通过插值恢复结果，得到最终积。

##### 1. 拆分整数

假设有两个大整数 \(x\) 和 \( y \)，将它们拆成三部分：

\[
x = 2^{2n/3} x_1 + 2^{n/3} x_2 + x_3
\]
\[
y = 2^{2n/3} y_1 + 2^{n/3} y_2 + y_3
\]

这里 \(n\) 是数字的位数，按照 \( n/3 \) 为单位拆分。

##### 2. 展开乘积

乘积 \(xy\) 可以写成：

\[
xy = 2^{4n/3} x_1 y_1 + 2^n (x_1 y_2 + x_2 y_1) + 2^{2n/3} (x_1 y_3 + x_2 y_2 + x_3 y_1) + 2^{n/3} (x_2 y_3 + x_3 y_2) + x_3 y_3
\]

发现需要计算五种部分的乘积和加法组合：

- \(x_1 y_1\)
- \(x_1 y_2 + x_2 y_1\)
- \(x_1 y_3 + x_2 y_2 + x_3 y_1\)
- \(x_2 y_3 + x_3 y_2\)
- \(x_3 y_3\)

##### 3. 多项式形式表示

将 \(x\) 和 \(y\) 看成多项式：

\[
x(B) = B^2 x_1 + B x_2 + x_3
\]
\[
y(B) = B^2 y_1 + B y_2 + y_3
\]

其中 \( B = 2^{n/3} \)。乘积是：

\[
z(B) = x(B) \times y(B)
\]

\(z(B)\) 的次数最多是4，写成：

\[
z(B) = z_4 B^4 + z_3 B^3 + z_2 B^2 + z_1 B + z_0
\]

##### 计算插值点 \( z(B) \) 的值

为了得到 \( z_i \) 系数，可以通过5个点的值插值，再计算：

\[
z(0), z(1), z(-1), z(2), z(-2)
\]

这里：

- \(z(0) = x_3 \cdot y_3\)
- \(z(1) = (x_1 + x_2 + x_3)(y_1 + y_2 + y_3)\)
- \(z(-1) = (x_1 - x_2 + x_3)(y_1 - y_2 + y_3)\)
- $z(2)=(4x_1+2x_2+x_3)(4y_1+2y_2+y_3)$
- $z(-2)=(4x_1-2x_2+x_3)(4y_1-2y_2+y_3)$

带入$0,\pm 1,\pm 2$，得到方程组：
\[
\begin{cases}
z(-2) = z_4 (-2)^4 + z_3 (-2)^3 + z_2 (-2)^2 + z_1 (-2) + z_0 \\
z(-1) = z_4 (-1)^4 + z_3 (-1)^3 + z_2 (-1)^2 + z_1 (-1) + z_0 \\
z(0) = z_4 (0)^4 + z_3 (0)^3 + z_2 (0)^2 + z_1 (0) + z_0 \\
z(1) = z_4 (1)^4 + z_3 (1)^3 + z_2 (1)^2 + z_1 (1) + z_0 \\
z(2) = z_4 (2)^4 + z_3 (2)^3 + z_2 (2)^2 + z_1 (2) + z_0 \\
\end{cases}
\]

##### 把每个多项式的幂写成矩阵，系数排列如下：

\[
\begin{bmatrix}
1 & (-2) & (-2)^2 & (-2)^3 & (-2)^4 \\
1 & (-1) & (-1)^2 & (-1)^3 & (-1)^4 \\
1 & 0 & 0 & 0 & 0 \\
1 & 1 & 1 & 1 & 1 \\
1 & 2 & 4 & 8 & 16 \\
\end{bmatrix}
\cdot
\begin{bmatrix}
z_0 \\ z_1 \\ z_2 \\ z_3 \\ z_4
\end{bmatrix}
=
\begin{bmatrix}
z(-2) \\ z(-1) \\ z(0) \\ z(1) \\ z(2)
\end{bmatrix}
\]

- 求解此矩阵方程即为**多项式插值恢复系数的线性代数方法**
- 因为 \(b_i\) 均不同且数量满足次数+1，矩阵是**范德蒙德矩阵**，它是可逆的（只要点两两不同），所以能唯一求解 \(z_0, z_1, \dots, z_4\)。

得到：

\[
\begin{pmatrix}
z_5 \\
z_4 \\
z_3 \\
z_2 \\
z_1
\end{pmatrix}
=
\begin{pmatrix}
0 & 0 & 1 & 0 & 0 \\
1/12 & -2/3 & 0 & 2/3 & -1/12 \\
-1/24 & 2/3 & -5/4 & 2/3 & -1/24 \\
-1/12 & 1/6 & 0 & -1/6 & 1/12 \\
1/24 & -1/6 & 1/4 & -1/6 & 1/24
\end{pmatrix}
\cdot
\begin{pmatrix}
z(-2) \\
z(-1) \\
z(0) \\
z(1) \\
z(2)
\end{pmatrix}
\]

即：

\[
z(B_*) =
\begin{pmatrix}
1 \\
B_* \\
B_*^2 \\
B_*^3 \\
B_*^4
\end{pmatrix}^T \cdot
\begin{pmatrix}
0 & 0 & 1 & 0 & 0 \\
1/12 & -2/3 & 0 & 2/3 & -1/12 \\
-1/24 & 2/3 & -5/4 & 2/3 & -1/24 \\
-1/12 & 1/6 & 0 & -1/6 & 1/12 \\
1/24 & -1/6 & 1/4 & -1/6 & 1/24
\end{pmatrix}
\cdot
\begin{pmatrix}
z(-2) \\
z(-1) \\
z(0) \\
z(1) \\
z(2)
\end{pmatrix}
\]



时间复杂度满足$T(n)=5T(n/3)+O(n)$，$T(n)=n^{\log_35}=O(n^{1.46})<n^{1.59}$

---

**多项式乘法（Polynomial multiplication）**

- 输入两个多项式：
  \[
  p(x) = a_0 + a_1 x + a_2 x^2 + \cdots + a_{n-1} x^{n-1}
  \]
  \[
  q(x) = b_0 + b_1 x + b_2 x^2 + \cdots + b_{n-1} x^{n-1}
  \]

- 输出它们的乘积：
  \[
  p(x) q(x) = c_0 + c_1 x + \cdots + c_{2n-2} x^{2n-2}
  \]

##### 乘积多项式的最高次为 \(2n - 2\)，因此设置：

\[
m = 2n - 1
\]

1. **计算 \(p(x)\) 在点 \(0, 1, 2, ..., m - 1\) 的取值**，即 \(p(0), p(1), ..., p(m-1)\)。

2. **计算 \(q(x)\) 在同样点的取值**，即
    \(q(0), q(1), ..., q(m-1)\)。

3. **逐点相乘得到乘积多项式的值**  
   计算：
   \[
   p(0) q(0), \quad p(1) q(1), \quad \ldots, \quad p(m-1) q(m-1)
   \]

4. **用这些点值做多项式插值还原**  
   根据这些点的乘积值，恢复多项式 \(p(x) q(x)\) 的所有系数 \(c_0, c_1, \ldots, c_{2n-2}\)。

用矩阵乘向量的方式，一次性计算所有点的值：

\[
\begin{pmatrix}
1 & 0 & \cdots & 0 \\
1 & 1 & \cdots & 1 \\
1 & 2 & \cdots & 2^{m-1} \\
\vdots &\vdots & & \vdots \\
1 & m-1 & \cdots & (m-1)^{m-1}
\end{pmatrix}
\cdot
\begin{pmatrix}
a_0 \\
a_1 \\
\vdots \\
a_{m-1}
\end{pmatrix}
=
\begin{pmatrix}
p(0) \\
p(1) \\
\vdots \\
p(m-1)
\end{pmatrix}
\]

- **精度问题**：矩阵元素可能非常大，导致需要很高精度（\(O(n)\)词长）来保存。
- **效率问题**：矩阵向量乘法时间复杂度是 \(O(n^2)\)。

---

##### 利用单位根优化求值（FFT基础）

- 仍是计算多项式在多个点（共$m$个点）的值，但点位置改为**单位根**：

  \[
  \omega = \cos\frac{2\pi}{m} + i \sin \frac{2\pi}{m}
  \]

- 输出点变成：

  \[
  p(1), p(\omega), p(\omega^2), \ldots, p(\omega^{m-1})
  \]

---

#### 矩阵变成：

\[
\begin{pmatrix}
1 & 1 & \cdots & 1 \\
1 & \omega & \cdots & \omega^{m-1} \\
1 & \omega^2 & \cdots & \omega^{2(m-1)} \\
\vdots & \vdots & & \vdots \\
1 & \omega^{m-1} & \cdots & \omega^{(m-1)(m-1)}
\end{pmatrix}
\cdot
\begin{pmatrix}
a_0 \\
a_1 \\
\vdots \\
a_{m-1}
\end{pmatrix}
=
\begin{pmatrix}
p(0) \\
p(\omega) \\
\vdots \\
p(\omega^{m-1})
\end{pmatrix}
\]

---

##### 用FFT算法，可以把矩阵向量乘法加速到 \(O(n \log n)\)，但单位根是浮点数，需要注意精度。

---

#### FFT算法的分治递归思想

- **输入输出同上**，建议 \(m\) 是偶数。

- **将多项式拆分成偶次幂和奇次幂两部分**：

  \[
  p_e(x) = a_0 + a_2 x + a_4 x^2 + \cdots + a_{m-2} x^{\frac{m}{2}-1}
  \]
  \[
  p_o(x) = a_1 + a_3 x + a_5 x^2 + \cdots + a_{m-1} x^{\frac{m}{2}-1}
  \]

- 多项式表达为：

  \[
  p(x) = x\cdot p_o(x^2) + p_e(x^2)
  \]

#### 递归计算多项式值

- 计算 \(p(\omega^k)\) 分为两类：

  \[
  p(\omega^k) = p_o(\omega^{2k}) + \omega^k \cdot p_e(\omega^{2k}), \quad 0 \leq k \leq \frac{m}{2}-1
  \]

  \[
  p\left(\omega^{k + \frac{m}{2}}\right) = p_o(\omega^{2k}) - \omega^k \cdot p_e(\omega^{2k}), \quad 0 \leq k \leq \frac{m}{2} - 1
  \]

- 这里用到单位根性质：

  \[
  \omega^{k + \frac{m}{2}} = - \omega^k
  \]


---

时间复杂度$T(n)=2(T/2)+O(m)=O(m\log m)=O(n\log n)$

**多项式插值还原**

- 多项式值与系数的关系可写为：
  
  \[
  \begin{pmatrix}
  1 & 1 & \cdots & 1 \\
  1 & \omega & \cdots & \omega^{m-1} \\
  1 & \omega^2 & \cdots & \omega^{2(m-1)} \\
  \vdots & \vdots &  & \vdots \\
  1 & \omega^{m-1} & \cdots & \omega^{(m-1)(m-1)}
  \end{pmatrix}
  \cdot
  \begin{pmatrix}
  c_0 \\ c_1 \\ \vdots \\ c_{m-1}
  \end{pmatrix}
  =
  \begin{pmatrix}
  r(1) \\ r(\omega) \\ \vdots \\ r(\omega^{m-1})
  \end{pmatrix}
  \]

- 这个矩阵是上面**FFT求值时用的矩阵**，称为**范德蒙德矩阵**。

- 通过对上面的矩阵求逆，解线性方程得到系数：
  
  \[
  \begin{pmatrix}
  c_0 \\ c_1 \\ \vdots \\ c_{m-1}
  \end{pmatrix}
  =
  \text{(范德蒙德矩阵)}^{-1}
  \cdot
  \begin{pmatrix}
  r(1) \\ r(\omega) \\ \vdots \\ r(\omega^{m-1})
  \end{pmatrix}
  \]

- 直接求逆代价高，但单位根的结构使这个逆有解析形式：

  \[
  \text{逆矩阵} = \frac{1}{m}
  \begin{pmatrix}
  1 & 1 & \cdots & 1 \\
  1 & \omega^{-1} & \cdots & \omega^{-(m-1)} \\
  \vdots & \vdots &  & \vdots \\
  1 & \omega^{-(m-1)} & \cdots & \omega^{-(m-1)(m-1)}
  \end{pmatrix}
  \]

- 原FFT用 \(\omega = e^{2\pi i/m}\)，逆FFT用 \(\omega^{-1} = e^{-2\pi i/m}\)
- 计算公式相似，区别在于旋转方向和最后除以$m$

总流程：$2\times \text{FFT}+\text{逆FFT}$

注：FFT本质上是把**多项式系数转成点值**的正变换，插值就是把点值还原回多项式系数的逆变换。

给定多项式系数向量

\[
\mathbf{c} = (c_0, c_1, \ldots, c_{m-1})
\]

FFT通过乘以单位根矩阵

\[
F = \begin{pmatrix}
1 & 1 & \dots & 1 \\
1 & \omega & \dots & \omega^{m-1} \\
\dots & \dots & & \dots \\
1 & \omega^{m-1} & \dots & \omega^{(m-1)(m-1)}
\end{pmatrix}
\]

把系数转化成点上的值：

\[
\mathbf{r} = F \mathbf{c} = (r(1), r(\omega), \ldots, r(\omega^{m-1}))
\]

插值是：

- 已知点值 \(\mathbf{r}\)
- 求出使得 \(r(x) = \sum c_k x^k\) 各系数 \(\mathbf{c}\)

即解方程：

\[
F \mathbf{c} = \mathbf{r}
\]

直接求 \(\mathbf{c} = F^{-1} \mathbf{r}\)

关键是矩阵 \(F\) 是**范德蒙德矩阵**，对于单位根矩阵有明显性质：

\[
F^{-1} = \frac{1}{m} \overline{F}
\]

其中 \(\overline{F}\) 是元素共轭转置矩阵，对应单位根变成 \(\omega^{-1}\)。在此处使用逆FFT。

- 逆FFT就是用单位根的共轭 \(\omega^{-1} = e^{-2\pi i / m}\) 构成矩阵
- 乘以该矩阵并除以 \(m\)，即可完成从点值回到系数的转换

---

**矩阵乘法（Matrix multiplication）优化算法（Strassen算法）**

传统矩阵乘法时间复杂度：$\Theta(n^3)$

考虑分块：把两个 \(n \times n\) 大矩阵分成4个 \(n/2 \times n/2\) 小矩阵：
\[
X = \begin{pmatrix} A & B \\ C & D \end{pmatrix}, \quad Y = \begin{pmatrix} E & F \\ G & H \end{pmatrix}
\]

矩阵乘法可以写成4个子块：
\[
XY = \begin{pmatrix}
AE + BG & AF + BH \\
CE + DG & CF + DH
\end{pmatrix}
\]

##### 传统分块乘法递推

需要计算8个大小是\(n/2\)的矩阵乘法（\(AE, BG, AF, BH, CE, DG, CF, DH\)）

时间递推是：
\[
T(n) = 8 \cdot T(n/2) + \Theta(n^2)
\]

解这个递推，复杂度仍为 \(\Theta(n^3)\)，没有减少。

##### Strassen优化算法：用7次乘法代替8次

通过巧妙设计7个中间矩阵（线性组合），用7个乘法结果组合起来得到最终结果。

- 将大矩阵分解成7个**秩为1（rank-1）**的矩阵和相应的线性函数的组合
- 每个乘法对应计算这7个rank-1矩阵中的一个
- 最终通过线性组合还原出4个结果子矩阵

##### Strassen算法流程

设7个乘积为 \(P_1, ..., P_7\)，分别是对以下矩阵块的乘法：

- \(P_1 = (A + D)(E + H)\)
- \(P_2 = (C + D)E\)
- \(P_3 = A(F - H)\)
- \(P_4 = D(G - E)\)
- \(P_5 = (A + B)H\)
- \(P_6 = (C - A)(E + F)\)
- \(P_7 = (B - D)(G + H)\)

然后用这7个结果组合成结果矩阵4个块：

\[
\begin{cases}
XY_{11} = P_1 + P_4 - P_5 + P_7 \\
XY_{12} = P_3 + P_5 \\
XY_{21} = P_2 + P_4 \\
XY_{22} = P_1 - P_2 + P_3 + P_6
\end{cases}
\]

##### 新递推关系变为：

\[
T(n) = 7 T(n/2) + \Theta(n^2)
\]

**解该递推得到：**
\[
T(n) = O(n^{\log_2 7}) \approx O(n^{2.81})
\]

优于传统 \(O(n^3)\)。

**使用数学归纳法计算递归式**：$T(n)=7(n/2)+\Theta(n^2)$
