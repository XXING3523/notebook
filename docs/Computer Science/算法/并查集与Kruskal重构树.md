并查集

<span style="color: #76EE00;">**【二分】【种类并查集】LuoguP1525 关押罪犯**</span>

**【题目大意】**将$N$号人划分为2个集团，存在对敌对关系，每对关系包含三个信息，表示若划分到同一集团，将产生分数，对全体合理的划分方案，求产生分数最大值的最小值（若上述关系均未触发，结果为0）

答案的求解满足二分的求解要求，故将其转化为判断合法性问题。

将关系按降序排序，并只关注大于等于mid的部分，要求此部分不触发任何关系。对于二元种类并查集，若要使$(a,b),(b,c)$不触发关系，则$a,c$必划分到同一集团。即若要使$(a,b)$不触发关系，则必将$a$与$b$的所有敌人划分到同一集团。

此处并查集将扩充1倍，后$N$个元素表示对应敌人，对某关系$(a_j,b_j,c_j)$，有$Union(a_j,b_j+N),Union(b_j,a_j+N)$

<span style="color: #76EE00;">**【种类并查集】LuoguP2024**</span>

<span style="color: #76EE00;">**【二分】【并查集】LuoguP4047 部落划分**</span>



<span style="color: #76EE00;">**【离散化】【种类并查集】LuoguP1955**</span>

<span style="color: ORANGE;">**LuoguP1396 营救**</span>

Kruskal重构树

在利用Kruskal算法求解某个图最小生成树的过程中，将待加入的边记为一个新结点，其点权为此边的边权，且此边连接的两个儿子为结点的左、右儿子。

（1）得到的重构树是一个二叉树，共有$2n-1$个结点，其恰有$n$个叶子结点

（2）重构树可视为大根堆

**（3）原图中两点间所有简单路径的最大边权的最小值，等于最小生成树上两点之间边权最大值，等于重构树上两点LCA的点权**

（4）到某个结点简单路径上的最大边权最小值$\le k$的全体结点均在重构树上的某棵子树内，且恰为该子树的叶子结点。

**【例题】**

<span style="color: #7ec0ee;">**【Kruskal重构树】【ST表】CF1706E**</span>

**【题目大意】**连通无向图$|V|=n,|E|=m$，其中边按顺序给出，要求回答$q$个询问，每个询问包含参数$L,R$，输出最小的$k$，使得全体满足$L\le a<b\le R$的整数对$(a,b)$，顶点$a,b$仅使用前$k$条边可以相互到达。

以边的顺序为标准建立Kruskal重构树后，求出顶点$i,i+1$的LCA权值，要求$[L,R]$区域的最小$k$，只需快速求区间最大值，使用$ST$表，总时间复杂度$O(\max(n\log n,q,m))$

<span style="color: #7ec0ee;">**【Kruskal重构树】LuoguP1967/P2245 货车运输/星际导航**</span>

无向图$|V|=n,|E|=m$，边权为$w_i$，给出$q$个询问，先判断$x,y$是否连通，连通则求出$x$到$y$所有可能路径中最小边权最大值。

使用并查集判断连通。

方法一：直接套用Kruskal重构树；

???success "<span style="color: #7ec0ee;">**LuoguP1967/P2245 货车运输**</span>参考解答一"
	```
	#include<bits/stdc++.h>
    using namespace std;
    const int N=1e5+5,M=1e6+5;
    int n,m,q,root,tot;
    int s[N],depth[N],fa[N][25],l[N],r[N],val[N];
    struct edge{int x,y,w;}a[M];
    bool cmp(edge x,edge y){return x.w>y.w;}
    int find(int x)
    {
        if(x==s[x]) return x;
        return s[x]=find(s[x]);
    }
    void getdepth(int x,int d)
    {
        depth[x]=d;
        if(l[x]) getdepth(l[x],d+1);
        if(r[x]) getdepth(r[x],d+1);
    }
    int lca(int x,int y)
    {
        if(depth[x]<depth[y]) swap(x,y);
        for(int i=20;i>=1;i--)
        {
            if(depth[fa[x][i]]>=depth[y])
                x=fa[x][i];
        }
        if(x==y) return x;
        for(int i=20;i>=1;i--)
        {
            if(fa[x][i]!=fa[y][i])
                x=fa[x][i],y=fa[y][i];
        }
        return fa[x][1];
    }
    int main()
    {
        scanf("%d%d",&n,&m);
        tot=n;
        for(int i=1;i<=2*n-1;i++) s[i]=i;
        for(int i=1;i<=m;i++)
        {
            scanf("%d%d%d",&a[i].x,&a[i].y,&a[i].w);

        }
        sort(a+1,a+m+1,cmp);
        for(int i=1;i<=m;i++)
        {
            int xx=find(a[i].x);
            int yy=find(a[i].y);
            if(xx==yy) continue;
            tot++;
            s[xx]=s[yy]=tot;
            fa[xx][1]=fa[yy][1]=tot;
            l[tot]=xx,r[tot]=yy;
            val[tot]=a[i].w;
        }
        for(int i=1;i<=tot;i++)
            if(fa[i][1]==0)
                getdepth(i,0);
        scanf("%d",&q);
        int u,v;
        for(int i=2;i<=20;i++)	
            for(int j=1;j<=tot;j++)
                fa[j][i]=fa[fa[j][i-1]][i-1];
        for(int i=1;i<=q;i++)
        {
            scanf("%d%d",&u,&v);
            if(find(u)!=find(v)) printf("-1\n");
            else printf("%d\n",val[lca(u,v)]);
        }
        return 0;
    }
    ```

方法二：使用朴素的倍增区间最大值、LCA

在倍增求解$fa_{j,i}$时增加$ST_{j,i}$表示从$j$结点开始向上到达第$2^i$个祖先路径上的最小边权值值，初始化$st_{j,0}=w_0,由(fa_{j,0},j,w_0)边在求解depth_j,fa_{j,0}$函数中得到。

$st_{j,i}=\min(st_{j,i-1},st_{fa_{j,i-1},i-1})$

在求解LCA时，顺便求出路径区间最小值。

???success "<span style="color: #7ec0ee;">**LuoguP1967/P2245 货车运输**</span>参考解答二"
	```
	#include<bits/stdc++.h>
    using namespace std;
    const int N=1e4+5,M=1e6+5;
    struct edge{int v,w,next;}a[M];
    struct edge2{int u,v,w;}b[M];
    int st[N][25],fa[N][25],tot,n,m,q,h[M];
    int depth[N],s[N];
    int find(int x)
    {
        if(x==s[x]) return x;
        return s[x]=find(s[x]);
    }
    bool cmp(edge2 x,edge2 y){return x.w>y.w;}
    void add(int x,int y,int z)
    {
        a[++tot]=(edge){y,z,h[x]};
        h[x]=tot;
    }
    void maketree(int x,int father,int d)
    {
        fa[x][0]=father,depth[x]=d;
        for(int i=h[x];i;i=a[i].next)
        {
            int v=a[i].v;
            if(v==father) continue;
            st[v][0]=a[i].w;
            maketree(v,x,d+1);
        }
    }
    int getans(int x,int y)
    {
        int ans=1e9;
        if(depth[x]<depth[y]) swap(x,y);
        for(int i=20;i>=0;i--)
            if(depth[fa[x][i]]>=depth[y])
                ans=min(ans,st[x][i]),x=fa[x][i];
        if(x==y) return ans;
        for(int i=20;i>=0;i--)
            if(fa[x][i]!=fa[y][i])
            {
                ans=min(ans,min(st[x][i],st[y][i]));
                x=fa[x][i],y=fa[y][i];
            }
        return min(ans,min(st[x][0],st[y][0]));
    }
    int main()
    {
        cin>>n>>m;
        for(int i=1;i<=n;i++) s[i]=i;
        for(int i=1;i<=m;i++) 
            scanf("%d%d%d",&b[i].u,&b[i].v,&b[i].w);
        sort(b+1,b+m+1,cmp);
        for(int i=1;i<=m;i++)
        {
            int xx=find(b[i].u),yy=find(b[i].v);
            if(xx==yy) continue;
            s[xx]=yy;
            add(b[i].u,b[i].v,b[i].w);
            add(b[i].v,b[i].u,b[i].w);
        }
        for(int i=1;i<=n;i++)
            if(s[i]==i) maketree(i,0,1);
        for(int i=1;i<=20;i++)
            for(int j=1;j<=n;j++)
                fa[j][i]=fa[fa[j][i-1]][i-1];
        for(int i=1;i<=20;i++)
            for(int j=1;j<=n;j++)
                st[j][i]=min(st[j][i-1],st[fa[j][i-1]][i-1]);
        cin>>q;
        int u,v;
        for(int i=1;i<=q;i++)
        {
            scanf("%d%d",&u,&v);
            if(find(u)!=find(v)) printf("-1\n");
            else printf("%d\n",getans(u,v));
        }
        return 0;
    }
	```


<span style="color: #ff00ff;">**【Kruskal重构树】LuoguP4768 归程**</span>

【题目大意】无向连通图$G$，$|V|=n,|E|=m$，其边为四元组$(x_i,y_i,w_i,p_i)$，表示从$x_i$到有长度为$w_i$，海拔为$p_i$的双向边。有$Q$个询问，指示当天的出发点$v$与水位线$p$。

每条询问中，某人要从$v$号结点到达1号结点，在起始点处有一辆车，允许在高于水位线的边上行驶，否则需要停车步行，求停车步行的最短距离。

每条询问是独立的，车的信息只适用于本条询问。

为求出车可以行驶到达的结点集合，选择建立最小生成树，再构建kruskal重构树，对于某水位线$p_0$，从结点$v$出发通过车辆行驶可以互相到达的结点一定处于Kruskal重构树的某个子树$T$中。

记$dis_i$表示从1号结点到号结点的最短路长度，可知最终答案为$\min\limits_{j\in T}dis_j$，记1号结点的祖先路径为$path$，若$T\cap path \neq \varnothing$，则答案为0，否则，可以在构建Kruskal重构树，将$x,y$设为新结点$z$的儿子时，增加记录$dis_z=\min(dis_x,dis_y)$

最终输出$dis_{root}即可，其中root为T的根$

???success "参考实现"
	```
	#include<bits/stdc++.h>
    using namespace std;
    const int N=4e5+5,M=8e5+5;
    int tot,dis[N],vis[N],h[M],fa[N][21],stop[N];
    int val[N],n,m,s[N];
    struct edge{int v,w,next;}a[M];
    struct edge2{int u,v,h;}e[M];
    bool cmp(edge2 x,edge2 y){return x.h>y.h;}
    int find(int x)
    {
        if(x==s[x]) return x;
        return s[x]=find(s[x]);
    }
    struct priority
    {
        int w,v;
        bool operator<(const priority &x)const
        {
            return x.w<w;
        }
    };
    void add(int x,int y,int z)
    {
        a[++tot]=(edge){y,z,h[x]};
        h[x]=tot;
    }
    void dijkstra()
    {
        for(int i=1;i<=2*n-1;i++) dis[i]=1e9;
        std::priority_queue<priority> q;
        q.push((priority){0,1});
        dis[1]=0;
        memset(vis,0,sizeof(vis));
        while(!q.empty())
        {
            priority temp=q.top();q.pop();
            int x=temp.v;
            if(vis[x]) continue;
            vis[x]=1;
            for(int i=h[x];i;i=a[i].next)
            {
                int v=a[i].v;
                if(dis[v]>dis[x]+a[i].w)
                {
                    dis[v]=dis[x]+a[i].w;
                    if(!vis[v])
                        q.push((priority){dis[v],v});
                }
            }
        }
    }
    void kruskal()
    {
        int cnt=0;
        for(int i=1;i<n;)
        {
            cnt++;
            int xx=find(e[cnt].u),yy=find(e[cnt].v);
            if(xx==yy) continue;
            s[xx]=s[yy]=i+n;
            fa[xx][0]=fa[yy][0]=i+n;
            dis[n+i]=min(dis[xx],dis[yy]);
            val[n+i]=e[cnt].h;
            i++;
        }
        for(int i=1;i<=20;i++)
            for(int j=1;j<=2*n-1;j++)
                fa[j][i]=fa[fa[j][i-1]][i-1];
    }
    int getans(int x,int p)
    {
        for(int i=20;i>=0;i--)
            if(stop[fa[x][i]]!=1&&val[fa[x][i]]>p)
                x=fa[x][i];
        if(stop[fa[x][0]]==1&&val[fa[x][0]]>p)
            return 0;
        else return dis[x];
    }
    void findreverse()
    {
        int cnt=1;
        while(cnt) stop[cnt]=1,cnt=fa[cnt][0];
        stop[0]=1;
    }
    void test()
    {
        scanf("%d%d",&n,&m);
        for(int i=1;i<=2*n-1;i++) s[i]=i;
        int w,Q,K,S,lastans=0,V,P;
        for(int i=1;i<=m;i++) 
        {
            scanf("%d%d%d%d",&e[i].u,&e[i].v,&w,&e[i].h);
            add(e[i].u,e[i].v,w);
            add(e[i].v,e[i].u,w);
        }
        sort(e+1,e+m+1,cmp);
        dijkstra();
        kruskal();
        findreverse();
        cin>>Q>>K>>S;
        for(int i=1;i<=Q;i++)
        {
            scanf("%d%d",&V,&P);
            int v=(V+K*lastans-1)%n+1;
            int p=(P+K*lastans)%(S+1);
            lastans=getans(v,p);
            printf("%d\n",lastans);
        }
    }
    int main()
    {
        //freopen("D:\\return5.in","r",stdin);
        //freopen("D:\\out.txt","w",stdout);
        int t;cin>>t;
        while(t--) 
        {
            test();
            tot=0;
            memset(a,0,sizeof(a));
            memset(h,0,sizeof(h));
            memset(val,0,sizeof(val));
            memset(fa,0,sizeof(fa));
            memset(stop,0,sizeof(stop));
        }
        return 0;
    } 
	```
