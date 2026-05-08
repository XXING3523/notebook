1.  **先证 $y = f(x)$ 的值域是闭区间 $[\alpha, \beta]$**：
    设 $y$ 是 $[\alpha, \beta]$ 中任意一点，如果 $y = \alpha$ 或 $\beta$，那么相应的 $x = a$ 或 $b$，即有 $f(a) = \alpha$ 或 $f(b) = \beta$。换言之，$\alpha, \beta$ 在 $f(x)$ 的值域中。又如果 $\alpha = f(a) < y_0 < f(b) = \beta$，由连续函数中间值定理，在 $[a, b]$ 之间必存在一点 $x_0$ 满足 $f(x_0) = y_0$，即 $[\alpha, \beta]$ 内任一点都属于值域 $f([a, b])$。由此证明了 $f(x)$ 的值域是 $[\alpha, \beta]$。

2.  **再证 $f$ 是单射的**：
    因为一个严格递增函数 $f$ 满足条件：
    \[ x_1 < x_2 \quad \Rightarrow \quad f(x_1) < f(x_2) \]
    即自变量的值与函数值是一一对应的，所以 $f$ 是单射的。由此可知函数 $f$ 是可逆的，因此存在一个反函数 $f^{-1}: [\alpha, \beta] \mapsto [a, b]$，其中 $x = f^{-1}(y)$。

3.  **证明 $f^{-1}$ 的递增性**：
    假设 $y_1, y_2$ 是 $[\alpha, \beta]$ 内的两个数，并且 $y_1 < y_2$，又设 $x_1 = f^{-1}(y_1), x_2 = f^{-1}(y_2)$。对于这两个数 $x_1$ 和 $x_2$ 只有三种可能：$x_1 < x_2, x_1 = x_2, x_1 > x_2$。
    如果 $x_1 \ge x_2$，由于 $f$ 的递增性质，知道
    \[ y_1 = f(x_1) \ge f(x_2) = y_2 \]
    这与 $y_1 < y_2$ 的假设矛盾，因此 $x_1 < x_2$，即
    \[ y_1 < y_2 \quad \Rightarrow \quad f^{-1}(y_1) = x_1 < x_2 = f^{-1}(y_2) \]
    这就证明了 $x = f^{-1}(y)$ 是 $[\alpha, \beta]$ 上的递增函数



根据您提供的一系列图片内容，我为您整理成了符合要求的 LaTeX 格式。

---

【例 1.4】（2015 山东理 10）设函数 $\displaystyle f(x) = \begin{cases} 3x - 1, & x < 1 \\ 2^x, & x \geqslant 1 \end{cases}$，则满足 $\displaystyle f(f(a)) = 2^{f(a)}$ 的 $\displaystyle a$ 的取值范围是（ ）。
\choice{$\displaystyle \left[ \frac{2}{3}, 1 \right]$}{$\displaystyle [0, 1]$}{$\displaystyle \left[ \frac{2}{3}, +\infty \right)$}{$\displaystyle [1, +\infty )$}

【例 1.23】已知函数 $\displaystyle f(x) = \frac{x^3 - x}{x^4 + 2x^2 + 1}$，则 $\displaystyle y = f(x)$ 的值域为 \_\_\_\_\_\_。

【例 1.57】（2012 新课标文 16）设函数 $\displaystyle f(x) = \frac{(x+1)^2 + \sin x}{x^2 + 1}$ 的最大值为 $\displaystyle M$，最小值为 $\displaystyle m$，则 $\displaystyle M + m = $ \_\_\_\_\_\_。

【结论总结 1.6】常见周期函数模型（一）：
（1）对任意的 $\displaystyle x \in \mathbb{R}$，若 $\displaystyle f(x+a) + f(x) = c$（$\displaystyle c$ 为常数），则 $\displaystyle T = 2|a|$；
（2）对任意的 $\displaystyle x \in \mathbb{R}$，若 $\displaystyle f(x+a) \cdot f(x) = c$（$\displaystyle c$ 是不为零的常数），则 $\displaystyle T = 2|a|$。

【例 1.75】$\displaystyle f(x)$ 定义域为 $\displaystyle \mathbb{R}$，且对任意 $\displaystyle x \in \mathbb{R}$ 都有 $\displaystyle f(x+1) = \frac{1 - f(x)}{1 + f(x)}$，若 $\displaystyle f(2) = 1$，则 $\displaystyle f(2018) = $ \_\_\_\_\_\_。

【结论总结 1.7】若 $\displaystyle f(x)$ 满足 $\displaystyle f(x) = f(x+a) - f(x+2a)$，则 $\displaystyle f(x)$ 的周期为 $\displaystyle T = 6|a|$。

【例 2.21】（2014 四川文 21）已知函数 $\displaystyle f(x) = e^x - ax^2 - bx - 1$，若 $\displaystyle g(x)$ 是函数 $\displaystyle f(x)$ 的导函数，求函数 $\displaystyle g(x)$ 在区间 $\displaystyle [0, 1]$ 上的最小值。

【2024上海12】无穷等比数列 $ \displaystyle \{a_n\} $$ 满足首项 $ $ \displaystyle a_1 > 0, q > 1 $$，记 $ $ \displaystyle I_n = \{x-y \mid x,y \in [a_1, a_2] \cup [a_n, a_{n+1}]\} $，若对任意正整数 $ \displaystyle n $$ 集合 $$ \displaystyle I_n $$ 是闭区间，则 $$ \displaystyle q $ 的取值范围是

【2019上海12】已知 $ \displaystyle f(x) = \left| \frac{2}{x-1} - a \right| $$ ($$ \displaystyle x > 1, a > 0 $$)，$$\displaystyle f(x)$$ 与 $$ \displaystyle x $$ 轴交点为 $$ \displaystyle A $$，若对于 $$\displaystyle f(x)$$ 图像上任意一点 $$ \displaystyle P $$，在其图像上总存在另一点 $$ \displaystyle Q $$ ($$ \displaystyle P, Q $$ 异于 $$ \displaystyle A $$)，满足 $$ \displaystyle AP \perp AQ $$，且 $$ \displaystyle |AP| = |AQ| $$，则 $$ \displaystyle a = $

【2015上海理12】赌博有陷阱．某种赌博每局的规则是：赌客先在标记有 $$ \displaystyle 1, 2, 3, 4, 5 $$ 的卡片中随机摸取一张，将卡片上的数字作为其赌金（单位：元）；随后放回该卡片，再随机摸取两张，将这两张卡片上数字之差的绝对值的 $$ \displaystyle 1.4 $$ 倍作为其奖金（单位：元）．若随机变量 $$ \displaystyle \xi_1 $$ 和 $$ \displaystyle \xi_2 $$ 分别表示赌客在一局赌博中的赌金和奖金，则 $$ \displaystyle E\xi_1 - E\xi_2 = $$（元）．

【2015上海理13】已知函数 $$ \displaystyle f(x) = \sin x $$．若存在 $$ \displaystyle x_1, x_2, \dots, x_m $$ 满足 $$ \displaystyle 0 \leqslant x_1 < x_2 < \dots < x_m \leqslant 6\pi $$，且 $$ \displaystyle |f(x_1) - f(x_2)| + |f(x_2) - f(x_3)| + \dots + |f(x_{m-1}) - f(x_m)| = 12 $$ ($$ \displaystyle m \geqslant 2, m \in \mathbb{N}^* $$)，则 $$\displaystyle m$$ 的最小值为

【2015上海理14】在锐角三角形 $$ \displaystyle ABC $$ 中，$$ \displaystyle \tan A = \frac{1}{2} $$，$$ \displaystyle D $$ 为边 $$ \displaystyle BC $$ 上的点，$$ \displaystyle \triangle ABD $$ 与 $$ \displaystyle \triangle ACD $$ 的面积分别为 $$ \displaystyle 2 $$ 和 $$ \displaystyle 4 $$．过 $$ \displaystyle D $$ 作 $$ \displaystyle DE \perp AB $$ 于 $$ \displaystyle E $$，$$ \displaystyle DF \perp AC $$ 于 $$ \displaystyle F $$，则 $ \displaystyle \overrightarrow{DE} \cdot \overrightarrow{DF} = $

【2015上海理23】对于定义域为 $$\displaystyle \mathbb{R}$$ 的函数 $$\displaystyle g(x)$$，若存在正常数 $$ \displaystyle T $$，使得 $$ \displaystyle \cos g(x) $$ 是以 $$ \displaystyle T $$ 为周期的函数，则称 $$\displaystyle g(x)$$ 为余弦周期函数，且称 $$ \displaystyle T $$ 为其余弦周期．已知 $$\displaystyle f(x)$$ 是以 $$ \displaystyle T $$ 为余弦周期的余弦周期函数，其值域为 $$\displaystyle \mathbb{R}$$．设 $$\displaystyle f(x)$$ 单调递增，$$ \displaystyle f(0) = 0, f(T) = 4\pi $$．
（1）验证 $$ \displaystyle g(x) = x + \sin \frac{x}{3} $$ 是以 $$ \displaystyle 6\pi $$ 为周期的余弦周期函数；
（2）设 $$ \displaystyle a < b $$，证明对任意 $$ \displaystyle c \in [f(a), f(b)] $$，存在 $$ \displaystyle x_0 \in [a, b] $$，使得 $$ \displaystyle f(x_0) = c $$；
（3）证明：“$$ \displaystyle u_0 $$ 为方程 $$ \displaystyle \cos f(x) = 1 $$ 在 $$ \displaystyle [0, T] $$ 上得解，”的充要条件是“$$ \displaystyle u_0 + T $$ 为方程 $$ \displaystyle \cos f(x) = 1 $$ 在区间 $$ \displaystyle [T, 2T] $$ 上的解”，并证明对于任意 $$ \displaystyle x \in [0, T] $$，都有 $$ \displaystyle f(x+T) = f(x) + f(T) $$．

【2008上海理12】方程 $$ \displaystyle x^2 + \sqrt{2}x - 1 = 0 $$ 的解可视为函数 $$ \displaystyle y = x + \sqrt{2} $$ 的图像与函数 $$ \displaystyle y = \frac{1}{x} $$ 的图像交点的横坐标．若方程 $$ \displaystyle x^4 + ax - 4 = 0 $$ 的各个实根 $$ \displaystyle x_1, x_2, \dots, x_k $$ ($$ \displaystyle k \leqslant 4 $$) 所对应的点 $$ \displaystyle \left(x_i, \frac{4}{x_i}\right) $$ ($$ \displaystyle i = 1, 2, \dots, k $$) 均在直线 $$ \displaystyle y = x $$ 的同侧，则实数 $$\displaystyle a$$ 的取值范围是 

（平面向量）【2025上海12】已知 $$ \displaystyle f(x) = \begin{cases} 1, & x > 0 \\ 0, & x = 0 \\ -1, & x < 0 \end{cases} $$，$$ \displaystyle \vec{a}, \vec{b}, \vec{c} $$ 是平面内三个不同的单位向量．若 $$ \displaystyle f(\vec{a} \cdot \vec{b}) + f(\vec{b} \cdot \vec{c}) + f(\vec{c} \cdot \vec{a}) = 0 $$，则 $$ \displaystyle |\vec{a} + \vec{b} + \vec{c}| $$ 的取值范围是

【2025上海21】已知函数 $$\displaystyle y = f(x)$$ 的定义域为 $$\displaystyle \mathbb{R}$$．对于正实数 $$\displaystyle a$$，定义集合 $$ \displaystyle M_a = \{x \mid f(x+a) = f(x)\} $$．
（1）若 $$ \displaystyle f(x) = \sin x $$，判断 $$ \displaystyle \frac{\pi}{3} $$ 是否是 $$ \displaystyle M_\pi $$ 中的元素，请说明理由；
（2）若 $$ \displaystyle f(x) = \begin{cases} x+2, & x < 0 \\ \sqrt{x}, & x \geqslant 0 \end{cases} $$，$$ \displaystyle M_a \neq \varnothing $$，求 $$\displaystyle a$$ 的取值范围；
（3）若 $$\displaystyle y = f(x)$$ 是偶函数，当 $$ \displaystyle x \in (0, 1] $$ 时，$$ \displaystyle f(x) = 1 - x $$，且对任意 $$ \displaystyle a \in (0, 2) $$，均有 $$ \displaystyle M_a \subseteq M_2 $$．写出 $$ \displaystyle y = f(x), x \in (1, 2) $$ 解析式，并证明：对任意实数 $$\displaystyle c$$，函数 $$ \displaystyle y = f(x) - c $$ 在 $$ \displaystyle [-3, 3] $$ 上至多有 $$ \displaystyle 9 $$ 个零点．


> **(拓展问) 设 $f(x) = 4x(1-x)$，若已知系统中存在周期为 3 的点，是否存在一个初始值 $a_1$，使得数列 $\{a_n\}$ 既不是周期数列，也不收敛于任何点？**

**答案是肯定的。** 这就是李-约克定理揭示的真相：在如此简单的规则下，隐藏着无穷无尽的、不重复的轨迹。
