# 无向图（Undigraph）

> 无向图：两点之间的连接没有方向。 

## 树与无向图

树是一副无环完全图，一个含有V个节点，满足以下条件之一时，它就是一棵树：

1) 有V-1条边且没有环；

2）有V-1条边且是连接的；

3）图是连通的，但是删除任意一条边都会使它不连通；

4）图是无环的，但是加上任意一条边都会使它产生一条环；

5）任意一对简单顶点之间仅存在一条简单路径（没有重复顶点的路径）。

## 深度优先

深度优先搜索标记与起点**连通**的所有顶点所需的时间与顶点度数之和成正比。

深度优先搜索可以回答一些与连通有关的问题：一个图是否连通，一个图有多少的连通分量，两点之间是否存在路径等。


## 广度优先

广度优先经常用于寻找**最短路径**。

对于任意可达的s到v，广度优先搜索都能找到s到v的最短路径。

广度优先搜索需要的时间在最坏情况下与V+E成正比。

## DFS VS BFS 

深度优先和广度优先搜索的步骤是相同的，都先将起点存入数据结构中（栈或队列），然后重复以下步骤直到数据结构被清空：

1）取出其中下一个顶点v，并标记它；

2）将v的所有的相邻的但是没有被标记的顶点存入数据结构。

两个算的不同仅在于取出下一个顶点：

深度优先：取出最后加入的顶点

广度优先：去除最先加入的顶点

深度优先的路径通常长而曲折；广度优先的路径通常短而直接。


## 思考

### 问题1

连通图至少存在这样一个顶点，删去这个点（以及与它连接的边），图依然是连通的。找出这些点：

思路:  

注意删去了点和边

```C++
for each in 图的全部顶点：
    新图 = 旧图 - each
    dfs(新图) // 判断连通
    if 不连通：
        each是一个所求点
```

删去边的问题同理，利用dfs判断改变之后的额图是否连通。


### 问题2

判断一个图是不是无环图

思路:

```C++
HasCycle = false 
visited[1000] = {false} ;

void ifCycle(Graph G)
    for each in G.V :
        if !visited[each]:                 // 每个点dfs
            dfs(G,each,each)

void dfs(Graph G, int v, int u) 
    visited[v] = true
    for each in G.adj[v]:
        if !visited[each]:
            dfs(G,each,v)
        else if each != u:                // each已经被访问过，且each不是v的上一个点，说明有环。
            HasCycle = true 
```





