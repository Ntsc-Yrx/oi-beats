# 各种最短路算法的Hack与区别

我们给出以下题目来探讨这个问题。

## [APIO2013] 出题人

题目描述

当今世界上各类程序设计竞赛层出不穷。而设计一场好比赛绝非易事，比如给题目设计测试数据就是一项挑战。一组好的测试数据需要对不同的程序有区分度：满足所有要求的程序自然应该得到满分，而那些貌似正确的程序则会在某些特殊数据上出错。

在本题中，你在比赛中的角色反转啦！作为一名久经百战的程序员，你将帮助 Happy Programmer Contest 的命题委员会设计这次比赛的测试数据。本次比赛命题委员会选择了两个图论问题，分为 $8$ 个子任务。委员会写了一些貌似可以解决这些子任务的代码。在给任务设计数据的时候，命题委员会期望其中的一些源程序能够得到满分，而另外的一些则只能得到 $0$ 分或者少许的部分分。现在你将会获得这些源程序（C, C++, Pascal 版本）。对于每个子任务，你需要去产生一组数据 $X$ 使得它能将该任务给定的 $2$ 种源程序 $A$ 和 $B$ 区分开来。更具体地说，生成的数据必须满足如下两个条件:

输入 $X$ 对于源程序 $A$ 一定不会出现超出时间限制（TLE）的问题。

输入 $X$ 一定会导致源程序 $B$ 产生超出时间限制的问题。

此外,命题委员喜欢较小规模的测试数据，希望测试数据最好能够包含不超过 $T$ 个整数。

本题中只关心源程序 $A$ 和 $B$ 是否超时，不关心是否结果正确。

命题委员会选择了单源最短路（SSSP）以及一个被称之为神秘问题（Mystery）的两个图论问题来作为比赛的题目。我们将命题委员会完成的伪代码列在了附录中，而具体的 C、C++ 和 Pascal 源程序被我们放在了下发的文件当中。

### 子任务

参见下表。表中每一行描述了一个子任务。其中前六个子任务与单源最短路相关，子任务 7,8 与神秘问题相关。每个任务所占分数见下表。

![https://cdn.luogu.com.cn/upload/pic/4428.png](各种最短路算法的Hack与区别/4428.png)

### 思路

我们要让A通过且B出现TLE。

## Dijkstra和Floyd

卡Floyd，最好的方法就是从复杂度入手。这里我们可以构造一个含有101个点的输入，就可以卡掉了

## 干Bellman-ford：

复杂度Θ(QVE)，来个负权，再来一堆自环/重边，人肉二分保证数据不超过T，且让Bellman-ford刚刚超过一丁点，就可以了，

第2个点要Floyd过，V=100即可。

第5个点要Dijkstra过，那么就让0号点到299号点连正权边，其它点搞一堆负环+自环+重边，Bellman-ford轻松干掉。

## 干Dijkstra：

说了Dijkstra看到负权就GG，所以构造一堆0边诱惑他，然后再让他从右边的点进去，举个栗子：

V=0,1,2,3,4  D,E=(0,1,2),(1,2,-4),(2,3,1),(3,4,-2),(0,2,0),(2,4,0)

那么就先把它拐到4，发现路长为0，然后走2~3是最短的，拐到3，开始觉醒后，发现0~1再到2，路长为-2，再走2~3，傻傻地Dijkstra就被坑了，

## 干染色图算法



