---
title: "Evaluating FAIR Digital Object and Linked Data as distributed object systems"
weight: 31
lang: en-GB
aliases:
 - /2022/phd/evaluating-fdo/
categories:
  - PhD
  - Publications
keywords:
  - FAIR
  - FDO
  - digital object
  - Linked Data
  - EOSC
  - distributed objects
  - frameworks
  - interoperability
  - middleware
authors: 
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
  - name: Carole Goble
    orcid: https://orcid.org/0000-0003-1219-2137
  - name: Paul Groth
    orcid: https://orcid.org/0000-0003-0183-6910
summary: > 
  Journal article published in PeerJ Computer Science
description: > 
  FAIR Digital Object (FDO) is an emerging concept that is highlighted by European Open Science Cloud (EOSC) as a potential candidate for building a ecosystem of machine-actionable research outputs. In this work we systematically evaluate FDO and its implementations as a global distributed object system, by using five different conceptual frameworks that cover interoperability, middleware, FAIR principles, EOSC requirements and FDO guidelines themselves. 
  We compare the FDO approach with established Linked Data practices and the existing Web architecture, and provide a brief history of the Semantic Web while discussing why these technologies may have been difficult to adopt for FDO purposes. We conclude with recommendations for both Linked Data and FDO communities to further their adaptation and alignment.  
---

<h2>Cite as</h2>

Stian Soiland-Reyes, Carole Goble, Paul Groth (2024):  
**Evaluating FAIR Digital Object and Linked Data as distributed object systems**.  
_PeerJ Computer Science_ **10**:e1781  
<https://doi.org/10.7717/peerj-cs.1781>

# Evaluating FAIR Digital Object and Linked Data as distributed object systems

_Stian Soiland-Reyes¹², Carole Goble¹, Paul Groth²_

<div class="affiliations">

¹ Department of Computer Science, The University of Manchester, Manchester, UK  
² Informatics Institute, University of Amsterdam, Amsterdam, The Netherlands  

</div>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown; figure caption formatting; tables repositioned and re-styles; reference in s11 house style; inline citation hyperlinks to open access version where available; disclaimer added to acknowledgement; footnote on EOSC-IF update; DOI for Weiland 2022a.


## Abstract

FAIR Digital Object (FDO) is an emerging concept that is highlighted by European Open Science Cloud (EOSC) as a potential candidate for building a ecosystem of machine-actionable research outputs. In this work we systematically evaluate FDO and its implementations as a global distributed object system, by using five different conceptual frameworks that cover interoperability, middleware, FAIR principles, EOSC requirements and FDO guidelines themselves.

We compare the FDO approach with established Linked Data practices and the existing Web architecture, and provide a brief history of the Semantic Web while discussing why these technologies may have been difficult to adopt for FDO purposes. We conclude with recommendations for both Linked Data and FDO communities to further their adaptation and alignment.

An [RO-Crate for this article](https://w3id.org/ro/doi/10.5281/zenodo.8075229) is archived at <https://doi.org/10.5281/zenodo.8075229>

## Introduction {#sec:introduction}

The FAIR principles [[Wilkinson 2016]] encourage sharing of scientific data with machine-readable metadata and the use of interoperable formats, and are being adapted by a wide range of research infrastructures. They have been recognised by the research community and policy makers as a goal to strive for [[Ayris 2016]]. In particular, the European Open Science Cloud ([EOSC](https://www.eosc.eu/)) has promoted adaptation of FAIR data sharing of data resources across electronic research infrastructures [[Mons 2017]]. The EOSC Interoperability Framework [[Corcho 2021]] puts particular emphasis on how interoperability can be achieved technically, semantically, organisationally, and legally – laying out a vision of how data, publication, software and services can work together to form an ecosystem of rich digital objects.

Specifically, the EOSC Interoperability framework highlights the emerging FAIR Digital Object (FDO) concept [[Schultes 2019]] as a possible foundation for building a semantically interoperable ecosystem to fully realise the FAIR principles beyond individual repositories and infrastructures. The FDO approach has great potential, as it proposes strong requirements for identifiers, types, access and formalises interactive operations on objects.

In other discourse, Linked Data [[Bizer 2009]] has been seen as an established set of principles based on Semantic Web technologies that can achieve the vision of the FAIR principles [[Bonino 2016], [Hasnain 2018]]. Yet regular researchers and developers of emerging platforms for computation and data management are reluctant to adapt such a “FAIR Linked Data approach” fully [[Verborgh 2020]], opting instead for custom in-house models and JSON-derived formats from RESTful Web services [[Meroño-Peñuela 2021a], [Neumann 2021]]. While such focus on simplicity allows for rapid development and highly specialised services, it raises wider concerns about interoperability [[Turcoane 2014], [Wilkinson 2022]].

One challenge that may, perhaps counter-intuitively, steer developers towards a not-invented-here mentality [[Stefi 2015a], [Stefi 2015b]] when exposing their data on the Web is the heterogeneity and apparent complexity of Semantic Web approaches themselves [[Meroño-Peñuela 2021b]].

These approaches – FDO and Linked Data – thus, form two of the major avenues for allowing developers and the wider research community to achieve the goal of FAIR data. Given their importance, in this article we aim to compare FAIR Digital Objects with Linked Data and the Web architecture in the context of the discourse around FAIR data.

Concretely, the contribution of this article is **a systematic comparison between FDO and Linked Data using 5 different conceptual frameworks** that capture different perspectives on interoperability and readiness for implementation.

In the [background section](#sec:background) we give a background primer on FDO and Linked Data to provide a foundation for this work. The rest of this article is organised as follows:  In the [method section](#sec:method) we introduce the conceptual frameworks we use for comparison. Subsequently, in the [results section](#sec:results), we systematically step through the outcomes of applying these frameworks to both FDO and Linked Data. For each framework, we derive key observations. We end with a [discussion](#sec:discussion) of these results and their implications for both approaches and conclude.


## Background and related work {#sec:background}

In the following[^99], we discuss the related work with respect to FAIR Digital Objects and Linked Data. We do so by looking through the lens of development of these technologies over time, including future directions.

[^99]: An expanded version of this section is in [chapter 2](../background/).


### FAIR Digital Object {#sec:fdo}

The concept of **FAIR Digital Objects** [[Schultes 2019]] has been introduced as way to expose research data as active objects that conform to the FAIR principles [[Wilkinson 2016]]. This builds on the *Digital Object* (DO) concept [[Kahn 2006]], first introduced by [[Kahn 1995]] as a system of *repositories* containing *digital objects* identified by *handles* and described by *metadata* which may have references to other handles. DO was the inspiration for the [ITU-T X.1255] framework which introduced an abstract *Digital Entity Interface Protocol* for managing such objects programmatically, first realised by the Digital Object Interface Protocol (DOIP) [[Reilly 2009]].

In brief, the structure of a FAIR Digital Object (FDO) is to, given a *persistent identifier* (PID) such as a DOI, resolve to a *PID Record* that gives the object a *type* along with a mechanism to retrieve its *bit sequences*, *metadata* and references to further programmatic *operations*. The type of an FDO (itself an FDO) defines attributes to semantically describe and relate such FDOs to other concepts (typically other FDOs referenced by PIDs). The premise of systematically building an ecosystem of such digital objects is to give researchers a way to organise complex digital entities, associated with identifiers, metadata, and supporting automated processing [[Wittenburg 2019]].

Recently, FDOs have been recognised by the European Open Science Cloud ([EOSC](https://eosc.eu/)) as a suggested part of its Interoperability Framework [[Corcho 2021]], in particular, for deploying active and interoperable FAIR resources that are *machine actionable*. Development of the FDO concept continued within Research Data Alliance ([RDA](https://www.rd-alliance.org/)) groups and EOSC projects like [GO-FAIR](https://www.go-fair.org/), concluding with a set of guidelines for implementing FDO [[Bonino 2019](https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx)]. The [FAIR Digital Objects Forum](https://fairdo.org/) has since taken over the maturing of FDO through focused working groups which have currently drafted several more detailed specification documents (see [*Next steps for FDO*](#sec:next-step-fdo)).

#### FDO approaches {#sec:fdo-approaches}

FDO is an evolving concept. A set of FDO Demonstrators [[Wittenburg 2022b]] highlights how current adapters are approaching implementations of FDO from different angles:

  - Building on the Digital Object concept, using the simplified [[DONA 2018]] specification, which detail how to exchange JSON objects through a text-based protocol[^1] (usually TCP/IP over TLS). The main DOIP operations are retrieving, creating and updating digital objects. These are mostly realised using the reference implementation Cordra [[Tupelo-Schneck 2022]]. FDO types are registered in the local Cordra instance, where they are specified using JSON Schema [[Wright 2022]] and PIDs are assigned using the Handle system. Several type registries have been established.

  - Following a Linked Data approach, but using the DOIP protocol, e.g. using JSON-LD and schema.org within DOIP in Materal Sciences archives [[Riccardi 2022]].

  - Approaching the FDO principles from existing Linked Data practices on the Web, e.g. WorkflowHub use of RO-Crate and schema.org [[Soiland-Reyes 2022a]].

From this it becomes apparent that there is a potentially large overlap between the goals and approaches of FAIR Digital Objects and Linked Data, which we will cover in a subsequent [section](#sec:ld).

#### Next steps for FDO {#sec:next-step-fdo}

The [FAIR Digital Object Forum](https://fairdo.org/) working groups have prepared detailed requirement documents [[FDO 2022]] setting out the path for realising FDOs, named *FDO Recommendations*. As of 2023-06-17, most of these documents are open for public review, while some are still in draft stages for internal review. As these documents clarify the future aims and focus of FAIR Digital Objects [[Lannom 2022b]], we provide a brief summary of each:

**FAIR Digital Object Overview and Specifications** [[Anders 2023]] is a comprehensive overview of FAIR Digital Object specifications listed below. It serves as a primer that introduces FDO concepts and the remaining documents. It is accompanied by an FDO Glossary [[Broeder 2022a]].

The **FDO Forum Document Standards** [[Weiland 2022a]] documents the recommendation process within the forum, starting at *Working Draft* (WD) status within the closed working group and later within the open forum, then *Proposed Recommendation* (PR) published for public review, finalised as *FDO Forum Recommendation* (REC) following any revisions. In addition, the forum may choose to *endorse* existing third-party notes and specifications.

The **FDO Requirement Specifications** [[Anders 2023]] is an update of [[Bonino 2019](https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx)] as the foundational definition of FDO. This sets the criteria for classifying an digital entity as a FAIR Digital Object, allowing for multiple implementations. The requirements shown in [Table 3](#tbl:fdo-checks) are largely equivalent, but in this specification clarified with references to other FDO documents.

The **Machine actionability** [[Weiland 2022b]] sets out to define what is meant by *machine actionability* for FDOs. *Machine readable* is defined as elements of bit-sequences defined by structural specification, *machine interpretable* elements that can be identified and related with semantic artefacts, while *machine actionable* are elements with a type with operations in a symbolic grammar. The document largely describes requirements for resolving an FDO to metadata, and how types should be related to possible operations.

**Configuration Types** [[Lannom 2022a]] classifies different granularities for organising FDOs in terms of PIDs, PID Records, Metadata and bit sequences, e.g. as a single FDO or several daisy-chained FDOs. Different patterns used by current DOIP deployments are considered, as well as FAIR Signposting [[Van de Sompel 2015], [Van de Sompel 2022]].

**PID Profiles & Attributes** [[Anders 2022]] specifies that PIDs must be formally associated with a *PID Profile*, a separate FDO that defines attributes required and recommended by FDOs following said profile. This forms the *kernel attributes*, building on recommendations from RDA’s *PID Information Types* working group [[Broeder 2022b]]. This document makes a clear distinction between a minimal set of attributes needed for PID resolution and FDO navigation, which needs to be part of the *PID Record* [[Islam 2023]], compared with a richer set of more specific attributes as part of the *metadata* for an FDO, possibly represented as a separate FDO.

**Kernel Attributes & Metadata** [[Broeder 2022b]] elaborates on categories of FDO Mandatory, FDO Optional and Community Attributes, recommending kernel attributes like `dateCreated`, `ScientificDomain`, `PersistencePolicy`, `digitalObjectMutability`, etc. This document expands on RDA Recommendation on PID Kernel Information [[Weigel 2018]]. It is worth noting that both documents are relatively abstract and do not establish PIDs or namespaces for the kernel attributes.

**Granularity, Versioning, Mutability** [[Hellström 2022]] considers how granularity decisions for forming FDOs must be agreed by different communities depending on their pragmatic usage requirements. The affect on versioning, mutability and changes to PIDs are considered, based on use cases and existing PID practices.

**DOIP Endorsement Request** [[Schwardmann 2022a]] is an endorsement of the DOIP v2.0 [[DONA 2018]] specification as a potential FDO implementation, as it has been applied by several institutions [[Wittenburg 2022b]]. The document proposes that DOIP shall be assessed for completeness against FDO – in this initial draft this is justified as *“we can state that DOIP is compliant with the FDO specification documents in process”* (the documents listed above).

**Upload of FDO** [[Blanchi 2022a]] illustrates the operations for uploading an FDO to a repository, what checks it should do (for instance conformance with the PID Profile, if PIDs resolve). ResourceSync [[ANSI 2017]] is suggested as one type of service to list FDOs. This document highlights potential practices by repositories and their clients, without adding any particular requirements.

**Typing FAIR Digital Objects** [[Lannom 2022a]] defines what *type* means for FDOs, primarily to enable machine actionability and to define an FDO’s purpose. This document lays out requirements for how *FDO Types* should themselves be specified as FDOs, and how an *FDO Type Framework* allows organising and locating types. Operations applicable to an FDO is not predefined for a type, however, operations naturally will require certain FDO types to work. How to define such FDO operations is not specified.

**Implementation of Attributes, Types, Profiles and Registries** [[Blanchi 2022b]] details how to establish FDO registries for types and FDO profiles, with their association with PID systems. This document suggest policies and governance structures, together with guidelines for implementations, but without mandating any explicit technology choices. Differences in use of attributes are examplified using FDO PIDs for scientific instruments, and the proto-FDO approach of [DARIAH-DE](https://de.dariah.eu/) [[Schwardmann 2022b]].

It is worth pointing out that, except for the DOIP endorsement, all of these documents are conceptual, in the sense that they permit any technical implementation of FDO, if used according to the recommendations. Existing FDO implementations [[Wittenburg 2022b]] are thus not fully consolidated in choices such as protocols, type systems and serialisations – this divergence and corresponding additional technical requirements mean that FDOs are not yet in a single ecosystem.

### From the Semantic Web to Linked Data {#sec:ld}

In order to describe *Linked Data* as it is used today, we’ll start with an (opinionated) description of the evolution of its foundation, the *Semantic Web*.

#### A brief history of the Semantic Web {#sec:semweb}

The **Semantic Web** was developed as a vision by Tim Berners-Lee [[Berners-Lee 1999]], at a time that the Web had already become widely established for information exchange, being a global set of hypermedia documents which are cross-related using universal links in the form of URLs. The foundations of the Web (e.g. URLs, HTTP, SSL/TLS, HTML, CSS, ECMAScript/JavaScript, media types) were standardised by [W3C](https://www.w3.org/standards/), [Ecma](https://www.ecma-international.org/), [IETF](https://www.ietf.org/standards/) and later [WHATWG](https://whatwg.org/). The goal of Semantic Web was to further develop the machine-readable aspects of the Web, in particular, adding *meaning* (or semantics) to not just the link relations, but also to the *resources* that the URLs identified, and for machines thus being able to meaningfully navigate across such resources, e.g. to answer a particular query.

Through W3C, the Semantic Web was realised with the Resource Description Framework (RDF) [[Schreiber 2014]] that used *triples* of subject-predicate-object statements, with its initial serialisation format [[Lassila 1999]] being RDF/XML (XML was at the time seen as a natural data-focused evolution from the document-centric SGML and HTML).

While triple-based knowledge representations were not new [[Stanczyk 1987]], the main innovation of RDF was the use of global identifiers in the form of URIs[^2] as the primary identifier of the *subject* (what the statement is about), *predicate* (relation/attribute of the subject) and *object* (what is pointed to). By using URIs not just for documents[^3], the Semantic Web builds a self-described system of types and properties, where the meaning of a relation can be resolved by following its hyperlink to the definition within a *vocabulary*. By applying these principles as well to any kind of resource that could be described at a URL, this then forms a global distributed Semantic Web.

The early days of the Semantic Web saw fairly lightweight approaches with the establishment of vocabularies such as FOAF (to describe people and their affiliations) and Dublin Core (for bibliographic data). Vocabularies themselves were formalised using RDFS or simply as human-readable HTML web pages defining each term. The main approach of this *Web of Data* was that a URI identified a *resource* (e.g. an author) with a HTML *representation* for human readers, along with a RDF representation for machine-readable data of the same resource. By using [*content negotiation*](https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation) in HTTP, the same identifier could be used in both views, avoiding `index.html` vs `index.rdf` exposure in the URLs. The concept of *namespaces* gave a way to give a group of RDF resources with the same URI base from a Semantic Web-aware service a common *prefix*, avoiding repeated long URLs.

The mid-2000s saw large academic interest and growth of the Semantic Web, with the development of more formal representation system for ontologies, such as OWL [[W3C 2012]], allowing complex class hierarchies and logic inference rules following *open world* paradigm. More human-readable syntaxes for RDF such as Turtle evolved at this time, and conferences such as [ISWC](https://iswc2022.semanticweb.org/) [[Horrocks 2002]] gained traction, with a large interest in knowledge representation and logic systems based on Semantic Web technologies evolving at the same time.

Established Semantic Web services and standards include: SPARQL [[W3C 2013]] (pattern-based triple queries), [named graphs](https://www.w3.org/TR/rdf11-concepts/#section-dataset) [[Wood 2014]] (triples expanded to *quads* to indicate statement source or represent conflicting views), triple/quad stores (graph databases such as OpenLink Virtuoso, GraphDB, 4Store), mature RDF libraries (including Redland RDF, Apache Jena, Eclipse RDF4J, RDFLib, RDF.rb, rdflib.js), and graph visualisation.

RDF is one way to implement *knowledge graphs*, a system of named edges and nodes[^5] [[Nurdiati 2008]], which when used to represent a sufficiently detailed model of the world, can then be queried and processed to answer detailed research questions. The creation of RDF-based knowledge graphs grew particularly in fields like bioinformatics, e.g. for describing genomes and proteins [[Goble 2008], [Williams 2012]]. In theory, the use of RDF by the life sciences would enable interoperability between the many data repositories and support combined views of the many aspects of bio-entities – however, in practice most institutions ended up making their own ontologies and identifiers, for what to the untrained eye would mean roughly the same. One can argue that the toll of adding the semantic logic system of rich ontologies meant that small, but fundamental, differences in opinion (e.g. *should a gene identifier signify just the particular DNA sequence letters, or those letters as they appear in a particular position on a human chromosome?*) led to large differences in representational granularity, and thus needed different identifiers.

Facing these challenges, thanks to the use of universal identifiers in the form of URIs, *mappings* could retrospectively be developed not just between resources, but also across vocabularies. Such mappings can be expressed themselves using lightweight and flexible RDF vocabularies such as SKOS [[Isaac 2009]] (e.g. `dct:title skos:closeMatch schema:name` to indicate near equivalence of two properties). Exemplifying the need for such cross-references, automated ontology mappings have identified large potential overlaps like 372 definitions of `Person` [[Hu 2011]].

The move towards *Open Science* data sharing practices did from the late 2000s encourage knowledge providers to distribute collections of RDF descriptions as downloadable *datasets*,[^6] so that their clients can avoid thousands of HTTP requests for individual resources. This enabled local processing, mapping and data integration across datasets (e.g. Open PHACTS [[Groth 2014]]), rather than relying on the providers’ RDF and SPARQL endpoints (which could become overloaded when handling many concurrent, complex queries).

With these trends, an emerging problem was that adopters of the Semantic Web primarily utillised it as a set of graph technologies, with little consideration to existing Web resources. This meant that links stayed mainly within a single information system, with little URI reuse even with large term overlaps [[Kamdar 2017]]. Just like *link rot* affect regular Web pages and their citations from scholarly communication [[Klein 2014]], for a majority of described RDF resources in the [Linked Open Data](https://lod-cloud.net/) (LOD) Cloud’s gathering of more than thousand datasets, unfortunately do not actually link to (still) downloadable (*dereferenceable*) Linked Data [[Polleres 2020]]. Another challenge facing potential adopters is the plethora of choices, not just to navigate, understand and select to reuse the many possible vocabularies and ontologies [[Carriero 2020]], but also technological choices on RDF serialisation (at least [7 formats](https://www.w3.org/TR/rdf11-primer/#section-graph-syntax)), type system (RDFS [[Guha 2014]], OWL [[W3C 2012]], OBO [[Tirmizi 2011]], SKOS [[Isaac 2009]]), and deployment challenges [[Sauermann 2008]] (e.g. hash vs slash in namespaces, HTTP status codes and PID redirection strategies).

#### Linked Data: Rebuilding the Web of Data {#sec:ld-web}

The **Linked Data** (LD) concept [[Bizer 2009]] was kickstarted as a set of best practices [[Berners-Lee 2006]] to bring the Web aspect of the Semantic Web back into focus. Crucial to Linked Data is the *reuse of existing URIs*, rather than making new identifiers. This means a loosening of the semantic restrictions previously applied, and an emphasis on building navigable data resources, rather than elaborate graph representations.

Vocabularies like [schema.org](https://schema.org/) evolved not long after, intended for lightweight semantic markup of existing Web pages, primarily to improve search engines’ understanding of types and embedded data. In addition to several such embedded *microformats* [[OGP], [WHATWG 2023], [Sporny 2015]], we find JSON-LD [[Sporny 2020]] as a Web-focused RDF serialisation that aims for improved programmatic generation and consumption, including from Web applications. JSON-LD is as of 2023-05-18 used[^7] by 45% of the top 10 million websites [[W3Tech 2023]].

Recently there has been a renewed emphasis to improve the *Developer Experience* [[Verborgh 2018]] for consumption of Linked Data, for instance RDF Shapes – expressed in SHACL [[Kontokostas 2017]] or ShEx [[Baker 2019]] – can be used to validate RDF Data [[Gayo 2017], [Thornton 2019]] before consuming it programmatically, or reshaping data to fit other models. While a varied set of tools for Linked Data consumptions have been identified, most of them still require developers to gain significant knowledge of the underlying Semantic Web technologies, which hampers adaption by non-LD experts [[Klímek 2019]], which then tend to prefer non-semantic two-dimensional formats such as CSV files.

A valid concern is that the Semantic Web research community has still not fully embraced the Web, and that the “final 20%” engineering effort is frequently overlooked in favour of chasing new trends such as Big Data and AI, rather than making powerful Linked Data technologies available to the wider groups of Web developers [[Verborgh 2020]]. One bridging gap here by the Linked Data movement has been “Linked Data by stealth” approaches such as structured data entry spreadsheets powered by ontologies [[Wolstencroft 2011]], the use of Linked Data as part of REST Web APIs [[Page 2011]], and as shown by the big uptake by publishers to annotate the Web using schema.org [[Bernstein 2016]], with vocabulary use patterns documented by copy-pastable JSON-LD examples, rather than by formalised ontologies or developer requirements to understand the full Semantic Web stack.

Linked Data provides technologies that have evolved over time to satisfy its primary purpose of data interoperability. The needs to embrace the Web and developer experience have been central lessons learned. In contrast, FDO is a new approach with many different potential paths forward, and having a partial overlap with the aims of Linked Data.

## Method {#sec:method}

Our main motivation for this article is to investigate how FAIR Digital Objects may differ from the learnt experiences of Linked Data and the Web. We also aim to reflect back from FDO’s motivation of machine-actionability to consider the Web as a distributed computational system.

To better understand the relationship between the FDO framework and other existing approaches, we use the following for analysis:

1.  An Interoperability Framework and Distributed Platform for Fast Data Applications [[Delgado 2016]], which proposes quality measurements for comparing how frameworks support interoperability, particularly from a service architectural view.
2.  The FAIR Digital Object guidelines [[Bonino 2019]], validated against its current implementations for completeness.
3.  A Comparison Framework for Middleware Infrastructures [[Zarras 2004]], which suggest dimensions like openness, performance and transparency, mainly focused on remote computational methods.
4.  Cross-checks against RDA’s FAIR Data Maturity Model [[Bahim 2020]] to find how the FAIR principles are achieved in FDO, in particular, considering access, sharing and openness.
5.  EOSC Interoperability Framework [[Corcho 2021]] which gives recommendations for technical, semantic, organisational and legal interoperability, particularly from a metadata perspective.

Conceptual framework 1, 3, 5 considers more general views of interoperability between systems, whereas frameworks 2 and 4 are developed specifically for addressing FAIR principles. 

The reason for this wide-ranged comparison is to exercise the different dimensions that together form FAIR Digital Objects: Data, Metadata, Service, Access, Operations, Computation. We have left out further considerations on type systems, persistent identifiers and social aspects as principles and practices within these dimensions are still taking form within the FDO community (as detailed in the [earlier section](#sec:next-step-fdo)).

Some of these frameworks invite a comparison on a conceptual level, while others relate better to implementations and current practices. For conceptual comparisons we consider FAIR Digital Objects and the Web broadly. For implementations, we contrast the main FDO realisation using the DOIPv2 protocol [[DONA 2018]] against Linked Data as implemented in general practice[^8].

## Results {#sec:results}

### Considering FDO/Web as interoperability framework for Fast Data {#sec:interoperability-compare}

The Interoperability Framework for Fast Data Applications [[Delgado 2016]] categorises interoperability between applications along 6 strands, covering different architectural levels: from *symbiotic* (agreement to cooperate) and *pragmatic* (ability to choreograph processes), through *semantic* (common understanding) and *syntactic* (common message formats), to low-level *connective* (transport-level) and *environmental* (deployment practices).

We have chosen to investigate using this framework as it covers the higher levels of the OSI Model [[Stallings 1990]] better with regards to automated machine-to-machine interaction (and thus interoperability), which is a crucial aspect of the FAIR principles. In [Table 1](#tbl:fdo-web-interoperability-framework) we use the interoperability framework to compare the current FAIR Digital Object approach against the Web and its Linked Data practices.



<div id="tbl:fdo-web-interoperability-framework">

_**Table 1**: Considering FDO and Web according to the quality levels of the Interoperability Framework for Fast Data [[Delgado 2016]]_

| Quality    | FDO w/ DOIP    | Web w/ Linked Data    |
| :---- | :---- | :---- |
| **Symbiotic**: *to what extent multiple applications can agree to interact, align, collaborate or cooperate*    | The purpose of FDO is to enable federated machine actionable digital objects for scholarly purposes, in practice this also requires agreement of compatibility between FDO types. FDO encourages research communities to develop common type registries to be shared across instances. In current DOIP practice, each service have their own types, attributes and operations. The wider symbiosis is consistent use of PIDs.    | The Web is loosely coupled and encourages collaboration and linking by URL. In practice, REST APIs [[Fielding 2000]] end up being mandated centrally by dominant (often commercial) providers [[Fielding 2017]], and the clients are required to use each API as-is with special code per service. Use of Linked Data enables common tooling and semantic mapping across differences. |
| **Pragmatic**: *using interaction contracts so processes can be choreographed in workflows*    | FDO types and operations enable detailed choreography (Canonical Workflows [[CWFR 2021]]). Attributes[^98] `0.TYPE/DOIPOperation` has lightweight definition of operation, `0.DOIP/Request` or `0.DOIP/Response` may give FDO Type or any other kind of “specifics” (incl. human-readable docs). Semantics/purpose of operations not formalised (similar operations can be grouped with `0.DOIP/OperationReference`).    | “Follow your nose” crawler navigation, which may lead to frequent dead ends. Operational composition, typically within a single API provider, documented by OpenAPI 3 [[Miller 2021]], [schema.org Actions], WSDL/SOAP [[Liu 2007]], but frequently just as human-readable developer documentation with examples.    |
| **Semantic**: *ensuring consistent understanding of messages, interoperability of rules, knowledge and ontologies* | FDO semantic enable navigation and typing. Every FDO has a type. Types maintained in FDO Type registries, which may add additional semantics, e.g. the ePIC [PID-InfoType for Model](https://hdl.handle.net/21.11104/c1a0ec5ad347427f25d6). No single type semantic, Type FDOs can link to existing vocabularies & ontologies. JSON-LD used within some FDO objects (e.g. DISSCO Digital Specimen, NIST Material Science schema) [[Wittenburg 2022b]] | Lightweight HTTP semantics for authenticity/navigation. Semantic Type not commonly expressed on PID/header level, may be declared within Linked Data metadata. Semantic of type implied by Linked Data formats (e.g. OWL2, RDFS), although choice of type system may not be explicit.    |
| **Syntactic**: *serialising messages for digital exchange, structure representation*    | DOIP serialise FDOs as JSON, metadata commonly use JSON, typed with JSON Schema. Multiple byte stream attachments of any media type.    | Textual HTTP headers (including any signposting), single byte stream of any media type, e.g. Linked Data formats (JSON-LD, Turtle, RDF/XML) or embedded in document (HTML with RDFa, JSON-LD or Microdata). XML was previously the main syntax used by APIs, JSON is now dominant.    |
| **Connective**: *transferring messages to another application, e.g. wrapping in other protocols*    | [[DONA 2018]] is transport-independent, commonly TLS TCP/IP port 9000, DOIP over HTTP [CNRI 2023b]   | HTTP/1.1, TCP/IP port 80 [[Fielding 1999]]; HTTP/1.1+TLS, TCP/IP 443 [[Rescorla 2000]]; HTTP/2, as HTTP/1\* but binary [[Belshe 2015]]; HTTP/3, like HTTP/2+TLS but UDP [[Bishop 2022]]    |
| **Environmental**: *how applications are deployed and affected by its environment, portability*    | Main DOIP implementation is [*Cordra*](https://www.cordra.org/), which can be single-instance or [distributed](https://www.cordra.org/documentation/configuration/distributed-deployment.html). Cordra [storage backends](https://www.cordra.org/documentation/configuration/storage-backends.html) include file system, S3, MongoDB (itself scalable). Unique DOIP protocol can be hard to add to existing Web application frameworks, although proxy services have been developed (e.g. B2SHARE adapter).    | HTTP services widely deployed in a myriad of ways, ranging from single instance servers, horizontally & vertically scaled application servers, to multi-cloud Content-Delivery Networks (CDN). Current scalable cloud technologies for Web hosting may not support HTTP features previously seen as important for Semantic Web, e.g. content negotiation and semantic HTTP status codes.    |

</div>

[^98]: DOIP's predefined attributes, types and operations have Handle-like identifiers with prefixes `0.TYPE` and `0.DOIP, these are, however, not registered in the Handle system.


Based on the analysis shown in [Table 1](#tbl:fdo-web-interoperability-framework), we draw the following conclusions:

The Web has already showed us how one can compose workflows of hetereogeneous Web Services [[Wolstencroft 2013]]. However, this is mostly done via developer or human interaction [[Lamprecht 2021]]. Similiarly, FDO does not enable automatic composition because operation semantics are not well defined. There is a question as to whether the extensive documentation and broad developer usage that is available for Web APIs could potentially be utilised for FDO.

A difference between Web technologies and FDO is the stringency of the requirements for both syntax and semantics. Whereas the Web allows many different syntactic formats (e.g. from HTML to XML, PDFs), FDO realised with DOIP requires JSON. On the semantic front, FDO mandates that every object have a well-defined type and structured form. This is clearly not the case on the Web.

In terms of connectivity and the deployment of applications, the Web has a plethora of software, services, and protocols that are widely deployed. These have shown interoperability. The Web standards bodies (e.g. IETF and W3C) follow the OpenStand principles [[OpenStand 2017]] to embrace openness, transparency, and broad consensus. In contrast, FDO has a small number of implementations and corresponding protocols, although with a growing community, as evidenced at the first international FDO conference [[Loo 2022]]. This is not to say that it is not worth developing further Handle+DOIP implementations in the future, but we note that the current FDO functionality can easily be implemented using Web technologies, even as DOIP-over-HTTP [[CNRI 2023b]].

It is also a question as to whether a highly constrained protocol revolving around persistent identifiers is in fact necessary. For example, DOIs are mostly resolved on the web using HTTP redirects with the common `https://doi.org/` prefix, hiding their Handle nature as an implementation detail [[DOI 2017]].

#### Mapping of Metamodel concepts {#sec:metamodel}

The Interoperability Framework for Fast Data also provides a brief *metamodel* which we use in [Table 2](#tbl:metamodel-concepts) to map and examplify corresponding concepts in FDO’s DOIP realization and the Web using HTTP semantics [[Fielding 2022]].

From this mapping[^15] we can identify the conceptual similarities between DOIP and HTTP, often with common terminology. Notable are that neither DOIP or HTTP have strong support for transactions (explored further in [section on middleware](#sec;middleware)), as well that HTTP has poor direct support for processes, as the Web is primarily stateless by design.

<div id="tbl:metamodel-concepts">

_**Table 2**: Mapping the Metamodel concepts from the Interoperability Framework for Fast Data [[Delgado 2016]] to equivalent concepts for FDO and Web._

| Metamodel concept | FDO/DOIP concept      | Web/HTTP concept      |
| :---------------- | :----------------------------------------------------------- | :---------------------------------------------------- |
| Resource          | FDO/DO            | Resource    |
| Service           | DOIP service      | Server/endpoint    |
| Transaction       | (not supported)   | Conditional requests, `409 Conflict`    |
| Process           | Extended operations    | (primarily stateless), `100 Continue`, `202 Accepted`    |
| Operation         | DOIP Operation    | Method, query parameters    |
| Request           | DOIP Request      | Request    |
| Response          | DOIP Response     | Response    |
| Message           | Segment, `requestId`  | Message, Representation    |
| Channel           | DOIP Transport protocol (e.g. TCP/IP, TLS). JSWS signatures. | TCP/IP, TLS, UDP    |
| Protocol          | DOIP 2.0, ++      | HTTP/1.1, HTTP/2, HTTP/3    |
| Link              | PID/Handle        | URL    |

</div>

### Assessing FDO implementations {#sec:doip-fdo-compare}

The FAIR Digital Object guidelines [[Bonino 2019](https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx)] sets out recommendations for FDO implementations. Note that the proposed update to FDO specification [[Anders 2023]] clarifies these definitions with equivalent identifiers[^9] and relates them to further FDO requirements such as FDO Data Type Registries.

In [Table 3](#tbl:fdo-checks) we evaluate completeness of the guidelines in two current FDO realizations, using DOIPv2 [[DONA 2018]] and using Linked Data Platform [[Speicher 2015]], as proposed by [[Bonino 2022]].

A key observation from this is that simply using DOIP does not achieve many of the FDO guidelines. Rather the guidelines set out how a protocol like DOIPs should be used to achieve FAIR Digital Object goals. The DOIP Endorsement [[Schwardmann 2022a]] set out that to comply, DOIP must be used according to the set of FDO requirement documents (see [previous section](#sec:next-step-fdo)), and notes *Achieving FDO compliance requires more than DOIP and full compliance is thus left to system designers*. Likewise, a Linked Data approach will need to follow the same requirements to actually comply as an FDO implementation.

From our evaluation, we can observe:

  - G1 and G2 call for stability and trustworthiness. While the foundations of both DOIP and Linked Data approaches are now well established – the FDO requirements and in particular, how they can be implemented, are still taking shape and subject to change.

  - Machine actionability (G4, G6) is a core feature of both FDOs and Linked Data. Conceptually they differ in the which way types and operations are discovered, with FDO seemingly more rigorous. In practice, however, we see that DOIP also relies on dynamic discovery of operations and that operation expectations for types (FDOF7) have not yet been defined.

  - FDO proposes that types can have additional operations beyond CRUD (FDOF5, FDOF6), while Linked Data mainly achieves this with RESTful patterns using CRUD on additional resources, e.g. `order/152/items`. These are mainly stylistics but affect the architectural view – FDOs have more of an object-oriented approach.

  - FDO puts strong emphasis on the use of PIDs (FDOF1, FDOF2, FDOF3, FDOF5), but in current practice DOIP use local types, local extended operations (FDOF5) and attributes (FDOF4) that are not bound to any global namespace.

  - Linked Data have a strong emphasis on semantics (FDOF8), and metadata schemas developed by community agreements (FDOF10). FDO types need to be made reusable across servers.

  - While FDO recommends nested metadata FDOs (FDOF8, FDOF9), in practice this is not found (or linked with custom keys), particularly due to lack of namespaces and the favouring of local types rather than type/property re-use. Linked Data frequently have multiple representations, but often not sufficiently linked (link relation `alternate` [[Nottingham 2017]]) or related (`prov:specializationOf` from [Lebo 2013a]).

  - FDO collections are not yet defined for DOIP, while Linked Data seemingly have too many alternatives. LDP has specific native support for containers.

  - Tombstones for deleted resources are not well supported, nor specified, for either approach, although the continued availability of metadata when data is removed is a requirement for FAIR principles (see [RDA-A2-01M](#RDA-A2-01M) in [Table 5](#tbl:fair-data-maturity-model)).

  - DOIP supports multiple chunks of data for an object (FDOF3), while Linked Data can support content-negotiation. In either case it can be unclear to clients what is the meaning or equivalence of any additional chunks.

<div id="tbl:fdo-checks">

_**Table 3**: Checking FDO guidelines [[Bonino 2019]] against its current implementations as DOIP [[DONA 2018]] and Linked Data Platform (LDP) [[Bonino 2022]], with suggestions for required additions._

| **FDO Guideline** | DOIP 2.0 | FDO suggestions | Linked Data Platform | LDP suggestion |
| :---------------- | :------- | :-------------- | :------------------- | :------------- |
| G1: *invest for many decades*    | Handle system stable for 20 years, DOIP 2.0 since 2017.    | Ensure FDO types will not be protocol-bound as DOIP might be updated/replaced    | HTTP stable for 30 years, Semantic Web for 20 years. `http://` URIs mostly replaced by `https://`.    | Keep flexibility of RDF serialisation formats which may change more frequently    |
| G2: *trustworthiness*    | DOI/Handle trusted by all major academic publishers and data repositories. DOIP relatively unknown, in effect only one implementation.    | Further promote DOIP and justify its benefits. Build tutorials and OSI open source implementations. Standardise DOIP-over-HTTP alternative.    | JSON-LD used by half of all websites [[W3Tech 2023]], however previous bad experiences with Semantic Web may deter adopters    | Ensure simplicity for end developers, rather than semantic overengineering. Example-driven documentation.    |
| G3: *follows FAIR principles*    | See [Table 5](#tbl:fair-data-maturity-model)    | Ensure all FAIR principles are covered, build complete examples.    | Touched briefly, see [Table 5](#tbl:fair-data-maturity-model)    | Add explicit expression to show each FAIR principle fulfilled.    |
| G4: *machine actionability*    | CRUD and extension operations dynamically listed (see [Table 4](#tbl:fdo-web-middleware))    | Specify which operations should work for a given type, to reduce need for dynamic lookup. Specify input/output expectations formally (e.g. JSON Schema).    | HTTP CRUD operations, Open API (see [Table 4](#tbl:fdo-web-middleware))    | Document operations so client can make subsequent HTTP calls.    |
| G5: *abstraction principle*    | Handle PIDs as abstraction base. DOIP operations can use any transport protocol.    | Document transport protocols as FDOs, recommend which transport to use.    | URI as abstraction base. Does not specify PID requirements.    | Give stronger deployment recommendations.    |
| G6: *stable binding between entities*    | Machine-navigation through PIDs and operations specified per type. Unclear when metadata field is a PID or plain text.    | Make datatype of fields explicit to support navigation.    | Machine-navigation through URIs via properties and types. Unclear when URI should be followed or is just identifier, but always distinct from plain text.    |    |
| G7: *encapsulation*    | Operations discovered at runtime (`0.DOIP/Op.ListOperations`).    | Allow method discovery by type FDOs in advance [[Lannom 2022a]].    | HTTP methods discovered at runtime (`OPTIONS`), indempotent methods attempted directly. Unsupported methods reported using LDP constraints to human-readable text.    | Declare supported methods in advance, e.g. OpenAPI [[Miller 2021]]    |
| G8: *technology independence*    | In theory independent, in reality depends on single implementations of Handle system and DOIP    | Encourage open source DOIP testbeds and lighter reference implementations    | Multiple HTTP implementations, multiple LDP implementations. No FDOF implementations.    | Develop demonstrator of FDOF usage based on existing LDP server.    |
| G9: *standard compliance*    | Handle [[Sun 2003a]], DOIP [[DONA 2018]]. FDO requirements not standardised yet.    | Formalise standard process of FDO requirements [[Weiland 2022a]]    | HTTP, LDP. However FDOF is not yet standardised.    | Formalise FDOF from FDOF-SEM working group.    |
| FDOF1: *PID as basis*    | Extensive use of Handle system.    | Clarify how local testing handles can be used during development, how “temporary” FDOs should evolve [[Anders 2022]]. Register `0.DOIP/*` and `0.FDO/*` as actual PIDs.    | HTTP URLs as basis for identifiers, but they are frequently not persistent.    | Add strong guidance for PID services like w3id and persistence policies [[McMurry 2017]].    |
| FDOF2: *PID record w/ type*    | Unspecified how to resolve from Handle to DOIP Service (\!), in practice `10320/loc`, `0.TYPE/DOIPService`, `URL`, `URL_REPLICA`    | Document requirements for PID Record    | w3id/purl PIDs redirect without giving any metadata. Datacite DOIs content-negotiate to give registered metadata.    | Add FAIR Signposting [[Van de Sompel 2022]] at PID provider for minimal PID record    |
| FDOF3: *PID resolvable to bytestream & metadata*    | Byte stream resolvable (`0.DOIP/Retrieve`), `includeElementData` option can retrieve bytestream or full object structure. No method/attribute defined for separate metadata, only directly in PID Record. Unclear meaning of multiple items and bytestream chunks.    | Clarify expectations for multiple items. Recommend chunks to not be used.    | URIs resolvable by default. Multiple ways to resolve metadata, unclear preference.    | Add FAIR Signposting and preference order.    |
| FDOF4: *Additional attributes*    | Freetext attribute keys. Attributes should be defined for FDO type.    | Require that attribute keys should be PIDs (or have predefined mapping to PIDs). Explicitly allow attributes not already defined in type.    | All attributes individually identified. Any Linked Data attributes can be used by URI or with mapped prefix.    | Clarify type expectations of required/recommended/optional attributes.    |
| FDOF5: *Interface: operation by PID*    | Extended operations use PID, but “pid-like” DOIP operations/types are not registered as handles.    | Register `0.DOIP/*` and `0.FDO/*` as PIDs. Clarify that operations can be mapped to protocol directly.    | CRUD operations used directly in HTTP (e.g. `PUT`). Unclear how to provide PID for additional operations.    | Specify how additional operations should be called over HTTP.    |
| FDOF6: *CRUD operations + extensions*    | `0.DOIP/Op.Create`, `Op.Retrieve`, `Op.Update`, `Op.Delete` but also `0.DOIP/Op.Search`.    | Document    | `PUT`, `GET`, `POST`, `DELETE`, `PATCH`, `HEAD` – extension operations (e.g. WebDAV `COPY`) not used, resource patterns  [[Ekuan 2023]] are used instead.    | Document how operation resources can be discovered from an LPD container. Document search API.    |
| FDOF7: *FDOF Types related to operations*    | Not yet formalised, by DOIP discoverable on a given FDO rather than type. PR-TypingFDOs leaves this open.    | Add explicit relation between type and operations    | `OPTIONS` per LDP Resource, but not by type. Common types (`ldp:Resource`, `ldp:Container`) indicate LDP support, but are not required.    | Always make LDP types explicit in FDO profile.    |
| FDOF8: *Metadata as FDO, semantic assertions*    | DOIP includes all metadata in PID Record. Separate Metadata FDO need custom property.    | Specify a `0.FDO/metadata` or similar to point to Metadata FDOs.    | Assertions are always with semantics, using RDF vocabularies. Unspecified how to find additional metadata resources, `rdfs:seeAlso` is common.    | Use FAIR Signposting `describedby` link relation to additional metadata PIDs    |
| FDOF9: *Different metadata levels*    | Defines open-ended “Response Attributes” without namespaces, but mandated as “None” for all CRUD operations. Metadata would need to be bundled within custom FDO types or attributes. Unclear how levels are separated within single FDO representation (may need FDOF8).    | Declare which metadata are expected within response attribute or within FDO object. Require PIDs for custom attributes. Define how alternate metadata levels can be represented separately.    | Undefined how to handle multiple metadata granularities or domains, alternative LDP containers can present different views on same stored objects.    | Define how to navigate to alternate views and their semantic implications, e.g. `owl:sameAs`    |
| FDOF10: *Metadata schemas by community*    | Metadata schemas are in practice managed on single Cordra server as local types, using JSON Schema.    | Require types to be FDOs with registered PIDs, implement shared types.    | Plethora of existing RDF vocabularies/ontologies managed by larger communities, e.g. [OBO Foundry](https://obofoundry.org/) [[Smith 2007]]    | Rather document better how individual ad-hoc schemas can be started for prototypes.    |
| FDOF11: *FDO collections w/ semantic relations*    | Collection type undefined by DOIP. Informal use of `HAS_PARTS` Handle attribute (e.g. [[Semmler 2022]]).    |    | LDP Containers required by specification, also user-created (eg. `BasicContainer`).    | Clarify relation to other collections like DCAT 3 [[Albertoni 2023]], [Schema.org Dataset](https://schema.org/Dataset), OAI-ORE [[Lagoze 2008]]    |
| FDOF12: *Deleted FDO preserve PID w/ tombstone*    | Tombstone for deleted resource undefined by DOIP. `0.DOIP/Status.104` status code does not distinguish “Not Found” or “Gone”    | Formalise tombstone requirements with new FDO type    | `410 Gone` recommended, but `404 Not Found` common. No requirement for tombstone serialisation    | Formalise tombstone requirements and serialisation    |

</div>

### Comparing FDO and Web as middleware infrastructures {#middleware}

In this section, we take the perspective that FDO principles are in effect proposing a global infrastructure of machine-actionable digital objects. As such we can consider implementations of FDO as **middleware infrastructures** for programmatic usage, and can evaluate them based on expectations for client and server developers.

We argue that the Web, with its now ubiquitous use of REST API [[Fielding 2000]], can be compared as a similar global middleware. Note that while early moves for developing Semantic Web Services [[Fensel 2011]] attempted to merge the Web Service and RDF aspects, we are here considering mainly the current programmatic Web and its mostly light-weight use of 3 out of possible *5 stars Linked Data* [[Hausenblas 2012]].

For this purpose, we here utillise the Comparison Framework for Middleware Infrastructures [[Zarras 2004]] that formalise multiple dimensions of openness, scalability, transparency, as well as characteristics known from Object-oriented programming such as modularity, encapsulation and inheritance.

Based on the analysis in [Table 4](#tbl:fdo-web-middleware), we make the following observations:

  - With respect to the aspect of *Performance*, it is interesting to note that while the first version of DOIP [[Reilly 2009]] supported multiplexed channels similar to HTTP/2 (allowing concurrent transfer of several digital objects). Multiplexing was removed for the much simplified DOIP 2.0 [[DONA 2018]]. Unlike DOIP 1.0, DOIP 2.0 will require a DO response to be sent back completely, as a series of segments (which again can be split the bytes of each binary *element* into sized *chunks*), before transmission of another DO response can start on the transport channel. It is unclear what is the purpose of splitting a binary into chunks on a channel which no longer can be multiplexed and the only property of a chunk is its size[^10].

  - HTTP has strong support for scalability and caching, but this mostly assumes read-operations from static resources. FDO has no view on immutability or validity of retrieved objects, but this should be taken into consideration to support large-scale usage.

  - HTTP optimisations for performance (e.g. HTTP/2, multiplexing) is largely used for commercial media distribution (e.g. Netflix), and not commonly used by providers of FAIR data

  - Cloud deployment of Web applications give many middleware benefits (Scalability, Distribution, Access transparancy, Location transparancy) – it is unclear how DOIP as a custom protocol would perform in a cloud setting as most of this infrastructure assumes HTTP as the protocol.

  - Programmatically the Web is rather unstructured as middleware, as there are many implementation choices. Usually it is undeclared what to expect for a given URI/service, and programmers follow documented examples for a particular service rather than automated programmatic exploration across providers. This mean one can consider the Web as an ecosystem of smaller middlewares with commonalities.

  - Many providers of FAIR Linked Data also provide programmatic REST API endpoints, e.g. [UNIPROT](https://www.uniprot.org/help/programmatic_access), [ChEMBL](https://chembl.gitbook.io/chembl-interface-documentation/web-services), but keeping the FAIR aspects such as retrieving metadata in such a scenario may require combining different services using multiple formats and identifier conventions.

<div id="tbl:fdo-web-middleware">

| Quality | FDO w/ DOIP | Web w/ Linked Data |
| :------ | :---------- | :----------------- |
| **Openness**: *framework enable extension of applications*    | FDOs can be cross-linked using PIDs, pointing to multiple FDO endpoints. Custom DOIP operations can be exposed, although it is unclear if these can be outside the FDO server. PID minting requires Handle.net prefix subscription, or use of services like [Datacite](https://datacite.org/), [B2Handle](https://eudat.eu/services/userdoc/b2handle).    | The Web is inherently open and made by cross-linked URLs. Participation requires DNS domain purchase (many free alternatives also exists). PID minting can be free using PURL/ARK services, or can use DOI/Handle with HTTP redirects.    |
| **Scalability**: *application should be effective at many different scales*    | No defined methods for caching or mirroring, although this could be handled by backend, depending on exposed FDO operations (e.g. Cordra can scale to multiple backend nodes)    | Cache control headers reduce repeated transfer and assist explicit and transparent proxies for speed-up. HTTP `GET` can be scaled to world-population-wide with Content-Delivery Networks (CDNs), while write-access scalability is typically manage by backend.    |
| **Performance**: *efficient and predictable execution*    | DOIP has been shown moderately scalable to 100 millions of objects, create operation at 900 requests/second. DOIP protocol is reusable for many operations, multiple requests may be answered out of order (by `requestId`). Multiple connections possible. Setup is typically through TCP and TLS which adds latency.    | HTTP traffic is about 10% of global Internet traffic, excluding video and social networks [[Sandvine 2022]]. HTTP 1 connections are serial and reusable, and concurrent connections is common. HTTP/2 adds asynchronous responses and multiplexed streams [[Belshe 2015]] but still has TCP+TLS startup costs. For reduced latency, HTTP/3 [[Bishop 2022]] use QUIC [[Iyengar 2021]] rather than TCP, already adapted heavily (30% of EMEA traffic) of which Instagram & Facebook video is the majority of traffic [[Joras 2020]].    |
| **Distribution transparency**: *application perceived as a consistent whole rather than independent elements.*    | Each FDO is accessed separately along with its components (typically from the same endpoint). FDOs should provide the mandatory kernel metadata fields. FDOs of the same declared type typically share additional attributes (although that schema may not be declared). DOIP does not enforce metadata typing constraints, this need to be established as FDO conventions.    | Each URL accessed separately. Common HTTP headers provide basic metadata, although it is often not reliable. A multitude of schemas and serializations for metadata exists, conventions might be implied by a declared profile or certain media types. Metadata is not always machine findable, may need pre-agreed API URI Templates [[Gregorio 2012]], content-negotiation [[MDN 2023]] or FAIR Signposting [[Van de Sompel 2022]].    |
| **Access transparency**: *local/remote elements accessed similarly*    | FDOs should be accessed through PID indirection, this means difficult to make private test setup. Commonly a fixed DOIP server is used directly, which permits local non-PID identifiers.    | Global HTTP protocol frequently used locally and behind firewalls, but at risk of non-global URIs (e.g. `http://localhost/object/1`) and SSL issues (e.g. self-signed certificates, local CAs)    |
| **Location transparency**: *elements accessed without knowledge of physical location*    | FDOs always accessed through PIDs. Multiple locations possible in Handle system, can expose geo-info.    | PIDs and URL redirects. DNS aliases and IP routing can hide location. Geo-localised servers common for large cloud deployments.    |
| **Concurrency transparency**: *concurrent processing without interference*    | No explicit concurrency measures. FDO kernel metadata can include checksum and date.    | HTTP operations are classified as being stateless/idempotent or not (e.g. `PUT` changes state, but can be repeated on failure), although these constraints are occassionally violated by Web applications. Cache control, `ETag` (e.g. checksum) and modification date in HTTP headers allows detection of concurrent changes on a single resource.    |
| **Failure transparency**: *service provisioning resilient to failures*    | DOIP status codes, e.g. `0.DOIP/Status.104`, additional codes can be added as custom attributes    | HTTP [status codes](https://datatracker.ietf.org/doc/html/rfc7231#section-6.5) e.g. `404 Not Found`, specific meaning of standard codes can be [documented in Open API](https://swagger.io/docs/specification/describing-responses/). Custom codes uncommon.    |
| **Migration transparency**: *allow relocating elements without interfering application*    | Update of PID record URLs, indirection through `0.TYPE/DOIPServiceInfo` (not always used consistently). No redirection from DOIP service.    | HTTP `30x` status codes provide temporary or permanent redirections, commonly used for PURLs but also by endpoints.    |
| **Persistence transparency**: *conceal deactivation/reactivation of elements from their users*    | FDO requires use of PIDs for object persistence, including a tombstone response for deleted objects. There is no guarantee that an FDO is immutable or will even stay the same type (note: Cordra extends DOIP with [version tracking](https://www.cordra.org/documentation/design/object-versioning.html)).    | URLs are not required to persist, although encouraged [[Berners-Lee 1998]]. Persistence requires convention to use PIDs/PURLs and HTTP `410 Gone`. An URL may change its content, change in type may sometimes force new URLs if exposing extensions like `.json`. Memento [[Van de Sompel 2013]] expose versioned snapshots. WebDAV `VERSION-CONTROL` method [[Clemm 2002]] (used by SVN).    |
| **Transaction transparency**: *coordinate execution of atomic/isolated transactions*    | No transaction capabilities declared by FDO or DOIP. Internal synchronisation possible in backend for Extended operations.    | Limited transaction capabilities (e.g. `If-Unmodified-Since`) on same resource. WebDAV [locking mechanisms](https://datatracker.ietf.org/doc/html/rfc4918#section-6) [[Dusseault 2007]] with `LOCK` and `UNLOCK` methods.    |
| **Modularity**: *application as collection of connected/distributed elements*    | FDOs are inheritedly modular using global PID spaces and their cross-references. In practice, FDOs of a given type are exposed through a single server shared within a particular community/institution.    | The Web is inheritently modular in that distributed objects are cross-referenced within a global URI space. In practice, an API’s set of resources will be exposed through a single HTTP service, but modularity enables fine-grained scalability in backend.    |
| **Encapsulation**: *separate interface from implementation. Specify interface as contract, multiple implementations possible*    | Indirection by PID gives separation. FDO principles are protocol independent, although it may be unclear which protocol to use for which FDO (although `0.DOIP/Transport` can be specified after already contacting DOIP). Cordra supports [native DOIP](https://www.cordra.org/documentation/api/doip.html), [DOIP over HTTP](https://www.cordra.org/documentation/api/doip-api-for-http-clients.html) and [Cordra REST API](https://www.cordra.org/documentation/api/rest-api.html))    | HTTP/1.1 semantics can seemlessly upgrade to HTTP/2 and HTTP/3. `http` vs `https` URIs exposes encryption detail[^11]. Implementation details may leak into URIs (e.g. `search.aspx`), countered by deliberate design of URI patterns [[Berners-Lee 1998]]) and PIDs via Persistent URLs (PURL).    |
| **Inheritance**: *Deriving specialised interface from another type*    | DOIP types nested with parents, implying shared FDO structures (unclear if operations are inherited). FDO establishes need for multiple Data Type Registries (e.g. managed by a community for a particular domain). Semantics of type system currently undefined for FDO and DOIP, syntactic types can also piggyback of FDO type’s schema (e.g. [Cordra `$ref`](https://www.cordra.org/documentation/design/schemas.html#schema-references) use of [JSON Schema references](https://json-schema.org/draft/2020-12/json-schema-core.html#references) [[Wright 2022]])    | Syntactically Media Type with multiple suffixes [[Sporny 2023]] (mainly used with `+json`), declaration of subtypes as profiles (RFC6906) . In metadata, semantic type systems (RDFS [[Guha 2014]]), OWL2 [[W3C 2012]], SKOS [[Isaac 2009]]). OpenAPI 3 [[Miller 2021]] [inheritance and Polymorphism](https://spec.openapis.org/oas/v3.1.0#composition-and-inheritance-polymorphism). XML `xsd:schemaLocation` or `xsd:type` [[Thompson 2012]], JSON `$schema` [[Wright 2022]]), JSON-LD `@context` [[Sporny 2020]]. Large number of domain-specific and general ontologies define semantic types, but finding and selecting remains a challenge.    |
| **Signal interfaces**: *asynchronous handling of messages*    | DOIP 2.0 is synchronous, in FDO async operations undefined. Could be handled as custom jobs/futures FDOs    | HTTP/2 [multiplexed streams](https://datatracker.ietf.org/doc/html/rfc7540#section-5) [[Belshe 2015]], Web Sockets [[Rice 2022]], Linked Data Notifications [[Capadisli 2017]], AtomPub [[Gregorio 2007]], SWORD [[Jones 2022]], Micropub [[Parecki 2017]], more typically ad-hoc jobs/futures REST resources    |
| **Operation interfaces**: *defining operations possible on an instance, interface of request/response messages*    | CRUD predefined in DOIP, custom operations through `0.DOIP/Op.ListOperations` (can be FDOs of type `0.TYPE/DOIPOperation`, more typically local identifiers like `"getProvenance"`)    | CRUD predefined in [HTTP methods](https://datatracker.ietf.org/doc/html/rfc7231#section-4.3) [[Fielding 2014b]] , ([extended by registration](https://www.iana.org/assignments/http-methods/http-methods.xhtml)), URI Templates [[Gregorio 2012]], [OpenAPI operations](https://spec.openapis.org/oas/v3.1.0.html#operation-object) [[Miller 2021]], HATEOAS[^12] incl. Hydra [[Lanthaler 2021]], [schema.org Actions], JSON HAL [[Kelly 2016]] & Link headers (RFC8288) [[Nottingham 2017]]    |
| **Stream interfaces**: *operations that can handle continuous information streams*    | Undefined in FDO. DOIP can support multiple byte stream elements (need custom FDO type to determine stream semantics)    | HTTP 1.1 [[Fielding 2014a]] [chunked transfer](https://datatracker.ietf.org/doc/html/rfc7230#section-4.1), HLS (RFC8216) [[Pantos 2017]], MPEG-DASH [[ISO 23009]]    |

_**Table 4**: Comparing FAIR Digital Object (with the DOIP 2.0 protocol [[DONA 2018]]) and Web technologies (using Linked Data) as middleware infrastructures [[Zarras 2004]]_

</div>

### Assessing FDO against FAIR {#sec:fair-compare}

In addition to having “FAIR” in its name, the FAIR Digital Object guidelines [[Anders 2023]] also include *G3: FDOs must offer compliance with the FAIR principles through measurable indicators of FAIRness*.

Here we evaluate to what extent the FDO guidelines and its implementation with DOIP and Linked Data Platform [[Bonino 2022]] comply with the FAIR principles [[Wilkinson 2016]]. Here we’ve used the RDA’s FAIR Data Maturity Model [[Bahim 2020]] as it has decomposed the FAIR principles to a structured list of FAIR indicators [[Bahim 2020]], importantly considering *Data* and *Metadata* separately. In our interpretation for [Table 5](#tbl:fair-data-maturity-model) we have for simplicity chosen to interpret “data” in FDOs as the associated bytestream of arbitrary formats, with remaining JSON or RDF structures always considered as metadata.

From this evaluation we observe:

  - Linked Data in general is strong on metadata indicators, but LDP approach is weak as it has little concrete metadata guidance.

  - FDO/DOIP are stronger on identifier indicators, while Linked Data approach for identifiers relies on best practices.

  - Indicators on standard protocols (RDA-A1-04M, RDA-A1-04D, RDA-A1.1-01M, RDA-A1.1-01D) favour LDP’s mature standards (HTTP, URI) – the DOIPv2 specification [[DONA 2018]] has currently only a couple of implementations and is expressed informally. The underlying Handle system for PIDs is arguably mature and commonly used by researchers (this article alone references about 80 DOIs), however DOIs are more commonly accessed as HTTP redirects through resolvers like <https://doi.org/> and <http://hdl.handle.net/> rather than the Handle protocol.

  - RDA-A1-02M and RDA-A1-02D highlights access by manual intervention, which is common for http/https URIs, but also using above PID resolvers for DOIP implementation [Cordra](https://www.cordra.org/) (e.g. <https://hdl.handle.net/21.14100/90ec1c7b-6f5e-4e12-9137-0cedd16d1bce>), yet neither LDP, FDO nor DOIP specifications recommends human-readable representations to be provided

  - Neither DOIP nor LDP require license to be expressed (RDA-R1.1-01M, RDA-R1.1-02M, RDA-R1.1-03M), yet this is crucial for re-use and machine actionability of FAIR data and metadata to be legal

  - Machine-understandable types, provenance and data/metadata standards (RDA-R1.1-03M RDA-R1.3-02M, RDA-R1.3-02M, RDA-R1.3-02D) are important for machine actionability, but are currently unspecified for FDOs. [Blanchi 2022b] explores possible machine-readable FDO types, however the type systems themselves have not yet been formalised. Linked Data on the other side have too many semantic and syntactic type systems, making it difficult to write consistent clients.

  - Indicators for FAIR data are weak for either approach, as too much reliance is put on metadata. For instance in Linked Data, given a URL of a CSV file, what is its persistant identifier or license information? Signposting [[Van de Sompel 2015]] can improve findability of metadata using HTTP Link relations, which enable an FDO-like overlay for any HTTP resource. In DOIP, responses for bytestreams can include the data identifier: if that is a PID (not enforced by DOIP), its metadata is accessible.

  - Resolving FDOs via Handle PIDs to the corresponding DOIP server is currently undefined by FDO and DOIP specifications. `0.TYPE/DOIPServiceInfo` lookup is only possible once DOIP server is known.

<div id="tbl:fair-data-maturity-model">

_**Table 5**: Assessing RDA’s FAIR Data Maturity Model  [[RDA 2020],  [Bahim 2020]] (first 2 columns) against the FDO guidelines [[Bonino 2019]], FDO implemented with the protocol DOIPv2 [[DONA 2018]], Linked Data Platform (LDP) [[Bonino 2022]] and examples from Linked Data practices in general.\
(— indicates *Unspecified*, may be possible with additional conventions)_

| FAIR ID    | Indicator | FDO guidelines | FDO/DOIP | FDO/LDP | Linked Data examples |
| :--------- | :-------- | :------------- | :------- | :------ | :------------------- |
| RDA-F1-01M    | Metadata is identified by a persistent identifier    | FDOF4    | Optional *Metadata FDO* w/separate PID    | Content-negotiation to URL, not required to be PID    | Metadata typically don’t have own PID    |
| RDA-F1-01D    | Data is identified by a persistent identifier    | FDOF1    | PIDs required (FDOF1). Handle, DOI.    | FDOF-IR (Identifier Record). PID can be any URI    | “Cool” URIs [[Berners-Lee 1998]], PURL services incl. `purl.org`, `w3id.org`    |
| RDA-F1-02M    | Metadata is identified by a globally unique identifier    | FDOR4 FDOF8    | Optional *Metadata FDO*, unspecified how to indicate    | Content-negotiation to URL    | Not required, content-negotiation can redirect to URL or `Content-Location`. FAIR Signposting.    |
| RDA-F1-02D    | Data is identified by a globally unique identifier    | FDOF1    | All FDOs have PIDs (FDOR1), DOIP uses Handle system    | FDOF-IR (Identifier Record)    | Always accessed by URL    |
| RDA-F2-01M    | Rich metadata is provided to allow discovery    | FDOF2 FDOF4 FDOF8 FDOF9 | FDO has key-value metadata. Unclear how to link to additional metadata.    | FDOF-IR links to multiple metadata records    | RDF-based metadata by content negotiation or FAIR Signposting. Embedded in landing page (RDFa).    |
| RDA-F3-01M    | Metadata includes the identifier for the data    | —    | `id` and `type` are required metadata elements PIDs, also implicit as requests must use PID    | PID only required in FDOF-IR record.    | PID inclusion typical, but often inconsistent (e.g. `www.example.com` vs `example.com`) or missing (use of `<>` as *this* subject)    |
| RDA-F4-01M    | Metadata is offered in such a way that it can be harvested and indexed    | FDOF10    | No, registries not required (except Data Type Registries). Handle registry only searchable by PID.    | —    | Not specified, several registries/catalogues for vocabularies/types (e.g. [NCBO BioPortal]). Indexing by search engines if exposing HTML w/schema.org.    |
| RDA-A1-01M    | Metadata contains information to enable the user to get access to the data    | FDOF3 FDOF6    | Directly by DOIP, but not included in FDO metadata. `handle.net` HTTP resolution may redirect to landing page    | Any property can point to URIs, but unclear if it is data    | Common with clickable “follow your nose” URLs    |
| RDA-A1-02M    | Metadata can be accessed manually (i.e. with human intervention)    | —    | (Cordra HTML landing page from `handle.net` URIs)    | Optional content-negotiation, e.g. by Apache Marmotta, OpenLink Virtuoso    | HTTP content-negotiation to HTML is common    |
| RDA-A1-02D    | Data can be accessed manually (i.e. with human intervention)    | —    | (Cordra HTML landing page from `handle.net` URIs)    | Optional content-negotiation    | Direct download, HTML landing pages common for DOIs    |
| RDA-A1-03M    | Metadata identifier resolves to a metadata record    | FDOF8+FDOF2    | —    | —    | `Content-Location` or HTTP redirection may indicate metadata URI    |
| RDA-A1-03D    | Data identifier resolves to a digital object    | FDOF2    | Required, but frequently not directly resolvable    | Recommended, but any URI acceptable    | Resolvable HTTP/HTTPS URIs are most common, now infrequent URNs are not directly resolvable    |
| RDA-A1-04M    | Metadata is accessed through standardised protocol    | G9 FDOF3    | Retrievable from PID (FDOF3). Informal DOIP standard maintained by DONA Foundation    | LDP standard maintained by W3C, HTTP standards maintained by IETF, FDO components resolved by informal proposals (custom vocabulary, extra HTTP methods) or HTTP content negotiation)    | Formal HTTP standards maintained by IETF, HTTP content negotiation, informal FAIR Signposting    |
| RDA-A1-04D    | Data is accessible through standardised protocol    | G9    | (see above)    | HTTP [[Fielding 2022]]    | HTTP/HTTPS, FTP (now less common), GridFTP [[Allcock 2005]] (for large data), ARK [[Kunze 2022]]    |
| RDA-A1-05D    | Data can be accessed automatically (i.e. by a computer program)    | G4 FDOF3 FDOF6    | Required, but few client libraries    | HTTP `GET`, content-negotiation for `fdof/object`    | Ubiquitous, hundreds of HTTP libraries    |
| RDA-A1.1-01M    | Metadata is accessible through a free access protocol    | G1 G8 G9    | Partially realised: Handle system is open[^13] protocol [[Sun 2003b]]. One server implementation [[CNRI 2022]], free[^14]. One DOIPv2 implementation ([Cordra](https://www.cordra.org/)): free under BSD-like license (not recognised as Open Source). | LDP is open W3C recommendation [[Speicher 2015]]. [Multiple LDP implementations](https://www.w3.org/wiki/LDP_Implementations). | DNS, HTTP, TLS, RDF standards are open, free and universal, large number of Open Source clients and [servers](https://en.wikipedia.org/wiki/Comparison_of_web_server_software).    |
| RDA-A1.1-01D    | Data is accessible through a free access protocol    | G9    | (see above)    | URI, DNS, HTTP, TLS    | URI, DNS, HTTP, TLS. Non-free DRM may be used (e.g. subscription video streaming)    |
| RDA-A1.2-01D    | Data is accessible through an access protocol that supports authentication and authorisation | (FDOR9)    | TLS certificates, `authentication` field (details unspecified)    | Implied    | HTTP authentication, TLS certificates    |
| <span id="RDA-A2-01M" label="RDA-A2-01M">RDA-A2-01M</span> | Metadata is guaranteed to remain available after data is no longer available    | FDOF12    | —    | Unspecified, however FDOF-IR links to separate metadata records    | —    |
| RDA-I1-01M    | Metadata uses knowledge representation expressed in standardised format    | FDOF8    | Required, but not currently defined    | —    | Always implied by use of RDF syntaxes.    |
| RDA-I1-01D    | Data uses knowledge representation expressed in standardised format    | —    | —    | —    | Common (e.g. HDF5, JSON, XML), yet common scientific data formats frequently not standardised    |
| RDA-I1-02M    | Metadata uses machine-understandable knowledge representation    | FDOF8    | Required    | Optional RDF metadata with any vocabulary    | Always implied by use of RDF syntaxes.    |
| RDA-I1-02D    | Data uses machine-understandable knowledge representation    | G4 G7 FDOR2    | No requirements on binary data formats    | Only indirectly, [LDP Basic Container](https://www.w3.org/TR/ldp/#dfn-linked-data-platform-basic-container) reference only information resources    | Common, specially for scientific data formats    |
| RDA-I2-01M    | Metadata uses FAIR-compliant vocabularies    | G3 FDOF10    | Informally required    | Unspecified, implied by use of RDF?    | FAIR practices for LD vocabularies increasingly common, sometimes inconsistent (e.g. PURLs that don’t resolve) or incomplete (e.g. unknown license)    |
| RDA-I2-01D    | Data uses FAIR-compliant vocabularies    | —    | —    | —    | Uncommon, except for some XML and RDF-embedding formats, e.g. Extensible Metadata Platform (XMP) [[ISO 16684]]    |
| RDA-I3-01M    | Metadata includes references to other metadata    | FDOR8    | Implied (attributes to PIDs), currently unspecified if given attribute is value or reference    | —    | By definition (Linked Data reference existing URIs [[W3C 2015]]), `rdfs:seeAlso`, FAIR signposting [[Van de Sompel 2022]] `describedby`    |
| RDA-I3-01D    | Data includes references to other data    | G6 FDOR3 FDOR11    | —    | —    | URL hyperlinks common in several formats (HTML, PDF, JSON, XML).    |
| RDA-I3-02M    | Metadata includes references to other data    | G6 FDOR3 FDOR8    | Implied from custom FDO type’s attribute    | LDP Direct Container members can be any resources    | URI objects are frequently data references, may be indirect via PID    |
| RDA-I3-02D    | Data includes qualified references to other data    | FDOR3 FDOR11    | Only indirectly through FDO metadata    | Indirectly through LDP membership    | Uncommon: Link relations, FAIR Signposting    |
| RDA-I3-03M    | Metadata includes qualified references to other metadata    | (FDOR3)    | Qualification by attribute keys defined per FDO Type    | [LDP Direct Container](https://www.w3.org/TR/ldp/#dfn-linked-data-platform-direct-container)    | Qualifications by property, PROV bundles [[Lebo 2013b]], [schema.org/Role](https://schema.org/Role)    |
| RDA-I3-04M    | Metadata include qualified references to other data    | (FDOR3)    | Qualification by attribute keys defined per FDO type    | [LDP Indirect Container](https://www.w3.org/TR/ldp/#dfn-linked-data-platform-indirect-container)    | Qualifications by property, n-ary indirection (schema.org Role [[Holland 2014]], `prov:specializationOf` [[Lebo 2013a]], OAI-ORE Proxy [[Lagoze 2008]])    |
| RDA-R1-01M    | Plurality of accurate and relevant attributes are provided to allow reuse    | FDOF4    | Required. Kernel metadata attributes desired [[Broeder 2022b]] but not assigned PIDs yet.    | Unspecified. Multiple metadata records can allow multiple semantic profiles.    | Large number of general and domain-specific vocabularies can make it hard to find relevant attributes. Rough consensus on kernel metadata: [schema.org], Dublin Core Terms [[DCMI 2020]], DCAT [[Browning 2020]], FOAF [[Brickley 2014]] |
| RDA-R1.1-01M    | Metadata includes information about the licence under which the data can be reused    | —    | `licenseConditions` URL/PID in kernel metadata [[Broeder 2022b]]    | —    | Dublin Core Terms `dct:license` frequently recommended, frequently not required, e.g. [by DCAT 2](https://www.w3.org/TR/vocab-dcat-2/#Property:distribution_license) [[Browning 2020]]    |
| RDA-R1.1-02M    | Metadata refers to a standard reuse licence    | —    | —    | —    | [SPDX](https://spdx.org/licenses/) and [Creative Commons](https://creativecommons.org/) URIs common, identifiers often inconsistent    |
| RDA-R1.1-03M    | Metadata refers to a machine-understandable reuse licence    | —    | —    | —    | [SPDX documents](https://spdx.dev/resources/use/#documents) uncommon    |
| RDA-R1.2-01M    | Metadata includes provenance information according to community-specific standards    | FDOR9 FDOR10    | Unspecified (some Cordra types add getProvenance methods). PID Kernel attributes?    | —    | W3C PROV-O, PAV    |
| RDA-R1.2-02M    | Metadata includes provenance information according to a cross-community language    | FDOR9 FDOR8    | —    | —    | W3C PROV-O [[Lebo 2013a]], PAV [[Ciccarese 2013]], Dublin Core Terms [[DCMI 2020]]    |
| RDA-R1.3-01M    | Metadata complies with a community standard    | FDOR10 FROR8    | (Emerging, e.g. DiSSCo Digital Specimen [[Hardisty 2022]])    | —    | Common, e.g. DCAT 2 [[Browning 2020]], BioSchemas [[Gray 2017]]    |
| RDA-R1.3-01D    | Data complies with a community standard    | (FDOR3)    | —    | —    | Common, HTTP use registered IANA [media types](https://www.iana.org/assignments/media-types/media-types.xhtml), additional scientific file formats frequently not standardised or identified    |
| RDA-R1.3-02M    | Metadata is expressed in compliance with a machine-understandable community standard    | FDOF4 FDOF10    | Recommended                                                                                                                                                                                       14    | —    | Common practice for ontologies, specially in bioinformatics, e.g. [NCBO BioPortal], Darwin Core [[Wieczorek 2012]]    |
| RDA-R1.3-02D    | Data is expressed in compliance with a machine-understandable community standard    | (FDOR2)    | No, FDO is typed but data can be any bytestream    | —    | Occassionally, (e.g. [GFF3](https://github.com/The-Sequence-Ontology/Specifications/blob/master/gff3.md), [FITS](https://fits.gsfc.nasa.gov/fits_standard.html), [ESRI](https://www.loc.gov/preservation/digital/formats/fdd/fdd000280.shtml))    |

</div>


### EOSC Interoperability Framework {#sec:eosc}

The European Open Science Cloud (EOSC) is a large EU initiative to promote Open Science by implementing a joint research infrastructure by federating existing and new services and focusing on interoperability, accessability, best practices as well as technical infrastructure [[Ayris 2016]]. The EOSC Interoperability Framework[^74] [[Corcho 2021]] details the principles for creating a common way to achieve interoperability between all digital aspects of research activities in EOSC, including data, protocols and software. The recommendations are realized through 4 layers, Technical (e.g. protocols), Semantic (e.g. metadata models), Organisational (e.g. recommendations) and Legal (e.g. agreements), with a particular aim to address the FAIR interoperability principles and building on the concept of FAIR Digital Objects.

[^74]: EOSC-IF has since been expanded on by an EOSC report [[Åkerström 2024](https://doi.org/10.5281/zenodo.10843882)], which references the preprint of this article.

As covered in our [introduction](#sec:introduction), EOSC proposes FAIR Digital Objects as a way to improve interoperability, for instance invoked by scientific workflows, carried by metadata frameworks and semantic artefacts. Therefore we here find it important to summarize how FDO and Linked Data can help satisfy the EOSC requirements.

In [Table 6](#tbl:eosc) we review the EOSC Interoperability Framework (EOSC IF) recommendations, and evaluate to what extent they are addressed by the principles of FDO and Linked Data or their common implementations.

Firstly, we observe that the EOSC IF recommendations are at a high level, mainly affecting governance and practices by communities. This *Organizational* level is also highlighted by the FDO recommendations, for instance the FDO Typing [[Lannom 2022a]] propose a governance structure to recognize community-endorsed services. While these community aspects are not mandated by Linked Data practices, best practices have become established for aspects like ontology development [[Norris 2021]]. EOSC IF’s *Technical* layer is likewise at a architecturally high level, such as service-level agreements, but also highlight PID policies which is strongly required by FDO, while Linked Data communities choose PID practices separately. The recommendations for the *Semantic* layer are largely already implemented by Linked Data practices, yet for FDO mostly consist of encouragements. For instance *clear definitions of semantic concepts* is required by FDO guidelines, but how to technically define them has not been formalised by FDO specifications.

The *Legal* layer of interoperability is perhaps the one most emphasised by EOSC, by enabling collaboration across organizational barriers to joinly build a research infrastructure, but this is an area that both FDO and Linked Data are relatively weak in directly supporting. The EOSC IF recommendations in this layer are largely related to governance practices and metadata, for instance licensing, privacy and usage policies; these are also essential for cross-institutional and cross-repository access of FAIR objects.

Likewise, search and indexing is important FAIR aspect for Findability, but is poorly supported globally by FDO and Linked Data. Efforts such as Open Research Knowledge Graph (ORKG) [[Jaradeh 2019]], DataCite’s PID Graph [[Fenner 2019]] and Google Knowledge Graph [[Singhal 2012]] have improved programmatic findability to some degree, however not significantly for domain-specific semantic artefacts, currently scattered across multiple semantic catalogues [[Corcho 2023]]. There is a strong role for organizations like EOSC to provide such broader registries, moving beyond scholarly output metadata federations. The [EOSC Marketplace](https://marketplace.eosc-portal.eu/) has for instance recently been expanded to include training material, software and data sources.

<div id="tbl:eosc">

_**Table 6**: Assessing EOSC Interoperability Framework [[Corcho 2021], [sec 3.6](https://op.europa.eu/o/opportal-service/download-handler?identifier=d787ea54-6a87-11eb-aeb5-01aa75ed71a1&format=pdf#page=29)] against the FDO guidelines [[Bonino 2019]] and Linked Data practices._

| Layer | Recommendation | FDO | Linked Data |
| :---- | :------------- | :-- | :---------- |
| Technical    | Open Specification    | FDO specifications are semi-open, process gradually more transparent    | Open and transparent standard processes through W3C & IETF    |
| Technical    | Common security & privacy framework    | Unspecified    | TLS for encryption, multiple approaches for single-sign-on (e.g. ORCID, Life Science Login). Privacy largely unspecified.    |
| Technical    | Easy SLAs for service providers    | Unspecified    | None    |
| Technical    | Access data in different formats    | None formalised, custom operations or relations    | Content-negotiation, `rel=alternate` relations    |
| Technical    | Coarse-grained/fine-grained search tools    | Freetext `0.DOIP/Op.Search` on local DOIP, no federation    | Coarse-grained e.g. [Google Dataset Search](https://datasetsearch.research.google.com/), fine-grained (e.g. federated SPARQL) require detailed vocabulary/metadata insight |
| Technical    | Clear PID policy    | Strong FDO requirements, tends towards Handle system.    | Not required, different communities set policies    |
| Semantic    | Clear definitions for concepts/metadata/schemas    | Required by FDO requirements, but not yet formalised    | Ontologies, SKOS, OWL    |
| Semantic    | Semantic artefacts w/ open licenses    | All artefacts are PIDs, license not yet required by kernel metadata    | Open License is best practice for ontology publishing    |
| Semantic    | Documentation for each semantic artefact    | No direct rendering from FDO, no requirement for human-readable description    | Ontology rendering, content-negotiation    |
| Semantic    | Repositories of artefacts    | Required, but not formalised    | Bioontologies, otherwise not usually federated    |
| Semantic    | Repositories w/ clear governance    | Recommended    | Largely self-governed repositories, if well-established may have clear governance.    |
| Semantic    | Minimal metadata model for federated discovery    | Kernel metadata [[Broeder 2022b]] based on RDA recommendations [[Weigel 2018]]. | DCAT, schema.org, Dublin Core    |
| Semantic    | Crosswalks from minimal metadata model    | FDO Typing recommends referencing existing type definitions, but not as separate crosswalks    | Multiple crosswalks for common metadata models, but frequently not in semantic format    |
| Semantic    | Extensibility options for diciplinary metadata    | Communities encouraged to establish own types    | Extensible by design, domain-specific metadata may be at different granularity    |
| Semantic    | Clear protocols/building blocks for federation/harvesting of artefact catalogues | Collection types not yet defined    | SWORD, OAI-PMH    |
| Organisational | Interoperability-focused rules of participation recommendations    | Recommended    | Implied only by some communities, tendency to specialise    |
| Organisational | Usage recommendations of standardised data formats    | None    | None – but common for metadata (e.g. JSON-LD)    |
| Organisational | Usage recommendations of vocabularies    | Recommended by community    | Common (see [RDMKit](https://rdmkit.elixir-europe.org/metadata_management))    |
| Organisational | Usage recommendations of metadata    | Recommended by community    | RO-Crate, Bioschemas    |
| Organisational | Management of permanent organization names/functions    | Handle owner, but unclear contact. Contact info in DOIP service provider    | ROR. DCAT contacts.    |
| Legal    | Standardised human and machine-readable licenses    | None    | [SPDX](https://spdx.org/licenses/), but not that frequently used    |
| Legal    | Permissive licenses for metadata (CC0, CC-BY-4.0)    | Undefined    | Both CC0, CC-BY-4.0 common, e.g. in DCAT    |
| Legal    | Different licenses for different parts    | Each part as separate FDO can have separate license    | DCAT, RO-Crate, Named graphs for splitting metadata    |
| Legal    | Mark expired/inexistent copyright    | Undefined    | Unclear, semantics assume copyright valid    |
| Legal    | Mark orphaned data    | Tombstone for deleted data, but no owner of DOIP server means FDO disappears    | Frequently data and endpoint has no known maintainer, archiving in common repositories becoming common    |
| Legal    | List recommended licenses    | Undefined    | Best practice recommendations    |
| Legal    | Track license evolution for dataset    | Undefined    | Versioning with PAV/PROV/DCAT    |
| Legal    | Policy/guidance for patent/trade secrets violation    | Undefined    | Undefined, legal owner may be specified. [ODRL](https://www.w3.org/TR/2018/REC-odrl-vocab-20180215/) can express policies.    |
| Legal    | GDPR compliance for personal data    | Undefined    | Undefined    |
| Legal    | Restrict access/use if legally required    | By transport protocol (undefined by FDO/DOIP)    | Diverging approaches, typically landing pages w/ auth\&auth or click-thru    |
| Legal    | Harmonised terms-of-use    | Undefined    | Undefined    |
| Legal    | Alignment between EOSC and national legislation    | Not applicable    | Not applicable    |

</div>

## Discussion {#sec:discussion}

We have evaluated the FAIR Digital Object concept using multiple frameworks, and contrasted FDO against existing experiences from Linked Data on the Web. In this section we discuss the implications of this evaluation, and propose how these two approaches can be better combined.

### Framework evaluation {#sec:framework-evaluation}

Having considered FDO and the Web architecture [as interoperability frameworks](#sec:interoperability-compare), we observe that neither are magic bullets, but each bring different aspects of interoperability. The Web comes with a large degree of flexibility and openness, however this means interoperability can suffer as services have different APIs and data models, although with common patterns. This is also true for Linked Data on the Web, with many overlapping ontologies and frequent inconsistencies in resolution mechanisms; although somewhat alleviated in recent years by schema.org becoming common metadata model for semantic markup inline in Web pages. The Web is based on a common HTTP protocol which has remained stable architecturally throughout its 32 years of largely backwards-compatible evolution. FDO on the other side sets down multiple rigid rules for identifiers, types, methods etc. that are advanterous for interoperability and predictability for FAIR consumption. Yet there is a large degree of freedom in how the FDO rules can be implemented by a given community, for instance there is no common metadata model or identifier resolution mechanism, and DOIP is just one possible transport method for FDOs, which itself does not enforce these rules.

When evaluating FDO implementations [against the FDO guidelines](#sec:doip-fdo-compare) we see that several technical pieces and community practices still need to be developed and further defined, for instance the FDO type system, how to declare FDO actions, how to resolve persistent identifiers, or how to know which pattern of FDO composition is used. Achieving fully interoperable FAIR Digital Objects would require further convergence on implementation practices, and it is not given that this needs to diverge from the established Web architecture. It is not clear from FDO guidelines if moving from HTTP/DNS to DOIP/Handle as a way to expose distributed digital objects will benefit FAIR practitioners, when both approaches require additional equably implementable restrictions and conventions, such as using persistent identifiers or pre-defining an object’s type.

Considering this, by comparing FDO and Web [as middleware](#sec:middleware) we saw that programmatic access to digital objects, a core promise of FDO, is not particularly improved by the use of the protocol DOIP as compared to HTTP, e.g. lack of concurrency and transparancy. Recent updates to HTTP have added many features needed for large-scale usage such as video streaming services (e.g. caching, multiplexing, cloud deployments), and having the option to transparently apply these also to FDOs seems like a strong incentive. Many programmatic features for distributed objects are however missing or needing custom extensions in both aspects, such as transactions, asynchronous operations and streaming.

By assessing FDO [against the FAIR principles](#sec:fair-compare) we found that both FDO implementations are underspecified in several aspects (licences, provenance, data references, data vocabularies, metadata persistence). While there are implementations of each of these in general Linked Data examples, there is no single set of implementation guides that fully realizes the FAIR principles. *FAIRification* efforts like the FAIR Cookbook [[Rocca-Serra 2023]] and FAIR Implementation Profiles [[Schultes 2020]] are bringing existing practices together, but there remains a potential role for FDO in giving a coherent set of implementation practices that can practically achieve FAIR. Significant effort, also within EOSC, is now moving towards FAIR metrics [[Devaraju 2021]], which in practice need to make additional assumptions on how FAIR principles are implemented, but these are not always formalised [[Wilkinson 2022]] nor can they be taken to be universally correct [[Verburg 2023]]. Given that most of the existing FAIR guides and assessment tools are focused on Web and Linked Data, it would be reasonable for FDO to then provide a profile of such implementation choices that can achieve best of both worlds.

EOSC has been largely supportive of FDO, FAIR and related services. By contrasting the [EOSC Interoperability Framework](#sec:eosc-interoperability-framework) with FDO, we found that there are important dimensions that are not solved at a technical level, but through organization collaboration, legal requirements and building community practices. FDO recommendations highlight community aspects, but at the same time the largest FAIR communities in many science domains are already producing and consuming Linked Data. Just as the Linked Data community has a challenge in convincing more research fields to use Semantic Web technologies, FDO currently need to build many new communities in areas that have shown interest in that approach (e.g. material science). It may be advantageous for both these effort to be aligned and jointly promoted under the EOSC umbrella.

### What does FDO mean for Linked Data? {#sec:what-does-it-mean-for-linked-data}

The FAIR Digital Object approach raises many important points for Linked Data practictioners. At first glance, the explicit requirements of FDOs may seem to be easy to furfill by different parts of the Semantic Web Cake [[Berners-Lee 2000]], as has previously been proposed [[Soiland-Reyes 2022a]]. However, this deeper investigation, based on multiple frameworks, highlights that the openness and variability of how Linked Data is deployed can make it difficult to achieve the FDO goals without significant effort.

While RDF and Linked Data have been suggested as prime candidates for making FAIR data, we argue that when different developers have too many degrees of freedom (such as serialization formats, vocabularies, identifiers, navigation), interoperability is hampered – this makes it hard for machines to reliably consume multiple FAIR resources across repositories and data providers. Indeed, this may be one reason why the initial FDO effort steered away from Linked Data approaches, but now seems in a danger of opening the many same degrees of freedom within FDO.

We therefore identify the need for a new explicit FDO profile of Linked Data that sets pragmatic constraints and stronger recommendations for consistent and developer-friendly deployment of digital objects. Such a combination of efforts could utillise both the benefits of mature Semantic Web technologies (e.g. federated knowledge graph queries and rich validation) and data management practices that follow FDO guidance in order to grow an ecosystem of machine-actionable objects. It is beyond the scope of this work to detail such a profile, but we suggest the following potential key aspects:

  - Use HTTP(S) as protocol.
  - Use URIs as identifiers, with persistent identifier promises.
  - Provide consistent identifier resolution that does not require heuristics.
  - Common core metadata model.
  - References are always URIs, and should be persistent identifiers.
  - Types, attributes and actions are self-defined by their identifier.
  - Use Web approaches directly where possible, rather than wrap in a new model.

The FAIR and Linked Data communities likewise need to recognize the need for simpler, more pragmatic approaches that make it easier for FAIR practitioners to adapt the technologies with "just enough" semantics.

## Conclusion {#sec:conclusion}

In this work, we have considered FAIR Digital Objects (FDO) as a potential distributed object system for FAIR data and compared it with established Web approaches focusing on Linked Data. We have described the background of the Semantic Web and FAIR Digital Objects, and evaluated both using multiple conceptual frameworks.

We find that both FDO and Linked Data approaches can significantly benefit from each-other and should be aligned further. Namely, Linked Data proponents need to make their technologies more approachable, agreeing on predictable and consistent implementations of FAIR principles.

The FDO recommendations show that FAIR thinking in this regard need to move beyond data publishing and into machine actionability across digital objects, and with broader community consensus. As flexibility for extensions is a necessary ingredient alongside rigidity for core concepts, the FDO community likewise need to settle on directly implementable specifications rather than just guidelines, and avoid making similar mistakes as learnt by early Semantic Web adopters.

By implementing the goals of FAIR Digital Objects with the mature technology stack developed for Linked Data, EOSC research infrastructures and researchers in general can create and use FAIR machine-actionable research outputs for decades to come.

## Acknowledgments 

This work was funded by the European Union programmes *Horizon 2020* under grant agreements H2020-INFRAEDI-02-2018 [823830](https://doi.org/10.3030/823830) ([BioExcel-2](https://bioexcel.eu/)), H2020-INFRAEOSC-2018-2 [824087](https://doi.org/10.3030/824087) ([EOSC-Life](https://www.eosc-life.eu/)) and *Horizon Europe* under grant agreements HORIZON-INFRA-2021-EMERGENCY-01 [101046203](https://doi.org/10.3030/101046203) ([BY-COVID](https://by-covid.eu/)), HORIZON-INFRA-2021-EOSC-01 [101057388](https://doi.org/10.3030/101057388) ([EuroScienceGateway](https://eurosciencegateway.eu/)), HORIZON-INFRA-2021-EOSC-01-05 [101057344](https://doi.org/10.3030/101057344) ([FAIR-IMPACT](https://fair-impact.eu/)), HORIZON-INFRA-2021-TECH-01 [101057437](https://doi.org/10.3030/101057437) ([BioDT](https://biodt.eu/)), HORIZON-CL4-2021-HUMAN-01-01 [101070305](https://doi.org/10.3030/101070305) ([ENEXA](https://enexa.eu/)) and by UK Research and Innovation (UKRI) under the UK government’s *Horizon Europe funding guarantee* grants [10038963](https://gtr.ukri.org/projects?ref=10038963) (EuroScienceGateway), [10038992](https://gtr.ukri.org/projects?ref=10038992) (FAIR-IMPACT), [10038930](https://gtr.ukri.org/projects?ref=10038930) (BioDT).


We would like to acknowledge the [FAIR Digital Object Forum](https://fairdo.org/) community and working groups, where SSR and CG are members.

Views and opinions expressed in this work are those of the authors only and do not necessarily reflect those of the funded projects, FAIR Digital Object Forum, European Union nor the European Commission. 


## Author contributions

Contributions to this article according to the [CASRAI CRediT](https://credit.niso.org/) taxonomy:

  - Stian Soiland-Reyes  
    Conceptualization, Formal Analysis, Funding acquisition, Investigation, Methodology, Writing – original draft, Writing – review & editing

  - Carole Goble  
    Funding acquisition, Supervision, Writing – review & editing

  - Paul Groth  
    Conceptualization, Methodology, Supervision, Writing – review & editing


[^1]: For a brief introduction to DOIP 2.0, see [[CNRI 2023a]]
    
[^2]: URIs [[Berners-Lee 2005]] are generalised forms of URLs that include locator-less identifiers such as ISBN book numbers (URNs). The distinction between locator-full and locator-less identifiers have weakened in recent years [[OCLC 2010]], for instance DOI identifiers now are commonly expressed with the prefix `https://doi.org/` rather than as URNs with `info:doi:` given that the URL/URN gap has been bridged by HTTP resolvers and the use of Persistent Identifiers (PIDs) [[Juty 2011]]. RDF 1.1 formats use Unicode to support *IRI*s [[Dürst 2005]], which extends URIs to include international characters and domain names.

[^3]: URIs can also identify *non-information resources* for any kind of physical object (e.g. people), such identifiers can resolve with `303 See Other` redirections to a corresponding *information resources* [[Sauermann 2008]].    

[^5]: In RDF, each triple represent an edge that is named using its property URI, and the nodes are subject/object as URIs, blank nodes or (for objects) typed literal values [[Schreiber 2014]].    

[^6]: *Datasets* that distribute RDF graphs should not be confused with [*RDF Datasets*](https://www.w3.org/TR/rdf11-concepts/#section-dataset) used for partitioning *named graphs*.
    

[^7]: Presumably this large uptake of JSON-LD is mainly for the purpose of Search Engine Optimisation (SEO), with typically small amounts of metadata which may not constitute Linked Data as introduced above, however, this deployment nevertheless constitute machine-actionable structured data.
    
[^8]: For further background on FDO implemented with Linked Data see [[Bonino 2022], [Soiland-Reyes 2022c]]
    
[^9]: Newer [[Anders 2023]] renames `FDOF*` to `FDOR*` but follows same ordering.

[^10]: Although it is possible with `0.DOIP/Op.Retrieve` to request only particular individual elements of an DO (e.g. one file), unlike HTTP’s `Range` request, it is not possible to select individual chunks of an element’s bytestream.

[^11]: The `http` protocol (port 80) can in theory also upgrade [[Khare 2000]] to TLS encryption, as commonly used by [Internet Printing Protocol](https://www.rfc-editor.org/rfc/rfc8010.html#section-8.2) for `ipp` URIs, but on the Web, best practice is explicit `https` (port 443) URLs to ensure following links stay secure.
    
[^12]:   HATEOAS: Hypermedia as the Engine of Application State [[Fielding 2000]], an important element of the REST architectural style.
    
[^13]: The `Handle.net` system was previously covered by software patent [US6135646A](https://patents.google.com/patent/US6135646A/en) which [expired](https://circleid.com/posts/20161025_selling_dona_snake_oil_at_the_itu#11461) in 2013.

[^14]: The [Handle.net public license](http://www.handle.net/HNRj/HNR-9-License.pdf) is not OSI-approved [[ 2022]] as an open source license – it includes usage restrictions and requires Service Agreements. It is not a DOIP requirement to host a local Handle instance, e.g. EOSC provides the [B2HANDLE](https://sp.eudat.eu/catalog/resources/fc6b2d30-09cd-4c25-b71a-7bc6de77910c) service for acquiring Handle prefixes.

[^15]: An equivalent SKOS mappping [[Isaac 2009]] is provided as part of the [RO-Crate for this article](https://w3id.org/ro/doi/10.5281/zenodo.8075229) [[Soiland-Reyes 2023]].


References 
==========

[Albertoni 2023]: https://www.w3.org/TR/2023/WD-vocab-dcat-3-20230307/ "Data Catalog Vocabulary (DCAT)- Version 3"
\[Albertoni 2023\]
Riccardo Albertoni, David Browning, Simon Cox, Alejandra Gonzalez Beltran, Andrea Perego, Peter Winstanley (2023):\
**Data Catalog Vocabulary (DCAT)- Version 3**.\
<https://www.w3.org/TR/2023/WD-vocab-dcat-3-20230307/>

[Allcock 2005]: https://marketing.globuscs.info/production/strapi/uploads/gridftp_final_cca95d9e12.pdf "The Globus Striped GridFTP Framework and Server"
\[Allcock 2005\] William Allcock, John Bresnahan, Rajkumar Kettimuthu, Michael Link, Catalin Dumitrescu, Ioan Raicu, Ian Foster (2005):\
**The Globus Striped GridFTP Framework and Server**.\
*SC '05: Proceedings of the 2005 ACM/IEEE Conference on Supercomputing*,
Seattle, WA, USA, IEEE\
<https://doi.org/10.1109/sc.2005.72>

[Anders 2022]: https://doi.org/10.5281/zenodo.7825630 "PR-PIDProfileAttributes: FDO PID profiles & attributes"
\[Anders 2022\]
Ivonne Anders, Maggie Hellström, Sharif Islam, Thomas Jejkal, Larry Lannom, Ulrich Schwardmann, Peter Wittenburg (2022):\
**FDO PID profiles & attributes**\
*FDO Specification Documents* PR-PIDProfileAttributes-2.1-20221017\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825630>

[Anders 2023]: https://doi.org/10.5281/zenodo.7782262 "PR-RequirementSpec: FAIR Digital Objects Forum FDO requirement specifications"
\[Anders 2023\]
<small>Ivonne Anders, Christophe Blanchi, Daan Broder, Maggie Hellström, Sharif
Islam, Thomas Jejkal, Larry Lannom, Karsten Peters-von Gehlen, Robert
Quick, Alexander Schlemmer, Ulrich Schwardmann, Stian Soiland-Reyes,
George Strawn, Dieter van Uytvanck, Claus Weiland, Peter Wittenburg,
Carlo Zwölf</small> (2023):\
**FAIR Digital Objects Forum FDO requirement specifications**. Version 3.0.\
George Strawn, Peter Wittenburg (eds.)\
*FDO Specification Documents* PR-RequirementSpec-3.0\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7782262>

[ANSI 2017]: http://www.openarchives.org/rs/1.1/resourcesync "ANSI/NISO Z39.99-2017, ResourceSync Framework Specification"
\[ANSI 2017\]
ANSI/NISO (2017):\
**ANSI/NISO Z39.99-2017, ResourceSync Framework Specification**.\
*National Information Standards Organization ResourceSync Standing Committee*.\
<https://doi.org/10.3789/ansi.niso.z39.99-2017>\
<http://www.openarchives.org/rs/1.1/resourcesync>

[Ayris 2016]: https://op.europa.eu/o/opportal-service/download-handler?identifier=2ec2eced-9ac5-11e6-868c-01aa75ed71a1&format=pdf "Realising the European open science cloud"
\[Ayris 2016\]
Paul Ayris, Jean-Yves Berthou, Rachel Bruce, Stefanie Lindstaedt, Anna Monreale, Barend Mons, Yasuhiro Murayama, Caj Södergård, Klaus Tochtermann, Ross Wilkinson (2016):
**Realising the European Open Science Cloud**.
First report and recommendations of the Commission high level expert group on the European Open Science Cloud. \
*Publications Office of the EU*\
<https://doi.org/10.2777/940154>

[Bahim 2020]: https://doi.org/10.5334/dsj-2020-041 "The FAIR data maturity model: An approach to harmonise FAIR assessments"
\[Bahim 2020\]
Christophe Bahim, Carlos Casorrán-Amilburu, Makx Dekkers, Edit Herczog,
Nicolas Loozen, Konstantinos Repanas, Keith Russell, Shelley Stall
(2020):\
**The FAIR data maturity model: An approach to harmonise FAIR assessments**.\
*Data Science Journal* **19**(1)\
<https://doi.org/10.5334/dsj-2020-041>

[Baker 2019]: http://shex.io/shex-primer/ "Shape Expressions (ShEx) 2.1 Primer"
\[Baker 2019\]
Thomas Baker, Eric Prud'hommeaux (2019):\
**Shape Expressions (ShEx) 2.1 Primer**.\
<http://shex.io/shex-primer/> (accessed 26 May 2022)

[Belshe 2015]: https://www.rfc-editor.org/rfc/rfc7540.html "RFC 7540: Hypertext Transfer Protocol Version 2 (HTTP/2)"
\[Belshe 2015\]
Mike Belshe, Roberto Peon, Martin Thomson (2015):\
**Hypertext Transfer Protocol Version 2 (HTTP/2)**\
*RFC Editor*, RFC 7540\
<https://doi.org/10.17487/rfc7540>

[Berners-Lee 1998]: https://www.w3.org/Provider/Style/URI "Cool URIs don't change"
\[Berners-Lee 1998\]
Tim Berners-Lee (1998):\
**Cool URIs don't change**.\
*Style Guide for online hypertext*, W3C\
<https://www.w3.org/Provider/Style/URI>

[Berners-Lee 1999]: https://identifiers.org/isbn/9780062515865 "Weaving the Web: The original design and ultimate destiny of the World Wide Web by its inventor"
\[Berners-Lee 1999\]
Tim Berners-Lee, Mark Fischetti (1999):\
**Weaving the Web: The original design and ultimate destiny of the World Wide Web by its inventor**.\
[ISBN 978-0-06-251586-5](https://identifiers.org/isbn/9780062515865)

[Berners-Lee 2000]: https://www.w3.org/2000/Talks/1206-xml2k-tbl/slide10-0.html "Semantic Web on XML"
\[Berners-Lee 2000\]
Tim Berners-Lee (2000):\
**Semantic Web on XML** (slide 10).\
*XML 2000*, Washington DC, 2000-12-06.\
<https://www.w3.org/2000/Talks/1206-xml2k-tbl/slide10-0.html> (accessed
24 January 2023)

[Berners-Lee 2005]: https://www.rfc-editor.org/rfc/rfc3986.html "RFC 3986: Uniform Resource Identifier (URI): Generic Syntax"
\[Berners-Lee 2005\]
Tim Berners-Lee, Roy T. Fielding, Larry M. Masinter (2005):\
**Uniform Resource Identifier (URI): Generic Syntax**.\
*RFC Editor*, RFC 3986\
<https://doi.org/10.17487/rfc3986>

[Berners-Lee 2006]: https://www.w3.org/DesignIssues/LinkedData.html "Linked Data"
\[Berners-Lee 2006\]
Tim Berners-Lee (2006):\
**Linked Data**\
*Design Issues*, W3C\
<https://www.w3.org/DesignIssues/LinkedData.html>

[Bernstein 2016]: https://dl.acm.org/doi/pdf/10.1145/2890489 "A new look at the semantic web"
\[Bernstein 2016\]
Abraham Bernstein, James Hendler, Natalya Noy (2016):\
**A new look at the semantic web**.\
*Communications of the ACM* **59**(9)\
<https://doi.org/10.1145/2890489>

[Bishop 2022]: https://www.rfc-editor.org/rfc/rfc9114.html "RFC 9114: HTTP/3"
\[Bishop 2022\]
Mike Bishop (2022):\
**HTTP/3**\
*RFC Editor*, RFC 9114\
<https://doi.org/10.17487/rfc9114>

[Bizer 2009]: https://doi.org/10.4018/jswis.2009081901 "Linked data - the story so far"
\[Bizer 2009\]
Christian Bizer, Tom Heath, Tim Berners-Lee (2009):\
**Linked data - the story so far**.\
*International journal on Semantic Web and information systems*
**5**(3)\
<https://doi.org/10.4018/jswis.2009081901>

[Blanchi 2022a]: https://doi.org/10.5281/zenodo.7825549 "PEN-FDO-Upload: FDO -- upload of FDO"
\[Blanchi 2022a\]
Christophe Blanchi, Daan Broeder, Thomas Jejkal, Islam Sharif, Alexander Schlemmer, Dieter van Uytvanck, Peter Wittenburg (2022):\
**FDO -- upload of FDO**.\
*FDO Specification Documents* PEN-FDO-Upload-1.1-20221017\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825549>

[Blanchi 2022b]: https://doi.org/10.5281/zenodo.7825572 "WD-Implementation-of-Attributes Implementation of attributes, types, profiles and registries"
\[Blanchi 2022b\]
Christophe Blanchi, Maggie Hellström, Larry Lannom, Andreas Pfeil, Ulrich Schwardmann, Peter Wittenburg (2022):\
**Implementation of attributes, types, profiles and registries**.\
*FDO Specification Documents*
WD-Implementation-of-Attributes-0.4-20230314\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825572>

[Bonino 2016]: https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability "FAIR Data points supporting big data interoperability"
\[Bonino 2016\]
Luiz Olavo Bonino Da Silva Santos, Mark D. Wilkinson, Arnold Kuzniar, Rajaram Kaliyaperumal, Mark Thompson, Michel Dumontier, Kees Burger (2016):\
**FAIR Data points supporting big data interoperability**.\
*Enterprise interoperability in the digitized and networked factory of the future*, 
Martin Zelm, Guy Doumeingts, Joao Pedro Mendonça (eds.).\
iSTE Press.\
[ISBN 978-1-84704-044-2](http://www.iste.co.uk/book.php?id=1073)
[[preprint](https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability)]

[Bonino 2019]: https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx "FAIR digital object framework"
\[Bonino 2019\]
Luiz Bonino, Oeter Wittenburg, Bonnie Carroll, Alex Hardisty, Mark Leggott, Carlo Zwölf (2019):\
**FAIR digital object framework**.\
FDOF technical implementation guideline.\
*Group of European Data Experts in RDA (GEDE-RDA)*\
<https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx>

[Bonino 2022]: https://fairdigitalobjectframework.org/ "FAIR Digital Object Framework Documentation"
\[Bonino 2022\]
Luiz Olavo Bonino da Silva Santos, Giancarlo Guizzardi, Tiago Prince Sales (2022):\
**FAIR Digital Object Framework Documentation**\
<https://fairdigitalobjectframework.org/> (accessed 26 May 2022)

[Brickley 2014]: http://xmlns.com/foaf/spec/ "FOAF Vocabulary Specification"
\[Brickley 2014\]
Dan Brickley, Libby Miller (2014):\
**FOAF Vocabulary Specification**.\
<http://xmlns.com/foaf/spec/> (accessed 26 May 2022)

[Broeder 2022a]: https://drive.google.com/file/d/1laIw7MtdTMSBGXrcfHznklSpqxxotD34 "FDO glossary november 2022"
\[Broeder 2022a\]
Daan Broeder, Peter Wittenburg (2022):\
**FDO glossary november 2022**.\
*FDO Specification Documents* (internal draft)\
FAIR Digital Objects Forum\
<https://hdl.handle.net/20.500.14132/fdo-spec-docs>
(accessed 2 February 2023)

[Broeder 2022b]: https://doi.org/10.5281/zenodo.7825693 "PR-FDO-KernelAttributesAndMetadata: FDO -- kernel attributes & metadata"
\[Broeder 2022b\]
Daan Broeder, Peter Wittenburg, Ivonne Anders, Karsten Peters-von Gehlen (2022):\
**FDO -- kernel attributes & metadata**.\
*FDO Specification Documents*
PR-FDO-KernelAttributesAndMetadata-2.0-20221017\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825693>

[Browning 2020]: https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/ "Data Catalog Vocabulary (DCAT) - Version 2"
\[Browning 2020\]
David Browning, Peter Winstanley, Andrea Perego, Simon Cox, Riccardo Albertoni, Alejandra Gonzalez Beltran (2020):\
**Data Catalog Vocabulary (DCAT)** - Version 2.\
*W3C Recommendation*\
<https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/>

[Capadisli 2017]: https://www.w3.org/TR/2017/REC-ldn-20170502/ "Linked Data Notifications"
\[Capadisli 2017\]
Sarven Capadisli, Amy Guy, eds. (2017):\
**Linked Data Notifications**.\
_W3C Recommendation_\
<https://www.w3.org/TR/2017/REC-ldn-20170502/>

[Carriero 2020]: https://doi.org/10.3233/ssw200033 "The landscape of ontology reuse approaches"
\[Carriero 2020\]
Valentina Anita Carriero, Marilena Daquino, Aldo Gangemi, Andrea Giovanni Nuzzolese, Silvio Peroni, Valentina Presutti, Francesca Tomasi (2020):\
**The landscape of ontology reuse approaches**.\
*Applications and practices in ontology design, extraction, and
reasoning*\
<https://doi.org/10.3233/ssw200033>

[Ciccarese 2013]: https://doi.org/10.1186/2041-1480-4-37 "PAV ontology: Provenance, authoring and versioning"
\[Ciccarese 2013\]
Paolo Ciccarese, Stian Soiland-Reyes, Khalid Belhajjame, Alasdair JG Gray, Carole Goble, Tim Clark (2013):\
**PAV ontology: Provenance, authoring and versioning**.\
*Journal of Biomedical Semantics* **4**(1):37\
<https://doi.org/10.1186/2041-1480-4-37>

[Clemm 2002]: https://www.rfc-editor.org/rfc/rfc3253.html "RFC 3253: Versioning Extensions to WebDAV"
\[Clemm 2002\]
Geoffrey M. Clemm, Jim Amsden, Tim Ellison, Christopher Kaler, Jim Whitehead (2002):\
**Versioning Extensions to WebDAV** (Web Distributed Authoring and Versioning).\
*RFC Editor*, RFC 3253\
<https://doi.org/10.17487/rfc3253>

[CNRI 2022]: https://www.handle.net/download_hnr.html "Handle.Net Software"
\[CNRI 2022\]
CNRI (2022):\
**Handle.Net Software**.\
<https://www.handle.net/download_hnr.html> (accessed 24 January 2023)

[CNRI 2023a]: https://www.cordra.org/documentation/api/doip.html "DOIP and Examples"
\[CNRI 2023a\]
CNRI (2023):\
**DOIP and Examples**\
*Cordra® Software Technical Manual Version 2.5.0*\
Corporation for National Research Initiatives.\
<https://www.cordra.org/documentation/api/doip.html> (accessed 14 June
2023)

[CNRI 2023b]: https://www.cordra.org/documentation/api/doip-api-for-http-clients.html "DOIP API for HTTP Clients"
\[CNRI 2023b\]
CNRI (2023):\
**DOIP API for HTTP Clients**\
*Cordra® Software Technical Manual Version 2.5.0*\
Corporation for National Research Initiatives.\
<https://www.cordra.org/documentation/api/doip-api-for-http-clients.html>
(accessed 13 June 2023)

[Corcho 2021]: https://doi.org/10.2777/620649 "EOSC Interoperability Framework"
\[Corcho 2021\]
Oscar Corcho, Magnus Eriksson, Krzysztof Kurowski, Milan Ojsteršek, Christine Choirat, Mark Sanden, Frederik Coppens, EOSC Executive Board
(2021):\
**EOSC Interoperability Framework**.\
*Publications Office of the EU*\
<https://doi.org/10.2777/620649>

[Corcho 2023]: https://doi.org/10.48550/arXiv.2305.06746 "A maturity model for catalogues of semantic artefacts"
\[Corcho 2023\]
Oscar Corcho, Fajar J. Ekaputra, Ivan Heibi, Clement Jonquet, Andras Micsik, Silvio Peroni, Emanuele Storti (2023):\
**A maturity model for catalogues of semantic artefacts**.\
*arXiv* 2305.06746 \[cs.DL\]\
<https://doi.org/10.48550/arXiv.2305.06746>

[CWFR 2021]: https://osf.io/3rekv/ "Canonical Workflow Frameworks for Research"
\[CWFR 2021]
CWFR Group (2021)\
**Canonical Workflow Frameworks for Research: Position Paper**\
Alex Hardisty, Peter Wittenburg (eds.). 
_OSF_
<https://osf.io/3rekv/>

[DCMI 2020]: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/2020-01-20/ "DCMI Metadata Terms"
\[DCMI 2020\]
DCMI Usage Board (2020):\
**DCMI Metadata Terms**.\
DCMI Recommendation\
<https://www.dublincore.org/specifications/dublin-core/dcmi-terms/2020-01-20/>

[Delgado 2016]: https://doi.org/10.1007/978-3-319-31861-5_1 "An Interoperability Framework and Distributed Platform for Fast Data Applications"
\[Delgado 2016\]
José Carlos Martins Delgado (2016):\
**An Interoperability Framework and Distributed Platform for Fast Data Applications**.\
*Data Science and Big Data Computing*\
<https://doi.org/10.1007/978-3-319-31861-5_1>

[Devaraju 2021]: https://doi.org/10.5334/dsj-2021-004 "From conceptualization to implementation: FAIR assessment of research data objects"
\[Devaraju 2021\]
Anusuriya Devaraju, Mustapha Mokrane, Linas Cepinskas, Robert Huber, Patricia Herterich, Jerry de Vries, Vesa Akerman, Hervé L'Hours, Joy Davidson, Michael Diepenbroek (2021):\
**From conceptualization to implementation: FAIR assessment of research data objects**.\
*Data Science Journal* **20** \
<https://doi.org/10.5334/dsj-2021-004>

[DOI 2017]: https://www.doi.org/doi_handbook/3_Resolution.html "DOI Handbook - Resolution"
\[DOI 2017\]
DOI (2017):\
**DOI Handbook - Resolution**.\
*DOI Handbook*\
International DOI Foundation\
<https://doi.org/10.1000/182>\
<https://www.doi.org/doi_handbook/3_Resolution.html>

[DONA 2018]: https://hdl.handle.net/0.DOIP/DOIPV2.0 "Digital object interface protocol specification, version 2.0"
\[DONA 2018\]
DONA (2018):\
**Digital object interface protocol specification, version 2.0**.\
*DONA Foundation*\
<https://hdl.handle.net/0.DOIP/DOIPV2.0>

[Dürst 2005]: https://www.rfc-editor.org/rfc/rfc3987.html "RFC 3987: Internationalized Resource Identifiers (IRIs)"
\[Dürst 2005\]
Martin J. Dürst, Michel Suignard (2005):\
**Internationalized Resource Identifiers (IRIs)**.\
*RFC Editor*, RFC 3987\
<https://doi.org/10.17487/rfc3987>

[Dusseault 2007]: https://www.rfc-editor.org/rfc/rfc4918.html "RFC 4918: HTTP Extensions for Web Distributed Authoring and Versioning (WebDAV)"
\[Dusseault 2007\]
Lisa M. Dusseault (2007):\
**HTTP Extensions for Web Distributed Authoring and Versioning**
(WebDAV).\
*RFC Editor*, RFC 4918.\
<https://doi.org/10.17487/rfc4918>

[Ekuan 2023]: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design "Web API design best practices"
\[Ekuan 2023\]
Martin Ekuan, Mick Alberts, Tim Sherer, Udi Dahan, Mike Kistler et al.  (2023):\
**Web API design best practices**.\
*Azure Architecture Center*\
<https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design>
(accessed 24 January 2023)

[FDO 2022]: https://fairdo.org/specifications/ "FDO Specification Documents"
\[FDO 2022]
FDO (2022):\
**FDO Specification Documents - November 2022**  
*FAIR Digital Objects Forum*  
<https://hdl.handle.net/20.500.14132/fdo-spec-docs>\
<https://fairdo.org/specifications/> (accessed 2 February 2023)

[Fenner 2019]: https://doi.org/10.5438/jwvf-8a66 "Introducing the PID graph"
\[Fenner 2019\]
Martin Fenner, Amir Aryani (2019):\
**Introducing the PID graph**.\
*DataCite Blog*\
<https://doi.org/10.5438/jwvf-8a66>

[Fensel 2011]: https://doi.org/10.1007/978-3-642-19193-0 "Semantic Web Services"
\[Fensel 2011]
Dieter Fensel, Federico Michele Facca, Elena Simperl, Ioan Toma (2011):\
**Semantic Web Services**\
<https://doi.org/10.1007/978-3-642-19193-0>

[Fielding 1999]: https://www.rfc-editor.org/rfc/rfc2616.html "RFC 2616: Hypertext Transfer Protocol -- HTTP/1.1"
\[Fielding 1999\]
Roy T. Fielding, Jim Gettys, Jeffrey Mogul, Henrik Frystyk Nielsen, Larry M Masinter, Paul J. Leach, Tim Berners-Lee (1999):\
**Hypertext Transfer Protocol -- HTTP/1.1**.\
*RFC Editor*, RFC 2616\
<https://doi.org/10.17487/rfc2616>

[Fielding 2000]: https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm "Architectural styles and the design of network-based software architectures"
\[Fielding 2000]
Roy Thomas Fielding (2000):\
**Architectural styles and the design of network-based software architectures**\
Doctoral Thesis, *University of California*, Irvine.\
<https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm> (accessed
28 June 2022) 

[Fielding 2014a]: https://doi.org/10.17487/rfc7230 "RFC 7230: Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing"
\[Fielding 2014a\]
Roy T. Fielding, Julian Reschke (2014):\
**Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing**\
*RFC Editor*, RFC 7230\
<https://doi.org/10.17487/rfc7230>

[Fielding 2014b]: https://doi.org/10.17487/rfc7231 "RFC 7231: Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content"
\[Fielding 2014b\]
Roy T. Fielding, Julian Reschke (2014):\
**Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content**\
*RFC Editor*, RFC 7231\
<https://doi.org/10.17487/rfc7231>

[Fielding 2017]: https://doi.org/10.1145/3106237.3121282 "Reflections on the REST architectural style and \"principled design of the modern web architecture\" (impact paper award)"
\[Fielding 2017\]
Roy T. Fielding, Richard N. Taylor, Justin R. Erenkrantz, Michael M.  Gorlick, Jim Whitehead, Rohit Khare, Peyman Oreizy (2017):\
**Reflections on the REST architectural style and \"principled design of the modern web architecture\" (impact paper award)**.\
*Proceedings of the 2017 11th joint meeting on foundations of software engineering - ESEC/FSE 2017*, New York, New York, USA.\
<https://doi.org/10.1145/3106237.3121282>

[Fielding 2022]: https://doi.org/10.17487/rfc9110 "RFC 9110: HTTP Semantics"
\[Fielding 2022\]
Roy T. Fielding, Mark Nottingham, Julian Reschke (2022):\
**HTTP Semantics**\
*RFC Editor*, RFC 9110\
<https://doi.org/10.17487/rfc9110>

[Gayo 2017]: https://doi.org/10.2200/s00786ed1v01y201707wbe016 "Validating RDF Data"
\[Gayo 2017\]
Jose Emilio Labra Gayo, Eric Prud'hommeaux, Iovka Boneva, Dimitris Kontokostas (2017):\
**Validating RDF Data**.\
*Synthesis Lectures on the Semantic Web: Theory and Technology* **7**\
<https://doi.org/10.2200/s00786ed1v01y201707wbe016>

[Goble 2008]: https://doi.org/10.1016/j.jbi.2008.01.008 "State of the nation in data integration for bioinformatics"
\[Goble 2008\]
Carole Goble, Robert Stevens (2008):\
**State of the nation in data integration for bioinformatics**.\
*Journal of Biomedical Informatics* **41**(5)\
<https://doi.org/10.1016/j.jbi.2008.01.008>

[Gray 2017]: https://ceur-ws.org/Vol-1963/paper579.pdf "Bioschemas: From potato salad to protein annotation"
\[Gray 2017\]
Alasdair Gray, Carole Goble, Rafael Jimenez, Bioschemas Community (2017):\
**Bioschemas: From potato salad to protein annotation**.\
*Proceedings of the ISWC 2017 posters & demonstrations and industry tracks co-located with 16th international semantic web conference (ISWC 2017)*, Vienna, Austria.\
*CEUR Workshop Proceedings* **1963**\
<https://ceur-ws.org/Vol-1963/paper579.pdf>

[Gregorio 2007]: https://doi.org/10.17487/rfc5023 "RFC 5023: The Atom Publishing Protocol"
\[Gregorio 2007\]
Joe Gregorio, Bill de hÓra (2007):\
**The Atom Publishing Protocol**.\
*RFC Editor*, RFC 5023\
<https://doi.org/10.17487/rfc5023>

[Gregorio 2012]: https://doi.org/10.17487/rfc6570 "RFC 6570: URI Template"
\[Gregorio 2012\]
Joe Gregorio, Roy T. Fielding, Marc Hadley, Mark Nottingham, David Orchard (2012):\
**URI Template**. \
*RFC Editor*, RFC 6570\
<https://doi.org/10.17487/rfc6570>

[Groth 2014]: https://doi.org/10.1016/j.websem.2014.03.003 "API-centric Linked Data integration: The Open PHACTS Discovery Platform case study"
\[Groth 2014\]
Paul Groth, Antonis Loizou, Alasdair J. G. Gray, Carole Goble, Lee
Harland, Steve Pettifer (2014):\
**API-centric Linked Data integration: The Open PHACTS Discovery Platform case study**.\
*Journal of Web Semantics* **29**\
<https://doi.org/10.1016/j.websem.2014.03.003>

[Guha 2014]: http://www.w3.org/TR/rdf-schema/ "RDF Schema 1.1"
\[Guha 2014\]
Ramanathan Guha, Dan Brickley (2014):\
**RDF Schema 1.1**.\
*W3C Recommendation*\
<http://www.w3.org/TR/rdf-schema/>

[Hardisty 2022]: https://doi.org/10.1162/dint_a_00134 "The Specimen Data Refinery"
\[Hardisty 2022\]
Alex Hardisty, Paul Brack, Carole Goble, Laurence Livermore, Ben Scott, Quentin Groom, Stuart Owen, Stian Soiland-Reyes (2022):\
**The Specimen Data Refinery**: A Canonical Workflow Framework and FAIR Digital Object Approach to Speeding up Digital Mobilisation of Natural History Collections.\
*Data Intelligence* **4**(2)\
<https://doi.org/10.1162/dint_a_00134>

[Hasnain 2018]: https://doi.org/10.1007/978-3-319-98192-5_60 "Assessing FAIR data principles against the 5-star open data principles"
\[Hasnain 2018\]
Ali Hasnain, Dietrich Rebholz-Schuhmann (2018):\
**Assessing FAIR data principles against the 5-star open data principles**.\
*The Semantic Web: ESWC 2018 satellite events*, Heraklion, Crete,
Greece, 2018-06-03/--07\
<https://doi.org/10.1007/978-3-319-98192-5_60>

[Hausenblas 2012]: http://5stardata.info/ "5-Star Open Data"
\[Hausenblas 2012\]
Michael Hausenblas et al. (2012):\
**5-star Open Data**.\
<http://5stardata.info/> (accessed 24 January 2023)

[Hellström 2022]: https://doi.org/10.5281/zenodo.7825686 "PR-Granularity: FDO -- granularity, versioning, mutability"
\[Hellström 2022\]
Maggie Hellström, Carlo Zwölf, Peter Wittenburg (2022):\
**FDO -- granularity, versioning, mutability**.\
*FDO Specification Documents* PR-Granularity-2.2-20221017\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825686>

[Holland 2014]: http://blog.schema.org/2014/06/introducing-role.html "Introducing 'Role'"
\[Holland 2014\]
Vicki Tardif Holland, Jason Johnson (2014):\
**Introducing 'Role'**.\
*schema blog*\
<http://blog.schema.org/2014/06/introducing-role.html>

[Horrocks 2002]: https://doi.org/10.1007/3-540-48005-6 "The Semantic Web --- ISWC 2002"
\[Horrocks 2002\]
Ian Horrocks, James Hendler, eds. (2002):\
**The Semantic Web --- ISWC 2002**\
First International Semantic Web Conference, Sardinia, Italy, June 9-12, 2002\
<https://doi.org/10.1007/3-540-48005-6>

[Hu 2011]: https://identifiers.org/isbn/9783642210334 "How matchable are four thousand ontologies on the semantic web"
\[Hu 2011\]
Wei Hu, Jianfeng Chen, Hang Zhang, Yuzhong Qu (2011):\
**How matchable are four thousand ontologies on the semantic web**.\
In Grigoris Antoniou, Marko Grobelnik, Elena Simperl, Bijan Parsia, Dimitris Plexousakis, Pieter De Leenheer, Jeff Pan,eds.,\
*The semantic web: Research and applications*, pp. 290--304\
[ISBN 978-3-642-21033-4](https://identifiers.org/isbn/9783642210334)

[Isaac 2009]: https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/ "SKOS Simple Knowledge Organization System Primer"
\[Isaac 2009\]
Antoine Isaac, Ed Summers (2009):\
**SKOS Simple Knowledge Organization System Primer**.\
W3C Note\
<https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/>

[Islam 2023]: https://doi.org/10.3233/FC-230001 "FAIR digital objects, persistent identifiers and machine actionability"
\[Islam 2023\]
Sharif Islam (2023):\
**FAIR digital objects, persistent identifiers and machine actionability**.\
*FAIR Connect* **1**(1)\
<https://doi.org/10.3233/FC-230001>

[ISO 16684]: https://www.iso.org/standard/75163.html "ISO 16684-1:2019 --- graphic technology --- extensible metadata platform (XMP)"
\[ISO 16684\]
ISO (2019):\
**ISO 16684-1:2019 --- graphic technology --- extensible metadata platform (XMP)** 
--- part 1: Data model, serialization and core properties.\
ISO standard\
<https://www.iso.org/standard/75163.html>

[ISO 23009]: https://www.iso.org/standard/83314.html "ISO/IEC 23009-1:2022 --- information technology --- dynamic adaptive streaming over HTTP (DASH)"
\[ISO 23009\]
ISO/IEC (2022):\
**ISO/IEC 23009-1:2022 --- information technology --- dynamic adaptive streaming over HTTP (DASH)** --- 
part 1: Media presentation description and segment formats.\
ISO standard\
<https://www.iso.org/standard/83314.html>

[ITU-T X.1255]: https://www.itu.int/rec/T-REC-X.1255-201309-I "X.1255 : Framework for Discovery of Identity Management Information"
\[ITU-T X.1255\]
ITU-T (2013):\
**X.1255 : Framework for Discovery of Identity Management Information**.\
*Series X: Data networks, open system communications and security* ITU-T X.1255\
The International Telecommunication Union (ITU).\
<https://www.itu.int/rec/T-REC-X.1255-201309-I>

[Ivonne 2023]: https://doi.org/10.5281/zenodo.7824714 "FAIR digital object technical overview"
\[Ivonne 2023\]
Ivonne Anders, Christophe Blanchi, Daan Broder, Maggie Hellström, Sharif
Islam, Thomas Jejkal, Larry Lannom Larry, Karsten Peters-von Gehlen,
Robert Quick, Alexander Schlemmer, Ulrich Schwardmann, Stian
Soiland-Reyes, George Strawn, Dieter van Uytvanck, Claus Weiland, Peter
Wittenburg, Carlo Zwölf (2023):\
**FAIR digital object technical overview**. Version PEN 2.0.\
*FDO Specification Documents* Full FDO Overview PEN-2.0-v2\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7824714>

[Iyengar 2021]: https://doi.org/10.17487/rfc9000 "RFC 9000: QUIC: A UDP-Based Multiplexed and Secure Transport"
\[Iyengar 2021\]
Jana Iyengar, Martin Thomson (2021):\
**QUIC: A UDP-Based Multiplexed and Secure Transport**.\
*RFC Editor*, RFC 9000\
<https://doi.org/10.17487/rfc9000>

[Jaradeh 2019]: https://doi.org/10.1007/978-3-030-30760-8_31 "Open research knowledge graph: A system walkthrough"
\[Jaradeh 2019\]
Mohamad Yaser Jaradeh, Allard Oelen, Manuel Prinz, Markus Stocker, Sören Auer (2019):\
**Open research knowledge graph: A system walkthrough**.\
*Digital libraries for open knowledge* 348--351.\
<https://doi.org/10.1007/978-3-030-30760-8_31>

[Jones 2022]: https://swordapp.github.io/swordv3/swordv3.html "SWORD 3.0 Specification"
\[Jones 2022\]
Richard Jones, Neil Jefferies (2022):\
**SWORD 3.0 Specification**.\
<https://swordapp.github.io/swordv3/swordv3.html> (accessed 26 May 2022)

[Joras 2020]: https://engineering.fb.com/2020/10/21/networking-traffic/how-facebook-is-bringing-quic-to-billions "How Facebook is bringing QUIC to billions"
\[Joras 2020\]
Matt Joras, Yang Chi (2020):\
**How Facebook is bringing QUIC to billions**.\
*Engineering at Meta*\
<https://engineering.fb.com/2020/10/21/networking-traffic/how-facebook-is-bringing-quic-to-billions>

[Juty 2011]: https://doi.org/10.1093/nar/gkr1097 "Identifiers.org and MIRIAM Registry: Community resources to provide persistent identification"
\[Juty 2011\]
Nick Juty, Nicolas Le Novère, Camille Laibe (2011):\
**Identifiers.org and MIRIAM Registry: Community resources to provide persistent identification**.\
*Nucleic Acids Research* **40**(D1)\
<https://doi.org/10.1093/nar/gkr1097>

[Kahn 1995]: http://www.cnri.reston.va.us/k-w.html "A framework for distributed digital object services"
\[Kahn 1995\]
Robert Kahn, Robert Wilensky (1995):\
**A framework for distributed digital object services** (CNRI).\
<http://www.cnri.reston.va.us/k-w.html> (accessed 9 May 2022)

[Kahn 2006]: https://doi.org/10.1007/s00799-005-0128-x "A framework for distributed digital object services"
\[Kahn 2006\]
Robert Kahn, Robert Wilensky (2006):\
**A framework for distributed digital object services**.\
*International Journal on Digital Libraries* **6**\
<https://doi.org/10.1007/s00799-005-0128-x>

[Kamdar 2017]: https://doi.org/10.3233/sw-160238 "A systematic analysis of term reuse and term overlap across biomedical ontologies"
\[Kamdar 2017\]
Maulik R. Kamdar, Tania Tudorache, Mark A. Musen (2017):\
**A systematic analysis of term reuse and term overlap across biomedical ontologies**.\
*Semantic Web* **8**(6)\
<https://doi.org/10.3233/sw-160238>

[Kelly 2016]: https://datatracker.ietf.org/doc/draft-kelly-json-hal/08/ "JSON Hypertext Application Language"
\[Kelly 2016\]
Mike Kelly (2016):\
**JSON Hypertext Application Language**.\
*Internet Engineering Task Force*\
<https://datatracker.ietf.org/doc/draft-kelly-json-hal/08/>

[Khare 2000]: https://doi.org/10.17487/rfc2817 "RFC 2817: Upgrading to TLS Within HTTP/1.1"
\[Khare 2000\]
Rohit Khare, Scott Lawrence (2000):\
**Upgrading to TLS Within HTTP/1.1**.\
*RFC Editor*, RFC 2817.\
<https://doi.org/10.17487/rfc2817>

[Klein 2014]: https://doi.org/10.1371/journal.pone.0115253 "Scholarly Context Not Found: One in Five Articles Suffers from Reference Rot"
\[Klein 2014\]
Martin Klein, Herbert Van de Sompel, Robert Sanderson, Harihar Shankar, Lyudmila Balakireva, Ke Zhou, Richard Tobin (2014):\
**Scholarly Context Not Found: One in Five Articles Suffers from Reference Rot**.\
*PLOS ONE* **9**(12):e115253\
<https://doi.org/10.1371/journal.pone.0115253>

[Klímek 2019]: https://doi.org/10.3233/SW-180316 "Survey of tools for linked data consumption"
\[Klímek 2019\]
Jakub Klímek, Petr Škoda, Martin Nečaský (2019):\
**Survey of tools for linked data consumption**.\
*Semantic Web* **10**(4)\
<https://doi.org/10.3233/SW-180316>

[Kontokostas 2017]: https://www.w3.org/TR/shacl/ "Shapes Constraint Language (SHACL)"
\[Kontokostas 2017\]
Dimitris Kontokostas, Holger Knublauch (2017):\
**Shapes Constraint Language (SHACL)**.\
*W3C Recommendation*\
<https://www.w3.org/TR/shacl/> (accessed 26 May 2022)

[Kunze 2022]: https://datatracker.ietf.org/doc/draft-kunze-ark/36/ "The ARK Identifier Scheme"
\[Kunze 2022\]
John A. Kunze, Emmanuelle Bermès (2022):\
**The ARK Identifier Scheme**.\
*Internet Engineering Task Force*\
<https://datatracker.ietf.org/doc/draft-kunze-ark/36/>

[Lagoze 2008]: http://www.openarchives.org/ore/1.0/datamodel#Proxies "ORE Specification"
\[Lagoze 2008\]
Carl Lagoze, Herbert Van de Sompel, Pete Johnston, Michael Nelson, Robert Sanderson, Simeon Warner (2008):\
**ORE Specification** - Abstract Data Model.\
*Open Archives Initiative*\
<http://www.openarchives.org/ore/1.0/datamodel#Proxies>

[Lamprecht 2021]: https://doi.org/10.12688/f1000research.54159.1 "Perspectives on automated composition of workflows in the life sciences"
\[Lamprecht 2021\]
<small>Anna-Lena Lamprecht, Magnus Palmblad, Jon Ison, Veit Schwämmle, Mohammad Sadnan Al Manir, Ilkay Altintas, Christopher J. O. Baker, Ammar Ben Hadj Amor, Salvador Capella-Gutierrez, Paulos Charonyktakis, Michael R.  Crusoe, Yolanda Gil, Carole Goble, Timothy J. Griffin, Paul Groth, Hans Ienasescu, Pratik Jagtap, Matúš Kalaš, Vedran Kasalica, Alireza Khanteymoori, Tobias Kuhn, Hailiang Mei, Hervé Ménager, Steffen Möller, Robin A. Richardson, Vincent Robert, Stian Soiland-Reyes, Robert Stevens, Szoke Szaniszlo, Suzan Verberne, Aswin Verhoeven, Katherine Wolstencroft</small> (2021):\
**Perspectives on automated composition of workflows in the life sciences**.\
*F1000Research* **10** (2021):897\
<https://doi.org/10.12688/f1000research.54159.1>

[Sun 2003a]: https://doi.org/10.17487/rfc3650 "RFC 3650: Handle System Overview"
\[Sun 2003a\]
Sam Sun, Larry Lannom, Brian P. Boesch (2003):\
**Handle System Overview**\
*RFC Editor*, RFC 3650\
<https://doi.org/10.17487/rfc3650>

[Sun 2003b]: https://doi.org/10.17487/rfc3652 "RFC 3652: Handle System Protocol (ver 2.1) Specification"
\[Sun 2003b\]
Sam Sun, Sean Reilly, Larry Lannom, Jason Petrone (2003) (2003):\
**Handle System Protocol (ver 2.1) Specification**.\
*RFC Editor*, RFC 3652\
<https://doi.org/10.17487/rfc3652>

[Lannom 2022a]: https://doi.org/10.5281/zenodo.7825703 "PR-ConfigurationTypes FDO configuration types"
\[Lannom 2022a\]
Larry Lannom, Karsten Peters-von Gehlen, Ivonne Anders, Andreas Pfeil, Alexander Schlemmer, Zach Trautt, Peter Wittenburg (2022):\
**FDO configuration types**.\
*FDO Specification Documents* PR-ConfigurationTypes-2.1-20221017\
FAIR Digital Objects Forum\
<https://doi.org/10.5281/zenodo.7825703>

[Lannom 2022b]: https://doi.org/10.5281/zenodo.7824673 "FAIR digital objects roadmap. Version 5 november 2022"
\[Lannom 2022b\]
Larry Lannom, Ulrich Schwardmann, Christophe Blanchi, Ivonne Anders, Claus Weiland, Peter Wittenburg (2022):\
**FAIR digital objects roadmap. Version 5 november 2022**.\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7824673>

[Lannom 2022c]: https://doi.org/10.5281/zenodo.7825599 "PR-TypingFDOs Typing FAIR digital objects"
\[Lannom 2022c\]
Larry Lannom, Ulrich Schwardmann, Cristophe Blanchi, Peter Wittenburg (2022):\
**Typing FAIR digital objects**.\
*FDO Specification Documents* PR-TypingFDOs-2.0-20220608\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825599>

[Lanthaler 2021]: http://www.hydra-cg.com/spec/latest/core/ "Hydra Core Vocabulary"
\[Lanthaler 2021\]
Markus Lanthaler, ed. (2021):\
**Hydra Core Vocabulary**\
Hydra W3C Community Group\
<http://www.hydra-cg.com/spec/latest/core/>

[Lassila 1999]: https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/ "Resource Description Framework (RDF) Model and Syntax Specification"
\[Lassila 1999\]
Ora Lassila, Ralph R. Swick (1999):\
**Resource Description Framework (RDF) Model and Syntax Specification**.\
*W3C Recommendation*\
<https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/>

[Lebo 2013a]: https://www.w3.org/TR/2013/REC-prov-o-20130430/ "PROV-O: The PROV Ontology"
\[Lebo 2013a\]
Timothy Lebo and Deborah McGuinness and Satya Sahoo (2013):\
**PROV-O: The PROV Ontology**.\
*W3C Recommendation*\
<https://www.w3.org/TR/2013/REC-prov-o-20130430/>

[Lebo 2013b]: https://www.w3.org/TR/2013/NOTE-prov-links-20130430/ "Linking Across Provenance Bundles"
\[Lebo 2013b\]
Timothy Lebo, Luc Moreau (2013):\
**Linking Across Provenance Bundles**.\
*W3C Note*\
<https://www.w3.org/TR/2013/NOTE-prov-links-20130430/>

[Liu 2007]: https://www.w3.org/TR/2007/REC-wsdl20-primer-20070626/ "Web Services Description Language"
\[Liu 2007\]
Kevin Liu, David Booth (2007):\
**Web Services Description Language** (WSDL) Version 2.0 Part 0:
Primer.\
*W3C Recommendation*\
<https://www.w3.org/TR/2007/REC-wsdl20-primer-20070626/>

[Loo 2022]: https://doi.org/10.3897/rio.coll.190 "First International Conference on FAIR Digital Objects"
\[Loo 2022\]
Tina Loo, ed. (2022):\
**First International Conference on FAIR Digital Objects**.\
*Research Ideas and Outcomes*\
<https://doi.org/10.3897/rio.coll.190>

[McMurry 2017]: https://doi.org/10.1371/journal.pbio.2001414 "Identifiers for the 21st century"
\[McMurry 2017\]
Julie A McMurry, Nick Juty, Niklas Blomberg, Tony Burdett, Tom Conlin, Nathalie Conte, Mélanie Courtot, John Deck, Michel Dumontier, Donal K Fellows, Alejandra Gonzalez-Beltran, Philipp Gormanns, Jeffrey Grethe, Janna Hastings, Jean-Karim Hériché, Henning Hermjakob, Jon C Ison, Rafael C Jimenez, Simon Jupp, John Kunze, Camille Laibe, Nicolas Le Novère, James Malone, Maria Jesus Martin, Johanna R McEntyre, Chris Morris, Juha Muilu, Wolfgang Müller, Philippe Rocca-Serra, Susanna-Assunta Sansone, Murat Sariyar, Jacky L Snoep, Stian Soiland-Reyes, Natalie J Stanford, Neil Swainston, Nicole Washington, Alan R Williams, Sarala M Wimalaratne, Lilly M Winfree, Katherine Wolstencroft, Carole Goble, Cristopher J Mungall, Melissa A Haendel, Helen Parkinson (2017):  
**Identifiers for the 21st century: How to design, provision, and reuse identifiers to maximize utility and impact of life science data**. *PLOS Biology* **15**(6):e2001414  
<https://doi.org/10.1371/journal.pbio.2001414>

[MDN 2023]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation "HTTP Content negotiation"
\[MDN 2023\]
MDN (2023):\
**HTTP Content negotiation**.\
*Web technology for developers*.\
MDN Web Docs\
<https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation>
(accessed 26 May 2022)

[Meroño-Peñuela 2021a]: https://doi.org/10.1007/978-3-031-01917-3_7 "Conclusion and future challenges"
\[Meroño-Peñuela 2021a\]
Albert Meroño-Peñuela, Pasquale Lisena, Carlos Martínez-Ortiz (2021):\
**Conclusion and future challenges**.\
*Web data apis for knowledge graphs: Easing access to semantic data for
application developers*\
Synthesis Lectures on Data, Semantics, and Knowledge\
<https://doi.org/10.1007/978-3-031-01917-3_7>

[Meroño-Peñuela 2021b]: https://doi.org/10.1007/978-3-031-01917-3_3 "Web data APIs over SPARQL"
\[Meroño-Peñuela 2021b\]
Albert Meroño-Peñuela, Pasquale Lisena, Carlos Martínez-Ortiz (2021):\
**Web data APIs over SPARQL**.\
*Web Data APIs for Knowledge Graphs : Easing access to semantic data for
application developers*, Synthesis Lectures on Data, Semantics, and
Knowledge.\
<https://doi.org/10.1007/978-3-031-01917-3_3>

[Miller 2021]: https://spec.openapis.org/oas/v3.1.0.html "OpenAPI Specifications"
\[Miller 2021\]
Darrel Miller, Jeremy Whitlock, Marsh Gardiner, Mike Ralphson, Ron Ratovsky, Uri Sarid, eds. (2021):\
**OpenAPI Specification** v3.1.0.\
*OpenAPI Initiative*, The Linux Foundation.\
<https://spec.openapis.org/oas/v3.1.0.html> (accessed 21 March 2023)

[Mons 2017]: https://doi.org/10.3233/ISU-170824 "Cloudy, increasingly FAIR; revisiting the FAIR data guiding principles for the European Open Science Cloud"
\[Mons 2017\]
Barend Mons, Cameron Neylon, Jan Velterop, Michel Dumontier, Luiz Olavo Bonino Silva Santos, Mark D. Wilkinson (2017):\
**Cloudy, increasingly FAIR; revisiting the FAIR data guiding principles for the European Open Science Cloud**.\
*Information Services & Use* **37**(1)\
<https://doi.org/10.3233/ISU-170824>

[NCBO BioPortal]: https://bioportal.bioontology.org/ontologies "NCBO BioPortal"
\[NCBO BioPortal\]
**NCBO BioPortal**.\
National Center for Biomedical Ontology\
<https://bioportal.bioontology.org/ontologies> (accessed 26 May 2022)

[Neumann 2021]: https://doi.org/10.1109/TSC.2018.2847344 "An analysis of public REST web service apis"
\[Neumann 2021\]
Andy Neumann, Nuno Laranjeiro, Jorge Bernardino (2021):\
**An analysis of public REST web service apis**.\
*IEEE Transactions on Services Computing* **14**(4)\
<https://doi.org/10.1109/TSC.2018.2847344>

[Norris 2021]: https://doi.org/10.1186/s13326-021-00240-6 "Why and how to engage expert stakeholders in ontology development: Insights from social and behavioural sciences"
\[Norris 2021\]
Emma Norris, Janna Hastings, Marta M. Marques, Ailbhe N. Finnerty Mutlu, Silje Zink, Susan Michie (2021):\
**Why and how to engage expert stakeholders in ontology development: Insights from social and behavioural sciences**.\
*Journal of Biomedical Semantics* **12**\
<https://doi.org/10.1186/s13326-021-00240-6>

[Nottingham 2017]: https://doi.org/10.17487/rfc8288 "RFC 8288: Web Linking"
\[Nottingham 2017\]
Mark Nottingham (2017):\
**Web Linking**.\
*RFC Editor*, RFC 8288\
<https://doi.org/10.17487/rfc8288>

[Nurdiati 2008]: https://purl.utwente.nl/publications/64931 "25 years development of knowledge graph theory: the results and the challenge"
\[Nurdiati 2008\]
Sri Nurdiati, Cornelis Hoede (2008):\
**25 years development of knowledge graph theory: the results and the challenge**.\
Memorandum No. 2/1876\
_University of Twente_\
<https://purl.utwente.nl/publications/64931>

[OCLC 2010]: http://info-uri.info/ "Info URI Registry"
\[OCLC 2010\]
OCLC (2010):\
**\"Info\" URI Registry** (Frozen).\
OCLC\
<http://info-uri.info/> (accessed 24 January 2023)

[OGP]: https://ogp.me/ "The Open Graph protocol"
\[OGP\]
**The Open Graph protocol**.\
<https://ogp.me/> (accessed 26 May 2022)

[OpenStand 2017]: https://open-stand.org/about-us/principles/ "The modern Standards Paradigm"
\[OpenStand 2017\]
OpenStand (2017):\
**The Modern Standards Paradigm** - Five Key Principles.\
<https://open-stand.org/about-us/principles/> (accessed 24 January 2023)

[OSI 2022]: https://opensource.org/licenses "Licences & Standards"
\[OSI 2022\]
OSI (2022):\
**Licenses & Standards**. Open Source Initiative\
<https://opensource.org/licenses> (accessed 24 January 2023)

[Page 2011]: https://doi.org/10.1145/1967428.1967435 "REST and Linked Data"
\[Page 2011\]
Kevin R. Page, David C. De Roure, Kirk Martinez (2011):\
**REST and Linked Data**.\
*Proceedings of the Second International Workshop on RESTful Design -
WS-REST '11*\
<https://doi.org/10.1145/1967428.1967435>

[Pantos 2017]: https://doi.org/10.17487/rfc8216 "RFC 8216: HTTP Live Streaming"
\[Pantos 2017\]
Roger Pantos, William May (2017):\
**HTTP Live Streaming**.\
*RFC Editor*, RFC 8216\
<https://doi.org/10.17487/rfc8216>

[Parecki 2017]: https://www.w3.org/TR/2017/REC-micropub-20170523/ "Micropub"
\[Parecki 2017\]
Aaron Parecki, ed. (2017):\
**Micropub**. *W3C Recommendation*\
<https://www.w3.org/TR/2017/REC-micropub-20170523/>

[Polleres 2020]: https://doi.org/10.3233/SW-190380 "A more decentralized vision for linked data"
\[Polleres 2020\]
Axel Polleres, Maulik Rajendra Kamdar, Javier David Fernández, Tania Tudorache, Mark Alan Musen (2020):\
**A more decentralized vision for linked data**.\
*Semantic Web* **11**(1)\
<https://doi.org/10.3233/SW-190380>

[RDA 2020]: https://doi.org/10.15497/rda00050 "FAIR data maturity model: Specification and guidelines"
\[RDA 2020\]
FAIR Data Maturity Model Working Group (2020):\
**FAIR data maturity model: Specification and guidelines**.\
*Research Data Alliance*\
<https://doi.org/10.15497/rda00050>

[Rescorla 2000]: https://www.rfc-editor.org/rfc/rfc2818.html "RFC 2818: HTTP over TLS"
\[Rescorla 2000\]
Eric Rescorla (2000):\
**HTTP Over TLS**.\
*RFC Editor*, RFC 2818\
<https://doi.org/10.17487/rfc2818>

[Reilly 2009]: https://www.dona.net/doipv1doc "Digital Object Interface Protocol 1.0"
\[Reilly 2009\]
Sean Reilly (2009):\
**Digital Object Interface Protocol Version 1.0**.\
<https://www.dona.net/doipv1doc> (accessed 26 May 2022)

[Riccardi 2022]: https://doi.org/10.1002/jcc.26842 "Towards improved FAIRness of the ThermoML Archive"
\[Riccardi 2022\]
Demian Riccardi, Zachary Trautt, Ala Bazyleva, Eugene Paulechka, Vladimir Diky, Joseph W. Magee, Andrei F. Kazakov, Scott A. Townsend, Chris D Muzny (2022):\
**Towards improved FAIRness of the ThermoML Archive**.\
*Journal of Computational Chemistry* **43**(12)\
<https://doi.org/10.1002/jcc.26842>

[Rice 2022]: https://websockets.spec.whatwg.org/ "WebSockets Standard"
[Rice 2022]
Adam Rice, Ian Hickson, Anne van Kesteren, Yutaka Hirano (2022):\
**WebSockets Standard**.\
*WHATWG*\
<https://websockets.spec.whatwg.org/> (accessed 26 May 2022)

[Rocca-Serra 2023]: https://doi.org/10.1038/s41597-023-02166-3 "The FAIR cookbook - the essential resource for and by FAIR doers"
\[Rocca-Serra 2023\]
<small>Philippe Rocca-Serra, Wei Gu, Vassilios Ioannidis, Tooba Abbassi-Daloii, Salvador Capella-Gutierrez, Ishwar Chandramouliswaran, Andrea Splendiani, Tony Burdett, Robert T. Giessmann, David Henderson, Dominique Batista, Ibrahim Emam, Yojana Gadiya, Lucas Giovanni, Egon Willighagen, Chris Evelo, Alasdair J. G. Gray, Philip Gribbon, Nick Juty, Danielle Welter, Karsten Quast, Paul Peeters, Tom Plasterer, Colin Wood, Eelke van der Horst, Dorothy Reilly, Herman van Vlijmen, Serena Scollen, Allyson Lister, Milo Thurston, Ramon Granell, Gabriel Backianathan, Sebastian Baier, Anne Cambon Thomsen, Martin Cook, Melanie Courtot, Mike d'Arcy, Kurt Dauth, Eva Marin del Piico, Leyla Garcia, Ulrich Goldmann, Valentin Grouès, Daniel J. B. Clarke, Erwan Lefloch, Isuru Liyanage, Petros Papadopoulos, Cyril Pommier, Emiliano Reynares, Francesco Ronzano, Alejandra Delfin-Rossaro, Venkata Sagatopam, Ashni Sedani, Vitaly Sedlyarov, Liubov Shilova, Sukhi Singh, Jolanda Strubel, Kees van Bochove, Zachary Warnes, Peter Woollard, Fuqi Xu, Andrea Zaliani, Susanna-Assunta Sansone</small> (2023):\
**The FAIR cookbook - the essential resource for and by FAIR doers**.\
*Scientific Data* **10**(10)\
<https://doi.org/10.1038/s41597-023-02166-3>

[Sandvine 2022]: https://www.sandvine.com/global-internet-phenomena-report-2022 "Global Internet Phenomena Report"
\[Sandvine 2022\]
Sandvine (2022):\
**Global Internet Phenomena Report**.\
<https://www.sandvine.com/global-internet-phenomena-report-2022>
(accessed 26 May 2022)

[Sauermann 2008]: http://www.w3.org/TR/cooluris/ "Cool URIs for the semantic web"
\[Sauermann 2008\]
Leo Sauermann, Richard Cyganiak, Danny Ayers, Max Völkel (2008):\
**Cool URIs for the semantic web**\
*W3C Interest Group Note*\
<http://www.w3.org/TR/cooluris/>

[schema.org]: https://schema.org/
\[schema\]
**Schema.org**\
<https://schema.org/> (accessed 26 May 2022)

[schema.org Actions]: https://schema.org/docs/actions.html
\[schema Actions\]
**Schema.org Actions**.\
*schema.org*.\
<https://schema.org/docs/actions.html> (accessed 26 May 2022)

[Schreiber 2014]: http://www.w3.org/TR/2014/NOTE-rdf11-primer-20140624 "RDF 1.1 Primer"
\[Schreiber 2014\]
Guus Schreiber, Yves Raimond (2014):\
**RDF 1.1 Primer**.\
*W3C Note*\
<http://www.w3.org/TR/2014/NOTE-rdf11-primer-20140624>

[Schultes 2019]: https://doi.org/10.1007/978-3-030-23584-0_1 "FAIR principles and digital objects: Accelerating convergence on a data infrastructure"
\[Schultes 2019\]
Erik Schultes, Peter Wittenburg (2019):\
**FAIR principles and digital objects: Accelerating convergence on a data infrastructure**.\
*Data analytics and management in data intensive domains*: 20th
international conference, DAMDID/RCDL 2018, Moscow, Russia,
2018-10-09/--12.\
<https://doi.org/10.1007/978-3-030-23584-0_1>
[[preprint](https://doi.org/10.23728/B2SHARE.166A074BFF614A31B05E9DF5BFD9809D)]

[Schultes 2020]: https://doi.org/10.1007/978-3-030-65847-2_13 "Reusable FAIR implementation profiles as accelerators of FAIR convergence"
\[Schultes 2020\]
Erik Schultes, Barbara Magagna, Kristina Maria Hettne, Robert Pergl, Marek Suchánek, Tobias Kuhn (2020):\
**Reusable FAIR implementation profiles as accelerators of FAIR convergence**.\
*International Conference on Conceptual Modeling*, ER 2020: Advances in
Conceptual Modeling, 2022-11-03/--06, Vienna, Austria.\
*Lecture notes in Computer Science* **12584**\
<https://doi.org/10.1007/978-3-030-65847-2_13>

[Schwardmann 2022a]: https://doi.org/10.5281/zenodo.7824796 "PED-DOIPEndorsement DOIP endorsement request"
\[Schwardmann 2022a\]
Ulrich Schwardmann, George Strawn, Robert Quick, Peter Wittenburg (2022):\
**DOIP endorsement request**.\
*FDO Specification Documents* PED-DOIPEndorsement-1.1-20221017\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7824796>

[Schwardmann 2022b]: https://doi.org/10.3897/rio.8.e96014 "Two Examples on How FDO Types can Support Machine and Human Readability"
\[Schwardmann 2022b\]
Ulrich Schwardmann, Tibor Kálmán (2022):\
**Two Examples on How FDO Types can Support Machine and Human Readability**.\
*Research Ideas and Outcomes* **8**\
<https://doi.org/10.3897/rio.8.e96014>

[Semmler 2022]: https://hdl.handle.net/21.14100/2fcf49d3-0608-3373-a47f-0e721b7eaa87 "IPCC DDC: AWI AWI-CM1.1MR model output prepared for CMIP6 CMIP historical"
\[Semmler 2022\]
Tido Semmler, Sergey Danilov, Thomas Rackow, Dmitry Sidorenko, Dirk Barbi, Jan Hegewald, Dmitri Sein, Qiang Wang, Thomas Jung (2022):\
**IPCC DDC: AWI AWI-CM1.1MR model output prepared for CMIP6 CMIP historical**.\
<https://www.wdc-climate.de/ui/entry?acronym=C6CMAWAWMhi>\
<https://hdl.handle.net/21.14100/2fcf49d3-0608-3373-a47f-0e721b7eaa87>

[Singhal 2012]: https://blog.google/products/search/introducing-knowledge-graph-things-not/ "Introducing the knowledge graph: Things, not strings"
\[Singhal 2012]
Amit Singhal (2012):\
**Introducing the knowledge graph: Things, not strings**.\
<https://blog.google/products/search/introducing-knowledge-graph-things-not/>
(accessed 18 May 2023)

[Smith 2007]: https://doi.org/10.1038/nbt1346 "The OBO Foundry: Coordinated evolution of ontologies to support biomedical data integration"
\[Smith 2007\]
<small>Barry Smith, Michael Ashburner, Cornelius Rosse, Jonathan Bard, William Bug, Werner Ceusters, Louis J. Goldberg, Karen Eilbeck, Amelia Ireland, Christopher J. Mungall, Neocles Leontis, Philippe Rocca-Serra, Alan Ruttenberg, Susanna-Assunta Sansone, Richard H. Scheuermann, Nigam Shah, Patricia L. Whetzel, Suzanna Lewis</small> (2007):\
**The OBO Foundry: Coordinated evolution of ontologies to support biomedical data integration**.\
*Nature Biotechnology* **25**(11)\
<https://doi.org/10.1038/nbt1346>

[Soiland-Reyes 2022a]: https://doi.org/10.3897/rio.8.e93937 "Creating lightweight FAIR digital objects with RO-Crate"
\[Soiland-Reyes 2022a\]
Stian Soiland-Reyes, Peter Sefton, Leyla Jael Castro, Frederik Coppens, Daniel Garijo, Simone Leo, Marc Portier, Paul Groth (2022):\
**Creating lightweight FAIR digital objects with RO-crate**.\
*Research Ideas and Outcomes* **10**(8).
<https://doi.org/10.3897/rio.8.e93937>

[Soiland-Reyes 2022b]: https://doi.org/10.3233/ds-210053 "Packaging research artefacts with RO-Crate"
\[Soiland-Reyes 2022b\]
Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):\
**Packaging research artefacts with RO-Crate**.\
*Data Science* **5**(2)\
<https://doi.org/10.3233/ds-210053>

[Soiland-Reyes 2022c]: https://doi.org/10.3897/rio.8.e94501 "Updating linked data practices for FAIR digital object principles"
\[Soiland-Reyes 2022c\]
Stian Soiland-Reyes, Leyla Jael Castro, Daniel Garijo, Marc Portier, Carole Goble, Paul Groth (2022):\
**Updating linked data practices for FAIR digital object principles**.\
*Research Ideas and Outcomes* **10**(8)\
<https://doi.org/10.3897/rio.8.e94501>

[Soiland-Reyes 2023]: https://w3id.org/ro/doi/10.5281/zenodo.8075229 "Comparison tables for evaluating FAIR Digital Object and Linked Data"
\[Soiland-Reyes 2023\]
Stian Soiland-Reyes (2023):  
**Comparison tables for evaluating FAIR Digital Object and Linked Data**.  
RO-Crate. _Zenodo_  
<https://w3id.org/ro/doi/10.5281/zenodo.8075229>  
<https://doi.org/10.5281/zenodo.8075229>

[Speicher 2015]: https://www.w3.org/TR/2015/REC-ldp-20150226/ "Linked data platform 1.0"
\[Speicher 2015\]
Steve Speicher, John Arwe, Ashok Malhotra (2015):\
**Linked data platform 1.0**.\
*W3C Recommendation*\
<https://www.w3.org/TR/2015/REC-ldp-20150226/>

[Sporny 2015]: https://www.w3.org/TR/2015/NOTE-rdfa-primer-20150317/ "RDFa 1.1 Primer"
\[Sporny 2015\]
Manu Sporny, Ivan Herman, Ben Adida, Mark Birbeck (2015):\
**RDFa 1.1 Primer** - Third Edition.\
*W3C Note*\
<https://www.w3.org/TR/2015/NOTE-rdfa-primer-20150317/>

[Sporny 2020]: https://www.w3.org/TR/2020/REC-json-ld11-20200716/ "JSON-LD 1.1"
\[Sporny 2020\]
Manu Sporny, Dave Longley, Gregg Kellogg, Markus Lanthaler, Pierre-Antoine Champin, Niklas Lindström (2020):\
**JSON-LD 1.1**.\
*W3C Recommendation*.\
<https://www.w3.org/TR/2020/REC-json-ld11-20200716/>

[Sporny 2023]: https://datatracker.ietf.org/doc/draft-ietf-mediaman-suffixes/03/ "Media Types with Multiple Suffixes"
\[Sporny 2023\]
Manu Sporny, Amy Guy (2023):\
**Media Types with Multiple Suffixes**.\
Internet Engineering Task Force.\
<https://datatracker.ietf.org/doc/draft-ietf-mediaman-suffixes/03/>

[Stallings 1990]: https://doi.org/10.21954/ou.ro.0000f821 "Handbook of computer-communications standards: The Open Systems (OSI) model and OSI-related standards"
\[Stallings 1990\]
William Stallings (1990):\
**Handbook of computer-communications standards: The Open Systems (OSI) model and OSI-related standards**, 2nd ed.\
Sams.\
[ISBN 978-0-672-22697-7](https://identifiers.org/isbn/9780672226977)

[Stanczyk 1987]: https://doi.org/10.21954/ou.ro.0000f821 "Process modelling for information system description"
\[Stanczyk 1987]
Stefan K. Stanczyk (1987):\
**Process modelling for information system description**.\
*The Open University*\
<https://doi.org/10.21954/ou.ro.0000f821>

[Stefi 2015a]: http://doi.org/10.1007/978-3-319-19593-3_18 "To develop or to reuse? Two perspectives on external reuse in software projects"
\[Stefi 2015a\]
Anisa Stefi, Thomas Hess (2015):\
**To develop or to reuse? Two perspectives on external reuse in software projects**.\
*International Conference of Software Business* (ICSOB 2015), Braga,
Portugal, 2015-06-10/--12.\
*ICSOB 2015: Software business*\
<http://doi.org/10.1007/978-3-319-19593-3_18>

[Stefi 2015b]: https://doi.org/10.18151/7217489 "Do Developers Make Unbiased Decisions? - The Effect of Mindfulness and Not-Invented-Here Bias on the Adoption of Software Components"
\[Stefi 2015b\]
Anisa Stefi (2015):\
**Do Developers Make Unbiased Decisions? - The Effect of Mindfulness and Not-Invented-Here Bias on the Adoption of Software Components**.\
*European Conference on Information Systems* (ECIS 2015), Münster,
Germany, 2015-05-26/--29\
<https://doi.org/10.18151/7217489>

[Thompson 2012]: https://www.w3.org/TR/2012/REC-xmlschema11-1-20120405/ "W3C XML Schema Definition Language"
\[Thompson 2012\]
Henry Thompson, Sandy Gao, David Beech, Murray Maloney, Noah Mendelsohn, Michael Sperberg-McQueen (2012):\
**W3C XML Schema Definition Language** (XSD) 1.1 Part 1: Structures.\
*W3C Recommendation*\
<https://www.w3.org/TR/2012/REC-xmlschema11-1-20120405/>

[Thornton 2019]: https://doi.org/10.1007/978-3-030-21348-0_39 "Using shape expressions (ShEx) to share RDF data models and to guide curation with rigorous validation"
\[Thornton 2019\]
Katherine Thornton, Harold Solbrig, Gregory S. Stupp, Jose Emilio Labra Gayo, Daniel Mietchen, Eric Prud, Andra Waagmeester (2019):\
**Using shape expressions (ShEx) to share RDF data models and to guide curation with rigorous validation**.\
*The Semantic Web: 16th international conference*, (ESWC 2019),
Portorož, Slovenia, 2019-06-02/--06.\
<https://doi.org/10.1007/978-3-030-21348-0_39>

[Tirmizi 2011]: https://doi.org/10.1186/2041-1480-2-s1-s3 "Mapping between the OBO and OWL ontology languages"
\[Tirmizi 2011\]
Syed Tirmizi, Stuart Aitken, Dilvan A. Moreira, Chris Mungall, Juan Sequeda, Nigam H. Shah, Daniel P. Miranker (2011):\
**Mapping between the OBO and OWL ontology languages**.\
*Journal of Biomedical Semantics* **2**:S3\
<https://doi.org/10.1186/2041-1480-2-s1-s3>

[Tupelo-Schneck 2022]: https://www.rd-alliance.org/sites/default/files/Cordra.2022.pdf "Brief Introduction to Cordra & DOIP"
\[Tupelo-Schneck 2022\]
Robert Tupelo-Schneck, Larry Lannom (2022):\
**Brief Introduction to Cordra & DOIP**.\
_RDA FAIR DO Fabric_ \\
<https://www.rd-alliance.org/sites/default/files/Cordra.2022.pdf>

[Turcoane 2014]: https://doi.org/10.55630/dipp.2014.4.11 "Linked data, JSON-LD and the semantics of cultural and scientific heritage"
\[Turcoane 2014\]
Ovidiu Turcoane (2014):\
**Linked data, JSON-LD and the semantics of cultural and scientific heritage**.\
*Digital Presentation and Preservation of Cultural and Scientific
Heritage* **4**\
<https://doi.org/10.55630/dipp.2014.4.11>

[Van de Sompel 2013]: https://doi.org/10.17487/rfc7089 "RFC 7089: HTTP Framework for Time-Based Access to Resource States -- Memento"
\[Van de Sompel 2013\]
Herbert Van de Sompel, Michael Nelson, Robert Sanderson (2013):\
**HTTP Framework for Time-Based Access to Resource States -- Memento**.\
*RFC Editor*, RFC 7089\
<https://doi.org/10.17487/rfc7089>

[Van de Sompel 2015]: https://doi.org/10.1045/november2015-vandesompel "Reminiscing About 15 Years of Interoperability Efforts"
\[Van de Sompel 2015\]
Herbert Van de Sompel, Michael L. Nelson (2015)  
**Reminiscing About 15 Years of Interoperability Efforts**.  
*D-Lib Magazine* **21**(11/12).  
<https://doi.org/10.1045/november2015-vandesompel>

[Van de Sompel 2022]: https://signposting.org/FAIR/ "FAIR Signposting Profile"
\[Van de Sompel 2022\]
Herbert Van de Sompel, Martin Klein, Shawn Jones, Michael L. Nelson, Simeon Warner, Anusuriya Devaraju, Robert Huber, Wilko Steinhoff, Vyacheslav Tykhonov, Luc Boruta, Enno Meijers, Stian Soiland-Reyes, Mark Wilkinson (2022):\
**FAIR Signposting Profile**.\
<https://signposting.org/FAIR/> (accessed 5 January 2023)

[Verborgh 2018]: https://ruben.verborgh.org/blog/2018/12/28/designing-a-linked-data-developer-experience/ "Designing a Linked Data developer experience"
\[Verborgh 2018\]
Ruben Verborgh (2018):\
**Designing a Linked Data developer experience**.\
<https://ruben.verborgh.org/blog/2018/12/28/designing-a-linked-data-developer-experience/>
(accessed 26 May 2022)

[Verborgh 2020]: https://doi.org/10.3233/SW-190372 "The semantic web identity crisis: In search of the trivialities that never were"
\[Verborgh 2020\]
Ruben Verborgh, Miel Vander Sande (2020):\
**The semantic web identity crisis: In search of the trivialities that never were**.\
*Semantic Web* **11**(1)\
<https://doi.org/10.3233/SW-190372>

[Verburg 2023]: https://doi.org/10.5281/zenodo.7848102 "FAIR-IMPACT project response to \"FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons\""
\[Verburg 2023\]
Maaike Verburg, Robert Huber, Clement Jonquet, Daniel Garijo (2023):\
**FAIR-IMPACT project response to \"FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons\"**.\
*Zenodo*\
<https://doi.org/10.5281/zenodo.7848102>

[W3C 2012]: https://www.w3.org/TR/2012/REC-owl2-overview-20121211 "OWL 2 Web Ontology Language Document Overview"
\[W3C 2012\]
W3C OWL Working Group (2012):\
**OWL 2 Web Ontology Language Document Overview** (Second Edition).\
*W3C Recommendation*\
<https://www.w3.org/TR/2012/REC-owl2-overview-20121211>

[W3C 2013]: https://www.w3.org/TR/2013/REC-sparql11-overview-20130321/ "SPARQL 1.1 Overview"
\[W3C 2013]
The W3C SPARQL Working Group (2013):\
**SPARQL 1.1 Overview**.\
*W3C Recommendation*\
<https://www.w3.org/TR/2013/REC-sparql11-overview-20130321/>

[W3C 2015]: https://www.w3.org/standards/semanticweb/data "Linked Data"
\[W3C 2015]
W3C (2015):\
**Linked Data**\
<https://www.w3.org/standards/semanticweb/data> (accessed 26 May 2022)

[W3Tech 2023]: https://w3techs.com/technologies/details/da-jsonld "Usage Statistics of JSON-LD for Websites"
\[W3Tech 2023]
W3Techs 2023:\
**Usage Statistics of JSON-LD for Websites**. 2023-05.\
*W3Techs - World Wide Web Technology Surveys*, Q-Success.\
<https://w3techs.com/technologies/details/da-jsonld> (accessed 18 May
2023)

[Weigel 2018]: https://doi.org/10.15497/rda00031 "RDA Recommendation on PID Kernel Information"
\[Weigel 2018\]
Tobias Weigel, Beth Plale, Mark Parsons, Gabriel Zhou, Yu Luo, Ulrich Schwardmann, Robert Quick, Margareta Hellström, Kei Kurakawa (2018):\
**RDA Recommendation on PID Kernel Information**\
*Research Data Alliance*\
<https://doi.org/10.15497/rda00031>

[WHATWG 2023]: https://html.spec.whatwg.org/multipage/microdata.html "Microdata"
\[WHATWG 2023]
WHATWG (2023):\
**Microdata**.\
*HTML Living Standard*\
<https://html.spec.whatwg.org/multipage/microdata.html> (accessed 13
June 2023)

[Weiland 2022a]: https://doi.org/10.5281/zenodo.10943371 "FAIR Digital Objects Forum Document Standards"
\[Weiland 2022a\]
C. Weiland, U. Schwardmann, P. Wittenburg, C. Kirkpatrick, R. Hanisch, Z. Trautt, C. Weiland, U. Schwardmann, P. Wittenburg (2022):\
**FAIR Digital Objects Forum Document Standards**
WD-DocProcessStd-1.1-20220129  
*FAIR Digital Objects Forum*  
<https://doi.org/10.5281/zenodo.10943371>

[Weiland 2022b]: https://doi.org/10.5281/zenodo.7825650 "FDO machine actionability"
\[Weiland 2022b]
Claus Weiland, Sharif Islam, Daan Broder, Ivonne Anders, Peter Wittenburg (2022):\
**FDO machine actionability**. Version 2.2\
PR-MachineActionDef-2.2-20221119\
*FAIR Digital Objects Forum*\
<https://doi.org/10.5281/zenodo.7825650>

[Wieczorek 2012]: https://doi.org/10.1371/journal.pone.0029715 "Darwin Core: An Evolving Community-Developed Biodiversity Data Standard"
\[Wieczorek 2012\]
John Wieczorek, David Bloom, Robert Guralnick, Stan Blum, Markus Döring, Renato Giovanni, Tim Robertson, David Vieglais (2012):\
**Darwin Core: An Evolving Community-Developed Biodiversity Data Standard**.\
*PLOS ONE* **7**(1):e29715.
<https://doi.org/10.1371/journal.pone.0029715>

[Wilkinson 2016]: https://doi.org/10.1038/sdata.2016.18 "The FAIR Guiding Principles for scientific data management and stewardship"
\[Wilkinson 2016\]
<small>Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas Blomberg, Jan-Willem Boiten, Luiz Bonino da Silva Santos, Philip E. Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas, Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard Finkers, Alejandra Gonzalez-Beltran, Alasdair J. G. Gray, Paul Groth, Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A. C. 't Hoen, Rob Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E. Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe Rocca-Serra, Marco Roos, Rene van Schaik, Susanna-Assunta Sansone, Erik Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz, Mark Thompson, Johan van der Lei, Erik van Mulligen, Jan Velterop, Andra Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, Barend Mons</small> (2016):\
**The FAIR Guiding Principles for scientific data management and stewardship**.\
*Scientific Data* **3**(1)\
<https://doi.org/10.1038/sdata.2016.18>

[Wilkinson 2022]: https://doi.org/10.5281/zenodo.7463421 "FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons"
\[Wilkinson 2022\]
Mark D. Wilkinson, Susanna-Assunta Sansone, Grootveld Marjan, Josefine Nordling, Richard Dennis, David Hecker (2022):\
**FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons**.\
EOSC FAIR Metrics subgroup\
*Zenodo*\
<https://doi.org/10.5281/zenodo.7463421>

[Wilkinson 2022]: https://doi.org/10.48550/arxiv.2209.09022 "F\*\*\* workflows: When parts of FAIR are missing"
\[Wilkinson 2022\]
Sean R. Wilkinson, Greg Eisenhauer, Anuj J. Kapadia, Kathryn Knight, Jeremy Logan, Patrick Widener, Matthew Wolf (2022):\
**F\*\*\* workflows: When parts of FAIR are missing**.\
*arXiv* 2209.09022 \[cs.DL\]\
<https://doi.org/10.48550/arxiv.2209.09022>

[Williams 2012]: https://doi.org/10.1016/j.drudis.2012.05.016 "Open PHACTS: Semantic interoperability for drug discovery"
\[Williams 2012\]
Antony J. Williams, Lee Harland, Paul Groth, Stephen Pettifer, Christine Chichester, Egon L. Willighagen, Chris [T. Evelo, Niklas Blomberg, Gerhard Ecker, Carole Goble, Barend Mons (2012):\
**Open PHACTS: Semantic interoperability for drug discovery**.\
*Drug Discovery Today* **17**(21-22)\
<https://doi.org/10.1016/j.drudis.2012.05.016>

[Wittenburg 2019]: https://doi.org/10.23728/b2share.b605d85809ca45679b110719b6c6cb11 "Digital objects as drivers towards convergence in data infrastructures"
\[Wittenburg 2019\]
Peter Wittenburg, George Strawn, Barend Mons, Luiz Bonino, Erik Schultes (2019):\
**Digital objects as drivers towards convergence in data infrastructures**.\
*B2Share*\
<https://doi.org/10.23728/b2share.b605d85809ca45679b110719b6c6cb11>

[Wittenburg 2022b]: https://doi.org/10.5281/zenodo.5872645 "FAIR digital object demonstrators 2021"
\[Wittenburg 2022b\]
<small>Peter Wittenburg, Ivonne Anders, Christophe Blanchi, Merret Buurman, Carole Goble, Jonas Grieb, Alex Hardisty, Sharif Islam, Thomas Jejkal, Tibor Kálmán, Christine Kirkpatrick, Laurence Lannom, Thomas Lauer, Giridhar Manepalli, Karsten Peters-von Gehlen, Andreas Pfeil, Robert Quick, Mark Sanden, Ulrich Schwardmann, Stian Soiland-Reyes, Rainer Stotzka, Zachary Trautt, Dieter Van Uytvanck, Claus Weiland, Philipp Wieder</small> (2022):\
**FAIR digital object demonstrators 2021**.\
*Zenodo*\
<https://doi.org/10.5281/zenodo.5872645>

[Wittenburg 2023]: https://osf.io/3rekv/ "Canonical workflow frameworks for research"
\[Wittenburg 2023\]
Peter Wittenburg, et al (2023):\
**Canonical workflow frameworks for research**.\
*OSF*\
<https://osf.io/3rekv/>

[Wolstencroft 2011]: https://doi.org/10.1093/bioinformatics/btr312 "RightField: Embedding ontology annotation in spreadsheets"
\[Wolstencroft 2011\]
Katy Wolstencroft, Stuart Owen, Matthew Horridge, Olga Krebs, Wolfgang Mueller, Jacky L. Snoep, Franco du Preez, Carole Goble (2011):\
**RightField: Embedding ontology annotation in spreadsheets**.\
*Bioinformatics* **27**(14)\
<https://doi.org/10.1093/bioinformatics/btr312>

[Wolstencroft 2013]: https://doi.org/10.1093/nar/gkt328 "The Taverna workflow suite: Designing and executing workflows of Web Services on the desktop, web or in the cloud"
\[Wolstencroft 2013\]
<small>Katherine Wolstencroft, Robert Haines, Donal Fellows, Alan Williams, David Withers, Stuart Owen, Stian Soiland-Reyes, Ian Dunlop, Aleksandra Nenadic, Paul Fisher, Jiten Bhagat, Khalid Belhajjame, Finn Bacall, Alex Hardisty, Abraham Nieva de la Hidalga, Maria P. Balcazar Vargas, Shoaib Sufi, Carole Goble</small> (2013):\
**The Taverna workflow suite: Designing and executing workflows of Web Services on the desktop, web or in the cloud**.\
*Nucleic Acids Research* **41**(W1)\
<https://doi.org/10.1093/nar/gkt328>

[Wood 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
\[Wood 2014\]
David Wood, Richard Cyganiak, Markus Lanthaler (2014):\
**RDF 1.1 Concepts and Abstract Syntax**\
*W3C Recommendation*\
<https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/>

[Wright 2022]: https://datatracker.ietf.org/doc/draft-bhutton-json-schema/01/ "JSON schema: A media type for describing JSON documents"
\[Wright 2022\]
Austin Wright, Henry Andrews, Ben Hutton, Greg Dennis (2022):\
**JSON schema: A media type for describing JSON documents**.\
*Internet Engineering Task Force*\
<https://datatracker.ietf.org/doc/draft-bhutton-json-schema/01/>

[Zarras 2004]: https://doi.org/10.5381/jot.2004.3.5.a2 "A Comparison Framework for Middleware Infrastructures"
\[Zarras 2004\]
Apostolos Zarras (2004):\
**A Comparison Framework for Middleware Infrastructures**.\
*The Journal of Object Technology* **3**(5)\
<https://doi.org/10.5381/jot.2004.3.5.a2>

