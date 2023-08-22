---
title: Hexo-1-搭建博客系统
index_img: /img/page/hexo_about/home.jpg
excerpt: 关于如何使用Hexo搭建自己的博客系统。
tags: [使用教程, Hexo]
categories: 
  - [Hexo]
---

> 建立个人博客的需求由来已久，能拥有自己的技术博客是广大程序员的梦想。相比于早些时候的WordPress、织梦等框架，就个人站点来说，用Hexo搭建博客可以用“怎一个爽字了得”形容。Hexo基于Node.js开发，具有轻量、方便、易部署等特点，主题丰富简约，依赖github即可构建站点，近些年受到广泛关注。此篇文章旨在和与我一样的初学者分享经验，有疑问欢迎在评论区交流。



## 前置条件

- `github账号`：需要申请一个属于你的github账号，可以在[<font color='#3eaf7c'>这里申请</font>](https://github.com/)。
- `git bash`： 需要有git bash运行环境，相关安装和使用教程请询问度娘。
- `Node.js`： 必须安装 Node.js 开发环境，建议参考[<font color='#3eaf7c'>node.js 安装</font>]()



## Hexo的安装，初始化和本地预览

### 安装Hexo

在shell命令窗口输入下面命令

```sh
$ mkdir my_hexo
$ cd my_hexo
$ npm install hexo
```

或者下面全局安装

```sh
$ npm install -g hexo-cli
```



### 建站

创建一个文件夹，并且输入建站命令，如下：

```sh
$ mkdir myBlog
$ cd myBlog
$ npx hexo init
```

新建完成后，指定文件夹的目录如下：

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

- `_config.yml`：站点配置文件。
- `source`：生成的文章在该文件下的 `_post` 文件夹中。个人博客网站的图片都存在改文件夹下。



### 本地预览

为了查看本地站点的实际效果，可以输入下面命令：

```sh
$ npx hexo server
```

会在本地搭建服务器挂载生成的本地站点，通过访问 [http://localhost:4000](http://localhost:4000/) 浏览自己的网站。



## Hexo部署到GitHub

### 创建GitHub仓库

仓库名必须为：<Github 账号>.github.io



### 安装 **hexo-deployer-git**

注意进入到**博客网站的文件下**输入下面命令：

```sh
$ npm install hexo-deployer-git --save
```



### 修改_config.yml

```yaml
deploy:
  type: git
  repo: <repository url> #使用SSH，不适用HTTPS的，例如git@github.com:youName/youName.github.io.git
  branch: [branch]
  message: [message]
  
----------------------------
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https:<Github账号>.github.io
root: /
```



### 推送到GitHub

```sh
$ npx hexo g
$ npx hexo d
```

当出现下面显示语句即为成功：

```sh
INFO  Deploy done: git
```

访问的域名为：`https://<Github账号>.github.io`。



{% note warning %}

如果出现下面访问git失败的情况，请看 {% post_link Git连接远程GitHub配置 **Git 连接远程 GitHub 配置** %}

```sh
fatal: 无法读取远程仓库。

请确认您有正确的访问权限并且仓库存在。
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
Error: Spawn failed
    at ChildProcess.<anonymous> (/Users/dengyang/Desktop/未命名文件夹 2/myblog/node_modules/hexo-util/lib/spawn.js:51:21)
    at ChildProcess.emit (node:events:513:28)
    at ChildProcess._handle.onexit (node:internal/child_process:291:12)
```

{% endnote %}
