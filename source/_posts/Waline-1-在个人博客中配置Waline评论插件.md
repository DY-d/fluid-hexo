---
title: Waline-1-在个人博客中配置Waline评论插件
date: 2023-08-20 18:38:24
index_img: /img/page/waline_about/home.png
excerpt: Waline是一款基于Valine衍生的简洁、安全的评论系统，本文主要记录如何在自己的博客系统中引入评论插件。
tags: [Web前端, 中间件, Waline]
categories: 
  - [中间件, Waline]
  - [Web前端, Waline]
  - [Hexo, Waline]
---

> Waline是一款基于Valine衍生的简洁、安全的评论系统，本文主要记录如何在自己的博客系统中引入改评论插件。

## 简介

Waline 是一款基于 Valine 衍生的简洁、安全的评论系统。

- 官网链接：https://waline.js.org/
- 相对于 Valine 有一些后天的优势：

| 优势         | 描述                                                    |
| ------------ | ------------------------------------------------------- |
| 自由评论     | 完全的 Markdown 支持，同时包含表情、数学公式、HTML 嵌入 |
| 轻量         | 54kB gzip 的完整客户端大小                              |
| 强大的安全性 | 内容校验、防灌水、保护敏感数据等                        |
| 登录支持     | 在允许匿名评论的基础上，支持账号注册，保持身份          |
| 完全免费部署 | 可免费部署在 Vercel 上                                  |
| 易于部署     | 多种部署部署方式和存储服务支持                          |



## LeanCloud 设置 (数据库)

1. [登录](https://console.leancloud.app/login) 或 [注册](https://console.leancloud.app/register) `LeanCloud 国际版` 并进入 [控制台](https://console.leancloud.app/apps)
2. 点击左上角 [创建应用](https://console.leancloud.app/apps) 并起一个你喜欢的名字 (请选择免费的开发版):

![](/img/page/2023/08/20/leancloud-1.png)

3. 进入应用，选择左下角的 `设置` > `应用 Key`。你可以看到你的 `APP ID`,`APP Key` 和 `Master Key`。请记录它们，以便后续使用。

![](/img/page/2023/08/20/leancloud-2.png)

{% note warning %}

**国内版需要完成备案接入**

如果你正在使用 Leancloud 国内版 ([leancloud.cnopen in new window](https://leancloud.cn/))，我们推荐你切换到国际版 ([leancloud.appopen in new window](https://leancloud.app/))。否则，你需要为应用额外绑定**已备案**的域名，同时购买独立 IP 并完成备案接入:

- 登录国内版并进入需要使用的应用
- 选择 `设置` > `域名绑定` > `API 访问域名` > `绑定新域名` > 输入域名 > `确定`。
- 按照页面上的提示按要求在 DNS 上完成 CNAME 解析。
- 购买独立 IP 并提交工单完成备案接入。(独立 IP 目前价格为 ￥ 50/个/月)

![](/img/page/2023/08/20/leancloud-3.png)

{% endnote %}



## Vercel 部署 (服务端)

<p align><a href="https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fwalinejs%2Fwaline%2Ftree%2Fmain%2Fexample"><img src="/img/page/2023/08/20/vercel-1.svg"></a></p>

1. 点击上方 `Deploy` 按钮，跳转至 Vercel 进行 Server 端部署。
2. 如果你未登录的话，Vercel 会让你注册或登录，请使用 GitHub 账户进行快捷登录。
3. 输入一个你喜欢的 Vercel 项目名称并点击 `Create` 继续:

![](/img/page/2023/08/20/vercel-2.png)

4. 此时 Vercel 会基于 Waline 模板帮助你新建并初始化仓库，仓库名为你之前输入的项目名。

![](/img/page/2023/08/20/vercel-3.png)

一两分钟后，满屏的烟花会庆祝你部署成功。此时点击 `Go to Dashboard` 可以跳转到应用的控制台。

![](/img/page/2023/08/20/vercel-4.png)

5. 点击顶部的 `Settings` - `Environment Variables` 进入环境变量配置页，并配置三个环境变量 `LEAN_ID`, `LEAN_KEY` 和 `LEAN_MASTER_KEY` 。它们的值分别对应上一步在 LeanCloud 中获得的 `APP ID`, `APP KEY`, `Master Key`。

![](/img/page/2023/08/20/vercel-5.png)

{% note warning %}

如果你使用 LeanCloud 国内版，请额外配置 `LEAN_SERVER` 环境变量，值为你绑定好的域名。

{% endnote %}

6. 环境变量配置完成之后点击顶部的 `Deployments` 点击顶部最新的一次部署右侧的 `Redeploy` 按钮进行重新部署。该步骤是为了让刚才设置的环境变量生效。

![](/img/page/2023/08/20/vercel-6.png)

7. 此时会跳转到 `Overview` 界面开始部署，等待片刻后 `STATUS` 会变成 `Ready`。此时请点击 `Visit` ，即可跳转到部署好的网站地址，此地址即为你的服务端地址。

![](/img/page/2023/08/20/vercel-7.png)



## 从HTML引入(客户端)

在你的网页中进行如下设置:

1. 使用 CDN 引入 Waline: `//cdn.jsdelivr.net/npm/@waline/client`。
2. 创建 `<script>` 标签使用 Waline() 函数初始化，并传入必要的 `el` 与 `serverURL` 选项。
   - `el` 选项是 Waline 渲染使用的元素，你可以设置一个字符串形式的 CSS 选择器或者一个 HTMLElement 对象。
   - `serverURL` 是服务端的地址，即上一步获取到的值。

```html
<head>
  ..
  <script src="//cdn.jsdelivr.net/npm/@waline/client"></script>
  ...
</head>
<body>
  ...
  <div id="waline"></div>
  <script>
    Waline({
      el: '#waline',
      serverURL: 'https://your-domain.vercel.app',
    });
  </script>
</body>
```

3. 评论服务此时就会在你的网站上成功运行 🎉。



## Fluid 主题引入(客户端)

1. 设置主题配置文件 `comments -> type` 值为 `waline`

```yaml
# 评论插件
# Comment plugin
comments:
	enable: true
	# 指定的插件，需要同时设置对应插件的必要参数
	# The specified plugin needs to set the necessary parameters at the same time
	# Options: utterances | disqus | gitalk | valine | waline | changyan | livere | remark42 | twikoo | cusdis
	type: waline

```

2. 配置 waline 相关信息

```yaml
# Waline
# 从 Valine 衍生而来，额外增加了服务端和多种功能
# Derived from Valine, with self-hosted service and new features
# See: https://waline.js.org/
waline:
  serverURL: 'path-to-your-server-url'
  placeholder: 遗憾莫过于难忘你的背影，却找不到你来过的痕迹 ...
  path: window.location.pathname
  avatar: retro
  meta: ['nick', 'mail', 'link']
  pageSize: 10
  lang: zh-CN
  highlight: true
  avatarCDN: ''
  avatarForce: false
  requiredFields: []
  emojiCDN:
  emojiMaps:
  anonymous:
```

{% note success %}

最重要的是填入之前得到的 **服务端地址** 到`serverURL` 中

{% endnote %}



## 评论管理 (管理端)

1. 部署完成后，请访问 `<serverURL>/ui/register` 进行注册。首个注册的人会被设定成管理员。
2. 管理员登陆后，即可看到评论管理界面。在这里可以修改、标记或删除评论。
3. 用户也通过评论框注册账号，登陆后会跳转到自己的档案页。

