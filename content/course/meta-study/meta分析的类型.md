---
title: Meta分析的类型
linktitle: Meta分析的类型
type: book
date: "2019-05-05T00:00:00+01:00"

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

证据是循证医学( Evidence-based Medcine，EBM) 的核心，基于随机对照试验( RCT) 的系统评价/Meta 分析是当前公认的最高级别证据。meta分析是指对以往的研究结果进行系统定量综合的统计学方法。近些年来，随着meta分析方法学的发展，其类型也多种多样，本文将对meta分析的类型作简单介绍。

### **1.单组率的meta分析**

**定义**：只提供一组人群的总人数和时间发生人数，多为患病率，检出率，知晓率，病死率，感染率。一般基于的研究为横断面研究。

**缺点**：异质性很难控制

**方法**：①加权计算:
即根据每个独立研究的样本量大小，给予不同的权重，对各独立样本的效应量率进行合并; ②直接等权相加:
即把各独立的结果事件直接等权相加，然后直接计算合并率，再用近似正态法计算其可信区间 ; ③调整后再等权相加:
即对各个独立研究资料的率进行调整后再行等权相加，计算出合并率的大小。

例如：Jones
L, Bellis M A, Wood S, et al. Prevalence and risk of violence against
children with disabilities: a systematic review and meta-analysis of
observational studies[J]. The Lancet, 2012, 380(9845): 899-907.



![img](https://i.loli.net/2021/03/13/xg6dPEZhVSi4beT.jpg)

### **2.单纯P值的meta分析**

**定义**：即将多个研究的P值进行合并

**缺点**：不同研究未能根据研究特点进行加权;无法获知事件的发生信息，故无法得出有任何临床意义的信息;无法分析两个结论相反的研究;无法进一步评价研究之间的差异。一般不推荐。

**方法**：当纳入研究仅给出了P 值，且按照Cochrane 系统评价员手册给出计算方法也不能计算出需要的数据，且临床实践需要合并，那么，在这种情况下可以考虑单纯对P 值进行合并。

### **3.meta回归分析**

**定义**：主要通过对多因素的效应量进行联合分析，主要评价研究间异质性的大小及来源，是亚组分析的一种扩大。

**缺点**：纳入的研究数量在 10 个以上时才行此分析

**方法**：将效应估计量( 如RR、OR、MD 或logRR等)
作为结果变量，将可影响效应量大小的研究特征因素( “协变量”或“潜在效应量改变因子”)
作为解释变量，则回归系数描述了结果变量怎样随着解释变量的单位增加而改变;
其统计学差异性通过对结果变量和解释变量之间有无线性关系来确定，通过回归系数的P 值来判断这种差异有无统计学意义

**例如**：Ettehad
D, Emdin C A, Kiran A, et al. Blood pressure lowering for prevention of
cardiovascular disease and death: a systematic review and
meta-analysis[J]. The Lancet, 2016, 387(10022): 957-967.

![img](https://i.loli.net/2021/03/13/ZnTfKmbtRBFJuX5.jpg)

### **4.累积meta分析**

**定义**：将研究资料作为一个连续的统一体，按研究开展的时间顺序及时将新出现研究纳入原有meta分析。

**优点**：反映研究结果的动态变化趋势及各研究对结果的影响，也有助于尽早发现有统计学意义的干预措施。

**方法**：每次研究加入后均重复一次meta分析。

**例如：**Jüni
P, Nartey L, Reichenbach S, et al. Risk of cardiovascular events and
rofecoxib: cumulative meta-analysis[J]. The Lancet, 2004, 364(9450):
2021-2029.

![img](https://i.loli.net/2021/03/13/bmIishEgJeSOkA8.jpg)

### **5.网状meta分析**

**定义**：在临床实践中，若有一系列的药物可以治疗某种疾病，但 RCT 均是药物与安慰剂的对照，而药物互相之间的 RCT 都没有进行或很少，那么在这种情况下，就需要将间接比较和直接比较的证据进行合并。

**方法**：首要的是构造一个等级模型，以处理抽样变异、治疗异质性及研究治疗比较间的不一致性，并提供模型的最大似然比。目前，主要的方法有经典的频率学法和贝叶斯法。

**例如：**Palmer
S C, Mavridis D, Nicolucci A, et al. Comparison of clinical outcomes
and adverse events associated with glucose-lowering drugs in patients
with type 2 diabetes: a meta-analysis[J]. JAMA, 2016, 316(3): 313-324.

![img](https://i.loli.net/2021/03/13/dQUEMC9fIOBozhH.jpg)

### **6.诊断性meta分析**

**定义**：因地区、个体、诊断方法及条件的差异，使得发表的关于同一诊断方法的研究结果存在着不同甚至是矛盾的;且随着新技术的不断走向临床，选择也愈来愈多。该类型主要是为评价某种诊断措施对目标疾病的准确率，多为对目标疾病的敏感性、特异性进行评价，报道似然比、诊断比值比等。

**例如**： Cousin
F, Ortega-Deballon P, Bourredjem A, et al. Diagnostic Accuracy of
Procalcitonin and C-reactive Protein for the Early Diagnosis of
Intra-abdominal Infection After Elective Colorectal Surgery: A
Meta-analysis[J]. Annals of surgery, 2016.



![img](https://i.loli.net/2021/03/13/aGqzX1xSFpbcZTn.jpg)

### **7.个体数据meta分析**

**定义**：该研究类型不是直接利用已经发表的研究结果总结数据进行 Meta 分析，而是通过从原始研究作者那里获取每个参与者的原始数据，并对这些数据进行 Meta分析。

### **8.前瞻性meta分析**

定义：是指在 RCT 的结果尚未出来之前，先进行系统检索、评价和制定纳入及排除标准的一种 Meta 分析。因 PMA 是在研究开始之前或者进行中就制定好了计划，可以避免各研究间出现较大的差异，同时具有个体数据 Meta 分析的优点。

优点：是针对需要行多中心、大样本研究但现实又不能实现的情况下的最有效方式。

缺点：但成本非常高、操作困难且需要耗费大量的时间。

### **9.常规meta分析**

**定义**：常规 Meta 分析主要基于有对照组的直接比较的研究，最常见的是基于 RCT的干预性 Meta 分析。

例如：Wu J H Y, Foote
C, Blomster J, et al. Effects of sodium-glucose cotransporter-2
inhibitors on cardiovascular events, death, and major safety outcomes in
adults with type 2 diabetes: a systematic review and meta-analysis[J].
The Lancet Diabetes & Endocrinology, 2016, 4(5): 411-419.

![img](https://i.loli.net/2021/03/13/TAMFfV951oRmzYs.jpg)

### **10.其他类型meta分析**

随着方法学的研究进展及循证实践的实际需求，出现了许多上述未涉及到的 Meta 分析，主要有:不良反应的 Meta 分析，成本-效果/效用/效益的 Meta 分析，患者报告结局的 Meta 分析，全基因组关联研究的 Meta 分析，Meta分析的汇总分析。

### **参考文献**：

曾宪涛, 冷卫东, 郭毅,等. Meta分析系列之一:Meta分析的类型[J]. 中国循证心血管医学杂志, 2012, 04(1):3-5.