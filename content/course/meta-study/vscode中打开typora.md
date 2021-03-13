---
title: vscode中打开typora
linktitle: vscode中打开typora
type: book
date: "2019-05-05T00:00:00+01:00"
# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

VSCode中编辑markdown没有typora来的舒服，但是VSCode中的文件又不能直接使用typora打开，必须先进入文件路径，比较麻烦。
然后VSCode插件市场搜了一下，发现确实有这么一个插件：
![在这里插入图片描述](https://i.loli.net/2021/03/12/MZVsnDbrhzac2mW.png)
**只是没有用**，似乎在开发阶段

## 使用Open in External App

而另外一个五星好评的插件Open in External App则可以在vscode中用typora打开md文件，不仅如此，还有设定其他应用打开相应的文件，比如chrome打开html。插件食用方法也比较简单，安装后，在`settings.json`中将以下内容添加进去，注意在windows要更改 "openCommand"命令对应的程序路径：

```json
"openInExternalApp.openMapper": [
    {
        // represent file extension name
        "extensionName": "html",
        // the external applications to open the file which extension name is html
        "apps": [
            // openCommand can be shell command or the complete executable application path
            // title will be shown in the drop list if there are several apps
            {
                "title": "chrome",
                "openCommand": "/Applications/Google Chrome.app"
            },
           
        ]
    },
    {
        "extensionName": "md",
        "apps": [
            {
                "title": "typora",
                "openCommand":"/Applications/Typora.app"
            }
        ]
        
    },
    
]
```

添加好之后，双击md文件即可看到`Open in External App`选项，点击即可跳转到typora。

## vscode的配置文件setting.json的UI界面或者json形式

 快速打开
使用快捷键 Ctrl+Shift+P ，然后搜索setting

![](https://i.loli.net/2021/03/12/hJB98aTmnIEZcVy.png)

首选项：打开设置（json）这个打开的是settings.json文件

![](https://i.loli.net/2021/03/12/7UIFyEuct8N2DZd.png)

首选项：打开默认设置（json）,这个打开的是defaultSettings.json文件
首选项：打开工作区设置，这个打开的是

![](https://i.loli.net/2021/03/12/CMV2uasdgQ9GjDo.png)

设置界面是UI形式还是json形式，可以通过这个图标来进行切换


![](https://i.loli.net/2021/03/12/zdBpgjoCnhUfmDw.png)