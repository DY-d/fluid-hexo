---
title: 关于fluid主题的配置-首页设置篇
date: 2023-08-20 00:41:07
index_img: /img/page/fluid_about/home.png
excerpt: 关于如何使用Hexo博客系统的Fluid主题，包括首页设置。Fluid：一款 Material Design 风格的主题。
tags: [Fluid, 使用教程, Hexo]
categories: 
  - [Hexo, Theme]
  - [Fluid]
---

> 关于如何使用Hexo博客系统的Fluid主题，包括首页设置。Fluid：一款 Material Design 风格的主题。

## 首页

### 打字机效果

首页大图的打字机效果可以在 **_config.fluid.yml**  中设置：

```yaml
index:
  slogan:
    enable: true
    text: 这是一条 Slogan
    api:
      enable: false
      url: "https://v1.hitokoto.cn/"
      method: "GET"
      headers: {}
      keys: ["hitokoto"]
```

如果 `text` 为空，则按 **_config.yml** 中的 `subtitle` 显示。

{% note warning %}

**TIP**

请求API的功能必须同时开启打字机效果才行。

{% endnote %}



### 文章摘要

开关自动摘要（默认开启）：

```yaml
index:
  auto_excerpt:
    enable: true
```

若要手动指定摘要，使用 `<!-- more -->` MD文档里划分，如：

```md
正文的一部分作为摘要
<!-- more -->
余下的正文
```

或者在 [<font color='#3eaf7c'>Front-matter </font>](https://hexo.io/zh-cn/docs/front-matter) 里面设置 `excerpt` 字段，如：

```yaml
---
title: 这是标题
excerpt: 这是摘要
---
```

{% note success %}

**TIP**

优先级: 手动摘要 > 自动摘要

如果关闭自动摘要，并且没有设置手动摘要，摘要区域空白

无论哪种摘要都最多显示 3 行，当屏幕宽度不足时会隐藏部分摘要。

{% endnote %}



### 文章跳转方式

```yaml
index:
	post_url_target: _self
```

可选值：

1. `_blank:` 新标签页打开
2. `_self`: 当前页打开

