---
title: github Desktop使用
linktitle: github Desktop使用
type: book
date: "2019-05-05T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## 从github官网上clone仓库代码到本地

1. 打开github官网，登录成功后，New repository创建新的仓库，给新创建的仓库命名Rhine.github.io、添加描述（可选）、添加README说明（可选）:

   ![img](https://static.oschina.net/uploads/img/202011/30194754_XXTu.jpg)

   创建仓库

![img](https://static.oschina.net/uploads/img/202011/30194754_0DpS.jpg)

创建成功

2.打开github Desktop，选择Clone a repository：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_nGiV.jpg)

填入需要从线上clone的repository的名称以及即将存入本地的路径，这里选择D盘下的githubCloneProj文件夹（文件夹需新建）。如果Clone时提示project找不到，那么第一行将github网页上clone or download所提供的网页地址填入：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_e2WA.jpg)

填入仓库地址及保存路径

![img](https://static.oschina.net/uploads/img/202011/30194754_p18s.jpg)

正在 clone

clone下来的仓库：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_ErcQ.jpg)

clone下来的仓库

3.vscode打开文件夹githubCloneProj：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_VlYA.jpg)

进行编辑，搭建一个简单的html页面：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_jxKm.jpg)

4.vscode编辑完毕后，此时可见github Desktop桌面版已经自动将刚才编辑的代码同步完毕：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_M95v.jpg)

5.添加描述信息（summary,Description）后，点击Commit to master进行提交：

 

![img](https://static.oschina.net/uploads/img/202011/30194754_gfsU.jpg)

添加描述信息

## push到github网页上

1. 点击Push origin

   ![img](https://static.oschina.net/uploads/img/202011/30194754_qeDF.jpg)

   ![img](https://static.oschina.net/uploads/img/202011/30194754_TSsm.jpg)

   正在push.png

2. 打开github页面，可见Rhine.github.io仓库已经push成功：

   ![img](https://static.oschina.net/uploads/img/202011/30194754_Tc4W.jpg)

push成功后的github仓库在<a href = "https://github.com/Rhine1/Rhine.github.io">这里</a>。

## 从github网页上删除某个项目

1. 点击用户头像 -> your profile，查看已有的仓库：

   ![img](https://static.oschina.net/uploads/img/202011/30194754_ysOQ.jpg)

   查看仓库

2. 点击需要删除的仓库 -> settings：

   ![img](https://static.oschina.net/uploads/img/202011/30194754_Psog.jpg)

3. 将页面一直下拉到最低端，选择Delete this repository，确认删除即可：

   ![img](https://static.oschina.net/uploads/img/202011/30194754_TNzU.jpg)

![img](https://static.oschina.net/uploads/img/202011/30194754_ekyP.jpg)

输入仓库名称并确认删除

