---
title: "Chapter 2: Background"
weight: 20
lang: en-GB
categories:
  - PhD
summary: > 
  In this chapter, we discuss the related work with respect to FAIR Digital Objects and Linked Data. We do so by looking through the lens of development of these technologies over time, including future directions.
---

In the following chapter, we discuss the related work with respect to FAIR Digital Objects and Linked Data. We do so by looking through the lens of development of these technologies over time, including future directions.

### FAIR Digital Object {#sec:fdo}

The concept of **FAIR Digital Objects** [[Schultes 2019]] has been introduced as way to expose research data as active objects that conform to the FAIR principles [[Wilkinson 2016]]. This builds on the *Digital Object* (DO) concept [[Kahn 2006]], first introduced by [[Kahn 1995]] as a system of *repositories* containing *digital objects* identified by *handles* and described by *metadata* which may have references to other handles. DO was the inspiration for the [ITU-T X.1255] framework which introduced an abstract *Digital Entity Interface Protocol* for managing such objects programmatically, first realised by the Digital Object Interface Protocol (DOIP) [[Reilly 2009]].

In brief, the structure of a FAIR Digital Object (FDO) is to, given a *persistent identifier* (PID) such as a DOI, resolve to a *PID Record* that gives the object a *type* along with a mechanism to retrieve its *bit sequences*, *metadata* and references to further programmatic *operations* (figure 1). The type of an FDO (itself an FDO) defines attributes to semantically describe and relate such FDOs to other concepts (typically other FDOs referenced by PIDs). The premise of systematically building an ecosystem of such digital objects is to give researchers a way to organise complex digital entities, associated with identifiers, metadata, and supporting automated processing [[Wittenburg 2019]].

{{< figure src="fdo.svg" link="fdo.svg" id="fig:fdo" 
  width="100%" title="Idealised overview of a FAIR Digital Object"
  caption="The persistent identifier (PID), (e.g. a Handle, DOI or permalink), refers to an FDO through a PID Record, which may reference downloadble bytes, and optionally additional metadata in another FDO. A series of operations are accessible from an FDO (for instance retrieving the bytes). Similar to in object-oriented programming, the FDO Type indicates which operations and attributes are applicable to an FDO. FDOs can be cross-related using the PIDs, a Collection is then another such FDO which aggregates other FDOs by reference. <p>The configuration shown here is just one of many possible [<a href='https://doi.org/10.5281/zenodo.7825703'>Lannom 2022a</a>], along with the choice of PID system, nature of the PID Record and metadata vocabularies, which are identified through an FDO Profile. In practice, some compromises from this idealised picture are taken depending on the implementation, for instance attribute keys may be simple strings rather than PIDs, and default operations are not explicitly declared." >}}

Recently, FDOs have been recognised by the European Open Science Cloud ([EOSC](https://eosc.eu/)) as a suggested part of its Interoperability Framework [[Corcho 2021]], in particular for deploying active and interoperable FAIR resources that are *machine actionable*. Development of the FDO concept continued within Research Data Alliance ([RDA](https://www.rd-alliance.org/)) groups and EOSC projects like [GO-FAIR](https://www.go-fair.org/), concluding with a set of guidelines for implementing FDO [[Bonino 2019](https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx)]. The [FAIR Digital Objects Forum](https://fairdo.org/) has since taken over the maturing of FDO through focused working groups which have currently drafted several more detailed specification documents (see [*Next steps for FDO*](#sec:next-step-fdo)).

#### FDO approaches {#sec:fdo-approaches}

FDO is an evolving concept. A set of FDO Demonstrators [[Wittenburg 2022]] highlights how current adapters are approaching implementations of FDO from different angles:

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

**DOIP Endorsement Request** [[Schwardmann 2022a]] is an endorsement of the DOIP v2.0 [[DONA 2018]] specification as a potential FDO implementation, as it has been applied by several institutions [[Wittenburg 2022]]. The document proposes that DOIP shall be assessed for completeness against FDO – in this initial draft this is justified as *“we can state that DOIP is compliant with the FDO specification documents in process”* (the documents listed above).

**Upload of FDO** [[Blanchi 2022a]] illustrates the operations for uploading an FDO to a repository, what checks it should do (for instance conformance with the PID Profile, if PIDs resolve). ResourceSync [[ANSI 2017]] is suggested as one type of service to list FDOs. This document highlights potential practices by repositories and their clients, without adding any particular requirements.

**Typing FAIR Digital Objects** [[Lannom 2022a]] defines what *type* means for FDOs, primarily to enable machine actionability and to define an FDO’s purpose. This document lays out requirements for how *FDO Types* should themselves be specified as FDOs, and how an *FDO Type Framework* allows organising and locating types. Operations applicable to an FDO is not predefined for a type, however operations naturally will require certain FDO types to work. How to define such FDO operations is not specified.

**Implementation of Attributes, Types, Profiles and Registries** [[Blanchi 2022b]] details how to establish FDO registries for types and FDO profiles, with their association with PID systems. This document suggest policies and governance structures, together with guidelines for implementations, but without mandating any explicit technology choices. Differences in use of attributes are examplified using FDO PIDs for scientific instruments, and the proto-FDO approach of [DARIAH-DE](https://de.dariah.eu/) [[Schwardmann 2022b]].

It is worth pointing out that, except for the DOIP endorsement, all of these documents are conceptual, in the sense that they permit any technical implementation of FDO, if used according to the recommendations. Existing FDO implementations [[Wittenburg 2022]] are thus not fully consolidated in choices such as protocols, type systems and serialisations – this divergence and corresponding additional technical requirements mean that FDOs are not yet in a single ecosystem.

### From the Semantic Web to Linked Data {#sec:ld}

In order to describe *Linked Data* as it is used today, we’ll start with an (opinionated) description of the evolution of its foundation, the *Semantic Web*.

#### A brief history of the Semantic Web {#sec:semweb}

The **Semantic Web** was developed as a vision by Tim Berners-Lee [[Berners-Lee 1999]], at a time that the Web had already become widely established for information exchange, being a global set of hypermedia documents which are cross-related using universal links in the form of URLs. The foundations of the Web (e.g. URLs, HTTP, SSL/TLS, HTML, CSS, ECMAScript/JavaScript, media types) were standardised by [W3C](https://www.w3.org/standards/), [Ecma](https://www.ecma-international.org/), [IETF](https://www.ietf.org/standards/) and later [WHATWG](https://whatwg.org/). The goal of Semantic Web was to further develop the machine-readable aspects of the Web, in particular adding *meaning* (or semantics) to not just the link relations, but also to the *resources* that the URLs identified, and for machines thus being able to meaningfully navigate across such resources, e.g. to answer a particular query.

Through W3C, the Semantic Web was realised with the Resource Description Framework (RDF) [[Schreiber 2014]] that used *triples* of subject-predicate-object statements, with its initial serialisation format [[Lassila 1999]] being RDF/XML (XML was at the time seen as a natural data-focused evolution from the document-centric SGML and HTML).

While triple-based knowledge representations were not new [[Stanczyk 1987]], the main innovation of RDF was the use of global identifiers in the form of URIs[^2] as the primary identifier of the *subject* (what the statement is about), *predicate* (relation/attribute of the subject) and *object* (what is pointed to -- see [Figure 3](#triples)). By using URIs not just for documents[^3], the Semantic Web builds a self-described system of types and properties, where the meaning of a relation can be resolved by following its hyperlink to the definition within a *vocabulary*. By applying these principles as well to any kind of resource that could be described at a URL, this then forms a global distributed Semantic Web.

{{< figure src="jsonld.svg" link="jsonld.svg" id="fig:jsonld" 
  width="100%" title="Example of linked RDF resources"
  caption="Each <em>resource</em> in an RDF graph has an identifier, here shown as absolute URIs, a type and a series of properties. A property value can either be a <em>literal</em> (e.g. <code>\"Josiah Carberry\"</code>) or another resource (e.g. <code>https://ror.org/03f0f6041</code>). A graph is formed by such cross-references across resources.  In the idealised Semantic Web, every URI would resolve to a description of its resource in RDF. In practice there can be misalignments of identifiers, vocabularies, resolution mechanisms, or simply lack of RDF adoptation. <p>Therefore any RDF graph can describe any Web resource identified by its URI, and these descriptions, using an <em>open world assumption</em> [<a href='https://www.cs.man.ac.uk/~drummond/presentations/OWA.pdf'>Drummond 2006</a>], can be merged with other graphs describing the same resource. For brevity and comparison from later chapters this figure uses the newer RDF format JSON-LD \cite{w3-json-ld}, which can be expanded with context <kbd><a href='http://schema.org/'>http://schema.org/</a></kbd> (not shown) to anchor types and  properties as absolute URIs and generate corresponding RDF triples (<a href='#triples'>Figure 3</a>)." >}}


<figure id="triples">

```turtle
<http://example.com/figure.png> a <http://schema.org/ImageObject> .
<http://example.com/figure.png> <http://schema.org/name> "XXL-CT-scan of an XXL Tyrannosaurus rex skull" .
<http://example.com/figure.png> <http://schema.org/author> <https://orcid.org/0000-0002-1825-0097> .
<http://example.com/figure.png> <http://schema.org/encodingFormat> "image/png" .

<https://orcid.org/0000-0002-1825-0097> a <http://schema.org/Person> .
<https://orcid.org/0000-0002-1825-0097> <http://schema.org/name> "Josiah Carberry" .
<https://orcid.org/0000-0002-1825-0097> <http://schema.org/affiliation> <https://ror.org/03f0f6041> .

<https://ror.org/03f0f6041> a <http://schema.org/Organization> .
<https://ror.org/03f0f6041> <http://schema.org/name> "University of Technology Sydney" .
<https://ror.org/03f0f6041> <http://schema.org/url> "https://www.uts.edu.au/" .
```

<figcaption>

#### Example of RDF triples
These triples correspond to figure 2 after expansion with a JSON-LD context. In this example the properties and types are all using the same vocabulary <http://schema.org/>, in the traditional Semantic Web it is common to mix vocabularies. This    uses the RDF syntax [N-Triples](http://www.w3.org/TR/2014/REC-n-triples-20140225/) where each line indicates _subject_, _predicate_ and _object_. Notable here is the syntactical difference between an URI reference that is part of the graph <https://ror.org/03f0f6041>  and a string literal `"https://www.uts.edu.au/"` which just happens to be a URI. 

</figcaption>
</figure>


The early days of the Semantic Web saw fairly lightweight approaches with the establishment of vocabularies such as FOAF (to describe people and their affiliations) and Dublin Core (for bibliographic data). Vocabularies themselves were formalised using RDFS or simply as human-readable HTML web pages defining each term. The main approach of this *Web of Data* was that a URI identified a *resource* (e.g. an author) with a HTML *representation* for human readers, along with a RDF representation for machine-readable data of the same resource. By using [*content negotiation*](https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation) in HTTP, the same identifier could be used in both views, avoiding `index.html` vs `index.rdf` exposure in the URLs. The concept of *namespaces* gave a way to give a group of RDF resources with the same URI base from a Semantic Web-aware service a common *prefix*, avoiding repeated long URLs.

The mid-2000s saw large academic interest and growth of the Semantic Web, with the development of more formal representation system for ontologies, such as OWL [[W3C 2012]], allowing complex class hierarchies and logic inference rules following *open world* paradigm. More human-readable syntaxes for RDF such as Turtle evolved at this time, and conferences such as [ISWC](https://iswc2022.semanticweb.org/) [[Horrocks 2002]] gained traction, with a large interest in knowledge representation and logic systems based on Semantic Web technologies evolving at the same time.

Established Semantic Web services and standards include: SPARQL [[W3C 2013]] (pattern-based triple queries), [named graphs](https://www.w3.org/TR/rdf11-concepts/#section-dataset) [[Wood 2014]] (triples expanded to *quads* to indicate statement source or represent conflicting views), triple/quad stores (graph databases such as OpenLink Virtuoso, GraphDB, 4Store), mature RDF libraries (including Redland RDF, Apache Jena, Eclipse RDF4J, RDFLib, RDF.rb, rdflib.js), and graph visualisation.

RDF is one way to implement *knowledge graphs*, a system of named edges and nodes[^5] [[Nurdiati 2008]], which when used to represent a sufficiently detailed model of the world, can then be queried and processed to answer detailed research questions. The creation of RDF-based knowledge graphs grew particularly in fields like bioinformatics, e.g. for describing genomes and proteins [[Goble 2008], [Williams 2012]]. In theory, the use of RDF by the life sciences would enable interoperability between the many data repositories and support combined views of the many aspects of bio-entities – however in practice most institutions ended up making their own ontologies and identifiers, for what to the untrained eye would mean roughly the same. One can argue that the toll of adding the semantic logic system of rich ontologies meant that small, but fundamental, differences in opinion (e.g. *should a gene identifier signify just the particular DNA sequence letters, or those letters as they appear in a particular position on a human chromosome?*) led to large differences in representational granularity, and thus needed different identifiers.

Facing these challenges, thanks to the use of universal identifiers in the form of URIs, *mappings* could retrospectively be developed not just between resources, but also across vocabularies. Such mappings can be expressed themselves using lightweight and flexible RDF vocabularies such as SKOS [[Isaac 2009]] (e.g. `dct:title skos:closeMatch schema:name` to indicate near equivalence of two properties). Exemplifying the need for such cross-references, automated ontology mappings have identified large potential overlaps like 372 definitions of `Person` [[Hu 2011]].

The move towards *Open Science* data sharing practices did from the late 2000s encourage knowledge providers to distribute collections of RDF descriptions as downloadable *datasets*,[^6] so that their clients can avoid thousands of HTTP requests for individual resources. This enabled local processing, mapping and data integration across datasets (e.g. Open PHACTS [[Groth 2014]]), rather than relying on the providers’ RDF and SPARQL endpoints (which could become overloaded when handling many concurrent, complex queries).

With these trends, an emerging problem was that adopters of the Semantic Web primarily utillised it as a set of graph technologies, with little consideration to existing Web resources. This meant that links stayed mainly within a single information system, with little URI reuse even with large term overlaps [[Kamdar 2017]]. Just like *link rot* affect regular Web pages and their citations from scholarly communication [[Klein 2014]], for a majority of described RDF resources in the [Linked Open Data](https://lod-cloud.net/) (LOD) Cloud’s gathering of more than thousand datasets, unfortunately do not actually link to (still) downloadable (*dereferenceable*) Linked Data [[Polleres 2020]]. Another challenge facing potential adopters is the plethora of choices, not just to navigate, understand and select to reuse the many possible vocabularies and ontologies [[Carriero 2020]], but also technological choices on RDF serialisation (at least [7 formats](https://www.w3.org/TR/rdf11-primer/#section-graph-syntax)), type system (RDFS [[Guha 2014]], OWL [[W3C 2012]], OBO [[Tirmizi 2011]], SKOS [[Isaac 2009]]), and deployment challenges [[Sauermann 2008]] (e.g. hash vs slash in namespaces, HTTP status codes and PID redirection strategies).

#### Linked Data: Rebuilding the Web of Data {#sec:ld-web}

The **Linked Data** (LD) concept [[Bizer 2009]] was kickstarted as a set of best practices [[Berners-Lee 2006]] to bring the Web aspect of the Semantic Web back into focus. Crucial to Linked Data is the *reuse of existing URIs*, rather than making new identifiers. This means a loosening of the semantic restrictions previously applied, and an emphasis on building navigable data resources, rather than elaborate graph representations.

Vocabularies like [schema.org](https://schema.org/) evolved not long after, intended for lightweight semantic markup of existing Web pages, primarily to improve search engines’ understanding of types and embedded data. In addition to several such embedded *microformats* [[OGP], [WHATWG 2023], [Sporny 2015]], we find JSON-LD [[Sporny 2020]] as a Web-focused RDF serialisation that aims for improved programmatic generation and consumption, including from Web applications. JSON-LD is as of 2023-05-18 used[^7] by 45% of the top 10 million websites [[W3Tech 2023]].

Recently there has been a renewed emphasis to improve the *Developer Experience* [[Verborgh 2018]] for consumption of Linked Data, for instance RDF Shapes – expressed in SHACL [[Kontokostas 2017]] or ShEx [[Baker 2019]] – can be used to validate RDF Data [[Gayo 2017], [Thornton 2019]] before consuming it programmatically, or reshaping data to fit other models. While a varied set of tools for Linked Data consumptions have been identified, most of them still require developers to gain significant knowledge of the underlying Semantic Web technologies, which hampers adaption by non-LD experts [[Klímek 2019]], which then tend to prefer non-semantic two-dimensional formats such as CSV files.

A valid concern is that the Semantic Web research community has still not fully embraced the Web, and that the “final 20%” engineering effort is frequently overlooked in favour of chasing new trends such as Big Data and AI, rather than making powerful Linked Data technologies available to the wider groups of Web developers [[Verborgh 2020]]. One bridging gap here by the Linked Data movement has been “Linked Data by stealth” approaches such as structured data entry spreadsheets powered by ontologies [[Wolstencroft 2011]], the use of Linked Data as part of REST Web APIs [[Page 2011]], and as shown by the big uptake by publishers to annotate the Web using schema.org [[Bernstein 2016]], with vocabulary use patterns documented by copy-pastable JSON-LD examples, rather than by formalised ontologies or developer requirements to understand the full Semantic Web stack.

Linked Data provides technologies that have evolved over time to satisfy its primary purpose of data interoperability. The needs to embrace the Web and developer experience have been central lessons learned. In contrast, FDO is a new approach with many different potential paths forward, and having a partial overlap with the aims of Linked Data.

----

_This chapter is an extract from the preprint [Evaluating FAIR Digital Object and Linked Data as distributed object systems](../evaluating-fdo/), authored by Stian Soiland-Reyes, Carole Goble, Paul Groth._

[^1]: For a brief introduction to DOIP 2.0, see [[CNRI 2023a]]
    
[^2]: URIs [[Berners-Lee 2005]] are generalised forms of URLs that include locator-less identifiers such as ISBN book numbers (URNs). The distinction between locator-full and locator-less identifiers have weakened in recent years [[OCLC 2010]], for instance DOI identifiers now are commonly expressed with the prefix `https://doi.org/` rather than as URNs with `info:doi:` given that the URL/URN gap has been bridged by HTTP resolvers and the use of Persistent Identifiers (PIDs) [[Juty 2011]]. RDF 1.1 formats use Unicode to support *IRI*s [[Dürst 2005]], which extends URIs to include international characters and domain names.

[^3]: URIs can also identify *non-information resources* for any kind of physical object (e.g. people), such identifiers can resolve with `303 See Other` redirections to a corresponding *information resources* [[Sauermann 2008]].    

[^5]: In RDF, each triple represent an edge that is named using its property URI, and the nodes are subject/object as URIs, blank nodes or (for objects) typed literal values [[Schreiber 2014]].    

[^6]: *Datasets* that distribute RDF graphs should not be confused with [*RDF Datasets*](https://www.w3.org/TR/rdf11-concepts/#section-dataset) used for partitioning *named graphs*.
    

[^7]: Presumably this large uptake of JSON-LD is mainly for the purpose of Search Engine Optimisation (SEO), with typically small amounts of metadata which may not constitute Linked Data as introduced above, however this deployment nevertheless constitute machine-actionable structured data.

[Albertoni 2023]: https://www.w3.org/TR/2023/WD-vocab-dcat-3-20230307/ "Data Catalog Vocabulary (DCAT)- Version 3"

[Allcock 2005]: https://marketing.globuscs.info/production/strapi/uploads/gridftp_final_cca95d9e12.pdf "The Globus Striped GridFTP Framework and Server"

[Anders 2022]: https://doi.org/10.5281/zenodo.7825630 "PR-PIDProfileAttributes: FDO PID profiles & attributes"

[Anders 2023]: https://doi.org/10.5281/zenodo.7782262 "PR-RequirementSpec: FAIR Digital Objects Forum FDO requirement specifications"

[ANSI 2017]: http://www.openarchives.org/rs/1.1/resourcesync "ANSI/NISO Z39.99-2017, ResourceSync Framework Specification"

[Ayris 2016]: https://op.europa.eu/o/opportal-service/download-handler?identifier=2ec2eced-9ac5-11e6-868c-01aa75ed71a1&format=pdf "Realising the European open science cloud"

[Bahim 2020]: https://doi.org/10.5334/dsj-2020-041 "The FAIR data maturity model: An approach to harmonise FAIR assessments"

[Baker 2019]: http://shex.io/shex-primer/ "Shape Expressions (ShEx) 2.1 Primer"

[Belshe 2015]: https://www.rfc-editor.org/rfc/rfc7540.html "RFC 7540: Hypertext Transfer Protocol Version 2 (HTTP/2)"

[Berners-Lee 1998]: https://www.w3.org/Provider/Style/URI "Cool URIs don't change"

[Berners-Lee 1999]: https://identifiers.org/isbn/9780062515865 "Weaving the Web: The original design and ultimate destiny of the World Wide Web by its inventor"

[Berners-Lee 2000]: https://www.w3.org/2000/Talks/1206-xml2k-tbl/slide10-0.html "Semantic Web on XML"

[Berners-Lee 2005]: https://www.rfc-editor.org/rfc/rfc3986.html "RFC 3986: Uniform Resource Identifier (URI): Generic Syntax"

[Berners-Lee 2006]: https://www.w3.org/DesignIssues/LinkedData.html "Linked Data"

[Bernstein 2016]: https://dl.acm.org/doi/pdf/10.1145/2890489 "A new look at the semantic web"

[Bishop 2022]: https://www.rfc-editor.org/rfc/rfc9114.html "RFC 9114: HTTP/3"

[Bizer 2009]: https://doi.org/10.4018/jswis.2009081901 "Linked data - the story so far"

[Blanchi 2022a]: https://doi.org/10.5281/zenodo.7825549 "PEN-FDO-Upload: FDO -- upload of FDO"

[Blanchi 2022b]: https://doi.org/10.5281/zenodo.7825572 "WD-Implementation-of-Attributes Implementation of attributes, types, profiles and registries"

[Bonino 2016]: https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability "FAIR Data points supporting big data interoperability"

[Bonino 2019]: https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx "FAIR digital object framework"

[Bonino 2022]: https://fairdigitalobjectframework.org/ "FAIR Digital Object Framework Documentation"

[Brickley 2014]: http://xmlns.com/foaf/spec/ "FOAF Vocabulary Specification"

[Broeder 2022a]: https://drive.google.com/file/d/1laIw7MtdTMSBGXrcfHznklSpqxxotD34 "FDO glossary november 2022"

[Broeder 2022b]: https://doi.org/10.5281/zenodo.7825693 "PR-FDO-KernelAttributesAndMetadata: FDO -- kernel attributes & metadata"

[Browning 2020]: https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/ "Data Catalog Vocabulary (DCAT) - Version 2"

[Capadisli 2017]: https://www.w3.org/TR/2017/REC-ldn-20170502/ "Linked Data Notifications"

[Carriero 2020]: https://doi.org/10.3233/ssw200033 "The landscape of ontology reuse approaches"

[Ciccarese 2013]: https://doi.org/10.1186/2041-1480-4-37 "PAV ontology: Provenance, authoring and versioning"

[Clemm 2002]: https://www.rfc-editor.org/rfc/rfc3253.html "RFC 3253: Versioning Extensions to WebDAV"

[CNRI 2022]: https://www.handle.net/download_hnr.html "Handle.Net Software"

[CNRI 2023a]: https://www.cordra.org/documentation/api/doip.html "DOIP and Examples"

[CNRI 2023b]: https://www.cordra.org/documentation/api/doip-api-for-http-clients.html "DOIP API for HTTP Clients"

[Corcho 2021]: https://doi.org/10.2777/620649 "EOSC Interoperability Framework"

[Corcho 2023]: https://doi.org/10.48550/arXiv.2305.06746 "A maturity model for catalogues of semantic artefacts"

[CWFR 2021]: https://osf.io/3rekv/ "Canonical Workflow Frameworks for Research"

[DCMI 2020]: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/2020-01-20/ "DCMI Metadata Terms"

[Delgado 2016]: https://doi.org/10.1007/978-3-319-31861-5_1 "An Interoperability Framework and Distributed Platform for Fast Data Applications"

[Devaraju 2021]: https://doi.org/10.5334/dsj-2021-004 "From conceptualization to implementation: FAIR assessment of research data objects"

[DOI 2017]: https://www.doi.org/doi_handbook/3_Resolution.html "DOI Handbook - Resolution"

[DONA 2018]: https://hdl.handle.net/0.DOIP/DOIPV2.0 "Digital object interface protocol specification, version 2.0"

[Dürst 2005]: https://www.rfc-editor.org/rfc/rfc3987.html "RFC 3987: Internationalized Resource Identifiers (IRIs)"

[Dusseault 2007]: https://www.rfc-editor.org/rfc/rfc4918.html "RFC 4918: HTTP Extensions for Web Distributed Authoring and Versioning (WebDAV)"

[Ekuan 2023]: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design "Web API design best practices"

[FDO 2022]: https://fairdo.org/specifications/ "FDO Specification Documents"

[Fenner 2019]: https://doi.org/10.5438/jwvf-8a66 "Introducing the PID graph"

[Fensel 2011]: https://doi.org/10.1007/978-3-642-19193-0 "Semantic Web Services"

[Fielding 1999]: https://www.rfc-editor.org/rfc/rfc2616.html "RFC 2616: Hypertext Transfer Protocol -- HTTP/1.1"

[Fielding 2000]: https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm "Architectural styles and the design of network-based software architectures"

[Fielding 2014a]: https://doi.org/10.17487/rfc7230 "RFC 7230: Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing"

[Fielding 2014b]: https://doi.org/10.17487/rfc7231 "RFC 7231: Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content"

[Fielding 2017]: https://doi.org/10.1145/3106237.3121282 "Reflections on the REST architectural style and \"principled design of the modern web architecture\" (impact paper award)"

[Fielding 2022]: https://doi.org/10.17487/rfc9110 "RFC 9110: HTTP Semantics"

[Gayo 2017]: https://doi.org/10.2200/s00786ed1v01y201707wbe016 "Validating RDF Data"

[Goble 2008]: https://doi.org/10.1016/j.jbi.2008.01.008 "State of the nation in data integration for bioinformatics"

[Gray 2017]: https://ceur-ws.org/Vol-1963/paper579.pdf "Bioschemas: From potato salad to protein annotation"

[Gregorio 2007]: https://doi.org/10.17487/rfc5023 "RFC 5023: The Atom Publishing Protocol"

[Gregorio 2012]: https://doi.org/10.17487/rfc6570 "RFC 6570: URI Template"

[Groth 2014]: https://doi.org/10.1016/j.websem.2014.03.003 "API-centric Linked Data integration: The Open PHACTS Discovery Platform case study"

[Guha 2014]: http://www.w3.org/TR/rdf-schema/ "RDF Schema 1.1"

[Hardisty 2022]: https://doi.org/10.1162/dint_a_00134 "The Specimen Data Refinery"

[Hasnain 2018]: https://doi.org/10.1007/978-3-319-98192-5_60 "Assessing FAIR data principles against the 5-star open data principles"

[Hausenblas 2012]: http://5stardata.info/ "5-Star Open Data"

[Hellström 2022]: https://doi.org/10.5281/zenodo.7825686 "PR-Granularity: FDO -- granularity, versioning, mutability"

[Holland 2014]: http://blog.schema.org/2014/06/introducing-role.html "Introducing 'Role'"

[Horrocks 2002]: https://doi.org/10.1007/3-540-48005-6 "The Semantic Web --- ISWC 2002"

[Hu 2011]: https://identifiers.org/isbn/9783642210334 "How matchable are four thousand ontologies on the semantic web"

[Isaac 2009]: https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/ "SKOS Simple Knowledge Organization System Primer"

[Islam 2023]: https://doi.org/10.3233/FC-230001 "FAIR digital objects, persistent identifiers and machine actionability"

[ISO 16684]: https://www.iso.org/standard/75163.html "ISO 16684-1:2019 --- graphic technology --- extensible metadata platform (XMP)"

[ISO 23009]: https://www.iso.org/standard/83314.html "ISO/IEC 23009-1:2022 --- information technology --- dynamic adaptive streaming over HTTP (DASH)"

[ITU-T X.1255]: https://www.itu.int/rec/T-REC-X.1255-201309-I "X.1255 : Framework for Discovery of Identity Management Information"

[Ivonne 2023]: https://doi.org/10.5281/zenodo.7824714 "FAIR digital object technical overview"

[Iyengar 2021]: https://doi.org/10.17487/rfc9000 "RFC 9000: QUIC: A UDP-Based Multiplexed and Secure Transport"

[Jaradeh 2019]: https://doi.org/10.1007/978-3-030-30760-8_31 "Open research knowledge graph: A system walkthrough"

[Jones 2022]: https://swordapp.github.io/swordv3/swordv3.html "SWORD 3.0 Specification"

[Joras 2020]: https://engineering.fb.com/2020/10/21/networking-traffic/how-facebook-is-bringing-quic-to-billions "How Facebook is bringing QUIC to billions"

[Juty 2011]: https://doi.org/10.1093/nar/gkr1097 "Identifiers.org and MIRIAM Registry: Community resources to provide persistent identification"

[Kahn 1995]: http://www.cnri.reston.va.us/k-w.html "A framework for distributed digital object services"

[Kahn 2006]: https://doi.org/10.1007/s00799-005-0128-x "A framework for distributed digital object services"

[Kamdar 2017]: https://doi.org/10.3233/sw-160238 "A systematic analysis of term reuse and term overlap across biomedical ontologies"

[Kelly 2016]: https://datatracker.ietf.org/doc/draft-kelly-json-hal/08/ "JSON Hypertext Application Language"

[Khare 2000]: https://doi.org/10.17487/rfc2817 "RFC 2817: Upgrading to TLS Within HTTP/1.1"

[Klein 2014]: https://doi.org/10.1371/journal.pone.0115253 "Scholarly Context Not Found: One in Five Articles Suffers from Reference Rot"

[Klímek 2019]: https://doi.org/10.3233/SW-180316 "Survey of tools for linked data consumption"

[Kontokostas 2017]: https://www.w3.org/TR/shacl/ "Shapes Constraint Language (SHACL)"

[Kunze 2022]: https://datatracker.ietf.org/doc/draft-kunze-ark/36/ "The ARK Identifier Scheme"

[Lagoze 2008]: http://www.openarchives.org/ore/1.0/datamodel#Proxies "ORE Specification"

[Lamprecht 2021]: https://doi.org/10.12688/f1000research.54159.1 "Perspectives on automated composition of workflows in the life sciences"

[Sun 2003a]: https://doi.org/10.17487/rfc3650 "RFC 3650: Handle System Overview"

[Sun 2003b]: https://doi.org/10.17487/rfc3652 "RFC 3652: Handle System Protocol (ver 2.1) Specification"

[Lannom 2022a]: https://doi.org/10.5281/zenodo.7825703 "PR-ConfigurationTypes FDO configuration types"

[Lannom 2022b]: https://doi.org/10.5281/zenodo.7824673 "FAIR digital objects roadmap. Version 5 november 2022"

[Lannom 2022c]: https://doi.org/10.5281/zenodo.7825599 "PR-TypingFDOs Typing FAIR digital objects"

[Lanthaler 2021]: http://www.hydra-cg.com/spec/latest/core/ "Hydra Core Vocabulary"

[Lassila 1999]: https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/ "Resource Description Framework (RDF) Model and Syntax Specification"

[Lebo 2013a]: https://www.w3.org/TR/2013/REC-prov-o-20130430/ "PROV-O: The PROV Ontology"

[Lebo 2013b]: https://www.w3.org/TR/2013/NOTE-prov-links-20130430/ "Linking Across Provenance Bundles"

[Liu 2007]: https://www.w3.org/TR/2007/REC-wsdl20-primer-20070626/ "Web Services Description Language"

[Loo 2022]: https://doi.org/10.3897/rio.coll.190 "First International Conference on FAIR Digital Objects"

[McMurry 2017]: https://doi.org/10.1371/journal.pbio.2001414 "Identifiers for the 21st century"

[MDN 2023]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation "HTTP Content negotiation"

[Meroño-Peñuela 2021a]: https://doi.org/10.1007/978-3-031-01917-3_7 "Conclusion and future challenges"

[Meroño-Peñuela 2021b]: https://doi.org/10.1007/978-3-031-01917-3_3 "Web data APIs over SPARQL"

[Miller 2021]: https://spec.openapis.org/oas/v3.1.0.html "OpenAPI Specifications"

[Mons 2017]: https://doi.org/10.3233/ISU-170824 "Cloudy, increasingly FAIR; revisiting the FAIR data guiding principles for the European Open Science Cloud"

[NCBO BioPortal]: https://bioportal.bioontology.org/ontologies "NCBO BioPortal"

[Neumann 2021]: https://doi.org/10.1109/TSC.2018.2847344 "An analysis of public REST web service apis"

[Norris 2021]: https://doi.org/10.1186/s13326-021-00240-6 "Why and how to engage expert stakeholders in ontology development: Insights from social and behavioural sciences"

[Nottingham 2017]: https://doi.org/10.17487/rfc8288 "RFC 8288: Web Linking"

[Nurdiati 2008]: https://purl.utwente.nl/publications/64931 "25 years development of knowledge graph theory: the results and the challenge"

[OCLC 2010]: http://info-uri.info/ "Info URI Registry"

[OGP]: https://ogp.me/ "The Open Graph protocol"

[OpenStand 2017]: https://open-stand.org/about-us/principles/ "The modern Standards Paradigm"

[OSI 2022]: https://opensource.org/licenses "Licences & Standards"

[Page 2011]: https://doi.org/10.1145/1967428.1967435 "REST and Linked Data"

[Pantos 2017]: https://doi.org/10.17487/rfc8216 "RFC 8216: HTTP Live Streaming"

[Parecki 2017]: https://www.w3.org/TR/2017/REC-micropub-20170523/ "Micropub"

[Polleres 2020]: https://doi.org/10.3233/SW-190380 "A more decentralized vision for linked data"

[RDA 2020]: https://doi.org/10.15497/rda00050 "FAIR data maturity model: Specification and guidelines"

[Rescorla 2000]: https://www.rfc-editor.org/rfc/rfc2818.html "RFC 2818: HTTP over TLS"

[Reilly 2009]: https://www.dona.net/doipv1doc "Digital Object Interface Protocol 1.0"

[Riccardi 2022]: https://doi.org/10.1002/jcc.26842 "Towards improved FAIRness of the ThermoML Archive"

[Rice 2022]: https://websockets.spec.whatwg.org/ "WebSockets Standard"

[Rocca-Serra 2023]: https://doi.org/10.1038/s41597-023-02166-3 "The FAIR cookbook - the essential resource for and by FAIR doers"

[Sandvine 2022]: https://www.sandvine.com/global-internet-phenomena-report-2022 "Global Internet Phenomena Report"

[Sauermann 2008]: http://www.w3.org/TR/cooluris/ "Cool URIs for the semantic web"

[schema.org]: https://schema.org/

[schema.org Actions]: https://schema.org/docs/actions.html

[Schreiber 2014]: http://www.w3.org/TR/2014/NOTE-rdf11-primer-20140624 "RDF 1.1 Primer"

[Schultes 2019]: https://doi.org/10.1007/978-3-030-23584-0_1 "FAIR principles and digital objects: Accelerating convergence on a data infrastructure"

[Schultes 2020]: https://doi.org/10.1007/978-3-030-65847-2_13 "Reusable FAIR implementation profiles as accelerators of FAIR convergence"

[Schwardmann 2022a]: https://doi.org/10.5281/zenodo.7824796 "PED-DOIPEndorsement DOIP endorsement request"

[Schwardmann 2022b]: https://doi.org/10.3897/rio.8.e96014 "Two Examples on How FDO Types can Support Machine and Human Readability"

[Semmler 2022]: https://hdl.handle.net/21.14100/2fcf49d3-0608-3373-a47f-0e721b7eaa87 "IPCC DDC: AWI AWI-CM1.1MR model output prepared for CMIP6 CMIP historical"

[Singhal 2012]: https://blog.google/products/search/introducing-knowledge-graph-things-not/ "Introducing the knowledge graph: Things, not strings"

[Smith 2007]: https://doi.org/10.1038/nbt1346 "The OBO Foundry: Coordinated evolution of ontologies to support biomedical data integration"

[Soiland-Reyes 2022a]: https://doi.org/10.3897/rio.8.e93937 "Creating lightweight FAIR digital objects with RO-Crate"

[Soiland-Reyes 2022b]: https://doi.org/10.3233/ds-210053 "Packaging research artefacts with RO-Crate"

[Soiland-Reyes 2022c]: https://doi.org/10.3897/rio.8.e94501 "Updating linked data practices for FAIR digital object principles"

[Soiland-Reyes 2023]: https://w3id.org/ro/doi/10.5281/zenodo.8075229 "Comparison tables for evaluating FAIR Digital Object and Linked Data"

[Speicher 2015]: https://www.w3.org/TR/2015/REC-ldp-20150226/ "Linked data platform 1.0"

[Sporny 2015]: https://www.w3.org/TR/2015/NOTE-rdfa-primer-20150317/ "RDFa 1.1 Primer"

[Sporny 2020]: https://www.w3.org/TR/2020/REC-json-ld11-20200716/ "JSON-LD 1.1"

[Sporny 2023]: https://datatracker.ietf.org/doc/draft-ietf-mediaman-suffixes/03/ "Media Types with Multiple Suffixes"

[Stallings 1990]: https://doi.org/10.21954/ou.ro.0000f821 "Handbook of computer-communications standards: The Open Systems (OSI) model and OSI-related standards"

[Stanczyk 1987]: https://doi.org/10.21954/ou.ro.0000f821 "Process modelling for information system description"

[Stefi 2015a]: http://doi.org/10.1007/978-3-319-19593-3_18 "To develop or to reuse? Two perspectives on external reuse in software projects"

[Stefi 2015b]: https://doi.org/10.18151/7217489 "Do Developers Make Unbiased Decisions? - The Effect of Mindfulness and Not-Invented-Here Bias on the Adoption of Software Components"

[Thompson 2012]: https://www.w3.org/TR/2012/REC-xmlschema11-1-20120405/ "W3C XML Schema Definition Language"

[Thornton 2019]: https://doi.org/10.1007/978-3-030-21348-0_39 "Using shape expressions (ShEx) to share RDF data models and to guide curation with rigorous validation"

[Tirmizi 2011]: https://doi.org/10.1186/2041-1480-2-s1-s3 "Mapping between the OBO and OWL ontology languages"

[Tupelo-Schneck 2022]: https://www.rd-alliance.org/sites/default/files/Cordra.2022.pdf "Brief Introduction to Cordra & DOIP"

[Turcoane 2014]: https://doi.org/10.55630/dipp.2014.4.11 "Linked data, JSON-LD and the semantics of cultural and scientific heritage"

[Van de Sompel 2013]: https://doi.org/10.17487/rfc7089 "RFC 7089: HTTP Framework for Time-Based Access to Resource States -- Memento"

[Van de Sompel 2015]: https://doi.org/10.1045/november2015-vandesompel "Reminiscing About 15 Years of Interoperability Efforts"

[Van de Sompel 2022]: https://signposting.org/FAIR/ "FAIR Signposting Profile"

[Verborgh 2018]: https://ruben.verborgh.org/blog/2018/12/28/designing-a-linked-data-developer-experience/ "Designing a Linked Data developer experience"

[Verborgh 2020]: https://doi.org/10.3233/SW-190372 "The semantic web identity crisis: In search of the trivialities that never were"

[Verburg 2023]: https://doi.org/10.5281/zenodo.7848102 "FAIR-IMPACT project response to \"FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons\""

[W3C 2012]: https://www.w3.org/TR/2012/REC-owl2-overview-20121211 "OWL 2 Web Ontology Language Document Overview"

[W3C 2013]: https://www.w3.org/TR/2013/REC-sparql11-overview-20130321/ "SPARQL 1.1 Overview"

[W3C 2015]: https://www.w3.org/standards/semanticweb/data "Linked Data"

[W3Tech 2023]: https://w3techs.com/technologies/details/da-jsonld "Usage Statistics of JSON-LD for Websites"

[Weigel 2018]: https://doi.org/10.15497/rda00031 "RDA Recommendation on PID Kernel Information"

[WHATWG 2023]: https://html.spec.whatwg.org/multipage/microdata.html "Microdata"

[Weiland 2022a]: https://drive.google.com/file/d/1lPNBBROjEoZ6fTfrtdqcMa3Q2G27PoC_ "FAIR Digital Objects Forum Document Standards"

[Weiland 2022b]: https://doi.org/10.5281/zenodo.7825650 "FDO machine actionability"

[Wieczorek 2012]: https://doi.org/10.1371/journal.pone.0029715 "Darwin Core: An Evolving Community-Developed Biodiversity Data Standard"

[Wilkinson 2016]: https://doi.org/10.1038/sdata.2016.18 "The FAIR Guiding Principles for scientific data management and stewardship"

[Wilkinson 2022]: https://doi.org/10.5281/zenodo.7463421 "FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons"

[Wilkinson 2022]: https://doi.org/10.48550/arxiv.2209.09022 "F\*\*\* workflows: When parts of FAIR are missing"

[Williams 2012]: https://doi.org/10.1016/j.drudis.2012.05.016 "Open PHACTS: Semantic interoperability for drug discovery"

[Wittenburg 2019]: https://doi.org/10.23728/b2share.b605d85809ca45679b110719b6c6cb11 "Digital objects as drivers towards convergence in data infrastructures"

[Wittenburg 2022]: https://doi.org/10.5281/zenodo.5872645 "FAIR digital object demonstrators 2021"

[Wittenburg 2023]: https://osf.io/3rekv/ "Canonical workflow frameworks for research"

[Wolstencroft 2011]: https://doi.org/10.1093/bioinformatics/btr312 "RightField: Embedding ontology annotation in spreadsheets"

[Wolstencroft 2013]: https://doi.org/10.1093/nar/gkt328 "The Taverna workflow suite: Designing and executing workflows of Web Services on the desktop, web or in the cloud"

[Wood 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"

[Wright 2022]: https://datatracker.ietf.org/doc/draft-bhutton-json-schema/01/ "JSON schema: A media type for describing JSON documents"

[Zarras 2004]: https://doi.org/10.5381/jot.2004.3.5.a2 "A Comparison Framework for Middleware Infrastructures"
