---
published: false
layout: post
date: '2019-04-011 08:34:00 +0800'
categories: AI
tags:
  - 模型评估
  - 准确率(Accuracy)
  - 精确率(Precision)
  - 召回率(Recall)
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

<div align="center"><img src="https://www.bobinsun.cn/assets/images/Accuracy-01.png"/></div>

试举例计算模型的准确率，假设某模型将100个肿瘤分为**恶性**（正类别）或**良性**（负类别）:

<div align="center"><img src="https://www.bobinsun.cn/assets/images/accuracy-example-01.png"/></div>

根据上述例子我们来计算**准确率**：

<div align="center"><img src="https://www.bobinsun.cn/assets/images/Accuracy-02.png"/></div>

---

## 精确率



---

## 召回率



---

##
