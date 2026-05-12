\iffalse

\subsection{拓展阅读：导数的严格引入}

如果想要严格化导数的定义，我们一般按照如下路径学习：


\begin{center}
    数列极限 $\to$ 函数极限 $\to$ 导数
\end{center}

\subsubsection{数列的极限}

我们先从离散的数列极限讲起。

对于数列

\begin{center}
    $\displaystyle a_1=1,a_2=\frac{1}{2},a_3=\frac{1}{4},\cdots,a_n=\frac{1}{2^{n-1}},\cdots$
\end{center}

我们感性地认为，当$n$趋向无穷大时，$a_n$的值应该会无限趋近于0，这个0就是所谓数列$\{a_n\}$的极限，如果不严格地处理极限理论，这样直观给出数列极限定义是可行的。但是，从严谨的极限理论来说，我们不允许对数学概念的刻画中出现“无限趋近”这种意义不明的词语，这仅仅只对数列变化性态作了一种形象的描述，并非定量的定义，因此我们要在此基础之上更进一步，尝试对数列的极限给出严格的定义。

如果我们说：“数列$\{a_n\}$无限趋近于常数$A$。”，也就相当于说：“数列$\{|a_n-A|\}$无限趋近于0”，即$a_n$与$A$的距离无限趋近于0。

人们便想到了通过控制距离来描述“数列的极限”，给定一个误差$\varepsilon>0$，如果数列$\{a_n\}$无限趋近于常数$A$，那么在某项之后，即存在$N$，当$n>N$时，$|a_n-A|$应当都小于$\varepsilon$。从图形上直观的感受看，$\{a_n\}$最终应当无限靠近常数$A$，因此任意给定一个范围$[A-\varepsilon ,A+\varepsilon]$，$\{a_n\}$在经过若干项后都应该落在其中。

\paragraph{定义（数列的极限）}对于数列$\{x_n\}$，$A$是一个实常数，如果对任意给定的$\varepsilon>0$，都可以找到正整数$N$，使得当$n>N$时，有

\begin{center}
    $|x_n-A|<\varepsilon$
\end{center}

成立，则称\textbf{$A$是数列$\{x_n\}$的极限}，记为$\lim\limits_{n\to \infty}x_n=A$。此时也称\textbf{数列$\{x_n\}$收敛于$A$}，如果不存在实数$A$，使得$\{x_n\}$收敛于$A$，那么称数列$\{x_n\}$\textbf{发散}。

数列极限的符号表述法为

\begin{center}
    $\lim\limits_{n\to\infty}x_n=a\iff \forall \varepsilon>0,\exists N,\forall n>N:|x_n-A|<\varepsilon$
\end{center}



\subsubsection{函数的极限}

\subsubsection{导数}

\paragraph{定义（邻域，Neighborhood，去心邻域）}设 $x_0$ 是实轴上的一个点，$\delta$ 是一个正数。集合
$$U(x_0, \delta) = \{x \mid |x - x_0| < \delta\}$$
称为点 $x_0$ 的 $\delta$ 邻域。如果在这个集合中去掉点 $x_0$ 本身，这成为点$x_0$的$\delta$去心邻域，记作 $\mathring{U}(x_0, \delta)$。

\paragraph{定义（函数的极限）}设函数 $f(x)$ 在点 $x_0$ 的某个去心邻域 $\mathring{U}(x_0, \delta)$ 内有定义。若对于任意给定的正数 $\epsilon$（无论它多么小），总存在正数 $\delta$，使得对于满足不等式 $0 < |x - x_0| < \delta$ 的一切 $x$，对应的函数值 $f(x)$ 都满足：
$$|f(x) - A| < \epsilon$$
则称常数 $A$ 为函数 $f(x)$ 当 $x \to x_0$ 时的极限。\footnote{这是由柯西（Cauchy）和魏尔斯特拉斯（Weierstrass）形式化的定义，旨在消灭“无限趋近”这种模糊的文学描述，将其转化为纯粹的逻辑和不等式。}

\paragraph{定义（连续）}设函数 $f(x)$ 在点 $x_0$ 的某个去心邻域$\mathring{U}(x_0, \delta)$内有定义。若对于任意给定的正数 $\epsilon$，总存在正数 $\delta > 0$，使得对于满足 $|x - x_0| < \delta$ 的一切 $x$，都有：
$$|f(x) - f(x_0)| < \epsilon$$
那么称函数 $f(x)$ 在点 $x_0$ 处连续。

函数的极限唯一：若$f(x)$在邻域$U(x_0,\delta)$有定义，$\lim\limits_{x\to x_0}f(x)=A,\lim\limits_{x\to x_0}f(x)=B$，则$A=B$。

你会采取什么证明方法？（可以将你所学过的方法一个个排除。）

\begin{proof}

    假设$A\neq B$，据极限定义：
    
    $\lim\limits_{x\to x_0}f(x)=A\Longrightarrow\forall \varepsilon,\exists \delta_1>0$，当$|x-x_0|<\delta_1$时，$|f(x)-A|<\varepsilon$
    
    $\lim\limits_{x\to x_0}f(x)=B\Longrightarrow\forall \varepsilon,\exists \delta_1>0$，当$|x-x_0|<\delta_1$时，$|f(x)-B|<\varepsilon$
    
    取$\delta =\min\{\delta_1,\delta_2\}$，当$|x-x_0|<\delta$时，有$|f(x)-A|<\varepsilon,|f(x)-B|<\varepsilon$.
    
    取$\displaystyle \varepsilon=\frac{|A-B|}{2}$时导出矛盾.\marginnote{为什么可以得到这一步？}
    
    故$A=B$

\end{proof}

夹逼定理：若在$\mathring{U}(x_0, \delta_0)$内，$g(x)\leqslant f(x)\leqslant h(x)$，且$\lim\limits_{x\to x_0}h(x)=\lim\limits_{x\to x_0}g(x)=A$，则$\lim\limits_{x\to x_0}f(x)=A$。

\begin{proof}

根据极限定义，有：

$\lim\limits_{x\to x_0}h(x)=A\Longrightarrow\forall \varepsilon,\exists \delta_1>0$，当$|x-x_0|<\delta_1$时，$|h(x)-A|<\varepsilon\Longrightarrow A-\varepsilon < h(x)<A+\varepsilon$

    $\lim\limits_{x\to x_0}g(x)=A\Longrightarrow\forall \varepsilon,\exists \delta_2>0$，当$|x-x_0|<\delta_2$时，$|g(x)-A|<\varepsilon\Longrightarrow A-\varepsilon <g(x)<A+\varepsilon$
    
    取$\delta_3=\min\{\delta,\delta_1,\delta_2\}$，又由于当$|x-x_0|<\delta_3$时，有$A-\varepsilon <g(x)\leqslant f(x)\leqslant h(x)<A+\varepsilon$，则$|f(x)-A|<\varepsilon$，可得$\lim\limits_{x\to x_0}f(x)=A$

\end{proof}

\paragraph{连续函数的局部保号性}如果函数 $f(x)$ 在点 $x_0$ 处连续，且 $f(x_0) > 0$（或 $f(x_0) < 0$），那么存在点 $x_0$ 的一个邻域 $U(x_0, \delta)$，使得对于该邻域内的任何点 $x$，都有：
$f(x) > 0 \quad (\text{或 } f(x) < 0)$

\begin{proof}
    据连续的定义：对于任意给定的正数 $\epsilon$，总存在正数 $\delta > 0$，使得对于满足 $|x - x_0| < \delta$ 的一切 $x$，都有：$|f(x) - f(x_0)| < \epsilon$，取 $\epsilon = f(x_0)$，有

    $$|f(x)-f(x_0)|<f(x_0)\Longrightarrow f(x)>0$$

\end{proof}

（2）考虑理解下述命题的证明。

\paragraph{命题}设 $f(x) = g(x)h(x)$ 且 $f(x_0) = \varphi(x_0) = 0$。
若 $g(x_0) > 0$，则 $f(x)$ 在 $x_0$ 取极值的类型（极大/极小）与 $\varphi(x)$ 完全一致。

\begin{proof}
    先证明$f(x)$在$x_0$取极大值$\Longrightarrow\varphi(x)$在$x_0$取极大值：

    考虑$x=0$的一个邻域$U(0,\delta)$，在这个邻域中，有$g(x)>0$，故：
$$f(x) \leqslant f(0) \iff g(x) \cdot \varphi(x) \leqslant 0$$
因为 $g(x)>0$，不等式两边同除以 $g(x)$ ，得$\varphi(x) \leqslant 0$，又$\varphi(0) = 0$，有

$$\varphi(x) \leqslant \varphi(0)$$

由此可说明$x_0$是$\varphi(x)$的极大值。

同理可证明：$f(x)$在$x_0$取极小值$\Longrightarrow\varphi(x)$在$x_0$取极小值：
\end{proof}

\fi