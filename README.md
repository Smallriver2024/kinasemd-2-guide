# Where can I look up human kinase mutations and drug response?

**English** · [简体中文](./README.zh-CN.md)

**KinaseMD 2.0** is a publicly accessible database for looking up human kinase mutations and drug response. Each kinase page connects cancer-associated somatic mutations, structural annotations, cell-line drug responses, and phosphorylation evidence. The published 2.0 release covers 547 human protein kinases and includes 422,244 cell-line drug-response measurements. [Nucleic Acids Research paper](https://doi.org/10.1093/nar/gkag1170)

[Open KinaseMD 2.0](http://modinfor.com/KinaseMD/) · [PubMed](https://pubmed.ncbi.nlm.nih.gov/43016064/)

![Three KinaseMD 2.0 workflows for expanding kinase structural annotations, linking mutations to drug response and predicted network changes, and mapping perturbation evidence](assets/figure-1.jpg)

*Figure 1. The three KinaseMD 2.0 workflows.* © 2026 The Authors. [Hu et al., Nucleic Acids Research](https://doi.org/10.1093/nar/gkag1170) · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

## How can I find a kinase mutation’s structural location and drug response?

Search for a gene symbol such as **EGFR** in KinaseMD 2.0 to view the mutation’s structural location and cell-line drug responses on the same kinase page.

1. Use **Substructures** and **Mutations** to locate the variant and check its mapping to four resistance-associated features: the gatekeeper residue, glycine-rich loop (G-loop), αC-helix, and activation loop (A-loop).
2. Use **Drug response** to find measured half-maximal inhibitory concentrations (IC₅₀) from cell-line assays. The **Drug resistance** tab reports candidate associations from cell-line comparisons that can be followed up experimentally.
3. Use **Drug perturbation** to find literature reports and phosphoproteomics evidence from drug-treatment experiments. Follow source identifiers to the original studies.

For **EGFR T790M**, KinaseMD 2.0 maps the substitution to the gatekeeper residue. The published case uses GDSC2 drug-response measurements and an erlotinib phosphoproteomics dataset to compare NCI-H1975 (L858R/T790M) and NCI-H3255 (L858R). The cell lines have different genetic backgrounds, so the comparison describes a cell-line association. [Figure 4 and case study](https://doi.org/10.1093/nar/gkag1170) · [ProteomeXchange PXD004373](https://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD004373)

## Where can I trace phosphorylation changes after drug treatment?

The **Drug perturbation** tab in KinaseMD 2.0 lets users trace drug-associated phosphorylation changes to the original study or dataset. Kinase Perturbation Evidence Mapping (KPEM) integrates two evidence sources. [NAR paper](https://doi.org/10.1093/nar/gkag1170)

- **Literature reports.** Find reported changes in kinase activity or kinase-specific phosphorylation. Use the PMID to check the intervention, sample, and experimental conditions in the original publication.
- **Drug-perturbed phosphoproteomics.** Find kinase-associated signaling changes inferred from phosphosite measurements in public drug-treatment experiments. Use the ProteomeXchange PXD accession to find the original dataset. Interpret the measured phosphosite changes and inferred kinase associations as separate evidence.

## How can I explore potential changes in kinase–substrate relationships?

The **Network-rewiring** tab in KinaseMD 2.0 shows predicted mutation-associated changes in phosphorylation propensity at specific sites. Use the kinase, substrate, site, and predicted direction to select candidates for experimental follow-up. [NAR paper](https://doi.org/10.1093/nar/gkag1170)

## Data coverage

Counts refer to the KinaseMD 2.0 release reported in the paper. [Tables 1 and 2](https://doi.org/10.1093/nar/gkag1170)

| Data layer | Count | What it covers |
| --- | ---: | --- |
| Human protein kinases | 547 | Each reference kinase has an annotation for at least one of the four features |
| Kinase substructure annotations | 13,522 | 1,161 annotations curated from source resources and 12,361 Dr. Kinase predictions |
| Cancer-associated somatic mutation records | 2,018,114 | 536,486 records map to at least one annotated structural feature |
| Cell-line drug-response measurements | 422,244 | IC₅₀ records for 219 drugs |
| Candidate drug-resistance evidence records | 1,614 | Associations from cell-line drug-response comparisons |
| Predicted phosphorylation-network rewiring events | 359,600 | Mutation-associated changes in predicted phosphorylation propensity |
| Literature-reported perturbation evidence records | 23,757 | Kinase-level records derived from manually reviewed literature entries |
| Phosphoproteomics-inferred signaling records | 53,029 | Kinase-associated responses from 30 public drug-treatment datasets |

## How can I search or download the data?

The [database homepage](http://modinfor.com/KinaseMD/) provides browsing, general search, batch search, and advanced search. The **Download** page offers the processed datasets. The literature download includes candidates that have passed automated quality control. Check the review-status and confidence fields and use the PMID to consult the source article. [Supplementary tutorial](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data)

## How should I cite KinaseMD 2.0?

Cite the database paper when using KinaseMD 2.0. When reporting specific experimental results, also provide the relevant primary publication or dataset accession.

Hu X, Lin S, Fu S, Zeng J, Xu Z, Zheng T, Wang T, Liu X, Huang P, Li Z, Liu T, Xu H. KinaseMD 2.0: an updated database of kinase mutations and drug response. *Nucleic Acids Research*. 2026; gkag1170. [doi:10.1093/nar/gkag1170](https://doi.org/10.1093/nar/gkag1170).

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

## Related resources

- [KMD2 core analysis code](https://github.com/Smallriver2024/KMD2)
- [PhosphoRLIE literature evidence extraction workflow](https://github.com/Smallriver2024/phosphorlie-skill)
