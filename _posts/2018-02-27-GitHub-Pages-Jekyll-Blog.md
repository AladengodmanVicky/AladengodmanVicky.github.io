---
layout: post
title: 使用GitHub Pages与Jekyll搭建免费博客
date: '2018-10-23 12:34:45 +0800'
categories: Blog
published: true
tags:
  - 博客搭建
  - GitHub Pages
  - Jekyll
---

> 你好，欢迎来到[阿拉灯神丁Vicky](https://www.bobinsun.cn/)的个人博客

## 本博客所用工具介绍

- **服务器托管**：[GitHub Pages](https://pages.github.com/)

- **博客生成工具**：[Jekyll](https://jekyllrb.com/)

- **Jekyll Schemes**: Mist

- **评论功能**：[gitalk](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)

- **分享功能**：[Baidu Share](http://share.baidu.com/)

- **自定义域名**： [在阿里云买的域名](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=uxdvd8jo)。当然，也可**通过此链接**[购买自己的服务器](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=uxdvd8jo)

- **访客统计**: 使用[ClustrMaps](https://clustrmaps.com/)，进行网站实时访客地图统计并展示。


## 免费CDN加速

使用[Cloudflare](https://dash.cloudflare.com/login)免费对博客进行加速，并且可加SSL,使用https协议。O(∩_∩)O哈哈~

如需使用可参考文章：[Github Pages 免费使用 SSL 以及 CDN 加速](https://leamtrop.com/2018/01/28/github-pages-cloudflare/#more)

如需有针对性的优化博客访问速度，查看哪些外链拖慢了你的网站，可使用：[Cloudflare加速优化测试](http://webpagetest.org)，输入你的网站地址可获得测试报告。

## 博客后台管理系统

授权[Prose.io](https://prose.io)去管理博客

其简单好用的特点，让我爱不释手。喜欢玩博客的朋友们可以试试！

好了总算搞完了。有问题的同学可以留言咨询。欢迎Fork.

## GitHub pages博客发布流程

### 1. 更新本地博客
```
git pull                                  #从GitHub更新本地博客代码
```
### 2. MWeb写作
`command + E`切换至“外部模式”，`command + L`切换至“文档库模式”
![mweb-wirte-blog](https://i.loli.net/2020/11/13/OcQosyGZmYqd1Df.png) 
### 3. 本地启动jekyll服务
```
bundle exec jekyll serve                  #启动本地jekyll服务
```
### 4. 查看博客、文章效果
打开链接🔗
```
http://127.0.0.1:5000                     #浏览器访问本地jekyll博客
```              
![blog-view](https://i.loli.net/2020/11/13/Q6xrhBmcwb5LUuV.png)
### 5. Jekyll站点部署到Github pages(线上环境)
```
git add --all                             #添加到暂存区
git commit -m "提交jekyll默认页面"          #提交到本地仓库
git push origin master                    #线上的站点是部署在master下面的
```
### 6. 等待几分钟，Github有一定的时间缓存...



