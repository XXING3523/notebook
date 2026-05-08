**二叉堆Binary Heap**

---

最大堆的三个操作：插入，删除，建堆。

**插入基本步骤**

- $ A[n]\gets k,i\gets n,\text{While}:A[i]>A[i/2]\text{ and }i>1$


- $\text{swap }A[i],A[i/2],i\gets i/2$


**删除基本步骤**

- $A[1]\gets A[n]$（将堆底放到堆顶），$n\gets n-1$


- $\text{While }A[i]\text{ has larger child}$


- $j\gets \arg \max \{A[2i],A[2i+1]\},\text{Swap }A[i],A[j],i\gets j$


**建堆基本步骤**

- $\text{For }i=n/2\text{ to }1,\text{Siftdown(A,i)}$


$\text{Siftdown}$：

- $\text{While }A[i]\text{ has larger child}$


- $j\gets \arg \max \{A[2i],A[2i+1]\},\text{Swap }A[i],A[j],i\gets j$


建堆时间复杂度为$\displaystyle \sum_{i=1}^{n/2}O(\text{Siftdown(A,i)})=\sum_{i=1}^{n/2}O(\log i-\log n)=\sum_{i=1}^{n/2}O(\log (n/i))$

当$\displaystyle \frac{n}{2^k}\leqslant i<\frac{n}{2^{k-1}}$时，$\text{runtime}\leqslant O(k)$

故时间复杂度为$O(\displaystyle \sum_{k}^{}\frac{nk}{2^k})=O(n)$

---

**堆排序（Heap Sort）**

输入$A[1,\cdots,n]$，输出$A[1,\cdots,n]$的非递增排序

- 对$A[1,\cdots,n]$建最大堆，输出$A[1]$


- 替换堆顶$A[1]$为$A[i](i=n,\cdots,1)$，做一次$\text{Siftdown(A,1)}$，在$i-1$处终止，如此往复。


**多路归并排序（Multi-way merge-sort）**

输入$A[1,\cdots,n]$，输出$A[1,\cdots,n]$的升序排序

- 将数组划分为$k$个部分$\displaystyle A[1,\cdots,\frac{n}{k}],A[\frac{n}{k}+1,\cdots,\frac{2n}{k}],\cdots$


- 对每一部分递归分割


- 合并$k$个排好序的子序列


关键在合并操作：记$S_1,S_2,\cdots,S_k$为排好序的序列，取出每个序列的第一项$S_{1,1},\cdots,S_{k,1}$建最小堆，取出堆顶，设堆顶为$S_{j,k}$，若该元素不是所属序列最后一项，则插入$S_{j,k+1}$。合并时间复杂度为$O(|S|\log k)$

时间复杂度$T(n)$满足$\displaystyle T(n)=kT(\frac{n}{k})+O(n\log k)=O(n\log n)$

---

求解递推式：$T(n)=\sqrt{n}T(\sqrt{n})+O(n\log n)$，$T(n)=O(n\log n)$

（画出递归树即可）
