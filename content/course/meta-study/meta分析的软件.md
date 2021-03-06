---
title: Meta分析的软件
linktitle: Meta分析的软件
type: book
date: "2019-05-05T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

所谓“工欲善其事，必先利其器”，随着循证医学的发展，META分析已被公认为客观评价和合并针对某一特定问题研究证据的最佳手段,想要做好META分析，离不开合适的META分析工具。在琳琅满目的各种META分析软件中，该选择哪一款？究竟是免费的好还是收费的好？这是一个大问题！

目前常用的Meta分析软件大抵可分为两种，编程软件和非编程软件。其中好评如潮的Stata和R软件均属于编程软件，这类软件的优点在于其开放式的编程环境，这就意味着会有不少统计学家为它们量身打造各种优秀的可用于Meta分析的扩展包，作为终端用户只需要在网络上搜寻到这些扩展包，就可以直接坐享其福；当然，使用者也必须对软件的基本模块和命令有一定的了解。另一类非编程软件，如RevMan和Meta-Analyst都属于Meta分析专用软件，这类软件多来源于官方，易于操作、界面简洁友好，操作性更高，但其分析模式和功能相对更为固定。

### 1.RevMan：Cochrane协作网META分析软件

RevMan（ReviewManager）是国际Cochrane协作网提供给评价者准备和维护更新Cochrane系统评价而设计的软件，也可以说是专门为临床医生量身定做的Meta分析软件，它不仅可以协助我们完成Meta 分析的计算过程，还可以帮助我们了解Meta分析的架构并学习系统评价的方法，最后把完成的系统评价制作成易于通过电子转换的文件以标准统一的格式发送到CDSR，便于电子出版和日后更新。

RevMan是所有Meta分析软件中唯一可与GRADEprofile软件相互导入进行证据等级评级的软件，也是当前医学领域应用最广泛的Meta分析软件。RevMan软件中设置了干预措施系统评价、诊断试验精确性系统评价、方法学评价和系统评价汇总评价4类格式，可绘制森林图及漏斗图，但不能进行Meta回归分析、累积Meta分析、BeggS检验、EggerS检验及绘制拉贝图等。

RevMan是一款可以免费下载及使用的软件，能够输入中文，除以上功能外，最新版RevMan还具有风险偏倚评估工具表、证据结果总结表、计算器（可输入效应量、可信区间、标准误、Z值、P值进行效应值的转化）、PRISMA文献检索流程图、森林图小数位数的调整等。

### 2.Stata：功能强大的META分析软件

Stata是基于C语言的一款功能强大而又小巧玲珑的统计分析软件，最初由美国计算机资源中心研制，现为Stata公司的产品。

Stata的许多高级统计模块均是程序文件（ado文件），并允许用户自行修改、添加和发布ado文件，用户可以随时到Stata网站或者其它个人网站上搜索并下载所需的程序安装包并使用。

Meta分析通过Stata的meta.ado模块完成，包括metan、metareg、metabias等常用命令，可完成二分两变量、连续型变量、诊断试验、单纯P值、单组率、剂量反应关系、生存资料的Meta分析，也可以完成Meta回归分析、累积Meta分析、网状Meta分析等几乎所有的Meta分析方法，还可以进行BeggS检验、EggerS检验，可绘制Meta分析的相关图像，如森林图、漏斗图和拉贝图，也可排除单个研究行敏感性分析。

Stata是目前Meta分析人群中最受推崇的软件，国外高质量软件业更倾向于接受Stata Meta分析图形界面。

### 3.R：META分析全才

R软件是属于GNU系统的一个自由、免费、源代码开发的软件，由奥克兰大学的志愿者开发，目前由R核心开发小组维护。R软件具备完整的数据处理、计算和作图功能，相对于其他软件。

它的特色在于：

有效的数据存储和处理；

有用一整套数组和矩阵运算工具；

完整连贯的统计分析工具，大多数经典的统计方法和最新的技术都可以再R中直接得到；

优秀的统计绘图功能；

完善、间接和高效的编程语言。

R是自由软件，但是它的能力不会比任何同类型商业软件差，大多数人用R就是因为它的统计功能。它的部分统计功能整合在R语言底层，大多数功能也可以程序包的形式提供。目前常用的程序包有metafor、meta、rmeta等。扩展的程序包使大部分终端用户可以通过搜索扩展包，不仅可完成经典的Meta分析功能，一些新近出现的Meta分析方法如网络Meta分析等，也可以在R中完美实现，从某种意义上讲，R软件堪称Meta分析全才。

### 4.Meta-Analyst：免费的Meta分析专用软件

Meta-Analyst是一款基于微软网络框架（Microsoft. NET framework）的免费Meta分析专用软件，它是Tufts循证实践中心受美国卫生保健保健和质量管理局（AHRQ）委托编制，被AHRQ指定为循证实践中心专用Meta分析、提供证据报告的软件而广泛应用。

### 5.MIX：教学和实现Meta分析的自由软件

MIX是一款基于Excel 2000及以上版本的，采用VB语言编写的Meta分析软件，只能运行于Windows系统。MIX 1.7版以前均为免费，而更新的新版本则分为了缩减（Lite）版和专业（Pro）版，前者免费只能用于Meta分析的学习，用户不能创建数据进行Meta分析。收费的专业版则可以实现Meta分析，主要适用于治疗性研究、队列研究和病例对照研究等因果关系的研究。

### 6.Meta-DiSc：诊断性试验Meta分析工具

Meta-DiSc软件是一款基于VB语言，由西班牙卫生部门基金资助，专门用于诊断试验的Meta分析软件。Meta-DiSc软件可进行异质性检验及Meta回归分析，也可生成森林图、ROC平面及SROC曲线图。

除上述软件以外，常用的META分析软件还有CMA、MetaWin等。我们在选择时除了根据其编程环境的开放性进行选择外，更为重要的一点是，我们需要明确增加的分析需求，因为有的软件可以进行各种META分析，但有的仅仅针对某一种类型的META分析。

最后，附上一张各种Meta分析软件的比较图，各位收藏备用吧:)

![img](https://i.loli.net/2021/03/13/cBEFiPmdS94V2LC.jpg)