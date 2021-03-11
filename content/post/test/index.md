---
title: Typora 图片自动上传服务器设置
date: 2021-03-11T02:53:44.189Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
<!--StartFragment-->

* 打开 **Typora** ,点击左上角 ”**菜单**“，进入 ”**偏好设置**“ ，”**图像**“ 选项卡设置如下：

![](https://pic3.zhimg.com/80/v2-2112e982fc14f2d2084da385c687d47e_720w.jpg)

* 当选择 “**上传图片**” 选项时，在图片复制进 **Typora** 时，图片将立即被自动上传至已经配置好的服务器；选择 “**无特殊操作**” 时，将不会自动上传，稍后可通过右键图片弹出菜单 “**上传图片**” 进行手动上传。

![](https://pic3.zhimg.com/80/v2-82ed110b7a637748428460c0f90980fe_720w.jpg)

![](https://pic3.zhimg.com/80/v2-13437a21eeb0cbc0c4449aea895d4a8e_720w.jpg)

​ “**上传服务器设定**” 中，推荐选择 “**PicGo-Core (Command line)**” 以命令行上传图片，仅在上传时运行 “**PicGo-Core**“ 命令行，上传成功(或失败)后立即退出，占用系统资源低；

​ 如果选择 “**PicGo (app)**" ,将占用相对命令行更多的系统资源，因为 **PicGo.app** 需常驻后台，但 **PicGo.app** 将提供更多其他功能，如上传历史记录、自动重命名等。

![](https://pic2.zhimg.com/80/v2-68400e0470b365a98485d8ffebb36dcd_720w.jpg)

​ 选定 “**PicGo-Core (Command line)**” 后，点击 ”**下载或更新**“ 按钮，下载或更新 "**PicGo-Core**" 。

<!--StartFragment-->

* 配置smms

​ “**smms**" 简单实用，可快速上手，而且免费，由于服务器在国外，不一定稳定。

* 注册smms账号

[smms](https://link.zhihu.com/?target=https%3A//sm.ms/home/apitoken)账号注册链接如下：<!--StartFragment-->

```text
https://sm.ms/home/apitoken
```

<!--EndFragment-->

* 生成 Secret Token

注册完成后，再次复制该链接打开如下界面：

![](https://pic2.zhimg.com/80/v2-463f42e8e1f4316d34846e170ad66039_720w.jpg)

点击 “**Generate Secret Token**" 生成 ”**Secret Token**" ，复制以备用。

* 配置文件

​ 打开 "**Typora**" 配置文件，将以下方代码复制到配置文件，其中 ”**token**" 即为上面图片中的 "**Secret Token**" ，保存配置文件。



* ![](https://pic3.zhimg.com/80/v2-63e1a4ed28df1d2bfd96b021dae1eb3a_720w.jpg)大功告成

最后 ，点击 “**验证图片上传选项**” ，提示 “**验证成功**” ，则大功告成！

<!--StartFragment-->

* GitHub

```text
{
  "picBed": {
    "uploader": "github",
    "github": {
        "repo": "", // 仓库名，格式是username/reponame
        "token": "", // github token
        "path": "", // 自定义存储路径，比如img/
        "customUrl": "", // 自定义域名，注意要加http://或者https://
        "branch": "" // 分支名，默认是master 
    }
  },
  "picgoPlugins": {}
}
```

<!--EndFragment-->

<!--EndFragment-->