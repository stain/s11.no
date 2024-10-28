---
title: "Scientific workflows, community roadmap, data management, AI workflows, exascale computing, interoperability"
categories:
  - Publication
keywords:
  - scientific workflows
  - community roadmap
  - data management
  - AI workflows
  - exascale computing
  - interoperability
authors:
  - name: Rafael Ferreira da Silva
    orcid: https://orcid.org/0000-0002-1720-0928
  - name: Henri Casanova
    orcid: https://orcid.org/0000-0001-6310-0365    
  - name: Kyle Chard
    orcid: https://orcid.org/0000-0002-7370-4805
  - name: Ilkay Altintas
    orcid: https://orcid.org/0000-0002-2196-0305
  - name: Rosa M Badia
    orcid: https://orcid.org/0000-0003-2941-5499
  - name: Bartosz Balis
    orcid: https://orcid.org/0000-0002-3082-4209
  - name: Tainã Coleman
    orcid: https://orcid.org/0000-0002-0982-1919
  - name:  Frederik Coppens
    orcid: https://orcid.org/0000-0001-6565-5145
  - name: Frank Di Natale
    orcid: https://orcid.org/0000-0002-3082-4209
  - name: Björn Enders
    orcid: https://orcid.org/0000-0002-6009-6281
  - name: Thomas Fahringer
    orcid: https://orcid.org/0000-0003-4293-1228
  - name: Rosa Filgueira
    orcid: https://orcid.org/0000-0002-5715-3046
  - name: Grigori Fursin
    orcid: https://orcid.org/0000-0001-7719-1624
  - name: Daniel Garijo
    orcid: https://orcid.org/0000-0003-0454-7145
  - name: Carole Goble
    orcid: https://orcid.org/0000-0003-1219-2137
  - name: Dorran Howell
    orcid: https://github.com/dorranh
  - name: Shantenu Jha
    orcid: https://orcid.org/0000-0002-5040-026X
  - name: Daniel S. Katz
    orcid: https://orcid.org/0000-0001-5934-7525
  - name: Daniel Laney
    orcid: https://people.llnl.gov/laney1
  - name: Ulf Leser
    orcid: https://orcid.org/0000-0003-2166-9582
  - name: Maciej Malawski
    orcid: https://orcid.org/0000-0001-6005-0243
  - name: Kshitij Mehta
    orcid: https://orcid.org/0000-0002-9714-9981
  - name: Loïc Pottier
    orcid: https://orcid.org/0000-0002-7681-3521
  - name: Jonathan Ozik
    orcid: https://orcid.org/0000-0002-3495-6735
  - name: J. Luc Peterson
    orcid: https://orcid.org/0000-0002-5167-5708
  - name: Lavanya Ramakrishnan
    orcid: https://orcid.org/0000-0003-1761-4132
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
  - name: Douglas Thain        
    orcid: https://orcid.org/0000-0001-5218-1956
  - name: Matthew Wolf
    orcid: https://orcid.org/0000-0002-8393-4436
summary: >
  Preprint for proceedings article for 2021 IEEE Workshop on Workflows in Support of Large-Scale Science
description: >
  The landscape of workflow systems for scientific applications is notoriously convoluted with hundreds of seemingly equivalent workflow systems, many isolated research claims, and a steep learning curve. To address some of these challenges and lay the groundwork for transforming workflows research and development, the WorkflowsRI and ExaWorks projects partnered to bring the international workflows community together. This paper reports on discussions and findings from two virtual “Workflows Community Summits” (January and April, 2021). The overarching goals of these workshops were to develop a view of the state of the art, identify crucial research challenges in the workflows community, articulate a vision for potential community efforts, and discuss technical approaches for realizing this vision. To this end, participants identified six broad themes: FAIR computational workflows; AI workflows; exascale challenges; APIs, interoperability, reuse, and standards; training and education; and building a workflows community. We summarize discussions and recommendations for each of these themes.
---

<h2>Cite as</h2>

Rafael Ferreira da Silva, Henri Casanova, Kyle Chard, Ilkay Altintas, Rosa M Badia, Bartosz Balis, Tainã Coleman, Frederik Coppens, Frank Di Natale, Bjoern Enders, Thomas Fahringer, Rosa Filgueira, Grigori Fursin, Daniel Garijo, Carole Goble, Dorran Howell, Shantenu Jha, Daniel S. Katz, Daniel Laney, Ulf Leser, Maciej Malawski, Kshitij Mehta, Loïc Pottier, Jonathan Ozik, J. Luc Peterson, Lavanya Ramakrishnan, Stian Soiland-Reyes, Douglas Thain, Matthew Wolf(2021):  
** **
[**A Community Roadmap for Scientific Workflows Research and Development**](https://arxiv.org/pdf/2110.02168).  
_2021 IEEE Workshop on Workflows in Support of Large-Scale Science ([WORKS](https://works-workshop.org/))_  
<https://doi.org/10.1109/WORKS54523.2021.00016>  
[arXiv:2110.02168](https://arxiv.org/abs/2110.02168) [cs.DC]


* **Is based on**:
<https://arxiv.org/pdf/2110.02168v2> (Author-submitted article)
* **License**: © 2021 IEEE.  Personal use of this material is permitted.  Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.
* **Modifications**: Formatting as Markdown from preprint LaTeX; references in s11 house style; table 2 changed to definition list; additional paragraph breaks for readability.


# Scientific workflows, community roadmap, data management, AI workflows, exascale computing, interoperability

_Rafael Ferreira da Silva<sup>1,2</sup>, Henri Casanova<sup>3</sup>, Kyle Chard<sup>4,5</sup>, Ilkay Altintas<sup>6</sup>, Rosa M Badia<sup>7</sup>, Bartosz Balis<sup>8</sup>, Tainã Coleman<sup>2</sup>, Frederik Coppens<sup>9,10</sup>, Frank Di Natale<sup>11</sup>, Bjoern Enders<sup>21</sup>, Thomas Fahringer<sup>12</sup>, Rosa Filgueira<sup>13</sup>, Grigori Fursin<sup>14</sup>, Daniel Garijo<sup>15</sup>, Carole Goble<sup>16</sup>, Dorran Howell<sup>17</sup>, Shantenu Jha<sup>18</sup>, Daniel S. Katz<sup>19</sup>, Daniel Laney<sup>11</sup>, Ulf Leser<sup>20</sup>, Maciej Malawski<sup>8</sup>, Kshitij Mehta<sup>1</sup>, Loïc Pottier<sup>2</sup>, Jonathan Ozik<sup>4,5</sup>, J. Luc Peterson<sup>11</sup>, Lavanya Ramakrishnan<sup>21</sup>, Stian Soiland-Reyes<sup>16,22</sup>, Douglas Thain<sup>23</sup>, Matthew Wolf<sup>1</sup>_

<div class="affiliations">

<sup>1</sup>Oak Ridge National Laboratory, Oak Ridge, TN, USA  
<sup>2</sup>University of Southern California, Marina Del Rey, CA, USA  
<sup>3</sup>University of Hawaii, Honolulu, HI, USA  
<sup>4</sup>Argonne National Laboratory, Lemont, IL, USA  
<sup>5</sup>The University of Chicago, Chicago, IL, USA  
<sup>6</sup>University of California, San Diego, La Jolla, CA, USA  
<sup>7</sup>Barcelona Supercomputing Center, Spain  
<sup>8</sup>AGH University of Science and Technology, Krakow, Poland  
<sup>9</sup>Ghent University, Ghent, Belgium  
<sup>10</sup>VIB Center for Plant Systems Biology, Belgium  
<sup>11</sup>Lawrence Livermore National Lab, Livermore, CA, USA  
<sup>12</sup>University of Innsbruck, Innsbruck, Austria  
<sup>13</sup>Heriot-Watt University, Edinburgh, UK  
<sup>14</sup>OctoML, USA  
<sup>15</sup>Universidad Politécnica de Madrid, Spain  
<sup>16</sup>The University of Manchester, Manchester, UK  
<sup>17</sup>Tweag, Zürich, Switzerland  
<sup>18</sup>Brookhaven National Laboratory, Upton, NY, USA  
<sup>19</sup>University of Illinois at Urbana-Champaign, USA  
<sup>20</sup>Humboldt-Universität zu Berlin, Berlin, Germany  
<sup>21</sup>Lawrence Berkeley National Lab, Berkeley, CA, USA  
<sup>22</sup>University of Amsterdam, Amsterdam, The Netherlands  
<sup>23</sup>University of Notre Dame, Indiana, USA  

</div>

## Abstract

The landscape of workflow systems for scientific applications is notoriously convoluted with hundreds of seemingly equivalent workflow systems, many isolated research claims, and a steep learning curve. To address some of these challenges and lay the groundwork for transforming workflows research and development, the WorkflowsRI and ExaWorks projects partnered to bring the international workflows community together. 

This paper reports on discussions and findings from two virtual “Workflows Community Summits” (January and April, 2021). The overarching goals of these workshops were to develop a view of the state of the art, identify crucial research challenges in the workflows community, articulate a vision for potential community efforts, and discuss technical approaches for realizing this vision. 

To this end, participants identified six broad themes: FAIR computational workflows; AI workflows; exascale challenges; APIs, interoperability, reuse, and standards; training and education; and building a workflows community. We summarize discussions and recommendations for each of these themes.

## Introduction

Scientific workflows are used almost universally across scientific domains for solving complex and large-scale computing and data analysis problems. The importance of workflows is highlighted by the fact that they have underpinned some of the most significant discoveries of the past decades \[[Badia 2017]\]. Many of these workflows have significant computational, storage, and communication demands, and thus must execute on a range of large-scale platforms, from local clusters to public clouds and upcoming exascale HPC platforms \[[Ferreira da Silva 2017]\]. Managing these executions is often a significant undertaking, requiring a sophisticated and versatile software infrastructure.

Historically, infrastructures for workflow execution consisted of complex, integrated systems, developed in-house by workflow practitioners with strong dependencies on a range of legacy technologies—even including sets of ad-hoc scripts. Due to the increasing need to support workflows, dedicated workflow systems were developed to provide abstractions for creating, executing, and adapting workflows conveniently and efficiently while ensuring portability. While these efforts are all worthwhile individually, there are now hundreds of independent workflow systems \[[CWL 2021]\]. These workflow systems are created and used by thousands of researchers and developers, leading to a rapidly growing corpus of workflows research publications. The resulting workflow system technology landscape is fragmented, which may present significant barriers for future workflow users due to many seemingly comparable, yet usually mutually incompatible, systems that exist.

<table>
<thead>
<tr>
    <th>Theme</th> 
    <th>Challenges</th>
    <th>Community Activities</th>
</tr>
</thead>
<tbody>
<tr>
<th>FAIR Computational Workflows</th>
<td><ul>
<li>FAIR principles for computational workflows that consider the complex lifecycle from specification to execution and data products</li>
<li>Metrics to measure the “FAIRness” of a workflow</li>
<li>Principles, policies, and best practices</li>
</ul></td>
<td><ul>
<li>Review prior and current efforts for FAIR data and software with respect to workflows, and outline principles for FAIR workflows</li>
<li>Define recommendations for FAIR workflow developers and systems</li>
<li>Automate FAIRness in workflows by recording necessary provenance data</li>
</ul></td>
</tr>
<tr>
<th>AI Workflows</th>
<td><ul>
<li>Support for heterogeneous compute resources and fine-grained data management features, versioning, and data provenance capabilities</li>
<li>Capabilities for enabling workflow steering and dynamic workflows</li>
<li> Integration of ML frameworks into the current HPC landscape </li>  
</ul></td>
<td><ul>
<li>Develop comprehensive use cases for sample problems with representative workflow structures and data types</li>
<li>Define a process for characterizing the challenges for enabling AI workflows</li>
<li>Develop AI workflows as a way to benchmark HPC systems</li>
</ul></td>
</tr>
<tr>
<th>Exascale Challenges and Beyond</th>
<td><ul>
<li>Resource allocation policies and schedulers are not designed for workflow-aware abstractions, thus users tend to use an ill-fitted job abstraction</li>
<li>Unfavorable design of resource descriptions and mechanisms for workflow users/systems, and lack of fault-tolerance and fault-recovery solutions</li>
</ul></td>
<td><ul>
<li>Develop documentation in the form of workflow templates/recipes/miniapps for execution on high-end HPC systems</li>
<li>Specify benchmark workflows for exascale execution</li>
<li>Include workflow requirements as part of the machine procurement process</li>
</ul></td>
</tr>
<tr>
<th>APIs, Reuse, Interoperability, and Standards</th>
<td><ul>
<li>Workflow systems differ by design, thus interoperability at some layers is likely to be more impactful than others</li>
<li>Workflow standards are typically developed by a subset of the community</li>
<li>Quantifying the value of common representations of workflows is not trivial</li>
</ul></td>
<td><ul>
<li>Identify differences and commonalities between different systems</li>
<li>Identify and characterize domain-specific efforts, identify workflow patterns, and develop case-studies of business process workflows and serverless workflow systems</li>
</ul></td>
</tr>
<tr>
<th>Training and Education</th>
<td><ul>
<li>Many workflow systems have high barriers to entry and lack training materials</li>
<li>Homegrown workflow solutions and constraints can prevent users from reproducing their functionality on workflow systems developed by others</li>
<li>Unawareness of the workflow technological and conceptual landscape  </li>
</ul></td>
<td><ul>
<li>Identify basic sample workflow patterns, develop a community workflow knowledge-base, and look at current research on technology adoption</li>
<li>Include workflow terminology and concepts in university curricula and software carpentry efforts</li>
</ul></td>
</tr>
<tr>
<th>Building a Workflows Community</th>
<td><ul>
<li>Diverse definitions of a “workflows community”</li>
<li>Remedy the inability to link developers and users to bridge translational gaps</li>
<li>Pathways for participation in a network of researchers, developers, and users</li>
</ul></td>
<td><ul>
<li>Establish a common knowledge-base for workflow technology</li>
<li>Establish a <emph>Workflow Guild</emph>: an organization focused on interaction and relationships, providing self-support between workflow developers and their systems</li>
</ul></td>
</tr>
</tbody>
<caption><strong>Table 1</strong>: 
Summary of current workflows research and development challenges and proposed community activities</caption>
</table>


In the current workflow research, there are conflicting theoretical bases and abstractions for what constitutes a workflow system. It may be possible to translate between systems that use the same underlying abstractions; however, the contrary is not feasible. Specifically, typical systems have a layered model that abstractly underlie them: (i) if the models are the same for two systems, they are compatible to some extent, and if they implement the same layers, they can be interchanged (modulo some translation effort); (ii) if the models are the same for two systems, but they are implemented by components at different layers, they can be complementary, and may have common elements that could be shared; (iii) if the models are distinct, workflows or system components are likely not exchangeable or interoperable. As a result, many teams still elect to build their own custom solutions rather than adopt, adapt, or build upon, existing workflow systems. This current state of the workflow systems landscape negatively impacts workflow users, developers, and researchers \[4\].

The WorkflowsRI \[5\] and ExaWorks \[6\] projects have partnered to bring the workflows community (researchers, developers, science and engineering users, and cyberinfrastructure experts) together to collaboratively elucidate the R\&D efforts necessary to remedy the above situation. They conducted a series of virtual events entitled “Workflows Community Summits,” in which the overarching goal was to (i) develop a view of the state of the art, (ii) identify key research challenges, (iii) articulate a vision for potential activities, and (iv) explore technical approaches for realizing (part of) this vision. The summits gathered over 70 participants, including lead researchers and developers from around the world, and spanning distinct workflow systems and user communities.
The outcomes of the summits have been compiled and published in two technical reports \[7–8\]. In this paper, we summarize the discussions and findings by presenting a consolidated view of the state of the art, challenges, and potential efforts, which we synthesize into a community roadmap. Table 1 presents, in the form of top-level themes, a summary of those challenges and targeted community activities. Table [\[tab:roadmap\]](#tab:roadmap) summarizes a proposed community roadmap with technical approaches.

The remainder of this paper is organized as follows. Sections [2](#sec:fair)--[7](#sec:community) provide a brief state of the art and challenges for each theme and proposed community activities. Section [8](#sec:roadmap) discusses technical approaches for a community roadmap. Section [9](#sec:conclusion) concludes with a summary of discussions.



## FAIR Computational Workflows {#sec:fair}

The FAIR principles \[9\] have laid a foundation for sharing and publishing digital assets and, in particular, data. The FAIR principles emphasize machine accessibility and that all digital assets should be Findable, Accessible, Interoperable, and Reusable. Workflows encode the methods by which the scientific process is conducted and via which data are created. It is thus important that workflows both support the creation of FAIR data and themselves adhere to the FAIR principles.

### Brief State-of-the-art and Challenges

Workflows are hybrid processual digital assets that can be considered as data or software, or some combination of both. As such, there is a range of considerations to take into account with respect to the FAIR principles \[10\]. Some perspectives are already well explored in data/software FAIRness, such as descriptive metadata, software metrics, and versioning; however, workflows create unique challenges such as representing a ***complex lifecycle*** from specification to execution via a workflow system, through to the data created at the completion of the workflow execution.

As a specialized kind of software, workflows have two properties that FAIRness fundamentally must address: ***abstraction and composition***. As far as possible a workflow specification, as a graph or some declarative expression, is abstracted from its execution undertaken by a dedicated software platform. Workflows are composed of modular building blocks and expected to be remixed. FAIR applies “all the way down” at the specification and execution level, and for the whole workflow and each of its components. One of the most challenging aspects of making workflows FAIR is ensuring that they can be ***reused***. These challenges include being able to capture and then move workflow components, dependencies, and application environments in such a way as not to affect the resulting execution of the workflow. Further work is required to understand use cases for reuse, before exploring methods for capturing necessary context and enabling reuse in the same or different environments.

Once use cases are defined, there are many ***metrics and features*** that could be considered to determine whether a workflow is FAIR. These features may differ depending on the type of workflow and its application domain. Prior work in data and software FAIRness \[9–11\] provides a starting point, however, these metrics need to be revised for workflows. In terms of labeling workflows as being FAIR, there has been widespread adoption of reproducibility badges for publications and of FAIR labels for data in repositories \[12\]. Similar approaches could be applied to computational workflows.
Finally, developing methods for FAIR workflows requires ***community engagement*** (i) to define principles, policies, and best practices to share workflows; (ii) to standardize metadata representation and collection processes; (iii) to create developer-friendly guidelines and workflow-friendly tools; and (iv) to develop shared infrastructure for enabling development, execution, and sharing of FAIR workflows.

### A Vision for Potential Community Activities

Given current efforts for developing FAIR data and software, it is important to first understand what efforts could be adapted to workflow problems. An immediate activity is to participate in working groups focused on applying FAIR principles to data and software. For instance, FAIR4RS \[13\] coordinates community-led discussions around FAIR principles for research software. Workflows could then be initially tackled from the point of view of workflows as software, which could originate a novel ***task force***. Proposed working groups such as FAIR for Virtual Research Environments \[14\] represent adequate progress towards this goal.

A fundamental tenet of FAIR is the universal availability of machine processable metadata. The European EOSC-Life Workflow Collaboratory, for example, has developed a metadata framework for FAIR workflows based on schema.org \[15\], RO-Crate \[16\], and CWL \[17\]. This could be a community starting point for standardization of metadata about workflows.

An integral aspect of a FAIR computational workflows task force would be to collect a set of real-world use cases and workflows in several domains to examine from the perspective of the FAIR data principles. This exercise will likely highlight areas in which the FAIR data principles adequately represent challenges in workflows. Based on these experiences, a set of ***simple rules*** could be defined for creating FAIR workflows, similar to those defined for software \[18\]. From these rules,
prominent workflow repositories (e.g., WorkflowHub.eu \[19\] and Dockstore \[20\]), communities, and workflow systems can define ***recommendations*** to support the development and sharing of FAIR workflows. These efforts relate not only to the workflows themselves, but the workflow components, execution environments, and the different types of data.

Ensuring ***provenance*** can capture the necessary information is key for enabling FAIRness in workflows. Many provenance models \[21\] can be implemented or extended to capture the information needed for FAIR workflows. Further, FAIR principles are more likely to be followed if the process for capturing these metrics is automated and embedded in workflow systems. In this case, a workflow execution will become FAIR by default, or perhaps with minimal user curation.

## AI Workflows

Artificial intelligence (AI) and machine learning (ML) techniques are becoming increasingly popular within the scientific community. Many workflows now integrate ML models to guide analysis, couple simulation and data analysis codes, and exploit specialized computing hardware (e.g., GPUs, neuromorphic chips) \[22\]. These workflows inherently couple various types of tasks, such as short ML inference, multi-node simulations, and long-running ML model training. They are also often iterative and dynamic, with learning systems deciding in real time how to modify the workflow, for example, by adding new simulations or changing the workflow all together. AI-enabled workflow systems therefore must be able to optimally place and manage single- and multi-node tasks, exploit heterogeneous architectures (CPUs, GPUs, and accelerators), and seamlessly coordinate the dynamic coupling of disparate simulation tools.

### Brief State-of-the-art and Challenges

Workflows empowered with ML techniques largely differ from traditional workflows running on HPC systems.
ML workflows that target model training usually require an enormous quantity of input data (either via files or from a collection of databases) and produce a small number of trained models. After training, these models are used to infer new quantities (during “model inference”) and behave like very lightweight applications that produce small output data volumes. These models can be stand-alone applications, or even embedded within larger traditional simulations. There exists an inherent tension between traditional HPC, which evolved around executing large capacity-style codes and AI-HPC, which requires the coordinated execution of many smaller capability-scale applications (e.g., large ensembles of data generation co-mingled with inference and coinciding with periodic retraining of models).

With its reliance of data, effective AI workflows should provide ***fine-grained data management*** and versioning features, as well as adequate data provenance capabilities. This data management must be flexible: some applications and workflows may move data via a file-system, while others may be better served from a traditional database, data store, or a streaming dataflow model. During inference, it may be best to couple the (lightweight) model as close to the data it is processing as possible. In any case, effective data management is a key feature of successful AI workflows.

AI workflows often require non-traditional hardware, such as GPUs and tensor processing units (TPUs), which can significantly accelerate both training and inference steps. Workflow systems thus need to provide mechanisms for managing execution on ***heterogeneous resources***, for example, by offloading heavy computations to GPUs, and managing data between GPU and CPU memory hierarchies. Furthermore, since ML training and inference may be best executed on different hardware from the main simulation, AI workflows may need to enable execution on ***multi-machine federated systems*** (with the main code executed on a traditional HPC system and the ML model training or inference on a separate system). Further, it is also necessary to provide tight ***integration with widely-used ML frameworks***, the development of which is not driven by the HPC community. ML frameworks use Python and R-based libraries and do not follow the classic HPC model: C/C++/Fortran, MPI, and OpenMP, and submission to an HPC batch scheduler. Yet, some efforts in the HPC community seem promising, such as LBANN \[23\], EMEWS \[24\], and eFlows4HPC \[25\]. Other approaches like Merlin \[26\] blend HPC and cloud technologies to enable federated workflows. However, there is a clear disconnect between HPC motivations, needs, and requirements, and current AI practices.

Finally, one of the major differences between traditional and AI workflows is the inherent ***iterative nature of ML processes***—AI workflows often feature feedback loops over a data set. Data are created, the model is retrained, and its accuracy evaluated. ML training tasks might leverage hyperparameter optimization frameworks \[27–29\] to adjust their execution settings in real time. The final trained model is often used to select new data to acquire (in an “active learning” environment, the model is used to decide which new simulations to run to better train the model on the next iteration). By design, ML-empowered workflows are dynamic, in contrast to traditional workflows with more structured and deterministic computations. At runtime, the workflow execution graph can potentially evolve based on internal metrics (accuracy), which may reshape the graph or trigger task preemption. Workflow systems should thus support ***dynamic branching*** (e.g., conditionals, criteria) and partial workflow re-execution on-demand.

### A Vision for Potential Community Activities

To address the disconnect between HPC systems and AI workflows, the community needs to develop sets of example ***use cases for sample problems*** with representative workflow structures and data types. In addition to expanding upon the above challenges, the community could “codify” these challenges in example use cases. However, the set of challenges for enabling AI workflows is extensive. The community thus should define a ***systematic process*** for identifying and categorizing these challenges. A short-term recommendation would be to write a “community white paper” about AI Workflow challenges and needs.

Building on the use cases above for the needs and requirements of AI workflows, the community could define ***AI-Workflow mini-apps***, which could be used to pair with vendors/future HPC developers so that the systems can be benchmarked against these workflows, and therefore support the co-design of emerging or future systems (e.g., MLCommons \[30\] and the Collective Knowledge framework \[31\]).

## Exascale Challenges and Beyond

Given the computational demands of many workflows, it is crucial that their execution be not only feasible but also effortless and efficient on large-scale HPC systems, and in particular upcoming exascale systems \[2\]. Exascale systems are likely to contain millions of independent computing elements that can be concurrently scheduled across more than 10,000 nodes, millions of cores, and tens of thousands of accelerators.

### Brief State-of-the-art and Challenges

HPC resource allocation policies and schedulers typically do not consider workflow applications: they provide a “job” abstraction rather than workflow-aware abstractions. Workflow users and systems are forced to make their workflows run on top of this ***ill-fitted abstraction***. As a result, it is difficult to control low-level behavior that is critical to workflows (e.g., precise mapping of tasks to specific compute resources on a compute node). Furthermore, there is a clear lack of support for elasticity (i.e., scaling up/down the number of nodes). Overall, it is currently difficult to run workflows efficiently and conveniently on HPC systems without extending (or even overhauling) resource management/scheduling approaches, which ideally would allow programmable, fine-grain application-level resource allocation and scheduling.

Related to the above challenge, it is currently not possible to support both workflow and non-workflow users harmoniously and/or efficiently on the same system. Some features needed by workflows are often unavailable. For instance, batch schedulers can support elastic jobs (e.g., Slurm); however, experience shows that system admins may not be willing to enable this capability, as they deem long static allocations to be preferable. A ***cultural change*** is perhaps needed as workflows are not often considered to be high-priority applications by high-end compute facilities.

Hybrid architectures are increasingly key to achieving high performance and many workflows can or are specifically designed to exploit such architectures; however, on HPC systems, the necessary ***resource descriptions and mechanisms*** are not necessarily available to workflow users/systems (even though some workflow systems have successfully interfaced to such mechanisms on particular systems) \[32\]. Although these resource descriptions and mechanisms are typically available as part of the “job” abstraction, it is often not clear how a workflow system can discover and use them effectively.

Finally, ***fault-tolerance and fault-recovery*** have been extensively studied on exascale systems, with several working solutions available for traditional parallel jobs \[33\]. In the context of workflows, specific techniques have been the subject of several studies \[34\]; however, workflow-specific solutions are typically not readily available or deployed. Moreover, workflows are built on smaller platforms, thus operating and testing at exascale would entail expressing new requirements/capabilities and dealing with new constraints (e.g., what is a “local” exascale workflow?).

### A Vision for Potential Community Activities

An immediate activity is to document, in the form of ***workflow templates, recipes, or miniapps***, example exascale workflows that can be hosted on a community website.
Some efforts underway provide partial solutions \[35\]. For instance, collections of workflows exist but typically do not provide large-scale execution capabilities (e.g., community testbeds). Some compute facilities provide workflow system documentation to support their users \[36\]. These solutions should be cataloged as a starting point, and HPC facilities could promote yearly “workflow days,” in which they offer workflow users and developers training and early access to machines to test their workflows, thus gathering feedback from users and developers.

To drive the design of workflow-aware abstractions, the community could specify ***community benchmark workflows*** for exascale execution, exerting all relevant hardware as well as functionality capabilities. It will then become possible for different workflow systems to execute these benchmarks. Initial efforts could build on previous benchmark solutions \[37–38\]. These benchmarks could be included in ***acceptability tests for exascale machines***. Note that there will be a need to select particular workflow systems to run these benchmarks, which will foster training and education of HPC personnel.

Finally, including workflow requirements very early on in ***machine procurement process*** for machines at computing facilities will significantly lower the barriers for enabling workflow execution and therefore porting workflow applications. This effort is therefore preconditioned on the availability of miniapps and/or benchmark specifications, as well as API/scheduler specifications, as outlined above.

## APIs, Interoperability, Reuse, and Standards

There has been an explosion of workflow technologies in the last decade \[3\]. Individual workflow systems often serve a particular user community, a specific underlying compute infrastructure, a dedicated software engineering vision, or follow a specific historical trait. As a result, there are substantial technical and conceptual overlaps. Reasons for divergence include (i) use cases require different workflow structures, (ii) organizations have very different optimization goals, (iii) predefined execution systems provide fundamentally different capabilities, or (iv) availability and scarcity of different types of resources. Another reason is that it is relatively easy to start building a workflow system for a specific narrow focus (i.e., these systems have a gentle software development curve \[39\]), leading to large numbers of packages that provide some basic functionality, and developers who are subject to the sunk cost fallacy and then continue to invest in their custom packages, rather than joining forces and building community packages. This divergence leads to missed opportunities for interoperability. It is often difficult for workflows to be ported across systems, for system components to be interchanged, for provenance to be captured and exploited in similar ways, and for developers to leverage different execution engines, schedulers, or monitoring services.

### Brief State-of-the-art and Challenges

Workflow systems often grow organically: developers start by solving a concrete problem and they end up with a new workflow system. In some cases, workflow systems may ***differ by design***, rather than by accident. For example, they offer fundamentally different abstractions or models for a workflow: DAG-structured *vs.* recursive, imperative *vs.* declarative, data flow *vs.* control (and data) flow. These fundamental differences, catering for different use cases, make it such that full interoperability may simply not be possible.
However, in spite of these differences, workflow systems are often implemented with many layers and components that may be interchangeable, for example, workflow specifications, task descriptions, data passing methods, file handling, and task execution engines. Interoperability at some layers is likely to be more impactful than others; for instance, being able to run the same workflow specification (with appropriately encapsulated task implementations) on different workflow infrastructures would be a major relief for users trying to reuse workflows implemented in other organizations. Further, interoperability does not need to imply agreement and for workflow systems to implement a standard interface; instead, it may occur via shim layers or intermediate representations, in a similar manner to compiling to a high level language. With the reuse goal, projects as eFlows4HPC proposes the HPC Workflows as a Service (HPCWaaS) methodology, where workflows will be defined by expert developers and provided as a service to community users \[25\].

Most efforts to unify workflow systems and/or their components have led to the definition of various specifications developed by a subset of the community \[40–41\]. However, the specialization of some of these specifications may require that other systems conform to that specification, thus resulting in low adoption. Attempts to standardize also may lead to overly generic interfaces that in the end inhibit usability and lead to hidden incompatibilities.

A particularly pressing problem at the interface of workflow technology and HPC systems is the need for a ***common submission model*** that is compatible with heterogeneous platforms. The differences between the methods by which workflow engines, schedulers, and execution engines interact is a universal challenge faced by workflow developers when trying to target multiple infrastructures underlying long-lasting design decisions. Further challenges relate to authentication and authorization models deployed on many systems (e.g., two-factor authentication). Some efforts in this area are currently undergoing \[42\].

### A Vision for Potential Community Activities

An immediate and continuous action would be to host several ***“bake-offs”*** to compare workflow systems, including task and workflow definitions, a benchmark set of workflows with defined input and output data, as well as job execution interfaces. This would entail engaging participants to write and execute these workflows and identify commonalities between systems. A successful example is the GA4GH-DREAM challenge \[43\]. An open question is whether such attempts should be domain-specific or domain-overarching; there is likely a greater opportunity for standardization within domains (and indeed some domains have already made significant progress), but domain-specific standards would only partly solve the interoperability problem. The workflow community should then review these areas, determine and then publicize what has worked, and build on successful prior efforts.

With the emergence of FaaS (Function-as-a-Service) platforms (e.g., AWS Lambda, Azure Durable Functions, Google Cloud Functions, IBM Composer), or CaaS (Container-as-a-Service) services (e.g. AWS Fargate, Google Cloud Run), the community should identify a set of ***suggested use cases*** and compare them against an implementation with popular or recently developed FaaS-enabled workflow systems \[44–46\]. Such a comparison may identify complementary features that can benefit both industry and the workflows community. In addition to features, a set of common workflow patterns could also be identified. However, there is still some uncertainty regarding the scope of previously developed patterns (e.g., for representing patterns in dynamic workflows). Thus, it is necessary to ***survey published patterns*** \[47–48\] and identify gaps seen by the community.

Although the above proposed activities have the potential to advance interoperability, the current funding and research recognition models often implicitly work against standardization by constantly requiring innovative ideas even in areas where outreach, uptake, and maintenance rather than innovation seems to be the most pressing problem. Developing ***sustained funding models*** for building and evolving workflow standards, encouraging their adoption, supporting interoperability, testing, and providing user and developer training would help address these challenges.

## Training and Education for Workflow Users

There is a crucial need for more, better, and new training and education opportunities for workflow users. Many users “re-invent the wheel” without reusing software infrastructures and workflow systems that would make their workflow execution more convenient, more efficient, easier to evolve, and more portable. This is partly due to the lack of comprehensive and intuitive training materials available to guide users through the process of designing a workflow (besides the typical “toy” examples provided in tutorials).

### Brief State-of-the-art and Challenges

Adopting and using workflow systems can require significant effort and time, due to a ***steep learning curve***. A contributing factor is that users may not be familiar with workflows terminology and concepts. As a result, some have noted that what would be needed in the current technology landscape is to “ship a developer along with the workflow system”.

One of the reasons for the above challenge is that there are ***few “recipes” or “cookbooks”*** for workflow systems. Furthermore, given that workflows and their execution platforms are complex and diverse, in addition to mere training material, there is a need for a training infrastructure that consists of workflows and accompanying data (small enough to be used for training purposes but large enough to be meaningful) as well as execution testbeds for running these workflows.

Given the multitude of workflow systems \[3\], and the lack of standards (Section [5](#sec:interoperability)), users cannot easily pick the appropriate system(s) for their needs. More importantly, there is an understandable fear of being locked into a tool that at some point in the near future will no longer be supported. Although documentation can be a problem, ***guidance*** is the more crucial issue. Many users have the basic skills to create and execute workflows on some system, but as requirements gradually increase many users evolve their simple approaches in ad-hoc ways, thus developing/maintaining a working but ***imperfect homegrown system***. There is thus a high risk of hitting technological or labor-intensiveness roadblocks, which could be remedied by using a workflow system. But, when “graduating” to such a system, there will likely be constraints that prevent users from reproducing the functionality of their homegrown system. The benefits of using the workflow system should thus largely outweigh the drawback of these constraints.

Given all the above challenges, it is not easy to ***reach out to users at the appropriate time***. Reach out too early and users will not find the need to use a particular workflow system compelling. Reach out too late, and users are already locked into their homegrown system, even though in the long run this approach will severely harm their productivity.

### A Vision for Potential Community Activities

Lowering the entry barrier is key for enabling the next-generation of researchers to benefit from workflow systems. An initial approach would be to provide a basic set of simple, yet conceptually rich, ***sample workflow patterns*** (e.g., “hello world” one-task workflows, chain workflows, fork-join workflows, simple dynamic workflows), all with a few ways of handling data and I/O, and all with several target execution platforms. Then workflow system teams can provide (interactive) documentation (or could be hosted on a community Web site) describing how to run these patterns with their system \[36\]. Further, mechanisms should be identified at the institutional level to commit workflow systems ***training efforts in person***: (i) this should be based on existing facilities and universities efforts; (ii) the scope of the training should be narrowed so it is manageable; and (iii) the issue of “who trains the trainers?” needs to be addressed.

In light of workforce training, workflow concepts should be taught at early stages of the researchers/users education path. Precisely, these concepts should be included in university curricula, including domain science curricula. Recent efforts have produced pedagogic modules that target workflow education \[49–50\]. Pedagogic content could also be distributed as workflow modules to existing software carpentry efforts \[51\].

There is an established community of workflow researchers, developers, and users that has extensive expertise knowledge regarding specific systems, tools, applications, etc. It is crucial that this knowledge be captured to bootstrap a ***community workflow knowledge-base*** (following standards for documentation, interoperability, etc.) for training and education. The workflows community would also benefit from collaborations with social scientists and sociologists so as to help define an overall strategy for approaching some of the above challenges.

## Building a Workflows Community {#sec:community}

Given the current large size and fragmentation of the workflow technology landscape, there is a clear need to establish a cohesive community of workflow developers and users. This community would be crucial for avoiding unnecessary duplication of effort and would allow for sharing, and thus growing, of knowledge. To this end, there are four main components that need to be addressed for building a community: (i) identity building, (ii) trust, (iii) participation, and (iv) rewards.

### Brief State-of-the-art and Challenges

The most natural idea is to think of two ***distinct communities***: (i) a Workflow Research and Development Community, and (ii) a Workflow User Community. The former gathers people who share interest in workflow research and development, and corresponding sub-disciplines. Subgroups of this community are based on common methodologies, technical domains (e.g., computing, provenance, and design), scientific disciplines, as well as geographical and funding areas. The latter gathers anyone using workflows for optimization of their work processes. However, most domain scientists prioritize rigor on their domain-specific objectives, often viewing workflow development as a means to a solution.

The two aforementioned communities are not necessarily disjoint, but currently have little overlap. And yet, it is crucial that they interact. Such interaction seems to happen only on a case-by-case basis, rather than via organized community efforts. One could, instead, envision a single community (e.g., team of users, or “team-flow”) that gathers both workflow system developers and workflow-focused users, with the common goal of spreading knowledge and adoption of workflows, thus working towards increased ***sharing and convergence/interoperation*** of technologies and approaches.

Establishing trust and processes is key for bringing both communities together. There is no one-size-fits-all workflow system or solution for all domains, instead each domain presents their own specific needs and have different preferred ways to address problems. There is a pressing need for ***maintaining documentation and dissemination*** that fits different usage options and needs.

### A Vision for Potential Community Activities

Given the above, there are several existing community efforts that could serve as inspiration, for example, the WorkflowHub Club \[19\] and Galaxy \[52\]. One approach is to gather experience from computing facilities where teams have successfully adopted and are successfully running workflow systems \[36\]. Another possibility is to use proposal/project reviews as mechanisms for spreading workflow technology knowledge. Specifically, finding ways to make proposal authors (typically domain scientists) aware of available technology would prevent their proposed work from “re-inventing the wheel.” Finally, it is clear that solving the “community challenge” has large overlap with solving the “education challenge” (Section [6](#sec:training)).

A short-term activity would entail ***establishing a common knowledge-base for workflow technology*** so that workflow users could navigate the current technology landscape. User criteria (for navigation) need to be defined. Workflow system developers can add to this knowledge base via self-reporting and could include test statuses for a set of standard workflow configurations, especially if workflow systems are deployed across sites. There is large overlap with similar proposed community efforts identified in Sections [4](#sec:exascale) and [6](#sec:training).

An ambitious vision would be to ***establish a “Workflow Guild”***, an organization focused on interactions, relationships, and self-support between subscribing workflow developers and their systems, as well as dissemination of best-practices and tools that are used in the development and use of these systems. However, there are still barriers to be conquered: (i) such a community could be too self-reflecting, and yet still remain fragmented; (ii) a cultural/social problem is that creating a new system is typically more exciting for computer scientists as opposed to re-using an existing system; and (iii) building trust and reducing internal competition will be difficult, though building community identity will help the Guild work together against external competitors.

## A Roadmap for Workflows Research and Development

In the previous sections, we have described broad challenges for the workflows community and proposed a vision for community activities to address these challenges. Here, we explore technical approaches for realizing (part of) that vision. Based on the outcomes of the first summit \[7\], we identified three technical thrusts for discussion in the second summit \[8\]. Some of these thrusts align with a single theme of the first summit and some are cross-cutting. In the following subsections, we summarize discussions at the second summit and propose roadmap milestones that emerged from these discussions. Additional details can be found in the report from the second summit \[8\]. A summary of the roadmap milestones is shown in Table [\[tab:roadmap\]](#tab:roadmap).

### Defining Common Workflow Patterns and Benchmarks

The above sections highlight the need to establish repositories of common workflow patterns and benchmarks (Sections [3](#sec:ai), [4](#sec:exascale), [5](#sec:interoperability), and [6](#sec:training)). One objective is to develop workflow patterns in which each pattern should be easy for users to leverage as a starting point for their own specific workflow applications—they should provide links to one or more implementations, where each implementation is for a particular workflow system and can be downloaded and easily modified by the user. However, the *level of abstraction* of these patterns (i.e., the level of connection to real application use-cases) should still be defined. At one extreme, workflow patterns could be completely abstract with no connection to any real-world application. At the other extreme, workflow patterns could be completely use-case-driven and correspond to actual scientific applications, with realistic task computations and data sets. The end goal is thus to identify useful patterns that span the spectrum of possible levels of abstraction.

Another aspect is the level of detail with which a pattern specifies the platform on which it is to be executed and the logistics of the execution on that platform. The platform description could be left completely abstract, or it could be fully specified. Under-specifying execution platforms and logistics may render the pattern useless, but over-specifying them could render the pattern too niche.

Benchmark specifications should make it easy for workflow system developers to develop them or to determine that their system cannot implement these specifications. Each benchmark should provide links to implementations and data sets, where each implementation is for a particular workflow system. These implementations would be provided, maintained, and evolved by workflow system developers. They should be able to be packaged so that they are executed out of the box on the classes of platforms they support. Moreover, the input data of these workflows should be configurable in size to enable both weak and strong scaling experiments. For all configurations, also the output of the workflow must be provided to allow functional testing.

Given the above, the following milestones are proposed:

***M1.***
Define small sets (between 5 and 10) of workflow patterns and workflow benchmark deliverables. These should be defined by eliciting feedback from users and workflow system developers, as well as based on existing sources that provide or define real-world or synthetic workflow patterns.

***M2.***
Work with a selected set of workflow systems to implement the above patterns and benchmarks.

***M3.***
Investigate options for automatic generation of patterns and/or benchmarks using existing approaches \[38–53\].

***M4.***
Identify or create a centralized repository to host and curate the above patterns and benchmarks \[19–38\].

### Paths Toward Interoperability of Workflow Systems

Workflow systems differ in many ways, such as expressivity, execution models, and ecosystems. These differences are mainly due to individual implementations of language, control mechanisms (e.g., fault tolerance, loops), data management mechanisms, execution backends, reproducibility aspects for sharing workflows, and provenance and FAIR metadata capturing. The need for interoperability is paramount and can occur at multiple technical levels (e.g., task, tools, workflows, data, metadata, provenance, and packaging) as well as non-technical level including semantics, organizational, and legal issues (e.g., licenses compatibility, data sharing policies).

The need for interoperability of workflow applications and systems is commonly modeled as a problem of porting applications across systems, which may require days up to weeks of development effort \[54–55\]. Most of the previous approaches for tackling the interoperability problem attempted to develop complete vertical solutions rather than consider the perspective of making interoperable components. There is significant duplication between workflow systems and thus an opportunity to reuse and share components between systems. Developing interoperable components
will require defining standardized APIs, which is still an open challenge \[56–57\].

There is a tendency to tie the workflow with its execution model and data structures (e.g., the intertwine between the abstract workflow and its execution). Understanding which component in the workflow system architecture accounts for which functionality, is then paramount. Thus, separation of concerns is key for interoperability at many levels, for example, separation of orchestration of the workflow graph from its execution.

Given the above, the following milestones are proposed:

***M5.***
Define concrete notions of interoperability for different stakeholders, in particular workflow designers, workflow system developers, and workflow execution organizations.

***M6.***
Establish a “requirements” document per a small set of *abstraction layers* that will (i) capture the commonalities between components of workflow systems; and (ii) perform a separation of concerns to identify interoperability gaps.

***M7.***
Develop real-world workflow *benchmarks* featuring different configurations and complexities (see previous section). Such benchmarks would be key to evaluate the functionality of workflow systems and computing platforms systematically.

***M8.***
Develop *use cases* for interoperability based on real-life scenarios, such as porting workflows between platforms that provide different file systems and different resource managers.

***M9.***
Develop *common APIs* that represent a set of workflow system components, enabling interoperability to be achieved at the component level \[17–58–59\], including APIs for defining inputs, storing intermediate results, and output data.

***M10.***
Establish a workflow systems *developer community*. An immediate activity would be to develop a centralized repository of workflow-related research papers, and a workflow system registry aimed at DevOps and/or users.

### Improving Workflow Systems’ Interface with Legacy and Emerging HPC Software and Hardware Stacks

Improving the interface between workflow systems and existing as well as emerging HPC and cloud infrastructure is particularly important as workflows are designed to be used for long periods of time and may be moved between computing providers. This challenge is exacerbated with the specialization of hardware and software systems (e.g., with accelerators, virtualization, containers, and cloud or serverless infrastructures). Thus, it is important to address the challenges faced by workflow systems with respect to discovering and interacting with a diverse set of cyberinfrastructure resources and also the difficulties authenticating remote connections while adhering to facility policies.

Workflow systems require a standard method for querying a site on how to use that site, for example, information about the batch system, file system configuration, data transfer methods, and machine capabilities. It is crucial then to first understand what information is needed by workflow systems, what information could be made available programmatically and what must be manually curated (similar ongoing efforts \[60\] may provide the foundations for this effort).

A key capability provided by workflow systems is remote job execution, which is necessary in cases where workflows span facilities. However, authentication has always been challenging. Many workflow systems rely on fragile SSH connections and in the past the use of GSISSH for delegated authentication. Recently, sites have moved towards two factor authentication and even OAuth-based solutions. There are ongoing efforts to provide programmatic identity and access management in scientific domains \[61–63\]. While the topic of remote authentication is much more broad than the workflows community, there are important considerations that should be included in this discussion related to programmatic access, community credentials, and long-term access.

Given the above, the following milestones are proposed:

***M11.***
Document a machine-readable description of the essential properties of popular sites, for example, by defining a JSON schema and populating a GitHub repository with site descriptions.

***M12.***
Document remote authentication requirements from the workflow perspective and organize an event involving workflow system developers, end users, authentication technology providers, and facility operators.


## Summary of technical roadmap milestones per research and development thrust

Workflow patterns and benchmarks
: Investigate automatic generation of patterns and configurable benchmarks (e.g., to enable weak and strong scaling experiments).
: Establish or leverage a centralized repository to host and curate patterns and benchmarks.

Interoperability of workflow
: Develop real-world workflow benchmarks, use cases for interoperability, and common APIs that represent workflow library components.
: Establish a workflow systems developer community.

Interface with legacy and emerging HPC software and hardware stacks
: Identify new workflow patterns (e.g., motivated by AI workflows), attain portability across heterogeneous hardware, and develop a registry of execution environment information.
: Organize a community event involving workflow system developers, end users, authentication technology providers, and facility operators.


## Conclusion {#sec:conclusion}

In this paper, we have documented and summarized the wealth of information acquired as a result of two virtual “Workflows Community Summits.” The goal of these summits was to identify the common and current challenges faced by the workflows community, and outline a vision for short- and long-term community activities to address these challenges. From this vision, we have defined a community roadmap consisting of 12 milestones, which proposes solutions and technical approaches for achieving that vision. This initial series of successful events reinforces the need for continued engagement among workflow researchers, developers, and users, as well as enlarging the scope of the community to also embrace key stakeholders (e.g., computing facility operators and funding agency representatives) for enabling the proposed vision and roadmap.


-----

## Acknowledgements

This work was funded by NSF awards \#2016610, \#2016682, and \#2016619, and by the Exascale Computing Project (17-SC-20-SC), a collaborative effort of the U.S. Department of Energy (DOE) Office of Science and the National Nuclear Security Administration (NNSA).

This research used resources of the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. DOE under Contract \#DE-AC05-00OR22725.

CG and SSR acknowledge funding from European Commission’s contracts BioExcel-2 (H2020-INFRAEDI-2018-1 823830), EOSC-Life (H2020-INFRAEOSC-2018-2 824087), IBISBA 1.0 (H2020-INFRAIA-2017-1-two-stage 730976), PREP-IBISBA (H2020-INFRADEV-2019-2 871118), SyntheSys+ (H2020-INFRAIA-2018-1 823827). UL acknowledges funding from the German Research Council for CRC 1404 FONDA.

FC is supported by the Research Foundation-Flanders (FWO, I002819N) and by the European Union’s Horizon 2020 research and innovation programme under grant \#824087 (EOSC-Life).
BSC authors acknowledge EuroHPC JU under contract 955558 (eFlows4HPCproject).

We thank all participants of the Workflows Community Summits, held in January 2021 and April 2021.


## References

<div id="refs" class="references">

\[Badia 2017\]
1\. Rosa Maria Badia Sala, Eduard Ayguade, Jesus Labarta(2017):  
** **
**Workflows for science**: A challenge when facing the convergence of HPC and big data.  
*Supercomputing frontiers and innovations* **4**(1)  
<https://doi.org/10.14529/jsfi170102>

\[Ferreira da Silva 2017]\
2\. Rafael Ferreira da Silva, Rosa Filgueira, Ilia Pietri, Ming Jiang, Rizos Sakellariou, Ewa Deelman(2017):  
** **
**A characterization of workflow management systems for extreme-scale applications**.  
*Future Generation Computer Systems* **75**  
<https://doi.org/10.1016/j.future.2017.02.026>
[[preprint](https://research.manchester.ac.uk/en/publications/d9825e4c-5117-431b-ac71-da95747c5762)]

\[CWL 2021\]: Peter Amstutz, Maxim Mikheev, Michael R. Crusoe, Nebojša Tijanić, Samuel Lampa, et al.(2021):  
** **
**Existing Workflow systems**.  
Common Workflow Language wiki, GitHub.  
<https://s.apache.org/existing-workflow-systems> accessed 2021


[Badia 2017]: https://doi.org/10.14529/jsfi170102 "Workflows for science"
[Ferreira da Silva 2017]: https://research.manchester.ac.uk/en/publications/d9825e4c-5117-431b-ac71-da95747c5762 "A characterization of workflow management systems for extreme-scale applications"
[CWL 2021]: https://s.apache.org/existing-workflow-systems "Existing Workflow systems"


3\.(2021):  
**Existing workflow systems**. (2021)

</div>

<div id="ref-deelman2018future">

4\. Ewa Deelman & others(2018):  
**The future of scientific workflows**.   
_International Journal of High Performance Computing Applications_ **32**

</div>

<div id="ref-workflowsri">

5\.(2021):  
**workflowsRI**. (2021)

</div>

<div id="ref-al2021exaworks">

6\. Aymen Al-Saadi, Dong H. Ahn, Yadu Babuji, Kyle Chard, James Corbett, Mihael Hategan, Stephen Herbein, Shantenu Jha, Daniel Laney, Andre Merzky, & others(2021):  
**ExaWorks**: Workflows for Exascale. *arXiv preprint arXiv:2108.13521*, (2021)

</div>

<div id="ref-ferreiradasilva2021wcs">

7\. Rafael Ferreira da Silva, Henri Casanova, Kyle Chard, Dan Laney, Dong Ahn, Shantenu Jha, Carole Goble, Lavanya Ramakrishnan, & others(2021):  
**Workflows Community Summit**: Bringing the Scientific Workflows Community Together. (2021).
<https://doi.org/10.5281/zenodo.4606958>

</div>

<div id="ref-wcs2021technical">

8\. Rafael Ferreira da Silva, Henri Casanova, Kyle Chard, & others(2021):  
**Workflows Community Summit**: Advancing the State-of-the-art of Scientific Workflows Management Systems Research and Development. (2021).
<https://doi.org/10.5281/zenodo.4915801>

</div>

<div id="ref-wilkinson2016fair">

9\. Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, & others(2016):  
**The FAIR guiding principles for scientific data management and stewardship**.   
_Scientific Data_ **3**
<https://doi.org/10.1038/sdata.2016.18>

</div>

<div id="ref-goble2020">

10\. Carole Goble, Sarah Cohen-Boulakia, Stian Soiland-Reyes, Daniel Garijo, Yolanda Gil, Michael R. Crusoe, Kristian Peters, & Daniel Schober(2020):  
**FAIR Computational Workflows**.   
_Data Intelligence_ **2**
<https://doi.org/10.1162/dint_a_00033>

</div>

<div id="ref-katz2021taking">

11\. Daniel S. Katz, Morane Gruenpeter, & Tom Honeyman(2021):  
**Taking a fresh look at FAIR for research software**.   
_Patterns_ **2**
<https://doi.org/10.1016/j.patter.2021.100222>

</div>

<div id="ref-acm-badges">

12\.(2021):  
**Software and Data Artifacts in the ACM Digital Library**. (2021)

</div>

<div id="ref-fair4rs">

13\.(2021):  
**FAIR for Research Software **(FAIR4RS) WG. (2021)

</div>

<div id="ref-fair4vre">

14\.(2021):  
**FAIR for Virtual Research Environments WG**. (2021)

</div>

<div id="ref-bioschemas-ComputationalWorkflow">

15\. Alan Williams & others(2021):  
**ComputationalWorkflow**: Bioschemas specification for describing a computational workflow. (2021).
<https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE>

</div>

<div id="ref-rocrate">

16\. Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, & others(2021):  
**Packaging research artefacts with ro-crate**. *Data Science*, (2021)

</div>

<div id="ref-cwl">

17\. Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, & others(2021):  
**Methods included**: Standardizing computational reuse and portability with the common workflow language. *Communications of the ACM*, (2021).
<https://doi.org/10.1145/3486897>

</div>

<div id="ref-monteil2020nine">

18\. Alain Monteil & others(2020):  
**Nine best practices for research software registries and repositories**: A concise guide. *arXiv:2012.13117*, (2020)

</div>

<div id="ref-workflowhub">

19\.(2021):  
**WorkflowHub**.eu. (2021)

</div>

<div id="ref-yuen2021dockstore">

20\. Denis Yuen & others(2021):  
**The dockstore**: Enhancing a community platform for sharing reproducible and accessible computational protocols. *Nucleic Acids Research*, (2021)

</div>

<div id="ref-oliveira2018provenance">

21\. Wellington Oliveira & others(2018):  
**Provenance analytics for workflow-based computational experiments**: A survey.   
_ACM Computing Surveys (CSUR)_ **51**

</div>

<div id="ref-zhou2017machine">

22\. Lina Zhou, Shimei Pan, Jianwu Wang, & Athanasios V. Vasilakos(2017):  
**Machine learning on big data**: Opportunities and challenges.   
_Neurocomputing_ **237**

</div>

<div id="ref-lbann">

23\. Brian Van Essen, Hyojin Kim, Roger Pearce, Kofi Boakye, & Barry Chen(2015):  
** **
**LBANN: Livermore big artificial neural network hpc toolkit**  
*Workshop on machine learning in high-performance computing environments* (2015).
<https://doi.org/10.1145/2834892.2834897>

</div>

<div id="ref-ozik_population_2021">

24\. Jonathan Ozik, Justin M. Wozniak, & others(2021):  
**A population data-driven workflow for COVID-19 modeling and learning**.   
_The International Journal of High Performance Computing Applications_ **35**
<https://doi.org/10.1177/10943420211035164>

</div>

<div id="ref-eflows">

25\. Jorge Ejarque, Rosa Badia, & others(2021):  
**Enabling dynamic and intelligent workflows for hpc**, big data, and ai convergence. *Future Generation Computing Systems*, **under review** (2021)

</div>

<div id="ref-merlin">

26\. J. Luc Peterson, Ben Bay, Joe Koning, Peter Robinson, & others(2021):  
**Enabling machine learning-ready HPC ensembles with merlin**. (2021).
<http://arxiv.org/abs/1912.02892>

</div>

<div id="ref-akiba2019optuna">

27\. Takuya Akiba, Shotaro Sano, Toshihiko Yanase, & others(2019):  
** **
**Optuna: A next-generation hyperparameter optimization framework**  
*25th acm sigkdd international conference on knowledge discovery & data mining* (2019)

</div>

<div id="ref-bergstra2013hyperopt">

28\. James Bergstra & others(2013):  
** **
**Hyperopt: A python library for optimizing the hyperparameters of machine learning algorithms**  
*12th python in science conference* (2013)

</div>

<div id="ref-wozniak2018">

29\. Justin M. Wozniak, Rajeev Jain, Prasanna Balaprakash, Jonathan Ozik, & others(2018):  
**CANDLE**/Supervisor: A workflow framework for machine learning applied to cancer research.   
_BMC Bioinformatics_ **19**
<https://doi.org/10.1186/s12859-018-2508-4>

</div>

<div id="ref-mlcommons">

30\.(2021):  
**ML Commons**. (2021)

</div>

<div id="ref-fursin2020collective">

31\. Grigori Fursin(2020):  
**Collective knowledge**: Organizing research projects as a database of reusable components and portable workflows with common apis.  
*arXiv:2011.01149*

</div>

<div id="ref-ahn2020flux">

32\. Dong H. Ahn & others(2020):  
**Flux**: Overcoming scheduling challenges for exascale workflows.   
_Future Generation Computer Systems_ **110**

</div>

<div id="ref-heldens2020landscape">

33\. Stijn Heldens & others(2020):  
**The landscape of exascale research**: A data-driven literature analysis.   
_ACM Computing Surveys_ **53**

</div>

<div id="ref-prathiba2017survey">

34\. Soma Prathiba & S. Sowvarnica(2017):  
**Survey of failures and fault tolerance in cloud**  
*2nd international conference on computing and communications technologies (iccct)* (2017)

</div>

<div id="ref-ewels2020nf">

35\. Philip A. Ewels & others(2020):  
**The nf-core framework for community-curated bioinformatics pipelines**.   
_Nature biotechnology_ **38**

</div>

<div id="ref-nersc-workflows">

36\.(2021):  
**NERSC Workflow Management Tools**. (2021)

</div>

<div id="ref-openebench">

37\.(2021):  
**OpenEBench**. (2021)

</div>

<div id="ref-coleman2021wfcommons">

38\. Tainã Coleman, Henri Casanova, Loı̈c Pottier, Manav Kaushik, Ewa Deelman, & Rafael Ferreira da Silva(2021):  
**WfCommons**: A framework for enabling scientific workflow research and development. *Future Generation Computer Systems*, (2021)

</div>

<div id="ref-SDCblog">

39\. Daniel S. Katz(2021):  
**Introducing the software development curve**. (2021)

</div>

<div id="ref-terstyanszky2014enabling">

40\. Gabor Terstyanszky & others(2014):  
**Enabling scientific workflow sharing through coarse-grained interoperability**.   
_Future Generation Computer Systems_ **37**

</div>

<div id="ref-cwl-annotations">

41\.(2021):  
**Common Workflow Language**: Metadata and Annotations. (2021)

</div>

<div id="ref-JLESC-common-registry">

42\. Daniel S. Katz, Rosa M. Badia, Chard Kyle, & Jorge Ejarque(2020):  
**JLESC research project**: A common workflow registry of compute endpoints and applications. (2020)

</div>

<div id="ref-ga4gh">

43\.(2021):  
**GA4GH-DREAM Workflow Execution Challenge**. (2021)

</div>

<div id="ref-chard2020funcx">

44\. Ryan Chard, Yadu Babuji, Zhuozhao Li, & others(2020):  
** **
**FuncX: A federated function serving fabric for science**  
*29th international symposium on high-performance parallel and distributed computing* (2020)

</div>

<div id="ref-smirnov2020apollo">

45\. Fedor Smirnov & others(2020):  
** **
**Apollo: Modular and distributed runtime system for serverless function compositions on cloud, edge, and iot resources**  
*1st workshop on high performance serverless computing* (2020)

</div>

<div id="ref-malawski2020serverless">

46\. Maciej Malawski, Adam Gajek, & others(2020):  
**Serverless execution of scientific workflows**: Experiments with hyperflow, aws lambda and google cloud functions.   
_Future Generation Computer Systems_ **110**

</div>

<div id="ref-workflowpatterns">

47\.(2021):  
**Workflow Patterns**. (2021)

</div>

<div id="ref-garijo2014common">

48\. Daniel Garijo, Pinar Alper, Khalid Belhajjame, Oscar Corcho, Yolanda Gil, & Carole Goble(2014):  
**Common motifs in scientific workflows**: An empirical analysis.   
_Future Generation Computer Systems_ **36**
<https://doi.org/10.1016/j.future.2013.09.018>

</div>
(2021):  
**Introducing the software development curve**
<div id="ref-eduwrench">

50\.(2021):  
**The EduWRENCH Pedagogic Modules**. (2021)

</div>

<div id="ref-swcarpentry">

51\.(2021):  
**Software Carpentry**. (2021)

</div>

<div id="ref-galaxy">

52\.(2021):  
**Galaxy Community Hub**. (2021)

</div>

<div id="ref-katz2016application">

53\. Daniel S. Katz, Andre Merzky, & others(2016):  
**Application skeletons**: Construction and use in eScience.   
_Future Generation Computer Systems_ **59**

</div>

<div id="ref-schiefer2020portability">

54\. Christopher Schiefer & others(2020):  
**Portability of scientific workflows in ngs data analysis**: A case study. *arXiv preprint arXiv:2006.03104*, (2020)

</div>

<div id="ref-LFB+21">

55\. Fabian Lehmann, David Frantz, & others(2021):  
** **
**FORCE on nextflow: Scalable analysis of earth observation data on commodity clusters**  
*Int. Workshop on complex data challenges in earth observation* (2021)

</div>

<div id="ref-turilli2019middleware">

56\. Matteo Turilli & others(2019):  
**Middleware building blocks for workflow systems**.   
_Computing in Science & Engineering_ **21**

</div>

<div id="ref-billings2017toward">

57\. Jay Jay Billings & Shantenu Jha(2017):  
**Toward common components for open workflow systems**. *arXiv preprint arXiv:1710.06774*, (2017)

</div>

<div id="ref-arshad2015definition">

58\. Junaid Arshad, Gabor Terstyanszky, Tamas Kiss, & Noam Weingarten(2015):  
** **
**A definition and analysis of the role of meta-workflows in workflow interoperability**  
*7th international workshop on science gateways* (2015)

</div>

<div id="ref-Fursin_2021">

59\. Grigori Fursin(2021):  
**Collective knowledge**: Organizing research projects as a database of reusable components and portable workflows with common interfaces.   
_Philosophical Transactions of the Royal Society A_ **379**
<https://doi.org/10.1098/rsta.2020.0211>

</div>

<div id="ref-sgci">

60\.(2021):  
**SGCI Resource Inventory**. (2021)

</div>

<div id="ref-tuecke16globus">

61\. Steven Tuecke, Rachana Ananthakrishnan, Kyle Chard, Mattias Lidman, Brendan McCollam, Stephen Rosen, & Ian Foster(2016):  
** **
**Globus auth: A research identity and access management platform**  
*12th ieee international conference on e-science (e-science)* (2016), pp. 203–212.
<https://doi.org/10.1109/eScience.2016.7870901>

</div>

<div id="ref-alt2020oauth">

62\. Jason Alt & others(2020):  
** **
**OAuth ssh with globus auth**  
*Practice and experience in advanced research computing* (2020)

</div>

<div id="ref-withers2018scitokens">

63\. Alex Withers, Brian Bockelman, Derek Weitzel, & others(2018):  
** **
**SciTokens: Capability-based secure access to remote scientific data**  
*Practice and experience on advanced research computing* (2018)

</div>

</div>
