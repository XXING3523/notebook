收到，我将严格遵循“一个字都不漏”的原则，对图片中 8 道大题的手写解题过程进行最完整的 LaTeX 转录。包括所有的推导步骤、分类讨论、汉字说明以及图中对取点符号的标注。

---

### Problem Set 1 Solution

#### **1.**
(1). $f'(x) = xe^x - 2ax = x(e^x - 2a)$.
① $a \in (-\infty, 0]$ 时，$f(x)$ 在 $(-\infty, 0] \downarrow, [0, +\infty) \uparrow$.
② $a \in (0, \frac{1}{2})$ 时，$f(x)$ 在 $(-\infty, \ln 2a] \uparrow, (\ln 2a, 0] \downarrow, (0, +\infty) \uparrow$.
③ $a = \frac{1}{2}$ 时，$f(x)$ 在 $\mathbb{R}$ 上 $\uparrow$.
④ $a \in (\frac{1}{2}, +\infty)$ 时，$f(x)$ 在 $(-\infty, 0] \uparrow, (0, \ln 2a) \downarrow, (\ln 2a, +\infty) \uparrow$.

(2). 选 1 “$\frac{1}{2} < a \le \frac{e^2}{2}, b > 2a$”. $f(0) = b - 1 > 0$. $f(\ln 2a) = 2a(\ln 2a - 1) - a(\ln 2a)^2 + b$
$> 2a \ln 2a - a(\ln 2a)^2 = a \ln 2a (2 - \ln 2a) \ge 0$. 故 $f(x)$ 在 $[0, +\infty)$ 恒正.
现取点 $x_0$ 使 $f(x_0) < 0$ ($x_0 < 0$). $x \in (-\infty, 0)$ 时，
$(x - 1)e^x - ax^2 + b < -ax^2 + b < 0$. 取 $x_0$ 如 $x < -\sqrt{\frac{b}{a}}$ 即可.
故 $\exists x_1 \in (x_0, 0), f(x_1) = 0$. $x_1$ 为唯一零点.

选 2 “$0 < a < \frac{1}{2}, b \le 2a$”. $f(0) = b - 1 < 0$. $f(\ln 2a) \le a \ln 2a (2 - \ln 2a) < 0$.
现取点 $x_0$ 使 $f(x_0) > 0$. ($x > 0$). $(x - 1)e^x - ax^2 + b > \frac{1}{2}x^3(x - 1) - ax^2 + b$
$> x^2(\frac{1}{2}x - \frac{1}{2} - a)$. 取 $x_0 > 2a + 1$ 即可. $\exists x_1 \in (0, x_0), f(x_1) = 0$.
$x_1$ 为唯一零点.

---

#### **2.**
(1) $f'(x) = 3x^2 + b, f'(\frac{1}{2}) = \frac{3}{4} + b$. 切线 $y = (\frac{3}{4} + b)(x - \frac{1}{2}) + \frac{1}{8} + \frac{1}{2}b + c \implies b = -\frac{3}{4}, c = \frac{1}{4}$.

(2). $f(x) = x^3 - \frac{3}{4}x + c, f'(x) = 3x^2 - \frac{3}{4}$. $f(x)$ 在 $(-\infty, -\frac{1}{2}) \uparrow, (-\frac{1}{2}, \frac{1}{2}) \downarrow, (\frac{1}{2}, +\infty) \uparrow$.
$f(-1) = c - \frac{1}{4}, f(1) = c + \frac{1}{4}, f(-\frac{1}{2}) = c + \frac{1}{4}, f(\frac{1}{2}) = c - \frac{1}{4}$.
① 当 $c \in (-\infty, -\frac{1}{4})$ 时，在 $[0, 1]$ 上无零点，满足题意.
② 当 $c \in [-\frac{1}{4}, \frac{1}{4}]$ 时，$f(-\frac{1}{2}) \cdot f(1) > 0, f(-1) \cdot f(\frac{1}{2}) < 0$.
故 $\exists x_1 \in (-1, -\frac{1}{2}), x_2 \in (-\frac{1}{2}, \frac{1}{2}), x_3 \in (\frac{1}{2}, 1)$ 使 $f(x_i) = 0$. ($i=1,2,3$).
满足题意.
③ 当 $c \in (\frac{1}{4}, +\infty)$ 时，在 $[0, 1]$ 上无零点. 综上得证.

---

#### **3.**
(1). $f'(x) = \cos x - \frac{1}{x+1}, f''(x) = -\sin x + \frac{1}{(x+1)^2}$. $f'''(x) = -\cos x - \frac{2}{(x+1)^3}$.
故 $f''(x)$ 在 $(0, \frac{1}{2}\pi) \downarrow, f''(0) = 1, f''(\frac{1}{2}\pi) = -1 + \frac{1}{(1+\frac{1}{2}\pi)^2} < 0. \text{故} \exists x_0 \in (0, \frac{1}{2}\pi) \text{使} f''(x_0) = 0$.
故 $f'(x)$ 在 $(0, x_0) \uparrow, (x_0, \frac{1}{2}\pi) \downarrow, f'(0) = 0, f'(\frac{1}{2}\pi) = -\frac{1}{1+\frac{1}{2}\pi} < 0$.
故 $\exists x_1 \in (0, \frac{1}{2}\pi) \text{使} f'(x_1) = 0$ 且为唯一极大值点.

(2) 可知 $f'(x)$ 在 $x \in (\frac{1}{2}\pi, \frac{3}{2}\pi)$ 为负. 故 $f(x)$ 在 $(-\pi, 0] \downarrow, (0, x_1) \uparrow, (x_1, \frac{3}{2}\pi] \downarrow, f(\frac{3}{2}\pi) = -1 - \ln(1 + \frac{3}{2}\pi) < 0$.
$f(0) = 0, f(x_1) > 0$. 故 $\exists x_2 \in (x_1, \frac{3}{2}\pi) \text{使} f(x_2) = 0$. 且当 $x \in (\frac{3}{2}\pi, +\infty)$ 时，$f(x) < 0$.
故仅 2 零点，$0$ 与 $x_2$.

---

#### **4.**
(1) $f'(x) = 2ae^{2x} + (a-2)e^x + 1 = (ae^x - 1)(2e^x + 1)$.
① 当 $a \in (-\infty, 0]$ 时，$f'(x) < 0, f(x)$ 在 $\mathbb{R}$ 上 $\downarrow$.
② 当 $a \in (0, +\infty)$ 时，$f(x)$ 在 $(-\infty, -\ln a) \downarrow, (-\ln a, +\infty) \uparrow$.

(2). 极值点 $a \in (0, +\infty)$ 时，$f(-\ln a) = \frac{a}{a^2} + (a-2) \cdot \frac{1}{a} + \ln a = 1 - \frac{1}{a} + \ln a$.
令 $g(a) = 1 - \frac{1}{a} + \ln a, g'(a) > 0, g(1) = 0$.
故当 $a \in (0, 1)$ 时，$f(-\ln a) < 0$。是满足题意的必要条件. 下证充分.
当 $x < 0$ 时，$f(x) > (a-2) - x > 0$. 取 $x_0 < a-2$ 即可. (且 $a-2 < -\ln a$).
当 $x > 0$ 时，$f(x) > e^x(ae^x + a - 3) > 0$. 取 $x_1 > \ln \frac{3-a}{a}$ 即可. (或取 $x_1 > \ln \frac{3-a}{a} - \ln a$ 保证 $x_1 > -\ln a$).
故 $\exists x_2 \in (x_0, -\ln a), x_3 \in (-\ln a, x_1)$ 使 $f(x_2) = f(x_3) = 0$ 成立. 故 $a \in (0, 1)$.

---

#### **5.**
(1). $f'(x) = 2ax - a - 1 - \ln x, f'(1) = a - 1. f(1) = 0$. 若 $f'(1) > 0$ 时, $\exists \delta > 0$ 使 $x \in (1-\delta, 1+\delta)$ 时 $f(x) \uparrow$. 故 $f(1-\delta) < 0$. 不满足. 同理 $f'(1) < 0$ 时, 不成立. 当 $a=1$ 时, $f(x) = (x-1-\ln x) \cdot x \ge 0$. 成立. $a = 1$.

(2). $f'(x) = 2x - 2 - \ln x. f''(x) = 2 - \frac{1}{x}. f(x)$ 在 $(0, \frac{1}{2}) \downarrow, (\frac{1}{2}, +\infty) \uparrow. f'(\frac{1}{2}) = \ln 2 - 1 < 0. \lim_{x \to 0^+} f'(x) > 0$.
$\exists x_0 \in (0, \frac{1}{2})$ 使 $2x_0 - 2 - \ln x_0 = 0$. 且 $x_0$ 为唯一极大值点. $f(x_0) = x_0^2 - x_0 - x_0 \ln x_0 = x_0^2 - x_0 - x_0(2x_0-2) = -x_0^2 + x_0 < \frac{1}{4}$.
可知 $f'(\frac{1}{e}) < 0$. 故 $x_0 < \frac{1}{e}, f(x_0) > f(\frac{1}{e}) = \frac{1}{e^2} - \frac{1}{e}$. 得证. $0 < \frac{1}{e} < \frac{1}{2}, x_0 \neq \frac{1}{e}$.

---

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

---

#### **8.**
