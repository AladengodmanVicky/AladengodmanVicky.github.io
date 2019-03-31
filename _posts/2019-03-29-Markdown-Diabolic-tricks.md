---
published: true
layout: post
date: '2019-03-29 08:34:00 +0800'
categories: Blog
tags:
  - Markdown
  - 奇技淫巧
  - 图片居中
  - 视频适配
excerpt: 本篇文章不涉及Markdown的基本用法，主要总结本人在使用Markdown写博客时所用到的奇技淫巧，如有需要，拿走不谢。
title: Markdown用法之-奇技淫巧
---
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

---

本篇文章不涉及`Markdown`的基本用法，主要总结本人在使用`Markdown`写博客时所用到的奇技淫巧，如有需要，拿走不谢。


## Markdown图片用法

#### 图片居中

```
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>
```

> 效果展示

<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>


#### 自定义图片大小与位置

```
<div align="center"><img width="200" height="auto" src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>
```

> 效果展示

<div align="center"><img width="300" height="auto" src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

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

> 效果展示

<video src="http://qiniu.swarma.org/newUser.mp4" controls="controls" width="100%" height="auto"/>

---

## 插入Emoji表情符号

#### Emoji资源库

`资源链接`:[EMOJI CHEAT SHEET](https://www.webfx.com/tools/emoji-cheat-sheet/):https://www.webfx.com/tools/emoji-cheat-sheet/

`资源截图：`

<div align="center"><img width="600" height="auto" src="https://www.bobinsun.cn/assets/images/emoji-01.png"/></div>

<div align="center"><img width="600" height="auto" src="https://www.bobinsun.cn/assets/images/emoji-02.png"/></div>

> 效果展示

:bowtie: :money_with_wings: :anguished: :family: :ox: :mega: :bath: :soccer: :watermelon: :bike: :us: :cn: :one: :u5408: :u6709: :do_not_litter: :sos: :x:

## 设置字体颜色与大小

#### 改变颜色

```
<font color="#191970">我要变成这个颜色#191970</font>
```

- <font color="#191970">我要变成这个颜色#191970</font>

