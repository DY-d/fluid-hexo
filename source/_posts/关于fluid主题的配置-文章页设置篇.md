---
title: 关于fluid主题的配置-文章页设置篇
date: 2023-08-20 00:50:12
index_img: /img/page/fluid_about/home.png
excerpt: 关于如何使用Hexo博客系统的Fluid主题，包括文章页设置。Fluid：一款 Material Design 风格的主题。
tags: [Fluid, 使用教程, Hexo]
categories: 
  - [Hexo, Theme]
  - [Fluid]
---

> 关于如何使用Hexo博客系统的Fluid主题，包括文章页设置。Fluid：一款 Material Design 风格的主题。

## 文章页

### 文章在首页封面图

对于单篇文章，在文章开头 [<font color='#3eaf7c'>Front-matter </font> ](https://hexo.io/zh-cn/docs/front-matter)中配置 `index_img` 属性。

```yaml
---
title: 文章标题
tags: [Hexo, Fluid]
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
---
以下是文章内容
```

和 Banner 配置相同，`/img/example.jpg` 对应的是存放在 `/source/img/example.jpg` 目录下的图片（目录也可自定义，但必须在 source 目录下）。

也可以使用外链 Url 的绝对路径。

如果想统一给文章设置一个默认图片（文章不设置 `index_img` 则默认使用这张图片），可在**_config.yml**中设置：

```yaml
post:
  default_index_img: /img/example.jpg
```

当 `default_index_img` 和 `index_img` 都为空时，该文章在首页将不显示图片。



### 文章页顶部大图

默认显示**主题配置**中的 `post.banner_img`，如需要设置单个文章的 Banner，在 [<font color='#3eaf7c'>Front-matter </font> ](https://hexo.io/zh-cn/docs/front-matter)中指定 `banner_img` 属性。

本地图片存放位置同上。

```yaml
---
title: 文章标题
tags: [Hexo, Fluid]
index_img: /img/example.jpg
banner_img: /img/post_banner.jpg
date: 2019-10-10 10:00:00
---
以下是文章内容
```



### 代码块

```yaml
code:
  copy_btn: true
  highlight:
    enable: true
    line_number: true
    lib: "highlightjs"
    highlightjs:
      style: 'Github Gist'
      bg_color: false
    prismjs:
      style: "default"
      preprocess: true
```

`copy_btn`: 是否开启复制代码的按钮

`line_number`: 是否开启行号

`highlight`: 是否开启代码高亮

`lib`: 选择生成高亮的库，可选项: highlightjs、prismjs，对应下面两组配置，高亮的配置说明具体见**_config.yml**中的注释



### 评论

开启评论需要在**_config.fluid.yml**中开启并指定评论模块：

```yaml
post:
  comments:
    enable: true
    type: waline
```

然后在下方还要设置对应评论模块的参数，比如 waline 对应设置：

```yaml
waline:
  serverURL: 
  path: window.location.pathname
  meta: ['nick', 'mail', 'link']
  requiredMeta: ['nick']
  lang: 'zh-CN'
  emoji: ['https://cdn.jsdelivr.net/gh/walinejs/emojis/weibo','https://unpkg.com/@waline/emojis@1.2.0/bilibili', 'https://unpkg.com/@waline/emojis@1.2.0/tw-emoji']
  dark: 'html[data-user-color-scheme="dark"]'
  wordLimit: 0
  pageSize: 10
  reaction: true
```

当前支持的评论插件如下：

- [<font color='#3eaf7c'>Valine </font>](https://valine.js.org/configuration.html):基于 LeanCloud
- [<font color='#3eaf7c'>Waline </font>](https://waline.js.org/): 从 Valine 衍生而来，额外增加了服务端和多种功能
- [<font color='#3eaf7c'>Gitalk </font>](https://github.com/gitalk/gitalk): 基于 GitHub Issues
- [<font color='#3eaf7c'>Utterances</font>](https://utteranc.es/): 基于 GitHub Issues
- [<font color='#3eaf7c'>Disqus</font>](https://disqus.com/): 基于第三方的服务
- [<font color='#3eaf7c'>畅言</font>](http://changyan.kuaizhan.com/): 基于第三方的服务
- [<font color='#3eaf7c'>来必力(Livere)</font>](https://www.livere.com/): 基于第三方的服务
- [<font color='#3eaf7c'>Remark42</font>](https://remark42.com/): 需要自托管服务端
- [<font color='#3eaf7c'>Twikoo</font>](https://twikoo.js.org/): 基于腾讯云开发
- [<font color='#3eaf7c'>Cusdis</font>](https://cusdis.com/): 基于第三方服务或自托管服务
- [<font color='#3eaf7c'>Giscus</font>](https://giscus.app/zh-CN): 基于 GitHub Discussion

{% note success %}

关于本博客使用的waline评论系统请查看另一篇博客 {% post_link Waline-1-在个人博客中配置Waline评论插件 **Waline-1-在个人博客中配置Waline评论插件** %} 

{% endnote %}



### 脚注

主题内置了脚注语法支持，可以在文章末尾自动生成带有锚点的脚注，该功能在**_config.fluid.yml**中默认开启：

```yaml
post:
  footnote:
    enable: true
    header: ''
```

脚注语法如下：

```md
这是一句话[^1]
[^1]: 这是对应的脚注
```



### Tag 插件

#### 便签

在 markdown 中加入如下的代码来使用便签：

```md
{% note success %}
文字 或者 `markdown` 均可
{% endnote %}
```

可选标签：

{% note success %}

success

{% endnote %}

{% note primary %}

primary

{% endnote %}

{% note warning %}

warning

{% endnote %}

{% note secondary %}

secondary

{% endnote %}

{% note danger %}

danger

{% endnote %}

{% note light %}

light

{% endnote %}

{% note info %}

info

{% endnote %}

{% note warning %}

**<font color='ff9933'>WARNING</font>**

使用时 `{% note primary %}` 和 `{% endnote %}` 需单独一行，否则会出现问题

{% endnote %}



