---
title: 关于fluid主题的配置-自定义页设置篇
date: 2023-08-20 15:15:24
index_img: /img/page/fluid_about/home.png
excerpt: 关于如何使用Hexo博客系统的Fluid主题，包括自定义页设置。Fluid：一款 Material Design 风格的主题。
tags: [Fluid, 使用教程, Hexo]
categories: 
  - [Hexo, Theme]
  - [Fluid]
---

> 关于如何使用Hexo博客系统的Fluid主题，包括自定义页设置。Fluid：一款 Material Design 风格的主题。

## 自定义页面

### 创建页面

如果想单独生成一个页面，步骤和创建「关于页」类似。

1. 首先用命令行创建页面：

```sh
$ hexo new page example
```

2. 创建成功后编辑博客目录下 `/source/example/index.md`：

```yaml
---
title: example
subtitle: 若不填默认是 title
---

这里写正文，支持 Markdown, HTML
```

正文默认没有 Markdown 样式，如果希望和文章相同的样式，可以加上：

```html
<div class="markdown-body">
正文
</div>
```

### 配置

页面的参数配置可以在**_config.fluid.yml**中统一设置：

```yaml
page:
  banner_img: /img/default.png
  banner_img_height: 70
  banner_mask_alpha: 0.3
```

也可以直接在 [<font color='#3eaf7c'>Front-matter</font>](https://hexo.io/zh-cn/docs/front-matter)里单独设置：

```yaml
---
title: example
banner_img: /img/default.png
banner_img_height: 60
banner_mask_alpha: 0.5
---

这里可以写正文
```

### 评论

自定义页面也可以开启评论插件，和关于页的方式相同，通过在 [<font color='#3eaf7c'>Front-matter</font>](https://hexo.io/zh-cn/docs/front-matter)设置 `comment: bool` 来控制评论开关，或者通过 `comment: 'type'` 来开启指定的评论插件：

```yaml
---
title: example
comment: 'valine'
---
```
