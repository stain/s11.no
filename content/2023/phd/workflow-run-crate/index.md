---
title: "Recording provenance of workflow runs with RO-Crate"
weight: 54
lang: en-GB
categories:
  - PhD
keywords:
  - workflow
  - provenance
  - RO-Crate
summary: > 
  Preprint submitted to PLOS One
description: > 
    Recording the provenance of scientific computation results is key to the support of traceability, reproducibility and quality assessment of data products. Several data models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, existing approaches tend to lack interoperable adoption across workflow management systems.
    
    In this work we present Workflow Run RO-Crate, an extension of RO-Crate (Research Object Crate) and Schema.org to capture the provenance of the execution of computational workflows at different levels of granularity and bundle together all their associated products (inputs, outputs, code, etc.). The model is supported by a diverse, open community that runs regular meetings, discussing development, maintenance and adoption aspects. Workflow Run RO-Crate is already implemented by several workflow management systems, allowing interoperable comparisons between workflow runs from heterogeneous systems. We describe the model, its alignment to standards such as W3C PROV, and its implementation in six workflow systems. Finally, we illustrate the application of Workflow Run RO-Crate in two use cases of machine learning in the digital image analysis domain.
---

<h2>Cite as</h2>

Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2023):  
**Recording provenance of workflow runs with RO-Crate**.  
_arXiV_:2312.07852  
<https://doi.org/10.48550/arXiv.2312.07852>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown and figure caption formatting; references in s11 house style; URLs as footnotes/hyperlinks; enumerations made explicit; listing captions; some paragraphs split for readability; details moved to footnote, acknowledgement and references moved to separate chapters; fixed minor typos and grammatical errors


# Recording provenance of workflow runs with RO-Crate

_Simone Leo<sup>1</sup>, Michael R. Crusoe<sup>2,3,4</sup>, Laura Rodríguez-Navas<sup>5</sup>, Raül Sirvent<sup>5</sup>, Alexander Kanitz<sup>6,7</sup>, Paul De Geest<sup>8</sup>, Rudolf Wittner<sup>9,10,11</sup>, Luca Pireddu<sup>1</sup>, Daniel Garijo<sup>12</sup>, José M. Fernández<sup>5</sup>, Iacopo Colonnelli<sup>13</sup>, Matej Gallo<sup>9</sup>, Tazro Ohta<sup>14,15</sup>, Hirotaka Suetake<sup>16</sup>, Salvador Capella-Gutierrez<sup>5</sup>, Renske de Wit<sup>2</sup>, Bruno de Paula Kinoshita<sup>5</sup>, Stian Soiland-Reyes<sup>17,18</sup>_

<div class="affiliations">

<sup>1</sup> Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Loc. Piscina Manna, Edificio 1, 09050 Pula (CA), Italy\
<sup>2</sup> Vrije Universiteit Amsterdam, The Netherlands\
<sup>3</sup> DTL Projects, The Netherlands\
<sup>4</sup> Forschungszentrum Jülich, Germany\
<sup>5</sup> Barcelona Supercomputing Center (Spain)\
<sup>6</sup> Biozentrum, University of Basel, Switzerland\
<sup>7</sup> Swiss Institute of Bioinformatics, Lausanne, Switzerland\
<sup>8</sup> VIB-UGent Center for Plant Systems Biology, Gent, Belgium\
<sup>9</sup> Faculty of Informatics, Masaryk University, Botanická 68a, 602 00, Brno, Czech Republic\
<sup>10</sup> Institute of Computer Science, Masaryk University, Šumavská 416/15, 602 00, Brno, Czech Republic\
<sup>11</sup> BBMRI-ERIC, Neue Stiftingtalstrasse 2, 8010, Graz, Austria\
<sup>12</sup> Ontology Engineering Group, Universidad Politécnica de Madrid\
<sup>13</sup> Università degli Studi di Torino, Computer Science Dept. Corso Svizzera 185, 10149, Torino, Italy\
<sup>14</sup> Database Center for Life Science, Joint Support-Center for Data Science Research, Research Organization of Information and Systems, Shizuoka, Japan\
<sup>15</sup> Institute for Advanced Academic Research, Chiba University, Chiba, Japan"\
<sup>16</sup> Department of Creative Informatics, Graduate School of Information Science and Technology, The University of Tokyo, Tokyo, Japan\
<sup>17</sup> Department of Computer Science, The University of Manchester, Manchester, United Kingdom \
<sup>18</sup> Informatics Institute, Faculty of Science, University of Amsterdam, Amsterdam, The Netherlands

</div>

## Abstract

Recording the provenance of scientific computation results is key to the support of traceability, reproducibility and quality assessment of data products. Several data models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, existing approaches tend to lack interoperable adoption across workflow management systems.

In this work we present **Workflow Run RO-Crate**, an extension of RO-Crate (Research Object Crate) and Schema.org to capture the provenance of the execution of computational workflows at different levels of granularity and bundle together all their associated products (inputs, outputs, code, etc.). The model is supported by a diverse, open community that runs regular meetings, discussing development, maintenance and adoption aspects. Workflow Run RO-Crate is already implemented by several workflow management systems, allowing interoperable comparisons between workflow runs from heterogeneous systems. We describe the model, its alignment to standards such as W3C PROV, and its implementation in six workflow systems. Finally, we illustrate the application of Workflow Run RO-Crate in two use cases of machine learning in the digital image analysis domain.


## Introduction {#introduction}

A crucial part of scientific research is recording the provenance of its outputs. The W3C PROV standard defines provenance as "a record that describes the people, institutions, entities, and activities involved in producing, influencing, or delivering a piece of data or a thing" \[[Moreau 2013]\]. Provenance is instrumental to activities such as traceability, reproducibility, accountability, and quality assessment \[[Herschel 2017]\]. The constantly growing size and complexity of scientific datasets and the analysis that is required to extract useful information from them has made science increasingly dependent on advanced automated processing techniques in order to get from experimental data to final results \[[Himanen 2019], [Gauthier 2019], [Huntingford 2019]\]. Consequently, a large part of the provenance information for scientific outputs consists of descriptions of complex computer-aided data processing steps. This data processing is often expressed as workflows, i.e., high-level applications that coordinate multiple tools and manage intermediate outputs in order to produce the final results.

In order to homogenise the collection and interchange of provenance records, the W3C consortium proposed the PROV-O standard \[[Lebo 2013a]\], an OWL \[[W3C 2012]\] representation of PROV for provenance in the Web. PROV-O has been widely extended for workflows (D-PROV \[[Missier 2013]\], ProvONE \[[Cuevas-Vicenttín 2016]\], OPMW \[[Garijo 2011]\], P-PLAN \[[Garijo 2012]\]), where provenance information is collected in two main forms: prospective and retrospective \[[Freire 2008]\]. *Prospective provenance* -- the execution plan -- is essentially the workflow itself: it includes a machine-readable specification with the processing steps to be performed and the data and software dependencies to carry out each computation. *Retrospective provenance* refers to what actually happened during an execution, i.e. what were the values of the input parameters, which outputs were produced, which tools were executed, how much time did the execution take, whether the execution was successful or not, etc. Retrospective provenance can also be represented at different levels of abstraction depending on available computing resources: for instance, by the workflow execution becoming a single activity which produces results, by specifying the individual execution of each workflow step, or by going a step further and indicating how each step is divided into sub-processes when a workflow is deployed in a cluster.

Different workflow systems have adopted and extended PROV (and its PROV-O representation) to the workflow domain (WINGS \[[Gil 2011], [Garijo 2014b]\], VisTrails \[[Scheidegger 2008], [Costa 2013]\]), in order to ease the burden of provenance collection from tool developers to workflow management systems (WMS) \[[Atkinson 2017], [Pérez 2018]\].

D-PROV, PROV-ONE, OPMW-PROV, P-Plan propose representations of workflow plans and their respective executions, taking into account the features of the workflow systems implementing them (e.g., hierarchical representations, sub-processes, etc.). Other data models like *wfprov* and *wfdesc* \[[Belhajjame 2015]\] go a step further by considering not only the link between plans and executions, but how to package the various artefacts as a Research Object (RO)  \[[Bechhofer 2013]\] in order to ease portability while keeping the context of a digital experiment.

However, while these models address some workflow provenance representation issues, they have two main limitations: Firstly, the extensions of PROV are not directly interoperable because of differences in granularity or different assumptions in their workflow representations; secondly, their support from WMS is typically one system per model. An early approach to unify and integrate workflow provenance traces across WMS was WEST (Workflow Ecosystems through STandards) \[[Garijo 2014b]\], through the use of WINGS \[[Gil 2011]\] to build workflow templates and different converters.

In all of these workflow provenance models, the emphasis is on the workflow execution structure as a directed graph, with only partial references for the data items. The REPRODUCE-ME ontology \[[Samuel 2022]\] extended PROV and P-Plan to explain the overall scientific process with the experimental context including real life objects (e.g. instruments, specimens) and human activities (e.g. lab protocols, screening), demonstrating provenance of individual Jupyter Notebook and highlighting the need for provenance also where there is no workflow management system.

More recently, interoperability have been partially addressed by Common Worlflow Language Prov (CWLProv) \[[Khan 2019]\], which represents workflow enactments as ROs serialised according to the Big Data Bag (BDBag) approach \[[Chard 2016]\]. The resulting format is a folder containing several data and metadata files \[[Soiland-Reyes 2018]\], expanding on the RO Bundle approach of Taverna \[[Soiland-Reyes 2016]\]. CWLProv also extends PROV with a representation of executed processes (activities), their inputs and outputs (entities) and their executors (agents), together with their Common Workflow Language specification \[[Crusoe 2022]\] -- a standard workflow specification adopted by at least a dozen different . Although CWLProv includes prospective provenance as a *plan* within PROV (based on the *wfdesc* model), in practice its implementation does not include tool definitions or file formats, as proposed by the wfdesc extension . In order for CWLProv consumers to reconstruct the full prospective provenance for understanding the workflow, they would also need to inspect the separate workflow definition in the native language of the WMS. Additionally, the CWLProv RO may include several other metadata files and PROV serialisations conforming to different formats, complicating its generation and consumption.

As for granularity, CWLProv proposed multiple levels of provenance [@Khan; @2019 figure 2], from Level 0 (capturing workflow definition) to Level 3 (domain-specific annotations). In practice, the CWL reference implementation *cwltool* \[[Amstutz 2023]\] and the corresponding CWLProv specification \[[Soiland-Reyes 2018]\] records provenance details of all task executions together with the intermediate data and any nested workflows (CWLProv level 2), a granularity level that requires substantial support from the WMS. This approach is appropriate for workflow languages where the execution plan, including its distribution among the various tasks, is known well in advance (such as CWL). However, it can be at odds with other systems where the execution is more dynamic, depending on the verification of specific runtime conditions, such as the size and distribution of the data (e.g., COMPSs \[[Lordan 2014]\]).

This makes the implementation of CWLProv challenging, as shown by the fact that at the time of writing the format is supported only by cwltool. Finally, being based on the PROV model, CWLProv is highly focused on the interaction between agents, processes and related entities, while support for contextual metadata (such as workflow authors, licence or creation date) in the Research Object Bundle is and stored in a separate manifest file, that includes the data identifier mapping to filenames. A project that uses serialised ROs similar to those used by CWLProv is Whole Tale \[[Chard 2019]\], a web platform with a focus on the narrative around scientific studies and their reproducibility, where the serialised ROs are used to export data and metadata from the platform. In contrast, our work is primarily focused on the ability to capture the provenance of computational workflow execution including its data and executable workflow definitions.

RO-Crate \[[Soiland-Reyes 2022a]\] is a recent approach to packaging research data together with their metadata; it extends Schema.org \[[Guha 2015]\], a popular vocabulary for describing resources on the Web. In its simplest form, an RO-Crate is a directory structure that contains a single JSON-LD \[[Sporny 2020]\] metadata file at the top level. The metadata file describes all entities stored in the RO-Crate along with their relationships; it is both machine-readable and human-readable. RO-Crate is general enough to be able to describe any dataset, but can also be made as specific as needed through the use of extensions called *profiles*. At the same time, the broad set of types and properties from Schema.org, complemented by a few additional terms from other vocabularies, make the RO-Crate model capable of expressing a wide range of contextual information that complements and enriches the core information specified by the profile. This may include, among others, the workflow authors and their affiliations, associated publications, licensing information, related software, etc. This is an approach used by WorkflowHub \[[Goble 2021]\], a workflow system agnostic workflow registry which specifies a Workflow RO-Crate profile \[[Bacall 2022]\] to gather the workflow definition with such metadata in an archived RO-Crate [^1].

In this work, we present **Workflow Run RO-Crate** (WRROC), an extension of RO-Crate for representing computational workflow execution provenance. Our main contributions are the following:

-   A collection of RO-Crate profiles to represent and package both the prospective and the retrospective provenance of a computational workflow run in a way that is machine-actionable \[[Batista 2022]\], independent of the specific workflow language or execution system, and including support for re-execution.

-   Implementations of the model in six workflow management systems and one conversion tool.

-   A mapping of our profiles against the W3C PROV-O Standard using the Simple Knowledge Organisation System (SKOS) \[[Isaac 2009]\].

To foster usability, the profiles are characterised by different levels of detail, and the set of mandatory metadata items is kept to a minimum in order to ease the implementation. This flexible approach increases the model's adaptability to the diverse landscape of WMS used in practice. The base profile, in particular, is applicable to any kind of computational process, not necessarily described in a formal workflow language. All profiles are supported and sustained by the Workflow Run RO-Crate community, which meets regularly to discuss extensions, issues and new implementations.

The rest of this section is organised as follows: we first describe the Workflow Run RO-Crate profiles; we then illustrate implementations and usage examples; this is followed by a discussion and plans for future work.


## The Workflow Run RO-Crate profiles {#the-workflow-run-ro-crate-profiles}

RO-Crate profiles are extensions of the base RO-Crate specification that describe how to represent the entities and relationships that appear in a specific domain or use case[^2]. An RO-Crate conforming to a profile is not just machine-readable, but also machine-actionable as a digital object whose type is represented by the profile itself \[[Soiland-Reyes 2022c]\].

The Workflow Run RO-Crate profiles are the main outcome of the activities of the Workflow Run RO-Crate , an open working group that includes workflow users and developers, WMS users and developers, and researchers and software engineers interested in workflow execution provenance and Findable, Accessible, Interoperable and Reusable (FAIR) approaches for data and software. In order to develop the Workflow-Run RO-Crate profiles, one of the first community efforts was to compile a list of requirements in the form of competency to be addressed by the model. Each requirement was backed up by a rationale and linked to a GitHub issue to drive the public discussion forward. When a requirement was addressed, related changes were integrated into the profiles and the relevant issue was closed. Many of the original issues are now closed, and the profiles have had four official releases on Zenodo.

As requirements were being defined, it became apparent that one single profile would not have been sufficient to cater for all possible usage scenarios. In particular, while some use cases required a detailed description of all computations orchestrated by the workflow, others were only concerned with a "black box" representation of the workflow and its execution as a whole (i.e., whether the execution was successful and which results were obtained). Additionally, some computations involve a data flow across multiple applications that are executed without the aid of a WMS and thus are not formally described in a standard workflow language. These observations led to the development of three profiles:

(1) to describe the execution of one or more tools that contribute to a computation.

(2) to describe a computation orchestrated by a predefined workflow.

(3) to describe a workflow computation including the internal details of individual step executions.

In the rest of this section we describe each of the above profiles in detail. We use italics to denote the types and properties describing entities and their relationships: these are defined in the RO-Crate JSON-LD , which extends Schema.org with terms from the Bioschemas \[[Gray 2017]\] ComputationalWorkflow and other vocabularies. More specifically, from Bioschemas we use the *ComputationalWorkflow* and *FormalParameter* types as well as the *input* and *output* properties. Note that these terms, though coming from Bioschemas, are not specific to the life sciences. We also developed a context extension through a dedicated "workflow-run" to represent concepts that are not captured by terms in the RO-Crate context.

### Process Run Crate {#process-run-crate}

The Process Run Crate profile \[[WRROC 2023a]\] contains specifications on describing the execution of one or more software applications that contribute to the same overall computation, but are not necessarily coordinated by a top-level workflow or script. For instance, they could be executed manually by a human agent, one after the other as intermediate datasets become available, as shown in the process run from \[[Meurisse 2023]\].

Being the basis for all profiles in the WRROC collection, Process Run Crate specifies how to describe the fundamental entities involved in a computational run: a software application (represented by a *SoftwareApplication*, *SoftwareSourceCode* or *ComputationalWorkflow* entity) and its execution (represented by a *CreateAction* entity), with the latter linking to the former via the *instrument* property. Other important properties of the *CreateAction* entity are *object*, which links to the action's inputs, and *result*, which links to its outputs. The time the execution started and ended can be provided, respectively, via the *startTime* and *endTime* properties. The *Person* or *Organization* entity that performed the action is referred to via the *agent* property. Figure [1](#fig:process_crate_er){reference-type="ref" reference="fig:process_crate_er"} shows the entities used in Process Run Crate together with their relationships.

![**UML class diagram for Process Run Crate.** The central entity is the *CreateAction*, which represents the execution of an application. It relates with the application itself via *instrument*, with the entity that executed it via *agent* and with its inputs and outputs via *object* and *result*, respectively. *File* is an RO-Crate alias for Schema.org's *MediaObject*. Some inputs (and, less commonly, outputs), however, are not stored as files or directories, but passed to the application (e.g., via a command line interface) as values of various types (e.g., a number or string). In this case, the profile recommends a representation via *PropertyValue*. For simplicity, we left out the rest of the RO-Crate structure (e.g. the root *Dataset*). In this UML class notation diamond $\Diamond$ arrows indicate aggregation and regular arrows indicate references, $*$ indicates multiple instances, $1$ means single instance. ](figures/ch54/wrroc-figure1.drawio.pdf){#fig:process_crate_er width="26em"}

As an example, suppose a user called John Doe runs the `head` UNIX command to extract the first ten lines of an input file named `lines.txt`, storing the result in another file called `selection.txt`. John then runs the `sort` command on `selection.txt`, storing the sorted output in a new file named `sorted_selection.txt`. Figure [2](#fig:head_sort){reference-type="ref" reference="fig:head_sort"} contains a diagram of the two actions and their relationships to the other entities involved. Note how the actions are connected by the fact that the output of "Run Head" is also the input of "Run Sort": they form an "implicit workflow", whose steps have been executed manually rather than by a software tool.

![**Diagram of a simple workflow** where the `head` and `sort` programs were run manually by a user. The executions of the individual software programs are connected by the fact that the file output by `head` was used as input for `sort`, documenting the computational flow in an implicit way. Such executions can be represented with Process Run Crate.](figures/ch54/wrroc-figure-example.drawio.pdf){#fig:head_sort width="29em"}

Process Run Crate extends the RO-Crate guidelines on representing software used to create files with additional requirements and conventions. This arrangement is typical of the RO-Crate approach, where the base specification provides general recommendations to allow for high flexibility, while profiles -- being more concerned with the representation of specific domains and machine actionability -- provide more detailed and structured definitions. Nevertheless, in order to be broadly applicable, profiles also need to avoid the specification of too many strict requirements, trying to strike a good trade-off between flexibility and actionability. One of the implications of this approach is that consumers need to code defensively, avoiding unwarranted assumptions -- e.g. by verifying that a value exists for an optional property before trying to retrieve it and use it.

### Workflow Run Crate {#workflow-run-crate}

The Workflow Run Crate profile \[[WRROC 2023b]\] combines the Process Run Crate and WorkflowHub's Workflow RO-Crate \[[Bacall 2022]\] profiles to describe the execution of "proper" computational workflows managed by a WMS. Such workflows are typically written in a special-purpose language, such as CWL or Snakemake \[[Köster 2012]\], and run by one or more WMS (e.g., StreamFlow \[[Colonnelli 2021]\], Galaxy \[[Galaxy 2022]\]). As in Process Run Crate, the execution is described by a *CreateAction* that links to the application via *instrument*, but in this case the application must be a workflow, as prescribed by Workflow RO-Crate. More specifically, Workflow RO-Crate states that the RO-Crate must contain a main workflow typed as *File*, *SoftwareSourceCode* and *ComputationalWorkflow*. The execution of the individual workflow steps, instead, is not represented: that is left to the more detailed Provenance Run Crate profile (described in the next section [1.2.3](#provenance-run-crate){reference-type="ref" reference="provenance-run-crate"}).

The Workflow Run RO-Crate profile also contains recommendations on how to represent the workflow's input and output parameters, based on the aforementioned Bioschemas \[[Gray 2017]\] ComputationalWorkflow profile. All these elements are represented via the *FormalParameter* entity and are referenced from the main workflow via the *input* and *output* properties. While the entities referenced from *object* and *result* in the *CreateAction* represent data entities and argument values that were actually used in the workflow execution, the ones referenced from *input* and *output* correspond to formal parameters, which acquire a value when the workflow is run (see Figure [3](#fig:workflow_crate_er){reference-type="ref" reference="fig:workflow_crate_er"}). In the profile, the relationship between an actual value and the corresponding formal parameter is expressed through the *exampleOfWork* property -- the downloadable file is a realisation of the formal parameter definition. For instance, in the JSON-LD snippet of Listing [\[[formalparameter]\]](#formalparameter){reference-type="ref" reference="formalparameter"} a formal parameter (`#annotations`) is illustrated together with a corresponding `final-annotations.tsv` file:

```json
    {
        "@id": "#annotations",
        "@type": "FormalParameter",
        "additionalType": "File",
        "encodingFormat": "text/tab-separated-values",
        "valueRequired": "True",
        "name": "annotations"
    },
    {
        "@id": "final-annotations.tsv",
        "@type": "File",
        "contentSize": "14784",
        "exampleOfWork": {"@id": "#annotations"}
    }
```

The derivation of Workflow Run Crate from Workflow RO-Crate makes RO-Crates that conform to this profile compatible with the WorkflowHub workflow registry by also conforming to its Workflow RO-Crate profile. Thus, users of a WMS that implements this profile (or Provenance Run Crate, which inherits it) are able to register their workflows in WorkflowHub -- together with an execution trace -- by simply running them and uploading the resulting RO-Crates. Additionally, the inheritance mechanism allows to reuse the specifications already developed for Workflow RO-Crate, which form part of the guidelines on representing the prospective provenance.

Figure [3](#fig:workflow_crate_er){reference-type="ref" reference="fig:workflow_crate_er"} shows the entities used in Workflow Run Crate together with their relationships.

![**UML class diagram for Workflow Run Crate.** The main differences with Process Run Crate are the representation of formal parameters and the fact that the application is expected to be an entity with types *File*, *SoftwareSourceCode* and *ComputationalWorkflow*. Effectively, the entity belongs to all three types, and its properties are the union of the properties of the individual types. The filled diamond $\blacklozenge$ indicates composition, empty diamond $\Diamond$ aggregation, and other arrows relations. ](figures/ch54/wrroc-figure2.drawio.pdf){#fig:workflow_crate_er width="26em"}

### Provenance Run Crate {#provenance-run-crate}

The Provenance Run Crate profile \[[WRROC 2023c]\] extends Workflow Run Crate by adding new concepts to describe the internal details of a workflow run, including individual tool executions, intermediate outputs and related parameters. Individual tool executions are represented by additional *CreateAction* instances that refer to the tool itself via *instrument* -- analogously to its use in Process Run Crate. The workflow is required to refer to the tools it orchestrates through the *hasPart* property, as suggested in the Bioschemas ComputationalWorkflow profile, though in the latter it is only a recommendation.

To represent the logical steps defined by the workflow, this profile uses i.e., "A step in the instructions for how to achieve a result". Steps point to the corresponding tools via the *workExample* property and are referenced from the workflow via the *step* property; the execution of a step is represented by a *ControlAction* pointing to the *HowToStep* via *instrument* and to the *CreateAction* instance(s) that represent the corresponding tool execution(s) via *object*. Note that a step execution does not coincide with a tool execution: an example where this distinction is apparent is when a step maps to multiple executions of the same tool over a list of inputs (e.g. the "scattering" feature in CWL).

An RO-Crate following this profile can also represent the execution of the WMS itself (e.g., cwltool) via *OrganizeAction*, pointing to a representation of the WMS via *instrument*, to the steps via *object* and to the workflow run via *result*. The *object* attribute of the *OrganizeAction* can additionally point to a configuration file containing a description of the settings that affected the behaviour of the WMS during the execution.

Figure [4](#fig:provenance_crate_er){reference-type="ref" reference="fig:provenance_crate_er"} shows the various entities involved in the representation of a workflow run via Provenance Run Crate together with their relationships.

![**UML class diagram for Provenance Run Crate.** In addition to the workflow run, this profile represents the execution of individual steps and their related tools.](figures/ch54/wrroc-figure3.drawio.pdf){#fig:provenance_crate_er width="\\textwidth"}

This profile also includes specifications on how to describe connections between parameters. Parameter connections -- a fundamental feature of computational workflows -- describe (i) how tools take as input the intermediate outputs generated by other tools and (ii) how workflow-level parameters are mapped to tool-level parameters. For instance, consider again the workflow depicted in Figure [2](#fig:head_sort){reference-type="ref" reference="fig:head_sort"}, and suppose it is implemented in a workflow language such as CWL. The workflow-level input (a text file) is connected to the input of the "head" tool wrapper, and the output of the latter is connected to the input of the "sort" tool wrapper.

A representation of parameter connections is particularly useful for traceability, since it allows to document the inputs and tools on which workflow outputs depend. Since the current RO-Crate context has no suitable terms for the description of such relationships, we added appropriate ones to the aforementioned "workflow-run" context extension (the <https://w3id.org/ro/terms/workflow-run#> namespace): a *ParameterConnection* type with *sourceParameter* and *targetParameter* attributes that respectively map to the source and target formal parameters, and a *connection* property to link from the relevant step or workflow to the *ParameterConnection* instances.

This profile is the most detailed of the three, and offers the highest level of granularity. Fig. [5](#fig:profile_venn){reference-type="ref" reference="fig:profile_venn"} shows the relationship between the specifications of the profiles as a Venn diagram.

![**Venn diagram of the specifications for the various RO-Crate profiles.** Workflow Run Crate inherits the specifications of both Process Run Crate and Workflow RO-Crate. Provenance Run Crate, in turn, inherits the specifications of Workflow Run Crate.](figures/ch54/wrroc-venn.drawio.pdf){#fig:profile_venn width="26em"}


## Implementations {#implementations}

Support for the Workflow Run RO-Crate profiles presented in this work has been implemented in a number of systems, showing support from the community and demonstrating their usability in practice. We describe seven of these implementations (one in a conversion tool and six in WMS) in the following sections. These tools have been developed in parallel by different teams, and independently from each other. RO-Crate has a strong ecosystem of tools \[[Soiland-Reyes 2022a]\] (section [\[[tooling]\]](#tooling){reference-type="ref" reference="tooling"}), and the WRROC implementations have either re-used these or added their own approach to the standards.

### Runcrate {#runcrate}

\[[Leo 2023a]\] is a Workflow Run RO-Crate toolkit which also serves as a reference implementation of the proposed profiles. It consists of a Python package with a command line interface, providing a straightforward path to integration in Python software and other workflows. The runcrate toolkit includes functionality to convert CWLProv ROs to RO-Crates conforming to the Provenance Run Crate profile (*runcrate convert*), effectively providing an indirect implementation of the format for cwltool. Indeed, the CWLProv model provided a basis for the Provenance Run Crate profile, and the implementation of a conversion tool in runcrate at times drove the improvement and extension of the profile as new requirements or gaps in the old designs emerged. Runcrate converts both the retrospective provenance part of the CWLProv RO (the RDF graph of the workflow's execution) and the prospective provenance part (the CWL files, including the workflow itself). Both parts are thus converted into a single, workflow language-agnostic metadata resource.

Another functionality offered by the runcrate package is *runcrate report* which reports on the various executions described in an input RO-Crate, listing their starting and ending times, the values of the various parameters, etc. (example output in listing [\[[lst:ml\_pipeline\_streamflow\_report]\]](#lst:ml_pipeline_streamflow_report){reference-type="ref" reference="lst:ml_pipeline_streamflow_report"}). Runcrate report demonstrates how the provenance profiles presented in this work enable comparison of runs interoperably across different workflow languages or different implementations of the same language. This functionality has also been used as a lightweight validator for the various implementations.

We also added a *run* subcommand to re-execute the computation described by an input Workflow Run Crate or Provenance Run Crate where CWL was used as a workflow language. It works by mapping the RO-Crate description of input parameters and their values (the workflow's *input* and the action's *object*) to the format expected by CWL, which is then used to relaunch the workflow on the input data. This functionality shows the machine-actionability of the profiles to support reproducibility, and was used to successfully re-execute the digital pathology annotation workflow described in section [1.4.1](#provenance-run-crate-for-digital-pathology){reference-type="ref" reference="provenance-run-crate-for-digital-pathology"}.

Of course, achieving a full re-execution in the general case may not always be possible: reproducibility is supported by the profiles, but also benefits from the characteristics of the workflow language (which should provide a clear formalism to map input items to their corresponding parameter slots) and from cooperation on the part of the workflow's author, who can help considerably by containerizing the environment required by each step and providing the relevant annotations (if allowed by the workflow language).

### Galaxy {#galaxy}

The Galaxy project \[[Galaxy 2022]\] provides a WMS with data management functionalities as a multi-user platform, aiming to make computational biology more accessible to research scientists that do not have computer programming or systems administration experience. Galaxy's most prominent features include: a collection of 7500+ integrated ; a web interface that allows the execution and definition of workflows using the integrated tools; a network of dedicated (public) Galaxy instances.

The export of workflow execution provenance data as Workflow Run Crates has been added in Galaxy's 23.0 release. This feature provides a more interoperable alternative to the basic export of Galaxy workflow *invocations*: the workflow definition; a set of serialisations of the invocation-related metadata in Galaxy native, json-formatted files; and the input and output data files. This is achieved by extracting provenance from Galaxy entities related to the workflow run, along with associated metadata, converting them to RO-Crate metadata using the ro-crate-py library \[[De Geest 2023a]\]; by describing all files contained in the basic invocation export within the RO-crate metadata; and finally by making the Workflow Run Crate available for export to the user through Galaxy's web interface and API \[[De Geest 2022]\].

We extract the prospective provenance contained in Galaxy's YAML-based workflow definition, which includes details of the analysis pipeline such as the graph of tools that need to be executed, and metadata about the data types required. The retrospective provenance -- i.e., the details of the executed workflow such as the inputs, outputs, parameter values used -- is extracted from Galaxy's data , which is not directly accessible to users in the context of a public Galaxy server. All of this provenance information is then mapped to RO-Crate metadata, including some Galaxy-specific data entities such as dataset collections. An exemplary exported Galaxy Workflow Run Crate is available on Zenodo \[[De Geest 2023b]\].

In practice, a user would take the following steps to obtain a Workflow Run Crate from a Galaxy instance:

(1) Create or download a Galaxy workflow definition (e.g.: from WorkflowHub) and import it in a Galaxy instance, or create a workflow through the Galaxy GUI directly.

(2) Execute the workflow, providing the required inputs.

(3) After the workflow has run successfully, the corresponding RO-Crate will be available for export from the Workflow Invocations list.

### COMPSs {#compss}

COMPSs \[[Lordan 2014]\] is a task-based programming model that allows users to transform a sequential application into a parallel one by simply annotating some of its methods, thus making it efficient to exploit the resources available (either distributed or in a cluster). When a COMPSs application is executed, a corresponding workflow describing the application's tasks and their data dependencies is dynamically generated and used by the COMPSs runtime to orchestrate the execution of the application in the infrastructure. As a WMS, COMPSs stands out for its many advanced features that enable applications to achieve fine-grained high efficiency in HPC systems, such as the ability to exploit underlying parallelisation frameworks (i.e. MPI, OpenMP), compilers (e.g. NUMBA), failure management, task grouping, and more.

Provenance recording for COMPSs workflows has been explored in previous work \[[Sirvent 2022]\], where the Workflow RO-Crate profile was adopted in the implementation of a very lightweight approach to document provenance while avoiding the introduction of any significant run time performance overheads. However, because of the dynamic nature of COMPSs workflows, the Workflow Run Crate profile is better suited to represent them, since workflows are created when the application is executed and, thus, a prior static workflow definition does not exist before that moment. Due to this limitation, the workflow entity in the metadata file references the entry point application run by COMPSs, and formal parameters are not listed (note that listing them is not required by the profile) because inputs and outputs (both for each task and the whole workflow) are determined at runtime. COMPSs is able to export provenance data with a post-processing operation that can be triggered at any moment after the application has finished. The RO-Crate generation post-process uses information recorded by the runtime to detect and automatically add metadata of any input or output data assets used by the workflow.

Implementing Workflow Run Crate support in COMPSs required particular attention to the generation of a unique id for the *CreateAction* representing the workflow run, combining hostname and queuing system job id for supercomputer executions (as extra information added), and just using generated UUIDs for distributed environments, to add as much information as available from the run while ensuring the id is unique. In the *CreateAction*, the *description* term includes system information, as well as relevant environment variables that provide details on the execution environment (e.g., node list, CPUs per node). Finally, the *subjectOf* property of the *CreateAction* references the system's monitoring tool (when available), where authorised users can see detailed profiling of the corresponding job execution, as provided by the MareNostrum IV .

To showcase the COMPSs adoption of the Workflow Run Crate profile, we provide as an example the execution of the BackTrackBB \[[Poiata 2016]\] application in the MareNostrum IV supercomputer. BackTrackBB targets the detection and location of seismic sources using the statistical coherence of the wave field recorded by seismic networks and antennas. The resulting RO-Crate \[[Poiata 2023]\] complies with the Workflow Run Crate profile, and includes the application source files, a diagram of the workflow's graph, application profiling and input and output files.

The implementation of provenance recording following Workflow Run Crate has been fully integrated in the COMPSs runtime, and is available since \[[Ejarque 2023]\].

### StreamFlow {#streamflow}

The framework \[[Colonnelli 2021]\] is a container-native WMS based on the CWL standard. It has been designed around two primary principles: first, it allows the execution of tasks in multi-container environments, supporting the concurrent execution of communicating tasks in a multi-agent ecosystem; second, it relaxes the requirement of a single shared data space, allowing for hybrid workflow executions on top of multi-cloud, hybrid cloud/HPC, and federated infrastructures. StreamFlow orchestrates hybrid workflows by combining a *workflow description* (e.g., a CWL workflow description and a set of input values) with one or more *deployment descriptions* -- i.e. representations of the execution environments in terms of infrastructure-as-code (e.g., Docker Compose files \[[Reis 2022]\], HPC batch scripts, and Helm charts \[[Zerouali 2023]\]). A `streamflow.yml` file -- the entry point of each StreamFlow execution -- binds each workflow step with the set of most suitable execution environments. At execution time, StreamFlow automatically takes care of all the secondary aspects, like scheduling, checkpointing, fault tolerance, and data movements.

StreamFlow stores prospective and retrospective provenance data in a proprietary format into a persistent pluggable database (using sqlite3 as the default choice). After a CWL workflow execution completes, users can generate an RO-Crate through the `streamflow prov <workflow_name>` command, which extracts the provenance data stored in the database for one or more workflow executions and converts it to an RO-Crate archive that is fully compliant with the Provenance Run Crate Profile, including the details of each task run by the WMS. Support for the format has been integrated into the main development branch and will be included in release 0.2.0 \[[Colonnelli 2023b]\].

From the StreamFlow point of view, the main limitation in the actual version of the Provenance Run Crate standard is the lack of support for distributed provenance, i.e., a standard way to describe the set of locations involved in a workflow execution and their topology. As a temporary solution, the StreamFlow configuration and a description of the hybrid execution environment are preserved by directly including the `streamflow.yml` file into the generated archive. However, this product-specific solution prevents a wider adoption from other WMS and forces agnostic frameworks (e.g., WorkflowHub) to provide ad-hoc plugins to interpret the StreamFlow format. Since the support for hybrid and cross-facility workflows is gaining traction in the WMS ecosystem, we envision support for distributed provenance as a feature for future versions of Workflow Run RO-Crate.

### WfExS-backend {#wfexs}

is a FAIR workflow execution orchestrator that aims to address some of the difficulties found in analysis reproducibility and analysis of sensitive data in a secure manner. WfExS-backend requires that the software used by workflow steps is available in publicly available software containers for reproducibility. Actual workflow execution is delegated to one of the supported workflow engines which matches with the workflow, right now either Nextflow or cwltool. The orchestrator prepares and stages all the elements needed to run the workflow -- i.e. all the files of the workflow itself, the specific version of the workflow engine, the required software containers and the inputs. All these elements are referred through resolvable identifiers, ideally public, permanent ones. Due to this, the orchestrator can consume workflows which are originally available in different kinds of locations, like git repositories, Software Heritage, or even RO-Crates from WorkflowHub.

WfExS-backend development milestones aim to reach FAIR workflow execution through the generation and consumption of RO-Crates following the latest Workflow Run Crate profiles, which have proven to be a mechanism suitable to semantically describe digital objects in a way that simplifies embedding key details involved in analysis reproducibility and replicability.

The orchestrator records details relevant to the prospective provenance when a workflow is prepared for execution, such as the public URLs used to fetch input data and workflows, content digestion fingerprints (typically sha256 checksums) and metadata derived from workflow files, container images and input files. Most of this metadata is represented in the generated RO-Crates. WfExS-backend has explicit commands to generate and publish both prospective and retrospective provenance RO-Crates based on a given existing staged execution scenario. These RO-Crates can selectively include copies of used elements as payloads. Workflows can be executed more than once in the same staged directory, with all the executions sharing the same inputs. Thus, run details from all the executions are represented in the retrospective provenance RO-Crate. Support for Workflow Run RO-Crate is available since WfExS-backend version 0.10.1 \[[Fernández 2023a]\]. Future developments will also add support for embedding URLs of output results that have been deposited into a suitable repository (like Zenodo DOIs, for instance) as well as consuming previously produced RO-Crates.

An example of Workflow Run Crate generated by WfExS-backend from a Nextflow workflow run \[[Bouyssié 2023]\] is available from Zenodo \[[Fernández 2023b]\].

### Sapporo {#sapporo}

Sapporo \[[Suetake 2022]\] is an implementation of the Workflow Execution Service (WES) API . WES is a standard proposed by the Global Alliance for Genomics and Health (GA4GH) for cloud-based data analysis platforms that receive requests to execute workflows. Sapporo supports the execution of several workflow engines, including cwltool \[[Amstutz 2023]\], Toil \[[Vivian 2017]\], and StreamFlow \[[Colonnelli 2021]\]. Sapporo includes features specifically tailored to bioinformatics applications, including the calculation of feature statistics from specific types of outputs generated by workflow runs. For example, the system calculates the mapping rate of DNA sequence alignments from BAM format files. To describe the feature values, Sapporo uses the Workflow Run Crate profile extended with additional terms to represent these biological .

Further, the Tonkaz companion command line software has integrated functionality to compare Run Crates generated by Sapporo to measure the reproducibility of the workflow outputs \[[Suetake 2023a]\]. Developers can use this unique feature to build a CI/CD platform for their workflows to ensure that changes to the product do not produce an unexpected result. Workflow users can also use this feature to verify the results from the same workflow deployed in different environments.

While Sapporo supports Workflow Run Crate, since WES is a WMS wrapper, it does not parse the provided workflow definition files. Instead, it embeds the information in the files passed by the WES request to record the provenance of execution rather than using the actual workflow parameters meant for the wrapped WMS. Therefore, the current implementation of Sapporo does not capture the connections between the inputs/outputs depicted in the workflow and the actual files used/generated during the run. Thus, the profile generated by Sapporo has fields representing input and output files, but they are not linked to formal parameters.

Sapporo supports export to Workflow Run Crate since release 1.5.1 \[[Suetake 2023b]\]. An example of RO-Crate generated by Sapporo is available on Zenodo \[[Ohta 2023]\].

### Autosubmit {#autosubmit}

Autosubmit \[[Manubens-Gil 2016]\] is an open source lightweight workflow manager and meta-scheduler created in 2011 for use in climate research to configure and run scientific experiments. It supports scheduling jobs via SSH to Slurm \[[Yoo 2003]\], PBS \[[Feng 2007]\] and other remote batch servers used in HPC.

The "archive" feature was added in , released in 2015. This feature archives the experiment directory and all its contents into a ZIP file, which can be used later to access the provenance data or to execute the Autosubmit experiment again. Even though the data in the ZIP file includes prospective provenance and retrospective provenance, it contains no structure, and users have no way to tell which is which from just looking at the ZIP file and its contents.

Recent releases of Autosubmit 4 include an updated YAML configuration management system that allows users to combine multiple YAML files into a single unified configuration file. While this gave users flexibility, it also increased the complexity to track the configuration changes and to relate these to the provenance data. Another feature added in Autosubmit 4 is the option to use only the experiment manager features of Autosubmit, delegating the workflow execution to a different backend workflow engine, like ecFlow \[[Bahra 2011]\], Cylc \[[Oliver 2019]\], or a CWL runner.

In order to give users a more structured way to archive provenance, which includes the complete experiment configuration and the parameters used to generate the unified experiment configuration, and also to allow interoperability between workflow managers, the archive feature received a new flag in Autosubmit 4.0.100 \[[Beltrán 2023]\] to generate Workflow Run RO-Crates.

The prospective provenance data is extracted from the Autosubmit experiment configuration. This includes the multiple YAML files, and the unified YAML configuration, as well as the parameters used to preprocess each file -- preprocessing replaces placeholders in script templates with values from the experiment configuration. The retrospective provenance data is included with the RO-Crate archive and includes logs and other traces produced by the experiment workflow. Both prospective and retrospective provenance data are included in the final RO-Crate JSON-LD metadata file. Autosubmit uses the Workflow Run RO-Crate profile.

As one of the most recent implementations, much of the code added in Autosubmit 4 for RO-Crates was adapted from existing implementations like COMPSs and StreamFlow. ro-crate-py \[[De Geest 2023a]\] was used for the heavy lifting work of creating the RO-Crate archive in Python, and adding information for the JSON-LD metadata.

The main challenges for adopting RO-Crate in Autosubmit were incorporating Autosubmit's "Project" feature, and the lack of validation tools and of documentation and examples on how to use the standard with *coarse-grained* workflow management systems (as described in \[[Goble 2020]\]) that do not track inputs and outputs, which is the case of Autosubmit -- as well as the Cylc and ecFlow workflow engines.

A Project in Autosubmit is an abstract concept that has a type and a location, and is used to separate experiment configuration and template scripts and other auxiliary files The type can be Git, Subversion, or Local. For each type the location represents the URL of a code repository, or a directory on a workstation or HPC file system used to copy the Project and its template scripts (written in Shell, R, or Python) and any other files (input data for a model, extra configuration files, binaries, etc.). The workflows in Autosubmit have tasks with dependencies to other tasks, and each of these tasks execute one of these template scripts. The RO-Crate file generated by Autosubmit includes only the project type and location, and not the complete Project. Therefore, users have the provenance of the Project, but only those with the correct permissions can access its constituent resources (many applications run with Autosubmit can not be publicly shared without consent).

Validation tools for RO-Crate archives are still under development, and while there is a community-based review process to help and guide new implementations, a tool that others can use as code is written will contribute to a more agile development.

After working with the RO-Crate community on these issues, the Autosubmit team adopted a mixed approach where Autosubmit initialises the JSON-LD metadata from its configuration and local trace files, and the user is responsible for providing a partial JSON-LD metadata object in the Autosubmit YAML configuration. A pull request was created to ro-crate-py to allow the RO-Crate JSON-LD metadata to be patched by these partial JSON-LD metadata objects. This way, users are able to provide the missing information from the Autosubmit configuration model, like licence, authors, inputs, outputs, formal parameters, and more. And by modifying ro-crate-py, future implementers of RO-Crate that have a similar workflow configuration as Autosubmit should be able to re-use it, while also using COMPSs, StreamFlow, Autosubmit, and other implementations as reference.

A workflow was created using an example Autosubmit Project \[[Kinoshita 2023]\] designed using UFZ's mHM (mesoscale Hydrological Model) \[[Samaniego 2010], [Kumar 2013]\]. This workflow was used to validate the RO-Crate produced by Autosubmit. This validation was performed by the Workflow Run RO-Crate community in a public GitHub and also using the aforementioned Runcrate.

### Summary of implementations

Table [1](#implementation_summary_table){reference-type="ref" reference="implementation_summary_table"} shows an overview of the different implementations presented in this section.

::: {#implementation_summary_table}
  **Impl.**    **Profile**   **Version URL/DOI**    **Example**
  ------------ ------------- ---------------------- ----------------------
  runcrate     Provenance    \[[Leo 2023a]\]          \[[Leo 2023]\]
  Galaxy       Workflow      \[[Afgan 2023]\]         \[[De Geest 2023b]\]
  COMPSs       Workflow      \[[Ejarque 2023]\]       \[[Poiata 2023]\]
  Streamflow   Provenance    \[[Colonnelli 2023b]\]   \[[Colonnelli 2023a]\]
  WfExS        Workflow      \[[Fernández 2023a]\]    \[[Fernández 2023b]\]
  Sapporo      Workflow      \[[Suetake 2023b]\]      \[[Ohta 2023]\]
  Autosubmit   Workflow      \[[Beltrán 2023]\]       \[[Kinoshita 2023]\]

  : **Workflow Run Crate implementations**. Summary of each WRROC implementation, together with the profiles it implements, the latest software citation and an example crate of its application. Runcrate is a toolkit that converts CWLProv ROs to Provenance Run Crates, while the others are WMS.
:::


## Exemplary Use Cases {#exemplary-use-cases}

We illustrate Workflow Run RO-Crate on two exemplary use cases, which are similar in terms of application domain -- machine learning-aided tumour detection in human prostate images -- but quite different in the way computations are executed and provenance is represented: in the first, the analysis is conducted by means of a CWL workflow and the outcome is represented with Provenance Run Crate; in the second, a combination of Process Run Crate and CPM RO-Crate is used to represent a sequence of computations linked to their corresponding CPM provenance information.

### Provenance Run Crate for Digital Pathology {#provenance-run-crate-for-digital-pathology}

We present a use case that demonstrates the effectiveness of our most detailed profile Provenance Run Crate at recording provenance data in the context of digital pathology. More specifically, we demonstrate the generation of RO-Crates to save provenance data associated with the computational annotation of magnified prostate tissue areas and cancer subregions using deep learning models \[[Del Rio 2022]\]. The image annotation process is implemented in a CWL workflow consisting of three steps, each executing inference on an image using a deep learning model: inference of a low-resolution tissue mask to select areas for further processing; high-resolution tissue inference on areas identified in the previous step to refine borders; high-resolution cancer identification on areas identified in the first step. The two tissue inference steps run the same tool, but set different values for the parameter that controls the magnification level. The workflow is integrated in the , a web-based platform to support clinical studies involving the examination and/or the annotation of digital pathology images.

To assess the interoperability of WRROC, we recorded the provenance of the same exemplary workflow in two different execution platforms. In the first case, the workflow was executed with the StreamFlow WMS, for which the Provenance Run Crate implementation is discussed in Section [1.3.4](#streamflow){reference-type="ref" reference="streamflow"}. In the second case, we executed the CWL workflow with cwltool and converted the resulting CWLProv RO to a Provenance Run Crate with the runcrate tool (Section [1.3.1](#runcrate){reference-type="ref" reference="runcrate"}).

The RO-Crates obtained in the two cases \[[Colonnelli 2023a], [Leo 2023]\] are very similar to each other, differing only in a few details: for instance, \[[Colonnelli 2023a]\] includes the StreamFlow configuration file and has separate files for the workflow and the two tools, while \[[Leo 2023]\] has the workflow and the tools stored in a single file (CWL's "packed" format). Apart from these minor differences, the description of the computation is essentially the same.

Four actions are represented: the workflow itself, the two executions of the tissue extraction tool and the execution of the tumour classification tool. Each action is linked to the corresponding workflow or tool via the *instrument* property, and reports its starting and ending time. For each action, input and output slots are referenced by the workflow, while the corresponding values are referenced by the action itself. The data entities and *PropertyValue* instances corresponding to the input and output values link to the corresponding parameter slots via the *exampleOfWork* property, providing information on the values taken by the parameters.

Listing [\[[lst:ml\_pipeline\_streamflow\_report]\]](#lst:ml_pipeline_streamflow_report){reference-type="ref" reference="lst:ml_pipeline_streamflow_report"} shows the output of the `runcrate report` command for the StreamFlow RO-Crate. For each action (workflow or tool run), the tool reports the associated instrument (workflow or tool), the starting and ending time and the list of inputs and outputs, with arrows pointing from the formal parameter to the corresponding actual value taken during the execution of the action.

    action: #30a65cba-1b75-47dc-ad47-1d33819cf156
      instrument: predictions.cwl (['SoftwareSourceCode', 
             'ComputationalWorkflow', 'HowTo', 'File'])
      started: 2023-05-09T05:10:53.937305+00:00
      ended: 2023-05-09T05:11:07.521396+00:00
      inputs:
        #af0253d688f3409a2c6d24bf6b35df7c4e271292 <- predictions.cwl#slide
        tissue_low <- predictions.cwl#tissue-low-label
        9 <- predictions.cwl#tissue-low-level
        tissue_low>0.9 <- predictions.cwl#tissue-high-filter
        tissue_high <- predictions.cwl#tissue-high-label
        4 <- predictions.cwl#tissue-high-level
        tissue_low>0.99 <- predictions.cwl#tumor-filter
        tumor <- predictions.cwl#tumor-label
        1 <- predictions.cwl#tumor-level
      outputs:
        06133ec5f8973ec3cc5281e5df56421c3228c221 <- predictions.cwl#tissue
        4fd6110ee3c544182027f82ffe84b5ae7db5fb81 <- predictions.cwl#tumor
    action: #457c80d0-75e8-46d6-bada-b3fe82ea0ef1
      step: predictions.cwl#extract-tissue-low
      instrument: extract_tissue.cwl (['SoftwareApplication', 'File'])
      started: 2023-05-09T05:10:55.236742+00:00
      ended: 2023-05-09T05:10:55.910025+00:00
      inputs:
        tissue_low <- extract_tissue.cwl#label
        9 <- extract_tissue.cwl#level
        #af0253d688f3409a2c6d24bf6b35df7c4e271292 <- extract_tissue.cwl#src
      outputs:
        6b15de40dd0ee3234062d0f261c77575a60de0f2 <- extract_tissue.cwl#tissue
    action: #d09a8355-1a14-4ea4-b00b-122e010e5cc9
      step: predictions.cwl#extract-tissue-high
      instrument: extract_tissue.cwl (['SoftwareApplication', 'File'])
      started: 2023-05-09T05:10:58.417760+00:00
      ended: 2023-05-09T05:11:03.153912+00:00
      inputs:
        tissue_low>0.9 <- extract_tissue.cwl#filter
        6b15de40dd0ee3234062d0f261c77575a60de0f2 <- extract_tissue.cwl#filter_slide
        tissue_high <- extract_tissue.cwl#label
        4 <- extract_tissue.cwl#level
        #af0253d688f3409a2c6d24bf6b35df7c4e271292 <- extract_tissue.cwl#src
      outputs:
        06133ec5f8973ec3cc5281e5df56421c3228c221 <- extract_tissue.cwl#tissue
    action: #ae2163a8-1a2a-4d78-9c81-caad76a72e47
      step: predictions.cwl#classify-tumor
      instrument: classify_tumor.cwl (['SoftwareApplication', 'File'])
      started: 2023-05-09T05:10:58.420654+00:00
      ended: 2023-05-09T05:11:06.708344+00:00
      inputs:
        tissue_low>0.99 <- classify_tumor.cwl#filter
        6b15de40dd0ee3234062d0f261c77575a60de0f2 <- classify_tumor.cwl#filter_slide
        tumor <- classify_tumor.cwl#label
        1 <- classify_tumor.cwl#level
        #af0253d688f3409a2c6d24bf6b35df7c4e271292 <- classify_tumor.cwl#src
      outputs:
        4fd6110ee3c544182027f82ffe84b5ae7db5fb81 <- classify_tumor.cwl#tumor

The *exampleOfWork* link between input / output values and parameter slots is used by `runcrate run` to reconstruct the CWL input parameters document needed to rerun the computation. The *alternateName* property (a Schema.org property applicable to all entities), which records the original name of data entities (at the time the computation was run), is also crucial for reproducibility in this case: both StreamFlow and CWLProv, to avoid clashes, record input and output files and directories using their SHA1 checksum as their names. However, this particular workflow expects the input dataset to be in the format, where the "main" file taken as an input parameter by the processing application must be accompanied by a directory in the same location with the same name apart from the extension. The runcrate tool uses the *alternateName* to rename the input dataset as required, so that the expected pattern can be picked up by the workflow during the re-execution. This use case was the main motivation to include a recommendation to use *alternateName* with the above semantics in Process Run Crate.

Thanks to the fact that both RO-Crates were generated following the best practices to support reproducibility mentioned in the profiles, we were able to re-execute both computations with the runcrate tool. This was also made possible by the fact that the CWL workflow included information on which container images to use for each tool. Overall, this shows how reproducibility is a hard-to-achieve goal that can only be supported, but not ensured, by the profiles, since it also depends on factors like the characteristics of the computation, the choice of workflow language and whether best practices such as containerisation are followed.

This use case highlighted the need to add specifications on how to represent multi-file datasets [@WRROC; @2023a section Representing multi-file objects]. In the MIRAX format, in fact, the "main" file must be accompanied by a directory in the same location containing additional files with a specific structure. To represent this, we added specifications to the Process Run Crate profile on consisting of multiple files and directories to be treated as a single unit -- as opposed to more conventional input or output parameters consisting of a single file. The profile specifies that such datasets should be represented by a *Collection* entity linking to individual files and directories via the *hasPart* property, and referencing the main part (if any) via the *mainEntity* property. Note that, by adding this specification to Process Run Crate, we also made it available to Workflow Run Crate and Provenance Run Crate. In the output of the runcrate report tool the additional files are not shown, since the formal parameter points to the *Collection* entity that describes the whole dataset.

### Process Run Crate and CPM RO-Crate for cancer detection {#process-run-crate-and-cpm-ro-crate-for-cancer-detection}

This section presents an RO-Crate created to describe an execution of a computational pipeline that trains AI models to detect the presence of carcinoma cells in high-resolution digital images of magnified human prostate tissue. The RO-Crate makes use of Process Run Crate and CPM RO-, an RO-Crate profile that supports the representation of entities described according to the Common Provenance Model (CPM) \[[Wittner 2022], [Wittner 2023b]\].

The CPM, an extension of the W3C PROV model \[[Moreau 2013]\] is a recently developed provenance model that enables the representation of distributed provenance. Distributed provenance is created when an object involved in the research process, either digital or physical (e.g., biological material), is exchanged between organisations, so that each organisation can document only a portion of the object's life cycle. Individual provenance components are generated, stored, and managed individually by each organisation, and are linked together in a chain. The CPM prescribes how to represent such provenance, and how to enable its traversal and processing using a common algorithm, independently from the type of object being described. In addition, the CPM defines a notion of meta-provenance, which contains metadata about the history of individual provenance components.

CPM RO-Crate supports the identification of CPM-based provenance and meta-provenance files within an RO-Crate, allowing to pack data, metadata, and CPM-based provenance information together. An RO-Crate generated according to the CPM-RO-Crate profile embeds parts of the distributed provenance, which may be linked to the provenance of precursors and successors of the packed data.

The CPM-RO-Crate profile synergises well with Process Run Crate, since the former can add references to CPM-based provenance descriptions of computational executions described with the latter, integrating them in the distributed provenance. Since CPM-based provenance and meta-provenance files are typically themselves produced by computations, Process Run Crate allows to represent these along with the main computations that produce the datasets being exchanged, providing the full picture in a cohesive ensemble.

The pipeline consists of three main computational steps: a preprocessing step that splits input images into small patches and divides them into a training and a testing set; a training step that trains the model to recognise the presence of carcinoma cells in the images; an evaluation step that measures the accuracy of the trained model on the testing set. In addition to the pipeline steps, the RO-Crate describes additional computations related to the generation of the CPM provenance and meta-provenance files. All computations are described according to the Process Run Crate profile, while the CPM files are referenced according to the CPM RO-Crate profile.

Also represented via Process Run Crate are: the input dataset; the results of the pipeline execution; the scripts that implement the pipeline; the log files generated by the scripts; a script that converts the logs into the CPM files. This allowed us to describe all involved elements as a single aggregate, with entities and their relationships represented according to the RO-Crate model. The RO-Crate discussed here is available from Zenodo \[[Wittner 2023c]\].

The CPM files complement the RO-Crate with internal details about the pipeline execution, such as how the input dataset was split into training and testing sets, or detailed information about each training iteration of the AI model. For instance, it contains a representation of a checkpoint of the AI model after the second training iteration. The corresponding entity's attributes contain paths to the respective model stored as a file. The entity is related to the respective training iteration activity, which contains the iteration parameters represented as an attribute list.

In addition, the CPM generally provides means to link the input dataset provenance to the provenance of its precursors -- human prostate tissues and biological samples the tissues were derived from; this is not included in the example because we used a publicly available input database for which provenance of the precursors was not available. However, the linking mechanism for provenance precursors is exactly the same as between the bundles for the AI pipeline parts.

While the RO-Crate is focused on the execution of the pipeline, the provenance included in the CPM files intends to be interlinked with provenance of the precursors or successors, providing means to traverse the whole provenance chain. For the described digital pathology pipeline, the precursors would be:

1. A biological sample acquired from a patient.
2. Slices of the sample processed and put on glass slides.
3. The images created as a result of scanning the slides using a microscope.

As a result, combining the CPM and RO-Crate enables the lookup of research artefacts related to the computation across heterogeneous organisations using the underlying provenance chain.

## Discussion {#discussion}

The RO-Crate profiles presented here provide a unified data model to describe the prospective and retrospective provenance of the execution of a computational workflow, together with contextual metadata about the workflow itself and its associated entities (inputs, outputs, code, etc.). The profiles are flexible, allowing to tailor the description to a broad variety of use cases, agnostic with respect to the WMS used and allow describing provenance traces at different levels of granularity. This facilitates developing implementations by multiple workflow systems (often with heterogeneous assumptions and requirements) -- six of which have already been developed and are described in Section [1.3](#implementations){reference-type="ref" reference="implementations"} -- allowing to perform comparisons between runs across heterogeneous systems. For instance, the query in listing [\[[sparql]\]](#sparql){reference-type="ref" reference="sparql"} returns all actions in a Workflow Run RO-Crate, together with their instruments and their starting and ending times:

```sql
    PREFIX schema: <http://schema.org/>
    SELECT ?action ?instrument ?start ?end
    WHERE {
      ?action a schema:CreateAction .
      ?action schema:instrument ?instrument .
      OPTIONAL { ?action schema:startTime ?start } .
      OPTIONAL { ?action schema:endTime ?end }
    }
```

Additionally, having workflow runs and plans described according to the RO-Crate model allows capturing the context of the workflow itself (e.g. authors, related publications, other workflows, etc.) rather than the trace alone. Being based on RO-Crate, the profiles and their implementations are part of a growing of tools and services maintained by the RO-Crate community.

Another advantage of RO-Crate is that the files corresponding to the data entities (inputs, outputs, code, etc.) do not necessarily have to be stored together with the metadata file: for instance, they can be remote and referred to via an http(s) URI. This is mostly relevant in situations where the file is very large or cannot be shared publicly: the data entity's identifier can be a URI that is accessible only through authentication, or resolvable only within the boundaries of the generating organisation.

The derivation of Workflow Run Crate from Workflow RO-Crate and, in turn, of Provenance Run Crate from Workflow Run Crate makes RO-Crates that conform to these profiles compatible with the WorkflowHub workflow registry, allowing workflow runs to be registered and easily found and shared with other researchers. Additionally, the inheritance mechanism allows reusing the specifications already developed for Workflow RO-Crate, which form part of the guidelines on representing the prospective provenance

The Workflows Community Summit \[[Ferreira da Silva]\] identified as one of the current open challenges in the Scientific Workflows domain the ability to build FAIR into Workflow Management Systems, with the objective of achieving FAIR Computational Workflows. The profiles introduced in this article are able to help tackle this by introducing interoperable metadata among WMSs that captures the provenance of their corresponding workflow executions.

The Workflow Run RO-Crate profiles, the associated tooling, the implementations and the examples are developed by a community that runs regular virtual meetings (every two weeks at the time of writing) and coordinates on Slack and the RO-Crate mailing list. The WRROC community brings together members of the RO-Crate community \[[Soiland-Reyes 2022a]\], WMS users and developers, Workflow users and developers, GA4GH \[[Rehm 2021]\] Cloud developers and provenance model authors, and is open to anyone who is interested in the representation of workflow provenance. The inclusion of WMS developers and workflow users was key to keeping the specifications flexible, easy to implement and grounded on real use cases, while the diversity of the stakeholders allowed to keep a plurality of viewpoints while driving the model's development forward.

One of the main benefits of this development process is that the profiles are already in use, with seven implementations (six WMS and one conversion tool) already available as described in section [1.3](#implementations){reference-type="ref" reference="implementations"}.

In the following subsections, we provide an evaluation of the metadata coverage of runcrate and we discuss WRROC relates to standards such as W3C PROV and to other community projects.

### Evaluation of metadata coverage using runcrate convert

In order to assess the metadata coverage of *Leo 2023a* (section [1.3.1](#runcrate){reference-type="ref" reference="runcrate"}), we performed a qualitative analysis of the tool's *convert* mode, in which we evaluated how the generated RO-Crates preserve the metadata contained in the CWLProv ROs from which they are derived. For this analysis, we followed the same approach as for an earlier evaluation of CWLProv \[[de Wit 2022]\]. In that work, we identified and analysed three levels of representation: firstly, in RDF; secondly, in a structured, but CWL-specific document; and finally, in an unstructured, human-readable format. 

From this earlier analysis, we concluded that the CWLProv RDF representation of the workflow runs lacked many provenance metadata that was included in CWL-specific documents, such as the packed workflow and input parameter file. For example, the CWLProv RDF only contained the name of each workflow step, without including the link to the underlying CommandLineTool or nested Workflow that was executed; information that could be extracted from the packed workflow.

In our analysis of runcrate, we compared the CWLProv RDF provenance graph with the RO-Crate metadata file. The results of the analysis are summarised in Table [2](#analysis_table){reference-type="ref" reference="analysis_table"} [^3]. Overall, most of the information contained in CWLProv RDF is transferred to the RO-Crate metadata. In addition, the representation of some categories of metadata has improved, notably Workflow parameters (WF2), which were insufficiently described in CWLProv RDF but defined with type and format in RO-Crate. Moreover, the format of input files (D2), which was partially represented in CWLProv RDF, is fully represented in RO-Crate.

::: {#analysis_table}

| Type | Subtype | Name                      | CWL | CWLProv | RO-Crate | WRROC | 
| ---: | ------- | ------------------------- | :-: | :-----: | :------: | :---: | 
|   T1 | SC1     | Workflow design           |  •  |   ·     |   ◦      |   …   |
|      | SC2     | Entity annotations        |  ·  |   ·     |   ·      |   …   |
|      | SC3     | Workflow execution ann.   |  ·  |   ·     |   ·      |   …   |
|   T2 | D1      | Data identification       |  ◦  |   ·     |   ·      |   …   |
|      | D2      |  File characteristics     |  ◦  |   ◦     |   •      |   ◦   |
|      | D3      |  Data access              |  ◦  |   ·     |   ·      |   …   | 
|      | D4      |  Parameter mapping        |  •  |   •     |   •      |   •   |
|   T3 | SW1     | Software identification   |  ◦  |   ·     |   ◦      |   …   |
|      | SW2     | Software documentation    |  ·  |   ·     |   ·      |   …   |
|      | SW3     | Software access           |  ·  |   ·     |   ·      |   …   |
|   T4 | WF1     | Workflow software         |  •  |   ◦     |   ◦      |   …   |
|      | WF2     | Workflow parameters       |  •  |   ◦     |   •      |   •   |
|      | WF3     | Workflow requirements     |  •  |   ·     |   ◦      |   ◦   |  
|   T5 | ENV1    | Software environment      |  ·  |   ·     |   ·      |   ·   |  
|      | ENV2    | Hardware environment      |  ·  |   ·     |   ·      |   ·   | 
|      | ENV3    | Container image           |  ◦  |   ◦     |   ◦      |   •   |
|   T6 | EX1     |  Execution timestamps     |  ·  |   •     |   •      |   •   |
|      | EX2     |  Consumed resources       |  ·  |   ·     |   ·      |   ·   |  
|      | EX3     |  Workflow engine          |  ·  |   ◦     |   ◦      |   ◦   | 
|      | EX4     |  Human agent              |  ·  |   •     |   •      |   •   |
 
  : Summarised results of our qualitative analysis of runcrate
:::

We compared RO-Crates with the CWLProv ROs from which they were generated. The analysis was based on a provenance taxonomy reflecting relevant provenance metadata based on realistic use cases for ROs associated with a real-life bioinformatics workflow \[[de Wit 2022]\]. CWL-specific documents are: `packed.cwl` (the workflow), `primary-job.json` (the inputs file), and `primary-output.json` (the outputs file). Since `packed.cwl` is also included in RO-Crate, we only considered how the metadata was represented in `ro-crate-metadata.json`.\
For completeness we also show the theoretical capability of the Provenance Run Crate profile (WRROC column) assuming all its MUST/SHOULD requirements are complete. The categories in the first three columns are explained in \[[de Wit 2022]\].\
**Legend:** • fully represented $\;\;\circ$ partially represented $\;\;\cdot$ missing or unstructured representation $\;\;\dots$ optional (e.g. schema.org attribute)

[\[[analysis\_table]\]]{#analysis_table label="analysis_table"}

In conclusion, our analysis shows that runcrate preserves most provenance metadata previously shown to be relevant in realistic RO use case scenarios. The full results of the analysis can be found in \[[de Wit 2023]\].

From this analysis it is worth highlighting the gaps and potential for Workflow Run RO-Crates. Several areas have been flagged by this study as important aspects of workflow metadata, such as Data Access (D3), Software Documentation (SW2) and Workflow Requirements (WF3). Many such aspects require human annotation and cannot be provided by workflow engines alone, although they may be propagated from workflow and tool definitions. Some areas like Consumed Resources (EX2) require additional terms to be defined, and are part of future work.

### Workflow Run RO-Crate and the W3C PROV standard {#prov}

Our aim is to be compatible with both Schema.org and W3C PROV. Provenance Run Crate is the profile that most closely matches the level of detail provided by CWLProv, which extends W3C PROV. Table [3](#rocrate_prov_mapping){reference-type="ref" reference="rocrate_prov_mapping"} shows how the main entities and relationships represented by Provenance Run Crate map to PROV constructs, using the SKOS vocabulary to indicate the type of relationship between each pair of terms. A machine-readable version of the mapping can be found in the of this article \[[Leo 2023c]\].

::: {#rocrate_prov_mapping}


| RO-Crate | Relationship | W3C PROV-O |
| -------- | -------- | -------- | 
| *Action* (superclass of *CreateAction*, *OrganizeAction*) | Has close match                                                                                   | *Activity*                   |
|                                                           |                                                                                                   |                              |
|                                                           | (schema.org Actions may also be potential actions in the future)                                  |                              |
| *CreateAction*, *OrganizeAction*                          | Has broader match                                                                                 | *Activity*                   |
| *Person*                                                  | Has exact match                                                                                   | *Person*                     |
| *Organization*                                            | Has exact match                                                                                   | *OrganizeAction*             |
| *SoftwareApplication*                                     | Has related match                                                                                 | *SoftwareAgent*              |
| *ComputationalWorkflow*, *SoftwareApplication*, *HowTo*   | Has broader match                                                                                 | *Plan*, *Entity*             |
| *File*, *Dataset*, *PropertyValue*                        | Has broader match                                                                                 | *Entity*                     |
| *startTime* on *CreateAction*                             | Has close match                                                                                   | *startedAtTime*              |
| *endTime* on *CreateAction*                               | Has close match                                                                                   | *endedAtTime*                |
| *agent* on *CreateAction*                                 | Has related match                                                                                 | *wasStartedBy*, *wasEndedBy* |
| *agent* and *instrument* on *CreateAction*                | Has broader match                                                                                 | *wasAssociatedWith*          |
| *instrument* on *CreateAction*                            | Has related match                                                                                 | *hadPlan* on *Association*   |
|                                                           |                                                                                                   |                              |
|                                                           | (Complex mapping: an instrument implies a qualified association with the agent, linked to a plan) |                              |
| *object* on *CreateAction*                                | Has exact match                                                                                   | *used*                       |
| *result* on CreateAction                                  | Has close match                                                                                   | inverse *wasGeneratedBy*     |

:  **Mapping from Workflow Run RO-Crate to equivalent W3C PROV concepts** using SKOS \[[Isaac 2009]\]. For instance, *CreateAction* has **broader** match PROV's *Activity*, meaning that *Activity* is more general.
:::

[\[[rocrate\_prov\_mapping]\]]{#rocrate_prov_mapping label="rocrate_prov_mapping"}

### Five Safes Workflow Run Crate {#trusted-workflow-run-crate}

The *Five Safes RO-Crate* \[[Soiland-Reyes 2023e]\] profile has been developed to extend the Workflow Run RO- Crate profile for use in Trusted Research Environments (TRE) in order to handle sensitive health data in federated workflow execution across TREs in the UK \[[Giles 2023]\] and following the Five Safes Framework \[[Desai 2016]\]. A crate with a workflow run request references a pre-approved workflow and project details for manual and automated assessment according to the TRE's agreement policy for the sensitive dataset.

The crate then goes through multiple phases internal to the TRE, including validation, sign-off, workflow execution and disclosure control \[[Soiland-Reyes 2023f]\]. At this stage the crate is also conforming to the Workflow Run Crate profile. The final crate is then safe to be made public. This extension of Workflow Run Crate documents and supports the *human review process* -- important for transparency on TRE data usage. The initial implementation of this profile used WfExS as the workflow execution backend, and this approach will form the basis for further work on implementing federated workflow execution in the British initiatives DARE UK and \[[Snowley 2023]\] and in the European project for Trusted Research Environment.

### Biocompute Object RO-Crate {#bco-crate}

\[[IEEE 2791-2020]\], colloquially *Biocompute Objects* (BCO), is a standard for representing provenance of a genomic sequencing pipeline, intended for submission of the workflow to regulatory bodies, e.g. as part of a personalised medical treatment method \[[Alterovitz 2018]\]. The BCO is represented as a single JSON file which includes description of the workflow and its steps and intended purpose, as well as references for tools used and data sources accessed. There is overlap in the goals of BCO and Workflow Run Crate profiles; however, their intentions and focus are different. BCO is primarily conveying a computational method for the purpose of manual regulatory review and further reuse, with any values provided as an exemplar run. A Workflow Run Crate, however, is primarily documenting a particular workflow execution, and the workflow is associated to facilitate rerun rather than reuse.

Previously, a to packaging BioCompute Objects using RO-Crate was developed as a profile to combine both standards \[[Soiland-Reyes 2021]\]. In this early approach, RO-Crate was primarily a vessel to transport the BCO along with its constituent resources, including the workflow and data files, as well as provide these resources with additional typing and licence metadata that is not captured by the BCO JSON. Further work is being planned with the BCO community to update the BCO-RO profile to align with the newer Workflow Run Crate profiles.


## Conclusion and Future Work {#conclusion}

In this work we presented Workflow Run RO-Crate, a collection of RO-Crate profiles to represent the provenance of the execution of computational workflows at different levels of granularity. We described each profile and their corresponding implementations, shown how they apply to real use cases and described the community behind their development process. Workflow Run RO-Crate has already been adopted by six WMS, including Galaxy, StreamFlow and COMPSs. The flexibility of our model eases its implementation in more systems, allowing interoperability between their workflow run descriptions.

Workflow Run RO-Crate is an ongoing project driven by an open community. A natural consequence of this is that the profiles are not static entities, but keep being updated to cater for new requirements and use cases. In-progress features are tracked in the GitHub repository and are open to discussion for the community. New features under discussion include a representation of the execution environment and recording workflow resource usage. The runcrate toolkit is planned to be expanded both to better support the current features and to include new ones that may arise.

Many of the presented implementations will also develop new features. For example, the Galaxy implementation will add metadata detailing each step of a workflow run to conform to the Provenance Run Crate profile; develop and/or integrate RO-Crate more deeply with import and export of Galaxy histories through the implementation of a profile; and further developing features to allow for user-guided import of RO-Crates as Galaxy datasets, histories and workflows.

Finally, we are currently exploring the cloud execution of Workflow Run RO-Crates. On the one hand, the Workflow Execution Service (WES) specification is used by the Global Alliance for Genomics and Health (GA4GH) \[[Rehm 2021]\] to enable WMS-agnostic interpretation of workflows and scheduling of task execution. On the other hand, the Task Execution Service (TES) specification enables the execution of individual, atomic, containerised tasks in a compute backend-independent manner.

We are planning to undertake an in-depth analysis of the degree of interoperability between the TES and WES API standards -- roughly the equivalents of Process and Workflow Run Crates, respectively -- by placing their focus on the actual execution of tasks/processes and workflows in cloud environments and liaising with the GA4GH Cloud community to align schemas where necessary. We will then build an interconversion library that attempts to:

(1) Construct WES workflow and TES task run requests from RO-Crates containing Provenance, Workflow or Process Run requests and therefore allow their easy (re)execution on any GA4GH Cloud API-powered infrastructure.

(2) Bundle information from the WES and TES (as well as other GA4GH Cloud API resources, where available) to create or extend RO-Crates with standards-compliant Process, Workflow or even Provenance RO-Crates.


[^1]: See section [\[[workflows]\]](#workflows){reference-type="ref" reference="workflows"}.

[^2]: See sections  [\[[inuse]\]](#inuse){reference-type="ref" reference="inuse"} and [\[[ch61:profiles]\]](#ch61:profiles){reference-type="ref" reference="ch61:profiles"}.

[^3]: The three dots (...) in the WRROC column indicate that the concept is supported in an RO-Crate using existing schema.org vocabulary (e.g. <https://schema.org/softwareHelp>) but is not required or recommended by the WRROC profiles.



## References

See chapter [references](../references/).


<!-- van der Aalst 2014 -->
[van der Aalst 2014]: https://doi.org/10.1007/978-3-319-04948-9_2 "Data Scientist: The Engineer of the Future"
<!-- ch8-5 -->
[Addink 2019]: https://doi.org/10.3897/biss.3.37502 "DiSSCo as a New Regional Model for Scientific Collections in Europe"
<!-- Afgan 2018 -->
[Afgan 2018]: https://doi.org/10.1093/nar/gky379 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2018 update"
<!-- Afgan 2023 -->
[Afgan 2023]: https://github.com/galaxyproject/galaxy/releases/tag/v23.1.1 "galaxyproject/galaxy"
<!-- Agarwal 2021 -->
[Agarwal 2021]: https://data.agu.org/DataCitationCoP/2nd-workshop-data-citation "Data Citation Community of Practice -- 8 June 2021 Workshop"
<!-- DCAT2 2020 -->
[Albertoni 2020]: https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/ "Data Catalog Vocabulary (DCAT) -- Version 2"
<!-- w3-vocab-dcat-3 -->
[Albertoni 2023]: https://www.w3.org/TR/2023/WD-vocab-dcat-3-20230307/ "Data Catalog Vocabulary (DCAT)- Version 3"
<!-- ch8-10 -->
[Allan 2019]: https://doi.org/10.3897/BDJ.7.e32342 "A Novel Automated Mass Digitisation Workflow for Natural History Microscope Slides"
<!-- allcockGlobusStripedGridFTP -->
[Allcock 2005]: https://doi.org/10.1109/sc.2005.72 "The Globus Striped GridFTP Framework and Server"
<!-- Almeida 2019 -->
[Almeida 2019]: https://doi.org/10.1038/s41586-019-0965-1 "A new genomic blueprint of the human gut microbiota"
<!-- Alterovitz 2018 -->
[Alterovitz 2018]: https://doi.org/10.1371/journal.pbio.3000099 "Enabling precision medicine via standard communication of HTS provenance, analysis, and results"
<!-- Alves 2021 -->
[Alves 2021]: https://doi.org/10.37044/osf.io/k8znb "ELIXIR Software Management Plan for Life Sciences"
<!-- Amorim 2016 -->
[Amorim 2016]: https://doi.org/10.1007/s10209-016-0475-y "A comparison of research data management platforms: Architecture, flexible metadata and interoperability"
<!-- ch8-43 -->
[Amstutz 2021]: https://s.apache.org/existing-workflow-systems "Existing Workflow systems"
<!-- Amstutz 2023 -->
[Amstutz 2023]: https://doi.org/10.5281/zenodo.7575947 "common-workflow-language/cwltool: 3.1.20230127121939"
<!-- fdo-PIDProfileAttributes -->
[Anders 2022]: https://doi.org/10.5281/zenodo.7825630 "FDO PID profiles & attributes"
<!-- fdo-RequirementSpec -->
[Anders 2023]: https://doi.org/10.5281/zenodo.7782262 "FAIR Digital Objects Forum FDO requirement specifications"
<!-- ch6-10 -->
[Andrio 2019]: https://doi.org/10.1038/s41597-019-0177-4 "BioExcel Building Blocks, a software library for interoperable biomolecular simulation workflows"
<!-- ResourceSyncFrameworkSpecification -->
[ANSI/NISO Z39.99-2017]: https://doi.org/10.3789/ansi.niso.z39.99-2017 "ANSI/NISO Z39.99-2017, ResourceSync Framework Specification"
<!-- Arend 2022 -->
[Arend 2022]: https://doi.org/10.37044/osf.io/c724r "BioHackEU22 Project 22: Plant data exchange and standard interoperability"
<!-- Arfaoui 2020 -->
[Arfaoui 2020]: https://github.com/GhaithArf/ro-crate-rda-madmp-mapper "RO-Crate RDA maDMP Mapper"
<!-- Arkisto 2022 -->
[Arkisto 2022]: https://arkisto-platform.github.io/tools/portal/ "Tools: Data Portal & Discovery"
<!-- Atkinson 2017 -->
[Atkinson 2017]: https://doi.org/10.1016/j.future.2017.05.041 "Scientific workflows: Past, present and future"
<!-- dx-prof -->
[Atkinson 2019]: https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/ "The Profiles Vocabulary"
<!-- 10.2777/940154 -->
[Ayris 2016]: https://doi.org/10.2777/940154 "Realising the European Open Science Cloud"
<!-- Azeroual2022PuttingFP -->
[Azeroual 2022]: https://hdl.handle.net/11366/2243 "Putting FAIR Principles in the Context of Research Information: FAIRness for CRIS and CRIS for FAIRness"
<!-- Bacall 2019 -->
[Bacall 2019]: https://esciencelab.org.uk/projects/ro-composer/ "eScienceLab: RO-Composer"
<!-- Bacall 2022 -->
[Bacall 2022]: https://w3id.org/workflowhub/workflow-ro-crate/1.0 "Workflow RO-Crate Profile 1.0"
<!-- Bacall 2022b -->
[Bacall 2022b]: https://github.com/ResearchObject/ro-crate-ruby "GitHub -- ResearchObject/ro-crate-ruby: A Ruby gem for creating, manipulating and reading RO-Crates"
<!-- Bahra 2011 -->
[Bahra 2011]: https://doi.org/10.21957/nr843dob "Managing work flows with ecFlow"
<!-- bahimFAIRDataMaturity2020a -->
[Bahui 2020]: https://doi.org/10.5334/dsj-2020-041 "The FAIR data maturity model: An approach to harmonise FAIR assessments"
<!-- Baker 2013 -->
[Baker 2013]: https://doi.org/10.1016/j.websem.2013.05.001 "Key choices in the design of Simple Knowledge Organization System (SKOS)"
<!-- ShapeExpressionsShEx -->
[Baker 2019]: http://shex.io/shex-primer/ "Shape Expressions (ShEx) 2.1 Primer"
<!-- Baker 2020 -->
[Baker 2020]: https://doi.org/10.1371/journal.ppat.1008643 "No more business as usual: Agile and effective responses to emerging pathogen threats require open data and open analytics"
<!-- Barker 2019 -->
[Barker 2019]: https://doi.org/10.5334/dsj-2019-044 "The Australian Research Data Commons"
<!-- Barker 2022 -->
[Barker 2022]: https://doi.org/10.1038/s41597-022-01710-x "Introducing the FAIR Principles for research software"
<!-- Batista 2022 -->
[Batista 2022]: https://doi.org/10.1038/s41597-022-01707-6 "Machine actionable metadata models"
<!-- Baxter 2012 -->
[Baxter 2012]: https://www.research.ed.ac.uk/en/publications/e8416ad7-750f-442f-9b17-d812b9bb414d "The Research Software Engineer"
<!-- ch6-24 -->
[Bayarri 2021a]: https://doi.org/10.48546/workflowhub.workflow.29.3 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in CWL"
<!-- ch6-25 -->
[Bayarri 2021b]: https://doi.org/10.48546/workflowhub.workflow.120.2 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in Jupyter Notebook"
<!-- Bayarri 2022 -->
[Bayarri 2022]: https://doi.org/10.48546/workflowhub.workflow.255.1 "CWL GMX Automatic Ligand Parameterization tutorial"
<!-- Bechhofer 2013 -->
[Bechhofer 2013]: https://doi.org/10.1016/j.future.2011.08.004 "Why Linked Data is not enough for scientists"
<!-- ch6-14 -->
[Beg 2021]: https://doi.org/10.1109/MCSE.2021.3052101 "Using Jupyter for Reproducible Scientific Workflows"
<!-- Beier 2024 -->
[Beier 2024]: https://doi.org/10.37044/osf.io/7y2jh "Enabling continuous RDM using Annotated Research Contexts with RO-Crate profiles for ISA"
<!-- Belchev 2021 -->
[Belchev 2021]: https://github.com/KockataEPich/CheckMyCrate "KockataEPich/CheckMyCrate: A command line application for validating a RO-Crate object against a JSON profile"
<!-- Belhajjame 2015 -->
[Belhajjame 2015]: https://doi.org/10.1016/j.websem.2015.01.003 "Using a suite of ontologies for preserving workflow-centric research objects"
<!-- rfc7540 -->
[Belshe 2022]: https://doi.org/10.17487/rfc7540 "Hypertext Transfer Protocol Version 2 (HTTP/2)"
<!-- Beltrán 2023 -->
[Beltrán 2023]: https://doi.org/10.5281/zenodo.10199020 "Autosubmit v4.0.100"
<!-- Benureau 2017 -->
[Benureau 2017]: https://doi.org/10.3389/fninf.2017.00069 "Re-run, repeat, reproduce, reuse, replicate: Transforming code into scientific contributions"
<!-- Berman 2007 -->
[Berman 2007]: https://doi.org/10.1093/nar/gkl971 "The worldwide Protein Data Bank (wwPDB): Ensuring a single, uniform archive of PDB data"
<!-- berners-lee-cool-uris -->
[Berners-Lee 1998]: https://www.w3.org/Provider/Style/URI "Cool URIs don't change"
<!-- berners-leeWeavingWebOriginal1999 -->
[Berners-Lee 1999]: https://identifiers.org/isbn/9780062515865 "Weaving the Web: The original design and ultimate destiny of the World Wide Web by its inventor"
<!-- SemanticWebXML2000 -->
[Berners-Lee 2000]: https://www.w3.org/2000/Talks/1206-xml2k-tbl/slide10-0.html "Semantic Web on XML"
<!-- rfc3986 -->
[Berners-Lee 2005]: https://doi.org/10.17487/rfc3986 "Uniform Resource Identifier (URI): Generic Syntax"
<!-- LinkedDataDesign -->
[Berners-Lee 2006]: https://www.w3.org/DesignIssues/LinkedData.html "Linked Data"
<!-- bernsteinNewLookSemantic2016a -->
[Bernstein 2016]: https://doi.org/10.1145/2890489 "A new look at the semantic web"
<!-- Bietrix 2021 -->
[Bietrix 2021]: https://doi.org/10.5281/zenodo.4705078 "EOSC-Life methodology framework to enhance reproducibility within EOSC Life"
<!-- ch6-27 -->
[BioMoby 2008]: https://doi.org/10.1093/bib/bbn003 "Interoperability with Moby 1.0---It's better than sharing your toothbrush!"
<!-- rfc9114 -->
[Bishop 2022]: https://doi.org/10.17487/rfc9114 "HTTP/3"
<!-- Bizer 2009 -->
[Bizer 2009]: https://doi.org/10.4018/jswis.2009081901 "Linked Data - The Story So Far"
<!-- Bizer 2011 -->
[Bizer 2011]: https://doi.org/10.4018/978-1-60960-593-3.ch008 "Linked data: The story so far"
<!-- fdo-FDO-Upload -->
[Blanchi 2022]: https://doi.org/10.5281/zenodo.7825549 "FDO -- upload of FDO"
<!-- fdo-ImplAttributesTypesProfiles -->
[Blanchi 2023]: https://doi.org/10.5281/zenodo.7825572 "Implementation of attributes, types, profiles and registries"
<!-- ch6-32 -->
[Blankenberg 2014]: https://doi.org/10.1186/gb4161 "Dissemination of scientific software with Galaxy ToolShed"
<!-- Blomquist 2009 -->
[Blomquist 2009]: https://doi.org/10.1145/1597735.1597743 "Experiments on pattern-based ontology design"
<!-- boninodasilvasantosFAIRDataPoints2016a -->
[Bonino 2016]: https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability "FAIR Data points supporting big data interoperability"
<!-- bonino2019 -->
[Bonino 2019]: https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR\%20Digital\%20Objects/FDOF/FAIR\%20Digital\%20Object\%20Framework-v1-02.docx "FAIR digital object framework v1.02"
<!-- bonino2021 -->
[Bonino 2020]: https://fairdigitalobjectframework.org/ "FAIR Digital Object Framework Documentation"
<!-- Bouyssié 2023 -->
[Bouyssié 2023]: https://doi.org/10.1101/2023.10.02.560412 "WOMBAT-P: Benchmarking Label-Free Proteomics Data Analysis Workflows"
<!-- ch6-37 -->
[Brack 2022a]: https://doi.org/10.1371/journal.pcbi.1009823 "Ten Simple Rules for making a software tool workflow-ready"
<!-- Brack 2022 -->
[Brack 2022b]: https://doi.org/10.48546/workflowhub.workflow.373.1 "De novo digitisation."
<!-- Brand 2015 -->
[Brand 2015]: https://doi.org/10.1087/20150211 "Beyond authorship: Attribution, contribution, collaboration, and credit"
<!-- ch8-48 -->
[Bray 2017]: https://doi.org/10.17487/rfc8259 "The JavaScript Object Notation (JSON) Data Interchange Format"
<!-- Brenner 2020 -->
[Brenner 2020]: https://github.com/BrennerG/Ro-Crate_2_ma-DMP "BrennerG/Ro-Crate\_2\_ma-DMP: v1.0.0"
<!-- FOAFVocabularySpecification -->
[Brickley 2014]: http://xmlns.com/foaf/spec/ "FOAF Vocabulary Specification"
<!-- fdo-Glossary -->
[Broeder 2022]: https://drive.google.com/file/d/1KJ9l0p96naKi_2HPJ_MPqPTwS_zlP92G "FDO glossary november 2022"
<!-- Buck 2022 -->
[Buck 2022]: https://doi.org/10.1002/essoar.10509966.1 "AGU data citation community of practice - Credit for creators of data within collections using the concept of a reliquary"
<!-- w3-ldn -->
[Capadisli 2017]: https://www.w3.org/TR/2017/REC-ldn-20170502/ "Linked Data Notifications"
<!-- Cardoso 2020a -->
[Cardoso 2020a]: https://doi.org/10.1007/978-3-030-45442-5_15 "Machine-actionable data management plans: A knowledge retrieval approach to automate the assessment of funders' requirements"
<!-- Cardoso 2020b -->
[Cardoso 2020b]: https://repository.publisso.de/resource/frl:6423289 "Towards Semantic Representation of Machine-Actionable Data Management Plans"
<!-- ch8-38 -->
[Carranza-Rojas 2017]: https://doi.org/10.1186/s12862-017-1014-z "Going deeper in the automated identification of Herbarium specimens"
<!-- carrieroLandscapeOntologyReuse2020a -->
[Carriero 2010]: https://doi.org/10.3233/ssw200033 "The landscape of ontology reuse approaches"
<!-- n-triples -->
[Carrothers 2014]: http://www.w3.org/TR/2014/REC-n-triples-20140225/ "RDF 1.1 N-Triples"
<!-- Chard 2014 -->
[Chard 2014]: https://doi.org/10.1109/MCC.2014.52 "Efficient and secure transfer, synchronization, and sharing of big data"
<!-- Chard 2016 -->
[Chard 2016]: https://static.aminer.org/pdf/fa/bigdata2016/BigD418.pdf "I'll take that to go: Big data bags and minimal identifiers for exchange of large, complex datasets"
<!-- Chard 2019 -->
[Chard 2019]: https://zenodo.org/record/3381754 "Application of BagIt-serialized research object bundles for packaging and re-execution of computational analyses"
<!-- ch5-76 -->
[Chard 2020]: https://doi.org/10.3233/APC200107 "Toward enabling reproducibility for data-intensive research using the Whole Tale platform"
<!-- ciccaresePAVOntologyProvenance2013e -->
[Ciccarese 2013]: https://doi.org/10.1186/2041-1480-4-37 "PAV ontology: Provenance, authoring and versioning"
<!-- Ciccarese 2017 -->
[Ciccarese 2017]: https://www.w3.org/TR/2017/REC-annotation-model-20170223/ "Web Annotation Data Model"
<!-- Claerbout 1992 -->
[Claerbout 1992]: http://sep.stanford.edu/oldsep/matt/join/redoc/web/seg92.html "Electronic documents give reproducible research a new meaning"
<!-- rfc3253 -->
[Clemm 2002]: https://doi.org/10.17487/rfc3253 "Versioning Extensions to WebDAV"
<!-- DOIPAPIHTTPa -->
[CNRI 2023a]: https://www.cordra.org/documentation/api/doip-api-for-http-clients.html "DOIP API for HTTP Clients"
<!-- DOIPExamplesCordraa -->
[CNRI 2023b]: https://www.cordra.org/documentation/api/doip.html "DOIP and Examples"
<!-- Cohen 2020 -->
[Cohen 2020]: https://doi.org/10.1109/MS.2020.2973362 "The Four Pillars of Research Software Engineering"
<!-- Cohen-Boulakia 2017 -->
[Cohen-Boulakia 2017]: https://hal.archives-ouvertes.fr/hal-01516082 "Scientific workflows for computational reproducibility in the life sciences: Status, challenges and opportunities"
<!-- Colonnelli 2021 -->
[Colonnelli 2021]: https://doi.org/10.1109/TETC.2020.3019202 "StreamFlow: cross-breeding Cloud with HPC"
<!-- Colonnelli 2023 -->
[Colonnelli 2023a]: https://doi.org/10.5281/zenodo.7911906 "StreamFlow run of digital pathology tissue/tumor prediction workflow"
<!-- Colonnelli 2023b -->
[Colonnelli 2023b]: https://github.com/alpha-unito/streamflow/releases/tag/0.2.0.dev10 "alpha-unito/streamflow"
<!-- ch8-52 -->
[Corcho 2021]: https://doi.org/10.5281/zenodo.4913285 "D5.1 RO Model Adapted to EOSC"
<!-- 10.48550/arXiv.2305.06746 -->
[Corcho 2023]: https://doi.org/10.48550/arXiv.2305.06746 "A maturity model for catalogues of semantic artefacts"
<!-- Cossu 2018 -->
[Cossu 2018]: https://github.com/duraspace/pcdm/wiki "Portland Common Data Model"
<!-- Costa 2013 -->
[Costa 2013]: https://doi.org/10.1145/2457317.2457365 "Capturing and querying workflow runtime provenance with PROV"
<!-- Crosas 2011 -->
[Crosas 2011]: https://doi.org/10.1045/january2011-crosas "The DataVerse Network: An open-source application for sharing, discovering and preserving data"
<!-- Crosas 2020 -->
[Crosas 2020]: https://doi.org/10.7557/5.5422 "Harvard Data Commons"
<!-- Crosswell 2012 -->
[Crosswell 2012]: https://doi.org/10.1016/j.tibtech.2012.02.002 "ELIXIR: A distributed infrastructure for European biological data"
<!-- CRS4 2022 -->
[CRS4 2022]: https://about.lifemonitor.eu/ "LifeMonitor, a testing and monitoring service for scientific workflows"
<!-- Crusoe 2022 -->
[Crusoe 2022]: https://doi.org/10.1145/3486897 "Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language"
<!-- Cruz 2009 -->
[Cruz 2009]: https://doi.org/10.1109/SERVICES-I.2009.18 "Towards a Taxonomy of Provenance in Scientific Workflow Management Systems"
<!-- Cuevas-Vicenttín 2016 -->
[Cuevas-Vicenttín 2016]: https://purl.dataone.org/provone-v1-dev "ProvONE: A PROV Extension Data Model for Scientific Workflow Provenance"
<!-- cwfr -->
[CWFR 2021]: https://osf.io/3rekv/ "Canonical Workflow Frameworks for Research"
<!-- da Veiga Leprevost 2017 -->
[da Veiga Leprevost 2017]: https://doi.org/10.1093/bioinformatics/btx192 "BioContainers: An open-source and community-driven framework for software standardization"
<!-- DCMIMetadataTerms -->
[DCMI 2020]: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/2020-01-20/ "DCMI Metadata Terms"
<!-- De Geest 2022 -->
[De Geest 2022]: https://doi.org/10.3897/rio.8.e95164 "Enhancing RDM in Galaxy by integrating RO-Crate"
<!-- ro-crate-py -->
[De Geest 2023a]: https://github.com/researchobject/ro-crate-py "GitHub -- ResearchObject/ro-crate-py: Python library for RO-Crate"
<!-- De Geest 2023b -->
[De Geest 2023b]: https://doi.org/10.5281/zenodo.7785861 "Run of an example Galaxy collection workflow"
<!-- ch6-31 -->
[De Giovanni 2016]: https://doi.org/10.1111/ecog.01552 "ENM Components: a new set of web service‐based workflow components for ecological niche modelling"
<!-- ch8-57 -->
[De Roure 2010]: https://web.archive.org/web/20140828142306/http://journal.webscience.org/325/ "Anchors in shifting sand: the primacy of method in the web of data"
<!-- De Smedt 2020 -->
[De Smedt 2020]: https://doi.org/10.3390/publications8020021 "FAIR Digital Objects for Science: From Data Pieces to Actionable Knowledge Units"
<!-- Del Rio 2022 -->
[Del Rio 2022]: https://doi.org/10.1007/978-3-031-13321-3_48 "AI Support for Accelerating Histopathological Slide Examinations of Prostate Cancer in Clinical Studies"
<!-- delgadoInteroperabilityFrameworkDistributed2016a -->
[Delgado 2016]: https://doi.org/10.1007/978-3-319-31861-5_1 "An Interoperability Framework and Distributed Platform for Fast Data Applications"
<!-- Desai 2016 -->
[Desai 2016]: https://econpapers.repec.org/RePEc:uwe:wpaper:20161601 "Five Safes: designing data access for research"
<!-- Devaraju_2021 -->
[Devaraju 2021]: https://doi.org/10.5334/dsj-2021-004 "From conceptualization to implementation: FAIR assessment of research data objects"
<!-- Dillen 2019 -->
[Dillen 2019a]: https://doi.org/10.3897/biss.3.37080 "Zenodo, an archive and publishing repository: A tale of two herbarium specimen pilot projects"
<!-- ch8-59 -->
[Dillen 2019b]: https://doi.org/10.3897/BDJ.7.e31817 "A benchmark dataset of herbarium specimen imagfes with label data"
<!-- Di Tommaso 2017 -->
[Di Tommaso 2017]: https://doi.org/10.1038/nbt.3820 "Nextflow enables reproducible computational workflows"
<!-- DOIHandbookResolution -->
[DOI 2019]: https://doi.org/10.1000/182 "DOI Handbook - Resolution"
<!-- DONA 2018 -->
[DONA 2018]: https://hdl.handle.net/0.DOIP/DOIPV2.0 "Digital Object Interface Protocol specification, version 2.0"
<!-- ch8-62 -->
[DONA 2021]: https://www.dona.net/node/88 "Digital Object Architecture"
<!-- Drummond 2006 -->
[Drummond 2006]: https://www.cs.man.ac.uk/~drummond/presentations/OWA.pdf "The Open World Assumption"
<!-- Duerst 2005 -->
[Dürst 2005]: https://doi.org/10.17487/rfc3987 "Internationalized resource identifiers (IRIs)"
<!-- rfc4918 -->
[Dusseault 2007]: https://doi.org/10.17487/rfc4918 "HTTP Extensions for Web Distributed Authoring and Versioning"
<!-- ch5-50 -->
[Eguinoa 2020]: https://github.com/workflowhub-eu/galaxy2cwl "GitHub workflowhub-eu/galaxy2cwl"
<!-- Eguinoa 2023 -->
[Eguinoa 2023]: https://doi.org/10.37044/osf.io/24jst "BioHackEU22 Report: Enhancing Research Data Management in Galaxy and Data Stewardship Wizard by utilising RO-Crates"
<!-- Ejarque 2023 -->
[Ejarque 2023]: https://doi.org/10.5281/zenodo.7975340 "COMPSs"
<!-- martinekuanWebAPIDesign -->
[Ekuan 2023]: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design "Web API design best practices"
<!-- Ellerm 2023 -->
[Ellerm 2023]: https://doi.org/10.1109/e-Science58273.2023.10254857 "LivePublication: The Science Workflow Creates and Updates the Publication"
<!-- Ellis 2007 -->
[Ellis 2007]: https://doi.org/10.1109/ICSE.2007.85 "The Factory Pattern in API Design: A Usability Evaluation"
<!-- EMBL-EBI 2019 -->
[EMBL-EBI 2019]: http://ftp.ebi.ac.uk/pub/databases/metagenomics/umgs_analyses/ "FTP index of /pub/databases/metagenomics/umgs\_analyses/"
<!-- EMBL-EBI 2020 -->
[EMBL-EBI 2020]: https://github.com/Finn-Lab/MGS-gut "GitHub -- Finn-Lab/MGS-gut: Analysing Metagenomic Species (MGS)"
<!-- h2020fair2016 -->
[EU 2016]: https://ec.europa.eu/research/participants/data/ref/h2020/grants_manual/hi/oa_pilot/h2020-hi-oa-data-mgt_en.pdf "Guidelines on FAIR Data Management in Horizon 2020"
<!-- Ewels 2020 -->
[Ewels 2020]: https://doi.org/10.1038/s41587-020-0439-x "The nf-core framework for community-curated bioinformatics pipelines"
<!-- groupFAIRDataMaturity2020 -->
[FAIR Maturity 2020]: https://doi.org/10.15497/rda00050 "FAIR data maturity model: Specification and guidelines"
<!-- Falk 2010 -->
[Falk 2010]: https://doi.org/10.1016/j.shpsc.2010.10.014 "What is a gene?—Revisited"
<!-- Farnel 2014 -->
[Farnel 2014]: https://dcpapers.dublincore.org/pubs/article/view/3714 "Metadata for research data: Current practices and trends"

<!-- FAIRDigitalObject -->
[FDO]: https://fairdo.org/ "FAIR Digital Object Forum"
<!-- fdo-Specs -->
[FDO Specs]: https://hdl.handle.net/20.500.14132/fdo-spec-docs "FDO Specification Documents - November 2022"
<!-- Feng 2007 -->
[Feng 2007]: https://doi.org/10.1145/1254882.1254906 "PBS: a unified priority-based scheduler"
<!-- 10.5438/jwvf-8a66 -->
[Fenner 2019]: https://doi.org/10.5438/jwvf-8a66 "Introducing the PID graph"
<!-- fenselSemanticWebServices2011 -->
[Fensel 2011]: https://doi.org/10.1007/978-3-642-19193-0 "Semantic Web Services"
<!-- Fernández 2023a -->
[Fernández 2023a]: https://doi.org/10.5281/zenodo.10068956 "inab/WfExS-backend"
<!-- Fernández 2023b -->
[Fernández 2023b]: https://doi.org/10.5281/zenodo.10091550 "RO-Crate from staged WfExS working directory"
<!-- ch6-39 -->
[Ferreira da Silva 2021]: https://doi.org/10.48550/arXiv.2110.02168 "A Community Roadmap for Scientific Workflows Research and Development"
<!-- Ferreira 2022 -->
[Ferreira da Silva]: https://doi.org/10.48550/arXiv.2304.00019 "Workflows Community Summit 2022"
<!-- rfc2616 -->
[Fielding 1999]: https://doi.org/10.17487/rfc2616 "Hypertext Transfer Protocol -- HTTP/1.1"
<!-- fieldingArchitecturalStylesDesign2000a -->
[Fielding 2000]: https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm "Architectural styles and the design of network-based software architectures"
<!-- rfc7230 -->
[Fielding 2014a]: https://doi.org/10.17487/rfc7230 "Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing"
<!-- rfc7231 -->
[Fielding 2014b]: https://doi.org/10.17487/rfc7231 "Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content"
<!-- fieldingReflectionsRESTArchitectural2017a -->
[Fielding 2017]: https://doi.org/10.1145/3106237.3121282 "Reflections on the REST architectural style and \"principled design of the modern web architecture\" (impact paper award)"
<!-- rfc9110 -->
[Fielding 2022]: https://doi.org/10.17487/rfc9110 "HTTP Semantics"
<!-- ch6-21 -->
[Fillbrunn 2017]: https://doi.org/10.1016/j.jbiotec.2017.07.028 "KNIME for reproducible cross-domain analysis of life science data"
<!-- Fouilloux 2023 -->
[Fouilloux 2023]: https://doi.org/10.3897/rio.9.e108765 "FAIR Research Objects for realizing Open Science with RELIANCE EOSC project"
<!-- Freire 2008 -->
[Freire 2008]: https://doi.org/10.1109/MCSE.2008.79 "Provenance for Computational Tasks: A Survey"
<!-- Galaxy 2022 -->
[Galaxy 2022]: https://doi.org/10.1093/nar/gkac247 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update"
<!-- Gamma 1995 -->
[Gamma 1995]: https://identifiers.org/isbn/9780201633610 "Design Patterns"
<!-- ch6-40 -->
[Garcia 2020]: https://doi.org/10.1371/journal.pcbi.1007808 "Ten simple rules to run a successful BioHackathon"
<!-- ch5-48 -->
[Garcia-Silva 2019]: https://doi.org/10.48550/arXiv.1809.10617 "Enabling FAIR research in Earth science through research objects"
<!-- Garijo 2011 -->
[Garijo 2011]: https://doi.org/10.1145/2110497.2110504 "A New Approach for Publishing Workflows"
<!-- Garijo 2012 -->
[Garijo 2012]: https://ceur-ws.org/Vol-951/paper6.pdf "Augmenting PROV with Plans in P-PLAN: Scientific Processes as Linked Data"
<!-- ch6-30 -->
[Garijo 2014a]: https://doi.org/10.1016/j.future.2013.09.018 "Common Motifs in Scientific Workflows: An Empirical Analysis"
<!-- Garijo 2014 -->
[Garijo 2014b]: https://doi.org/10.1109/works.2014.13 "Towards Workflow Ecosystems through Semantic and Standard Representations"
<!-- Gauthier 2019 -->
[Gauthier 2019]: https://doi.org/10.1093/bib/bby063 "A brief history of bioinformatics"
<!-- ch8-7 -->
[GBIF 2021]: https://doi.org/10.35035/bezp-jj23 "GBIF Science Review 2020"
<!-- Gewirtz 1996 -->
[Gewirtz 1996]: https://heinonline.org/HOL/P?h=hein.journals/ylr105&i=1057 "On I Know It When I See It"
<!-- Gil 2011 -->
[Gil 2011]: https://doi.org/10.1109/MIS.2010.9 "Wings: Intelligent Workflow-Based Design of Computational Experiments"
<!-- trefx -->
[Giles 2023]: https://doi.org/10.5281/zenodo.10055354 "TRE-FX: Delivering a federated network of trusted research environments to enable safe data analytics"
<!-- ch5-85 -->
[GitHub 2021]: https://docs.github.com/en/repositories/working-with-files/managing-large-files "Managing large files -- GitHub Docs"
<!-- gobleStateNationData2008c -->
[Goble 2008]: https://doi.org/10.1016/j.jbi.2008.01.008 "State of the nation in data integration for bioinformatics"
<!-- ch5-57 -->
[Goble 2010]: https://doi.org/10.1093/nar/gkq429 "myExperiment: A repository and social network for the sharing of bioinformatics workflows"
<!-- ch5-54 -->
[Goble 2016]: http://repscience2016.research-infrastructures.eu/img/CaroleGoble-ReproScience2016v2.pdf "What Is Reproducibility? The R* Brouhaha"
<!-- goble-ro2018 -->
[Goble 2018]: https://doi.org/10.5281/zenodo.1313066 "Research Object Community Update"
<!-- Goble 2020 -->
[Goble 2020]: https://doi.org/10.1162/dint_a_00033 "FAIR Computational Workflows"
<!-- Goble 2021 -->
[Goble 2021]: https://doi.org/10.5281/zenodo.4605654 "Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory"
<!-- 10.5281/zenodo.7157647 -->
[Goble 2022]: https://doi.org/10.5281/zenodo.7157647 "FAIR-IMPACT: T3.2.1 PIDs in data production workflows"
<!-- FAIROs -->
[González 2022]: https://dgarijo.com/papers/TPDL2022_gonzalez.pdf "FAIROs: Towards FAIR Assessment in Research Objects"
<!-- Gray 2017 -->
[Gray 2017]: https://iswc2017.semanticweb.org/paper-579/ "Bioschemas: From Potato Salad to Protein Annotation"
<!-- rfc5023 -->
[Gregorio 2007]: https://doi.org/10.17487/rfc5023 "The Atom Publishing Protocol"
<!-- rfc6570 -->
[Gregorio 2012]: https://doi.org/10.17487/rfc6570 "URI Template"
<!-- ch8-35 -->
[Groom 2020]: https://doi.org/10.1093/database/baaa072 "People are essential to linking biodiversity data"
<!-- ch5-59 -->
[Grossman 2016]: https://doi.org/10.1109/MCSE.2016.92 "A case for data commons: Toward data science as a service"
<!-- grothAPIcentricLinkedData2014b -->
[Groth 2014]: https://doi.org/10.1016/j.websem.2014.03.003 "API-centric Linked Data integration: The Open PHACTS Discovery Platform case study"
<!-- Gruning 2018a -->
[Grüning 2018a]: https://doi.org/10.1038/s41592-018-0046-7 "Bioconda: Sustainable and Comprehensive Software Distribution for the Life Sciences"
<!-- Gruning 2018b -->
[Grüning 2018b]: https://doi.org/10.1016/j.cels.2018.03.014 "Practical Computational Reproducibility in the Life Sciences"
<!-- w3-rdf-schema -->
[Guha 2014]: http://www.w3.org/TR/rdf-schema/ "RDF Schema 1.1"
<!-- Guha 2015 -->
[Guha 2015]: https://doi.org/10.1145/2857274.2857276 "Schema.org: Evolution of Structured Data on the Web: Big data makes common schemas even more necessary"
<!-- Guha 2016 -->
[Guha 2016]: https://doi.org/10.1145/2844544 "Schema.org: evolution of structured data on the web"
<!-- Gurevich 1995 -->
[Gurevich 1995]: https://identifiers.org/isbn/9780198538547 "Evolving Algebras 1993: Lipari Guide"
<!-- HandleNetRegistry -->
[Handle]: https://www.handle.net/download_hnr.html "Handle.Net Software"
<!-- ch8-58 -->
[Hardisty 2016]: https://doi.org/10.1186/s12898-016-0103-y "BioVeL: a virtual laboratory for data analysis and modelling in biodiversity science and ecology"
<!-- Hardisty 2019 -->
[Hardisty 2019a]: https://doi.org/10.3897/biss.3.37033 "`openDS' -- A New Standard for Digital Specimens and Other Natural Science Digital Object Types"
<!-- ch8-28 -->
[Hardisty 2019b]: https://doi.org/10.5281/zenodo.3532937 "Provisional Data Management Plan for DiSSCo infrastructure"
<!-- ch8-30 -->
[Hardisty 2020]: https://doi.org/10.3897/rio.6.e54280 "Conceptual design blueprint for the DiSSCo digitization infrastructure - DELIVERABLE D8.1"
<!-- Hardisty 2022 -->
[Hardisty 2022]: https://doi.org/10.1162/dint_a_00134 "The Specimen Data Refinery"
<!-- ch8-19 -->
[Harrow 2021]: https://doi.org/10.15252/embj.2020107409 "ELIXIR-EXCELERATE: establishing Europe's data infrastructure for the life science research of the future"
<!-- Harrow 2022 -->
[Harrow 2022]: https://doi.org/10.1093/bioinformatics/btab481 "ELIXIR: providing a sustainable infrastructure for life science data at European scale"
<!-- Hasnain 2018 -->
[Hasnain 2018]: https://doi.org/10.1007/978-3-319-98192-5_60 "Assessing FAIR Data Principles Against the 5-Star Open Data Principles"
<!-- OpenData -->
[Hausenblas 2012]: http://5stardata.info/ "5-star Open Data"
<!-- ch5-63 -->
[Heath 2011]: https://doi.org/10.2200/S00334ED1V01Y201102WBE001 "Linked Data: Evolving the Web into a Global Data Space"
<!-- ch8-14 -->
[Heberling 2019]: https://doi.org/10.1093/biosci/biz094 "The Changing Uses of Herbarium Data in an Era of Global Change: An Overview Using Automated Content Analysis"
<!-- ch8-8 -->
[Heberling 2021]: https://doi.org/10.1073/pnas.2018093118 "Data integration enables global biodiversity synthesis"
<!-- fdo-Granularity -->
[Hellström 2022]: https://doi.org/10.5281/zenodo.7825686 "FDO -- granularity, versioning, mutability"
<!-- ch8-11 -->
[Hereld 2019]: https://doi.org/10.3897/biss.3.37228 "LightningBug ONE: An experiment in high-throughput digitization of pinned insects"
<!-- Herschel 2017 -->
[Herschel 2017]: https://doi.org/10.1007/s00778-017-0486-1 "A survey on provenance: What for? What form? What from?"
<!-- Himanen 2019 -->
[Himanen 2019]: https://doi.org/10.1002/advs.201900808 "Data-Driven Materials Science: Status, Challenges, and Perspectives"
<!-- Hitzler 2016 -->
[Hitzler 2016]: https://identifiers.org/isbn/9781614996767 "Ontology engineering with ontology design patterns"
<!-- hollandIntroducingRole2014 -->
[Holland 2014]: http://blog.schema.org/2014/06/introducing-role.html "Introducing 'Role'"
<!-- horrocksSemanticWebISWC2002 -->
[Horrocks 2022]: https://doi.org/10.1007/3-540-48005-6 "The Semantic Web --- ISWC 2002"
<!-- ch6-12 -->
[Hospital 2020]: https://doi.org/10.5281/zenodo.4540432 "BioExcel-2 Deliverable 2.3 -- First release of demonstration workflows"
<!-- ch6-26 -->
[Hospital 2021a]: https://doi.org/10.48546/workflowhub.workflow.200.1 "Protein MD Setup HPC tutorial using BioExcel Building Blocks (biobb) in PyCOMPSs"
<!-- ch6-23 -->
[Hospital 2021b]: https://doi.org/10.48546/workflowhub.workflow.201.1 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in KNIME"
<!-- huHowMatchableAre2011a -->
[Hu 2011]: https://identifiers.org/isbn/9783642210334 "How matchable are four thousand ontologies on the semantic web"
<!-- ch8-44 -->
[Hui 2012]: https://doi.org/10.1111/j.1467-9973.2012.01761.x "What is a Digital Object?"
<!-- Huntingford 2019 -->
[Huntingford 2019]: https://doi.org/10.1088/1748-9326/ab4e55 "Machine learning and artificial intelligence to aid climate change research and preparedness"
<!-- ch8-37 -->
[Hussein 2021]: https://doi.org/10.48550/arXiv.2104.08732 "Application of Computer Vision and Machine Learning for Digitized Herbarium Specimens: A Systematic Literature Review"
<!-- ieee2791 -->
[IEEE 2791-2020]: https://research.manchester.ac.uk/en/publications/936de52b-ac53-4f0e-9927-77fd7073e88d "IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication"
<!-- w3-skos-primer -->
[Isaac 2009]: https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/ "SKOS Simple Knowledge Organization System Primer"
<!-- ch8-65 -->
[Islam 2020]: https://doi.org/10.5334/dsj-2020-050 "Incorporating RDA Outputs in the Design of a European Research Infrastructure for natural history Collections"
<!-- islam_2023 -->
[Islam 2023]: https://doi.org/10.3233/FC-230001 "FAIR digital objects, persistent identifiers and machine actionability"
<!-- iso16684 -->
[ISO 16684]: https://www.iso.org/standard/75163.html "ISO 16684-1:2019 --- graphic technology --- extensible metadata platform (XMP)"
<!-- iso23009 -->
[ISO 23009-1]: https://www.iso.org/standard/83314.html "ISO/IEC 23009-1:2022 --- information technology --- dynamic adaptive streaming over HTTP (DASH)"
<!-- ch6-11 -->
[Ison 2013]: https://doi.org/10.1093/bioinformatics/btt113 "EDAM: an ontology of bioinformatics operations, types of data and identifiers, topics and formats"
<!-- ch6-35 -->
[Ison 2021]: https://doi.org/10.1093/gigascience/giaa157 "biotoolsSchema: a formalized schema for bioinformatics software description"
<!-- x1255FrameworkDiscovery -->
[ITU-T X.1255]: https://www.itu.int/rec/T-REC-X.1255-201309-I "X.1255 : Framework for Discovery of Identity Management Information"
<!-- fdo-Overview -->
[Ivonne 2023]: https://doi.org/10.5281/zenodo.7824714 "FAIR digital object technical overview"
<!-- rfc9000 -->
[Iyengar 2021]: https://doi.org/10.17487/rfc9000 "QUIC: A UDP-Based Multiplexed and Secure Transport"
<!-- Jacobsen 2020 -->
[Jacobsen 2020]: https://doi.org/10.1162/dint_r_00024 "FAIR Principles: Interpretations and Implementation Considerations"
<!-- 10.1007/978-3-030-30760-8_31 -->
[Jaradeh 2019]: https://doi.org/10.1007/978-3-030-30760-8_31 "Open research knowledge graph: A system walkthrough"
<!-- ch5-65 -->
[Jensen 2017]: https://doi.org/10.1182/blood-2017-03-735654 "The NCI Genomic Data Commons as an engine for precision medicine"
<!-- ch5-66 -->
[Jones 2021]: https://doi.org/10.5281/zenodo.4477164 "Science-on-Schema.org v1.2.0"
<!-- SWORDSpecification -->
[Jones 2022]: https://swordapp.github.io/swordv3/swordv3.html "SWORD 3.0 Specification"
<!-- joras2020 -->
[Joras 2020]: https://engineering.fb.com/2020/10/21/networking-traffic/how-facebook-is-bringing-quic-to-billions "How Facebook is bringing QUIC to billions"
<!-- ch8-60 -->
[JSONPath 2023]: https://datatracker.ietf.org/doc/id/draft-ietf-jsonpath-base-10 "JSONPath: Query Expressions for JSON"
<!-- ch6-15 -->
[Jupyter 2018]: https://doi.org/10.25080/majora-4af1f417-011 "Binder 2.0 - Reproducible, Interactive, Sharable Environments for Science at Scale"
<!-- jutyIdentifiersOrgMIRIAM2011 -->
[Juty 2011]: https://doi.org/10.1093/nar/gkr1097 "Identifiers.org and MIRIAM Registry: Community resources to provide persistent identification"
<!-- Juty 2020 -->
[Juty 2020]: https://doi.org/10.1162/dint_a_00025 "Unique, Persistent, Resolvable: Identifiers as the foundation of FAIR"
<!-- kahnFrameworkDistributedDigital1995a -->
[Kahn 1995]: http://www.cnri.reston.va.us/k-w.html "A framework for distributed digital object services"
<!-- Kahn 2006 -->
[Kahn 2006]: https://doi.org/10.1007/s00799-005-0128-x "A framework for distributed digital object services"
<!-- ch8-45 -->
[Kallinikos 2013]: https://www.jstor.org/stable/43825913 "The ambivalent ontology of digital artifacts"
<!-- kamdarSystematicAnalysisTerm2017a -->
[Kamdar 2017]: https://doi.org/10.3233/sw-160238 "A systematic analysis of term reuse and term overlap across biomedical ontologies"
<!-- ch5-67 -->
[Katsumi 2016]: https://doi.org/10.3233/978-1-61499-660-6-9 "What is ontology reuse?"
<!-- ch6-3 -->
[Katz 2021a]: https://doi.org/10.48550/arXiv.2101.10883 "A Fresh Look at FAIR for Research Software"
<!-- Katz 2021b -->
[Katz 2021b]: https://doi.org/10.1016/j.patter.2021.100222 "A Fresh Look at FAIR for Research Software"
<!-- Draftkellyjsonhal08 -->
[Kelly 2016]: https://datatracker.ietf.org/doc/draft-kelly-json-hal/08/ "JSON Hypertext Application Language"
<!-- Khan 2019 -->
[Khan 2019]: https://doi.org/10.1093/gigascience/giz095 "Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv"
<!-- rfc2817 -->
[Khare 2000]: https://doi.org/10.17487/rfc2817 "Upgrading to TLS Within HTTP/1.1"
<!-- ch8-15 -->
[Kharouba 2019]: https://doi.org/10.1098/rstb.2017.0405 "Using insect natural history collections to study global change impacts: challenges and opportunities"
<!-- ch5-69 -->
[Kim 2008]: https://doi.org/10.1002/cpe.1228 "Provenance trails in the Wings/Pegasus system"
<!-- Kinoshita 2023 -->
[Kinoshita 2023]: https://doi.org/10.5281/zenodo.8144612 "RO-Crate created using Autosubmit version 4.0.100 workflow running kinow/auto-mhm-test-domains"
<!-- kleinScholarlyContextNot2014a -->
[Klein 2014]: https://doi.org/10.1371/journal.pone.0115253 "Scholarly Context Not Found: One in Five Articles Suffers from Reference Rot"
<!-- klimekSurveyToolsLinked2019a -->
[Klímek 2019]: https://doi.org/10.3233/SW-180316 "Survey of tools for linked data consumption"
<!-- Kluyver 2016 -->
[Kluyver 2016]: https://doi.org/10.3233/978-1-61499-649-1-87 "Jupyter Notebooks – a publishing format for reproducible computational workflows"
<!-- ch8-36 -->
[Knyshov 2021]: https://doi.org/10.1093/isd/ixab004 "Pretrained Convolutional Neural Networks Perform Well in a Challenging Test Case: Identification of Plant Bugs (Hemiptera: Miridae) Using a Small Number of Training Images"
<!-- ch5-72 -->
[Koesten 2020]: https://doi.org/10.1016/j.patter.2020.100136 "Dataset reuse: Toward translating principles to practice"
<!-- ch5-71 -->
[Koesten 2021]: https://doi.org/10.1016/j.ijhcs.2020.102562 "Talking datasets -- understanding data sensemaking behaviours"
<!-- w3-shacl -->
[Kontokostas 2017]: https://www.w3.org/TR/shacl/ "Shapes Constraint Language (SHACL)"
<!-- Koster 2012 -->
[Köster 2012]: https://doi.org/10.1093/bioinformatics/bts480 "Snakemake—a scalable bioinformatics workflow engine"
<!-- Kuhn 2021 -->
[Kuhn 2021]: https://doi.org/10.7717/peerj-cs.387 "Semantic micro-contributions with decentralized nanopublication services"
<!-- Kumar 2013 -->
[Kumar 2013]: https://doi.org/10.1029/2012WR012195 "Implications of distributed hydrologic model parameterization on water fluxes at multiple scales and locations"
<!-- ch5-74 -->
[Kunze 2018]: https://doi.org/10.17487/rfc8493 "The BagIt File Packaging Format"
<!-- ARKIdentifierScheme -->
[Kunze 2022]: https://datatracker.ietf.org/doc/draft-kunze-ark/36/ "The ARK Identifier Scheme"
<!-- eosc-interop-framework -->
[Kurowski 2021]: https://doi.org/10.2777/620649 "EOSC Interoperability Framework"
<!-- Käfer 2018a -->
[Käfer 2018a]: http://events.linkeddata.org/ldow2018/papers/LDOW2018_paper_7.pdf "Rule-based Programming of User Agents for Linked Data"
<!-- Käfer 2018b -->
[Käfer 2018b]: https://doi.org/10.1007/978-3-030-00671-6_25 "Specifying, Monitoring, and Executing Workflows in Linked Data Environments"
<!-- ch5-51 -->
[La Rosa 2021a]: https://github.com/CoEDL/modpdsc/ "GitHub -- CoEDL/modpdsc"
<!-- ch5-52 -->
[La Rosa 2021b]: https://github.com/CoEDL/ocfl-tools "GitHub -- CoEDL/ocfl-tools: Tools to process and manipulate an OCFL tree"
<!-- ch5-77 -->
[La Rosa 2021c]: https://arkisto-platform.github.io/describo-online/ "Arkisto Platform: Describo Online"
<!-- ch5-78 -->
[La Rosa 2021d]: https://arkisto-platform.github.io/describo/ "Arkisto Platform: Describo"
<!-- gayoValidatingRDFData2017a -->
[Labra Gayo 2017]: https://doi.org/10.2200/s00786ed1v01y201707wbe016 "Validating RDF Data"
<!-- ORESpecificationAbstract -->
[Lagoze 2008]: http://www.openarchives.org/ore/1.0/datamodel#Proxies "ORE Specification - Abstract Data Model"
<!-- ch5-79 -->
[Lammey 2020]: https://doi.org/10.6087/kcse.192 "Solutions for identification problems: A look at the research organization registry"
<!-- Lamprecht 2019 -->
[Lamprecht 2019]: https://doi.org/10.3233/DS-190026 "Towards FAIR principles for research software"
<!-- lamprechtPerspectivesAutomatedComposition2021b -->
[Lamprecht 2021]: https://doi.org/10.12688/f1000research.54159.1 "Perspectives on automated composition of workflows in the life sciences"
<!-- ch8-6 -->
[Lannom 2020]: https://doi.org/10.1162/dint_a_00034 "FAIR Data and Services in Biodiversity Science and Geoscience"
<!-- fdo-ConfigurationTypes -->
[Lannom 2022a]: https://doi.org/10.5281/zenodo.7825703 "FDO configuration types"
<!-- fdo-Roadmap -->
[Lannom 2022b]: https://doi.org/10.5281/zenodo.7824673 "FAIR digital objects roadmap. Version 5 november 2022"
<!-- fdo-TypingFDOs -->
[Lannom 2022c]: https://doi.org/10.5281/zenodo.7825599 "Typing FAIR digital objects"
<!-- HydraW3CCommunity -->
[Lanthaler 2021]: http://www.hydra-cg.com/spec/latest/core/ "Hydra Core Vocabulary"
<!-- w3-rdf-syntax99 -->
[Lassila 1999]: https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/ "Resource Description Framework (RDF) Model and Syntax Specification"
<!-- w3-prov-o -->
[Lebo 2013a]: https://www.w3.org/TR/2013/REC-prov-o-20130430/ "PROV-O: The PROV Ontology"
<!-- w3-prov-links -->
[Lebo 2013b]: https://www.w3.org/TR/2013/NOTE-prov-links-20130430/ "Linking Across Provenance Bundles"
<!-- Lee 2018 -->
[Lee 2018]: https://doi.org/10.1371/journal.pcbi.1006561 "Ten simple rules for documenting scientific software"
<!-- Leipzig 2021 -->
[Leipzig 2021]: https://doi.org/10.1016/j.patter.2021.100322 "The role of metadata in reproducible computational research"
<!-- runcrate -->
[Leo 2023a]: https://github.com/ResearchObject/runcrate "runcrate"
<!-- workflow-run-crate -->
[Leo 2023b]: https://doi.org/10.48550/arXiv.2312.07852 "Recording provenance of workflow runs with RO-Crate"
<!-- wrroc-crate -->
[Leo 2023c]: https://w3id.org/ro/doi/10.5281/zenodo.10368989 "Recording provenance of workflow runs with RO-Crate"
<!-- run-pathology -->
[Leo 2023]: https://doi.org/10.5281/zenodo.7774351 "Run of digital pathology tissue/tumor prediction workflow"
<!-- ch8-39 -->
[Little 2020]: https://doi.org/10.1002/aps3.11365 "An algorithm competition for automatic species identification from herbarium specimens"
<!-- w3-wsdl20-primer -->
[Liu 2007]: https://www.w3.org/TR/2007/REC-wsdl20-primer-20070626/ "Web Services Description Language"
<!-- Livermore 2022a -->
[Livermore 2022a]: https://doi.org/10.48546/workflowhub.workflow.374.1 "DLA-Collections-test."
<!-- Livermore 2022b -->
[Livermore 2022b]: https://doi.org/10.48546/workflowhub.workflow.375.1 "HTR-Collections-test"
<!-- ch8-56 -->
[Lohonya 2020]: https://doi.org/10.3897/BDJ.8.e50503 "Georeferencing the Natural History Museum's Chinese type collection: of plateaus, pagodas and plants"
<!-- looFirstInternationalConference2022 -->
[Loo 2022]: https://doi.org/10.3897/rio.coll.190 "First International Conference on FAIR Digital Objects"
<!-- Lordan 2014 -->
[Lordan 2014]: https://doi.org/10.1007/s10723-013-9272-5 "ServiceSs: An interoperable programming framework for the cloud"
<!-- ch6-22 -->
[Lowe 2021a]: https://doi.org/10.48546/workflowhub.workflow.194.1 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in Galaxy"
<!-- ch5-83 -->
[Lowe 2021b]: https://doi.org/10.48546/workflowhub.workflow.56.1 "Protein Ligand Complex MD Setup tutorial using BioExcel Building Blocks (biobb) (jupyter notebook)"
<!-- Ludascher 2016 -->
[Ludäscher 2016]: https://doi.org/10.1007/978-3-319-40226-0_7 "A Brief Tour Through Provenance in Scientific Workflows and Databases"
<!-- ch8-17 -->
[Lughadha 2019]: https://doi.org/10.1111/cobi.13289 "Harnessing the potential of integrated systematics for conservation of taxonomically complex, megadiverse plant groups"
<!-- Luo 2022 -->
[Luo 2022]: https://www.proquest.com/docview/2763290077 "Knowledge enhanced digital objects"
<!-- Luo 2023 -->
[Luo 2023]: https://doi.org/10.1109/CCGridW59191.2023.00064 "Knowledge Enhanced Digital Objects: a Data Lake Approach"
<!-- ch5-84 -->
[Lynch 2022]: https://www.npmjs.com/package/ro-crate-excel "npm: ro-crate-excel"
<!-- Mai Chan 1995 -->
[Mai Chan 1995]: https://identifiers.org/isbn/9781563081910 "Library of Congress Subject Headings: Principles and Application"
<!-- Manubens-Gil 2016 -->
[Manubens-Gil 2016]: https://doi.org/10.1109/HPCSim.2016.7568429 "Seamless management of ensemble climate prediction experiments on HPC platforms"
<!-- Marinescu 2022 -->
[Marinescu 2023]: https://identifiers.org/isbn/9780323852777 "Cloud Computing: Theory and Practice"
<!-- Matentzoglu 2022 -->
[Matentzoglu 2022]: https://doi.org/10.1093/database/baac087 "Ontology Development Kit: a toolkit for building, maintaining and standardizing biomedical ontologies"
<!-- McMurry 2017 -->
[McMurry 2017]: https://doi.org/10.1371/journal.pbio.2001414 "Identifiers for the 21st century: How to design, provision, and reuse identifiers to maximize utility and impact of life science data"
<!-- ContentNegotiationHTTP -->
[MDN 2023]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation "HTTP Content negotiation"
<!-- de Mello 2022 -->
[de Mello 2022]: https://doi.org/10.1007/s12553-022-00639-w "Semantic interoperability in health records standards: a systematic literature review"
<!-- merono-penuelaConclusionFutureChallenges2021a -->
[Meroño-Peñuela 2021a]: https://doi.org/10.1007/978-3-031-01917-3_7 "Conclusion and future challenges"
<!-- merono-penuelaWebDataApis2021b -->
[Meroño-Peñuela 2021b]: https://doi.org/10.1007/978-3-031-01917-3_3 "Web data APIs over SPARQL"
<!-- Meurisse 2023 -->
[Meurisse 2023]: https://s11.no/2023/phd/federated-causal-inference/ "Federated causal inference based on real-world observational data sources"
<!-- ch5-121 -->
[Miksa 2019a]: https://doi.org/10.15497/rda00039 "RDA DMP Common Standard for Machine-Actionable Data Management Plans"
<!-- ch5-88 -->
[Miksa 2019b]: https://doi.org/10.1371/journal.pcbi.1006750 "Ten principles for machine-actionable data management plans"
<!-- Miksa 2020 -->
[Miksa 2020]: https://doi.org/10.4126/frl01-006423291 "Research Object Crates and Machine-actionable Data Management Plans"
<!-- Millard 2010 -->
[Millard 2010]: https://ceur-ws.org/Vol-665/MillardEtAl_COLD2010.pdf "Consuming multiple linked data sources: Challenges and Experiences"
<!-- OpenAPISpecificationV3 -->
[Miller 2021]: https://spec.openapis.org/oas/v3.1.0.html "OpenAPI Specification"
<!-- Missier 2010 -->
[Missier 2010]: https://doi.org/10.1109/WORKS.2010.5671861 "Linking multiple workflow provenance traces for interoperable collaborative science"
<!-- Missier 2013 -->
[Missier 2013]: https://doi.org/10.5555/2482949.2482961 "D-PROV: extending the PROV provenance model with workflow structure"
<!-- ch5-89 -->
[Möller 2010]: https://doi.org/10.1186/1471-2105-11-S12-S5 "Community-driven computational biology with Debian Linux"
<!-- ch6-4 -->
[Möller 2017]: https://doi.org/10.1007/s41019-017-0050-4 "Robust cross-platform workflows: How technical and scientific communities collaborate to develop, test and share best practices for data analysis"
<!-- Mons 2017 -->
[Mons 2017]: https://doi.org/10.3233/ISU-170824 "Cloudy, increasingly FAIR; revisiting the FAIR Data guiding principles for the European Open Science Cloud"
<!-- ch5-91 -->
[Mons 2018]: https://identifiers.org/isbn/9781315351148 "Data Stewardship for Open Science"
<!-- Moreau 2013 -->
[Moreau 2013]: https://www.w3.org/TR/2013/REC-prov-dm-20130430/ "PROV-DM: The PROV Data Model"
<!-- ch5-92 -->
[myExperiment 2009]: https://web.archive.org/web/20091115080336/http%3a%2f%2frdf.myexperiment.org/ontologies "myExperiment Ontology Modules"
<!-- ch5-53 -->
[Nature 2019]: https://doi.org/10.1038/s41592-019-0350-x "Giving software its due"
<!-- NCBOBioPortal -->
[NCBO]: https://bioportal.bioontology.org/ontologies "NCBO BioPortal"
<!-- ch8-3 -->
[Nelson 2019a]: https://doi.org/10.1098/rstb.2017.0391 "The history and impact of digitization and digital data mobilization on biodiversity research"
<!-- ch8-4 -->
[Nelson 2019b]: https://doi.org/10.3897/biss.3.37896 "DiSSCo, iDigBio and the Future of Global Collaboration"
<!-- neumannAnalysisPublicREST2021a -->
[Neumann 2021]: https://doi.org/10.1109/TSC.2018.2847344 "An analysis of public REST web service apis"
<!-- ch5-93 -->
[Newman 2009]: http://ceur-ws.org/Vol-523/Newman.pdf "myExperiment: An ontology for e-Research"
<!-- ch5-94 -->
[Neylon 2017]: https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/ "As a researcher \ldots I'm a bit bloody fed up with Data Management"
<!-- ch8-33 -->
[Nieva de la Hidalga 2021]: https://doi.org/10.1007/s00138-022-01276-z "Cross-validation of a semantic segmentation network for natural history collection specimens"
<!-- ch6-17 -->
[Niewielska 2020]: https://doi.org/10.5281/zenodo.4916060 "BioExcel-2 Deliverable 2.5 - Provision of a Workflow Environment at BioExcel portal"
<!-- 10.1186/s13326-021-00240-6 -->
[Norris 2021]: https://doi.org/10.1186/s13326-021-00240-6 "Why and how to engage expert stakeholders in ontology development: Insights from social and behavioural sciences"
<!-- rfc8288 -->
[Nottingham 2017]: https://doi.org/10.17487/rfc8288 "Web Linking"
<!-- nurdiati2008 -->
[Nurdiati 2008]: https://purl.utwente.nl/publications/64931 "25 years development of knowledge graph theory: the results and the challenge"
<!-- OCarragain 2019 -->
[Ó Carragáin 2019a]: https://doi.org/10.5281/zenodo.3250687 "A lightweight approach to research object data packaging"
<!-- 10.5281/zenodo.3337883 -->
[Ó Carragáin 2019b]: https://s11.no/2019/phd/ro-crate/ "RO-Crate: A lightweight approach to research object data packaging"
<!-- ch5-96 -->
[OCFL 2020]: https://ocfl.io/1.0/spec/ "OCFL, Oxford Common File Layout Specification"
<!-- InfoURIRegistry -->
[OCLC 2010]: http://info-uri.info/ "Info URI Registry (Frozen)"
<!-- Ohta 2023 -->
[Ohta 2023]: https://doi.org/10.5281/zenodo.10134581 "Example of Workflow Run RO-Crate Output in Sapporo"
<!-- Oliver 2019 -->
[Oliver 2019]: https://doi.org/10.1109/MCSE.2019.2906593 "Workflow Automation for Cycling Systems"
<!-- OpenGraphProtocol -->
[Open Graph]: https://ogp.me/ "The Open Graph protocol"
<!-- ch8-47 -->
[openDS 2021]: https://github.com/DiSSCo/openDS "Draft specification for open Digital Specimens (openDS)"
<!-- ModernStandardsParadigm -->
[OpenStand 2017]: https://open-stand.org/about-us/principles/ "The Modern Standards Paradigm"
<!-- LicensesStandardsOpen -->
[OSI 022]: https://opensource.org/licenses "Licenses & Standards"
<!-- ch8-18 -->
[Owen 2020]: https://doi.org/10.3897/rio.6.e58030 "Towards a scientific workflow featuring Natural Language Processing for the digitisation of natural history collections"
<!-- pageRESTLinkedData2011 -->
[Page 2011]: https://doi.org/10.1145/1967428.1967435 "REST and Linked Data"
<!-- rfc8216 -->
[Pantos 2017]: https://doi.org/10.17487/rfc8216 "HTTP Live Streaming"
<!-- w3-micropub -->
[Parecki 2017]: https://www.w3.org/TR/2017/REC-micropub-20170523/ "Micropub"
<!-- ya2ro -->
[Pavel 2023]: https://doi.org/10.4126/frl01-006444984 "Ya2ro: A tool for creating Research Objects from minimum metadata"
<!-- Pérez 2018 -->
[Pérez 2018]: https://doi.org/10.1007/s10115-018-1164-3 "A systematic review of provenance systems"
<!-- Pergl 2019 -->
[Pergl 2019]: https://doi.org/10.5334/dsj-2019-059 "``Data Stewardship Wizard'': A Tool Bringing Together Researchers, Data Stewards, and Data Experts around Data Management Planning"
<!-- ch5-97 -->
[Piper 2020]: https://doi.org/10.1080/14490854.2020.1796500 "Digital crowdsourcing and public understandings of the past: Citizen historians meet criminal characters"
<!-- Poiata 2016 -->
[Poiata 2016]: https://doi.org/10.1093/gji/ggw071 "Multiband array detection and location of seismic sources recorded by dense seismic networks"
<!-- Poiata 2023 -->
[Poiata 2023]: https://doi.org/10.5281/zenodo.7788030 "BackTrackBB: Multi-band array detection and location of seismic sources (PyCOMPSs implementation)"
<!-- polleresMoreDecentralizedVision2020a -->
[Polleres 2020]: https://doi.org/10.3233/SW-190380 "A more decentralized vision for linked data"
<!-- Poveda 2010 -->
[Poveda 2010]: https://doi.org/10.1007/978-3-642-14264-2_10 "Common Pitfalls in Ontology Development"
<!-- ch8-12 -->
[Price 2018]: https://doi.org/10.31219/osf.io/s2p73 "ALICE: Angled Label Image Capture and Extraction for high throughput insect specimen digitisation"
<!-- Prlić 2012 -->
[Prlić 2012]: https://doi.org/10.1371/journal.pcbi.1002802 "Ten Simple Rules for the Open Development of Scientific Software"
<!-- ch8-40 -->
[Pryer 2022]: https://doi.org/10.1002/aps3.11372 "Using computer vision on herbarium specimen images to discriminate among closely related horsetails (Equisetum)"
<!-- RDF 1.1 2014 -->
[RDF 1.1 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
<!-- Rehm 2021 -->
[Rehm 2021]: https://doi.org/10.1016/j.xgen.2021.100029 "GA4GH: International policies and standards for data sharing across genomic research and healthcare"
<!-- DigitalObjectInterface -->
[Reilly 2009]: https://www.dona.net/doipv1doc "Digital Object Interface Protocol Version 1.0"
<!-- Reis 2022 -->
[Reis 2022]: https://doi.org/10.1109/ACCESS.2021.3137671 "Developing Docker and Docker-Compose Specifications"
<!-- rfc2818 -->
[Rescorla 2000]: https://doi.org/10.17487/rfc2818 "HTTP Over TLS"
<!-- ch5-100 -->
[Rettberg 2015]: https://doi.org/10.5860/crln.76.6.9326 "OpenAIRE: Supporting a European open access mandate"
<!-- 10.1002/jcc.26842 -->
[Riccardi 2022]: https://doi.org/10.1002/jcc.26842 "Towards improved FAIRness of the ThermoML Archive"
<!-- WebSocketsStandard -->
[Rice 2022]: https://websockets.spec.whatwg.org/ "WebSockets Standard"
<!-- ch5-105 -->
[RO-Crate 1.0]: https://doi.org/10.5281/zenodo.3541888 "RO-Crate Metadata Specification 1.0"
<!-- ch5-107 -->
[RO-Crate 1.1]: https://w3id.org/ro/crate/1.1 "RO-Crate Metadata Specification 1.1"
<!-- rocrate1.1 -->
[RO-Crate 1.1.3]: https://w3id.org/ro/crate/1.1 "RO-Crate Metadata Specification 1.1.3"
<!-- rocrate1.2 -->
[RO-Crate 1.2]: https://www.researchobject.org/ro-crate/1.2-DRAFT/ "RO-Crate Metadata Specification 1.2.0"
<!-- ch5-95 -->
[ro-crate-html-js]: https://www.npmjs.com/package/ro-crate-html-js "ro-crate-html-js"
<!-- 10.7490/f1000research.1114375.1 -->
[Robinson 2017]: https://doi.org/10.7490/f1000research.1114375.1 "CWL Viewer: The Common Workflow Language viewer"
<!-- cwlviewer -->
[Robinson 2023]: https://github.com/common-workflow-language/cwlviewer "common-workflow-language/cwlviewer: v1.4.7"
<!-- faircookbook -->
[Rocca-Serra 2023]: https://doi.org/10.1038/s41597-023-02166-3 "The FAIR cookbook - the essential resource for and by FAIR doers"
<!-- ch6-28 -->
[Saltz 2006]: https://doi.org/10.1093/bioinformatics/btl272 "caGrid: design and implementation of the core architecture of the cancer biomedical informatics grid"
<!-- Samaniego 2010 -->
[Samaniego 2010]: https://doi.org/10.1029/2008WR007327 "Multiscale parameter regionalization of a grid-based hydrologic model at the mesoscale"
<!-- Samuel 2022 -->
[Samuel 2022]: https://doi.org/10.1186/s13326-021-00253-1 "End-to-End provenance representation for the understandability and reproducibility of scientific experiments using a semantic approach"
<!-- ch5-101 -->
[Sandve 2013]: https://doi.org/10.1371/journal.pcbi.1003285 "Ten simple rules for reproducible computational research"
<!-- sandvineGlobalInternetPhenomena -->
[Sandvine 2022]: https://www.sandvine.com/global-internet-phenomena-report-2022 "Global Internet Phenomena Report"
<!-- sauermannCoolURIsSemantic2011 -->
[Sauermann 2008]: http://www.w3.org/TR/cooluris/ "Cool URIs for the semantic web"
<!-- Scheidegger 2008 -->
[Scheidegger 2008]: https://doi.org/10.1145/1376616.1376747 "Querying and re-using workflows with VsTrails"
<!-- schema.org -->
[schema.org]: https://schema.org/ "Schema.org - Schema.org"
<!-- SchemaOrgActions -->
[schema actions]: https://schema.org/docs/actions.html "Schema.org Actions"
<!-- w3-rdf11-primer -->
[Schreiber 2014]: http://www.w3.org/TR/2014/NOTE-rdf11-primer-20140624 "RDF 1.1 Primer"
<!-- ch5-102 -->
[Schriml 2020]: https://doi.org/10.1038/s41597-020-0524-5 "COVID-19 pandemic reveals the peril of ignoring metadata standards"
<!-- Schröder 2022 -->
[Schröder 2022]: https://doi.org/10.1186/s13326-021-00257-x "Structure-based knowledge acquisition from electronic lab notebooks for research data provenance documentation"
<!-- Schultes 2019 -->
[Schultes 2019]: https://doi.org/10.23728/B2SHARE.166A074BFF614A31B05E9DF5BFD9809D "FAIR principles and digital objects: Accelerating convergence on a data infrastructure"
<!-- FIP -->
[Schultes 2020]: https://doi.org/10.1007/978-3-030-65847-2_13 "Reusable FAIR implementation profiles as accelerators of FAIR convergence"
<!-- 10.3389/data.2022.883341 -->
[Schultes 2022]: https://doi.org/10.3389/data.2022.883341 "FAIR Digital Twins for Data-Intensive Research"
<!-- fdo-DOIPEndorsement -->
[Schwardmann 2022a]: https://doi.org/10.5281/zenodo.7824796 "DOIP endorsement request"
<!-- schwardmannTwoExamplesHow2022 -->
[Schwardmann 2022b]: https://doi.org/10.3897/rio.8.e96014 "Two Examples on How FDO Types can Support Machine and Human Readability"
<!-- surveyOntology -->
[Scrocca 2021]: https://doi.org/10.4126/frl01-006429412 "The Survey Ontology: Packaging Survey Research as Research Objects"
<!-- Sefton 2018 -->
[Sefton 2018]: https://doi.org/10.5281/zenodo.1445817 "DataCrate: a method of packaging, distributing, displaying and archiving Research Objects"
<!-- ch5-49 -->
[Sefton 2021b]: https://github.com/UTS-eResearch/ro-crate-js "GitHub -- UTS-eResearch/ro-crate-js"
<!-- Sefton 2021 -->
[Sefton 2021a]: http://ptsefton.com/2021/04/07/rdmpic/ "FAIR Data Management; It's a lifestyle not a lifecycle"
<!-- DataInformationView -->
[Semmler 2022]: https://www.wdc-climate.de/ui/entry?acronym=C6CMAWAWMhi "IPCC DDC: AWI AWI-CM1.1MR model output prepared for CMIP6 CMIP historical"
<!-- singhal2012 -->
[Singhal 2012]: https://blog.google/products/search/introducing-knowledge-graph-things-not/ "Introducing the knowledge graph: Things, not strings"
<!-- Sirvent 2022 -->
[Sirvent 2022]: https://hdl.handle.net/2117/384589 "Automatic, Efficient, and Scalable Provenance Registration for FAIR HPC Workflows"
<!-- smithOBOFoundryCoordinated2007a -->
[Smith 2007]: https://doi.org/10.1038/nbt1346 "The OBO Foundry"
<!-- Smith 2016 -->
[Smith 2016]: https://doi.org/10.7717/peerj-cs.86 "Software citation principles"
<!-- LREC2022 -->
[Smith 2022]: https://aclanthology.org/2022.signlang-1.28 "Integrating Auslan Resources into the Language Data Commons of Australia"
<!-- Snowley 2023 -->
[Snowley 2023]: https://www.hdruk.ac.uk/wp-content/uploads/2023/10/Integrating-Our-Community_v1-Oct-2023-compressed.pdf "Integrating Our Community"
<!-- ch5-111 -->
[Soiland-Reyes 2014]: https://w3id.org/bundle/2014-11-05/ "Research Object Bundle 1.0"
<!-- Soiland-Reyes 2016 -->
[Soiland-Reyes 2016]: https://s11.no/2016/provweek-tavernaprov/ "Tracking Workflow Execution With TavernaPROV"
<!-- Soiland-Reyes 2018 -->
[Soiland-Reyes 2018]: https://doi.org/10.5281/zenodo.1471585 "common-workflow-language/cwlprov: CWLProv 0.6.0"
<!-- ch5-108 -->
[Soiland-Reyes 2020a]: https://twitter.com/soilandreyes/status/1250721245622079488 "I am looking for which bioinformatics journals encourage authors to submit their code/pipeline/workflow supporting data analysis"
<!-- Soiland-Reyes 2021 -->
[Soiland-Reyes 2021]: https://doi.org/10.5281/zenodo.4633732 "Describing and packaging workflows using RO-Crate and BioCompute Objects"
<!-- Soiland-Reyes 2022 -->
[Soiland-Reyes 2022a]: https://s11.no/2022/phd/ro-crate/ "Packaging research artefacts with RO-Crate"
<!-- Soiland-Reyes 2022b -->
[Soiland-Reyes 2022b]: https://s11.no/2022/phd/canonical-workflow-building-blocks/ "Making Canonical Workflow Building Blocks interoperable across workflow languages"
<!-- 10.3897/rio.8.e93937 -->
[Soiland-Reyes 2022c]: https://s11.no/2022/phd/fdo-with-ro-crate/ "Creating lightweight FAIR digital objects with RO-Crate"
<!-- 10.3897/rio.8.e94501 -->
[Soiland-Reyes 2022d]: https://s11.no/2022/phd/updating-ld-for-fdo/ "Updating Linked Data practices for FAIR Digital Object principles"
<!-- 10.5281/zenodo.7256713 -->
[Soiland-Reyes 2022e]: https://doi.org/10.5281/zenodo.7256713 "stain/signposting: Signposting v0.9.0"
<!-- 10.5281/zenodo.7152762 -->
[Soiland-Reyes 2022f]: https://doi.org/10.5281/zenodo.7152762 "EuroScienceGateway: WP2 introduction"
<!-- 10.5281/zenodo.5833456 -->
[Soiland-Reyes 2022g]: https://w3id.org/ro/doi/10.5281/zenodo.5146227 "Packaging research artefacts with RO-Crate"
<!-- soilandreyes2023 -->
[Soiland-Reyes 2023a]: https://w3id.org/ro/doi/10.5281/zenodo.8075229 "Comparison tables for evaluating FAIR Digital Object and Linked Data"
<!-- soilandreyes2023b -->
[Soiland-Reyes 2023b]: https://doi.org/10.5281/zenodo.7774582 "Enabling FAIR Signposting and RO-Crate for content/metadata discovery and consumption"
<!-- soilandreyes2023c -->
[Soiland-Reyes 2023c]: https://s11.no/2023/phd/evaluating-fdo/ "Evaluating FAIR Digital Object and Linked Data as distributed object systems"
<!-- fdo-collections -->
[Soiland-Reyes 2023d]: https://doi.org/10.5281/zenodo.7828632 "Building diverse FDO Collections using RO-Crate"
<!-- 5s-crate -->
[Soiland-Reyes 2023e]: https://w3id.org/5s-crate/0.4 "Five Safes RO-Crate profile"
<!-- Soiland-Reyes 2023f -->
[Soiland-Reyes 2023f]: https://doi.org/10.5281/zenodo.10376350 "TRE-FX Technical Documentation - Five Safes RO-crate"
<!-- Soiland-Reyes 2024 -->
[Soiland-Reyes 2024]: https://doi.org/10.37044/osf.io/gmk2h "Enabling FAIR Digital Objects with RO-Crate, Signposting and Bioschemas"
<!-- ch8-66 -->
[Speicher 2015]: http://www.w3.org/TR/2015/REC-ldp-20150226/ "Linked Data Platform 1.0"
<!-- w3-ldp -->
[Sporny 2014]: https://www.w3.org/TR/2014/REC-json-ld-20140116/ "JSON-LD 1.0: A JSON-based Serialization for Linked Data"
<!-- w3-rdfa-primer -->
[Sporny 2015]: https://www.w3.org/TR/2015/NOTE-rdfa-primer-20150317/ "RDFa 1.1 Primer"
<!-- w3-json-ld -->
[Sporny 2020]: https://www.w3.org/TR/2020/REC-json-ld11-20200716/ "JSON-LD 1.1: A JSON-based Serialization for Linked Data"
<!-- Draftietfmediamansuffixes00MediaTypes -->
[Sporny 2023]: https://datatracker.ietf.org/doc/draft-ietf-mediaman-suffixes/03/ "Media Types with Multiple Suffixes"
 
<!-- stallingsHandbookComputercommunicationsStandards1990 -->
[Stallings 1990]: https://identifiers.org/isbn/9780672226977 "Handbook of computer-communications standards: The open systems (OSI) model and OSI-related standards"
 
<!-- stanczykProcessModellingInformation1987 -->
[Stanczyk 1987]: https://doi.org/10.21954/ou.ro.0000f821 "Process modelling for information system description"
<!-- stefiDevelopReuseTwo2015a -->
[Stefi 2015a]: http://doi.org/10.1007/978-3-319-19593-3_18 "To develop or to reuse? Two perspectives on external reuse in software projects"
<!-- stefiDevelopersMakeUnbiased2015 -->
[Stefi 2015b]: https://doi.org/10.18151/7217489 "Do Developers Make Unbiased Decisions? - The Effect of Mindfulness and Not-Invented-Here Bias on the Adoption of Software Components"
<!-- Stodden 2016 -->
[Stodden 2016]: https://doi.org/10.1126/science.aah6168 "Enhancing reproducibility for computational methods"
<!-- Suetake 2022a -->
[Suetake 2022]: https://doi.org/10.12688/f1000research.122924.1 "Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics"
<!-- Suetake 2023 -->
[Suetake 2023a]: https://doi.org/10.1093/gigascience/giad031 "A workflow reproducibility scale for automatic validation of biological interpretation results"
<!-- Suetake 2023b -->
[Suetake 2023b]: https://doi.org/10.5281/zenodo.10134452 "sapporo-wes/sapporo-service"
<!-- rfc3650 -->
[Sun 2003a]: https://doi.org/10.17487/rfc3650 "Handle System Overview"
<!-- rfc3652 -->
[Sun 2003b]: https://doi.org/10.17487/rfc3652 "Handle System Protocol (ver 2.1) Specification"
<!-- ch8-9 -->
[Sweeney 2018]: https://doi.org/10.12705/671.10 "Large-scale digitization of herbarium specimens: Development and usage of an automated, high-throughput conveyor system"
<!-- Taschuk 2017 -->
[Taschuk 2017]: https://doi.org/10.1371/journal.pcbi.1005412 "Ten simple rules for making research software more robust"
<!-- Taivalsaari 2021 -->
[Taivalsaari 2021]: https://doi.org/10.1007/978-3-030-74296-6_28 "Full Stack Is Not What It Used to Be"
<!-- ch8-13 -->
[Tegelberg 2017]: https://doi.org/10.1109/eScience.2017.85 "Mass Digitization of Individual Pinned Insects Using Conveyor-Driven Imaging"
<!-- ch6-20 -->
[Tejedor 2017]: https://doi.org/10.1177/1094342015594678 "PyCOMPSs: Parallel computational workflows in Python"
<!-- ch5-114 -->
[Thieberger 2012]: https://hdl.handle.net/10125/4567 "Keeping records of language diversity in melanesia: The Pacific and regional archive for digital sources in endangered cultures (PARADISEC)"
<!-- ch8-2 -->
[Thiers 2016]: https://doi.org/10.1007/s12228-016-9423-7 "Digitization of the New York Botanical Garden herbarium"
<!-- w3-xmlschema11 -->
[Thompson 2012]: https://www.w3.org/TR/2012/REC-xmlschema11-1-20120405/ "W3C XML Schema Definition Language (XSD) 1.1 Part 1"
<!-- Thompson 2020 -->
[Thompson 2020]: https://doi.org/10.1162/dint_a_00031 "Making FAIR Easy with FAIR Tools: From Creolization to Convergence"
<!-- thorntonUsingShapeExpressions2019a -->
[Thornton 2019]: https://doi.org/10.1007/978-3-030-21348-0_39 "Using shape expressions (ShEx) to share RDF data models and to guide curation with rigorous validation"
<!-- tirmiziMappingOBOOWL2011a -->
[Tirmizi 2011]: https://doi.org/10.1186/2041-1480-2-s1-s3 "Mapping between the OBO and OWL ontology languages"
<!-- Tran 2014 -->
[Tran 2014]: https://doi.org/10.1007/978-3-319-05458-2_27 "Linked Data Mashups: A Review on Technologies, Applications and Challenges"
<!-- Trautwein 2022 -->
[Trautwein 2022]: https://doi.org/10.48550/arXiv.2208.05877 "Design and Evaluation of IPFS: A Storage Layer for the Decentralized Web"
<!-- ch8-32 -->
[Triki 2020]: https://doi.org/10.5220/0009170005230529 "Objects Detection from Digitized Herbarium Specimen based on Improved YOLO V3"
<!-- ch5-116 -->
[Troncy 2010]: https://www.persistent-identifier.nl/urn:nbn:nl:ui:18-14511 "VAMP: A service for validating MPEG-7 descriptions w.r.t. to formal profile definitions"
<!-- Tudorache 2020 -->
[Tudorache 2020]: https://doi.org/10.3233/SW-190382 "Ontology engineering: Current state, challenges, and future directions"
<!-- tupelo-schneckrobertBriefIntroductionCordra2022 -->
[Tupelo-Scheck 2022]: https://www.rd-alliance.org/sites/default/files/Cordra.2022.pdf "Brief Introduction to Cordra & DOIP"
<!-- turcoaneLinkedDataJSONLD2014a -->
[Turcoane 2014]: https://doi.org/10.55630/dipp.2014.4.11 "Linked data, JSON-LD and the semantics of cultural and scientific heritage"
<!-- ch8-41 -->
[Unger 2016]: https://doi.org/10.1186/s12862-016-0827-5 "Computer vision applied to herbarium specimens of German trees"
<!-- ch5-117 -->
[Van de Sompel 2007]: http://icl.utk.edu/ctwatch/quarterly/articles/2007/08/interoperability-for-the-discovery-use-and-re-use-of-units-of-scholarly-communication/ "Interoperability for the discovery, use, and re-use of units of scholarly communication"
<!-- rfc7089 -->
[Van de Sompel 2013]: https://doi.org/10.17487/rfc7089 "HTTP Framework for Time-Based Access to Resource States --Memento"
<!-- vandesompel2015 -->
[Van de Sompel 2015]: https://doi.org/10.1045/november2015-vandesompel "Reminiscing About 15 Years of Interoperability Efforts"
<!-- Van de Sompel 2022 -->
[Van de Sompel 2022]: https://signposting.org/FAIR/ "FAIR Signposting Profile"
<!-- Van de Sompel 2023 -->
[Van de Sompel 2023]: https://doi.org/10.5281/zenodo.7977333 "FAIR Digital Objects and FAIR Signposting"
<!-- DesigningLinkedData2018 -->
[Verborgh 2018]: https://ruben.verborgh.org/blog/2018/12/28/designing-a-linked-data-developer-experience/ "Designing a Linked Data developer experience"
<!-- verborghSemanticWebIdentity2020a -->
[Verborgh 2020]: https://doi.org/10.3233/SW-190372 "The semantic web identity crisis: In search of the trivialities that never were"
<!-- 10.5281/zenodo.7848102 -->
[Verburg 2023]: https://doi.org/10.5281/zenodo.7848102 "FAIR-IMPACT project response to \"FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons\""
<!-- 10.5281/zenodo.4671709 -->
[Vergoulis 2021]: https://doi.org/10.5281/zenodo.4671709 "Use of RO-Crates in SCHeMa"
<!-- ch5-118 -->
[Vergoulis 2022]: https://doi.org/10.48550/arXiv.2103.13138 "SCHeMa: Scheduling Scientific Containers on a Cluster of Heterogeneous Machines"
<!-- de Visser 2023 -->
[de Visser 2023]: https://doi.org/10.1371/journal.pcbi.1011369 "Ten quick tips for building FAIR workflows"
<!-- Vivian 2017 -->
[Vivian 2017]: https://doi.org/10.1038/nbt.3772 "Toil enables reproducible, open source, big biomedical data analyses"
<!-- ch5-119 -->
[Volk 2014]: https://doi.org/10.1007/s00267-014-0258-2 "Why is data sharing in collaborative natural resource efforts so hard and what can we do to improve it?"
<!-- ch5-120 -->
[W3C 2007]: https://www.w3.org/2001/tag/doc/httpRange-14/2007-08-31/HttpRange-14.html "Dereferencing HTTP URIs"
<!-- w3-owl2-overview -->
[W3C 2012]: https://www.w3.org/TR/2012/REC-owl2-overview-20121211 "OWL 2 Web Ontology Language Document Overview"
<!-- w3-sparql11-overview -->
[W3C 2013]: https://www.w3.org/TR/2013/REC-sparql11-overview-20130321/ "SPARQL 1.1 Overview"
<!-- DataW3C -->
[W3C 2015]: https://www.w3.org/standards/semanticweb/data "Linked Data"
<!-- UsageStatisticsJSONLD -->
[W3Techs 2023]: https://w3techs.com/technologies/details/da-jsonld "Usage Statistics of JSON-LD for Websites"
<!-- Walton 2020 -->
[Walton 2020a]: https://doi.org/10.3897/rio.6.e57602 "Landscape Analysis for the Specimen Data Refinery"
<!-- ch8-34 -->
[Walton 2020b]: https://doi.org/10.3897/rio.6.e56211 "A cost analysis of transcription systems"
<!-- ch8-16 -->
[Watanabe 2019]: https://doi.org/10.1093/biosci/biy163 "The Evolution of Natural History Collections: New research tools move specimens, data to center stage"
<!-- HTMLStandard -->
[WHATWG 2023]: https://html.spec.whatwg.org/multipage/microdata.html "Microdata"
<!-- weigelRDARecommendationPID2018 -->
[Weigel 2018]: https://doi.org/10.15497/rda00031 "RDA Recommendation on PID Kernel Information"
<!-- fdo-KernelAttributes -->
[Weigel 2022]: https://doi.org/10.5281/zenodo.7825693 "FDO -- kernel attributes & metadata"
<!-- fdo-DocProcessStd -->
[Weiland 2022a]: https://drive.google.com/file/d/1lPNBBROjEoZ6fTfrtdqcMa3Q2G27PoC_ "FAIR Digital Objects Forum Document Standards"
<!-- fdo-MachineActionDef -->
[Weiland 2022b]: https://doi.org/10.5281/zenodo.7825650 "FDO machine actionability"
<!-- de Wit 2022 -->
[de Wit 2022]: https://doi.org/10.5281/zenodo.7113250 "A Non-Intimidating Approach to Workflow Reproducibility in Bioinformatics"
<!-- de Wit 2023 -->
[de Wit 2023]: https://doi.org/10.5281/zenodo.10251812 "Analysis of runcrate"
<!-- wieczorekDarwinCoreEvolving2012 -->
[Wieczorek 2012]: https://doi.org/10.1371/journal.pone.0029715 "Darwin Core: An Evolving Community-Developed Biodiversity Data Standard"
<!-- rfc6906 -->
[Wilde 2013]: https://doi.org/10.17487/rfc6906 "The 'profile' Link Relation Type"
<!-- RFC9264 -->
[Wilde 2020]: https://doi.org/10.17487/rfc9264 "Linkset: Media Types and a Link Relation Type for Link Sets"
<!-- Wilkinson 2016 -->
[Wilkinson 2016]: https://doi.org/10.1038/sdata.2016.18 "The FAIR Guiding Principles for scientific data management and stewardship"
<!-- Wilkinson 2018 -->
[Wilkinson 2018]: https://doi.org/10.1038/sdata.2018.118 "A design framework and exemplar metrics for FAIRness"
<!-- 10.5281/zenodo.7463421 -->
[Wilkinson 2022a]: https://doi.org/10.5281/zenodo.7463421 "FAIR Assessment Tools: Towards an “Apples to Apples” Comparisons"
<!-- wilkinsonWorkflowsWhenParts2022b -->
[Wilkinson 2022b]: https://doi.org/10.48550/arxiv.2209.09022 "F*** workflows: When parts of FAIR are missing"
<!-- Wilkinson2023 -->
[Wilkinson 2023a]: https://doi.org/10.12688/openreseurope.15364.2 "Community-driven governance of FAIRness assessment"
<!-- Wilkinson2024 -->
[Wilkinson 2024]: https://doi.org/10.5281/zenodo.10453348 "Report on FAIR Signposting and its uptake by the community"
<!-- williamsOpenPHACTSSemantic2012c -->
[Williams 2012]: https://doi.org/10.1016/j.drudis.2012.05.016 "Open PHACTS: Semantic interoperability for drug discovery"
<!-- wittenburgDigitalObjectsDrivers2019a -->
[Wittenburg 2019]: https://doi.org/10.23728/b2share.b605d85809ca45679b110719b6c6cb11 "Digital objects as drivers towards convergence in data infrastructures"
<!-- ch8-27 -->
[Wittenburg 2021]: https://doi.org/10.1162/dint_a_00132 "Canonical Workflows to Make Data FAIR"
<!-- wittenburgFAIRDigitalObject2022b -->
[Wittenburg 2022]: https://doi.org/10.5281/zenodo.5872645 "FAIR digital object demonstrators 2021"
<!-- Wittenburg 2023a -->
[Wittenburg 2023a]: https://doi.org/10.52825/cordi.v1i.263 "FDOs to Enable Cross-Silo Work"
<!-- Wittenburg 2023b -->
[Wittenburg 2023b]: https://doi.org/10.52825/cordi.v1i.374 "FDO to Structure the Domain of Knowledge"
<!-- Wittner 2020 -->
[Wittner 2020]: https://s11.no/2021/phd/iso-23494-provenance/ "ISO 23494: Biotechnology - Provenance Information Model for Biological Specimen and Data"
<!-- Wittner 2022 -->
[Wittner 2022]: https://doi.org/10.1038/s41597-022-01537-6 "Lightweight Distributed Provenance Model for Complex Real--world Environments"
<!-- Wittner 2023 -->
[Wittner 2023a]: https://doi.org/10.1002/lrh2.10365 "Toward a common standard for data and specimen provenance in life sciences"
<!-- Wittner 2023b -->
[Wittner 2023b]: https://s11.no/2023/phd/linking-provenance/ "Linking provenance and its metadata in multi-organizational environments of life sciences"
<!-- Wittner 2023c -->
[Wittner 2023c]: https://doi.org/10.5281/zenodo.8095888 "Packing provenance using CPM RO-Crate profile"
<!-- wolstencroftRightFieldEmbeddingOntology2011b -->
[Wolstencroft 2011]: https://doi.org/10.1093/bioinformatics/btr312 "RightField: Embedding ontology annotation in spreadsheets"
<!-- wolstencroftTavernaWorkflowSuite2013d -->
[Wolstencroft 2013]: https://doi.org/10.1093/nar/gkt328 "The Taverna workflow suite"
<!-- w3-rdf11-concepts -->
[Wood 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
<!-- Woolland 2022 -->
[Woolland 2022]: https://doi.org/10.3897/rio.8.e94349 "Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows"
<!-- ch5-124 -->
[WorkflowHub 2023]: https://w3id.org/workflowhub/ "WorkflowHub project: Project pages for developing and running the WorkflowHub, a registry of scientific workflows"
<!-- Draftbhuttonjsonschema -->
[Wright 2022]: https://datatracker.ietf.org/doc/draft-bhutton-json-schema/01/ "JSON schema: A media type for describing JSON documents"
<!-- WRROC 2023a -->
[WRROC 2023a]: https://w3id.org/ro/wfrun/process/0.4 "Process Run Crate specification"
<!-- WRROC 2023b -->
[WRROC 2023b]: https://w3id.org/ro/wfrun/workflow/0.4 "Workflow Run Crate specification"
<!-- WRROC 2023c -->
[WRROC 2023c]: https://w3id.org/ro/wfrun/provenance/0.4 "Provenance Run Crate specification"
<!-- Yoo 2003 -->
[Yoo 2003]: https://doi.org/10.1007/10968987_3 "SLURM: Simple Linux Utility for Resource Management"
<!-- Yuen 2021 -->
[Yuen 2021]: https://doi.org/10.1093/nar/gkab346 "The Dockstore: enhancing a community platform for sharing reproducible and accessible computational protocols"
<!-- zarrasComparisonFrameworkMiddleware2004a -->
[Zarras 2004]: https://doi.org/10.5381/jot.2004.3.5.a2 "A Comparison Framework for Middleware Infrastructures"
<!-- Zerouali 2023 -->
[Zerouali 2023]: https://doi.org/10.1109/MSR59073.2023.00078 "Helm Charts for Kubernetes Applications: Evolution, Outdatedness and Security Risks"
<!-- ch5-125 -->
[Zhao 2012]: https://research.manchester.ac.uk/en/publications/cba81ca4-e92c-408e-8442-383d1f15fcdf "Why workflows break -- understanding and combating decay in taverna workflows"
<!-- ch5-126 -->
[Zoubek 2021]: https://github.com/e11938258/RO-Crates-and-Excel "RO Crates and Excel"
<!-- ch5-127 -->
[Žumer 2009]: https://doi.org/10.1515/9783598441844 "National Bibliographies in the Digital Age: Guidance and New Directions"
