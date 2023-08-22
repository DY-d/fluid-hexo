---
title: 关于fluid主题的配置-友情链接页设置篇
date: 2023-08-20 15:09:47
index_img: /img/page/fluid_about/home.png
excerpt: 关于如何使用Hexo博客系统的Fluid主题，包括友情链接页设置。Fluid：一款 Material Design 风格的主题。
tags: [Fluid, 使用教程, Hexo]
categories: 
  - [Hexo, Theme]
  - [Fluid]
---

> 关于如何使用Hexo博客系统的Fluid主题，包括友情链接页设置。Fluid：一款 Material Design 风格的主题。

## 友情链接页

友情链接页用于展示好友的博客入口，默认关闭，开启需要先在 `navbar` 项中将 `links` 的注释(#号)删掉：

```yaml
navbar:
  menu:
    - { key: 'links', link: '/links/', icon: 'iconfont icon-link-fill' }
```

然后找到 `links` 的配置项，对页面内容进行配置：

```yaml
links:
  items:
    - {
      title: 'Fluid Docs',
      intro: '主题使用指南',
      link: 'https://hexo.fluid-dev.com/docs/',
      avatar: '/img/favicon.png'
    }
  default_avatar: /img/avatar.png
```

- `title`: 友链站的标题
- `intro`: 站点或博主的简介，可省略
- `link`: 跳转链接
- `avatar`: 头像图片，可省略
- `default_avatar`: 成员的默认头像（仅在指定了头像并且加载失败时生效）

友链页也可以使用自定义区域和评论，使用方式类似于文章页，具体见配置项与相关注释。
