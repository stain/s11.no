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

Science is increasingly dependent on digital means, with computational methods used in almost all aspects of research, ranging from digitising plant specimens in herbariums [[Thiers 2016]], to molecular simulations of protein bindings for pharmacetical drug design [[Śledź 2018]].

Academics, government agencies and industry are now commonly making data publicly available under open licenses, feeding a broadening democratisation of science [[Kitchin 2021]] across social-economic borders[^10], and expanding the potential for new multidiciplinary fields, commercialisation, citizen engagement and wider societal benefits [[Bisol 2014]].

[^10]: Although current open data practices do not benefit the Global South equally [[Serwadda 2018]].


Cloud-based computational infrastructures for “big data” are readily available for use with a wide range of open source software, enabling large scale secondary data analysis and detailed visualisations of research outputs [[Hashem 2015]].

However, in this accelerated ecosystem of Open Science, concerns have been raised about replicability of research findings [[Ioannidis 2005]], flagged as a “reproducibility crisis” [[Baker 2016]]. It is perhaps then ironic that the increased use of computers—with their inherently repeatable execution mechanisms—can negatively contribute to this crisis, as research publications do *not* commonly provide sufficient computational details such as code, data formats or software versions [[Stodden 2016]].

The recent increased focus on *reusability* of digital data and computational methods has been given the attention of funders and research communities. This led to the development of the <abbr title="Findable, Accessible, Interoperable, Reusable">FAIR</abbr> principles for making data and their metadata *Findable, Accessible, Interoperable and Reusable*, e.g. retrievable and understandable for programmatic use [[Wilkinson 2016]].

One technological measure for achieving FAIR is using Linked Data (<abbr>LD</abbr>), a set of practices for publishing and relating data on the Web using controlled vocabularies [[Berners-Lee 2006]], serialised using formats of the Resource Description Framework (<abbr>RDF</abbr>) [[Schreiber 2014]] and organised using the Web Ontology Language (<abbr>OWL</abbr>) [[W3C 2012]], however the combined complexity of these underlying *Semantic Web* technologies can hamper adoption by developers [[Klímek 2019]] and researchers who want to make their data available.

Computational workflows have been developed as ways to structure execution of software tools, for instance for scientific data analysis, so that, by using a Workflow Management system (<abbr>WfMS</abbr>), tool execution is reproducible, scalable and documented. For these purposes, workflow systems have become heavily adopted by some research fields such as life sciences, however the workflow definitions themselves are not yet commonly shared as part of scholarly outputs, and only gradually being recognised as a form of *FAIR Research Software* [[Katz 2021b]].

Research Object (<abbr>RO</abbr>) is a concept proposed for sharing composites of research artefacts, together with their history and related resources such as software, workflows and external references [[Bechhofer 2013]]. The initial implementations of RO heavily used ontologies, and required a tight integration with the workflow management systems, but has great potential for FAIR publication of any scholarly outputs.

The FAIR principles are widely referenced in Open Science literature, and nominally adapted by many research data repositories and funder policies—but how can they better be translated into practice by typical researcher software developers which may be using workflow systems, but not know any Linked Data technologies?

This is the focus for this thesis, where I investigate *Linked Data approaches to implementing FAIR Research Objects and sharing reproducible Computational Workflows*.

# Motivation – achieving FAIR research outputs



## FAIR Principles

## Existing approaches to implementing FAIR

## FAIR Digital Objects (FDO)

## Research Software and Computational Workflows

## Gathering scholarly outputs in Research Objects


-------------


# Research Outline and Questions {#intro:outline}

In this thesis I investigate Linked Data approaches to implementing FAIR Research Objects and sharing reproducible Computational Workflows.


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

I address RQ1 in [Chapter 2](../../../2023/phd/background/) and [Chapter 3](../../../2023/phd/fdo-and-linked-data/).


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

RQ2 is primarily addressed by [Chapter 4](../../../2023/phd/ro-crate/).


Aims for FAIR Computational Workflows (RQ3) {#intro:rq3}
-------------------------------------------

A growing (if not majority) part of scientific analysis is now conducted using software and computational models. The concept of *Research Software Engineering* \[[Cohen 2020]\] has been established along with new professions *Research Software Engineer* \[[Baxter 2012]\] and *Data Scientist* \[[van der Aalst 2014]\] -- researchers are not just using off-the-shelf software, but also combining computational tools (e.g. pipelines) and writing their own analytical source code (e.g. R scripts) and simulations.

From this observation emerges the need to treat software as FAIR artefacts \[[Lamprecht 2019]\], following best practices for documentation \[[Lee 2018]\], open development \[[Prlić 2012]\] and ensuring research software is robust \[[Taschuk 2017]\] so it can be reused and cited as scholarly outputs \[[Smith 2016]\]. With this motivation the principles of FAIR Research Software \[[Katz 2021b]\] have been established by the RDA FAIR for Research Software (FAIR4RS) Working Group \[[Barker 2022]\] and are gradually building traction, particularly in the life sciences. A remaining challenge is how citations of research software can be practically propagated following their execution.

While sharing of research software helps distribute the computational methods, the *way* software is used for a particular analysis requires additional measures to make it *reproducible* \[[Stodden 2016], [Sandve 2013]\].

*Computational Workflows* (or Scientific Workflows) are used to structure and automate data analysis pipelines so they can be scalable, portable and explainable \[[Atkinson 2017]\], and as a side-effect of these features can significantly improve reproducibility \[[Cohen-Boulakia 2017]\]. There exists, however, a plethora of workflow systems and languages \[[Leipzig 2021], [Amstutz 2021]\], although recent efforts have created the Common Workflow Language \[[Crusoe 2022]\] as a standard representation with that is executable by multiple engines.

Notably, workflow definitions themselves can be considered FAIR scholarly outputs \[[Goble 2020]\] and are published in repositories including Dockstore \[[Yuen 2021]\] and WorkflowHub \[[Goble 2021]\]. One could consider computational workflows as a kind of FAIR Research Software \[[de Visser 2023]\], but by their nature workflows also *encourage the FAIR principles* (e.g. preparing a computational tool for a workflow system \[[Brack 2022a]\] may include publishing it in a container registry). Workflow systems are also useful for creating and consuming FAIR Digital Objects \[[Wittenburg 2022a]\], and in addition workflow systems commonly provide explicit provenance logs of their executions.

Approaches to describing workflow provenance in a machine-readable format were initially diverse \[[Cruz 2009]\], and later converged on the use of ontologies \[[Missier 2010]\], most notably using W3C PROV-O \[[Lebo 2013a]\] but with various specializations \[[Garijo 2011], [Garijo 2012], [Missier 2013], [Belhajjame 2015], [Cuevas-Vicenttín 2016]\].

The tendency for workflow provenance models to diverge may be down to differences in the execution semantics of different workflow systems -- which if accurately reflected in provenance means further differences at this level. This in turn leads to incompatibility of provenance traces and lack of common tooling. In addition execution details may obscure the link from the computational procesesses and the final workflow data outputs that researchers ultimately care more about than the intricacies of the workflow engine.

The third research question from these considerations is therefore:

#### RQ3: {#rq3}

> Can a FAIR Digital Object approach for computational workflows unify machine-readable descriptions of research software, data and provenance, which can be consistently implemented by developers of different workflow management systems?

The multiple aspects of RQ3, as highlighted in this section, are adressed by [Chapter 5](../../../2023/phd/workflows/).


Main Contributions {#intro:contributions}
==================

The contributions from this PhD include:

-   An evaluation of FAIR Digital Objects and Linked Data, considering them from a developer perspective as distributed object systems.
-   A Research Object implementation based on familiar Web technologies, adapted and extended by numerous research projects and software developers.
-   A profile to capture provenance of computational workflow runs using this implementation, implemented by at least six workflow management systems.

These contributions have not evolved in isolation, but in co-development with multiple international collaborations (see [Appendix A](../acknowledgements/#acknowledgements)).

Thesis Overview {#intro:overview}
===============

[Chapter 2](../../../2023/phd/background/) gives the background of the concepts *FAIR Digital Object* (FDO) and *Linked Data*, including a brief history of the *Semantic Web*, followed by a critical analysis of these technologies and their use.

[Chapter 3](../../../2023/phd/fdo-and-linked-data/) targets RQ1 and contributes a framework-based evaluation of Linked Data and FDO as possible architectures for implementing a distributed object system for the purpose of FAIR data publishing. The discussion in this chapter considers how the two approaches can benefit from each other's strengths.

[Chapter 4](../../../2023/phd/ro-crate/) addresses RQ2 by introducing the contribution of *RO-Crate* -- a pragmatic data packaging mechanism using Linked Data standards to implement FDO and be extensible for domain-specific metadata.


[Chapter 5](../../../2023/phd/workflows/) considers RQ3 by exploring the relationship between Computational Workflows and FAIR practices using RO-Crate and FDO, with use cases from molecular dynamics and specimen digitization. The contribution of the *Workflow Run Crate profiles* is presented as an interoperable way to capture and publish workflow execution provenance.

[Chapter 6](../conclusions/) summarises and discusses the contributions from this thesis, reflects on later third-party developments and concludes by evaluating the research questions.

Origins {#intro:origins}
=======

[Chapter 2](../../../2023/phd/background/) and section [3.1](../../../2023/phd/evaluating-fdo/) are based on the journal article *Evaluating FAIR Digital Object and Linked Data as distributed object systems* \[[Soiland-Reyes 2023c]\] (see appendices [A.4.1](../acknowledgements/#fdo) and [B.1.1](../contributions/#fdo)). I am the main author of this manuscript.

[Section 3.2](../updating-ld-for-fdo/) is based on *Updating Linked Data practices for FAIR Digital Object principles* \[[Soiland-Reyes 2022d]\] (see appendices [A.4.2](../acknowledgements/#updating-ld) and [B.1.2](../contributions/#updating-ld)). I am the main author of this manuscript.

[Section 4.1](../ro-crate/) and [section 4.3](../ro-crate/formalizing/) are based on the publication *Packaging research artefacts with RO-Crate* \[[Soiland-Reyes 2022a]\] (see appendices [A.4.3](../acknowledgements/#packagingrocrate), [B.1.3](../contributions/#packagingrocrate) and [B.1.5](../contributions/#formalizing)). I am the main author of this manuscript.

[Section 4.2](../fdo-with-ro-crate/) is based on the publication _Creating lightweight FAIR digital objects with RO-Crate_ \[[Soiland-Reyes 2022c]\] (see appendices 
[A.4.4](../acknowledgements/#lightweight) and [B.1.4](../contributions/#lightweight)). I am the main author of this manuscript.

[Section 5.1](../canonical-workflow-building-blocks/) is based on the publication _Making Canonical Workflow Building Blocks interoperable across workflow languages_  \[[Soiland-Reyes 2022b]\] (see appendices  [A.4.5](../acknowledgements/#canonical) and [B.1.6](../contributions/#canonical)). I am the main author of this manuscript.

[Section 5.2](../specimen-data-refinery/) is based on the publication _The Specimen Data Refinery: A canonical workflow framework and FAIR Digital Object approach to speeding up digital mobilisation of natural history collections_ \[[Hardisty 2022]\] (see appendices [A.4.6](../acknowledgements/#refinery) and [B.1.7](../contributions/#refinery)).
I mainly contributed to sections 
[5.2.2.2](../specimen-data-refinery/#workflow-management-systems-and-canonical-workflows-for-research), 
[5.2.2.3](../specimen-data-refinery/#fair-packaging-of-researchworkflow-objects-with-ro-crate), 
[5.2.4.1](../specimen-data-refinery/#fdo-types), 
[5.2.7](../specimen-data-refinery/#discussion) in this manuscript.

[Section 5.3](../incrementally-building-fdos/) is based on the publication _Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows_ \[[Woolland 2022]\] (see appendices [A.4.7](../acknowledgements/#incrementally-fdo) and [B.1.8](../contributions/#incrementally-fdo)). I am the main author of this manuscript.

[Section 5.3](../../../2023/phd/workflow-run-crate/#wrroc) is based on the preprint *Recording provenance of workflow runs with RO-Crate* \[[Leo 2023b]\] (see appendices [A.4.8](../acknowledgements#wrroc) and [B.1.9](../contributions#wrroc)). I am the last author of this manuscript, and have mainly contributed to sections [5.4.1](../../../2023/phd/workflow-run-crate/#introduction), [5.4.5](../../../2023/phd/workflow-run-crate/#discussion), [5.4.5.3](../../../2023/phd/workflow-run-crate/#trusted-workflow-run-crate), [5.4.5.4](../../../2023/phd/workflow-run-crate/#bco-crate).


## References

See chapter [references](../../2023/references/).

[van der Aalst 2014]: https://doi.org/10.1007/978-3-319-04948-9_2 "Data Scientist: The Engineer of the Future"
[Addink 2019]: https://doi.org/10.3897/biss.3.37502 "DiSSCo as a New Regional Model for Scientific Collections in Europe"
[Afgan 2018]: https://doi.org/10.1093/nar/gky379 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2018 update"
[Afgan 2023]: https://github.com/galaxyproject/galaxy/releases/tag/v23.1.1 "galaxyproject/galaxy"
[Agarwal 2021]: https://data.agu.org/DataCitationCoP/2nd-workshop-data-citation "Data Citation Community of Practice -- 8 June 2021 Workshop"
[Albertoni 2020]: https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/ "Data Catalog Vocabulary (DCAT) -- Version 2"
[Albertoni 2023]: https://www.w3.org/TR/2024/CR-vocab-dcat-3-20240118/ "Data Catalog Vocabulary (DCAT)- Version 3"
[Allan 2019]: https://doi.org/10.3897/BDJ.7.e32342 "A Novel Automated Mass Digitisation Workflow for Natural History Microscope Slides"
[Allcock 2005]: https://doi.org/10.1109/sc.2005.72 "The Globus Striped GridFTP Framework and Server"
[Almeida 2019]: https://doi.org/10.1038/s41586-019-0965-1 "A new genomic blueprint of the human gut microbiota"
[Alterovitz 2018]: https://doi.org/10.1371/journal.pbio.3000099 "Enabling precision medicine via standard communication of HTS provenance, analysis, and results"
[Alves 2021]: https://doi.org/10.37044/osf.io/k8znb "ELIXIR Software Management Plan for Life Sciences"
[Amorim 2016]: https://doi.org/10.1007/s10209-016-0475-y "A comparison of research data management platforms: Architecture, flexible metadata and interoperability"
[Amstutz 2021]: https://s.apache.org/existing-workflow-systems "Existing Workflow systems"
[Amstutz 2023]: https://doi.org/10.5281/zenodo.7575947 "common-workflow-language/cwltool: 3.1.20230127121939"
[Anders 2022]: https://doi.org/10.5281/zenodo.7825630 "FDO PID profiles & attributes"
[Anders 2023]: https://doi.org/10.5281/zenodo.7782262 "FAIR Digital Objects Forum FDO requirement specifications"
[Andrio 2019]: https://doi.org/10.1038/s41597-019-0177-4 "BioExcel Building Blocks, a software library for interoperable biomolecular simulation workflows"
[ANSI/NISO Z39.99-2017]: https://doi.org/10.3789/ansi.niso.z39.99-2017 "ANSI/NISO Z39.99-2017, ResourceSync Framework Specification"
[Arend 2022]: https://doi.org/10.37044/osf.io/c724r "BioHackEU22 Project 22: Plant data exchange and standard interoperability"
[Arfaoui 2020]: https://github.com/GhaithArf/ro-crate-rda-madmp-mapper "RO-Crate RDA maDMP Mapper"
[Arkisto 2022]: https://arkisto-platform.github.io/tools/portal/ "Tools: Data Portal & Discovery"
[Atkinson 2017]: https://doi.org/10.1016/j.future.2017.05.041 "Scientific workflows: Past, present and future"
[Atkinson 2019]: https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/ "The Profiles Vocabulary"
[Ayris 2016]: https://doi.org/10.2777/940154 "Realising the European Open Science Cloud"
[Azeroual 2022]: https://hdl.handle.net/11366/2243 "Putting FAIR Principles in the Context of Research Information: FAIRness for CRIS and CRIS for FAIRness"
[Bacall 2019]: https://esciencelab.org.uk/projects/ro-composer/ "eScienceLab: RO-Composer"
[Bacall 2022]: https://w3id.org/workflowhub/workflow-ro-crate/1.0 "Workflow RO-Crate Profile 1.0"
[Bacall 2022b]: https://github.com/ResearchObject/ro-crate-ruby "GitHub -- ResearchObject/ro-crate-ruby: A Ruby gem for creating, manipulating and reading RO-Crates"
[Bahra 2011]: https://doi.org/10.21957/nr843dob "Managing work flows with ecFlow"
[Bahui 2020]: https://doi.org/10.5334/dsj-2020-041 "The FAIR data maturity model: An approach to harmonise FAIR assessments"
[Baker 2013]: https://doi.org/10.1016/j.websem.2013.05.001 "Key choices in the design of Simple Knowledge Organization System (SKOS)"
[Baker 2016]: https://doi.org/10.1038/533452a "1,500 scientists lift the lid on reproducibility"
[Baker 2019]: http://shex.io/shex-primer/ "Shape Expressions (ShEx) 2.1 Primer"
[Baker 2020]: https://doi.org/10.1371/journal.ppat.1008643 "No more business as usual: Agile and effective responses to emerging pathogen threats require open data and open analytics"
[Barker 2019]: https://doi.org/10.5334/dsj-2019-044 "The Australian Research Data Commons"
[Barker 2022]: https://doi.org/10.1038/s41597-022-01710-x "Introducing the FAIR Principles for research software"
[Batista 2022]: https://doi.org/10.1038/s41597-022-01707-6 "Machine actionable metadata models"
[Baxter 2012]: https://www.research.ed.ac.uk/en/publications/e8416ad7-750f-442f-9b17-d812b9bb414d "The Research Software Engineer"
[Bayarri 2021a]: https://doi.org/10.48546/workflowhub.workflow.29.3 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in CWL"
[Bayarri 2021b]: https://doi.org/10.48546/workflowhub.workflow.120.2 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in Jupyter Notebook"
[Bayarri 2022]: https://doi.org/10.48546/workflowhub.workflow.255.1 "CWL GMX Automatic Ligand Parameterization tutorial"
[Bechhofer 2013]: https://doi.org/10.1016/j.future.2011.08.004 "Why Linked Data is not enough for scientists"
[Beg 2021]: https://doi.org/10.1109/MCSE.2021.3052101 "Using Jupyter for Reproducible Scientific Workflows"
[Beier 2024]: https://doi.org/10.37044/osf.io/7y2jh "Enabling continuous RDM using Annotated Research Contexts with RO-Crate profiles for ISA"
[Belchev 2021]: https://github.com/KockataEPich/CheckMyCrate "KockataEPich/CheckMyCrate: A command line application for validating a RO-Crate object against a JSON profile"
[Belhajjame 2015]: https://doi.org/10.1016/j.websem.2015.01.003 "Using a suite of ontologies for preserving workflow-centric research objects"
[Belshe 2022]: https://doi.org/10.17487/rfc7540 "Hypertext Transfer Protocol Version 2 (HTTP/2)"
[Beltrán 2023]: https://doi.org/10.5281/zenodo.10199020 "Autosubmit v4.0.100"
[Benureau 2017]: https://doi.org/10.3389/fninf.2017.00069 "Re-run, repeat, reproduce, reuse, replicate: Transforming code into scientific contributions"
[Berman 2007]: https://doi.org/10.1093/nar/gkl971 "The worldwide Protein Data Bank (wwPDB): Ensuring a single, uniform archive of PDB data"
[Berners-Lee 1998]: https://www.w3.org/Provider/Style/URI "Cool URIs don't change"
[Berners-Lee 1999]: https://identifiers.org/isbn/9780062515865 "Weaving the Web: The original design and ultimate destiny of the World Wide Web by its inventor"
[Berners-Lee 2000]: https://www.w3.org/2000/Talks/1206-xml2k-tbl/slide10-0.html "Semantic Web on XML"
[Berners-Lee 2005]: https://doi.org/10.17487/rfc3986 "Uniform Resource Identifier (URI): Generic Syntax"
[Berners-Lee 2006]: https://www.w3.org/DesignIssues/LinkedData.html "Linked Data"
[Bernstein 2016]: https://doi.org/10.1145/2890489 "A new look at the semantic web"
[Bietrix 2021]: https://doi.org/10.5281/zenodo.4705078 "EOSC-Life methodology framework to enhance reproducibility within EOSC Life"
[BioMoby 2008]: https://doi.org/10.1093/bib/bbn003 "Interoperability with Moby 1.0---It's better than sharing your toothbrush!"
[Bishop 2022]: https://doi.org/10.17487/rfc9114 "HTTP/3"
[Bizer 2009]: https://doi.org/10.4018/jswis.2009081901 "Linked Data - The Story So Far"
[Bizer 2011]: https://doi.org/10.4018/978-1-60960-593-3.ch008 "Linked data: The story so far"
[Blanchi 2022]: https://doi.org/10.5281/zenodo.7825549 "FDO -- upload of FDO"
[Blanchi 2023]: https://doi.org/10.5281/zenodo.7825572 "Implementation of attributes, types, profiles and registries"
[Blankenberg 2014]: https://doi.org/10.1186/gb4161 "Dissemination of scientific software with Galaxy ToolShed"
[Blomquist 2009]: https://doi.org/10.1145/1597735.1597743 "Experiments on pattern-based ontology design"
[Bonino 2016]: https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability "FAIR Data points supporting big data interoperability"
[Bonino 2019]: https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR\%20Digital\%20Objects/FDOF/FAIR\%20Digital\%20Object\%20Framework-v1-02.docx "FAIR digital object framework v1.02"
[Bonino 2020]: https://fairdigitalobjectframework.org/ "FAIR Digital Object Framework Documentation"
[Bouyssié 2023]: https://doi.org/10.1101/2023.10.02.560412 "WOMBAT-P: Benchmarking Label-Free Proteomics Data Analysis Workflows"
[Brack 2022a]: https://doi.org/10.1371/journal.pcbi.1009823 "Ten Simple Rules for making a software tool workflow-ready"
[Brack 2022b]: https://doi.org/10.48546/workflowhub.workflow.373.1 "De novo digitisation."
[Brand 2015]: https://doi.org/10.1087/20150211 "Beyond authorship: Attribution, contribution, collaboration, and credit"
[Bray 2017]: https://doi.org/10.17487/rfc8259 "The JavaScript Object Notation (JSON) Data Interchange Format"
[Brenner 2020]: https://github.com/BrennerG/Ro-Crate_2_ma-DMP "BrennerG/Ro-Crate\_2\_ma-DMP: v1.0.0"
[Brickley 2014]: http://xmlns.com/foaf/spec/ "FOAF Vocabulary Specification"
[Broeder 2022]: https://drive.google.com/file/d/1KJ9l0p96naKi_2HPJ_MPqPTwS_zlP92G "FDO glossary november 2022"
[Buck 2022]: https://doi.org/10.1002/essoar.10509966.1 "AGU data citation community of practice - Credit for creators of data within collections using the concept of a reliquary"
[Capadisli 2017]: https://www.w3.org/TR/2017/REC-ldn-20170502/ "Linked Data Notifications"
[Cardoso 2020a]: https://doi.org/10.1007/978-3-030-45442-5_15 "Machine-actionable data management plans: A knowledge retrieval approach to automate the assessment of funders' requirements"
[Cardoso 2020b]: https://repository.publisso.de/resource/frl:6423289 "Towards Semantic Representation of Machine-Actionable Data Management Plans"
[Carranza-Rojas 2017]: https://doi.org/10.1186/s12862-017-1014-z "Going deeper in the automated identification of Herbarium specimens"
[Carriero 2010]: https://doi.org/10.3233/ssw200033 "The landscape of ontology reuse approaches"
[Carrothers 2014]: http://www.w3.org/TR/2014/REC-n-triples-20140225/ "RDF 1.1 N-Triples"
[Chard 2014]: https://doi.org/10.1109/MCC.2014.52 "Efficient and secure transfer, synchronization, and sharing of big data"
[Chard 2016]: https://static.aminer.org/pdf/fa/bigdata2016/BigD418.pdf "I'll take that to go: Big data bags and minimal identifiers for exchange of large, complex datasets"
[Chard 2019]: https://zenodo.org/record/3381754 "Application of BagIt-serialized research object bundles for packaging and re-execution of computational analyses"
[Chard 2020]: https://doi.org/10.3233/APC200107 "Toward enabling reproducibility for data-intensive research using the Whole Tale platform"
[Ciccarese 2013]: https://doi.org/10.1186/2041-1480-4-37 "PAV ontology: Provenance, authoring and versioning"
[Ciccarese 2017]: https://www.w3.org/TR/2017/REC-annotation-model-20170223/ "Web Annotation Data Model"
[Claerbout 1992]: http://sep.stanford.edu/oldsep/matt/join/redoc/web/seg92.html "Electronic documents give reproducible research a new meaning"
[Clemm 2002]: https://doi.org/10.17487/rfc3253 "Versioning Extensions to WebDAV"
[CNRI 2023a]: https://www.cordra.org/documentation/api/doip-api-for-http-clients.html "DOIP API for HTTP Clients"
[CNRI 2023b]: https://www.cordra.org/documentation/api/doip.html "DOIP and Examples"
[Cohen 2020]: https://doi.org/10.1109/MS.2020.2973362 "The Four Pillars of Research Software Engineering"
[Cohen-Boulakia 2017]: https://hal.archives-ouvertes.fr/hal-01516082 "Scientific workflows for computational reproducibility in the life sciences: Status, challenges and opportunities"
[Colonnelli 2021]: https://doi.org/10.1109/TETC.2020.3019202 "StreamFlow: cross-breeding Cloud with HPC"
[Colonnelli 2023a]: https://doi.org/10.5281/zenodo.7911906 "StreamFlow run of digital pathology tissue/tumor prediction workflow"
[Colonnelli 2023b]: https://github.com/alpha-unito/streamflow/releases/tag/0.2.0.dev10 "alpha-unito/streamflow"
[Corcho 2021]: https://doi.org/10.5281/zenodo.4913285 "D5.1 RO Model Adapted to EOSC"
[Corcho 2023]: https://doi.org/10.48550/arXiv.2305.06746 "A maturity model for catalogues of semantic artefacts"
[Cossu 2018]: https://github.com/duraspace/pcdm/wiki "Portland Common Data Model"
[Costa 2013]: https://doi.org/10.1145/2457317.2457365 "Capturing and querying workflow runtime provenance with PROV"
[Crosas 2011]: https://doi.org/10.1045/january2011-crosas "The DataVerse Network: An open-source application for sharing, discovering and preserving data"
[Crosas 2020]: https://doi.org/10.7557/5.5422 "Harvard Data Commons"
[Crosswell 2012]: https://doi.org/10.1016/j.tibtech.2012.02.002 "ELIXIR: A distributed infrastructure for European biological data"
[CRS4 2022]: https://about.lifemonitor.eu/ "LifeMonitor, a testing and monitoring service for scientific workflows"
[Crusoe 2022]: https://doi.org/10.1145/3486897 "Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language"
[Cruz 2009]: https://doi.org/10.1109/SERVICES-I.2009.18 "Towards a Taxonomy of Provenance in Scientific Workflow Management Systems"
[Cuevas-Vicenttín 2016]: https://purl.dataone.org/provone-v1-dev "ProvONE: A PROV Extension Data Model for Scientific Workflow Provenance"
[CWFR 2021]: https://osf.io/3rekv/ "Canonical Workflow Frameworks for Research"
[da Veiga Leprevost 2017]: https://doi.org/10.1093/bioinformatics/btx192 "BioContainers: An open-source and community-driven framework for software standardization"
[DCMI 2020]: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/2020-01-20/ "DCMI Metadata Terms"
[De Geest 2022]: https://doi.org/10.3897/rio.8.e95164 "Enhancing RDM in Galaxy by integrating RO-Crate"
[De Geest 2023a]: https://github.com/researchobject/ro-crate-py "GitHub -- ResearchObject/ro-crate-py: Python library for RO-Crate"
[De Geest 2023b]: https://doi.org/10.5281/zenodo.7785861 "Run of an example Galaxy collection workflow"
[De Giovanni 2016]: https://doi.org/10.1111/ecog.01552 "ENM Components: a new set of web service‐based workflow components for ecological niche modelling"
[De Roure 2010]: https://web.archive.org/web/20140828142306/http://journal.webscience.org/325/ "Anchors in shifting sand: the primacy of method in the web of data"
[De Smedt 2020]: https://doi.org/10.3390/publications8020021 "FAIR Digital Objects for Science: From Data Pieces to Actionable Knowledge Units"
[Del Rio 2022]: https://doi.org/10.1007/978-3-031-13321-3_48 "AI Support for Accelerating Histopathological Slide Examinations of Prostate Cancer in Clinical Studies"
[Delgado 2016]: https://doi.org/10.1007/978-3-319-31861-5_1 "An Interoperability Framework and Distributed Platform for Fast Data Applications"
[Desai 2016]: https://econpapers.repec.org/RePEc:uwe:wpaper:20161601 "Five Safes: designing data access for research"
[Devaraju 2021]: https://doi.org/10.5334/dsj-2021-004 "From conceptualization to implementation: FAIR assessment of research data objects"
[Dillen 2019a]: https://doi.org/10.3897/biss.3.37080 "Zenodo, an archive and publishing repository: A tale of two herbarium specimen pilot projects"
[Dillen 2019b]: https://doi.org/10.3897/BDJ.7.e31817 "A benchmark dataset of herbarium specimen imagfes with label data"
[Di Tommaso 2017]: https://doi.org/10.1038/nbt.3820 "Nextflow enables reproducible computational workflows"
[DOI 2019]: https://doi.org/10.1000/182 "DOI Handbook - Resolution"
[DONA 2018]: https://hdl.handle.net/0.DOIP/DOIPV2.0 "Digital Object Interface Protocol specification, version 2.0"
[DONA 2021]: https://www.dona.net/node/88 "Digital Object Architecture"
[Drummond 2006]: https://www.cs.man.ac.uk/~drummond/presentations/OWA.pdf "The Open World Assumption"
[Dürst 2005]: https://doi.org/10.17487/rfc3987 "Internationalized resource identifiers (IRIs)"
[Dusseault 2007]: https://doi.org/10.17487/rfc4918 "HTTP Extensions for Web Distributed Authoring and Versioning"
[Eguinoa 2020]: https://github.com/workflowhub-eu/galaxy2cwl "GitHub workflowhub-eu/galaxy2cwl"
[Eguinoa 2023]: https://s11.no/2023/phd/enhancing-rdm-galaxy-dsw "BioHackEU22 Report: Enhancing Research Data Management in Galaxy and Data Stewardship Wizard by utilising RO-Crates"
[Ejarque 2023]: https://doi.org/10.5281/zenodo.7975340 "COMPSs"
[Ekuan 2023]: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design "Web API design best practices"
[Ellerm 2023]: https://doi.org/10.1109/e-Science58273.2023.10254857 "LivePublication: The Science Workflow Creates and Updates the Publication"
[Ellis 2007]: https://doi.org/10.1109/ICSE.2007.85 "The Factory Pattern in API Design: A Usability Evaluation"
[EMBL-EBI 2019]: http://ftp.ebi.ac.uk/pub/databases/metagenomics/umgs_analyses/ "FTP index of /pub/databases/metagenomics/umgs\_analyses/"
[EMBL-EBI 2020]: https://github.com/Finn-Lab/MGS-gut "GitHub -- Finn-Lab/MGS-gut: Analysing Metagenomic Species (MGS)"
[EU 2016]: https://ec.europa.eu/research/participants/data/ref/h2020/grants_manual/hi/oa_pilot/h2020-hi-oa-data-mgt_en.pdf "Guidelines on FAIR Data Management in Horizon 2020"
[Ewels 2020]: https://doi.org/10.1038/s41587-020-0439-x "The nf-core framework for community-curated bioinformatics pipelines"
[FAIR Maturity 2020]: https://doi.org/10.15497/rda00050 "FAIR data maturity model: Specification and guidelines"
[Falk 2010]: https://doi.org/10.1016/j.shpsc.2010.10.014 "What is a gene?—Revisited"
[Farnel 2014]: https://dcpapers.dublincore.org/pubs/article/view/3714 "Metadata for research data: Current practices and trends"
[FDO]: https://fairdo.org/ "FAIR Digital Object Forum"
[FDO Specs]: https://hdl.handle.net/20.500.14132/fdo-spec-docs "FDO Specification Documents - November 2022"
[Feng 2007]: https://doi.org/10.1145/1254882.1254906 "PBS: a unified priority-based scheduler"
[Fenner 2019]: https://doi.org/10.5438/jwvf-8a66 "Introducing the PID graph"
[Fensel 2011]: https://doi.org/10.1007/978-3-642-19193-0 "Semantic Web Services"
[Fernández 2023a]: https://doi.org/10.5281/zenodo.10068956 "inab/WfExS-backend"
[Fernández 2023b]: https://doi.org/10.5281/zenodo.10091550 "RO-Crate from staged WfExS working directory"
[Ferreira da Silva 2021]: https://doi.org/10.48550/arXiv.2110.02168 "A Community Roadmap for Scientific Workflows Research and Development"
[Ferreira da Silva]: https://doi.org/10.48550/arXiv.2304.00019 "Workflows Community Summit 2022"
[Fielding 1999]: https://doi.org/10.17487/rfc2616 "Hypertext Transfer Protocol -- HTTP/1.1"
[Fielding 2000]: https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm "Architectural styles and the design of network-based software architectures"
[Fielding 2014a]: https://doi.org/10.17487/rfc7230 "Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing"
[Fielding 2014b]: https://doi.org/10.17487/rfc7231 "Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content"
[Fielding 2017]: https://doi.org/10.1145/3106237.3121282 "Reflections on the REST architectural style and \"principled design of the modern web architecture\" (impact paper award)"
[Fielding 2022]: https://doi.org/10.17487/rfc9110 "HTTP Semantics"
[Fillbrunn 2017]: https://doi.org/10.1016/j.jbiotec.2017.07.028 "KNIME for reproducible cross-domain analysis of life science data"
[Fouilloux 2023]: https://doi.org/10.3897/rio.9.e108765 "FAIR Research Objects for realizing Open Science with RELIANCE EOSC project"
[Freire 2008]: https://doi.org/10.1109/MCSE.2008.79 "Provenance for Computational Tasks: A Survey"
[Galaxy 2022]: https://doi.org/10.1093/nar/gkac247 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update"
[Gamma 1995]: https://identifiers.org/isbn/9780201633610 "Design Patterns"
[Garcia 2020]: https://doi.org/10.1371/journal.pcbi.1007808 "Ten simple rules to run a successful BioHackathon"
[Garcia-Silva 2019]: https://doi.org/10.48550/arXiv.1809.10617 "Enabling FAIR research in Earth science through research objects"
[Garijo 2011]: https://doi.org/10.1145/2110497.2110504 "A New Approach for Publishing Workflows"
[Garijo 2012]: https://ceur-ws.org/Vol-951/paper6.pdf "Augmenting PROV with Plans in P-PLAN: Scientific Processes as Linked Data"
[Garijo 2014a]: https://doi.org/10.1016/j.future.2013.09.018 "Common Motifs in Scientific Workflows: An Empirical Analysis"
[Garijo 2014b]: https://doi.org/10.1109/works.2014.13 "Towards Workflow Ecosystems through Semantic and Standard Representations"
[Gauthier 2019]: https://doi.org/10.1093/bib/bby063 "A brief history of bioinformatics"
[GBIF 2021]: https://doi.org/10.35035/bezp-jj23 "GBIF Science Review 2020"
[Gewirtz 1996]: https://heinonline.org/HOL/P?h=hein.journals/ylr105&i=1057 "On I Know It When I See It"
[Gil 2011]: https://doi.org/10.1109/MIS.2010.9 "Wings: Intelligent Workflow-Based Design of Computational Experiments"
[Giles 2023]: https://doi.org/10.5281/zenodo.10055354 "TRE-FX: Delivering a federated network of trusted research environments to enable safe data analytics"
[GitHub 2021]: https://docs.github.com/en/repositories/working-with-files/managing-large-files "Managing large files -- GitHub Docs"
[Goble 2008]: https://doi.org/10.1016/j.jbi.2008.01.008 "State of the nation in data integration for bioinformatics"
[Goble 2010]: https://doi.org/10.1093/nar/gkq429 "myExperiment: A repository and social network for the sharing of bioinformatics workflows"
[Goble 2016]: http://repscience2016.research-infrastructures.eu/img/CaroleGoble-ReproScience2016v2.pdf "What Is Reproducibility? The R* Brouhaha"
[Goble 2018]: https://doi.org/10.5281/zenodo.1313066 "Research Object Community Update"
[Goble 2020]: https://doi.org/10.1162/dint_a_00033 "FAIR Computational Workflows"
[Goble 2021]: https://doi.org/10.5281/zenodo.4605654 "Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory"
[Goble 2022]: https://doi.org/10.5281/zenodo.7157647 "FAIR-IMPACT: T3.2.1 PIDs in data production workflows"
[González 2022]: https://dgarijo.com/papers/TPDL2022_gonzalez.pdf "FAIROs: Towards FAIR Assessment in Research Objects"
[Gray 2017]: https://iswc2017.semanticweb.org/paper-579/ "Bioschemas: From Potato Salad to Protein Annotation"
[Gregorio 2007]: https://doi.org/10.17487/rfc5023 "The Atom Publishing Protocol"
[Gregorio 2012]: https://doi.org/10.17487/rfc6570 "URI Template"
[Groom 2020]: https://doi.org/10.1093/database/baaa072 "People are essential to linking biodiversity data"
[Grossman 2016]: https://doi.org/10.1109/MCSE.2016.92 "A case for data commons: Toward data science as a service"
[Groth 2014]: https://doi.org/10.1016/j.websem.2014.03.003 "API-centric Linked Data integration: The Open PHACTS Discovery Platform case study"
[Grüning 2018a]: https://doi.org/10.1038/s41592-018-0046-7 "Bioconda: Sustainable and Comprehensive Software Distribution for the Life Sciences"
[Grüning 2018b]: https://doi.org/10.1016/j.cels.2018.03.014 "Practical Computational Reproducibility in the Life Sciences"
[Guha 2014]: http://www.w3.org/TR/rdf-schema/ "RDF Schema 1.1"
[Guha 2015]: https://doi.org/10.1145/2857274.2857276 "Schema.org: Evolution of Structured Data on the Web: Big data makes common schemas even more necessary"
[Guha 2016]: https://doi.org/10.1145/2844544 "Schema.org: evolution of structured data on the web"
[Gurevich 1995]: https://identifiers.org/isbn/9780198538547 "Evolving Algebras 1993: Lipari Guide"
[Handle]: https://www.handle.net/download_hnr.html "Handle.Net Software"
[Hardisty 2016]: https://doi.org/10.1186/s12898-016-0103-y "BioVeL: a virtual laboratory for data analysis and modelling in biodiversity science and ecology"
[Hardisty 2019a]: https://doi.org/10.3897/biss.3.37033 "`openDS' -- A New Standard for Digital Specimens and Other Natural Science Digital Object Types"
[Hardisty 2019b]: https://doi.org/10.5281/zenodo.3532937 "Provisional Data Management Plan for DiSSCo infrastructure"
[Hardisty 2020]: https://doi.org/10.3897/rio.6.e54280 "Conceptual design blueprint for the DiSSCo digitization infrastructure - DELIVERABLE D8.1"
[Hardisty 2022]: https://doi.org/10.1162/dint_a_00134 "The Specimen Data Refinery"
[Harrow 2021]: https://doi.org/10.15252/embj.2020107409 "ELIXIR-EXCELERATE: establishing Europe's data infrastructure for the life science research of the future"
[Harrow 2022]: https://doi.org/10.1093/bioinformatics/btab481 "ELIXIR: providing a sustainable infrastructure for life science data at European scale"
[Hasnain 2018]: https://doi.org/10.1007/978-3-319-98192-5_60 "Assessing FAIR Data Principles Against the 5-Star Open Data Principles"
[Hausenblas 2012]: http://5stardata.info/ "5-star Open Data"
[Heath 2011]: https://doi.org/10.2200/S00334ED1V01Y201102WBE001 "Linked Data: Evolving the Web into a Global Data Space"
[Heberling 2019]: https://doi.org/10.1093/biosci/biz094 "The Changing Uses of Herbarium Data in an Era of Global Change: An Overview Using Automated Content Analysis"
[Heberling 2021]: https://doi.org/10.1073/pnas.2018093118 "Data integration enables global biodiversity synthesis"
[Hellström 2022]: https://doi.org/10.5281/zenodo.7825686 "FDO -- granularity, versioning, mutability"
[Hereld 2019]: https://doi.org/10.3897/biss.3.37228 "LightningBug ONE: An experiment in high-throughput digitization of pinned insects"
[Herschel 2017]: https://doi.org/10.1007/s00778-017-0486-1 "A survey on provenance: What for? What form? What from?"
[Himanen 2019]: https://doi.org/10.1002/advs.201900808 "Data-Driven Materials Science: Status, Challenges, and Perspectives"
[Hitzler 2016]: https://identifiers.org/isbn/9781614996767 "Ontology engineering with ontology design patterns"
[Holland 2014]: http://blog.schema.org/2014/06/introducing-role.html "Introducing 'Role'"
[Horrocks 2022]: https://doi.org/10.1007/3-540-48005-6 "The Semantic Web --- ISWC 2002"
[Hospital 2020]: https://doi.org/10.5281/zenodo.4540432 "BioExcel-2 Deliverable 2.3 -- First release of demonstration workflows"
[Hospital 2021a]: https://doi.org/10.48546/workflowhub.workflow.200.1 "Protein MD Setup HPC tutorial using BioExcel Building Blocks (biobb) in PyCOMPSs"
[Hospital 2021b]: https://doi.org/10.48546/workflowhub.workflow.201.1 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in KNIME"
[Hu 2011]: https://identifiers.org/isbn/9783642210334 "How matchable are four thousand ontologies on the semantic web"
[Hui 2012]: https://doi.org/10.1111/j.1467-9973.2012.01761.x "What is a Digital Object?"
[Huntingford 2019]: https://doi.org/10.1088/1748-9326/ab4e55 "Machine learning and artificial intelligence to aid climate change research and preparedness"
[Hussein 2021]: https://doi.org/10.48550/arXiv.2104.08732 "Application of Computer Vision and Machine Learning for Digitized Herbarium Specimens: A Systematic Literature Review"
[IEEE 2791-2020]: https://research.manchester.ac.uk/en/publications/936de52b-ac53-4f0e-9927-77fd7073e88d "IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication"
[Isaac 2009]: https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/ "SKOS Simple Knowledge Organization System Primer"
[Islam 2020]: https://doi.org/10.5334/dsj-2020-050 "Incorporating RDA Outputs in the Design of a European Research Infrastructure for natural history Collections"
[Islam 2023]: https://doi.org/10.3233/FC-230001 "FAIR digital objects, persistent identifiers and machine actionability"
[ISO 16684]: https://www.iso.org/standard/75163.html "ISO 16684-1:2019 --- graphic technology --- extensible metadata platform (XMP)"
[ISO 23009-1]: https://www.iso.org/standard/83314.html "ISO/IEC 23009-1:2022 --- information technology --- dynamic adaptive streaming over HTTP (DASH)"
[Ison 2013]: https://doi.org/10.1093/bioinformatics/btt113 "EDAM: an ontology of bioinformatics operations, types of data and identifiers, topics and formats"
[Ison 2021]: https://doi.org/10.1093/gigascience/giaa157 "biotoolsSchema: a formalized schema for bioinformatics software description"
[ITU-T X.1255]: https://www.itu.int/rec/T-REC-X.1255-201309-I "X.1255 : Framework for Discovery of Identity Management Information"
[Ivonne 2023]: https://doi.org/10.5281/zenodo.7824714 "FAIR digital object technical overview"
[Iyengar 2021]: https://doi.org/10.17487/rfc9000 "QUIC: A UDP-Based Multiplexed and Secure Transport"
[Jacobsen 2020]: https://doi.org/10.1162/dint_r_00024 "FAIR Principles: Interpretations and Implementation Considerations"
[Jaradeh 2019]: https://doi.org/10.1007/978-3-030-30760-8_31 "Open research knowledge graph: A system walkthrough"
[Jensen 2017]: https://doi.org/10.1182/blood-2017-03-735654 "The NCI Genomic Data Commons as an engine for precision medicine"
[Jones 2021]: https://doi.org/10.5281/zenodo.4477164 "Science-on-Schema.org v1.2.0"
[Jones 2022]: https://swordapp.github.io/swordv3/swordv3.html "SWORD 3.0 Specification"
[Joras 2020]: https://engineering.fb.com/2020/10/21/networking-traffic/how-facebook-is-bringing-quic-to-billions "How Facebook is bringing QUIC to billions"
[JSONPath 2023]: https://datatracker.ietf.org/doc/id/draft-ietf-jsonpath-base-10 "JSONPath: Query Expressions for JSON"
[Jupyter 2018]: https://doi.org/10.25080/majora-4af1f417-011 "Binder 2.0 - Reproducible, Interactive, Sharable Environments for Science at Scale"
[Juty 2011]: https://doi.org/10.1093/nar/gkr1097 "Identifiers.org and MIRIAM Registry: Community resources to provide persistent identification"
[Juty 2020]: https://doi.org/10.1162/dint_a_00025 "Unique, Persistent, Resolvable: Identifiers as the foundation of FAIR"
[Kahn 1995]: http://www.cnri.reston.va.us/k-w.html "A framework for distributed digital object services"
[Kahn 2006]: https://doi.org/10.1007/s00799-005-0128-x "A framework for distributed digital object services"
[Kallinikos 2013]: https://www.jstor.org/stable/43825913 "The ambivalent ontology of digital artifacts"
[Kamdar 2017]: https://doi.org/10.3233/sw-160238 "A systematic analysis of term reuse and term overlap across biomedical ontologies"
[Katsumi 2016]: https://doi.org/10.3233/978-1-61499-660-6-9 "What is ontology reuse?"
[Katz 2021a]: https://doi.org/10.48550/arXiv.2101.10883 "A Fresh Look at FAIR for Research Software"
[Katz 2021b]: https://doi.org/10.1016/j.patter.2021.100222 "A Fresh Look at FAIR for Research Software"
[Kelly 2016]: https://datatracker.ietf.org/doc/draft-kelly-json-hal/08/ "JSON Hypertext Application Language"
[Khan 2019]: https://doi.org/10.1093/gigascience/giz095 "Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv"
[Khare 2000]: https://doi.org/10.17487/rfc2817 "Upgrading to TLS Within HTTP/1.1"
[Kharouba 2019]: https://doi.org/10.1098/rstb.2017.0405 "Using insect natural history collections to study global change impacts: challenges and opportunities"
[Kim 2008]: https://doi.org/10.1002/cpe.1228 "Provenance trails in the Wings/Pegasus system"
[Kinoshita 2023]: https://doi.org/10.5281/zenodo.8144612 "RO-Crate created using Autosubmit version 4.0.100 workflow running kinow/auto-mhm-test-domains"
[Klein 2014]: https://doi.org/10.1371/journal.pone.0115253 "Scholarly Context Not Found: One in Five Articles Suffers from Reference Rot"
[Klímek 2019]: https://doi.org/10.3233/SW-180316 "Survey of tools for linked data consumption"
[Kluyver 2016]: https://doi.org/10.3233/978-1-61499-649-1-87 "Jupyter Notebooks – a publishing format for reproducible computational workflows"
[Knyshov 2021]: https://doi.org/10.1093/isd/ixab004 "Pretrained Convolutional Neural Networks Perform Well in a Challenging Test Case: Identification of Plant Bugs (Hemiptera: Miridae) Using a Small Number of Training Images"
[Koesten 2020]: https://doi.org/10.1016/j.patter.2020.100136 "Dataset reuse: Toward translating principles to practice"
[Koesten 2021]: https://doi.org/10.1016/j.ijhcs.2020.102562 "Talking datasets -- understanding data sensemaking behaviours"
[Kontokostas 2017]: https://www.w3.org/TR/shacl/ "Shapes Constraint Language (SHACL)"
[Köster 2012]: https://doi.org/10.1093/bioinformatics/bts480 "Snakemake—a scalable bioinformatics workflow engine"
[Kuhn 2021]: https://doi.org/10.7717/peerj-cs.387 "Semantic micro-contributions with decentralized nanopublication services"
[Kumar 2013]: https://doi.org/10.1029/2012WR012195 "Implications of distributed hydrologic model parameterization on water fluxes at multiple scales and locations"
[Kunze 2018]: https://doi.org/10.17487/rfc8493 "The BagIt File Packaging Format"
[Kunze 2022]: https://datatracker.ietf.org/doc/draft-kunze-ark/36/ "The ARK Identifier Scheme"
[Kurowski 2021]: https://doi.org/10.2777/620649 "EOSC Interoperability Framework"
[Käfer 2018a]: http://events.linkeddata.org/ldow2018/papers/LDOW2018_paper_7.pdf "Rule-based Programming of User Agents for Linked Data"
[Käfer 2018b]: https://doi.org/10.1007/978-3-030-00671-6_25 "Specifying, Monitoring, and Executing Workflows in Linked Data Environments"
[La Rosa 2021a]: https://github.com/CoEDL/modpdsc/ "GitHub -- CoEDL/modpdsc"
[La Rosa 2021b]: https://github.com/CoEDL/ocfl-tools "GitHub -- CoEDL/ocfl-tools: Tools to process and manipulate an OCFL tree"
[La Rosa 2021c]: https://arkisto-platform.github.io/describo-online/ "Arkisto Platform: Describo Online"
[La Rosa 2021d]: https://arkisto-platform.github.io/describo/ "Arkisto Platform: Describo"
[Labra Gayo 2017]: https://doi.org/10.2200/s00786ed1v01y201707wbe016 "Validating RDF Data"
[Lagoze 2008]: http://www.openarchives.org/ore/1.0/datamodel#Proxies "ORE Specification - Abstract Data Model"
[Lammey 2020]: https://doi.org/10.6087/kcse.192 "Solutions for identification problems: A look at the research organization registry"
[Lamprecht 2019]: https://doi.org/10.3233/DS-190026 "Towards FAIR principles for research software"
[Lamprecht 2021]: https://doi.org/10.12688/f1000research.54159.1 "Perspectives on automated composition of workflows in the life sciences"
[Lannom 2020]: https://doi.org/10.1162/dint_a_00034 "FAIR Data and Services in Biodiversity Science and Geoscience"
[Lannom 2022a]: https://doi.org/10.5281/zenodo.7825703 "FDO configuration types"
[Lannom 2022b]: https://doi.org/10.5281/zenodo.7824673 "FAIR digital objects roadmap. Version 5 november 2022"
[Lannom 2022c]: https://doi.org/10.5281/zenodo.7825599 "Typing FAIR digital objects"
[Lanthaler 2021]: http://www.hydra-cg.com/spec/latest/core/ "Hydra Core Vocabulary"
[Lassila 1999]: https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/ "Resource Description Framework (RDF) Model and Syntax Specification"
[Lebo 2013a]: https://www.w3.org/TR/2013/REC-prov-o-20130430/ "PROV-O: The PROV Ontology"
[Lebo 2013b]: https://www.w3.org/TR/2013/NOTE-prov-links-20130430/ "Linking Across Provenance Bundles"
[Lee 2018]: https://doi.org/10.1371/journal.pcbi.1006561 "Ten simple rules for documenting scientific software"
[Leipzig 2021]: https://doi.org/10.1016/j.patter.2021.100322 "The role of metadata in reproducible computational research"
[Leo 2023a]: https://github.com/ResearchObject/runcrate "runcrate"
[Leo 2023b]: https://doi.org/10.48550/arXiv.2312.07852 "Recording provenance of workflow runs with RO-Crate"
[Leo 2023c]: https://w3id.org/ro/doi/10.5281/zenodo.10368989 "Recording provenance of workflow runs with RO-Crate"
[Leo 2023]: https://doi.org/10.5281/zenodo.7774351 "Run of digital pathology tissue/tumor prediction workflow"
[Little 2020]: https://doi.org/10.1002/aps3.11365 "An algorithm competition for automatic species identification from herbarium specimens"
[Liu 2007]: https://www.w3.org/TR/2007/REC-wsdl20-primer-20070626/ "Web Services Description Language"
[Livermore 2022a]: https://doi.org/10.48546/workflowhub.workflow.374.1 "DLA-Collections-test."
[Livermore 2022b]: https://doi.org/10.48546/workflowhub.workflow.375.1 "HTR-Collections-test"
[Lohonya 2020]: https://doi.org/10.3897/BDJ.8.e50503 "Georeferencing the Natural History Museum's Chinese type collection: of plateaus, pagodas and plants"
[Loo 2022]: https://doi.org/10.3897/rio.coll.190 "First International Conference on FAIR Digital Objects"
[Lordan 2014]: https://doi.org/10.1007/s10723-013-9272-5 "ServiceSs: An interoperable programming framework for the cloud"
[Lowe 2021a]: https://doi.org/10.48546/workflowhub.workflow.194.1 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in Galaxy"
[Lowe 2021b]: https://doi.org/10.48546/workflowhub.workflow.56.1 "Protein Ligand Complex MD Setup tutorial using BioExcel Building Blocks (biobb) (jupyter notebook)"
[Ludäscher 2016]: https://doi.org/10.1007/978-3-319-40226-0_7 "A Brief Tour Through Provenance in Scientific Workflows and Databases"
[Lughadha 2019]: https://doi.org/10.1111/cobi.13289 "Harnessing the potential of integrated systematics for conservation of taxonomically complex, megadiverse plant groups"
[Luo 2022]: https://www.proquest.com/docview/2763290077 "Knowledge enhanced digital objects"
[Luo 2023]: https://doi.org/10.1109/CCGridW59191.2023.00064 "Knowledge Enhanced Digital Objects: a Data Lake Approach"
[Lynch 2022]: https://www.npmjs.com/package/ro-crate-excel "npm: ro-crate-excel"
[Mai Chan 1995]: https://identifiers.org/isbn/9781563081910 "Library of Congress Subject Headings: Principles and Application"
[Manubens-Gil 2016]: https://doi.org/10.1109/HPCSim.2016.7568429 "Seamless management of ensemble climate prediction experiments on HPC platforms"
[Marinescu 2023]: https://identifiers.org/isbn/9780323852777 "Cloud Computing: Theory and Practice"
[Matentzoglu 2022]: https://doi.org/10.1093/database/baac087 "Ontology Development Kit: a toolkit for building, maintaining and standardizing biomedical ontologies"
[McMurry 2017]: https://doi.org/10.1371/journal.pbio.2001414 "Identifiers for the 21st century: How to design, provision, and reuse identifiers to maximize utility and impact of life science data"
[MDN 2023]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation "HTTP Content negotiation"
[de Mello 2022]: https://doi.org/10.1007/s12553-022-00639-w "Semantic interoperability in health records standards: a systematic literature review"
[Meroño-Peñuela 2021a]: https://doi.org/10.1007/978-3-031-01917-3_7 "Conclusion and future challenges"
[Meroño-Peñuela 2021b]: https://doi.org/10.1007/978-3-031-01917-3_3 "Web data APIs over SPARQL"
[Meurisse 2023]: https://s11.no/2023/phd/federated-causal-inference/ "Federated causal inference based on real-world observational data sources"
[Miksa 2019a]: https://doi.org/10.15497/rda00039 "RDA DMP Common Standard for Machine-Actionable Data Management Plans"
[Miksa 2019b]: https://doi.org/10.1371/journal.pcbi.1006750 "Ten principles for machine-actionable data management plans"
[Miksa 2020]: https://doi.org/10.4126/frl01-006423291 "Research Object Crates and Machine-actionable Data Management Plans"
[Millard 2010]: https://ceur-ws.org/Vol-665/MillardEtAl_COLD2010.pdf "Consuming multiple linked data sources: Challenges and Experiences"
[Miller 2021]: https://spec.openapis.org/oas/v3.1.0.html "OpenAPI Specification"
[Missier 2010]: https://doi.org/10.1109/WORKS.2010.5671861 "Linking multiple workflow provenance traces for interoperable collaborative science"
[Missier 2013]: https://doi.org/10.5555/2482949.2482961 "D-PROV: extending the PROV provenance model with workflow structure"
[Möller 2010]: https://doi.org/10.1186/1471-2105-11-S12-S5 "Community-driven computational biology with Debian Linux"
[Möller 2017]: https://doi.org/10.1007/s41019-017-0050-4 "Robust cross-platform workflows: How technical and scientific communities collaborate to develop, test and share best practices for data analysis"
[Mons 2017]: https://doi.org/10.3233/ISU-170824 "Cloudy, increasingly FAIR; revisiting the FAIR Data guiding principles for the European Open Science Cloud"
[Mons 2018]: https://identifiers.org/isbn/9781315351148 "Data Stewardship for Open Science"
[Moreau 2013]: https://www.w3.org/TR/2013/REC-prov-dm-20130430/ "PROV-DM: The PROV Data Model"
[myExperiment 2009]: https://web.archive.org/web/20091115080336/http%3a%2f%2frdf.myexperiment.org/ontologies "myExperiment Ontology Modules"
[Nature 2019]: https://doi.org/10.1038/s41592-019-0350-x "Giving software its due"
[NCBO]: https://bioportal.bioontology.org/ontologies "NCBO BioPortal"
[Nelson 2019a]: https://doi.org/10.1098/rstb.2017.0391 "The history and impact of digitization and digital data mobilization on biodiversity research"
[Nelson 2019b]: https://doi.org/10.3897/biss.3.37896 "DiSSCo, iDigBio and the Future of Global Collaboration"
[Neumann 2021]: https://doi.org/10.1109/TSC.2018.2847344 "An analysis of public REST web service apis"
[Newman 2009]: http://ceur-ws.org/Vol-523/Newman.pdf "myExperiment: An ontology for e-Research"
[Neylon 2017]: https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/ "As a researcher \ldots I'm a bit bloody fed up with Data Management"
[Nieva de la Hidalga 2021]: https://doi.org/10.1007/s00138-022-01276-z "Cross-validation of a semantic segmentation network for natural history collection specimens"
[Niewielska 2020]: https://doi.org/10.5281/zenodo.4916060 "BioExcel-2 Deliverable 2.5 - Provision of a Workflow Environment at BioExcel portal"
[Norris 2021]: https://doi.org/10.1186/s13326-021-00240-6 "Why and how to engage expert stakeholders in ontology development: Insights from social and behavioural sciences"
[Nottingham 2017]: https://doi.org/10.17487/rfc8288 "Web Linking"
[Nurdiati 2008]: https://purl.utwente.nl/publications/64931 "25 years development of knowledge graph theory: the results and the challenge"
[Ó Carragáin 2019a]: https://doi.org/10.5281/zenodo.3250687 "A lightweight approach to research object data packaging"
[Ó Carragáin 2019b]: https://s11.no/2019/phd/ro-crate/ "RO-Crate: A lightweight approach to research object data packaging"
[OCFL 2020]: https://ocfl.io/1.0/spec/ "OCFL, Oxford Common File Layout Specification"
[OCLC 2010]: http://info-uri.info/ "Info URI Registry (Frozen)"
[Ohta 2023]: https://doi.org/10.5281/zenodo.10134581 "Example of Workflow Run RO-Crate Output in Sapporo"
[Oliver 2019]: https://doi.org/10.1109/MCSE.2019.2906593 "Workflow Automation for Cycling Systems"
[Open Graph]: https://ogp.me/ "The Open Graph protocol"
[openDS 2021]: https://github.com/DiSSCo/openDS "Draft specification for open Digital Specimens (openDS)"
[OpenStand 2017]: https://open-stand.org/about-us/principles/ "The Modern Standards Paradigm"
[OSI 022]: https://opensource.org/licenses "Licenses & Standards"
[Owen 2020]: https://doi.org/10.3897/rio.6.e58030 "Towards a scientific workflow featuring Natural Language Processing for the digitisation of natural history collections"
[Page 2011]: https://doi.org/10.1145/1967428.1967435 "REST and Linked Data"
[Pantos 2017]: https://doi.org/10.17487/rfc8216 "HTTP Live Streaming"
[Parecki 2017]: https://www.w3.org/TR/2017/REC-micropub-20170523/ "Micropub"
[Pavel 2023]: https://doi.org/10.4126/frl01-006444984 "Ya2ro: A tool for creating Research Objects from minimum metadata"
[Pérez 2018]: https://doi.org/10.1007/s10115-018-1164-3 "A systematic review of provenance systems"
[Pergl 2019]: https://doi.org/10.5334/dsj-2019-059 "``Data Stewardship Wizard'': A Tool Bringing Together Researchers, Data Stewards, and Data Experts around Data Management Planning"
[Piper 2020]: https://doi.org/10.1080/14490854.2020.1796500 "Digital crowdsourcing and public understandings of the past: Citizen historians meet criminal characters"
[Poiata 2016]: https://doi.org/10.1093/gji/ggw071 "Multiband array detection and location of seismic sources recorded by dense seismic networks"
[Poiata 2023]: https://doi.org/10.5281/zenodo.7788030 "BackTrackBB: Multi-band array detection and location of seismic sources (PyCOMPSs implementation)"
[Polleres 2020]: https://doi.org/10.3233/SW-190380 "A more decentralized vision for linked data"
[Poveda 2010]: https://doi.org/10.1007/978-3-642-14264-2_10 "Common Pitfalls in Ontology Development"
[Price 2018]: https://doi.org/10.31219/osf.io/s2p73 "ALICE: Angled Label Image Capture and Extraction for high throughput insect specimen digitisation"
[Prlić 2012]: https://doi.org/10.1371/journal.pcbi.1002802 "Ten Simple Rules for the Open Development of Scientific Software"
[Pryer 2022]: https://doi.org/10.1002/aps3.11372 "Using computer vision on herbarium specimen images to discriminate among closely related horsetails (Equisetum)"
[RDF 1.1 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
[Rehm 2021]: https://doi.org/10.1016/j.xgen.2021.100029 "GA4GH: International policies and standards for data sharing across genomic research and healthcare"
[Reilly 2009]: https://www.dona.net/doipv1doc "Digital Object Interface Protocol Version 1.0"
[Reis 2022]: https://doi.org/10.1109/ACCESS.2021.3137671 "Developing Docker and Docker-Compose Specifications"
[Rescorla 2000]: https://doi.org/10.17487/rfc2818 "HTTP Over TLS"
[Rettberg 2015]: https://doi.org/10.5860/crln.76.6.9326 "OpenAIRE: Supporting a European open access mandate"
[Riccardi 2022]: https://doi.org/10.1002/jcc.26842 "Towards improved FAIRness of the ThermoML Archive"
[Rice 2022]: https://websockets.spec.whatwg.org/ "WebSockets Standard"
[RO-Crate 1.0]: https://doi.org/10.5281/zenodo.3541888 "RO-Crate Metadata Specification 1.0"
[RO-Crate 1.1]: https://w3id.org/ro/crate/1.1 "RO-Crate Metadata Specification 1.1"
[RO-Crate 1.1.3]: https://w3id.org/ro/crate/1.1 "RO-Crate Metadata Specification 1.1.3"
[RO-Crate 1.2]: https://www.researchobject.org/ro-crate/1.2-DRAFT/ "RO-Crate Metadata Specification 1.2.0"
[ro-crate-html-js]: https://www.npmjs.com/package/ro-crate-html-js "ro-crate-html-js"
[Robinson 2017]: https://doi.org/10.7490/f1000research.1114375.1 "CWL Viewer: The Common Workflow Language viewer"
[Robinson 2023]: https://github.com/common-workflow-language/cwlviewer "common-workflow-language/cwlviewer: v1.4.7"
[Rocca-Serra 2023]: https://doi.org/10.1038/s41597-023-02166-3 "The FAIR cookbook - the essential resource for and by FAIR doers"
[Saltz 2006]: https://doi.org/10.1093/bioinformatics/btl272 "caGrid: design and implementation of the core architecture of the cancer biomedical informatics grid"
[Samaniego 2010]: https://doi.org/10.1029/2008WR007327 "Multiscale parameter regionalization of a grid-based hydrologic model at the mesoscale"
[Samuel 2022]: https://doi.org/10.1186/s13326-021-00253-1 "End-to-End provenance representation for the understandability and reproducibility of scientific experiments using a semantic approach"
[Sandve 2013]: https://doi.org/10.1371/journal.pcbi.1003285 "Ten simple rules for reproducible computational research"
[Sandvine 2022]: https://www.sandvine.com/global-internet-phenomena-report-2022 "Global Internet Phenomena Report"
[Sauermann 2008]: http://www.w3.org/TR/cooluris/ "Cool URIs for the semantic web"
[Scheidegger 2008]: https://doi.org/10.1145/1376616.1376747 "Querying and re-using workflows with VsTrails"
[schema.org]: https://schema.org/ "Schema.org - Schema.org"
[schema actions]: https://schema.org/docs/actions.html "Schema.org Actions"
[Schreiber 2014]: http://www.w3.org/TR/2014/NOTE-rdf11-primer-20140624 "RDF 1.1 Primer"
[Schriml 2020]: https://doi.org/10.1038/s41597-020-0524-5 "COVID-19 pandemic reveals the peril of ignoring metadata standards"
[Schröder 2022]: https://doi.org/10.1186/s13326-021-00257-x "Structure-based knowledge acquisition from electronic lab notebooks for research data provenance documentation"
[Schultes 2019]: https://doi.org/10.23728/B2SHARE.166A074BFF614A31B05E9DF5BFD9809D "FAIR principles and digital objects: Accelerating convergence on a data infrastructure"
[Schultes 2020]: https://doi.org/10.31219/osf.io/2p85g "Reusable FAIR implementation profiles as accelerators of FAIR convergence"
[Schultes 2022]: https://doi.org/10.3389/data.2022.883341 "FAIR Digital Twins for Data-Intensive Research"
[Schwardmann 2022a]: https://doi.org/10.5281/zenodo.7824796 "DOIP endorsement request"
[Schwardmann 2022b]: https://doi.org/10.3897/rio.8.e96014 "Two Examples on How FDO Types can Support Machine and Human Readability"
[Scrocca 2021]: https://doi.org/10.4126/frl01-006429412 "The Survey Ontology: Packaging Survey Research as Research Objects"
[Sefton 2018]: https://doi.org/10.5281/zenodo.1445817 "DataCrate: a method of packaging, distributing, displaying and archiving Research Objects"
[Sefton 2021b]: https://github.com/UTS-eResearch/ro-crate-js "GitHub -- UTS-eResearch/ro-crate-js"
[Sefton 2021a]: http://ptsefton.com/2021/04/07/rdmpic/ "FAIR Data Management; It's a lifestyle not a lifecycle"
[Semmler 2022]: https://www.wdc-climate.de/ui/entry?acronym=C6CMAWAWMhi "IPCC DDC: AWI AWI-CM1.1MR model output prepared for CMIP6 CMIP historical"
[Singhal 2012]: https://blog.google/products/search/introducing-knowledge-graph-things-not/ "Introducing the knowledge graph: Things, not strings"
[Sirvent 2022]: https://hdl.handle.net/2117/384589 "Automatic, Efficient, and Scalable Provenance Registration for FAIR HPC Workflows"
[Smith 2007]: https://doi.org/10.1038/nbt1346 "The OBO Foundry"
[Smith 2016]: https://doi.org/10.7717/peerj-cs.86 "Software citation principles"
[Smith 2022]: https://aclanthology.org/2022.signlang-1.28 "Integrating Auslan Resources into the Language Data Commons of Australia"
[Snowley 2023]: https://www.hdruk.ac.uk/wp-content/uploads/2023/10/Integrating-Our-Community_v1-Oct-2023-compressed.pdf "Integrating Our Community"
[Soiland-Reyes 2014]: https://w3id.org/bundle/2014-11-05/ "Research Object Bundle 1.0"
[Soiland-Reyes 2016]: https://s11.no/2016/provweek-tavernaprov/ "Tracking Workflow Execution With TavernaPROV"
[Soiland-Reyes 2018]: https://doi.org/10.5281/zenodo.1471585 "common-workflow-language/cwlprov: CWLProv 0.6.0"
[Soiland-Reyes 2020a]: https://twitter.com/soilandreyes/status/1250721245622079488 "I am looking for which bioinformatics journals encourage authors to submit their code/pipeline/workflow supporting data analysis"
[Soiland-Reyes 2021]: https://doi.org/10.5281/zenodo.4633732 "Describing and packaging workflows using RO-Crate and BioCompute Objects"
[Soiland-Reyes 2022a]: https://s11.no/2022/phd/ro-crate/ "Packaging research artefacts with RO-Crate"
[Soiland-Reyes 2022b]: https://s11.no/2022/phd/canonical-workflow-building-blocks/ "Making Canonical Workflow Building Blocks interoperable across workflow languages"
[Soiland-Reyes 2022c]: https://s11.no/2022/phd/fdo-with-ro-crate/ "Creating lightweight FAIR digital objects with RO-Crate"
[Soiland-Reyes 2022d]: https://s11.no/2022/phd/updating-ld-for-fdo/ "Updating Linked Data practices for FAIR Digital Object principles"
[Soiland-Reyes 2022e]: https://doi.org/10.5281/zenodo.7256713 "stain/signposting: Signposting v0.9.0"
[Soiland-Reyes 2022f]: https://doi.org/10.5281/zenodo.7152762 "EuroScienceGateway: WP2 introduction"
[Soiland-Reyes 2022g]: https://w3id.org/ro/doi/10.5281/zenodo.5146227 "Packaging research artefacts with RO-Crate"
[Soiland-Reyes 2023a]: https://w3id.org/ro/doi/10.5281/zenodo.8075229 "Comparison tables for evaluating FAIR Digital Object and Linked Data"
[Soiland-Reyes 2023b]: https://doi.org/10.5281/zenodo.7774582 "Enabling FAIR Signposting and RO-Crate for content/metadata discovery and consumption"
[Soiland-Reyes 2023c]: https://s11.no/2023/phd/evaluating-fdo/ "Evaluating FAIR Digital Object and Linked Data as distributed object systems"
[Soiland-Reyes 2023d]: https://doi.org/10.5281/zenodo.7828632 "Building diverse FDO Collections using RO-Crate"
[Soiland-Reyes 2023e]: https://w3id.org/5s-crate/0.4 "Five Safes RO-Crate profile"
[Soiland-Reyes 2023f]: https://doi.org/10.5281/zenodo.10376350 "TRE-FX Technical Documentation - Five Safes RO-crate"
[Soiland-Reyes 2024]: https://doi.org/10.37044/osf.io/gmk2h "Enabling FAIR Digital Objects with RO-Crate, Signposting and Bioschemas"
[Speicher 2015]: http://www.w3.org/TR/2015/REC-ldp-20150226/ "Linked Data Platform 1.0"
[Sporny 2014]: https://www.w3.org/TR/2014/REC-json-ld-20140116/ "JSON-LD 1.0: A JSON-based Serialization for Linked Data"
[Sporny 2015]: https://www.w3.org/TR/2015/NOTE-rdfa-primer-20150317/ "RDFa 1.1 Primer"
[Sporny 2020]: https://www.w3.org/TR/2020/REC-json-ld11-20200716/ "JSON-LD 1.1: A JSON-based Serialization for Linked Data"
[Sporny 2023]: https://datatracker.ietf.org/doc/draft-ietf-mediaman-suffixes/03/ "Media Types with Multiple Suffixes"
[Stallings 1990]: https://identifiers.org/isbn/9780672226977 "Handbook of computer-communications standards: The open systems (OSI) model and OSI-related standards" 
[Stanczyk 1987]: https://doi.org/10.21954/ou.ro.0000f821 "Process modelling for information system description"
[Stefi 2015a]: http://doi.org/10.1007/978-3-319-19593-3_18 "To develop or to reuse? Two perspectives on external reuse in software projects"
[Stefi 2015b]: https://doi.org/10.18151/7217489 "Do Developers Make Unbiased Decisions? - The Effect of Mindfulness and Not-Invented-Here Bias on the Adoption of Software Components"
[Stodden 2016]: https://doi.org/10.1126/science.aah6168 "Enhancing reproducibility for computational methods"
[Suetake 2022]: https://doi.org/10.12688/f1000research.122924.1 "Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics"
[Suetake 2023a]: https://doi.org/10.1093/gigascience/giad031 "A workflow reproducibility scale for automatic validation of biological interpretation results"
[Suetake 2023b]: https://doi.org/10.5281/zenodo.10134452 "sapporo-wes/sapporo-service"
[Sun 2003a]: https://doi.org/10.17487/rfc3650 "Handle System Overview"
[Sun 2003b]: https://doi.org/10.17487/rfc3652 "Handle System Protocol (ver 2.1) Specification"
[Sweeney 2018]: https://doi.org/10.12705/671.10 "Large-scale digitization of herbarium specimens: Development and usage of an automated, high-throughput conveyor system"
[Taschuk 2017]: https://doi.org/10.1371/journal.pcbi.1005412 "Ten simple rules for making research software more robust"
[Taivalsaari 2021]: https://doi.org/10.1007/978-3-030-74296-6_28 "Full Stack Is Not What It Used to Be"
[Tegelberg 2017]: https://doi.org/10.1109/eScience.2017.85 "Mass Digitization of Individual Pinned Insects Using Conveyor-Driven Imaging"
[Tejedor 2017]: https://doi.org/10.1177/1094342015594678 "PyCOMPSs: Parallel computational workflows in Python"
[Thieberger 2012]: https://hdl.handle.net/10125/4567 "Keeping records of language diversity in melanesia: The Pacific and regional archive for digital sources in endangered cultures (PARADISEC)"
[Thiers 2016]: https://doi.org/10.1007/s12228-016-9423-7 "Digitization of the New York Botanical Garden herbarium"
[Thompson 2012]: https://www.w3.org/TR/2012/REC-xmlschema11-1-20120405/ "W3C XML Schema Definition Language (XSD) 1.1 Part 1"
[Thompson 2020]: https://doi.org/10.1162/dint_a_00031 "Making FAIR Easy with FAIR Tools: From Creolization to Convergence"
[Thornton 2019]: https://doi.org/10.1007/978-3-030-21348-0_39 "Using shape expressions (ShEx) to share RDF data models and to guide curation with rigorous validation"
[Tirmizi 2011]: https://doi.org/10.1186/2041-1480-2-s1-s3 "Mapping between the OBO and OWL ontology languages"
[Tran 2014]: https://doi.org/10.1007/978-3-319-05458-2_27 "Linked Data Mashups: A Review on Technologies, Applications and Challenges"
[Trautwein 2022]: https://doi.org/10.48550/arXiv.2208.05877 "Design and Evaluation of IPFS: A Storage Layer for the Decentralized Web"
[Triki 2020]: https://doi.org/10.5220/0009170005230529 "Objects Detection from Digitized Herbarium Specimen based on Improved YOLO V3"
[Troncy 2010]: https://www.persistent-identifier.nl/urn:nbn:nl:ui:18-14511 "VAMP: A service for validating MPEG-7 descriptions w.r.t. to formal profile definitions"
[Tudorache 2020]: https://doi.org/10.3233/SW-190382 "Ontology engineering: Current state, challenges, and future directions"
[Tupelo-Scheck 2022]: https://www.rd-alliance.org/sites/default/files/Cordra.2022.pdf "Brief Introduction to Cordra & DOIP"
[Turcoane 2014]: https://doi.org/10.55630/dipp.2014.4.11 "Linked data, JSON-LD and the semantics of cultural and scientific heritage"
[Unger 2016]: https://doi.org/10.1186/s12862-016-0827-5 "Computer vision applied to herbarium specimens of German trees"
[Van de Sompel 2007]: http://icl.utk.edu/ctwatch/quarterly/articles/2007/08/interoperability-for-the-discovery-use-and-re-use-of-units-of-scholarly-communication/ "Interoperability for the discovery, use, and re-use of units of scholarly communication"
[Van de Sompel 2013]: https://doi.org/10.17487/rfc7089 "HTTP Framework for Time-Based Access to Resource States --Memento"
[Van de Sompel 2015]: https://doi.org/10.1045/november2015-vandesompel "Reminiscing About 15 Years of Interoperability Efforts"
[Van de Sompel 2022]: https://signposting.org/FAIR/ "FAIR Signposting Profile"
[Van de Sompel 2023]: https://doi.org/10.5281/zenodo.7977333 "FAIR Digital Objects and FAIR Signposting"
[Verborgh 2018]: https://ruben.verborgh.org/blog/2018/12/28/designing-a-linked-data-developer-experience/ "Designing a Linked Data developer experience"
[Verborgh 2020]: https://doi.org/10.3233/SW-190372 "The semantic web identity crisis: In search of the trivialities that never were"
[Verburg 2023]: https://doi.org/10.5281/zenodo.7848102 "FAIR-IMPACT project response to \"FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons\""
[Vergoulis 2021]: https://doi.org/10.5281/zenodo.4671709 "Use of RO-Crates in SCHeMa"
[Vergoulis 2022]: https://doi.org/10.48550/arXiv.2103.13138 "SCHeMa: Scheduling Scientific Containers on a Cluster of Heterogeneous Machines"
[de Visser 2023]: https://doi.org/10.1371/journal.pcbi.1011369 "Ten quick tips for building FAIR workflows"
[Vivian 2017]: https://doi.org/10.1038/nbt.3772 "Toil enables reproducible, open source, big biomedical data analyses"
[Volk 2014]: https://doi.org/10.1007/s00267-014-0258-2 "Why is data sharing in collaborative natural resource efforts so hard and what can we do to improve it?"
[W3C 2007]: https://www.w3.org/2001/tag/doc/httpRange-14/2007-08-31/HttpRange-14.html "Dereferencing HTTP URIs"
[W3C 2012]: https://www.w3.org/TR/2012/REC-owl2-overview-20121211 "OWL 2 Web Ontology Language Document Overview"
[W3C 2013]: https://www.w3.org/TR/2013/REC-sparql11-overview-20130321/ "SPARQL 1.1 Overview"
[W3C 2015]: https://www.w3.org/standards/semanticweb/data "Linked Data"
[W3Techs 2023]: https://w3techs.com/technologies/details/da-jsonld "Usage Statistics of JSON-LD for Websites"
[Walton 2020a]: https://doi.org/10.3897/rio.6.e57602 "Landscape Analysis for the Specimen Data Refinery"
[Walton 2020b]: https://doi.org/10.3897/rio.6.e56211 "A cost analysis of transcription systems"
[Watanabe 2019]: https://doi.org/10.1093/biosci/biy163 "The Evolution of Natural History Collections: New research tools move specimens, data to center stage"
[WHATWG 2023]: https://html.spec.whatwg.org/multipage/microdata.html "Microdata"
[Weigel 2018]: https://doi.org/10.15497/rda00031 "RDA Recommendation on PID Kernel Information"
[Weigel 2022]: https://doi.org/10.5281/zenodo.7825693 "FDO -- kernel attributes & metadata"
[Weiland 2022a]: https://drive.google.com/file/d/1lPNBBROjEoZ6fTfrtdqcMa3Q2G27PoC_ "FAIR Digital Objects Forum Document Standards"
[Weiland 2022b]: https://doi.org/10.5281/zenodo.7825650 "FDO machine actionability"
[de Wit 2022]: https://doi.org/10.5281/zenodo.7113250 "A Non-Intimidating Approach to Workflow Reproducibility in Bioinformatics"
[de Wit 2023]: https://doi.org/10.5281/zenodo.10251812 "Analysis of runcrate"
[Wieczorek 2012]: https://doi.org/10.1371/journal.pone.0029715 "Darwin Core: An Evolving Community-Developed Biodiversity Data Standard"
[Wilde 2013]: https://doi.org/10.17487/rfc6906 "The 'profile' Link Relation Type"
[Wilde 2020]: https://doi.org/10.17487/rfc9264 "Linkset: Media Types and a Link Relation Type for Link Sets"
[Wilkinson 2016]: https://doi.org/10.1038/sdata.2016.18 "The FAIR Guiding Principles for scientific data management and stewardship"
[Wilkinson 2018]: https://doi.org/10.1038/sdata.2018.118 "A design framework and exemplar metrics for FAIRness"
[Wilkinson 2022a]: https://doi.org/10.5281/zenodo.7463421 "FAIR Assessment Tools: Towards an “Apples to Apples” Comparisons"
[Wilkinson 2022b]: https://doi.org/10.48550/arxiv.2209.09022 "F*** workflows: When parts of FAIR are missing"
[Wilkinson 2023a]: https://doi.org/10.12688/openreseurope.15364.2 "Community-driven governance of FAIRness assessment"
[Wilkinson 2024]: https://s11.no/2024/signposting-report/ "Report on FAIR Signposting and its uptake by the community"
[Williams 2012]: https://doi.org/10.1016/j.drudis.2012.05.016 "Open PHACTS: Semantic interoperability for drug discovery"
[Wittenburg 2019]: https://doi.org/10.23728/b2share.b605d85809ca45679b110719b6c6cb11 "Digital objects as drivers towards convergence in data infrastructures"
[Wittenburg 2022a]: https://doi.org/10.1162/dint_a_00132 "Canonical Workflows to Make Data FAIR"
[Wittenburg 2022b]: https://doi.org/10.5281/zenodo.5872645 "FAIR digital object demonstrators 2021"
[Wittenburg 2023a]: https://doi.org/10.52825/cordi.v1i.263 "FDOs to Enable Cross-Silo Work"
[Wittenburg 2023b]: https://doi.org/10.52825/cordi.v1i.374 "FDO to Structure the Domain of Knowledge"
[Wittner 2020]: https://s11.no/2021/phd/iso-23494-provenance/ "ISO 23494: Biotechnology - Provenance Information Model for Biological Specimen and Data"
[Wittner 2022]: https://doi.org/10.1038/s41597-022-01537-6 "Lightweight Distributed Provenance Model for Complex Real--world Environments"
[Wittner 2023a]: https://doi.org/10.1002/lrh2.10365 "Toward a common standard for data and specimen provenance in life sciences"
[Wittner 2023b]: https://s11.no/2023/phd/linking-provenance/ "Linking provenance and its metadata in multi-organizational environments of life sciences"
[Wittner 2023c]: https://doi.org/10.5281/zenodo.8095888 "Packing provenance using CPM RO-Crate profile"
[Wolstencroft 2011]: https://doi.org/10.1093/bioinformatics/btr312 "RightField: Embedding ontology annotation in spreadsheets"
[Wolstencroft 2013]: https://doi.org/10.1093/nar/gkt328 "The Taverna workflow suite"
[Wood 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
[Woolland 2022]: https://doi.org/10.3897/rio.8.e94349 "Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows"
[WorkflowHub 2023]: https://w3id.org/workflowhub/ "WorkflowHub project: Project pages for developing and running the WorkflowHub, a registry of scientific workflows"
[Wright 2022]: https://datatracker.ietf.org/doc/draft-bhutton-json-schema/01/ "JSON schema: A media type for describing JSON documents"
[WRROC 2023a]: https://w3id.org/ro/wfrun/process/0.4 "Process Run Crate specification"
[WRROC 2023b]: https://w3id.org/ro/wfrun/workflow/0.4 "Workflow Run Crate specification"
[WRROC 2023c]: https://w3id.org/ro/wfrun/provenance/0.4 "Provenance Run Crate specification"
[Yoo 2003]: https://doi.org/10.1007/10968987_3 "SLURM: Simple Linux Utility for Resource Management"
[Yuen 2021]: https://doi.org/10.1093/nar/gkab346 "The Dockstore: enhancing a community platform for sharing reproducible and accessible computational protocols"
[Zarras 2004]: https://doi.org/10.5381/jot.2004.3.5.a2 "A Comparison Framework for Middleware Infrastructures"
[Zerouali 2023]: https://doi.org/10.1109/MSR59073.2023.00078 "Helm Charts for Kubernetes Applications: Evolution, Outdatedness and Security Risks"
[Zhao 2012]: https://research.manchester.ac.uk/en/publications/cba81ca4-e92c-408e-8442-383d1f15fcdf "Why workflows break -- understanding and combating decay in taverna workflows"
[Zoubek 2021]: https://github.com/e11938258/RO-Crates-and-Excel "RO Crates and Excel"
[Žumer 2009]: https://doi.org/10.1515/9783598441844 "National Bibliographies in the Digital Age: Guidance and New Directions"
[Bisol 2014]: https://www.isita-org.com/jass/Contents/2014vol92/Destro/25020017.pdf "Perspectives on Open Science and Scientific Data Sharing"
[Carballo-Garcia 2022]: https://doi.org/10.37441/cejer/2022/4/2/11379 "FAIR Data: History and Present Context"
[Davidson 2019]: https://doi.org/10.5281/zenodo.5537032 "D3.1 FAIR Policy Landscape Analysis"
[Davidson 2022]: https://doi.org/10.5281/zenodo.6699333 "D3.8 Final report on policy and practice recommendations and support"
[Duarte 2023]: https://doi.org/10.1088/2632-2153/ad12e3 "FAIR AI models in high energy physics"
[Garcia 2020a]:  https://doi.org/10.1371/journal.pcbi.1007854 "Ten simple rules for making training materials FAIR"
[Gruenpeter 2021]: https://doi.org/10.5281/zenodo.5504016 "Defining Research Software: A Controversial Discussion"
[Hashem 2015]: https://doi.org/10.1016/j.is.2014.07.006 "The rise of “big data” on cloud computing"
[Ioannidis 2005]: https://doi.org/10.1371/journal.pmed.1004085 "Why Most Published Research Findings Are False"
[Kitchin 2021]: https://identifiers.org/isbn/9781529733761 "The Data Revolution"
[Leach 2005]: https://doi.org/10.17487/rfc4122 "A Universally Unique IDentifier (UUID) URN Namespace"
[Mons 2020]: https://doi.org/10.1162/dint_e_00023 "The FAIR Principles: First Generation Implementation Choices and Challenges"
[Riungu-Kalliosaari 2022]: https://doi.org/10.5281/zenodo.6685820 "D2.10 3rd Report on FAIR requirements for persistence and interoperability"
[Sansone 2019]: https://doi.org/10.1038/s41587-019-0080 "FAIRsharing as a community approach to standards, repositories and policies"
[Schouppe 2018]: https://ceur-ws.org/Vol-2277/paper01.pdf "Relevance of EOSC and FAIR in the Realm of Open Science and Phases of Implementing the EOSC"
[Serwadda 2018]: https://doi.org/10.1126/science.aap8395 "Open data sharing and the Global South—Who benefits?"
[Shanahan 2021]: https://doi.org/10.1016/j.patter.2021.100324 "Progress toward a comprehensive teaching approach to the FAIR data principles"
[Śledź 2018]: https://doi.org/10.1016/j.sbi.2017.10.010 "Protein structure-based drug design"
[Soiland-Reyes 2024c] https://s11.no/2024/webby-fdos/ "Practical webby FDOs with RO-Crate and FAIR Signposting"
[Åkerström 2024]: https://doi.org/10.5281/zenodo.10843882 "Developing and implementing the semantic interoperability recommendations of the EOSC Interoperability Framework"
