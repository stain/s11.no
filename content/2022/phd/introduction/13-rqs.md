# Research Outline and Questions

Following the motivation in Section [\[ch10:motivation\]](#ch10:motivation), this section elaborates Research Questions (RQ) on three interlinked ideas:

1.  Realization of the FAIR Digital Object concept using Web technologies.

2.  Implementing FAIR Research Objects with an pragmatic use of Linked Data practices.

3.  Unifying a FAIR Digital Object approach for computational workflows

## Aims for FAIR Digital Objects on the Web (RQ1)

The Web is ubiquitous in modern software engineering \[Taivalsaari 2021\], used for everything from user interfaces, mobile applications and controlling devices to enterprise cross-platform integrations, backend data processing and microservices, frequently utilising cloud computing which itself is controlled using Web technologies \[Marinescu 2023\].

The principles of seem important to achieve machine-actionable scholarly outputs, but several of these goals have an overlap with the motivations for the Semantic Web and Linked Data—yet it is not clear if changing from the Web stack to a different set of network protocols are necessary to achieve the FDO benefits.

A relevant research question therefore is:

#### RQ1:

Can the promising FDO concept be realised using existing Web technology, taking into account the lessons learnt from the early Semantic Web developments and more recent Linked Data practices?

I address RQ1 in Chapters [\[chapter:background\]](#chapter:background) and [\[chapter:fdo\]](#chapter:fdo).

## Aims for FAIR Research Objects (RQ2)

Following the lessons learnt on early <span data-acronym-label="RO" data-acronym-form="singular+full">RO</span> implementations and the emerging <span data-acronym-label="FAIR" data-acronym-form="singular+abbrv">FAIR</span> principles, a new engagement between the RO and digital libraries communities started in 2018, where it was agreed to formulate a lightweight approach to Research Objects \[Sefton 2018,Ó Carragáin 2019b\] for the purpose of data packaging. From this initative, the updated aims of *FAIR Research Objects* can be summarised as:

  - Describe and package data collections, datasets, software etc. with their metadata.

  - Platform-independent object exchange between repositories and services.

  - Support reproducibility and analysis: link data with codes and workflows.

  - Transfer of sensitive/large distributed datasets with persistent identifiers.

  - Aggregate citations and persistent identifiers.

  - Propagate provenance and existing metadata.

  - Publish and archive mixed objects and references.

  - Reuse existing standards, but hide their complexity.

Following from these aims, the second research question is:

#### RQ2:

Can a more pragmatic use of Linked Data practices better implement Research Objects for a wider developer audience, by using familiar Web technologies and give lightweight recommendations?

RQ2 is primarily addressed by Chapter [\[chapter:ro-crate\]](#chapter:ro-crate).

## Aims for FAIR Computational Workflows (RQ3)

There exists a plethora of <span data-acronym-label="workflow" data-acronym-form="singular+short">workflow</span> systems and languages \[Leipzig 2021,Amstutz 2021\], with recent efforts creating the Common Workflow Language \[Crusoe 2022\] as a standard representation with [FAIR metadata capabilities](https://www.commonwl.org/user_guide/topics/metadata-and-authorship.html) that is executable by multiple engines.

Notably, workflow definitions themselves can be considered FAIR scholarly outputs \[Goble 2020\]—*FAIR Computational Workflows* which are published in repositories like Dockstore \[Yuen 2021\] and WorkflowHub \[Goble 2021\].
One could consider computational workflows as a kind of FAIR Research Software \[de Visser 2023\], but by their nature workflows also *encourage the FAIR principles* (e.g. preparing a computational tool for a workflow system \[Brack 2022a\] may include publishing it in a container registry). Workflow systems are also useful for creating and consuming FAIR Digital Objects \[Wittenburg 2022b\], and in addition workflow systems commonly provide explicit provenance logs of their executions.

Approaches to describing workflow provenance in a machine-readable format were initially diverse \[Cruz 2009\], and later converged on the use of ontologies \[Missier 2010\], most notably using W3C PROV-O \[Lebo 2013a\] but with various specializations \[Garijo 2011,Garijo 2012,Missier 2013,Belhajjame 2015,Cuevas-Vicenttín 2016\].

The tendency for workflow provenance models to diverge may be down to differences in the execution semantics of different workflow systems—which if accurately reflected in provenance means further differences at this level. This in turn leads to incompatibility of provenance traces and lack of common tooling. In addition execution details may obscure the link from the computational procesesses and the final workflow data outputs that researchers ultimately care more about than the intricacies of the workflow engine.

The third research question from these considerations is therefore:

#### RQ3:

Can a FAIR Digital Object approach for computational workflows unify machine-readable descriptions of Research Software, data and provenance, which can be consistently implemented by developers of different workflow management systems?

The multiple aspects of RQ3, as highlighted in this section, are adressed by Chapter [\[chapter:workflows\]](#chapter:workflows).
