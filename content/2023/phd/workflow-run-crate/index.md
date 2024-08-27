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
  Preprint resubmitted to PLOS One following peer review
description: > 
    Recording the provenance of scientific computation results is key to the support of traceability, reproducibility and quality assessment of data products. Several data models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, existing approaches tend to lack interoperable adoption across workflow management systems.
    
    In this work we present Workflow Run RO-Crate, an extension of RO-Crate (Research Object Crate) and Schema.org to capture the provenance of the execution of computational workflows at different levels of granularity and bundle together all their associated objects (inputs, outputs, code, etc.). The model is supported by a diverse, open community that runs regular meetings, discussing development, maintenance and adoption aspects. Workflow Run RO-Crate is already implemented by several workflow management systems, allowing interoperable comparisons between workflow runs from heterogeneous systems. We describe the model, its alignment to standards such as W3C PROV, and its implementation in six workflow systems.Finally, we illustrate the application of Workflow Run RO-Crate in two use cases of machine learning in the digital image analysis domain.
authors: 
  - orcid: https://orcid.org/0000-0001-8271-5429
    name: Simone Leo
  - orcid: https://orcid.org/0000-0002-2961-9670
    name: Michael R Crusoe
  - orcid: https://orcid.org/0000-0003-4929-1219
    name: Laura Rodríguez-Navas
  - orcid: https://orcid.org/0000-0003-0606-2512
    name: Raül Sirvent
  - orcid: https://orcid.org/0000-0002-3468-0652
    name: Alexander Kanitz
  - orcid: https://orcid.org/0000-0002-8940-4946
    name: Paul De Geest
  - orcid: https://orcid.org/0000-0002-0003-2024
    name: Rudolf Wittner
  - orcid: https://orcid.org/0000-0002-4663-5613
    name: Luca Pireddu
  - orcid: https://orcid.org/0000-0003-0454-7145
    name: Daniel Garijo
  - orcid: https://orcid.org/0000-0002-4806-5140
    name: José M. Fernández
  - orcid: https://orcid.org/0000-0001-9290-2017
    name: Iacopo Colonnelli
  - orcid: https://orcid.org/0000-0002-1119-1792
    name: Matej Gallo
  - orcid: https://orcid.org/0000-0003-3777-5945
    name: Tazro Ohta
  - orcid: https://orcid.org/0000-0003-2765-0049
    name: Hirotaka Suetake
  - orcid: https://orcid.org/0000-0002-0309-604X
    name: Salvador Capella-Gutierrez
  - orcid: https://orcid.org/0000-0003-0902-0086
    name: Renske de Wit
  - orcid: https://orcid.org/0000-0001-8250-4074
    name: Bruno de Paula Kinoshita
  - orcid: https://orcid.org/0000-0001-9842-9718
    name: Stian Soiland-Reyes
---

<style>
#analysis_table td,#analysis_table th { 
  border: black thin solid;
}
#analysis_table td[style~="text-align:center"] {
  font-weight: bold;
  font-size: 200%;
  line-height: 50%;
}
</style>

<h2>Cite as</h2>

Simone Leo, Michael R.  Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M.  Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2024):  
**Recording provenance of workflow runs with RO-Crate**.  
_PLOS One_ (accepted 10.1371/journal.pone.0309210)
_arXiV_:2312.07852  
<https://doi.org/10.48550/arXiv.2312.07852>


* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown and figure caption formatting; references in s11 house style; URLs as footnotes/hyperlinks; enumerations made explicit; listing captions; some paragraphs split for readability; details moved to footnote, acknowledgement and references moved to separate chapters; fixed minor typos and grammatical errors; table 2 moved earlier with added internal bookmark links; `prov:` added to prefix list; header added in prefix table.

_Warning: The below article has not yet been fully prepared for the Web_.

<article>

# Recording provenance of workflow runs with RO-Crate

_Simone Leo<sup>1</sup>, Michael R. Crusoe<sup>2,3,4</sup>, Laura Rodríguez-Navas<sup>5</sup>, Raül Sirvent<sup>5</sup>, Alexander Kanitz<sup>6,7</sup>, Paul De Geest<sup>8</sup>, Rudolf Wittner<sup>9,10,11</sup>, Luca Pireddu<sup>1</sup>, Daniel Garijo<sup>12</sup>, José M. Fernández<sup>5</sup>, Iacopo Colonnelli<sup>13</sup>, Matej Gallo<sup>9</sup>, Tazro Ohta<sup>14,15</sup>, Hirotaka Suetake<sup>16</sup>, Salvador Capella-Gutierrez<sup>5</sup>, Renske de Wit<sup>2</sup>, Bruno de Paula Kinoshita<sup>5</sup>, Stian Soiland-Reyes<sup>17,18</sup>_

<div class="affiliations">

<sup>1</sup> Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Loc.
Piscina Manna, Edificio 1, 09050 Pula (CA), Italy  
<sup>2</sup> Vrije Universiteit Amsterdam, The Netherlands  
<sup>3</sup> DTL Projects, The Netherlands  
<sup>4</sup> Forschungszentrum Jülich, Germany  
<sup>5</sup> Barcelona Supercomputing Center (Spain)  
<sup>6</sup> Biozentrum, University of Basel, Switzerland  
<sup>7</sup> Swiss Institute of Bioinformatics, Lausanne, Switzerland  
<sup>8</sup> VIB-UGent Center for Plant Systems Biology, Gent, Belgium  
<sup>9</sup> Faculty of Informatics, Masaryk University, Botanická 68a, 602 00, Brno, Czech Republic  
<sup>10</sup> Institute of Computer Science, Masaryk University, Šumavská 416/15, 602 00, Brno, Czech Republic  
<sup>11</sup> BBMRI-ERIC, Neue Stiftingtalstrasse 2, 8010, Graz, Austria  
<sup>12</sup> Ontology Engineering Group, Universidad Politécnica de Madrid  
<sup>13</sup> Università degli Studi di Torino, Computer Science Dept., Torino, Italy  
<sup>14</sup> Database Center for Life Science, Joint Support-Center for Data Science Research, Research Organization of Information and Systems, Shizuoka, Japan  
<sup>15</sup> Institute for Advanced Academic Research, Chiba University, Chiba, Japan  
<sup>16</sup> Sator, Incorporated, Tokyo, Japan   
<sup>17</sup> Department of Computer Science, The University of Manchester, Manchester, United Kingdom   
<sup>18</sup> Informatics Institute, Faculty of Science, University of Amsterdam, Amsterdam, The Netherlands

</div>

## Abstract

Recording the provenance of scientific computation results is key to the support of traceability, reproducibility and quality assessment of data products.
Several data models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing.
However, existing approaches tend to lack interoperable adoption across workflow management systems.
In this work we present **Workflow Run RO-Crate**, an extension of RO-Crate (Research Object Crate) and Schema.org to capture the provenance of the execution of computational workflows at different levels of granularity and bundle together all their associated objects (inputs, outputs, code, etc.).
The model is supported by a diverse, open community that runs regular meetings, discussing development, maintenance and adoption aspects.
Workflow Run RO-Crate is already implemented by several workflow management systems, allowing interoperable comparisons between workflow runs from heterogeneous systems.
We describe the model, its alignment to standards such as W3C PROV, and its implementation in six workflow systems.
Finally, we illustrate the application of Workflow Run RO-Crate in two use cases of machine learning in the digital image analysis domain.

An [RO-Crate for this article](https://w3id.org/ro/doi/10.5281/zenodo.10368989) is archived at <https://doi.org/10.5281/zenodo.10368989>


## Introduction {#introduction}
A crucial part of scientific research is recording the provenance of its outputs.
The W3C PROV standard defines provenance as “a record that describes the people, institutions, entities, and activities involved in producing, influencing, or delivering a piece of data or a thing” [[Moreau 2013]].
Provenance is instrumental to activities such as traceability, reproducibility,
accountability, and quality assessment [[Herschel 2017]].
The constantly growing size and complexity of scientific datasets and the analysis that is required to extract useful information from them has made science increasingly dependent on advanced automated processing techniques in order to get from experimental data to final results [[Himanen 2019], [Gauthier 2019], [Huntingford 2019]].
Consequently, a large part of the provenance information for scientific outputs consists of descriptions of complex computer-aided data processing steps. This data processing is often expressed as workflows -- i.e., high-level applications that coordinate multiple tools and manage intermediate outputs in order to produce the final results.

In order to homogenise the collection and interchange of provenance records, the W3C consortium proposed a standard for representing provenance in the Web (PROV [[Moreau 2013]]), along with the PROV ontology (PROV-O) [[Lebo 2013a]], an OWL [[W3C 2012]] representation of PROV.
PROV-O has been widely extended for workflows (e.g., D-PROV [[Missier 2013]], ProvONE [[Cuevas-Vicenttín 2016]], OPMW [[Garijo 2011]] (Open Provenance Model for Workflows), P-PLAN [[Garijo 2012]]), where provenance information is collected in two main forms: prospective and retrospective [[Freire 2008]]. 

*Prospective provenance* -- the execution plan -- is essentially the workflow itself: it includes a machine-readable specification with the processing steps to be performed and the data and software dependencies to carry out each computation.

*Retrospective provenance* refers to what actually happened during an execution -- i.e. what were the values of the input parameters, which outputs were produced, which tools were executed, how much time did the execution take, whether the execution was successful or not, etc.
Retrospective provenance may be represented at different levels of abstraction, depending on the information that is available and/or required: a workflow execution may be interpreted (i) as a single end-to-end activity, (ii) as a set of individual execution of workflow steps, or (iii) by going a step further and indicating how each step is divided into sub-processes when a workflow is deployed in a cluster.

Various workflow management systems, such as WINGS [[Gil 2011]] (Workflow INstance Generation and Specialization) and VisTrails [[Scheidegger 2008], [Costa 2013]], have adopted PROV and its PROV-O representation to lift the burden of provenance collection from tool users and developers [[Atkinson 2017], [Pérez 2018]].


D-PROV, PROV-ONE, OPMW, P-PLAN propose representations of workflow plans and their respective executions, taking into account the features of the workflow systems implementing them (e.g., hierarchical representations, sub-processes, etc.).
Other data models, such as *wfprov* and *wfdesc* [[Belhajjame 2015]], go a step further by considering not only the link between plans and executions, but also how to package the various artefacts as a Research Object (RO) [[Bechhofer 2013]] to improve metadata interoperability and document the context of a digital experiment.

However, while these models address some workflow provenance representation issues, they have two main limitations: first, the extensions of PROV are not directly interoperable because of differences in their granularities or different assumptions in their workflow representations; second, their support from Workflow Management Systems (WMS) is typically one system per model. An early approach to unify and integrate workflow provenance traces across WMSs was the Workflow Ecosystems through STandards (WEST) [[Garijo 2014b]], which used WINGS to build workflow templates and different converters. In all of these workflow provenance models, the emphasis is on the workflow execution structure as a directed graph, with only partial references for the data items.
The REPRODUCE-ME ontology [[Samuel 2022]] extended PROV and P-PLAN to explain the overall scientific process with the experimental context including real life objects (e.g. instruments, specimens) and human activities (e.g. lab protocols, screening), demonstrating provenance of individual Jupyter Notebook cells [[Samuel 2018]] and highlighting the need for provenance also where there is no workflow management system.

More recently, interoperability has been partially addressed by Common Workflow Language Prov (CWLProv) [[Khan 2019]], which represents workflow enactments as research objects serialised according to the Big Data Bag approach [[Chard 2016]].
The resulting format is a folder containing several data and metadata files [[Soiland-Reyes 2018]], expanding on the Research Object Bundle approach of Taverna [[Soiland-Reyes 2016]].
CWLProv also extends PROV with a representation of executed processes (activities), their inputs and outputs (entities) and their executors (agents), together with their Common Workflow Language (CWL) specification [[Crusoe 2022]] -- a standard workflow specification adopted by at least a dozen different [workflow systems](https://www.commonwl.org/implementations/). 

Although CWLProv includes prospective provenance as a *plan*
within PROV (based on the *wfdesc* model), in practice its implementation does not include tool definitions or file formats.
Thus, for CWLProv consumers to reconstruct the full prospective provenance for understanding the workflow, they would also need to inspect the separate workflow definition in the native language of the workflow management system.
Additionally, the CWLProv RO may include several other metadata files and PROV serialisations conforming to different formats, complicating its generation and consumption.

As for granularity, CWLProv proposes multiple levels of provenance [[Khan 2019]], from Level 0 (capturing workflow definition) to Level 3 (domain-specific annotations).
In practice, the CWL reference implementation *cwltool* [[Amstutz 2023]] and the corresponding CWLProv specification [[Soiland-Reyes 2018]] record provenance details of all task executions together with the intermediate data and any nested workflows (CWLProv level 2). This level of granularity requires substantial support from the workflow management system implementing the CWL specification, resulting appropriate for workflow languages where the execution plan, including its distribution among the various tasks, is well known in advance.
However, it can be at odds with other systems where the execution is more dynamic, depending on the verification of specific runtime conditions, such as the size and distribution of the data (e.g., COMPSs [[Lordan 2014]]).
This design makes the implementation of CWLProv challenging, which the authors suspect may be one of the main causes for the low adoption of CWLProv (at the time of writing the format is supported only by cwltool).

Finally, being based on the PROV model, CWLProv is highly focused on the interaction between agents, processes and related entities, while support for contextual metadata (such as workflow authors, licence or creation date) in the Research Object Bundle is [limited](https://w3id.org/bundle/context) and stored in a separate manifest file, which includes the data identifier mapping to filenames.
A project that uses serialised Research Objects similar to those used by CWLProv is Whole Tale [[Chard 2019]], a web platform with a focus on the narrative around scientific studies and their reproducibility, where the serialised ROs are used to export data and metadata from the platform. In contrast, our work is primarily focused on the ability to capture the provenance of computational workflow execution including its data and executable workflow definitions.

RO-Crate [[Soiland-Reyes 2022a]] is an approach for packaging research data together with their metadata and associated resources. RO-Crate extends Schema.org [[Guha 2015]], a popular vocabulary for describing resources on the Web.
In its simplest form, an RO-Crate is a directory structure that contains a single JSON-LD [[Sporny 2020]] metadata file at the top level.
The metadata file describes all entities stored in the RO-Crate along with their relationships, and it is both machine-readable and human-readable.
RO-Crate is general enough to be able to describe any dataset, but can also be made as specific as needed through the use of extensions called *profiles*. [Profiles](https://www.researchobject.org/ro-crate/profiles.html\#ro-crate-profiles) describe “a set of conventions, types and properties that one minimally can require and expect to be present in that subset of RO-Crates”.
The broad set of types and properties from Schema.org, complemented by a few additional terms from other vocabularies, make the RO-Crate model a candidate for expressing a wide range of contextual information that complements and enriches the core information specified by the profile.
This information may include, among others, the workflow authors and their affiliations, associated publications, licensing information, related software, etc.
This approach is used by WorkflowHub [[Goble 2021]], a workflow-system-agnostic workflow registry which specifies a Workflow RO-Crate profile [[Bacall 2022]] to gather the workflow definition with such metadata in an archived RO-Crate[^1].

In this work, we present **Workflow Run RO-Crate** (WRROC), an extension of RO-Crate for representing computational workflow execution provenance.
Our main contributions include:

- a collection of RO-Crate profiles to represent and package both the prospective and the retrospective provenance of a computational workflow run in a way that is machine-actionable [[Batista 2022]], independently of the specific workflow language or execution system, and including support for re-execution;
- implementations of this new model in six workflow management systems and in one conversion tool;
- a mapping of our profiles against the W3C PROV-O Standard using the Simple Knowledge Organisation System (SKOS) [[Isaac 2009]].

To foster usability, the profiles are characterised by different levels of detail, and the set of mandatory metadata items is kept to a minimum in order to ease the implementation.
This flexible approach increases the model's adaptability to the diverse landscape of WMSs used in practice.
The base profile, in particular, is applicable to any kind of computational process, not necessarily described in a formal workflow language.
All profiles are supported and sustained by the Workflow Run RO-Crate community, which meets regularly to discuss extensions, issues and new implementations.

The rest of this work is organised as follows: we first describe the Workflow Run RO-Crate profiles in Section [2](#the-workflow-run-ro-crate-profiles); we then illustrate implementations in Section [3](#implementations) and usage examples in Section [4](#exemplary-use-cases); finally, we include a discussion in Section [5](#discussion) and we conclude the paper with our plans for future work in Section [6](#conclusion).


## The Workflow Run RO-Crate profiles {#profiles}

RO-Crate profiles are extensions of the base RO-Crate specification that describe how to represent the classes and relationships that appear in a specific domain or use case[^2].
An RO-Crate conforming to a profile is not just machine-readable, but also machine-actionable, as a digital object whose type is represented by the profile itself [[Soiland-Reyes 2022b]].

The Workflow Run RO-Crate profiles are the main outcome of the activities of the [Workflow Run RO-Crate Community](https://www.researchobject.org/workflow-run-crate), an open working group that includes workflow users and developers, WMS users and developers, and researchers and software engineers interested in workflow execution provenance and Findable, Accessible, Interoperable and Reusable (FAIR) approaches for data and software.
One of the first steps in the development of the Workflow-Run RO-Crate profiles was to compile a list of requirements to be addressed by the model from all interested participants, in the form of *[competency questions](https://www.researchobject.org/workflow-run-crate/requirements)* (CQs).
The process also included reviewing existing state of the art models, such as wfprov [[Belhajjame 2015]], ProvONE [[Cuevas-Vicenttin 2016]] or OPMW [[Garijo 2011]]. The result was the definition of 11 CQs capturing requirements which span a broad application scope and consider different levels of provenance granularity.
Each requirement was supported by a rationale and linked to a GitHub issue to drive the public discussion forward. When a requirement was addressed, related changes were integrated into the profiles and the relevant issue was closed. All the original issues are now closed, and the profiles have had five official releases on Zenodo [[WRROC 2024a WRROC 2024b WRROC 2024c]].
The target of several of the original CQs evolved during profile development, as the continuous discussion within the community highlighted the main points to be addressed. This continuous process is reflected in the corresponding issues and pull requests in the community's GitHub repository. The final implementation of the CQs in the profiles is validated with SPARQL queries that can be run on RO-Crate metadata samples, also available on the GitHub repository [ResearchObject/workflow-run-crate](https://github.com/ResearchObject/workflow-run-crate/tree/main/docs/sparql).

As requirements were being defined, it became apparent that one single profile would not have been sufficient to cater for all possible usage scenarios.
In particular, while some use cases required a detailed description of all computations orchestrated by the workflow, others were only concerned with a “black box” representation of the workflow and its execution as a whole (i.e., whether the workflow execution as a whole was successful and which results were obtained).
Additionally, some computations involve a data flow across multiple applications that are executed without the aid of a WMS and thus are not formally described in a standard workflow language.
These observations led to the development of three profiles:

1)  [Process Run Crate](https://w3id.org/ro/wfrun/process)
    to describe the execution of one or more tools that contribute to a computation.

2)  [Workflow Run Crate](https://w3id.org/ro/wfrun/workflow)
    to describe a computation orchestrated by a predefined workflow.

3)  [Provenance Run Crate](https://w3id.org/ro/wfrun/provenance)
    to describe a workflow computation including the internal details of individual step executions.


In the rest of this section we describe each of these profiles in detail. We use the term "class" to refer to a type as defined in RDF(s) and "entity" to refer to an instance of a class. We use italics to denote the properties and classes in each profile: these are defined in the RO-Crate  [JSON-LD context](https://www.researchobject.org/ro-crate/1.1/context.jsonld), which extends Schema.org with terms from the Bioschemas [[Gray 2017]]  [ComputationalWorkflow profile](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) and other vocabularies.
Note that terms coming from Bioschemas are not specific to the life sciences.
We also developed a [dedicated term set](https://w3id.org/ro/terms/workflow-run#) to represent concepts that are not captured by terms in the RO-Crate context. New terms are defined in RDF(s) following Schema.org guidelines (i.e., using `domainIncludes` and `rangeIncludes` to define domains and ranges of properties).

In the rest of the text and images, the following prefixes are used to represent the corresponding namespaces:

| Prefix        |     | Namespace                                 |
| ------------: | :-: | ----------------------------------------- |
|          *s:* |  →  | <https://schema.org/>                     |
| *bioschemas:* |  →  | <https://bioschemas.org/>                 |
|        *bsp:* |  →  | <https://bioschemas.org/properties/>      |
|      *wfrun:* |  →  | <https://w3id.org/ro/terms/workflow-run#> |
|       *prov:* |  →  | <http://www.w3.org/ns/prov#>              |


### Process Run Crate {#process-run-crate}

The Process Run Crate profile [[WRROC 2024a]] contains specifications to describe the execution of one or more software applications that contribute to the same overall computation, but are not necessarily coordinated by a top-level workflow or script (e.g. when executed manually by a human, one after the other as intermediate datasets become available).

The Process Run Crate is the basis for all profiles in the WRROC collection. It specifies how to describe the fundamental classes involved in a computational run:

i. a software application represented by a [`s:SoftwareApplication`](https://schema.org/SoftwareApplication), [`s:SoftwareSourceCode`](http://schema.org/SoftwareSourceCode) or [](https://bioschemas.org/ComputationalWorkflow) class; and

ii. its execution, represented by a [`s:CreateAction`](http://schema.org/CreateAction) class, and linking to the application via the [`s:instrument`](http://schema.org/instrument) property.

Other important properties of the
[`s:CreateAction`](http://schema.org/CreateAction) class are [`s:object`](http://schema.org/object), which links to the action's inputs, and [`s:result`](http://schema.org/result), which links to its outputs.
The time the execution started and ended can be provided, respectively, via the
[`s:startTime`](http://schema.org/startTime) and [`s:endTime`](http://schema.org/endTime) properties.
The [`s:Person`](http://schema.org/Person) or
[`s:Organization`](http://schema.org/Organization) class that performed the action is specified via the [`s:agent`](http://schema.org/agent) property.
[Figure 1](#fig:process_crate_er) shows the classes used in Process Run Crate together with their relationships.



{{< figure src="wrroc-figure1.drawio.svg" link="wrroc-figure1.drawio.svg" id="fig:process_crate_er" 
  width="60%" title="UML class diagram for Process Run Crate"
  caption="The central class is the [`s:CreateAction`](http://schema.org/CreateAction), which represents the execution of an application. It links to the application itself via [`s:instrument`](http://schema.org/instrument), to the entity that executed it via [`s:agent`](http://schema.org/agent), and to its inputs and outputs via [`s:object`](http://schema.org/object) and [`s:result`](http://schema.org/result), respectively. In this and following figures, classes and properties are shown with prefixes to indicate their origin. Some inputs (and, less commonly, outputs) are not stored as files or directories, but passed to the application (e.g., via a command line interface) as values of various types (e.g., a number or string). In this case, the profile recommends a representation via [`s:PropertyValue`](http://schema.org/PropertyValue). For simplicity, we left out the rest of the RO-Crate structure (e.g. the root [`s:Dataset`](http://schema.org/Dataset)), and attributes (e.g. [`s:startTime`](http://schema.org/startTime), [`s:endTime`](http://schema.org/endTime), [`s:description`](http://schema.org/description), [`s:actionStatus`](http://schema.org/actionStatus)). In this UML class notation, diamond <samp>◇</samp> arrows indicate aggregation and regular arrows indicate references, <samp>*</samp> indicates zero or more occurrences, <samp>1</samp> means single occurrence." >}}



As an example,
suppose a user named John Doe runs the UNIX command `head` to extract the first ten lines of an input file named `lines.txt`, storing the result in another file called `selection.txt`.
John then runs the `sort`
UNIX command on `selection.txt`, storing the sorted output in a new file named `sorted_selection.txt`.


[Figure 2](#fig:head_sort) contains a diagram of the two actions and their relationships to the other involved entities.
Note how the actions are connected by the fact that the output of `Run Head` is also the input of `Run Sort`: they form an "implicit workflow", whose steps have been executed manually rather than by a software tool.

{{< figure src="wrroc-figure-example.drawio.svg" link="wrroc-figure-example.drawio.svg" id="fig:head_sort" 
  width="75%" title="Diagram of a simple workflow"
  caption="where the `head` and `sort` programs were run manually by a user. The executions of the individual software programs are connected by the fact that the file output by `head` was used as input for `sort`, documenting the computational flow in an implicit way. Such executions can be represented with Process Run Crate." >}}


Process Run Crate extends the RO-Crate guidelines on representing software used to create files with additional requirements and conventions.
This arrangement is typical of the RO-Crate approach, where the base specification provides general recommendations to allow for high flexibility, while profiles -- being more concerned with the representation of specific domains and machine actionability -- provide more detailed and structured definitions.
Nevertheless, in order to be broadly applicable, profiles also need to avoid the specification of too many strict requirements, trying to strike a good trade-off between flexibility and actionability.


### Workflow Run Crate {#workflow-run-crate}

The Workflow Run Crate profile [[WRROC 2024b]] combines the Process Run Crate and WorkflowHub's Workflow RO-Crate [[Bacall 2022]] profiles to describe the execution of computational workflows managed by a WMS.
Such workflows are typically written in a domain-specific language, such as CWL or Snakemake
[[Koster 2012]], and run by one or more WMS (e.g., StreamFlow [[Colonnelli 2021]], Galaxy [[Galaxy 2022]]).
[Figure 3](#fig:workflow_crate_er) illustrates the classes used in this profile together with their relationships.
As in Process Run Crate, the execution is described by a [`s:CreateAction`](http://schema.org/CreateAction)
that links to the application via [`s:instrument`](http://schema.org/instrument), but in this case the application must be a workflow, as prescribed by Workflow RO-Crate.
More specifically, Workflow RO-Crate states that the RO-Crate must contain a main workflow typed as *File* (an RO-Crate mapping to [`s:MediaObject`](http://schema.org/MediaObject)), [`s:SoftwareSourceCode`](http://schema.org/SoftwareSourceCode)
and [`bioschemas:ComputationalWorkflow`](https://bioschemas.org/ComputationalWorkflow).
The execution of the individual workflow steps, instead, is not represented: that is left to the more detailed Provenance Run Crate profile (described in the next section).

The Workflow Run Crate profile also contains recommendations on how to represent the workflow's input and output parameters, based on the Bioschemas ComputationalWorkflow profile.
All these elements are represented via the [`bioschemas:FormalParameter`](https://bioschemas.org/FormalParameter) class and are referenced from the main workflow via the [`bsp:input`](https://bioschemas.org/properties/input) and
[`bsp:output`](https://bioschemas.org/properties/output) properties.
While the classes referenced from
[`s:object`](http://schema.org/object) and [`s:result`](http://schema.org/result) in the [`s:CreateAction`](http://schema.org/CreateAction) represent data entities and argument values that were actually used in the workflow execution, the ones referenced from [`bsp:input`](https://bioschemas.org/properties/input) and
[`bsp:output`](https://bioschemas.org/properties/output) correspond to formal parameters, which acquire a value when the workflow is run (see Fig [3](#fig:workflow_crate_er)).
In the profile, the relationship between an actual value and the corresponding formal parameter is expressed through the [`s:exampleOfWork`](http://schema.org/exampleOfWork) property.
For instance, in the following JSON-LD snippet a formal parameter (`#annotations`) is illustrated together with a corresponding `final-annotations.tsv` file:

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

{{< figure src="wrroc-figure2.drawio.svg" link="wrroc-figure2.drawio.svg" id="fig:workflow_crate_er" 
  width="75%" title="UML class diagram for Workflow Run Crate"
  caption="The main differences with Process Run Crate are the representation of formal parameters and the fact that the workflow is expected to be an entity with types [`s:MediaObject`](http://schema.org/MediaObject) (*File* in RO-Crate JSON-LD), [`s:SoftwareSourceCode`](http://schema.org/SoftwareSourceCode) and [`bioschemas:ComputationalWorkflow`](https://bioschemas.org/ComputationalWorkflow). Effectively, the workflow belongs to all three types, and its properties are the union of the properties of the individual types. In this profile, the execution history (retrospective provenance) is augmented by a (prospective) workflow definition, giving a high-level overview of the workflow and its input and output parameter definitions ([`bioschemas:FormalParameter`](https://bioschemas.org/FormalParameter)). The inner structure of the workflow is not represented in this profile. In the provenance part, individual files ([`s:MediaObject`](http://schema.org/MediaObject)) or arguments ([`s:PropertyValue`](http://schema.org/PropertyValue)) are then connected to the parameters they realise. Most workflow systems can consume and produce multiple files, and this mechanism helps to declare each file's role in the workflow execution. The filled diamond <samp>⬧</samp> indicates composition, empty diamond <samp>◇</samp> aggregation, and other arrows relations." >}}


### Provenance Run Crate {#provenance-run-crate}


The Provenance Run Crate profile [[WRROC 2024c]] extends Workflow Run Crate by adding new concepts to describe the internal details of a workflow run, including individual tool executions, intermediate outputs and related parameters.
Individual tool executions are represented by additional [`s:CreateAction`](http://schema.org/CreateAction) instances that refer to the tool itself via [`s:instrument`](http://schema.org/instrument) -- analogously to its use in Process Run Crate.
The workflow is required to refer to the tools it orchestrates through the [`s:hasPart`](http://schema.org/hasPart) property, as suggested in the Bioschemas ComputationalWorkflow profile, though in the latter it is only a recommendation.

To represent the logical steps defined by the workflow, this profile uses [`s:HowToStep`](http://schema.org/HowToStep) -- i.e., "A step in the instructions for how to achieve a result" [[howtostep-def]].
Steps point to the corresponding tools via the [`s:workExample`](http://schema.org/workExample) property and are referenced from the workflow via the [`s:step`](http://schema.org/step) property; the execution of a step is represented by a [`s:ControlAction`](http://schema.org/ControlAction) pointing to the
[`s:HowToStep`](http://schema.org/HowToStep) via [`s:instrument`](http://schema.org/instrument) and to the [`s:CreateAction`](http://schema.org/CreateAction)
entities that represent the corresponding tool execution(s) via
[`s:object`](http://schema.org/object).
Note that a step execution does not coincide with a tool execution: an example where this distinction is apparent is when a step maps to multiple executions of the same tool over a list of inputs (e.g. the "scattering" feature in CWL).

An RO-Crate following this profile can also represent the execution of the WMS itself (e.g., cwltool) via
[`s:OrganizeAction`](http://schema.org/OrganizeAction), pointing to a representation of the WMS via
[`s:instrument`](http://schema.org/instrument), to the steps via [`s:object`](http://schema.org/object) and to the workflow run via [`s:result`](http://schema.org/result).
The [`s:object`](http://schema.org/object) attribute of the
[`s:OrganizeAction`](http://schema.org/OrganizeAction) can additionally point to a configuration file containing a description of the settings that affected the behaviour of the WMS during the execution.
Fig [4](#fig:provenance_crate_er) illustrates the various classes involved in the representation of a workflow run via Provenance Run Crate together with their relationships.


{{< figure src="wrroc-figure3.drawio.svg" link="wrroc-figure3.drawio.svg" id="fig:provenance_crate_er" 
  width="100%" title="UML class diagram for Provenance Run Crate"
  caption="In addition to the workflow run, this profile represents the execution of individual steps and their related tools. The prospective side (the execution plan) is shown by the workflow listing a series of [`s:HowToStep`](http://schema.org/HowToStep)s, each linking to the [`s:SoftwareApplication`](http://schema.org/SoftwareApplication) that is to be executed. The [`bsp:input`](https://bioschemas.org/properties/input) and [`bsp:output`](https://bioschemas.org/properties/output) parameters for each tool are described in a similar way to the overall workflow parameter in [Figure 3](#fig:workflow_crate_er). The retrospective provenance side of this profile includes each tool execution as an additional [`s:CreateAction`](http://schema.org/CreateAction) with similar mapping to the realised parameters as [`s:MediaObject`](http://schema.org/MediaObject) or [`s:PropertyValue`](http://schema.org/PropertyValue), allowing intermediate values to be included in the RO-Crate even if they are not workflow outputs. <br>The workflow execution is described the same as in the Workflow Run Crate profile with an overall [`s:CreateAction`](http://schema.org/CreateAction) (the workflow outputs will typically also appear as outputs from inner tool executions). An additional [`s:OrganizeAction`](http://schema.org/OrganizeAction) represents the workflow engine execution, which orchestrated the steps from the workflow plan through corresponding [`s:ControlAction`](http://schema.org/ControlAction)s that spawned the tool's execution ([`s:CreateAction`](http://schema.org/CreateAction)). It is possible that a single workflow step had multiple such executions (e.g. array iterations). Not shown in figure: [`s:actionStatus`](http://schema.org/actionStatus) and [`s:error`](http://schema.org/error) to indicate step/workflow execution status. The filled diamond <samp>⬧</samp> indicates composition, empty diamond <samp>◇</samp> aggregation, and other arrows relations." >}}

Additionally, this profile specifies how to describe connections between parameters,
through *parameter connections* -- a fundamental feature of computational workflows.
Specifically, parameter connections describe: (i) how tools consume as input the intermediate outputs generated by other tools; and (ii) how workflow-level parameters are mapped to tool-level parameters.
As an example, consider again the workflow depicted in Fig [2](#fig:head_sort),
and suppose it is implemented in a workflow language such as CWL: the workflow-level input (a text file) is linked through a parameter connection to the input of the `head` tool wrapper, and then a second parameter connection links this tool's output to the input of the `sort` tool wrapper.
A representation of parameter connections is particularly useful for traceability, since it provides the means to document the inputs and tools on which workflow outputs depend.
Since the current RO-Crate context has no suitable terms for the description of such relationships,
we added appropriate ones to the aforementioned dedicated term set [[wrroc-terms]]:
a [`wfrun:ParameterConnection`](https://w3id.org/ro/terms/workflow-run#ParameterConnection) type with
[`wfrun:sourceParameter`](https://w3id.org/ro/terms/workflow-run#sourceParameter) and [`wfrun:targetParameter`](https://w3id.org/ro/terms/workflow-run#targetParameter) attributes that respectively map to the source and target formal parameters, and a
[`wfrun:connection`](https://w3id.org/ro/terms/workflow-run#connection) property to link from the relevant step or workflow to the [`wfrun:ParameterConnection`](https://w3id.org/ro/terms/workflow-run#ParameterConnection) instances.

In our set of profiles, Provenance Run Crate is the most detailed one and offers the highest level of granularity; its specification is a superset of Workflow Run RO-Crate, which in turn is a superset of Process Run Crate. This relationship between the three profiles is illustrated in Fig [5](#fig:profile_venn), as a Venn diagram.
Theoretically, all computational provenance information could be represented through the Provenance Run Crate profile alone (possibly relaxing some requirements), since it inherits from the other ones. In practice, though, this choice would require the use of the most complex model even for simple use cases. 

Having three separate profiles provides a way to represent information at different levels of granularity, while keeping all RO-Crates generated with them interoperable. This approach gives a straightforward path to supporting the representation of computational provenance in simpler use cases such as with simple command executions, i.e. the Process Run Crate. Additionally, the approach lowers the accessibility barrier for implementation in WMSs, as developers may choose to initially implement only the more basic support in their WMS, with reduced effort and complexity, and gradually scale to more detailed representations. This encourages the adoption of WRROC across the diverse landscape of use cases and WMSs.

{{< figure src="wrroc-venn.drawio.svg" link="wrroc-venn.drawio.svg" id="fig:profile_venn" 
  width="60%" title="Venn diagram of the specifications for the various RO-Crate profiles"
  caption="Process Run Crate specifies how to describe the fundamental classes involved in a computational run, and thus is the basis for all profiles in the WRROC collection. Workflow Run Crate inherits the specifications of both Process Run Crate and Workflow RO-Crate. Provenance Run Crate, in turn, inherits the specifications of Workflow Run Crate (and in a sense includes multiple Process Runs for each step execution, but within a single Crate)." >}}


### Profile formats {#formats}

The WRROC profiles are available both in human-readable (HTML) and in machine-readable format (RO-Crate). The human-readable profiles are at:

-   <https://w3id.org/ro/wfrun/process/0.5>
-   <https://w3id.org/ro/wfrun/workflow/0.5>
-   <https://w3id.org/ro/wfrun/provenance/0.5>

And the corresponding machine-readable ones at:

-   <https://doi.org/10.5281/zenodo.12158562>
-   <https://doi.org/10.5281/zenodo.12159311>
-   <https://doi.org/10.5281/zenodo.12160782>

The RO-Crate metadata files for the machine readable profiles can be retrieved using the same URLs as the human-readable ones, but with JSON-LD content negotiation: this is done by setting `"Accept:application/ld+json"` in the HTTP header.

The new terms we defined to represent concepts that could not be expressed with existing Schema.org ones are at:

-   <https://w3id.org/ro/terms/workflow-run#>

These terms are available in multiple formats with content negotiation, as explained at the above link.


## Implementations {#implementations}


Support for the Workflow Run RO-Crate profiles presented in this work has been implemented in a number of systems, showing support from the community and demonstrating their usability in practice.
We describe seven of these implementations (one in a conversion tool and six in WMS) in the following sections.
[Table  1](#implementation_summary_table) provides an overview of the implementations, along with the respective profile implemented, and links to the implementation itself and to an example RO-Crate.
These tools have been developed in parallel by different teams, and independently from each other.
RO-Crate has a strong ecosystem of tools \[[Soiland-Reyes 2022a], section [Tooling](../../../2022/phd/ro-crate/#tooling)\], and the WRROC implementations have either re-used these or added their own approach to the standards.





### Summary of implementations

[Table 1](#implementation_summary_table) shows an overview of the different implementations presented in this section.

<div id="implementation_summary_table">

| **Implementation**        | **Profile** | **Version URL/DOI**    | **Example**            |
| ------------------------- | ----------- | ---------------------- | ---------------------- |
| [runcrate](#runcrate)     | Provenance  | \[[Leo 2023a]\]        | \[[Leo 2023]\]         |
| [Galaxy](#galaxy)         | Workflow    | \[[Afgan 2023]\]       | \[[De Geest 2023b]\]   |
| [COMPSs](#compss)         | Workflow    | \[[Ejarque 2023]\]     | \[[Poiata 2023]\]      |
| [Streamflow](#streamflow) | Provenance  | \[[Colonnelli 2023b]\] | \[[Colonnelli 2023a]\] |
| [WfExS](#wfexs)           | Workflow    | \[[Fernández 2023a]\]  | \[[Fernández 2023b]\]  |
| [Sapporo](#sapporo)       | Workflow    | \[[Suetake 2023b]\]    | \[[Ohta 2023]\]        |
| [Autosubmit](#autosubmit) | Workflow    | \[[Beltrán 2023]\]     | \[[Kinoshita 2023]\]   |

_**Table 1**: **Workflow Run Crate implementations**. Summary of each WRROC implementation, together with the profiles it implements, the software version that makes it available and an example RO-Crate. Runcrate is a toolkit that converts CWLProv ROs to Provenance Run Crates, while the others are workflow management systems._

</div>


### Runcrate {#runcrate}

[Runcrate](https://github.com/ResearchObject/runcrate) [[runcrate]] is a Workflow Run RO-Crate toolkit which also serves as a reference implementation of the proposed profiles.
It consists of a Python package with a command line interface, providing a straightforward path to integration in Python software and other workflows.
The runcrate toolkit includes functionality to convert CWLProv ROs to RO-Crates conforming to the Provenance Run Crate profile (`runcrate convert`), effectively providing an indirect implementation of the format for cwltool.

Indeed, the CWLProv model provided a basis for the Provenance Run Crate profile, and the implementation of a conversion tool in runcrate at times drove the improvement and extension of the profile as new requirements or gaps in the old designs emerged.
Runcrate converts both the retrospective provenance part of the CWLProv RO (the RDF graph of the workflow's execution) and the prospective provenance part (the CWL files, including the workflow itself).
Both parts are thus converted into a single, workflow-language-agnostic metadata resource.

Another functionality offered by the runcrate package is `runcrate report`, which reports on the various executions described in an input RO-Crate, listing their starting and ending times, the values of the various parameters, etc.
Runcrate report demonstrates how the provenance profiles presented in this work enable comparison of runs interoperably across different workflow languages or different implementations of the same language.
This functionality has also been used as a lightweight validator for the various implementations.

Runcrate also includes a `run` subcommand to re-execute the computation described by an input Workflow Run Crate or Provenance Run Crate where CWL is used as a workflow language.
It works by mapping the RO-Crate description of input parameters and their values (the workflow's
[`bsp:input`](https://bioschemas.org/properties/input) and the action's [`s:object`](http://schema.org/object)) to the format expected by CWL, which is then used to relaunch the workflow on the input data.
This functionality shows the machine-actionability of the profiles to support reproducibility, and was used to successfully re-execute the digital pathology annotation workflow described in Section [4.1](#provenance-run-crate-for-digital-pathology).

Of course, achieving a full re-execution in the general case may not always be possible: reproducibility is supported by the profiles, but also benefits from specific characteristics of the workflow language (which should provide a clear formalism to map input items to their corresponding parameter slots) and of the specific workflow's implementation, which can be made considerably easier to reproduce by containerising the computational environment required by each step (if allowed by the workflow language).


### Galaxy {#galaxy}

The Galaxy project [[Galaxy 2022]] provides a WMS with data management functionalities as a multi-user platform, aiming to make computational biology more accessible to research scientists that do not have computer programming or systems administration experience.
Galaxy's most prominent features include: a collection of 7500+ integrated [tools](https://galaxyproject.org/toolshed/) [[Blankenberg 2014]];
a web interface that allows the definition and execution of workflows using the integrated tools; a network of dedicated (public) Galaxy instances.

The export of workflow execution provenance data as Workflow Run Crates was added to Galaxy in version 23 [[Galaxy 2023]] providing a more interoperable alternative to the basic export of Galaxy workflow
*invocations*. A WRROC export from Galaxy includes: the workflow definition; a set of serialisations of the invocation-related metadata in Galaxy native, JSON-formatted files;
and the input and output data files.
This result is achieved by:

1) extracting provenance data from Galaxy entities related to the workflow run, along with their associated metadata;

2) converting them to RO-Crate metadata using the ro-crate-py library [[ro-crate-py]];

3) describing all files contained in the basic invocation export within the RO-Crate metadata; and

4) making the Workflow Run Crate available for export to the user through Galaxy's web interface and API [[De Geest 2022b]].



We extract the prospective provenance contained in Galaxy's YAML-based gxformat2
[gxformat2](https://galaxyproject.github.io/gxformat2/v19_09.html)  workflow definition, which includes details of the analysis pipeline such as the graph of the tools that need to be executed and metadata about the data types required.
The retrospective provenance -- i.e., the details of the executed workflow, such as the inputs, outputs, and parameter values used -- is extracted from Galaxy's [data model](https://docs.galaxyproject.org/en/master/lib/galaxy.model.html),
which is not directly accessible to users in the context of a public Galaxy server.
All of this provenance information is then mapped to RO-Crate metadata, including some Galaxy-specific data entities such as dataset collections.
An exemplary Workflow Run Crate exported from Galaxy, through its *Workflow Invocations* list, is available on Zenodo [[De Geest 2023]].

In practice, a user would take the following steps to obtain a Workflow Run Crate from a Galaxy instance:

1)  Create or download a Galaxy workflow definition (e.g.: from WorkflowHub) and import it in a Galaxy instance, or create a workflow through the Galaxy GUI directly.

2)  Execute the workflow, providing the required inputs.

3)  After the workflow has run successfully, the corresponding RO-Crate will be available for export from the Workflow Invocations list.


### COMPSs {#compss}


[COMPSs](https://www.bsc.es/research-and-development/software-and-apps/software-list/comp-superscalar) [[Lordan 2014]] is a task-based programming model that allows users to transform a sequential application into a parallel one by simply annotating some of its methods, thus facilitating scaling applications to increasing amounts of computing resources.
When a COMPSs application is executed, a corresponding workflow describing the application's tasks and their data dependencies is dynamically generated and used by the COMPSs runtime to orchestrate the execution of the application in the infrastructure.
As a WMS, COMPSs stands out for its many advanced features that enable applications to achieve fine-grained high efficiency in HPC systems, such as the ability to exploit underlying parallelisation frameworks (e.g. MPI [[Gabriel 2004]], OpenMP [[Dagum 1998]]), compilers (e.g. NUMBA [[Lam 2015]]), failure management, task grouping, and more. Also, provenance recording for COMPSs workflows has been explored in previous work [[Sirvent 2022]], where the Workflow RO-Crate profile was used to capture structured descriptive metadata about the executed workflow, without introducing any significant run time performance overheads.

In this work, COMPSs has been further improved by implementing the generation of provenance
information conformant to the Workflow Run Crate profile, thus also capturing
details about the actual execution of the workflow.
The dynamic nature of COMPSs workflows poses some challenges to capturing
provenance, which were met thanks to the instruments
provided by the WRROC model.
For instance, a COMPSs workflow is created when the application is executed and, thus, a prior static workflow definition does not exist before that moment.
Due to this design, the workflow entity in the metadata file references the entry point application run by COMPSs -- instead of, for instance, a dedicated workflow definition file as one might find with other WMSs. Also, formal parameters are not included in the prospective provenance (note that specifying them is not required by the profile) because inputs and outputs (both for each task and the whole workflow) are determined at runtime.
However, the RO-Crate generation by COMPSs leverages the information recorded by the runtime to automatically add metadata of all input or output data assets used or produced by the workflow.

Because of the supercomputing environments where COMPSs is used, the integration of Workflow Run Crate support required paying particular attention to the generation of a unique ID for the [`s:CreateAction`](http://schema.org/CreateAction) representing the workflow run. Our implementation uses UUIDs for distributed environments, while it adds a combination of hostname and queuing system job ID for supercomputer executions, to provide as much information as possible from the run while preserving ID uniqueness.
In the [`s:CreateAction`](http://schema.org/CreateAction), the [`s:description`](http://schema.org/description) term includes system information, as well as relevant environment variables that provide details on the execution environment (e.g., node list, CPUs per node).
Finally, the [`s:subjectOf`](http://schema.org/subjectOf) property of the [`s:CreateAction`](http://schema.org/CreateAction) references the system's monitoring tool (when available),
where authorised users can see detailed profiling of the corresponding job execution, as provided by the [MareNostrum IV supercomputer](https://bsc.es/supportkc/docs/MareNostrum4/intro/).

To showcase the COMPSs adoption of the Workflow Run Crate profile, we provide as an example the execution of the BackTrackBB [[Poiata 2016]]
application in the MareNostrum IV supercomputer.
BackTrackBB targets the detection and location of seismic sources using the statistical coherence of the wave field recorded by seismic networks and antennas.
The resulting RO-Crate [[Poiata 2023]] captures the provenance of the execution results and complies with the Workflow Run Crate profile. It includes the application source files, a diagram of the workflow's graph, application profiling and input and output files.

The implementation of provenance recording using Workflow Run Crate has been fully integrated in the COMPSs runtime and is available as of release 3.2 [[Ejarque 2023]].


### StreamFlow {#streamflow}

The [StreamFlow](https://github.com/alpha-unito/streamflow) framework [[Colonnelli 2021]] is a container-native WMS for the execution of workflows defined in CWL.
It has been designed around two primary principles: first, it allows the execution of tasks in multi-container environments, supporting the concurrent execution of communicating tasks in a multi-agent ecosystem; second, it relaxes the requirement of a single shared data space, allowing for hybrid workflow executions on top of multi-cloud, hybrid cloud/HPC, and federated infrastructures.
StreamFlow orchestrates hybrid workflows by combining a *workflow description* (e.g., a CWL workflow description and a set of input values) with one or more *deployment descriptions* -- i.e.
representations of the execution environments in terms of infrastructure-as-code (e.g., Docker Compose files [[Reis 2022]], HPC batch scripts, and Helm charts [[Zerouali 2023]]).
A `streamflow.yml` file -- the entry point of each StreamFlow execution -- binds each workflow step with the set of most suitable execution environments.
At execution time, StreamFlow automatically takes care of all the secondary aspects, like scheduling, checkpointing, fault tolerance, and data movements.

StreamFlow collects prospective and retrospective provenance data in a custom format and persists it into a pluggable database (using sqlite3 as the default choice).
After a CWL workflow execution completes, users can generate an RO-Crate through the `streamflow prov`
command, which extracts the provenance data stored in the database for one or more workflow executions and converts it to an RO-Crate archive that is fully compliant with the Provenance Run Crate Profile, including the details of each task run by the WMS.
Support for the format has been integrated into the main development branch and will be included in release 0.2.0 [[Colonnelli 2023b]].

From the StreamFlow point of view, the main limitation in the actual version of the Provenance Run Crate standard is the lack of support for distributed provenance -- i.e., a standard way to describe the set of locations involved in a workflow execution and their topology. As a temporary solution,
the StreamFlow configuration and a description of the hybrid execution environment are preserved by directly including the `streamflow.yml` file into the generated archive.
However, this product-specific solution prevents a wider adoption from other WMS and forces agnostic frameworks (e.g., WorkflowHub) to provide ad-hoc plugins to interpret the StreamFlow format.
Since the support for hybrid and cross-facility workflows is gaining traction in the WMS ecosystem, we envision support for distributed provenance as a feature for future versions of Workflow Run RO-Crate.


### WfExS-backend {#wfexs}

[WfExS-backend](https://github.com/inab/WfExS-backend) [[Fernandez 2024a]] is a FAIR workflow execution orchestrator that aims to address some of the difficulties found in analysis reproducibility and analysis of sensitive data in a secure manner.
WfExS-backend requires that the software used by workflow steps is available in publicly accessible software containers for reproducibility.

Actual workflow execution is delegated to one of the supported workflow engines -- currently either Nextflow [[Di Tommaso 2017]] or cwltool.
The orchestrator prepares and stages all the elements needed to run the workflow -- i.e. all the files of the workflow itself, the specific version of the workflow engine, the required software containers and the inputs.
All these elements are referenced through resolvable identifiers, ideally public, permanent ones.

Thanks to this approach, the orchestrator can consume workflows from various types of sources, such as git repositories, Software Heritage, or even RO-Crates from WorkflowHub.
WfExS-backend development milestones have aimed to reach FAIR workflow execution through the generation and consumption of RO-Crates following the Workflow Run Crate profile, which has proven to be a mechanism suitable to semantically describe digital objects in a way that simplifies embedding details crucial to analysis reproducibility and replicability.

When the orchestrator prepares a workflow for execution it records details relevant to the prospective provenance, such as the public URLs used to fetch input data and workflows, content digestion fingerprints (typically sha256 checksums) and metadata derived from workflow files, container images and input files.
Most of this captured metadata is later included in the generated RO-Crates. WfExS-backend has explicit commands to generate and publish both prospective and retrospective provenance RO-Crates based on a given existing staged execution scenario.
These RO-Crates can selectively include copies of used elements as payloads.
Workflows can be executed more than once in the same staged directory, with all the executions sharing the same inputs.
In this case, run details from all the executions are represented in the retrospective provenance RO-Crate. 

Support for the consumption of Workflow Run RO-Crates to reproduce the operations they document is available as of WfExS-backend version 1.0.0a0 [[Fernandez 2024a]].
We have created examples of Workflow Run Crates generated by WfExS-backend to capture provenance information from the execution of a Nextflow workflow [[Bouyssie 2023]] and a CWL workflow [[Amstutz 2023]]; these crates are both available on Zenodo [[Fernandez 2024b Fernandez 2024c]].
Future developments to WfExS-backend will also add support for embedding in the RO-Crates the URLs of output results that have been deposited into a suitable repository (like Zenodo DOIs, for instance).


### Sapporo {#sapporo}

[Sapporo](https://github.com/sapporo-wes/sapporo) \[[Suetake 2022]\] iis an implementation of the Workflow Execution Service (WES) API specification [[Rehm 2021]].
WES is a standard proposed by the Global Alliance for Genomics and Health (GA4GH) for cloud-based data analysis platforms that receive requests to execute workflows.
Sapporo supports the execution of several workflow engines, including cwltool [[Amstutz 2023]], Toil [[Vivian 2017]], and StreamFlow [[Colonnelli 2021]].
Sapporo includes features specifically tailored to bioinformatics applications, including the calculation of feature statistics from specific types of outputs generated by workflow runs.
For example, the system calculates the mapping rate of DNA sequence alignments from BAM format files.
To describe the feature values, Sapporo uses the Workflow Run Crate profile extended with additional terms to represent these biological features [[sapporo-terms]].

Further, the Tonkaz companion command line software has integrated functionality to compare Run Crates generated by Sapporo to measure the reproducibility of the workflow outputs [[Suetake 2023]].
Developers can use this unique feature to build a CI/CD platform for their workflows to ensure that changes to the product do not produce an unexpected result.
Workflow users can also use this feature to verify the results from the same workflow deployed in different environments.

While Sapporo supports Workflow Run Crate, since WES is a WMS wrapper, it does not parse the provided workflow definition files.
Instead, it embeds the information in the files passed by the WES request to record the provenance of execution rather than using the actual workflow parameters meant for the wrapped WMS.
Therefore, the current implementation of Sapporo does not capture the connections between the inputs/outputs depicted in the workflow and the actual files used/generated during the run.
The profile generated by Sapporo has fields representing input and output files, but they are not linked to formal parameters.

Sapporo supports export to Workflow Run Crate as of release 1.5.1 [[Suetake 2023b]]. An example of a Workflow Run RO-Crate generated by Sapporo is available on Zenodo [[Ohta 2023]].

### Autosubmit {#autosubmit}

[Autosubmit](https://autosubmit.readthedocs.io/) \[[Manubens-Gil 2016]\] is an open source, lightweight workflow manager and meta-scheduler tailored to configuring and running scientific experiments in climate research. It supports scheduling jobs via SSH to Slurm [[Yoo 2003]], PBS [[Feng 2007]] and other remote batch servers used in HPC.

Autosubmit's "archive" feature archives the experiment directory and all its contents into a ZIP file, which can be used later to access the provenance data or to execute the Autosubmit experiment again.
Even though the data in the ZIP file includes prospective provenance and retrospective provenance, it is not structured, and a simple examination yields no way to distinguish the provenance types.

Recent releases of Autosubmit 4 have added features to increase user flexibility. An updated YAML configuration management system has been implemented that allows users to combine multiple YAML files into a single unified configuration file.
Also, the option to use only the experiment manager features of Autosubmit has been added, delegating the workflow execution to a different backend workflow engine -- like ecFlow [[Bahra 2011]], Cylc [[Oliver 2019]], or a CWL runner.
While these features provide some much appreciated flexibility, they have increased the complexity involved in reliably tracking the experiment configuration and other metadata for provenance documentation purposes.

In order to give users a more structured way to archive provenance, which includes the complete experiment configuration, the parameters used to generate it, and is also interoperable between workflow managers, the archive feature was enhanced with a new option in Autosubmit 4.0.100 [[Beltran 2023]] to enable the generation of provenance data in Workflow Run RO-Crates.
The prospective provenance data for the crate is extracted from the Autosubmit experiment configuration.
This data includes the multiple YAML files, the unified YAML configuration, as well as the parameters used to preprocess each file -- preprocessing replaces placeholders in script templates with values from the experiment configuration.

The retrospective provenance data is included with the RO-Crate archive and includes logs and other traces produced by the experiment workflow.
Both prospective and retrospective provenance data are included in the final RO-Crate, which is compliant with the Workflow Run Crate profile.
At a practical level, the implementation was able to leverage the `ro-crate-py` library for many of the details pertaining to the creation of the RO-Crate archive in Python, and adding information for the JSON-LD metadata.

One of the main challenges for implementing WRROC support in Autosubmit was incorporating Autosubmit's *Project* feature.
A Project in Autosubmit is an abstract concept that references a code repository and is used to define experiment configuration and contains template scripts defining workflow tasks and other auxiliary files.
The project has a type that defines the *type* of the repository (e.g., git) and a *location* that is the URL to retrieve it.
The RO-Crate file generated by Autosubmit includes the project type and location, but it does not include the complete Project and so it is lacking configuration details and scripts.
Therefore, users receive provenance data of the Project, but only those with the appropriate privileges can access its constituent resources (many applications run with Autosubmit can not be publicly shared without consent).

After consulting with the RO-Crate community regarding the specific Autosubmit requirements, the Autosubmit team adopted a mixed approach where Autosubmit initialises the JSON-LD metadata from its configuration and local trace files, and the user is responsible for providing a partial JSON-LD metadata object in the Autosubmit YAML configuration.
`ro-crate-py` was extended to allow the RO-Crate JSON-LD metadata to be patched by these partial JSON-LD metadata objects.
This way, users are able to provide the information that is missing from the Autosubmit configuration model, but is required by WRROC -- e.g., licence, authors, inputs, outputs, formal parameters, etc.

Future implementations of WRROC support should be facilitated by the new
functionality added to ro-crate-py to support the user-mediated metadata
integration approach.
On the other hand, the integration of WRROC support would have been facilitated by an automated validation tool for RO-Crate archives, and by documentation and examples on how to use the profiles with *coarse-grained* workflow management systems (as defined in [[Goble 2020]]) that do not track inputs and outputs, which is the case of Autosubmit -- as well as the Cylc and ecFlow workflow engines. The feedback generated by this use case was welcomed by the WRROC community and work to address these issues is either planned on under way at the time of writing.

To demonstrate Autosubmit's new WRROC-based functionality to generate structured provenance data, a workflow was created using an example Autosubmit Project designed using UFZ's mHM (mesoscale Hydrological Model) [[Samaniego 2010], [Kumar 2013]], and it was executed with Autosubmit. The resulting Workflow Run Crate is available from Zenodo [[Kinoshita 2023]].







## Exemplary Use Cases {#exemplary-use-cases}

We illustrate Workflow Run RO-Crate on two exemplary use cases. These are similar in terms of application domain, as they both relate to the application of machine learning techniques for the analysis of human prostate images for the purpose of supporting cancer tissue detection. However, the use cases are quite different in the way computations are executed and provenance is represented: in the first, the analysis is conducted by means of a CWL workflow and the outcome is represented with Provenance Run Crate; in the second, Process Run Crate is used in combination with a complementary model to represent a provenance chain that can extend beyond the computational analysis.


### Provenance Run Crate for Digital Pathology {#digital-pathology}

In this section, we present a use case that demonstrates the effectiveness of the Provenance Run Crate profile at capturing provenance data in the context of digital pathology.
More specifically, we demonstrate the generation of RO-Crates to save provenance data associated with the computational annotation of magnified prostate tissue areas and cancer subregions using deep learning models [[Del Rio 2022]].
The image annotation process is implemented in a CWL workflow consisting of three steps, each executing inference on an image using a deep learning model:

i) inference of a low-resolution tissue mask to select areas for further processing
ii) high-resolution tissue inference to refine borders
iii) high-resolution cancer tissue identification


The two tissue inference steps run the same tool, but set different values for the parameter that controls the magnification level, and the second runs on a subset of the image area.
The workflow is integrated in the CRS4 Digital Pathology Platform [[digital-pathology-platform]], a web-based platform to support clinical studies involving the examination and/or the annotation of digital pathology images.

To assess the interoperability of WRROC, we recorded the provenance of the execution of the same exemplary workflow on two different WMSs.
In the first case, we executed the CWL workflow with cwltool and converted the resulting CWLProv RO to a Provenance Run Crate with the runcrate tool (Section [3.1](#runcrate)).
In the second case, the workflow was executed with the StreamFlow WMS (Section [3.4](#streamflow)).
The RO-Crates obtained in the two cases [[run-pathology Colonnelli 2023]]
are very similar to each other, differing only in a few details. For instance, Streamflow includes its configuration file in the crate and has separate files for the workflow and the two tools, while
cwltool with runcrate results in the workflow and the tools being stored in a single file (CWL's "packed" format).
Apart from these minor differences, the description of the computation is essentially the same, so the RO-Crates are fully interoperable.
Four actions are represented: the workflow itself, the two executions of the tissue extraction tool and the execution of the tumour classification tool.
Each action is linked to the corresponding workflow or tool via the
[`s:instrument`](http://schema.org/instrument) property, and reports its starting and ending time. For each action, input and output slots are referenced by the workflow, while the corresponding values are referenced by the action itself.
The data and [`s:PropertyValue`](http://schema.org/PropertyValue) entities corresponding to the input and output values link to the corresponding parameter slots via the [`s:exampleOfWork`](http://schema.org/exampleOfWork) property, providing information on the values taken by the parameters during execution.
Listing [\[lst:ml\_pipeline\_streamflow\_report\]](#lst:ml_pipeline_streamflow_report) shows the output of the
`runcrate report` command for the StreamFlow RO-Crate.
For each action (workflow or tool run), runcrate reports the associated instrument (workflow or tool), the starting and ending time and the list of inputs and outputs, with pointers from the formal parameter to the corresponding actual value taken during the execution of the action.


<figure id="lst:ml_pipeline_streamflow_report>

```console
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
```

<figcaption>
  <h4>runcrate report command line output</h4>
  This informal listing of relevant RO-Crate entities describe each step execution. Note that inputs and outputs are of different types (not shown), e.g. `tissue_low>0.9` is a string parameter, `6b15de…` is a filename, `#af0253…` is a collection.
</figcaption>

</figure>


The [`s:exampleOfWork`](http://schema.org/exampleOfWork) link between input / output values and parameter slots is used by `runcrate run` to reconstruct the CWL input parameter mapping needed to rerun the computation.
The [`s:alternateName`](http://schema.org/alternateName) property (a Schema.org property applicable to all entities), which records the original name of data entities (at the time the computation was run), is also crucial for reproducibility in this case: both StreamFlow and CWLProv, to avoid clashes, record input and output files and directories using their SHA1
checksum as their names.
However, for this particular workflow file names are important: it expects the input image data to be in the [MIRAX](https://openslide.org/formats/mirax/) format, where the "main" dataset file taken as an input parameter by the processing application must be accompanied by a directory of additional data files, in the same location and with the same name, apart from the extension.
The runcrate tool uses the [`s:alternateName`](http://schema.org/alternateName) to rename the input dataset as required, so that the expected pattern can be picked up by the workflow during the re-execution.
This use case was the main motivation to include a recommendation to use [`s:alternateName`](http://schema.org/alternateName) with the above semantics in Process Run Crate.

Thanks to the fact that both RO-Crates were generated following the best practices to support reproducibility mentioned in the profiles, we were able to automatically re-execute both computations with the runcrate tool.
This was also made possible by the fact that the CWL workflow included information on which container images to use for each tool.
Overall, this shows how reproducibility is a hard-to-achieve goal that can only be supported, but not ensured, by the profiles, since it also depends on factors like the characteristics of the computation, the choice of workflow language and whether best practices such as containerisation are followed.

This use case highlighted the need to add specifications on how to represent multi-file datasets [[WRROC 2024a]], driven by the need to handle the aforementioned MIRAX image format.
To represent these, we added specifications to the Process Run Crate profile on [describing “composite” datasets](https://w3id.org/ro/wfrun/process/0.4#representing-multi-file-objects) consisting of multiple files and directories to be treated as a single unit -- as opposed to more conventional input or output parameters consisting of a single file. The profile specifies that such datasets should be represented by a [`s:Collection`](http://schema.org/Collection) class linking to individual files and directories via the [`s:hasPart`](http://schema.org/hasPart) property, and referencing the main part (if any) via the [`s:mainEntity`](http://schema.org/mainEntity) property. Note that, by adding this specification to Process Run Crate, we also made it available to Workflow Run Crate and Provenance Run Crate. In the output of the runcrate report tool the additional files are not shown, since the formal parameter points to the [`s:Collection`](http://schema.org/Collection) class that describes the whole dataset.

This use case also demonstrates the usage of parameter connections (described in Section [2.3](#provenance-run-crate)). The RO-Crate resulting from the workflow run contains a representation of all connections between workflow-level parameters (the overall input and output parameters) and tool-level parameters. This allows crate consumers to programmatically find which tool is affected by a workflow-level parameter, thus providing insight on how the workflow works internally (the main feature of the Provenance Run Crate profile). For instance, the `tissue-high-level` workflow parameter is connected to the `level` parameter of the `extract_tissue.cwl` tool by the `extract-tissue-high` step. This parameter regulates the resolution level (pyramidal images are organised into multiple levels of resolution) at which the image is processed in the high-resolution tissue extraction phase. A similar connection is present for the tissue extraction at low resolution. Since [`wfrun:ParameterConnection`](https://w3id.org/ro/terms/workflow-run#ParameterConnection)s are referenced from the relevant [`s:HowToStep`](http://schema.org/HowToStep), the crate consumer can easily determine the resolution level used for both image processing phases from the retrospective provenance.





### Process Run Crate and CPM RO-Crate for cancer detection {#cancer-detection}


This section presents an RO-Crate created to describe an execution of a computational pipeline that trains AI models to detect the presence of carcinoma cells in high-resolution digital images of magnified human prostate tissue.
This RO-Crate makes use of Process Run Crate and CPM RO-Crate [[cpm-ro-crate]], an RO-Crate profile that supports the representation of entities described according to the Common Provenance Model (CPM) [[Wittner 2022], [Wittner 2023b Wittner 2024]].

The CPM is a recently developed extension of the W3C PROV model [[Moreau 2013]]. It enables the representation of distributed provenance,
which is created when an object involved in the research process -- either digital or physical (e.g., biological material) -- is exchanged between organisations, so that each organisation can document only a portion of the object's life cycle.
Using CPM, each involed organisation can document its portion of the life cycle by generating, storing, and managing individual provenance components, which are then linked together in a chain that spans multiple organizations.

The CPM prescribes how to represent such provenance, and how to enable its traversal and processing using a common algorithm, independently from the type of object being described. In addition, the CPM defines a notion of meta-provenance, which contains metadata about the history of individual provenance components.

CPM RO-Crate supports the identification of CPM-based provenance and meta-provenance files within an RO-Crate, so that data, metadata, and CPM-based provenance information can be packed together.
An RO-Crate generated according to the CPM-RO-Crate profile embeds parts of the distributed provenance, which may be linked to the provenance of precursors and successors of the packed data.

The CPM-RO-Crate profile synergises well with Process Run Crate, since the former can add references to CPM-based provenance descriptions of computational executions described with the latter, integrating them in the distributed provenance. Since CPM-based provenance and meta-provenance files are typically themselves produced by computations, Process Run Crate allows to represent these along with the main computations that produce the datasets being exchanged, providing the full picture in a cohesive ensemble.

The use case pipeline consists of three main computational steps:

1) a preprocessing step that splits input images into small patches and divides them into a training and a testing set;
2) a training step that trains the model to recognise the presence of carcinoma cells in the images;
3) an evaluation step that measures the accuracy of the trained model on the testing set.

In addition to these pipeline steps, the RO-Crate describes additional computations related to the generation of the CPM provenance and meta-provenance files.
All computations are described according to the Process Run Crate profile, while the CPM files are referenced according to the CPM RO-Crate profile.

Also represented via Process Run Crate are: the input dataset; the results of the pipeline execution; the scripts that implement the pipeline; the log files generated by the scripts; a script that converts the logs into the CPM files.
This approach allowed us to describe all elements as a single RO-Crate, which
is available on Zenodo [[Wittner 2023a]].

Listing [\[lst:model\_training\_pipeline\_report\]](#lst:model_training_pipeline_report) presents the `runcrate report` output for the RO-Crate,
including action inputs and outputs while omitting other details. The listing shows the connections between the actions, forming an "implicit workflow" as discussed in [Section  2.1](#process-run-crate). For instance, the `prov_train.log` file is both an output of the training action (`#train_script:ROCRATE-PUB-…`) and an input of the CPM provenance generation action for the training phase (`#train_script:6efa9a06-…:CPM-provgen`), highlighting the interdependency between the steps.


<figure id="lst:model_training_pipeline_report>

```yaml
action: #convert_script:ff67ce65-736f-46d5-9fec-10953cad8695
  inputs:
    wsi/test/
    wsi/train/
    prov_converter_config.json
  outputs:
    cam16_mrxs.h5
    prov_preprocess.log

action: #test_script:ROCRATE-PUB-1438b57a750ce887d4433d9e
  inputs:
    prov_test_config.json
    cam16_mrxs.h5
  outputs:
    predictions.h5
    prov_test.log

action: #test_script:d3cfd9cf-6851-43c6-bee9-c8dc18f22368:CPM-provgen
  inputs:
    prov_test.log
  outputs:
    prov_test.provn
    prov_test.provn.log
    prov_test.png

action: #train_script:ROCRATE-PUB-1438b57a750ce887d4433d9e
  inputs:
    prov_train_config.json
    cam16_mrxs.h5
  outputs:
    prov_train.log
    model/weights/auc_01.ckpt.index
    model/weights/auc_01.ckpt.data-00000-of-00001
    model/weights/auc_02.ckpt.index
    model/weights/auc_02.ckpt.data-00000-of-00001
    model/weights/best_loss.ckpt.index
    model/weights/best_loss.ckpt.data-00000-of-00001
    model/weights/auc_03.ckpt.index
    model/weights/auc_03.ckpt.data-00000-of-00001

action: #train_script:6efa9a06-b8e9-4cfc-88c7-e9d35e5263c3:CPM-provgen
  inputs:
    prov_train.log
  outputs:
    prov_train.provn
    prov_train.png
    prov_train.provn.log

action: #convert_script:9d030b68-70d8-4526-82fe-160d9cfe4806:CPM-provgen
  inputs:
    prov_preprocess.log
  outputs:
    prov_preprocess.provn
    prov_preprocess.png
    prov_preprocess.provn.log

action: #meta_provn_script:86bae258-4c51-4215-854b-32cb49f239ab:CPM-provgen
  inputs:
    prov_train.provn.log
    prov_test.provn.log
    prov_preprocess.provn.log
  outputs:
    meta_provenance.provn
    meta_provenance.png
    meta_provenance.provn.log
```

<figcaption>
  <h4>
  
  Excerpt of the output of the `runcrate report` command for the AI model training Process Run Crate
  
  </h4>

  Only inputs and outputs of the actions are shown. The listing shows the connections between the pipeline actions through the entities they produce or consume -- e.g., `cam16_mrxs.h5` is output of the conversion script `convert_script:ff67…` and input for the training script `train_script:ROCRATE…`.

</figcaption>

</figure>


The CPM files complement the RO-Crate with details about the pipeline execution process, such as how the input dataset was split into training and testing sets, or detailed information about each training iteration of the AI model.
For instance, the RO-Crate contains a representation of a checkpoint of the AI model after the second training iteration, with the corresponding entity's attributes containing paths to the respective model stored as a file.
The entity is related to the respective training iteration activity, which contains the iteration parameters represented as an attribute list.

In addition, the CPM generally provides means to link the input dataset provenance to the provenance of its precursors -- human prostate tissues and biological samples the tissues were derived from; this is not included in the example because we used a publicly available input database for which provenance of the precursors was not available.
However, the linking mechanism for provenance precursors is exactly the same as between the bundles for the AI pipeline parts.

While the RO-Crate is focused on the execution of the pipeline, the provenance included in the CPM files intends to be interlinked with provenance of the precursors or successors, providing means to traverse the whole provenance chain.
For the described digital pathology pipeline, the precursors would be:

1) a biological sample acquired from a patient;

2) slices of the sample processed and put on glass slides;

3) the images created as a result of scanning the slides using a microscope.

As a result, combining the CPM and RO-Crate enables the lookup of research artefacts related to the computation across heterogeneous organisations using the underlying provenance chain.




## Discussion

The RO-Crate profiles presented in this work provide a unified data model to describe the prospective and retrospective provenance of the execution of a computational workflow, together with contextual metadata about the workflow itself and its associated entities (inputs, outputs, code, etc.).
The profiles are flexible, allowing one to tailor the provenance description to a broad variety of use cases, agnostic to the WMS used, and allow describing provenance traces at different levels of granularity.
These characteristics facilitate implementing support in workflow systems. Six WMS have already integrated support for a WRROC profile, as described in Section [3](#implementations). These new RO-Crate profiles enable interoperability between implementations, which has been demonstrated through the comparison of workflow executions on heterogeneous systems.

Choosing to base our approach on the RO-Crate model has led to a number of benefits. The collected provenance data can be treated with standard RDF tools. As an example, the following SPARQL [[sparql11-overview]] query returns all actions in a Workflow Run RO-Crate, together with their instruments and their starting and ending times, independently of the original workflow type or the WMS that executed the workflow:


<figure id="sparql">

```sparql
PREFIX schema: <http://schema.org/>
SELECT ?action ?instrument ?start ?end
WHERE {
  ?action a schema:CreateAction .
  ?action schema:instrument ?instrument .
  OPTIONAL { ?action schema:startTime ?start } .
  OPTIONAL { ?action schema:endTime ?end }
}
```

<figcaption>
  <h4>SPARQL query to find actions in a Workflow Run RO-Crate</h4>
</figcaption>

</figure>
Further, having workflow runs and plans described according to the RO-Crate model allows capturing the context of the workflow itself (e.g. authors, related publications, other workflows, etc.), in addition to the trace alone.
Another advantage of RO-Crate is that the files corresponding to the data entities (inputs, outputs, code, etc.) do not necessarily have to be stored together with the metadata file: for instance, they can be remote and referred to via an http(s) URI. This aspect is mostly relevant in situations where the file is very large or cannot be shared publicly, since a URI can reference a resource to which access is limited (e.g., accessible only after authentication, or from specific network boundaries, etc.).

The WRROC profiles are extensions of the base RO-Crate specification that specialise it for the use case of workflow execution provenance representation. The additional terms, constraints and recommendations introduced by the profiles allow users to represent classes and relationships involved in a workflow execution in a precise and detailed way, so that consumers of the RO-Crate can programmatically retrieve the relevant information according to predefined patterns and act upon it. This is a crucial advantage over using the base RO-Crate specification, which was not designed to answer the competency questions defined for capturing the provenance of workflow executions.

The ability to build FAIR into Workflow Management Systems was identified as one of the current open challenges in the Scientific Workflows domain at
the Workflows Community Summit [[Ferreira 2023]], with the objective of achieving FAIR Computational Workflows. The profiles introduced in this article help tackle this challenge by introducing interoperable metadata among WMSs that captures the provenance of their corresponding workflow executions.

The derivation of Workflow Run Crate, and in turn Provenance Run Crate, from Workflow RO-Crate makes the digital objects that conform to these new profiles compatible with the WorkflowHub workflow registry [[Goble 2021]]. This design entails that Workflow Run RO-Crates directly reference the workflow with which the provenance was generated, and it allows workflow runs to be registered on WorkflowHub and easily found and shared with other researchers. Additionally, the inheritance mechanism allows reusing the specifications already developed for Workflow RO-Crate, which form part of the guidelines on representing the prospective provenance.

The Workflow Run RO-Crate profiles, the associated tooling, the implementations and the examples are developed and supported by the open WRROC Community.
At the time of writing, the Community numbers nearly 40 members and brings together members of the RO-Crate community [[Soiland-Reyes 2022a]], WMS users and developers, workflow users and developers, GA4GH Cloud  [[Rehm 2021]] developers and provenance model authors, and is open to anyone who is interested in the representation of workflow execution provenance.

The inclusion of WMS developers and workflow users has been key to keeping the specifications flexible, easy to implement and grounded on real use cases, while the diversity of the stakeholders has included a plurality of viewpoints while driving the model's development forward, resulting in profiles that are already being used (as described in [Section 3](#implementations)).

In the following subsections, we provide an evaluation of the metadata coverage of runcrate and we discuss how WRROC relates to standards such as W3C PROV-O and to other community projects.


### Evaluation of metadata coverage using runcrate convert {#metadata-coverage}

Since CWLProv was a starting point in the development of WRROC (Section [3.1](#runcrate)), as a baseline validation we chose to verify that the metadata contained in CWLProv ROs is preserved in the RO-Crates produced by their conversion through runcrate's *convert* command. 

In previous work we had conducted a qualitative analysis of metadata coverage in CWLProv (version 0.6.0), based on concrete examples of ROs associated with a realistic bioinformatics workflow [[De Wit 2022]];
in this work we repeated this analysis for WRROC, and compared the WRROC RDF representation (in `ro-crate-metadata.json`) with the CWLProv RDF provenance graph.

To summarise, the analysis focuses on the comparison of the degree of representation by the two models of six provenance data
types defined in [[De Wit 2022]], which we recall here for clarity.

1.  **Scientific context**: the choices which were made in the design of the workflow and parameter values.
2.  **Data**: input and output data.
3.  **Software**: the tools directly orchestrated by the workflow, and their dependencies.
4.  **Workflow**: the workflow and tool descriptions, but not the software they control.
5.  **Computational environment**: metadata about the system on which the workflow was executed, comprising both software and hardware.
6.  **Execution details**: additional information about the workflow execution itself.

Each type is in turn articulated in a set of data subtypes, forming a hierarchy
of elements that should be represented in
workflow provenance data to satisfy a range of use cases spanning from
supporting workflow development to supporting a service based on the
execution of the workflow, with several other use cases in between. For a full
motivation and description of the criteria the reader may refer to the original work [[De Wit 2022]].

Our analysis shows that, overall, most of the information contained in the CWLProv RDF is transferred to the RO-Crate metadata.
The results are summarised in Table [2](#analysis_table);
for completeness, we also report the (non-RDF) representation of provenance metadata in CWL-specific documents (`packed.cwl` and `primary-job.json`), which are included in both CWLProv ROs and RO-Crates generated by runcrate.

We observe that out of the total 20 provenance data subtypes that are part of the analysis, WRROC represented 13 (65%) of them (9 fully, 4 partially), while CWLProv RDF captured 8 (3 fully, 5 partially). The representation of some entire categories of metadata has improved -- notably Workflow parameters (WF2), which were insufficiently described in CWLProv RDF, but defined with type and format in RO-Crate.
Moreover, the Workflow Run RO-Crate RDF contains a representation of tools orchestrated by the workflow (T3), as well as a much more extensive description of the workflow itself (T4) compared to CWLProv.

In conclusion, our analysis shows that runcrate preserves most provenance metadata previously shown to be relevant in realistic RO use case scenarios.
More detailed results of the analysis can be found in [[de Wit 2024]].


<div id="analysis_table">

| CWL (non-RDF) | Type | Subtype | Name                    | CWLProv RDF | WRROC RDF |
| :-----------: | ---: | ------- | ----------------------- | :---------: | :-------: |
|      •        |   T1 | SC1     | Workflow design         |      ·      |     •     |  
|      ∘        |      | SC2     | Entity annotations      |      ·      |     ·     |  
|      ·        |      | SC3     | Workflow execution ann. |      ·      |     ·     |  
|      ◦        |   T2 | D1      | Data identification     |      ·      |     ·     |  
|      ◦        |      | D2      | File characteristics    |      ◦      |     ◦     |  
|      ◦        |      | D3      | Data access             |      ·      |     ·     |  
|      •        |      | D4      | Parameter mapping       |      •      |     •     |  
|      •        |   T3 | SW1     | Software identification |      ·      |     •     |  
|      •        |      | SW2     | Software documentation  |      ·      |     •     |  
|      •        |      | SW3     | Software access         |      ·      |     •     |  
|      •        |   T4 | WF1     | Workflow software       |      ◦      |     •     |  
|      •        |      | WF2     | Workflow parameters     |      ◦      |     •     |  
|      •        |      | WF3     | Workflow requirements   |      ·      |     ◦     |  
|      ·        |   T5 | ENV1    | Software environment    |      ·      |     ·     |  
|      ·        |      | ENV2    | Hardware environment    |      ·      |     ·     |  
|      ◦        |      | ENV3    | Container image         |      ◦      |     ◦     |  
|      ·        |   T6 | EX1     | Execution timestamps    |      •      |     •     |  
|      ·        |      | EX2     | Consumed resources      |      ·      |     ·     |  
|      ·        |      | EX3     | Workflow engine         |      ◦      |     ◦     |  
|      ·        |      | EX4     | Human agent             |      •      |     •     |  

**Table 2**: **Summarised results of our qualitative analysis of runcrate**. We converted CWLProv (v0.6.0) ROs to WRROC with runcrate 0.5.0. The table compares the degree to which the data subtypes of the provenance data taxonomy
(identified by the triple (`Type`, `Subtype`, `Name`)) are preserved
by the CWLProv RDF and the WRROC RDF models; the taxonomy is defined in previous work [[De Wit 2022]],
where relevant provenance metadata are identified based on realistic
use cases for ROs associated with a real-life bioinformatics workflow.<br>
For completeness, the *CWL (non-RDF)* column also reports the non-RDF representation of provenance metadata
in CWL-specific documents: `packed.cwl` (the workflow) and `primary-job.json` (the input parameter file).
Since `packed.cwl` and `primary-job.json` are also included in RO-Crate, we only considered how the metadata was represented in `ro-crate-metadata.json`.\
**Legend:** • fully represented  ◦ partially represented  · missing or unstructured representation

</div>



### Workflow Run RO-Crate and the W3C PROV standard {#prov}

One of our aims for the WRROC profiles is to make them compatible with both Schema.org and W3C PROV. Provenance Run Crate is the profile that most closely matches the level of detail provided by CWLProv, which extends W3C PROV. [Table 3](#rocrate_prov_mapping) shows how the main classes and relationships represented by Provenance Run Crate map to PROV constructs, using the SKOS vocabulary to indicate the type of relationship between each pair of terms. A machine-readable version of the mapping can be found in the [RO-Crate accompanying](https://w3id.org/ro/doi/10.5281/zenodo.10368989) this article [[wrroc-crate wrroc-crate-html]].



<div id="rocrate_prov_mapping">



| RO-Crate |     Relationship      | W3C PROV-O                   |
| ------------------------------------------------------: | :-------------------: | ---------------------------- |
| [`s:Action`](http://schema.org/Action) <br><small>(superclass of [`s:CreateAction`](http://schema.org/CreateAction), [`s:OrganizeAction`](http://schema.org/OrganizeAction))</small> |  Has close match <br><small>(schema.org Actions may also be potential actions in the future)</small>  | [`prov:Activity`](http://www.w3.org/ns/prov#Activity)                   |
| [`s:CreateAction`](http://schema.org/CreateAction),  [`s:OrganizeAction`](http://schema.org/OrganizeAction) |   Has broader match   | [`prov:Activity`](http://www.w3.org/ns/prov#Activity)                   |
| [`s:Person`](http://schema.org/Person) |    Has exact match    | [`prov:Person`](http://www.w3.org/ns/prov#Person)                     |
| [`s:Organization`](http://schema.org/Organization) |    Has exact match    | [`prov:Organization`](http://www.w3.org/ns/prov#Organization)             |
| [`s:SoftwareApplication`](http://schema.org/SoftwareApplication) |   Has related match   | [`prov:SoftwareAgent`](http://www.w3.org/ns/prov#SoftwareAgent)              |
| [`bioschemas:ComputationalWorkflow`](https://bioschemas.org/ComputationalWorkflow),  [`s:SoftwareApplication`](http://schema.org/SoftwareApplication),  [`s:HowTo`](http://schema.org/HowTo) |   Has broader match   | [`prov:Plan`](http://www.w3.org/ns/prov#Plan), [`prov:Entity`](http://www.w3.org/ns/prov#Entity)             |
| [`s:MediaObject`](http://schema.org/MediaObject),  [`s:Dataset`](http://schema.org/Dataset),  [`s:PropertyValue`](http://schema.org/PropertyValue) |   Has broader match   | [`prov:Entity`](http://www.w3.org/ns/prov#Entity)                     |
| [`s:startTime`](http://schema.org/startTime) on [`s:CreateAction`](http://schema.org/CreateAction) |    Has close match    | [`prov:startedAtTime`](http://www.w3.org/ns/prov#startedAtTime)              |
| [`s:endTime`](http://schema.org/endTime) on [`s:CreateAction`](http://schema.org/CreateAction) |    Has close match    | [`prov:endedAtTime`](http://www.w3.org/ns/prov#endedAtTime)                |
| [`s:agent`](http://schema.org/agent) on [`s:CreateAction`](http://schema.org/CreateAction) |   Has related match   | [`prov:wasStartedBy`](http://www.w3.org/ns/prov#wasStartedBy), [`prov:wasEndedBy`](http://www.w3.org/ns/prov#wasEndedBy) |
| [`s:agent`](http://schema.org/agent) and  [`s:instrument`](http://schema.org/instrument) on [`s:CreateAction`](http://schema.org/CreateAction) |   Has broader match   | [`prov:wasAssociatedWith`](http://www.w3.org/ns/prov#wasAssociatedWith)          |
| [`s:instrument`](http://schema.org/instrument) on [`s:CreateAction`](http://schema.org/CreateAction) | Has related match <br><small>(Complex mapping: an instrument implies a qualified association with the agent, linked to a plan)</small> | [`prov:hadPlan`](http://www.w3.org/ns/prov#hadPlan) on [`prov:Association`](http://www.w3.org/ns/prov#Association)   |
| [`s:object`](http://schema.org/object) on [`s:CreateAction`](http://schema.org/CreateAction) |    Has exact match    | [`prov:used`](http://www.w3.org/ns/prov#used)                       |
| [`s:result`](http://schema.org/result) on [`s:CreateAction`](http://schema.org/CreateAction) |    Has close match    | inverse [`prov:wasGeneratedBy`](http://www.w3.org/ns/prov#wasGeneratedBy)     |

_**Table 3**: **Mapping from Workflow Run RO-Crate to equivalent W3C PROV concepts** using SKOS \[[Isaac 2009]\]. For instance, [`s:CreateAction`](http://schema.org/CreateAction) has **broader** match PROV's [`prov:Activity`](http://www.w3.org/ns/prov#Activity) , meaning that *Activity* is more general._

</div>

### Five Safes Workflow Run Crate {#5s-crate}

The *Five Safes RO-Crate* \[[Soiland-Reyes 2023e]\] profile has been developed to extend the Workflow Run RO- Crate profile for use in Trusted Research Environments (TRE) following the Five Safes Framework [[Desai 2016]] to better handle sensitive health data in federated workflow execution across TREs in the UK  \[[Giles 2023]\].

A crate with a workflow run request references a pre-approved workflow and project details for manual and automated assessment according to the TRE’s agreement policy for the sensitive dataset.
The crate then goes through multiple phases internal to the TRE, including validation, sign-off, workflow execution and disclosure control [[Soiland-Reyes 2023f]\].
At this stage the crate is also conforming to the Workflow Run Crate profile.
The final crate is then safe to be made public.

This extension of Workflow Run Crate documents and supports the *human review process* – important for transparency on TRE data usage.
The initial implementation of this process used WfExS as the workflow execution backend, and this approach will form the basis for further work on implementing federated workflow execution in the British initiatives DARE UK and [HDR UK](https://www.hdruk.ac.uk/research/research-data-infrastructure/federated-analytics/) \[[Snowley 2023]\] and in the European [EOSC-ENTRUST](http://eosc-entrust.eu/) project for Trusted Research Environment.



### Biocompute Object RO-Crate {#bco-crate}

[IEEE 2791-2020], colloquially *Biocompute Objects* (BCO), is a standard for representing provenance of a genomic sequencing pipeline, intended for submission of the workflow to regulatory bodies, e.g. as part of a personalised medical treatment method \[[Alterovitz 2018]\].
The BCO is represented as a single JSON file which includes description of the workflow and its steps and intended purpose, as well as references for tools used and data sources accessed.

There is overlap in the goals of BCO and Workflow Run Crate profiles; however, their intentions and focus are different.
BCO is primarily conveying a computational method for the purpose of manual regulatory review and further reuse, with any values provided as an exemplar run.
A Workflow Run Crate, however, is primarily documenting a particular workflow execution, and the workflow is associated to facilitate rerun rather than reuse.

Previously, a [guide](https://biocompute-objects.github.io/bco-ro-crate/) to packaging BioCompute Objects using RO-Crate was developed as a profile to combine both standards \[[Soiland-Reyes 2021]\].
In this early approach, RO-Crate was primarily a vessel to transport the BCO along with its constituent resources, including the workflow and data files, as well as provide these resources with additional typing and licence metadata that is not captured by the BCO JSON.
Further work is being planned with the BCO community to update the BCO-RO profile to align with the newer Workflow Run Crate profiles.

## Conclusion and Future Work {#conclusion}

The Workflow Run RO-Crate profile collection presented in this manuscript is a
new model to represent and package both the prospective
and the retrospective provenance relating to the execution of computational
workflows in a way that is
machine-actionable, interoperable, independent of the specific workflow language or
execution system, and including support for re-execution.
These new profiles build on RO-Crate and Schema.org to include contextual
information and bundle together all objects of the workflow execution
(inputs, outputs, code, etc.).

Our approach minimizes the set of mandatory metadata items
and defines a hierarchy of profiles -- Process Run Crate, Workflow Run
Crate, and Provenance Run Crate -- that capture provenance information at increasing
levels of detail and complexity.
This flexible approach increases the model's adaptability to the diverse
landscape of WMSs used in practice, and modulates the implementation effort as a
function of the requirements of the specific use case.

As a result, there has already been significant uptake of Workflow Run RO-Crate, as shown by its adoption in six WMS, including Galaxy, StreamFlow and COMPSs;
in addition, the `runcrate` toolkit has been implemented as part of this
work providing various inspection, conversion and re-execution functionalities.
Moreover, we have shown how WRROC has been applied in real use cases.

Workflow Run RO-Crate is an ongoing project. Therefore, our profiles and the surrounding software are not static entities, but keep being updated to cater for new requirements and use cases.
As examples of ongoing work, at the time of writing there are plans to expand the runcrate toolkit to better support the creation and querying of WRROC objects. Also, work is ongoing to implement automated conformance validation of crates.

In addition, several of the implementations presented in this work will also develop new features. For instance, the Galaxy community plans to extend its WRROC support to: include metadata detailing each step of a workflow run to conform to the Provenance Run Crate profile; develop and/or integrate RO-Crate more deeply with import and export of Galaxy histories; and further develop user-guided import of RO-Crates as Galaxy datasets, histories and workflows.

Further, we are currently exploring the cloud execution of Workflow Run RO-Crates.
The Workflow Execution Service (WES) specification is used by the Global Alliance for Genomics and Health (GA4GH) [[Rehm 2021]] to enable WMS-agnostic interpretation of workflows and scheduling of task execution. 
In addition, the Task Execution Service (TES) specification enables the execution of individual, atomic, containerised tasks in a compute backend-independent manner.

We are planning to undertake an in-depth analysis of the degree of interoperability between the TES and WES API standards -- roughly the equivalents of Process and Workflow Run Crates, respectively -- by placing their focus on the actual execution of tasks/processes and workflows in cloud environments and liaising with the GA4GH Cloud community to align schemas where necessary.
We will then build an interconversion library that attempts to

1) construct WES workflow and TES task run requests from RO-Crates containing Provenance, Workflow or Process Run requests and therefore allow their easy (re)execution on any GA4GH Cloud API-powered infrastructure, and

2) bundle information from the WES and TES (as well as other GA4GH Cloud API resources, where available) to create or extend RO-Crates with standards-compliant Process, Workflow or even Provenance RO-Crates.

The maintenance and development of WRROC is driven by an open community,
currently numbering about 40 members. The Community runs regular virtual
meetings (every two weeks at the time of writing) and coordinates on Slack and
the RO-Crate mailing list.

Naturally, feedback and contributions from the community are welcome and
encouraged, and new requirements and features are discussed and sustained, particularly
through the WRROC GitHub repository issue tracker [[run-crate-repository]].
Through the open Community we expect to encourage and support further adoption of WRROC, be it by the other WMS or other use cases, maybe in time converging towards a common workflow execution provenance representation.



[^1]: See [section 4.1.4.1](../../../2022/phd/ro-crate/#workflows)
[^2]: See [section 4.1.4](../../../2022/phd/ro-crate/#inuse) and [section 6.1.2.4](../discussion/#profiles).


<footer>

### Acknowledgements {#acknowledgements}

The authors would like to thank all participants to the [Workflow Run RO-Crate working group](https://www.researchobject.org/workflow-run-crate/#community) meetings for the fruitful discussions and valuable feedback.


The authors acknowledge funding from: 

  - Sardinian Regional Government through the XData Project (S.L., L.P.);
  - Spanish Government (contract PID2019-107255GB) (R.S.);
  - Spanish Government MCIN/AEI/10.13039/501100011033 (CEX2021-001148-S) (R.S.);
  - Generalitat de Catalunya (contract 2021-SGR-00412) (R.S.);
  - European High-Performance Computing Joint Undertaking (JU) (No [955558](https://doi.org/10.3030/955558)) (R.S.);
  - EU Horizon research and innovation programme under Grant agreement No [101058129](https://doi.org/10.3030/101058129) (DT-GEO) (R.S.);
  - ELIXIR Platform Task 2022-2023 funding for Task "Container Orchestration" (A.K.);
  - Research Foundation - Flanders (FWO) for ELIXIR Belgium (I000323N and I002819N) (P.D.G.);
  - Multiannual Agreement with Universidad Politécnica de Madrid in the line Support for R&D projects for Beatriz Galindo researchers, in the context of the V PRICIT (Regional Programme of Research and Technological Innovation) (D.G.);
  - Comunidad de Madrid through the call Research Grants for Young Investigators from Universidad Politécnica de Madrid (D.G.);
  - ICSC - Centro Nazionale di Ricerca in High-Performance Computing, Big Data and Quantum Computing, funded by European Union - NextGenerationEU (I.C.);
  - ACROSS project, HPC Big Data Artificial Intelligence Cross Stack Platform Towards Exascale, funded by the European High-Performance Computing Joint Undertaking (JU) under G.A. n. [955648](https://doi.org/10.3030/955648) (I.C.);
  - EUPEX project, European Pilot for Exascale, funded by the European High-Performance Computing Joint Undertaking (JU) under G.A. n.  [101033975](https://doi.org/10.3030/101033975) (I.C.);
  - Life Science Database Integration Project, NBDC of Japan Science and Technology Agency (T.O.);
  - JSPS KAKENHI (Grant Number [20J22439](https://kaken.nii.ac.jp/en/grant/KAKENHI-PROJECT-20J22439/));
  - European Commission Horizon 2020 
    - H2020-SC1-2018-Single-Stage-RTD [825575](https://doi.org/10.3030/825575) (European Joint Programme on Rare Diseases; SC1-BHC-04-2018 Rare Disease European Joint Programme Cofund) (L.R.N., J.M.F., S.C.G.), 
    - EU NextGenerationEU/PRTR H2020-JTI-EuroHPC-2019-1 [955558](https://doi.org/10.3030/955558) (eFlows4HPC) (R.S.), 
    - H2020-INFRAEDI-02-2018 [823830](https://doi.org/10.3030/823830) (BioExcel-2) (S.S.R.), 
    - H2020-INFRAEOSC-2018-2 [824087](https://doi.org/10.3030/824087) (EOSC-Life) (S.L., L.R.N., P.D.G., R.W., L.P., J.M.F., S.C.G., S.S.R.);
  - Horizon Europe 
    - HORIZON-INFRA-2021-EMERGENCY-01 [101046203](https://doi.org/10.3030/101046203) (BY-COVID) (S.L., L.R.N., P.D.G., R.W., L.P., J.M.F., S.C.G., S.S.R.), 
    - HORIZON-INFRA-2021-EOSC-01 [101057388](https://doi.org/10.3030/101057388) (EuroScienceGateway) (P.D.G., J.M.F., S.C.G., S.S.R.), 
    - HORIZON-INFRA-2021-EOSC-01-05 [101057344](https://doi.org/10.3030/101057344) (FAIR-IMPACT) (D.G., S.S.R.);
  - UK Research and Innovation (UKRI) under the UK government's Horizon Europe funding guarantee 
    - [10038963](https://gtr.ukri.org/projects?ref=10038963) (EuroScienceGateway), 
    - [10038992](https://gtr.ukri.org/projects?ref=10038992) (FAIR-IMPACT) (S.S.R.).

H.S. is founder and CEO of the Software company Sator Inc., Tokyo, which did not fund the present work.

The funders had no role in study design, data collection and analysis, decision to publish, or preparation of the manuscript.


## Author contributions {#author-contributions}

Author contributions following the CRediT Taxonomy:

Simone Leo
:   Conceptualization, Data Curation, Investigation, Methodology, Resources, Software, Supervision, Validation, Visualization, Writing -- Original Draft preparation, Writing -- Review & Editing

Michael R. Crusoe
:   Conceptualization, Investigation, Software, Supervision

Laura Rodríguez-Navas
:   Software, Writing -- Original Draft preparation

Raül Sirvent
:   Data Curation, Software, Writing -- Original Draft preparation, Writing -- Review & Editing

Alexander Kanitz
:   Writing -- Original Draft preparation, Writing -- Review & Editing

Paul De Geest
:   Data Curation, Software, Writing -- Original Draft preparation

Rudolf Wittner
:   Data Curation, Writing -- Original Draft preparation, Writing -- Review & Editing

Luca Pireddu
:   Funding acquisition, Project Administration, Supervision, Writing -- Review & Editing

Daniel Garijo
:   Conceptualization, Formal Analysis, Writing -- Original Draft preparation, Writing -- Review & Editing

José M. Fernández
:   Data Curation, Software, Writing -- Original Draft preparation

Iacopo Colonnelli
:   Data Curation, Software, Writing -- Original Draft preparation

Matej Gallo
:   Data Curation, Software

Tazro Ohta
:   Data Curation, Software, Writing -- Original Draft preparation

Hirotaka Suetake
:   Data Curation, Software, Writing -- Original Draft preparation

Salvador Capella-Gutierrez
:   Funding Acquisition, Resources, Supervision, Writing -- Original Draft preparation

Renske de Wit
:   Software, Writing -- Original Draft preparation, Writing -- Review & Editing

Bruno de Paula Kinoshita
:   Data Curation, Software, Writing -- Original Draft preparation, Writing -- Review & Editing

Stian Soiland-Reyes
:   Conceptualization, Formal Analysis, Funding Acquisition, Investigation, Methodology, Resources, Software, Supervision, Visualization, Writing -- Original Draft preparation, Writing -- Review & Editing


## References {#references}

\[Afgan 2023\] Enis Afgan, Istvan Albert, Renato Alves et al. (2023):  
**galaxyproject/galaxy** version 23.1.1  
_GitHub_  
<https://github.com/galaxyproject/galaxy/releases/tag/v23.1.1>  
<https://identifiers.org/swh:1:rel:33ce0ce4f6e3d77d5c0af8cff24b2f68ba8d57e9>

[Afgan 2023]: https://github.com/galaxyproject/galaxy/releases/tag/v23.1.1 "galaxyproject/galaxy v23.1.1"

\[Alterovitz 2018\] Gil Alterovitz, Dennis A Dean II, Carole Goble, Michael R Crusoe, Stian Soiland-Reyes, Amanda Bell, Anais Hayes, Anita Suresh, Charles Hadley S King IV, Dan Taylor, KanakaDurga Addepalli, Elaine Johanson, Elaine E Thompson, Eric Donaldson, Hiroki Morizono, Hsinyi Tsang, Jeet K Vora, Jeremy Goecks, Jianchao Yao, Jonas S Almeida, Jonathon Keeney, KanakaDurga Addepalli, Konstantinos Krampis, Krista Smith, Lydia Guo, Mark Walderhaug, Marco Schito, Matthew Ezewudo, Nuria Guimera, Paul Walsh, Robel Kahsay, Srikanth Gottipati, Timothy C Rodwell, Toby Bloom, Yuching Lai, Vahan Simonyan, Raja Mazumder (2018):  
**Enabling precision medicine via standard communication of HTS provenance, analysis, and results**.  
*PLOS Biology* **16**(12):e3000099  
<https://doi.org/10.1371/journal.pbio.3000099>

\[Amstutz 2023\] Peter Amstutz, Michael R. Crusoe, Farah Zaib Khan, Stian Soiland-Reyes, Manvendra Singh, Kapil kumar, John Chilton, Thomas Hickman, boysha, Tomoya Tanjo, Rupert Nash, Kevin Hannon, ash, Michael Kotliar, Brad Chapman, Andrey Kartashov, Guillermo Carrasco, Dan Leehr, Nebojsa Tijanic, Joshua C. Randall, Miguel Boland, bogdang989, Chuck McCallum, Hervé Ménager, Pau Ruiz Safont, Bruno P. Kinoshita, Denis Yuen, Gijs Molenaar (2023):  
**common-workflow-language/cwltool: 3.1.20230127121939**.  
<https://doi.org/10.5281/zenodo.7575947>

\[Atkinson 2017\] Malcolm Atkinson, Sandra Gesing, Johan Montagnat, Ian Taylor (2017):  
**Scientific workflows: Past, present and future**.  
*Future Generation Computer Systems* **75**  
<https://doi.org/10.1016/j.future.2017.05.041>

\[Bacall 2022\] Finn Bacall, Alan R. Williams, Stuart Owen, Stian Soiland-Reyes (2022):  
**Workflow RO-Crate Profile 1.0**.  
*WorkflowHub community*  
<https://w3id.org/workflowhub/workflow-ro-crate/1.0>

\[Bacall 2022b\] Finn Bacall, Martyn Whitwell (2022):  
**GitHub – ResearchObject/ro-crate-ruby: A Ruby gem for creating, manipulating and reading RO-Crates**.  
<https://github.com/ResearchObject/ro-crate-ruby>

\[Bahra 2011\] Avi Bahra (2011):  
**Managing work flows with ecFlow**.  
*ECMWF Newsletter* **129**  
<https://doi.org/10.21957/nr843dob>

\[Batista 2022\] Dominique Batista, Alejandra Gonzalez-Beltran, Susanna-Assunta Sansone, Philippe Rocca-Serra (2022):  
**Machine actionable metadata models**.  
*Scientific Data* **9**:592  
<https://doi.org/10.1038/s41597-022-01707-6>

\[Bechhofer 2013\] Sean Bechhofer, Iain Buchan, David De Roure, Paolo Missier, John Ainsworth, Jiten Bhagat, Phillip Couch, Don Cruickshank, Mark Delderfield, Ian Dunlop, Matthew Gamble, Danius Michaelides, Stuart Owen, David Newman, Shoaib Sufi, Carole Goble (2013):  
**Why Linked Data is not enough for scientists**.  
*Future Generation Computer Systems* **29**(2) pp. 599--611.  
<https://doi.org/10.1016/j.future.2011.08.004>

\[Belhajjame 2015\] Khalid Belhajjame, Jun Zhao, Daniel Garijo, Matthew Gamble, Kristina Hettne, Raul Palma, Eleni Mina, Oscar Corcho, José Manuel Gómez-Pérez, Sean Bechhofer, Graham Klyne, Carole Goble (2015):  
**Using a suite of ontologies for preserving workflow-centric research objects**.  
*Web Semantics: Science, Services and Agents on the World Wide Web* **32** pp. 16--42.  
<https://doi.org/10.1016/j.websem.2015.01.003>

\[Beltrán 2023\] Daniel Beltrán Mora, Miguel Castrillo, Manuel G. Marciani, Bruno P. Kinoshita, Luiggi Tenorio Ku, Aina Gaya-Àvila, Francesc Roura Adserias, Pierre-Antoine Bretonnière, Oriol Mula Valls, Pablo Goitia, Julian Rodrigo Berlin, Miguel Andrés-Martínez, Kim Serradell, Wilmer Uruchi Ticona, Domingo Manubens-Gil, Larissa Batista Leite, Isabel Andreu-Burillo, Javier Vegas-Regidor, Hui Du, Danila Volpi, Fabian Lienert, Joan Giralt, Joan Lopez, Muhammad Asif, Virginie Guemas, Xavier Abellan Ecija (2023):  
**Autosubmit v4.0.100**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10199020>

\[Bouyssié 2023\] David Bouyssié, Pınar Altıner, Salvador Capella-Gutierrez, José M. Fernández, Yanick Paco Hagemeijer, Peter Horvatovich, Martin Hubálek, Fredrik Levander, Pierluigi Mauri, Magnus Palmblad, Wolfgang Raffelsberger, Laura Rodríguez-Navas, Dario Di Silvestre, Balázs Tibor Kunkli, Julian Uszkoreit, Yves Vandenbrouck, Juan Antonio Vizcaíno, Dirk Winkelhardt, Veit Schwämmle (2023):  
**WOMBAT-P: Benchmarking Label-Free Proteomics Data Analysis Workflows**.  
*bioRxiv* 2023.10.02.560412  
<https://doi.org/10.1101/2023.10.02.560412>

\[Chard 2016\] Kyle Chard, Mike D' Arcy, Ben Heavner, Ian Foster, Carl Kesselman, Ravi Madduri, Alexis Rodriguez, Stian Soiland-Reyes, Carole Goble, Kristi Clark, Eric W. Deutsch, Ivo Dinov, Nathan Price, Arthur Toga (2016):  
**I'll take that to go: Big data bags and minimal identifiers for exchange of large, complex datasets**.  
*2016 IEEE International Conference on Big Data (Big Data)*, IEEE, pp. 319--328.  
ISBN 978-1-4673-9005-7.  
<https://static.aminer.org/pdf/fa/bigdata2016/BigD418.pdf>  
<https://doi.org/10.1109/BigData.2016.7840618>

\[Chard 2019\] Kyle Chard, Niall Gaffney, Matthew B. Jones, Kacper Kowalik, Bertram Ludascher, Timothy McPhillips, Jarek Nabrzyski, Victoria Stodden, Ian Taylor, Thomas Thelen, Matthew J. Turk, Craig Willis (2019):  
**Application of BagIt-serialized research object bundles for packaging and re-execution of computational analyses**.  
*15th International Conference on eScience (eScience 2019)*, IEEE, pp. 514--521.  
ISBN 978-1-7281-2451-3.  
<https://zenodo.org/record/3381754>  
<https://doi.org/10.1109/eScience.2019.00068>

\[Colonnelli 2021\] Iacopo Colonnelli, Barbara Cantalupo, Ivan Merelli, Marco Aldinucci (2021):  
**StreamFlow: cross-breeding Cloud with HPC**.  
*IEEE Transactions on Emerging Topics in Computing* **9**(4)  
<https://doi.org/10.1109/TETC.2020.3019202>

\[Colonnelli 2023a\] Iacopo Colonnelli (2023):  
**StreamFlow run of digital pathology tissue/tumor prediction workflow**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.7911906>

\[Colonnelli 2023b\] Iacopo Colonnelli, Barbara Cantalupo, Marco Aldinucci, Gaetano Saitta, Alberto Mulone (2023):  
alpha-unito/streamflow version 0.2.0.dev10  
*GitHub*  
<https://github.com/alpha-unito/streamflow/releases/tag/0.2.0.dev10>  
<https://identifiers.org/swh:1:rev:b2014add57189900fa5a0a0403b7ae3a384df73b>

\[Costa 2013\] Flavio Costa, Vítor Silva, Daniel de Oliveira, Kary Ocaña, Eduardo Ogasawara, Jonas Dias, Marta Mattoso (2013):  
**Capturing and querying workflow runtime provenance with PROV**: a practical approach.  
*Proceedings of the Joint EDBT/ICDT 2013 Workshops (EDBT '13)*  
<https://doi.org/10.1145/2457317.2457365>

\[Crusoe 2022\] Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian Soiland-Reyes, Bogdan Gavrilović, Carole Goble, The CWL Community (2022):  
**Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language**.  
*Communications of the ACM* **65**(6)  
<https://doi.org/10.1145/3486897>

\[Cuevas-Vicenttín 2016\] Víctor Cuevas-Vicenttín, Bertram Ludäscher, Paolo Missier, Khalid Belhajjame, Fernando Chirigati, Yaxing Wei, Saumen Dey, Parisa Kianmajd, David Koop, Shawn Bowers, Ilkay Altintas, Christopher Jones, Matthew B. Jones, Lauren Walker, Peter Slaughter, Ben Leinfelder, Yang Cao (2016):  
**ProvONE: A PROV Extension Data Model for Scientific Workflow Provenance**.  
<https://purl.dataone.org/provone-v1-dev>  
(accessed [2023-11-06](https://web.archive.org/web/20231106005203/http://jenkins-1.dataone.org/jenkins/view/Documentation%20Projects/job/ProvONE-Documentation-trunk/ws/provenance/ProvONE/v1/provone.html))

\[De Geest 2022\] Paul De Geest, Frederik Coppens, Stian Soiland-Reyes, Ignacio Eguinoa, Simone Leo (2022):  
**Enhancing RDM in Galaxy by integrating RO-Crate**.  
1st International Conference on FAIR Digital Objects ([FDO 2022](https://www.fdo2022.org/)) (poster)  
*Research Ideas and Outcomes* **8**:e95164  
<https://doi.org/10.3897/rio.8.e95164>

\[De Geest 2023a\] Paul De Geest, Bert Droesbeke, Ignacio Eguinoa, Alban Gaignard, Sebastiaan Huber, Bruno Kinoshita, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, Raül Sirvent, Stian Soiland-Reyes (2023):  
**GitHub – ResearchObject/ro-crate-py: Python library for RO-Crate**, version 0.9.0.  
<https://github.com/researchobject/ro-crate-py>  
<https://doi.org/10.5281/zenodo.10017862>

\[De Geest 2023b\] Paul De Geest (2023):  
**Run of an example Galaxy collection workflow**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.7785861>

\[Del Rio 2022\] Mauro Del Rio, Luca Lianas, Oskar Aspegren, Giovanni Busonera, Francesco Versaci, Renata Zelic, Per H. Vincent, Simone Leo, Andreas Pettersson, Olof Akre, Luca Pireddu (2022):  
**AI Support for Accelerating Histopathological Slide Examinations of Prostate Cancer in Clinical Studies**.  
*Image Analysis and Processing*. ICIAP 2022 Workshops. ICIAP 2022.  
*Lecture Notes in Computer Science* **13373**  
<https://doi.org/10.1007/978-3-031-13321-3_48>

\[Desai 2016\] Tanvi Desai, Felix Ritchie, Richard Welpton (2016):  
**Five Safes: designing data access for research**.  
*Economics Working Paper Series* **1601**  
<https://econpapers.repec.org/RePEc:uwe:wpaper:20161601>

\[Ejarque 2023\] Jorge Ejarque, Francesc Lordan, Rosa Maria Badia, Raul Sirvent, Daniele Lezzi, Fernando Vazquez, Cristian Tatu, Gabriel Puigdemunt, Nihad Mammadli, Javier Conejero (2023):  
**COMPSs**. bsc-wdc/compss. Version 3.2  
*Zenodo*  
<https://doi.org/10.5281/zenodo.7975340>

\[Feng 2007\] Hanhua Feng, Vishal Misra, Dan Rubenstein (2007):  
**PBS: a unified priority-based scheduler**.  
*Proceedings of the 2007 ACM SIGMETRICS international conference on Measurement and modeling of computer systems* (SIGMETRICS '07)  
<https://doi.org/10.1145/1254882.1254906>

\[Fernández 2023a\] José María Fernández, Laura Rodríguez-Navas, Adrián Muñoz-Cívico, Paula Iborra, Daniel Lea (2023):  
**inab/WfExS-backend**. Version 0.10.1  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10068956>

\[Fernández 2023b\] José María Fernández González (2023):  
**RO-Crate from staged WfExS working directory** 047b6dfc-3547-4e09-92f8-df7143038ff4 (overbridging templon).  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10091550>

\[Ferreira da Silva 2021\] Rafael Ferreira da Silva, Henri Casanova, Kyle Chard, Ilkay Altintas, Rosa M Badia, Bartosz Balis, Tainã Coleman, Frederik Coppens, Frank Di Natale, Bjoern Enders, Thomas Fahringer, Rosa Filgueira, Grigori Fursin, Daniel Garijo, Carole Goble, Dorran Howell, Shantenu Jha, Daniel S. Katz, Daniel Laney, Ulf Leser, Maciej Malawski, Kshitij Mehta, Loïc Pottier, Jonathan Ozik, J. Luc Peterson, Lavanya Ramakrishnan, Stian Soiland-Reyes, Douglas Thain, Matthew Wolf (2021):  
**A Community Roadmap for Scientific Workflows Research and Development**.  
*2021 IEEE Workshop on Workflows in Support of Large-Scale Science (WORKS)*  
\[arXiv:2110.02168\](https://doi.org/10.48550/arXiv.2110.02168)  
<https://doi.org/10.1109/WORKS54523.2021.00016>

\[Ferreira da Silva\] Rafael Ferreira da Silva, Rosa M. Badia, Venkat Bala, Debbie Bard, Peer-Timo Bremer, Ian Buckley, Silvina Caino-Lores, Kyle Chard, Carole Goble, Shantenu Jha, Daniel S. Katz, Daniel Laney, Manish Parashar, Frederic Suter, Nick Tyler, Thomas Uram, Ilkay Altintas, Stefan Andersson, William Arndt, Juan Aznar, Jonathan Bader, Bartosz Balis, Chris Blanton, Kelly Rosa Braghetto, Aharon Brodutch, Paul Brunk, Henri Casanova, Alba Cervera Lierta, Justin Chigu, Taina Coleman, Nick Collier, Iacopo Colonnelli, Frederik Coppens, Michael Crusoe, Will Cunningham, Bruno de Paula Kinoshita, Paolo Di Tommaso, Charles Doutriaux, Matthew Downton, Wael Elwasif, Bjoern Enders, Chris Erdmann, Thomas Fahringer, Ludmilla Figueiredo, Rosa Filgueira, Martin Foltin, Anne Fouilloux, Luiz Gadelha, Andy Gallo, Artur Garcia Saez, Daniel Garijo, Roman Gerlach, Ryan Grant, Samuel Grayson, Patricia Grubel, Johan Gustafsson, Valerie Hayot-Sasson, Oscar Hernandez, Marcus Hilbrich, AnnMary Justine, Ian Laflotte, Fabian Lehmann, Andre Luckow, Jakob Luettgau, Ketan Maheshwari, Motohiko Matsuda, Doriana Medic, Pete Mendygral, Marek Michalewicz, Jorji Nonaka, Maciej Pawlik, Loic Pottier, Line Pouchard, Mathias Putz, Santosh Kumar Radha, Lavanya Ramakrishnan, Sashko Ristov, Paul Romano, Daniel Rosendo, Martin Ruefenacht, Katarzyna Rycerz, Nishant Saurabh, Volodymyr Savchenko, Martin Schulz, Christine Simpson, Raul Sirvent, Tyler Skluzacek, Stian Soiland-Reyes, Renan Souza, Sreenivas Rangan Sukumar, Ziheng Sun, Alan Sussman, Douglas Thain, Mikhail Titov, Benjamin Tovar, Aalap Tripathy, Matteo Turilli, Bartosz Tuznik, Hubertus van Dam, Aurelio Vivas , Logan Ward, Patrick Widener, Sean Wilkinson, Justyna Zawalska, Mahnoor Zulfiqar (2023):  
**Workflows Community Summit 2022**: A Roadmap Revolution.  
*arXiv*:2304.00019  
<https://doi.org/10.48550/arXiv.2304.00019>

\[Freire 2008\] Juliana Freire, David Koop, Emanuele Santos, Cl Silva (2008):  
**Provenance for Computational Tasks: A Survey**.  
*Computing in Science & Engineering* **10**(3)  
<https://doi.org/10.1109/MCSE.2008.79>

\[Galaxy 2022\] The Galaxy Community (E. Afgan, A. Nekrutenko, B. A. Grüning, D. Blankenberg, J. Goecks, M. C. Schatz, A. E. Ostrovsky, A. Mahmoud, A. J. Lonie, A. Syme, A. Fouilloux, A. Bretaudeau, A. Nekrutenko, A. Kumar, A. C. Eschenlauer, A. D. DeSanto, A. Guerler, B. Serrano-Solano, B. Batut, B. A. Grüning, B. W. Langhorst, B. Carr, B. A. Raubenolt, C. J. Hyde, C. J. Bromhead, C. B. Barnett, C. Royaux, C. Gallardo, D. Blankenberg, D. J. Fornika, D. Baker, D. Bouvier, D. Clements, D. A. de Lima Morais, D. L. Tabernero, D. Lariviere, E. Nasr, E. Afgan, F. Zambelli, F. Heyl, F. Psomopoulos, F. Coppens, G. R. Price, G. Cuccuru, G. L. Corguillé, G. Von Kuster, G. G. Akbulut, H. Rasche, H. Hans-Rudolf, I. Eguinoa, I. Makunin, I. J. Ranawaka, J. P. Taylor, J. Joshi, J. Hillman-Jackson, J. Goecks, J. M. Chilton, K. Kamali, K. Suderman, K. Poterlowicz, L. B. Yvan, L. Lopez-Delisle, L. Sargent, M. E. Bassetti, M. A. Tangaro, M. van den Beek, M. Čech, M. Bernt, M. Fahrner, M. Tekman, M. C. Föll, M. C. Schatz, M. R. Crusoe, M. Roncoroni, N. Kucher, N. Coraor, N. Stoler, N. Rhodes, N. Soranzo, N. Pinter, N. A. Goonasekera, P. A. Moreno, P. Videm, P. Melanie, P. Mandreoli, P. D. Jagtap, Q. Gu, R. J. M. Weber, R. Lazarus, R. H. P. Vorderman, S. Hiltemann, S. Golitsynskiy, S. Garg, S. A. Bray, S. L. Gladman, S. Leo, S. P. Mehta, T. J. Griffin, V. Jalili, V. Yves, V. Wen, V. K. Nagampalli, W. A. Bacon, W. de Koning, W. Maier, P. J. Briggs) (2022):  
**The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update**.  
*Nucleic Acids Research* **50**  
<https://doi.org/10.1093/nar/gkac247>

\[Garijo 2011\] Daniel Garijo, Yolanda Gil (2011):  
**A New Approach for Publishing Workflows**.  
*Proceedings of the 6th Workshop on Workflows in Support of Large-Scale Science - WORKS '11*.  
<https://doi.org/10.1145/2110497.2110504>

\[Garijo 2012\] Daniel Garijo, Yolanda Gil (2012):  
**Augmenting PROV with Plans in P-PLAN: Scientific Processes as Linked Data**.  
*Proceedings of the Second International Workshop on Linked Science 2012 - Tackling Big Data*. (LISC 2021)  
*CEUR Workshop Proceedings* **951**  
<https://ceur-ws.org/Vol-951/paper6.pdf>

\[Garijo 2014b\] Daniel Garijo, Yolanda Gil, Oscar Corcho (2014):  
**Towards Workflow Ecosystems through Semantic and Standard Representations**.  
*9th Workshop on Workflows in Support of Large-Scale Science (WORKS 2014)*  
<https://doi.org/10.1109/works.2014.13>

\[Gauthier 2019\] Jeff Gauthier, Antony T Vincent, Steve J Charette, Nicolas Derome (2019):  
**A brief history of bioinformatics**.  
*Briefings in Bioinformatics* **20**(6)  
<https://doi.org/10.1093/bib/bby063>

\[Gil 2011\] Yolanda Gil, Varun Ratnakar, Jihie Kim, Pedro Gonzalez-Calero, Paul Groth, Joshua Moody, Ewa Deelman (2011):  
**Wings: Intelligent Workflow-Based Design of Computational Experiments**.  
*IEEE Intelligent Systems* **26**(1)  
<https://doi.org/10.1109/MIS.2010.9>

\[Giles 2023\] Thomas Giles, Stian Soiland-Reyes, Jonathan Couldridge, Stuart Wheater, Blaise Thomson, Jillian Beggs, Suzy Gallier, Sam Cox, Daniel Lea, Justin Biddle, Rima Doal, Naaman Tammuz, Becca Wilson, Christian Cole, Elizabeth Sapey, Simon Thompson, Professor Emily Jefferson, Phillip Quinlan, Carole Goble (2023):  
**TRE-FX: Delivering a federated network of trusted research environments to enable safe data analytics**.  
*Zenodo* / *DARE UK*  
<https://doi.org/10.5281/zenodo.10055354>

\[Goble 2020\] Carole Goble, Sarah Cohen-Boulakia, Stian Soiland-Reyes, Daniel Garijo, Yolanda Gil, Michael R. Crusoe, Kristian Peters, Daniel Schober (2020):  
**FAIR Computational Workflows**.  
*Data Intelligence* **2**(1--2) pp 108--121.  
<https://doi.org/10.1162/dint_a_00033>

\[Goble 2021\] Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, José Mª Fernández, Salvador Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano, Philip Ewels, Frederik Coppens (2021):  
**Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.4605654>

\[Gray 2017\] Alasdair Gray, Carole Goble, Rafael Jimenez, Bioschemas Community (2017):  
**Bioschemas: From Potato Salad to Protein Annotation**.  
*Proceedings of the ISWC 2017 posters & demonstrations and industry tracks co-located with 16th international semantic web conference (ISWC 2017)*, Vienna, Austria.  
*CEUR Workshop Proceedings* **1963**  
<https://iswc2017.semanticweb.org/paper-579/>  
<https://ceur-ws.org/Vol-1963/paper579.pdf>

\[Guha 2015\] Ramanathan V Guha, Dan Brickley, Steve Macbeth (2015):  
**Schema.org: Evolution of Structured Data on the Web: Big data makes common schemas even more necessary**.  
*Queue* **13**(9) pp. 10--37.  
<https://doi.org/10.1145/2857274.2857276>

\[Herschel 2017\] Melanie Herschel, Ralf Diestelkämper, Houssem Ben Lahmar (2017):  
**A survey on provenance: What for? What form? What from?**  
*The VLDB Journal* **26**  
<https://doi.org/10.1007/s00778-017-0486-1>

\[Himanen 2019\] Lauri Himanen, Amber Geurts, Adam Stuart Foster, Patrick Rinke (2019):  
**Data-Driven Materials Science: Status, Challenges, and Perspectives**.  
*Advanced Science* **6**(21):1900808  
<https://doi.org/10.1002/advs.201900808>

\[Huntingford 2019\] Chris Huntingford, Elizabeth S Jeffers, Michael B Bonsall, Hannah M Christensen, Thomas Lees and Hui Yang (2019):  
**Machine learning and artificial intelligence to aid climate change research and preparedness**.  
*Environmental Research Letters* **14**(12):124007  
<https://doi.org/10.1088/1748-9326/ab4e55>

\[IEEE 2791-2020\] Raja Mazumder, Vahan Simonyan (eds.) (2020):  
**IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication**.  
*IEEE Std* **2791-2020**.  
ISBN 978-1-5044-6466-6.  
<https://research.manchester.ac.uk/en/publications/936de52b-ac53-4f0e-9927-77fd7073e88d>  
<https://doi.org/10.1109/ieeestd.2020.9094416>

\[Isaac 2009\] Antoine Isaac, Ed Summers (2009):  
**SKOS Simple Knowledge Organization System Primer**.  
W3C Working Group Note 18 August 2009  
<https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/>

\[Khan 2019\] Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):  
**Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv**.  
*GigaScience* **8**(11)  
<https://doi.org/10.1093/gigascience/giz095>

\[Kinoshita 2023\] Bruno de Paula Kinoshita (2023):  
**RO-Crate created using Autosubmit version 4.0.100 workflow running kinow/auto-mhm-test-domains**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.8144612>

\[Köster 2012\] Johannes Köster, Sven Rahmann (2012):  
**Snakemake---a scalable bioinformatics workflow engine**.  
*Bioinformatics* **28**(19) pp. 2520--2522.  
<https://doi.org/10.1093/bioinformatics/bts480>

\[Kumar 2013\] Rohini Kumar, Luis Samaniego, Sabine Attinger (2013):  
**Implications of distributed hydrologic model parameterization on water fluxes at multiple scales and locations**.  
*Water Resources Research* **49**(1)  
<https://doi.org/10.1029/2012WR012195>

\[Lebo 2013a\] Timothy Lebo, Satya Sahoo, Deborah McGuinness, Khalid Belhajjame, James Cheney, David Corsar, Daniel Garijo, Stian Soiland-Reyes, Stephan Zednik, Jun Zhao (2013):  
**PROV-O: The PROV Ontology**.  
*W3C Recommendation* 30 April 2013.  
<https://www.w3.org/TR/2013/REC-prov-o-20130430/>

\[Leo 2023a\] Simone Leo, Stian Soiland-Reyes, Michael R. Crusoe (2023):  
**runcrate** 0.5.0  
*Zenodo* / *GitHub*  
<https://github.com/ResearchObject/runcrate>  
<https://doi.org/10.5281/zenodo.10203433>

\[Leo 2023b\] Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2023):  
**Recording provenance of workflow runs with RO-Crate**.  
*arXiv* 2312.07852 
\[Leo 2023c\] Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2023):  
**Recording provenance of workflow runs with RO-Crate** (RO-Crate and mapping).  
RO-Crate  
*Zenodo*  
<https://w3id.org/ro/doi/10.5281/zenodo.10368989>  
<https://doi/10.5281/zenodo.10368989>

\[Leo 2023\] Simone Leo (2023):  
**Run of digital pathology tissue/tumor prediction workflow**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.7774351>

\[Lordan 2014\] Francesc Lordan, Enric Tejedor, Jorge Ejarque, Roger Rafanell, Javier Álvarez, Fabrizio Marozzo, Daniele Lezzi, Raül Sirvent, Domenico Talia, Rosa M. Badia (2014):  
**ServiceSs: An interoperable programming framework for the cloud**.  
*Journal of Grid Computing*, **12**(1)  
<https://doi.org/10.1007/s10723-013-9272-5>

\[Manubens-Gil 2016\] Domingo Manubens-Gil, Javier Vegas-Regidor, Chloe Prodhomme, Oriol Mula-Valls, Francisco J. Doblas-Reyes (2016):  
**Seamless management of ensemble climate prediction experiments on HPC platforms**.  
*2016 International Conference on High Performance Computing & Simulation* (HPCS), Innsbruck, Austria  
<https://doi.org/10.1109/HPCSim.2016.7568429>

\[Meurisse 2023\] Marjan Meurisse, Francisco Estupiñán-Romero, Javier González-Galindo, Natalia Martínez-Lizaga, Santiago Royo-Sierra, Simon Saldner, Lorenz Dolanski-Aghamanoukjan, Alexander Degelsegger-Marquez, Stian Soiland-Reyes, Nina Van Goethem, Enrique Bernal-Delgado, On Behalf of BeYond-COVID project contributors (2023):  
**Federated causal inference based on real-world observational data sources: application to a SARS-CoV-2 vaccine effectiveness assessment**.  
*BMC Medical Research Methodology* **23**:248  
<https://doi.org/10.1186/s12874-023-02068-3> 

\[Missier 2013\] Paolo Missier, Saumen Dey, Khalid Belhajjame, Víctor Cuevas-Vicenttín, Bertram Ludäscher (2013):  
**D-PROV: extending the PROV provenance model with workflow structure**.  
*Proceedings of the 5th USENIX Workshop on the Theory and Practice of Provenance (TaPP '13)*  
<https://doi.org/10.5555/2482949.2482961>

\[Moreau 2013\] Luc Moreau, Paolo Missier, Khalid Belhajjame, Reza B'Far, James Cheney, Sam Coppens, Stephen Cresswell, Yolanda Gil, Paul Groth, Graham Klyne, Timothy Lebo, Jim McCusker, Simon Miles, James Myers, Satya Sahoo, Curt Tilmes (2013):  
**PROV-DM: The PROV Data Model**.  
*W3C Recommendation 30 April 2013*  
<https://www.w3.org/TR/2013/REC-prov-dm-20130430/>.

\[Ohta 2023\] Tazro Ohta, Hirotaka Suetake (2023):  
**Example of Workflow Run RO-Crate Output in Sapporo**  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10134581>
Hilary Oliver, Matthew Shin, David Matthews, Oliver Sanders, Sadie Bartholomew, Andrew Clark, Ben Fitzpatrick, Ronald van Haren, Rolf Hut, Niels Drost (2019):  
**Workflow Automation for Cycling Systems**.  
*Computing in Science & Engineering* **21**(4)  
<https://doi.org/10.1109/MCSE.2019.2906593>

\[Pérez 2018\] Beatriz Pérez, Julio Rubio, Carlos Sáenz-Adán (2018):  
**A systematic review of provenance systems**.  
*Knowledge and Information Systems* **57**  
<https://doi.org/10.1007/s10115-018-1164-3>

\[Poiata 2016\] Natalia Poiata, Claudio Satriano, Jean-Pierre Vilotte, Pascal Bernard, Kazushige Obara (2016):  
**Multiband array detection and location of seismic sources recorded by dense seismic networks**.  
*Geophysical Journal International* **205**(3)  
<https://doi.org/10.1093/gji/ggw071>

\[Poiata 2023\] Natalia Poiata, Claudio Satriano, Javier Conejero (2023):  
**BackTrackBB**: Multi-band array detection and location of seismic sources (PyCOMPSs implementation).  
*Zenodo*  
<https://doi.org/10.5281/zenodo.7788030>

\[Rehm 2021\] <small>Heidi L. Rehm, Angela J.H. Page, Lindsay Smith, Jeremy B. Adams, Gil Alterovitz, Lawrence J. Babb, Maxmillian P. Barkley, Michael Baudis, Michael J.S. Beauvais, Tim Beck, Jacques S. Beckmann, Sergi Beltran, David Bernick, Alexander Bernier, James K. Bonfield, Tiffany F. Boughtwood, Guillaume Bourque, Sarion R. Bowers, Anthony J. Brookes, Michael Brudno, Matthew H. Brush, David Bujold, Tony Burdett, Orion J. Buske, Moran N. Cabili, Daniel L. Cameron, Robert J. Carroll, Esmeralda Casas-Silva, Debyani Chakravarty, Bimal P. Chaudhari, Shu Hui Chen, J. Michael Cherry, Justina Chung, Melissa Cline, Hayley L. Clissold, Robert M. Cook-Deegan, Mélanie Courtot, Fiona Cunningham, Miro Cupak, Robert M. Davies, Danielle Denisko, Megan J. Doerr, Lena I. Dolman, Edward S. Dove, L. Jonathan Dursi, Stephanie O.M. Dyke, James A. Eddy, Karen Eilbeck, Kyle P. Ellrott, Susan Fairley, Khalid A. Fakhro, Helen V. Firth, Michael S. Fitzsimons, Marc Fiume, Paul Flicek, Ian M. Fore, Mallory A. Freeberg, Robert R. Freimuth, Lauren A. Fromont, Jonathan Fuerth, Clara L. Gaff, Weiniu Gan, Elena M. Ghanaim, David Glazer, Robert C. Green, Malachi Griffith, Obi L. Griffith, Robert L. Grossman, Tudor Groza, Jaime M. Guidry Auvil, Roderic Guigó, Dipayan Gupta, Melissa A. Haendel, Ada Hamosh, David P. Hansen, Reece K. Hart, Dean Mitchell Hartley, David Haussler, Rachele M. Hendricks-Sturrup, Calvin W.L. Ho, Ashley E. Hobb, Michael M. Hoffman, Oliver M. Hofmann, Petr Holub, Jacob Shujui Hsu, Jean-Pierre Hubaux, Sarah E. Hunt, Ammar Husami, Julius O. Jacobsen, Saumya S. Jamuar, Elizabeth L. Janes, Francis Jeanson, Aina Jené, Amber L. Johns, Yann Joly, Steven J.M. Jones, Alexander Kanitz, Kazuto Kato, Thomas M. Keane, Kristina Kekesi-Lafrance, Jerome Kelleher, Giselle Kerry, Seik-Soon Khor, Bartha M. Knoppers, Melissa A. Konopko, Kenjiro Kosaki, Martin Kuba, Jonathan Lawson, Rasko Leinonen, Stephanie Li, Michael F. Lin, Mikael Linden, Xianglin Liu, Isuru Udara Liyanage, Javier Lopez, Anneke M. Lucassen, Michael Lukowski, Alice L. Mann, John Marshall, Michele Mattioni, Alejandro Metke-Jimenez, Anna Middleton, Richard J. Milne, Fruzsina Molnár-Gábor, Nicola Mulder, Monica C. Munoz-Torres, Rishi Nag, Hidewaki Nakagawa, Jamal Nasir, Arcadi Navarro, Tristan H. Nelson, Ania Niewielska, Amy Nisselle, Jeffrey Niu, Tommi H. Nyrönen, Brian D. O'Connor, Sabine Oesterle, Soichi Ogishima, Vivian Ota Wang, Laura A.D. Paglione, Emilio Palumbo, Helen E. Parkinson, Anthony A. Philippakis, Angel D. Pizarro, Andreas Prlic, Jordi Rambla, Augusto Rendon, Renee A. Rider, Peter N. Robinson, Kurt W. Rodarmer, Laura Lyman Rodriguez, Alan F. Rubin, Manuel Rueda, Gregory A. Rushton, Rosalyn S. Ryan, Gary I. Saunders, Helen Schuilenburg, Torsten Schwede, Serena Scollen, Alexander Senf, Nathan C. Sheffield, Neerjah Skantharajah, Albert V. Smith, Heidi J. Sofia, Dylan Spalding, Amanda B. Spurdle, Zornitza Stark, Lincoln D. Stein, Makoto Suematsu, Patrick Tan, Jonathan A. Tedds, Alastair A. Thomson, Adrian Thorogood, Timothy L. Tickle, Katsushi Tokunaga, Juha Törnroos, David Torrents, Sean Upchurch, Alfonso Valencia, Roman Valls Guimera, Jessica Vamathevan, Susheel Varma, Danya F. Vears, Coby Viner, Craig Voisin, Alex H. Wagner, Susan E. Wallace, Brian P. Walsh, Marc S. Williams, Eva C. Winkler, Barbara J. Wold, Grant M. Wood, J. Patrick Woolley, Chisato Yamasaki, Andrew D. Yates, Christina K. Yung, Lyndon J. Zass, Ksenia Zaytseva, Junjun Zhang, Peter Goodhand, Kathryn North, Ewan Birney</small> (2021):  
**GA4GH: International policies and standards for data sharing across genomic research and healthcare**.  
*Cell Genomics* **1**(2):100029  
<https://doi.org/10.1016/j.xgen.2021.100029>

\[Reis 2022\] David Reis, Bruno Piedade, Filipe F, Correia, João Pedro Dias, Ademar Aguiar (2022): **Developing Docker and Docker-Compose Specifications**: A Developers' Survey.  
*IEEE Access* **10** pp. 2318--2329  
<https://doi.org/10.1109/ACCESS.2021.3137671>

\[Samaniego 2010\] Luis Samaniego, Rohini Kumar, Sabine Attinger (2010):  
**Multiscale parameter regionalization of a grid-based hydrologic model at the mesoscale**.  
<https://doi.org/10.1029/2008WR007327>

\[Samuel 2018\]
Sheeba Samuel, Birgitta König-Ries (2018):  
**ProvBook: Provenance-based Semantic Enrichment of Interactive Notebooks for Reproducibility**.  
_The 17th International Semantic Web Conference_ (ISWC) 2018 Demo Track.  
_CEUR Workshop Proceedings_ **2180**  
<http://ceur-ws.org/Vol-2180/paper-57.pdf>

\[Samuel 2022\] Sheeba Samuel, Birgitta König-Ries (2022):  
**End-to-End provenance representation for the understandability and reproducibility of scientific experiments using a semantic approach**.  
*Journal of Biomedical Semantics* **13**:1  
<https://doi.org/10.1186/s13326-021-00253-1>

\[Scheidegger 2008\] Carlos E. Scheidegger, Huy T. Vo, David Koop, Juliana Freire, Claudio T. Silva (2008):  
**Querying and re-using workflows with VsTrails**. *Proceedings of the 2008 ACM SIGMOD international conference on Management of data (SIGMOD '08)*  
<https://doi.org/10.1145/1376616.1376747>

\[Sirvent 2022\] Raul Sirvent, Javier Conejero, Francesc Lordan, Jorge Ejarque, Laura Rodriguez-Navas, Jose M. Fernandez, Salvador Capella-Gutierrez, Rosa M. Badia (2022):  
**Automatic, Efficient, and Scalable Provenance Registration for FAIR HPC Workflows**.  
*2022 IEEE/ACM Workshop on Workflows in Support of Large-Scale Science (WORKS)*  
<https://doi.org/10.1109/works56498.2022.00006>  
<https://hdl.handle.net/2117/384589>

\[Snowley 2023\] Kay Snowley, Lara Edwards, Ben Crosby, Helen Tatlow (2023):  
**Integrating Our Community**. Year 1  
*Health Data Research UK* (report)  
<https://www.hdruk.ac.uk/wp-content/uploads/2023/10/Integrating-Our-Community_v1-Oct-2023-compressed.pdf> (accessed [2023-12-06]())

\[Soiland-Reyes 2016\] Stian Soiland-Reyes, Pinar Alper, Carole Goble (2016):  
**Tracking Workflow Execution With TavernaPROV**, *ProvenanceWeek 2016*, session "PROV: Three Years Later"  
<https://s11.no/2016/provweek-tavernaprov/>  
<https://doi.org/10.5281/zenodo.51314>

\[Soiland-Reyes 2018\] Stian Soiland-Reyes, Farah Zaib Khan, Michael R Crusoe (2018):  
**common-workflow-language/cwlprov: CWLProv 0.6.0**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.1471585>

\[Soiland-Reyes 2021\] Stian Soiland-Reyes (2021):  
**Describing and packaging workflows using RO-Crate and BioCompute Objects**.  
Webinar for U.S. Food and Drug Administration (FDA), 2021-05-12  
*Zenodo*  
<https://doi.org/10.5281/zenodo.4633732>

\[Soiland-Reyes 2022a\] Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):  
**Packaging research artefacts with RO-Crate**.  
*Data Science* **5**(2)  
<https://doi.org/10.3233/DS-210053> 

\[Soiland-Reyes 2022c\] Stian Soiland-Reyes, Peter Sefton, Leyla Jael Castro, Frederik Coppens, Daniel Garijo, Simone Leo, Marc Portier, Paul Groth (2022):  
**Creating lightweight FAIR digital objects with RO-Crate**.  
*Research Ideas and Outcomes* **10**(8)  
<https://doi.org/10.3897/rio.8.e93937> 

\[Soiland-Reyes 2023e\] Stian Soiland-Reyes, Stuart Wheater (2023):  
**Five Safes RO-Crate profile**, version 0.4.  
*TRE-FX Candidate Recommendation*  
<https://w3id.org/5s-crate/0.4>

\[Soiland-Reyes 2023f\] Stian Soiland-Reyes, Stuart Wheater, Thomas Giles, Carole Goble, Philip Quinlan (2023):  
**TRE-FX Technical Documentation - Five Safes RO-crate**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10376350>

\[Sporny 2020\] Manu Sporny, Dave Longley, Gregg Kellogg, Markus Lanthaler, Pierre-Antoine Champin, Niklas Lindström (2020):  
**JSON-LD 1.1: A JSON-based Serialization for Linked Data**.  
*W3C Recommendation* 16 July 2020  
<https://www.w3.org/TR/2020/REC-json-ld11-20200716/>

\[Suetake 2022\] Hirotaka Suetake, Tomoya Tanjo, Manabu Ishii, Bruno P. Kinoshita, Takeshi Fujino, Tsuyoshi Hachiya, Yuichi Kodama, Takatomo Fujisawa, Osamu Ogasawara, Atsushi Shimizu, Masanori Arita, Tsukasa Fukusato, Takeo Igarashi, Tazro Ohta (2022):  
**Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics** 
\[version 1; peer review: 2 approved with reservations\].  
*F1000Research* **11**:889  
<https://doi.org/10.12688/f1000research.122924.1>¾¾

\[Suetake 2023a\] Hirotaka Suetake, Tsukasa Fukusato, Takeo Igarashi, Tazro Ohta (2023):  
**A workflow reproducibility scale for automatic validation of biological interpretation results**.  
*GigaScience* **12**:iad031  
<https://doi.org/10.1093/gigascience/giad031>

\[Suetake 2023b\] Hirotaka Suetake, Tazro Inutano Ohta, Tomoya Tanjo, Manabu ISHII, Bruno P. Kinoshita, DrYak (2023):  
**sapporo-wes/sapporo-service**: 1.5.1  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10134452>

\[Vivian 2017\] John Vivian, Arjun Arkal Rao, Frank Austin Nothaft, Christopher Ketchum, Joel Armstrong, Adam Novak, Jacob Pfeil, Jake Narkizian, Alden D Deran, Audrey Musselman-Brown, Hannes Schmidt, Peter Amstutz, Brian Craft, Mary Goldman, Kate Rosenbloom, Melissa Cline, Brian O'Connor, Megan Hanna, Chet Birger, W James Kent, David A Patterson, Anthony D Joseph, Jingchun Zhu, Sasha Zaranek, Gad Getz, David Haussler & Benedict Paten (2017):  
**Toil enables reproducible, open source, big biomedical data analyses**.  
*Nature Biotechnology* **35**(4)  
<https://doi.org/10.1038/nbt.3772>

\[W3C 2012\] W3C OWL Working Group (2012):  
**OWL 2 Web Ontology Language Document Overview** (Second Edition).  
*W3C Recommendation* 11 December 2012  
<https://www.w3.org/TR/2012/REC-owl2-overview-20121211>

\[de Wit 2022\] Renske de Wit (2022):  
**A Non-Intimidating Approach to Workflow Reproducibility in Bioinformatics**: Adding Metadata to Research Objects through the Design and Evaluation of Use-Focused Extensions to CWLProv.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.7113250>

\[de Wit 2023\] Renske de Wit, Michael R Crusoe (2023):  
**Analysis of runcrate**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.10251812>

\[Wittner 2022\] Rudolf Wittner, Cecilia Mascia, Matej Gallo, Francesca Frexia, Heimo Müller, Markus Plass, Jörg Geiger, Petr Holub (2022):  
**Lightweight Distributed Provenance Model for Complex Real--world Environments**.  
*Scientific Data* **9**:503  
<https://doi.org/10.1038/s41597-022-01537-6>

\[Wittner 2023b\] Rudolf Wittner, Matej Gallo, Simone Leo, Cecilia Mascia, Francesca Frexia, Markus Plass, Stian Soiland-Reyes, Heimo Müller, Jörg Geiger, Petr Holub (2023):  
**Linking provenance and its metadata in multi-organizational environments of life sciences**.  
*Submitted* (PeerJ Computer Science)  
<https://s11.no/2023/phd/linking-provenance/> (Supplement 17)

\[Wittner 2023c\] Rudolf Wittner, Matej Rudolf, Simone Leo, Stian Soiland-Reyes (2023):  
**Packing provenance using CPM RO-Crate profile** (Version 1.1)  
Data set.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.8095888>

\[WRROC 2024a\] Workflow Run RO-Crate working group (2024):  
**Process Run Crate specification**. Version 0.5  
*Zenodo*  
<https://w3id.org/ro/wfrun/process/0.5>  
<https://doi.org/10.5281/zenodo.12158562>

\[WRROC 2024b\] Workflow Run RO-Crate working group (2024):  
**Workflow Run Crate specification**. Version 0.4  
*Zenodo*  
<https://w3id.org/ro/wfrun/workflow/0.5>  
<https://doi.org/10.5281/zenodo.12159311>

\[WRROC 2024c\] Workflow Run RO-Crate working group (2024):  
**Provenance Run Crate specification**. Version 0.4  
*Zenodo*  
<https://w3id.org/ro/wfrun/provenance/0.5>  
<https://doi.org/10.5281/zenodo.12160782>

\[Yoo 2003\] Andy B. Yoo, Morris A. Jette, Mark Grondona (2003):  
**SLURM: Simple Linux Utility for Resource Management**.  
*Job Scheduling Strategies for Parallel Processing* (JSSPP 2003)  
*Lecture Notes in Computer Science* **2862**  
<https://doi.org/10.1007/10968987_3>

\[Zerouali 2023\] Ahmed Zerouali, Ruben Opdebeeck, Coen De Roover (2023):\
**Helm Charts for Kubernetes Applications: Evolution, Outdatedness and Security Risks**.\
*IEEE/ACM 20th International Conference on Mining Software Repositories* (MSR), Melbourne, Australia\
<https://doi.org/10.1109/MSR59073.2023.00078>


[Alterovitz 2018]: https://doi.org/10.1371/journal.pbio.3000099 "Enabling precision medicine via standard communication of HTS provenance, analysis, and results"
[Amstutz 2023]: https://doi.org/10.5281/zenodo.7575947 "common-workflow-language/cwltool: 3.1.20230127121939"
[Atkinson 2017]: https://doi.org/10.1016/j.future.2017.05.041 "Scientific workflows: Past, present and future"
[Bacall 2022]: https://w3id.org/workflowhub/workflow-ro-crate/1.0 "Workflow RO-Crate Profile 1.0"
[Bacall 2022b]: https://github.com/ResearchObject/ro-crate-ruby "GitHub – ResearchObject/ro-crate-ruby: A Ruby gem for creating, manipulating and reading RO-Crates"
[Bahra 2011]: https://doi.org/10.21957/nr843dob "Managing work flows with ecFlow"
[Batista 2022]:  https://doi.org/10.1038/s41597-022-01707-6 "Machine actionable metadata models"
[Bechhofer 2013]: https://doi.org/10.1016/j.future.2011.08.004 "Why Linked Data is not enough for scientists"
[Belhajjame 2015]: https://doi.org/10.1016/j.websem.2015.01.003 "Using a suite of ontologies for preserving workflow-centric research objects"
[Beltrán 2023]: https://doi.org/10.5281/zenodo.10199020 "Autosubmit v4.0.100"
[Bouyssié 2023]: https://doi.org/10.1101/2023.10.02.560412 "WOMBAT-P: Benchmarking Label-Free Proteomics Data Analysis Workflows"
[Chard 2016]: https://static.aminer.org/pdf/fa/bigdata2016/BigD418.pdf "I'll take that to go: Big data bags and minimal identifiers for exchange of large, complex datasets"
[Chard 2019]: https://zenodo.org/record/3381754 "Application of BagIt-serialized research object bundles for packaging and re-execution of computational analyses"
[Colonnelli 2021]: https://doi.org/10.1109/TETC.2020.3019202 "StreamFlow: cross-breeding Cloud with HPC"
[Colonnelli 2023a]: https://doi.org/10.5281/zenodo.7911906 "StreamFlow run of digital pathology tissue/tumor prediction workflow"
[Colonnelli 2023b]: https://github.com/alpha-unito/streamflow/releases/tag/0.2.0.dev10 "alpha-unito/streamflow"
[Costa 2013]: https://doi.org/10.1145/2457317.2457365 "Capturing and querying workflow runtime provenance with PROV"
[Crusoe 2022]: https://doi.org/10.1145/3486897 "Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language"
[Cuevas-Vicenttín 2016]: https://purl.dataone.org/provone-v1-dev "ProvONE: A PROV Extension Data Model for Scientific Workflow Provenance"
[De Geest 2022]: https://doi.org/10.3897/rio.8.e95164 "Enhancing RDM in Galaxy by integrating RO-Crate"
[De Geest 2023a]: https://github.com/researchobject/ro-crate-py "GitHub – ResearchObject/ro-crate-py: Python library for RO-Crate"
[De Geest 2023b]: https://doi.org/10.5281/zenodo.7785861 "Run of an example Galaxy collection workflow"
[Del Rio 2022]: https://doi.org/10.1007/978-3-031-13321-3_48 "AI Support for Accelerating Histopathological Slide Examinations of Prostate Cancer in Clinical Studies"
[Desai 2016]: https://econpapers.repec.org/RePEc:uwe:wpaper:20161601 "Five Safes: designing data access for research"
[Ejarque 2023]: https://doi.org/10.5281/zenodo.7975340 "COMPSs"
[Feng 2007]: https://doi.org/10.1145/1254882.1254906 "PBS: a unified priority-based scheduler"
[Fernández 2023a]: https://doi.org/10.5281/zenodo.10068956 "inab/WfExS-backend"
[Fernández 2023b]: https://doi.org/10.5281/zenodo.10091550 "RO-Crate from staged WfExS working directory"
[Ferreira da Silva 2021]: https://doi.org/10.48550/arXiv.2110.02168 "A Community Roadmap for Scientific Workflows Research and Development"
[Ferreira da Silva]: https://doi.org/10.48550/arXiv.2304.00019 "Workflows Community Summit 2022"
[Freire 2008]: https://doi.org/10.1109/MCSE.2008.79 "Provenance for Computational Tasks: A Survey"
[Galaxy 2022]: https://doi.org/10.1093/nar/gkac247 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update"
[Garijo 2011]: https://doi.org/10.1145/2110497.2110504 "A New Approach for Publishing Workflows"
[Garijo 2012]: https://ceur-ws.org/Vol-951/paper6.pdf "Augmenting PROV with Plans in P-PLAN: Scientific Processes as Linked Data"
[Garijo 2014b]: https://doi.org/10.1109/works.2014.13 "Towards Workflow Ecosystems through Semantic and Standard Representations"
[Gauthier 2019]: https://doi.org/10.1093/bib/bby063 "A brief history of bioinformatics"
[Gil 2011]: https://doi.org/10.1109/MIS.2010.9 "Wings: Intelligent Workflow-Based Design of Computational Experiments"
[Giles 2023]: https://doi.org/10.5281/zenodo.10055354 "TRE-FX: Delivering a federated network of trusted research environments to enable safe data analytics"
[Goble 2020]: https://doi.org/10.1162/dint_a_00033 "FAIR Computational Workflows"
[Goble 2021]: https://doi.org/10.5281/zenodo.4605654 "Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory"
[Gray 2017]: https://iswc2017.semanticweb.org/paper-579/ "Bioschemas: From Potato Salad to Protein Annotation"
[Guha 2015]: https://doi.org/10.1145/2857274.2857276 "Schema.org: Evolution of Structured Data on the Web: Big data makes common schemas even more necessary"
[Herschel 2017]: https://doi.org/10.1007/s00778-017-0486-1 "A survey on provenance: What for? What form? What from?"
[Himanen 2019]: https://doi.org/10.1002/advs.201900808 "Data-Driven Materials Science: Status, Challenges, and Perspectives"
[Huntingford 2019]: https://doi.org/10.1088/1748-9326/ab4e55 "Machine learning and artificial intelligence to aid climate change research and preparedness"
[IEEE 2791-2020]: https://research.manchester.ac.uk/en/publications/936de52b-ac53-4f0e-9927-77fd7073e88d "IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication"
[Isaac 2009]: https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/ "SKOS Simple Knowledge Organization System Primer"
[Khan 2019]: https://doi.org/10.1093/gigascience/giz095 "Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv"
[Kinoshita 2023]: https://doi.org/10.5281/zenodo.8144612 "RO-Crate created using Autosubmit version 4.0.100 workflow running kinow/auto-mhm-test-domains"
[Köster 2012]: https://doi.org/10.1093/bioinformatics/bts480 "Snakemake—a scalable bioinformatics workflow engine"
[Kumar 2013]: https://doi.org/10.1029/2012WR012195 "Implications of distributed hydrologic model parameterization on water fluxes at multiple scales and locations"
[Lebo 2013a]: https://www.w3.org/TR/2013/REC-prov-o-20130430/ "PROV-O: The PROV Ontology"
[Leo 2023a]: https://github.com/ResearchObject/runcrate "runcrate"
[Leo 2023b]: https://doi.org/10.48550/arXiv.2312.07852 "Recording provenance of workflow runs with RO-Crate"
[Leo 2023c]: https://w3id.org/ro/doi/10.5281/zenodo.10368989 "Recording provenance of workflow runs with RO-Crate"
[Leo 2023]: https://doi.org/10.5281/zenodo.7774351 "Run of digital pathology tissue/tumor prediction workflow"
[Lordan 2014]: https://doi.org/10.1007/s10723-013-9272-5 "ServiceSs: An interoperable programming framework for the cloud"
[Manubens-Gil 2016]: https://doi.org/10.1109/HPCSim.2016.7568429 "Seamless management of ensemble climate prediction experiments on HPC platforms"
[Meurisse 2023]: https://s11.no/2023/phd/federated-causal-inference/ "Federated causal inference based on real-world observational data sources"
[Missier 2013]: https://doi.org/10.5555/2482949.2482961 "D-PROV: extending the PROV provenance model with workflow structure"
[Moreau 2013]: https://www.w3.org/TR/2013/REC-prov-dm-20130430/ "PROV-DM: The PROV Data Model"
[Ohta 2023]: https://doi.org/10.5281/zenodo.10134581 "Example of Workflow Run RO-Crate Output in Sapporo"
[Oliver 2019]: https://doi.org/10.1109/MCSE.2019.2906593 "Workflow Automation for Cycling Systems"
[Pérez 2018]: https://doi.org/10.1007/s10115-018-1164-3 "A systematic review of provenance systems"
[Poiata 2016]: https://doi.org/10.1093/gji/ggw071 "Multiband array detection and location of seismic sources recorded by dense seismic networks"
[Poiata 2023]: https://doi.org/10.5281/zenodo.7788030 "BackTrackBB: Multi-band array detection and location of seismic sources (PyCOMPSs implementation)"
[Rehm 2021]: https://doi.org/10.1016/j.xgen.2021.100029 "GA4GH: International policies and standards for data sharing across genomic research and healthcare"
[Reis 2022]: https://doi.org/10.1109/ACCESS.2021.3137671 "Developing Docker and Docker-Compose Specifications"
[Samaniego 2010]: https://doi.org/10.1029/2008WR007327 "Multiscale parameter regionalization of a grid-based hydrologic model at the mesoscale"
[Samuel 2018]: http://ceur-ws.org/Vol-2180/paper-57.pdf "ProvBook: Provenance-based Semantic Enrichment of Interactive Notebooks for Reproducibility"
[Samuel 2022]: https://doi.org/10.1186/s13326-021-00253-1 "End-to-End provenance representation for the understandability and reproducibility of scientific experiments using a semantic approach"
[Scheidegger 2008]: https://doi.org/10.1145/1376616.1376747 "Querying and re-using workflows with VsTrails"
[Sirvent 2022]: https://hdl.handle.net/2117/384589 "Automatic, Efficient, and Scalable Provenance Registration for FAIR HPC Workflows"
[Snowley 2023]: https://www.hdruk.ac.uk/wp-content/uploads/2023/10/Integrating-Our-Community_v1-Oct-2023-compressed.pdf "Integrating Our Community"
[Soiland-Reyes 2016]: https://s11.no/2016/provweek-tavernaprov/ "Tracking Workflow Execution With TavernaPROV"
[Soiland-Reyes 2018]: https://doi.org/10.5281/zenodo.1471585 "common-workflow-language/cwlprov: CWLProv 0.6.0"
[Soiland-Reyes 2021]: https://doi.org/10.5281/zenodo.4633732 "Describing and packaging workflows using RO-Crate and BioCompute Objects"
[Soiland-Reyes 2022a]: https://s11.no/2022/phd/ro-crate/ "Packaging research artefacts with RO-Crate"
[Soiland-Reyes 2022c]: https://s11.no/2022/phd/fdo-with-ro-crate/ "Creating lightweight FAIR digital objects with RO-Crate"
[Soiland-Reyes 2023e]: https://w3id.org/5s-crate/0.4 "Five Safes RO-Crate profile"
[Soiland-Reyes 2023f]: https://doi.org/10.5281/zenodo.10376350 "TRE-FX Technical Documentation - Five Safes RO-crate"
[Sporny 2020]: https://www.w3.org/TR/2020/REC-json-ld11-20200716/ "JSON-LD 1.1: A JSON-based Serialization for Linked Data"
[Suetake 2022]: https://doi.org/10.12688/f1000research.122924.1 "Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics"
[Suetake 2023a]: https://doi.org/10.1093/gigascience/giad031 "A workflow reproducibility scale for automatic validation of biological interpretation results"
[Suetake 2023b]: https://doi.org/10.5281/zenodo.10134452 "sapporo-wes/sapporo-service"
[Vivian 2017]: https://doi.org/10.1038/nbt.3772 "Toil enables reproducible, open source, big biomedical data analyses"
[W3C 2012]: https://www.w3.org/TR/2012/REC-owl2-overview-20121211 "OWL 2 Web Ontology Language Document Overview"
[de Wit 2022]: https://doi.org/10.5281/zenodo.7113250 "A Non-Intimidating Approach to Workflow Reproducibility in Bioinformatics"
[de Wit 2023]: https://doi.org/10.5281/zenodo.10251812 "Analysis of runcrate"
[Wittner 2022]: https://doi.org/10.1038/s41597-022-01537-6 "Lightweight Distributed Provenance Model for Complex Real--world Environments"
[Wittner 2023b]: https://s11.no/2023/phd/linking-provenance/ "Linking provenance and its metadata in multi-organizational environments of life sciences"
[Wittner 2023c]: https://doi.org/10.5281/zenodo.8095888 "Packing provenance using CPM RO-Crate profile"
[WRROC 2024a]: https://w3id.org/ro/wfrun/process/0.4 "Process Run Crate specification"
[WRROC 2024b]: https://w3id.org/ro/wfrun/workflow/0.4 "Workflow Run Crate specification"
[WRROC 2024c]: https://w3id.org/ro/wfrun/provenance/0.4 "Provenance Run Crate specification"
[Yoo 2003]: https://doi.org/10.1007/10968987_3 "SLURM: Simple Linux Utility for Resource Management"
[Zerouali 2023]: https://doi.org/10.1109/MSR59073.2023.00078 "Helm Charts for Kubernetes Applications: Evolution, Outdatedness and Security Risks"

### Unmerged references


\[CWL 2024\] Common Workflow Language (2024):  
[**Common Workflow Language Implementations*](https://www.commonwl.org/implementations/)  
_commonwl.org_ (2024-05-24)  
<https://www.commonwl.org/implementations/> [accessed 2024-05-24]()

[CWL 2024]: https://www.commonwl.org/implementations/ "Common Workflow Language Implementations"


Research Object Bundle context \[cited 2024 May 24\]
<https://w3id.org/bundle/context>



Workflow Run RO-Crate \[cited 2024 May 24\].
<https://www.researchobject.org/workflow-run-crate>

Workflow Run RO-Crate competency questions \[cited 2024 May 24\].
<https://www.researchobject.org/workflow-run-crate/requirements>

SPARQL queries for the Competency Questions \[cited 2024 June 4\].
<https://github.com/ResearchObject/workflow-run-crate/tree/main/docs/sparql>

Workflow Run RO-Crate GitHub repository \[cited 2024 July 2\].
<https://github.com/ResearchObject/workflow-run-crate>

RO-Crate JSON-LD context, version 1.1 \[cited 2024 May 24\].
<https://www.researchobject.org/ro-crate/1.1/context.jsonld>


Bioschemas ComputationalWorkflow Profile, version 1.0-RELEASE (09 March 2021) \[cited 2024 May 24\].
<https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE>

ro-terms: Workflow run namespace \[cited 2024 Jul 03\].
<https://w3id.org/ro/terms/workflow-run>


Schema.org HowToStep definition \[cited 2024 May 24\].
<https://schema.org/HowToStep>


Blankenberg D, Von Kuster G, Bouvier E, Baker D, Afgan E, Stoler N, et al.
Dissemination of scientific software with Galaxy ToolShed.
Genome Biology 2014;15:403.
doi: [10.1186/gb4161](https://doi.org/10.1186/gb4161)


Galaxy Workflow Format 2 Description \[cited 2024 May 24\].
<https://galaxyproject.github.io/gxformat2/v19_09.html>


Gabriel E, Fagg GE, Bosilca G, Angskun T, Dongarra JJ, Squyres JM et al.
Open MPI: Goals, Concept, and Design of a Next Generation MPI Implementation.
Lecture Notes in Computer Science, 2004;3241:97--104.
doi: [10.1007/978-3-540-30218-6\_19](https://doi.org/10.1007/978-3-540-30218-6_19).

Dagum L, Menon R.
OpenMP: an industry standard API for shared-memory programming.
IEEE Computational Science and Engineering 1998;5(1):46-55.
doi: [10.1109/99.660313](https://doi.org/10.1109/99.660313).

Lam SK, Pitrou A, Seibert S.
Numba: a LLVM-based Python JIT compiler.
In Proceedings of the Second Workshop on the LLVM Compiler Infrastructure in HPC 2015.
doi: [10.1145/2833157.2833162](https://doi.org/10.1145/2833157.2833162).


MareNostrum 4 user's guide \[cited 2024 May 24\].
<https://bsc.es/supportkc/docs/MareNostrum4/intro/>


Fernández JM, Rodríguez-Navas L, Muñoz-Cívico A, Iborra P, Lea D.
WfExS-backend. Version 1.0.0a0.
Zenodo, 2024.
doi: [10.5281/zenodo.12589121](https://doi.org/10.5281/zenodo.12589121)

Di Tommaso P, Chatzou M, Floden EW, Prieto Barja P, Palumbo E, Notredame C.
Nextflow enables reproducible computational workflows.
Nature Biotechnology 2017;35:316--319.
doi: [10.1038/nbt.3820](https://doi.org/10.1038/nbt.3820)

Bouyssié D, Altıner P, Capella-Gutierrez S, Fernández JM, Hagemeijer YP, Horvatovich P, et al.
WOMBAT-P: Benchmarking Label-Free Proteomics Data Analysis Workflows.
Journal of Proteome Research, 2023.
doi: [10.1021/acs.jproteome.3c00636](https://doi.org/10.1021/acs.jproteome.3c00636)

Fernández González JM.
RO-Crate from staged WfExS working directory 047b6dfc-3547-4e09-92f8-df7143038ff4 (overbridging templon).
Zenodo, 2024.
doi: [10.5281/zenodo.12588049](https://doi.org/10.5281/zenodo.12588049)

Fernández JM.
RO-Crate from staged WfExS working directory a37fee9e-4288-4a9e-b493-993a867207d0 (meer oxometalate).
Zenodo, 2024.
doi: [10.5281/zenodo.12622362](https://doi.org/10.5281/zenodo.12622362)

ro-terms: Sapporo namespace \[cited 2024 May 28\].
<https://github.com/ResearchObject/ro-terms/tree/master/sapporo>

The Galaxy Community.
Galaxy. Version 23.1
Software Heritage Archive, 2023.
<https://identifiers.org/swh:1:rel:33ce0ce4f6e3d77d5c0af8cff24b2f68ba8d57e9>


CRS4 Digital Pathology Platform \[cited 2024 May 27\].
<https://github.com/crs4/DigitalPathologyPlatform>

RO-Crate profiles \[cited 2024 July 1\].
<https://www.researchobject.org/ro-crate/profiles.html#ro-crate-profiles>

MIRAX format \[cited 2024 May 27\].
<https://openslide.org/formats/mirax/>

Common Provenance Model RO-Crate profile \[cited 2024 May 27\].
<https://w3id.org/cpm/ro-crate>

Wittner R, Holub P, Mascia C, Frexia F, Müller H, Plass M. et al.
Towards a Common Standard for Data and Specimen Provenance in Life Sciences.
Learning Health Systems 2023;e10365.
doi: [10.1002/lrh2.10365](https://doi.org/10.1002/lrh2.10365)

Wittner R, Soiland-Reyes S, Leo S, Meurisse M, Hermjakob H.
BY-COVID D4.3 Provenance model for infectious diseases.
Zenodo, 2024
doi: [10.5281/zenodo.10927253](https://doi.org/10.5281/zenodo.10927253)

The W3C SPARQL Working Group.
SPARQL 1.1 Overview. W3C Recommendation 21 March 2013 \[cited 2024 May 27\].
<https://www.w3.org/TR/sparql11-overview/>


de Wit R, Crusoe MR.
Analysis of runcrate.
Zenodo, 2024.
doi: [10.5281/zenodo.12689424](https://doi.org/10.5281/zenodo.12689424)

Leo S, Crusoe MR, Rodríguez-Navas L, Sirvent R, Kanitz A, De Geest P, et al.
Recording provenance of workflow runs with RO-Crate (RO-Crate and mapping).
Zenodo, 2023.
doi: [10.5281/zenodo.10368990](https://doi.org/10.5281/zenodo.10368990)


EOSC-ENTRUST: Creating a European network of TRUSTed research environments \[cited 2024 May 27\].
<https://eosc-entrust.eu/>


Stian Soiland-Reyes. Packaging BioCompute Objects using RO-Crate \[cited 2024 May 27\].
<https://biocompute-objects.github.io/bco-ro-crate/>

</footer>

</article>
