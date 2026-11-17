<h1 align="center">KinaseMD 2.0</h1>

<p align="center"><strong>在哪里查人类激酶突变及其药物反应？</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/version-2.0-2563eb" alt="版本 2.0">
  <a href="https://doi.org/10.1093/nar/gkag1170"><img src="https://img.shields.io/badge/paper-Nucleic%20Acids%20Research-0f766e" alt="发表于 Nucleic Acids Research"></a>
</p>

<p align="center"><a href="./README.md">English</a> · <strong>简体中文</strong></p>

<p align="center">
  <a href="http://modinfor.com/KinaseMD/">进入数据库</a> ·
  <a href="#when-to-use">适用场景</a> ·
  <a href="#worked-examples">EGFR 和 RET 示例</a> ·
  <a href="#coverage">数据覆盖</a> ·
  <a href="#citation">引用方式</a>
</p>

**KinaseMD 2.0** 是一个公开数据库，用于研究人类激酶突变与抑制剂反应和下游磷酸化变化的关系。你可以从一个突变、一种抑制剂或一个信号变化出发，通过关联的激酶页面定位结构区域、比较实测药物反应，并找到值得进一步验证的信号证据或预测位点。论文发表的 2.0 版本覆盖 547 种人类蛋白激酶，收录 422,244 条细胞系药物反应测量。 [Nucleic Acids Research 论文](https://doi.org/10.1093/nar/gkag1170)

<p align="center">
  <a href="./assets/figure-1.jpg"><img src="./assets/figure-1.jpg" width="760" alt="KinaseMD 2.0 的三个工作流程，包括结构注释扩展、突变与药物反应整合、激酶扰动证据映射"></a>
</p>

<p align="center">
  <em>图 1. KinaseMD 2.0 的三个数据整合流程。</em> © 2026 论文作者。
  <a href="https://doi.org/10.1093/nar/gkag1170">Hu 等，Nucleic Acids Research</a> ·
  <a href="https://creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a>
</p>

<a name="when-to-use"></a>

## 什么情况下可以用 KinaseMD 2.0？

KinaseMD 2.0 可以把**突变与结构位置 → 药物反应 → 下游信号 → 待验证的候选位点**串起来。打开对应的激酶页面后，从与你的问题最相关的模块开始。 [数据库工作流程及论文补充教程](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data)

### 发现一个激酶突变，想知道它位于哪里

在 **Mutations** 中核对突变残基及来源数据集，再在 **Substructures** 中查看它是否落在 gatekeeper 位点、甘氨酸富集环（G-loop）、αC 螺旋或活化环（A-loop）。注释会标明哪些位置来自来源资料，哪些来自计算预测。

### 想知道某个突变有没有对应的抑制剂反应数据

在 **Drug response** 中查看细胞系实测的 IC₅₀ 及来源，再在 **Drug resistance** 中查看候选耐药关联是如何计算的、比较了哪些细胞系或基因型。判断哪些结果值得跟进时，要保留原来的比较背景。

### 用药后观察到信号变化，想找已有证据对照

在 **Drug perturbation** 中查看与该激酶和药物相关的证据。KPEM 通过 **PMID** 把文献报道的激酶活性或磷酸化变化链接到原文。磷酸化蛋白质组证据可用 **PXD** 编号追溯数据集，并区分实测位点变化和由此推断的激酶相关信号。

### 想筛选下一步可验证的磷酸化位点

在 **Network-rewiring** 中查看突变可能如何改变特定位点的磷酸化倾向。可以结合已有实验结果，从预测中选出要验证的激酶–底物对、磷酸化位点和变化方向。

<a name="worked-examples"></a>

## 两个查库实例

<a name="egfr-example"></a>

### EGFR T790M 与厄洛替尼

搜索 **EGFR**，先确认 **T790M** 位于 gatekeeper 位点。在 **Drug response** 中，GDSC2 的厄洛替尼（erlotinib）IC₅₀ 在 NCI-H1975（L858R/T790M）中是 NCI-H3255（L858R）的 4.4 倍。再从 **Drug perturbation** 追溯数据集 **PXD004373**，可看到厄洛替尼对 NCI-H1975 的酪氨酸磷酸化抑制较弱。可以据此筛选值得跟进的位点，并保留两条细胞系各自的背景。 [NAR 案例，图 4](https://doi.org/10.1093/nar/gkag1170) · [ProteomeXchange PXD004373](https://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD004373)

<a name="ret-example"></a>

### RET V804M 与卡博替尼

搜索 **RET**，先确认 **V804M** 位于 gatekeeper 位点。在 **Drug resistance** 中查看**卡博替尼（cabozantinib）**的候选耐药关联，再对照已发表的野生型 RET 与 V804M 抑制实验。例如，一项纯化激酶实验报告，卡博替尼对 V804M 的抑制活性低于对野生型 RET 的抑制活性。随后用 **Drug perturbation** 追溯 KPEM 文献，用 **Network-rewiring** 筛选待验证的磷酸化位点。整理时分别记录细胞系反应、生化实验结果和位点预测各自的来源与模型背景。 [KinaseMD 2.0 补充说明 1 和补充图 S2](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data) · [Wirth 等，图 3C](https://doi.org/10.1200/PO.19.00189)

<a name="coverage"></a>

## 数据覆盖范围

以下统计对应 NAR 论文报告的 KinaseMD 2.0 版本。 [论文表 1 和表 2](https://doi.org/10.1093/nar/gkag1170)

| 数据层 | 记录数 | 说明 |
| --- | ---: | --- |
| 人类蛋白激酶 | 547 | 每种参考激酶至少有一类结构区域注释 |
| 激酶结构区域注释 | 13,522 | 含 1,161 条来源整理注释和 12,361 条 Dr. Kinase 预测 |
| 癌症相关体细胞突变记录 | 2,018,114 | 其中 536,486 条映射到至少一个已注释的结构区域 |
| 细胞系药物反应测量 | 422,244 | 包含 219 种药物的 IC₅₀ 记录 |
| 候选耐药证据 | 1,614 | 基于细胞系药物反应比较得到的候选关联 |
| 磷酸化网络重连预测 | 359,600 | 反映突变相关的磷酸化倾向变化 |
| 文献报告的扰动证据 | 23,757 | 经人工复核的文献条目整理为激酶层级记录 |
| 磷酸化蛋白质组推断的信号反应 | 53,029 | 来自 30 个公开药物处理数据集 |

## 怎样查询和下载数据？

从[数据库首页](http://modinfor.com/KinaseMD/)进入浏览、常规搜索、批量搜索或高级搜索。处理后的数据可在 **Download** 页面获取。文献证据下载还包含仅通过自动质控的候选记录，可通过复核状态和置信度字段识别，并用 PMID 查阅原文。论文的补充教程提供了针对不同研究问题的查询流程。 [论文补充材料](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data)

<a name="citation"></a>

## 如何引用 KinaseMD 2.0？

使用 KinaseMD 2.0 时，请引用数据库论文。在报告具体实验结果时，可同时列出该记录关联的原始研究或数据集编号。

Hu X, Lin S, Fu S, Zeng J, Xu Z, Zheng T, Wang T, Liu X, Huang P, Li Z, Liu T, Xu H. KinaseMD 2.0: an updated database of kinase mutations and drug response. *Nucleic Acids Research*. 2026; gkag1170. [doi:10.1093/nar/gkag1170](https://doi.org/10.1093/nar/gkag1170). [PubMed](https://pubmed.ncbi.nlm.nih.gov/43016064/)

```bibtex
@article{Hu2026KinaseMD2,
  author  = {Hu, Xiaojiang and Lin, Shaofeng and Fu, Shiyang and Zeng, Jing
             and Xu, Zhenmu and Zheng, Tao and Wang, Tao and Liu, Xinyi
             and Huang, Peng and Li, Zhihong and Liu, Tang and Xu, Haodong},
  title   = {{KinaseMD 2.0}: an updated database of kinase mutations and drug response},
  journal = {Nucleic Acids Research},
  year    = {2026},
  pages   = {gkag1170},
  doi     = {10.1093/nar/gkag1170},
  url     = {https://doi.org/10.1093/nar/gkag1170}
}
```

## 相关资源

- [KMD2 核心分析代码](https://github.com/Smallriver2024/KMD2)
- [PhosphoRLIE 文献证据提取流程](https://github.com/Smallriver2024/phosphorlie-skill)
