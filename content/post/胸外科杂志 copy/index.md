---
title: 群晖 Docker 部署 Calibre Web 打造全功能书库
date: 2021-03-11T02:53:44.189Z
draft: false
featured: true
image:
  filename: https://images.pexels.com/photos/256514/pexels-photo-256514.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500
  focal_point: Smart
  preview_only: false

---
- **本文作者：** ZhangYong
- **本文链接：** https://www.zhyong.cn/posts/fcef/

## 功能简介

平时喜欢搜集网络上的精品电子书，那么管理成为了一个问题，放在硬盘的一堆电子书文件，想看也不知道看哪本，正好之前[安装的黑群晖](https://www.zhyong.cn/posts/f10c/)，了解到 [Calibre web](https://github.com/janeczku/calibre-web) 这样的一个开源项目，于是就完成了这样的项目搭建。功能包括：

1. 管理自己的电子书，可管理海量书籍，包括书籍的分类、作者、简介等
2. 可在线观看、书籍格式转换、推送到 Kindle 等
3. 可选：通过 frp 等内外穿透工具实现任意地方访问



## Calibre Web 安装步骤

> 前提：安装好了群晖并安装了 Docker（需要 CPU 支持）

首先打开群晖管理界面的 Docker，在注册表里搜索 `calibre-web`，选择第二个 Docker 映像双击下载。

[![推荐使用](https://i.loli.net/2021/03/24/he3rWpR247guaNl.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805205948.png)

[推荐使用](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805205948.png)



对应的 Docker Hub 地址：[technosoft2000/calibre-web - Docker Hub](https://registry.hub.docker.com/r/technosoft2000/calibre-web/)

> PS：试过很多的 Calibre web 镜像，这个镜像是功能最强大的，包括电子书格式转换和在线阅读，而 [linuxserver/calibre-web ](https://registry.hub.docker.com/r/linuxserver/calibre-web/)只能没有在线阅读和转换的功能。

<details style="display: block; color: rgb(85, 85, 85); font-family: Monda, &quot;PingFang SC&quot;, &quot;Microsoft YaHei&quot;, sans-serif; font-size: 17.64px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: justify; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="display: list-item;">technosoft2000 的镜像详细功能如下</summary></details>

等待下载完成后，在映像中，双击下载好的映像，则可以创建容器。

[![创建Calibre web容器](https://i.loli.net/2021/03/24/WgCyQFtvcYjPmL9.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805211516.png)

[创建 Calibre web 容器](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805211516.png)



官方推荐的启动代码为：

```
docker create --name=calibre-web --restart=always \
-v <your Calibre books folder>:/books \
-p <HTTP PORT>:8083 \
technosoft2000/calibre-web
```

复制

因此我们设置一个文件夹映射和端口映射即可。首先打开 File Station，创建一个用于存放电子书的文件夹，我是直接建立了一个 `books` 共享文件夹，然后再建立了一个 `calibre` 文件夹用于存放电子书（推荐）。建好之后，回到 Docker 中来。

设置名称为 `calibre-web`，可根据喜好设置，对应代码中的 `--name=calibre-web`，然后点击高级设置。

[![设置好名称](https://i.loli.net/2021/03/24/sYJZFpck8w7bWLo.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805212452.png)

[设置好名称](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805212452.png)



勾选启用自动重新启动，对应代码中的 `--restart=always`，可根据需要设置，若不勾选，则重启群晖则不自动运行此容器。

[![自动启动](https://i.loli.net/2021/03/24/9o1aiYEDIFbSLjK.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805212809.png)

[自动启动](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805212809.png)



点击`卷`，添加文件夹，选择刚刚创建用于存放电子书的文件夹，转载路径为 `/books`，对应代码中的 `-v <your Calibre books folder>:/books`

[![映射文件夹](https://i.loli.net/2021/03/24/LgIAmNhyPcC638i.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805213049.png)

[映射文件夹](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805213049.png)



然后点击`端口映射`，设置一个本地端口，不冲突即可，如我的为 25556，那么之后访问即：[http://IP:25556，对应代码中的：`-p](http://ip:25556，对应代码中的：`-p/) :8083`。不推荐使用默认的`自动 `，这样每次重启会改变端口，造成访问地址的改变。

[![端口映射](https://i.loli.net/2021/03/24/qwR86QtXgLulsja.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805213345.png)

[端口映射](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805213345.png)



点击应用即可，然后启动该容器。

这里打开群晖 IP: 端口访问，如我的 IP 为 `192.168.0.102`，可以看到已经可以成功打开。

[![配置书库](https://i.loli.net/2021/03/24/PnjuVQCHevxdTKF.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805214016.png)

[配置书库](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805214016.png)



在书库配置中，设置为 `/books`，点击保存。

此时会提示`数据库路径无效，请输入正确的路径`。

[![报错](https://i.loli.net/2021/03/24/KZYdoiJDGVhFXH3.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805214303.png)

[报错](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805214303.png)



由于 Calibre-web 是基于 Calibre 这款软件的，书库里会有 `metadata.db` 的数据库文件，而我们创建的文件夹是没有任何文件。

因此我们电脑中安装 [Calibre](https://www.zhyong.cn/posts/59a8/)，然后用电脑挂载群晖，在此位置建立一个空白书库（注意：群晖需要安装 WebDAV Server）。

[![创建书库](https://i.loli.net/2021/03/24/46y5NmAi18ax3ls.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805214931.png)

[创建书库](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805214931.png)



[![创建书库](https://i.loli.net/2021/03/24/z7CZqPNfdkrojnh.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215333.png)

[创建书库](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215333.png)



完成后，就会在该位置生成一个 `metadata.db` 的文件。然后重试，提示配置已经更新。

[![配置](https://i.loli.net/2021/03/24/ExWoUiLYcarNBet.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215542.png)

[配置](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215542.png)



> 若仍出现问题，则在 File Station 中设置一下该文件夹的权限，设置为 `Everyone` 为读取、写入。

点击登录，用户名：admin 密码：admin123

[![登录](https://i.loli.net/2021/03/24/3H7X5wJzTfQ6Snm.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215718.png)

[登录](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215718.png)



[![终于成功](https://i.loli.net/2021/03/24/QkMVPeAbRhKW7Y1.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215737.png)

[终于成功](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805215737.png)



## 配置

### 设置中文

默认为英文界面，在 admin——language 设置即可。

[![设置中文](https://i.loli.net/2021/03/24/zPaBgHrWo6yR15p.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805220203.png)

[设置中文](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805220203.png)



### 开启网页上传，对于少量书籍上传非常实用

在管理权限 —— 编辑基本配置 —— 功能配置中，其它功能也可在此开启。

[![启用上传](https://i.loli.net/2021/03/24/1sSteIO8C6FNfWg.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805220739.png)

[启用上传](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805220739.png)



刷新一下页面，在右上角则出现`上传书籍`。测试上传书籍报错：

```
数据库错误：(sqlite3.OperationalError) attempt to write a readonly database [SQL: INSERT INTO authors (name, sort, link) VALUES (?, ?, ?)] [parameters: (u'\u672a\u77e5', u'\u672a\u77e5', u'')] (Background on this error at: http://sqlalche.me/e/e3q8)。
```

复制

原因在于无写入权限，将创建的文件夹设置为完全控制（读取、写入应该就可以了），然后重启容器，即可解决此问题。

[![img](https://i.loli.net/2021/03/24/aLmTupXRNYFQ7Eq.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805221331.png)

成功在 Web 上传：

[![web上传](https://i.loli.net/2021/03/24/oGzIKWRfEVF8Sdh.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805221800.png)

[web 上传](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805221800.png)



上传或编辑书籍时，可点击最下面的获取元数据，即可获得作者、解决、封面图片等各类信息，这是我非常喜欢的一个功能，很强大。获取后保存即可，封面更改有时会迟一点生效。

[![获取元数据](https://i.loli.net/2021/03/24/KrRzTDmqfklWcEV.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222044.png)

[获取元数据](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222044.png)



### 转换书籍为 epub 格式从而在线观看

此程序可以在线观看 TXT、pdf 和 epub 格式，epub 格式是一个通用的电子书格式，因此将其它书籍转换为此格式从而在线阅读。

[![编辑书籍](https://i.loli.net/2021/03/24/KrRzTDmqfklWcEV.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222044.png)

[编辑书籍](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222044.png)



[![转换为epub格式](https://i.loli.net/2021/03/24/xlsqyBvEubSdLYQ.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222528.png)

[转换为 epub 格式](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222528.png)



这样就可以在线阅读了，有目录导航，可以添加书签，全屏阅读等，并且可以记住阅读位置，下一次打开接着阅读（不可跨设备，书签可以跨设备），体验非常棒。

[![在线阅读](https://i.loli.net/2021/03/24/bMgSZEKqYQOAuCX.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222723.png)

[在线阅读](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805222723.png)



### 设置 Kindle 推送

可参考：[Kindle 推送教程：教你用电子邮箱推送电子书 – 书伴](https://bookfere.com/post/3.html)

Kindle 推送稍微复杂点，首先必须有一个亚马逊账号，登录 Kindle（Kindle 软件或设备都可以）后，会有一个个人文档邮箱，然后在 Kindle 设备或 APP 或[登录亚马逊账号](http://z.cn/myk)都可以查看，以 `@kindle.cn` 结尾的邮箱。

第一步，到 Calibre web 中，填写 Kindle 邮箱；

[![Kindle邮箱](https://i.loli.net/2021/03/24/7oUQEftRravVH1k.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805223730.png)

[Kindle 邮箱](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805223730.png)



第二步，配置邮件发送服务器；

[![配置邮件服务器](https://i.loli.net/2021/03/24/zcjxEV8mqXMfdAg.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805223921.png)

[配置邮件服务器](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805223921.png)



这里推荐使用 163 邮箱，主机名为 `smtp.163.com`，配置如下：

[![邮箱配置](https://i.loli.net/2021/03/24/KrXLgtcjZUTM1JW.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805224156.png)

[邮箱配置](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805224156.png)



登录 163 邮箱，开启 smtp 服务，然后生成一个授权码：

[![开启smtp](https://i.loli.net/2021/03/24/IFqd7WahDmMS1p2.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805224514.png)

[开启 smtp](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805224514.png)



[![授权码生成](https://i.loli.net/2021/03/24/Z5bHlM1TXw2F8Iv.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805224626.png)

[授权码生成](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805224626.png)



然后将授权码填入到 SMTP 密码一栏。

第三步，将配置的发送邮件服务器添加到 Kindle 已认可邮箱列表

在[设置](https://www.amazon.cn/mn/dcw/myx.html/ref=kinw_myk_redirect#/home/settings/payment)中，首选项 —— 个人文档设置 —— 已认可的发件人电子邮箱列表，添加该邮箱即可。

[![添加认可的电子邮件](https://i.loli.net/2021/03/24/mcaGNWAxDSVJR5d.png)](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805225048.png)

[添加认可的电子邮件](https://zhyong-1254441582.cos.ap-nanjing.myqcloud.com/20200805225048.png)



全部完成后，即可一键发送电子书到 Kindle 设备了。

### 批量上传电子书

那么如果有大量电子书该如何上传呢？思路还是一样，直接用电脑挂载群晖的文件夹，使用 [Calibre](https://calibre-ebook.com/) 打开该书库，然后就可以批量上传、管理了。

## 总结

总之，搭建过程还是较为麻烦，涉及的方面较多，需要了解相关的基础知识，但是此篇教程我写的较为详细，相信只要耐心都能搭建成功，毕竟我使用这个有一段时间了，有的需要注意的地方我都写出来了，Docker 映像也选择好了，注意文件夹的权限是一个大坑，搭建不成功很大方面是这个原因。

另外内外穿透方面，这涉及的更多了，提供这一种思路，有能力自行折腾了。