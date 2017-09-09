---
title: HEXO建站-基本设置 
tags: hexo
grammar_cjkRuby: true
password: 
categories: hexo
---
<hr>

## 前言

本文主要围绕两部分进行介绍：

*   1、HEXO的基本命令与基本目录结构
*   2、HEXO网站的配置文件与基本配置

## HEXO的基本命令与基本目录结构
![enter description here][1]
<!--more-->
基本目录结构

**主目录**

``` stylus
├── .deploy       #需要部署的文件
├── node_modules  #Hexo插件
├── public        #生成的静态网页文件
├── scaffolds     #模板
├── source        #博客正文和其他源文件, 404 favicon CNAME 等都应该放在这里
|   ├── _drafts   #草稿
|   └── _posts    #文章
├── themes        #主题
├── _config.yml   #全局配置文件
└── package.json

```
**主题目录**

``` stylus
├── languages          #国际化
|   ├── default.yml    #默认
|   └── zh-CN.yml      #中文
├── layout             #布局
|   ├── _partial       #局部的布局
|   └── _widget        #小挂件的布局
├── script             #js脚本
├── source             #源代码文件
|   ├── css            #CSS
|   |   ├── _base      #基础CSS
|   |   ├── _partial   #局部CSS
|   |   ├── fonts      #字体
|   |   ├── images     #图片
|   |   └── style.styl #style.css
|   ├── fancybox       #fancybox
|   └── js             #js
├── _config.yml        #主题配置文件
└── README.md          #主题介绍
```
以上目录，并不一一介绍，我们主要了解其中主要的部分：
主目录常用部分：
scaffolds
source
themes
config.yml
主题目录：
看需要，日常操作都会涉及到：但主要的还是config.yml、languages等。
接下来，我们继续根据目录介绍涉及的部分，站点配置部分更多涉及主题目录的配置。

### HEXO的基本命令

每次部署的步骤，可按以下三步来进行。

``` stylus
hexo clean      #清除PUBLIC和编译文件

hexo generate   #编译网站目录

hexo deploy     #同步到GIT 或者CODING

npm install <plugin-name> --save #安装

npm update #升级

npm uninstall <plugin-name> #卸载
```
一些常用命令：

hexo new”postName” #新建文章 #存放在主目录的source下的POST目录下

hexo new page”pageName” #新建页面

hexo generate #生成静态页面至public目录

hexo server #开启预览访问端口（默认端口4000，’ctrl + c’关闭server）

hexo deploy #将.deploy目录部署到GitHub

hexo help # 查看帮助

hexo version #查看Hexo的版本

## HEXO网站配置文件与基本配置

### HEXO网站的配置文件

1.  在根目录下的_config.yml主要是对网站的总属性进行设置
    如：网站标题，网站logo,网站插件使用等全局的属性
2.  主题目录下的_config.yml主要是针对网站的布局，导航等特性设置进行设置

    ### 基本配置

    **主配置文件介绍**
	
	


``` stylus
主配置文件
<pre># Site #站点信息
title: lmintlcx #标题
subtitle: 做人不卖萌跟咸鱼有什么区别 #副标题
description: lmintlcx lm lcx blog #描述
author: lmintlcx #作者
language: zh-Hans #语言
timezone: Asia/Shanghai #时区

# URL #链接格式
url: http://joryhe.coding.me/ #网址
root: / #根目录
permalink: post/:title.html #文章的链接格式
permalink_defaults:

# Directory #目录
source_dir: source #源文件
public_dir: public #生成的网页文件
tag_dir: tags #标签
archive_dir: archives #归档
category_dir: categories #分类
code_dir: downloads/code
i18n_dir: :lang #国际化
skip_render:

# Writing #写作
new_post_name: :title.md #新文章标题
default_layout: post #默认模板
titlecase: false #标题转换成大写
external_link: true #新标签页里打开连接
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight: #语法高亮
  enable: true
  line_number: false #显示行号
  auto_detect: true
  tab_replace:

# Category & Tag #分类和标签
default_category: uncategorized #默认分类
category_map:
tag_map:

# Date / Time format #日期时间格式
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination #分页
per_page: 20 #每页文章数, 设置成 0 禁用分页
pagination_dir: page

# Extensions #插件和主题
## 插件: http://hexo.io/plugins/
## 主题: http://hexo.io/themes/
theme: next

# Deployment #部署, joryhe是我的用户名, 同时发布GitHub 
deploy:
  type: git
  repo: 
    github: github: git@github.com:joryhe/joryhe.github.io.git,master

# Disqus #Disqus评论系统
disqus_shortname: 

plugins: #插件，例如生成 RSS 和站点地图的
- hexo-generator-feed
- hexo-generator-sitemap</pre>

```
### **主题配置文件**

``` stylus
menu: #菜单
  home: / #首页
  archives: /archives #归档
  about: /about #关于
  #commonweal: /404.html #公益404
  #tags: /tags #标签
  #categories: /categories #分类
## 经典介绍配置
# 小图标
favicon: /favicon.ico

# 默认关键词
keywords: 

# 留空使用默认的, false 禁用, 也可以写指定的地址
rss:

# Icon fonts
# default | linecons | fifty-shades | feather
icon_font: default

# 代码高亮主题 https://github.com/chriskempson/tomorrow-theme
# normal | night | night eighties | night blue | night bright
highlight_theme: normal

# MathJax Support #数学公式
mathjax: true

# Schemes #启用主题中的主题Mist
scheme: Mist

# 侧边栏
#  - post    只在文章页面显示
#  - always  所有页面显示
#  - hide    隐藏
sidebar: always

# 自动滚动到"阅读更多"标记的下面
scroll_to_more: true

# 自动给目录添加序号
toc_list_number: true

# 自动截取摘要
auto_excerpt:
  enable: false
  length: 150

# Lato 字体
use_font_lato: true

# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: false
  user_id: 0
  #admin_nickname: ROOT

## DO NOT EDIT THE FOLLOWING SETTINGS
## UNLESS YOU KNOW WHAT YOU ARE DOING

# 动画
use_motion: true

# Fancybox 看图插件
fancybox: true

# Static files
vendors: vendors
css: css
js: js
images: images

# Theme version
version: 0.4.5.1
```
#### 添加小图标

将 favicon.ico 文件放在 source 目录下, 修改主题配置文件

``` stylus
favicon: /favicon.ico
```
#### 语言设置 
**主要语言代码：** English (en) 中文简体 (zh-Hans) French (fr-FR) 正体中文 (zh-hk/zh-tw) Russian (ru) German (de) **站点配置文件下定义语言：**

``` stylus
language: zh-hk
```
#### 菜单导航栏设置

配置在主题配置文件下

``` stylus
menu:
  home: /
  archives: /archives
  categories: /categories
  tags: /tags
  commonweal: /404.html
  about: /about
```
#### 新增标签页

使用命令hexp new page “tags” 并将页面类型设置为tags

``` stylus
title: tags
date: 2016-04-19 22:37:08
type: "tags"
---
```
通常情况下你的标签页并不需要评论框，取消评论代码

``` stylus
title: tags
date: 2016-04-19 22:37:08
type: "tags"
comments: false
---
```
在主题配置文件下的菜单设置项memu下设置，设置完成在主页导航可以看到标签导航栏

``` stylus
menu:
  categories: /categories
```
#### 关于自己颜面about

hexo new page “about”新增about页面
编辑source/about/index.md:
添加菜单导航，在主题配置文件

``` stylus
menu:
  about: /about
```
#### RSS设置

NPM install hexo-generator-feed安装RSS插件
编辑主题配置文件 rss 字段

``` stylus
rss: true
```
正常情况下，会在你的网站根目录下生成atom.xml

#### 侧栏设置

post - 默认行为, 在文章页面(拥有目录列表)时显示
always - 在所有页面中都显示
hide - 在所有页面中都隐藏(可以手动展开)。

``` stylus
sidebar: post
```
#### 头像设置 编辑站点配置文件, 新增字段 avatar

``` stylus

avatar: /images/xxx.jpg
```
#### 作者名称

编辑站点配置文件的author

站点描述设置

编辑站点配置文件的description

#### 侧边栏社交链接

站点配置文件新增字段 social, 然后添加社交站点名称与地址

``` stylus
# Social links
social:
  GitHub: https://github.com/lmintlcx
  Twitter: https://twitter.com/lmintlcx
  Zhihu: http://www.zhihu.com/people/lmintlcx
  Douban: http://www.douban.com/people/lmintlcx
  #Weibo: http://weibo.com/lmlcx
```
#### 腾讯公益 404 页面

source 目录下新建 404.html 页面

``` stylus
<!DOCTYPE HTML>
<html>
<head>
  <meta http-equiv="content-type" content="text/html;charset=utf-8;"/>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="robots" content="all" />
  <meta name="robots" content="index,follow"/>
</head>
<body>
<script type="text/javascript" src="http://www.qq.com/404/search_children.js" charset="utf-8" homePageUrl="your-site-url" homePageName="回到我的主页"></script>
</body>
</html>
```
#### 文章摘录

NexT 支持三种方式来控制首页文章的显示方式
1.在文章中使用 手动进行截断
2.在文章的 front-matter 中添加 description, 内容为文章摘要
3.自动形成摘要, 在主题配置文件中添加


``` stylus
auto_excerpt:
  enable: true
  length: 150 #默认截取的长度为 150 字符

```
#### 设定首页/归档/标签页面文章的篇数

安装以下插件

``` stylus
hexo-generator-index
hexo-generator-archive
hexo-generator-tag
```
站点配置文章中设定

``` stylus
index_generator:
  per_page: 5

archive_generator:
  per_page: 20
  yearly: true
  monthly: true

tag_generator:
  per_page: 10
```


  [1]: https://www.github.com/liyehuicn/liyehui/raw/master/img/1504928376915.jpg