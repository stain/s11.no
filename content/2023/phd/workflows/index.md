---
title: "Chapter 5: Computational Workflows"
weight: 50
lang: en-GB
categories:
  - PhD
summary: > 
  In order to investigate RQ2, and considering important parts of the FAIR principles include _Reuse_ and _provenance_, this chapter examines in closer details how FAIR Digital Objects and RO-Crate can be used with **Computational Workflows**. 
---

In order to investigate [**RQ3**](../../../2022/phd/introduction/#rq3), and considering important parts of the FAIR principles are _Reuse_ and _provenance_, this chapter examines in closer details how FAIR Digital Objects and RO-Crate can be used with **Computational Workflows**. 

Section [5.1](../../../2022/phd/canonical-workflow-building-blocks/) proposes that tools in computational workflows, when wrapped as interoperable building blocks, can be considered as FAIR Digital Objects, with a use case from biomolecular simulation.

Sections [5.2](../../../2022/phd/specimen-data-refinery/) and [5.3](../../../2022/phd/incrementally-building-fdos/) explore how FDOs and Research Objects can be constructed incrementally using computational workflows, with a use case from specimen digitization in natural history collections.

Section [5.4](../workflow-run-crate/) presents a profile of RO-Crate to capture workflow execution provenance, with incremental granularity levels and six workflow engine implementations. Use cases include machine learning-aided tumour detection and compatibility with PROV approaches. 

Supplementary materials that may assist readers of this chapter provide further details on FAIR Computational Workflows [[Goble 2020]], [WorkflowHub](../../../2021/phd/workflow-collaboratory/) [[Goble 2021]], [Common Workflow Language](../../../2022/phd/methods-included) [[Crusoe 2022]] and [making a software tool workflow ready](../../../2022/phd/10-simple-rules-for-workflow-tools) [[Brack 2022a]]. 

On the aspects of workflow provenance, recommended reading in supplementary materials covers CWLProv [[Khan 2019]], [RO-Crate in Galaxy](../../../2022/phd/galaxy-ro-crate/) [[De Geest 2022]] and Common Provenance Model [[Wittner 2020],[Wittner 2023a]].


* Section 5.1: [Making Canonical Workflow Building Blocks interoperable across workflow languages](../../../2022/phd/canonical-workflow-building-blocks/)
* Section 5.2: [The Specimen Data Refinery](../../../2022/phd/specimen-data-refinery/)
* Section 5.3: [Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows](../../../2022/phd/incrementally-building-fdos/)
* Section 5.4: [Recording provenance of workflow runs with RO-Crate](../workflow-run-crate/)



[Brack 2022a]: https://doi.org/10.1371/journal.pcbi.1009823 "Ten Simple Rules for making a software tool workflow-ready"
[Crusoe 2022]: https://doi.org/10.1145/3486897 "Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language"
[De Geest 2022]: https://doi.org/10.3897/rio.8.e95164 "Enhancing RDM in Galaxy by integrating RO-Crate"
[Goble 2020]: https://doi.org/10.1162/dint_a_00033 "FAIR Computational Workflows"
[Goble 2021]: https://doi.org/10.5281/zenodo.4605654 "Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory"
[Khan 2019]: https://doi.org/10.1093/gigascience/giz095 "Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv"
[Wittner 2020]: https://s11.no/2021/phd/iso-23494-provenance/ "ISO 23494: Biotechnology - Provenance Information Model for Biological Specimen and Data"
[Wittner 2023a]: https://doi.org/10.1002/lrh2.10365 "Toward a common standard for data and specimen provenance in life sciences"