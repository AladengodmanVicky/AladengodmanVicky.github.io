---
layout: post
title: 使用GitHub Pages与Jekyll搭建免费且优雅的博客
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
* 服务器托管: [GitHub Pages](https://pages.github.com/)
* 客生成工具: [Jekyll](https://jekyllrb.com/)
* Jekyll Schemes:  Mist
* 评论功能: [gitalk](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)
* 自定义域名: [在阿里云买的域名](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=uxdvd8jo)。当然，也可通过此链接[购买自己的服务器](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=uxdvd8jo)
* 使用[Cloudflare](https://dash.cloudflare.com/login)免费对博客进行加速，并且可加SSL,使用https协议。O(∩_∩)O哈哈~
* 如需使用可参考文章：[Github Pages 免费使用 SSL 以及 CDN 加速](https://leamtrop.com/2018/01/28/github-pages-cloudflare/#more)
* 如需有针对性的优化博客访问速度，查看哪些外链拖慢了你的网站，可使用：[Cloudflare加速优化测试](http://webpagetest.org)，输入你的网站地址可获得测试报告。
* 博客后台管理授权[Prose.io](https://prose.io)去管理博客，其简单好用的特点，让人爱不释手，喜欢玩博客的朋友们可以试试！好了总算搞完了。有问题的同学可以留言咨询。欢迎Fork.

## GitHub pages博客发布流程

### 更新本地博客
```
git pull                                  #从GitHub更新本地博客代码
```
### MWeb写作
`command + E`切换至“外部模式”，`command + L`切换至“文档库模式”
![mweb-wirte-blog](https://i.loli.net/2020/11/13/OcQosyGZmYqd1Df.png) 
### 本地启动jekyll服务
```
bundle exec jekyll serve                  #启动本地jekyll服务
```
### 查看博客、文章效果
打开链接🔗
```
http://127.0.0.1:5000                     #浏览器访问本地jekyll博客
```              
![blog-view](https://i.loli.net/2020/11/13/Q6xrhBmcwb5LUuV.png)
### Jekyll站点部署到Github pages(线上环境)
```
git add --all                             #添加到暂存区
git commit -m "提交jekyll默认页面"          #提交到本地仓库
git push origin master                    #线上的站点是部署在master下面的
```
**等待几分钟，Github有一定的时间缓存...**

## MWeb添加GitHub为图床

### 为什么需要使用PicBed4MWeb

Github需要用**PUT**方法提交文件，而MWeb只能使用**POST**方法，所以就需要本地启动一个服务（[PicBed4MWeb](https://github.com/gaop-0561/PicBed4MWeb)），接受请求，转换后转发给github。

### 安装PicBed4MWeb项目
* 下载PicBed4MWeb至本地: `git clone https://github.com/gaopeng-hz/PicBed4MWeb.git`
* 安装依赖: `npm install`
* 修改配置文件config.json:
  ![config.json](https://raw.githubusercontent.com/AladengodmanVicky/Figurebed/master/20201214103000.jpg)
修改配置参考: 
```
"repo": "gaopeng-hz/images",  // 仓库名称
"token": "xxxx",  // token，不能公开，获取方式参考上面那篇文章
"port": 8081,  // node服务器监听端口，默认8080
"url": "/upload"  // 服务上传url，默认/upload
```
* 手动启动项目目录下`node index.js`启动服务，**终端窗口不能关闭**。
### MWeb配置
* 打开 MWeb 设置界面 - 发布服务 - 图床 - 自定义
![MWeb配置](https://raw.githubusercontent.com/AladengodmanVicky/Figurebed/master/20201214103550.jpg)
* 点击验证，上传图片，若出现以下提示则成功:
![验证成功](https://raw.githubusercontent.com/AladengodmanVicky/Figurebed/master/20201214103709.jpg)
### 设置开机启动服务
* 设置后台运行服务: `nohup node index.js &`
* 配置后台启动服务: 项目根目录下新建run.sh文件，并添加以下内容
```
 #!/usr/bin/env bash
 # 修改成自己的目录
 nohup node /你的路径/PicBed4MWeb/index.js &
```
* 给run.sh赋权限: `sudo chmod 777 run.sh`
* 将run.sh文件打开方式修改为**终端.app**
* 添加开机启动: 系统偏好设置-用户与群组-登录项-添加run.sh文件即可
### 扩展内容
* 查询端口: `lsof -i :8100`
* 关闭进程，PID 替换为查询的: `kill -9 PID`
* 查询服务 PID: `ps | grep index.js`

## 问题集锦

### 本地jekyll查看与实际效果不一致
由于长期未更新本地jekyll及其依赖包，导致本地jekyll查看效果与实际效果不一致，参考[更新Jekyll](https://www.cnblogs.com/obarong/p/12596067.html)。
```
bundle update jekyll                      #更新jekyll
```
更新bundle，非常慢，因为`Gemfile.lock`固定了gem源：
```
GEM
  remote: https://rubygems.org/
```
那么修改镜像：
```
bundle config mirror.https://rubygems.org https://gems.ruby-china.com
```
修改完镜像，升级bundle，中间需要输入密码
```
bundle update
```
升级完，运行`bundle exec jekyll serve`

### 安装Homebrew

> Homebrew是Mac OS 不可或缺的套件管理器 ---- Homebrew官方

Homebrew是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷。

#### Homebrew官方指定的安装方法

将以下命令粘贴到终端：
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
但这种方法并不适用国内的Mac用户，因为网络资源的原因，电脑下载是龟速，实在是无法忍受，不信你自己试试就知道了。

解决下载慢有两个办法：
1. 替换镜像源，将下载资源改为国内镜像资源即可（推荐）
2. 科学上网，通过全局代理来进行安装，也是解决网络问题的一种方法（不推荐）

#### 使用国内镜像资源
```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```
可以选择: 

1.中科大下载源，如图，然后根据提示输入开机密码，（这里需要提示下，输入密码的时候，光标是不移动的，保护机制，不用管，输入完直接回车键即可)

![iShot2020-12-13 12.04.11](https://i.loli.net/2020/12/13/67LYqH82kaWl9Ad.jpg)

### 本地运行bundle exec jekyll serve报错
本地运行`bundle exec jekyll serve`命令启动jekyll时，出现以下错误:
```
Could not find commonmarker-0.17.13 in any of the sources
```
并提示运行`bundle install`,执行后报错：
```
An error occurred while installing commonmarker (0.17.13), and Bundler cannot continue.
Make sure that `gem install commonmarker -v '0.17.13' --source 'https://rubygems.org/'` succeeds before bundling.

In Gemfile:
  github-pages was resolved to 192, which depends on
    jekyll-commonmark-ghpages was resolved to 0.1.5, which depends on
      jekyll-commonmark was resolved to 1.2.0, which depends on
        commonmarker
```
提示执行`gem install commonmarker -v '0.17.13' --source 'https://rubygems.org/'`,执行结果：
```
Building native extensions.  This could take a while...
ERROR:  Error installing commonmarker:
        ERROR: Failed to build gem native extension.

    current directory: /Library/Ruby/Gems/2.3.0/gems/commonmarker-0.17.13/ext/commonmarker
/System/Library/Frameworks/Ruby.framework/Versions/2.3/usr/bin/ruby -r ./siteconf20181112-6105-u9aca2.rb extconf.rb
creating Makefile

current directory: /Library/Ruby/Gems/2.3.0/gems/commonmarker-0.17.13/ext/commonmarker
make "DESTDIR=" clean

current directory: /Library/Ruby/Gems/2.3.0/gems/commonmarker-0.17.13/ext/commonmarker
make "DESTDIR="
make: *** No rule to make target `/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.13.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.3/usr/include/ruby-2.3.0/universal-darwin16/ruby/config.h', needed by `arena.o'.  Stop.

make failed, exit code 2

Gem files will remain installed in /Library/Ruby/Gems/2.3.0/gems/commonmarker-0.17.13 for inspection.
Results logged to /Library/Ruby/Gems/2.3.0/extensions/universal-darwin-16/2.3.0/commonmarker-0.17.13/gem_make.out
```
看报错信息可能是由于系统ruby环境和jekyll之间的一些分歧造成的，最简单的解决方法是创建一个新的环境。使用rvm来管理ruby版本，以避免删除系统ruby并破坏您的操作系统。
1. RVM是一个命令行工具，它允许轻松地安装、管理和使用从解释器到多个ruby环境。
2. 使用Ruby原因：
    * 虽然 macOS 自带了一个 ruby 环境，但是是系统自己使用的，所以权限很小，只有 system。而/Library目录是root权限，所以很多会提示无权限。
    * 使用自带ruby更新,管理不方便
    * 一系列无原因的报错

**安装RVM**
1. 下载并安装: `curl -L https://get.rvm.io | bash -s stable`
2. 载入RVM环境: `source ~/.rvm/scripts/rvm`
3. 查看RVM版本: `rvm -v`
4. 更新RVM版本: `rvm get stable`

**RVM安装Ruby环境**
1. 列出已知的Ruby版本: `rvm list known`
2. 查看当前Ruby版本: `ruby -v`
3. 安装Ruby版本: `rvm install 2.7.0`
4. 将指定版本设置为系统默认版本: `rvm use 2.7.0 --default`
5. 查看Ruby版本: `ruby -v`

**安装完成之后更新jekyll环境**
1. 安装bundler: `gem install bundler`
2. 安装jekyll: `gem install jekyll`
3. 安装项目依赖的所有gem包: `bundle install`

升级完，运行`bundle exec jekyll serve`

### 更换评论系统

奈何基于github的gitalk评论系统经常报错404/403等，极其不稳定，故考虑将其换掉。新的评论系统需要满足以下几点：

1.对国内用户友好，不需要科学上网。

2.不需要跳转至第三方登录，满足方便，如果基于github，那么想评论就必须要有github账户。

3.色彩简单与博客主题相适配，简单优雅。

经过一番查找，最终选择了[Valine](https://valine.js.org)，该评论系统基于[LeanCloud](https://leancloud.cn)，并且支持Jekyll。参考了[这篇文章](https://www.codepeople.cn/2019/01/03/Jkeyll-Valine/)，经过约10分钟操作，大功告成。来吧，展示：

![评论功能图片](https://raw.githubusercontent.com/AladengodmanVicky/Figurebed/master/jekyll_blog_comment.png)


## 更新日志
* 创建时间：2018-2-27
* 更新时间：2020-12-13
