---
title: "Supplement 2: Enhancing RDM in Galaxy by integrating RO-Crate"
weight: 220
lang: en-GB
categories:
  - PhD
date-meta: '2022-07-10'
summary: >
  Poster abstract presented at FAIR Digital Objects conference (FDO2022)
description: >
  We introduce how the Galaxy research environment integrates with RO-Crate as an implementation of Findable Accessible Interoperable Reproducible Digital Objects and how using RO-Crate as an exchange mechanism of workflows and their execution history helps integrate Galaxy with the wider ecosystem of ELIXIR and EOSC to enable FAIR and reproducible data analysis.
keywords:
  - FAIR digital object
  - workflow
  - exchange format
  - packaging format
  - metadata description
  - FAIR
  - reproducible data analysis  
---

<h2>Cite as</h2>

Paul De Geest, Frederik Coppens, Stian Soiland-Reyes, Ignacio Eguinoa, Simone Leo (2022):  
**Enhancing RDM in Galaxy by integrating RO-Crate**.  
1st International Conference on FAIR Digital Objects ([FDO 2022](https://www.fdo2022.org/)) (poster)  
_Research Ideas and Outcomes_ **8**:e95164  
<https://doi.org/10.3897/rio.8.95164>

# Enhancing RDM in Galaxy by integrating RO-Crate

_Paul De Geest¹, Frederik Coppens¹, Stian Soiland-Reyes²³, Ignacio Eguinoa¹, Simone Leo⁴_

<div class="affiliations">

¹ VIB-UGent Center for Plant Systems Biology, Gent, Belgium  
² Department of Computer Science, The University of Manchester, Manchester, United Kingdom  
³ Informatics Institute, University of Amsterdam, Amsterdam, Netherlands  
⁴ Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Pula (CA), Italy  

</div>

## Abstract

We introduce how the Galaxy research environment integrates with RO-Crate as an implementation of Findable Accessible Interoperable Reproducible Digital Objects and how using RO-Crate as an exchange mechanism of workflows and their execution history helps integrate Galaxy with the wider ecosystem of ELIXIR and EOSC to enable FAIR and reproducible data analysis.

RO-Crate [[Soiland-Reyes 2022](https://doi.org/10.3233/ds-210053)] is a generic packaging format containing datasets and their description using standards for FAIR Linked Data. The format is based on schema.org [[Guha 2016](https://doi.org/10.1145/2844544)] annotations in JSON-LD, which allows for rich metadata representation. The RO-Crate effort aims to make best-practice in formal metadata description accessible and practical for use in a wider variety of situations, from an individual researcher working with a folder of data, to large data-intensive computational research environments.

The [RO-Crate](https://w3id.org/ro/crate) community brings together practitioners from very different backgrounds, and with different motivations and use-cases. Among the core target users are:

- researchers engaged with computation and data-intensive, workflow-driven analysis;
- digital repository managers and infrastructure providers;
- individual researchers looking for a straight-forward tool or how-to guide to “FAIRify” their data;
- data stewards supporting research projects in creating and curating datasets.

Given the wide applicability of RO-Crate and the lack of practical implementations of FDOs, ELIXIR [[Harrow 2021](https://doi.org/10.1093/bioinformatics/btab481)] co-opted this initiative as the project to define a common format for research data exchange and repository entries. Thus, during the last year it’s been implemented in a wide range of services, such as: [WorkflowHub](https://workflowhub.eu/) [[Goble 2021](https://doi.org/10.5281/zenodo.4605654)] (a registry for describing, sharing and publishing scientific computational workflows) uses RO-Crates as an exchange format to improve reproducibility of computational workflows that follow the Workflow RO-Crate profile [[Bacall 2022b](https://w3id.org/workflowhub/workflow-ro-crate/1.0)]; LifeMonitor [[Leo 2022](https://about.lifemonitor.eu/)] (a service to support the sustainability of computational workflows being developed as part of the [EOSC-Life](https://www.eosc-life.eu/) project) uses RO-Crate as an exchange format for describing test suites associated with workflows. 

Tools have been developed towards aiding the previously mentioned use-cases and increasing the general usability of RO-Crates by providing a user-friendly (programmatic) interface for consumption -- and production of RO-Crates through programmatic libraries for consuming/producing RO-Crates (ro-crate-py [[De Geest 2022](https://doi.org/10.5281/zenodo.3956493)], ro-crate-ruby [[Bacall 2022a](https://doi.org/10.5281/zenodo.6810687]), ro-crate-js [[Lynch 2021](https://github.com/UTS-eResearch/ro-crate-js)]).

The [Galaxy](https://galaxyproject.org/) project [[Jalili 2020](https://doi.org/10.1093/nar/gkaa434)] provides a research environment with data analysis and data management functionalities as a multi user platform, aiming to make computational biology accessible to research scientists that do not have computer programming or systems administration experience. As such, it stores not just analysis related data but also the complete analytical workflow, including its metadata. The internal data model involves the history entity, including all steps performed in a specific analysis, and the workflow entity, defining the structure of an analytical pipeline. 

From the start, Galaxy aims to enable reproducible analyses by providing capabilities to export (and import) all the analysis history details and workflow data and metadata in a FAIR way. As such it helps  its users with the daily research data management. The Galaxy community is continuously improving and adding features, the integration of the FAIR Digital Object principles is a natural next step in this. 

To be able to support these FDOs, Galaxy leverages the RO-Crate Python client library [[De Geest 2022](https://doi.org/10.5281/zenodo.3956493)] and provides multiple entry points to import and export different research data objects representing its internal entities and associated metadata. These objects include:

1. a workflow definition, which is used to share/publish the details of an analysis pipeline, including the graph of tools that need to be executed, and metadata about the data types required
2. individual data files or a collection of datasets related to an analysis history
3. a compressed archive of the entire analysis history including the metadata associated with it such as the tools used, their versions, the parameters chosen, workflow invocation related metadata, inputs, outputs, license, author, CWLProv description [[Khan 2019](https://doi.org/10.1093/gigascience/giz095)] of the workflow, contextual references (DOIs), EDAM terms [[Ison 2013](https://doi.org/10.1093/bioinformatics/btt113)], etc. 

The adoption of RO-Crate by Galaxy allows a standardised exchange of FDOs with other platforms in the ELIXIR Tools ecosystem, such as WorkflowHub and LifeMonitor. Integrating RO-Crate deeply into Galaxy and offering import and export options of various Galaxy objects as Research Objects allows for increased standardisation, improved RDM functionalities, smoother UX as well as improved interoperability with other systems. 

RO-Crate integration in a platform used by biologists to do data intensive analysis, facilitates the publication of workflows and workflow invocations for all skill levels, democratising the ability to perform Open Science.



## Presenting author

Paul De Geest

## Submitted to be presented at

First International Conference on FAIR Digital Objects, poster

* Poster: <https://doi.org/10.5281/zenodo.7257146>


## References

[Bacall 2022a] Finn Bacall, Martyn Whithell (2022):  
**ResearchObject/ro-crate-ruby** v0.4.17  
_Zenodo_  
<https://doi.org/10.5281/zenodo.6810687>

[Bacall 2022b] Finn Bacall, Alan R. Williams, Stuart Owen, Stian Soiland-Reyes (2022):  
**Workflow RO-Crate Profile 1.0**.  
<https://w3id.org/workflowhub/workflow-ro-crate/1.0>

[De Geest 2022] Paul De Geest, Bert Droesbeke, Ignacio Eguinoa, Alban Gaignard, Sebastiaan Alban, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, Raül Sirvent, Stian Soiland-Reyes (2022):  
**ro-crate-py** v0.7.0  
_Zenodo_  
<https://doi.org/10.5281/zenodo.3956493>

[Goble 2021] Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca Pireddu, Laura Rodriguez-Navas, José Mª Fernández, Salvador Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano, Philip Ewels, Frederik Coppens (2021):  
**Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory**.  
_Zenodo_  
<https://doi.org/10.5281/zenodo.4605654>

[Guha 2016] R. V. Guha, Dan Brickley, Steve Macbeth (2016):  
**Schema.org: evolution of structured data on the web**.  
_Communications of the ACM_ **59**(2)  
<https://doi.org/10.1145/2844544>

[Harrow 2021] Jennifer Harrow, Rachel Drysdale, Andrew Smith, Susanna Repo, Jerry Lanfear, Niklas Blomberg (2021):  
**ELIXIR: providing a sustainable infrastructure for life science data at European scale**.  
_Bioinformatics_ **37**(16)  
<https://doi.org/10.1093/bioinformatics/btab481>

[Ison 2013] Jon Ison, Matúš Kalaš, Inge Jonassen, Dan Bolser, Mahmut Uludag, Hamish McWilliam, James Malone, Rodrigo Lopez, Steve Pettifer, Peter Rice (2013):  
**EDAM: an ontology of bioinformatics operations, types of data and identifiers, topics and formats**.  
*Bioinformatics* **29**(10)  
<https://doi.org/10.1093/bioinformatics/btt113>

[Jalili 2020] Vahid Jalili, Enis Afgan, Qiang Gu, Dave Clements, Daniel Blankenberg, Jeremy Goecks, James Taylor, Anton Nekrutenko (2020):  
**The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2020 update**.  
_Nucleic Acids Research_ **48**(W1)  
<https://doi.org/10.1093/nar/gkaa434>

[Khan 2019] Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):  
**Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv**.
_GigaScience_ **8**(11):giz095
<https://doi.org/10.1093/gigascience/giz095>

[Leo 2022] Simone Leo, Marco Enrico Piras, Luca Pireddu (2022):  
**Welcome to Life-Monitor**.  
<https://about.lifemonitor.eu/> (accessed [2022-07-12](https://web.archive.org/web/20220712130933/https://about.lifemonitor.eu/))

[Lynch 2021] Mike Lynch, Peter Sefton, Stian Soiland-Reyes (2021):  
**UTS-eResearch/ro-crate-js v2.0.7**.  
_GitHub_, Release date: 2021-12-07  
<https://github.com/UTS-eResearch/ro-crate-js>
    
[Soiland-Reyes 2022] Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):  
[**Packaging research artefacts with RO-Crate**](../ro-crate/).  
_Data Science_ (pre-press)  
<https://doi.org/10.3233/DS-210053>

