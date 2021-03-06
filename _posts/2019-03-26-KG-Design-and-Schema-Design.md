---
published: true
layout: post
date: '2019-03-26 10:34:00 +0800'
categories: Works
tags:
  - 知识图谱
  - 产品设计
  - Schema
  - 思考&整理
excerpt: >-
  1、知识图谱所说的关系是底层存储时以关系的形式存储，还是上层以关系的形式展示/应用，到底什么样的图产品可以称之为知识图谱？
  2、知识图谱的Schema如何设计，设计要点在哪，以及流程是什么样的？
title: 知识图谱产品设计与Schema定义(KG-PM系列)
---
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

---

## 背景

与@伟哥微信认识一个多月了，两周前约见并对于知识图谱的一些问题和想法进行讨论，感谢伟哥带着电脑并向我演示了他们的产品。

```
Tips：以下知识图谱（简称：KG）
```

## 方向

整个讨论以伟哥演示他们的产品为主线，围绕**如何理解KG**、**to B KG产品设计策略**、**to B KG产品的发展方向**三大块进行讨论交流。

> 对于如何理解KG，先来看学术界的定义：

知识图谱是结构化的语义知识库，用于以符号形式描述物理世界中的概念及其相互关系，其基本组成单位是『实体-关系-实体』三元组，以及实体及其相关属性-值对，实体之间通过关系相互联结，构成网状的知识结构。

## 疑问

**对于上述定义有两点疑问：**

1.上面所说的关系是底层存储时以关系的形式存储，还是上层以关系的形式展示/应用，到底什么样的图产品可以称之为知识图谱？

2.KG的Schema如何设计，设计要点在哪，以及流程是什么样的？

---

## 问题1

### 方案

当时并未对第1点达成一致，后来伟哥提到一个新框架：**图平台 + 算法平台 + 应用平台**

**是不是有点抽象，先来拆分一下：**

- **图平台**：所谓图平台就是把结构化、非结构化等数据以关系的形式进行存储，提供给其他应用平台提供数据支持。其实知识图谱就隐藏在图平台里，说白了知识图谱就是将各类源数据转换成以关系的形式进行存储，所谓数据的抽取、表示、建模、获取、融合、存储等等一系列操作都是进行数据组织的过程，无所谓是用关系型数据库还是用图数据库存储。

- **算法平台**：算法平台是连接图平台与应用平台的中间件，数据组织的过程要用到算法，上层的查询推理也要用到算法，算法可以说贯穿整个从构建到应用的过程。

- **应用平台**：应用平台就是常说的业务场景，包含通用场景与细分行业场景，产业界所有的技术都应以支撑业务为中心，应用平台侧重知识的查询与推理，用最简单、最直接的操作获得数据的商业价值。

### 思考

> 在了解了伟哥演示的产品后，发现一个问题，（要吐槽了，伟哥勿打），作为细分行业to B产品，该产品只是基于已有数据做了图的展示，进行数据的图关系展示、查询搜索、路径打点连接、数据分布展示等。**用我原话说：“感觉这个产品没有灵魂，没有核心竞争力”**。

为什么这么说呢？是，该产品将数据的关系梳理清楚，合理展示，以及展示数据在各个区段内的分布，能在短时间内发现数据之间的关联，方便业务人员进行查看了解关系盲区、数据盲区，缺点是基于数据的各条线路过于宽泛、杂乱，不能帮助业务人员有针对性的分析发现问题、聚焦问题，为决策提供有效帮助，属于一个信息聚合产品。因此，伟哥这个KG产品只能算是图平台。

我的想法是可以根据业务场景梳理思维逻辑，抽象出规则，根据现在的数据关系基于某条规则、某条线路进行推理，根据一些算法如聚类、分类、关键点发现等等去挖掘业务问题点，真正做到让数据支撑业务决策，属于基于图谱实现算法对标业务场景。这一层涉及到具体的业务应用，算是应用平台。

### 发展

> 据我对国内业界的了解，大多KG公司对于构建图平台已经不是难点了，困难在于根据业务场景构建应用平台与算法平台，以及由应用平台与算法平台反哺图平台。下一步KG的发展方向应该聚焦基于图平台的应用平台设计。

---

## 问题2

> 针对第2点，KG的Schema如何设计，设计要点在哪，以及流程是什么样的？

**KG的Schema相当于领域内的数据模型，属于KG的模式层，其实就是用来描述本体层(Ontology)**。为KG设计Schema相当于为其建立本体(Ontology)，包括概念、概念层次、属性、属性值类型、关系、关系定义域（Domain）概念集以及关系值域（Range）概念集。

Schema是用来规范KG的领域与描述对象，起到管理KG的作用，比如概念本身的属性可以直接传递到实例，不需要为实例重新定义属性(模式层的属性)，实例可不完全包含概念的属性。如：“公司”会有“注册日期”，但具体到某个实例如“腾讯”可以没有这个属性，但如果“腾讯”有“注册日期”这个属性，可以直接用概念“公司”中的“注册日期”作为属性

KG的设计主要为满足业务需求与应用场景，业务需求与应用场景决定产品设计，**图平台产品设计**的基础任务又是定义Schema，其中产品经理的主要任务就是考虑Schema该如何构建。

Schema定义是与业务强行绑定的，每个KG的实际情况都不尽相同，没有通用的标准与流程，希望可以从从别人的只言片语中得到些许灵感或方向。

### 伟哥看法

我觉得schema这部分分为两层，1.架构上的schema，2.是基于架构上的schema进行业务梳理的实例化，第一点我觉得和技术选型底层设计息息相关，毕竟谁家的schema样式结构都不一样，第二点我觉得是基于第一点进行的业务数据构建，这部分产品经理可以通过梳理业务数据进行实例构建，不清楚你提的是第一点还是第二点。

可以说一个是系统Schema,一个是业务Schema 。系统Schema主要由架构师来定，从表设计到数据库的构建过程。伟哥认为：第一个是系统的schema构建，另一个是基于业务梳理的实例化展示，这里好像没有schema的事。

### 画一个逗逗陪着我的看法
> 以下是简书作者：**画一个逗逗陪着我**的一些经验分享，原文地址：[知识图谱基础（三）-schema的构建，整理过来以供参考](https://www.jianshu.com/p/704e935c98a9)。

### Schema定义

1.**构建域**

域（Domain）的概念在类型（type）之上，定义域时应尽量抽象，域与域之间尽量相互独立，不交叉，如省份就不可定义为域，考虑是否要把一个概念当做域时，主要看这个概念是否可继续向上抽象，省份之上地区、国家、洲等等，他们都属于地理位置域。

2.**确定域的类型**

确定KG的业务需求、应用场景，思考Schema的核心需求，基于需求，需要确定哪些概念？如：汽车领域，包括汽车品牌、车系、发动机、油耗等；NBA领域，包括球队、所属联盟、教练、球员等。针对不同的需求，需要在域下面定义不同的类型满足需求。

3.**确定属性**

可从两方面思考：1、以用户需求为出发点；2、以数据统计为证据；比如构建了足球领域的球队类型后，类型集合了所有的球队实体，从用户角度出发，需要关注哪些关系。

<div align="center"><img src="https://www.bobinsun.cn/assets/images/kg-score.png"/></div>

### Schema的确认流程

1.**需求划分**

将应用根据需求强弱将其划分，可分为：基础核心需求、Schema特色需求、惊喜性需求、系统扩展需求。

基础核心需求：构建KG的Schema需要的完成的核心需求，其优先级最高。
Schame特色需求：需求优先级不是最高，但能形成与竞品形成差异化。
惊喜性需求：非基础核心需求，做了最好，不做也可以。
扩展型需求：需要充分考虑产品未来业务变化，该类需求可大大改变Schema结构。

2.**列出功能点**

根据需求划分，列出功能点，对功能点进行优先级排期，并充分考虑扩展性与业务发展变化。

3.**转化查询结构**

对每个功能点进行梳理，列出要点、重点，将产品需求转化为查询结构，查询语句可以是对用户体验最重要的一环，是从用户输入到结构返回的整个过程。尽量避免其中的逻辑漏洞。

4.**转化为开发需求**

将构建好的Schema与产品文档找与开发探讨，开发同学对该方案进行工程实现、查询效率、计算量、实现周期等方面进行考虑，产品经理设计时更侧重从需求与功能的方面思考，双方进行合理评估才得出最优方案。

---

## 结束

所以这块的具体情况还不是很清楚，**后续再来补充**。

> 以上是近期对于知识图谱的一些思考与总结，知识图谱系列会持续更新，也会加大关注AI领域的其他产品设计。
