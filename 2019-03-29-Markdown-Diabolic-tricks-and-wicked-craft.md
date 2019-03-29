title: Markown用法之-奇技淫巧
layout: post
date: '2019-03-29 08:34:00 +0800'
categories: Blog
published: true
tags:
  - Markdown
  - 奇技淫巧
  - 图片居中
  - 视频适配
excerpt: >-
  本篇文章不涉及Markdown的基本用法，主要总结本人在使用Markdown写博客时所用到的Markdown奇技淫巧，如有需要，拿走不谢。

<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

---

## Markdown图片用法

#### 图片居中

```
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>
```

#### 自定义图片大小与位置

```
<div align="center"><img width=" " height=" " src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>
```

---

## Markdown插入视频

#### 视频适配屏幕

```
<video src="http://qiniu.swarma.org/newUser.mp4" controls="controls" width="100%" height="auto"/>

```

```
src：视频地址---http://qiniu.swarma.org/newUser.mp4

controls：显示或隐藏播放器 true/false

width：播放器宽度

height：播放器的高度
```