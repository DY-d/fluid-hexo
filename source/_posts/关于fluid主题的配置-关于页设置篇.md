---
title: 关于fluid主题的配置-关于页设置篇
date: 2023-08-20 12:23:01
index_img: /img/page/fluid_about/home.png
excerpt: 关于如何使用Hexo博客系统的Fluid主题，包括关于页设置。Fluid：一款 Material Design 风格的主题。
tags: [Fluid, 使用教程, Hexo]
categories: 
  - [Hexo, Theme]
  - [Fluid]
---

> 关于如何使用Hexo博客系统的Fluid主题，包括关于页设置。Fluid：一款 Material Design 风格的主题。

## 关于页

### 创建关于页

首次使用主题的「关于页」需要手动创建：

```sh
$ hexo new page about
```

创建成功后修改 `/source/about/index.md`，添加 `layout` 属性。

修改后的文件示例如下：

```yaml
---
title: 标题
layout: about
---

这里可以写正文，支持 Markdown, HTML
```

{% note warning %}

**<font color='ff9933'>WARNING</font>**

`layout: about` 必须存在，并且不能修改成其他值，否则不会显示头像等样式。

{% endnote %}



### 关于信息

在关于页介绍自己的基础信息，可以在**_config.fluid.yml**中设置：

```yaml
about:
  avatar: /img/avatar.png
  name: "Fluid"
  intro: "An elegant theme for Hexo"
```

