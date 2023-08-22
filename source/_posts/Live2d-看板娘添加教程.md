---
title: Live2d-看板娘添加教程
date: 2023-08-21 21:59:30
index_img: /img/page/live2d_about/home.png
excerpt: “看板娘”，简而言之就是小店的女服务生，也有“吸引顾客，招揽生意，提高人气”等作用类似品牌形象代言人的含义。而网页中的看板娘，所用的技术是live2D。
tags: [Web前端,Live2d]
categories:
  - [Hexo, Live2d]
  - [Web前端, Live2d]
---

> “看板娘”，简而言之就是小店的女服务生，也有“吸引顾客，招揽生意，提高人气”等作用类似品牌形象代言人的含义。而网页中的看板娘，所用的技术是live2D。live2d并不是一种先进的技术，它产生的效果，都是用基本的平移、旋转、透明、曲面变形等操作实现的。最终的效果与贴图关系很大，而每一个动作，都需要制作师的精细调整。



## 安装 hexo-helper-live2d

{% note success %}

官方链接：[<font color='#3eaf7c'>hexo-helper-live2d官网</font>](https://github.com/EYHN/hexo-helper-live2d/blob/HEAD/README.zh-CN.md)

{% endnote %}

cd到 `博客目录`，然后输入下面命令下载：

```sh
$ npm install --save hexo-helper-live2d
```



## 挑选模型

### chitose

![](/img/page/2023/08/21/live2d/chitose.png)

### epsilon2_1

![](/img/page/2023/08/21/live2d/epsilon2_1.png)

### gf

![](/img/page/2023/08/21/live2d/gf.png)

### haru/01

![](/img/page/2023/08/21/live2d/haru_01.png)

### haru/02

![](/img/page/2023/08/21/live2d/haru_02.png)

### haruto

![](/img/page/2023/08/21/live2d/haruto.png)

### hibiki

![](/img/page/2023/08/21/live2d/hibiki.png)

### hijiki

![](/img/page/2023/08/21/live2d/hijiki.png)

### izumi

![](/img/page/2023/08/21/live2d/izumi.png)

### koharu

![](/img/page/2023/08/21/live2d/koharu.png)

### miku

![](/img/page/2023/08/21/live2d/miku.png)

### nico

![](/img/page/2023/08/21/live2d/nico.png)

### nietzsche

![](/img/page/2023/08/21/live2d/nietzsche.png)

### ni-j

![](/img/page/2023/08/21/live2d/ni-j.png)

### nipsilon

![](/img/page/2023/08/21/live2d/nipsilon.png)

### nito

![](/img/page/2023/08/21/live2d/nito.png)

### shizuku

![](/img/page/2023/08/21/live2d/shizuku.png)

### tororo

![](/img/page/2023/08/21/live2d/tororo.png)

### tsumiki

![](/img/page/2023/08/21/live2d/tsumiki.png)

### unitychan

![](/img/page/2023/08/21/live2d/unitychan.png)

### wanko

![](/img/page/2023/08/21/live2d/wanko.png)

### z16

![](/img/page/2023/08/21/live2d/z16.png)



## 模型下载

### 命令行下载

选好上面模型之后记下名字，依然在 `博客目录` 下输入下面命令：

```sh
$ npm install --save live2d-widget-model-模型名字
```

此时 `博客目录`\node_modules\目录下会出现你刚才下载的模块。



### github下载

> 除了命令行下载之外，还可以去github找各种各样的模型，推荐[<font color='#3eaf7c'>这里</font>](https://github.com/summerscar/live2dDemo)。

从GitHub上下载下来模型的文件夹之后可以按照下面的方法使用模型：

1. 在您博客根目录下创建一个 `live2d_models` 文件夹.
2. 在此文件夹内新建一个子文件夹.
3. 将你的 Live2D 模型复制到这个子文件夹中.
4. 将子文件夹的名称输入 `_config.yml` 的 `model.use` 中.

**更详细的使用方法请访问** [<font color='#3eaf7c'>hexo-helper-live2d官网</font>](https://github.com/EYHN/hexo-helper-live2d/blob/HEAD/README.zh-CN.md)



{% note warning %}

**TIP**

下载的模型需要区分是moc格式的，还是moc3格式的。moc3格式的模型请看这篇文章 {% post_link Git连接远程GitHub配置 **Live2d-moc3模型的看板娘加载方式** %}

{% endnote %}



## 配置

当我们做好上述步骤之后，就需要到 `_config.yml` 中进行配置：

```yaml
# Live2D
## https://github.com/EYHN/hexo-helper-live2d
live2d:
  enable: true
  # enable: false
  scriptFrom: local # 默认
  pluginRootPath: live2dw/ # 插件在站点上的根目录(相对路径)
  pluginJsPath: lib/ # 脚本文件相对与插件根目录路径
  pluginModelPath: assets/ # 模型文件相对与插件根目录路径
  # scriptFrom: jsdelivr # jsdelivr CDN
  # scriptFrom: unpkg # unpkg CDN
  # scriptFrom: https://cdn.jsdelivr.net/npm/live2d-widget@3.x/lib/L2Dwidget.min.js # 你的自定义 url
  tagMode: false # 标签模式, 是否仅替换 live2d tag标签而非插入到所有页面中
  debug: false # 调试, 是否在控制台输出日志
  model:
    use: lafei_4 # npm-module package name
  # use: wanko # 博客根目录/live2d_models/ 下的目录名
  # use: ./wives/wanko # 相对于博客根目录的路径
  # use: https://cdn.jsdelivr.net/npm/live2d-widget-model-wanko@1.0.5/assets/wanko.model.json # 你的自定义 url
    scale: 1
    hHeadPos: 0.5
    vHeadPos: 0.618
  display:
    superSample: 2
    width: 150
    height: 300
    position: left
    hOffset: 0
    vOffset: -20
  mobile:
    show: true
    scale: 0.5
  react:
    opacityDefault: 0.7
    opacityOnHover: 0.2
```



## haru

haru 和其他模型有些不同，haru包中包含 01 / 02 两个模型，在使用时模型名字为：

```yaml
model:
  use: live2d-widget-model-haru/01
```

或

```yaml
model:
  use: live2d-widget-model-haru/02
```

{% note warning %}

此时模型仍然无法正确加载，因为`hexo根目录`/node_modules/live2d-widget-model-haru/01/或02/ 中的json文件是空的，所以需要把`hexo根目录`/node_modules/live2d-widget-model-haru/中的json文件复制到01/或02/文件夹中。

{% endnote %}



## 测试

```sh
$ npx hexo clean
$ npx hexo s
```

