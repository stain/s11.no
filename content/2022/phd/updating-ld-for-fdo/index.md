---
title: "Updating Linked Data practices for FAIR Digital Object principles"
weight: 32
lang: en-GB
categories:
  - PhD
date-meta: '2022-07-10'
authors: 
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
  - name: Leyla Jael Castro
    orcid: https://orcid.org/0000-0003-3986-0510
  - name: Daniel Garijo
    orcid: https://orcid.org/0000-0003-3986-0510
  - name: Marc Portier
    orcid: https://orcid.org/0000-0002-9648-6484
  - name: Carole Goble
    orcid: https://orcid.org/0000-0003-1219-2137
  - name: Paul Groth
    orcid: https://orcid.org/0000-0003-0183-6910
summary: >
  Talk abstract presented at FAIR Digital Objects conference (FDO2022)
description: >
  Realization of FAIR Digital Objects has a great potential if combined with the mature technology stack of Linked Data and knowledge graphs.

  Here I will briefly discuss how FDO principles can be achieved using existing standards that have powered the Web for the last 30 years. Using this mature approach can accelerate uptake of FDO by scholars and existing research infrastructures.

  I will also reflect on how the Linked Data community can adapt to better welcome approaches like FDO.
---

<h2>Cite as</h2>

Stian Soiland-Reyes, Leyla Jael Castro, Daniel Garijo, Marc Portier, Carole Goble, Paul Groth (2022):  
**Updating Linked Data practices for FAIR Digital Object principles**.  
1st International Conference on FAIR Digital Objects ([FDO 2022](https://www.fdo2022.org/)) (abstract).  
_Research Ideas and Outcomes_ **8**:e94501  
<https://doi.org/10.3897/rio.8.e94501>


# Updating Linked Data practices for FAIR Digital Object principles

_Stian Soiland-Reyes¹², Leyla Jael Castro³, Daniel Garijo⁴, Marc Portier⁵, Carole Goble¹, Paul Groth²_

<div class="affiliations">

¹ Department of Computer Science, The University of Manchester, Manchester, United Kingdom  
² Informatics Institute, Faculty of Science, University of Amsterdam, Amsterdam, Netherlands  
³ Informationszentrum Lebenswissenschaften (ZB Med), Cologne, Germany  
⁴ Ontology Engineering Group, Universidad Politécnica de Madrid, Madrid, Spain  
⁵ Vlaams Instituut voor de Zee (VLIZ), Oostende, Belgium  

</div>

## Abstract

Realization of FAIR Digital Objects has a great potential if combined with the mature technology stack of Linked Data and knowledge graphs.

Here I will briefly discuss how FDO principles can be achieved using existing standards that have powered the Web for the last 30 years. Using this mature approach can accelerate uptake of FDO by scholars and existing research infrastructures.

I will also reflect on how the Linked Data community can adapt to better welcome approaches like FDO.


### Background

The _FAIR principles_ [[Wilkinson 2016](https://doi.org/10.1038/sdata.2016.18)] are fundamental for data discovery, sharing, consumption and reuse; however their broad interpretation and many ways to implement can lead to inconsistencies and incompatibility [[Jacobsen 2020](https://doi.org/10.1162/dint_r_00024)].

The European Open Science Cloud ([EOSC](https://www.eosc.eu/)) has been instrumental in maturing and encouraging FAIR practices across a wide range of research areas. Linked Data in the form of [RDF](https://www.w3.org/TR/rdf11-primer/) (Resource Description Framework) is the common way to implement machine-readability in FAIR, however the principles do not prescribe RDF or any particular technology [[Mons 2017](https://doi.org/10.3233/ISU-170824)].


#### FAIR Digital Object

**FAIR Digital Object** (FDO) [[Schultes 2019](https://doi.org/10.1007/978-3-030-23584-0_1)] has been proposed to improve researcher’s access to digital objects through formalising their metadata, types, identifiers and exposing their computational operations, making them actionable FAIR objects rather than passive data sources. 

FDO is a set of principles [[Bonino 2019](https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx)], implementable in multiple ways. Current realisations mostly use _Digital Object Interface Protocol_ (DOIPv2) [[DONA 2018](https://hdl.handle.net/0.DOIP/DOIPV2.0)], with the main implementation [CORDRA](https://www.cordra.org/documentation/api/doip.html). We can consider DOIPv2 as a simplified combination of object-oriented (CORBA, SOAP) and document-based (HTTP, FTP) approaches.

More recently, the [FDO Forum](https://fairdo.org/) has prepared detailed [recommendations](https://drive.google.com/drive/u/0/folders/1-SbZk7enOqjy2Rf57PMB-CQW7qMOUXgO), currently open for comments, including a [DOIP endorsement](https://docs.google.com/document/d/10ESWe-m0ex7fIW0ZYOYeVg6gAcIaBKyO3W-Vg8tXzdw/edit#) and updated [FDO requirements](https://docs.google.com/document/d/1-4_yGRrIcgdMIwaFvHyUt6lxDdfzGpqLUCEihE0vJ-g/edit#heading=h.gjdgxs). These point out **Linked Data** as another possible technology stack, which is the focus of this work.


#### Linked Data

[Linked Data standards](https://www.w3.org/standards/semanticweb/data) (LD), based on the Web architecture, are commonplace in sciences like bioinformatics, chemistry and medical informatics – in particular to publish Open Data as machine-readable resources. LD has become ubiquitous on the general Web, the [schema.org](https://schema.org/) vocabulary is used by over 10 million sites for indexing by search engines – [43% of all websites](https://w3techs.com/technologies/details/da-jsonld) use [JSON-LD](https://json-ld.org/).

Although LD practices align to FAIR [[Hasnain 2018](https://doi.org/10.1007/978-3-319-98192-5_60)], they do not fully encompass active aspects of FDOs. The HTTP protocol is used heavily for applications (e.g. mobile apps and cloud services), with REST APIs of customised [JSON structures](https://json-schema.org/). Approaches that merge the LD and REST worlds include [Linked Data Platform](https://www.w3.org/TR/ldp/) (LDP), [Hydra](https://www.hydra-cg.com/) and [Web Payments](https://www.w3.org/TR/webpayments-http-messages/).


### Meeting FDO principles using Linked Data standards

Considering the potential of FDOs when combined with the mature technology stack of LD, here we briefly discuss how FDO principles can be achieved using existing standards. The general principles (G1–G9) apply well: Open standards with HTTP being stable for 30 years, JSON-LD is widely used, FAIR practitioners mainly use RDF, and a clear abstraction between the RDF model with stable bindings available in multiple serialisations. 

However, when considering the specific principles (FDOF1–FDOF12) we find that additional constraints and best practices need to be established – arbitrary LD resources cannot be assumed to follow FDO principles. This is equivalent to how existing use of DOIP is not FDO-compliant without additional constraints.

Namely, persistent identifiers (PIDs) [[McMurry 2017](https://doi.org/10.1371/journal.pbio.2001414)] (FDOF1) are common in LD world (e.g. using [http://purl.org/](http://purl.org/) or [https://w3id.org/](https://w3id.org/)); however, they don’t always have a declared type (FDOF2), or the PID may not even appear in the metadata. URL-based PIDs are resolvable (FDOF3), typically over HTTP using redirections and content-negotiation. One great advantage of RDF is that all attributes are defined semantic artefacts with PIDs (FDOF4), and attributes can be reused across vocabularies. 

While CRUD operations (FDOF6) are supported by native HTTP operations (GET/PUT/POST/DELETE) as in [LDP](https://www.w3.org/TR/ldp/), there is little consistency on how to define operation interfaces in LD (FDOF5). Existing REST approaches like [OpenAPI](https://swagger.io/specification/) and [URI templates](https://doi.org/10.17487/RFC6570) are mature and good candidates, and should be related to defined types to support machine-actionable composition (FDOF7). HTTP error code _410 Gone_ is used in tombstone pages for removed resources (FDOF12), although more frequent is _404 Not Found_.

Metadata is resolved to HTTP documents with their own URIs, but these frequently don’t have their own PID (FDOF8). [RDF-Star](https://w3c.github.io/rdf-star/) and nanopublications [[Kuhn 2021](https://doi.org/10.7717/peerj-cs.387)] give ways to identify and trace provenance of individual assertions. 

Different metadata levels (FDOF9) are frequently developed for LD vocabularies across different communities (FDOF10), such as [FHIR](http://hl7.org/fhir/) for health data, [Bioschemas](https://bioschemas.org/) for bioinformatics and >1000 more specific [bioontologies](https://bioportal.bioontology.org/ontologies). Increased declaration and navigation of _profiles_ is therefore essential for machine-actionability and consistent consumption across FAIR endpoints. 

Several standards exist for rich collections (FDOF11), e.g. [OAI-ORE](https://www.openarchives.org/ore/), [DCAT](https://www.w3.org/TR/vocab-dcat-3/), [RO-Crate](https://www.researchobject.org/ro-crate/), [LDP](https://www.w3.org/TR/ldp/). These are used and extended heterogeneously across the Web, but consistent machine-actionable FDOs will need specific choices of core standards and vocabularies. Another challenge is when multiple PIDs refer to “almost the same” concept in different collections – significant effort have created manual and automated semantic mappings [[Baker 2013](https://doi.org/10.1016/j.websem.2013.05.001), [de Mello 2022](https://doi.org/10.1007/s12553-022-00639-w)]).

Currently the FDO Forum has suggested the use of LDP as a possible alternative for implementing FAIR Digital Objects [[Bonino 2021](https://fairdigitalobjectframework.org/)], which proposes a novel approach of content-negotiation with custom media types. 


### Discussion

The Linked Data stack provides a set of specifications, tools and guidelines in order to help the FDO principles become a reality. This mature approach can accelerate uptake of FDO by scholars and existing research infrastructures such as the European Open Science Cloud (EOSC). 

However, the amount of standards and existing metadata vocabularies poses a potential threat for adoption and interoperability. Yet, the challenges for agreeing on usage profiles apply equally to DOIP as LD approaches.

We have worked with different scientific communities to define RO-Crate [[Soiland-Reyes 2022](https://doi.org/10.3233/DS-210053)], a lightweight method to package research outputs along with their metadata. While RO-Crate’s use of schema.org shows just one possible metadata model, it's powerful enough to be able to express FDOs, and familiar to web developers.

We have also used FAIR Signposting [[Van de Sompel 2022](https://signposting.org/FAIR/)] with HTTP `Link:` headers as a way to support navigation to the individual core properties of an FDO (PID, type, metadata, licence, bytestream) that does not require heuristics of content-negotiation and is agnostic to particular metadata vocabularies and serialisations.

We believe that by adopting Linked Data principles, we can accelerate FDO today – and even start building practical ways to assist scientists in efficiently answering topical questions based on knowledge graphs.


## Presenting author

Stian Soiland-Reyes


## Submitted to present at

First International Conference on FAIR Digital Objects, presentation

* Slides: <https://doi.org/10.5281/zenodo.7256428>

## Acknowledgements

We would like to acknowledge the [RO-Crate community](https://www.researchobject.org/ro-crate/community.html) and the [WorkflowHub Club](https://about.workflowhub.eu/project/acknowledgements/). Thanks to Rudolf Wittner for valuable comments.


## Funding

European Commission Horizon 2020 (EOSC-Life [824087](https://cordis.europa.eu/project/id/824087)), Horizon Europe (BY-COVID [101046203](https://cordis.europa.eu/project/id/101046203), FAIR-IMPACT [101057344](https://cordis.europa.eu/project/id/101057344)). 

Leyla Jael Castro is supported by a German Research Foundation DFG grant for NFDI4DataScience. 

Daniel Garijo is supported by the Madrid Government (Comunidad de Madrid-Spain) under the Multiannual Agreement with Universidad Politécnica de Madrid in the line Support for R&D projects for Beatriz Galindo researchers, in the context of the V PRICIT (Regional Programme of Research and Technological Innovation)


## Author contributions

Author contributions to this article according to the Contributor Roles Taxonomy [CASRAI CrEDiT](https://casrai.org/credit/):

Stian Soiland-Reyes
: Conceptualization, Formal Analysis, Funding acquisition, Investigation, Software, Writing – original draft, Writing – review and editing

Leyla Jael Castro
: Writing – original draft

Daniel Garijo
: Conceptualization, Funding acquisition, Writing – review and editing

Marc Portier
: Investigation, Writing – original draft, Writing – review and editing

Carole Goble:
: Funding acquisition, Supervision

Paul Groth
: Supervision


## References

[Baker 2013] Thomas Baker, Sean Bechhofer, Antoine Isaacc, Alistair Miles, Guus Schreiber, Ed Summers (2013):  
**Key choices in the design of Simple Knowledge Organization System (SKOS)**.
_Journal of Web Semantics_ **20**  
<https://doi.org/10.1016/j.websem.2013.05.001>

[Bonino 2019] Luiz Bonino, Peter Wittenburg, Bonnie Carroll, Alex Hardisty, Mark Leggott, Carlo Zwölf (2019):  
**FAIR digital object framework v1.02. _FDOF technical implementation guideline_** 
<https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR%20Digital%20Objects/FDOF/FAIR%20Digital%20Object%20Framework-v1-02.docx>

[Bonino 2021] Luiz Olavo Bonino da Silva Santos (2021):  
**FAIR Digital Object Framework Documentation**.  
_Working Draft_  
<https://fairdigitalobjectframework.org/>

[de Mello 2022] Blanda Helena de Mello, Sandro José Rigo, Cristiano André da Costa, Rodrigo da Rosa Righi, Bruna Donida, Marta Rosecler Bez, Luana Carina Schunke (2022):  
**Semantic interoperability in health records standards: a systematic literature review**.  
_Health and Technology_ **12**  
<https://doi.org/10.1007/s12553-022-00639-w>

[DONA 2018] DONA Foundation (2018):  
**Digital Object Interface Protocol specification, version 2.0**.  
<https://hdl.handle.net/0.DOIP/DOIPV2.0>

[Hasnain 2018] Ali Hasnain, Dietrich Rebholz-Schuhmann (2019):  
**Assessing FAIR Data Principles Against the 5-Star Open Data Principles**.  
ESWC 2018: The Semantic Web: ESWC 2018 Satellite Events,  
_Lecture Notes in Computer Science_ **11155**  
<https://doi.org/10.1007/978-3-319-98192-5_60>

[Jacobsen 2020] <small>
Annika Jacobsen,
Ricardo de Miranda Azevedo,
Nick Juty,
Dominique Batista,
Simon Coles,
Ronald Cornet,
Mélanie Courtot,
Mercè Crosas,
Michel Dumontier,
Chris T. Evelo,
Carole Goble,
Giancarlo Guizzardi,
Karsten Kryger Hansen,
Ali Hasnain,
Kristina Hettne,
Jaap Heringa,
Rob W.W. Hooft,
Melanie Imming,
Keith G. Jeffery,
Rajaram Kaliyaperumal,
Martijn G. Kersloot,
Christine R. Kirkpatrick,
Tobias Kuhn,
Ignasi Labastida,
Barbara Magagna,
Peter McQuilton,
Natalie Meyers,
Annalisa Montesanti,
Mirjam van Reisen,
Philippe Rocca-Serra,
Robert Pergl,
Susanna-Assunta Sansone,
Luiz Olavo Bonino da Silva Santos,
Juliane Schneider,
George Strawn,
Mark Thompson,
Andra Waagmeester,
Tobias Weigel,
Mark D. Wilkinson,
Egon L. Willighagen,
Peter Wittenburg,
Marco Roos,
Barend Mons,
Erik Schultes</small> (2020):  
**FAIR Principles: Interpretations and Implementation Considerations**.  
_Data Intelligence_ **2**(1):10–29  
<https://doi.org/10.1162/dint_r_00024>

[Kuhn 2021] Tobias Kuhn, Vincent Emonet, Haris Antonatos, Stian Soiland-Reyes, Michel Dumontier (2021):  
[**Semantic micro-contributions with decentralized nanopublication services**](../../../2021/phd/nanopub/).  
_PeerJ Computer Science_ **7**:e387  
<https://doi.org/10.7717/peerj-cs.387> 

[McMurry 2017]  <small>Julie A McMurry, Nick Juty, Niklas Blomberg, Tony Burdett, Tom Conlin, Nathalie Conte, Mélanie Courtot, John Deck, Michel Dumontier, Donal K Fellows, Alejandra Gonzalez-Beltran, Philipp Gormanns, Jeffrey Grethe, Janna Hastings, Jean-Karim Hériché, Henning Hermjakob, Jon C Ison, Rafael C Jimenez, Simon Jupp, John Kunze, Camille Laibe, Nicolas Le Novère, James Malone, Maria Jesus Martin, Johanna R McEntyre, Chris Morris, Juha Muilu, Wolfgang Müller, Philippe Rocca-Serra, Susanna-Assunta Sansone, Murat Sariyar, Jacky L Snoep, Stian Soiland-Reyes, Natalie J Stanford, Neil Swainston, Nicole Washington, Alan R Williams, Sarala M Wimalaratne, Lilly M Winfree, Katherine Wolstencroft, Carole Goble, Cristopher J Mungall, Melissa A Haendel, Helen Parkinson</small> (2017):  
**Identifiers for the 21st century: How to design, provision, and reuse identifiers to maximize utility and impact of life science data.**  
_PLOS Biology_ **15**(6):e2001414
<https://doi.org/10.1371/journal.pbio.2001414>

[Mons 2017] Barend Mons, Cameron Neylon, Jan Velterop, Michel Dumontier, Luiz Olavo Bonino da Silva Santos, Mark D. Wilkinson (2017):  
**Cloudy, increasingly FAIR; revisiting the FAIR Data guiding principles for the European Open Science Cloud**.  
_Information Services & Use_ **37**(1)  
<https://doi.org/10.3233/ISU-170824>

[Schultes 2019] Erik Schultes, Peter Wittenburg (2019):  
**FAIR principles and digital objects: Accelerating convergence on a data infrastructure**.  
_Data analytics and management in data intensive domains: 20th international conference_ (DAMDID/RCDL 2018)  
<https://doi.org/10.1007/978-3-030-23584-0_1>

[Soiland-Reyes 2022] Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):  
[**Packaging research artefacts with RO-Crate**](../ro-crate/).  
_Data Science_ **5**(2)  
<https://doi.org/10.3233/DS-210053>

[Van de Sompel 2022] Herbert Van de Sompel, Martin Klein, Shawn Jones, Michael L. Nelson, Simeon Warner, Anusuriya Devaraju, Robert Huber, Wilko Steinhoff, Vyacheslav Tykhonov, Luc Boruta, Enno Meijers, Stian Soiland-Reyes, Mark Wilkinson (2022):   
**FAIR Signposting Profile**. (version 20220727).  
<https://signposting.org/FAIR/>

[Wilkinson 2016] <small>Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas Blomberg, Jan-Willem Boiten, Luiz Bonino da Silva Santos, Philip E. Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas, Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard Finkers, Alejandra Gonzalez-Beltran, Alasdair J.G. Gray, Paul Groth, Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A.C ’t Hoen, Rob Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E. Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe Rocca-Serra, Marco Roos, Rene van Schaik, Susanna-Assunta Sansone, Erik Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz, Mark Thompson, Johan van der Lei, Erik van Mulligen, Jan Velterop, Andra Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, Barend Mons</small> (2016):  
**The FAIR Guiding Principles for scientific data management and stewardship**.   
_Nature Scientific Data_ **3**:160018   
<https://doi.org/10.1038/sdata.2016.18>
