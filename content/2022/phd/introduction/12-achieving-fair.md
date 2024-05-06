# Motivation – achieving FAIR research outputs

This section gives the motivation for the thesis, together with a brief background to inform the research questions in [Section 1.2](#outline). Further details on existing work are provided in [Section 2](../../../2023/phd/background/).

## FAIR Principles

The <abbr>FAIR</abbr> Principles [[Wilkinson 2016]] were introduced to improve sharing and digital reuse of research outputs ("*data*") as part of emerging open research practices. The main goals of FAIR are to support **F**indability, **A**ccessability, **I**nteroperability and **R**eusability, through machine-readable metadata and standardised publication methods for data, as quoted in Table [[[ch10:fair]]](#ch10:fair).

<div id="ch10:fair">

|      |                                                                                                  |
| ---: | :----------------------------------------------------------------------------------------------- |
|      | In order to be **Findable**:                                                                     |
|   F1 | (Meta)data are assigned a globally unique and persistent *identifier*.                           |
|   F2 | Data are described with rich *metadata* (defined by R1 below).                                   |
|   F3 | Metadata clearly and explicitly *include the identifier* of the data it describes.               |
|   F4 | (Meta)data are *registered* or *indexed* in a searchable resource.                               |
|      |                                                                                                  |
|      |                                                                                                  |
|   A1 | (Meta)data are *retrievable* by their identifier using a *standardized* communications protocol. |
| A1.1 | The protocol is *open*, free, and universally implementable.                                     |
| A1.2 | The protocol allows for an *authentication* and *authorization* procedure, where necessary.      |
|   A2 | *Metadata* are accessible, even when the *data are no longer available*.                         |
|      |                                                                                                  |
|      |                                                                                                  |
|   I1 | (Meta)data use a *formal*, accessible, shared, and broadly applicable *language for*             |
|      | *knowledge representation*.                                                                      |
|   I2 | (Meta)data use *vocabularies* that follow FAIR principles.                                       |
|   I3 | (Meta)data include qualified *references* to other (meta)data..                                  |
|      |                                                                                                  |
|      |                                                                                                  |
|   R1 | Meta(data) are richly described with a plurality of accurate and relevant *attributes*.          |
| R1.1 | (Meta)data are released with a clear and accessible *data usage license*.                        |
| R1.2 | (Meta)data are associated with detailed *provenance*.                                            |
| R1.3 | (Meta)data meet domain-relevant community *standards*.                                           |

FAIR Guiding Principles; adapted from [[Wilkinson 2016]], emphasis added in *italics*.

</div>

Although these guidelines are quite specific, they do not prescribe any particular technology or repository [[Mons 2017]]. Further formalizations of the FAIR principles include RDA’s FAIR Data Maturity Model [[FAIR Maturity 2020],[Bahui 2020]]. FAIR has also been expanded beyond data, e.g. to cover software [[Katz 2021b]], computational workflows [[Goble 2020]], training materials [[Garcia 2020a]], machine learning models [[Duarte 2023]] and digital twins [[Schultes 2022]].

The FAIR principles have become highly influential for open research stakeholders [[Jacobsen 2020]], particularly in large research infrastructure initatives such as by the European Open Science Cloud [(EOSC)](https://eosc.eu/) [[Schouppe 2018]], and increasing awareness and support for the principles by national Open Science policies and funders [[Davidson 2019],[Davidson 2022]].
Implementation of the principles by platform developers and researchers have however raised many questions and practical challenges [[Mons 2020],[Riungu-Kalliosaari 2022]].

For instance, in order to evaluate a given resource’s *FAIRness*, additional technical constraints need to be assumed, such as use of particular formal vocabularies. *FAIR metrics* [[Wilkinson 2018],[Devaraju 2021]] have recently become an area of active research, as different FAIR assessment tools may give a range of results for the same data resource, primarily based on which technical assumptions are made [[Wilkinson 2022a],[Verburg 2023]].

Recently there have been increased emphasis on training and awareness on the FAIR principles [[Shanahan 2021],[Rocca-Serra 2023]], and registries of standards and vocabularies [[Sansone 2019]].
However—with a general lack of skills in data management planning, inadequate (opaque) data formats and lack of time investment to provide rich metadata—data, even when shared through repositories, often becomes effectively "un-findable" or near impossible to reuse [[Carballo-Garcia 2022]].

From this we can identify several challenges with regards to finding practical ways for developers of <abbr>RS</abbr> to generate and consume FAIR data.

## Existing approaches to implementing FAIR

The vision on the Semantic Web [[Berners-Lee 1999]] were proposed as a way to make structured data on the Web. This evolved into a <abbr>LD</abbr> stack that uses logic-based ontologies, Web deployment of individually described resources, and cross-references between these resources with <abbr>URI</abbr> identifiers. The *Semantic Web* can be considered as the ecosystem of such <abbr>LD</abbr> resources, which can be queried, traversed and reasoned about.

Linked Data was seen early on as a possible mean to implementing the FAIR principles, and a large focus of initiatives like [GO-FAIR](https://www.go-fair.org/) and [Research Data Alliance](https://www.rd-alliance.org/) and the wider FAIR community has been to find ways to *FAIRify* existing data sources, such as developing domain-specific vocabularies and mappings, along with training and tooling to support these processes. FAIR publishing of datasets is encouraged using Data Catalog Vocabulary (DCAT) [[Albertoni 2023]], e.g. by the European Commission’s Semantic Interoperability Community Europe [(SEMIC)](https://joinup.ec.europa.eu/collection/semic-support-centre) and the larger [Interoperable Europe](https://joinup.ec.europa.eu/interoperable-europe) initiative.

There are now a large number of choices for Semantic Web technologies, serialisation formats, vocabularies, deployments and identifiers—motivating the proposal of *FAIR Implementation Profiles* [[Schultes 2020]] to document and guide these choices.

The field of Life Sciences was an early adopter of Linked Data, establishing training portals like [FAIR Cookbook](https://faircookbook.elixir-europe.org) [[Rocca-Serra 2023]] and has over [170 training materials for FAIR](https://tess.elixir-europe.org/materials?q=FAIR) listed in ELIXIR Europe’s training portal TeSS (as of 2024-04-28).
The ELIXIR service [FAIRsharing](https://fairsharing.org/) [[Sansone 2019]] has over 1700 standards, 2100 databases and 250 policies (as of 2024-04-28) for FAIR sharing of research data[^11].

A challenge for consumption of FAIR services in such a diverse landscape is thus how to support reliable *machine actionability*—making the data generally interpretable and typed sufficiently to allow invocation of pre-defined operations.

## FAIR Digital Objects (FDO)

*FAIR Digital Object* (<abbr>FDO</abbr>) has been proposed as a machine-actionable ecosystem of scholarly outputs [[Schultes 2019]], and has now become a major initiative for realising the <abbr>FAIR</abbr> principles in a different way than the initial Semantic Web approach.
FDO proponents envision a programmable mesh of strongly typed objects, which goes beyond the open data publication practices that the FAIR guidelines have popularised.
For this, FDO aims to provide concrete constraints for systems, which lead to predictable machine actions.

The FDO guidelines[[^12]] [[Anders 2023]] and the more detailed FDO specifications [[Ivonne 2023]] are largely conceptual in nature, with several demonstrated implementations [[Wittenburg 2022a],[Lannom 2022a]] which in theory can operate side-by-side.
Many of these, however, rely novel or older network protocols [[Reilly 2009],[Sun 2003a]] which are not particularly familiar to software developers, and not commonly supported by software libraries or frameworks.

This divergence from the more Web-centric “FAIR majority view”, while sound from a technical perspective and promising with regards to predictable computational consumption, raises organisational challenges for wider adoption of FDOs, e.g. within EOSC and research infrastructures, and might be introducing a steeper learning curve than already exists for FAIR, particularly for developers of <abbr>RS</abbr> who are primarily interested in solving scientific challenges.

Clearly the existing adoptions of Linked Data as-is would not present a coherent ecosystem for FDO machine-actionability, but it can be worth examining which aspects of the Web can benefit FDO development.

## Research Software and Computational Workflows

A growing (if not majority) part of scientific analysis is now conducted using software and computational models.
The concept of *Research Software Engineering* [[Cohen 2020]] has been established along with new professions *Research Software Engineer* [[Baxter 2012]] and *Data Scientist* [[van der Aalst 2014]]—researchers are not just using off-the-shelf software, but also combining multiple computational tools (e.g. in pipelines) and writing their own analytical source code (e.g. statistical R scripts) and simulations.

From this observation emerges the need to treat software as FAIR artefacts [[Lamprecht 2019]], following best practices for documentation [[Lee 2018]], open development [[Prlić 2012]] and ensuring Research Software (<abbr>RS</abbr>) is robust [[Taschuk 2017]] so it can be reused and cited as scholarly outputs [[Smith 2016]].
With this motivation, the principles of *FAIR Research Software* [[Katz 2021b]] have been established by the Research Data Allience (<abbr>RDA</abbr>) working group FAIR for Research Software (FAIR4RS) [[Barker 2022]] and are gradually building traction, particularly in the life sciences.
An example of a remaining challenge is how citations of Research Software can be practically propagated following their execution.

Sharing of Research Software according to these principles helps communicate the computational methods, expanding tremendously the potential for consumption, analysis and production of scientific data across organisations and their application to a broadening scope of research problems.

However, the *way* software is used for a particular analysis to reach a given scientific goal requires additional measures to make it *reproducible* [[Stodden 2016],[Sandve 2013]]. *Computational Workflows* (or scientific workflows) can structure and automate data analysis pipelines so they are scalable, portable and explainable [[Atkinson 2017]], and as a side-effect of these features can significantly improve reproducibility [[Cohen-Boulakia 2017]].

Several challenges emerge when considering sharing of workflows as FAIR digital objects. For instance, a workflow composes multiple tools that themselves need to be shared. Data used by a workflow have their own attribution and licenses. The execution of a workflow produces many intermediate data, but understanding that data creation from the workflow definition alone requires deep knowledge about the particular Workflow Management System (<abbr>WfMS</abbr>).

## Gathering scholarly outputs in Research Objects

The identified need for communicating computational methods through Research Software and workflows highlights that science must go beyond sharing of just data and metadata in order to achieve the FAIR principles. For a third-party researcher to fully take advantage of software and data, and to avoid delving further into the reproducibility crisis, the full set of contextual digital resources should be grouped and communicated as a scholarly unit.

[[Bechhofer 2013]] have been proposed as a mechanism to capture a range of diverse scholarly outputs in a single archivable item with detailed metadata. The RO concept was first realised using Semantic Web ontologies [[myExperiment 2009],[Belhajjame 2015]]—these approaches primarily targetted long-term preservation of scientific workflows, utillised by RO as a mechanism to capture computational methods, augmented by the workflow inputs, outputs, workflow engine configuration and human-readable explanation of each step.

The principles of Research Objects extend far beyond workflows—however, early RO implementations mainly focused on capturing software [[Goble 2018]]. To some extent, the lack of wider adoption of ontology-based ROs can also be explained by Research Software Engineers (e.g. molecular dynamics simulations) and platforms (e.g. repositories, data management systems) having a lack of familiarity with workflow systems or Semantic Web technology—or worse, they tried these technologies and then struggled [[Carriero 2010],[Tudorache 2020]].

From this, a challenge is to make Linked Data technology approachable for developers who are best placed at implementing the FAIR principles, in platforms that are effectively making Research Objects.

[11]: It is worth noting that not all of these databases and standards are based on Linked Data methods, and may be supporting FAIR principles in a looser sense.

[12]: See [Section 2](../../../2023/phd/background/#ch3:fdo-requirements)
