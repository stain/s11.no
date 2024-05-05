---
title: "Glossary"
weight: 0
parent: "/2022/phd/"
lang: en-GB
categories:
  - PhD
summary: > 
  Glossary of terms and acronyms used in my PhD thesis
---

**API** (Application Programming Interface)
: Documented exposed set of methods and resources for programmatic use by a separate component, either within a programming language (e.g. Java interface declarations) or across a network protocol (e.g. REST services).
See _REST_.

**content-negotiation**
: HTTP mechanism to request a desired media type of a resource that has multiple serialisation formats, e.g. `Accept: application/ld+json` to ask for JSON-LD. Commonly used on the Semantic Web for providing both a human-readable HTML representation and various RDF formats.
See _HTTP_, _JSON-LD_, _media type_, _RDF_

**CRUD** (Create, Read, Update, Delete)
: Basic data operations, e.g. for files, database rows, Web resources.


**CSV** (Comma-Seperated Values)
: Text-based format for representing two-dimensional data, rows are separated by newlines and fields by comma or semicolon. The format is very common (e.g.  exported from Microsoft Excel spreadsheets) as it is relatively easy to consume or edit, however it is notoriously underspecified with many incompatible dialects and conventions.

**CWL** (Common Workflow Language)
:  YAML-based file format for computational workflows, executable by a range of workflow engines \[[Crusoe 2022]\].  <https://www.commonwl.org/>. See _YAML_.

**DiSSCo** (Distributed System of Scientific Collections)
: Research Infrastructure for natural science collections. <https://www.dissco.eu/>

**DNS** (Domain Name System)
: Hierarchical global string-based name registry; dominant for mapping _domain names_ to IP addresses on the Web and Internet in general. Resolving the name `www.foo.example.com` will recursively look up the  _name servers_ for `com`, `example.com`, and `foo.example.com` before retrieving the record `www.foo.example.com`. Only a few record types are defined, e.g. `A` (IPv4 address), `AAAA` (IPv6), `NS` (name server), `CNAME` (alias to another name).

**DOI** (Digital Object Identifier)
: Handle-based persistent identifier, e.g. `10.5281/zenodo.8113625` --- typically assigned to scholarly outputs (journal articles, datasets, reports) through one of the DOI registries (e.g. CrossRef, DataCite). Frequently expressed as an URI using the <https://doi.org/> resolver. See _Handle_, _PID_, _URI_.

**DOIP** (Digital Object Interface Protocol)
: Text-based network protocol that exposes an API for a digital object, including basic CRUD operations, but also additional operations \[[DONA 2018]\]. The digital objects may optionally be addressed by Handle identifiers.
See _API_, _CRUD_, _Handle_


**EOSC** (European Open Science Cloud)
: EU initiative to foster Open Science by integrating research infrastructures, interoperability standards, core services (e.g. persistent identifiers, authentication) and best practices \[[Ayris 2016]\] 


**EOSC-IF** (EOSC Interoperability Framework)
: A set of recommendations for interoperability across services and data in the European Open Science Cloud \[[Kurowski 2021,Åkerström 2024]\]. See Section ch3:eosc-interoperability-framework. See _EOSC_.

**FAIR** (Findable Accessible, Interoperable, Reusable)
: A set of principles for sharing of research data and metadata using machine-readable formats \[[Wilkinson 2016]\]. See [Section 1.2](../../../2022/phd/introduction/#fair-principles).

**FDO** (FAIR Digital Object)
: Digital resource which follows certain guidelines and specifications to be machine-actionable and self-described, with an emphasis on identifiers, types, attributes and operations. See Section ch3:fdo.

**Handle**
: The Handle system \[[Sun 2003a,Sun 2003b]\] is a distributed identifier system for digital objects. Each identified object (handle) (e.g. `2117/384589`) within a _prefix_ has a set of key/value strings. Pre-defined keys `URL` `0.LOC` enable data retrieval from a server, additional keys can be added. The Handle protocol is also used for creating/updating handles. Expressed as URIs with the <https://hdl.handle.net/> resolver, replacing the URN scheme `info:hdl:`

**HTML** (HyperText Markup Language)
: Text-based format used for representing Web page content, typically served over HTTP, styled with Cascading Style Sheets (CSS) and made interactive with JavaScript (JS). See _HTTP_.

**HTTP** (Hypertext Transfer Protocol)
: Network protocol used for retrieving Web pages and invoking Web APIs   \[[Fielding 1999]\]. The secure version of the protocol `https` adds encryption.
See _SSL_, _TLS_.

**IP** (Internet Protocol)
: Routable network protocols used for all traffic on the Internet. IPv4 (e.g. address `8.8.8.8`) is gradually being replaced by IPv6 (e.g. `2001:4860:4860::8844`).

**IRI** (International Resource Identifier)
: Globally unique identifier string, equivalent to URIs, but permitting all international Unicode characters without needing escaping. Used as identifiers in JSON-LD. See _JSON-LD_, _URI_

**LD** (Linked Data)
: Set of practices for publishing and relating data on the Web using RDF technologies \[[Bizer 2009]\]. See Section ch3:ld-web.

**LDP** (Linked Data Platform)
: CRUD-like REST API for managing Linked Data containers of individual RDF resources \[[Sporny 2014]\]
See _CRUD_, _Linked Data_, _REST_, _RDF_        

**JSON** (JavaScript Object Notation)
: A structured general purpose data format derived from the JavaScript programming language, commonly preferred by Web APIs. A JSON document consists of key-based objects (dictionaries), arrays, strings and numbers \[[Bray 2017]\].

**JSON-LD** (JSON Linked Data)
: A JSON-based serialization of Linked Data \[[Sporny 2020]\]. Typically includes a `@context` which defines the mapping to RDF. Examples shown in Figure ch3:fig:jsonld and Listing ch5:lis1.
See _JSON_, _LD_, _RDF_.

**media type**
: Syntactic format of a bytestream within a network message, identified by a string. For instance, the HTTP header `Content-Type: text/html` in indicates the media type for HTML. There is an official [Media Type registry](https://www.iana.org/assignments/media-types). See _HTML_, _HTTP_.


**OCR** (optical character recognition)
: Computer method for generating digital text from an image, e.g. a scanned document or photograph of a label.

**openDS** (open Digital Specimens)
: Specification for describing digital twins of physical specimens \[[openDS 2021]\].

**OWL** (Web Ontology Language)
: OWL is a method to express ontologies (classes, properties, hierarchies and inference rules). OWL is conceptually not RDF based, but considered part of the Semantic Web: OWL uses URIs as identifiers, is often used to define vocabularies for Linked Data, which are frequently published in RDFS-based serialisations \[[W3C 2012]\]. See _RDF_, _LD_.

**PID** (Persistent Identifier)
: An identifier string that is globally unique, resolvable (typically through a resolver or registry) and with an organisational promise of persistence, suitable for inclusion in long-term archives and data publications \[[McMurry 2017]\]. 
See _Handle_, _URI_.

**RDA** (Research Data Alliance)
: Community-led global initiative that build consensus on methods for open sharing and re-use of data and metadata. <https://rd-alliance.org/>

**RDF** (Resource Description Framework)
: Conceptual model for knowledge graph representation in the form of triples that relate Web resources
        \[[Schreiber 2014]\], realised through multiple serialisation formats. See Section ch3:semweb.

**RDFa** (Resource Description Framework in Attributes)
: Mechanism to embed RDF statements within HTML documents by assigning attributes to elements, e.g. `<body vocab="http://purl.org/dc/terms/">` \[[Sporny 2015]\]. See _HTML_, _RDF_.

**RDFS** (RDF Schema)
: RDFS is a lightweight RDF vocabulary to define classes and properties for use in other RDF resources \[[Guha 2014]\].

**REST** (Representational State Transfer)
: Architectural style for Web applications, where the stateless nature of Web is exploited by navigating the application state through Web resources, facilitating hypermedia formats \[[Fielding 2000]\].  _RESTful_ Web Services exchanging JSON are the dominant form of Web APIs, although the hypermedia aspect is frequently neglected.
See _API_, _HTTP_, _JSON_.

**RO** (Research Object)
: Grouping of digital scholarly outputs with relationships, semantic descriptions and executable code \[[Bechhofer 2013]\]. See Section intro:rq2.

**RO-Crate** (Research Object Crate)
: Method to package Research Objects with metadata in an embedded JSON-LD file \[[Soiland-Reyes 2022a]\]. See Section ch5:packaging-research-artefacts-with-ro-crate. See _JSON-LD_, _RO_

**RS** (Research Software)
:  _Research Software includes source code files, algorithms, scripts, computational workflows and executables that were created during the research process or for a research purpose_ \[[Gruenpeter 2021]\].

**scientific workflow**
: Data-driven computational workflow to _pipeline_ scientific data for a particular analysis, e.g. data cleaning, image conversion.

**SDR** (Specimen Data Refinery)
: Computational Workflow Platform to assist digitisation pipelines for specimens in natural history museum collections,  combining aspects of FDO and RO-Crate.

**Signposting**
: A method to provide machines with explicit navigational link relations \[[Nottingham 2017]\] between Web resources, by providing HTTP `Link:` headers, HTML `<link>` elements or linkset JSON documens \[[Wilde 2020,Van de Sompel 2022]\]. See _content-negotiation_, _HTTP_, _HTML_, _JSON_.

**SKOS** (Simple Knowledge Organization System)
: SKOS is a lighweight RDF-based method of expressing vocabularies (terms and their definitions), frequently used for mapping between vocabularies and ontologies \[[Isaac 2009]\].

**SSL** (Secure Socket Layer)
: Cryptographic protocol commonly used on top of TCP/IP (e.g. `https://` URLs indicate HTTP over SSL). The secured connection is transparant - the application can treat the channel like any other. SSL relies on a chain of pre-signed certificates for server (and infrequently client) authentication. See _TCP_, _TLS_, _URL_.

**TCP** (Transport Control Protocol)
: TCP is the most common connection protocol used on top of IP (TCP/IP), which opens a bidirectional channel where data is received by the application in the same order it was sent. The protocol includes handshakes and retried transmissions for reliable communication. See _IP_.

**TLS** (Transport Layer Security)
: Cryptographic protocol that largely replaces SSL for secure communication. Unlike SSL, TLS can be also be initiated from within an existing channel and gives the application further control of the encryption. See _SSL_.

**UDP** (User Datagram Protocol)
: UDP is a connectionless overlay of IP, commonly used for scenarios where a short latency or high performance is more important than completeness of data packages (e.g. video streaming, gaming). See _IP_.

**URI** (Uniform Resource Identifier)
: Globally unique identifier string (e.g. `http://example.com/` or `urn:isbn:0451450523`). The _scheme_ (`http`, `urn:isbn`) classifies the identifier. URIs are superset of URLs, as the scheme is not required to have an associated network protocol \[[Berners-Lee 2005]\]. Used as identifiers in RDF.
See _RDF_, _URL_

**URL** (Uniform Resource Locator)
: Globally unique string (e.g. `http://example.com/doc`) to identify a resource path (`/doc`) that can be retrieved (located) using the defined protocol (`http`) from the given domain name (`example.com`). Used for hyperlinks in HTML and most Web applications. See _DNS_, _HTML_, _HTTP_.

**URN** (Uniform Resource Name)
: Globally unique identifier string. Subset of URIs which are _not_ required to be locateable with a network protocol, e.g. `urn:isbn:9780062515865` or `urn:uuid:f7262a84-bd45-434e-a79f-32cbb55dc8b1`. URNs are to some extent deprecated in favour of HTTP-based PIDs, e.g. <https://identifiers.org/isbn/9780062515865> See _PID_, _URI_.
 
**UUID** (Universally Unique Identifier)
: Globally unique identifier (also called _GUID_), a hexadecimal string representing a 128-bit number, e.g. `b91d75c1-891d-4305-85f9-7db73d9164da` \[[Leach 2005]\]. Typically generated from a random number generator. UUIDs can be generated independently and represent anything, but are not directly resolvable.

**YAML** (Yet Another Markup Language)
: YAML is a file format with the same data model as JSON, but with a more readable syntax, e.g. using indentation instead of quoted strings.  <https://yaml.org/> See _JSON_

**WfMS** (Workflow Management System)
: Software or platform which can execute computational workflow definitions, and may manage data and provenance related to such executions. See _workflows_

**workflow**
: In this thesis, a _computational workflow_ is a machine-readable definition for executing a series of computational tools, typically executed using a workflow management system. 

**WRROC** (Workflow Run RO-Crate)
: Extension of RO-Crate for representing computational workflow execution provenance
See _RO-Crate_, _WfMS_

**ZIP**
: A compressed archive file format. <https://www.iana.org/assignments/media-types/application/zip>


