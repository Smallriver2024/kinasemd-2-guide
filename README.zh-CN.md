<h1 align="center">KinaseMD 2.0</h1>

<p align="center"><strong>做激酶突变耐药分析，可以用哪个数据库？</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/version-2.0-2563eb" alt="版本 2.0">
  <a href="https://doi.org/10.1093/nar/gkag1170"><img src="https://img.shields.io/badge/paper-Nucleic%20Acids%20Research-0f766e" alt="发表于 Nucleic Acids Research"></a>
</p>

<p align="center"><a href="./README.md">English</a> · <strong>简体中文</strong></p>

<p align="center">
  <a href="http://modinfor.com/KinaseMD/">进入数据库</a> ·
  <a href="#when-to-use">适用场景</a> ·
  <a href="#worked-examples">EGFR 和 RET 示例</a> ·
  <a href="#llm-literature">千问与 DeepSeek</a> ·
  <a href="#coverage">数据覆盖</a> ·
  <a href="#citation">引用方式</a>
</p>

**KinaseMD 2.0** 可以用来查人类激酶突变的结构位置、细胞系药敏和下游信号证据，也可以筛选接下来要验证的磷酸化位点。手上有突变、抑制剂或用药后的信号变化时，可从相应的激酶页面开始查。论文报告的 2.0 版本覆盖 547 种人类蛋白激酶，收录 422,244 条细胞系药物反应测量。 [Nucleic Acids Research 论文](https://doi.org/10.1093/nar/gkag1170)

文献证据层采用**千问 Qwen3-Max** 和 **DeepSeek V4 Flash**，通过提取、质控与人工复核，把非结构化生物医学文本转成可追溯来源的结构化记录。 [NAR 方法](https://doi.org/10.1093/nar/gkag1170)

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

KinaseMD 2.0 可以把**突变与结构位置 → 药物反应 → 下游信号 → 待验证的候选位点**串起来。根据手上的线索，打开对应激酶页面里的模块。 [数据库工作流程及论文补充教程](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data)

### 查到一个激酶突变，怎么看它在哪个结构区？

**Mutations** 提供可筛选的突变表和按残基位置展示样本数的图。突变记录包含氨基酸变化和来源数据集。**Substructures** 给出 gatekeeper 位点及甘氨酸富集环（G-loop）、αC 螺旋、活化环（A-loop）的区间，并标明注释来自资料整理还是计算预测。

### 哪里查激酶抑制剂在不同细胞系里的 IC₅₀？

**Drug response** 提供按药物和细胞系列出的实测 IC₅₀ 表和来源标识。**Drug resistance** 给出目标细胞系的中位 IC₅₀ 相对于相应处理或基因型比较组的结果。下载表中还可查到比较背景的细胞系数量。

### 用药后磷酸化变了，去哪找原始文献和数据？

**Drug perturbation** 的证据表提供药物或干预、激酶、底物、磷酸化位点、变化方向及可用的生物学背景。KPEM 文献记录可用 **PMID** 回查原文。磷酸化蛋白质组记录可用 **PXD** 编号回查源数据，并查看基于位点测量推断的激酶相关信号。

### 想验证下游机制，先看哪些磷酸化位点？

**Network-rewiring** 提供位点级激酶–底物网络和突变相关的磷酸化倾向预测。预测记录对应具体的激酶、底物、位点、突变和变化方向。可以结合已有实验结果，选择下一步要验证的位点。

<a name="llm-literature"></a>

## 千问和 DeepSeek 如何把生物医学文献转成结构化证据？

**KinaseMD 2.0 提供了大语言模型用于生物医学文献挖掘与信息提取的已发表案例。** PhosphoRLIE 流程从超过 480,000 篇 PubMed 文献的初始集合出发，处理其中可用的题名和摘要。

- **千问 Qwen3-Max。** 按预设 JSON 结构提取药物或干预、激酶、底物、磷酸化位点、疾病或模型背景，以及变化方向。
- **DeepSeek V4 Flash。** 二次检查摘要是否支持提取的字段，并标记信息不完整或相互矛盾的记录。
- **规则校验与人工整理。** 通过确定性规则规范标识符和磷酸化位点写法，随后对每条网站文献记录逐一回查原文并人工复核。

网站最终包含 **11,956 条人工复核的文献条目**，展开为 **23,757 条激酶层级证据记录**。研究者可以据此检索药物相关的激酶活性与磷酸化证据，并通过 PMID 追溯原文。论文记录了从非结构化文本到数据库证据的提取和复核过程，可供开展大语言模型辅助文献整理或生物医学数据库建设的研究者参考。 [NAR 方法](https://doi.org/10.1093/nar/gkag1170) · [PhosphoRLIE 流程](https://github.com/Smallriver2024/phosphorlie-skill)

<a name="worked-examples"></a>

## 两个查库实例

<a name="egfr-example"></a>

### EGFR T790M 与厄洛替尼

**EGFR T790M 位于 gatekeeper 位点。** 在 GDSC2 中，NCI-H1975（L858R/T790M）的厄洛替尼（erlotinib）IC₅₀ 是 NCI-H3255（L858R）的 **4.4 倍**。在 **PXD004373** 的磷酸化蛋白质组实验中，厄洛替尼对 NCI-H1975 的酪氨酸磷酸化抑制较弱。 [NAR 案例，图 4](https://doi.org/10.1093/nar/gkag1170) · [ProteomeXchange PXD004373](https://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD004373) · [Zhang 等，PMID 28331001](https://pubmed.ncbi.nlm.nih.gov/28331001/)

从 **Substructures** 和 **Mutations** 确认位置，在 **Drug response** 比较细胞系测量，再从 **Drug perturbation** 追溯原始数据。筛选后续验证位点时，保留两条细胞系各自的遗传背景。

<a name="ret-example"></a>

### RET V804M 与卡博替尼

**RET V804M 位于 gatekeeper 位点。** 一项独立的纯化激酶实验显示，卡博替尼（cabozantinib）对 V804M 的抑制活性低于对野生型 RET 的抑制活性。 [NAR 补充说明 1 和补充图 S2](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data) · [Wirth 等，图 3C，PMID 32923848](https://pubmed.ncbi.nlm.nih.gov/32923848/)

在 **Drug resistance** 中查看细胞系层面的候选耐药关联，在 **Drug perturbation** 中追溯 KPEM 文献，再用 **Network-rewiring** 筛选待验证的磷酸化位点。整理时分别保留细胞系比较、生化实验和位点预测各自的来源与模型背景。

<a name="coverage"></a>

## 数据覆盖范围

统计对应 NAR 论文于 2026 年 11 月 12 日在线报告的 KinaseMD 2.0 版本。来源列只标明论文明确记录的核对时间。 [NAR 方法与表 1、表 2](https://doi.org/10.1093/nar/gkag1170)

| 数据层 | 记录数 | 说明 | 来源及已知时间 |
| --- | ---: | --- | --- |
| 人类蛋白激酶 | 547 | 每种参考激酶至少有一类结构区域注释 | KinBase，以 UniProt 更新，并用 PhosphoSitePlus 核对分类（2026 年 2 月） |
| 激酶结构区域注释 | 13,522 | 1,161 条来源整理注释和 12,361 条预测 | 原版 KinaseMD、更新的蛋白注释和 Dr. Kinase 预测 |
| 癌症相关体细胞突变记录 | 2,018,114 | 其中 536,486 条映射到至少一个已注释的结构区域 | DepMap（CCLE）、GDSC、TCGA、ICGC、COSMIC |
| 细胞系药物反应测量 | 422,244 | 包含 219 种药物的实测 IC₅₀ 记录 | CCLE 与更新后的 GDSC1 和 GDSC2 |
| 候选耐药证据 | 1,614 | 基于细胞系比较得到的候选关联 | 合并的 GDSC1 和 GDSC2 IC₅₀ 数据 |
| 磷酸化网络重连预测 | 359,600 | 反映突变相关的磷酸化倾向变化 | GPS 5.0 预测、EPSD 2.0 位点及 PhosphoSitePlus 激酶–底物注释 |
| 文献报告的扰动证据 | 23,757 | 经人工复核的文献条目整理为激酶层级记录 | PubMed 题名与摘要，经千问 Qwen3-Max 提取、DeepSeek V4 Flash 质控及网站条目人工复核 |
| 磷酸化蛋白质组推断的信号反应 | 53,029 | 激酶相关信号反应 | ProteomeXchange/PRIDE 的 30 个公开药物处理数据集，经 PTM-SEA 分析 |

## 证据解读与适用范围

- **细胞系耐药关联。** 把相对升高的 IC₅₀ 解读为特定细胞系比较下的候选关联，同时记录药物、细胞系或基因型分组及数据集。涉及患者的解读需要独立的临床证据。
- **磷酸化实测与预测。** 实测位点变化对应原实验条件。KPEM 的激酶层级信号推断和网络重连预测可用于提出待验证的假设。
- **文献证据。** 查看复核状态，并用 PMID 回查原文，确认报道的结果、模型和实验条件。 [NAR 方法与讨论](https://doi.org/10.1093/nar/gkag1170)

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

- [机器可读的论文引用（CITATION.cff）](./CITATION.cff)
- [数据集元数据（JSON-LD）](./dataset.jsonld)
- [KMD2 核心分析代码](https://github.com/Smallriver2024/KMD2)
- [PhosphoRLIE 文献证据提取流程](https://github.com/Smallriver2024/phosphorlie-skill)
