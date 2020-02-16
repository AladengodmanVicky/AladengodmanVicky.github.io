---
published: true
layout: post
date: '2020-02-16 17:30:00 +0800'
categories: tools
tags:
  - EverNote
  - Sublime
  - Markdown
  - 云端同步
  - 写作系统
excerpt: Mac环境下使用EverNote与Sublime搭建简洁、优雅的云端同步Markdown写作系统。
title: EverNote与Sublime搭建云端Markdown写作系统
---
## 天下苦秦久矣

自从开始写博客，越来越迷恋`Markdown`这种优雅的写作方式，无论写什么，一直在寻觅一种优雅地、得心应手地`Markdown`写作系统，苦于未果。

## 写作系统的痛点

许久未找到搜寻到适合的写作系统，究其原因，主要有两大痛点未被满足：

1. 市面上大多数`Markdown`编辑器都需要保存在本地，而我确需要多终端同步，在家里电脑、公司电脑以及手机端同步。
2. Evernote、有道云笔记等云笔记既要满足多终端云同步，同时满足Markdown编辑方式，但我需要预览、查看、编辑拆分开来（这里的预览与查看状态不同），使操作轻量化、简洁化。

以上的写作环境都不能满足我轻量化、优雅地编辑体验。因此，转而继续寻觅...

## 初见曙光

直到看到吕立青的一篇文章[敏捷写作：MACOS 环境下写作系统的最优配置](https://gitpress.io/@jimmylv/2016-06-11-write-in-mac-os-x)，瞬间眼前一亮，里面提及Evernote与Sublime无缝对接的方式。

* Evernote：一款多平台的云笔记；
* Sublime：一款轻量级的编辑器；

## 为什么是它们？

**为什么是Evernote？**有道云笔记没有和Sublime联动的插件，Evernote在Sublime上有插件[sublime-evernote](https://github.com/bordaigorl/sublime-evernote)-使用Markdown打开和保存Sublime中的Evernote笔记。

**为什么是Sublime？**Sublime是收费软件，但可以无限期试用，有漂亮的用户界面和强大的功能，安装包小巧、功能插件丰富。

**这里先看一下效果吧：**

![Evernote&Sublime组合使用效果](https://www.bobinsun.cn/assets/images/evernote-sublime-01.png)

## Sublime-Evernote插件特点

* **发送笔记至Evernote**： 将当前视图中的Markdown文件转化为富文本格式并将其发送到Evernote，并且可设置标题、标签和存储位置；
* **打开Evernote笔记**：Sublime命令面板可从Evernote笔记本中选择笔记，或通过搜索将富文本笔记转换成Markdown笔记在Sublime视图中显示；
* **更新Evernote笔记**：在Sublime编辑已打开笔记的Markdown文件后，可以将其保存回Evernote（以富文本格式）；
* **支持全面双向Metadata**：可以在Markdown文件中设置YAML Metadata更改文件中的笔记本、标题和标签；
* **附件**：可以打开、插入、罗列、删除附件；
* **剪辑笔记**：可将当前所选文字作为代码段保存到新笔记中；

## Evernote&Sublime环境配置

第一步，安装Evernote和Sublime，这里就不多说了，去官网下载最新版本。

### Sublime安装MarkdownEditing

`MarkdownEditing`是一款Sublime中编辑Markdown的插件，安装后Sublime可支持编辑Markdown文件。

在Sublime中`工具`栏打开`命令面板`，输入`Package Control:Install Package`打开下载仓库，输入MarkdownEditing下载安装。

如果不支持在线安装，则移步[MarkdownEditing-github](https://github.com/SublimeText-Markdown/MarkdownEditing)下载，进行手动导入安装。

### Sublime安装Evernote插件

在Sublime中`工具`栏打开`命令面板`，输入`Package Control:Install Package`打开下载仓库，输入Evernote下载安装。

### Sublime连接印象笔记账号

* 首先从[Evernote Token](https://app.yinxiang.com/api/DeveloperToken.action)获取你`Evernote`的Token，获取之后切记保密。
* 拿到Token后，在`Preferences > Package Settings > Evernote > Settings-User`填写`noteStoreUrl`和`token`字段。
* 保存并重新启动Sublime，完成账号的关联。

```
{
    "noteStoreUrl": "your noteStoreurl XXX",
    "token": "your token XXX",
}
```

### Sublime操作同步至Evernote

在Sublime中`工具`栏打开`命令面板`，此时输入Evernote就会出现有关操作Evernote的指令，常用指令包括：

```
Command Palette > Evernote: New empty note    //新建空笔记
Command Palette > Evernote: Open Evernote Note   //打开笔记本
Command Palette > Evernote: Send to Evernote    //发送至Evernote
Command Palette > Evernote: Update Evernote Note    //更新Evernote笔记
```

![Sublime操作Evernote方式](https://www.bobinsun.cn/assets/images/evernote-sublime-02.png)

以上只是常用指令，详细指令可查看Evernote插件的官方Github地址：[sublime-evernote](https://github.com/bordaigorl/sublime-evernote)

同时`sublime-evernote`非常友好的提供了快捷键设置操作，在Sublime中打开`Preferences > Key Bindings-User `，将以下配置项填写至其中：

```
{ "keys": ["super+e"], "command": "show_overlay", "args": {"overlay": "command_palette", "text": "Evernote: "} },
{ "keys": ["ctrl+e", "ctrl+s"], "command": "send_to_evernote" },
{ "keys": ["ctrl+e", "ctrl+o"], "command": "open_evernote_note" },
{ "keys": ["ctrl+e", "ctrl+u"], "command": "save_evernote_note" },
```

好了，剩下的就自己体验吧！可以说是很优雅了。

## MacOS中使用ShiftIt管理窗口的大小和位置

![ShiftIt快速布局多应用窗口效果](https://www.bobinsun.cn/assets/images/evernote-sublime-03.png)

这里多说两句，上面的截图使用了左右窗口，此窗口不是手动布局，而是通过[ShiftIt工具](https://github.com/fikovnik/ShiftIt)进行自动布局，可使用快捷键快速布局多应用界面窗口。

![ShiftIt快捷键列表](https://www.bobinsun.cn/assets/images/evernote-sublime-04.png)

> 安装软件时切记打开对应的权限。

结合个人应用需求不断探索、寻找高效率软件，提高单位时间内的输入、产出结果。
