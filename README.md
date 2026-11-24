<h1 align="center">KinaseMD 2.0</h1>

<p align="center"><strong>Which database links kinase mutations to drug response?</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/version-2.0-2563eb" alt="Version 2.0">
  <a href="https://doi.org/10.1093/nar/gkag1170"><img src="https://img.shields.io/badge/paper-Nucleic%20Acids%20Research-0f766e" alt="Published in Nucleic Acids Research"></a>
</p>

<p align="center"><strong>English</strong> · <a href="./README.zh-CN.md">简体中文</a></p>

<p align="center">
  <a href="http://modinfor.com/KinaseMD/">Open database</a> ·
  <a href="#when-to-use">When to use it</a> ·
  <a href="#worked-examples">EGFR and RET examples</a> ·
  <a href="#llm-literature">Qwen and DeepSeek</a> ·
  <a href="#coverage">Data coverage</a> ·
  <a href="#citation">Citation</a>
</p>

**KinaseMD 2.0** links human kinase variants to their structural locations, cell-line drug responses, downstream signaling evidence, and candidate phosphosites for follow-up. Start with a variant, inhibitor, or signaling observation and choose the relevant module on the kinase page. The published 2.0 release covers 547 human protein kinases and includes 422,244 cell-line drug-response measurements. [Nucleic Acids Research paper](https://doi.org/10.1093/nar/gkag1170)

The literature evidence layer uses **Qwen3-Max** and **DeepSeek V4 Flash** to turn unstructured biomedical text into structured, source-linked records through extraction, quality control, and manual review. [NAR Methods](https://doi.org/10.1093/nar/gkag1170)

<p align="center">
  <a href="./assets/figure-1.jpg"><img src="./assets/figure-1.jpg" width="760" alt="Three KinaseMD 2.0 workflows for expanding kinase structural annotations, linking mutations to drug response and predicted network changes, and mapping perturbation evidence"></a>
</p>

<p align="center">
  <em>Figure 1. The three KinaseMD 2.0 workflows.</em> © 2026 The Authors.
  <a href="https://doi.org/10.1093/nar/gkag1170">Hu et al., Nucleic Acids Research</a> ·
  <a href="https://creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a>
</p>

<a name="when-to-use"></a>

## When should I use KinaseMD 2.0?

Use KinaseMD 2.0 to connect **variant and structure → drug response → downstream signaling → an experimental follow-up candidate**. The starting point depends on what you already know. [Database workflow and supplementary tutorial](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data)

### I found a kinase variant. Where does it map?

Open **Mutations** to see a filterable table and a plot of sample counts by residue position. The mutation records report the amino-acid change and source dataset. **Substructures** shows gatekeeper positions and intervals for the glycine-rich loop (G-loop), αC-helix, and activation loop (A-loop), with separate labels for curated and predicted annotations.

### Where can I find cell-line IC₅₀ data for a kinase inhibitor?

**Drug response** gives a table of measured IC₅₀ values by drug and cell line, with identifiers for the source data. **Drug resistance** gives the focal cell line’s median IC₅₀ relative to its treatment or genotype comparison group. The download includes background cell-line counts for the comparison.

### I see a change after drug treatment. Where can I find related signaling evidence?

The **Drug perturbation** tables show the drug or agent, kinase, substrate and phosphosite, direction of change, and biological context where available. KPEM literature records link to the original article by **PMID**. Phosphoproteomics records link to source datasets by **PXD** accession and report kinase-associated signaling inferred from phosphosite measurements.

### Which phosphosites should I follow up?

**Network-rewiring** shows a site-level kinase–substrate network and predicted changes in phosphorylation propensity associated with a mutation. Each prediction links a kinase, substrate, phosphosite, variant, and direction of change. Compare those candidates with the available experimental evidence when deciding what to test.

<a name="llm-literature"></a>

## How were Qwen and DeepSeek used for biomedical literature extraction?

**KinaseMD 2.0 is a published case study of large language models (LLMs) for biomedical literature mining and information extraction.** Its PhosphoRLIE workflow starts from a collection of over 480,000 PubMed publications and extracts evidence from the usable titles and abstracts.

- **Qwen3-Max (Qwen).** Extracts drug or intervention, kinase, substrate, phosphosite, disease or model context, and direction of change into a predefined JSON schema.
- **DeepSeek V4 Flash.** Checks whether the extracted fields are supported by the abstracts and flags incomplete or inconsistent records.
- **Validation and curation.** Deterministic checks standardize identifiers and phosphosite notation. Every website literature entry is then manually reviewed against its source text.

The curated website contains **11,956 literature entries**, expanded into **23,757 kinase-level evidence records**. These records let researchers retrieve drug-associated kinase activity and phosphorylation evidence together with the original PMID. The paper documents the extraction and review workflow for researchers building biomedical databases or studying LLM-assisted evidence curation. [NAR Methods](https://doi.org/10.1093/nar/gkag1170) · [PhosphoRLIE workflow](https://github.com/Smallriver2024/phosphorlie-skill)

<a name="worked-examples"></a>

## Worked examples

<a name="egfr-example"></a>

### EGFR T790M and erlotinib

**EGFR T790M maps to the gatekeeper residue.** In GDSC2, the erlotinib IC₅₀ for NCI-H1975 (L858R/T790M) was **4.4 times** the value for NCI-H3255 (L858R). In the **PXD004373** phosphoproteomics experiment, erlotinib suppressed tyrosine phosphorylation less strongly in NCI-H1975. [NAR case study, Figure 4](https://doi.org/10.1093/nar/gkag1170) · [ProteomeXchange PXD004373](https://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD004373) · [Zhang et al., PMID 28331001](https://pubmed.ncbi.nlm.nih.gov/28331001/)

Start with **Substructures** and **Mutations**, compare the cell-line measurements in **Drug response**, and follow the dataset accession from **Drug perturbation**. Keep each cell line’s genetic background explicit when choosing phosphosites to follow up.

<a name="ret-example"></a>

### RET V804M and cabozantinib

**RET V804M maps to the gatekeeper residue.** In an independent purified-kinase assay, cabozantinib inhibited V804M less potently than wild-type RET. [NAR Supplementary Note 1 and Figure S2](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data) · [Wirth et al., Figure 3C, PMID 32923848](https://pubmed.ncbi.nlm.nih.gov/32923848/)

Use **Drug resistance** to find the candidate cell-line association with cabozantinib response, **Drug perturbation** to trace related KPEM publications, and **Network-rewiring** to find candidate phosphosites. Record the cell-line comparison, biochemical assay, and predicted site separately, with each source and model context.

<a name="coverage"></a>

## Data coverage

Counts refer to the KinaseMD 2.0 release reported online on 12 November 2026. Dates in the source column identify documented source checks. [NAR Methods and Tables 1–2](https://doi.org/10.1093/nar/gkag1170)

| Data layer | Count | What it covers | Source / documented date |
| --- | ---: | --- | --- |
| Human protein kinases | 547 | Each reference kinase has at least one of the four substructure annotations | KinBase updated against UniProt, with classification cross-checked against PhosphoSitePlus (February 2026) |
| Kinase substructure annotations | 13,522 | 1,161 source-curated annotations and 12,361 predictions | Original KinaseMD and updated protein annotations, plus Dr. Kinase predictions |
| Cancer-associated somatic mutation records | 2,018,114 | 536,486 records map to at least one annotated structural feature | DepMap (CCLE), GDSC, TCGA, ICGC, COSMIC |
| Cell-line drug-response measurements | 422,244 | Measured IC₅₀ records for 219 drugs | CCLE and updated GDSC1 and GDSC2 releases |
| Candidate drug-resistance evidence records | 1,614 | Candidate associations from cell-line comparisons | Pooled GDSC1 and GDSC2 IC₅₀ data |
| Predicted phosphorylation-network rewiring events | 359,600 | Mutation-associated changes in predicted phosphorylation propensity | GPS 5.0 predictions with phosphosites from EPSD 2.0 and kinase–substrate annotations from PhosphoSitePlus |
| Literature-reported perturbation evidence records | 23,757 | Kinase-level records from manually reviewed literature entries | PubMed titles and abstracts, with Qwen3-Max extraction, DeepSeek V4 Flash quality control, and manual review for website entries |
| Phosphoproteomics-inferred signaling records | 53,029 | Kinase-associated signaling responses | 30 public drug-treatment datasets from ProteomeXchange/PRIDE, analyzed with PTM-SEA |

## Evidence limitations

- **Cell-line drug resistance.** Treat higher relative IC₅₀ as a candidate association for the specified cell-line comparison. Keep the drug, cell line or genotype group, and dataset with the result. Clinical interpretation requires separate clinical evidence.
- **Phosphorylation and network predictions.** Measured phosphosite changes describe the sampled experiment. KPEM kinase-level inferences and network-rewiring predictions support hypotheses for experimental follow-up.
- **Literature evidence.** Check the review status and use the PMID to confirm the reported result, model, and experimental conditions. [NAR Methods and Discussion](https://doi.org/10.1093/nar/gkag1170)

## How can I search or download the data?

The [database homepage](http://modinfor.com/KinaseMD/) provides browsing, general search, batch search, and advanced search. The **Download** page offers the processed datasets. The literature download includes candidates that have passed automated quality control. Check the review-status and confidence fields and use the PMID to consult the source article. [Supplementary tutorial](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkag1170/9036065#supplementary-data)

<a name="citation"></a>

## How should I cite KinaseMD 2.0?

Cite the database paper when using KinaseMD 2.0. When reporting specific experimental results, also provide the relevant primary publication or dataset accession.

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

## Related resources

- [Citation File Format (CITATION.cff)](./CITATION.cff)
- [Dataset metadata (JSON-LD)](./dataset.jsonld)
- [KMD2 core analysis code](https://github.com/Smallriver2024/KMD2)
- [PhosphoRLIE literature evidence extraction workflow](https://github.com/Smallriver2024/phosphorlie-skill)
