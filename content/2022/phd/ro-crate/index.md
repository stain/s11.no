---
title: "Chapter 5: Packaging research artefacts with RO-Crate"
weight: 50
bib: ro-crate
categories:
  - PhD
keywords:
- research object
- linked data
- scholarly communication
- Data publishing
- Data packaging
- FAIR
- Linked Data
- Metadata
- Reproducibility
- Research Object
lang: en-GB
date-meta: '2022-01-10'
author-meta:
- Stian Soiland-Reyes
- Peter Sefton
- Mercè Crosas
- Leyla Jael Castro
- Frederik Coppens
- José M. Fernández
- Daniel Garijo
- Björn Grüning
- Marco La Rosa
- Simone Leo
- Eoghan Ó Carragáin
- Marc Portier
- Ana Trisovic
- RO-Crate Community
- Paul Groth
- Carole Goble
summary: > 
  Journal article published in _Data Science_
description: > 
    An increasing number of researchers support reproducibility by including pointers to and descriptions of datasets, software and methods in their publications. However, scientific articles may be ambiguous, incomplete and difficult to process by automated systems. In this paper we introduce RO-Crate, an open, community-driven, and lightweight approach to packaging research artefacts along with their metadata in a machine readable manner. RO-Crate is based on Schema.org annotations in JSON-LD, aiming to establish best practices to formally describe metadata in an accessible and practical way for their use in a wide variety of situations. 

    An RO-Crate is a structured archive of all the items that contributed to a research outcome, including their identifiers, provenance, relations and annotations. As a general purpose packaging approach for data and their metadata, RO-Crate is used across multiple areas, including bioinformatics, digital humanities and regulatory sciences. By applying "just enough" Linked Data standards, RO-Crate simplifies the process of making research outputs FAIR while also enhancing research reproducibility.
---

<style>
  @import url("https://fonts.googleapis.com/css?family=Open+Sans:400,600,700"),
  @import url("https://fonts.googleapis.com/css?family=Source+Code+Pro"),
  @import url("https://fonts.googleapis.com/css2?family=STIX+Two+Text:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700&display=swap");
</style>

<h2>Cite as</h2>

Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):  
**Packaging research artefacts with RO-Crate**.  
_Data Science_ **5**(2)  
<https://doi.org/10.3233/DS-210053>  

# Packaging research artefacts with RO-Crate

_Stian Soiland-Reyes<sup>a,b</sup>, Peter Sefton<sup>c</sup>, Mercè Crosas<sup>d</sup>, Leyla Jael Castro<sup>e</sup>, Frederik Coppens<sup>f</sup>, José M. Fernández<sup>g</sup>, Daniel Garijo<sup>h</sup>, Björn Grüning<sup>i</sup>, Marco La Rosa<sup>j</sup>, Simone Leo<sup>k</sup>, Eoghan Ó Carragáin<sup>l</sup>, Marc Portier<sup>m</sup>, Ana Trisovic<sup>d</sup>, RO-Crate Community<sup>n</sup>, Paul Groth<sup>b</sup>, Carole Goble<sup>a</sup>_

<div class="affiliations">

<sup>a</sup> Department of Computer Science, The University of Manchester, Manchester, UK  
<sup>b</sup> Informatics Institute, University of Amsterdam, Amsterdam, The Netherlands  
<sup>c</sup> Faculty of Science, University Technology Sydney, Australia  
<sup>d</sup> Institute for Quantitative Social Science, Harvard University, Cambridge, MA, USA.  
<sup>e</sup> ZB MED Information Centre for Life Sciences, Cologne, Germany.  
<sup>f</sup> VIB-UGent Center for Plant Systems Biology, Gent, Belgium.  
<sup>g</sup> Barcelona Supercomputing Center, Barcelona, Spain.  
<sup>h</sup> Ontology Engineering Group, Universidad Politécnica de Madrid, Madrid, Spain.  
<sup>i</sup> Bioinformatics Group, Department of Computer Science, Albert-Ludwigs-University Freiburg, Freiburg, Germany.  
<sup>j</sup> PARADISEC, Melbourne, Australia.  
<sup>k</sup> Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Pula (CA), Italy.  
<sup>l</sup> University College Cork, Ireland.  
<sup>m</sup> Vlaams Instituut voor de Zee, Oostende, Belgium.  
<sup>n</sup> <https://www.researchobject.org/ro-crate/community> (see [Appendix B](#communitylist))  

</div>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown; figure caption formatting; reference in s11 house style; added identifiers, authors and years clarified where missing in citations; inline citation hyperlinks to open access version where available.

## Abstract 

An increasing number of researchers support reproducibility by including pointers to and descriptions of datasets, software and methods in their publications. However, scientific articles may be ambiguous, incomplete and difficult to process by automated systems. In this paper we introduce RO-Crate, an open, community-driven, and lightweight approach to packaging research artefacts along with their metadata in a machine readable manner. RO-Crate is based on Schema.org annotations in JSON-LD, aiming to establish best practices to formally describe metadata in an accessible and practical way for their use in a wide variety of situations. 

An RO-Crate is a structured archive of all the items that contributed to a research outcome, including their identifiers, provenance, relations and annotations. As a general purpose packaging approach for data and their metadata, RO-Crate is used across multiple areas, including bioinformatics, digital humanities and regulatory sciences. By applying "just enough" Linked Data standards, RO-Crate simplifies the process of making research outputs FAIR while also enhancing research reproducibility.

An [RO-Crate for this article](https://w3id.org/ro/doi/10.5281/zenodo.5146227) is archived at <https://doi.org/10.5281/zenodo.5146227>


## Introduction 

The move towards Open Science has increased the need and demand for the publication of artefacts of the research process [[1](http://ptsefton.com/2021/04/07/rdmpic/)]. This is particularly apparent in domains that rely on computational experiments; for example, the publication of software, datasets and records of the dependencies that such experiments rely on [[113](https://stodden.net/papers/ERCM2016-STODDEN.pdf)]. 

It is often argued that the publication of these assets, and specifically software [[80](https://doi.org/10.3233/DS-190026)], workflows [[55](https://doi.org/10.1162/dint_a_00033)] and data, should follow the FAIR principles [[123](https://doi.org/10.1038/sdata.2016.18)]; namely, that they are Findable, Accessible, Interoperable and Reusable. These principles are agnostic to the _implementation_ strategy needed to comply with them. Hence, there has been an increasing amount of work in the development of platforms and specifications that aim to fulfil these goals [[91](https://identifiers.org/isbn/9781315351148)]. 

Important examples include data publication with rich metadata (e.g. Zenodo [[40](https://doi.org/10.3897/biss.3.37080)]), domain-specific data deposition (e.g. PDB [[16](https://doi.org/10.1093/nar/gkl971)]) and following practices for reproducible research software [[101](https://doi.org/10.1371/journal.pcbi.1003285)] (e.g. use of containers). While these platforms are useful, experience has shown that it is important to put greater emphasis on the interconnection of the multiple artefacts that make up the research process [[71](https://doi.org/10.1016/j.ijhcs.2020.102562)]. 

The notion of **Research Objects** [[12](https://www.research.manchester.ac.uk/portal/en/publications/why-linked-data-is-not-enough-for-scientists(479e591e-b295-4478-b0c7-a145c19dcd45).html)] (RO) was introduced to address this connectivity, providing semantically rich _aggregations_ of (potentially distributed) resources with a layer of structure over a research study; this is then to be delivered in a _machine-readable format_. 

A Research Object combines the ability to bundle multiple types of artefacts together, such as spreadsheets, code, examples, and figures. The RO is augmented with annotations and relationships that describe the artefacts' _context_ (e.g. a CSV being used by a script, a figure being a result of a workflow). 

This notion of ROs provides a compelling vision as an approach for implementing FAIR data. However, existing Research Object implementations require a large technology stack [[14](https://doi.org/10.1016/j.websem.2015.01.003)], are typically tailored to a particular platform and are also not easily usable by end-users. 

To address this gap, a new community came together [[23](https://doi.org/10.5281/zenodo.3250687)] to develop **RO-Crate** — an _approach to package and aggregate research artefacts with their metadata and relationships_. The aim of this paper is to introduce RO-Crate and assess it as a strategy for making multiple types of research artefacts FAIR.  Specifically, the contributions of this paper are as follows:

1. An introduction to RO-Crate, its purpose and context;
2. A guide to the RO-Crate community and tooling;
3. Examples of RO-Crate usage, demonstrating its value as connective tissue for different artefacts from different communities.

The rest of this paper is organised as follows. We first describe RO-Crate through its development methodology that formed the RO-Crate concept, showing its foundations in Linked Data and emerging principles. We then define RO-Crate technically, before we introduce the community and tooling. We move to analyse RO-Crate with respect to usage in a diverse set of domains. Finally, we present related work and conclude with some remarks including RO-Crate highlights and future work. The appendix adds a formal definition of RO-Crate using First-Order logic.

## RO-Crate {#rocrate}

RO-Crate aims to provide an approach to packaging research artefacts with their metadata that can be easily adopted. To illustrate this, let us imagine a research paper reporting on the sequence analysis of proteins obtained from an experiment on mice. The sequence output files, sequence analysis code, resulting data and reports summarising statistical measures are all important and inter-related research artefacts, and consequently would ideally all be co-located in a directory and accompanied with their corresponding metadata. In reality, some of the artefacts (e.g. data or software) will be recorded as external reference to repositories that are not necessarily following the FAIR principles. This conceptual directory, along with the relationships between its constituent digital artefacts, is what the RO-Crate model aims to represent, linking together all the elements of an experiment that are required for the experiment's reproducibility and reusability. 

The question then arises as to how the directory with all this material should be packaged in a manner that is accessible and usable by others. This means programmatically and automatically accessible by machines and human readable. A de facto approach to sharing collections of resources is through compressed archives (e.g. a zip file). This solves the problem of “packaging”, but it does not guarantee downstream access to all artefacts in a programmatic fashion, nor describe the role of each file in that particular research. Both features, the ability to automatically access and reason about an object, are crucial and lead to the need for explicit metadata about the contents of the folder, describing each and linking them together.

Examples of metadata descriptions across a [wide range of domains](https://rdamsc.bath.ac.uk/scheme-index) abound within the literature, both in research data management [[6](https://doi.org/10.1007/s10209-016-0475-y)] [[46](https://dcpapers.dublincore.org/pubs/article/view/3714)] [[75](https://doi.org/10.2777/620649)] and within [library and information systems](https://www.loc.gov/librarians/standards) [[24](https://identifiers.org/isbn/9781563081910)] [[127](https://doi.org/10.1515/9783598441844)]. However, many of these approaches require knowledge of metadata schemas, particular annotation systems, or the use of complex software stacks. Indeed, particularly within research, these requirements have led to a lack of adoption and growing  frustration with current tooling and specifications [[94](https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/)] [[119](https://doi.org/10.1007/s00267-014-0258-2)] [[102](https://doi.org/10.1038/s41597-020-0524-5)].

RO-Crate seeks to address this complexity by:

1. being conceptually simple and easy to understand for developers;
2. providing strong, easy tooling for integration into community projects;
3. providing a strong and opinionated guide regarding current best practices;
4. adopting de-facto standards that are widely used on the Web.

In the following sections we demonstrate how the RO-Crate specification and ecosystem achieve these goals.



### Development Methodology {#methodology}

It is a good question as to what base level we assume for ‘conceptually simple’. We take simplicity to apply at two levels: for the _developers_ who produce the platforms and for the _data practitioners_ and users of those platforms. 

For our development methodology we followed the mantra of working closely with a small group to really get a deep understanding of requirements and ensure rapid feedback loops. We created a pool of early adopter projects from a range of disciplines and groups, primarily addressing developers of platforms. Thus the base level for simplicity was **developer friendliness**. 

We assumed a developer familiar with making Web applications with JSON data (who would then learn how to make _RO-Crate JSON-LD_), which informed core design choices for our JSON-level documentation approach and RO-Crate serialization (section on [implementation](#implementation)). Our group of early adopters, growing as the community evolved, drove the RO-Crate requirements and provided feedback through our multiple communication channels including bi-monthly meetings, which we describe in section on [community](#community) along with the established norms. 

Addressing the simplicity of understanding and engaging with RO-Crate by data practitioners is through the platforms, for example with interactive tools (section [RO-Crate tooling](#tooling)) like [Describo](https://arkisto-platform.github.io/describo/) [[78]](https://arkisto-platform.github.io/describo/) and Jupyter notebooks [[70](https://doi.org/10.3233/978-1-61499-649-1-87)], and by close discussions with domain scientists on how to appropriately capture what they determine to be relevant metadata. This ultimately requires a new type of awareness and learning material separate from developer specifications, focusing on the simplicity of extensibility to serve the user needs, along with user-driven development of new RO-Crate Profiles specific for their needs (section on [in use](#inuse)).



### Conceptual Definition {#conceptual}

A key premise of RO-Crate is the existence of a wide variety of resources on the Web that can help describe research. As such, RO-Crate relies on the Linked Data principles [[63](https://doi.org/10.2200/S00334ED1V01Y201102WBE001)]. [Figure 1](#fig:conceptual) shows the main conceptual elements involved in an RO-Crate: The RO-Crate Metadata File (top) describes the Research Object using structured metadata including external references, coupled with the contained artefacts (bottom) bundled and described by the RO-Crate.

The conceptual notion of a _Research Object_ [[12](https://www.research.manchester.ac.uk/portal/en/publications/why-linked-data-is-not-enough-for-scientists(479e591e-b295-4478-b0c7-a145c19dcd45).html)] is thus realised with the RO-Crate model and serialised using Linked Data constructs within the RO-Crate metadata file.

{{< figure src="ro-crate-overview.svg" 
link="ro-crate-overview.svg" id="fig:conceptual" 
width="100%" title="Conceptual RO-Crate Overview"
caption="A *Persistent Identifier* (PID) [[86](https://doi.org/10.1371/journal.pbio.2001414)] points to a *Research Object* (RO), which may be archived using different packaging approaches like BagIt [[74](https://doi.org/10.17487/rfc8493)], OCFL [[96]](https://ocfl.io/1.0/spec/), git or ZIP. The RO is described within a *RO-Crate Metadata File*, providing identifiers for *authors* using ORCID, *organisations* using Research Organization Registry (ROR) [[79](https://doi.org/10.6087/kcse.192)] and licences such as Creative Commons using SPDX identifiers. The *RO-Crate content* is further described with additional metadata following a Linked Data approach. Data can be embedded files and directories, as well as links to external Web resources, PIDs and nested RO-Crates." >}}


#### Linked Data as a foundation {#linkeddata}

The **Linked Data** principles [[18](https://doi.org/10.4018/978-1-60960-593-3.ch008)] (use of IRIs[^1] to identify resources (i.e. artefacts), resolvable via HTTP, enriched with metadata and linked to each other) are core to RO-Crate; therefore IRIs are used to identify an RO-Crate, its constituent parts and metadata descriptions, and the properties and classes used in the metadata.

RO-Crates are _self-described_ and follow the Linked Data principles to describe all of their resources in both human and machine readable manner.  Hence, resources are identified using global identifiers (absolute IRIs) where possible; and relationships between two resources are defined with links.

The foundation of Linked Data and shared vocabularies also means that multiple RO-Crates and other Linked Data resources can be indexed, combined, queried, validated or transformed using existing Semantic Web technologies such as [SPARQL](https://www.w3.org/TR/sparql11-overview), [SHACL](https://www.w3.org/TR/shacl/) and well established _knowledge graph_ triple stores like [Apache Jena](https://jena.apache.org/) and [OntoText GraphDB](https://www.ontotext.com/products/graphdb/). 

The possibilities of consuming[^15] RO-Crate metadata with such powerful tools gives another strong reason for using Linked Data as a foundation. This use of mature Web[^14] technologies also means its developers and consumers are not restricted to the Research Object aspects that have already been specified by the RO-Crate community, but can extend and integrate RO-Crate in multiple standardised ways.

[^1]: **IRI**s [[42](https://doi.org/10.17487/rfc3987)] are a generalisation of *URI*s (which include well-known http/https URLs), permitting international Unicode characters without percent encoding, commonly used on the browser address bar and in HTML5.

[^14]: Note that an RO-Crate is not required to be published on the Web, see section on [self-described](#selfdescribed).

[^15]: Some consideration is needed in processing of RO-Crates as knowledge graphs, e.g. establishing absolute IRIs for files inside a ZIP archive, detailed [in the RO-Crate specification](https://www.researchobject.org/ro-crate/1.1/appendix/relative-uris.html)


#### RO-Crate is a self-described container {#selfdescribed}

An [RO-Crate is defined](https://www.researchobject.org/ro-crate/1.1/structure.html#ro-crate-metadata-file-ro-crate-metadatajson) as a self-described **Root Data Entity** that describes and contains _data entities_, which are further described by referencing _contextual entities_.  A **data entity** is either a _file_ (i.e. a byte sequence stored on disk somewhere) or a _directory_ (i.e. set of named files and other directories). A file does not need to be stored inside the RO-Crate root, it can be referenced via a PID/IRI. A **contextual entity** exists outside the information system (e.g. a Person, a workflow language) and is stored solely by its metadata. The representation of a _data entity_ as a byte sequence makes it possible to store a variety of research artefacts including not only data but also, for instance, software and text.

The Root Data Entity is a directory, the _RO-Crate Root_, identified by the presence of the **RO-Crate Metadata File** `ro-crate-metadata.json` (top of [Figure 1](#fig:conceptual). This file fdescribes the RO-Crate using Linked Data, its content and related metadata using Linked Data in JSON-LD format [[112]](https://www.w3.org/TR/2014/REC-json-ld-20140116/). This is a W3C standard RDF serialisation that has become popular; it is easy to read by humans while also offering some advantages for data exchange on the Internet. JSON-LD, a subset of the widely supported and well-known JSON format, has tooling available for many [programming languages](https://json-ld.org/#developers).

The minimal [requirements for the root data entity metadata](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html#direct-properties-of-the-root-data-entity) are `name`, `description` and `datePublished`, as well as a contextual entity identifying its `license` — additional metadata are commonly added to entities depending on the purpose of the particular RO-Crate.

RO-Crates can be stored, transferred or published in multiple ways, e.g. BagIt [[74](https://doi.org/10.17487/rfc8493)], Oxford Common File Layout [[96]](https://ocfl.io/1.0/spec/) (OCFL), downloadable ZIP archives in Zenodo or through dedicated online repositories, as well as published directly on the Web, e.g. using [GitHub Pages](https://pages.github.com/). Combined with Linked Data identifiers, this caters for a diverse set of storage and access requirements across different scientific domains, from metagenomics workflows producing hundreds of gigabytes of genome data to cultural heritage records with access restrictions for personally identifiable data. Specific _RO-Crate profiles_ (section on [extensibility](#profiles)) may constrain serialization and publication expectations, and require additional contextual types and properties.



#### Data Entities are described using Contextual Entities {#contextualentities}

RO-Crate distinguishes between [data and contextual entities](https://www.researchobject.org/ro-crate/1.1/contextual-entities.html#contextual-vs-data-entities) in a similar way to HTTP terminology's early attempt to separate _information_ (data) and _non-information_ (contextual) resources [[120]](https://www.w3.org/2001/tag/doc/httpRange-14/2007-08-31/HttpRange-14.html). Data entities are usually files and directories located by relative IRI references within the RO-Crate Root, but they can also be Web resources or restricted data identified with absolute IRIs, including _Persistent Identifiers_ (PIDs) [[86](https://doi.org/10.1371/journal.pbio.2001414)].

As both types of entities are identified by IRIs, their distinction is allowed to be blurry; data entities can be located anywhere and be complex, while contextual entities can have a Web presence beyond their description inside the RO-Crate. For instance `https://orcid.org/0000-0002-1825-0097` is primarily an identifier for a person, but secondarily it is also a Web page and a way to refer to their academic work. 

A particular IRI may appear as a contextual entity in one RO-Crate and as a data entity in another; the distinction lies in the fact that data entities can be considered to be _contained_ or captured by that RO-Crate (_RO Content_ in [Figure 1](#fig:conceptual), while contextual entities mainly _explain_ an RO-Crate or its content (although this distinction is not a formal requirement).

In RO-Crate, a referenced contextual entity (e.g. a person identified by ORCID) should always be described within the RO-Crate Metadata File with at least a _type_ and _name_, even where their PID might resolve to further Linked Data. This is so that clients are not required to follow every link for presentation purposes, for instance HTML rendering. Similarly any imported [extension terms](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#extending-ro-crate) would themselves also have a human-readable description in the case where their PID does not directly resolve to human-readable documentation. 

[Figure 2](#fig:uml) shows a simplified UML class diagram of RO-Crate, highlighting the different types of data entities and contextual entities that can be aggregated and related. While an RO-Crate would usually contain one or more data entities (`hasPart`), it may also be a pure aggregation of contextual entities (`mentions`).

{{< figure src="ro-crate-uml.svg" 
link="ro-crate-uml.svg" 
id="fig:uml" width="100%" title="Simplified UML class diagram of RO-Crate"
caption="The *RO-Crate Metadata File* conforms to a version of the specification; and contains a JSON-LD graph [[112]](https://www.w3.org/TR/2014/REC-json-ld-20140116/) that describes the entities that make up the RO-Crate. The *RO-Crate Root Data Entity* represent the Research Object as a dataset. The RO-Crate aggregates *data entities* (`hasPart`) which are further described using *contextual entities* (which may include aggregated and non-aggregated data entities). Multiple types and relations from Schema.org allow annotations to be more specific, including figures, nested datasets, computational workflows, people, organisations, instruments and places. Contextual entities not otherwise cross-referenced from other entities' properties (*describes*) can be grouped under the root entity (`mentions`)." >}}



#### Guide through Recommended Practices {#recommendedpractices}

RO-Crate as a specification aims to build a set of recommended practices on how to practically apply existing standards in a common way to describe research outputs and their provenance, without having to learn each of the underlying technologies in detail.

As such, the [RO-Crate 1.1](https://w3id.org/ro/crate/1.1) specification [[106](https://doi.org/10.5281/zenodo.4541002)] can be seen as an opinionated and example-driven guide to writing [Schema.org](https://schema.org/) [[62](https://doi.org/10.1145/2857274.2857276)] metadata as JSON-LD [[112]](https://www.w3.org/TR/2014/REC-json-ld-20140116/) (see section on [implementation](#implementation), which leaves it open for implementers to include additional metadata using other Schema.org types and properties, or even additional Linked Data vocabularies/ontologies or their own ad-hoc terms.

However the primary purpose of the RO-Crate specification is to assist developers in leveraging Linked Data principles for the focused purpose of describing Research Objects in a structured language, while reducing the steep learning curve otherwise associated with Semantic Web adaptation, like development of ontologies, identifiers, namespaces, and RDF serialization choices.

#### Ensuring Simplicity {#simplicity}

One aim of RO-Crate is to be conceptually simple. This simplicity has been repeatedly checked and confirmed through an informal community review process. For instance, in the discussion on supporting [ad-hoc vocabularies](https://github.com/ResearchObject/ro-crate/issues/71) in RO-Crate, the community explored potential Linked Data solutions. The conventional wisdom in [RDF best practices](https://www.w3.org/TR/swbp-vocab-pub/) is to establish a vocabulary with a new IRI namespace, formalised using [RDF Schema](http://www.w3.org/TR/2014/REC-rdf-schema-20140225/) or [OWL](http://www.w3.org/TR/2012/REC-owl2-overview-20121211/) ontologies. However, this may seem an excessive learning curve for non-experts in semantic knowledge representation, and the RO-Crate community instead agreed on a dual lightweight approach: (i) [Document](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#adding-new-or-ad-hoc-vocabulary-terms) how projects with their own Web-presence can make a pure HTML-based vocabulary, and (ii) provide a community-wide PID namespace under `https://w3id.org/ro/terms` that redirect to simple CSV files [maintained in GitHub](https://github.com/ResearchObject/ro-terms). 

To further verify this idea of simplicity, we have formalised the RO-Crate definition (see Appendix on [Formal Definition](#formaldefinition)). An important result of this exercise is that the underlying data structure of RO-Crate, although conceptually a graph, is represented as a depth-limited tree. This formalisation also emphasises the _boundedness_ of the structure; namely, the fact that elements are specifically identified as being either semantically _contained_ by the RO-Crate as _Data Entities_ (`hasPart`) or mainly referenced (`mentions`) and typed as _external_ to the Research Object as _Contextual Entities_.  It is worth pointing out that this semantic containment can extend beyond the physical containment of files residing within the RO-Crate Root directory on a given storage system, as the RO-Crate data entities may include any data resource globally identifiable using IRIs.

#### Extensibility and RO-Crate profiles {#profiles}

The RO-Crate specification provides a core set of conventions to describe research outputs using types and properties applicable across scientific domains. However we have found that domain-specific use of RO-Crate will, implicitly or explicitly, form a specialised **profile** of RO-Crate; i.e., _a set of conventions, types and properties that are minimally required and one can expect to be present in that subset of RO-Crates_. For instance, RO-Crates used for exchange of workflows will have to contain a data entity of type `ComputationalWorkflow`, or cultural heritage records should have a `contentLocation`. 

Making such profiles explicit allow further reliable programmatic consumption and generation of RO-Crates beyond the core types defined in the RO-Crate specification. Following the RO-Crate mantra of _guidance over strictness_, profiles are mainly _duck-typing_ rather than strict syntactic or semantic types, but may also have corresponding machine-readable schemas at multiple levels (file formats, JSON, RDF shapes, RDFS/OWL semantics).

The next version of the RO-Crate specification 1.2 will define a [formalization](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles) for publishing and declaring conformance to RO-Crate profiles. Such a profile is primarily a human-readable document of before-mentioned expectations and conventions, but may also define a machine-readable profile as a **Profile Crate**: Another RO-Crate that describe the profile and in addition can list schemas for validation, compatible software, applicable repositories, serialization/packaging formats, extension vocabularies, custom JSON-LD contexts and examples (see for example the [Workflow RO-Crate profile](https://w3id.org/workflowhub/workflow-ro-crate/)).

In addition, there are sometimes existing domain-specific metadata formats, but they are either not RDF-based (and thus time-consuming to construct terms for in JSON-LD) or are at a different granularity level that might become overwhelming if represented directly in the RO-Crate Metadata file (e.g. W3C PROV bundle detailing every step execution of a workflow run [[68](https://doi.org/10.1093/gigascience/giz095)]). RO-Crate allows such _alternative metadata files_ to co-exist, and be described as data entities with references to the standards and vocabularies they conform to. This simplifies further programmatic consumption even where no filename or file extension conventions have emerged for those metadata formats.

Section on [in use](#inuse) examines the observed specializations of RO-Crate use in several domains and their emerging profiles.


### Technical implementation of the RO-Crate model {#implementation}

The RO-Crate conceptual model has been realised using JSON-LD and Schema.org in a prescriptive form as discussed in section on [conceptual definition](#conceptual). These technical choices were made to cater for simplicity from a developer perspective (as introduced in section on [methodology](#methodology)). 

[JSON-LD](https://json-ld.org/) [[112]](https://www.w3.org/TR/2014/REC-json-ld-20140116/) provides a way to express Linked Data as a JSON structure, where a _context_ provides mapping to RDF properties and classes. While JSON-LD cannot map arbitrary JSON structures to RDF, we found that it does lower the barrier compared to other RDF syntaxes, as the JSON syntax nowadays is a common and popular format for data exchange on the Web.

However, JSON-LD alone has too many degrees of freedom and hidden complexities for software developers to reliably produce and consume without specialised expertise or large RDF software frameworks.  A large part of the RO-Crate specification is therefore dedicated to describing the acceptable subset of JSON structures. 

#### RO-Crate JSON-LD {#jsonld}

RO-Crate [mandates](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html) the use of flattened, compacted JSON-LD in the RO-Crate Metadata file `ro-crate-metadata.json`[^4] where a single `@graph` array contains all the data and contextual entities in a flat list. An example can be seen in the JSON-LD snippet in Listing 1 below, describing a simple RO-Crate containing data entities described using contextual entities:

```json
{ "@context": "https://w3id.org/ro/crate/1.1/context",
  "@graph": [
      { "@id": "ro-crate-metadata.json",      
        "@type": "CreativeWork",
        "conformsTo": {"@id": "https://w3id.org/ro/crate/1.1"},
        "about": {"@id": "./"}
      },
      { "@id": "./",
        "@type": "Dataset",
        "name": "A simplified RO-Crate",
        "author": {"@id": "#alice"},
        "license": {"@id": "https://spdx.org/licenses/CC-BY-4.0"},
        "datePublished": "2021-11-02T16:04:43Z",
        "hasPart": [
          {"@id": "survey-responses-2019.csv"},
          {"@id": "https://example.com/pics/5707039334816454031_o.jpg"}
        ]
      },
      { "@id": "survey-responses-2019.csv",
        "@type": "File",
        "about": {"@id": "https://example.com/pics/5707039334816454031_o.jpg"},
        "author": {"@id": "#alice"}
      },
      { "@id": "https://example.com/pics/5707039334816454031_o.jpg",
        "@type": ["File", "ImageObject"],
        "contentLocation": {"@id": "http://sws.geonames.org/8152662/"},
        "author": {"@id": "https://orcid.org/0000-0002-1825-0097"}
      },
      { "@id": "#alice",
        "@type": "Person",
        "name": "Alice"
      },
      { "@id": "https://orcid.org/0000-0002-1825-0097",
        "@type": "Person",
        "name": "Josiah Carberry"
      },
      { "@id": "http://sws.geonames.org/8152662/",
        "@type": "Place",
        "name": "Catalina Park"
      },
      { "@id": "https://spdx.org/licenses/CC-BY-4.0",
        "@type": "CreativeWork",
        "name": "Creative Commons Attribution 4.0"
      }
  ]
}
```

**Listing 1**: Simplified[^5] RO-Crate metadata file showing the flattened compacted JSON-LD `@graph` array containing the data entities and contextual entities, cross-referenced using `@id`. The `ro-crate-metadata.json` entity self-declares conformance with the RO-Crate specification using a versioned persistent identifier, further RO-Crate descriptions are on the root data entity `./` or any of the referenced data or contextual entities. This is exemplified by the data entity `ImageObject` referencing contextual entities for `contentLocation` and `author` that differs from that of the overall RO-Crate. In this crate, `about` of the CSV data entity reference the `ImageObject`, which then take the roles of both a data entity and contextual entity. While `Person` entities ideally are identified with ORCID PIDs as for Josiah, `#alice` is here in contrast an RO-Crate local identifier, highlighting the pragmatic “just enough” Linked Data approach.
\normalsize

In this flattened profile of JSON-LD, each `{entity}` are directly under `@graph` and represents the RDF triples with a common _subject_ (`@id`), mapped _properties_ like `hasPart`, and _objects_ — as either literal `"string"` values, referenced `{objects}` (which properties are listed in its own entity), or a JSON `[list]` of these.  If processed as JSON-LD, this forms an RDF graph by matching the `@id` IRIs and applying the `@context` mapping to Schema.org terms. 
\normalsize

#### Flattened JSON-LD

When JSON-LD 1.0 [[112]](https://www.w3.org/TR/2014/REC-json-ld-20140116/) was proposed, one of the motivations was to seamlessly apply an RDF nature on top of regular JSON as frequently used by Web APIs. JSON objects in APIs are frequently nested with objects at multiple levels, and the perhaps most common form of JSON-LD is the [compacted form](https://json-ld.org/spec/REC/json-ld/20140116/#compacted-document-form) which follows this expectation ([JSON-LD 1.1](https://www.w3.org/TR/2020/REC-json-ld11-20200716/) further expands these capabilities, e.g. allowing nested `@context` definitions).  

While this feature of JSON-LD can be seen as a way to “hide” its RDF nature, we found that the use of nested trees (e.g. a `Person` entity appearing as `author` of a `File` which nests under a `Dataset` with `hasPart`) counter-intuitively forces consumers to consider the JSON-LD as an RDF Graph, since an identified `Person` entity can appear at multiple and repeated points of the tree (e.g. author of multiple files), necessitating node merging or duplication, which can become complicated as this approach also invites the use of _blank nodes_ (entities missing `@id`). 

By comparison, a single flat `@graph` array approach, as required by RO-Crate, means that applications can choose to process and edit each entity as pure JSON by a simple lookup based on `@id`. At the same time, lifting all entities to the same level reflects the Research Object principles [[12](https://www.research.manchester.ac.uk/portal/en/publications/why-linked-data-is-not-enough-for-scientists(479e591e-b295-4478-b0c7-a145c19dcd45).html)] in that describing the context and provenance is just as important as describing the data, and the requirement of `@id` of every entity forces RO-Crate generators to consciously [consider existing IRIs and identifiers](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#describing-entities-in-json-ld). 


#### JSON-LD context

In JSON-LD, the `@context` is a reference to another JSON-LD document that provides mapping from JSON keys to Linked Data term IRIs, and can enable various JSON-LD directives to cater for customised JSON structures for translating to RDF.

RO-Crate reuses vocabulary terms and IRIs from Schema.org, but provides its own versioned [JSON-LD context](https://w3id.org/ro/crate/1.1/context), which has a flat list with the mapping from JSON-LD keys to their IRI equivalents (e.g. key `"author"` maps to the <http://schema.org/author> property). 

The rationale behind this decision is to support JSON-based RO-Crate applications that are largely unaware of JSON-LD, that still may want to process the `@context` to find or add Linked Data definitions of otherwise unknown properties and types. Not reusing the official Schema.org context means RO-Crate is also able to map in additional vocabularies where needed, namely the _Portland Common Data Model_ (PCDM) [[31]](https://github.com/duraspace/pcdm/wiki) for repositories and Bioschemas [[58]](https://iswc2017.semanticweb.org/paper-579/) for describing computational workflows. RO-Crate profiles may [extend](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#extending-ro-crate) the `@context` to re-use additional domain-specific ontologies.

Similarly, while the Schema.org context [currently](https://schema.org/version/13.0/schemaorg-current-http.jsonld) have `"@type": "@id"` annotations for implicit object properties, RO-Crate JSON-LD distinguishes explicitly between references to other entities (`{"@id": "#alice"}`) and string values (`"Alice"`) — meaning RO-Crate applications can find references for corresponding entities and IRIs without parsing the `@context` to understand a particular property.  Notably this is exploited by the _ro-crate-html-js_
 [[95]](https://www.npmjs.com/package/ro-crate-html-js) tool to provide reliable HTML rendering for otherwise unknown properties and types.

[^4]: The avid reader may spot that the RO-Crate Metadata file use the extension `.json` instead of `.jsonld`, this is to emphasise the developer expectations as a JSON format, while the file's JSON-LD nature is secondary. See [ResearchObject/ro-crate#82](https://github.com/ResearchObject/ro-crate/issues/82).

[^5]: Recommended properties for types shown in Listing 1 also include `affiliation`, `citation`, `contactPoint`, `description`, `encodingFormat`,  `funder`, `geo`, `identifier`, `keywords`, `publisher`;  these properties and corresponding contextual entities are excluded here for brevity. See [complete example](https://www.researchobject.org/2021-packaging-research-artefacts-with-ro-crate/listing1/).


### RO-Crate Community {#community}

The RO-Crate conceptual model, implementation and best practices are developed by a growing community of researchers, developers and publishers. RO-Crate's community is a key aspect of its effectiveness in making research artefacts FAIR. Fundamentally, the community provides the overall context of the implementation and model and ensures its interoperability. 

The RO-Crate community consists of:

1. a diverse set of people representing a variety of stakeholders;
2. a set of collective norms;
3. an open platform that facilitates communication (GitHub, Google Docs, monthly teleconferences).

#### People

The initial concept of RO-Crate was formed at the first Workshop on Research Objects ([RO2018](https://www.researchobject.org/ro2018/)), held as part of the IEEE conference on eScience. This workshop followed up on considerations made at a [Research Data Alliance (RDA) meeting on Research Data Packaging](https://rd-alliance.org/approaches-research-data-packaging-rda-11th-plenary-bof-meeting) that found similar goals across multiple data packaging efforts [[23](https://doi.org/10.5281/zenodo.3250687)]: simplicity, structured metadata and the use of JSON-LD.

An important outcome of discussions that took place at RO2018 was the conclusion that the original Wf4Ever Research Object ontologies [[14](https://doi.org/10.1016/j.websem.2015.01.003)], in principle sufficient for packaging research artefacts with rich descriptions, were, in practice, considered inaccessible for regular programmers (e.g., Web developers) and in danger of being incomprehensible for domain scientists due to their reliance on Semantic Web technologies and other ontologies.

DataCrate [[103](https://doi.org/10.5281/zenodo.1445817)] was presented at RO2018 as a promising lightweight alternative approach, and an agreement was made by a group of volunteers to attempt building what was initially called _“RO Lite”_ as a combination of DataCrate's implementation and Research Object's principles.

This group, originally made up of library and Semantic Web experts, has subsequently grown to include domain scientists, developers, publishers and more. This perspective of multiple views led to the specification being used in a variety of domains, from bioinformatics and regulatory submissions to humanities and cultural heritage preservation. 

The RO-Crate community is strongly engaged with the European-wide biology/bioinformatics collaborative e-Infrastructure ELIXIR [[34](https://doi.org/10.1016/j.tibtech.2012.02.002)], along with [European Open Science Cloud](https://eosc.eu/) (EOSC) projects including [EOSC-Life](https://www.eosc-life.eu/), [FAIRplus](https://fairplus-project.eu/), [CS3MESH4EOSC](https://cs3mesh4eosc.eu/) and [BY-COVID](https://by-covid.eu/). RO-Crate has also established collaborations with Bioschemas [[58]](https://iswc2017.semanticweb.org/paper-579/), GA4GH [[99](https://doi.org/10.1016/j.xgen.2021.100029)],  OpenAIRE [[100]](https://doi.org/10.5860/crln.76.6.9326) and multiple H2020 projects.

A key set of stakeholders are developers: the RO-Crate community has made a point of attracting developers who can implement the specifications but, importantly, keeps “developer user experience” in mind. This means that the specifications are straightforward to implement and thus do not require expertise in technologies that are not widely deployed. 

This notion of catering to “developer user experience” is an example of the set of norms that have developed and now define the community. 


#### Norms

The RO-Crate community is driven by informal conventions and notions that are prevalent but not neccessarily written down. Here, we distil what we as authors believe are the critical set of norms that have facilitated the development of RO-Crate and contributed to the ability for RO-Crate research packages to be FAIR. This is not to say that there are no other norms within the community nor that everyone in the community holds these uniformly. Instead, what we emphasise is that these norms are helpful and also shaped by community practices. 

1. Simplicity
2. Developer friendliness
3. Focus on examples and best practices rather than rigorous specification
4. Reuse “just enough” Web standards

A core norm of RO-Crate is that of **simplicity**, which sets the scene for how we guide developers to structure metadata with RO-Crate. We focus mainly on documenting simple approaches to the most common use cases, such as authors having an affiliation. This norm also influences our take on **developer friendliness**; for instance, we are using the Web-native JSON format, allowing only a few of JSON-LD's flexible Linked Data features. Moreover, the RO-Crate documentation is largely built up by **examples** showcasing **best practices**, rather than rigorous specifications. We build on existing **Web standards** that themselves are defined rigorously, which we utilise _“**just enough**”_ in order to benefit from the advantages of Linked Data (e.g., extensions by namespaced vocabularies), without imposing too many developer choices or uncertainties (e.g., having to choose between the many RDF syntaxes). 

While the above norms alone could easily lead to the creation of “yet another” JSON format, we keep the goal of **FAIR interoperability** of the captured metadata, and therefore follow closely FAIR best practices and current developments such as data citations, PIDs, open repositories and recommendations for sharing research outputs and software.


#### Open Platforms

The critical infrastructure that enables the community around RO-Crate is the use of open development platforms. This underpins the importance of open community access to supporting FAIR. Specifically, it is difficult to build and consume FAIR research artefacts without being able to access the specifications, understand how they are developed, know about any potential implementation issues, and discuss usage to evolve best practices. 

The development of RO-Crate was driven by capturing documentation of real-life examples and best practices rather than creating a rigorous specification. At the same time, we agreed to be opinionated on the syntactic form to reduce the jungle of implementation choices; we wanted to keep the important aspects of Linked Data to adhere to the FAIR principles while retaining the option of combining and extending the structured metadata using the existing Semantic Web stack, not just build a standalone JSON format. 

Further work during 2019 started adapting the DataCrate documentation through a more collaborative and exploratory _RO Lite_ phase, initially using Google Docs for review and discussion, then moving to GitHub as a collaboration space for developing what is now the RO-Crate specification, [maintained](https://github.com/researchobject/ro-crate/) as Markdown in GitHub Pages and published through Zenodo. 

In addition to the typical Open Source-style development with GitHub issues and pull requests, the RO-Crate Community have, at time of writing, two regular monthly calls, a Slack channel and a mailing list for coordinating the project; also many of its participants collaborate on RO-Crate at multiple conferences and coding events such as the [ELIXIR BioHackathon](https://biohackathon-europe.org/). The community is jointly developing the RO-Crate specification and Open Source tools, as well as providing support and considering new use cases. The [RO-Crate Community](https://www.researchobject.org/ro-crate/community) is open for anyone to join, to equally participate under a code of conduct, and as of October 2021 has more than 50 members (see Appendix [RO-Crate Community](#communitylist)). 


## RO-Crate Tooling {#tooling}

The work of the community has led to the development of a number of tools for creating and using RO-Crates. Table 1 shows the current set of implementations. Reviewing this list, one can see support for commonly used programming languages, including Python, JavaScript, and Ruby. Additionally, the tools can be integrated into commonly used research environments, in particular, the command line tool *ro-crate-html-js* [[95]](https://www.npmjs.com/package/ro-crate-html-js) for creating a human-readable preview of an RO-Crate as a sidecar HTML file. Furthermore, there are tools that cater to end-users (*Describo* [[78]](https://arkisto-platform.github.io/describo/), *WorkflowHub* [[124]](https://w3id.org/workflowhub/)), in order to simplify creating and managing RO-Crate. For example, Describo was developed to help researchers of the Australian [Criminal Characters project](https://criminalcharacters.com/) to annotate historical prisoner records for greater insight into the history of Australia [[97](https://doi.org/10.1080/14490854.2020.1796500)]. 

While the development of these tools is promising, our analysis of their maturity status shows that the majority of them are in the Beta stage. This is partly due to the fact that the RO-Crate specification itself only recently reached 1.0 status, in November 2019 [[105](https://doi.org/10.5281/zenodo.3541888)]. Now that there is a fixed point of reference: With version 1.1 (October 2020) [[107](https://doi.org/10.5281/zenodo.4031327)] RO-Crate has stabilised based on feedback from application development, and now we are seeing a further increase in the maturity of these tools, along with the creation of new ones.

Given the stage of the specification, these tools have been primarily targeting developers, essentially providing them with the core libraries for working with RO-Crate. Another target has been that of research data managers who need to manage and curate large amounts of data. 


| Tool Name | Targets | Language /Platform | Status | Brief Description |
| --------  | ------  | ------------------  | -----  | ----------------  |
| Describo [[78]](https://arkisto-platform.github.io/describo/) | Research Data Managers | NodeJS (Desktop) | RC | Interactive desktop application to create, update and export RO-Crates for different profiles |
| Describo Online [[77]](https://arkisto-platform.github.io/describo-online/) | Platform developers | NodeJS (Web) | Alpha | Web-based application to create RO-Crates using cloud storage |
| ro-crate-excel [[84]](https://www.npmjs.com/package/ro-crate-excel) | Data managers | JavaScript | Beta | Command-line tool to create/edit RO-Crates with spreadsheets |
| ro-crate-html-js [[95]](https://www.npmjs.com/package/ro-crate-html-js) | Developers | JavaScript | Beta | HTML rendering of RO-Crate |
| ro-crate-js [[49]](https://github.com/UTS-eResearch/ro-crate-js) | Research Data Managers | JavaScript | Alpha | Library for creating/manipulating crates; basic validation code |
| ro-crate-ruby [[9]](https://github.com/ResearchObject/ro-crate-ruby) | Developers | Ruby | Beta | Ruby library for reading/writing RO-Crate, with workflow support |
| ro-crate-py [[41]](https://doi.org/10.5281/zenodo.3956493)) | Developers | Python | Alpha | Object-oriented Python library for reading/writing RO-Crate and use by Jupyter Notebook |
| WorkflowHub [[124]](https://w3id.org/workflowhub/) | Workflow users | Ruby | Beta | Workflow repository; imports and exports Workflow RO-Crate |
| Life Monitor [[35]](https://about.lifemonitor.eu/) | Workflow developers | Python | Alpha | Workflow testing and monitoring service; Workflow Testing profile of RO-Crate |
| SCHeMa [[118]](https://arxiv.org/abs/2103.13138v1) | Workflow users | PHP | Alpha | Workflow execution using RO-Crate as exchange mechanism [[10.5281/zenodo.4671709](https://doi.org/10.5281/zenodo.4671709)] |
| galaxy2cwl [[50]](https://github.com/workflowhub-eu/galaxy2cwl) | Workflow developers | Python | Alpha | Wraps Galaxy workflow as Workflow RO-Crate |
| Modern PARADISEC [[51]](https://github.com/CoEDL/modpdsc/) | Repository managers | Platform | Beta | Cultural Heritage portal based on OCFL and RO-Crate |
| ONI express [[115]](https://arkisto-platform.github.io/tools/portal/) | Repository managers | Platform | Beta | Platform for publishing data and documents stored in an OCFL repository via a Web interface |
| ocfl-tools [[52]](https://github.com/CoEDL/ocfl-tools) | Developers | JavaScript (CLI) | Beta | Tools for managing RO-Crates in an OCFL repository |
| RO Composer [[8]](https://esciencelab.org.uk/projects/ro-composer/) | Repository developers | Java | Alpha | REST API for gradually building ROs for given profile. |
| RDA maDMP Mapper [[7](https://doi.org/10.5281/zenodo.3922136)] | Data Management Plan users | Python | Beta | Mapping between machine-actionable data management plans (maDMP) and RO-Crate [[87](https://doi.org/10.4126/frl01-006423291)] |
| Ro-Crate_2_ma-DMP [[20](https://doi.org/10.5281/zenodo.3903463)] | Data Management Plan users | Python | Beta | Convert between machine-actionable data management plans (maDMP) and RO-Crate |
| CheckMyCrate [[13]](https://github.com/KockataEPich/CheckMyCrate) | Developers | Python (CLI) | Alpha | Validation according to Workflow RO-Crate profile |
| RO-Crates-and-Excel [[126](https://doi.org/10.5281/zenodo.5068950)] | Data Managers | Java (CLI) | Alpha | Describe column/data details of spreadsheets as RO-Crate using DataCube vocabulary | 

Table 1: Applications and libraries implementing RO-Crate, targeting different types of users across multiple programming languages. Status is indicative as assessed by this work (Alpha < Beta < Release Candidate (RC) < Release).

## Profiles of RO-Crate in use {#inuse}

RO-Crate fundamentally forms part of an infrastructure to help build FAIR research artefacts. In other words, the key question is whether RO-Crate can be used to share and (re)use research artefacts. Here we look at three research domains where RO-Crate is being applied: Bioinformatics, Regulatory Science and Cultural Heritage. In addition, we note how RO-Crate may have an important role as part of machine-actionable data management plans and institutional repositories.

From these varied uses of RO-Crate we observe natural differences in their detail level and the type of entities described by the RO-Crate. For instance, on submission of an RO-Crate to a workflow repository, it is reasonable to expect the RO-Crate to contain at least one workflow, ideally with a declared licence and workflow language. Specific additional recommendations such as on identifiers is also needed to meet the emerging requirements of [FAIR Digital Objects](https://fairdo.org/). [Work has now begun](https://github.com/ResearchObject/ro-crate/issues/153) to formalise these different _profiles_ of RO-Crates, which may impose additional constraints based on the needs of a specific domain or use case. 



### Bioinformatics workflows {#workflows}

[WorkflowHub.eu](https://workflowhub.eu/) is a European cross-domain registry of computational workflows, supported by European Open Science Cloud projects, e.g. [EOSC-Life](https://www.eosc-life.eu/), and research infrastructures including the pan-European bioinformatics network [ELIXIR](https://elixir-europe.org/) [[34](https://doi.org/10.1016/j.tibtech.2012.02.002)]. As part of promoting workflows as reusable tools, WorkflowHub includes documentation and high-level rendering of the workflow structure independent of its native workflow definition format. The rationale is that a domain scientist can browse all relevant workflows for their domain, before narrowing down their workflow engine requirements. As such, the WorkflowHub is intended largely as a registry of workflows already deposited in repositories specific to particular workflow languages and domains, such as UseGalaxy.eu [[10](https://doi.org/10.1371/journal.ppat.1008643)] and Nextflow nf-core [[45](https://doi.org/10.1038/s41587-020-0439-x)]. 

We here describe three different RO-Crate profiles developed for use with WorkflowHub.

#### Profile for describing workflows

Being cross-domain, WorkflowHub has to cater for many different workflow systems. Many of these, for instance Nextflow [[39](https://doi.org/10.1038/nbt.3820)] and Snakemake [[73](https://doi.org/10.1093/bioinformatics/bts480)], by virtue of their script-like nature, reference multiple neighbouring files typically maintained in a GitHub repository. This calls for a data exchange method that allows keeping related files together. WorkflowHub has tackled this problem by adopting RO-Crate as the packaging mechanism [[17](https://doi.org/10.5281/zenodo.4705078)], typing and annotating the constituent files of a workflow and — crucially — marking up the workflow language, as many workflow engines use common file extensions like `*.xml` and `*.json`. Workflows are further described with authors, license, diagram previews and a listing of their inputs and outputs. RO-Crates can thus be used for interoperable deposition of workflows to WorkflowHub, but are also used as an archive for downloading workflows, embedding metadata registered with the WorkflowHub entry and translated workflow files such as abstract Common Workflow Language (CWL) [[36](https://arxiv.org/abs/2105.07028)] definitions and diagrams [[56](https://doi.org/10.5281/zenodo.4605654)]. 

RO-Crate acts therefore as an interoperability layer between registries, repositories and users in WorkflowHub. The iterative development between WorkflowHub developers and the RO-Crate community heavily informed the creation of the Bioschemas [[58]](https://iswc2017.semanticweb.org/paper-579/) profile for [Computational Workflows](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE/), which again informed the [RO-Crate 1.1 specification on workflows](https://www.researchobject.org/ro-crate/1.1/workflows.html) and led to the RO-Crate Python library [[41]](https://doi.org/10.5281/zenodo.3956493) and WorkflowHub’s [**Workflow RO-Crate profile**](https://w3id.org/workflowhub/workflow-ro-crate/1.0), which, in a similar fashion to RO-Crate itself, recommends which workflow resources and descriptions are required. This co-development across project boundaries exemplifies the drive for simplicity and for establishing best practices.

#### Profile for recording workflow runs

RO-Crates in WorkflowHub have so far been focused on workflows that are ready to be run, and development of WorkflowHub is now creating a **Workflow Run RO-Crate profile** for the purposes of benchmarking, testing and executing workflows. As such, RO-Crate serves as a container of both a _workflow definition_ that may be executed and of a particular _workflow execution with test results_. 

This workflow run profile is a continuation of our previous work with capturing workflow provenance in a Research Object in CWLProv [[68](https://doi.org/10.1093/gigascience/giz095)] and TavernaPROV [[110](https://s11.no/2016/provweek-tavernaprov/)]. In both cases, we used the PROV Ontology [[81]](https://www.w3.org/TR/2013/REC-prov-o-20130430/), including details of every task execution with all the intermediate data, which required significant workflow engine integration.[^10] 

Simplifying from the CWLProv approach, the planned Workflow Run RO-Crate profile will use a high level [Schema.org provenance](https://www.researchobject.org/ro-crate/1.1/provenance.html#software-used-to-create-files) for the input/output boundary of the overall workflow execution. This _Level 1 workflow provenance_ [[68](https://doi.org/10.1093/gigascience/giz095)] can be expressed generally across workflow languages with minimal workflow engine changes, with the option of more detailed provenance traces as separate PROV artefacts in the RO-Crate as data entities. In the current development of [Specimen Data Refinery](https://github.com/DiSSCo/SDR) [[122](https://doi.org/10.3897/rio.6.e57602)] these RO-Crates will document the text recognition workflow runs of digitised biological specimens, exposed as FAIR Digital Objects [[38](https://doi.org/10.3390/publications8020021)]. 

WorkflowHub has recently enabled minting of Digital Object Identifiers (DOIs), a PID commonly used for scholarly artefacts, for registered workflows, e.g. `10.48546/workflowhub.workflow.56.1` [[83](https://doi.org/10.48546/workflowhub.workflow.56.1)], lowering the barrier for citing workflows as computational methods along with their FAIR metadata – captured within an RO-Crate. While it is not an aim for WorkflowHub to be a repository of workflow runs and their data, RO-Crates of *exemplar workflow runs* serve as useful workflow documentation, as well as being an exchange mechanism that preserves FAIR metadata in a diverse workflow execution environment.

[^10]:
    CWLProv and TavernaProv predate RO-Crate, but use RO-Bundle [[111](https://w3id.org/bundle/2014-11-05/)], a similar Research Object packaging method with JSON-LD metadata.  


#### Profile for testing workflows

The value of computational workflows, however, is potentially undermined by the "collapse" over time of the software and services they depend upon: for instance, software dependencies can change in a non-backwards-compatible manner, or active maintenance may cease; an external resource, such as a reference index or a database query service, could shift to a different URL or modify its access protocol; or the workflow itself may develop hard-to-find bugs as it is updated. This _workflow decay_ can take a big toll on the workflow's reusability and on the reproducibility of any processes it evokes [[125](https://www.research.manchester.ac.uk/portal/files/174861334/why_decay.pdf)].

For this reason, WorkflowHub is complemented by a monitoring and testing service called LifeMonitor [[35]](https://about.lifemonitor.eu/), also supported by EOSC-Life. LifeMonitor's main goal is to assist in the creation, periodic execution and monitoring of workflow tests, enabling the early detection of software collapse in order to minimise its detrimental effects. The communication of metadata related to workflow testing is achieved through the adoption of a [**Workflow Testing RO-Crate profile**](https://lifemonitor.eu/workflow_testing_ro_crate) stacked on top of the _Workflow RO-Crate_ profile. This further specialisation of Workflow RO-Crate allows to specify additional testing-related entities (test suites, instances, services, etc.), leveraging [RO-Crate's extension mechanism](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#extending-ro-crate) through the addition of terms from custom namespaces.

In addition to showcasing RO-Crate's extensibility, the testing profile is an example of the format's flexibility and adaptability to the different needs of the research community. Though ultimately related to a computational workflow, in fact, most of the testing-specific entities are more about describing a protocol for interacting with a monitoring service than a set of research outputs and its associated metadata. Indeed, one of LifeMonitor's main functionalities is monitoring and reporting on test suites running on existing Continuous Integration (CI) services, which is described in terms of service URLs and job identifiers in the testing profile. In principle, in this context, data could disappear altogether, leading to an RO-Crate consisting entirely of contextual entities. Such an RO-Crate acts more as an exchange format for communication between services (WorkflowHub and LifeMonitor) than as an aggregator for research data and metadata, providing a good example of the format's high versatility.



### Regulatory Sciences {#regulatorysciences}

[BioCompute Objects](https://biocomputeobject.org/) (BCO) [[5](https://doi.org/10.1371/journal.pbio.3000099)] is a community-led effort to standardise submissions of computational workflows to biomedical regulators. For instance, a genomics sequencing pipeline, as part of a personalised cancer treatment study, can be submitted to the US Food and Drugs Administration (FDA) for approval. BCOs are formalised in the standard IEEE 2791-2020 [[64](https://www.research.manchester.ac.uk/portal/en/publications/ieee-standard-for-bioinformatics-analyses-generated-by-highthroughput-sequencing-hts-to-facilitate-communication(936de52b-ac53-4f0e-9927-77fd7073e88d).html)] as a combination of [JSON Schemas](https://w3id.org/ieee/ieee-2791-schema/) that define the structure of JSON metadata files describing exemplar workflow runs in detail, covering aspects such as the usability and error domain of the workflow, its runtime requirements, the reference datasets used and representative output data produced.

BCOs provide a structured view over a particular workflow, informing regulators about its workings independently of the underlying workflow definition language. However, BCOs have only limited support for additional metadata.[^6] For instance, while the BCO itself can indicate authors and contributors, and in particular regulators and their review decisions, it cannot describe the provenance of individual data files or workflow definitions. 

As a custom JSON format, BCOs cannot be extended with Linked Data concepts, except by adding an additional top-level JSON object formalised in another JSON Schema. A BCO and workflow submitted by upload to a regulator will also frequently consist of multiple cross-related files. Crucially, there is no way to tell whether a given `*.json` file is a BCO file, except by reading its content and check for its `spec_version`. 

We can then consider how a BCO and its referenced artefacts can be packaged and transferred following FAIR principles. [**BCO RO-Crate**](https://biocompute-objects.github.io/bco-ro-crate/) [[109](https://doi.org/10.5281/zenodo.4633732)], part of the BioCompute Object user guides, defines a set of best practices for wrapping a BCO with a workflow, together with its exemplar outputs in an RO-Crate, which then provides typing and additional provenance metadata of the individual files, workflow definition, referenced data and the BCO metadata itself. 

Here the BCO is responsible for describing the _purpose_ of a workflow and its run at an abstraction level suitable for a domain scientist, while the more open-ended RO-Crate describes the surroundings of the workflow, classifying and relating its resources and providing provenance of their existence beyond the BCO. This emerging  _separation of concerns_ is shown in [Figure 3](#fig:sep_concerns), and highlights how RO-Crate is used side-by-side of existing standards and tooling, even where there are apparent partial overlaps. 

A similar separation of concerns can be found if considering the RO-Crate as a set of files, where the _transport-level_ metadata, such as checksum of files, are delegated to separate [BagIt](https://www.researchobject.org/ro-crate/1.1/appendix/implementation-notes.html#adding-ro-crate-to-bagit) manifests, a standard focusing on the preservation challenges of digital libraries [[74](https://doi.org/10.17487/rfc8493)]. As such, RO-Crate metadata files are not required to iterate all the files in their folder hierarchy, only those that benefit from being described.   

Specifically, a BCO description alone is insufficient for reliable re-execution of a workflow, which would need a compatible workflow engine depending on the original workflow definition language, so IEEE 2791 recommends using Common Workflow Language (CWL) [[36](https://arxiv.org/abs/2105.07028)] for interoperable pipeline execution. CWL itself relies on tool packaging in software containers using [Docker](https://www.docker.com/) or [Conda](https://docs.conda.io/). Thus, we can consider BCO RO-Crate as a stack: transport-level manifests of files (BagIt), provenance, typing and context of those files (RO-Crate), workflow overview and purpose (BCO), interoperable workflow definition (CWL) and tool distribution (Docker). 

[^6]: IEEE 2791-2020 do permit user extensions in the _extension domain_ by referencing additional JSON Schemas.


{{< figure src="ro-crate-bco-sep-of-concerns.svg" 
link="ro-crate-bco-sep-of-concerns.svg" 
id="fig:sep_concerns"
width="100%" title="Separation of Concerns in BCO RO-Crate"
caption="BioCompute Object (IEEE2791) is a JSON file that structurally explains the purpose and implementation of a computational workflow, for instance implemented in Common Workflow Language (CWL), that installs the workflow’s software dependencies as Docker containers or BioConda packages. An example execution of the workflow shows the different kinds of result outputs, which may be external, using GitHub LFS [[85]](https://docs.github.com/en/repositories/working-with-files/managing-large-files) to support larger data. RO-Crate gathers all these local and external resources, relating them and giving individual descriptions, for instance permanent DOI identifiers for reused datasets accessed from Zenodo, but also adding external identifiers to attribute authors using ORCID or to identify which licences apply to individual resources. The RO-Crate and its local files are captured in a BagIt whose checksum ensures completeness, combined with Big Data Bag [[25](https://www.research.manchester.ac.uk/portal/files/45989205/bagminid.pdf)] features to “complete” the bag with large external files such as the workflow outputs." >}}


### Digital Humanities: Cultural Heritage {#culturalheritage}

The Pacific And Regional Archive for Digital Sources in Endangered Cultures ([PARADISEC](https://www.paradisec.org.au/)) [[114](http://hdl.handle.net/10125/4567)] maintains a repository of more than 500,000 files documenting endangered languages across more than 16,000 items, collected and digitised over many years by researchers interviewing and recording native speakers across the region. 

The [Modern PARADISEC demonstrator](https://mod.paradisec.org.au/) has been [proposed](https://arkisto-platform.github.io/case-studies/paradisec/) as an update to the 18 year old infrastructure, to also help long-term preservation of these artefacts in their digital form. The demonstrator uses RO-Crate to describe the overall structure and to capture the metadata of each item. The existing PARADISEC data collection has been ported and captured as RO-Crates. A Web portal then exposes the repository and its entries by indexing the RO-Crate metadata files, presenting a domain-specific view of the items — the RO-Crate is “hidden” and does not change the user interface.

The PARADISEC use case takes advantage of several RO-Crate features and principles. Firstly, the transcribed metadata are now independent of the PARADISEC platform and can be archived, preserved and processed in its own right, using Schema.org as base vocabulary and extended with PARADISEC-specific terms. 

In this approach, RO-Crate is the holder of itemised metadata, stored in regular files that are organised using [Oxford Common File Layout](https://ocfl.io/1.0/spec/) (OCFL) [[96]](https://ocfl.io/1.0/spec/), which  ensures file integrity and versioning on a regular shared file system. This lightweight infrastructure also gives flexibility for future developments and maintenance. For example a consumer can use Linked Data software such as a graph database and query the whole corpora using SPARQL triple patterns across multiple RO-Crates. For long term digital preservation, beyond the lifetime of PARADISEC portals, a “last resort” fallback is storing the generic RO-Crate HTML preview [[95]](https://www.npmjs.com/package/ro-crate-html-js). Such human-readable rendering of RO-Crates can be hosted as static files by any Web server, in line with the approach taken by the Endings Project.[^3]

[^3]: The [Endings Project](https://endings.uvic.ca/) is a five-year project funded by the Social Sciences and Humanities Research Council (SSHRC) that is creating tools, principles, policies and recommendations for digital scholarship practitioners to create accessible, stable, long-lasting resources in the humanities.


### Machine-actionable Data Management Plans {#dmp}

Machine-actionable Data Management Plans (maDMPs) have been proposed as an improvement to automate FAIR data management tasks in research [[88](https://doi.org/10.1371/journal.pcbi.1006750)]; maDMPs use PIDs and controlled vocabularies to describe what happens to data over the research life cycle [[22](https://doi.org/10.1007/978-3-030-45442-5_15)]. The Research Data Alliance's _DMP Common Standard_ for maDMPs [[121](https://doi.org/10.15497/rda00039)] is one such formalisation for expressing maDMPs, which can be expressed as Linked Data using the DMP Common Standard Ontology [[21](https://doi.org/10.4126/frl01-006423289)], a specialisation of the W3C Data Catalog Vocabulary (DCAT) [[3]](https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/). RDA maDMPs are usually expressed using regular JSON, conforming to the DMP JSON Schema.

A mapping has been produced between Research Object Crates and Machine-actionable Data Management Plans [[87](https://doi.org/10.4126/frl01-006423291)], implemented by the RO-Crate RDA maDMP Mapper [[7](https://doi.org/10.5281/zenodo.3922136)]. A similar mapping has been implemented by _RO-Crate_2_ma-DMP_ [[20](https://doi.org/10.5281/zenodo.3903463)]. In both cases, a maDMP can be converted to a RO-Crate, or vice versa. In [[87](https://doi.org/10.4126/frl01-006423291)] this functionality caters for two use cases:

1. Start a skeleton data management plan based on an existing RO-Crate dataset, e.g. an RO-Crate from WorkflowHub.
2. Instantiate an RO-Crate based on a data management plan.

An important nuance here is that data management plans are (ideally) written in *advance* of data production, while RO-Crates are typically created to describe data *after* it has been generated. What is significant to note in this approach is the importance of **templating** in order to make both tasks automatable and achievable, and how RO-Crate can fit into earlier stages of the research life cycle.

### Institutional data repositories – Harvard Data Commons {#institutionalrepos}

The concept of a **Data Commons** for research collaboration was originally defined as _"cyber-infrastructure that co-locates data, storage, and computing infrastructure with commonly used tools for analysing and sharing data to create an interoperable resource for the research community"_ [[59](https://doi.org/10.1109/MCSE.2016.92)]. More recently, Data Commons has been established to mean integration of active data-intensive research with data management and archival best practices, along with a supporting computational infrastructure. Furthermore, the Commons features tools and services, such as computation clusters and storage for scalability, data repositories for disseminating and preserving regular, but also large or sensitive datasets, and other research assets. Multiple initiatives were undertaken to create Data Commons on national, research, and institutional levels. For example, the Australian Research Data Commons ([ARDC](https://ardc.edu.au)) [[11](https://doi.org/10.5334/dsj-2019-044)] is a national initiative that enables local researchers and industries to access computing infrastructure, training, and curated datasets for data-intensive research. NCI’s [Genomic Data Commons](https://gdc.cancer.gov/) (GDC) [[65](https://doi.org/10.1182/blood-2017-03-735654)] provides the cancer research community with access to a vast volume of genomic and clinical data. Initiatives such as [Research Data Alliance (RDA) Global Open Research Commons](https://www.rd-alliance.org/groups/global-open-research-commons-ig) propose standards for the implementation of Data Commons to prevent them becoming "data silos" and thus, enable interoperability from one Data Commons to another.

**Harvard Data Commons** [[33](https://doi.org/10.7557/5.5422)] aims to address the challenges of data access and cross-disciplinary research within a research institution. It brings together multiple institutional schools, libraries, computing centres and the [Harvard Dataverse](https://dataverse.harvard.edu/) data repository. [Dataverse](https://dataverse.org/) [[32](https://doi.org/10.1045/january2011-crosas)] is a free and open-source software platform to archive, share and cite research data. The Harvard Dataverse repository is the largest of 70 Dataverse installations worldwide, containing over 120K datasets with about 1.3M data files (as of 2021-11-16). Working toward the goal of facilitating collaboration and data discoverability and management within the university, Harvard Data Commons has the following primary objectives:

1. the integration of Harvard Research Computing with Harvard Dataverse by leveraging Globus endpoints [[27](https://doi.org/10.1109/MCC.2014.52)]; this will allow an automatic transfer of large datasets to the repository. In some cases, only the metadata will be transferred while the data stays stored in remote storage;
2. support for advanced research workflows and providing packaging options for assets such as code and workflows in the Harvard Dataverse repository to enable reproducibility and reuse, and 
3. interation of repositories supported by Harvard, which include [DASH](https://dash.harvard.edu/), the open access institutional repository, the Digital Repository Services (DRS) for preserving digital asset collections, and the Harvard Dataverse.

Particularly relevant to this article is the second objective of the Harvard Data Commons, which aims to support the deposit of research artefacts to Harvard Dataverse with sufficient information in the metadata to allow their future reuse ([Figure 4](#fig:hdc)). To support the incorporation of data, code, and other artefacts from various institutional infrastructures, Harvard Data Commons is currently working on RO-Crate adaptation. The RO-Crate metadata provides the necessary structure to make all research artefacts FAIR. The Dataverse software already has [extensive support for metadata](https://guides.dataverse.org/en/latest/user/appendix.html), including the Data Documentation Initiative (DDI), Dublin Core, DataCite, and Schema.org. Incorporating RO-Crate, which has the flexibility to describe a wide range of research resources, will facilitate their seamless transition from one infrastructure to the other within the Harvard Data Commons.

Even though the Harvard Data Commons is specific to Harvard University, the overall vision and the three objectives can be abstracted and applied to other universities or research organisations. The Commons will be designed and implemented using standards and commonly-used approaches to make it interoperable and reusable by others.

{{< figure src="data-commons-ro-crate-figure-5.svg"
 link="data-commons-ro-crate-figure-5.svg" width="100%" 
 id="fig:hdc" title="One aspect of Harvard Data Commons"
caption="Automatic encapsulation and deposit of artefacts from data management tools used during active research at the Harvard Dataverse repository." >}}


## Related Work {#relatedwork}

With the increasing digitisation of research processes, there has been a significant call for the wider adoption of interoperable sharing of data and its associated metadata. We refer to [[72](https://doi.org/10.1016/j.patter.2020.100136)] for a comprehensive overview and recommendations, in particular for data; notably that review highlights the wide variety of metadata and documentation that the literature prescribes for enabling data reuse. Likewise, we suggest [[82](https://doi.org/10.1016/j.patter.2021.100322)] that covers the importance of metadata standards in reproducible computational research.

Here we focus on approaches for bundling research artefacts along with their metadata. This notion of publishing compound objects for scholarly communication has a long history behind it [[29](https://doi.org/10.1190/1.1822162)] [[117]](http://icl.utk.edu/ctwatch/quarterly/articles/2007/08/interoperability-for-the-discovery-use-and-re-use-of-units-of-scholarly-communication/), but recent approaches have followed three main strands: 1) publishing to centralised repositories; 2) packaging approaches similar to RO-Crate; and 3) bundling the computational workflow around a scientific experiment.  


### Bundling and Packaging Digital Research Artefacts

Early work making the case for publishing compound scholarly communication units [[117]](http://icl.utk.edu/ctwatch/quarterly/articles/2007/08/interoperability-for-the-discovery-use-and-re-use-of-units-of-scholarly-communication/) led to the development of the [Object Re-Use and Exchange model](http://www.openarchives.org/ore/1.0/primer) (OAI-ORE), providing a structured **resource map** of the digital artefacts that together support a scholarly output. 

The challenge of describing computational workflows was one of the main motivations for the early proposal of _Research Objects_ (RO) [[12](https://www.research.manchester.ac.uk/portal/en/publications/why-linked-data-is-not-enough-for-scientists(479e591e-b295-4478-b0c7-a145c19dcd45).html)] as first-class citizens for sharing and publishing. The RO approach involves bundling datasets, workflows, scripts and results along with traditional dissemination materials like journal articles and presentations, forming a single package. Crucially, these resources are not just gathered, but also individually typed, described and related to each other using semantic vocabularies. As pointed out in [[12](https://doi.org/10.1016/j.future.2011.08.004)] an open-ended _Linked Data_ approach is not sufficient for scholarly communication: a common data model is also needed in addition to common and best practices for managing and annotating lifecycle, ownership, versioning and attributions.

Considering the FAIR principles [[123](https://doi.org/10.1038/sdata.2016.18)], we can say with hindsight that the initial RO approaches strongly targeted _Interoperability_, with a particular focus on the reproducibility of _in-silico experiments_ involving computational workflows and the reuse of existing RDF vocabularies. 

The first implementation of Research Objects for sharing workflows in myExperiment [[57](https://doi.org/10.1093/nar/gkq429)] was based on RDF ontologies [[93]](http://ceur-ws.org/Vol-523/Newman.pdf), building on Dublin Core, FOAF, SIOC, Creative Commons and OAI-ORE to form myExperiment ontologies for describing social networking, attribution and credit, annotations, aggregation packs, experiments, view statistics, contributions, and workflow components [[92]](https://web.archive.org/web/20091115080336/http%3a%2f%2frdf.myexperiment.org/ontologies).

This initially workflow-centric approach was further formalised as the Wf4Ever Research Object Model [[14](https://doi.org/10.1016/j.websem.2015.01.003)], which is a general-purpose research artefact description framework. This model is based on existing ontologies (FOAF, Dublin Core Terms, OAI-ORE and AO/OAC precursors to the W3C Web Annotation Model [[28]](https://www.w3.org/TR/2017/REC-annotation-model-20170223/)) and adds specializations for workflow models and executions using W3C PROV-O [[81]](https://www.w3.org/TR/2013/REC-prov-o-20130430/). The Research Object statements are saved in a _manifest_ (the OAI-ORE _resource map_), with additional annotation resources containing user-provided details such as title and description.

We now claim that one barrier for wider adoption of the Wf4Eer Research Object model for general packaging digital research artefacts was exactly this re-use of multiple existing vocabularies (FAIR principle I2: _Metadata use vocabularies that follow FAIR principles_), which in itself is recognized as a challenge [[67](https://doi.org/10.3233/978-1-61499-660-6-9)]. Adapters of the Wf4Ever RO model would have to navigate documentation of multiple overlapping ontologies, in addition to facing the usual Semantic Web development choices for RDF serialization formats, identifier minting and publishing resources on the Web.

Several developments for Research Objects improved on this situation, such as ROHub used by Earth Sciences [[48](https://arxiv.org/abs/1809.10617)], which provides a user-interface for making Research Objects, along with Research Object Bundle [[111](https://w3id.org/bundle/2014-11-05/)] (RO Bundle), which is a ZIP-archive embedding data files and a JSON-LD serialization of the manifest with mappings for a limited set of terms. RO Bundle was also used for storing detailed workflow run provenance (TavernaPROV [[110](https://s11.no/2016/provweek-tavernaprov/)]).

RO-Bundle evolved to [Research Object BagIt archives](https://w3id.org/ro/bagit), a variant of RO Bundle as a BagIt archive [[74](https://doi.org/10.17487/rfc8493)], used by Big Data Bags [[25](https://www.research.manchester.ac.uk/portal/files/45989205/bagminid.pdf)], CWLProv [[68](https://doi.org/10.1093/gigascience/giz095)] and WholeTale [[76](https://doi.org/10.3233/APC200107)] [[26](https://doi.org/10.1109/eScience.2019.00068)].  



### FAIR Digital Objects

FAIR Digital Objects (FDO) [[38](https://doi.org/10.3390/publications8020021)] have been proposed as a conceptual framework for making digital resources available in a Digital Objects (DO) architecture which encourages active use of the objects and their metadata. In particular, an FDO has five parts: (i) The FDO _content_, bit sequences stored in an accessible repository; (ii) a _Persistent Identifier_ (PID) such as a DOI that identifies the FDO and can resolve these same parts; (iii) Associated rich _metadata_, as separate FDOs; (iv) Type definitions, also separate FDOs; (v) Associated _operations_ for the given types. A Digital Object typed as a Collection aggregates other DOs by reference.

The Digital Object Interface Protocol [[47]](https://www.dona.net/sites/default/files/2018-11/DOIPv2Spec_1.pdf) can be considered an “abstract protocol” of requirements, DOs could be implemented in multiple ways. One suggested implementation is the [FAIR Digital Object Framework](https://fairdigitalobjectframework.org/), based on HTTP and the Linked Data Principles. While there is agreement on using PIDs based on DOIs, consensus on how to represent common metadata, core types and collections as FDOs has not yet been reached. We argue that RO-Crate can play an important role for FDOs:

1. By providing a predictable and extensible serialisation of structured metadata.
2. By formalising how to aggregate digital objects as collections (and adding their context).
3. By providing a natural Metadata FDO in the form of the RO-Crate Metadata File.
4. By being based on Linked Data and Schema.org vocabulary, meaning that PIDs already exist for common types and properties.

At the same time, it is clear that the goal of FDO is broader than that of RO-Crate; namely, FDOs are active objects with distributed operations, and add further constraints such as PIDs for every element. These features improve FAIR features of digital objects and are also useful for RO-Crate, but they also severely restrict the infrastructure that needs to be implemented and maintained in order for FDOs to remain accessible. RO-Crate, on the other hand, is more flexible: it can minimally be used within any file system structure, or ideally exposed through a range of Web-based scenarios. A _FAIR profile of RO-Crate_ (e.g. enforcing PID usage) will fit well within a FAIR Digital Object ecosystem.


### Packaging Workflows

The use of computational workflows, typically combining a chain of tools in an analytical pipeline, has gained prominence in particular in the life sciences. Workflows might be used primarily to improve computational scalability, as well as to assist in making computed data results FAIR [[55](https://doi.org/10.1162/dint_a_00033)], for instance by improving reproducibility [[30](https://doi.org/10.1016/j.future.2017.01.012)], but also because programmatic data usage help propagate their metadata and provenance [[69](https://doi.org/10.1002/cpe.1228)]. At the same time, workflows raise additional FAIR challenges, since they can be considered important research artefacts themselves. This viewpoint poses the problem of capturing and explaining the computational methods of a pipeline in sufficient machine-readable detail [[80](https://doi.org/10.3233/DS-190026)].

Even when researchers follow current best practices for workflow reproducibility [[60](https://doi.org/10.1016/j.cels.2018.03.014)] [[30](https://doi.org/10.1016/j.future.2017.01.012)], the communication of computational outcomes through traditional academic publishing routes effectively adds barriers as authors are forced to rely on a textual manuscript representations. This hinder reproducibility and FAIR use of the knowledge previously captured in the workflow.

As a real-life example, let us look at a metagenomics article [[4](https://doi.org/10.1038/s41586-019-0965-1)] that describes a computational pipeline. Here the authors have gone to extraordinary efforts to document the individual tools that have been reused, including their citations, versions, settings, parameters and combinations. The _Methods_ section is two pages in tight double-columns with twenty four additional references, supported by the availability of data on an FTP server (60 GB) [[43]](http://ftp.ebi.ac.uk/pub/databases/metagenomics/umgs_analyses/) and of open source code in GitHub [Finn-Lab/MGS-gut](https://github.com/Finn-Lab/MGS-gut) [[44]](https://github.com/Finn-Lab/MGS-gut), including the pipeline as shell scripts and associated analysis scripts in R and Python.

This attention to reporting detail for computational workflows is unfortunately not yet the norm, and although bioinformatics journals have strong _data availability_ requirements, they frequently do not require authors to include or cite _software, scripts and pipelines_ used for analysing and producing results [[108]](https://twitter.com/soilandreyes/status/1250721245622079488). Indeed, in the absence of a specific requirement and an editorial policy to back it up -- such as eliminating the reference limit -- authors are effectively discouraged from properly and comprehensively citing software [[53](https://doi.org/10.1038/s41592-019-0350-x)].

However detailed this additional information might be, another researcher who wants to reuse a particular computational method may first want to assess if the described tool or workflow is Re-runnable (executable at all), Repeatable (same results for original inputs on same platform), Reproducible (same results for original inputs with different platform or newer tools) and ultimately Reusable (similar results for different input data), Repurposable (reusing parts of the method for making a new method) or Replicable (rewriting the workflow following the method description) [[15](https://doi.org/10.3389/fninf.2017.00069)] [[54]](http://repscience2016.research-infrastructures.eu/img/CaroleGoble-ReproScience2016v2.pdf).

Following the textual description alone, researchers would be forced to jump straight to evaluate “Replicable” by rewriting the pipeline from scratch. This can be expensive and error-prone. They would firstly need to install all the software dependencies and download reference datasets. This can be a daunting task, which may have to be repeated multiple times as workflows typically are developed at small scale on desktop computers, scaled up to local clusters, and potentially put into production using cloud instances, each of which will have different requirements for software installations.

In recent years the situation has been greatly improved by software packaging and container technologies like Docker and Conda, these technologies have been increasingly adopted in life sciences [[90](https://doi.org/10.1007/s41019-017-0050-4)] thanks to collaborative efforts such as BioConda [[61](https://doi.org/10.1038/s41592-018-0046-7)] and BioContainers [[37](https://doi.org/10.1093/bioinformatics/btx192)], and support by Linux distributions (e.g. Debian Med [[89](https://doi.org/10.1186/1471-2105-11-S12-S5)]). As of November 2021, more than 9,000 software packages are available [in BioConda alone](https://anaconda.org/bioconda/), and 10,000 containers [in BioContainers](https://biocontainers.pro/#/registry). 

Docker and Conda have been integrated into workflow systems such as Snakemake [[73](https://doi.org/10.1093/bioinformatics/bts480)], Galaxy [[1](https://doi.org/10.1093/nar/gky379)] and Nextflow [[39](https://doi.org/10.1038/nbt.3820)], meaning a downloaded workflow definition can now be executed on a “blank” machine (except for the workflow engine) with the underlying analytical tools installed on demand. Even with using containers there is a reproducibility challenge, for instance [Docker Hub's retention policy will expire container images after six months](https://www.docker.com/blog/docker-hub-image-retention-policy-delayed-and-subscription-updates/), or a lack of recording versions of transitive dependencies of Conda packages could cause incompatibilities if the packages are subsequently updated. 

These container and package systems only capture small amounts of metadata[^11]. In particular, they do not capture any of the semantic relationships between their content. Understanding these relationships is made harder by the opaque wrapping of arbitrary tools with unclear functionality, licenses and attributions. 

From this we see that computational workflows are themselves complex digital objects that need to be recorded not just as files, but in the context of their execution environment, dependencies and analytical purpose in research – as well as other metadata (e.g. version, license, attribution and identifiers). 

It is important to note that having all these computational details in order to represent them in an RO-Crate is an ideal scenario -- in practice there will always be gaps of knowledge, and exposing all provenance details automatically would require improvements to the data sources, workflow, workflow engine and its dependencies. RO-Crate can be seen as a flexible annotation mechanism for augmenting automatic workflow provenance. Additional metadata can be added manually, e.g. for sensitive clinical data that cannot be publicly exposed[^24], or to cite software that lack persistent identifiers. This inline _FAIRifying_ allows researchers to achieve “just enough FAIR” to explain their computational experiments.

[^11]: Docker and Conda can use _build recipes_, a set of commands that construct the container image through downloading and installing its requirements. However these recipes are effectively another piece of software code, which may itself decay and become difficult to rerun.

[^24]: FAIR principle A2: _Metadata are accessible, even when the data are no longer available._ [[123](https://doi.org/10.1038/sdata.2016.18)]


## Conclusion

RO-Crate has been established as an approach to packaging digital research artefacts with structured metadata. This approach assists developers and researchers to produce and consume FAIR archives of their research. 

RO-Crate is formed by a set of best practice recommendations, developed by an open and broad community. These guidelines show how to use "just enough" standards in a consistent way. The use of structured metadata with a rich base vocabulary can cover general-purpose contextual relations, with a Linked Data foundation that ensures extensibility to domain- and application-specific uses.  We can therefore consider an RO-Crate not just as a structured data archive, but as a multimodal scholarly knowledge graph that can help "FAIRify" and combine metadata of existing resources. 

The adoption of simple Web technologies in the RO-Crate specification has helped a rapid development of a wide variety of supporting open source tools and libraries. RO-Crate fits into the larger landscape of open scholarly communication and FAIR Digital Object infrastructure, and can be integrated into data repository platforms. RO-Crate can be applied as a data/metadata exchange mechanism, assist in long-term archival preservation of metadata and data, or simply used at a small scale by individual researchers. Thanks to its strong community support, new and improved profiles and tools are being continuously added to the RO-Crate landscape, making it easier for adopters to find examples and support for their own use case.


### Strictness vs flexibility

There is always a tradeoff between flexibility and strictness [[116](https://www.persistent-identifier.nl/urn:nbn:nl:ui:18-14511] when deciding on semantics of metadata models. Strict requirements make it easier for users and code to consume and populate a model, by reducing choices and having mandated “slots” to fill in. But such rigidity can also restrict richness and applicability of the model, as it in turn enforce the initial assumptions about what can be described.

RO-Crate attempts to strike a balance between these tensions, and provides a common metadata framework that encourages extensions. However, just like the RO-Crate specification can be thought of as a _core profile_ of Schema.org in JSON-LD, we cannot stress the importance of also establishing domain-specific RO-Crate profiles and conventions, as explored in sections [extensibility](#profiles) and [profiles in use](#inuse). Specialization comes hand-in-hand with the principle of _graceful degradation_; RO-Crate applications and users are free to choose the semantic detail level they participate at, as long as they follow the common syntactic requirements. 

## Future Work {#futurework}

The direction of future RO-Crate work is determined by the community around it as a collaborative effort. We currently plan on further outreach, building training material (including a comprehensive entry-level tutorial) and maturing the reference implementation libraries. We will also collect and build examples of RO-Crate _consumption_, e.g. Jupyter Notebooks that query multiple crates using knowledge graphs. In addition, we are exploring ways to support some entity types requested by users, e.g. detailed workflow runs or container provenance, which do not have a good match in Schema.org. Such support could be added, for instance, by integrating other vocabularies or by having separated (but linked) metadata files. 

Furthermore, we want to better understand how the community uses RO-Crate in practice and how it contrasts with other related efforts; this will help us to improve our specification and tools. By discovering commonalities in emerging usage (e.g. additional Schema.org types), the community helps to reduce divergence that could otherwise occur with proliferation of further RO-Crate profiles. We plan to gather feedback via user studies, with the Linked Open Data community or as part of EOSC Bring-your-own-Data training events.

We operate in an open community where future and potential users of RO-Crate are actively welcomed to participate and contribute feedback and requirements. In addition, we are targeting a wider audience through extensive [outreach activities](https://www.researchobject.org/ro-crate/outreach.html) and by initiating new connections. Recent contacts include American Geophysical Union (AGU) on Data Citation Reliquary [[2](https://doi.org/10.5281/zenodo.4916734)],  National Institute of Standards and Technology (NIST) on material science, and [InvenioRDM](https://inveniosoftware.org/products/rdm/) used by the Zenodo data repository. New Horizon Europe projects adapting RO-Crate include [BY-COVID](https://by-covid.org/), which aims to improve FAIR access to data on COVID-19 and other infectious diseases. 

The main addition in the upcoming 1.2 release of the RO-Crate specifications will be the formalization of [profiles](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles) for different categories of crates. Additional entity types have been requested by users, e.g. workflow runs, business workflows, containers and software packages, tabular data structures; these are not always matched well with existing Schema.org types but may benefit from other vocabularies or even separate metadata files, e.g. from [Frictionless Data](https://frictionlessdata.io/). We will be further aligning and collaborating with related research artefact description efforts like [CodeMeta](https://codemeta.github.io/) for software metadata,  [Science-on-Schema.org](https://science-on-schema.org/) [[66](https://doi.org/10.5281/zenodo.4477164)] for datasets, [FAIR Digital Objects](https://fairdo.org/) [[38](https://doi.org/10.3390/publications8020021)] and activities in [EOSC task forces](https://www.eosc.eu/task-force-faq) including the EOSC Interoperability Framework [[75](https://doi.org/10.2777/620649)].

## Acknowledgements

This work has received funding from the European Commission's Horizon 2020 research and innovation programme for projects [BioExcel-2](https://cordis.europa.eu/project/id/823830) (H2020-INFRAEDI-2018-1 823830), [IBISBA 1.0](https://cordis.europa.eu/project/id/730976) (H2020-INFRAIA-2017-1-two-stage 730976), [PREP-IBISBA](https://cordis.europa.eu/project/id/871118) (H2020-INFRADEV-2019-2 871118), [EOSC-Life](https://cordis.europa.eu/project/id/824087) (H2020-INFRAEOSC-2018-2 824087), [SyntheSys+](https://cordis.europa.eu/project/id/823827) (H2020-INFRAIA-2018-1 823827). From the Horizon Europe Framework Programme this work has received funding for [BY-COVID](https://cordis.europa.eu/project/id/101046203) (HORIZON-INFRA-2021-EMERGENCY-01 101046203).

Björn Grüning is supported by DataPLANT ([NFDI 7/1 – 42077441](https://gepris.dfg.de/gepris/projekt/442077441)), part of the German National Research Data Infrastructure (NFDI), funded by the Deutsche Forschungsgemeinschaft (DFG).

Ana Trisovic is funded by the Alfred P. Sloan Foundation [(grant number P-2020-13988)](https://sloan.org/grant-detail/9555). Harvard Data Commons is supported by an award from Harvard University Information Technology (HUIT).


### Contributions

Author contributions to this article and the RO-Crate project according to the Contributor Roles Taxonomy [CASRAI CrEDiT](https://casrai.org/credit/) [[19](https://doi.org/10.1087/20150211)]:

Stian Soiland-Reyes
: Conceptualization, Data curation, Formal Analysis, Funding acquisition, Investigation, Methodology, Project administration, Software, Visualization, Writing – original draft, Writing – review \& editing

Peter Sefton
: Conceptualization, Investigation, Methodology, Project administration, Resources, Software, Writing – review \& editing

Mercè Crosas
: Writing – review \& editing

Leyla Jael Castro
: Methodology, Writing – review \& editing

Frederik Coppens
: Writing – review \& editing

José M. Fernández
: Methodology, Software, Writing – review \& editing

Daniel Garijo
: Methodology, Writing – review \& editing

Björn Grüning
: Writing – review \& editing

Marco La Rosa
: Software, Methodology, Writing – review \& editing

Simone Leo
: Software, Methodology, Writing – review \& editing

Eoghan Ó Carragáin
: Investigation, Methodology, Project administration, Writing – review \& editing

Marc Portier
: Methodology, Writing – review \& editing

Ana Trisovic
: Software, Writing – review \& editing

RO-Crate Community
: Investigation, Software, Validation, Writing – review \& editing

Paul Groth
: Methodology, Supervision, Writing – original draft, Writing – review \& editing

Carole Goble
: Conceptualization, Funding acquisition, Methodology, Project administration, Supervision, Visualization, Writing – review \& editing

  

We would also like to acknowledge contributions from:

Finn Bacall
: Software, Methodology

Herbert Van de Sompel
: Writing – review \& editing 

Ignacio Eguinoa
: Software, Methodology

Nick Juty
: Writing – review \& editing

Oscar Corcho
: Writing – review \& editing

Stuart Owen
: Writing – review \& editing

Laura Rodríguez-Navas
: Software, Visualization, Writing – review \& editing

Alan R. Williams
: Writing – review \& editing 


## Appendix A: Formalizing RO-Crate in First Order Logic {#formaldefinition}

Below is a formalization of the concept of RO-Crate as a set of relations using First Order Logic:

### Language


Definition of language `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊`:

```
𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊 = { Property(p), Class(c), Value(x), ℝ, 𝕊 }
     𝔻 =  𝕀𝕣𝕚
    𝕀𝕣𝕚 ≡  { IRIs as defined in RFC3987 }
     ℝ ≡  { real or integer numbers }
     𝕊 ≡  { literal strings }
```

The domain of discourse is the set of `𝕀𝕣𝕚` identifiers [[42](https://doi.org/10.17487/rfc3987)] (notation `<http://example.com/>`)[^9], with additional descriptions using numbers `ℝ` (notation `13.37`) and literal strings `𝕊` (notation `“Hello”`). 

From this formalised language `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊` we can interpret an RO-Crate in any representation that can gather these descriptions, their properties, classes, and literal attributes.  

### Minimal RO-Crate

Below we use `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊` to define a minimal[^8] RO-Crate:

```
                ROCrate(R) ⊨  Root(R) ∧ Mentions(R, R) ∧ hasPart(R, d) ∧ 
                               Mentions(R, d) ∧ DataEntity(d) ∧
                               Mentions(R, c) ∧ ContextualEntity(c)
               ∀r Root(r) ⇒  Dataset(r) ∧ name(r, n) ∧ 
                               description(r, d) ∧ 
                               datePublished(r, date) ∧
                               license(e, l)
          ∀e∀n name(e, n) ⇒  Value(n)
   ∀e∀s description(e, s) ⇒  Value(s)
 ∀e∀d datePublished(e, d) ⇒  Value(d)
       ∀e∀l license(e, l) ⇒  ContextualEntity(l)
             DataEntity(e) ≡  File(e) ⊕ Dataset(e)
                 Entity(e) ≡  DataEntity(e) ∨ ContextualEntity(e)
              ∀e Entity(e) ⇒ type(e, c) ∧ Class(c)
    ∀e ContextualEntity(e) ⇒ name(e, n)
            Mentions(R, s) ⊨  Relation(s, p, e)  ⊕  Attribute(s, p, l)
         Relation(s, p, o) ⊨  Entity(s) ∧ Property(p) ∧ Entity(o)
        Attribute(s, p, x) ⊨  Entity(s) ∧ Property(p) ∧ Value(x)
                  Value(x) ≡  x ∈ ℝ  ⊕  x ∈ 𝕊
```

An `ROCrate(R)` is defined as a self-described _Root Data Entity_, which describes and contains parts (_data entities_), which are further described in _contextual entities_.  These terms align with their use in the [RO-Crate 1.1 terminology](https://www.researchobject.org/ro-crate/1.1/terminology). 

The `Root(r)` is a type of `Dataset(r)`, and must as metadata have at least the attributes `name`, `description` and `datePublished`, as well as a contextual entity that identify its `license`. These predicates correspond to the RO-Crate 1.1 [minimal requirements for the root data entity](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html#direct-properties-of-the-root-data-entity).

The concept of an `Entity(e)` is introduced as being either a `DataEntity(e)`, a `ContextualEntity(e)`, or [both](https://www.researchobject.org/ro-crate/1.1/contextual-entities.html#contextual-vs-data-entities). Any `Entity(e)` must be typed with at least one `Class(c)`, and every `ContextualEntity(e)` must also have a `name(e,n)`; this corresponding to expectations for any _referenced contextual entity_ (see section on [contextual entities](#contextualentities)). 

For simplicity in this formalization (and to assist production rules below) `R` is a constant representing a single RO-Crate, typically written to independent RO-Crate Metadata files. `R` is used by `Mentions(R, e)` to indicate that `e` is an Entity described by the RO-Crate and therefore its metadata (a set of Relation and Attribute predicates) form part of the RO-Crate serialization. `Relation(s, p, o)` and `Attribute(s, p, x)` are defined as a _subject-predicate-object_ triple pattern from an `Entity(s)` using a `Property(p)` to either another `Entity(o)` or a `Literal(x)` value.


### Example of formalised RO-Crate 

The below is an example RO-Crate represented using the above formalization, assuming a base IRI of `http://example.com/ro/123/`:

```
RO-Crate(<http://example.com/ro/123/>)
name(<http://example.com/ro/123/, 
    “Data files associated with the manuscript:Effects of …”)
description(<http://example.com/ro/123/, 
    “Palliative care planning for nursing home residents …")
license(<http://example.com/ro/123/>, 
    <https://spdx.org/licenses/CC-BY-4.0>
datePublished(<http://example.com/ro/123/>, “2017")
hasPart(<http://example.com/ro/123/>, <http://example.com/ro/123/survey.csv>)
hasPart(<http://example.com/ro/123/>, <http://example.com/ro/123/interviews/>)

ContextualEntity(<https://spdx.org/licenses/CC-BY-4.0>)
name(<https://spdx.org/licenses/CC-BY-4.0, 
    “Creative Commons Attribution 4.0”)

ContextualEntity(<https://spdx.org/licenses/CC-BY-NC-4.0>)
name(<https://spdx.org/licenses/CC-BY-NC-4.0, 
    “Creative Commons Attribution Non Commercial 4.0”)

File(<http://example.com/ro/123/survey.csv>)
name(<http://example.com/ro/123/survey.csv>, “Survey of care providers”)

Dataset(<http://example.com/ro/123/interviews/>)
name(<http://example.com/ro/123/interviews/>, 
    “Audio recordings of care provider interviews”)
license(<http://example.com/ro/123/interviews/>, 
    <https://spdx.org/licenses/CC-BY-NC-4.0>

```

Notable from this triple-like formalization is that a RO-Crate R is fully represented as a tree at depth 2 helped by the use of `𝕀𝕣𝕚` nodes. For instance the aggregation from the root entity `hasPart(…interviews/>)` is at same level as the data entity’s property `license(…CC-BY-NC-4.0>)` and that contextual entity’s attribute name `(…Non Commercial 4.0”)`. As shown in section [RO-Crate JSON-LD](#jsonld), the RO-Crate Metadata File serialization is an equivalent shallow tree, although at depth 3 to cater for the JSON-LD preamble of `"@context"` and `"@graph"`.

In reality many additional attributes and contextual types from Schema.org types like <http://schema.org/affiliation> and <http://schema.org/Organization> would be used to further describe the RO-Crate and its entities, but as these are optional (_SHOULD_ requirements) they do not form part of this formalization.


### Mapping to RDF with Schema.org

A formalised RO-Crate can be mapped to different serializations. Assume a simplified[^7] language `𝕃ʀᴅꜰ` based on the RDF abstract syntax [98](https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/):

```
                𝕃𝖗𝖉𝖋 = { Triple(s,p,o), IRI(i), BlankNode(b), Literal(s),
                         𝕀𝕣𝕚, ℝ, 𝕊 }
                𝔻𝖗𝖉𝖋 = 𝕊
           ∀i IRI(i) ⇒ i ∈ 𝕀𝕣𝕚
∀s∀p∀o Triple(s,p,o) ⇒（ IRI(s) ∨ BlankNode(s) ）∧
                        IRI(p) ∧
                      （ IRI(o) ∨ BlankNode(o) ∨ Literal(o) ）
          Literal(v) ⊨ Value(v) ∧ Datatype(v,t) ∧ IRI(t)
         ∀v Value(v) ⇒ v ∈ 𝕊
    LanguageTag(v,l) ≡ Datatype(v,
          http://www.w3.org/1999/02/22-rdf-syntax-ns#langString)
```

Below follows a mapping from `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊` to `𝕃𝖗𝖉𝖋` using Schema.org.

```
        Property(p) ⇒ type(p,
             <http://www.w3.org/2000/01/rdf-schema#Property>)
           Class(c) ⇒ type(c,
             <http://www.w3.org/2000/01/rdf-schema#Class>)
         Dataset(d) ⇒ type(d, <http://schema.org/Dataset>)
            File(f) ⇒ type(f, <http://schema.org/MediaObject>)
ContextualEntity(e) ⇒ type(e, <http://schema.org/Thing>)
    CreativeWork(e) ⇒ ContextualEntity(e) ∧
                        type(e, <http://schema.org/CreativeWork>)
      hasPart(e, t) ⇒ Relation(e, <http://schema.org/hasPart>, t)
         name(e, n) ⇒ Attribute(e, <http://schema.org/name>, n)
  description(e, s) ⇒ Attribute(e, <http://schema.org/description>, s)
datePublished(e, d) ⇒ Attribute(e, <http://schema.org/datePublished>, d)
      license(e, l) ⇒ Relation(e, <http://schema.org/license>, l) ∧
                      CreativeWork(l)
         type(e, t) ⇒ Relation(e,
             <http://www.w3.org/1999/02/22-rdf-syntax-ns#type>, t) ∧
                      Class(t)
          String(s) ≡ Value(s) ∧  s ∈ 𝕊
          String(s) ⇒ Datatype(s, 
             <http://www.w3.org/2001/XMLSchema#string>)
         Decimal(d) ≡ Value(d) ∧  d ∈ ℝ
         Decimal(d) ⇒ Datatype(d,
             <http://www.w3.org/2001/XMLSchema#decimal>)
    Relation(s,p,o) ⇒ Triple(s,p,o) ∧ IRI(s) ∧ IRI(o)
   Attribute(s,p,o) ⇒ Triple(s,p,o) ∧ IRI(s) ∧ Literal(o)

```

Note that in the JSON-LD serialization of RO-Crate the expression of `Class` and `Property `is typically indirect: The JSON-LD `@context` maps to Schema.org IRIs, which, when resolved as Linked Data, embeds their formal definition as RDFa. Extensions may however include such term definitions directly in the RO-Crate.


### RO-Crate 1.1 Metadata File Descriptor

An important RO-Crate principle is that of being **self-described**. Therefore the serialization of the RO-Crate into a file should also describe itself in a [Metadata File Descriptor](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html#ro-crate-metadata-file-descriptor), indicating it is `about` (describing) the RO-Crate root data entity, and that it `conformsTo` a particular version of the RO-Crate specification:

```
               about(s,o) ⇒  Relation(s, <http://schema.org/about>, o)
          conformsTo(s,o) ⇒  Relation(s, 
                               <http://purl.org/dc/terms/conformsTo>, R)
MetadataFileDescriptor(m) ⇒ （ CreativeWork(m) ∧ about(m,R) ∧ ROCrate(R) ∧ 
                             conformsTo(m,
                               <https://w3id.org/ro/crate/1.1>) ）
```

Note that although the metadata file necessarily is an _information resource_ written to disk or served over the network (as JSON-LD), it is not considered to be a contained _part_ of the RO-Crate in the form of a _data entity_, rather it is described only as a _contextual entity_.

In the conceptual model the _RO-Crate Metadata File_ can be seen as the top-level node that describes the _RO-Crate Root_, however in the formal model (and the JSON-LD format) the metadata file descriptor is an additional contextual entity that is not affecting the depth-limit of the RO-Crate.


### Forward-chained Production Rules for JSON-LD

Combining the above predicates and Schema.org mapping with rudimentary JSON templates, these forward-chaining production rules can output JSON-LD according to the RO-Crate 1.1 specification[^2]:

```
 Mentions(R, s) ∧ Relation(s, p, o) ⇒  Mentions(R, o)
                             IRI(i) ⇒ "i"
                         Decimal(d) ⇒  d
                          String(s) ⇒ "s"
                     ∀e∀t type(e,t) ⇒  { "@id": s,
                                         "@type": t }
                                       }     
             ∀s∀p∀o Relation(s,p,o) ⇒  { "@id": s,
                                         p: { "@id": o }
                                       }     
            ∀s∀p∀v Attribute(s,p,v) ⇒  { "@id": s,
                                         p: v 
                                       }
                   ∀r∀c  ROCrate(R) ⇒  { "@graph": [ 
                                           Mentions(r, c)* 
                                         ]
                                       }
                                  R ⊨  <./>
                                  R ⇒ MetadataFileDescriptor(
                                        <ro-crate-metadata.json>) 
```

This exposes the first order logic domain of discourse of IRIs, with rational numbers and strings as their corresponding JSON-LD representation. These production rules first grow the graph of `R` by adding a transitive rule that anything described in `R` which is related to `o` means that `o` is also considered mentioned by the RO-Crate `R`. For simplicity this rule is one-way; in theory the JSON-LD graph can also contain free-standing contextual entities that have outgoing relations to data- and contextual entities, but these are proposed to be bound to the root data entity with Schema.org relation <http://schema.org/mentions>.

[^2]:
    Limitations: Contextual entities not related from the RO-Crate (e.g. using inverse relations to a data entity) would not be covered by the single direction `Mentions(R, s)` production rule; see [issue 122](https://github.com/ResearchObject/ro-crate/issues/122). The `datePublished(e, d)` rule do not include syntax checks for the ISO 8601 datetime format. Compared with RO-Crate examples, this generated JSON-LD does not use a `@context` as the IRIs are produced unshortened, a post-step could do JSON-LD Flattening with a versioned RO-Crate context. The `@type` expansion is included for clarity, even though this is also implied by the `type(e, t)` expansion to `Relation(e, xsd:type)`.

[^7]: This simplification and mapping does not cover the extensive list of literal datatypes built into RDF 1.1, only strings and decimal real numbers. Likewise, `LanguageTag` is deliberately not utillised below.

[^8]: The full list of types, relations and attribute properties from the RO-Crate specification are not included. Examples shown include `datePublished`, `CreativeWork` and `name`.

[^9]:
    For simplicity, blank nodes are not included in this formalization, as RO-Crate 
    [recommends the use of IRI identifiers](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#describing-entities-in-json-ld)


## Appendix B: RO-Crate Community {#communitylist}

As of 2021-10-04, the _RO-Crate_ Community members are:

* Peter Sefton <https://orcid.org/0000-0002-3545-944X> (co-chair)
* Stian Soiland-Reyes <https://orcid.org/0000-0001-9842-9718> (co-chair)
* Eoghan Ó Carragáin <https://orcid.org/0000-0001-8131-2150> (emeritus chair)
* Oscar Corcho <https://orcid.org/0000-0002-9260-0753>
* Daniel Garijo <https://orcid.org/0000-0003-0454-7145>
* Raul Palma <https://orcid.org/0000-0003-4289-4922>
* Frederik Coppens <https://orcid.org/0000-0001-6565-5145>
* Carole Goble <https://orcid.org/0000-0003-1219-2137>
* José María Fernández <https://orcid.org/0000-0002-4806-5140>
* Kyle Chard <https://orcid.org/0000-0002-7370-4805>
* Jose Manuel Gomez-Perez <https://orcid.org/0000-0002-5491-6431>
* Michael R Crusoe <https://orcid.org/0000-0002-2961-9670>
* Ignacio Eguinoa <https://orcid.org/0000-0002-6190-122X>
* Nick Juty <https://orcid.org/0000-0002-2036-8350>
* Kristi Holmes <https://orcid.org/0000-0001-8420-5254>
* Jason A. Clark <https://orcid.org/0000-0002-3588-6257>
* Salvador Capella-Gutierrez <https://orcid.org/0000-0002-0309-604X>
* Alasdair J. G. Gray <https://orcid.org/0000-0002-5711-4872>
* Stuart Owen <https://orcid.org/0000-0003-2130-0865>
* Alan R Williams <https://orcid.org/0000-0003-3156-2105>
* Giacomo Tartari <https://orcid.org/0000-0003-1130-2154>
* Finn Bacall <https://orcid.org/0000-0002-0048-3300>
* Thomas Thelen <https://orcid.org/0000-0002-1756-2128>
* Hervé Ménager <https://orcid.org/0000-0002-7552-1009>
* Laura Rodríguez-Navas <https://orcid.org/0000-0003-4929-1219>
* Paul Walk <https://orcid.org/0000-0003-1541-5631>
* brandon whitehead <https://orcid.org/0000-0002-0337-8610>
* Mark Wilkinson <https://orcid.org/0000-0001-6960-357X>
* Paul Groth <https://orcid.org/0000-0003-0183-6910>
* Erich Bremer <https://orcid.org/0000-0003-0223-1059>
* LJ Garcia Castro <https://orcid.org/0000-0003-3986-0510>
* Karl Sebby <https://orcid.org/0000-0001-6022-9825>
* Alexander Kanitz <https://orcid.org/0000-0002-3468-0652>
* Ana Trisovic <https://orcid.org/0000-0003-1991-0533>
* Gavin Kennedy <https://orcid.org/0000-0003-3910-0474>
* Mark Graves <https://orcid.org/0000-0003-3486-8193>
* Jasper Koehorst <https://orcid.org/0000-0001-8172-8981>
* Simone Leo <https://orcid.org/0000-0001-8271-5429>
* Marc Portier <https://orcid.org/0000-0002-9648-6484>
* Paul Brack <https://orcid.org/0000-0002-5432-2748>
* Milan Ojsteršek <https://orcid.org/0000-0003-1743-8300>
* Bert Droesbeke <https://orcid.org/0000-0003-0522-5674>
* Chenxu Niu <https://github.com/UstcChenxu>
* Kosuke Tanabe <https://orcid.org/0000-0002-9986-7223>
* Tomasz Miksa <https://orcid.org/0000-0002-4929-7875>
* Marco La Rosa <https://orcid.org/0000-0001-5383-6993>
* Cedric Decruw <https://orcid.org/0000-0001-6387-5988>
* Andreas Czerniak <https://orcid.org/0000-0003-3883-4169>
* Jeremy Jay <https://orcid.org/0000-0002-5761-7533>
* Sergio Serra <https://orcid.org/0000-0002-0792-8157>
* Ronald Siebes <https://orcid.org/0000-0001-8772-7904>
* Shaun de Witt <https://orcid.org/0000-0003-4196-3658>
* Shady El Damaty <https://orcid.org/0000-0002-2318-4477>
* Douglas Lowe <https://orcid.org/0000-0002-1248-3594>
* Sergio Serra <https://orcid.org/0000-0002-0792-8157>
* Xuanqi Li <https://orcid.org/0000-0003-1498-6205>


<hr />


## References

[1] Enis Afgan, Dannon Baker, Bérénice Batut, Marius van den Beek, Dave Bouvier, Martin Čech, John Chilton, Dave Clements, Nate Coraor, Björn A Grüning, Aysam Guerler, Jennifer Hillman-Jackson, Saskia Hiltemann, Vahid Jalili, Helena Rasche, Nicola Soranzo, Jeremy Goecks, James Taylor, Anton Nekrutenko, Daniel Blankenberg (2018):  
**The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2018 update**.  
_Nucleic Acids Research_ **46**(W1) W537–W544  
<https://doi.org/10.1093/nar/gky379>

[2] Deborah Agarwal, Carole Goble, Stian Soiland-Reyes, Ugis Sarkans, Daniel Noesgaard, Uwe Schindler, Martin Fenner, Paolo Manghi, Shelley Stall, Caroline Coward, Chris Erdmann (2021):  
**Data Citation Community of Practice – 8 June 2021 Workshop**.  
_Zenodo/AGU_  
<https://data.agu.org/DataCitationCoP/2nd-workshop-data-citation>  
<https://doi.org/10.5281/zenodo.4916734>

[3] R. Albertoni, D. Browning, S. Cox, A. Gonzalez Beltran, A. Perego, P. Winstanley and Dataset Exchange Working Group (2020):  
**Data Catalog Vocabulary (DCAT) – Version 2**.  
_W3C Recommendation_ (2020)  
<https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/>

[4] A. Almeida, A.L. Mitchell, M. Boland, S.C. Forster, G.B. Gloor, A. Tarkowska, T.D. Lawley and R.D. Finn (2019):  
**A new genomic blueprint of the human gut microbiota**.  
_Nature_ **568**(7753) 499–504.   
<https://doi.org/10.1038/s41586-019-0965-1>

[5] Gil Alterovitz, Dennis A Dean II, Carole Goble, Michael R Crusoe, Stian Soiland-Reyes, Amanda Bell, Anais Hayes, Anita Suresh, Charles Hadley S King IV, Dan Taylor, KanakaDurga Addepalli, Elaine Johanson, Elaine E Thompson, Eric Donaldson, Hiroki Morizono, Hsinyi Tsang, Jeet K Vora, Jeremy Goecks, Jianchao Yao, Jonas S Almeida, Jonathon Keeney, KanakaDurga Addepalli, Konstantinos Krampis, Krista Smith, Lydia Guo, Mark Walderhaug, Marco Schito, Matthew Ezewudo, Nuria Guimera, Paul Walsh, Robel Kahsay, Srikanth Gottipati, Timothy C Rodwell, Toby Bloom, Yuching Lai, Vahan Simonyan, Raja Mazumder (2018):  
**Enabling precision medicine via standard communication of HTS provenance, analysis, and results**.  
_PLOS Biology_ **16**(12):e3000099   
<https://doi.org/10.1371/journal.pbio.3000099>

[6] R.C. Amorim, J.A. Castro, J. Rocha da Silva and C. Ribeiro (2016):  
**A comparison of research data management platforms: Architecture, flexible metadata and interoperability**.  
_Universal Access in the Information Society_ **16** pp 851–862.   
<https://doi.org/10.1007/s10209-016-0475-y>

[7] G. Arfaoui and M. Jaoua (2020):  
**RO-Crate RDA maDMP Mapper**.  
_Zenodo_ <https://github.com/GhaithArf/ro-crate-rda-madmp-mapper>   
<https://doi.org/10.5281/zenodo.3922136>

[8] Finn Bacall, Stian Soiland-Reyes and M. Soares e Silva (2019):  
**eScienceLab: RO-Composer**.  
<https://esciencelab.org.uk/projects/ro-composer/> <https://github.com/ResearchObject/research-object-composer>

[9] Finn Bacall and M. Whitwell (2022):  
**GitHub – ResearchObject/ro-crate-ruby: A Ruby gem for creating, manipulating and reading RO-Crates**.  
<https://github.com/ResearchObject/ro-crate-ruby>

[10] D. Baker, M. van den Beek, D. Blankenberg, D. Bouvier, J. Chilton, N. Coraor, F. Coppens, I. Eguinoa, S. Gladman, B. Grüning, N. Keener, D. Larivière, A. Lonie, S. Kosakovsky Pond, W. Maier, A. Nekrutenko, J. Taylor and S. Weaver (2020):  
**No more business as usual: Agile and effective responses to emerging pathogen threats require open data and open analytics**.  
_PLOS Pathogens_ **16**(8):e1008643.   
<https://doi.org/10.1371/journal.ppat.1008643>

[11] M. Barker, R. Wilkinson and A. Treloar (2019):  
**The Australian Research Data Commons**, _Data Science Journal_ **18** (2019).   
<https://doi.org/10.5334/dsj-2019-044>

[12] S. Bechhofer, I. Buchan, D. De Roure, P. Missier, J. Ainsworth, J. Bhagat, P. Couch, D. Cruickshank, M. Delderfield, I. Dunlop, M. Gamble, D. Michaelides, S. Owen, D. Newman, S. Sufi and Carole Goble (2013):  
**Why Linked Data is not enough for scientists**.  
_Future Generation Computer Systems_ **29**(2), pp. 599–611.   
<https://doi.org/10.1016/j.future.2011.08.004>

[13] K. Belchev (2021):  
**KockataEPich/CheckMyCrate: A command line application for validating a RO-Crate object against a JSON profile**.  
_GitHub_.  
<https://github.com/KockataEPich/CheckMyCrate>

[14] K. Belhajjame, J. Zhao, D. Garijo, M. Gamble, K. Hettne, R. Palma, E. Mina, O. Corcho, J.M. Gómez-Pérez, S. Bechhofer, G. Klyne and Carole Goble (2015):  
**Using a suite of ontologies for preserving workflow-centric research objects**.  
_Web Semantics: Science, Services and Agents on the World Wide Web_ **32** pp. 16–42.   
<https://doi.org/10.1016/j.websem.2015.01.003>

[15] F.C.Y. Benureau and N.P. Rougier (2017):  
**Re-run, repeat, reproduce, reuse, replicate: Transforming code into scientific contributions**.  
_Frontiers in Neuroinformatics_ **11**:69.   
<https://doi.org/10.3389/fninf.2017.00069>

[16] H. Berman, K. Henrick, H. Nakamura and J.L. Markley (2007):  
**The worldwide Protein Data Bank (wwPDB): Ensuring a single, uniform archive of PDB data**.  
_Nucleic Acids Research_ **35**(Database issue) , D301–D303.   
<https://doi.org/10.1093/nar/gkl971>

[17] F. Bietrix, J.M. Carazo, S. Capella-Gutierrez, F. Coppens, M.L. Chiusano, R. David, J.M. Fernandez, M. Fratelli, J.-K. Heriche, Carole Goble, P. Gribbon, P. Holub, R.P. Joosten, S. Leo, S. Owen, H. Parkinson, R. Pieruschka, L. Pireddu, L. Porcu, M. Raess, L. Rodriguez- Navas, A. Scherer, Stian Soiland-Reyes and J. Tang (2021):  
**EOSC-life methodology framework to enhance reproducibility within EOSC-life**.  
_Zenodo_. <https://doi.org/10.5281/zenodo.4705078>

[18] C. Bizer, T. Heath and T. Berners-Lee (2011):  
**Linked data: The story so far**.  
In _Semantic Services, Interoperability and Web Applications: Emerging Concepts_, A. Sheth, ed., IGI Global, 2011, pp. 205–227. ISBN 9781609605933.   
<https://doi.org/10.4018/978-1-60960-593-3.ch008>

[19] A. Brand, L. Allen, M. Altman, M. Hlava and J. Scott (2015):  
**Beyond authorship: Attribution, contribution, collaboration, and credit**.  
_Learned Publishing_ **28**(2) pp. 151–155.   
<https://doi.org/10.1087/20150211>

[20] G. Brenner (2020):  
**BrennerG/Ro-Crate\_2\_ma-DMP: v1.0.0**.  
<https://github.com/BrennerG/Ro-Crate_2_ma-DMP>  
<https://doi.org/10.5281/zenodo.3903463>

[21] J. Cardoso, L.J. Garcia Castro, F. Ekaputra, M.-C. Jacquemot-Perbal, T. Miksa and J. Borbinha (2020):  
**Towards Semantic Representation of Machine-Actionable Data Management Plans**.  
_PUBLISSO_.  
<https://repository.publisso.de/resource/frl:6423289>   
<https://doi.org/10.4126/frl01-006423289>

[22] J. Cardoso, D. Proença and J. Borbinha (2020):  
**Machine-actionable data management plans: A knowledge retrieval approach to automate the assessment of funders’ requirements**.  
in: _Advances in Information Retrieval_, J.M. Jose, E. Yilmaz, J. Magalhães, P. Castells, N. Ferro, M.J. Silva and F. Martins (eds.). ISBN 978-3-030-45442-5.   
<https://doi.org/10.1007/978-3-030-45442-5_15>

[23] Eoghan Ó Carragáin, Carole Goble, Peter Sefton, Stian Soiland-Reyes (2019):  
**A lightweight approach to research object data packaging**.  
_Bioinformatics Open Source Conference (BOSC2019)_, 2019-07-24/2019-07-25, Basel, Switzerland.  
_Zenodo_.   
<https://doi.org/10.5281/zenodo.3250687>

[24] L.M. Chan (1995):  
**Library of Congress Subject Headings: Principles and Application**, 3rd edn, p. 556. <https://eric.ed.gov/?id=ED387146>.  
[ISBN 9781563081910](https://identifiers.org/isbn/9781563081910).

[25] K. Chard, M. D’Arcy, B. Heavner, I. Foster, C. Kesselman, R. Madduri, A. Rodriguez, Stian Soiland-Reyes, Carole Goble, K. Clark, E.W. Deutsch, I. Dinov, N. Price and A. Toga (2016):  
**I’ll take that to go: Big data bags and minimal identifiers for exchange of large, complex datasets**.  
_2016 IEEE International Conference on Big Data (Big Data)_, IEEE, pp. 319–328.  
ISBN 978-1-4673-9005-7.   
<https://static.aminer.org/pdf/fa/bigdata2016/BigD418.pdf>  
<https://doi.org/10.1109/BigData.2016.7840618>

[26] K. Chard, N. Gaffney, M.B. Jones, K. Kowalik, B. Ludascher, T. McPhillips, J. Nabrzyski, V. Stodden, I. Taylor, T. Thelen, M.J. Turk and C. Willis (2019):  
**Application of BagIt-serialized research object bundles for packaging and re-execution of computational analyses**.  
_15th International Conference on eScience (eScience 2019)_, IEEE, pp. 514–521.  
ISBN 978-1-7281-2451-3.   
<https://zenodo.org/record/3381754>  
<https://doi.org/10.1109/eScience.2019.00068>

[27] K. Chard, S. Tuecke and I. Foster (2014):  
**Efficient and secure transfer, synchronization, and sharing of big data**.  
_IEEE Cloud Computing_ **1**(3) pp. 46–55.   
<https://doi.org/10.1109/MCC.2014.52>

[28] P. Ciccarese, R. Sanderson and B. Young (2017):  
**Web Annotation Data Model**.   
_W3C Recommendation_, W3C.  
<https://www.w3.org/TR/2017/REC-annotation-model-20170223/>

[29] J.F. Claerbout and M. Karrenbach (1992):  
**Electronic documents give reproducible research a new meaning**.  
_SEG Technical Program Expanded Abstracts 1992_, Society of Exploration Geophysicists, pp. 601–604.   
<https://doi.org/10.1190/1.1822162>

[30] S. Cohen-Boulakia, K. Belhajjame, O. Collin, J. Chopard, C. Froidevaux, A. Gaignard, K. Hinsen, P. Larmande, Y.L. Bras, F. Lemoine, F. Mareuil, H. Ménager, C. Pradal and C. Blanchet (2017):  
**Scientific workflows for computational reproducibility in the life sciences: Status, challenges and opportunities**.  
_Future Generation Computer Systems_ **75** pp. 284–298.   
<https://doi.org/10.1016/j.future.2017.01.012>

[31] S. Cossu, E. Cowles, K. Estlund, C. Harlow, T. Johnson, M. Matienzo, D. Lamb, L. Rayle, R. Sanderson, J. Stroop and A. Woods (2018):  
**Portland Common Data Model**.  
<https://github.com/duraspace/pcdm/wiki>

[32] M. Crosas (2011):  
**The DataVerse Network: An open-source application for sharing, discovering and preserving data**.  
_D-Lib Magazine_ **17**(1/2)a   
<https://doi.org/10.1045/january2011-crosas>

[33] M. Crosas (2020):  
**Harvard Data Commons**.  
_European Dataverse Workshop 2020_, Tromsø, Norway. ISSN 2387-3086.   
<https://doi.org/10.7557/5.5422>

[34] L.C. Crosswell and J.M. Thornton (2012):  
**ELIXIR: A distributed infrastructure for European biological data**.  
_Trends in Biotechnology_ **30**(5) pp. 241–242.   
<https://doi.org/10.1016/j.tibtech.2012.02.002>

[35] CRS4 (2022):  
**LifeMonitor, a testing and monitoring service for scientific workflows**.  
<https://about.lifemonitor.eu/>

[36] M.R. Crusoe, S. Abeln, A. Iosup, P. Amstutz, J. Chilton, N. Tijanić, H. Ménager, Stian Soiland-Reyes and Carole Goble (2022):  
**Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language**.  
_Communications of the ACM_, accepted. <https://arxiv.org/abs/2105.07028>   
<https://doi.org/10.1145/3486897>

[37] F. da Veiga Leprevost, B.A. Grüning, S. Alves Aflitos, H.L. Röst, J. Uszkoreit, H. Barsnes, M. Vaudel, P. Moreno, L. Gatto, J. Weber, M. Bai, R.C. Jimenez, T. Sachsenberg, J. Pfeuffer, R. Vera Alvarez, J. Griss, A.I. Nesvizhskii and Y. Perez-Riverol (2017):  
**BioContainers: An open-source and community-driven framework for software standardization**.  
_Bioinformatics_ **33**(16) pp. 2580–2582.   
<https://doi.org/10.1093/bioinformatics/btx192>

[38] K. De Smedt, D. Koureas and P. Wittenburg (2020):  
**FAIR digital objects for science: From data pieces to actionable knowledge units**.  
_Publications_ **8**(2):21   
<https://doi.org/10.3390/publications8020021>

[39] P. Di Tommaso, M. Chatzou, E.W. Floden, P.P. Barja, E. Palumbo and C. Notredame (2017):  
**Nextflow enables reproducible computational workflows**.  
_Nature Biotechnology_ **35**(4) (2017), 316–319.   
<https://doi.org/10.1038/nbt.3820>

[40] M. Dillen, Q. Groom, D. Agosti and L. Nielsen (2019):  
**Zenodo, an archive and publishing repository: A tale of two herbarium specimen pilot projects**.  
_Biodiversity Information Science and Standards_ **3**:e37080 (2019).   
<https://doi.org/10.3897/biss.3.37080>

[41] B. Droesbeke, I. Eguinoa, A. Gaignard, L. Simone, L. Pireddu, L. Rodríguez-Navas and Stian Soiland-Reyes (2022):  
**GitHub – ResearchObject/ro-crate-py: Python library for RO-Crate**.  
<https://github.com/researchobject/ro-crate-py>  
<https://doi.org/10.5281/zenodo.3956493>

[42] M. Duerst and M. Suignard (2005):  
**Internationalized resource identifiers (IRIs)**.  
RFC 3987, _Internet Requests for Comments_, RFC Editor, (2005).   
<https://doi.org/10.17487/rfc3987>

[43] EMBL-EBI Microbiome Informatics Team (2019):  
**FTP index of /pub/databases/metagenomics/umgs\_analyses/**.  
<http://ftp.ebi.ac.uk/pub/databases/metagenomics/umgs_analyses/>

[44] EMBL-EBI Microbiome Informatics Team (2020):  
**GitHub – Finn-Lab/MGS-gut: Analysing Metagenomic Species (MGS)**.  
<https://github.com/Finn-Lab/MGS-gut>

[45] P.A. Ewels, A. Peltzer, S. Fillinger, H. Patel, J. Alneberg, A. Wilm, M.U. Garcia, P. Di Tommaso and S. Nahnsen (2020):  
**The nf-core framework for community-curated bioinformatics pipelines**.  
_Nature Biotechnology_ **38**(3), 276–278.   
<https://doi.org/10.1038/s41587-020-0439-x>

[46] S. Farnel and A. Shiri (2014):  
**Metadata for research data: Current practices and trends**.  
_2014 Proceedings of the International Conference on Dublin Core and Metadata Applications_, W. Moen and A. Rushing, eds, Dublin Core Metadata Initiative, ISSN 1939-1366.  
<https://dcpapers.dublincore.org/pubs/article/view/3714>.

[47] D. Foundation (2018):  
***Digital Object Interface Protocol Specification, version 2.0**.  
Technical Report.  
<https://www.dona.net/sites/default/files/2018-11/DOIPv2Spec_1.pdf>

[48] A. Garcia-Silva, J.M. Gomez-Perez, R. Palma, M. Krystek, S. Mantovani, F. Foglini, V. Grande, F. De Leo, S. Salvi, E. Trasatti, V. Romaniello, M. Albani, C. Silvagni, R. Leone, F. Marelli, S. Albani, M. Lazzarini, H.J. Napier, H.M. Glaves, T. Aldridge, C. Meertens, F. Boler, H.W. Loescher, C. Laney, M.A. Genazzio, D. Crawl and I. Altintas (2019):  
**Enabling FAIR research in Earth science through research objects**.  
_Future Generation Computer Systems_ **98** pp. 550–564.  
<https://arxiv.org/abs/1809.10617>   
<https://doi.org/10.1016/j.future.2019.03.046>

[49] P. Sefton, M. Lynch, Stian Soiland-Reyes (2021):  
**GitHub – UTS-eResearch/ro-crate-js: Research Object Crate (RO-Crate) utilities**.  
<https://github.com/UTS-eResearch/ro-crate-js>

[50] Ignacio Eguinoa, Stian Soiland-Reyes, Bert Droesbeke, Michael .R. Crusoe (2020):  
**GitHub – workflowhub-eu/galaxy2cwl: Standalone version tool to get cwl descriptions (initially an abstract cwl interface) of galaxy workflows and Galaxy workflows executions**.  
<https://github.com/workflowhub-eu/galaxy2cwl>

[51] Marco La Rosa (2021):  
**GitHub – CoEDL/modpdsc**, <https://github.com/CoEDL/modpdsc/>

[52] Marco La Rosa (2021):  
**GitHub – CoEDL/ocfl-tools: Tools to process and manipulate an OCFL tree**.  
<https://github.com/CoEDL/ocfl-tools>

[53] **Giving software its due**.  
_Nature Methods_ **16**(3) (2019), 207–207.   
<https://doi.org/10.1038/s41592-019-0350-x>

[54] Carole Goble (2016):  
**What Is Reproducibility? The R\* Brouhaha**.  
_SciRepro Workshop_, TPDL, Hannover, Germany, 2016. <http://repscience2016.research-infrastructures.eu/img/CaroleGoble-ReproScience2016v2.pdf>

[55] Carole Goble, S. Cohen-Boulakia, Stian Soiland-Reyes, D. Garijo, Y. Gil, M.R. Crusoe, K. Peters and D. Schober (2019):  
**FAIR Computational Workflows**.  
_Data Intelligence_ **2**(1–2) pp. 108–121.   
<https://doi.org/10.1162/dint_a_00033>

[56] Carole Goble, Stian Soiland-Reyes, Finn Bacall, S. Owen, A. Williams, I. Eguinoa, B. Droesbeke, S. Leo, L. Pireddu, L. Rodríguez-Navas, J.M. Fernández, S. Capella-Gutierrez, H. Ménager, B. Grüning, B. Serrano-Solano, P. Ewels and F. Coppens (2021):  
**Implementing FAIR digital objects in the EOSC-life workflow collaboratory**.  
_Zenodo_. <https://doi.org/10.5281/zenodo.4605654>

[57] Carole A. Goble, J. Bhagat, S. Aleksejevs, D. Cruickshank, D. Michaelides, D. Newman, M. Borkum, S. Bechhofer, M. Roos, P. Li and D. De Roure (2010):  
**myExperiment: A repository and social network for the sharing of bioinformatics workflows**.  
_Nucleic Acids Research_ **38**(Web Server issue) W677–W682.   
<https://doi.org/10.1093/nar/gkq429>

[58] A. Gray, Carole Goble and R. Jimenez, Bioschemas Community (2017):  
**Bioschemas: From Potato Salad to Protein Annotation**.  
_ISWC_, Vienna, Austria. <https://iswc2017.semanticweb.org/paper-579/>

[59] R.L. Grossman, A. Heath, M. Murphy, M. Patterson and W. Wells (2016):  
**A case for data commons: Toward data science as a service**.  
_Computing in Science & Engineering_ **18**(5) pp. 10–20.   
<https://doi.org/10.1109/MCSE.2016.92>

[60] B. Grüning, J. Chilton, J. Köster, R. Dale, N. Soranzo, M. van den Beek, J. Goecks, R. Backofen, A. Nekrutenko and J. Taylor (2018):  
**Practical computational reproducibility in the life sciences**.  
_Cell Systems_ **6**(6) pp. 631–635.   
<https://doi.org/10.1016/j.cels.2018.03.014>

[61] B. Grüning, R. Dale, A. Sjödin, B.A. Chapman, J. Rowe, C.H. Tomkins-Tinch, R. Valieris, J. Köster and Bioconda Team (2018):  
**Bioconda: Sustainable and comprehensive software distribution for the life sciences**.  
_Nature Methods_ **15**(7) pp. 475–476.   
<https://doi.org/10.1038/s41592-018-0046-7>

[62] R.V. Guha, D. Brickley and S. Macbeth (2015):  
**Schema.org: Evolution of Structured Data on the Web: Big data makes common schemas even more necessary**.  
_Queue_ **13**(9) pp. 10–37.   
<https://doi.org/10.1145/2857274.2857276>

[63] T. Heath and C. Bizer (2011):  
**Linked Data: Evolving the Web into a Global Data Space**.  
_Synthesis Lectures on the Semantic Web: Theory and Technology_ **1** pp. 1–136, ISSN 2160-4711. ISBN 9781608454310 / ISBN 9781608454303. <https://identifiers.org/isbn/9781608454303>   
<https://doi.org/10.2200/S00334ED1V01Y201102WBE001>

[64] **IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication**.  
_IEEE Std_ **2791-2020**.  
ISBN 978-1-5044-6466-6. <https://www.research.manchester.ac.uk/portal/en/publications/ieee-2791(936de52b-ac53-4f0e-9927-77fd7073e88d).html>   
<https://doi.org/10.1109/IEEESTD.2020.9094416>

[65] M.A. Jensen, V. Ferretti, R.L. Grossman and L.M. Staudt (2017):  
**The NCI Genomic Data Commons as an engine for precision medicine**.  
_Blood_ **130**(4) pp. 453–459.   
<https://doi.org/10.1182/blood-2017-03-735654>

[66] M.B. Jones, S. Richard, D. Vieglais, A. Shepherd, R. Duerr, D. Fils and L. McGibbney (2021):  
**Science-on-Schema.org v1.2.0**   
<https://doi.org/10.5281/zenodo.4477164>

[67] M. Katsumi and M. Grüninger (2016):  
**What is ontology reuse?**.  
In: _Formal Ontology in Information Systems_, R. Ferrario and W. Kuhn, eds, _Frontiers in Artificial Intelligence and Applications_ **283** pp. 9–22. ISBN 978-1-61499-660-6.   
<https://doi.org/10.3233/978-1-61499-660-6-9>

[68] Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):  
**Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv**.  
_GigaScience_ **8**(11).   
<https://doi.org/10.1093/gigascience/giz095>

[69] J. Kim, E. Deelman, Y. Gil, G. Mehta and V. Ratnakar (2008):  
**Provenance trails in the Wings/Pegasus system**.  
_Concurrency and Computation: Practice and Experience_ **20**(5) pp. 587–597.   
<https://doi.org/10.1002/cpe.1228>

[70] T. Kluyver, B. Ragan-Kelley, F. Pérez, B. Granger, M. Bussonnier, J. Frederic, K. Kelley, J. Hamrick, J. Grout, S. Corlay, P. Ivanov, D. Avila, S. Abdalla, C. Willing and Jupyter Development Team (2016):  
**Jupyter Notebooks – a publishing format for reproducible computational workflows**, in: _Positioning and Power in Academic Publishing: Players, Agents and Agendas_, _Proceedings of the 20th International Conference on Electronic Publishing_, pp. 87–90, ISBN 978-1-61499-649-1.   
<https://doi.org/10.3233/978-1-61499-649-1-87>

[71] L. Koesten, K. Gregory, P. Groth and E. Simperl (2021):  
**Talking datasets – understanding data sensemaking behaviours**.  
_International journal of human-computer studies_ **146**:102562.   
<https://doi.org/10.1016/j.ijhcs.2020.102562>

[72] L. Koesten, P. Vougiouklis, E. Simperl and P. Groth (2020):  
**Dataset reuse: Toward translating principles to practice**.  
_Patterns_ **1**(8):100136.   
<https://doi.org/10.1016/j.patter.2020.100136>

[73] J. Köster and S. Rahmann (2012):  
**Snakemake – a scalable bioinformatics workflow engine**.  
_Bioinformatics_ **28**(19) pp. 2520–2522.   
<https://doi.org/10.1093/bioinformatics/bts480>

[74] J. Kunze, J. Littman, E. Madden, J. Scancella and C. Adams (2018):  
**The BagIt File Packaging Format**, (V1.0), RFC 8493, _Internet Requests for Comments_, RFC Editor.   
<https://doi.org/10.17487/RFC8493>

[75] K. Kurowski, O. Corcho, C. Choirat, M. Eriksson, F. Coppens, M. van de Sanden and M. Ojsteršek, EOSC Interoperability Framework, Technical Report, 2021.   
<https://doi.org/10.2777/620649>

[76] C. Kyle, G. Niall, H. Mihael, K. Kacper, L. Bertram, M. Timothy, N. Jarek, S. Victoria, T. Ian, T. Thomas, M.J. Turk, C. Willis (2020):  
**Toward enabling reproducibility for data-intensive research using the Whole Tale platform**.  
_Advances in Parallel Computing_ **36** pp 766–778.   
<https://doi.org/10.3233/APC200107>

[77] M. La Rosa (2021):  
**Arkisto Platform: Describo Online**.  
<https://arkisto-platform.github.io/describo-online/>

[78] M. La Rosa and Peter Sefton (2021):  
**Arkisto Platform: Describo**.  
<https://arkisto-platform.github.io/describo/>

[79] R. Lammey (2020):  
**Solutions for identification problems: A look at the research organization registry**.  
_Science Editing_ **7**(1) pp. 65–69.   
<https://doi.org/10.6087/kcse.192>

[80] Anna-Lena Lamprecht, Leyla Garcia, Mateusz Kuzak, Carlos Martinez, Ricardo Arcila, Eva Martin Del Pico, Victoria Dominguez Del Angel, Stephanie Van De Sandt, Jon Ison, Paula Andrea Martinez, Peter Mcquilton, Alfonso Valencia, Jennifer Harrow, Fotis Psomopoulos, Josep Ll. Gelpi, Neil Chue Hong, Carole Goble, Salvador Capella-Gutierrez (2019):  
**Towards FAIR principles for research software**.  
_Data Science_ **3**(1) pp. 1–23.   
<https://doi.org/10.3233/DS-190026>

[81] T. Lebo, S. Sahoo, D. McGuinness, K. Belhajjame, J. Cheney, D. Corsar, D. Garijo, Stian Soiland-Reyes, S. Zednik and J. Zhao (2013):  
**PROV-O: The PROV Ontology**.  
_W3C Recommendation_ 30 April 2013. <https://www.w3.org/TR/2013/REC-prov-o-20130430/>

[82] J. Leipzig, D. Nüst, C.T. Hoyt, K. Ram and J. Greenberg (2021):  
**The role of metadata in reproducible computational research**.  
_Patterns_ **2**(9):100322.   
<https://doi.org/10.1016/j.patter.2021.100322>

[83] D. Lowe and G. Bayarri (2021):  
**Protein Ligand Complex MD Setup tutorial using BioExcel Building Blocks (biobb) (jupyter notebook)**.  
<https://doi.org/10.48546/workflowhub.workflow.56.1>

[84] M. Lynch and Peter Sefton (2022):  
**npm: ro-crate-excel**.  
_npm_ <https://www.npmjs.com/package/ro-crate-excel>

[85] GitHub (2021):  
**Managing large files – GitHub Docs**.  
<https://docs.github.com/en/repositories/working-with-files/managing-large-files>

[86] <small>Julie A McMurry, Nick Juty, Niklas Blomberg, Tony Burdett, Tom Conlin, Nathalie Conte, Mélanie Courtot, John Deck, Michel Dumontier, Donal K Fellows, Alejandra Gonzalez-Beltran, Philipp Gormanns, Jeffrey Grethe, Janna Hastings, Jean-Karim Hériché, Henning Hermjakob, Jon C Ison, Rafael C Jimenez, Simon Jupp, John Kunze, Camille Laibe, Nicolas Le Novère, James Malone, Maria Jesus Martin, Johanna R McEntyre, Chris Morris, Juha Muilu, Wolfgang Müller, Philippe Rocca-Serra, Susanna-Assunta Sansone, Murat Sariyar, Jacky L Snoep, Stian Soiland-Reyes, Natalie J Stanford, Neil Swainston, Nicole Washington, Alan R Williams, Sarala M Wimalaratne, Lilly M Winfree, Katherine Wolstencroft, Carole Goble, Cristopher J Mungall, Melissa A Haendel, Helen Parkinson</small> (2017):  
**Identifiers for the 21st century: How to design, provision, and reuse persistent identifiers to maximize utility and impact of life science data**.  
_PLOS Biology_ **15**(6):e2001414.   
<https://doi.org/10.1371/journal.pbio.2001414>

[87] T. Miksa, M. Jaoua and G. Arfaoui (2020):  
**Research object crates and machine-actionable data management plans**.  
_1st Workshop on Research Data Management for Linked Open Science_.   
<https://doi.org/10.4126/frl01-006423291>

[88] T. Miksa, S. Simms, D. Mietchen and S. Jones (2019):  
**Ten principles for machine-actionable data management plans**.  
_PLOS Computational Biology_ **15**(3): e1006750.   
<https://doi.org/10.1371/journal.pcbi.1006750>

[89] Steffen Möller, Hajo Nils Krabbenhöft, Andreas Tille, David Paleino, Alan Williams, Katy Wolstencroft, Carole Goble, Richard Holland, Dominique Belhachemi, Charles Plessy (2010):  
**Community-driven computational biology with Debian Linux**.  
_BMC Bioinformatics_ **11**(Suppl 12):S5.   
<https://doi.org/10.1186/1471-2105-11-S12-S5>

[90] Steffen Möller, Stuart W. Prescott, Lars Wirzenius; Petter Reinholdtsen, Brad Chapman, Pjotr Prins, Stian Soiland-Reyes, Fabian Klötzl, Andrea Bagnacani, Matúš Kalaš, Andreas Tille, Michael R. Crusoe (2017):  
**Robust cross-platform workflows: How technical and scientific communities collaborate to develop, test and share best practices for data analysis**.  
_Data Science and Engineering_ **2**(3) pp. 232–244.   
<https://doi.org/10.1007/s41019-017-0050-4>

[91] Barend Mons (2018):  
**Data Stewardship for Open Science**, 1st edn. Taylor & Francis, p. 240. [ISBN 9781315351148](https://identifiers.org/isbn/9781315351148).

[92] myExperiment (2009):  
**myExperiment Ontology Modules**.  
_myExperiment_ / _Internet Archive_  
<https://web.archive.org/web/20091115080336/http%3a%2f%2frdf.myexperiment.org/ontologies>

[93] D. Newman, S. Bechhofer and D. De Roure (2009):  
**myExperiment: An ontology for e-Research**.  
in: _Proceedings of the Workshop on Semantic Web Applications in Scientific Discourse (SWASD 2009)_, T. Clark, J.S. Luciano, M.S. Marshall, E. Prud’Hommeaux and S. Stephens, eds,  
_CEUR Workshop Proceedings_ **523**. ISSN 1613-0073.  
<http://ceur-ws.org/Vol-523/Newman.pdf>

[94] Cameron Neylon (2017):  
**As a researcher … I’m a bit bloody fed up with Data Management**.  
_Science in the Open_ (blog)
<https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/>.

[95] npm:  
**ro-crate-html-js**  
<https://www.npmjs.com/package/ro-crate-html-js>

[96] **OCFL, Oxford Common File Layout Specification**, Recommendation, 2020.  
<https://ocfl.io/1.0/spec/>

[97] A. Piper (2020):  
**Digital crowdsourcing and public understandings of the past: Citizen historians meet criminal characters**.  
_History Australia_ **17**(3) pp. 525–541.   
<https://doi.org/10.1080/14490854.2020.1796500>

[98] RDF Working Group (2014):  
**RDF 1.1 Concepts and Abstract Syntax**.  
_W3C Recommendation_ 25 Feb 2014. <https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/>.

[99] <small>Heidi L. Rehm, Angela J.H. Page, Lindsay Smith, Jeremy B. Adams, Gil Alterovitz, Lawrence J. Babb, Maxmillian P. Barkley, Michael Baudis, Michael J.S. Beauvais, Tim Beck, Jacques S. Beckmann, Sergi Beltran, David Bernick, Alexander Bernier, James K. Bonfield, Tiffany F. Boughtwood, Guillaume Bourque, Sarion R. Bowers, Anthony J. Brookes, Michael Brudno, Matthew H. Brush, David Bujold, Tony Burdett, Orion J. Buske, Moran N. Cabili, Daniel L. Cameron, Robert J. Carroll, Esmeralda Casas-Silva, Debyani Chakravarty, Bimal P. Chaudhari, Shu Hui Chen, J. Michael Cherry, Justina Chung, Melissa Cline, Hayley L. Clissold, Robert M. Cook-Deegan, Mélanie Courtot, Fiona Cunningham, Miro Cupak, Robert M. Davies, Danielle Denisko, Megan J. Doerr, Lena I. Dolman, Edward S. Dove, L. Jonathan Dursi, Stephanie O.M. Dyke, James A. Eddy, Karen Eilbeck, Kyle P. Ellrott, Susan Fairley, Khalid A. Fakhro, Helen V. Firth, Michael S. Fitzsimons, Marc Fiume, Paul Flicek, Ian M. Fore, Mallory A. Freeberg, Robert R. Freimuth, Lauren A. Fromont, Jonathan Fuerth, Clara L. Gaff, Weiniu Gan, Elena M. Ghanaim, David Glazer, Robert C. Green, Malachi Griffith, Obi L. Griffith, Robert L. Grossman, Tudor Groza, Jaime M. Guidry Auvil, Roderic Guigó, Dipayan Gupta, Melissa A. Haendel, Ada Hamosh, David P. Hansen, Reece K. Hart, Dean Mitchell Hartley, David Haussler, Rachele M. Hendricks-Sturrup, Calvin W.L. Ho, Ashley E. Hobb, Michael M. Hoffman, Oliver M. Hofmann, Petr Holub, Jacob Shujui Hsu, Jean-Pierre Hubaux, Sarah E. Hunt, Ammar Husami, Julius O. Jacobsen, Saumya S. Jamuar, Elizabeth L. Janes, Francis Jeanson, Aina Jené, Amber L. Johns, Yann Joly, Steven J.M. Jones, Alexander Kanitz, Kazuto Kato, Thomas M. Keane, Kristina Kekesi-Lafrance, Jerome Kelleher, Giselle Kerry, Seik-Soon Khor, Bartha M. Knoppers, Melissa A. Konopko, Kenjiro Kosaki, Martin Kuba, Jonathan Lawson, Rasko Leinonen, Stephanie Li, Michael F. Lin, Mikael Linden, Xianglin Liu, Isuru Udara Liyanage, Javier Lopez, Anneke M. Lucassen, Michael Lukowski, Alice L. Mann, John Marshall, Michele Mattioni, Alejandro Metke-Jimenez, Anna Middleton, Richard J. Milne, Fruzsina Molnár-Gábor, Nicola Mulder, Monica C. Munoz-Torres, Rishi Nag, Hidewaki Nakagawa, Jamal Nasir, Arcadi Navarro, Tristan H. Nelson, Ania Niewielska, Amy Nisselle, Jeffrey Niu, Tommi H. Nyrönen, Brian D. O’Connor, Sabine Oesterle, Soichi Ogishima, Vivian Ota Wang, Laura A.D. Paglione, Emilio Palumbo, Helen E. Parkinson, Anthony A. Philippakis, Angel D. Pizarro, Andreas Prlic, Jordi Rambla, Augusto Rendon, Renee A. Rider, Peter N. Robinson, Kurt W. Rodarmer, Laura Lyman Rodriguez, Alan F. Rubin, Manuel Rueda, Gregory A. Rushton, Rosalyn S. Ryan, Gary I. Saunders, Helen Schuilenburg, Torsten Schwede, Serena Scollen, Alexander Senf, Nathan C. Sheffield, Neerjah Skantharajah, Albert V. Smith, Heidi J. Sofia, Dylan Spalding, Amanda B. Spurdle, Zornitza Stark, Lincoln D. Stein, Makoto Suematsu, Patrick Tan, Jonathan A. Tedds, Alastair A. Thomson, Adrian Thorogood, Timothy L. Tickle, Katsushi Tokunaga, Juha Törnroos, David Torrents, Sean Upchurch, Alfonso Valencia, Roman Valls Guimera, Jessica Vamathevan, Susheel Varma, Danya F. Vears, Coby Viner, Craig Voisin, Alex H. Wagner, Susan E. Wallace, Brian P. Walsh, Marc S. Williams, Eva C. Winkler, Barbara J. Wold, Grant M. Wood, J. Patrick Woolley, Chisato Yamasaki, Andrew D. Yates, Christina K. Yung, Lyndon J. Zass, Ksenia Zaytseva, Junjun Zhang, Peter Goodhand, Kathryn North, Ewan Birney</small> (2021):  
**GA4GH: International policies and standards for data sharing across genomic research and healthcare**.  
_Cell Genomics_ **1**(2):100029.   
<https://doi.org/10.1016/j.xgen.2021.100029>

[100] N. Rettberg and B. Schmidt (2015):  
**OpenAIRE: Supporting a European open access mandate**.  
_College & Research Libraries News_ **76**(6) pp. 306–310. <http://resolver.sub.uni-goettingen.de/purl?gs-1/11942>   
<https://doi.org/10.5860/crln.76.6.9326>

[101] G.K. Sandve, A. Nekrutenko, J. Taylor and E. Hovig (2013):  
**Ten simple rules for reproducible computational research**.  
_PLOS Computational Biology_ **9**(10):e1003285.   
<https://doi.org/10.1371/journal.pcbi.1003285>

[102] Lynn M. Schriml, Maria Chuvochina, Neil Davies, Emiley A. Eloe-Fadrosh, Robert D. Finn, Philip Hugenholtz, Christopher I. Hunter, Bonnie L. Hurwitz, Nikos C. Kyrpides, Folker Meyer, Ilene Karsch Mizrachi, Susanna-Assunta Sansone, Granger Sutton, Scott Tighe, Ramona Walls (2020):  
**COVID-19 pandemic reveals the peril of ignoring metadata standards**.  
_Scientific Data_ **7**(1):188.   
<https://doi.org/10.1038/s41597-020-0524-5>

[103] Peter Sefton, G. Devine, C. Evenhuis, M. Lynch, S. Wise, M. Lake and D. Loxton (2018):  
**DataCrate: a method of packaging, distributing, displaying and archiving Research Objects**.  
in: _Workshop on Research Objects (RO 2018)_, 29 Oct 2018 at IEEE eScience 2018, Amsterdam, Netherland. _Zenodo_   
<https://doi.org/10.5281/zenodo.1445817>

[104] Peter Sefton (2021):  
**FAIR Data Management; It’s a lifestyle not a lifecycle**.  
_ptsefton.com_. <http://ptsefton.com/2021/04/07/rdmpic/>

[105] <small>Peter Sefton, Eoghan Ó Carragáin, Stian Soiland-Reyes, Oscar Corcho, Daniel Garijo, Raul Palma, Frederik Coppens, Carole Goble, José María Fernández, Kyle Chard, Jose Manuel Gomez-Perez, Michael R Crusoe, Ignacio Eguinoa, Nick Juty, Kristi Holmes, Jason A. Clark, Salvador Capella-Gutierrez, Alasdair J. G. Gray, Stuart Owen, Alan R. Williams, Giacomo Tartari, Finn Bacall, Thomas Thelen</small> (2019):  
**RO-Crate Metadata Specification 1.0**.  
<https://doi.org/10.5281/zenodo.3541888>

[106] <small>Peter Sefton, Eoghan Ó Carragáin, Stian Soiland-Reyes, Oscar Corcho, Daniel Garijo, Raul Palma, Frederik Coppens, Carole Goble, José María Fernández, Kyle Chard, Jose Manuel Gomez-Perez, Michael R Crusoe, Ignacio Eguinoa, Nick Juty, Kristi Holmes, Jason A. Clark, Salvador Capella-Gutierrez, Alasdair J. G. Gray, Stuart Owen, Alan R. Williams, Giacomo Tartari, Finn Bacall, Thomas Thelen, Hervé Ménager, Laura Rodríguez-Navas, Paul Walk, brandon whitehead, Mark Wilkinson, Paul Groth, Erich Bremer, LJ Garcia Castro, Karl Sebby, Alexander Kanitz, Ana Trisovic, Gavin Kennedy, Mark Graves, Jasper Koehorst, Simone Leo, Marc Portier</small> (2021):  
**RO-Crate Metadata Specification 1.1.1**.  
<https://doi.org/10.5281/zenodo.4541002>

[107] <small>Peter Sefton, Eoghan Ó Carragáin, Stian Soiland-Reyes, Oscar Corcho, Daniel Garijo, Raul Palma, Frederik Coppens, Carole Goble, José María Fernández, Kyle Chard, Jose Manuel Gomez-Perez, Michael R Crusoe, Ignacio Eguinoa, Nick Juty, Kristi Holmes, Jason A. Clark, Salvador Capella-Gutierrez, Alasdair J. G. Gray, Stuart Owen, Alan R. Williams, Giacomo Tartari, Finn Bacall, Thomas Thelen, Hervé Ménager, Laura Rodríguez-Navas, Paul Walk, brandon whitehead, Mark Wilkinson, Paul Groth, Erich Bremer, LJ Garcia Castro, Karl Sebby, Alexander Kanitz, Ana Trisovic, Gavin Kennedy, Mark Graves, Jasper Koehorst, Simone Leo</small> (2020):  
**RO-Crate Metadata Specification 1.1**.  
<https://doi.org/10.5281/zenodo.4031327>

[108] Stian Soiland-Reyes (2020):  
**I am looking for which bioinformatics journals encourage authors to submit their code/pipeline/workflow supporting data analysis**, _Twitter_ <https://twitter.com/soilandreyes/status/1250721245622079488>

[109] Stian Soiland-Reyes (2021):  
**Describing and packaging workflows using RO-Crate and BioCompute Objects** _Zenodo_, Webinar for U.S. Food and Drug Administration (FDA), 2021-05-12.   
<https://doi.org/10.5281/zenodo.4633732>

[110] Stian Soiland-Reyes, P. Alper and Carole Goble (2016):  
**Tracking Workflow Execution With TavernaPROV**, _ProvenanceWeek 2016_, session "PROV: Three Years Later". <https://s11.no/2016/provweek-tavernaprov/>   
<https://doi.org/10.5281/zenodo.51314>

[111] Stian Soiland-Reyes, M. Gamble and R. Haines (2014):  
**Research Object Bundle 1.0**.  
<https://w3id.org/bundle/2014-11-05/> <https://doi.org/10.5281/zenodo.12586>.

[112] M. Sporny, D. Longley, G. Kellogg, M. Lanthaler and N. Lindström (2014):  
**JSON-LD 1.0**, W3C Recommendation. <https://www.w3.org/TR/2014/REC-json-ld-20140116/>

[113] V. Stodden, M. McNutt, D.H. Bailey, E. Deelman, Y. Gil, B. Hanson, M.A. Heroux, J.P.A. Ioannidis and M. Taufer (2016):  
**Enhancing reproducibility for computational methods**.  
_Science_ **354**(6317) pp. 1240–1241.   
<https://doi.org/10.1126/science.aah6168>

[114] N. Thieberger and L. Barwick (2012):  
**Keeping records of language diversity in melanesia: The Pacific and regional archive for digital sources in endangered cultures (PARADISEC)**, in: _Melanesian Languages on the Edge of Asia: Challenges for the 21st Century_, N. Evans and M. Klamer, eds,  
_Language Documentation & Conservation Special Publication_ **SP05** University of Hawai’i Press, pp. 239–253. ISBN 978-0-9856211-2-4  
<http://hdl.handle.net/10125/4567>

[115] **Tools: Data Portal & Discovery**.  
<https://arkisto-platform.github.io/tools/portal/>

[116] R. Troncy, W. Bailer, M. Höffernig and M. Hausenblas (2010):  
**VAMP: A service for validating MPEG-7 descriptions w.r.t. to formal profile definitions**.  
_Multimedia tools and applications_ **46**(2–3) pp. 307–329.  
<https://www.persistent-identifier.nl/urn:nbn:nl:ui:18-14511>   
<https://doi.org/10.1007/s11042-009-0397-2>

[117] Herbert Van de Sompel, Carl Lagoze (2007):  
**Interoperability for the discovery, use, and re-use of units of scholarly communication**.  
_CTWatch Quarterly_ **3**(3).  
<http://icl.utk.edu/ctwatch/quarterly/articles/2007/08/interoperability-for-the-discovery-use-and-re-use-of-units-of-scholarly-communication/>

[118] T. Vergoulis, K. Zagganas, L. Kavouras, M. Reczko, S. Sartzetakis and T. Dalamagas (2021):  
**SCHeMa: Scheduling Scientific Containers on a Cluster of Heterogeneous Machines**.  
<https://arxiv.org/abs/2103.13138v1>

[119] C.J. Volk, Y. Lucero and K. Barnas (2014):  
**Why is data sharing in collaborative natural resource efforts so hard and what can we do to improve it?**.  
_Environmental Management_ **53**(5) pp. 883–893.   
<https://doi.org/10.1007/s00267-014-0258-2>

[120] W3C Technical Architecture Group (2007):  
**Dereferencing HTTP URIs**.  
Draft Tag Finding, 2007. <https://www.w3.org/2001/tag/doc/httpRange-14/2007-08-31/HttpRange-14.html>

[121] P. Walk, T. Miksa and P. Neish (2019):  
**RDA DMP Common Standard for Machine-Actionable Data Management Plans**.  
_Research Data Alliance_   
<https://doi.org/10.15497/rda00039>

[122] Stephanie Walton, Laurence Livermore, Olaf Bánki, Robert W. N. Cubey, Robyn Drinkwater, Markus Englund, Carole Goble, Quentin Groom, Christopher Kermorvant, Isabel Rey, Celia M Santos, Ben Scott, Alan R. Williams, Zhengzhe Wu (2020):  
**Landscape analysis for the specimen data refinery**.  
_Research Ideas and Outcomes_ **6**.  
<https://doi.org/10.3897/rio.6.e57602>

[123] <small>Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas Blomberg, Jan-Willem Boiten, Luiz Bonino da Silva Santos, Philip E. Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas, Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard Finkers, Alejandra Gonzalez-Beltran, Alasdair J.G. Gray, Paul Groth, Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A.C ’t Hoen, Rob Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E. Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe Rocca-Serra, Marco Roos, Rene van Schaik, Susanna-Assunta Sansone, Erik Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz, Mark Thompson, Johan van der Lei, Erik van Mulligen, Jan Velterop, Andra Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, Barend Mons</small> (2016):  
**The FAIR guiding principles for scientific data management and stewardship**.  
_Scientific Data_ **3**:160018.   
<https://doi.org/10.1038/sdata.2016.18>

[124] **WorkflowHub project: Project pages for developing and running the WorkflowHub, a registry of scientific workflows**.  
<https://w3id.org/workflowhub/>

[125] Jun Zhao, Jose Manuel Gomez-Perezy, Khalid Belhajjame, Graham Klyne, Esteban Garcia-Cuestay, Aleix Garridoy, Kristina Hettne, Marco Roos, David De Roure, Carole Goble (2012):  
**Why workflows break – understanding and combating decay in taverna workflows**.  
_2012 IEEE 8th International Conference on e-Science_, IEEE. <https://www.research.manchester.ac.uk/portal/files/174861334/why_decay.pdf> ISBN 978-1-4673-4466-1.   
<https://doi.org/10.1109/eScience.2012.6404482>

[126] F. Zoubek and M. Winkler (2021):  
**RO Crates and Excel**.  
<https://github.com/e11938258/RO-Crates-and-Excel> <https://doi.org/10.5281/zenodo.5068950>

[127] M. Žumer (2009):  
**National Bibliographies in the Digital Age: Guidance and New Directions**.  
_IFLA Series on Bibliographic Control_, IFLA Working Group on Guidelines for National Bibliographies, Walter de Gruyter – K. G. Saur, 2009, ISSN 1868-8438. ISBN 9783598441844.   
<https://doi.org/10.1515/9783598441844>
