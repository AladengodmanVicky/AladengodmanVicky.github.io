---
published: false
layout: post
date: '2020-12-01 30:34:00 +0800'
categories: Graph
tags:
  - 图算法
  - 图特征
excerpt: 
title: 图算法与图特征
---
# 图遍历算法
图的遍历是指从图的任意节点出发，对图中的所有节点进行访问，并且每个节点只访问一次。图的遍历操作和树的遍历操作功能相似。图的遍历是图的一种基本操作，图的其它许多操作都是建立在遍历操作的基础之上。

由于图结构本身的复杂性，图的遍历操作也较复杂，主要表现在以下4个方面：

1. 在图结构中，没有“自然”的首节点，图中任意节点都可作为第一个被访问的节点。
2. 在非连通图中，从一个节点出发，只能够访问它所在的[连通分量]()上的所有节点，因此，还需考虑如何选取下一个出发点以访问图中其余的连通分量。
3. 在图结构中，如果有[回路]()存在，那么一个节点被访问之后，有可能沿回路又回到该顶点。
4. 在图结构中，一个节点可以和其它多个节点相连，当这样的节点访问过后，存在如何选取下一个要访问的节点的问题。

图遍历通常有深度优先搜索、广度优先搜索和A*搜索，下面分别介绍：
## 深度优先搜索(DFS)
![DFS](https://i.loli.net/2020/12/01/uHPR7v42EkTFpe8.gif)

<div align="center" width="auto" height="40%"><img src="https://i.loli.net/2020/12/01/uHPR7v42EkTFpe8.gif"/></div>

## 广度优先搜索(BFS)
![BFS](https://i.loli.net/2020/12/01/l5kwuMtvapQjXOr.gif)
## A*搜索
# 最短路径算法
![zui_duan_lu_jing](https://i.loli.net/2020/12/01/iOLnDovbsQyX6tR.gif)
## Dijkstra算法
## Bellman-Ford算法
## Floyd-Warshall算法
# 最小生成树
![zui_xiao_sheng_cheng_shu](https://i.loli.net/2020/12/01/jMLIBAEdFGctDSm.gif)
## Prim算法
## Kruskal算法
# 图匹配
## 匈牙利算法
![pi_pei](https://i.loli.net/2020/12/01/CPZl7RgwQmhaMeX.gif)
# 强连通分支算法与网络流
## Ford-Fulkerson算法
![Maximum_Flow](https://i.loli.net/2020/12/01/tpK1hdJQSIUDibu.gif)

