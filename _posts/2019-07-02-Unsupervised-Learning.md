---
published: true
layout: post
date: '2019-07-02 18:34:00 +0800'
categories: AI
tags:
  - 统计学习
  - 无监督学习
  - 算法总结
excerpt: 无监督学习方法的模型、策略、算法总结。
title: 无监督学习方法的特点
---
## 无监督学习方法的模型、策略、算法

无监督学习用于聚类、降维、话题分析、图分析。


 / | 方法 | 模型 | 策略 | 算法 
 -| - | - | - | -
 **聚类** | 层次聚类 | 聚类树 | 类内样本距离最小 | 启发式算法
 **聚类** | K均值聚类 | K中心聚类 | 样本与类中心距离最小 | 迭代算法
 **聚类** | 高斯混合模型 | 高斯混合模型 | 似然函数最大 | EM算法
 **降维** | PCA | 低维正交空间 | 方差最大 | SVD
 **话题分析** | LSA | 矩阵分解模型 | 平方损失最小 | SVD
 **话题分析** | NMF | 矩阵分解模型 | 平方损失最小 | 非负矩阵分解
 **话题分析** | PLSA | PLSA模型 | 似然函数最大 | EM算法
 **话题分析** | LDA | LDA模型 | 后验概率估计 | 吉布斯抽样，变分推理
 **图分析** | PageRank | 有向图上的马尔可夫链 | 平稳分布求解 | 幂法
 
 
## 术语注释
 
 * **PCA** : 主成分分析（Principal Components Analysis）
 * **LSA** ：潜在语义分析（Latent Semantic Analysis）
 * **NMF** ：非矩阵分解（Non-negative Matrix Factorization）
 * **PLSA** : 概率潜在语义分析（Probabilistic Latent Semantic Analysis）
 * **SVD** : 奇异值分解（Singular Value Decomposition）
 * **LDA** : 潜在狄利克雷分配（Latent Dirichlet Allocation）
 
 >                                                  ---摘自《统计学习方法》·李航
