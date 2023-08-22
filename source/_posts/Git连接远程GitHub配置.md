---
title: Git连接远程GitHub配置
date: 2023-08-20 17:45:01
index_img: /img/page/git_about/home.jpg
excerpt: 本文章主要记录Git使用期间出现访问GitHub仓库无权限的问题，成功解决后即可向仓库中推送代码。
tags: [工具,Git]
categories: 
  - [Git]
---

> 本文章主要记录Git使用期间出现访问GitHub仓库无权限的问题，成功解决后即可想仓库中推送代码。

## 准备工作

- 申请GitHub账号
- 了解基础的Git语法
- 本地搭建好Git运行环境



## 建立远程仓库

登录到自己的GitHub之后点击右上角的+号创建仓库。

![](/img/page/2023/08/20/createRepo.png)

输入相应信息即可。



## 配置SSH秘钥

### 现有问题

当我们输入下面命令时：

```sh
$ ssh -T git@github.com
```

会输出下面的信息：

```sh
git@github.com: Permission denied (publickey).
```

说明我们没有配置秘钥，无权访问仓库。



### 创建SSH秘钥

在shell窗口中输入下面命令：

```sh
$ ssh-keygen -t rsa -C "你的GitHub邮箱"
```

一直按回车即可：

```sh
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/dengyang/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/dengyang/.ssh/id_rsa
Your public key has been saved in /Users/dengyang/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:47soutsMxsyEnrHNpu8FaKgRyFuFPN0lIrfOU7sQCLg 779581791@qq.com
The key's randomart image is:
+---[RSA 3072]----+
|....o+....       |
|+ .+=.o..        |
|oo o.o .         |
|Eo+ o o .        |
|+=.. = .S        |
|+** . o...       |
|.+*+ . ..        |
| .o+o  . .       |
| .**o.. o.       |
+----[SHA256]-----+
```

出现上面信息即为成功。我们需要到/Users/dengyang/.ssh/id_rsa.pub这个文件中复制出秘钥。



### 配置GitHub

到用户界面的setting中，选择 SSH and GPG keys，然后选择 new SSH key，填入相应信息即可。

![](/img/page/2023/08/20/setGitHubSSL.png)



### 测试

再次输入下面命令：

```sh
$ ssh -T git@github.com 
```

出现下面信息即为成功：

```sh
Hi DY-d! You've successfully authenticated, but GitHub does not provide shell access.
```

