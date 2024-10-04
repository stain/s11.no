---
title: Applying the FAIR Principles to Computational Workflows
categories:
  - Publication
summary: >
  arXiv preprint submitted to Scientific Data
description: >
  Recent trends within computational and data sciences show an increasing recognition and adoption of computational workflows as tools for productivity, reproducibility, and democratized access to platforms and processing know-how.  As digital objects to be shared, discovered, and reused, computational workflows benefit from the FAIR principles, which stand for Findable, Accessible, Interoperable, and Reusable. The Workflows Community Initiative’s FAIR Workflows Working Group (WCI-FW), a global and open community of researchers and developers working with computational workflows across disciplines and domains, has systematically addressed the application of both FAIR data and software principles to computational workflows. We present our recommendations with commentary that reflects our discussions and justifies our choices and adaptations. Like the software and data principles on which they are based, these are offered to workflow users and authors, workflow management system developers, and providers of workflow services as guide rails for adoption and fodder for discussion. Workflows are becoming more prevalent as documented, automated instruments for data analysis, data collection, AI-based predictions, and simulations. The FAIR recommendations for workflows that we propose in this paper will maximize their value as research assets and facilitate their adoption by the wider community.
tags:
  - FAIR
  - Workflow
authors:
  - name: Sean Wilkinson
    orcid: https://orcid.org/0000-0002-1443-7479
  - name: Meznah Aloqalaa
    orcid: https://orcid.org/0000-0002-1382-3896
  - name: Khalid Belhajjame
    orcid: https://orcid.org/0000-0001-6938-0820
  - name: Michael R. Crusoe
    orcid: https://orcid.org/0000-0002-2961-9670
  - name: Bruno de Paula Kinoshita
    orcid: https://orcid.org/0000-0001-8250-4074
  - name: Luiz Gadelha
    orcid: https://orcid.org/0000-0002-8122-9522
  - name: Daniel Garijo
    orcid: https://orcid.org/0000-0003-0454-7145
  - name: Ove Johan Ragnar Gustafsson
    orcid: https://orcid.org/0000-0002-2977-5032
  - name: Nick Juty
    orcid: https://orcid.org/0000-0002-2036-8350
  - name: Sehrish Kanwal
    orcid: https://orcid.org/0000-0002-5044-4692
  - name: Farah Zaib Khan
    orcid: https://orcid.org/0000-0002-6337-3037
  - name: Johannes Köster
    orcid: https://orcid.org/0000-0001-9818-9320
  - name: Karsten Peters-von Gehlen
    orcid: https://orcid.org/0000-0003-0158-2957
  - name: Line Pouchard
    orcid: https://orcid.org/0000-0002-2120-6521
  - name: Randy K. Rannow
    orcid: https://orcid.org/0009-0005-7406-6170
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
  - name: Nicola Soranzo
    orcid: https://orcid.org/0000-0003-3627-5340
  - name: Shoaib Sufi
    orcid: https://orcid.org/0000-0001-6390-2616
  - name: Ziheng Sun
    orcid: https://orcid.org/0000-0001-9810-0023
  - name: Baiba Vilne
    orcid: https://orcid.org/0000-0002-1084-7067
  - name: Merridee A. Wouters
    orcid: https://orcid.org/0000-0002-2121-912X
  - name: Denis Yuen
    orcid: https://orcid.org/0000-0002-6130-1021
  - name: Carole Goble
    orcid: https://orcid.org/0000-0003-1219-2137
---


<h2>Cite as</h2>

Sean Wilkinson, Meznah Aloqalaa, Khalid Belhajjame, Michael R. Crusoe, Bruno de Paula Kinoshita, Luiz Gadelha, Daniel Garijo, Ove Johan Ragnar Gustafsson, Nick Juty, Sehrish Kanwal, Farah Zaib Khan, Johannes Köster, Karsten Peters-von Gehlen, Line Pouchard, Randy K. Rannow, Stian Soiland-Reyes, Nicola Soranzo, Shoaib Sufi, Ziheng Sun, Baiba Vilne, Merridee A. Wouters, Denis Yuen, Carole Goble (2024):  
**Applying the FAIR Principles to Computational Workflows**.  
_arXiv_ (submitted)


# Applying the FAIR Principles to Computational Workflows

_Sean Wilkinson<sup>1</sup>, Meznah Aloqalaa<sup>2</sup>, Khalid Belhajjame<sup>3</sup>, Michael R. Crusoe<sup>4</sup>, Bruno de Paula Kinoshita<sup>5</sup>, Luiz Gadelha<sup>6</sup>, Daniel Garijo<sup>7</sup>, Ove Johan Ragnar Gustafsson<sup>8</sup>, Nick Juty<sup>2</sup>, Sehrish Kanwal<sup>9</sup>, Farah Zaib Khan<sup>8</sup>, Johannes Köster<sup>10</sup>, Karsten Peters-von Gehlen<sup>11</sup>, Line Pouchard<sup>12</sup>, Randy K. Rannow<sup>13</sup>, Stian Soiland-Reyes<sup>2,14</sup>, Nicola Soranzo<sup>15</sup>, Shoaib Sufi<sup>2</sup>, Ziheng Sun<sup>16</sup>, Baiba Vilne<sup>17</sup>, Merridee A. Wouters<sup>18</sup>, Denis Yuen<sup>19</sup>, Carole Goble<sup>2</sup>_

<div class="affiliations">

<sup>1</sup> Oak Ridge Leadership Computing Facility, Oak Ridge National Laboratory, Oak Ridge, Tennessee, USA  
<sup>2</sup> Department of Computer Science, University of Manchester, Manchester, UK  
<sup>3</sup> LAMSADE, PSL, Paris Dauphine University, Paris, France  
<sup>4</sup> Mathematics of Complex Systems division, Visual and Data-Centric Computing department, Bioinformatics in Medicine group, Zuse Institute Berlin (ZIB), Berlin, Germany  
<sup>5</sup> Earth Sciences, Barcelona Supercomputing Center, Barcelona, Spain  
<sup>6</sup> German Human Genome-Phenome Archive (GHGA, W620), German Cancer Research Center (DKFZ), Heidelberg, Germany  
<sup>7</sup> Ontology Engineering Group, Universidad Politécnica de Madrid, Madrid, Spain  
<sup>8</sup> Australian BioCommons, University of Melbourne, Melbourne, Victoria, Australia  
<sup>9</sup> Clinical Pathology, University of Melbourne Centre for Cancer Research (UMCCR), Parkville, Victoria, Australia  
<sup>10</sup> Bioinformatics and computational oncology (Bioinformatische Algorithmen in der Onkologie), Institute for AI in Medicine (IKIM), University Medicine Essen, University of Duisburg-Essen, Essen, Germany  
<sup>11</sup> Data Management Department, Deutsches Klimarechenzentrum GmbH, Hamburg, Germany  
<sup>12</sup> Center for Computing Research, Sandia National Laboratories, Albuquerque, New Mexico, USA  
<sup>13</sup> Silverdraft Supercomputing, Boise, Idaho, USA  
<sup>14</sup> Informatics Institute, University of Amsterdam, Amsterdam, The Netherlands  
<sup>15</sup> Earlham Institute, Norwich, UK  
<sup>16</sup> Center for Spatial Information Science and Systems, Department of Geography and Geoinformation Science, George Mason University, Fairfax, Virginia, USA  
<sup>17</sup> Bioinformatics Group, Riga Stradins University, Riga, Latvia  
<sup>18</sup> School of Clinical Medicine, University of New South Wales, Kensington, New South Wales, Australia  
<sup>19</sup> Ontario Institute for Cancer Research, Toronto, Ontario, Canada  

</div>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Reformatting as Markdown; references in s11 house style; inline citation hyperlinks; inline hyperlinks; paragraph breaks for readability. 


## Abstract

Recent trends within computational and data sciences show an increasing recognition and adoption of computational workflows as tools for productivity, reproducibility, and democratized access to platforms and processing know-how.  As digital objects to be shared, discovered, and reused, computational workflows benefit from the FAIR principles, which stand for Findable, Accessible, Interoperable, and Reusable. The Workflows Community Initiative’s FAIR Workflows Working Group (WCI-FW), a global and open community of researchers and developers working with computational workflows across disciplines and domains, has systematically addressed the application of both FAIR data and software principles to computational workflows. 

We present our recommendations with commentary that reflects our discussions and justifies our choices and adaptations. Like the software and data principles on which they are based, these are offered to workflow users and authors, workflow management system developers, and providers of workflow services as guide rails for adoption and fodder for discussion. Workflows are becoming more prevalent as documented, automated instruments for data analysis, data collection, AI-based predictions, and simulations. The FAIR recommendations for workflows that we propose in this paper will maximize their value as research assets and facilitate their adoption by the wider community.

## Computational workflows and why FAIR matters

Scale ups in research data and the rise of data driven science has spurred the research community to find solutions for managing and automating complex computational processes, ensuring efficiency, reproducibility , scalability, collaboration and quality assured transparency. Computational workflows are a special kind of software specifically targeted at handling multi-step, multi-code data pipelines, data analyses, and other data-handling operations, especially through the efficient use of computational resources to transform data inputs into desired outputs.

Computational workflows are software with two prominent characteristics: (i) the composition (component number, order, structure) of **multiple components** that include other software, workflows, code snippets, tools, and services  and  (ii) the **explicit abstraction** from the run mechanics in some form of **high-level workflow language** that precisely specifies the flow of data between the components, relying on a dedicated management system concerned with data handling and code execution.  Metadata details the dependencies and computational requirements, including those of the computational environment \[Schintke 2024\].

At one end of the scale the workflow language might be a simple script (e.g. Bash, Python, R) or enumerated stages in an electronic research notebook (e.g. Jupyter, RStudio, Apache Zeppelin) with a set of instructions that use inputs and outputs piping the results together. At the other end are fully fledged workflow management systems (WMS) such as Nextflow \[[Tommaso et al. 2017](http://www.nature.com/nbt/journal/v35/n4/full/nbt.3820.html)\], Galaxy \[The Galaxy Community, 2024, [ref](https://doi.org/10.1093/nar/gkae410)\], Snakemake \[[Mölder et al. 2021](https://doi.org/10.12688/f1000research.29032.2)\], and Parsl \[Babuji et al. 2019, [ref](https://doi.org/10.1145/3307681.3325400)\]. Using a workflow system can provide a number of benefits including abstraction, scaling, automation, reproducibility [(Kanwal et al. 2017\)](https://paperpile.com/c/VnGRZH/ZwIy) and provenance \[da Silva et al. 2022, [Ref](https://doi.org/10.5281/zenodo.7750670)\]. A fully featured WMS typically facilitates error handling and restarting, automatic restarting and data staging, provenance recording, the handling of large datasets and complex computations, task and resource allocation, and distributed task execution to scale over local workstations, cloud resources, or high-performance computing clusters. WMSes and modular containerized (e.g. Docker, Singularity) software components aid portability and reproducibility. In practice, researchers use mixtures (e.g. chaining scripts from a WMS that in turn is launched from a notebook). 

Workflows are complex digital objects with intra- and inter-object relationships that connect the entire workflow, its definition, and its scope. To help clarify our FAIR discussion, we present some definitions ([Figure 1](#fig:concepts)).

**A workflow** is the formal specification of the data flow and execution control between executable components, and the expected datasets and parameter files. Its complexity can be composed, and its overall process can be abstracted away from its execution. **A workflow run** is the instantiation of the workflow with inputs (parameters files, input datasets) and outputs (output data, the provenance execution log and lineage of data products).

**A workflow component** can be an executable and data. Executables include scripts, code, tools, containers, or workflows themselves remotely or locally executed, and native or third party; an example data component could be a reference dataset. For a workflow specification, data include metadata (e.g., its description), graphical images, test and benchmark datasets, parameter defaults, and so on. For a workflow run, data extends to the actual input and output datasets, the parameter files, and the provenance record detailing the code run and data product lineage. 

**A workflow management system and execution platform** handles the data flow and/or execution control and performs the heavy lifting for computational and data handling.  A workflow management system abstracts the workflow from the underlying digital infrastructure, supporting scalability, portability, and differences in hardware architectures.

{{< figure src="figure1.png" link="figure1.png" id="fig:concepts" 
  width="100%" title="Overview of workflow concepts"
  caption="A **workflow specification** formally specifies the data flow and/or execution control between components such as reference datasets, executable scripts, and AI/ML models. These components can be reused as parts of other workflow specifications. Using a workflow specification means instantiating it as a **workflow run** – typically by executing it within a **workflow management system** – by feeding it inputs like parameters and experimental/observational data as required. During execution, components will be used in some order, finally resulting in output data as well as logs and provenance metadata." >}}


The use of workflows has accelerated in the past few years.  The existence of more than 350 different workflow management systems of varying maturity evidences the increasing popularity of workflows \[[Amstutz et al](https://github.com/common-workflow-language/common-workflow-language/wiki/Existing-Workflow-systems). 2024\]. Workflows automate repetitive and time-consuming tasks, saving time and computational resources and ensuring that computational experiments can be replicated. They provide a documented record of the computational process which helps in understanding, reviewing, and auditing the workflow. As scientific activity often includes the exploration of analysis variance, modifying workflows to understand effects and changes on data products is simpler when those workflows are clearly described and comparable. Researchers can reuse workflows to re-analyze and adapt to incorporate new methods, tools, or data sources. Sharing and reusing workflows supports team collaboration and standardizes processes and analysis methods.

The Findable, Accessible, Interoperable, and Reusable (FAIR) principles aim to maximize the value and impact of scientific digital objects. Such objects cannot be reused if they cannot be found, accessed, or understood; they cannot be combined if they are not interoperable. The FAIR guidelines for scientific data \[[Wilkinson et al 2016](https://www.nature.com/articles/sdata201618)\] emphasize making data findable through metadata provision, unique and persistent identifier assignment, ensuring accessibility through open access or controlled access mechanisms, promoting interoperability through standardized formats and metadata schemas, and enabling reusability through clear licensing and documentation. The FAIR principles for research software (FAIR4RS) \[[Barker et al 2022](https://doi.org/10.1038/s41597-022-01710-x)\] recommend making software findable through repositories and registries, ensuring accessibility through open licensing and documentation, promoting interoperability through standardization and compatibility with other tools, and enabling reusability through versioning and clear documentation of functionality and dependencies. These principles have made a significant impact on policy and publishing, and they have been taken up by the public and private sector as well as spawning an industry of projects, research programs, and commercial businesses.

### FAIR Principles applied to Computational Workflows

FAIR4RS defines research software as “source code files, algorithms, scripts, computational workflows, and executables that were created during the research process or for a research purpose”. Workflows are a specific kind of software where reuse and modification should be inherent in their modularized composition of code and sub-workflows with an explicitly defined control and data flow. Workflow composition can be organized along levels of granularity (e.g. functions, tasks, stages, pipelines), for example similar to libraries in a software stack. The execution of a series of computational code can be difficult to standardize and share across different research environments, and each has its own set of dependencies and requirements, which can complicate the process of ensuring comprehensive FAIRness \[[de Visser et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37768885/)\]. Automating scientific experiments using workflows helps mitigate this issue. A key characteristic is the separation of the workflow specification from its execution; the description of the process is a form of data-describing method \[[Goble et al 2020](https://doi.org/10.1162/dint_a_00033)\]. Workflows that are chiefly concerned with the processing and creation of data are typically designed to be tightly coupled with their data, including test data and the provenance lineage history of data products. Therefore, workflows have an important role to play in ensuring that the data products they use and produce are FAIR.

Building on earlier work \[Goble et al 2020, da Silva et al. 2022, de Visser et al., 2023, Niehues et al., 2024, Zulfiqar et al. 2024\], the WCI FAIR Computational Workflows Working Group (WCI-FW) set out to systematically apply the FAIR principles to computational workflows. WCI-FW is an open, diverse, and interdisciplinary collective of workflow system professionals and workflow users and authors who meet bi-weekly online. The group comprises experts from YY organizations from ZZ countries specialized in various fields, including bioinformatics, climate science, data science, earth science, software engineering, and workflow management. This diversity of backgrounds and expertise allowed us to approach the task from multiple perspectives, ensuring that the FAIR principles for computational workflows are both practical and widely accepted to enhance the reusability, reliability, and impact of computational workflows across diverse research domains.

Several pivotal questions that surfaced in the course of our group discussions were:  
– Do we need to tailor software principles to the specific characteristics of workflows? As workflows are executables the principles of software should apply. Nevertheless, the characteristics of the heterogeneous components that make up workflows and the expected user behavior of variant reuse, modification, and portability led us to some customization of the principles. Technical information is needed that details each step’s inputs, outputs, dependencies, and computational requirements as well as configuration files, lists of software dependencies, and other information about the operational context. Missing context is one of the main difficulties faced when porting across computing platforms; applying FAIR to workflows requires fully describing the context necessary for executing the workflows as software.  
– How far do the data principles apply to workflows as digital data objects? Workflows and their components are frequently represented as collections of files, just like other datasets, and these files are interpreted as different kinds of objects like source code, raw data, and AI models. FAIR workflows augment this idea by encouraging comprehensive workflow “datasets” to include detailed metadata and documentation to describe their structures, purposes, and technical requirements. We applied the FAIR principles for data to the collection of files that represent the workflow. For example, these files should include descriptive metadata such as title, authors, creation date, and version, as well as version histories when possible. Workflows need persistent identifiers just like other datasets do, and they need to be accessible as data that can be retrieved over open protocols. Workflows also need licenses that explain clearly the conditions under which others are permitted to use and modify parts or the whole.

Table 1 summarizes our results with further discussion below. 

| FAIR PRINCIPLES APPLIED TO COMPUTATIONAL WORKFLOWS | Based on |
| :---- | :---- |
| **FINDABILITY Workflow and its associated metadata are easy for both humans and machines to find.** |  |
| F1. A workflow is assigned a globally unique and persistent identifier.  | S F1 D F1 |
|     F1.1. Components of the workflow representing levels of granularity are assigned distinct identifiers. | S F1.1  |
|     F1.2. Different versions of the workflow are assigned distinct identifiers. | S F1.2 |
| F2. A workflow and its components are described with rich metadata. | S F2 D F2 |
| F3. Metadata clearly and explicitly include the identifier of the workflow, and workflow versions, that they describe. | S F3 D F3 |
| F4. Metadata and workflow are registered or indexed in a searchable FAIR resource.  | S F4 D F4 |
| **ACCESSIBILITY Workflow and its metadata are retrievable via standardized protocols.** |  |
| A1. Workflow and its components are retrievable by their identifiers using a standardized communications protocol. | S A1 D A1 |
|     A1.1. The protocol is open, free, and universally implementable. | S A1.1 D A1.1 |
|   A1.2. The protocol allows for an authentication and authorization procedure, when necessary. | S A1.2 D A1.2 |
| A2. Metadata are accessible, even when the workflow is no longer available. | S A2 D A2 |
| **INTEROPERABILITY Workflow interoperates with other workflows, and workflow components interoperate, by exchanging data and/or metadata, and/or through interaction via APIs, described by standards.** |  |
| I1. Workflow and its metadata (including workflow run provenance) use a formal, accessible, shared, transparent, and broadly applicable language for knowledge representation. | S R1.2 D I1 |
| I2. Metadata and workflow use vocabularies that follow FAIR principles. | D I2 |
| I3. Workflow is specified in a way that allows its components to read, write, and exchange data (including intermediate data), in a way that meets domain-relevant standards. | S I1 D R3 |
| I4. Workflow and its metadata (including workflow run provenance) include qualified references to other objects and the workflow's components. | S I2 S R1.2 D I3 |
| **REUSABILITY Workflow is both usable (can be executed) and reusable (can be understood, modified, built upon, or incorporated into other workflows).** |  |
| R1. Workflow is described with a plurality of accurate and relevant attributes. | S R1 D R1 |
|    R1.1. Workflow is released with a clear and accessible license. | S R1.1 D R1.1 |
|    R1.2. Components of the workflow representing levels of granularity are given clear and accessible licenses. | S R1.1 D R1.1 |
|    R1.3. Workflow is associated with detailed provenance of the workflow and of the products of the workflow | S R1.2 D R1.2 |
| R2. Workflow includes qualified references to other workflows. | S R2 D I3 |
| R3. Workflow meets domain-relevant community standards. | S R3 D R1.3 |

_**Table 1**: The FAIR Principles applied to Computational Workflows, with sources from the \[S\]oftware and \[D\]ata Principles._

– Given that FAIR is primarily about persistent identifiers and metadata, what should be identified for a workflow, and what is the necessary metadata? Workflows are composite objects, where the entire object (with a persistent identifier and metadata) as well as its components (also with persistent identifiers and metadata), all in turn need to be FAIR. Executable components can be independent of the workflow (call-outs to tools, for example), embedded (internal scripts), or workflows themselves (so that FAIR principles are applied recursively).  Data components may be interpreted as data and as metadata. Workflows provide mechanisms to execute in one run independent components that may be independently FAIR, but their aggregation into a workflow also needs to be FAIR.

### Findability

The data and software principles generally apply to workflows, but with novel/additional considerations on our interpretation of a component and a strengthening of metadata associated with workflow versions. Workflows are subject to continuous refinement and independent modification, often resulting in multiple versions, adaptations, and variants, with workflows extended, nested, and reused as sub-workflows. Researchers modify workflows for specific purposes, adjust components, and provide alternative methods across various platforms; components are copied, pasted, and modified.

Identifiers are important because unlike software, authors often neglect to  “name” their workflows (although they do name their workflow management systems). Identifiers establish a clear lineage of each workflow and component's origin and changes, enabling researchers to understand the workflow structure and evolution, compare iterations, relate workflows to each other, and confidently build upon previous work. Persistent identifiers identify and reference specific versions to ensure accurate identification and traceability and to support developer citation and source workflow attribution (F1). Unique identifiers to different versions of workflows recognize their dynamic nature in research (F1.2), Unique identifiers for a workflow’s components and versions (whether a file, computational step, or sub-workflow) support traceability and facilitate reuse, reproducibility and portability across different workflow versions (F1.1). 

Rich metadata for the overall workflows and their components (including inputs and outputs) (F2, F3) should use a formal, accessible language for knowledge representation, such as schema.org, and standardized metadata such as the Bioschemas schema.org profile for Computational Workflows \[Bioschemas, 2023, [Bioschemas \- 1.0 Release](https://bioschemas.org/types/ComputationalWorkflow/1.0-RELEASE)\] (used for workflow components in Workflow Run Crate profile \[Leo 2024\]) and CodeMeta \[Jones et al. 2023, [https://w3id.org/codemeta/v3.0](https://w3id.org/codemeta/v3.0) ref\]. Other metadata forms for workflows include canonical “Rosetta” languages (CWL \[Crusoe et al. 2022, https://doi.org/10.1145/3486897\], WDL \[Voss et al. 2017, DOI:10.7490/f1000research.1114634.1\]) that abstract from the native workflow language for greater portability and comparability. Such metadata are used for registration and search in dedicated and trusted workflow registries such as WorkflowHub  \[[Goble et al. 2021](https://about.workflowhub.eu/project/citation/)\] and Dockstore (F4) \[[Yuen et al. 2021](https://academic.oup.com/nar/article/49/W1/W624/6274534?login=false)\]. 

### Accessibility

The data and software principles generally apply but with new considerations on what it means for a workflow to be available. The workflow may be restricted to execution at one facility, which is a common case in highly optimized HPC settings, and access to that facility may be restricted (A1.2).  Single sign-on for workflow components requires harmonized Authentication and Authorization Infrastructure (AAI) propagation through the different tasks, if they are hosted by different service providers. “A2. Metadata are accessible, even when the workflow is no longer available” requires further interpretation given a workflow’s dual nature as process description (data) and process execution (software) and we must understand what “no longer available” means. As a piece of software, a workflow execution platform or the infrastructure that it operates on may become deprecated and/or unavailable. Dependency on the component code and services makes a workflow vulnerable to “software rot”, and it is not always possible to completely containerize and preserve all code, such as when they are remotely executed third party tools or call-outs to online datasets \[[Zhao et al. 2012](https://ieeexplore.ieee.org/document/6404482/citations#citations),  
[https://doi.org/10.1109/eScience.2012.6404482](https://doi.org/10.1109/eScience.2012.6404482)\].

As a process description, the workflow captures both the steps and data flow of a recipe for a method, which is a form of the “metadata”. Thus at least the workflow and its components descriptions, and if relevant the workflow run components, should be preserved and archived in a long-term registry or repository, so that if the workflow is no longer executable, it will still be readable. If we interpret a workflow description file as data, the data principles decree that at least the metadata for that file should still be retrievable. For a workflow, however, that data file is the essence of the workflow. We interpret the workflow description to be a form of metadata of the software and therefore, it must always be accessible. A workflow associated with a publication may still be examined as a method, and its provenance may be inspected; the description should be enough to be translated for another workflow system. Apart from manual or AI-assisted porting of code, this can also happen via “Rosetta” workflow languages like CWL and WDL (as e.g. done in MGnify \[[Richardson et al. 2023](https://academic.oup.com/nar/article/51/D1/D753/6880769), [https://doi.org/10.1093/nar/gkac1080](https://doi.org/10.1093/nar/gkac1080)\] and by Snakemake’s CWL export).

### Interoperability

The data and software principles are combined and blur with principles from Reusability, as we tease apart the FAIR requirements for a workflow, its components (both executable and data), and an instantiated and executed run of the workflow. For example, principle I1 applies to describing the static workflow structure of the specification and capturing dynamic aspects of the run such as execution details and intermediate outputs. The workflow specification plays a role in data in I1, I2, and I4 adapting data principles, as well as the role of metadata of the software, co-opting software principles.

We adapt software principles for I3 and I4 to explicitly refer to the domain standard description of input and outputs of the workflow executable components. As data components of a workflow, the expected input and output datasets, benchmarks and parameters, and the actual datasets and parameter files from a workflow run, should also adhere to community standards (data principle R1.3), as should intermediate data derived during the execution. The principles encourage workflow portability across different types of computational environments (e.g., via containerization or OS-agnostic package management) \[[de Visser et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37768885/)\] and, ideally, easy translation from one language/management system to another or at least compatibility and seamless integration (in case of sub-workflows). 

Standard language formats like CWL encourage interoperability and offer the potential for workflow comparisons and exchange between different languages, through documentation of components, inputs, and outputs. We explicitly add workflow run provenance to interoperability as documented execution steps and data lineage traces are important components that should also be interoperable and machine-actionable \[Nicolae et al., 2023\].

### Reusability

Reusability of the workflow as an executable method with modifications to its parameters and input files is an expected and anticipated use of the workflow, tied up in the quality of its documentation and the accessibility of computational infrastructure capable of executing it. 

In findability we also highlighted the reusability of workflows as complex compositions intended to be modified, built upon, and incorporated into other workflows, as well as their reusability as runnable executions with modified datasets and parameter files \[Lamprecht et al. 2021\]. The data and software principles are adapted to emphasize the composite nature of workflows (both executable and data components) for licensing \[[Cohen-Boulakia et al. , 2017](https://www.sciencedirect.com/science/article/abs/pii/S0167739X17300316?via%3Dihub)\]. Workflows are composed of many parts, potentially from different authors with different intents for how their artifacts may be used; these intents must be clearly stated by the inclusion of licenses that cover all parts of the workflow and sub-parts of the workflows that can be reused as sub-workflows \[[de Visser et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37768885/)\].

The provenance history of the workflow – its authors, purpose, workflows of which it may be a variant, links to other sub-workflows and so on, are included in R1.3 drawing from both data and software principles R1.2. The provenance of data products tracked by the workflow run provenance collection is related to the data principles R1.2 where data (in this case the products of the workflow) are associated with detailed provenance that a workflow system should be able to provide. A benefit of using fully fledged workflow systems is the capture of computer-interpretable provenance (meta)data to track the history and origin of data processing steps. R1 and R3 expect that input and output datasets are thoroughly described with example input and expected output data for each step that adhere to data structure and file format standards \[[de Visser et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37768885/)\] and gold standards for benchmarking \[[Cohen-Boulakia et al. , 2017](https://www.sciencedirect.com/science/article/abs/pii/S0167739X17300316?via%3Dihub)\].

**Example workflow specification**

The Protein MD Setup workflow sets up a protein molecular dynamic simulation that returns a protein structure and simulated 3D trajectories \[[Stian Soiland-Reyes et al. 2022](https://doi.org/10.1162/dint_a_00135)\]. It is registered in WorkflowHub, where it has been assigned a globally unique digital object identifier \[[https://doi.org/10.48546/workflowhub.workflow.29.3](https://doi.org/10.48546/workflowhub.workflow.29.3)\] (F1). Different versions of this workflow can be identified using unique digital object identifiers (F1.2). The workflow is described using (rich) metadata (F2) that includes the identifier of the workflow and its unique version (F3). The workflow and associated metadata are registered (F4). Moreover, components of the workflow have their own individual persistent identifiers as the workflow is composed of sub-workflow BioBB building blocks from the [BioBB Library](https://workflowhub.eu/projects/11) (F1.2). The workflow and its components can be retrieved and downloaded using a standardized HTTPS protocol (A1, A1.1, A1.2). The metadata associated with the workflow and its components is independent from the GitHub code repository and are accessible on WorkflowHub even if the workflow (or its components) become inaccessible (A2).  
   
The Protein MD Setup is written using CWL which follows a formal and declarative paradigm for workflow implementation (I1). The workflow does not include all the best-practice principles to fulfill I2 and I3. This extends to the workflow metadata, which does not use a domain-specific ontology. The workflow and its metadata include qualified references to other objects and components (I4). However, CWL standard itself allows metadata and workflow vocabularies (e.g. Bioschemas, EDAM \[[Ison et al. 2013](https://doi.org/10.1093/bioinformatics/btt113)\]) that are consistent with FAIR principles (I2), enables the components of the workflows to read, write, and exchange data using format that meets domain-specific standards (I3), and assigns qualified references to workflow components, inputs, and outputs. 

The workflow is released under Apache License 2.0 software license (R1.1) and  WorkflowHub’s RO-Crate references that the embedded CWL code is archived from the corresponding GitHub source code repository \[[https://github.com/bioexcel/biobb-wf-md-setup-protein-cwl](https://github.com/bioexcel/biobb-wf-md-setup-protein-cwl)\]. The component BioBB building blocks of the workflow have their own clear and accessible licenses (R1.2). The workflow is associated with detailed provenance about its development, provided as a downloadable RO-Crate object (R1.3).

**Example workflow run**

Here, we demonstrate the application of the FAIR principles to a workflow run, which in this case is a dataset that represents an execution of a tissue/tumor prediction workflow for digital pathology using RO-Crate \[[Leo et al. 2023](https://zenodo.org/records/7774351)\].

The workflow run has been assigned a globally unique digital object identifier (F1).  Components of the workflow run (e.g. steps, inputs, outputs) are assigned distinct identifiers (F1.1). The workflow run is described using (rich) metadata (F2) that includes the identifier of the workflow run and its unique version (F3). The workflow is not registered but publicly available via GitHub \[[https://github.com/crs4/deephealth-pipelines](https://github.com/crs4/deephealth-pipelines)\] and the workflow run is available on Zenodo (F4) with a DOI \[[10.5281/zenodo.7669622](https://zenodo.org/doi/10.5281/zenodo.7669622)\].

The workflow run and its components can be retrieved and downloaded using a standardized HTTPS protocol (A1, A1.1, A1.2). The metadata associated with the workflow run and its components is independent from the GitHub code repository and is accessible on Zenodo even if the workflow (or its components) becomes inaccessible (A2). 

The workflow run provenance of digital pathology tissue/tumor prediction is generated using CWLProv \[[Khan et al. 2019](https://academic.oup.com/gigascience/article/8/11/giz095/5611001)\]  in the form of RO-Bundle and then converted to an RO-Crate \[[Sefton, et al. 2023](https://doi.org/10.5281/zenodo.7867028)\] that follows [Provenance Run Crate profile](https://www.researchobject.org/workflow-run-crate/profiles/0.1/provenance_run_crate). All these methods represent run information utilizing well-established standards and language    (I1). CWLProv and RO-Crate allow vocabularies that are consistent with FAIR principles, (I2). The workflow run provenance is generated using CWLProv and documented as Provenance Run Crate profile showing the exchange of data between components of the workflow.  However, the workflow run does not include domain-specific standards for metadata to fulfill I3. The workflow run provenance includes qualified references to other objects and the workflow's components (I4). 

The workflow run is released under MIT License (R1.1) and the associated code is publicly available on GitHub. The component Slaid (a library for applying DL models from the DeepHealth project \[[https://deephealth-project.eu/](https://deephealth-project.eu/)\]  on WSI) of the workflow run is released under MIT License (R1.2). The workflow run contains detailed provenance about the execution, provided as a downloadable RO-Crate object (R1.3). The workflow processes digital pathology images in the formats supported by OpenSlide (R3), a widespread software library for digital pathology images ([https://doi.org/10.4103/2153-3539.119005](https://doi.org/10.4103/2153-3539.119005)).

**FAIRness Beyond the FAIR Principles**     
The FAIR principles in Table 1 focus on the workflows as scholarly research assets to be found, accessed, interoperated, and reused. They do not extend to the quality of the workflows (FAIR+Q) or the extent of the reproducibility of the workflows (FAIR+R), and they only hint at their portability and sustainability. The Open Data, Open Code, Open Infrastructure (O3) guidelines complement FAIR by providing an actionable road map toward sustainability \[[Hoyt et al. 2024\]](https://pubmed.ncbi.nlm.nih.gov/38811583/). Note, however, that FAIR does not require openness; authors and companies may even choose not to publish their workflows or metadata at all, but still use “inner FAIR” principles (Crusoe 2018\) for their own benefits.

Workflows are composites of executable components that need to be validated and tested with clean interfaces, permissive access permissions if remotely executed, and compatible licenses. Work on canonical workflow libraries \[[Turilli et al. 2019](https://ieeexplore.ieee.org/document/8726147)\] and building blocks that are interoperable between languages \[[Stian Soiland-Reyes et al. 2022](https://doi.org/10.1162/dint_a_00135)\], workflow readiness of tools \[[Brack et al. 2022](https://pubmed.ncbi.nlm.nih.gov/35324885/)\], FAIR unit testing \[e.g., pytest-workflow for WDL [https://github.com/LUMC/pytest-workflow](https://github.com/LUMC/pytest-workflow)\], test monitoring \[e.g. LifeMonitor, [https://crs4.github.io/life\_monitor/](https://crs4.github.io/life_monitor/)\], and benchmarking \[e.g. OpenEBench, [https://openebench.bsc.es/](https://openebench.bsc.es/)\] are steps towards creating FAIR workflow professional practices that should include peer review, curation, and perhaps even certification.

We should also consider the relationship of FAIR to other services in a workflow’s service ecosystem. Container technologies such as Docker and Singularity play a role in the interoperability, reusability, and reproducibility of computational workflows by providing lightweight, portable, and self-contained environments that include all of the software dependencies and libraries required to run a workflow. In alignment with the FAIR principles, containers can be versioned and shared through registries like Docker Hub, Nexus Repository, or Github Container registry. FAIR workflows should be stored in version-controlled repositories like GitHub and GitLab and indexed by registries like Dockstore \[[Yuen et al. 2021](https://academic.oup.com/nar/article/49/W1/W624/6274534?login=false)\] and WorkflowHub \[[Goble et al. 2021](https://about.workflowhub.eu/project/citation/)\]. Workflow registries like Dockstore and WorkflowHub support findability and accessibility so workflows can be shared, published, and reused as well as downloaded or launched using dedicated infrastructure facilities such as Galaxy Europe. Both support example input and test data components for a workflow specification but do not retain the result components of a workflow run – the provenance and links to datasets that are the resulting products. That is expected to be managed by data repositories like Zenodo and Figshare that in turn need to support FAIR data principles. However, this container approach most probably shows practical limitations when applied to workflows executed on very large-scale, meticulously maintained and pampered HPC environments running on the verge of computational and technical stability. For such cases, reproducibility of workflows might always be an issue. 

Workflows are multi-part objects whose data components are as important as their executable steps; all these digital objects should be FAIR too. Community efforts like RO-Crate \[Soiland-Reyes et al. 2022, [https://www.researchobject.org/ro-crate/](https://www.researchobject.org/ro-crate/)\] propose the means to encapsulate workflows and all their components while capturing the context in which they are used (e.g., executions, bibliography, sketches, etc.). An RO-Crate Workflow profile \[[https://about.workflowhub.eu/Workflow-RO-Crate/](https://about.workflowhub.eu/Workflow-RO-Crate/)\] includes references to components which also need to be FAIR. By having workflows as composition of FAIR research outputs, the FAIRness of each contained resource is validated, since the execution of the workflow relies on these resources being available. Services like WorkflowHub (registry), LifeMonitor (test monitoring), and Galaxy (workflow platform) implement RO-Crate for comprehensive workflow representation and exchange as well as a step to sharing metadata and persistent identifiers to implement the FAIR principles of Table 1\.

As workflows typically operate on and produce datasets, they are well placed to make those data products FAIR; they provide the process description and automated data provenance collection, and fully fledged WMS can automate processes for generating FAIR data. Nevertheless, workflows have to be well designed to be “FAIR aware”: producing and consuming data in standardized formats, assigning license, handling identifiers, and metadata production, data versioning, etc \[Goble et al, 2020\]. Using workflows as automated instruments for “FAIR data by design” can encourage inputs and make outputs to be machine-actionable and more suitable for use in other workflows, for example those that span geographically distinct computing facilities \[Antypas2021-ph\].

## Conclusion

Computational workflows are key instruments for the advancement in scientific research, potentially revolutionizing how data is managed, analyzed, and shared. Workflows not only serve as software that can be used by experts and non-coders alike; they also serve as documentation of scientific processes, encapsulating not only the data and software used but also the context and conditions under which discoveries were made. It is expected that this comprehensive documentation will not only enhance the credibility of research findings but will also facilitate the replication and validation of scientific results across diverse settings and by different research teams.

FAIR data and FAIR software principles both apply to workflows, combining structured, well-described data with portable, well-documented software creating a powerful framework for advancing scientific knowledge. Moreover, the next generation of workflows – assisted auto-assembly, generative workflows, dynamic reconfiguration, and so on – will require rich, machine-actionable metadata.

FAIR application requires interpretation, however, to consider the abstraction and the compositional properties of workflows. The usual challenges for FAIR implementation are still present: incentives, resources, assessment, support services, and so on. Even when opportunities arise for metadata enrichment when registering workflows in WorkflowHub, for example, the best curators do not manage all the principles, and most take the simplest route. FAIR workflow implementation will “take a village” of services, including data services and support from workflow management systems, and well-designed workflows that are FAIR data-aware will require golden standard examples, training, and professionalization.



## Author Contributions

SW and CG are the primary authors of the manuscript. All other authors are listed alphabetically and contributed to the manuscript by participating in the WCI-FW meetings and/or by editing or commenting on the manuscript text.




## Acknowledgements

<small>

This research used resources of: the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. Department of Energy under Contract No. DE-AC05-00OR22725 (SW); Sandia National Laboratories, a multi-mission laboratory managed and operated by National Technology & Engineering Solutions of Sandia, LLC (NTESS), a wholly owned subsidiary of Honeywell International Inc., for the U.S. Department of Energy’s National Nuclear Security Administration (DOE/NNSA) under contract DE-NA0003525; the European Union programme Horizon Europe under grant agreements HORIZON-INFRA-2021-EOSC-01 101057388 (EuroScienceGateway),  HORIZON-INFRA-2023-EOSC-01-02 101129744 (EVERSE; SS), HORIZON-INFRA-2021-EMERGENCY-01 101046203 (BY-COVID), HORIZON-INFRA-2021-EOSC-01-05 101057344 and by UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee grants 10038963 (EuroScienceGateway; CG, S-SR), 10038992 (FAIR-IMPACT; NJ). This work received support from the National Research Agency under the France 2030 program, with reference to ANR-22-PESN0007. This work is supported by Australian BioCommons, which is enabled by NCRIS via Bioplatforms Australia funding (JG); Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) as part of GHGA – The German Human Genome-Phenome Archive (www.ghga.de, Grant Number 441914366 (NFDI 1/1)). We acknowledge the contribution of the Italian National Research Center in High Performance Computing, Big Data and Quantum Computing (MUR PNRR M4C2 \- Investimento 1.4 \- Avviso Centri Nazionali).


</small>

## References


de Visser C, Johansson LF, Kulkarni P, Mei H, Neerincx P, Joeri van der Velde K, et al. (2023) Ten quick tips for building FAIR workflows. *PLoS Comput Biol* 19(9): e1011369. [https://doi.org/10.1371/journal.pcbi.1011369](https://doi.org/10.1371/journal.pcbi.1011369)

Niehues, A., de Visser, C., Hagenbeek, F. A., Kulkarni, P., Pool, R., Karu, N., Kindt, A. S. D., Singh, G., Vermeiren, R. R. J. M., Boomsma, D. I., van Dongen, J., ’t Hoen, P. A. C., & van Gool, A. J. (2024). A multi-omics data analysis workflow packaged as a FAIR Digital Object. GigaScience, 13, giad115. [https://doi.org/10.1093/gigascience/giad115](https://doi.org/10.1093/gigascience/giad115)

S. R. Wilkinson *et al*., "F\*\*\* workflows: when parts of FAIR are missing," *2022 IEEE 18th International Conference on e-Science (e-Science)*, Salt Lake City, UT, USA, 2022, pp. 507-512, doi: 10.1109/eScience55777.2022.00090.

<!--

Richardson RA, Celebi R, van der Burg S, Djura Smits, Ridder L, Dumontier M, Kuhn T (2021). User-friendly Composition of FAIR Workflows in a Notebook Environment*. In Proc 11th Knowledge Capture Conference (K-CAP ’21), December 2–3, 2021*, Virtual Event, USA. https://doi.org/10.1145/3460210.3493546

Soiland-Reyes S, Bayarri G, Andrio P, Long R, Lowe D, Niewielska An, Hospital A, Groth G; Making Canonical Workflow Building Blocks Interoperable across Workflow Languages. Data Intelligence 2022; 4 (2): 342–357. doi: [https://doi.org/10.1162/dint\_a\_00135](https://doi.org/10.1162/dint_a_00135)
-->

Bayarri G, Andrio P, Gelpí JL, Hospital A, Orozco M (2024) Using interactive Jupyter Notebooks and BioConda for FAIR and reproducible biomolecular simulation workflows. *PLoS Comput Biol* 20(6): e1012173. [https://doi.org/10.1371/journal.pcbi.1012173](https://doi.org/10.1371/journal.pcbi.1012173)

Jones MB, Boettiger C, Cabunoc Mayes A, Smith A, Gruenpeter M et al (2023) CodeMeta: an exchange schema for software metadata. Version 3.0. [https://w3id.org/codemeta/v3.0](https://w3id.org/codemeta/v3.0)

Denis Yuen, Louise Cabansay, Andrew Duncan, Gary Luu, Gregory Hogue, Charles Overbeck, Natalie Perez, Walt Shands, David Steinberg, Chaz Reid, Nneka Olunwa, Richard Hansen, Elizabeth Sheets, Ash O’Farrell, Kim Cullion, Brian D O’Connor, Benedict Paten, Lincoln Stein, The Dockstore: enhancing a community platform for sharing reproducible and accessible computational protocols, *Nucleic Acids Research*, Volume 49, Issue W1, 2 July 2021, Pages W624–W632, [https://doi.org/10.1093/nar/gkab346](https://doi.org/10.1093/nar/gkab346)

Peter Amstutz, Maxim Mikheev, Michael R. Crusoe, Nebojša Tijanić, Samuel Lampa, et al. (2024): **Existing Workflow systems.** *Common Workflow Language wiki*, GitHub. [https://s.apache.org/existing-workflow-systems](https://s.apache.org/existing-workflow-systems) updated 2024-01-25, accessed 2024-01-25.

Carole Goble, Sarah Cohen-Boulakia, Stian Soiland-Reyes, Daniel Garijo, Yolanda Gil, Michael R. Crusoe, Kristian Peters, Daniel Schober; FAIR Computational Workflows. *Data Intelligence* 2020; 2 (1-2): 108–121. doi: [https://doi.org/10.1162/dint\_a\_00033](https://doi.org/10.1162/dint_a_00033)

Mahnoor Zulfiqar, Michael R. Crusoe, Birgitta König-Ries, Christoph Steinbeck,Kristian Peters Luiz Gadelha (2024): **Implementation of FAIR Practices in Computational Metabolomics Workflows**—A Case Study. *Metabolites* **14**(2) [https://doi.org/10.3390/metabo14020118](https://doi.org/10.3390/metabo14020118)

Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian Soiland-Reyes, Bogdan Gavrilović, Carole Goble, and The CWL Community. 2022\. Methods included: standardizing computational reuse and portability with the Common Workflow Language. Commun. ACM 65, 6 (June 2022), 54–63. https://doi.org/10.1145/3486897

Brack P, Crowther P, Soiland-Reyes S, Owen S, Lowe D, Williams AR, et al. (2022) Ten simple rules for making a software tool workflow-ready. PLoS Comput Biol 18(3): e1009823. [https://doi.org/10.1371/journal.pcbi.1009823](https://doi.org/10.1371/journal.pcbi.1009823)

Farah Zaib Khan, Stian Soiland-Reyes, Richard O Sinnott, Andrew Lonie, Carole Goble, Michael R Crusoe, Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv, *GigaScience*, Volume 8, Issue 11, November 2019, giz095, [https://doi.org/10.1093/gigascience/giz095](https://doi.org/10.1093/gigascience/giz095)

The Galaxy Community. [The Galaxy platform for accessible, reproducible, and collaborative data analyses: 2024 update](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkae410/7676834), *Nucleic Acids Research*, 2024;, gkae410, [https://doi.org/10.1093/nar/gkae410](https://doi.org/10.1093/nar/gkae410)

Yadu Babuji, Anna Woodard, Zhuozhao Li, Daniel S. Katz, Ben Clifford, Rohan Kumar, Lukasz Lacinski, Ryan Chard, Justin M. Wozniak, Ian Foster, Michael Wilde, and Kyle Chard. 2019\. Parsl: Pervasive Parallel Programming in Python. In Proceedings of the 28th International Symposium on High-Performance Parallel and Distributed Computing (HPDC '19). Association for Computing Machinery, New York, NY, USA, 25–36. [https://doi.org/10.1145/3307681.3325400](https://doi.org/10.1145/3307681.3325400)

Rafael Ferreira da Silva, Rosa M. Badia, Venkat Bala, Debbie Bard, Peer-Timo Bremer, Ian Buckley, Silvina Caino-Lores, Kyle Chard, Carole Goble, Shantenu Jha, Daniel S. Katz, Daniel Laney, Manish Parashar, Frederic Suter, Nick Tyler, Thomas Uram, Ilkay Altintas, Stefan Andersson, William Arndt, … Mahnoor Zulfiqar. (2023). Workflows Community Summit 2022: A Roadmap Revolution. Zenodo. [https://doi.org/10.5281/zenodo.7750670](https://doi.org/10.5281/zenodo.7750670)

Peter Amstutz, Maxim Mikheev, Michael R. Crusoe, Nebojša Tijanić, Samuel Lampa, et al. (2024): Existing Workflow systems. *Common Workflow Language wiki*, GitHub.  
[https://s.apache.org/existing-workflow-systems](https://s.apache.org/existing-workflow-systems) updated 2024-08-18, accessed 2024-08-18.

Zulfiqar M, Crusoe MR, König-Ries B, Steinbeck C, Peters K, Gadelha L. Implementation of FAIR Practices in Computational Metabolomics Workflows—A Case Study. *Metabolites*. 2024; 14(2):118. [https://doi.org/10.3390/metabo14020118](https://doi.org/10.3390/metabo14020118)

Bioschemas. Computational Workflow. 2023\. [https://bioschemas.org/types/ComputationalWorkflow/](https://bioschemas.org/types/ComputationalWorkflow/)

Matthew B. Jones, Carl Boettiger, Abby Cabunoc Mayes, Arfon Smith, Morane Gruenpeter, Valentin Lorentz, Thomas Morrell, Daniel Garijo, Peter Slaughter, Kyle Niemeyer, Yolanda Gil, Martin Fenner, Krzysztof Nowak, Mark Hahne:/Boettl, Luke Coy, Alice Allen, Mercè Crosas, Ashley Sands, Neil Chue Hong, Patricia Cruse, Daniel S. Katz, Carole Goble, Bryce Mecum, Alejandra Gonzalez-Beltran, Noam Ross. 2023\. CodeMeta: an exchange schema for software metadata. Version 3.0. [https://w3id.org/codemeta/v3.0](https://w3id.org/codemeta/v3.0)

Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian Soiland-Reyes, Bogdan Gavrilović, Carole Goble, and The CWL Community. 2022\. Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language. Commun. ACM 65, 6 (June 2022), 54–63. [https://doi.org/10.1145/3486897](https://doi.org/10.1145/3486897)

Voss K, Van der Auwera G and Gentry J. Full-stack genomics pipelining with GATK4 \+ WDL \+ Cromwell \[version 1; not peer reviewed\]. F1000Research 2017, 6(ISCB Comm J):1381 (slides) DOI:10.7490/f1000research.1114634.1

Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, José Mª Fernández, Salvador Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano, Philip Ewels, Frederik Coppens (2021): Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory.  
Zenodo [https://doi.org/10.5281/zenodo.4605654](https://doi.org/10.5281/zenodo.4605654)

Denis Yuen, Louise Cabansay, Andrew Duncan, Gary Luu, Gregory Hogue, Charles Overbeck, Natalie Perez, Walt Shands, David Steinberg, Chaz Reid, Nneka Olunwa, Richard Hansen, Elizabeth Sheets, Ash O’Farrell, Kim Cullion, Brian D O’Connor, Benedict Paten, Lincoln Stein, The Dockstore: enhancing a community platform for sharing reproducible and accessible computational protocols, Nucleic Acids Research, Volume 49, Issue W1, 2 July 2021, Pages W624–W632, [https://doi.org/10.1093/nar/gkab346](https://doi.org/10.1093/nar/gkab346)

Hoyt CT, Gyori BM. The O3 guidelines: open data, open code, and open infrastructure for sustainable curated scientific resources. Sci Data. 2024 May 29;11(1):547. doi: 10.1038/s41597-024-03406-w. PMID: 38811583; PMCID: PMC11136952.

J. Zhao et al., "Why workflows break — Understanding and combating decay in Taverna workflows," 2012 IEEE 8th International Conference on E-Science, Chicago, IL, USA, 2012, pp. 1-9, doi: 10.1109/eScience.2012.6404482. keywords: {Web services;Maintenance engineering;Data models;OWL;Databases;Biological system modeling},

Lorna Richardson, Ben Allen, Germana Baldi, Martin Beracochea, Maxwell L Bileschi, Tony Burdett, Josephine Burgin, Juan Caballero-Pérez, Guy Cochrane, Lucy J Colwell, Tom Curtis, Alejandra Escobar-Zepeda, Tatiana A Gurbich, Varsha Kale, Anton Korobeynikov, Shriya Raj, Alexander B Rogers, Ekaterina Sakharova, Santiago Sanchez, Darren J Wilkinson, Robert D Finn, MGnify: the microbiome sequence data analysis resource in 2023, Nucleic Acids Research, Volume 51, Issue D1, 6 January 2023, Pages D753–D759, [https://doi.org/10.1093/nar/gkac1080](https://doi.org/10.1093/nar/gkac1080)

Sarah Cohen-Boulakia, Khalid Belhajjame, Olivier Collin, Jérôme Chopard, Christine Froidevaux, Alban Gaignard, Konrad Hinsen, Pierre Larmande, Yvan Le Bras, Frédéric Lemoine, Fabien Mareuil, Hervé Ménager, Christophe Pradal, Christophe Blanchet,  
Scientific workflows for computational reproducibility in the life sciences: Status, challenges and opportunities, Future Generation Computer Systems, Volume 75, 2017, Pages 284-298, ISSN 0167-739X, [https://doi.org/10.1016/j.future.2017.01.012](https://doi.org/10.1016/j.future.2017.01.012)

Lamprecht AL, Palmblad M, Ison J et al. Perspectives on automated composition of workflows in the life sciences \[version 1; peer review: 2 approved\]. F1000Research 2021, 10:897, [https://doi.org/10.12688/f1000research.54159.1](https://doi.org/10.12688/f1000research.54159.1)

Stian Soiland-Reyes, Genís Bayarri, Pau Andrio, Robin Long, Douglas Lowe, Ania Niewielska, Adam Hospital, Paul Groth; Making Canonical Workflow Building Blocks Interoperable across Workflow Languages. Data Intelligence 2022; 4 (2): 342–357. doi: [https://doi.org/10.1162/dint\_a\_00135](https://doi.org/10.1162/dint_a_00135)

Simone Leo. (2023). Run of digital pathology tissue/tumor prediction workflow \[Data set\]. Zenodo. [https://doi.org/10.5281/zenodo.7774351](https://doi.org/10.5281/zenodo.7774351)

Farah Zaib Khan, Stian Soiland-Reyes, Richard O Sinnott, Andrew Lonie, Carole Goble, Michael R Crusoe, Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv, GigaScience, Volume 8, Issue 11, November 2019, giz095, [https://doi.org/10.1093/gigascience/giz095](https://doi.org/10.1093/gigascience/giz095)

Sefton, P., Ó Carragáin, E., Soiland-Reyes, S., Corcho, O., Garijo, D., Palma, R., Coppens, F., Goble, C., Fernández, J. M., Chard, K., Gomez-Perez, J. M., Crusoe, M. R., Eguinoa, I., Juty, N., Holmes, K., Clark, J. A., Capella-Gutierrez, S., Gray, A. J. G., Owen, S., … Radifar, M. (2023). RO-Crate Metadata Specification 1.1.3 (1.1.3). Zenodo. [https://doi.org/10.5281/zenodo.7867028](https://doi.org/10.5281/zenodo.7867028)

M. Turilli, V. Balasubramanian, A. Merzky, I. Paraskevakos and S. Jha, "Middleware Building Blocks for Workflow Systems," in *Computing in Science & Engineering*, vol. 21, no. 4, pp. 62-75, 1 July-Aug. 2019, doi: [10.1109/MCSE.2019.2920048](https://doi.org/10.1109/MCSE.2019.2920048)

Brack P, Crowther P, Soiland-Reyes S, Owen S, Lowe D, Williams AR, Groom Q, Dillen M, Coppens F, Grüning B, Eguinoa I, Ewels P, Goble C. Ten simple rules for making a software tool workflow-ready. PLoS Comput Biol. 2022 Mar 24;18(3):e1009823. doi: 10.1371/journal.pcbi.1009823. PMID: 35324885; PMCID: PMC8946750.

Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022): Packaging research artefacts with RO-Crate.  
*Data Science* **5**(2) [https://doi.org/10.3233/DS-210053](https://doi.org/10.3233/DS-210053)

Ahmed Z, Zeeshan S, Dandekar T. Developing sustainable software solutions for bioinformatics by the " Butterfly" paradigm. F1000Res. 2014 Mar 13;3:71. doi: 10.12688/f1000research.3681.2. PMID: 25383181; PMCID: PMC4215756.

Michael R. Crusoe (2018): From a chat with @soilandreyes, the idea of "Inner FAIR", in the spirit of "inner source".  *Twitter* (2018-03-22, archived 2022-12-24) [https://web.archive.org/web/20221224155747/https://twitter.com/biocrusoe/status/976827491460493312](https://web.archive.org/web/20221224155747/https://twitter.com/biocrusoe/status/976827491460493312) 

Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2024):  
[**Recording provenance of workflow runs with RO-Crate**](https://esciencelab.org.uk/publications/[https://arxiv.org/pdf/2312.07852.pdf]\(https://doi.org/10.1371/journal.pone.0309210\)).  
*PLOS One* **19**(9):e0309210  
[https://doi.org/10.1371/journal.pone.0309210](https://doi.org/10.1371/journal.pone.0309210)

Nicolae B, Islam TZ, Ross R, Pouchard LC, et al (2023) Building the I (Interoperability) of FAIR for Performance Reproducibility of Large-Scale Composable Workflows in RECUP. 2023 IEEE 19th International Conference on e-Science (e-Science). [https://doi.org/10.1109/e-science58273.2023.10254808](https://doi.org/10.1109/e-science58273.2023.10254808) 

Florian Schintke, Khalid Belhajjame, Ninon De Mecquenem, David Frantz, Vanessa Emanuela Guarino, Marcus Hilbrich, Fabian Lehmann, Paolo Missier, Rebecca Sattler, Jan Arne Sparka, Daniel T. Speckhard, Hermann Stolte, Anh Duc Vu, Ulf Leser: "Validity constraints for data analysis workflows." Future Generation Computer Systems, 157: 82-97 (2024).

Jon Ison, Matúš Kalaš, Inge Jonassen, Dan Bolser, Mahmut Uludag, Hamish McWilliam, James Malone, Rodrigo Lopez, Steve Pettifer, Peter Rice, EDAM: an ontology of bioinformatics operations, types of data and identifiers, topics and formats, Bioinformatics, Volume 29, Issue 10, May 2013, Pages 1325–1332, [https://doi.org/10.1093/bioinformatics/btt113](https://doi.org/10.1093/bioinformatics/btt113)

