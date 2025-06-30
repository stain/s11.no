# Computational workflows and why FAIR matters

Scale-ups in research data and the rise of data-driven science have spurred the research community to find solutions for managing and automating complex computational processes in order to ensure efficiency, reproducibility, scalability, collaboration, and quality-assured transparency. Computational workflows are a special kind of software specifically targeted at handling multi-step, multi-code data pipelines, data analyses, and other data-handling operations, especially through the efficient use of computational resources to transform data inputs into desired outputs.

Computational workflows are software with two prominent characteristics: (i) the composition (component number, order, structure) of **multiple components** that include other software, workflows, code snippets, tools, and services; and (ii) the **explicit abstraction** from the run mechanics in some form of **high-level workflow language** that precisely specifies the flow of data between the components, relying on a dedicated management system concerned with data handling and code execution. Metadata details the dependencies and computational requirements, including those of the computational environment \[1\].

At the simplest end of the complexity spectrum, the workflow language might consist of a script (e.g. Bash, Python, R) or enumerated stages in an electronic research notebook (e.g. Jupyter, RStudio, Apache Zeppelin, etc.) with a set of instructions that use inputs and outputs to pipe the results together. At the other end, workflows might employ a workflow management system (WMS) such as Nextflow [[Di Tommaso 2017]], Galaxy [[Galaxy 2024]], Snakemake [[Mölder 2021]], or Parsl [[Babuji 2019]]. Using a WMS can provide a number of benefits including abstraction, scaling, automation, reproducibility [[Kanwal 2017]], and provenance [[da Silva 2023]]. 

A fully featured WMS typically facilitates error handling and restarting, automatic data staging, provenance recording, handling of large datasets and complex computations, task and resource allocation, and distributed task execution to scale over local workstations, cloud resources, or high-performance computing clusters. WMSes and modular containerized software components (e.g. Docker, Singularity) aid portability and reproducibility, but they also face challenges (e.g., security issues when deployed in clusters, steep l earning curve, etc.). In practice, researchers use mixtures of techniques from across the spectrum, such as chaining scripts from a WMS that in turn is launched from a notebook.

Workflows are complex digital objects with intra- and inter-object relationships that connect the entire workflow, its definition, and its scope. To help clarify our FAIR discussion, we present some definitions along with an illustration in Figure [1](#fig:1).

A **workflow** is the formal specification of the data flow and execution control between executable components, the expected datasets, and parameter files. Its complexity can be composed, and its overall process can be abstracted away from its execution. A **workflow run** is the instantiation of the workflow with inputs (parameters files, input datasets) and outputs (output data, the provenance execution log and lineage of data products).

A **workflow component** can be an executable and data. Executables include scripts, code, tools, containers, or workflows themselves remotely or locally executed, and native or third party; an example data component could be a reference dataset. For a workflow specification, data include metadata (e.g., its description), graphical images, test and benchmark datasets, parameter defaults, and so on. For a workflow run, data extends to the actual input and output datasets, the parameter files, and the provenance record detailing the code run and data product lineage.

A **workflow management system** handles the data flow and/or execution control and performs the heavy lifting for computational and data handling. A workflow management system abstracts the workflow from the underlying digital infrastructure, supporting scalability, portability, and differences in hardware architectures.

![A **workflow specification** formally specifies the data flow and/or execution control between **components** such as reference datasets, executable scripts, and AI/ML models. These components can be reused as parts of other workflow specifications. Using a workflow specification means instantiating it as a **workflow run** – typically by executing it within a **workflow management system** – by feeding it inputs like parameters and experimental/observational data as required. During execution, components will be used in some order, finally resulting in output data as well as logs and provenance metadata.](figure1.png)

--- MERGED ABOVE

The use of workflows has accelerated in the past few years. The existence of more than 350 different workflow management systems of varying maturity evidences the increasing popularity of workflows (<https://s.apache.org/existing-workflow-systems>). Workflows help reduce the burden of manual human effort by automating repetitive and time-consuming tasks. This automation enables efficiency in terms of resource allocation both by allowing humans to return to human-only tasks and by allowing the computational tasks to take advantage of opportunities for automatic optimizations. Workflows also automate critical processes that require standardization and increased reproducibility, improving efficiency by removing humans from the analytical process, at times dispensing with the need for manual management of data flow through a set of processing steps, and reducing the need for repeat analyses due to human error and/or bias. Moreover, automation ensures that computational experiments can be replicated. Workflows also provide a documented record of the computational processes, which helps in understanding, reviewing, and auditing those processes. As scientific activity often includes the exploration of analysis variance, modifying workflows to understand effects and changes on data products is simpler when those workflows are clearly described and comparable. Researchers can reuse workflows to re-analyze and adapt to incorporate new methods, tools, or data sources. Sharing and reusing workflows supports team collaboration and standardizes processes and analysis methods \[8\].

The Findable, Accessible, Interoperable, and Reusable (FAIR) principles aim to maximize the value and impact of scientific digital objects. Such objects cannot be reused if they cannot be found, accessed, or understood; they cannot be combined if they are not interoperable. The FAIR guidelines for scientific data \[9\] emphasize making data findable through metadata provision, unique and persistent identifier assignment, ensuring accessibility through open access or controlled access mechanisms, promoting interoperability through standardized formats and metadata schemas, and enabling reusability through clear licensing and documentation. The FAIR principles for research software (FAIR4RS) \[10\] recommend making software findable through repositories and registries, ensuring accessibility through open licensing and documentation, promoting interoperability through standardization and compatibility with other tools, and enabling reusability through versioning and clear documentation of functionality and dependencies. These principles have made a significant impact on policy and publishing, and they have been taken up by the public and private sector as well as spawning an industry of projects, research programs, and commercial businesses \[11–12\].

# FAIR Principles applied to computational workflows

FAIR4RS defines research software as “source code files, algorithms, scripts, computational workflows, and executables that were created during the research process or for a research purpose”. Workflows are a specific kind of software where reuse and modification should be inherent in their modularized composition of code and sub-workflows with an explicitly defined control and data flow. Workflow composition can be organized along levels of granularity (e.g. functions, tasks, stages, pipelines), for example similar to libraries in a software stack. The execution of a series of computational code can be difficult to standardize and share across different research environments, and each has its own set of dependencies and requirements, which can complicate the process of ensuring comprehensive FAIRness \[13\]. Automating scientific experiments using workflows helps mitigate this issue. A key characteristic is the separation of the workflow specification from its execution; the description of the process is a form of data-describing method \[14\]. Workflows that are chiefly concerned with the processing and creation of data are typically designed to be tightly coupled with their data, including test data and the provenance lineage history of data products. Therefore, workflows have an important role to play in ensuring that the data products they use and produce are FAIR.

Building on earlier work \[13–18\], the WCI FAIR Computational Workflows Working Group (WCI-FW) set out to systematically apply the FAIR principles to computational workflows. WCI-FW is an open, diverse, and interdisciplinary collective of workflow system professionals and workflow users and authors who meet bi-weekly online. The group comprises experts from 40 organizations from 13 countries specialized in various fields, including bioinformatics, climate science, data science, earth science, software engineering, and workflow management. This diversity of backgrounds and expertise allowed us to approach the task from multiple perspectives, ensuring that the FAIR principles for computational workflows are both practical and widely accepted to enhance the reusability, reliability, and impact of computational workflows across diverse research domains.

The WCI-FW debated for many months whether to define a new, tailored set of principles for computational workflows or to apply the established principles for data and software. We concluded that we would directly apply the principles for FAIR data and software after recognizing that (a) we were naturally developing variations of these established principles because (b) workflows are a hybrid form of software, closely bound to data and even possessing data-like properties \[14\]. By building on the established FAIR framework, we have maintained consistency and enabled practices for workflows to integrate seamlessly with existing practices for data and software.

Several pivotal questions surfaced in the course of our group discussions:

  - Do we need to tailor software principles to the specific characteristics of workflows? As workflows are executables, the principles of software should apply. Nevertheless, the characteristics of the heterogeneous components that make up workflows and the expected user behavior of variant reuse, modification, and portability led us to some customization of the principles. Technical information is needed that details each step’s inputs, outputs, dependencies, and computational requirements as well as configuration files, lists of software dependencies, and other information about the operational context. Missing context is one of the main difficulties faced when porting across computing platforms; applying FAIR to workflows requires fully describing the context necessary for executing the workflows as software.

  - How far do the data principles apply to workflows as digital data objects? Workflows and their components are frequently represented as collections of files, just like other datasets, and these files are interpreted as different kinds of objects like source code, raw data, and AI models. FAIR workflows augment this idea by encouraging comprehensive workflow “datasets” to include detailed metadata and documentation to describe their structures, purposes, and technical requirements. We applied the FAIR principles for data to the collection of files that represent the workflow. For example, these files should include descriptive metadata such as title, authors, creation date, and version, as well as version histories when possible. Workflows need persistent identifiers just like other datasets do, and they need to be accessible as data that can be retrieved over open protocols. Workflows also need licenses that explain clearly the conditions under which others are permitted to use and modify parts or the whole.

  - Given that FAIR is primarily about persistent identifiers and metadata, what should be identified for a workflow, and what is the necessary metadata? Workflows are composite objects, where the entire object (with a persistent identifier and metadata) as well as its components (also with persistent identifiers and metadata), all in turn need to be FAIR. Executable components can be independent of the workflow (call-outs to tools, for example), embedded (internal scripts), or workflows themselves (so that FAIR principles are applied recursively). Data components may be interpreted as data and as metadata. Workflows provide mechanisms to execute in one run independent components that may be independently FAIR, but their aggregation into a workflow also needs to be FAIR.

Table [1](#tab:1) summarizes our results with further discussion below. In a nutshell, **Findability** means that a workflow and its associated metadata are easy for both humans and machines to find. **Accessibility** means that a workflow and its metadata are retrievable via standardized protocols. **Interoperability** means that a workflow interoperates with other workflows, and workflow components interoperate, by exchanging data and/or metadata, and/or through interaction via APIs, described by standards. Finally, **Reusability** means that a workflow is both usable (can be executed) and reusable (can be understood, modified, built upon, or incorporated into other workflows).

<div id="tab:1">

| Guideline                                                                                                                                                                      | Based on\[1\]          |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------- |
| F1. A workflow is assigned a globally unique and persistent identifier.                                                                                                        | D-F1 and S-F1          |
|                                                                                                                                                                                |                        |
| F1.1. Components of the workflow representing levels of granularity are assigned distinct identifiers.                                                                         | S-F1.1                 |
|                                                                                                                                                                                |                        |
| F1.2. Different versions of the workflow are assigned distinct identifiers.                                                                                                    | S-F1.2                 |
|                                                                                                                                                                                |                        |
| F2. A workflow and its components are described with rich metadata.                                                                                                            | D-F2 and S-F2          |
|                                                                                                                                                                                |                        |
| F3. Metadata clearly and explicitly include the identifier of the workflow, and workflow versions, that they describe.                                                         | D-F3 and S-F3          |
|                                                                                                                                                                                |                        |
| F4. Metadata and workflow are registered or indexed in a searchable FAIR resource.                                                                                             | D-F4 and S-F4          |
|                                                                                                                                                                                |                        |
| A1. Workflow and its components are retrievable by their identifiers using a standardized communications protocol.                                                             | D-A1 and S-A1          |
|                                                                                                                                                                                |                        |
| A1.1. The protocol is open, free, and universally implementable.                                                                                                               | D-A1.1 and S-A1.1      |
|                                                                                                                                                                                |                        |
| A1.2. The protocol allows for an authentication and authorization procedure, when necessary.                                                                                   | D-A1.2 and S-A1.2      |
|                                                                                                                                                                                |                        |
| A2. Metadata are accessible, even when the workflow is no longer available.                                                                                                    | D-A2 and S-A2          |
|                                                                                                                                                                                |                        |
| I1. Workflow and its metadata (including workflow run provenance) use a formal, accessible, shared, transparent, and broadly applicable language for knowledge representation. | D-I1 and S-R1.2        |
|                                                                                                                                                                                |                        |
| I2. Metadata and workflow use vocabularies that follow FAIR principles.                                                                                                        | D-I2                   |
|                                                                                                                                                                                |                        |
| I3. Workflow is specified in a way that allows its components to read, write, and exchange data (including intermediate data), in a way that meets domain-relevant standards.  | D-R3 and S-I1          |
|                                                                                                                                                                                |                        |
| I4. Workflow and its metadata (including workflow run provenance) include qualified references to other objects and the workflow’s components.                                 | D-I3, S-I2, and S-R1.2 |
|                                                                                                                                                                                |                        |
| R1. Workflow is described with a plurality of accurate and relevant attributes.                                                                                                | D-R1 and S-R1          |
|                                                                                                                                                                                |                        |
| R1.1. Workflow is released with a clear and accessible license.                                                                                                                | D-R1.1 and S-R1.1      |
|                                                                                                                                                                                |                        |
| R1.2. Components of the workflow representing levels of granularity are given clear and accessible licenses.                                                                   | D-R1.1 and S-R1.1      |
|                                                                                                                                                                                |                        |
| R1.3. Workflow is associated with detailed provenance of the workflow and of the products of the workflow.                                                                     | D-R1.2 and S-R1.2      |
|                                                                                                                                                                                |                        |
| R2. Workflow includes qualified references to other workflows.                                                                                                                 | D-I3 and S-R2          |
|                                                                                                                                                                                |                        |
| R3. Workflow meets domain-relevant community standards.                                                                                                                        | D-R1.3 and S-R3        |

The FAIR Principles Applied to Computational Workflows

</div>

## Findability

The data and software principles generally apply to workflows, but with novel/additional considerations on our interpretation of a component and a strengthening of metadata associated with workflow versions. Workflows are subject to continuous refinement and independent modification, often resulting in multiple versions, adaptations, and variants, with workflows extended, nested, and reused as sub-workflows. Researchers modify workflows for specific purposes, adjust components, and provide alternative methods across various platforms; components are copied, pasted, and modified.

Identifiers are important because unlike software, authors often neglect to “name” their workflows (although they do name their workflow management systems). Identifiers establish a clear lineage of each workflow and component’s origin and changes, enabling researchers to understand the workflow structure and evolution, compare iterations, relate workflows to each other, and confidently build upon previous work. Persistent identifiers identify and reference specific versions to ensure accurate identification and traceability and to support developer citation and source workflow attribution (F1). Unique identifiers to different versions of workflows recognize their dynamic nature in research (F1.2). Unique identifiers for a workflow’s components and versions (whether a file, computational step, or sub-workflow) support traceability and facilitate reuse, reproducibility, and portability across different workflow versions (F1.1).

Rich metadata for the overall workflows and their components (including inputs and outputs) (F2, F3) should use a formal, accessible language for knowledge representation, such as schema.org (<https://schema.org>), and standardized metadata such as the Bioschemas schema.org profile for Computational Workflows (<https://bioschemas.org/types/ComputationalWorkflow/>), used for workflow components in Workflow Run Crate profile \[19\] and CodeMeta (<https://w3id.org/codemeta/v3.0>). Other metadata forms for workflows include canonical “Rosetta” languages (e.g. CWL \[20\], WDL \[21\]) that abstract from the native workflow language for greater portability and comparability. Such metadata are used for registration and search in dedicated and trusted workflow registries such as WorkflowHub \[22\] and Dockstore (F4) \[23\].

## Accessibility

The data and software principles generally apply but with new considerations on what it means for a workflow to be available. The workflow may be restricted to execution at one facility, which is a common case in highly optimized HPC settings, and access to that facility may be restricted (A1.2). Single sign-on for workflow components requires harmonized Authentication and Authorization Infrastructure (AAI) propagation through the different tasks, if they are hosted by different service providers. “A2. Metadata are accessible, even when the workflow is no longer available” requires further interpretation given a workflow’s dual nature as process description (data) and process execution (software), and we must understand what “no longer available” means. As a piece of software, a workflow execution platform or the infrastructure that it operates on may become deprecated and/or unavailable. Dependency on the component code and services makes a workflow vulnerable to “software rot”, and it is not always possible to completely containerize and preserve all code, such as when they are remotely executed third party tools or call-outs to online datasets \[24\].

As a process description, the workflow captures both the steps and data flow of a recipe for a method, which is a form of the “metadata”. Thus at least the workflow and its components descriptions, and if relevant the workflow run components, should be preserved and archived in a long-term registry or repository, so that if the workflow is no longer executable, it will still be readable. If we interpret a workflow description file as data, the data principles decree that at least the metadata for that file should still be retrievable. For a workflow, however, that data file is the essence of the workflow. We interpret the workflow description to be a form of metadata of the software and therefore, it must always be accessible. A workflow associated with a publication may still be examined as a method, and its provenance may be inspected; the description should be enough to be translated for another workflow system. Apart from manual or AI-assisted porting of code, this can also happen via “Rosetta” workflow languages like CWL and WDL (as e.g. done in MGnify \[25\] and by Snakemake’s CWL export).

## Interoperability

The data and software principles combine and blur with principles from Reusability, as we tease apart the FAIR requirements for a workflow, its components (both executable and data), and an instantiated and executed run of the workflow. For example, principle I1 applies to describing the static workflow structure of the specification and capturing dynamic aspects of the run such as execution details and intermediate outputs. The workflow specification plays a role in data in I1, I2, and I4 adapting data principles, as well as the role of metadata of the software, co-opting software principles.

We adapt software principles for I3 and I4 to explicitly refer to the domain standard description of input and outputs of the workflow executable components. As data components of a workflow, the expected input and output datasets, benchmarks and parameters, and the actual datasets and parameter files from a workflow run, should also adhere to community standards (data principle R1.3), as should intermediate data derived during the execution. The principles encourage workflow portability across different types of computational environments (e.g., via containerization or OS-agnostic package management) \[13\] and, ideally, easy translation from one language/management system to another or at least compatibility and seamless integration (in case of sub-workflows).

Standard language formats like CWL encourage interoperability and offer the potential for workflow comparisons and exchange between different languages, through documentation of components, inputs, and outputs. We explicitly add workflow run provenance to interoperability as documented execution steps and data lineage traces are important components that should also be interoperable and machine-actionable \[26\].

## Reusability

Reusability of the workflow as an executable method with modifications to its parameters and input files is an expected and anticipated use of the workflow, tied up in the quality of its documentation and the accessibility of computational infrastructure capable of executing it.

While previously discussing findability, we also highlighted the reusability of workflows as complex compositions intended to be modified, built upon, and incorporated into other workflows, as well as their reusability as runnable executions with modified datasets and parameter files \[27\]. The data and software principles are adapted to emphasize the composite nature of workflows (both executable and data components) for licensing \[28\]. Workflows are composed of many parts, potentially from different authors with different intents for how their artifacts may be used; these intents must be clearly stated by the inclusion of licenses that cover all parts of the workflow and sub-parts of the workflows that can be reused as sub-workflows \[13\].

The provenance history of the workflow – its authors, purpose, workflows of which it may be a variant, links to other sub-workflows and so on, are included in R1.3 drawing from both data and software principles R1.2. The provenance of data products tracked by the workflow run provenance collection is related to the data principles R1.2 where data (in this case the products of the workflow) are associated with detailed provenance that a workflow system should be able to provide. A benefit of using fully fledged workflow systems is the capture of computer-interpretable provenance (meta)data to track the history and origin of data processing steps. R1 and R3 expect that input and output datasets are thoroughly described with example input and expected output data for each step that adhere to data structure and file format standards \[13\] and gold standards for benchmarking \[28\].

# Examples

Here, we provide concrete examples with detailed descriptions for applying the FAIR principles to both workflow specifications and workflow runs. For each case, we narrate through the FAIR principles sequentially. We recommend the reader to follow along with Table [1](#tab:1) as a guide.

## Example workflow specification

The Protein MD Setup workflow sets up a protein molecular dynamic simulation that returns a protein structure and simulated 3D trajectories \[29\]. It is registered in WorkflowHub (<https://doi.org/10.48546/workflowhub.workflow.29.3>), where it has been assigned a Digital Object Identifier (DOI) which is globally unique (F1). Different versions of this workflow can be identified using unique digital object identifiers (F1.2). The workflow is described using (rich) metadata (F2) that includes the identifier of the workflow and its unique version (F3). The workflow and associated metadata are registered (F4). Moreover, components of the workflow have their own individual persistent identifiers as the workflow is composed of sub-workflow BioBB building blocks from the BioBB Library (<https://workflowhub.eu/projects/11>) (F1.2). The workflow and its components can be retrieved and downloaded using a standardized HTTPS protocol (A1, A1.1, A1.2). The metadata associated with the workflow and its components is independent from the GitHub code repository and are accessible on WorkflowHub even if the workflow (or its components) become inaccessible (A2).

The Protein MD Setup is written using CWL which follows a formal and declarative paradigm for workflow implementation (I1). The workflow does not include all the best-practice principles to fulfill I2 and I3. This extends to the workflow metadata, which does not use a domain-specific ontology. The workflow and its metadata include qualified references to other objects and components (I4). However, CWL standard itself allows metadata and workflow vocabularies (e.g. Bioschemas, EDAM \[30\]) that are consistent with FAIR principles (I2), enables the components of the workflows to read, write, and exchange data using format that meets domain-specific standards (I3), and assigns qualified references to workflow components, inputs, and outputs.

The workflow is released under Apache License 2.0 software license (R1.1) and WorkflowHub’s RO-Crate references that the embedded CWL code is archived from the corresponding GitHub source code repository (<https://github.com/bioexcel/biobb-wf-md-setup-protein-cwl>). The component BioBB building blocks of the workflow have their own clear and accessible licenses (R1.2). The workflow is associated with detailed provenance about its development, provided as a downloadable RO-Crate object (R1.3).

## Example workflow run

Here, we demonstrate the application of the FAIR principles to a workflow run. Recall from our previous definitions that a workflow run is the instantiation of a workflow with inputs (parameters files, input datasets) and outputs (output data, the provenance execution log and lineage of data products). In this example, the workflow run is instantiated from a tissue/tumor prediction workflow specification for digital pathology, and it is represented using RO-Crate \[31\].

The workflow run has been assigned a globally unique DOI (F1), and components of the workflow run (e.g. steps, inputs, outputs) are also assigned their own distinct identifiers (F1.1). The workflow run is described using rich metadata (F2) that includes the identifier of the workflow run and its unique version (F3). The corresponding workflow specification is not registered, but it is publicly available via GitHub (<https://github.com/crs4/deephealth-pipelines>), and the workflow run is registered on Zenodo, which is a searchable FAIR resource (F4).

The workflow run and its components are also hosted on Zenodo, which means that they can be retrieved and downloaded using the HTTPS protocol, which is standardized (A1), open and free and universally implementable (A1.1), and able to support authentication and authorization procedures (A1.2). The metadata associated with the workflow run and its components are independent from the workflow run and components themselves, and they are accessible on Zenodo even if the workflow run and its components become inaccessible (A2).

Recall from Figure [1](#fig:1) that execution provenance is a product of a workflow run. Here, provenance from the digital pathology tissue/tumor prediction workflow run is generated using CWLProv \[32\] in the form of RO-Bundle and then converted to an RO-Crate \[33\] that follows the Provenance Run Crate profile (<https://www.researchobject.org/workflow-run-crate/profiles/0.1/provenance_run_crate>). All of these methods represent workflow run information by utilizing well-established standards and language (I1). CWLProv and RO-Crate allow vocabularies that are consistent with the FAIR principles (I2). The workflow run provenance is generated using CWLProv and documented as a Provenance Run Crate profile showing the exchange of data between components of the workflow. The workflow run does not, however, include domain-specific standards for metadata to fulfill (which means it does not satisfy I3). The workflow run provenance does include qualified references to other objects and the workflow’s components (I4).

The workflow run is described with many accurate and relevant attributes (R1), and it is released under the clear and accessible MIT License (R1.1). One of the workflow run’s components, Slaid, is a library for applying DL models from the DeepHealth project (<https://deephealth-project.eu/>) on whole slide images (WSI) that is also released independently under the MIT License (R1.2). The workflow run contains detailed provenance about the execution, provided as a downloadable RO-Crate object (R1.3). The workflow run processes digital pathology images in the formats supported by OpenSlide (R3), which is a widespread software library that represents a community standard for digital pathology images \[34\].

# FAIRness beyond the FAIR Principles

The FAIR principles in Table [1](#tab:1) focus on the workflows as scholarly research assets to be found, accessed, interoperated, and reused. They do not extend to the quality of the workflows (FAIR+Q) or the extent of the reproducibility of the workflows (FAIR+R), and they only hint at their portability and sustainability. The Open Data, Open Code, Open Infrastructure (O3) guidelines complement FAIR by providing an actionable road map toward sustainability \[35\]. Note, however, that FAIR does not require openness; authors and companies may even choose not to publish their workflows or metadata at all, but still use “inner FAIR” principles \[36\] for their own benefits.

Workflows are composites of executable components that need to be validated and tested with clean interfaces, permissive access permissions if remotely executed, and compatible licenses. Work on canonical workflow libraries \[37\] and building blocks that are interoperable between languages \[29\], workflow readiness of tools \[38\], FAIR unit testing like pytest-workflow for WDL (<https://github.com/LUMC/pytest-workflow>), test monitoring like LifeMonitor(<https://crs4.github.io/life_monitor/>), and benchmarking like OpenEBench (<https://openebench.bsc.es/>) are steps towards creating FAIR workflow professional practices that should include peer review, curation, and perhaps even certification.

We should also consider the relationship of FAIR to other services in a workflow’s service ecosystem. Container technologies such as Docker and Singularity play a role in the interoperability, reusability, and reproducibility of computational workflows by providing lightweight, portable, and self-contained environments that include all of the software dependencies and libraries required to run a workflow. In alignment with the FAIR principles, containers can be versioned and shared through registries like Docker Hub, Nexus Repository, or Github Container registry, but these registries are not truly FAIR because old versions may not be preserved. FAIR workflows should be stored in version-controlled repositories like GitHub and GitLab and indexed by registries like Dockstore \[23\] and WorkflowHub \[22\]. Workflow registries like Dockstore and WorkflowHub support findability and accessibility so workflows can be shared, published, and reused as well as downloaded or launched using dedicated infrastructure facilities such as Galaxy Europe. Both support example input and test data components for a workflow specification but do not retain the result components of a workflow run – the provenance and links to datasets that are the resulting products. That is expected to be managed by data repositories like Zenodo and Figshare that in turn need to support FAIR data principles. However, this container approach most probably shows practical limitations when applied to workflows executed on very large-scale, meticulously maintained and pampered HPC environments running on the verge of computational and technical stability. For such cases, reproducibility of workflows might always be an issue.

Workflows are multi-part objects whose data components are as important as their executable steps; all these digital objects should be FAIR too. Community efforts like RO-Crate \[39\] propose the means to encapsulate workflows and all their components while capturing the context in which they are used (e.g., executions, bibliography, sketches, etc.). An RO-Crate Workflow profile (<https://about.workflowhub.eu/Workflow-RO-Crate/>) includes references to components which also need to be FAIR. By having workflows as composition of FAIR research outputs, the FAIRness of each contained resource is validated, since the execution of the workflow relies on these resources being available. Services like WorkflowHub (registry), LifeMonitor (test monitoring), and Galaxy (workflow platform) implement RO-Crate for comprehensive workflow representation and exchange as well as a step to sharing metadata and persistent identifiers to implement the FAIR principles of Table [1](#tab:1).

As workflows typically operate on and produce datasets, they are well placed to make those data products FAIR; they provide the process description and automated data provenance collection, and a fully fledged WMS can automate processes for generating FAIR data. Nevertheless, workflows have to be well designed to be “FAIR aware”: producing and consuming data in standardized formats, assigning license, handling identifiers, and metadata production, data versioning, etc \[14\]. Using workflows as automated instruments for “FAIR data by design” can encourage inputs and make outputs to be machine-actionable and more suitable for use in other workflows, for example those that span geographically distinct computing facilities \[40\].

# Conclusion

Computational workflows are key instruments for the advancement in scientific research, potentially revolutionizing how data is managed, analyzed, and shared. Workflows not only serve as software that can be used by experts and non-coders alike; they also serve as documentation of scientific processes, encapsulating not only the data and software used but also the context and conditions under which discoveries were made. It is expected that this comprehensive documentation will not only enhance the credibility of research findings but will also facilitate the replication and validation of scientific results across diverse settings and by different research teams.

FAIR data and FAIR software principles both apply to workflows, combining structured, well-described data with portable, well-documented software creating a powerful framework for advancing scientific knowledge. Moreover, the next generation of workflows – assisted auto-assembly, generative workflows, dynamic reconfiguration, and so on – will require rich, machine-actionable metadata.

FAIR application requires interpretation, however, to consider the abstraction and the compositional properties of workflows. The usual challenges for FAIR implementation are still present: incentives, resources, assessment, support services, and so on. Even when opportunities arise for metadata enrichment when registering workflows in WorkflowHub, for example, the best curators do not manage all the principles, and most take the simplest route. FAIR workflow implementation will “take a village” of services, including data services and support from workflow management systems, and well-designed workflows that are FAIR data-aware will require golden standard examples, training, and professionalization.

This research used resources of: the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. Department of Energy under Contract No. DE-AC05-00OR22725 (SRW); Sandia National Laboratories, a multi-mission laboratory managed and operated by National Technology & Engineering Solutions of Sandia, LLC (NTESS), a wholly owned subsidiary of Honeywell International Inc., for the U.S. Department of Energy’s National Nuclear Security Administration (DOE/NNSA) under contract DE-NA0003525 (LP); the European Union programme Horizon Europe under grant agreements HORIZON-INFRA-2021-EOSC-01 101057388 (EuroScienceGateway), HORIZON-INFRA-2023-EOSC-01-02 101129744 (EVERSE; SS), HORIZON-INFRA-2021-EOSC-01-05 101057344 and by UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee grants 10038963 (EuroScienceGateway; CG, S-SR), 10038992 (FAIR-IMPACT; NJ); Australian BioCommons, which is enabled by NCRIS via Bioplatforms Australia funding (JG); Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) as part of GHGA – The German Human Genome-Phenome Archive (<https://www.ghga.de>, Grant Number 441914366 (NFDI 1/1)); the National Research Agency under the France 2030 program, with reference to ANR-22-PESN0007 (KB). This manuscript has been authored by UT-Battelle, LLC, under contract DE-AC05-00OR22725 with the US Department of Energy (DOE). This written work is authored by an employee of NTESS. The employee, not NTESS, owns the right, title and interest in and to the written work and is responsible for its contents. Any subjective views or opinions that might be expressed in the written work do not necessarily represent the views of the U.S. Government. The US government retains and the publisher, by accepting the article for publication, acknowledges that the US government retains a nonexclusive, paid-up, irrevocable, worldwide license to publish or reproduce the published form of this manuscript, or allow others to do so, for US government purposes. DOE will provide public access to these results of federally sponsored research in accordance with the DOE Public Access Plan (<https://www.energy.gov/doe-public-access-plan>).

SRW and CG are the primary authors of the manuscript. All other authors are listed alphabetically and contributed to the manuscript by participating in the WCI-FW meetings and by editing or commenting on the manuscript text.

The authors declare no competing interests.

<div id="refs" class="references">

<div id="ref-SCHINTKE202482">

1\. Florian Schintke, Khalid Belhajjame, Ninon De Mecquenem, David Frantz, Vanessa Emanuela Guarino, Marcus Hilbrich, Fabian Lehmann, Paolo Missier, Rebecca Sattler, Jan Arne Sparka, Daniel T. Speckhard, Hermann Stolte, Anh Duc Vu, & Ulf Leser (2024): Validity constraints for data analysis workflows. *Future Generation Computer Systems*, **157**. <https://doi.org/https://doi.org/10.1016/j.future.2024.03.037>

</div>

<div id="ref-DiTommaso2017">

2\. Paolo Di Tommaso, Maria Chatzou, Evan W. Floden, Pablo Prieto Barja, Emilio Palumbo, & Cedric Notredame (2017): Nextflow enables reproducible computational workflows. *Nature Biotechnology*, **35** (4). <https://doi.org/10.1038/nbt.3820>

</div>

<div id="ref-Galaxy2024">

3\. Linelle Ann L. Abueg, Enis Afgan, Olivier Allart, Ahmed H. Awan, Wendi A. Bacon, Dannon Baker, Madeline Bassetti, Bérénice Batut, Matthias Bernt, Daniel Blankenberg, Aureliano Bombarely, Anthony Bretaudeau, Catherine J. Bromhead, Melissa L. Burke, Patrick K. Capon, Martin Čech, María Chavero-Díez, John M. Chilton, Tyler J. Collins, Frederik Coppens, Nate Coraor, Gianmauro Cuccuru, Fabio Cumbo, John Davis, Paul F. De Geest, Willem de Koning, Martin Demko, Assunta DeSanto, José Manuel Domínguez Begines, Maria A. Doyle, Bert Droesbeke, Anika Erxleben-Eggenhofer, Melanie C. Föll, Giulio Formenti, Anne Fouilloux, Rendani Gangazhe, Tanguy Genthon, Jeremy Goecks, Alejandra N. Gonzalez Beltran, Nuwan A. Goonasekera, Nadia Goué, Timothy J. Griffin, Björn A. Grüning, Aysam Guerler, Sveinung Gundersen, Ove Johan Ragnar Gustafsson, Christina Hall, Thomas W. Harrop, Helge Hecht, Alireza Heidari, Tillman Heisner, Florian Heyl, Saskia Hiltemann, Hans-Rudolf Hotz, Cameron J. Hyde, Pratik D. Jagtap, Julia Jakiela, James E. Johnson, Jayadev Joshi, Marie Jossé, Khaled Jum’ah, Matúš Kalaš, Katarzyna Kamieniecka, Tunc Kayikcioglu, Markus Konkol, Leonid Kostrykin, Natalie Kucher, Anup Kumar, Mira Kuntz, Delphine Lariviere, Ross Lazarus, Yvan Le Bras, Gildas Le Corguillé, Justin Lee, Simone Leo, Leandro Liborio, Romane Libouban, David López Tabernero, Lucille Lopez-Delisle, Laila S. Los, Alexandru Mahmoud, Igor Makunin, Pierre Marin, Subina Mehta, Winnie Mok, Pablo A. Moreno, François Morier-Genoud, Stephen Mosher, Teresa Müller, Engy Nasr, Anton Nekrutenko, Tiffanie M. Nelson, Asime J. Oba, Alexander Ostrovsky, Polina V. Polunina, Krzysztof Poterlowicz, Elliott J. Price, Gareth R. Price, Helena Rasche, Bryan Raubenolt, Coline Royaux, Luke Sargent, Michelle T. Savage, Volodymyr Savchenko, Denys Savchenko, Michael C. Schatz, Pauline Seguineau, Beatriz Serrano-Solano, Nicola Soranzo, Sanjay Kumar Srikakulam, Keith Suderman, Anna E. Syme, Marco Antonio Tangaro, Jonathan A. Tedds, Mehmet Tekman, Wai Cheng (Mike) Thang, Anil S. Thanki, Michael Uhl, Marius van den Beek, Deepti Varshney, Jenn Vessio, Pavankumar Videm, Greg Von Kuster, Gregory R. Watson, Natalie Whitaker-Allen, Uwe Winter, Martin Wolstencroft, Federico Zambelli, Paul Zierep, & Rand Zoabi (2024): The galaxy platform for accessible, reproducible, and collaborative data analyses: 2024 update. *Nucleic Acids Research*, **52** (W1). <https://doi.org/10.1093/nar/gkae410>

</div>

<div id="ref-Molder2021">

4\. Felix Mölder, Kim Philipp Jablonski, Brice Letcher, Michael B. Hall, Christopher H. Tomkins-Tinch, Vanessa Sochat, Jan Forster, Soohyun Lee, Sven O. Twardziok, Alexander Kanitz, Andreas Wilm, Manuel Holtgrewe, Sven Rahmann, Sven Nahnsen, & Johannes Köster (2021): Sustainable data analysis with snakemake. *F1000Research*, **10**. <https://doi.org/10.12688/f1000research.29032.2>

</div>

<div id="ref-Babuji2019">

5\. Yadu Babuji, Anna Woodard, Zhuozhao Li, Daniel S. Katz, Ben Clifford, Rohan Kumar, Lukasz Lacinski, Ryan Chard, Justin M. Wozniak, Ian Foster, Michael Wilde, & Kyle Chard (2019): **Parsl: Pervasive parallel programming in python**. In, *Proceedings of the 28th international symposium on high-performance parallel and distributed computing* (ACM). <https://doi.org/10.1145/3307681.3325400>

</div>

<div id="ref-kanwal-2017">

6\. Sehrish Kanwal, Farah Zaib Khan, Andrew Lonie, & Richard O. Sinnott (n.d.): Investigating reproducibility and tracking provenance –a genomic workflow case study. *BMC Bioinformatics*, **18** (1). <https://doi.org/10.1186/s12859-017-1747-0>

</div>

<div id="ref-roadmap2022">

7\. Rafael Ferreira da Silva, Rosa M. Badia, Venkat Bala, Debbie Bard, Peer-Timo Bremer, Ian Buckley, Silvina Caino-Lores, Kyle Chard, Carole Goble, Shantenu Jha, Daniel S. Katz, Daniel Laney, Manish Parashar, Frederic Suter, Nick Tyler, Thomas Uram, Ilkay Altintas, Stefan Andersson, William Arndt, Juan Aznar, Jonathan Bader, Bartosz Balis, Chris Blanton, Kelly Rosa Braghetto, Aharon Brodutch, Paul Brunk, Henri Casanova, Alba Cervera Lierta, Justin Chigu, Taina Coleman, Nick Collier, Iacopo Colonnelli, Frederik Coppens, Michael Crusoe, Will Cunningham, Bruno De Paula Kinoshita, Paolo Di Tommaso, Charles Doutriaux, Matthew Downton, Wael Elwasif, Bjoern Enders, Chris Erdmann, Thomas Fahringer, Ludmilla Figueiredo, Rosa Filgueira, Martin Foltin, Anne Fouilloux, Luiz Gadelha, Andy Gallo, Artur Garcia Saez, Daniel Garijo, Roman Gerlach, Ryan Grant, Samuel Grayson, Patricia Grubel, Johan Gustafsson, Valerie Hayot-Sasson, Oscar Hernandez, Marcus Hilbrich, AnnMary Justine, Ian Laflotte, Fabian Lehmann, Andre Luckow, Jakob Luettgau, Ketan Maheshwari, Motohiko Matsuda, Doriana Medic, Pete Mendygral, Marek Michalewicz, Jorji Nonaka, Maciej Pawlik, Loic Pottier, Line Pouchard, Mathias Putz, Santosh Kumar Radha, Lavanya Ramakrishnan, Sashko Ristov, Paul Romano, Daniel Rosendo, Martin Ruefenacht, Katarzyna Rycerz, Nishant Saurabh, Volodymyr Savchenko, Martin Schulz, Christine Simpson, Raul Sirvent, Tyler Skluzacek, Stian Soiland-Reyes, Renan Souza, Sreenivas Rangan Sukumar, Ziheng Sun, Alan Sussman, Douglas Thain, Mikhail Titov, Benjamin Tovar, Aalap Tripathy, Matteo Turilli, Bartosz Tuznik, Hubertus Van Dam, Aurelio Vivas, Logan Ward, Patrick Widener, Sean Wilkinson, Justyna Zawalska, & Mahnoor Zulfiqar (2023): Workflows community summit 2022: A roadmap revolution. <https://doi.org/10.5281/ZENODO.7750670>

</div>

<div id="ref-garijo2014">

8\. Daniel Garijo, Oscar Corcho, Yolanda Gil, Meredith N. Braskie, Derrek Hibar, Xue Hua, Neda Jahanshad, Paul Thompson, & Arthur W. Toga (2014): **Workflow reuse in practice: A study of neuroimaging pipeline users**. In, *2014 ieee 10th international conference on e-science*, pp. 239–246. <https://doi.org/10.1109/eScience.2014.33>

</div>

<div id="ref-Wilkinson2016-vi">

9\. Mark D. Wilkinson, Michel Dumontier, Ijsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas Blomberg, Jan-Willem Boiten, Luiz Bonino da Silva Santos, Philip E. Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas, Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard Finkers, Alejandra Gonzalez-Beltran, Alasdair J. G. Gray, Paul Groth, Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A. C. ’t Hoen, Rob Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E. Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe Rocca-Serra, Marco Roos, Rene van Schaik, Susanna-Assunta Sansone, Erik Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz, Mark Thompson, Johan van der Lei, Erik van Mulligen, Jan Velterop, Andra Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, & Barend Mons (2016): The FAIR guiding principles for scientific data management and stewardship. *Sci. Data*, **3** (1). <https://doi.org/10.1038/sdata.2016.18>

</div>

<div id="ref-Barker2022-mn">

10\. Michelle Barker, Neil P. Chue Hong, Daniel S. Katz, Anna-Lena Lamprecht, Carlos Martinez-Ortiz, Fotis Psomopoulos, Jennifer Harrow, Leyla Jael Castro, Morane Gruenpeter, Paula Andrea Martinez, & Tom Honeyman (2022): Introducing the FAIR principles for research software. *Sci. Data*, **9** (1). <https://doi.org/10.1038/s41597-022-01710-x>

</div>

<div id="ref-industry-fair">

11\. Herman van Vlijmen, Albert Mons, Arne Waalkens, Wouter Franke, Arie Baak, Gerbrand Ruiter, Christine Kirkpatrick, Luiz Olavo Bonino da Silva Santos, Bert Meerman, Renger Jellema, Derk Arts, Martijn Kersloot, Sebastiaan Knijnenburg, Scott Lusher, Rudi Verbeeck, & Jean-Marc Neefs (2020): The need of industry to go fair. *Data Intelligence*, **2** (1-2). <https://doi.org/10.1162/dint_a_00050>

</div>

<div id="ref-harrow2022">

12\. Ian Harrow, Rama Balakrishnan, Hande Küçük McGinty, Tom Plasterer, & Martin Romacker (2022): Maximizing data value for biopharma through fair and quality implementation: FAIR plus q. *Drug Discovery Today*, **27** (5). <https://doi.org/https://doi.org/10.1016/j.drudis.2022.01.006>

</div>

<div id="ref-De_Visser2023-pr">

13\. Casper de Visser, Lennart F. Johansson, Purva Kulkarni, Hailiang Mei, Pieter Neerincx, K. Joeri van der Velde, Péter Horvatovich, Alain J. van Gool, Morris A. Swertz, Peter A. C. ’t Hoen, & Anna Niehues (2023): Ten quick tips for building FAIR workflows. *PLoS Comput. Biol.*, **19** (9). <https://doi.org/10.1371/journal.pcbi.1011369>

</div>

<div id="ref-Goble2020-sn">

14\. Carole Goble, Sarah Cohen-Boulakia, Stian Soiland-Reyes, Daniel Garijo, Yolanda Gil, Michael R. Crusoe, Kristian Peters, & Daniel Schober (2020): FAIR computational workflows. *Data Intell.*, **2** (1-2). <https://doi.org/10.1162/dint_a_00033>

</div>

<div id="ref-wolf2021">

15\. Matthew Wolf, Jeremy Logan, Kshitij Mehta, Daniel Jacobson, Mikaela Cashman, Angelica M. Walker, Greg Eisenhauer, Patrick Widener, & Ashley Cliff (2021): **Reusability first: Toward fair workflows**. In, *2021 ieee international conference on cluster computing (cluster)*, pp. 444–455. <https://doi.org/10.1109/Cluster48925.2021.00053>

</div>

<div id="ref-Wilkinson2022">

16\. Sean R. Wilkinson, Greg Eisenhauer, Anuj J. Kapadia, Kathryn Knight, Jeremy Logan, Patrick Widener, & Matthew Wolf (2022): **F\*\*\* workflows: when parts of FAIR are missing**. In, *2022 ieee 18th international conference on e-science (e-science)* (IEEE), pp. 507–512. <https://doi.org/10.1109/escience55777.2022.00090>

</div>

<div id="ref-Niehues2024">

17\. Anna Niehues, Casper de Visser, Fiona A. Hagenbeek, Purva Kulkarni, René Pool, Naama Karu, Alida S. D. Kindt, Gurnoor Singh, Robert R. J. M. Vermeiren, Dorret I. Boomsma, Jenny van Dongen, Peter A. C. ’t Hoen, & Alain J. van Gool (2024): A multi-omics data analysis workflow packaged as a fair digital object. *GigaScience*, **13**. <https://doi.org/10.1093/gigascience/giad115>

</div>

<div id="ref-Zulfiqar2024">

18\. Mahnoor Zulfiqar, Michael R. Crusoe, Birgitta König-Ries, Christoph Steinbeck, Kristian Peters, & Luiz Gadelha (2024): Implementation of fair practices in computational metabolomics workflows—a case study. *Metabolites*, **14** (2). <https://doi.org/10.3390/metabo14020118>

</div>

<div id="ref-Leo2024">

19\. Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno P. Kinoshita, & Stian Soiland-Reyes (2024): Recording provenance of workflow runs with ro-crate. *PLOS ONE*, **19** (9). <https://doi.org/10.1371/journal.pone.0309210>

</div>

<div id="ref-Crusoe2022">

20\. Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian Soiland-Reyes, Bogdan Gavrilović, Carole Goble, & The CWL Community (2022): Methods included: Standardizing computational reuse and portability with the common workflow language. *Communications of the ACM*, **65** (6). <https://doi.org/10.1145/3486897>

</div>

<div id="ref-Voss2017">

21\. Kate Voss, Geraldine Van Der Auwera, & Jeff Gentry (2017): Full-stack genomics pipelining with gatk4 + wdl + cromwell. <https://doi.org/10.7490/F1000RESEARCH.1114634.1>

</div>

<div id="ref-Goble2021">

22\. Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, José Mª Fernández, Salvador Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano, Philip Ewels, & Frederik Coppens (2021): Implementing fair digital objects in the eosc-life workflow collaboratory. <https://doi.org/10.5281/ZENODO.4605654>

</div>

<div id="ref-Yuen2021">

23\. Denis Yuen, Louise Cabansay, Andrew Duncan, Gary Luu, Gregory Hogue, Charles Overbeck, Natalie Perez, Walt Shands, David Steinberg, Chaz Reid, Nneka Olunwa, Richard Hansen, Elizabeth Sheets, Ash O’Farrell, Kim Cullion, Brian D. O’Connor, Benedict Paten, & Lincoln Stein (2021): The dockstore: Enhancing a community platform for sharing reproducible and accessible computational protocols. *Nucleic Acids Research*, **49** (W1). <https://doi.org/10.1093/nar/gkab346>

</div>

<div id="ref-Zhao2012">

24\. Jun Zhao, Jose Manuel Gomez-Perez, Khalid Belhajjame, Graham Klyne, Esteban Garcia-Cuesta, Aleix Garrido, Kristina Hettne, Marco Roos, David De Roure, & Carole Goble (2012): **Why workflows break – understanding and combating decay in taverna workflows**. In, *2012 ieee 8th international conference on e-science* (IEEE). <https://doi.org/10.1109/escience.2012.6404482>

</div>

<div id="ref-richardson2023">

25\. Lorna Richardson, Ben Allen, Germana Baldi, Martin Beracochea, Maxwell L. Bileschi, Tony Burdett, Josephine Burgin, Juan Caballero-Pérez, Guy Cochrane, Lucy J. Colwell, Tom Curtis, Alejandra Escobar-Zepeda, Tatiana A. Gurbich, Varsha Kale, Anton Korobeynikov, Shriya Raj, Alexander B. Rogers, Ekaterina Sakharova, Santiago Sanchez, Darren J. Wilkinson, & Robert D. Finn (2022): MGnify: the microbiome sequence data analysis resource in 2023. *Nucleic Acids Research*, **51** (D1). <https://doi.org/10.1093/nar/gkac1080>

</div>

<div id="ref-nicolae2023">

26\. Bogdan Nicolae, Tanzima Z. Islam, Robert Ross, Huub Van Dam, Kevin Assogba, Polina Shpilker, Mikhail Titov, Matteo Turilli, Tianle Wang, Ozgur O. Kilic, Shantenu Jha, & Line C. Pouchard (2023): **Building the i (interoperability) of fair for performance reproducibility of large-scale composable workflows in recup**. In, *2023 ieee 19th international conference on e-science (e-science)*, pp. 1–7. <https://doi.org/10.1109/e-Science58273.2023.10254808>

</div>

<div id="ref-Lamprecht2021">

27\. Anna-Lena Lamprecht, Magnus Palmblad, Jon Ison, Veit Schwämmle, Mohammad Sadnan Al Manir, Ilkay Altintas, Christopher J. O. Baker, Ammar Ben Hadj Amor, Salvador Capella-Gutierrez, Paulos Charonyktakis, Michael R. Crusoe, Yolanda Gil, Carole Goble, Timothy J. Griffin, Paul Groth, Hans Ienasescu, Pratik Jagtap, Matúš Kalaš, Vedran Kasalica, Alireza Khanteymoori, Tobias Kuhn, Hailiang Mei, Hervé Ménager, Steffen Möller, Robin A. Richardson, Vincent Robert, Stian Soiland-Reyes, Robert Stevens, Szoke Szaniszlo, Suzan Verberne, Aswin Verhoeven, & Katherine Wolstencroft (2021): Perspectives on automated composition of workflows in the life sciences. *F1000Research*, **10**. <https://doi.org/10.12688/f1000research.54159.1>

</div>

<div id="ref-Cohen-Boulakia2017-pw">

28\. Sarah Cohen-Boulakia, Khalid Belhajjame, Olivier Collin, Jérôme Chopard, Christine Froidevaux, Alban Gaignard, Konrad Hinsen, Pierre Larmande, Yvan Le Bras, Frédéric Lemoine, Fabien Mareuil, Hervé Ménager, Christophe Pradal, & Christophe Blanchet (2017): Scientific workflows for computational reproducibility in the life sciences: Status, challenges and opportunities. *Future Gener. Comput. Syst.*, **75**. <https://doi.org/https://doi.org/10.1016/j.future.2017.01.012>

</div>

<div id="ref-SoilandReyes2022">

29\. Stian Soiland-Reyes, Genís Bayarri, Pau Andrio, Robin Long, Douglas Lowe, Ania Niewielska, Adam Hospital, & Paul Groth (2022): Making canonical workflow building blocks interoperable across workflow languages. *Data Intelligence*, **4** (2). <https://doi.org/10.1162/dint_a_00135>

</div>

<div id="ref-edam2013">

30\. Jon Ison, Matúš Kalaš, Inge Jonassen, Dan Bolser, Mahmut Uludag, Hamish McWilliam, James Malone, Rodrigo Lopez, Steve Pettifer, & Peter Rice (2013): EDAM: an ontology of bioinformatics operations, types of data and identifiers, topics and formats. *Bioinformatics*, **29** (10). <https://doi.org/10.1093/bioinformatics/btt113>

</div>

<div id="ref-leo2023">

31\. Simone Leo (2023): Run of digital pathology tissue/tumor prediction workflow. <https://doi.org/10.5281/ZENODO.7774351>

</div>

<div id="ref-Khan2019">

32\. Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, & Michael R. Crusoe (2019): Sharing interoperable workflow provenance: A review of best practices and their practical application in cwlprov. *GigaScience*, **8** (11). <https://doi.org/10.1093/gigascience/giz095>

</div>

<div id="ref-Sefton2023">

33\. Peter Sefton, Eoghan Ó Carragáin, Stian Soiland-Reyes, Oscar Corcho, Daniel Garijo, Raul Palma, Frederik Coppens, Carole Goble, José M. Fernández, Kyle Chard, Jose Manuel Gomez-Perez, Michael R. Crusoe, Ignacio Eguinoa, Nick Juty, Kristi Holmes, Jason A. Clark, Salvador Capella-Gutierrez, Alasdair J. G. Gray, Stuart Owen, Alan R. Williams, Giacomo Tartari, Finn Bacall, Thomas Thelen, Hervé Ménager, Laura Rodríguez-Navas, Paul Walk, brandon whitehead, Mark Wilkinson, Paul Groth, Erich Bremer, Leyla Jael Castro, Karl Sebby, Alexander Kanitz, Ana Trisovic, Gavin Kennedy, Mark Graves, Jasper Koehorst, Simone Leo, Marc Portier, Paul Brack, Milan Ojsteršek, Bert Droesbeke, Chenxu Niu, Kosuke Tanabe, Tomasz Miksa, Marco La Rosa, Cedric Decruw, Andreas Czerniak, Jeremy Jay, Sergio Serra, Ronald Siebes, Shaun de Witt, Shady El Damaty, Douglas Lowe, Xuanqi Li, Sveinung Gundersen, & Muhammad Radifar (2023): RO-crate metadata specification 1.1.3. <https://doi.org/10.5281/ZENODO.7867028>

</div>

<div id="ref-openslide2013">

34\. Adam Goode, Benjamin Gilbert, Jan Harkes, Drazen Jukic, & Mahadev Satyanarayanan (2013): OpenSlide: A vendor-neutral software foundation for digital pathology. *Journal of Pathology Informatics*, **4** (1). <https://doi.org/https://doi.org/10.4103/2153-3539.119005>

</div>

<div id="ref-Hoyt2024">

35\. Charles Tapley Hoyt & Benjamin M. Gyori (2024): The o3 guidelines: Open data, open code, and open infrastructure for sustainable curated scientific resources. *Scientific Data*, **11** (1). <https://doi.org/10.1038/s41597-024-03406-w>

</div>

<div id="ref-CrusoeTwitter">

36\. (n.d.): From a chat with @soilandreyes, the idea of ‘inner fair’’, in the spirit of ‘inner source’’.

</div>

<div id="ref-Turilli2019">

37\. Matteo Turilli, Vivek Balasubramanian, Andre Merzky, Ioannis Paraskevakos, & Shantenu Jha (2019): Middleware building blocks for workflow systems. *Computing in Science & Engineering*, **21** (4). <https://doi.org/10.1109/mcse.2019.2920048>

</div>

<div id="ref-Brack2022">

38\. Paul Brack, Peter Crowther, Stian Soiland-Reyes, Stuart Owen, Douglas Lowe, Alan R. Williams, Quentin Groom, Mathias Dillen, Frederik Coppens, Björn Grüning, Ignacio Eguinoa, Philip Ewels, & Carole Goble (2022): Ten simple rules for making a software tool workflow-ready. *PLOS Computational Biology*, **18** (3). <https://doi.org/10.1371/journal.pcbi.1009823>

</div>

<div id="ref-SoilandReyes2022ROcrate">

39\. Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, & Carole Goble (2022): Packaging research artefacts with ro-crate. *Data Science*, **5** (2). <https://doi.org/10.3233/ds-210053>

</div>

<div id="ref-Antypas2021-ph">

40\. K. B. Antypas, D. J. Bard, J. P. Blaschke, R. Shane Canon, Bjoern Enders, Mallikarjun Arjun Shankar, Suhas Somnath, Dale Stansberry, Thomas D. Uram, & Sean R. Wilkinson (2021): **Enabling discovery data science through cross-facility workflows**. In, *2021 IEEE international conference on big data (big data)* (IEEE). <https://doi.org/10.1109/BigData52589.2021.9671421>

</div>

</div>

1.  1
