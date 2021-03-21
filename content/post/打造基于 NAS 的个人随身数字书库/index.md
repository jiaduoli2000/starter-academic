---
title: 打造基于 NAS 的个人随身数字书库
date: 2021-03-11T02:53:44.189Z
draft: false
featured: true
image:
  filename: https://images.pexels.com/photos/256514/pexels-photo-256514.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500
  focal_point: Smart
  preview_only: false
---

### **Matrix 首页推荐**

[Matrix](https://sspai.com/matrix) 是少数派的写作社区，我们主张分享真实的产品体验，有实用价值的经验与思考。我们会不定期挑选 Matrix 最优质的文章，展示来自用户的最真实的体验和观点。

文章代表作者个人观点，少数派仅对标题和排版略作修改。

------

在完成基于 NAS 的 Podcast 订阅管理平台以及密码库之后，我将下一步「私有化」的目标瞄上了自己多年来的精心收藏的数字书库。

我自己阅读的电子书除了从 Kindle 商店购买书籍之外，还有就是从第三方渠道下载以及自己 DIY 的电子书了。以前这些自制的电子书都被我放在电脑的某个文件目录中，而随着时间的推移，这些电子书文件越来越多，如何对这些数字文件进行高效的管理成为我心中的一大难题。

由于我主要的阅读工具都是通过 Kindle 来阅读，很少通过手机或者平板上进行电子书的阅读，因此我从其他渠道下载以及 DIY 的电子书都是基于 Kindle 的电子书格式 azw3，这种格式虽然在 Kindle 硬件上可以获得较好的阅读体验，但这也无形中让我个人随身书库的打造带来了相当多的难点，所以如果你也想打造类似的数字书库，那么下载的电子书的文件格式可以选择更为通用的 mobi，这样无论是管理还是阅读上都会更为方便。

下面就来介绍下我的个人随身数字书库打造过程吧。

## 使用工具来管理自己的电子书库

以前我会将下载的 azw3 格式的电子书经过简单的重命名后，直接保存在电脑的某个目录中。当时的考虑非常简单——将 AZW3 格式的电子书直接拷贝到 kindle 的存储空间就可以在设备上阅读了。

这种操作方式最为简单，但也带来了管理上的难题——无法确认 kindle 中已经保存了哪些书、是否重复等等。之后我开始使用桌面端的电子书管理软件来对书籍进行管理，也就是使用开源的电子书管理器 calibre。

![img](https://i.loli.net/2021/03/21/FQVjEbz78ynCpWK.png)

calibre 的优点在于可以通过刮削器完善书库中的电子书元数据信息，并且通过类似文件同步的方式来实现本地数字书库和 kindle 的电子书同步以及传输操作。同时 calibre 还可以实现电子书转换、编辑等操作，可以说是现阶段最为全面的本地化电子书管理工具了。

而通过将电子书导入到 calibre 中，我逐步建立起一个基于本地电脑的个人电子书数据库。而更大的设想还在后面——我能不能将其变成一个自己专属的电子书书库，并且实现全终端的在公网环境下的阅读甚至管理？

我将实现目标转向了家中的群晖。

## 基于 NAS 构建在线书库

### 做好第一步：将本地书库转移到 NAS 上

我的初期的目标很简单——实现家中局域网内的桌面设备（Windows 电脑和 Mac ）可以访问书库并使用 calibre 进行管理即可，那么首先就是要将原本存储在电脑中的书库转移到 NAS 上，当然也需要为此新增一个共享文件夹。

通过群晖的「控制面板」-「共享文件夹」，点击「新建」来创建书库目录（比如说我所创建的这个 `book` 目录），这里需要注意的是权限部分，为了方便访问可以给管理员以及访客开启「可读写」权限。

![img](https://i.loli.net/2021/03/21/KUVYBTlnbEX8cqR.png)

完成之后我们需要为该目录开启局域网内的共享访问，这里回到「控制面板」，然后在「文件服务」中找到 「SMB 服务」并勾选「启动 SMB 服务」。然后在「高级设置」里面对最低以及最高的 SMB 版本进行设置，并点击「应用」。

![img](https://cdn.sspai.com/2020/12/24/211867f8636b0582dac898e1100cb490.png?imageView2/2/w/1120/q/90/interlace/1/ignore-error/1)

再回到当前的 Windows 电脑中打开「网络」，然后在共享的设备中查看是否有 NAS 这个设备，然后看一下里面是否有新建的这个书库文件夹（如果提示需要验证输入 NAS 的管理员的账户和密码），如果可以在这个文件夹里新建或者删除文件就表示创建成功。

接下来就是将原本保存在 PC 上的书库目录拷贝到新建的 NAS 共享文件夹下面，我这里在 `book` 目录下方再创建了一个`library`目录，然后将之前保存到本地电脑中的书库全部拷贝进去，需要注意是一定要把 `metadata.db` 这个文件一并拷贝进去，也是书库数据的关键。

![img](https://i.loli.net/2021/03/21/I5d3JGyhcj4nApo.png)

接下来我们打开桌面端的 calibre 开始切换书库，点击工具栏中的「书库」-「切换/创建书库」，然后导航到网络中 NAS 下对应的 `book` 目录并选择`library`这个文件夹，并且勾选「使用当前现有的书库位置作为新的位置」并点击确定，如果前面设置正常，你将会看到和之前本地书库一样的书籍列表，只不过这时候的书库的位置被转移到了局域网中的 NAS 上。

![img](https://i.loli.net/2021/03/21/f5H9mLyJUAVGNi6.png)

### 使用 calibre web 的 Docker 镜像构建书库数据库

仅仅只是让书库放在 NAS 上通过 SMB 进行目录共享，也只能通过局域网中的桌面设备（Windows 电脑或者 Mac 电脑）进行访问。显然我希望的是实现全终端的访问（这当然包括手机以及平板设备），而要想实现这个目标，就需要为 NAS 上的虚拟书库生成为 OPDS 的目录结构。

OPDS 全称为 Open Publication Distribution System，即开放出版物发行系统，通过这个系统我们就可以通过 App 或者网页浏览器来对虚拟书库进行管理和访问，而不再需要通过文件目录访问的形式来管理你的书库。而要想生成 OPDS，我们就需要使用基于 calibre 的 web 分享服务，这里我选择的依旧是我们熟悉的 「Calibre-web」，只不过这次选择了一个新的 Docker 镜像版本（其实是此前我派介绍的镜像版本有点太老了）。

在下载镜像之前，我们需要对目标的文件目录进行权限上的修改，这里需要用到的除了之前我们存放虚拟书库的 `book` 目录之外，还需要一个存放配置文件的目录，这里我在 `docker` 文件夹下创建了一个 `calibre` 目录。

![img](https://i.loli.net/2021/03/21/svWQtGIk19RwD8H.png)

下面还是在 File station 中，选择 `book` 目录以及刚刚创建的 `docker/calibre` 并右击属性，在「权限」选项卡中选择 「Everyone」用户组并点击「编辑」，选择所有的权限并授予全部权限（全部控制），如果有 http 用户组也可以以此类推进行权限设置，这一步的设置主要是为了方便后续生成的应用容器可以正常读写该目录。

![img](https://i.loli.net/2021/03/21/OL69WDreotQzGJY.png)

接下来打开群晖的 Docker ，在侧栏中点击注册表并搜索 「Calibre-web」，并选择搜索结果中出现的「linuxserver/calibre-web」这个镜像，双击进行下载并等待下载完毕。

![img](https://i.loli.net/2021/03/21/TAozpR19c5EngIK.png)

在「映像」中找到双击刚刚下载的「linuxserver/calibre-web」，双击开始创建容器。

![img](https://i.loli.net/2021/03/21/5fITOGmL4aUnu8o.png)

在设置页面中点击高级设置，在「卷-添加文件夹」中选择书库目录（比我我的路径是`book/library`），转载路径输入`/books`，然后再添加一个配置文件路径（比如我的是 `docker/calibre`），转载路径为 `/config`。

![img](https://i.loli.net/2021/03/21/BJsvReO3i9NIuKF.png)

切换到端口设置选项卡，在本地端口上填入和容器端口一致的 8083 端口，完成之后选择点击「应用」并启动容器。

![img](https://i.loli.net/2021/03/21/YQBVDsSdgENh86R.png)

启动后在浏览器中输入`http://你的 NAS ip:8083` 进入设置页面，这里会要求你首先填入书库的路径，这里输入 `/books` 后点击 submit 完成设置，需要说明的是如果出现相关错误提示，可以在回到 File station 中检查 `books` 文件夹是否给「Everyone」提供了「全部控制」权限。

![img](https://i.loli.net/2021/03/21/VHcsC68TRBWadl2.png)

然后你再访问`http://你的 NAS ip:8083`，这时应该会直接进入到登录页面，在 `Username` 这里输入 `admin`，在 `Password` 这里输入 `admin123` 完成登录，如果看到首页上都是你收藏的书则表示 Calibre-web 已经成功创建你的在线书库了！

![img](https://i.loli.net/2021/03/21/9RWklupi4HGhoEv.png)

这里我们可以检验下 OPDS 是否创建成功，在浏览器的地址栏输入 `http://你的 NAS ip:8083/opds` 回车，如果弹出登录页面则表示目录创建成功。

![img](https://i.loli.net/2021/03/21/VjJWKo7MTpOq3mg.png)

### 让 NAS 上的数字书库可以在公网访问

显然我们看电子书不可能仅仅只在家中局域网环境内，我们更希望书库可以「随时随地」都可以被访问，因此这里我们需要解决的就是公网访问问题，这里除了使用 DDNS 之外，我选择了更稳定的 frp 内网穿透。

而在 NAS 上创建 frp 内网穿透服务，一般用得比较多的是使用 Docker 镜像，考虑灵活以及稳定性上，我这里选择通过计划任务来实现。

![img](https://i.loli.net/2021/03/21/ANXy4rEB9IhM8Cq.png)

首先在群晖的 `docker` 目录下创建 `frpc` 文件夹，在 `frp` 的 `GitHub` 主页上下载对应版本的 `frp` 包（这里选择的是 [Linux amd64](https://github.com/fatedier/frp/releases/tag/v0.34.3) 位版本），然后完全解压缩将 frpc 文件几个 frpc.ini 文件拷贝到 `frpc` 文件夹中。

![img](https://i.loli.net/2021/03/21/hgoxVKD5f6sCj4L.png)

在群晖的 File station 打开 `frpc` 文件夹，使用文本编辑器打开并添加一段新的配置项目（如图）并保存。

![img](https://i.loli.net/2021/03/21/32yqjfNdZ4eLXxz.png)

在打开「控制面板-计划任务」，点击「新增-计划的任务-用户定义的脚本」。

![img](https://i.loli.net/2021/03/21/zbxUHPCFf4O9ZL5.png)

在创建任务选项卡输入任务名称，用户账号可以选择 root（或者其他管理员账号），然后再切换到「任务设置」中，在「用户定义的脚本」中输入：

```shell
 nohup /volume1/docker/frpc/frpc -c /volume1/docker/frpc/frpc.ini &
```

在「计划」中设定任务排期（随便填写）点击保存。

![img](https://i.loli.net/2021/03/21/p1AP6z4m75RDUlV.png)

回到「计划任务」页选中新建的任务并点击「设置」，勾选「保存输入结果」并将其保存到和 frp 相同的目录并点击确定。

![img](https://i.loli.net/2021/03/21/G36EHNkZMtzYAeP.png)

最后在「计划任务」页中选中 frpc 任务并点击运行。这是再使用`http://<映射的公网 ip>:<映射的端口地址>`访问 calibre web，如果能显示 calibre web 的登录页面即表示内网穿透成功。

这样我们就可以在非家中局域网的环境下，通过浏览器和各种应用来访问自己的在线书库了。

## 在多个平台访问和管理私人书库

现在，我的私人数字书库已经基本搭建完毕，可以通过浏览器在任何地方管理书库，但我希望可以不仅仅只是通过浏览器来进行远程管理和访问，而希望即便是在公司的 PC 上也能管理家中的书库，甚至可以直接在手机上打开书库并下载书籍。

因此我需要解决的问题是如何在外网上安全访问到家中群晖的文件目录。

由于配置上的问题，最终我选择的依旧是通过 SSH / sftp 方式来实现远程的登录访问，首先在群晖中打开「控制面板」-「终端机和 SNMP」，勾选「启动 SSH 功能」并设置一个端口（最好不是 22）。

![img](https://i.loli.net/2021/03/21/lmyDNUfWPurVpxM.png)

然后在「文件服务」中切换到 「FTP」 选项卡，然后勾选 「启动 SFTP 服务」并设置和前面相同的端口号。

![img](https://i.loli.net/2021/03/21/FekQMog5N2qfADn.png)

最后增加一条 frpc 的配置，同样是打开 `frpc.ini` 并新增下面的一段配置并保存，最后重启 frpc 服务使其生效。至于确认是否成功则可以在外网的电脑通过 SSH 终端尝试是否可以登录。

![img](https://i.loli.net/2021/03/21/ivOMro3Ep485Xz2.png)

### 在 PC 上管理 NAS 上的书库

如果不考虑网页端管理，实际上我们在外网 PC 上依旧可以通过 calibre 软件进行管理，但这需要将群晖上相应的路径挂载到文件资源管理器上，这里我通过的是 SFTP 协议进行挂载。

将远程文件路径通过 sftp 协议挂载到文件资源管理器，在 Windows 上最方便的当然是 raidrive。创建驱动器时选择 NAS 下面的 SFTP，然后在地址栏输入 frp 映射的公网 IP 以及映射的端口，输入 NAS 的账号和密码并挂载。成功后你就可以在网络位置上看到新挂载的盘符了。

![img](https://i.loli.net/2021/03/21/ye8IH6UvxD5qnBd.png)

打开 calibre 然后选择「书库」-「切换/创建书库」，定位到 raidrive 生成的新驱动器下的书库目录（我自己的路径是：`X:\book\library`）并将其添加为新的书库目录，这时候你就可以看到 calibre 可以全部载入 NAS 上的书库，并且实现外网直接通过管理。

![img](https://i.loli.net/2021/03/21/YiovVMEQF7duy4p.png)

### 在 Mac 上管理 NAS 上的书库

和 Windows 类似，我们依旧选择的是将群晖的文件目录通过 SFTP 映射到本地的驱动器路径中，这里我选择的工具则是 cloudmounter ，使用的办法可以参考[支持 macOS / Windows，一站式网盘管理工具：CloudMounter](https://sspai.com/post/63683)。

![img](https://i.loli.net/2021/03/21/6qVhMjy3ol7PACB.png)

挂载到访达之后，打开 Mac 上的 calibre，同样是「书库」-「切换/创建书库」，这里选择刚刚挂载上去的群晖文件目录下的 「`book/library`」并且选择「使用当前现有的书库位置作为新的位置」，如果设置恰当，你同样可以在 calibre 看到 NAS 的书库列表，当然管理/增添书等操作也不在话下。

![img](https://i.loli.net/2021/03/21/c91kPaX2HrylWvb.png)

### 在 iPhone/iPad 打开个人数字书库

移动端访问书库则要简单一些，实际上就是使用第三方 App 读取生成的 OPDS 地址来实现在线的书库访问，在 iOS 平台我选择的是 kyreader 这款 App，主要是这款应用满足我的几个需求：可以基于 OPDS 访问书库，同时支持解析 awz3 格式的电子书。

打开 kyreader 后直接点击中间的「目录」来添加书库，输入你的书库名以及对应的 URL（`http://<映射的公网 ip>:<映射的端口地址>/opds`）并添加。然后在弹出的账户验证中输入 calibre web 的用户名以及密码，点击确认后就可以将个人书库添加到目录中了。

![img](https://i.loli.net/2021/03/21/Cz4EgPRZkTAqSif.png)

![img](https://i.loli.net/2021/03/21/1BvhOWJmkFAtsDw.png)

打开书库，在最新添加中就可以看到你的书库目录了，这里我选择一本 azw3 格式的书，然后点击下载就可以下载到手机中，直接点击阅读就可以用 kyreader 进行阅读了。唯一的缺点就是并不支持阅读进度同步（显然这个要求有些太难了）。

![img](https://i.loli.net/2021/03/21/PQZTayMhz1vWKN5.png)

![img](https://i.loli.net/2021/03/21/Y6apEi9xTucRwbX.png)

### 在 Android 设备上打开个人数字书库

相比 iOS 端，在 Android 上访问书库并且阅读 AWZ3 格式的书反而更加麻烦一些，原因是单纯的电子书阅读器在对 azw3 格式的电子书文件存在解析问题（会识别为 bin 数据文件），因此在 Android 上需要通过两款应用来实现我的需求。

首先我需要使用这款名为 [calibre companion](https://play.google.com/store/apps/details?id=com.multipie.calibreandroid) 的应用来实现书库的连接，打开应用点击右上角的 「setting」 进入 「Connecting to calibre」，在 「Content server connection」-「IP address and Port or URL」中输入书库映射出的公网 ip 和端口号。

![img](https://i.loli.net/2021/03/21/FuPZ6WqGODeKpAS.jpg)

![img](https://i.loli.net/2021/03/21/NwpPxrUd1RLDcYC.jpg)

然后在应用首页点击右上角的 「connect」-「to Content Server」并输入书库的用户名和密码完成书库的连接。

![img](https://i.loli.net/2021/03/21/IbMNsBxnrQXy7eK.jpg)

![img](https://i.loli.net/2021/03/21/3HRekivtKdyVGlj.jpg)

calibre companion 连接到书库后并不提供书籍的阅读，因此点击书籍后只会提供meta数据显示或者下载，点击下载之后会将书库的电子书文件保存到 calibre companion 目录下，这时候就需要要使用另一款电子书阅读器[FBReader](https://play.google.com/store/apps/details?id=org.geometerplus.zlibrary.ui.android)进行电子书阅读。

![img](https://i.loli.net/2021/03/21/IP4CibYzU5nTNpv.jpg)

![img](https://i.loli.net/2021/03/21/HJiOamIEcvSgpwG.jpg)

实际上 FBReader 就是用来解析 azw3 格式的电子书，点击侧栏的「选择文件」，然后定位到 calibre companion 的文件目录就可以看到刚才下载的电子书文件了，这时候选中就可以进行阅读了，和 iOS 平台类似，在 Android 平台同样不支持阅读进度的同步。

![img](https://i.loli.net/2021/03/21/5esxhbXoEKNk1Yd.jpg)

![img](https://i.loli.net/2021/03/21/P2qNn1QsXZ9TmrC.jpg)

## 结语

通过以上的一系列的操作，我终于实现了基于私有云的个人随身电子书库的搭建和外网访问，实现了个人书库的随身设备阅读访问。相比 Podcast 以及密码管理的私有云搭建，工具更多也更为复杂，但依然不失为个人书库的云端管理解决方案之一。