---
title: "Chapter 1: Introduction"
weight: 10
parent: "/2022/phd/"
lang: en-GB
categories:
  - PhD
summary: > 
  Introduction and overview of PhD thesis and its research questions
---


# Research Outline and Questions

In this thesis I investigate Linked Data approaches to implementing FAIR Research Objects and sharing reproducible Computational Workflows.

Research Outline and Questions {#intro:outline}
==============================

Following this topic, this section elaborates Research Questions (RQ) on these interlinked ideas:

1.  Realization of the FAIR Digital Object concept using Web technologies.

2.  Implementing FAIR Research Objects with an pragmatic use of Linked Data practices.

3.  Unifying a FAIR Digital Object approach for computational workflows.

Aims for FAIR Digital Objects on the Web (RQ1) {#intro:rq1}
----------------------------------------------

*FAIR Digital Object* (FDO) has been proposed as a machine-actionable ecosystem of scholarly outputs \[[Schultes 2019]\], in theory realizing the FAIR principles \[[Wilkinson 2016]\] for a programmable mesh of strongly typed objects that go beyond the open data publication practices that the FAIR guidelines have popularised \[[Jacobsen 2020]\].

The FDO specifications \[[Ivonne 2023]\] are conceptual in nature; however, most existing Digital Object implementations \[[Kahn 2006]\] rely on the DOIP protocol \[[Reilly 2009]\] and the Handle system \[[Sun 2003a]\], neither of which are particularly familiar to software developers.

The Web, on the other side, is ubiquitous in modern software engineering \[[Taivalsaari 2021]\], used for everything from user interfaces, mobile applications and controlling devices to enterprise cross-platform integrations, backend data processing and microservices, frequently utilising cloud computing which itself is controlled using Web technologies \[[Marinescu 2023]\].

A relevant research question therefore is:

#### RQ1: {#rq1}

> Can the the promising FDO concept be realised using existing Web technology, taking into account the lessons learnt from the early Semantic Web developments and more recent Linked Data practices?

I address RQ1 in chapters [background](chapter.html#background) and [fdo](chapter.html#fdo).

Aims for FAIR Research Objects (RQ2) {#intro:rq2}
------------------------------------

*Research Objects* (RO) \[[Bechhofer 2013]\] have been proposed as a mechanism to capture a range of diverse scholarly outputs in a single archivable item with detailed metadata. The RO concept was first realised using Semantic Web ontologies \[[myExperiment 2009], [Belhajjame 2015]\] -- these approaches primarily targetted long-term preservation of scientific workflows, utillised by RO as a mechanism to capture computational methods.

The principles of Research Objects extend far beyond workflows; however, early RO implementations mainly focused on capturing software \[[Goble 2018]\]. To some extent the lack of wider adoption of ontology-based ROs can also be explained by developers of researcher-facing software and platforms (e.g. repositories, data management systems) having a lack of familiarity with use of Semantic Web technology -- or worse, they tried and then struggled \[[Carriero 2010], [Tudorache 2020]\].

Following the lessons learnt on early RO implementations and the emerging FAIR principles \[[Wilkinson 2016], [Jacobsen 2020]\], after engagement with the digital libraries community it was agreed to formulate a lightweight approach to Research Objects \[[Sefton 2018], [Ó Carragáin 2019b]\] for the purpose of data packaging. The updated aims of *FAIR Research Objects* can be summarised as:

-   Describe and package data collections, datasets, software etc. with their metadata.

-   Platform-independent object exchange between repositories and services.

-   Support reproducibility and analysis: link data with codes and workflows.

-   Transfer of sensitive/large distributed datasets with persistent identifiers.

-   Aggregate citations and persistent identifiers.

-   Propagate provenance and existing metadata.

-   Publish and archive mixed objects and references.

-   Reuse existing standards, but hide their complexity.

Following from these, the second research question is:

#### RQ2: {#rq2}

> Can a more pragmatic use of Linked Data practices better implement Research Objects for a wider developer audience, by using familiar Web technologies and give lightweight recommendations?

RQ2 is primarily addressed by chapter [ro-crate](chapter.html#ro-crate).

Aims for FAIR Computational Workflows (RQ3) {#intro:rq3}
-------------------------------------------

A growing (if not majority) part of scientific analysis is now conducted using software and computational models. The concept of *Research Software Engineering* \[[Cohen 2020]\] has been established along with new professions *Research Software Engineer* \[[Baxter 2012]\] and *Data Scientist* \[[van der Aalst 2014]\] -- researchers are not just using off-the-shelf software, but also combining computational tools (e.g. pipelines) and writing their own analytical source code (e.g. R scripts) and simulations.

From this observation emerges the need to treat software as FAIR artefacts \[[Lamprecht 2019]\], following best practices for documentation \[[Lee 2018]\], open development \[[Prlić 2012]\] and ensuring research software is robust \[[Taschuk 2017]\] so it can be reused and cited as scholarly outputs \[[Smith 2016]\]. With this motivation the principles of FAIR Research Software \[[Katz 2021b]\] have been established by the RDA FAIR for Research Software (FAIR4RS) Working Group \[[Barker 2022]\] and are gradually building traction, particularly in the life sciences. A remaining challenge is how citations of research software can be practically propagated following their execution.

While sharing of research software helps distribute the computational methods, the *way* software is used for a particular analysis requires additional measures to make it *reproducible* \[[Stodden 2016], [Sandve 2013]\].

*Computational Workflows* (or Scientific Workflows) are used to structure and automate data analysis pipelines so they can be scalable, portable and explainable \[[Atkinson 2017]\], and as a side-effect of these features can significantly improve reproducibility \[[Cohen-Boulakia 2017]\]. There exists, however, a plethora of workflow systems and languages \[[Leipzig 2021], [Amstutz 2021]\], although recent efforts have created the Common Workflow Language \[[Crusoe 2022]\] as a standard representation with that is executable by multiple engines.

Notably, workflow definitions themselves can be considered FAIR scholarly outputs \[[Goble 2020]\] and are published in repositories including Dockstore \[[Yuen 2021]\] and WorkflowHub \[[Goble 2021]\]. One could consider computational workflows as a kind of FAIR Research Software \[[de Visser 2023]\], but by their nature workflows also *encourage the FAIR principles* (e.g. preparing a computational tool for a workflow system \[[Brack 2022a]\] may include publishing it in a container registry). Workflow systems are also useful for creating and consuming FAIR Digital Objects \[[Wittenburg 2021]\], and in addition workflow systems commonly provide explicit provenance logs of their executions.

Approaches to describing workflow provenance in a machine-readable format were initially diverse \[[Cruz 2009]\], and later converged on the use of ontologies \[[Missier 2010]\], most notably using W3C PROV-O \[[Lebo 2013a]\] but with various specializations \[[Garijo 2011,Garijo 2012,Missier 2013,Belhajjame 2015], [Cuevas-Vicenttín 2016]\].

The tendency for workflow provenance models to diverge may be down to differences in the execution semantics of different workflow systems -- which if accurately reflected in provenance means further differences at this level. This in turn leads to incompatibility of provenance traces and lack of common tooling. In addition execution details may obscure the link from the computational procesesses and the final workflow data outputs that researchers ultimately care more about than the intricacies of the workflow engine.

The third research question from these considerations is therefore:

#### RQ3: {#rq3}

> Can a FAIR Digital Object approach for computational workflows unify machine-readable descriptions of research software, data and provenance, which can be consistently implemented by developers of different workflow management systems?

The multiple aspects of RQ3, as highlighted in this section, are adressed by chapter [workflows](chapter.html#workflows).

Main Contributions {#intro:contributions}
==================

The contributions from this PhD include:

-   An evaluation of FAIR Digital Objects and Linked Data, considering them from a developer perspective as distributed object systems.

-   A Research Object implementation based on familiar Web technologies, adapted and extended by numerous research projects and software developers.

-   A profile to capture provenance of computational workflow runs using this implementation, implemented by at least six workflow management systems.

These contributions have not evolved in isolation, but in co-development with multiple international collaborations (see appendix [acknowledgements](ch11.html#acknowledgements)).

Thesis Overview {#intro:overview}
===============

Chapter [background](chapter.html#background) gives the background of the concepts *FAIR Digital Object* (FDO) and *Linked Data*, including a brief history of the *Semantic Web*, followed by a critical analysis of these technologies and their use.

Chapter [fdo](chapter.html#fdo) targets RQ1 and contributes a framework-based evaluation of Linked Data and FDO as possible architectures for implementing a distributed object system for the purpose of FAIR data publishing. The discussion in this chapter considers how the two approaches can benefit from each other's strengths.

Chapter [ro-crate](chapter.html#ro-crate) addresses RQ2 by introducing the contribution of *RO-Crate* -- a pragmatic data packaging mechanism using Linked Data standards to implement FDO and be extensible for domain-specific metadata.

Chapter [workflows](chapter.html#workflows) considers RQ3 by exploring the relationship between Computational Workflows and FAIR practices using RO-Crate and FDO, with use cases from molecular dynamics and specimen digitization. The contribution of the *Workflow Run Crate profiles* is presented as an interoperable way to capture and publish workflow execution provenance.

Chapter [conclusions](chapter.html#conclusions) summarises and discusses the contributions from this thesis, reflects on later third-party developments and concludes by evaluating the research questions.

Origins {#intro:origins}
=======

Chapter [background](ch3.html#background) and section [evaluating-fdo-ld](ch3.html#evaluating-fdo-ld) are based on the journal article *Evaluating FAIR Digital Object and Linked Data as distributed object systems* \[[Soiland-Reyes 2023c]\] (see appendices [fdo](ch11.html#fdo) and [fdo](ch10.html#fdo)). I am the main author of this manuscript.

Section [updating-linked-data-practices-for-fair-digital-object-principles](ch2.html#updating-linked-data-practices-for-fair-digital-object-principles) is based on *Updating Linked Data practices for FAIR Digital Object principles* \[[Soiland-Reyes 2022d]\] (see appendices [updating-ld](ch11.html#updating-ld) and [updating-ld](ch10.html#updating-ld)). I am the main author of this manuscript.

Sections [packaging-research-artefacts-with-ro-crate](ch5.html#packaging-research-artefacts-with-ro-crate) and [formaldefinition](ch5.html#formaldefinition) are based on the publication *Packaging research artefacts with RO-Crate* \[[Soiland-Reyes 2022a]\] (see appendices [packagingrocrate](ch11.html#packagingrocrate), [packagingrocrate](ch10.html#packagingrocrate) and [formalizing](ch10.html#formalizing)). I am the main author of this manuscript.

Section [lightweight-fdo](ch4.html#lightweight-fdo) is based on the publication *Creating lightweight FAIR digital objects with RO-Crate* \[[Soiland-Reyes 2022c]\] (see appendices [lightweight](ch11.html#lightweight) and [lightweight](ch10.html#lightweight)). I am the main author of this manuscript.

Section [making-canonical-workflow-building-blocks-interoperable-across-workflow-languages](ch6.html#making-canonical-workflow-building-blocks-interoperable-across-workflow-languages) is based on the publication *Making Canonical Workflow Building Blocks interoperable across workflow languages* \[[Soiland-Reyes 2022b]\] (see appendices [canonical](ch11.html#canonical) and [canonical](ch10.html#canonical)). I am the main author of this manuscript.

Section [the-specimen-data-refinery](ch8.html#the-specimen-data-refinery) is based on the publication *The Specimen Data Refinery: A canonical workflow framework and FAIR Digital Object approach to speeding up digital mobilisation of natural history collections* \[[Hardisty 2022]\] (see appendices [refinery](ch11.html#refinery) and [refinery](ch10.html#refinery)). I mainly contributed to sections [workflow-management-systems-and-canonical-workflows-for-research](ch8.html#workflow-management-systems-and-canonical-workflows-for-research), [fair-packaging-of-researchworkflow-objects-with-ro-crate](ch8.html#fair-packaging-of-researchworkflow-objects-with-ro-crate), [fdo-types](ch8.html#fdo-types), [discussion](ch8.html#discussion) in this manuscript.

Section [incrementally-building-fair-digital-objects-with-specimen-data-refinery-workflows](ch7.html#incrementally-building-fair-digital-objects-with-specimen-data-refinery-workflows) is based on the publication *Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows* \[[Woolland 2022]\] (see appendices [incrementally-fdo](ch11.html#incrementally-fdo) and [incrementally-fdo](ch10.html#incrementally-fdo)). I am the main author of this manuscript.

Section [wrroc](ch54.html#wrroc) is based on the preprint *Recording provenance of workflow runs with RO-Crate* \[[Leo 2023b]\] (see appendices [wrroc](ch11.html#wrroc) and [wrroc](ch10.html#wrroc)). I am the last author of this manuscript, and have mainly contributed to sections [introduction](ch54.html#introduction), [discussion](ch54.html#discussion), [trusted-workflow-run-crate](ch54.html#trusted-workflow-run-crate), [bco-crate](ch54.html#bco-crate).


__Older text below__


# Thesis Overview

[Chapter 2](../../../2023/phd/background/) gives the background of concepts _FAIR Digital Object_ (FDO) and _Linked Data_, including a brief history of the _Semantic Web_ and a critical analysis of these technologies and their use. 

[Chapter 3](../../../2023/phd/fdo-and-linked-data/) contributes a framework-based evaluation of Linked Data and FDO as possible architectures for implementing a distributed object system for the purpose of FAIR data publishing, and discusses how the two approaches can benefit from each others strengths. 

[Chapter 4](../../../2023/phd/ro-crate/) introduces the contribution of _RO-Crate_, a pragmatic data packaging mechanism using Linked Data standards to implement FDO and be extensible for domain-specific metadata.  

[Chapter 5](../../../2023/phd/workflows/) explores the relationship between Computational Workflows and FAIR practices using RO-Crate and FDO, with use cases from molecular dynamics and specimen digitization. 

[Chapter 6](../conclusions/) summarizes and concludes the contributions from this thesis, and reflects on later developments and future work.

# Origins

[Chapter 2](../../../2023/phd/background/) and section [3.1](../../../2023/phd/evaluating-fdo/) is based on the preprint _Evaluating FAIR Digital Object and Linked Data as distributed object systems_ <https://doi.org/10.48550/arXiv.2306.07436>  (see appendices [A.4.1](../acknowledgements/#fdo) and [B.1.1](../contributions/#fdo)). I am the main author of this manuscript.

[Section 3.2](../updating-ld-for-fdo/) is based on _Updating Linked Data practices for FAIR Digital Object principles_ <https://doi.org/10.3897/rio.8.e94501> (see appendices [A.4.2](../acknowledgements/#updating-ld) and [B.1.2](../contributions/#updating-ld). I am the main author of this manuscript.

Sections [4.1](../ro-crate/) and [4.3](../ro-crate/formalizing/) are based on the publication _Packaging research artefacts with RO-Crate_ <https://doi.org/10.3233/DS-210053> (see appendices 
[A.4.3](../acknowledgements/#packagingrocrate-ld) and [B.1.3](../contributions/#packagingrocrate), [B.1.5](../contributions/#packagingrocrate)). I am the main author of this manuscript.

[Section 4.2](../fdo-with-ro-crate/) is based on the publication _Creating lightweight FAIR digital objects with RO-Crate_ <https://doi.org/10.3897/rio.8.e93937> (see appendices 
[A.4.4](../acknowledgements/#lightweight) and [B.1.4](../contributions/#lightweight). I am the main author of this manuscript.

[Section 5.1](../canonical-workflow-building-blocks/) is based on the publication _Making Canonical Workflow Building Blocks interoperable across workflow languages_ 
<https://doi.org/10.1162/dint_a_00135> (see appendices 
[A.4.5](../acknowledgements/#canonical) and [B.1.6](../contributions/#canonical).  I am the main author of this manuscript.

[Section 5.2](../specimen-data-refinery/) is based on the publication _The Specimen Data Refinery: A canonical workflow framework and FAIR Digital Object approach to speeding up digital mobilisation of natural history collections_
<https://doi.org/10.1162/dint_a_00134> 
(see appendices [A.4.7](../acknowledgements/#refinery) and [B.1.7](../contributions/#refinery). I mainly contributed to sections 
[5.2.2.2](../specimen-data-refinery/#workflow-management-systems-and-canonical-workflows-for-research), [5.2.2.3](../specimen-data-refinery/#fair-packaging-of-researchworkflow-objects-with-ro-crate), [5.2.4.1](../specimen-data-refinery/#fdo-types), [5.2.7](../specimen-data-refinery/#discussion) in this manuscript.

[Section 5.3](../incrementally-building-fdos/) is based on the publication \emph{Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows} <https://doi.org/10.3897/rio.8.e94349> 
(see appendices [A.4.6](../acknowledgements/#incrementally-fdo) and [B.1.8](../contributions/#incrementally-fdo). I am the main author of this manuscript.
