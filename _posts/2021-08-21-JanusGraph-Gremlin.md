---
layout: post
title: Gremlin图遍历语言简明文档
date: '2021-08-21 12:34:45 +0800'
categories: Blog
published: true
tags:
  - Gremlin
  - JanusGraph
  - 知识图谱
---

最近一年对JanusGraph接触较多，故经常使用Gremlin图遍历语言，对其常见语法做简要整理，备忘。

# Gremlin语句基础用法介绍

## 基础语法

- **V()**：查询顶点，一般作为图查询的第1步，后面可以续接的语句种类繁多。例：g.V()，g.V('v_id')，查询所有点和特定点；

- **E()**：查询边，一般作为图查询的第1步，后面可以续接的语句种类繁多；

- **id()**：获取顶点、边的id。例：g.V().id()，查询所有顶点的id；

- **label()**：获取顶点、边的 label。例：g.V().label()，可查询所有顶点的label。

- **key()/values()**：获取属性的key/value的值。

- **properties()**：获取顶点、边的属性；可以和 **key()**、**value()**搭配使用，以获取属性的名称或值。例：g.V().properties('name')，查询所有顶点的 name 属性；

- **valueMap()**：获取顶点、边的属性，以Map的形式体现，和properties()比较像；

- **values()**：获取顶点、边的属性值。例：g.V().values() 等于 g.V().properties().value()

##  遍历
###  以“顶点”为基准

- **out(label)**：根据指定的Edge Label来访问【顶点的**OUT**方向邻接点】（零个Edge Label，代表所有类型边；也可为一个或多个Edge Label，代表任意给定Edge Label的边，下同）；

- **in(label)**：根据指定的Edge Label来访问【顶点的**IN**方向邻接点】；

- **both(label)**：根据指定的Edge Label来访问【顶点的双向邻接点】；

- **outE(label)**：根据指定的Edge Label来访问【顶点的**OUT**方向邻接边】；

- **inE(label)**：根据指定的Edge Label来访问【顶点的**IN**方向邻接边】；

- **bothE(label)**：根据指定的Edge Label来访问【顶点的双向邻接边】；

### 以“边”为基准

- **outV()**：访问【边的出顶点】，出顶点是指【边的起始顶点】；

- **inV()**：访问【边的入顶点】，入顶点是指【边的目标顶点】，箭头指向的顶点；

- **bothV()**：访问【边的双向顶点】；

- **otherV()**：访问【边的伙伴顶点】，即相对于基准顶点而言的另一端的顶点；

##  过滤
has语句是filter类型语句的代表，能够以顶点和边的属性作为过滤条件，决定哪些对象可以通过。常用的有下面几种:

- **has(key,value):** 通过属性的名字和值来过滤顶点或边；

- **has(label, key, value):** 通过label和属性的名字和值过滤顶点和边；

- **has(key,predicate):** 通过对指定属性用条件过滤顶点和边，例：g.V().has('age', gt(20))，可得到年龄大于20的顶点； **predicate**（断言）

- **hasLabel(labels…):** 通过 label 来过滤顶点或边，满足label列表中一个即可通过；

- **hasId(ids…):** 通过 id 来过滤顶点或者边，满足id列表中的一个即可通过；

- **hasKey(keys…):** 通过 properties 中的若干 key 过滤顶点或边；

- **hasValue(values…):** 通过 properties 中的若干 value 过滤顶点或边；

- **has(key):** properties 中存在 key 这个属性则通过，等价hasKey(key)；

- **hasNot(key):** 和 has(key) 相反；

##  路径

- **path()**：获取当前遍历过的所有路径；

- **simplePath()**：过滤掉路径中含有环路的对象，只保留路径中不含有环路的对象；

- **cyclicPath()**：过滤掉路径中不含有环路的对象，只保留路径中含有环路的对象。

##  迭代

- repeat()：指定要重复执行的语句；

- times()： 指定要重复执行的次数，如执行3次；

- until()：指定循环终止的条件，如一直找到某个名字的朋友为止；

- emit()：指定循环语句的执行过程中收集数据的条件，每一步的结果只要符合条件则被收集，不指定条件时收集所有结果；

- loops()：当前循环的次数，可用于控制最大循环次数等，如最多执行3次。

- repeat() 和 until() 的位置不同，决定了不同的循环效果：

- repeat() + until()：等同 do-while；

- until() + repeat()：等同 while-do。

- repeat() 和 emit() 的位置不同，决定了不同的循环效果：

- repeat() + emit()：先执行后收集；

- emit() + repeat()：表示先收集再执行。

## 排序

- order()

- order().by()

## 逻辑

- **is()**：可以接受一个对象（能判断相等）或一个判断语句（如：P.gt()、P.lt()、P.inside()等），当接受的是对象时，原遍历器中的元素必须与对象相等才会保留；当接受的是判断语句时，原遍历器中的元素满足判断才会保留，其实接受一个对象相当于P.eq()；

- **and()**：可以接受任意数量的遍历器（traversal），原遍历器中的元素，只有在每个新遍历器中都能生成至少一个输出的情况下才会保留，相当于过滤器组合的与条件；

- **or()**：可以接受任意数量的遍历器（traversal），原遍历器中的元素，只要在全部新遍历器中能生成至少一个输出的情况下就会保留，相当于过滤器组合的或条件；

- **not()**：仅能接受一个遍历器（traversal），原遍历器中的元素，在新遍历器中能生成输出时会被移除，不能生成输出时则会保留，相当于过滤器的非条件。

## 统计

- **sum()**：将 traversal 中的所有的数字求和；

- **max()**：对 traversal 中的所有的数字求最大值；

- **min()**：对 traversal 中的所有的数字求最小值；

- **mean()**：将 traversal 中的所有的数字求均值；

- **count()**：统计 traversal 中 item 总数。

# 常用Gremlin语句详解

### 查询所有点，但限制点的返回数量为100，也可以使用range(x, y)的算子，返回区间内的点数量

```
g.V().limit(100)

```

### 查询点的label值为'software'的点

```
g.V().hasLabel('software') # label为点类型名称，如：“员工”、“客户”，例：g.V().hasLabel('员工') ；g.V().hasLabel('账户','员工')
```

### 查询id为'11'的点
```
g.V('11')

g.V().id() #查询所有点的janusGraph生成的点id #12312
```

###  查询id为'8392'的点属性

```
g.V('8392').properties()

g.V('8392').valueMap()
```

###  查询账户点中卡账号属性为'6217002430020910004'的OUT方向邻接边

```
g.V().has('账户','卡账号','6217002430020910004').outE().limit(20)
```

### 查询账户点中卡账号属性为'6217002430020910004'的IN方向邻接边

```
g.V().has('账户','卡账号','6217002430020910004').inE().limit(20)
```

### 查询账户点中卡账号属性为'6217002430020910004'的双向邻接边

```
g.V().has('账户','卡账号','6217002430020910004').bothE().limit(20)

g.V().hasLabel('person') // lable 等于 person 的所有顶点；

g.V().has('age',inside(20,30)).values('age') // 所有年龄在20（含）~30（不含）之间的顶点；

g.V().has('age',outside(20,30)).values('age') // 所有年龄不在20（含）~30（不含）之间的顶点；

g.V().has('name',within('josh','marko')).valueMap() // name 是'josh'或'marko'的顶点的属性；

g.V().has('name',without('josh','marko')).valueMap() // name 不是'josh'或'marko'的顶点的属性；

g.V().has('name',not(within('josh','marko'))).valueMap() // 同上,用not修饰within来生成without语义

g.V().properties().hasKey('age').value() // age 这个属性的所有 value

g.V().hasNot('age').values('name') // 找到所有不含age属性的顶点，并且获取他们的name

g.V().has('账户','卡账号','6217002430020910004').bothE().bothV().bothE().limit(20)

g.V().has('账户','卡账号','6217002430020910004').both().both().bothE().limit(20)

g.V().has('账户','卡账号','6217002430020910004').both().both().bothE().hasLabel('转账交易').has('资金交易总金额',within('2342353')).limit(100)

g.V(602128).bothE().where(hasLabel('家庭地址').or().hasLabel('家庭电话')).bothV().dedup().has('座机号码',is('021-7625532')).valueMap()
```

### 查询过滤某个下一层点边的语法结构

```
g.V(16520).bothE().where(has().and().has().or().has()).otherV().hasLabel().where(has().and().has().or().has())
```

### where()中可以使用如下条件

```
g.V().has('age',inside(20,30)) // 所有年龄在20（含）~30（不含）之间的顶点；

g.V().has('age',outside(20,30)) // 所有年龄不在20（含）~30（不含）之间的顶点；

g.V().has('name',within('josh','marko')) // name 是'josh'或'marko'的顶点的属性；

g.V().has('name',without('josh','marko')) // name 不是'josh'或'marko'的顶点的属性；

g.V().has('name',not(within('josh','marko')))// 同上

g.V().has('name',is('josh'))
```

### 抽象示例

```
g.V(16520).bothE('edgeLabel1','edgeLabel2').where(has('edgeProp1',eq(edgeValue1)).and().has('edgeProp2',eq(edgeValue2)).or().has('edgeProp3',eq(edgeValue3))).otherV().hasLabel('vertexLabel1','vertexLabel2').where(has('vertexProp1',eq(vertexValue1)).and().has('vertexProp2',eq(vertexValue2)).or().has('vertexProp3',eq(vertexValue3)))
```

### 实际示例

```
g.V(16520).bothE('员工管辖客户','员工本人行内账户','关联关系','转账交易').where(has('资金交易总金额',eq(12124))).otherV().hasLabel('账户','账户').where(has('卡账号','6217002430020910014'))
```

# 参考文档

[1] [http://tinkerpop-gremlin.cn/](http://tinkerpop-gremlin.cn/)