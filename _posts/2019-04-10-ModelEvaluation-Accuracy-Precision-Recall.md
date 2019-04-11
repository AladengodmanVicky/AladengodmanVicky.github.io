---
published: false
layout: post
date: '2019-04-10 08:34:00 +0800'
categories: AI
tags:
  - 模型评估
  - 准确率(Accuracy)
  - 精确率(Precision)
  - 召回率(Recall)
  - 综合评价指标(F1-Measure)
excerpt: >-
  自然语言处理(NLP),机器学习(ML),信息检索(IR)等领域,评估(evaluation)是一个必要的工作,而其评价指标往往有如下几点:准确率(Accuracy),精确率(Precision),召回率(Recall)和综合评价指标(F1-Measure)。
publised: false
---
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

---

## 序言

自然语言处理(ML),机器学习(NLP),信息检索(IR)等领域,评估(evaluation)是一个必要的工作,而其评价指标往往有如下几点:准确率(Accuracy),精确率(Precision),召回率(Recall)和综合评价指标(F1-Measure)。

---

## 准确率

准确率(Accuracy)是一个用于评估分类模型的指标。用人话说就是，**准确率是模型预测正确的结果所占量的比例**。

**准确率**的伪公式：

```
准确率（Accuracy） = Number of correct predictions / Total number pf predictions = 正确预测数 / 预测总数
```

在二元分类中，可根据正类别与负类别按如下方式计算：

注：下方公式中，TP = 真正例 ， TN = 真负例 ， FP = 假正例 ， FN = 假负例。

<div align="center"><img src="https://www.bobinsun.cn/assets/images/accuracy_01.png"/></div>

试举例计算模型的准确率，假设某模型将100个肿瘤分为**恶性**（正类别）或**良性**（负类别）:

<div align="center"><img src="https://www.bobinsun.cn/assets/images/accuracy_eg_01.png"/></div>

根据上述例子的数据我们来计算该模型的**准确率**：

<div align="center"><img src="https://www.bobinsun.cn/assets/images/accuracy_02.png"/></div>

乍一看，该模型的准去确率为**0.91**，也就是**91%**，（100个样本中有91个预测正确），**这是不是可以表示我们的肿瘤分类器在识别恶性肿瘤方面酒标的非常出色呢？**

带着这个疑问，我们仔细分析一下正类别和负类别，深入理解改模型的效果。

100个肿瘤样本中，**91个为良性**，其中，1个FP（假正例）& 90个TN（真负例），**9个为恶性**，其中，1个TP（真正例）&8个FN（假负例）。

整个样本中有91个良性肿瘤，该模型将90个样本正确识别为良性肿瘤，将1个样本识别为恶性，这个效果很好。**但是**，在9个恶性肿瘤样本中，将8个样本识别为良性，9个恶性肿瘤有8个未被诊断出来，8/9，这个结果多么可怕！！！

91%的准确率，看起来还不错，如果另一个肿瘤分类器模型总是预测良性，那么这个模型使用我们的样本进行预测，也会得出相同的准确率。

换句话说，该模型与那些没有预测恶性肿瘤和良性肿瘤的模型差不多。

还有，当我们使用**分类不平衡的数据集**（如：正类别标签与负类别标签数量存在明显差异）时，淡淡一项准确率并不能反映情况。

> 为了更好的评估分类不平衡的数据集问题，下面引入精确率（Precision）和召回率（Recall）

---

## 精确率

精确率为解决`在被识别为正类别的样本中，为正类别的比例`。精确率的公式定义如下：

<div align="center"><img src="https://www.bobinsun.cn/assets/images/precision_01.png"/></div>

`Tips: 如果模型预测结果中没有假正例，则模型的精确率为1。`

那我们来接着上面肿瘤预测的样本结果来计算其精确率，好，接着看预测样本分布图：

<div align="center"><img src="https://www.bobinsun.cn/assets/images/precision_02.png"/></div>

其精确率的计算结果为：

<div align="center"><img src="https://www.bobinsun.cn/assets/images/precision_eg_01.png"/></div>

可以看到该肿瘤预测模型的精确率为0.5，换句话说就是，该模型在预测恶性肿瘤方面的正确率是50%。

---

## 召回率

召回率为解决`在所有正类别样本中，被正确识别为正类别的比例`。召回率的公式定义如下：

<div align="center"><img src="https://www.bobinsun.cn/assets/images/recall_01.png"/></div>

`Tips: 如果模型的预测结果没有假负例，则模型的召回率为1.0`。






---

##
