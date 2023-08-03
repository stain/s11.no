---
title: "Supplement 99: Recording provenance of workflow runs with RO-Crate"
weight: 9999
lang: en-GB
categories:
  - PhD
keywords:
  - workflow
  - provenance
  - RO-Crate
summary: > 
  Working Document
description: > 
    Recording the provenance of scientific computation results is fundamental to support traceability, reproducibility and quality assessment of data products. Several models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, they lack interoperability, flexibility and support from workflow management systems. In this work we present Workflow Run RO-Crate, an extension of RO-Crate (Research Object Crate) to capture the provenance of the execution of computational workflows at different levels of granularity. We describe the model, as well as its implementations in workflow systems, and show its applicability to machine learning for digital pathology use cases. The model is developed by a diverse, open community that runs regular meetings, discussing requirements and practical aspects. The format is already in use in several workflow managers, including Galaxy, allowing interoperable comparisons between runs from heterogeneous systems.
---

<h2>Cite as</h2>

Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2023):  
**Recording provenance of workflow runs with RO-Crate**.  
_In preparation_  

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown, abstract only


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

Recording the provenance of scientific computation results is fundamental to support traceability, reproducibility and quality assessment of data products. Several models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, they lack interoperability, flexibility and support from workflow management systems. In this work we present Workflow Run RO-Crate, an extension of RO-Crate (Research Object Crate) to capture the provenance of the execution of computational workflows at different levels of granularity. We describe the model, as well as its implementations in workflow systems, and show its applicability to machine learning for digital pathology use cases. The model is developed by a diverse, open community that runs regular meetings, discussing requirements and practical aspects. The format is already in use in several workflow managers, including Galaxy, allowing interoperable comparisons between runs from heterogeneous systems.

## (Work in progress)

_This manuscript is under development and will be published as a preprint once submitted. The below is a snapshot as of 2023-08-03 from <https://docs.google.com/document/d/1rq22Vu_lmmRLkmnZivsKVdRidq4aoePs-l20gHFYpu0/edit>_.


## Introduction

A crucial part of scientific research is recording the provenance of its
outputs. The W3C PROV standard defines provenance as "a record that
describes the people, institutions, entities, and activities involved in
producing, influencing, or delivering a piece of data or a thing"
\[Moreau 2013\]. Provenance is instrumental to activities such as
traceability, reproducibility, accountability, and quality assessment
\[Herschel 2017\]. The constantly growing size and complexity of
scientific datasets and the analysis that is required to extract useful
information from them has made science increasingly dependent on
advanced automated processing techniques in order to get from
experimental data to final results \[Himanen 2019, Gauthier 2019,
Huntingford 2019\]. Consequently, a large part of the provenance
information for scientific outputs consists of descriptions of complex
computer-aided data processing steps.

In order to homogenise the collection and interchange of provenance
records, the W3C consortium proposed the PROV-O standard \[Lebo 2013\],
a machine-readable representation for provenance in the Web. PROV-O has
been widely extended for workflows, where provenance information is
collected in two main forms: prospective and retrospective \[Freire
2008\]. *Prospective provenance*, i.e. the execution plan, is
essentially the workflow itself: it includes a machine-readable
specification with the steps to perform and the data and software
dependencies to carry out a computation. *Retrospective provenance*
refers to what actually happened during an execution, i.e. what were the
values of the input parameters, which outputs were produced, which tools
were executed, how much time did the execution take, whether the
execution was successful or not, etc. Retrospective provenance can also
be represented at different levels of abstraction depending on available
computing resources, e.g. by the workflow execution becoming a single
activity which produces results, by specifying the individual execution
of each workflow step, or by going a step further and indicating how
each step is further divided into sub-processes when a workflow is
deployed in a cluster.

Different workflow systems have adopted and extended PROV to the
workflow domain \[Belhajjame 2013b, pegasus, Vistrails etc.\], in order
to ease the burden of provenance collection from tool developers to
workflow management systems (WMSs) \[Atkinson 2017\]. For example, \[REF
D-PROV, PROV-ONE, OPMW-PROV, P-Plan, additionals?\] propose alternate
representations of workflow plans and their respective executions,
taking into account the features of the workflow systems implementing
them (e.g., hierarchical representations, sub-processes, etc.). Other
data models like *wfprov* and *wfdesc* \[Belhajjame 2015\] go a step
further by considering not only the link between plans and executions,
but how to package everything as a Research Object \[Bechhofer 2013\] in
order to ease portability while keeping the context of a digital
experiment. However, while these data models address some workflow
provenance representation issues, they have two main limitations: first,
the extensions are not interoperable at lower levels of granularity, due
to different assumptions in workflow representation. second, they lack
support from state of the art workflow systems, which aim for more
lightweight representations.

These problems have been partially addressed by CWLProv \[Khan 2019\],
which represents the workflow enactment as ROs serialised according to
the BDBag approach \[Chard 2016\]. The resulting format is a folder
containing several data and metadata files \[Soiland-Reyes 2018\].
CWLProv also extends PROV with a representation of executed processes
(activities), their inputs and outputs (entities) and their executors
(agents), together with their Common Workflow Language specification
\[Crusoe 2022\], a standard workflow specification adopted by at least a
dozen different workflow systems
([[https://www.commonwl.org/implementations/]{.underline}](https://www.commonwl.org/implementations/)).
Although CWLProv includes a prospective provenance as a *plan* within
the PROV (based on the *wfdesc* model), this does not include tool
definitions or file formats. In order for CWLProv consumers to
reconstruct the full perspective for understanding the workflow, they
would also need to inspect the separate workflow definition in the
WMS\'s native language. Additionally, the CWLProv RO can include several
other BagIt metadata files and PROV serialisations conforming to
different formats, complicating its generation and consumption.
Moreover, CWLProv in practice records the details of all task executions
together with the intermediate data, requiring substantial support from
the WMS \[Soiland-Reyes 2022a\]. This approach, while appropriate for
workflow languages where the execution plan, including its distribution
among the various tasks, is well known in advance (such as CWL), can be
at odds with other systems where the execution is more dynamic,
depending on the verification of specific runtime conditions, such as
the size and distribution of the data (e.g., COMPSs \[Lordan 2014\]).
This makes the implementation of CWLProv challenging, as shown by the
fact that at the time of writing the format is supported only by cwltool
\[Amstutz 2023\]. Finally, being based on the PROV model, CWLProv is
highly focused on the interaction between agents, processes and related
entities, while support for contextual metadata (e.g., workflow authors)
is limited and stored in a separate manifest file.

RO-Crate \[Soiland-Reyes 2022a\] is a recent approach to packaging
research data together with their metadata extending Schema.org \[Guha
2015\], a popular vocabulary for describing resources on the Web. In its
simplest form, an RO-Crate is a directory structure that contains a
single JSON-LD metadata file at the top level. The metadata file
describes all entities stored in the RO-Crate as well as their
relationships; it is both machine-readable and human-readable. The
format is general enough to be able to describe any dataset, but can
also be made as specific as needed through the use of extensions called
*profiles*. At the same time, the broad set of types and properties from
Schema.org, complemented by a few additional terms from other
vocabularies, make the RO-Crate model capable of expressing a wide range
of contextual information that complements and enriches the core
information regulated by the profile. This might include, for instance,
the workflow authors and their affiliations, associated publications,
licensing information, related software, etc.

In this work, we present Workflow Run RO-Crate (WRROC), an extension of
RO-Crate for representing computational workflow provenance. Our
contributions are the following:

-   A collection of RO-Crate profiles to represent both the prospective
    > and the retrospective provenance of a computational workflow run
    > in a way that is machine-actionable, independent of the specific
    > workflow language or execution system, and including support for
    > rerunnability.

-   Implementations of the model in XX workflow systems.

-   A governance and sustainability environment to discuss extensions,
    > issues and new implementations for the proposed profiles, possible
    > thanks to the WRROC community.

To foster usability, the profiles are characterised by different levels
of detail, and the number of required items is kept to a minimum in
order to ease the implementation. This flexible approach increases the
model's adaptability to the diverse landscape of WMSs used in practice.
The base profile, in particular, is applicable to any kind of
computational process, not necessarily described in a formal workflow
language. We describe several current or planned implementations as well
as demonstrations of the profiles\' application to multiple use cases.

The rest of this paper is organised as follows: we first describe the
Workflow Run RO-Crate profiles; we then illustrate implementations and
usage examples; this is followed by a discussion and plans for future
work.


## The Workflow Run RO-Crate profiles

An RO-Crate profile is an extension of the base RO-Crate specification
that describes how to represent the entities and relationships that
appear in a specific domain or use case. An RO-Crate conforming to a
profile is not just machine-readable, but also actionable as a digital
object whose type is represented by the profile itself \[Soiland-Reyes
2022c\].

The Workflow Run RO-Crate profiles are the main outcome of the
activities of an open working group that includes workflow users and
developers, WMS users and developers, and researchers and software
engineers interested in workflow execution provenance and FAIR
approaches for data and software. As requirements were being defined, it
became apparent that one single profile would not have been sufficient
to cater for all possible usage scenarios. In particular, while some use
cases required a detailed description of all computations orchestrated
by the workflow, others were only concerned with a "black box"
representation of the workflow and its execution as a whole.
Additionally, some computations, while involving a data flow across
multiple applications, are executed without the aid of a WMS and thus
are not formally described in a standard workflow language. This led to
the development of three profiles: Process Run Crate
([[https://w3id.org/ro/wfrun/process/0.1]{.underline}](https://w3id.org/ro/wfrun/process/0.1))
\[Workflow Run RO-Crate working group 2023a\] to describe the execution
of one or more tools that contribute to a computation; Workflow Run
Crate
([[https://w3id.org/ro/wfrun/workflow/0.1]{.underline}](https://w3id.org/ro/wfrun/workflow/0.1))
\[Workflow Run RO-Crate working group 2023b\] to describe a computation
orchestrated by a predefined workflow; Provenance Run Crate
([[https://w3id.org/ro/wfrun/provenance/0.1]{.underline}](https://w3id.org/ro/wfrun/provenance/0.1))
\[Workflow Run RO-Crate working group 2023c\] to describe a workflow
computation including the internal details of individual step
executions.

In the rest of this section we describe each of the above profiles in
detail; we also highlight their synergy with a profile to reference
distributed provenance representations and briefly touch on an extension
focused on workflows that handle sensitive data. We use italics to
denote the types and properties used to describe entities and their
relationships: these are defined in the RO-Crate JSON-LD context
([[https://www.researchobject.org/ro-crate/1.1/context.jsonld]{.underline}](https://www.researchobject.org/ro-crate/1.1/context.jsonld)),
which is largely based on Schema.org.


### Process Run Crate

The Process Run Crate profile contains guidelines on describing the
execution of one or more software applications that contribute to the
same overall computation, but are not necessarily coordinated by a
top-level workflow or script. For instance, they could be executed
manually by a human agent, one after the other as intermediate datasets
become available.

Being the basis for all profiles in the WRROC collection, Process Run
Crate specifies how to describe the fundamental entities involved in a
computational run: a software application (represented by
*SoftwareApplication*, *SoftwareSourceCode* or *ComputationalWorkflow*
entities) and its execution (represented by a *CreateAction* entity),
with the latter linking to the former via the *instrument* property.
Other important properties of the *CreateAction* entity are *object*,
which links to the action\'s inputs, and *result*, which links to its
outputs. The time the execution started and ended can be provided,
respectively, via the *startTime* and *endTime* properties. The *Person*
or *Organization* entity that performed the action is referred to via
the *agent* property. Fig. \[process\_crate\_er\] shows the entities
used in Process Run Crate together with their relationships.

![](image1.png)

Fig. \[process\_crate\_er\]. Entity-Relationship diagram for Process Run
Crate. The central entity is the *CreateAction*, which represents the
execution of an application. It relates with the application itself via
*instrument*, with the entity that executed it via *agent* and with its
inputs and outputs via *object* and *result*, respectively.

Suppose a user called John Doe runs the "head" tool to extract the first
ten lines of an input file called lines.txt, storing the result in
another file called selection.txt. Then, the same user runs the "sort"
tool on selection.txt, storing the sorted output in a file called
sorted\_selection.txt. Fig. \[head\_sort\] contains a diagram of the two
actions and their relationships to the other entities involved. Note how
the actions are connected by the fact that the output of "Run Head" is
also the input of "Run Sort": they form an "implicit workflow", whose
steps have been executed manually rather than by a higher level software
tool.

![](image2.png)

Fig. \[head\_sort\]. Diagram of a simple "implicit workflow" where the
head and sort programs were run manually by a user. The executions are
connected by the fact that the file output by head was used as input for
sort. Such executions can be represented with Process Run Crate.

Process Run Crate extends the RO-Crate guidelines on representing
software used to create files with additional requirements and
conventions. This arrangement is typical of the RO-Crate approach, where
the base specification provides general recommendations to allow for
high flexibility, while profiles, being more concerned with the
representation of specific domains and machine actionability, provide
more detailed and structured definitions. Nevertheless, in order to be
broadly applicable, profiles also need to avoid the specification of too
many strict requirements, trying to strike a good trade-off between
flexibility and actionability. One of the implications of this approach
is that consumers need to code defensively, avoiding unwarranted
assumptions.

While an input or output parameter is usually a single file or
directory, some applications expect a "composite" dataset consisting of
multiple files and directories, which is treated as a single unit; this
happens, for instance, with some digital image formats where a single
image can be stored across multiple data and metadata files. The profile
specifies that such datasets should be represented by a *Collection*
entity linking to individual files and directories via the *hasPart*
property, and referencing the main part (if any) via the *mainEntity*
property. An example of such a dataset is discussed in the section on
the digital pathology use case in Section TODO. Some inputs (and, less
commonly, outputs), however, are not stored as files or directories, but
passed to the application (e.g., via a command line interface) as single
values of various types (e.g., a number or string). In this case, the
profile recommends a representation via *PropertyValue*.


### Workflow Run Crate

This profile combines Process Run Crate and Workflow RO-Crate
([[https://w3id.org/workflowhub/workflow-ro-crate/1.0]{.underline}](https://w3id.org/workflowhub/workflow-ro-crate/1.0))
to describe the execution of workflows -- i.e., high-level applications
that coordinate multiple tools and manage intermediate outputs in order
to produce the final results. Such workflows are typically written in a
special-purpose language, such as CWL or Snakemake
[\[3\]](https://paperpile.com/c/x29KEH/SBay), and run by one or more WMS
(e.g., StreamFlow [\[1\]](https://paperpile.com/c/x29KEH/T16q),
Galaxy[\[2\]](https://paperpile.com/c/x29KEH/XOXr)). Like in Process Run
Crate, the execution is described by a *CreateAction* that links to the
application via *instrument*, but in this case the application must be a
workflow, as prescribed by Workflow RO-Crate. More specifically,
Workflow RO-Crate states that the RO-Crate must contain a main workflow
typed as *File*, *SoftwareSourceCode* and *ComputationalWorkflow*. The
execution of the individual workflow steps, instead, is not represented:
that is left to the Provenance Run Crate profile.

The Workflow Run RO-Crate profile also contains recommendations on how
to represent the workflow\'s input and output parameters, based on the
Bioschemas \[Gray 2017\] ComputationalWorkflow profile
([[https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE]{.underline}](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE))
(which, despite being part of Bioschemas, is not domain-specific). All
these elements are represented via the *FormalParameter* entity and are
referenced from the main workflow via the *input* and *output*
properties. While the entities referenced from *object* and *result* in
the *CreateAction* represent data entities and argument values that were
actually used in the workflow execution, the ones referenced from
*input* and *output* correspond to formal parameters, which acquire a
value when the workflow is run. In the profile, the relationship between
an actual value and the corresponding formal parameter is expressed
through the *exampleOfWork* property. For instance:

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

The derivation of Workflow Run Crate from Workflow RO-Crate makes
RO-Crates that conform to this profile compatible with the WorkflowHub
workflow registry \[Goble 2021\]. Thus, users of a WMS that implements
this profile (or Provenance Run Crate, which inherits it) are able to
register their workflows in WorkflowHub -- together with an execution
trace -- by simply running them and uploading the resulting RO-Crates.
Additionally, the inheritance mechanism allows to reuse the
specifications already developed for Workflow RO-Crate, which form part
of the guidelines on representing the prospective provenance.

Fig. \[workflow\_crate\_er\] shows the entities used in Workflow Run
Crate together with their relationships.

![](image3.png)

Fig. \[workflow\_crate\_er\]. Entity-Relationship diagram for Workflow
Run Crate. The main differences with Process Run Crate are the
representation of formal parameters and the fact that the application is
expected to be a workflow.



### Provenance Run Crate

The Provenance Run Crate profile extends Workflow Run Crate by adding
specifications on how to describe the internal details of the workflow
execution, including individual tool executions, intermediate outputs
and related parameters. Individual tool executions are represented by
additional *CreateAction* instances that refer to the tool itself via
*instrument* -- analogously to its use in Process Run Crate. The
workflow is required to refer to the tools it orchestrates through the
*hasPart* property, in line with recommendations from the Bioschemas
ComputationalWorkflow profile.

To represent the logical steps defined by the workflow, this profile
introduces the usage of *HowToStep* instances, which point to the
corresponding tools via the *workExample* property and are referenced
from the workflow via the *step* property; the execution of a step is
represented by a *ControlAction* pointing to the *HowToStep* via
*instrument* and to the *CreateAction* instance(s) that represent the
corresponding tool execution(s) via *object*. Note that a step execution
does not coincide with a tool execution: an example where this
distinction is apparent is when a step maps to multiple executions of
the same tool over a list of inputs (the \"scattering\" feature in CWL).

An RO-Crate following this profile can also represent the execution of
the WMS itself (e.g., cwltool, Nextflow \[Di Tommaso 2017\]) via
*OrganizeAction*, pointing to a representation of the WMS via
*instrument*, to the steps via *object* and to the workflow run via
*result*. The *object* attribute of the *OrganizeAction* can
additionally point to a configuration file containing a description of
the settings that affected the WMS\'s behaviour during the execution.

Fig. \[provenance\_crate\_er\] shows the various entities involved in
the representation of a workflow run via Provenance Run Crate together
with their relationships.

![](image4.png)

Fig. \[provenance\_crate\_er\]. Entity-Relationship diagram for
Provenance Run Crate. In addition to the workflow run, this profile
represents the execution of individual steps and their related tools.

This profile also includes specifications on how to describe connections
between parameters. Parameter connections -- a fundamental feature of
computational workflows -- describe (i) how tools take as input the
intermediate outputs generated by other tools and (ii) how
workflow-level parameters are mapped to tool-level parameters. For
instance, in the workflow pictured in Fig. \[revsort\], the output of
the *rev* step is used as one of the inputs for the *sorted* step.

![](image5.png)

Fig. \[revsort\]. Diagram of a simple workflow that reverses each line
of the input file and then sorts the resulting stream. The workflow
connects the output parameter of the "rev" tool to the input parameter
of the "sort" tool. Provenance Run Crate provides a formalism to
represent such connections.

A representation of parameter connections is particularly useful for
traceability, since it allows to document the inputs and tools on which
workflow outputs depend. However, the current RO-Crate context has no
suitable terms for the description of such relationships. This gap led
us to the development of a context extension through a dedicated
\"workflow-run\" namespace in ro-terms
([[https://github.com/ResearchObject/ro-terms]{.underline}](https://github.com/ResearchObject/ro-terms)).
The extension defines a new *ParameterConnection* type with
*sourceParameter* and *targetParameter* attributes that respectively map
to the source and target formal parameters, and a *connection* property
to link from the relevant step or workflow to the *ParameterConnection*
instances.

Provenance Run Crate is the profile that most closely matches the level
of detail provided by CWLProv, which extends W3C PROV. Table
\[rocrate\_prov\_mapping\] shows how the main entities and relationships
represented by Provenance Run Crate map to PROV constructs.

| W3C PROV                                | RO-Crate                                              |
| --------------------------------------- | ----------------------------------------------------- |
| *activity* (workflow/process execution) | *CreateAction*                                        |
| *agent* (WMS)                           | *OrganizeAction*                                      |
| *agent* -- *Person*                     | *Person*                                              |
| *agent* -- *Organization*               | *Organization*                                        |
| *agent* -- *SoftwareAgent*              | *SoftwareApplication*                                 |
| *entity* -- *Plan*                      | *ComputationalWorkflow*, *SoftwareApplication, HowTo* |
| *entity* (other)                        | *File*, *Dataset*, *PropertyValue*                    |
| *wasStartedBy*                          | *agent* and *startTime* on *CreateAction*             |
| *wasEndedBy*                            | *agent* and *endTime* on *CreateAction*               |
| *wasAssociatedWith*                     | *agent* and *instrument* on *CreateAction*            |
| *used*                                  | *object* on *CreateAction*                            |
| *wasGeneratedBy*                        | *result* on *CreateAction*                            |

Table \[rocrate\_prov\_mapping\]. Mapping between W3C PROV concepts and
their equivalents in Workflow Run RO-Crate.


### Synergy with the CPM RO-Crate profile

The Common Provenance Model (CPM) \[Wittner 2022\], an extension of the
W3C PROV model \[Moreau 2013\], is a recently developed provenance model
that enables the representation of distributed provenance. Distributed
provenance is created when an object involved in the research process,
either digital or physical (e.g., biological material), is exchanged
between organisations, so that each organisation can document only a
portion of the object's life cycle. Individual provenance components are
generated, stored, and managed individually by each organisation, and
are linked together in a *chain*. The CPM prescribes how to represent
such provenance, and how to enable its traversal and processing using a
common algorithm, independently from the type of object being described.
In addition, the CPM defines a notion of meta-provenance, which contains
metadata about the history of individual provenance components.

CPM RO-Crate
([[https://w3id.org/cpm/ro-crate]{.underline}](https://w3id.org/cpm/ro-crate))
is an RO-Crate profile that supports the identification of CPM-based
provenance and meta-provenance files within an RO-Crate, allowing to
pack data, metadata, and CPM-based provenance information together. An
RO-Crate generated according to the CPM-RO-Crate profile embeds parts of
the distributed provenance, which may be linked to the provenance of
precursors and successors of the packed data.

The CPM-RO-Crate profile synergises well with Process Run Crate, since
the former can add references to CPM-based provenance descriptions of
computational executions described with the latter, integrating them in
the distributed provenance. Since CPM-based provenance and
meta-provenance files are typically themselves produced by computations,
Process Run Crate allows to represent these along with the main
computations that produce the datasets being exchanged, providing the
full picture in a cohesive ensemble. An example of such an RO-Crate is
presented in section \[Process Run Crate and CPM RO-Crate\].


### Trusted Workflow Run Crate

The TRE-FX project
([[https://trefx.uk/]{.underline}](https://trefx.uk/)) has developed
*Trusted Workflow Run Crate*
([[https://w3id.org/trusted-wfrun-crate/0.3]{.underline}](https://w3id.org/trusted-wfrun-crate/0.3)),
a profile that extends the Workflow Run Crate profile for use in
*Trusted Research Environments* (TRE) to handle sensitive health data in
federated workflow execution across TREs in the UK following the Five
Safes Framework \[Desai et al 2016\].

In this scenario, a crate with a workflow run request references a
pre-approved workflow and project details for manual and automated
assessment according to the TRE's agreement policy for the sensitive
dataset.

The crate goes through multiple phases internal to the TRE, including
validation, sign-off, workflow execution and disclosure control. At this
stage the crate is also conforming to the Workflow Run Crate profile.
The final crate is then safe to be made public. This extension of
Workflow Run Crate documents and supports the human review process --
important for transparency on TRE data usage. TRE-FX is implementing
this profile using WfExS as the workflow execution backend.



## Implementations

Support for the Workflow Run RO-Crate profiles presented in this work
has been implemented in a number of systems, showing support from the
community and already demonstrating a degree of usability in practice.
In addition, software support for producing and consuming the profiles
is also provided by the runcrate \[Leo 2023a\] utility toolkit, which
also serves as a reference implementation. All these implementations are
described in the following subsections.


### Runcrate

Runcrate is a generic Workflow Run RO-Crate toolkit. It consists of a
Python package with a nested command line interface, providing a
straightforward path to integration in Python software and other
workflows. The runcrate toolkit includes functionality to convert
CWLProv ROs to RO-Crates conforming to the Provenance Run Crate profile
(*runcrate convert*), effectively providing an indirect implementation
of the format for cwltool. Indeed, the CWLProv model provided a basis
for the Provenance Run Crate profile, and the implementation of a
conversion tool in runcrate at times drove the improvement and extension
of the profile as new requirements or gaps in the old designs emerged.
Runcrate converts both the retrospective provenance part of the CWLProv
RO (the RDF graph of the workflow\'s execution) and the prospective
provenance part (the CWL files, including the workflow itself). Both
parts are thus converted into a single, workflow language-agnostic
metadata resource.

Another functionality offered by the runcrate package is a sample
consumer that reports on the various executions described in an input
RO-Crate, listing their starting and ending times, the values of the
various parameters, etc. This tool (*runcrate report*) demonstrates how
the provenance profiles presented in this work enable comparison of runs
interoperably across different workflow languages or different
implementations of the same language.

We also added a *run* subcommand to re-execute the computation described
by an input Workflow Run Crate or Provenance Run Crate where CWL was
used as a workflow language. It works by mapping the RO-Crate
description of input parameters and their values (the workflow's *input*
and the action's *object*) to the format expected by CWL, which is then
used to relaunch the workflow on the input data. This functionality
shows the ability of the profiles to support reproducibility, and was
used to successfully re-execute the digital pathology annotation
workflow described in the examples section. Of course, achieving a full
re-execution in the general case may not always be possible:
reproducibility is supported by the profiles, but also benefits from the
characteristics of the workflow language (which should provide a clear
formalism to map input items to their corresponding parameter slots) and
from cooperation on the part of the workflow's author, who can help
considerably by containerizing the environment required by each step and
providing the relevant annotations (and this, of course, must in turn be
allowed by the workflow language).

We performed a qualitative analysis of runcrate's *convert* mode, in
which we evaluated how the generated RO-Crates preserve the metadata
contained in the CWLProv ROs from which they are derived. For this
analysis, we followed the same approach as for an earlier evaluation of
CWLProv \[De Wit 2022\]. In summary, the analysis of CWLProv was based
on a taxonomy of provenance, which we derived from example use cases of
ROs associated with a real-life bioinformatics workflow. In this
qualitative analysis, we distinguished three levels of representation:
firstly, in RDF; secondly, in a structured, but CWL-specific document;
and finally, in an unstructured, non-machine-accessible format. From
this earlier analysis, we concluded that the CWLProv RDF representation
of the workflow runs was relatively sparse, even though much of the
provenance metadata was contained in CWL-specific documents, such as the
packed workflow and input parameter file.

In our analysis of runcrate, we compared the CWLProv RDF provenance
graph with the RO-Crate metadata file. Because runcrate only generates
RO-Crates *after* workflow execution, we only considered components that
in CWLProv were at least partially represented in structured format
(CWL-specific or RDF), and analyzed their presence in RDF in RO-Crate
(the packed CWL workflow is identical between CWLProv and RO-Crate).

The results of the analysis are summarised in Table \[analysis\_table\].
Overall, most of the information contained in CWLProv RDF is transferred
to the RO-Crate metadata. In addition, the representation of some
categories of metadata has improved, notably Workflow parameters (WF2),
which were insufficiently described in CWLProv RDF but defined with type
and format in RO-Crate. Moreover, the format of input files (D2), which
was absent in CWLProv RDF, is represented in RO-Crate. One aspect in
which RO-Crate RDF is sparser than CWLProv is computational environment
(T5): whereas in CWLProv names of container images were preserved
(ENV3), this information is not carried over to the RO-Crate metadata
file in the current runcrate version, as the representation of container
images in the profiles is under discussion. It should be noted, however,
that reproducibility is still supported by the presence of container
image information in the CWL workflow file included in the RO-Crate.

In conclusion, our analysis shows that runcrate preserves most
provenance metadata previously shown to be relevant in realistic RO use
case scenarios. The full results of the analysis can be found at
https://github.com/RenskeW/runcrate-analysis.

*\[analysis\_table\]: Summarised results of our qualitative analysis of
runcrate. We compared RO-Crates with the CWLProv ROs from which they
were generated. The analysis was based on a provenance taxonomy
reflecting relevant provenance metadata based on realistic use cases for
ROs associated with a real-life bioinformatics workflow. We only
considered provenance metadata which was already represented in CWLProv
RDF or CWL-specific documents (packed.cwl, primary-job.json, and
primary-output.json). Since packed.cwl is also included in RO-Crate, we
only considered how the metadata was represented in
ro-crate-metadata.json. p = partially represented, f = fully
represented. \* = missing or unstructured representation in CWLProv.*

| Type | Subtype                           | Name                       | CWL-specific | CWLProv RDF | RO-Crate RDF |
| ---- | --------------------------------- | -------------------------- | ------------ | ----------- | ------------ |
| T1   | SC1                               | Workflow design            | f            |             |              |
| SC2  | Entity annotations                | p                          |              |             |              |
| SC3  | Workflow execution annotations \* |                            |              |             |              |
| T2   | D1                                | Data identification        | p            |             |              |
| D2   | File characteristics              | p                          | p            | p           |              |
| D3   | Data access                       | p                          |              |             |              |
| D4   | Parameter mapping                 | f                          | f            | f           |              |
| T3   | SW1                               | Software identification    | p            |             |              |
| SW2  | Software documentation            | p                          |              |             |              |
| SW3  | Software access                   | p                          |              |             |              |
| T4   | WF1                               | Workflow software metadata | f            | p           | p            |
| WF2  | Workflow parameters               | f                          | p            | p           |              |
| WF3  | Workflow requirements             | f                          |              |             |              |
| T5   | ENV1                              | Software environment \*    |              |             |              |
| ENV2 | Hardware environment \*           |                            |              |             |              |
| ENV3 | Container image                   | p                          | p            |             |              |
| T6   | EX1                               | Execution timestamps       | f            | f           |              |
| EX2  | Consumed resources \*             |                            |              |             |              |
| EX3  | Workflow engine                   | p                          | f            |             |              |
| EX4  | Human agent                       | f                          | f            |             |              |

### Galaxy

The Galaxy project \[Jalili 2020\] provides a WMS with data management
functionalities as a multi-user platform, aiming to make computational
biology more accessible to research scientists that do not have computer
programming or systems administration experience. Galaxy's most
prominent features include: a collection of 7500+ integrated tools
([[https://galaxyproject.org/toolshed/]{.underline}](https://galaxyproject.org/toolshed/));
a web interface that allows the execution and definition of workflows
using the integrated tools; a network of dedicated (public) Galaxy
instances.

The export of workflow execution provenance data as Workflow Run Crates
has been added in Galaxy's 23.0 release. This feature provides a more
interoperable alternative to the basic export of Galaxy workflow
*invocations*: the workflow definition; a set of serialisations of the
invocation-related metadata in Galaxy native, json-formatted files; and
the input and output data files. This is achieved by extracting
provenance from Galaxy entities related to the workflow run, along with
associated metadata, converting them to RO-Crate metadata using the
ro-crate-py library \[De Geest 2022\]; by describing all files contained
in the basic invocation export within the RO-crate metadata; and finally
by making the Workflow Run Crate available for export to the user
through Galaxy's web interface and API.

We extract the prospective provenance contained in Galaxy's YAML-based
gxformat2
([[https://galaxyproject.github.io/gxformat2/v19\_09.html]{.underline}](https://galaxyproject.github.io/gxformat2/v19_09.html))
workflow definition, which includes details of the analysis pipeline
such as the graph of tools that need to be executed, and metadata about
the data types required. The retrospective provenance -- i.e., the
details of the executed workflow such as the inputs, outputs, parameter
values used -- is extracted from Galaxy's data model
([[https://docs.galaxyproject.org/en/master/lib/galaxy.model.html]{.underline}](https://docs.galaxyproject.org/en/master/lib/galaxy.model.html)),
which is not directly accessible to users in the context of a public
Galaxy server. All of this provenance information is then mapped to
RO-Crate metadata, including some Galaxy-specific data entities such as
dataset collections. An exemplary exported Galaxy Workflow Run Crate is
made available on Zenodo \[De Geest 2023\].

In practice, a user would take the following steps to obtain a Workflow
Run Crate from a Galaxy instance: 1) create or download a Galaxy
workflow definition (e.g.: from WorkflowHub) and import it in a Galaxy
instance, or create a workflow through the Galaxy GUI directly; 2)
execute the workflow, providing the required inputs; 3) after the
workflow has run successfully, the corresponding RO-Crate will be
available for export from the Workflow Invocations list.

Future work includes adding metadata detailing each step of the workflow
run to conform to the Provenance Run Crate profile; developing and/or
integrating RO-Crate more deeply with import and export of Galaxy
histories through the implementation of a profile; further developing
features to allow for user-guided import of RO-Crates as Galaxy
datasets, histories and workflows.

### COMPSs

COMPSs \[Lordan 2014\] is a task-based programming model that allows
users to transform a sequential application into a parallel one by
simply annotating some of its methods, thus making it efficient to
exploit the resources available (either distributed or in a cluster).
When a COMPSs application is executed, a corresponding workflow
describing the application's tasks and their data dependencies is
dynamically generated and used by the COMPSs runtime to orchestrate the
execution of the application in the infrastructure. As a WMS, COMPSs
stands out for its many advanced features that enable applications to
achieve fine-grained high efficiency in HPC systems, such as the ability
to exploit underlying parallelisation frameworks (i.e. MPI, OpenMP),
compilers (e.g. NUMBA), failure management, task grouping, and more.

Provenance recording for COMPSs workflows has been explored in previous
work \[Sirvent 2022\], where the Workflow RO-Crate profile was adopted
in the implementation of a very lightweight approach to document
provenance while avoiding the introduction of any significant run time
performance overheads. However, because of the dynamic nature of COMPSs
workflows, the Workflow Run Crate profile is better suited to represent
them, since the workflow is created when the application is executed
and, thus, a prior static workflow definition does not exist before that
moment. Due to this limitation, the workflow entity in the metadata file
references the entry point application run by COMPSs, and formal
parameters are not listed (note that listing them is not required by the
profile) because inputs and outputs (both for each task and the whole
workflow) are determined at runtime. Following the same lightweight
approach mentioned above, COMPSs is able to export provenance data with
a post-processing operation that can be triggered at any moment after
the application has finished. The RO-Crate generation post-process uses
information recorded by the runtime to detect and automatically add
metadata of any input or output data assets used by the workflow.

Implementing Workflow Run Crate support in COMPSs required particular
attention to some aspects. For instance, the generation of a unique id
for the *CreateAction* representing the workflow run, combining hostname
and queuing system job id for supercomputer executions, and using
generated UUIDs for distributed environments, to add as much as
information available from the run while ensuring the id is unique. In
the *CreateAction*, the *description* term includes system information,
as well as relevant environment variables that provide details on the
execution environment (e.g., node list, CPUs per node). Finally, a
reference to the system's monitoring tool (when available) is also
included in the *subjectOf* clause, where authorised users can see
detailed profiling of the corresponding job execution, as provided by
MareNostrum IV supercomputer
([[https://bsc.es/supportkc/docs/MareNostrum4/intro/]{.underline}](https://bsc.es/supportkc/docs/MareNostrum4/intro/)).

To showcase the COMPSs adoption of the Workflow Run Crate profile, we
provide as an example the execution of the BackTrackBB \[Poiata 2016\]
application in the MareNostrum IV supercomputer. BackTrackBB targets the
detection and location of seismic sources using the statistical
coherence of the wave field recorded by seismic networks and antennas.
The resulting RO-Crate \[Poiata 2023\] complies with the Workflow Run
Crate profile, and includes the application source files, a diagram of
the workflow's graph, application profiling and input and output files.

The implementation of provenance recording following Workflow Run Crate
has been fully integrated in the COMPSs runtime, and is available since
release 3.2 (May 2023).

### StreamFlow

The StreamFlow framework \[Colonnelli 2020\] is a container-native WMS
based on the CWL standard. It has been designed around two primary
principles: first, it allows the execution of tasks in multi-container
environments, supporting the concurrent execution of communicating tasks
in a multi-agent ecosystem; second, it relaxes the requirement of a
single shared data space, allowing for hybrid workflow executions on top
of multi-cloud, hybrid cloud/HPC, and federated infrastructures.
StreamFlow orchestrates hybrid workflows by combining a *workflow
description* (e.g., a CWL workflow description and a set of input
values) with one or more *deployment descriptions* -- i.e.
representations of the execution environments in terms of
infrastructure-as-code (e.g., Docker Compose files, HPC batch scripts,
and Helm charts). A streamflow.yml file -- the entry point of each
StreamFlow execution -- binds each workflow step with the set of most
suitable execution environments. At execution time, StreamFlow
automatically takes care of all the secondary aspects, like scheduling,
checkpointing, fault tolerance, and data movements.

StreamFlow stores provenance data in a proprietary format into a
persistent pluggable database (using sqlite3 as the default choice).
After a CWL workflow execution completes, users can generate an RO-Crate
through the streamflow prov \<workflow\_name\> command, which extracts
the provenance data stored in the database for one or more workflow
executions and converts it to an RO-Crate archive that is fully
compliant with the Provenance Run Crate Profile, including the details
of each task run by the WMS. The StreamFlow configuration and a
description of the hybrid execution environment are preserved by
directly including the streamflow.yml file into the generated archive.
Support for the format has been integrated into the main development
branch and will be included in release 0.2.0.

### WfExS

WfExS-backend
([[https://github.com/inab/WfExS-backend]{.underline}](https://github.com/inab/WfExS-backend))
is a FAIR workflow execution service that aims to address some of the
difficulties found in analysing sensitive data in a secure manner. The
WfExS-backend delegates the actual workflow execution to a specific
workflow manager (e.g., Nextflow or cwltool). WfExS-backend fetches and
materialises all the elements needed to run a workflow -- i.e. the
workflow itself, the WMS, the required software containers and the
inputs. Of note, the orchestrator can consume RO-Crates from WorkflowHub
to import workflows to be executed.

Support has been added to the WfExS-backend to export provenance data as
RO-Crates following the Workflow Run Crate profile, which has proven to
be a mechanism suitable to semantically describe digital objects in a
way that simplifies embedding key details involved in analysis
reproducibility and replicability.

The WfExS-backend records details relevant to the prospective provenance
when a workflow is prepared for execution, such as the public URIs used
to fetch input data and workflows, fingerprints, and metadata derived
from workflow files, container images and input files. WfExS-backend has
explicit commands to generate both prospective and retrospective
provenance RO-Crates. If a workflow is executed more than once in the
very same staged directory, run details from all the executions are
represented in the retrospective provenance RO-Crate. Future
developments will also add support for embedding URIs of output results
that have been published to a suitable repository(like Zenodo DOIs, for
instance).

### Sapporo

Sapporo \[Suetake 2022a\] is an implementation of the Workflow Execution
Service (WES) API specification. WES is a standard proposed by the
Global Alliance for Genomics and Health (GA4GH) for cloud-based data
analysis platforms that receive requests to execute workflows. Sapporo
supports the execution of several workflow types, including cwltool,
toil, and StreamFlow. Sapporo includes features specifically tailored to
bioinformatics applications, including the calculation of feature
statistics from specific types of outputs generated by workflow runs.
For example, the system calculates the mapping rate of DNA sequence
alignments from BAM format files. To describe the feature values,
Sapporo uses the Workflow Run Crate profile extended with additional RO
terms to represent these biological features.

Further, the Tonkaz companion command line software has integrated
functionality to compare Run Crates generated by Sapporo to measure the
reproducibility of the workflow outputs \[Suetake 2022b\]. Developers
can use this unique feature to build a CI/CD platform for their
workflows to ensure that changes to the product do not produce an
unexpected result. Workflow users can also use this feature to verify
the results from the same workflow deployed in different environments.

While Sapporo supports Workflow Run Crate, since WES is a WMS wrapper,
it embeds the information in the files passed by the WES request to
record the provenance of execution rather than using the actual workflow
parameters meant for the wrapped WMS. Therefore, the representation of
inputs and output in the RO-Crate generated by Sapporo reflects the
layout of WES implementations, rather than that of a specific WMS.

### Autosubmit

Autosubmit \[Manubens-Gil 2016\] is an open source lightweight workflow
manager and meta-scheduler created in 2011 for use in climate research
to configure and run scientific experiments. It supports scheduling jobs
via SSH to Slurm, PBS and other remote batch servers used in HPC.

The "archive" feature was added in Autosubmit 3.1.0, released in 2015.
This feature archives the experiment directory and all its contents into
a ZIP file, which can be used later to access the provenance data or to
execute the Autosubmit experiment again. Even though the data in the ZIP
file includes prospective provenance and retrospective provenance, it
contains no structure, and users have no way to tell which is which from
just looking at the ZIP file and its contents.

Recent releases of Autosubmit 4 include an updated YAML configuration
management system that allows users to combine multiple YAML files into
a single unified configuration file. While this gave users flexibility,
it also increased the complexity to track the configuration changes and
to relate these to the provenance data.

Another feature added in Autosubmit 4 was the option to use only the
experiment manager features of Autosubmit, delegating the workflow
execution to a different backend workflow engine, like ecFlow \[Bahra
2011\], Cylc \[Oliver 2023\], or a CWL runner.

In order to give users a more structured way to archive provenance,
which includes the complete experiment configuration and the parameters
used to generate the unified experiment configuration, and also to allow
interoperability between workflow managers, the archive feature received
a new flag to generate Workflow Run RO-Crates instead of plain ZIP
files.

The prospective provenance data is extracted from the Autosubmit
experiment configuration. This includes the multiple YAML files, and the
unified YAML configuration, as well as the parameters used to preprocess
each file --- preprocessing replaces placeholders in script templates
with values from the experiment configuration. The retrospective
provenance data is included with the RO-Crate archive and includes logs
and other traces produced by the experiment workflow. Both prospective
and retrospective provenance data are included in the final RO-Crate
JSON-LD metadata file.

As one of the most recent implementations, much of the code added in
Autosubmit 4 for RO-Crates was adapted from existing implementations
like COMPSs and StreamFlow. ro-crate-py \[De Geest 2022\] was used for
the heavy lifting work of creating the RO-Crate archive in Python, and
adding information for the JSON-LD metadata.

The main challenges for adopting RO-Crate in Autosubmit were
incorporating Autosubmit's "Project" feature, and the lack of validation
tools and of documentation and examples on how to use the standard with
*coarse-grained* workflow management systems (as described in \[Goble
2020\]) that do not track inputs and outputs, which is the case of
Autosubmit --- as well as Cylc and ecFlow.

A Project in Autosubmit is an abstract concept that has a type and a
location. The type can be Git, Subversion, or Local. For each type the
location represents the URL of a code repository, or a directory on a
workstation or HPC file system used to copy the Project and its template
scripts (written in Shell, R, or Python) and any other files (input data
for a model, extra configuration files, binaries, etc.). The workflows
in Autosubmit have tasks with dependencies to other tasks, and each of
these tasks execute one of these template scripts. The RO-Crate archive
generated by Autosubmit includes only the project type and location, and
not the complete Project. This means users have the provenance of the
Project, but only those with the correct permissions can access it (this
is important since many applications run with Autosubmit can not be
publicly shared without consent).

Validation tools for RO-Crate archives are still under development, and
while there is a community-based review process to help and guide new
implementations, a tool that others can use as code is written will
contribute to a more agile development.

After working with the RO-Crate community on these issues, the
Autosubmit team adopted a mixed approach where Autosubmit initialises
the JSON-LD metadata from its configuration and local trace files, and
the user is responsible for providing a partial JSON-LD metadata object
in the Autosubmit YAML configuration. A pull request was created to
ro-crate-py to allow the RO-Crate JSON-LD metadata to be patched by
these partial JSON-LD metadata objects.

This way, users are able to provide the missing information from the
Autosubmit configuration model, like licence, authors, inputs, outputs,
formal parameters, and more. And by modifying ro-crate-py, future
implementers of RO-Crate that have a similar workflow configuration as
Autosubmit should be able to re-use it, while also using COMPSs,
StreamFlow, Autosubmit, and other implementations as reference.

A workflow was created using an example Autosubmit Project \[Kinoshita
2023\] designed using UFZ's mHM (mesoscale Hydrological Model)
\[Samaniego 2010\]\[Kumar 2013\] to validate the RO-Crate produced by
Autosubmit.


## Exemplary Use Cases

We evaluate our proposed format on two exemplary use cases, which are
similar in terms of application domain -- machine learning-aided tumour
detection in human prostate images -- but quite different in the way
computations are executed and provenance is represented: in the first,
the analysis is conducted by means of a CWL workflow and the outcome is
represented with Provenance Run Crate; in the second, a combination of
Process Run Crate and CPM RO-Crate is used to represent a sequence of
computations linked to their corresponding CPM provenance information.

### Provenance Run Crate for Digital Pathology

We present a use case that demonstrates the effectiveness of Provenance
Run Crate at recording provenance data in the context of digital
pathology. More specifically, we demonstrate the generation of RO-Crates
to save provenance data associated with the computational annotation of
magnified prostate tissue areas and cancer subregions using deep
learning models \[Del Rio 2022\]. The image annotation process is
implemented in a CWL workflow consisting of three steps, each executing
inference on an image using a deep learning model: inference of a
low-resolution tissue mask to select areas for further processing;
high-resolution tissue inference on areas identified in the previous
step to refine borders; high-resolution cancer identification on areas
identified in the first step. The two tissue inference steps run the
same tool, but set different values for the parameter that controls the
magnification level. The workflow is integrated in the CRS4 Digital
Pathology Platform
([[https://github.com/crs4/DigitalPathologyPlatform]{.underline}](https://github.com/crs4/DigitalPathologyPlatform)),
a web-based platform to support clinical studies involving the
examination and/or the annotation of digital pathology images.

Using the same exemplary workflow, we implemented provenance recording
on two different execution platforms. In the first case, the workflow
was executed with the StreamFlow WMS, for which the Provenance Run Crate
implementation is discussed in Section XXX. In the second case, we
executed the CWL workflow with cwltool and converted the resulting
CWLProv RO to a Provenance Run Crate with the runcrate tool (see Section
XXX).

The RO-Crates obtained in the two cases \[Colonnelli 2023, Leo 2023b\]
are very similar to each other, differing only in a few details: for
instance, \[Colonnelli 2023\] includes the StreamFlow configuration file
and has separate files for the workflow and the two tools, while \[Leo
2023b\] has the workflow and the tools stored in a single file (CWL\'s
\"packed\" format). Apart from these minor differences, the description
of the computation is essentially the same. Four actions are
represented: the workflow itself, the two executions of the tissue
extraction tool and the execution of the tumour classification tool.
Each action is linked to the corresponding workflow or tool via the
*instrument* property, and its starting and ending time are recorded;
for each action, input and output slots are referenced by the workflow,
while the corresponding values are referenced by the action itself. The
data entities and *PropertyValue* instances corresponding to the input
and output values link to the corresponding parameter slots via the
*exampleOfWork* property, providing information on the values taken by
the parameters. Listing \[ml\_pipeline\_streamflow\_report\] shows the
output of the *runcrate report* command for the StreamFlow RO-Crate.

```yaml
action: #30a65cba-1b75-47dc-ad47-1d33819cf156
  instrument: predictions.cwl (['SoftwareSourceCode', 'ComputationalWorkflow', 'HowTo', 'File'])
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


\[ml\_pipeline\_streamflow\_report\]

The *exampleOfWork* link between input / output values and parameter
slots is used by *runcrate run* to reconstruct the CWL input parameters
document needed to rerun the computation. The *alternateName* property,
which records the original name (i.e., at the time the computation was
run) of data entities, is also crucial for reproducibility in this case:
both StreamFlow and CWLProv, to avoid clashes, record input and output
files and directories using their SHA1 checksum as their names; this
particular workflow, however, expects the input dataset to be in the
MIRAX
([[https://openslide.org/formats/mirax/]{.underline}](https://openslide.org/formats/mirax/))
format, where the \"main\" file taken as an input parameter by the
processing application must be accompanied by a directory in the same
location with the same name apart from the extension. The runcrate tool
uses the *alternateName* to rename the input dataset as required, so
that the expected pattern can be picked up by the workflow during the
re-execution.

Thanks to the fact that both RO-Crates were generated following the best
practices to support reproducibility mentioned in the profiles, we were
able to re-execute both computations with the runcrate tool. This was
also made possible, however, by the inclusion of the information on
which container images to use for each tool in the CWL workflow.
Overall, this shows how reproducibility is a hard-to-achieve goal that
can only be supported, but not ensured, by the profiles, since it also
depends on factors like the characteristics of the computation, the
choice of workflow language and whether best practices such as
containerization are followed.

Interestingly, this use case highlighted the need to add specifications
on how to represent multi-file datasets as described in Sec. \[Workflow
Run ROC :: Process Run Crate\]. In the MIRAX format, in fact, the
\"main\" file must be accompanied by a directory in the same location
containing additional files with a specific structure.

### Process Run Crate and CPM RO-Crate for cancer detection

This section presents an RO-Crate created to describe an execution of a
computational pipeline that trains AI models to detect the presence of
carcinoma cells in high-resolution digital images of magnified human
prostate tissue. The pipeline consists of three main computational
steps: a preprocessing step that splits input images into small patches
and divides them into a training and a testing set; a training step that
trains the model to recognize the presence of carcinoma cells in the
images; an evaluation step that measures the accuracy of the trained
model on the testing set.

In addition to the pipeline steps, the RO-Crate describes additional
computations related to the generation of the CPM provenance and
meta-provenance files. All computations are described according to the
Process Run Crate profile, while the CPM files are referenced according
to the CPM RO-Crate profile (see Sec. \[Synergy with other profiles: CPM
RO-Crate\]). Also represented via Process Run Crate are: the input
dataset; the results of the pipeline execution; the scripts that
implement the pipeline; the log files generated by the scripts; a script
that converts the logs into the CPM files. This allowed to describe all
involved elements as a single aggregate, with entities and their
relationships represented according to the RO-Crate model. The RO-Crate
discussed here is available from Zenodo \[Wittner 2023\].

The CPM files complement the RO-Crate with internal details about the
pipeline execution, such as how the input dataset was split into
training and testing sets, or detailed information about each training
iteration of the AI model. For instance, the entity
ns\_training:modelIter2 present in the ns\_training:bundle\_training
bundle represents a checkpoint of the AI model after the second training
iteration. The entity's attributes contain paths to the respective model
stored as a file. The entity is related to the respective training
iteration activity ns\_training:trainIter1, which contains the iteration
parameters represented as an attribute list. In addition, the CPM
generally provides means to link the input dataset provenance to the
provenance of its precursors -- human prostate tissues and biological
samples the tissues were derived from; this is not included in the
example because we used a publicly available input database for which
provenance of the precursors was not available. However, the linking
mechanism for provenance precursors is exactly the same as between the
bundles for the AI pipeline parts. While the RO-Crate is focused on the
execution of the pipeline, the provenance included in the CPM files
intends to be interlinked with provenance of the precursors or
successors, providing means to traverse the whole provenance chain. As a
result, combining the CPM and RO-Crate enables the lookup of research
artefacts related to the computation across heterogeneous organisations
using the underlying provenance chain.



## Discussion

Explain why our approach is filling the gaps we detected in the intro +
related work. Also, why is this effort beneficial

1\. Comparison across wf systems. Now it's possible, before it was more
difficult because each wf system had their own PROV implementation

2\. Wht makes WRROC different: growing ecosystem; semantic, mostly
agnostic description of the involved datasets and provenance, ... →
Careful, because this is what PROV allows.

3\. Maybe add having schema.org extended makes this directly searchable
in the web, aligned with the FAIR principles.

4\. Having everything as a RO-Crate makes it possible to capture the
context of the workflow, and not only the trace standalone.

5.  RO-Crate + Workflow-specific ROC Community support/adoption

6.  Competency questions


The RO-Crate profiles presented here provide a framework to describe the
execution of a computational workflow together with contextual
information about the workflow itself and related entities. The profiles
are flexible, allowing to tailor the description to a broad variety of
use cases, and agnostic with respect to the WMS used. This, together
with the fact that prospective and retrospective provenance are recorded
under the same metadata model, facilitates implementations by multiple
workflow systems -- several of which have already been developed and are
described here -- allowing to perform comparisons between runs across
heterogeneous systems. Additionally, having everything described
according to the RO-Crate model allows to capture the context of the
workflow (e.g. authors, related publications) rather than the trace
alone. Being based on RO-Crate, the profiles and their implementations
are part of a growing ecosystem of tools and services
([[https://www.researchobject.org/ro-crate/in-use/]{.underline}](https://www.researchobject.org/ro-crate/in-use/)).
In particular, the Workflow Run Crate and Provenance Run Crate profiles
are compatible with the WorkflowHub FAIR workflow registry, allowing
workflow runs created with those profiles to be registered and easily
found and shared.

In the introduction, we have provided background on computational
provenance representation, focusing on CWLProv as the present work is,
in part, an effort to overcome its limitations. A project that uses
Bagit-serialized ROs similar to those used by CWLProv is Whole Tale
\[Chard 2019\], a web platform with a focus on the narrative around
scientific studies and their reproducibility, where the serialized ROs
are used to export data and metadata from the platform. In contrast, our
work is primarily focused on the RO-Crate profiles and their ability to
capture the provenance of computational workflow execution.

The Workflow Run RO-Crate profiles, the associated tooling, the
implementations and the examples are developed by a community that runs
regular virtual meetings (every two weeks at the time of writing) and
coordinates on Slack and the RO-Crate mailing list. The WRROC community
brings together members of the RO-Crate community \[Soiland-Reyes
2022a\], WMS users and developers, Workflow users and developers, GA4GH
\[5\] Cloud developers and provenance model authors, and is open to
anyone who is interested in the representation of workflow provenance.
The inclusion of WMS developers and workflow users was key to keeping
the specifications flexible, easy to implement and grounded on real use
cases, while the diversity of the stakeholders allowed to keep a
plurality of viewpoints while driving the model's development forward.

One of the first community efforts was to compile a list of requirements
in the form of competency questions
([[https://www.researchobject.org/workflow-run-crate/requirements]{.underline}](https://www.researchobject.org/workflow-run-crate/requirements))
to be addressed by the model. Each requirement is backed up by a
rationale and linked to a GitHub issue to drive the discussion forward;
when a requirement is addressed, related changes are integrated into the
profiles and the relevant issue is closed. Many of the original issues
are now closed, and the profiles had two releases.

One of the main benefits of this development process is that the format
is already in use, with several implementations already available.

## Conclusion

We presented Workflow Run RO-Crate, a collection of RO-Crate profiles to
represent the provenance of the execution of computational workflows. We
described the profiles and their implementations, shown how they apply
to real use cases and described the community behind their development
process. Workflow Run RO-Crate is already in use in several WMSs,
including Galaxy, and its flexibility facilitates its implementation in
more systems, allowing interoperability between workflow run
descriptions.

## Future Work

As discussed above, Workflow Run RO-Crate is an ongoing project driven
by an open community. A natural consequence of this is that the profiles
are not static entities, but keep being updated to cater for new
requirements and use cases. In-progress features are normally tracked in
the GitHub repository issues section
([[https://github.com/ResearchObject/workflow-run-crate/issues]{.underline}](https://github.com/ResearchObject/workflow-run-crate/issues)).
Things under discussion include a representation of the execution
environment through a description of container images and recording
resource usage. The runcrate toolkit is planned to be expanded both to
better support the current features and to include new ones that may
arise.

### Direct implementation in cwltool


### Cloud execution of Workflow Run Crates

The Global Alliance for Genomics and Health (GA4GH)
[\[5\]](https://paperpile.com/c/x29KEH/Czg8), an international nonprofit
organisation that aims to set and promote community-developed standards
and policies for the sharing and processing of genome-scale data,
defines a number of Cloud API standards that are designed to
cooperatively enable federated data sharing and processing use cases in
on-premise, hybrid and multi-cloud environments. Among them are the
Workflow Execution Service (WES) specification, which (as described
above in the Sapporo use case) enables WMS-agnostic interpretation of
workflows and scheduling of task execution, and the Task Execution
Service (TES) specification, which enables the execution of individual,
atomic, containerized tasks in a compute backend-independent manner.
Despite these API standards originating from use cases of the life
sciences and health care sector, their application is in no way limited
to these domains.

Of note, there exists some conceptual equivalence between the TES and
WES API standards on the one hand, and the RO-Crate profiles described
in this paper on the other. They do, however, serve different purposes:
While the RO-Crate profiles encourage rich metadata annotation and
comprehensive provenance tracking, the TES and WES API standards --
roughly the equivalents of Process and Workflow Run Crates, respectively
-- place their focus on the actual execution of tasks/processes and
workflows in cloud environments, by identifying a minimum set of common
parameters necessary to provide abstraction over different WMSs and
compute backends.

We are planning to undertake an in-depth analysis of the degree of
interoperability between these two sets of standards and liaise with the
GA4GH Cloud community to align schemas where necessary. We will then
build an interconversion library that attempts to (1) construct WES
workflow and TES task run requests from RO-Crates containing Provenance,
Workflow or Process Run requests and therefore allow their easy
(re)execution on any GA4GH Cloud API-powered infrastructure, and (2)
bundle information from the WES and TES (as well as other GA4GH Cloud
API resources, where available) to create or extend RO-Crates with
standards-compliant Process, Workflow or even Provenance RO-Crates.

## Acknowledgments

* Sardinian Regional Government through the XData Project
* EJP-RD, European Joint Programme on Rare Diseases(SC1-BHC-04-2018 Rare Disease European Joint Programme Cofund)
* Spanish Government (contract PID2019-107255GB)
* MCIN/AEI/10.13039/501100011033 (CEX2021- 001148-S)
* Generalitat de Catalunya (contract 2021-SGR-00412)
* European High-Performance Computing Joint Undertaking (JU) (No 955558) 
* EU NextGenerationEU/PRTR (project eFlows4HPC).
* ELIXIR Platform Task 2022-2023 funding for Task "Container Orchestration"
* Life Science Database Integration Project, NBDC of Japan Science and Technology Agency
* JSPS KAKENHI (Grant Number 20J22439)
* European Commission Horizon 2020 H2020-INFRAEDI-02-2018 823830 (BioExcel-2)
* European Commission Horizon 2020 H2020-INFRAEOSC-2018-2 824087 (EOSC-Life) 
* European Commission Horizon Europe HORIZON-INFRA-2021-EMERGENCY-01 101046203 (BY-COVID)
* European Commission Horizon Europe HORIZON-INFRA-2021-EOSC-01 101057388 (EuroScienceGateway)
* European Commission Horizon Europe HORIZON-INFRA-2021-EOSC-01-05 101057344 (FAIR-IMPACT)
* UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee grant number 10038963 (EuroScienceGateway)
* UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee grant number 10038992 (FAIR-IMPACT)

The authors would like to thank all participants to the Workflow Run
RO-Crate working group meetings for the fruitful discussions and
valuable feedback.

## References

\[Amstutz 2023\] Peter Amstutz, Michael R. Crusoe, Farah Zaib Khan,
Stian Soiland-Reyes, Manvendra Singh, Kapil kumar, John Chilton, Thomas
Hickman, boysha, Tomoya Tanjo, Rupert Nash, Kevin Hannon, ash, Michael
Kotliar, Brad Chapman, Andrey Kartashov, Guillermo Carrasco, Dan Leehr,
Nebojsa Tijanic, Joshua C. Randall, Miguel Boland, bogdang989, Chuck
McCallum, Hervé Ménager, Pau Ruiz Safont, Bruno P. Kinoshita, Denis
Yuen, Gijs Molenaar (2023):\
**common-workflow-language/cwltool: 3.1.20230127121939.**\
[[https://doi.org/10.5281/zenodo.7575947]{.underline}](https://doi.org/10.5281/zenodo.7575947)

\[Atkinson 2017\] Malcolm Atkinson, Sandra Gesing, Johan Montagnat, Ian
Taylor (2017): **Scientific workflows: Past, present and future**.
Future Generation Computer Systems 75:216-227.
[[https://doi.org/10.1016/j.future.2017.05.041]{.underline}](https://doi.org/10.1016/j.future.2017.05.041)

\[Bechhofer 2013\] Sean Bechhofer, Iain Buchan, David De Roure, Paolo
Missier, John Ainsworth, Jiten Bhagat, Philip Couch, Don Cruickshank,
Mark Delderfield, Ian Dunlop, Matthew Gamble, Danius Michaelides, Stuart
Owen, David Newman, Shoaib Sufi, Carole Goble (2013):\
**Why linked data is not enough for scientists.**\
Future Generation Computer Systems **29**(2):599-611\
[[https://doi.org/10.1016/j.future.2011.08.004]{.underline}](https://doi.org/10.1016/j.future.2011.08.004)

\[Belhajjame 2013\] Khalid Belhajjame, Jun Zhao, Daniel Garijo, Aleix
Garrido, Stian Soiland-Reyes, Pinar Alper, Oscar Corcho (2013):\
**A workflow PROV-corpus based on Taverna and Wings**.\
*Proceedings of the Joint EDBT/ICDT 2013 Workshops\
*[[https://doi.org/10.1145/2457317.2457376]{.underline}](https://doi.org/10.1145/2457317.2457376)

\[Belhajjame 2015\] Khalid Belhajjame, Jun Zhao, Daniel Garijo, Matthew
Gamble, Kristina Hettne, Raul Palma, Eleni Mina, Oscar Corcho, José
Manuel Gómez-Pérez, Sean Bechhofer, Graham Klyne, Carole Goble (2015):\
**Using a suite of ontologies for preserving workflow-centric research
objects**.\
*Web Semantics: Science, Services and Agents on the World Wide Web*
**32\
**[[https://doi.org/10.1016/j.websem.2015.01.003]{.underline}](https://doi.org/10.1016/j.websem.2015.01.003)

\[Chard 2016\] Kyle Chard et al. (2016)\
**I\'ll take that to go: Big data bags and minimal identifiers for
exchange of large, complex datasets.**\
2016 IEEE International Conference on Big Data (Big Data), pp. 319-328\
[[https://doi.org/10.1109/BigData.2016.7840618]{.underline}](https://doi.org/10.1109/BigData.2016.7840618)

\[Chard 2019\] Kyle Chard, Niall Gaffney, Matthew B. Jones, Kacper
Kowalik, Bertram Ludäscher, Timothy McPhillips, Jarek Nabrzyski,
Victoria Stodden, Ian Taylor, Thomas Thelen, Matthew J. Turk, Craig
Willis (2019):\
**Application of BagIt-Serialized Research Object Bundles for Packaging
and Re-Execution of Computational Analyses**.\
*2019 15th International Conference on eScience (eScience)\
*[[https://doi.org/10.1109/eScience.2019.00068]{.underline}](https://doi.org/10.1109/eScience.2019.00068)

\[Colonnelli 2020\] Iacopo Colonnelli, Barbara Cantalupo, Ivan Merelli,
Marco Aldinucci, **StreamFlow: cross-breeding Cloud with HPC**, in IEEE
Transactions on Emerging Topics in Computing, vol. 9, iss. 4, p.
1723--1737, 221,
[[https://doi.org/10.1109/TETC.2020.3019202]{.underline}](https://doi.org/10.1109/TETC.2020.3019202)

\[Colonnelli 2023\] Colonnelli, Iacopo (2023):\
**StreamFlow run of digital pathology tissue/tumor prediction
workflow**.\
Zenodo.\
[[https://doi.org/10.5281/zenodo.7911905]{.underline}](https://doi.org/10.5281/zenodo.7911905)

\[Crusoe 2022\] Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter
Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian
Soiland-Reyes, Bogdan Gavrilović, Carole Goble, The CWL Community
(2022):\
**Methods Included: Standardizing Computational Reuse and Portability
with the Common Workflow Language**.\
*Communications of the ACM* **65**(6)\
[[https://doi.org/10.1145/3486897]{.underline}](https://doi.org/10.1145/3486897)

\[De Geest 2023\] Paul De Geest (2023):\
**Run of an example Galaxy collection workflow**.\
Zenodo.\
[[https://doi.org/10.5281/zenodo.7785861]{.underline}](https://doi.org/10.5281/zenodo.7785861)

\[Del Rio 2022\] Del Rio, M. et al. (2022). **AI Support for
Accelerating Histopathological Slide Examinations of Prostate Cancer in
Clinical Studies.** In: Image Analysis and Processing. ICIAP 2022
Workshops. ICIAP 2022. Lecture Notes in Computer Science, vol 13373.
[[https://doi.org/10.1007/978-3-031-13321-3\_48]{.underline}](https://doi.org/10.1007/978-3-031-13321-3_48)

\[Desai 2016\] Tanvi Desai, Felix Ritchie, Richard Welpton (2016):\
**Five Safes: designing data access for research**.\
*Economics Working Paper Series* **1601**.\
[[https://econpapers.repec.org/RePEc:uwe:wpaper:20161601]{.underline}](https://econpapers.repec.org/RePEc:uwe:wpaper:20161601)

\[De Geest 2022\] De Geest, Paul, Droesbeke, Bert, Eguinoa, Ignacio,
Gaignard, Alban, Huber, Sebastiaan, Leo, Simone, Pireddu, Luca,
Rodríguez-Navas, Laura, Sirvent, Raül, & Soiland-Reyes, Stian (2022):\
**ro-crate-py (0.7.0).**\
Zenodo.\
[[https://doi.org/10.5281/zenodo.6594974]{.underline}](https://doi.org/10.5281/zenodo.6594974)

\[De Wit 2022\] Renske de Wit (2022):\
**A Non-Intimidating Approach to Workflow Reproducibility in
Bioinformatics: Adding Metadata to Research Objects through the Design
and Evaluation of Use-Focused Extensions to CWLProv.**\
Zenodo.\
[[https://doi.org/10.5281/zenodo.7113250]{.underline}](https://doi.org/10.5281/zenodo.7113250)

\[Freire 2008\] J. Freire, D. Koop, E. Santos and C. T. Silva (2008):\
**Provenance for Computational Tasks: A Survey**\
Computing in Science & Engineering **10**(3) 11-21\
[[https://doi.org/10.1109/MCSE.2008.79]{.underline}](https://doi.org/10.1109/MCSE.2008.79)

\[Goble 2020\] Carole Goble, Sarah Cohen-Boulakia, Stian Soiland-Reyes,
Daniel Garijo, Yolanda Gil, Michael R. Crusoe, Kristian Peters, Daniel
Schober (2020):\
**FAIR Computational Workflows**.\
*Data Intelligence* **2**(1):108--121\
[[https://doi.org/10.1162/dint\_a\_00033]{.underline}](https://doi.org/10.1162/dint_a_00033)

\[Goble 2021\] Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart
Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca
Pireddu, Laura Rodriguez-Navas, José Mª Fernández, Salvador
Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano,
Philip Ewels, Frederik Coppens (2021):\
**Implementing FAIR Digital Objects in the EOSC-Life Workflow
Collaboratory**.\
*Zenodo\
*[[https://doi.org/10.5281/zenodo.4605654]{.underline}](https://doi.org/10.5281/zenodo.4605654)

\[Guha 2015\] R.V. Guha, Dan Brickley and Steve Macbeth (2015):\
**Schema.org: Evolution of Structured Data on the Web: Big data makes
common schemas even more necessary.**\
Queue **13**(9):10--37\
[[https://doi.org/doi:10.1145/2857274.2857276]{.underline}](https://doi.org/doi:10.1145/2857274.2857276)

\[Gauthier 2019\] Jeff Gauthier, Antony T Vincent, Steve J Charette,
Nicolas Derome (2019):\
**A brief history of bioinformatics.**\
Briefings in Bioinformatics 20(6):1981--1996\
[[https://doi.org/10.1093/bib/bby063]{.underline}](https://doi.org/10.1093/bib/bby063)

\[Gray 2017\] Alasdair JG Gray, Carole Goble, Rafael C Jimenez, The
Bioschemas Community (2017):\
**Bioschemas: From Potato Salad to Protein Annotation.**\
ISWC (Posters, Demos & Industry Tracks)\
[[https://iswc2017.semanticweb.org/paper-579/]{.underline}](https://iswc2017.semanticweb.org/paper-579/)

\[Himanen 2019\] Lauri Himanen, Amber Geurts, Adam Stuart Foster,
Patrick Rinke (2019):\
**Data-Driven Materials Science: Status, Challenges, and
Perspectives.**\
Advanced Science 6(21):1900808\
[[https://doi.org/10.1002/advs.201900808]{.underline}](https://doi.org/10.1002/advs.201900808)

\[Huntingford 2019\] Chris Huntingford, Elizabeth S Jeffers, Michael B
Bonsall, Hannah M Christensen, Thomas Lees and Hui Yang (2019):\
**Machine learning and artificial intelligence to aid climate change
research and preparedness.**\
Environmental Research Letters 14(12):124007\
[[https://doi.org/10.1088/1748-9326/ab4e55]{.underline}](https://doi.org/10.1088/1748-9326/ab4e55)

\[Herschel 2017\] Melanie Herschel, Ralf Diestelkämper, Houssem Ben
Lahmar (2017): **A survey on provenance: What for? What form? What
from?** The VLDB Journal 26:881--906.
[[https://doi.org/10.1007/s00778-017-0486-1]{.underline}](https://doi.org/10.1007/s00778-017-0486-1)

\[Holub 2021\] Petr Holub, Rudolf Wittner, Cecilia Mascia, Francesca
Frexia, Heimo Müller, Markus Plass, Clare Allocca, Fay Betsou, Tony
Burdett, Ibon Cancio, Adriane Chapman, Martin Chapman, Melanie Courtot,
Vasa Curcin, Johann Eder, Mark Elliot, Katrina Exter, Elliot
Fairweather, Carole Goble, Martin Golebiewski, Bron Kisler, Andreas
Kremer, Sheng Lin-Gibson, Anna Marsano, Marco Mattavelli, Josh Moore,
Hiroki Nakae, Isabelle Perseil, Ayat Salman, James Sluka, Stian
Soiland-Reyes, Caterina Strambio-De-Castillia, Michael Sussman, Jason R.
Swedlow, Kurt Zatloukal, Jörg Geiger (2021):\
**Towards a Common Standard for Data and Specimen Provenance in Life
Sciences**.\
*Zenodo* (Working Paper)*\
*[[https://doi.org/10.5281/zenodo.5093125]{.underline}](https://doi.org/10.5281/zenodo.5093125)

\[Ison 2021\] Jon Ison, Hans Ienasescu, Emil Rydza, Piotr Chmura,
Kristoffer Rapacki, Alban Gaignard, Veit Schwämmle, Jacques van Helden,
Matúš Kalaš, Hervé Ménager (2021):\
**biotoolsSchema: a formalized schema for bioinformatics software
description.\
***GigaScience* **10**(1):giaa157\
[[https://doi.org/10.1093/gigascience/giaa157]{.underline}](https://doi.org/10.1093/gigascience/giaa157)

\[Jalili 2020\] Vahid Jalili, Enis Afgan, Qiang Gu, Dave Clements,
Daniel Blankenberg, Jeremy Goecks, James Taylor, Anton Nekrutenko, **The
Galaxy platform for accessible, reproducible and collaborative
biomedical analyses: 2020 update**, Nucleic Acids Research, Volume 48,
Issue W1, 02 July 2020, Pages W395--W402,
[[https://doi.org/10.1093/nar/gkaa434]{.underline}](https://doi.org/10.1093/nar/gkaa434)

\[Khan 2019\] Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott,
Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):\
**Sharing interoperable workflow provenance: A review of best practices
and their practical application in CWLProv**.\
*GigaScience* **8**(11):giz095\
[[https://doi.org/10.1093/gigascience/giz095]{.underline}](https://doi.org/10.1093/gigascience/giz095)

\[Lebo 2013\] Timothy Lebo, Satya Sahoo, Deborah McGuinness, Khalid
Belhajjame, James Cheney, David Corsar, Daniel Garijo, Stian
Soiland-Reyes, Stephan Zednik, Jun Zhao (2013):\
**PROV-O: The PROV Ontology**.\
*W3C Recommendation* 30 April 2013.\
[[https://www.w3.org/TR/2013/REC-prov-o-20130430/]{.underline}](https://www.w3.org/TR/2013/REC-prov-o-20130430/)

\[Leo 2023a\] Leo, Simone, & Soiland-Reyes, Stian (2023):\
**Runcrate**.\
Zenodo.\
[[https://doi.org/10.5281/zenodo.7762627]{.underline}](https://doi.org/10.5281/zenodo.7762627)

\[Leo 2023b\] Simone Leo (2023):\
**Run of digital pathology tissue/tumor prediction workflow**.\
Zenodo.\
[[https://doi.org/10.5281/zenodo.7669622]{.underline}](https://doi.org/10.5281/zenodo.7669622)

\[Lordan 2014\] Francesc Lordan, Enric Tejedor, Jorge Ejarque, Roger
Rafanell, Javier Álvarez, Fabrizio Marozzo, Daniele Lezzi, Raül Sirvent,
Domenico Talia, Rosa M. Badia (2014):\
**ServiceSs: An interoperable programming framework for the cloud.**\
*Journal of Grid Computing*, 12(1)\
[[https://doi.org/10.1007/s10723-013-9272-5]{.underline}](https://doi.org/10.1007/s10723-013-9272-5)

\[Ludäscher 2016\] Bertram Ludäscher (2016):\
**A Brief Tour Through Provenance in Scientific Workflows and Databases\
**In: *Building Trust in Information,* Victoria L. Lemieux (eds).\
Springer Proceedings in Business and Economics (SPBE).\
[[https://doi.org/10.1007/978-3-319-40226-0\_7]{.underline}](https://doi.org/10.1007/978-3-319-40226-0_7)

\[Markovic 2019\] Milan Markovic, Daniel Garijo, Peter Edwards (2019):\
**Linking Abstract Plans of Scientific Experiments to their
Corresponding Execution Traces (short paper).**\
*Proceedings of the Third International Workshop on Capturing Scientific
Knowledge*, co-located with the 10th International Conference on
Knowledge Capture (K-CAP 2019)\
*CEUR Workshop Proceedings* **2526**\
[[http://ceur-ws.org/Vol-2526/short1.pdf]{.underline}](http://ceur-ws.org/Vol-2526/short1.pdf)

\[Mazumder 2020\] Raja Mazumder, Vahan Simonyan (eds), IEEE P2791
BioCompute Working Group (BCOWG) (2020):\
**IEEE Standard for Bioinformatics Analyses Generated by High-Throughput
Sequencing (HTS) to Facilitate Communication**.\
*IEEE Std* 2791-2020. IEEE SA Standards Board.\
[[https://doi.org/10.1109/IEEESTD.2020.9094416]{.underline}](https://doi.org/10.1109/IEEESTD.2020.9094416)

\[Mitchell 2022\] Sonia Natalie Mitchell, Andrew Lahiff, Nathan
Cummings, Jonathan Hollocombe, Bram Boskamp, Ryan Field, Dennis
Reddyhoff, Kristian Zarebski, Antony Wilson, Bruno Viola, Martin Burke,
Blair Archibald, Paul Bessell, Richard Blackwell, Lisa A. Boden, Alys
Brett, Sam Brett, Ruth Dundas, Jessica Enright, Alejandra N.
Gonzalez-Beltran, Claire Harris, Ian Hinder, Christopher David Hughes,
Martin Knight, Vino Mano, Ciaran McMonagle, Dominic Mellor, Sibylle
Mohr, Glenn Marion, Louise Matthews, Iain J. McKendrick, Christopher
Mark Pooley, Thibaud Porphyre, Aaron Reeves, Edward Townsend, Robert
Turner, Jeremy Walton, Richard Reeve (2022):\
**FAIR data pipeline: provenance-driven data management for traceable
scientific workflows**.\
*Philosophical Transactions of the Royal Society A: Mathematical,
Physical and Engineering Sciences* **380**(2233)\
[[https://doi.org/10.1098/rsta.2021.0300]{.underline}](https://doi.org/10.1098/rsta.2021.0300)

\[Moreau 2013\] Moreau L, Missier P, Belhajjame K et al. **PROV-DM: The
PROV Data Model**. 2013.
[[https://www.w3.org/TR/2013/REC-prov-dm-20130430/]{.underline}](https://www.w3.org/TR/2013/REC-prov-dm-20130430/).
Accessed 23 January 2023.

\[Poiata 2016\] N. Poiata, C. Satriano, J.-P. Vilotte, P. Bernard, and
K. Obara.\
**Multiband array detection and location of seismic sources recorded by
dense seismic networks**.\
*Geophysical Journal International* **205**(3)\
[[https://doi.org/10.1093/gji/ggw071]{.underline}](https://doi.org/10.1093/gji/ggw071)

\[Poiata 2023\] Natalia Poiata, Claudio Satriano, Javier Conejero
(2023):\
**BackTrackBB: Multi-band array detection and location of seismic
sources (PyCOMPSs implementation).**\
Zenodo.\
[[https://zenodo.org/record/7788030]{.underline}](https://zenodo.org/record/7788030)

\[Rehm 2021\] Heidi L. Rehm, Angela J.H. Page, Lindsay Smith, et al.
(2021):\
**GA4GH: International policies and standards for data sharing across
genomic research and healthcare**.\
*Cell Genomics* **1**(2)\
[[https://doi.org/10.1016/j.xgen.2021.100029]{.underline}](https://doi.org/10.1016/j.xgen.2021.100029)

\[Sandve 2013\] Geir Kjetil Sandve, Anton Nekrutenko, James Taylor,
Eivind Hovig (2013):\
**Ten Simple Rules for Reproducible Computational Research**.\
*PLOS Computational Biology* **9**(10):e1003285.\
[[https://doi.org/10.1371/journal.pcbi.1003285]{.underline}](https://doi.org/10.1371/journal.pcbi.1003285)

\[Sirvent 2022\] Raul Sirvent, Javier Conejero, Francesc Lordan, Jorge
Ejarque, Laura Rodriguez-Navas, Jose M. Fernandez, Salvador
Capella-Gutierrez, Rosa M. Badia (2022):\
**Automatic, Efficient, and Scalable Provenance Registration for FAIR
HPC Workflows.** In *2022 IEEE/ACM Workshop on Workflows in Support of
Large-Scale Science (WORKS)* (pp. 1-9). IEEE.\
[[https://doi.org/10.1109/works56498.2022.00006]{.underline}](https://doi.org/10.1109/works56498.2022.00006)\
[[http://hdl.handle.net/2117/384589]{.underline}](http://hdl.handle.net/2117/384589)

\[Soiland-Reyes 2014\] Stian Soiland-Reyes, Matthew Gamble and Robert
Haines (2014):\
**Research Object Bundle 1.0.**\
[[https://doi.org/10.5281/zenodo.12586]{.underline}](https://doi.org/10.5281/zenodo.12586)

\[Soiland-Reyes 2018\] Stian Soiland-Reyes, Farah Zaib Khan, Michael R
Crusoe (2018):\
**common-workflow-language/cwlprov: CWLProv 0.6.0**.\
Zenodo.\
[[https://doi.org/10.5281/zenodo.1471585]{.underline}](https://doi.org/10.5281/zenodo.1471585)

\[Soiland-Reyes 2022a\] Stian Soiland-Reyes, Peter Sefton, Mercè Crosas,
Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo,
Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc
Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble
(2022):\
**Packaging research artefacts with RO-Crate**.\
*Data Science* **5**(2)\
[[https://doi.org/10.3233/DS-210053]{.underline}](https://doi.org/10.3233/DS-210053)

\[Soiland-Reyes 2022b\] Stian Soiland-Reyes, Genís Bayarri, Pau Andrio,
Robin Long, Douglas Lowe, Ania Niewielska, Adam Hospital, Paul Groth
(2022):\
**Making Canonical Workflow Building Blocks interoperable across
workflow languages**.\
*Data Intelligence* **4**(2)\
[[https://doi.org/10.1162/dint\_a\_00135]{.underline}](https://doi.org/10.1162/dint_a_00135)

\[Soiland-Reyes 2022c\] Stian Soiland-Reyes, Peter Sefton, Leyla Jael
Castro, Frederik Coppens, Daniel Garijo, Simone Leo, Marc Portier, Paul
Groth (2022):\
**Creating lightweight FAIR Digital Objects with RO-Crate.**\
Research Ideas and Outcomes **8**:e93937.\
[[https://doi.org/10.3897/rio.8.e93937]{.underline}](https://doi.org/10.3897/rio.8.e93937)

\[Suetake 2022a\] Hirotaka Suetake, Tomoya Tanjo, Manabu Ishii, Bruno P.
Kinoshita, Takeshi Fujino, Tsuyoshi Hachiya, Yuichi Kodama, Takatomo
Fujisawa, Osamu Ogasawara, Atsushi Shimizu, Masanori Arita, Tsukasa
Fukusato, Takeo Igarashi, Tazro Ohta (2022):\
**Sapporo: A workflow execution service that encourages the reuse of
workflows in various languages in bioinformatics** \[version 1; peer
review: awaiting peer review\].\
*F1000Research* **11**:889\
[[https://doi.org/10.12688/f1000research.122924.1]{.underline}](https://doi.org/10.12688/f1000research.122924.1)

\[Suetake 2022b\] Hirotaka Suetake, Tsukasa Fukusato, Takeo Igarashi,
Tazro Ohta (2022):\
**A workflow reproducibility scale for automatic validation of
biological interpretation results**.\
*bioRxiv* 2022.10.11.511695\
[[https://doi.org/10.1101/2022.10.11.511695]{.underline}](https://doi.org/10.1101/2022.10.11.511695)

\[Villanueva-Rosales 2016\] Natalia Villanueva-Rosales, Luis Garnica
Chavira, Smriti Rajkarnikar Tamrakar, Deana Pennington, Raul Alejandro
Vargas-Acosta, Frank Ward , Alex S. Mayer (2016):\
**Capturing Scientific Knowledge for Water Resources Sustainability in
the Rio Grande Area**.\
In: Proceedings of Workshops and Tutorials of the 9th International
Conference on Knowledge Capture (K-CAP2017),\
*CEUR Workshop Proceedings* **2065\
**[[http://ceur-ws.org/Vol-2065/paper02.pdf]{.underline}](http://ceur-ws.org/Vol-2065/paper02.pdf)

\[Wilkinson 2016\] Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan
Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas
Blomberg, Jan-Willem Boiten, Luiz Bonino da Silva Santos, Philip E.
Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas,
Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard
Finkers, Alejandra Gonzalez-Beltran, Alasdair J.G. Gray, Paul Groth,
Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A.C 't Hoen, Rob
Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E.
Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe
Rocca-Serra, Marco Roos, Rene van Schaik, Susanna-Assunta Sansone, Erik
Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz,
Mark Thompson, Johan van der Lei, Erik van Mulligen, Jan Velterop, Andra
Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, Barend
Mons (2016):\
**The FAIR Guiding Principles for scientific data management and
stewardship.**\
*Scientific Data* **3**, 160018.\
[[https://doi.org/10.1038/sdata.2016.18]{.underline}](https://doi.org/10.1038/sdata.2016.18)

\[Wittner 2022\] Rudolf Wittner, Cecilia Mascia, Matej Gallo, Francesca
Frexia, Heimo Müller, Markus Plass, Jörg Geiger & Petr Holub (2022):\
**Lightweight Distributed Provenance Model for Complex Real--world
Environments.\
***Scientific Data* **9:**503 (2022).\
[[https://doi.org/10.1038/s41597-022-01537-6]{.underline}](https://doi.org/10.1038/s41597-022-01537-6)

\[Wittner 2023\] Rudolf Wittner, Matej Rudolf, Simone Leo, Stian
Soiland-Reyes (2023).\
**Packing provenance using CPM RO-Crate profile** (Version 1.1) \[Data
set\].\
*Zenodo*.
[[https://doi.org/10.5281/zenodo.8095888]{.underline}](https://doi.org/10.5281/zenodo.8095888)

\[Workflow Run RO-Crate working group 2023a\] Workflow Run RO-Crate
working group (2023):\
**Process Run Crate specification.**\
*Zenodo*.\
[[https://doi.org/10.5281/zenodo.7629720]{.underline}](https://doi.org/10.5281/zenodo.7629720)

\[Workflow Run RO-Crate working group 2023b\] Workflow Run RO-Crate
working group (2023):\
**Workflow Run Crate specification.**\
*Zenodo*.\
[[https://doi.org/10.5281/zenodo.7629813]{.underline}](https://doi.org/10.5281/zenodo.7629813)

\[Workflow Run RO-Crate working group 2023c\] Workflow Run RO-Crate
working group (2023):\
**Provenance Run Crate specification.**\
*Zenodo*.\
[[https://doi.org/10.5281/zenodo.7629863]{.underline}](https://doi.org/10.5281/zenodo.7629863)


Galaxy Community. The Galaxy platform for accessible, reproducible
and collaborative biomedical analyses: 2022 update. Nucleic Acids Res.
2022;50: W345--51.
doi:[10.1093/nar/gkac247](http://dx.doi.org/10.1093/nar/gkac247)

Köster J, Rahmann S. Snakemake\--a scalable bioinformatics workflow
engine. Bioinformatics. 2012;28: 2520--2522.
doi:[10.1093/bioinformatics/bts480](http://dx.doi.org/10.1093/bioinformatics/bts480)

Kotliar M, Kartashov AV, Barski A. CWL-Airflow: a lightweight
pipeline manager supporting Common Workflow Language. Gigascience.
2019;8: giz084.
doi:[10.1093/gigascience/giz084](http://dx.doi.org/10.1093/gigascience/giz084)

\[Manubens-Gil 2016\] D. Manubens-Gil, J. Vegas-Regidor, C. Prodhomme,
O. Mula-Valls and F. J. Doblas-Reyes (2016).\
**Seamless management of ensemble climate prediction experiments on HPC
platforms**.\
[[https://doi.org/10.1109/HPCSim.2016.7568429]{.underline}](https://doi.org/10.1109/HPCSim.2016.7568429)

\[Bahra 2011\] Bahra, Avi (2011).\
**Managing work flows with ecFlow.**\
[[https://doi.org/10.21957/nr843dob]{.underline}](https://doi.org/10.21957/nr843dob)

\[Oliver 2023\] Oliver, Hilary and Shin, Matthew and Matthews, David and
Sanders, Oliver and Bartholomew, Sadie and Clark, Andrew and
Fitzpatrick, Ben and van Haren, Ronald and Hut, Rolf and Drost, Niels
(2023).\
**Cylc: A Workflow Engine for Cycling Systems.**\
[[https://doi.org/10.1109/MCSE.2019.2906593]{.underline}](https://doi.org/10.1109/MCSE.2019.2906593)

\[Kinoshita 2023\] Bruno de Paula Kinoshita, Sebastian Müller (2023):\
**auto-mhm-test-domains: Autosubmit mHM workflow with mHM test domains
data.**\
Zenodo.\
[[https://doi.org/10.5281/zenodo.8144555]{.underline}](https://doi.org/10.5281/zenodo.8144555)

\[Samaniego 2010\] Luis Samaniego, Rohini Kumar, Sabine Attinger
(2010).\
**Multiscale parameter regionalization of a grid-based hydrologic model
at the mesoscale.**\
[[https://doi.org/10.1029/2008WR007327]{.underline}](https://doi.org/10.1029/2008WR007327)

\[Kumar 2013\] Rohini Kumar, Luis Samaniego, Sabine Attinger (2013).\
**Implications of distributed hydrologic model parameterization on water
fluxes at multiple scales and locations.\
**[[https://doi.org/10.1029/2012WR012195]{.underline}](https://doi.org/10.1029/2012WR012195)

