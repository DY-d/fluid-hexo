---
title: 关于fluid主题的配置-全局设置篇
date: 2023-08-20 00:28:54
index_img: /img/page/fluid_about/home.png
excerpt: 关于如何使用Hexo博客系统的Fluid主题，包括全局设置。Fluid：一款 Material Design 风格的主题。
tags: [Fluid, 使用教程, Hexo]
categories: 
  - [Hexo, Theme]
  - [Fluid]
---

> 关于如何使用Hexo博客系统的Fluid主题，包括全局设置。Fluid：一款 Material Design 风格的主题。

## 全局设置

### 页面顶部大图

每个页面都会有个 `banner_img` 属性，可以使用本地图片的相对路径，也可以使用外站链接。

图片都是放在网站文件夹下的 `source` 文件夹下，并且路径写法为：

```yaml
banner_img: /img/bg/index.jpg 		# 对应的本地路径是 /source/img/bg/index.jpg
```

{% note warning %}

**TIP**

如果是本地图片，目录文件夹可自定义，但必须在 source 目录下，博客与主题的 source 目录最终会合并，因此优先选择博客的 source。

图片大小建议压缩到 1MB 以内，否则会严重拖慢页面加载

{% endnote %}



### 博客标题

页面左上角的博客标题，默认使用  **_config.yml** 中的 `title` , 并且这个配置同时控制网站标签页名称。

如需单独设置左上角的名称，可以到  **_config.fluid.yml**  中设置：

```yaml
navbar:
	blog_title: 博客标题
```



### 导航菜单

```yaml
navbar:
  menu:
    - { key: 'home', link: '/', icon: 'iconfont icon-home-fill' }
    - { key: 'tag', link: '/tags/', icon: 'iconfont icon-tags-fill' }
    - { key: 'about', link: '/about/', icon: 'iconfont icon-user-fill', name: '联系我' }
```

- `  key `：菜单名称
- `link`：跳转的链接
- `icon`：图标的css class，可以省略（即没有图标），主题内置图标访问[<font color='#3eaf7c'>这里</font>](https://hexo.fluid-dev.com/docs/icon/#内置社交图标)

另外支持二级菜单（下拉菜单），配置写法如下：

```yaml
menu:
  - {
      key: '文档',
      icon: 'iconfont icon-books',
      submenu: [
        { key: '主题博客', link: 'https://hexo.fluid-dev.com/' },
        { key: '配置指南', link: 'https://hexo.fluid-dev.com/docs/guide/' },
        { key: '图标用法', link: 'https://hexo.fluid-dev.com/docs/icon/' }
      ]
  }
#
```



### 全局字体

所有页面的字体统一在 **_config.fluid.yml**  中的配置项配置：

```yaml
font:  					       # 主题字体配置
  font_size: 16px             # 全局字号
  font_family: PingFang SC    # 全局字体族
  code_font_size: 85%         # 代码的字号
```

如果想设置单独的页面，可以直接在 markdown 里通过 style 标签实现：

```html
---
title: example
---

<style>
  /* 设置整个页面的字体 */
  html, body, .markdown-body {
    font-family: KaiTi,"Microsoft YaHei",Georgia, sans, serif;
    font-size: 15px;
  }

  /* 只设置 markdown 字体 */
  .markdown-body {
    font-family: KaiTi,"Microsoft YaHei",Georgia, sans, serif;
    font-size: 15px;
  }
</style>
```

{% note success %}

更详细的配置请访问：https://hexo.fluid-dev.com/docs/guide/

{% endnote %}

