set

提供一种高效的方式维护一个既有序又唯一的集合。

内部使用红黑树实现

插入，删除，查找的时间复杂度均为$O(\log n)$

初始化：

```c++
set<int(type)> s(name)
```

或转移：

```c++
vector<int> vec={5,4,3,3,1,2};
set<int> s(vec.begin(),vec.end);
```

此时，s会包含从vec中提取的、去重并排序后的元素

拷贝：

```c++
set<int> original={2,3,1};
set<int> duplication=(original);
```

插入、查找、删除、清空：

```c++
set<int> s;
int x;
s.find(x);//未找到则指向s.end()
s.insert(x);
s.emplace(x);
s.erase(x);
s.clear();
```

!!!info "查找的其他方法"
	（1）使用`s.count(x)`，如果集合内存在，则为1，否则为0
	
	（2）范围查找可使用lower_bound(x),upper_bound(x)函数，分别指向不小于/大于x的第一个元素。

遍历：

```c++
for(int i=s.begin();i!=s.end();i++)
    cout<<*i<<" ";
for(int p:s) cout<<p<<" ";
```

自定义排序：

```c++
struct Compare
{
	bool operator<(const int a,const int b)const
	{
		return a>b;
	}
};
set<int,Compare> s={1,3,2,5,4};
```

set的应用：

<span style="color: #ff7f24;">**P1102 A-B数对**</span>

【题目大意】，提供序列$A=\left \{  a_1,a_2,\cdots,a_n\right \}$与参数$C$，求满足$a_i-a_j=C$的数对$(a_i,a_j)$数量。

将$A$存入set，使用map$(M)$对每个$a_i$的数量进行计数，对每个，查找是否存在于set中，若存在，结果累加$M_{a_i}$

???success "<span style="color: #ff7f24;">**P1102 A-B数对**</span>参考解答一"
	```
	#include<bits/stdc++.h>
    using namespace std;
    const int N=1e6+5;
    set<int> s;
    map<int,int> m;
    int a[N],n,c;
    long long ans;
    int main()
    {
        scanf("%d%d",&n,&c);
        for(int i=1;i<=n;i++)
        {
            scanf("%d",&a[i]);
            if(s.find(a[i])==s.end())
                s.insert(a[i]);
            m[a[i]]++;
        }
        for(int i=1;i<=n;i++)
        {
            int p=a[i]-c;
            if(s.find(p)!=s.end()) ans+=m[p];
        }
        printf("%lld",ans);
        return 0;
    }
    ```



法二：由$a_j=C+a_i$，可对$A$进行升序排序，随着$a_j$的值增加，满足条件的$a_i$的值也会增加，可采用双指针。

维护两个右端点$R_1,R_2$，$R_1$向右移动直到$a_{R_1}<a_j+C$不成立。

$R_2$向右移动直到$a_{R_2}\le a_i+C$不成立，现在判定$a_{R_1}=a_i+C,a_{R_2-1}+C=a_i+C$是否成立，若成立，则$[R_1,R_2-1]$中的数均满足条件，$ans$累加$R_2-R_1$，时间复杂度为$O(n\log n)$

???success "<span style="color: #ff7f24;">**P1102 A-B数对**</span>参考解答二"
	```
	#include<bits/stdc++.h>
    using namespace std;
    const int N=1e6+5;
    int a[N],n,c;
    long long ans;
    int main()
    {
        scanf("%d%d",&n,&c);
        for(int i=1;i<=n;i++) scanf("%d",&a[i]);
        int r1=1,r2=1;
        sort(a+1,a+n+1);
        for(int i=1;i<=n;i++)
        {
            while(a[r1]<a[i]+c&&r1<n) r1++;
            while(a[r2]<=a[i]+c&&r2<=n) r2++;
            if(a[r1]==a[i]+c&&a[r2-1]==a[i]+c)
                ans+=r2-r1;
        }
        printf("%lld",ans);
        return 0;
    }
    ```



deque 双端队列

`deque<int> q`常用函数

```
q.push_back(x);q.push_front(x);
q.pop_back(x);q.pop_front(x);
```

