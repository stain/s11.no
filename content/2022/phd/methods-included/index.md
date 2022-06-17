---
title: "Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language"
bib: references.bib
categories:
    - PhD
keywords:
    - workflows
    - computational data analysis
    - CWL
    - scientific workflows
    - standards
lang: en-GB
date-meta: '2022-05-20'
author-meta:
    - Michael R. Crusoe
    - Sanne Abeln
    - Alexandru Iosup
    - Peter Amstutz
    - John Chilton
    - Nebojša Tijanić
    - Hervé Ménager
    - Stian Soiland-Reyes
    - Bogdan Gavrilović
    - Carole Goble
    - The CWL Community
summary: >
    Journal article published in _Communications of the ACM_
description: > 
    Computational Workflows are widely used in data analysis, enabling innovation and decision-making. In many domains (bioinformatics, image analysis, radio astronomy) the analysis components are numerous and written in multiple different computer languages by third parties. However, many competing workflow systems exist, severely limiting portability of such workflows, thereby hindering the transfer of workflows between different systems, between different projects and different settings, leading to vendor lock-ins and limiting their generic re-usability. 
    
    Here we present the Common Workflow Language (CWL) project which produces free and open standards for describing command-line tool based workflows. The CWL standards provide a common but reduced set of abstractions that are both used in practice and implemented in many popular workflow systems. The CWL language is declarative, which allows expressing computational workflows constructed from diverse software tools, executed each through their command-line interface. Being explicit about the runtime environment and any use of software containers enables portability and reuse. 
    
    Workflows written according to the CWL standards are a reusable description of that analysis that are runnable on a diverse set of computing environments. These descriptions contain enough information for advanced optimization without additional input from workflow authors. The CWL standards support polylingual workflows, enabling portability and reuse of such workflows, easing for example scholarly publication, fulfilling regulatory requirements, collaboration in/between academic research and industry, while reducing implementation costs. CWL has been taken up by a wide variety of domains, and industries and support has been implemented in many major workflow systems.
---

<div class="citation">

<h2>Cite as</h2>

Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian Soiland-Reyes, Bogdan Gavrilović, Carole Goble, The CWL Community (2022):  
**Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language**.  
_Communications of the ACM_ **65**(6)  
<https://doi.org/10.1145/3486897>

<h3>Copyright and license</h3>

Ⓒ Copyright 2022 ACM, Inc. and the authors.  
This work is licensed under a [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

The text below has been adapted from [ACM's HTML article](https://cacm.acm.org/magazines/2022/6/261172-methods-included/fulltext) and [LaTeX source](https://github.com/mr-c/cwl_methods_included) with these modifications by Stian Soiland-Reyes: 
- Conversion to Markdown/HTML
- Re-inserted original high resolution figures as SVG
- Re-inserted table as text
- Re-inserted author affiliations & ORCIDs
- Re-inserted hyperlinks instead of footnotes
- References modified to [house style](/2021/house-rules/citation-style/)
- Typographical improvements for Web rendering
- Inline headers changed back to sub-headings
- Sidebars reformatted
- Some long paragraphs split for improved readability
- Spelling fixes (e.g. missing — in "") 
- Reinstated missing text in [sidebar](#mono-poly-lingual)
- Re-embed from online supplementary material: acknowledgement contributions list w/CRediT, related links
- Video abstract re-encoded to avoid Vimeo dependency
</div>

# Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language

[Michael R. Crusoe](https://orcid.org/0000-0002-2961-9670)¹², 
[Sanne Abeln](https://orcid.org/0000-0002-2779-7174)¹, 
[Alexandru Iosup](https://orcid.org/0000-0001-8030-9398)¹, 
[Peter Amstutz](https://orcid.org/0000-0003-3566-7705)³, 
[John Chilton](https://orcid.org/0000-0002-6794-0756)⁴⁵, 
[Nebojša Tijanić](https://orcid.org/0000-0001-8316-4067)⁶, 
[Hervé Ménager](https://orcid.org/0000-0002-7552-1009)⁷, 
[Stian Soiland-Reyes](https://orcid.org/0000-0001-9842-9718)⁸⁹, 
[Bogdan Gavrilović](https://orcid.org/0000-0003-1550-1716)⁶
[Carole Goble](https://orcid.org/)⁸, 
[The CWL Community](http://commonwl.org/)²


<div class="affiliations">

¹ Department of Computer Science, VU Amsterdam, Amsterdam, The Netherlands  
² Common Workflow Language project, Software Freedom Conservancy, Brooklyn, NY, USA  
³ Curii Corporation, Sommerville, MA, USA  
⁴ Department of Biochemistry and Molecular Biology, Pennsylvania State University, PA, USA  
⁵ Galaxy Project  
⁶ Seven Bridges, Charlestown, MA, USA  
⁷ Hub de Bioinformatique et Biostatistique, Département Biologie Computationnelle, Institut Pasteur, Paris, France  
⁸ Department of Computer Science, The University of Manchester, Manchester, UK  
⁹ Informatics Institute, University of Amsterdam, Amsterdam, The Netherlands

</div>

## Video abstract


<figure id="fig:abstract">

 <video controls="controls" poster="video/cwl-intro.jpeg" width="100%">
   <source src="video/cwl-intro-video-vp9.webm" type='video/webm; codecs="vp9,vorbis"' />
   <source src="video/cwl-intro-video-h264.m4v" type='video/mp4"' />   
   <track src="video/subtitles/english.vtt" label="English" kind="captions" srclang="en-us" default="" />
   <track src="video/subtitles/chinese_simplified.vtt" label="中文" kind="subtitles" srclang="zh-Hans" />
   <track src="video/subtitles/japanese.vtt" label="日本語" kind="subtitles" srclang="ja" />
   <track src="video/subtitles/french.vtt" label="Français" kind="subtitles" srclang="fr-fr" />
   <track src="video/subtitles/lithuanian.vtt" label="Lietuvių kalba" kind="subtitles" srclang="lt" />
   <track src="video/subtitles/romanian.vtt" label="Român" kind="subtitles" srclang="ro" />
   <track src="video/subtitles/russian.vtt" label="Русский язык" kind="subtitles" srclang="ru" />
   <track src="video/subtitles/ukranian.vtt" label="Українська" kind="subtitles" srclang="uk" />
   <track src="video/subtitles/urdu.vtt" label="اردو" kind="subtitles" srclang="ur" /> 
   <p>
   See video abstract at 
   <a href="https://player.vimeo.com/video/712414782">Vimeo</a>, 
   <a href="https://www.youtube.com/watch?v=86eY8xs-Vo8">YouTube</a>,
   download as 
   <a href="video/cwl-intro-video-h264.m4v">mp4</a> or
   <a href="video/cwl-intro-video-vp9.webm">webm</a>.
   </p>
  </video> 

<figcaption>

[Intro to Common Workflow Language](https://vimeo.com/712414782).
Adapted from [CWLViewer](https://www.youtube.com/watch?v=_yjhVTmvxLU) by 
[Mark Robinson](https://orcid.org/0000-0002-8184-7507), The University of Manchester.

</figcaption>
</figure>




<div id="insight" class="sidebar">

**Key Insights**

* Common Workflow Language is a set of open standards for describing and sharing computational workflows, used in many science and engineering domains.
* CWL standards support critical workflow concepts such as automation, scalability, abstraction, provenance, portability, and
reusability. 
* CWL standards are developed around core principles of community and shared decision making, reuse, and zero cost for participants.
</div>

    
## Introduction {#introduction}

*Computational workflows* are widely used in data analysis, enabling innovation and decision-making for the modern society. But their growing popularity is also a cause for concern. Unless we standardize computational reuse and portability, the use of workflows may end up hampering collaboration. How can we enjoy the common benefits of computational workflows and eliminate such risks?

To answer this general question, in this work we advocate for workflow thinking as a shared method of reasoning across all domains and practitioners, introduce Common Workflow Language (CWL) as a pragmatic set of standards for describing and sharing computational workflows, and discuss the principles around which these standards have become central to a diverse community of users across multiple fields in science and engineering. This article focuses on an overview of CWL standards and the CWL project and is complemented by the technical detail available in the [CWL standards](https://w3id.org/cwl/v1.2/).

### Workflow thinking

*Workflow thinking* is a form of _"conceptualizing processes as recipes and protocols, structured as dataflow [or workflow] graphs with computational steps, and subsequently developing tools and approaches for formalizing, analyzing, and communicating these process descriptions."_ [[14](https://doi.org/10.1353/lib.2017.0018)] It introduces the workflow, an abstraction which helps decouple expertise in a specific domainfor example, specific science or engineering fieldsfrom computing expertise. Derived from workflow thinking, a *computational workflow* describes a process for computing where different parts of the process (the tasks) are interdependentfor instance, a task can start processing after its predecessors have (partially) completed and where data flows between tasks.

Currently, many competing systems exist to enable simple workflow execution (_workflow runners_) or offer comprehensive management of workflows and data (_workflow management systems_). Each has its own syntax or method for describing workflows and infrastructure requirements, which can limit computational reuse and portability. Although dataflows are becoming more complex, most workflow abstractions do not enable explicit specifications of dataflows, significantly increasing the cost to have third parties reuse and port the workflow.

We thus identify an important problem in the broad, practical adoption of workflow thinking: Although communities require _polylingual workflows_ (workflows that execute tools written in multiple, different computer languages) and _multiparty workflows_, adopting and managing different workflow systems is costly and difficult. In this work, we propose to tame this complexity through a common abstraction that covers most features used in practice and that is (or can be) implemented in many workflow systems.

### CWL overview

{{< figure src="figure1.svg" link="figure1.svg" id="fig:sample_workflow" 
  width="100%" title="Excerpt from a large microbiome bioinformatics CWL workflow"
  caption="This part of the workflow (which is interpretable/executable on its own) has the aim to match the workflow inputs of genomic sequences to provided sequence-models, which are dispatched to four sub-workflows (e.g., `find_16S_matches`); the sub-workflows not detailed in the figure. <br>The sub-workflow outputs are then collated to identify unique sequence hits, then provided as overall workflow outputs. <br>Arrows define the connection between tasks and imply their partial ordering, depicted here as layers of tasks that may execute concurrently.  <br>Workflow steps (e.g., `mask_rRNA_and_tRNA`) execute command line tools, shown here with indicators for their different programming languages (e.g., `Py` for Python, `C` for the C language). <br><em>(Diagram adapted from <https://w3id.org/cwl/view/git/7bb76f33bf40b5cd2604001cac46f967a209c47f/workflows/rna-selector.cwl>, which was originally retrieved from a corresponding CWL workflow of the EBI Metagenomics project [[27](https://doi.org/10.1093/nar/gkz1035)], itself a conversion of the _rRNASelector_ [[25](https://doi.org/10.1007/s12275-011-1213-z)] program into a well structured workflow allowing for better parallelization of execution and provenance tracking.)</em>" >}}


In the computational workflow depicted in [Figure 1](fig:sample_workflow), practitioners solved the problem by adopting the CWL standards. In this work, we posit that the CWL standards provide the common abstraction that can help overcome the main obstacles to sharing workflows between institutions and users. CWL achieves this by providing a declarative language that allows expressing computational workflows constructed from diverse software tools—each executed through their command-line interface, with the inputs and outputs of each tool clearly specified and with inputs possibly resulting from the execution of other tools. We also set out to introduce the CWL standards, with a threefold focus:

1.  The CWL standards focus on maintaining a _separation of concerns_ between the description and execution of tools and workflows, proposing a language that only includes operations commonly used across multiple communities of practice.
2.  The CWL standards support workflow automation, scalability, abstraction, provenance, portability, and reusability.
3.  To achieve these results, the CWL project takes a principled, community-first open source and open-standard approach.

The CWL standards are the product of an open and free standards-making community. 
While the CWL project began in bioinformatics, its many contributors shaped the standards to be useful in any domain that faces the problem of “many tools written in many programming languages by many parties.”

Since the ratification of the first version in 2016, the CWL standards have been used in other fields, including hydrology, [radio astronomy](https://ec.europa.eu/research/participants/documents/downloadPublic?documentIds=080166e5c434868f&appId=PPGMS), geo-spatial analysis, [[13](http://docs.opengeospatial.org/per/20-042.html),[23](http://docs.opengeospatial.org/per/20-045.html),[32](https://docs.ogc.org/per/20-073.html)] and high-energy physics, [[4](https://cds.cern.ch/record/2315331/)] in addition to fast-growing bioinformatics fields such as metagenomics [[27](https://doi.org/10.1093/nar/gkz1035)] and cancer research [[24](https://doi.org/10.1158/0008-5472.can-17-0387)]. 
The CWL standards are featured in the IEEE 2791-2020 standard, sponsored and adopted by the U.S. FDA, [[16](https://doi.org/10.1109/IEEESTD.2020.9094416)] and the Netherlands' National Plan for Open Science [[34](https://doi.org/10.4233/uuid:9e9fa82e-06c1-4d0d-9e20-5620259a6c65)].

A list of free and open source implementations of the CWL standards is offered in the [Table](#runners). 
Multiple, commercially supported systems that follow the CWL standards for executing workflows are also available from vendors such as Curii (Arvados), DNAnexus, IBM (IBM® Spectrum LSF), Illumina (Illumina Connected Analytics), and Seven Bridges. The flexibility of the CWL standards enabled, for example, rapid collaboration on and prototyping of a COVID-19 public database and analysis resource [[15](https://sched.co/coLw)].

The separation of concerns proposed by the CWL standards enables diverse projects and can also benefit engineering and large industrial projects.  Likewise, users of Docker or other software-container technologies that distribute analysis tools can leverage just the CWL Command Line Tool standard to access a structured, work-flow-independent description of how to run their tool(s) in the container, what data must be provided to the container, expected results, and where to find them.


#### Selected F/OSS workflow runners and platforms that implement the CWL standards {#runners}

| Implementation[^snapshot]                                            | Platform support                          |
|:-----|:---------------------------------------------------------------------|
| [cwltool](https://pypi.org/project/cwltool)               | Linux, macOS, Windows (via WSL 2) local execution only |
| [Arvados](https://arvados.org)                            | In the cloud on AWS, Azure and GCP, on premise & hybrid clusters using Slurm or LSF  |
| [Toil](https://pypi.org/project/toil-cwl-runner) [[35](https://doi.org/10.1038/nbt.3772)]     | AWS, Azure, GCP, Grid Engine, HTCondor, LSF, Mesos, OpenStack, Slurm, PBS/Torque also local execution on Linux, macOS, MS Windows (via WSL 2) |
| [CWL-Airflow](https://pypi.org/project/cwl-airflow) [[21](https://doi.org/10.1093/gigascience/giz084)]  | Local execution on Linux, OS X or via dedicated Airflow enabled cluster. |
| [StreamFlow](https://streamflow.di.unito.it/) [[6](https://doi.org/10.1109/TETC.2020.3019202)]        | Kubernetes, HPC with Singularity (PBS, Slurm), Occam, multi-node SSH, local-only (Docker, Singularity) |
| [REANA](https://docs.reana.io/)                           | Kubernetes |

[^snapshot]: Snapshot of <https://www.commonwl.org/implementations/>


## Background on Workflows and Standards for Workflows {#background}

Workflows, and standards-based descriptions thereof, hold the potential to solve key problems in many domains of science and engineering.


<div id="mono-poly-lingual" class="sidebar">

### Monolingual and Polylingual Workflow Systems

Techniques for workflows can be implemented in many ways -- that is, with varying degrees of formalism -- which tends to correlate with execution flexibility and features. Whereas the most *informal techniques* typically require that all processing components are written in or are at least callable from the same programming language, *formal workflow techniques* tend to allow components to be developed in multiple programming languages.

Among the informal techniques, the *do-it-yourself approach* uses built-in capabilities from a particular programming language. For example, Python provides a `threading` library, and the Java-based Apache Hadoop [[33](#https://doi.org/10.1186/1471-2105-11-S12-S1)] provides MapReduce capabilities. To gain flexibility when working with a particular programming  language, general third-party libraries, such as _ipyparallel_[^ipyparallel] can enable remote or distributed execution without having to rewrite one's code.

[^ipyparallel]: [IPython Parallel]([ipyparallel](https://pypi.org/project/ipyparallel/)) (ipyparallel) is a Python package and collection of CLI scripts for controlling clusters of IPython processes,
built on the Jupyter protocol.

A more explicit workflow structure can be achieved by using a *workflow library* focusing on a specific programming language. For example, in Parsl [[2](https://doi.org/10.1145/3307681.3325400)], the workflow constructs (“this is a unit of processing” or “here are the dependencies between the units”) are made explicit and added by the developer to a Python script, to upgrade it to a scalable workflow. (While we list Parsl as an example of a **monolingual workflow** system, it also contains explicit support for executing external command-line tools.)

Two approaches—use of per-language *add-in libraries* or the use of the *Portable Operating System Interface command-line interface* (POSIX CLI) [[30](https://pubs.opengroup.org/onlinepubs/9699919799.2008edition/)]—can accommodate **polylingual workflows**, where components are written in more than one programming language or where components come from third parties and the user does not want to or cannot modify them. Using per-language add-in libraries entails either explicit
function calls (for example, using Python *ctypes* to call a C library[^ctypes]) or the addition of annotations to the user's functions; this requires mapping/restricting to a common, cross-language data model.

[^ctypes]: [ctypes](https://docs.python.org/3/library/ctypes.html) is a foreign function library for Python.

Essentially all programming languages support the creation of **POSIX CLIs**, which are familiar to many Linux and macOS users as scripts or binaries that can be invoked on the shell with a set of arguments, reading and writing files, and executed in a separate process. 

Choosing the POSIX command-line interface as the coordination point means the connection between components is performed by an array of string *arguments* representing program options (including paths to data files) along with string-based *environment variables* (key-value pairs).

Using the command line as a coordination interface has the advantage of not needing additional implementation in every programming language but is challenged by process start-up time and a very simple data model. (As a polylingual workflow standard, CWL uses the POSIX CLI data model.)
</div>

### Why workflows? {#why-workflows}

In many domains, workflows include diverse analysis components, written in multiple, different computer languages by both end users and third parties. Such polylingual and multi-party workflows are already common or dominant in data-intensive fields, such as bioinformatics, image analysis, and radio astronomy. We envision they could bring important benefits to many other domains.

To thread data through analysis tools, domain experts such as bioinformaticians use specialized command-line interfaces [[12](https://doi.org/10.1093/gigascience/giz109),[31](https://doi.org/10.1186/2047-217X-2-15)], while experts in other domains use proprietary, customized frameworks [[2](https://doi.org/10.1145/3307681.3325400),[5](https://doi.org/10.1145/1656274.1656280)]. Workflow engines also help with efficiently managing the resources used to run scientific workloads [[7](https://doi.org/10.1007/978-1-84628-757-2_22),[10](https://doi.org/10.1016/j.future.2014.10.008)].

The workflow approach helps compose an entire application of these command-line analysis tools: Developers build graphical or textual descriptions of how to run these command-line tools, and scientists and engineers connect their inputs and outputs so that the data flows through. An example of a complex workflow problem is metagenomic analysis, for which [Figure 1](#fig:sample_workflow) illustrates a subset (a *sub-workflow*).

In practice, many research and engineering groups use workflows of the kind described in Figure 1.  However, as highlighted in a “Technology Toolbox” article recently published in *Nature,* [[29](https://doi.org/10.1038/d41586-019-02619-z)] these groups typically lack the ability to share and collaborate across institutions and infrastructures without costly manual translation of their workflows.

Using workflow techniques, especially with digital analysis processes, has become quite popular and does not appear to be slowing down. One workflow-management system, Galaxy Publication Library, recently celebrated its [10,000th citation](https://galaxyproject.org/blog/2020-08-10k-pubs/), and more than 309 computational data-analysis workflow systems are [known to exist]((https://s.apache.org/existing-workflow-systems)).

A process, digital or otherwise, may grow to such complexity that its authors and users have difficulties understanding its structure, scaling and managing it, and keeping track of what happened in the past. Process dependencies may be undocumented, obfuscated, or otherwise effectively invisible. Outsiders or newcomers may find even an extensively documented process difficult to understand if it lacks a common framework or vocabulary. 

The need to run the process more frequently or with larger inputs is unlikely to be achieved by the initial entity—that is, either a script or a human—running the process. What seemed once a reasonable manual step—run this command here, paste the result there, and then call this person for permission—will become a bottleneck under the pressure of porting and reusing. Informal logs (if any) will quickly become unsuitable for helping an organization understand *what* happened, *when*, by *whom*, and to *which* data.  

Workflow techniques aim to solve these problems by providing the abstraction, scaling, automation, and provenance (ASAP) features [[8](https://doi.org/10.1007/s13222-012-0100-z)]. Workflow constructs enable a clear abstraction about the *components*, the *relationships* between them, and the *inputs* and *outputs* of the components turning them into well-labeled tools with documented expectations. This abstraction enables:

- **Scaling:** Execution can be parallelized and distributed.
- **Automation:** The abstraction can be used by a workflow engine to track, plan, and manage task execution.
- **Provenance tracking:** Descriptions of tasks, executors, inputs, and outputs—with timestamps, identifiers (unique names), and other logs—can be stored in relation to each other to later answer structured queries.

### Why Workflow Standards? {#why-standards}

Although workflows are very popular, prior to the CWL standards, all workflow systems were incompatible with each other. This means that users who do not use the CWL standards are required to express their computational workflows in a different way each time they use another workflow system, leading to local success but global _un_portability.

The success of workflows is now their biggest drawback. Users are locked into a particular vendor, project, and often a specific hardware setup, hampering sharing and reuse. Even non-academics suffer from this situation, as the lack of standards, or their adoption, hinders effective collaboration on computational methods within and between companies. Likewise, this _unportability_ affects public/private partnerships and the potential for technology transfer from public researchers.  

A second significant problem is that incomplete method descriptions are common when computational analysis is reported in academic research [[17](https://doi.org/10.1145/3186266)]. Reproduction, reuse, and replication [[11](https://doi.org/10.1145/2723872.2723875)] of these digital methods requires a complete description of which computer applications were used, how they were used, and how they were connected to each other. For precision and interoperability, this description should also be in an appropriate, standardized, machine-readable format.

A standard for sharing and reusing workflows can provide a solution to describing portable, reusable workflows while also being workflow-engine and vendor neutral.

Sharing workflow descriptions based on standards also addresses the second problem: The availability of the workflow description provides needed information when sharing, and the quality of the description provided by a structured, standards-based approach is much higher than the current approach of casual, unstructured, and almost always incomplete descriptions in scientific reports. Moreover, the operational parts of the description can be automated by the workflow-management system rather than by domain experts.

While (data) standards are commonly adopted and have become expected for funded projects in knowledge representation fields, the same cannot yet be said about workflows and workflow engines.

## Features of the Common Workflow Language Standards {#features}

The Common Workflow Language standards aim to cover the common needs of users and the commonly implemented features of workflow runners or platforms. The remainder of this section presents an overview of CWL features, how they translate to executing workflows in CWL format, and where the CWL standards are not helpful.

The CWL standards support polylingual and multi-party workflows, for which they enable computational reuse and portability. To do so, each release of the [CWL standards](https://www.commonwl.org/specification/) has two[^schemasalad] main components: (1) a standard for describing command-line tools and (2) a standard for describing workflows that compose such tool descriptions. 

The goal of the *[CWL Command Line Tool Description Standard](https://w3id.org/cwl/v1.2/CommandLineTool.html)* is to describe how a particular command-line tool works: What are the _inputs_ and _parameters_ and their types? How do you add the correct flags and switches to the command-line invocation? Where do you find the _output_ files?

[^schemasalad]: The third component, [Schema Salad](https://www.commonwl.org/v1.2/SchemaSalad.html), is only of interest to those who want to parse the syntax of the schema language that is used to define the syntax of CWL itself.

{{< figure src="figure2.svg" link="figure2.svg" id="fig:syntax" 
  width="100%" title="Example of CWL syntax and progressive enhancement"
  caption="(a) and (b) describe the same tool, but (b) is enhanced with additional features: human-readable documentation; file format identifiers for better validation of workflow connections; recommended software container image for more reproducible results and easier installation; and dynamically specified resource requirements to optimize task scheduling and resource usage without manual intervention. Resource requirements are expressed as hints. (c) shows an example of CWL Workflow syntax, where the underlying tool descriptions (`grep.cwl` and `wc.cwl`) are in external files for ease of reuse." >}}

The CWL standards define an *explicit language*, both in syntax and in its data and execution model. 
Its textual syntax, derived from YAML[^yaml] does not restrict the amount of detail. For example, [Figure 2a](#fig:syntax) depicts a simple example with sparse detail, and Figure 2b depicts the same example but with the execution augmented with more details. 

Each input to a tool has a name and a type—for instance, `File` (see Figure 2b, Item 1).
Tool-description authors are encouraged to include documentation and labels for all components, as shown in Figure 2b, to enable the automatic generation of helpful visual depictions and even graphical user interfaces (GUIs) for any given CWL description. Metadata about the tool-description authors encourages attribution of their efforts. 

As shown in Figure 2b, Item 3, these tool descriptions can contain well-defined `hints` or mandatory `requirements`, such as which software container to use or the amount of required compute resources: memory, number of CPU cores, amount of disk space, and/or the maximum time or deadline to complete the step or entire workflow.

[^yaml]: JSON is an acceptable subset of YAML, and common when converting from another format to CWL syntax.


### CWL execution model is explicit {#explicit}

Each tool's runtime environment is explicit, and any required elements must be specified by the CWL tool-description author (in contrast to hints, which are optional)[^runtime]. Each tool invocation uses a separate working directory, populated according to the CWL tool descriptionfor example, with the input files explicitly specified by the workflow author. Some applications expect particular filenames, directory layouts, and environment variables, and there are additional constructs in the CWL Command Line Tool standard to satisfy their needs.

[^runtime]: For details on how the CWL Command Line Tool standard specifies that tool executors should set up and control the runtime environment, visit <https://w3id.org/cwl/v1.2/CommandLineTool.html#Runtime_environment> which also specifies which directories tools are allowed to write to.


### Explicit runtime model enables portability {#portability}

CWL is explicit about data locations. As [Figure 3](#fig3) indicates, this enables the execution of CWL workflows in diverse environments as provided by various implementations of the CWL standards: the local environment of the author-scientist (for instance, a single desktop computer, laptop, or workstation), a remote batch production environment (for example, a cluster, an entire data center, or even a global multi-data center infrastructure), and an on-demand cloud environment.

{{< figure src="figure3.svg" link="figure3.svg" id="fig:portability" 
  width="100%" title="Example of CWL portability"
  caption="The same workflow description runs on the scientist's own laptop or single machine, on any batch-production environment, and on any common public or private cloud. The CWL standards enable execution portability by being explicit about data locations and execution models." >}}

The CWL standards explicitly support the use of *software container* technologies, such as Docker and Singularity, to enable the portability of the underlying analysis tools. [Figure 2b](#fig:syntax), Item 2 illustrates the process of pulling a Docker container image from the [Quay.io registry](https://quay.io/repository/biocontainers/spoa?tab=tags); then, the workflow engine automates the mounting of files and folders within the container. The container included in the figure has been developed by a trusted author and is commonly used in the bioinformatics field, with the expectation that its results are reproducible. 
Indeed, the use of containers can be seen as a confirmation that a tool's execution is _reproducible_ when using only its explicitly declared runtime environment. 

Similarly, when *distributed execution* is desired, no changes to the CWL tool description are needed. File or directory inputs are already explicitly defined in the CWL description, so the (distributed) workflow runner can handle job placement and data routing between compute nodes without additional configuration.  

Via these two features—special handling of data paths and the optional but recommended use of software containers—the CWL standards enable portability (execution  “without change”). While portability can be affected by various factors not controllable by software container technology—for instance, variation in the underlying operating-system kernel or in processor results—in practice, the exact same software container and data inputs lead to portability without further adjustment from the user.

To support features that are _not_ in the CWL standards, the standards define *extension points* that permit name-spaced, vendor-specific features in explicitly defined ways. If these extensions do not fundamentally change how the tool should operate, then they are added to the hints list, and other CWL-compatible engines can ignore them.  However, if the extension is required to properly run the tool being described—for instance, due to the need for some specialized hardware—then the extension is listed under `requirements`, and CWL-compatible engines can recognize and explicitly declare their inability to execute that CWL description.

### CWL Workflow Description Standard {#workflow-standard}

The [CWL Workflow Description Standard](https://w3id.org/cwl/v1.2/Workflow.html) builds upon the CWL Command Line Tool Standard. It has the same YAML- or JSON-style syntax, with explicit workflow-level inputs, outputs, and documentation ([Figure 2c](#fig:syntax)).  Workflow descriptions consist of a list of steps, comprising CWL Command Line Tools or CWL sub-workflows, each re-exposing their tool's required inputs. Inputs for each step are connected by referencing the name of either the common *workflow inputs* or of outputs from other steps. The *workflow outputs* expose selected outputs from workflow steps, making explicit which intermediate-step outputs will be returned from the workflow. All connections include identifiers, which CWL document authors are encouraged to name meaningfully—for example, `reference_genome` instead of `input7`.

CWL workflows form explicit dataflows, as required for a particular computational analysis. The connectivity between steps defines the partial execution order. Parallel execution of steps is permitted and encouraged whenever multiple steps have all their inputs satisfied. For example, in [Figure 1](#fig:sample_workflow), `find_16S_matches` and `find_S5_matches` are at the same data-dependency level and can execute concurrently or sequentially in any order. Additionally, a [scatter](https://www.commonwl.org/user_guide/23-scatter-workflow/) construct allows the repeated execution of a CWL step (perhaps overlapping in time, depending on the available resources), where most of the inputs are the same except for one or more inputs that vary. This is done without having to modify the underlying tool description. 

Starting with CWL version 1.2, workflows can also [conditionally skip](https://www.commonwl.org/user_guide/24_conditional-workflow/) execution of a step (tool or workflow), based upon a specified intermediate input or custom Boolean evaluation.  Combining these features allows for a flexible *branch* mechanism, which allows workflow engines to calculate data dependencies before the workflow starts and thus retains the predictability of the dataflow paradigm.

In contrast to hard-coded approaches that rely on implicit file paths specific to each workflow, CWL workflows are more *flexible*, *reusable*, and *portable*, which enables scalability. The use of explicit runtime environments in the CWL standards, combined with explicit inputs/outputs to form the dataflow, enables step reordering and explicit handling of iterations. The same features enable scalable remote execution and, more generally, flexible use of runtime environments. Moreover, individual tool definitions from multiple workflows can be reused in any new workflow.

CWL workflow descriptions are also *future-proof*. Forward compatibility of CWL documents is guaranteed, as each CWL document declares which version of the standards it was written for, and minor versions do not alter the required features of the major version. A [standalone upgrader](https://pypi.org/project/cwl-upgrader/) can automatically upgrade CWL documents from one version to the next, and many CWL-aware platforms will internally update user-submitted documents at runtime.

### Execution of workflows in CWL format {#execution}

CWL is a set of standards, not a particular software product to install, purchase, or rent. The CWL standards need to be implemented to be useful; a list of some implementations of the CWL standards is in the [Table](#runners).  Workflow/tool runners that claim compliance with the CWL standards are allowed significant flexibility in how and where they execute a user's CWL documents as long as they fulfill the requirements written in those documents. For example, they are allowed (and encouraged) to distribute execution of a workflow across all available computers that can fulfill user-specified resource requirements. Aspects of execution not defined by the CWL standards include Web APIs for workflow execution and real-time monitoring.

For example, details about when a step should be considered ready for execution are available in [Section 4 of the CWL Workflow Description standard](https://w3id.org/cwl/v1.2/Workflow.html#Workflow), but once all the inputs are available, the exact timing is up to the workflow engine itself.

Step execution may result in a temporary or permanent failure, as [defined](https://w3id.org/cwl/v1.2/Workflow.html#Workflow_success_and_failure) in Section 4 of the CWL Workflow Description standard. The workflow engine must control any automatic failure recovery attempts—for instance, to re-execute a workflow step. Most workflow engines that implement the CWL standards feature the ability to attempt several re-executions, set by the user, before reporting permanent failure.

The CWL community has developed the following optimizations without requiring that users rewrite their workflows to benefit:

-   Automatic streaming of data inputs and outputs instead of waiting for all data to be downloaded or uploaded (where those data inputs or outputs are marked with `streamable: true`).
-   Workflow step placement based on data location [[18](https://renci.org/technical-reports/tr-19-01/)], resource needs, and/or cost of data transfer [[19](https://renci.org/technical-reports/tr-19-02/)].
-   The reuse of the results from previously computed steps, even from a different workflow, as long as the inputs are identical. This can be controlled by the user via the [`WorkReuse` directive](https://w3id.org/cwl/v1.2/Workflow.html#WorkReuse) in the CWL Workflow Standard.

#### Real-world usage at scale {#usage}

CWL users and vendors routinely report that they analyze 5,000 whole-genome sequences in a single workflow execution. One customer of a commercial vendor reported a successful workflow run containing an 8,000-wide step; the entire workflow had 25,000 container executions. By design, the CWL standards do not impose any technical limitations on the size of files processed or to the number of tasks run in parallel. The major scalability bottlenecks are hardware-related—not having enough machines with enough memory, compute power, or disk space to process ever-growing data at a greater scale. As these boundaries move in the future with technological advances, the CWL standards should be able to keep up and not be a limitation.


#### When is CWL not useful {#when-not-useful}

The CWL standards were designed for a particular style of command-line, tool-based data analysis. Therefore, the following situations are out of scope and not appropriate (or possible) to describe using CWL syntax:

-   Safe interaction with stateful (web) services.
-   Real-time communication between workflow steps.
-   Interactions with command-line tools beside 1) constructing the command line and making available file inputs (both user-provided and synthesized from other inputs just prior to execution) and 2) consuming the output of the tool once its execution is finished, in the form of files created/changed, the POSIX standard output and error streams, and the POSIX exit code of the tool.
-   Advanced control-flow techniques beyond conditional steps.
-   Runtime workflow graph manipulations: dynamically adding or removing new steps during workflow execution, beyond any predefined conditional step execution tests that are in the original workflow description.
-   Workflows that contain cycles: “Repeat this step or sub-workflow a specific number of times” or “Repeat this step or sub-workflow until a condition is met.”[^cycles]
-   Workflows that need specific steps run on a specific day or at a specific time.

[^cycles]: Supporting cycles/loops as an optional feature has been suggested for a future version of the CWL standards, but it has yet to be put forth as a formal proposal with a prototype implementation. As a work around, one can launch a CWL workflow from within a workflow system that does support cycles, as documented in the eWaterCycle case study with Cylc [[28](https://doi.org/10.1109/MCSE.2019.2906593.00000)].


## Open Source, Open Standards, Open Community {#open}

<div id="foss" class="sidebar">

### Free and Open Source implementations of the CWL standards {#implementations}

As of 2021, the CWL standards have gained much traction and are widely supported in practice. In addition to the implementations in the Table, [Galaxy](https://github.com/common-workflow-language/galaxy/pull/47) [[1](https://doi.org/10.1093/nar/gky379)] and [Pegasus](https://pegasus.isi.edu/documentation/manpages/pegasus-cwl-converter.html) [[10](https://doi.org/10.1016/j.future.2014.10.008)] also have in-development support for the CWL standards.

Wide adoption benefits from our principles: The CWL standards include conformance tests, but the CWL community does not yet test or certify implementations of the standards or specific technology stacks. Instead, the authors and service providers of workflow runners and workflow-management systems self-certify support for the CWL standards, based on a particular technology configuration they deploy and maintain. 

#### F/OSS tools and libraries for working with CWL-format documents {#tools}

CWL plug-ins exist for Atom, Vim, Emacs, Visual Studio Code, IntelliJ, gedit, and any editor that supports the [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) (LSP) standard. There are tools to generate CWL syntax from Python (via argparse/click or via functions), ACD[^ajax], CTD[^ctd] and annotations in IPython Jupyter Notebooks. Libraries to generate and/or read CWL documents exist in many languages: Python, Java, R, Go, Scala, Javascript, Typescript, and C++.
</div>

[^tools]: Summarized from <https://www.commonwl.org/tools/>.

[^ajax]: "Ajax Command Definitions" as produced by the [EMBOSS tools](http://emboss.source-forge.net/developers/acd/).

[^ctd]: XML-based [Common Tool Descriptors](https://github.com/WorkflowConversion/CTDSchema) [[9](https://doi.org/10.1186/s12859-016-0978-9)] originating in the OpenMS project.

Given the numerous and diverse set of potential users, implementers, and other stakeholders, we posit that a project like CWL requires the combined development of code, standards, and community. Indeed, these requirements were part of the foundational design principles for CWL; in the long run, these principles have fostered free and open source software (see [sidebar](#foss)) and a vibrant and active ecosystem.

### CWL principles

The CWL project is based on a set of five principles:

-   **Principle 1:** At the core of the project is the community of people who care about its goals.
-   **Principle 2:** To achieve the best possible results, there should be few, if any, barriers to participation. Specifically, to attract people with diverse experiences and perspectives, there must be no cost to participate.
-   **Principle 3:** To enable the best outcomes, project outputs should
    be used as people see fit. Thus, the standards themselves must be licensed for reuse, with no acquisition price.
-   **Principle 4:** The project must not favor any one company or group over another, but neither should it try to be all things to all people. The community decides.
-   **Principle 5:** Concepts and ideas must be tested frequently.  Tested and functional code is the beginning of evaluating a proposal, not the end.

Over time, CWL project members learned that this approach is a superset of the [OpenStand Principles](https://open-stand.org/about-us/principles/), a joint “Modern Paradigm for Standards” promoted by the IAB, IEEE, IETF, Internet Society, and W3C. The CWL project additions to the OpenStand Principles are 1) to keep participation free of cost, and 2) the explicit choice of Apache License 2.0 for all its text, conformance tests, and reference implementations.

*Necessary and sufficient.* All these principles have proven to be essential for the CWL project. For example, Principles 2 and 3 have enabled many implementations of the CWL standards, several of which reuse different parts of the reference implementation of the CWL standards (*reference runner*). Being community-first, per Principle 1, has led participants to create several projects that are outside the CWL standards; the most important contributions have made their way back into the project (Principle 4).

As part of Principle 5, contributors to the CWL project have developed a suite of conformance tests for each version of the CWL standards. These publicly available tests were critical to the CWL project's success: They helped assess the reference implementation of the CWL standards, they provided early adopters with concrete examples, and they enabled developers and users of production implementations of the CWL standards to confirm their accuracy.

### CWL ecosystem

Beyond the ratified initial and updated CWL standards released over the last six years, the CWL community has developed many *tools, software libraries, and connected specifications*, and has shared CWL descriptions for popular tools. 
For example, there are software development kits (SDKs) for both [Python](https://pypi.org/project/cwl-utils/) and [Java](https://github.com/common-workflow-lab/cwljava) that are generated automatically from the CWL schema. This allows programmers to load, modify, and save CWL documents using an object-oriented model that directly corresponds to the standards themselves. CWL SDKs for other languages are possible by extending the code generation routines[^codegen]. (See [sidebar](#tools) for practical details.)

[^codegen]: See the `codegen*.py` files in <https://pypi.org/project/schema-salad/7.1.20210316164414/>

The CWL standards offer strong support for the acute *need to reuse* (and, correspondingly, *to share*) information on workflow execution as well as on authoring and provenance.
The [*CWLProv*](https://w3id.org/cwl/prov/) prototype was created to show how existing standards [[3](https://doi.org/10.1016/j.websem.2015.01.003),[22](https://www.rfc-editor.org/info/rfc8493),[26](https://doi.org/10.1145/2452376.2452478)] can be combined to represent the provenance of a specific execution of a CWL workflow [[20](https://doi.org/10.1093/gigascience/giz095)]. 
Although, to date, CWLProv has only been implemented in the CWL reference runner, interest in further development and implementation is high.




## Conclusion

The problem of standardizing computational reuse is only increasing in prominence and impact. Addressing this problem, various domains in science, engineering, and commerce have already started migrating to workflows, but efforts focusing on the portability and even definition of workflows remain scattered. In this work, we raise awareness to this problem and propose a community-driven solution.

The CWL is a family of standards for the description of command-line tools and of the workflows made from these tools. It includes many features developed in collaboration with the community: support for software containers, resource requirements, workflow-level conditional branching, and more. Built on a foundation of five guiding principles, the CWL project delivers open standards, open source code, and an open community.


> *By design, the CWL standards do not impose any technical limitations on the size of files processed or to the number of tasks run in parallel.*

For the past six years, the CWL community has grown organically.  Organizations looking to write, use, or fund data-analysis workflows based upon command-line tools should adopt or even require the CWL standards, because they offer a common yet reduced set of capabilities that are both used in practice and implemented in many popular workflow systems. There are other ways CWL offers value: It is supported by a large-scale community, diverse fields have already adopted it, and its adoption is rapidly growing. Specifically:

1.  With a reduced set of capabilities, the CWL standards limit the complexity encountered by new users when they first start and by operators during implementation. Feedback from the community indicates these are appreciated.
2.  CWL's use of declarative syntax allows users to specify workflows even if they do not know exactly where the workflows would (later) run.
3.  The CWL project is governed in the public interest and produces freely available open standards. The CWL project itself is not a specific work-flow-management system, workflow runner, or vendor.  This allows potential users, operators, and vendors to avoid lock-in and be more flexible in the future.
4.  By offering standards, the CWL project distinguishes itself, especially for the complex interactions that appear in scientific and engineering collaborations. These interactions include defining workflows from many different tools (or steps), sharing workflows, long-term archiving, fulfilling requirements of regulators (for example, U.S. FDA), and making workflow executions auditable and reproducible. This is especially useful in cooperative environments, where groups that compete also need to collaborate, or in scientific papers where results can be reused very efficiently if the analysis is described in a CWL workflow with publicly available software containers for all steps.
5.  The CWL standards are already implemented, adopted, and used, with many production-grade implementations available as open source and with zero-cost. Thus, the different communities of users of the CWL standards already offer numerous workflow and tool descriptions.  This is akin to how the Python ecosystem of shared libraries, code, and recipes is already helpful.

This is a call for others to embrace workflow thinking and join the CWL community in creating and sharing portable and complete workflow descriptions. With the CWL standards, the methods are included and ready to (re)use.

---------------------

<div class="appendix">

## Acknowledgments {#acknowledgements}

The list of those involved in the CWL project we would like to acknowledge is extensive.  A comprehensive list is available in the
[online supplementary material](https://dl.acm.org/doi/10.1145/3486897) and is included below.

### Funding acknowledgments

[European Commission](https://ec.europa.eu/programmes/horizon2020/) grants
BioExcel-2 (SSR) [H2020-INFRAEDI-02-2018 823830](https://cordis.europa.eu/project/id/823830),
BioExcel (SSR) [H2020-EINFRA-2015-1 675728](https://cordis.europa.eu/project/id/675728),
EOSC-Life (SSR) [H2020-INFRAEOSC-2018-2 824087](https://cordis.europa.eu/project/id/824087),
EOSCPilot (MRC) [H2020-INFRADEV-2016-2 739563](https://cordis.europa.eu/project/id/739563),
IBISBA 1.0 (SSR) [H2020-INFRAIA-2017-1-two-stage 730976](https://cordis.europa.eu/project/id/730976),
ELIXIR-EXCELERATE (SSR, HM) [H2020-INFRADEV-1-2015-1 676559](https://cordis.europa.eu/project/id/676559)
ASTERICS (MRC) [INFRADEV-4-2014-2015 653477](https://cordis.europa.eu/project/id/653477). 
[ELIXIR](https://elixir-europe.org/), the research infrastructure for life-science data, 
Interoperability Platform Implementation Study (MRC). [2018-CWL](https://elixir-europe.org/about-us/commissioned-services/cwl-2018).
Various universities have also co-sponsored this project; we thank Vrije Universiteit of Amsterdam, the Netherlands, where the first three authors have their primary affiliation.

### Contributions


The CWL project is immensely grateful to the following self-identified CWL Community members and their contributions to the project: 
* [Miguel d’Arcangues Boland](https://orcid.org/0000-0002-2703-8936) (Software, Bug Reports, Maintenance), 
* Alain Domissy (Conceptualization, Answering Questions, Tools), 
* Andrey Kislyuk (Software, Bug Reports), 
* [Brandi Davis-Dusenbery](https://orcid.org/0000-0001-7811-8613) (Conceptualization, Funding acquisition, Investigation, Project Administration, Resources, Supervision, Business Development, Event Organizing, Talks), 
* [Niels Drost](https://orcid.org/0000-0001-9795-7981) (Funding Acquisition, Blogposts, Event Organizing, Tutorials, Talks), 
* [Robert Finn](https://orcid.org/0000-0001-8626-2148) (Data acquisition, Funding acquisition, Investigation, Resources, Supervision), 
* [Michael Franklin](https://orcid.org/0000-0001-9292-1533) (Software, Bug Reports, Documentation, Event Organizing, Maintenance, Tools, Answering Questions, Talks), 
* [Manabu Ishii](https://orcid.org/0000-0002-5843-4712) (Blogposts, Documentation, Examples, Event Organizing, Maintenance, Tools, Answering Questions, Translation, Tutorials, Talks), 
* [Sinisa Ivkovic](https://orcid.org/0000-0003-4115-3313) (Software, Validation, Bug Reports, Tools), 
* [Alexander Kanitz](https://orcid.org/0000-0002-3468-0652) (Software, Business Development, Tools, Talks), 
* [Sehrish Kanwal](https://orcid.org/0000-0002-5044-4692) (Conceptualization, Formal Analysis, Investigation, Software, Validation, Bug Reports, Blogposts, Content, Event Organizing, Maintenance, Answering Questions, Tools, Tutorials, Talks, User Testing), 
* [Andrey Kartashov](https://orcid.org/0000-0001-9102-5681) (Conceptualization, Software, Validation, Examples, Tools, Answering Questions), 
* [Farah Khan](https://orcid.org/0000-0002-6337-3037) (Conceptualization, Formal Analysis, Funding Acquisition, Software), 
* [Michael Kotliar](https://orcid.org/0000-0002-6486-3898) (Software, Validation, Bug Reports, Blogposts, Examples, Maintenance, Answering Questions, Reviewed Contributions, Tools, Talks, User Testing), 
* [Folker Meyer](https://orcid.org/0000-0003-1112-2284) (Tools), 
* [Rupert Nash](https://orcid.org/0000-0002-6388-7353) (Software, Bug Reports, Talks, Videos), 
* [Maya Nedeljkovich](https://orcid.org/0000-0003-3705-948X) (Software, Validation, Visualization, Writing -- review & editing, Bug Reports, Tools, Talks), 
* [Tazro Ohta](https://orcid.org/0000-0003-3777-5945) (Formal Analysis, Funding Acquisition, Resources, Validation, Bug Reports, Blogposts, Content, Documentation, Examples, Event Organizing, Answering Questions, Tools, Translation, Tutorials, Talks, User Testing), 
* [Pjotr Prins](https://orcid.org/0000-0002-8021-9162) (Blogposts, Packaging, Bug Reports), 
* [Manvendra Singh](https://orcid.org/0000-0001-9279-9910) (Software, Blogposts, Packaging, Tools, Reviewed Contributions), 
* [Andrey Tovchigrechko](https://orcid.org/0000-0002-0959-4429) (Conceptualization, Software, Bug Reports), 
* [Alan Williams](https://orcid.org/0000-0003-3156-2105) (Investigation), 
* [Denis Yuen](https://orcid.org/0000-0002-6130-1021) (Software, Bug Reports, Documentation, Tools), 
* [Alexander (Sasha) Wait Zaranek](https://orcid.org/0000-0002-0415-9655) (Conceptualization, Funding Acquisition), 
* [Sarah Wait Zaranek](https://orcid.org/0000-0003-4716-9121) (Conceptualization, Funding Acquisition, Project Administration, Resources, Software, Accessibility, Bug Reports, Business Development, Content, Examples, Event Organizing, Answering Questions, Tutorials, Talks).  

The contributions to the CWL project by the authors of this paper are: 
* [Michael R. Crusoe](https://orcid.org/0000-0002-2961-9670) (Conceptualization, Funding Acquisition, Investigation, Project Administration, Resources, Software, Supervision, Validation, Writing — original draft, Bug Reports, Business Development, Content, Documentation, Examples, Event Organizing, Maintenance, Packaging, Answering Questions, Reviewing Contributions, Tutorials, Talks), 
* [Sanne Abeln](https://orcid.org/0000-0002-2779-7174) (Writing — original draft, and review & editing, Conceptualization, Supervision, Funding acquisition), 
* [Alexandru Iosup](https://orcid.org/0000-0001-8030-9398) (Writing — original draft, and review, editing, Conceptualization, Supervision, Funding acquisition), 
* [Peter Amstutz](https://orcid.org/0000-0003-3566-7705) (Conceptualization, Formal Analysis, Funding Acquisition, Methodology, Project Administration, Resources, Software, Supervision, Validation, Visualization, Bug Reports, Business Development, Content, Documentation, Examples, Event Organizing, Maintenance, Packaging, Answering Questions, Reviewed Contributions, Security, Tools, Tutorials, Talks), 
* [Nebojša Tijanić](https://orcid.org/0000-0001-8316-4067) (Conceptualization, Software), 
* [Hervé Ménager](https://orcid.org/0000-0002-7552-1009) (Conceptualization, Funding Acquisition, Investigation, Methodology, Project Administration, Resources, Software, Supervision, Bug Reports, Business Development, Examples, Event Organizing, Maintenance, Tools, Tutorials, Talks), 
* [Stian Soiland-Reyes](https://orcid.org/0000-0001-9842-9718) (Conceptualization, Funding Acquisition, Investigation, Project Administration, Resources, Software, Supervision, Validation, User Testing, Writing – review and editing, Bug Reports, Blogposts, Business Development, Content, Documentation, Examples, Event Organizing, Packaging, Tools, Answering Questions, Reviewed Contributions, Security, Tutorials, Talks, Videos), 
* [Bogdan Gavrilovic](https://orcid.org/0000-0003-1550-1716) (Conceptualization, Software, Validation, Bug Reports, Blogposts, Maintenance, Tools, Answering Questions, Reviewed Contributions, User Testing), 
* [Carole A.  Goble](https://orcid.org/0000-0003-1219-2137) (Conceptualization, Funding Acquisition, Resources, Supervision, Audio, Business Development, Content, Examples, Event Organizing, Tools, Talks, Videos).

### Authors {#authors}

**Michael R. Crusoe** is a promovendus at VU Amsterdam, Department of
Computer Science, Netherlands.; CWL Project Lead at Software Freedom
Conservancy, Inc., USA; and Project Leader Compute Platform in ELIXIR-NL
at DTL Projects, Utrecht, Netherlands.

**Sanne Abeln** is an associate professor in Bioinformatics at VU
Amsterdam, Department of Computer Science, Netherlands.

**Alexandru Iosup** is a university research chair and full professor at
VU Amsterdam, Department of Computer Science, Netherlands.

**Peter Amstutz** is a principal software engineer at Curii Corporation,
Sommerville, MA, USA.

**John Chilton** is a computational scientist at the Nekrutenko Lab at
Pennsylvania State University Department of Biochemistry and Molecular
Biology, State College, PA, USA.

**Neboja Tijanić** was a software engineer at Seven Bridges Genomics
Inc., Charlestown, MA, USA.

**Hervé Ménager** is a research engineer at the Institut Pasteur,
Université de Paris, Bioinformatics and Biostatistics Hub, F-75015,
Paris, France.

**Stian Soiland-Reyes** is a technical architect at The University of
Manchester, Department of Computer Science, Manchester, U.K.; and a
Ph.D. candidate at the Informatics Institute, University of Amsterdam,
Netherlands.

**Bogdan Gavrilović** is a product development director at Seven Bridges
Genomics Inc., Charlestown, MA, USA.

**Carole Goble** (CBE FREng FBCS CITP) is a full professor of Computer
Science at The University of Manchester, Department of Computer Science,
Manchester, U.K.


## Supplementary information

Relevant Links:
* Common Workflow Language Standards, v1.2: <https://w3id.org/cwl/v1.2/>
* European Open Science Cloud for Research Pilot Project:
<https://ec.europa.eu/research/participants/documents/downloadPublic?documentIds=080166e5c434868f&appId=PPGMS>
* Curii: <https://www.curii.com/>
* DNAnexus: <https://www.dnanexus.com/>
* IBM Spectrum LSF: <https://github.com/IBMSpectrumComputing/cwlexec>
* Illumina Connected Analytics:
<https://www.illumina.com/products/by-type/informatics-products/connected-analytics.html
* Seven Bridges: <https://www.sevenbridges.com/>
* Galaxy: The first 10,000 pubs: <https://galaxyproject.org/blog/2020-08-10k-pubs/>
* Existing Workflow Systems: <https://s.apache.org/existing-workflow-systems>
* Interactive Parallel Computing with IPython: <https://pypi.org/project/ipyparallel/>
* ctypes—A foreign function library for Python: <https://docs.python.org/3/library/ctypes.html>
* Common Workflow Language (CWL) Command Line Tool Description, v1.2:
<https://w3id.org/cwl/v1.2/CommandLineTool.html>
* How the CWL Command Line Tool standard specifies that tool executors should setup
and control the runtime environment:
<https://w3id.org/cwl/v1.2/CommandLineTool.html#Runtime_environment>
* Common Workflow Language (CWL) Workflow Description, v1.2:
<https://w3id.org/cwl/v1.2/Workflow.html>
* Common Workflow Language (CWL) Workflow Description, v1.2, Workflow:
<https://w3id.org/cwl/v1.2/Workflow.html#Workflow>
* Workflow Success and Failure:
<https://w3id.org/cwl/v1.2/Workflow.html#Workflow_success_and_failure>
* CWL Upgrader 1.2.2: <https://pypi.org/project/cwl-upgrader/>
* CWL 4.3.10 Work Reuse: <https://w3id.org/cwl/v1.2/Workflow.html#WorkReuse>
* Open Stand: <https://open-stand.org/about-us/principles/>
* What can execute CWL descriptions? <https://www.commonwl.org/implementations/>
* Implement a subset of the CWL:
<https://github.com/common-workflow-language/galaxy/pull/47>
* 11.6. pegasus-cwl-converter:
* <https://pegasus.isi.edu/documentation/manpages/pegasus-cwl-converter.html>
* Development Tools: <https://www.commonwl.org/tools/>
* Language Server Protocol: <https://microsoft.github.io/language-server-protocol/>
* Ajax Command Definitions as produced by the EMBOSS tools:
<http://emboss.sourceforge.net/developers/acd/>
* XML-based Common Tool Descriptors originating in the OpenMS project:
<https://github.com/WorkflowConversion/CTDSchema>
* Cwl-utils 0.13: <https://pypi.org/project/cwl-utils/>
* Common Workflow Lab, CWL Java: <https://github.com/common-workflow-lab/cwljava>
Crusoe et al.
* See the *codegen*.py files:
<https://pypi.org/project/schema-salad/7.1.20210316164414/>
* <https://w3id.org/cwl/prov/>

</div>

<div class="references">

## References {#references}

[1] Enis Afgan, Dannon Baker, Bérénice Batut, Marius van den Beek, Dave Bouvier, Martin Čech, John Chilton, Dave Clements, Nate Coraor, Björn A. Grüning, Aysam Guerler, Jennifer Hillman-Jackson, Saskia Hiltemann, Vahid Jalili, Helena Rasche, Nicola Soranzo, Jeremy Goecks, James Taylor, Anton Nekrutenko, Daniel Blankenberg (2018):  
**The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2018 update**.  
*Nucleic Acids Research* **46**(W1) W537–W544  
<https://doi.org/10.1093/nar/gky379> 

[2] Yadu Babuji, Anna Woodard, Zhuozhao Li, Daniel S. Katz, Ben Clifford, Rohan Kumar, Lukasz Lacinski, Ryan Chard, Justin M. Wozniak, Ian Foster, Michael Wilde, Kyle Chard (2019):  
**Parsl: Pervasive Parallel Programming in Python**.  
_Proceedings of the 28th International Symposium on High-Performance Parallel and Distributed Computing_  
<https://doi.org/10.1145/3307681.3325400> 

[3] Khalid Belhajjame, Jun Zhao, Daniel Garijo, Matthew Gamble, Kristina Hettne, Raul Palma, Eleni Mina, Oscar Corcho, José Manuel Gómez-Pérez, Sean Bechhofer, Graham Klyne, Carole Goble (2015):  
**Using a suite of ontologies for preserving workflow-centric research objects**.  
*Journal of Web Semantics* **32**  16–42  
<https://doi.org/10.1016/j.websem.2015.01.003> 

[4] Tim Bell, Luca Canali, Eric Grancher, Massimo Lamanna, Gavin McCance,  Pere Mato Vila, Danilo Piparo, Jakub Moscicki, Alberto Pace, Ricardo Brito Da Rocha, Tibor Simko, Tim Smith, Enric
Tejedor Saavedra (2017):  
**Web-based Analysis Services Report**.  
_CERN_ report (CERN-IT-Note-2018-004)  
<http://cds.cern.ch/record/2315331/> 

[5]  Michael R. Berthold, Nicolas Cebron, Fabian Dill, Thomas R. Gabriel, Tobias Kötter, Thorsten Meinl, Peter Ohl, Kilian Thiel, Bernd Wiswedel (2009):  
**KNIME - the Konstanz information miner: Version 2.0 and beyond**.  
*ACM SIGKDD Explorations Newsletter* **11**(1)  
<https://doi.org/10.1145/1656274.1656280>

[6] Iacopo Colonnelli, Barbara Cantalupo, Ivan Merelli, Marco Aldinucci (2020):  
**StreamFlow: Cross-breeding cloud with HPC**.  
*IEEE Transactions on Emerging Topics in Computing* **9**(4)  
<https://doi.org/10.1109/TETC.2020.3019202> 

[7] Peter Couvares, Tevfik Kosar, Alain Roy, Jeff Weber, Kent Wenger (2007):  
**Workflow Management in Condor**.  
_Workflows for e-Science: Scientific Workflows for Grids_  
<https://doi.org/10.1007/978-1-84628-757-2_22> 

[8] Víctor Cuevas-Vicenttín, Saumen Dey, Sven Köhler, Sean Riddle, Bertram Ludäscher (2012):  
**Scientific Workflows and Provenance: Introduction and Research Opportunities**.  
*Datenbank-Spektrum* **12**(3)  
<https://doi.org/10.1007/s13222-012-0100-z> 

[9] Luis de la Garza, Johannes Veit, Andras Szolek, Marc Röttig, Stephan Aiche, Sandra Gesing, Knut Reinert, Oliver Kohlbacher (2016):  
**From the desktop to the grid: Scalable bioinformatics via workflow conversion**.  
*BMC Bioinformatics* **17**(1):127  
<https://doi.org/10.1186/s12859-016-0978-9>

[10] Ewa Deelman, Karan Vahi, Gideon Juve, Mats Rynge, Scott Callaghan, Philip J. Maechling, Rajiv Mayani, Weiwei Chen, Rafael Ferreira da Silva, Miron Livny, Kent Wenger (2015):  
**Pegasus, a workflow management system for science automation**.  
*Future Generation Computer Systems* **46**  
<https://doi.org/10.1016/j.future.2014.10.008> 

[11] Dror G. Feitelson (2015):  
**From Repeatability to Reproducibility and Corroboration**.  
*ACM SIGOPS Operating Systems Review* **49**  
<https://doi.org/10.1145/2723872.2723875> 

[12] Peter Georgeson, Anna Syme, Clare Sloggett, Jessica Chung, Harriet Dashnow, Michael Milton, Andrew Lonsdale, David Powell, Torsten Seemann, Bernard Pope (2019):  
**Bionitio: Demonstrating and facilitating best practices for bioinformatics command-line software**.  
*GigaScience* **8**  
<https://doi.org/10.1093/gigascience/giz109> 

[13] Pedro Gonçalves (2020):  
**OGC Earth Observations Applications Pilot: Terradue Engineering Report**.  
_Open Geospatial Consortium_, OGC Public Engineering Report OGC 20-042  
<http://docs.opengeospatial.org/per/20-042.html> 

[14] Michael R. Gryk & Bertram Ludäscher (2017):  
**Workflows and Provenance: Toward Information Science Solutions for the Natural Sciences**.  
*Library Trends* **65**(4)  
<https://doi.org/10.1353/lib.2017.0018>

[15] Andrea Guarracino, Peter Amstutz, Thomas Liener, Michael Crusoe, Adam Novak, Erik Garrison, Tazro Ohta, Bonface Munyoki, Danielle Welter, Sarah Wait Zaranek, Alexander (Sasha) Wait Zaranek, Pjotr Prins (2020):  
**COVID-19 PubSeq: Public SARS-CoV-2 Sequence Resource**.  
_Bioinformatics Open Source Conference_ (BOSC), July 2020  
<https://sched.co/coLw>

[16] **IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication**.  
_IEEE Std_ **2791-2020**  
ISBN 978-1-5044-6466-6  
<https://doi.org/10.1109/IEEESTD.2020.9094416> [[preprint](https://www.research.manchester.ac.uk/portal/en/publications/ieee-2791(936de52b-ac53-4f0e-9927-77fd7073e88d).html)]

[17] Peter Ivie & Douglas Thain (2018):  
**Reproducibility in Scientific Computing**.  
*ACM Computing Surveys* **51**:63  
<https://doi.org/10.1145/3186266>

[18] Fan Jiang, Claris Castillo, Stan Ahalt (2019):  
**A Cloud-Agnostic Framework for Geo-Distributed Data-Intensive Applications**.  
_RENCI_ report TR-19-01, The University of North Carolina at Chapel Hill  
<https://renci.org/technical-reports/tr-19-01/> 

[19] Fan Jiang, Kyle Ferriter, Claris Castillo (2019):  
**PIVOT: Cost-Aware Scheduling of Data-Intensive Applications in a Cloud-Agnostic System**.  
_RENCI_ report TR-19-02, The University of North Carolina at Chapel Hill  
<https://renci.org/technical-reports/tr-19-02/> 

[20] Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):  
**Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv**.  
*GigaScience* **8**(11):giz095  
<https://doi.org/10.1093/gigascience/giz095> 

[21] Michael Kotliar, Andrey V. Kartashov, Artem Barski (2019):  
**CWL-Airflow: A lightweight pipeline manager supporting Common Workflow Language**.  
*GigaScience* **8**(7):giz084
<https://doi.org/10.1093/gigascience/giz084> 
 
[22] J. Kunze, J. Littman, E. Madden, J. Scancella, C. Adams (2018):  
**The BagIt File Packaging Format (V1.0)**.  
_RFC Editor_, RFC 8493  
<https://doi.org/10.17487/RFC8493>

[23] Tom Landry (2020):  
**OGC Earth Observation Applications Pilot: CRIM Engineering Report**.  
_Open Geospatial Consortium_, Public Engineering Report 20-045  
<http://docs.opengeospatial.org/per/20-045.html>

[24] Jessica W. Lau, Erik Lehnert, Anurag Sethi, Raunaq Malhotra, Gaurav Kaushik, Zeynep Onder, Nick Groves-Kirkby, Aleksandar Mihajlovic, Jack DiGiovanna, Mladen Srdic, Dragan Bajcic, Jelena Radenkovic, Vladimir Mladenovic, Damir Krstanovic, Vladan Arsenijevic, Djordje Klisic, Milan Mitrovic, Igor Bogicevic, Deniz Kural, Brandi Davis-Dusenbery (2017):   
**The Cancer Genomics Cloud: Collaborative, Reproducible, and Democratized—A New Paradigm in Large-Scale Computational Research**.  
*Cancer Research* **77**(21)  
<https://doi.org/10.1158/0008-5472.can-17-0387> 

[25] Jae-Hak Lee, Hana Yi, Jongsik Chun (2011):  
**rRNASelector: A computer program for selecting ribosomal RNA encoding sequences from metagenomic and metatranscriptomic shotgun libraries**.  
_The Journal of Microbiology_ **49**(4)  
<https://doi.org/10.1007/s12275-011-1213-z>

[26] Paolo Missier, Khalid Belhajjame, James Cheney (2013):  
**The W3C PROV family of specifications for modelling provenance metadata**.  
*Proceedings of the 16th International Conference on Extending Database Technology*  
<https://doi.org/10.1145/2452376.2452478>

[27] Alex L. Mitchell, Alexandre Almeida, Martin Beracochea, Miguel Boland, Josephine Burgin, Guy Cochrane, Michael R. Crusoe, Varsha Kale, Simon C. Potter, Lorna J. Richardson, Ekaterina Sakharova, Maxim Scheremetjew, Anton Korobeynikov, Alex Shlemov, Olga Kunyavskaya, Alla Lapidus, Robert D. Finn (2020):  
**MGnify: The microbiome analysis resource in 2020**.  
*Nucleic Acids Research* **48**(D1)  
<https://doi.org/10.1093/nar/gkz1035> 

[28] Hilary Oliver, Matthew Shin, David Matthews, Oliver Sanders, Sadie Bartholomew, Andrew Clark, Ben Fitzpatrick, Ronald van Haren, Rolf Hut, Niels Drost (2019):  
**Workflow automation for cycling systems: The Cylc Workflow Engine**.  
*Computing in Science Engineering* **21**(4)  
<https://doi.org/10.1109/MCSE.2019.2906593>

[29] Jeffrey M. Perkel (2019):  
**Workflow systems turn raw data into scientific knowledge**.  
*Nature* **573**(7772)  
<https://doi.org/10.1038/d41586-019-02619-z> 

[30] The Austin Group (2008):  
**POSIX.1-2008 (IEEE Std 1003.1™-2008 and The Open Group Technical Standard Base Specifications, Issue 7)**.  
_IEEE and The Open Group_  
<https://pubs.opengroup.org/onlinepubs/9699919799.2008edition/>

[31] Torsten Seemann (2013):  
**Ten recommendations for creating usable bioinformatics command line software**.  
*GigaScience* **2**(1)  
<https://doi.org/10.1186/2047-217X-2-15>

[32] Ingo Simonis (2020):  
**OGC Earth Observation Applications Pilot: Summary Engineering Report**.  
_Open Geospatial Consortium_, Public Engineering Report OGC 20-073  
<https://docs.ogc.org/per/20-073.html>

[33] Ronald C. Taylor (2010):  
**An overview of the Hadoop/MapReduce/HBase framework and its current applications in
bioinformatics**.  
*BMC Bioinformatics* **11**(S1)  
<https://doi.org/10.1186/1471-2105-11-S12-S1> 

[34] W.J.S.M. van Wezenbeek, H.J.J. Touwen, A.M.C. Versteeg, Astrid van Wesenbeeck (2017):  
**Nationaal plan open science**.  
_Ministerie van Onderwijs, Cultuur en Wetenschap_, The Netherlands  
<https://doi.org/10.4233/uuid:9e9fa82e-06c1-4d0d-9e20-5620259a6c65>.

[35] ohn Vivian, Arjun Arkal Rao, Frank Austin
Nothaft, Christopher Ketchum, Joel Armstrong, Adam Novak, Jacob Pfeil,
Jake Narkizian, Alden D. Deran, Audrey Musselman-Brown, Hannes Schmidt,
Peter Amstutz, Brian Craft, Mary Goldman, Kate Rosenbloom, Melissa
Cline, Brian O’Connor, Megan Hanna, Chet Birger, W. James Kent, David A.
Patterson, Anthony D. Joseph, Jingchun Zhu, Sasha Zaranek, Gad Getz,
David Haussler, Benedict Paten (2017):  
**Toil enables reproducible, open source, big biomedical data analyses**.  
*Nature Biotechnology* **35**(4)  
<https://doi.org/10.1038/nbt.3772> 

</div>



<script src="https://player.vimeo.com/api/player.js"></script>
