您好，这是李教授在课堂上布置的作业，问题如下：

问题：给定$A\in R^{m\times n}$，$R(A)$是$A$的像空间，$N(A)$是$A$的零空间，证明：$R(A)$是$R^m$的子空间，$N(A)$是$R^n$的子空间。

证明：

（1）先证$R(A)$是子空间。

易知零向量$0\in R(A)$

任取$\alpha,\beta\in R(A)$由像空间定义，存在向量$\gamma_1,\gamma_2\in R^n$使得$A\gamma_1=\alpha,A\gamma_2=\beta$。

而$\gamma_1+\gamma_2\in R^n,A(\gamma_1+\gamma_2)=A\gamma_1+A\gamma_2=\alpha+\beta\in R^m$

故$\alpha+\beta\in R(A)$

由此证明了$R(A)$对加法封闭，下证明$R(A)$对数量乘法封闭。

任取$\alpha\in R(A),k\in \text{数域}K$，则存在向量$\gamma\in R^n$使得$A\gamma=\alpha$。

而$k\gamma\in R^n,A(k\gamma)=kA\gamma=k\alpha\in R^m$

故$k\alpha\in R(A)$

由此证明了$R(A)$对数量乘法封闭。

故$R(A)$是$R^m$的子空间。

（2）再证$N(A)$是子空间。

易知零向量$0\in N(A)$

任取$\gamma_1,\gamma_2\in N(A)$由零空间定义，$A\gamma_1=0,A\gamma_2=0$。

而$\gamma_1+\gamma_2\in R^n,A(\gamma_1+\gamma_2)=A\gamma_1+A\gamma_2=0$

故$\gamma_1+\gamma_2\in N(A)$

由此证明了$N(A)$对加法封闭，下证明$N(A)$对数量乘法封闭。

任取$\alpha\in N(A),k\in \text{数域}K$，则存在向量$\gamma\in R^n$使得$A\gamma=0$。

而$k\gamma\in R^n,A(k\gamma)=kA\gamma=0$

故$k\gamma\in N(A)$

由此证明了$N(A)$对数量乘法封闭。

故$N(A)$是$R^n$的子空间。
