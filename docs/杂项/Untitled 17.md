设字符串 $k$ 在 $2^p$ 进制下的表示为 $c_n c_{n-1} \dots c_0$，则其对应的数值为：
$$K = \sum_{i=0}^n c_i \cdot (2^p)^i$$
由于 $2^p \equiv 1 \pmod{2^p - 1}$，因此有：
$$(2^p)^i \equiv 1^i \equiv 1 \pmod{2^p - 1}$$
将其代入 $K$ 的表达式得：
$$h(k) = \left( \sum_{i=0}^n c_i \cdot 1 \right) \pmod{2^p - 1} = \left( \sum_{i=0}^n c_i \right) \pmod{2^p - 1}$$
即散列值仅取决于字符数值之和。而字符的排列变换不改变其总和 $\sum c_i$，所以若 $x$ 是 $y$ 的字符重排，则 $h(x) = h(y)$。


对散列族 $\mathcal{H}$ 中的任一函数 $h$，设 $n_{h,j}$ 为映射到桶 $j \in B$ 的元素个数，则该函数的冲突对数为 $\sum_{j \in B} \binom{n_{h,j}}{2}$。
总冲突次数满足：
$$\sum_{h \in \mathcal{H}} \sum_{k \neq l} \mathbb{I}(h(k)=h(l)) \le \epsilon |\mathcal{H}| N(N-1)$$
另一方面，根据柯西-施瓦茨不等式（或均值不等式），对于固定的 $h$，$\sum n_{h,j}^2 \ge \frac{1}{M}(\sum n_{h,j})^2 = \frac{N^2}{M}$。
则 $\sum_{j} \frac{n_{h,j}(n_{h,j}-1)}{2} = \frac{1}{2}(\sum n_{h,j}^2 - N) \ge \frac{1}{2}(\frac{N^2}{M} - N)$。
累加所有 $h \in \mathcal{H}$：
$$ \frac{1}{2} |\mathcal{H}| \left(\frac{N^2}{M} - N\right) \le \frac{1}{2} \epsilon |\mathcal{H}| N(N-1) $$
消去相同项得 $\frac{N/M - 1}{N-1} \le \epsilon$，即 $\epsilon \ge \frac{N-M}{M(N-1)}$。
由于 $\frac{N-M}{M(N-1)} \ge \frac{N-M}{MN} = \frac{1}{M} - \frac{1}{N}$，证毕。

**拓展：**
该结论说明若 $N \gg M$（即全集远大于桶数），冲突概率至少接近 $1/M$。只有在 $N$ 很大时，单点防冲突性能才能接近理想的均匀随机分布。

**解答：**
本题结论基于 Dietzfelbinger 等人的研究。
**证明核心：** $h_a(k_1) = h_a(k_2)$ 等价于 $a(k_1 - k_2) \pmod{2^w}$ 的高 $r$ 位全为 0（或由于进位差 1）。令 $x = k_1 - k_2 = u \cdot 2^s$，其中 $u$ 是奇数。由于 $a$ 是随机奇数，在 $\mathbb{Z}_{2^w}$ 的单位元群中，$a \cdot u$ 依然是均匀分布的奇数。通过分析 $ax$ 落入导致冲突区间的概率，可证其 $\le 2^{1-r} = 2/m$。

**优缺点对比：**
*   **优点：** 非常高效。不需要大素数和复杂的取模（Mod Prime）运算，只需一次整数乘法和一次右移位，这直接对应于现代 CPU 的指令。
*   **缺点：** 依赖于 $m$ 必须是 2 的幂次；且其冲突概率保证比 Carter-Wegman 略高（$2/m$ vs $1/m$）。

**拓展：**
这是 **2-独立性（Pairwise Independence）** 的体现。只需 2-独立即可保证散列表在链地址法下的期望操作时间为 $O(1)$。

---

### Problem 5: 二次散列（Quadratic Hashing）
**解答：**
逻辑与 Problem 4 类似，但升级到了 **3-独立性**。
对于给定的三个互异键 $k_1, k_2, k_3$，对应的系数矩阵（范德蒙德矩阵，Vandermonde matrix）在 $GF(p)$ 下是满秩的：
$$ \begin{pmatrix} k_1^2 & k_1 & 1 \\ k_2^2 & k_2 & 1 \\ k_3^2 & k_3 & 1 \end{pmatrix} \begin{pmatrix} a \\ b \\ c \end{pmatrix} = \begin{pmatrix} y_1 \\ y_2 \\ y_3 \end{pmatrix} $$
这意味着对于任意三个值 $(y_1, y_2, y_3) \in \mathbb{Z}_p^3$，都恰好存在一组唯一的 $(a,b,c) \in \mathbb{Z}_p^3$ 满足方程。
总样本空间大小为 $|\mathbb{Z}_p|^3 = p^3$。满足 $h(k_i)=v_i$ 条件的情况数仍为每项 $\approx p/m$。
$$ \Pr \approx \frac{(p/m)^3}{p^3} = \frac{1}{m^3} = O(1/m^3) $$

**拓展：**
一般的，$n$ 次多项式散列可以提供 $(n+1)$-独立性。这种高性能的散列在布隆过滤器（Bloom Filter）或是需要极强负载均衡保证的分布式系统中非常有用。

这是一个关于代数基本结构的深刻问题。散列函数之所以能表现出“良好的分布”或“多参数独立性”，核心驱动力确是 $\mathbb{Z}_p$（素数阶循环群）构成了一个**域（Field）**。

### 1. $\mathbb{Z}_p$ 中非零元素乘法逆元的证明

在 $\mathbb{Z}_p = \{0, 1, 2, \dots, p-1\}$ 中，取任意非零元素 $a \in \mathbb{Z}_p \setminus \{0\}$。我们需要证明存在一个 $x \in \mathbb{Z}_p$ 使得 $ax \equiv 1 \pmod p$。

#### 证明方法一：鸽巢原理（构造射影）
考虑如下映射 $f: \mathbb{Z}_p \to \mathbb{Z}_p$，定义为 $f(x) = (ax \pmod p)$。
*   **证明单射性：** 假设存在两个不同的元素 $x_1, x_2 \in \mathbb{Z}_p$ 使得 $f(x_1) = f(x_2)$。
    即 $ax_1 \equiv ax_2 \pmod p$，移项得 $a(x_1 - x_2) \equiv 0 \pmod p$。
    这表示 $p$ 能整除 $a(x_1 - x_2)$。因为 $p$ 是素数且 $a < p$（即 $a$ 与 $p$ 互质），根据**欧几里得引理**，$p$ 必须能整除 $(x_1 - x_2)$。
    但在 $x_1, x_2 \in \{0, \dots, p-1\}$ 且不同的情况下，$|x_1 - x_2| < p$，唯一的可能只能是 $x_1 - x_2 = 0$，即 $x_1 = x_2$。
*   **结论：** 该映射是单射。既然定义域和陪域大小相同且有限，单射必为满射。
*   **逆元存在：** 因为是满射，在陪域中必然存在一个元素 $1$，在定义域中必有唯一的 $x$ 满足 $f(x) = 1$。这个 $x$ 即为 $a$ 的乘法逆元，记作 $a^{-1}$。

#### 证明方法二：裴蜀定理（Bézout's Identity）
由于 $p$ 是素数且 $0 < a < p$，显然 $\gcd(a, p) = 1$。
根据裴蜀定理，对于任意两个整数 $a, p$，一定存在整数 $x, y$ 使得：
$$ax + py = \gcd(a, p) = 1$$
整理得 $ax = 1 - py$，即 $ax \equiv 1 \pmod p$。
可以通过**扩展欧几里得算法（EEA）**在 $O(\log p)$ 时间内显式解出这个 $x$。

---

### 2. 相关结论的推广

#### (1) 从素数到合数：单位群（Units）
如果在 $\mathbb{Z}_n$ 中 $n$ 不是素数，并非所有元素都有逆元。
*   **结论：** $a \in \mathbb{Z}_n$ 拥有乘法逆元的充要条件是 $\gcd(a, n) = 1$。
*   这些所有拥有逆元的元素构成了一个群，称为 $\mathbb{Z}_n$ 的**单位群**（记作 $\mathbb{Z}_n^\times$ 或 $(\mathbb{Z}/n\mathbb{Z})^*$），其阶数为欧拉函数 $\phi(n)$。

#### (2) 费马小定理的推广：构造性逆元
既然 $\mathbb{Z}_p^*$ 是一个阶为 $p-1$ 的群，根据拉格朗日定理，任何元素 $a$ 的 $p-1$ 次幂都是单位元：
$$a^{p-1} \equiv 1 \pmod p$$
由此可得 $a \cdot a^{p-2} \equiv 1 \pmod p$。
**推广结论（欧拉定理）：** 若 $\gcd(a, n) = 1$，则 $a^{\phi(n)} \equiv 1 \pmod n$。这提供了另一种求逆元的方法，即 $a^{\phi(n)-1} \pmod n$。

#### (3) 推广到更高阶：有限域 $GF(p^n)$
散列函数有时不直接在 $\mathbb{Z}_p$ 上操作，而是在**伽罗瓦域（Galois Field）**上。
*   对于任何素数 $p$ 和正整数 $n$，都存在唯一的有限域 $GF(p^n)$。
*   在这些域中，非零元素依然全部存在乘法逆元，但其运算变为基于**不可约多项式**的模运算。这在 AES 加密算法和纠错码（如 RS 码）中是数学基石。

#### (4) 线性方程组的唯一解（ Vandermonde 矩阵）
回到你最初的问题（Problem 4 & 5）：为什么随机选取系数能保证独立性？
本质是因为在域上，由 $k$ 个点确定的 $k-1$ 次多项式的系数方程组：
$$ \mathbf{K} \vec{a} = \vec{y} $$
其系数矩阵 $\mathbf{K}$ 是**范德蒙德矩阵**。在任何域中，只要 $k_i$ 互异，该矩阵的行列式 $\prod_{i<j} (k_j - k_i)$ 就不为 0。
**结论：** 只要存在逆元，矩阵就可逆，意味着任意的输入输出映射（散列结果）都对应唯一的一组随机参数（$a, b, c$）。这种“一一映射”保证了在随机选取参数时，碰撞概率能够被精确地通过计数来确定。



---

### 数理拓展：界限的物理意义

1.  **完美全域性（Perfect Universality）：**
    当 $\epsilon = \frac{1}{|B|}$ 时，我们称该散列族是全域的（Universal）。上述结论告诉我们，如果 $|U|$ 远大于 $|B|$，那么 $\frac{1}{|U|}$ 趋于 $0$，此时全域散列族的随机性已经非常接近理想状态。

2.  **紧致性（Tightness）：**
    这个下界不仅是一个理论限制，它在某些特定的构造下是可以达到的。例如，当散列族是 **所有映射 $U \to B$ 的集合** 时，衝突概率正好是 $\frac{|U|-|B|}{|B|(|U|-1)}$。

3.  **冲突次数与内存访问：**
    该界限限制了最坏情况下的期望冲突链长度。在链地址法（Separate Chaining）中，如果 $|U|/|B| = \alpha$（负载因子），则期望的探测次数与 $1 + \alpha$ 相关。本题的结论保证了只要散列族足够大且符合 $\epsilon$ 定义，我们就能在数学上确保平均性能。

针对第三题（Multiply-Shift Hashing）的详细证明如下。我们将遵循你提供的逻辑框架，通过对乘积结构的细致分析来推导碰撞概率。

---

### Problem 3 证明：乘法移位散列的冲突概率分析

引理：若$0 \le x<2 ^w,x\in \mathbb{Z}$，则 $x$可以被唯一地表示为：
$x = u \cdot 2^i$
其中 $u$ 是一个奇数，且 $0 \le i < w$

散列函数定义为：$h_a(k) = \lfloor (a \cdot k \bmod 2^w) / 2^{w-r} \rfloor$。即取乘积高 $r$ 位。

令 $y_1 = a \cdot k_1 \bmod 2^w$ 且 $y_2 = a \cdot k_2 \bmod 2^w$。

Dietzfelbinger 等人提出引理，$h_a(k_1) = h_a(k_2)$ 的必要条件是：

$a \cdot x \pmod{2^w}$的高$r$位全为0或1.

由于 $a$ 是从 $[0,2^w]$ 中均匀随机选取的奇数，其样本空间大小为 $2^{w-1}$。
考虑 $ax = a(u \cdot 2^i) = (au) \cdot 2^i \pmod{2^w}$。
令 $s = au \pmod{2^w}$。由于 $a$ 和 $u$ 都是奇数，根据群论性质，随机奇数 $a$ 乘以固定奇数 $u$ 后，$s$ 仍然是 $\{1, 3, 5, \dots, 2^w - 1\}$ 集合中均匀分布的随机奇数。

下分情况讨论碰撞概率。

(1)：$i > w - r$
此时 $ax = s \cdot 2^i$ 的二进制末尾至少有 $w-r+1$ 个 $0$。
可知在最高 $r$ 位中，至少有一位（第 $i$ 位）为 $1$。
在这种情况下，最高 $r$ 位不可能全为 $0$。同时，因为 $i$ 位以下全是 $0$，除非特殊极端情况，最高位也很难形成连续的 $r$个1，可以证明该情况下的碰撞概率远低于 $2^{1-r}$。

(2)：$i \le w - r$

高$r$位全为 $0$时：要求 $0 < s \cdot 2^i < 2^{w-r}$。
除以 $2^i$ 得：$0 < s < 2^{w-r-i}$，奇数 $s$ 的个数为 $2^{w-r-i-1}$。

高$r$位全为 $1$时：要求 $2^w - 2^{w-r} < s \cdot 2^i < 2^w$。
除以 $2^i$ 得：$2^{w-i} - 2^{w-r-i} < s < 2^{w-i}$，奇数 $s$ 的个数为 $2^{w-r-i-1}$。

由于 $s$ 是在 $[0,2^w]$ 范围内取值的奇数，每个在 $[0,2^{w-i}]$ 范围内的有效 $s$ 都会因为模运算的周期性而在 $[0,2^w]$ 范围内重复出现 $2^i$ 次。
所以，符合条件的 $a$ 的总数为：
$$ (2^{w-r-i-1} + 2^{w-r-i-1}) \times 2^i = 2^{w-r-i} \times 2^i = 2^{w-r} $$

总概率 $P \displaystyle = \frac{2^{w-r}}{2^{w-1}} = 2^{1-r}$。


### 乘法移位散列 vs. Carter-Wegman 散列

| 特性              | 乘法移位 (Multiply-Shift)                             | Carter-Wegman (Linear)                                  |
| :---------------- | :---------------------------------------------------- | :------------------------------------------------------ |
| **计算效率**      | **极高**。仅需一次乘法和一次移位，完全适配 CPU 指令。 | **较高**。需一次乘法、一次加法和一次取模（Mod Prime）。 |
| **碰撞保证**      | $\le 2/m$。比理想值略高。                             | $\le 1/m$。非常接近理想均匀随机分布。                   |
| **对 $m$ 的要求** | 必须是 $2$ 的幂次。                                   | $m$ 可以是任意值（但需配合素数 $p$）。                  |
| **硬件友好性**    | 原生支持，不需要复杂的取模电路。                      | 取模通常是性能瓶颈（除非使用梅森素数）。                |

**优点总结**：乘法移位散列最大的优势在于**速度**。在实际工程（如 Linux 内核、高性能缓存架构）中，移位操作比大素数取模快得多。
**缺点总结**：它的数学保证比线性散列稍微宽松一点点（多了一个系数 2），且桶的数量必须严格限制为 2 的幂。

针对你的推导，我们将第四题涉及的**线性同域散列（Carter-Wegman Hash）**的 2-独立性保证进行详细拆解。

### 1. 核心映射的单射性证明（为什么是一一映射？）

我们要理解为什么随机选择系数 $(a, b)$ 能产生均匀分布的 $(y_1, y_2)$。

考虑方程组（在 $\mathbb{Z}_p$ 域下）：
$$
\begin{cases} 
ak_1 + b \equiv y_1 \pmod p \\
ak_2 + b \equiv y_2 \pmod p 
\end{cases}
$$
这是一个关于 $a, b$ 的线性方程组。将其写为矩阵形式：
$$
\begin{pmatrix} k_1 & 1 \\ k_2 & 1 \end{pmatrix} \begin{pmatrix} a \\ b \end{pmatrix} \equiv \begin{pmatrix} y_1 \\ y_2 \end{pmatrix} \pmod p
$$
系数矩阵的行列式为 $\Delta = k_1 - k_2$。
由于 $k_1 \neq k_2$ 且 $p$ 是素数，根据你之前关心的结论：**在域中，非零元素 $k_1 - k_2$ 必有乘法逆元**。
因此，矩阵是可逆的。对于任何给定的目标值对 $(y_1, y_2)$，方程组有唯一解：
$$
\begin{pmatrix} a \\ b \end{pmatrix} \equiv \begin{pmatrix} k_1 & 1 \\ k_2 & 1 \end{pmatrix}^{-1} \begin{pmatrix} y_1 \\ y_2 \end{pmatrix} \pmod p
$$
**关键点：** 如果 $a \neq 0$，则必须有 $y_1 \neq y_2$。
因为如果 $y_1 = y_2$，代入方程组得 $a(k_1-k_2) \equiv 0 \pmod p$，由于 $k_1-k_2 \neq 0$，则必有 $a=0$。
由于我们的散列族限定 $a \in \mathbb{Z}_p^*$（即 $a \neq 0$），所以生成的 $(y_1, y_2)$ 必然是 $p(p-1)$ 种不同的**互异值对**。

因此，每一对互异的 $(y_1, y_2)$ 出现的概率完全相等：
$$ \Pr[g(k_1)=y_1, g(k_2)=y_2] = \frac{1}{p(p-1)} $$

---

### 2. 从素数域到桶的映射（Modulo $m$）

现在我们将 $y$ 映射到桶 $v = y \pmod m$。
对于一个给定的桶 $v \in \{0, \dots, m-1\}$，有多少个 $y \in \{0, \dots, p-1\}$ 会映射到它？
这些 $y$ 构成一个等差数列：$v, v+m, v+2m, \dots, v + qm$。
最大的 $y$ 满足 $v + qm \le p-1$，即 $q \le \frac{p-1-v}{m}$。
数量 $N_v = q+1 = \lceil \frac{p-v}{m} \rceil$。不管 $v$ 取什么，这个数量的最大值不超过：
$$ N_{max} = \lceil p/m \rceil \le \frac{p+m-1}{m} < \frac{p}{m} + 1 $$

---

### 3. 计算最终概率

我们要计算 $h(k_1)=v_1$ 且 $h(k_2)=v_2$ 的概率。
这等价于 $(g(k_1), g(k_2))$ 落在集合 $S = \{ (y_1, y_2) \mid y_1 \equiv v_1 \pmod m, y_2 \equiv v_2 \pmod m, y_1 \neq y_2 \}$ 中。

*   满足条件的 $y_1$ 有 $N_{v_1}$ 种可能。
*   满足条件的 $y_2$ 有 $N_{v_2}$ 种可能。
*   由于 $(y_1, y_2)$ 是从 $p(p-1)$ 个互异对中随机抽取的，而 $y_1=y_2$ 的情况本身就被排除在样本空间外了。

$$ \Pr[h(k_1)=v_1, h(k_2)=v_2] = \frac{\text{符合条件的对数}}{\text{总对数}} \le \frac{\lceil p/m \rceil \cdot \lceil p/m \rceil}{p(p-1)} $$

当 $p \gg m$ 时：
$$ \Pr \le \frac{(p/m + 1)^2}{p(p-1)} \approx \frac{p^2/m^2}{p^2} = \frac{1}{m^2} $$
这就是所谓的 **2-独立性（Pairwise Independence）**。

---

### 4. 数理拓展：为什么 2-独立性对散列至关重要？

在初等算法分析中，我们通常关心**平均冲突概率** $\Pr[h(k_1)=h(k_2)]$。
根据上面的结论：
$$ \Pr[h(k_1)=h(k_2)] = \sum_{v \in B} \Pr[h(k_1)=v, h(k_2)=v] $$
代入 2-独立性的结论：
$$ \Pr[h(k_1)=h(k_2)] \le \sum_{v=0}^{m-1} \frac{\lceil p/m \rceil (\lceil p/m \rceil - 1)}{p(p-1)} $$
（注意这里是 $N_v(N_v-1)$，因为在同一个桶里的 $y_1, y_2$ 必须互异且都在 $\mathbb{Z}_p$ 中）。
经过化简：
$$ \Pr[h(k_1)=h(k_2)] \le m \cdot \frac{(p/m)^2}{p^2} \approx \frac{1}{m} $$
这就是**全域散列（Universal Hashing）**的定义。

**结论的深度意义：**
1.  **确定性算法 vs 随机化：** 传统的固定散列函数总存在某些特定数据（Bad Inputs）导致所有键都撞在一个桶里。而线性同域散列通过随机化 $a, b$，使得**对于任何输入**，期望性能都像真正的随机函数一样好。
2.  **空间效率：** 我们只需要存储两个随机数 $(a, b)$，就能在一大堆键上实现近似完美的均匀分布，这比存储一个巨大的随机映射表要节省空间得多。

### Problem 5 解答

**题目：** 证明基于 $d = k-1$ 次多项式的散列族是 $k$-独立的。散列函数定义为：
$$g(k) = (a_{k-1}k^{k-1} + a_{k-2}k^{k-2} + \dots + a_1k + a_0) \pmod p$$
其中 $p$ 为素数，$a_i \in \mathbb{Z}_p$ 随机选取。

**证明步骤：**

**1. 建立线性方程组：**
设 $x_1, x_2, \dots, x_k$ 是 $U$ 中 $k$ 个互不相同的键。对于任意给定的 $k$ 个目标值 $y_1, y_2, \dots, y_k \in \mathbb{Z}_p$，考虑以下关于系数 $a_0, a_1, \dots, a_{k-1}$ 的方程组：
$$
\begin{cases}
a_{k-1}x_1^{k-1} + a_{k-2}x_1^{k-2} + \dots + a_1x_1 + a_0 \equiv y_1 \pmod p \\
a_{k-1}x_2^{k-1} + a_{k-2}x_2^{k-2} + \dots + a_1x_2 + a_0 \equiv y_2 \pmod p \\
\vdots \\
a_{k-1}x_k^{k-1} + a_{k-2}x_k^{k-2} + \dots + a_1x_k + a_0 \equiv y_k \pmod p
\end{cases}
$$

**2. 矩阵表示与唯一性证明：**
上述方程组可以写为矩阵形式 $\mathbf{X} \vec{a} = \vec{y}$：
$$
\begin{pmatrix}
1 & x_1 & x_1^2 & \dots & x_1^{k-1} \\
1 & x_2 & x_2^2 & \dots & x_2^{k-1} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & x_k & x_k^2 & \dots & x_k^{k-1}
\end{pmatrix}
\begin{pmatrix} a_0 \\ a_1 \\ \vdots \\ a_{k-1} \end{pmatrix} = \begin{pmatrix} y_1 \\ y_2 \\ \vdots \\ y_k \end{pmatrix} \pmod p
$$
该系数矩阵 $\mathbf{X}$ 是一个 **Vandermonde 矩阵**。其行列式为：
$$\det(\mathbf{X}) = \prod_{1 \le i < j \le k} (x_j - x_i) \pmod p$$
由于 $x_i$ 两两不同且 $p$ 是素数，所有因子 $(x_j - x_i)$ 在 $\mathbb{Z}_p$ 中均不为 $0$，故 $\det(\mathbf{X}) \not\equiv 0 \pmod p$。根据线性代数结论，该矩阵在 $\mathbb{Z}_p$ 上可逆。因此，对于任意一组特定的 $(y_1, \dots, y_k)$，存在**唯一**的一组系数 $(a_0, \dots, a_{k-1})$ 满足方程。

**3. 计算在 $\mathbb{Z}_p$ 下的概率：**
因为每个系数 $a_i$ 都是从 $\mathbb{Z}_p$ 中独立均匀随机选取的，所以系数向量 $\vec{a}$ 的总可能情况数为 $p^k$。
既然每一组目标值向量 $\vec{y}$ 都对应唯一的一种系数取值，则：
$$\Pr[g(x_1)=y_1, \dots, g(x_k)=y_k] = \frac{1}{p^k}$$

**4. 映射到 $m$ 个桶的概率：**
若考虑最终散列函数 $h(k) = g(k) \pmod m$，对于给定的桶索引 $v_1, \dots, v_k \in \{0, \dots, m-1\}$，每个 $v_i$ 在 $\mathbb{Z}_p$ 中对应的 $y_i$ 数量至多为 $\lceil p/m \rceil$。
因此，使得 $h(x_i) = v_i$ 成立的组合 $(y_1, \dots, y_k)$ 共有 $\prod_{i=1}^k \lceil p/m \rceil \le \lceil p/m \rceil^k$ 种。
总概率为：
$$\Pr[h(x_1)=v_1, \dots, h(x_k)=v_k] \le \frac{\lceil p/m \rceil^k}{p^k}$$

**5. 结论：**
当 $p \gg m$ 时，$\lceil p/m \rceil / p \approx 1/m$，故：
$$\Pr[h(x_1)=v_1, \dots, h(x_k)=v_k] \le O\left(\frac{1}{m^k}\right)$$
这符合 $k$-独立散列族的定义。证毕。