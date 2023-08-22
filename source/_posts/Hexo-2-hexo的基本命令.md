---
title: Hexo-2-hexo的基本命令
date: 2023-08-19 17:28:54
index_img: /img/page/hexo_about/home.jpg
excerpt: 本文章主要叙述如何使用Hexo的命令来生成文章、建站、生成静态文件、本地预览、发布等。
tags: [使用教程, Hexo]
categories: 
  - [Hexo]
---

> 主要叙述如何使用Hexo的命令来生成文章、建站、生成静态文件、本地预览、发布等。

## 基本命令

### init

```sh
$ mkdir myblog
$ cd myblog
$ npx hexo init
```

新建一个网站。



### new

改命令主要用于新建一篇文章，生成关于页以及自定义页面。

```sh
$ npx hexo new "文章标题" # 生成文章
-------------------------------
$ hexo new page about # 生成关于页
-------------------------------
$ hexo new page example # 生成自定义页面
```



## generate

```sh
$ hexo generate
```

生成静态文件。



## server

```sh
$ hexo server
```

启动服务器。默认情况下，访问网址为： `http://localhost:4000/`。



## clean

```sh
$ hexo clean
```

清除缓存文件 (`db.json`) 和已生成的静态文件 (`public`)。

在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。



## deploy

```sh
$ hexo deploy
```

部署网站。
