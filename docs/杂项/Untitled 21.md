#### **6.**
(1). $f'(x) = \frac{(x-1)e^x(x+2) - (x-2)e^x}{(x+2)^2} = \frac{x^2e^x}{(x+2)^2} \ge 0. f(x)$ 在 $(-\infty, -2), (-2, +\infty) \uparrow$.
$f(0) = -1$. 已证 $\frac{x-2}{x+2}e^x + 1 > 0$ 显然成立.

(2). $g'(x) = \frac{(e^x-a)x^2 - 2x(e^x-ax-a)}{x^4} = \frac{xe^x - ax - 2e^x + 2ax + 2a}{x^3} = \frac{(x-2)e^x + a(x+2)}{x^3} \cdot (x+2)$.
令 $q(x) = \frac{x-2}{x+2}e^x + a. q(x) \uparrow, q(0) = a-1 < 0. q(2) = a > 0. \exists x_0 \in (0, 2], q(x_0) = 0$.
故 $a = -\frac{x_0-2}{x_0+2}e^{x_0}, x \in (0, 2]. h(a) = \varphi(x_0) = \frac{e^{x_0} \cdot (x_0+1)(x_0-2)}{x_0^2} \cdot \frac{e^{x_0}}{x_0+2} \dots = \frac{x_0}{x_0+2}e^{x_0}$.
在 $(0, 2] \uparrow$. 故 $h(a) \in (\frac{1}{2}, \frac{e^2}{4}]$.

---

#### **7.**
(1). $f'(x) = 3x^2 + a, f(x_0) = x_0^3 + ax_0 + \frac{1}{4}$. 切线 $y = f'(x_0)(x-x_0) + f(x_0)$. 由定义知与原点判定 $\begin{cases} f'(1) = 0 \\ f(x_0) - x_0 f'(x_0) = 0 \end{cases} \implies \begin{cases} x_0 = \frac{1}{2} \\ a = -\frac{3}{4} \end{cases}$.

(2). 由定义知 $h(x)$ 在 $(1, +\infty)$ 恒小于 $0$. 无零点.
$f'(x) = 0$. ① 当 $a \in [0, +\infty)$ 时, $f(x) \uparrow$. 且 $f(0) = \frac{1}{4} > 0, f(1) > 0$. 故 $h(x)$ 仅一个零点.
② $a \in (-\infty, 0)$ 时. $f'(-\sqrt{-\frac{a}{3}}) = f'(\sqrt{-\frac{a}{3}}) = 0. f(x)$ 在 $(0, \sqrt{-\frac{a}{3}}) \downarrow, (\sqrt{-\frac{a}{3}}, +\infty) \uparrow$.
$f(\sqrt{-\frac{a}{3}}) = \frac{1}{3}a\sqrt{-\frac{a}{3}} + \frac{2}{3}a\sqrt{-\frac{a}{3}} + \frac{1}{4} = \frac{2}{3}a\sqrt{-\frac{a}{3}} + \frac{1}{4} = 0 \implies a = -\frac{3}{4}$.
$f(\sqrt{-\frac{a}{3}}) > 0 \implies a > -\frac{3}{4}. f(\sqrt{-\frac{a}{3}}) < 0 \implies a < -\frac{3}{4}. f(1) = a + \frac{5}{4}$.
(I). 当 $a < -\frac{5}{4}$ 时, 仅一个零点. (II). $a = -\frac{5}{4}$ 时, 两个零点. (III). $-\frac{5}{4} < a < -\frac{3}{4}$ 时, 三个零点.
(IV). $a = -\frac{3}{4}$, 两个零点. $a \in (-\frac{3}{4}, 0)$, 一个零点.
综上, $a \in (-\infty, -\frac{5}{4}) \cup (-\frac{3}{4}, +\infty)$ 一个零点. $a \in (-\frac{5}{4}, -\frac{3}{4})$ 三个零点. $a \in \{-\frac{5}{4}, -\frac{3}{4}\}$ 两个.

