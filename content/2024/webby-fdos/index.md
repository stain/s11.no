---
title: 'Practical webby FDOs with RO-Crate and FAIR Signposting'
categories:
  - Conferences
keywords:
  - FDO
  - Web
  - RO-Crate
  - Signposting
  - metadata
  - linkset
  - community
summary: >
  Article submitted for proceedings of International FAIR Digital Objects Implementation Summit 2024
description: >
     Research Object Crate (RO-Crate) is a lightweight method to package research outputs along with their metadata.  Signposting provides a simple yet powerful approach to navigate scholarly objects on the Web. Combining these technologies form a "webby" implementation of the FAIR Digital Object principles  which is suitable for retrofitting to existing data infrastructures or even for ad-hoc research objects using regular Web hosting platforms. Here we give an update of recent community development and adoption of RO-Crate and Signposting. It is notable that programmatic access and more detailed profiles have received high attention, as well as several FDO implementations that use RO-Crate
authors:
  - name: Stian Soiland-Reyes
    orcid: 0000-0002-0715-6126
  - name: Peter Sefton
    orcid: 0000-0002-3545-944X
  - name: Simone Leo
    orcid: 0000-0001-8271-5429
  - name: Leyla Jael Castro
    orcid: 0000-0003-3986-0510
  - name: Claus Weiland
    orcid: 0000-0003-0351-6523
  - name: Herbert Van de Sompel
    orcid: 0000-0002-0715-6126
---

<h2>Cite as</h2>

Stian Soiland-Reyes, Peter Sefton, Simone Leo, Leyla Jael Castro, Claus Weiland, Herbert Van de Sompel (2024):
**Practical webby FDOs with RO-Crate and FAIR Signposting**: Experiences and lessons learned.  
International FAIR Digital Objects Implementation Summit 2024, Berlin, Germany, 2024-03-20/-\-21.  
_Open Conference Proceedings_ (submitted)  
<https://s11.no/2024/webby-fdos/>


# Practical webby FDOs with RO-Crate and FAIR Signposting: Experiences and lessons learned

_Stian Soiland-Reyes<sup>1,2</sup>, Peter Sefton<sup>3</sup>, Simone Leo<sup>4</sup>, Leyla Jael Castro<sup>5</sup>, Claus Weiland<sup>6</sup>, Herbert Van de Sompel<sup>7</sup>_

<div class="affiliations">

<sup>1</sup> The University of Manchester, UK  
<sup>2</sup> University of Amsterdam, The Netherlands  
<sup>3</sup> University of Queensland, Australia  
<sup>4</sup> Centro di Ricerca Sviluppo e Studi Superiori in Sardegna (CRS4), Italy  
<sup>5</sup> ZB MED Information Centre for Life Sciences, Germany  
<sup>6</sup> Senckenberg – Leibniz Institution for Biodiversity and Earth System Research, Germany  
<sup>7</sup> DANS, The Netherlands  

</div>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Reformatting as Markdown; figure caption formatted; references in s11 house style; example expanded. 


## Abstract

Research Object Crate (RO-Crate) is a lightweight method to package research outputs along with their metadata.  Signposting provides a simple yet powerful approach to navigate scholarly objects on the Web. Combining these technologies form a "webby" implementation of the FAIR Digital Object principles  which is suitable for retrofitting to existing data infrastructures or even for ad-hoc research objects using regular Web hosting platforms. Here we give an update of recent community development and adoption of RO-Crate and Signposting. It is notable that programmatic access and more detailed profiles have received high attention, as well as several FDO implementations that use RO-Crate

## Signposting

The Signposting \[1\] effort started around 2015 in an attempt to address a long-standing problem regarding machine interaction with scholarly objects on the web. Omnipresent landing pages support human interaction with scholarly objects by providing descriptive metadata and links to content. But those pages are not optimised for use by machine agents that navigate the scholarly web. For example, how can a robot determine which links on a landing page lead to content and which to metadata? And, how can a bot distinguish those links from the myriad of other links on the page? Signposting addresses this by suggesting some purposely simple, yet standard-based patterns for using typed web links \[2\] to unambiguously point from a landing page to descriptive metadata (`describedby` link), content resources (`item` link), persistent identifier (`cite-as` link), etc.

### FAIR Signposting

It is fair to say that the Signposting effort initially did not gather a lot of attention nor momentum. But that changed when, in 2020, the [FAIR Signposting Implementation Guideline](https://signposting.org/FAIR/) was published. FAIR Signposting goes beyond merely suggesting patterns as it specifies concrete, well-documented and illustrated recipes that developers can follow to add Signposting support to repository platforms or to implement compliance checks in FAIR assessment tools. It provides details regarding the precise semantics of the select set of link relation types, their cardinality, best practice recommendations for license and vocabulary URIs, levels of support, etc.

### Web technologies in Signposting

Web links \[2\] used by Signposting primarily take the form of additional `Link:` headers in the HTTP response to a given resource, with `rel=` indicating the link relations as standardised in the [IANA registry](https://www.iana.org/assignments/link-relations), e.g.:

```http
GET https://s11.no/2022/a2a-fair-metrics/103-fdo-gr2-pid-record/ HTTP/1.1

200 OK HTTP/1.1
Link: <https://schema.org/LearningResource>;rel="type"
Link: <https://w3id.org/a2a-fair-metrics/103-fdo-gr2-pid-record/>;
  rel="cite-as"
Link: <https://example.com/103-fdo-gr2-pid-record/metadata>;
  rel="describedby";type="text/plain"  
Content-Type: text/html

...
```

FAIR Signposting is a profile for systematic use of a handful of link relations in [level 1](https://signposting.org/FAIR/#level1), adding bi-directional completeness in [level 2](https://signposting.org/FAIR/#level2). This non-intrusive addition of links means Signposting can be added to any kind of Web resource (including large data), and then inspected by using the regular HTTP method `GET`, or `HEAD` to avoid potentially costly content retrieval. However, adding HTTP-level Signposting requires control of the Web server, and injecting headers can be cumbersome in some Web server frameworks.

Signposting can also be embedded in HTML-based *landing pages* by adding the corresponding `<link href="…" rel="…" />` element within the page `<head>`, just like the familiar `rel="stylesheet"` link relation. This option is useful when developer control is limited to HTML templates, e.g. in a content delivery network (CDN) or GitHub Pages \[3\], however the HTML approach do not as easily provide inverse links back to the landing page (e.g. `rel="describes"`).

In addition to the two previously mentioned Signposting approaches, typed links can also be provided in stand-alone documents named *link sets*. Two serialisations for linksets are defined in \[4\]: the text-based `application/linkset` format that is equivalent to the content of the HTTP Link header, and the JSON-based `application/linkset+json` format. Linksets are an attractive option when large collections of links need to be shared. They are made discoverable by means of links with the `rel="linkset"` relation (or `rel="api-catalogue"` for service descriptions). In theory, linkset representations can also be used in non-Web contexts such as the Handle system or local filesystems.

### Signposting as web-centric implementation of FDO

An extra boost for Signposting came when it became clear \[6\] that FAIR Signposting essentially provides a web-centric model ([Figure 1](#fig:fdo-signposting)) for the notion of the FAIR Digital Object ([Figure 2](#fig:fdo)) \[7\]. FAIR Signposting exposes the topology of a FDO on the web and does so by using the simplest possible ingredients. The choice for simplicity is motivated by a desire to minimise implementation and maintenance costs and is inspired by experience with numerous standardisation efforts over the years. The choice for web-centricity is about the availability of off-the-shelf tools and expertise as well as a realistic prospect of long-term sustainability.

{{< figure src="signposting-diagram.png" id="fig:fdo-signposting" 
  width="100%" title="FAIR Signposting"
  caption="implements FDO using link relations to the persistent identifier (`cite-as`), the type PID (`type`), data/code (`item`), and metadata (`describedby`). FDO attribute shown as signposting include PIDs of `author` and `license` (not shown). Adapted from \[6\]" >}}

{{< figure src="../../2023/phd/background/fdo.svg" link="../../2023/phd/background/fdo.svg" id="fig:fdo" 
  width="100%" title="An identified FAIR Digital Object (FDO)"
  caption="The FDO capture a digital object in a PID Record through attributes and associated types, profiles and metadata, each of which may be other FDOs. Adapted from \[5\]" >}}



[Table 1](#tab:relations) shows the correspondence between FAIR Signposting link relations and FDO concepts \[8\]. Note that while kernel attributes `author` and `license` are part of FAIR Signposting, any additional type-specific attributes should be provided by the metadata resource (e.g. a RO-Crate Metadata File), although [extension relations](https://w3id.org/a2a-fair-metrics/115-fdo-gr4-attribute-uuid/) are also possible.

<div id="tab:relations">

| **Link relation/attribute**              | **FDO concept**                                                               |
| :--------------------------------------- | :---------------------------------------------------------------------------- |
| Any `rel=` after PID redirect            | FDO/PID Record (PID Profile: Signposting)                                     |
| `rel=cite-as`                            | PID (persistent identifier)                                                   |
| `rel=linkset`                            | FDO Record (PID Profile: Linkset)                                             |
| `rel=describedby`                        | Metadata, or Metadata FDO if PID                                              |
| `rel=describes`                          | FDO Record that has this metadata                                             |
| `rel=item`                               | Bit-sequence                                                                  |
| `rel=collection`                         | FDO Collection, or FDO Record for a bitstream                                 |
| `rel=type`                               | FDO Type                                                                      |
| `type=` on `rel=item` or `rel=describes` | MIME type of bitstream                                                        |
| `rel=profile`                            | PID Profile                                                                   |
| `profile=` on `rel=describes`            | FDO Type of Metadata (e.g. PID Profile: RO-Crate <https://w3id.org/ro/crate>) |
| `rel=author` or `rel=license`            | Kernel attributes                                                             |
| `rel=api-catalogue` to linkset           | FDO Collection of FDO Operations                                              |
| `rel=service-desc` or `rel=service-doc`  | FDO Operation                                                                 |

Link relations and corresponding FDO concepts, using [FAIR Signposting](https://signposting.org/FAIR/) and [FAIRiCAT](https://signposting.org/FAIRiCat/).

</div>

### Signposting improves FAIR consumption

The EOSC [task force](https://eosc.eu/advisory-groups/fair-metrics-and-data-quality/) for FAIR Metrics and Data Quality organised a series of “Apples to apples” hackathons and workshops, and have reported on FAIR Signposting and its uptake \[9\]. It highlights Signposting as a mechanism for guiding FAIR consuming machine-agents to locate the globally unique identifiers, data records and metadata records, and the challenge for FAIR assessment tools to make consistent evaluations without these elements.

A series of detailed benchmarks for Signposting have been created by the hackathons \[10\], that include identified test cases for each FAIR principle. For instance, [55-rda-r1-01m-t5-type-unresolve](https://w3id.org/a2a-fair-metrics/55-rda-r1-01m-t5-type-unresolve/) is a negative test case of a Signposting FDO where each of the `rel=type` has resolution errors. Such benchmarks are used by evaluation tools like [F-UJI](https://www.f-uji.net/), as well as Signposting clients like the [signposting](https://pypi.org/project/signposting/) Python library and command line tool.

Recently, additional tests for “Webby FDO” using Signposting have been added, e.g. [108-fdo-gr3-bit-sequence-metadata-pid](https://w3id.org/a2a-fair-metrics/108-fdo-gr3-bit-sequence-metadata-pid/) verifies FDO principle [FDO-GR3](https://w3id.org/ro/doi/10.5281/zenodo.7782262;FDO-GR4) to reference a bit-sequence, alongside a PID, type PID and metadata PID. Work to further mature FDO benchmarks continues as part of a FDO Forum task force.

### Growing adoption through Support Actions and Hackathons

The FAIR-IMPACT project’s first [support action](https://fair-impact.eu/1st-open-call-support-closed) funded 18 participants contributing to FAIR assessments as well as 14 participants implementing Signposting and RO-Crate in their repositories and code bases. Among the latter, Signposting support was developed for University of Novi Sad’s Research Information System [DOSIRD UNS](http://dosird.uns.ac.rs/), Simula created a [Signposting extension](https://github.com/annefou/ckanext-signposting) for CKAN to be used by the [Norwegian Research Data Archive](https://www.sigma2.no/service/research-data-archive) \[11\], [ZB MED](https://zbmed-semtec.github.io/) developed Signposting for GitHub Pages \[3–12\].

Signposting *linkset* support was developed [for InvenioRDM](https://github.com/inveniosoftware/invenio-rdm-records/pull/1404) (used by Zenodo) and using HTML headers in Tunisia’s [Scientific and Technical Information Portal](https://www.pist.tn/) by Tunisia National University Center of Scientific and Technical Documentation. EURAC Research’s [Environmental Data Portal](https://edp-portal.eurac.edu/home) also added detailed signposting and new metadata serialisations, here the use of profiles in signposting was highlighted. The Digital Repository of Ireland (DRI) has implemented Signposting \[13\], adding detailed linksets at Level 2.

Several FAIR-IMPACT participants had planned to work on [Signposting support in Dataverse](https://guides.dataverse.org/en/5.14/admin/discoverability.html#signposting), but that was concurrently implemented by the Dataverse community and relatively complete. For these participants, focus moved to upgrading and testing Signposting in their instances, as well as contributing to RO-Crate support in Dataverse to support richer metadata (see section [2.6](#dataverse)).

When reaching out to the US NIH’s Generalist Repository Ecosystem Initiative ([GREI](https://datascience.nih.gov/data-ecosystem/generalist-repository-ecosystem-initiative)), among its members (including Dataverse and InvenioRDM/Zenodo, Figshare, OSF, Vivli, Mendeley Data and Dryad), many indicated they were developing support for Signposting as well as user-provided metadata.

A growing list of [adopters of Signposting](https://signposting.org/adopters/), including repositories and data platforms, shows the interest in and feasibility of implementing Signposting. In addition to the above, earlier adopters include repositories [WorkflowHub](https://about.workflowhub.eu/developer/signposting/) (Signposting to RO-Crate using profile), [DSpace](https://wiki.lyrasis.org/display/DSDOC7x/Signposting), [DSPACE-CRIS](https://wiki.duraspace.org/display/DSPACECRIS/Signposting), and [the DANS Data Stations](https://dans.knaw.nl/en/data-stations/). Journal system and preprint server support include [Episciences Overlay Journals](https://www.episciences.org/), [HAL Science](https://hal.science/) and [Open Journal System](https://openjournalsystems.com/).

As part of the ELIXIR Biohackathon \[12\], the [Signposting Sniffing](https://chromewebstore.google.com/detail/signposting-sniffing/pahanegeimljfcnjogglnamnlcgipmbc) plugin for Chromium-based browsers was developed and tested with signposting in the [HoloFood Data Portal](https://www.holofooddata.org/). The plugin supports both HTML- and HTTP-based Signposting, and can be used to debug and discover signposting.

These adopters highlight that it is easy to retrofit Signposting, but that the learning curve of other FAIR standards means that providing detailed metadata is more demanding.

## RO-Crate community updates

The [RO-Crate community](https://www.researchobject.org/ro-crate/community.html) supports and promotes FAIRification of research outcomes and provides tools for researchers to improve FAIRness. RO-Crate \[14\] makes it easy to package research outcomes in the form of digital objects together with their corresponding metadata, using and extending [schema.org](https://schema.org/) to describe an RO-crate package as a dataset and all its elements (i.e, research outcomes). Thanks to the use of [profiles](https://www.researchobject.org/ro-crate/profiles.html), researchers can choose a description that best suits their needs. A [Profile Crate](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles) provides a specification including types and properties tailored to a specific domain or community (effectively a *PID Profile* that lists *FDO Type*s).
In this section we provide an update on recent new community adoption of RO-Crate, see also \[14\] for existing adoptions.

### Workflows and provenance

Workflow Run RO-Crate \[15\] is a set of three RO-Crate profiles to capture the provenance of computational workflow execution: [Process Run Crate](https://w3id.org/ro/wfrun/process), which deals with possibly composite computations not necessarily described by a formal workflow; [Workflow Run Crate](https://w3id.org/ro/wfrun/workflow), which extends Process Run Crate with specifications to represent computations orchestrated by a workflow; [Provenance Run Crate](https://w3id.org/ro/wfrun/provenance), which extends Workflow Run Crate with guidelines on how to represent the execution of the various tools used by the workflow. The profiles are developed by a working group that includes workflow developers and users, workflow engine developers and users and other members interested in the provenance of workflow execution. Workflow Run RO-Crate is already implemented by six workflow engines: Galaxy, COMPSs, StreamFlow, WfExS-backend, Sapporo and Autosubmit, enabling interoperable comparisons between heterogeneous workflow executions.

#### Executable papers

[LivePublication](https://livepublication.github.io/LP_Pub_LID/) \[16\] is a proof of concept of an *executable paper*, whose interactive visualisation and statistical calculations can be regenerated on the fly taking into consideration data sources updated after the paper’s publication date. Here RO-Crate enables execution on the Globus infrastructure through an innovative use of individual RO-Crates and containers for each computable element of the paper, nested within a top-level Crate for the paper. This novel approach shows how it is possible to use RO-Crate as a machine-actionable object, which does not rely on bundling an underlying workflow representation in an existing workflow language.

#### TRE-FX and TREs

Trusted Research Environments (TREs) are used to provide computational analysis access to sensitive data. An architecture for federated analytics running workflows across such TREs \[17\] developed the Five Safes Crate profile \[18\], where the crate goes through manual and automatic review processes which are tracked within the crate and abstracts the workflow run requests so the federated analytics APIs are interoperable across different workflow engines \[19\].

### RO-Crate and FDO

RO-Crate has previously been proposed as a mechanism for implementing FDO \[20\], in particular for metadata FDOs. The FDO approach fosters self-contained and machine-actionable knowledge units which persistently bind necessary contextual metadata and typed operation semantics to enable processing of their actual content across different data spaces \[21\].

One way to implementing FAIR Digital Object is using dedicated network protocols including the Handle system and the Digital Object Interface Protocol (DOIP) \[22–23\]. In addition, an implementation path for web-based or “webby” FDOs \[24\] has been proposed to build on common web technologies \[25\]. This approach uses RO-Crate to provision structured metadata based on schema.org and its extension [Bioschemas](https://bioschemas.org/) \[26\], deployed on the Web with persistent identifiers and FAIR Signposting \[12\].

#### Distributed FDO architectures

The [DeSci Nodes](https://docs.desci.com) system has developed a *Distributed Persistent Identifier* ([dPID](https://www.dpid.org)) concept which acts as an overlay of the Interplanetary File System (IPFS) \[27\]. APIs for the DeSci use detached RO-Crates with dPID references. This is a novel FDO implementation that challenges both the traditional centralised FDO approach using the Handle system, as well as the mostly web-based RO-Crate ecosystem.

Further considerations of FDO and Linked Data as distributed systems \[28\] evaluates FDO approaches in terms of capabilities based on existing frameworks (including the FAIR and FDO principles themselves), and highlights that the FDO community should take advantage of lessons learnt by the Linked Data community (avoiding similar mistakes, e.g. with relation to rigidity), and utilise fully the mature and modern capabilities of the Web technology stack, e.g. multiplexed streams.

### Webby FDOs in biodiversity

The Biodiversity Digital Twin ([BioDT](https://biodt.eu/)) project is developing a specimen profile \[29\] that combines the Handle system and RO-Crate. A similar hybrid approach is taken for “retrofitting” Signposting to a FDO approach based on the digital object server [Cordra](https://www.cordra.org/) in Senckenberg’s [WildLIVE Portal](https://wildlive.senckenberg.de/captureevent/wildlive/7df91e6d148a386cc674) \[24\].
This deployment injects Signposting headers as part of the public [nginx](https://www.nginx.com/) server without modifying the proxied Cordra instance, except adding a single API method to generate the Signposting links \[12\] ([Figure 3](#fig:wildlive-signposting)).
Semantic mappings across biodiversity vocabularies \[30\] can also benefit from the use of RO-Crate, as a way to capture multiple mappings and to version and attribute the mapped semantic artefacts.

{{< figure src="wildlive2.png" link="wildlive2.png" id="fig:wildlive-signposting" 
  width="100%" title="Signposting detected in the WildLIVE portal"
  caption="Detected by the [Signposting Sniffing](https://chromewebstore.google.com/detail/signposting-sniffing/pahanegeimljfcnjogglnamnlcgipmbc) browser detailing a data capture event. The link relations provide the set of the images contained in a capture event, metadata like license and authorship, and an RO-Crate comprising the actual content such as annotations (e.g. AI-based taxon identification)." >}}


### Using the Crate-O editor and building ad-hoc vocabularies

The [Crate-O](https://language-research-technology.github.io/crate-o/) tool has been developed by Language Data Commons of Australia ([LDaCA](https://ldaca.edu.au/)) as a general-purpose RO-Crate editor as a successor or alternative to [Describo](https://describo.github.io/). This browser-based tool can use the [file system access API](https://wicg.github.io/file-system-access/), currently implemented in the Chrome and Edge browsers to describe any local folder with resources from the Web as an RO-Crate, or be embedded in an online service to work with any browser with server-side crates. It supports any schema.org type and property, pluggable with other *rdfs* vocabularies. A *mode file* selection indicates recommended and required properties; mode files combine schema information on classes, properties and defined terms, with RO-Crate Profile rules on how they may be defined. Notably this tool is also intended for creation of such “ad-hoc” vocabularies without need of Semantic Web, and is effectively a lightweight user interface for building [Profile Crates](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles#profile-crate) using “Schema.org style Schemas” (SOSSs). There are a number of [tools](https://github.com/Language-Research-Technology/ro-crate-schema-tools) associated with Crate-O which can create HTML documentation and Crate-O mode files from SOSSs, provide simple validation against a profile and infer schemas from example documents.

### Cultural heritage preservation in LDaCA

The Language Data Commons of Australia Program ([LDaCA](https://ldaca.edu.au/)) contributes to language research and cultural heritage preservation by archiving Australian Indigenous languages, regional languages of the Pacific, and Australian English, and making such data and annotations publicly available. LDaCA and the [Pacific and Regional Archive for Digital Sources in Endangered Cultures (PARADISEC)](https://www.paradisec.org.au/) use [RO-Crate](https://www.researchobject.org/ro-crate/in-use/LDaCA.html) with an [RO-Crate profile](https://w3id.org/ldac/profile), as an interchange and archive format for language data, and is providing data discovery portals and API access to data using RO-Crate-centric APIs. For instance, the [LDaCA data portal](https://data.atap.edu.au/) uses [detached RO-crates](https://www.researchobject.org/ro-crate/1.2-DRAFT/structure.html#detached-ro-crate) for FDO-style navigation of centralised API resources.

### Dataverse integration

In the research data repository software [Dataverse](https://dataverse.org/) \[31\], [RO-Crate support](https://github.com/IQSS/dataverse/issues/8688) is implemented by multiple plugins.
The [AROMA](https://sztaki.hun-ren.hu/en/innovation/news/developing-elkh-arp-aroma-published-describo-newsletter-australia) (ARP RO-Crate Manager) \[32\], used by Hungarian repository [CONCORDA](https://science-data.hu/), extends Dataverse for dynamic metadata editing using the Describo Crate Builder Web component.
The FAIR-IMPACT support action (section [1.5](#support-action)) saw community development of import, [export](https://github.com/IQSS/dataverse/pull/10086) and [preview](https://github.com/gdcc/dataverse-previewers/pull/41) plugins for RO-Crate in Dataverse, and [also](https://github.com/IQSS/dataverse/pull/9366) for the Electronic Lab Notebook format ([ELN](https://github.com/TheELNConsortium/TheELNFileFormat)), which is based on RO-Crate and also supported by the research platform [RSpace](https://www.researchspace.com/) \[33\].

## Discussion

“Webby FDOs” are being implemented by a range of adaptations that use Signposting and/or RO-Crate, in many cases accelerated by relatively modest support action funding (5 days FTE) or implemented at hackathons. This hints that these technologies are easy to deploy and developed, however there are some divergence between the approaches, which could be seen as a hindrance for full machine actionability.

Further documentation of the “Webby FDO” approach should specify concrete and testable recommendations (e.g. specifying a Signposting PID Profile), and the community should further develop the use of Profile Crate as a mechanism to formalise domain-specific PID Profiles, which should be made discoverable in a profile registry ([in development](https://github.com/vliz-be-opsci/profile-repository-to-pages/)).

The hybrid FDO approaches from biodiversity that combine the Handle system, Signposting and RO-Crate shows possible alignment across “FDO flavours”. Further development of the Signposting benchmarks and a common FDO testing framework should guide the FDO community towards a more unified ecosystem of FDO implementations.

## Underlying and related material

* Training material \[34\]: <https://doi.org/10.5281/zenodo.10892090>  
* Presentation slides \[35\]: <https://doi.org/10.5281/zenodo.10847062>  
* Signposting Benchmarks \[10\]: <https://w3id.org/a2a-fair-metrics>

## Author contributions

Contributions according to [CRediT](https://credit.niso.org/) taxonomy:

Stian Soiland-Reyes
: Conceptualization, Project administration, Software, Visualization, Writing – original draft, Writing –- review & editing. 

Peter Sefton
: Conceptualization, Project administration, Software, Supervision, Writing –- review & editing.  

Simone Leo 
: Software, Supervision, Validation, Writing –- review & editing.  

Leyla Jael Castro
: Investigation, Supervision, Validation, Writing –- review & editing.  

Claus Weiland
: Investigation, Software, Supervision, Validation, Writing –- review & editing.  

Herbert Van de Sompel
: Conceptualization, Project administration, Visualization, Writing – original draft, Writing –- review & editing.  

## Competing interests

SSR & HVS organised the FAIR-IMPACT support action, where LJC was one of the awardees. The authors declare that they have no other competing interests.

## Funding

This work was partially funded by the European Union programme Horizon Europe under grant agreements HORIZON-INFRA-2021-EOSC-01-05 101057344 (FAIR-IMPACT), HORIZON-INFRA-2021-EMERGENCY-01 101046203 (BY-COVID), HORIZON-INFRA-2021-EOSC-01 101057388 (EuroScienceGateway), HORIZON-INFRA-2021-TECH-01 101057437 (BioDT), and by UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee grants 10038992 (FAIR-IMPACT), 10038963 (EuroScienceGateway), 10038930 (BioDT). LJC’s work is partially supported by the NFDI4DataScience project, funded by the German Research Foundation (DFG), project number 460234259.

## Acknowledgements

We would like to acknowledge the [RO-Crate Community](https://www.researchobject.org/ro-crate/community.html), the [Signposting community](https://groups.google.com/g/signposting), the Apples-to-Apples hackathon participants and the FAIR-IMPACT Support Action \#2 participants.

<div id="refs" class="references">

<div id="ref-signposting">

1\. Herbert Van de Sompel, *et al.* (2024): Signposting the scholarly Web. (2024). <https://signposting.org/> (accessed 27 March 2024)

</div>

<div id="ref-rfc8288">

2\. Mark Nottingham (2017): Web Linking. (2017). \<<https://doi.org/10.17487/RFC8288>\>

</div>

<div id="ref-ravinder2024">

3\. Rohitha Ravinder, Nelson David Quiñones, Dietrich Rebholz-Schuhmann (2024):  
**A lightweight approach to FDOs via Bioschemas, RO-Crate and Signposting on GitHub Pages**.  
*International FAIR Digital Objects Implementation Summit 2024*, Berlin, Germany, 2024-03-20/-\-21.   
_Open Conference Proceedings_  (in review)  

</div>

<div id="ref-rfc9264">

4\. Erik Wilde & Herbert Van de Sompel (2022): Linkset: Media Types and a Link Relation Type for Link Sets. (2022). \<<https://doi.org/10.17487/RFC9264>\>

</div>

<div id="ref-10.5281/zenodo.10468447">

5\. Stian Soiland-Reyes (2024): **FAIR Research Objects and Computational Workflows – A Linked Data Approach**, PhD thesis, Zenodo, 2024. \<<https://doi.org/10.5281/zenodo.10468447>\>

</div>

<div id="ref-10.5281/zenodo.7977333">

6\. Herbert Van de Sompel (2023): FAIR Digital Objects and FAIR Signposting. (2023). \<<https://doi.org/10.5281/zenodo.7977333>\>

</div>

<div id="ref-10.2777/1524">

7\. European Commission and Directorate-General for Research and Innovation (2018): *Turning fair into reality – final report and action plan from the european commission expert group on fair data* (Publications Office, 2018). \<<https://doi.org/10.2777/1524>\>

</div>

<div id="ref-10.5281/zenodo.7824714">

8\. Anders Ivonne, Christophe Blanchi, Daan Broder, Maggie Hellström, Sharif Islam, Thomas Jejkal, Larry Lannom, Karsten Peters-von Gehlen, Robert Quick, Alexander Schlemmer, Ulrich Schwardmann, Stian Soiland-Reyes, George Strawn, Dieter van Uytvanck, Claus Weiland, Peter Wittenburg, & Carlo Zwölf (2023): FAIR Digital Object technical overview. (2023). \<<https://doi.org/10.5281/zenodo.7824714>\>

</div>

<div id="ref-10.5281/zenodo.10490289">

9\. Mark Wilkinson, Susanna-Assunta Sansone, Marjan Grootveld, Richard Dennis, David Hecker, Robert Huber, Stian Soiland-Reyes, Herbert Van de Sompel, Andreas Czerniak, Milo Thurston, Allyson Lister, & Alban Gaignard (2024): Report on FAIR Signposting and its Uptake by the Community. (2024). \<<https://doi.org/10.5281/zenodo.10490289>\>

</div>

<div id="ref-a2a-fair-metrics">

10\. Stian Soiland-Reyes, Alban Gaignard, Wilko Steinhoff, Mark Wilkinson, & Herbert Van de Sompel (2024): Benchmarks for apples-to-apples FAIR Signposting. (2024). <https://w3id.org/a2a-fair-metrics/> (accessed 27 March 2024)

</div>

<div id="ref-fouillaux2024">

11\. A. Fouillaux & A. Hasan (2024): **Enhancing FAIR data practices in the Norwegian Research Data Archive: Towards research objects and improved interoperability**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-10.37044/osf.io/gmk2h">

12\. Stian Soiland-Reyes, Leyla Jael Castro, Rohitha Ravinder, Claus Weiland, Jonas Grieb, Alexander Rogers, Christophe Blanchi, & Herbert Van de Sompel (2024): BioHackEU23 report: Enabling FAIR Digital Objects with RO-Crate, Signposting and Bioschemas. *BioHackrXiv*, (2024). \<<https://doi.org/10.37044/osf.io/gmk2h>\>

</div>

<div id="ref-dri2024">

13\. Murilo Dias (2024): *FAIR Signposting helps users to navigate the Scholarly Web* (Digital Repository of Ireland, 2024). <https://dri.ie/news/fair-signposting-helps-users-to-navigate-the-scholarly-web/> (accessed 8 April 2024)

</div>

<div id="ref-10.3233/ds-210053">

14\. Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, & Carole Goble (2022): Packaging research artefacts with RO-Crate. *Data Science*, **5** (2022) 97–138. \<<https://doi.org/10.3233/ds-210053>\>

</div>

<div id="ref-10.48550/arXiv.2312.07852">

15\. Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno P. Kinoshita, & Stian Soiland-Reyes (2023): Recording provenance of workflow runs with RO-Crate. (2023). \<<https://doi.org/10.48550/arXiv.2312.07852>\>

</div>

<div id="ref-10.1109/e-Science58273.2023.10254857">

16\. Augustus Ellerm, Mark Gahegan, & Benjamin Adams (2023): **LivePublication: The science workflow creates and updates the publication**. In, *2023 ieee 19th international conference on e-science (e-science)* (2023), pp. 1–10. \<<https://doi.org/10.1109/e-Science58273.2023.10254857>\>

</div>

<div id="ref-10.5281/zenodo.10055354">

17\. Thomas Giles, Stian Soiland-Reyes, Jonathan Couldridge, Stuart Wheater, Blaise Thomson, Jillian Beggs, Suzy Gallier, Sam Cox, Daniel Lea, Justin Biddle, Rima Doal, Naaman Tammuz, Becca Wilson, Christian Cole, Elizabeth Sapey, Simon Thompson, Emily Jefferson, Phillip Quinlan, & Carole Goble (2023): TRE-FX: Delivering a federated network of trusted research environments to enable safe data analytics. (2023). \<<https://doi.org/10.5281/zenodo.10055354>\>

</div>

<div id="ref-10.5281/zenodo.10376350">

18\. Stian Soiland-Reyes, Stuart Wheater, Thomas Giles, Carole Goble, & Philip Quinlan (2023): TRE-FX technical documentation - Five Safes RO-Crate. (2023). \<<https://doi.org/10.5281/zenodo.10376350>\>

</div>

<div id="ref-soilandreyes2024">

19\. S. Soiland-Reyes, S. Wheater, T. Giles, P. Quinlan, & C. Goble (2024): **Five Safes RO-Crate: FAIR Digital Objects for Trusted Research Environments for Health Data Research**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-10.52825/cordi.v1i.396">

20\. Leyla Jael Castro, Stian Soiland-Reyes, & Dietrich Rebholz-Schuhmann (2023): RO-crates meets fair digital objects. *Proceedings of the Conference on Research Data Infrastructure*, **1** (2023). \<<https://doi.org/10.52825/cordi.v1i.396>\>

</div>

<div id="ref-10.52825/cordi.v1i.263">

21\. Peter Wittenburg, Ulrich Schwardmann, Christophe Blanchi, & Claus Weiland (2023): FDOs to enable cross-silo work. *Proceedings of the Conference on Research Data Infrastructure*, **1** (2023). \<<https://doi.org/10.52825/cordi.v1i.263>\>

</div>

<div id="ref-10.5281/zenodo.7825573">

22\. Christophe Blanchi, Maggie Hellström, Larry Lannom, Andreas Pfeil, Ulrich Schwardmann, & Peter Wittenburg (2023): Implementation of Attributes, Types, Profiles and Registries. (2023). \<<https://doi.org/10.5281/zenodo.7825573>\>

</div>

<div id="ref-doip2">

23\. (2018): *Digital Object Interface Protocol Specification, version 2.0* (DONA Foundation, 2018). <https://hdl.handle.net/0.DOIP/DOIPV2.0>

</div>

<div id="ref-weiland2024">

24\. C. Weiland, M. Beukes, J. Grieb, M. Jansen, K. Wesche, & A. Wolodkin (2024): **Employing ‘Webby’ FAIR Digital Objects to support large-scale ecosystem monitoring and mitigation of biodiversity loss in the anthropocene**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-10.3897/rio.8.e93937">

25\. Stian Soiland-Reyes, Peter Sefton, Leyla Jael Castro, Frederik Coppens, Daniel Garijo, Simone Leo, Marc Portier, & Paul Groth (2022): Creating lightweight FAIR Digital Objects with RO-Crate. *Research Ideas and Outcomes*, **8** (2022). \<<https://doi.org/10.3897/rio.8.e93937>\>

</div>

<div id="ref-gray2017">

26\. Alasdair Gray, Carole Goble, Rafael Jimenez, & Bioschemas Community (2017): **Bioschemas: From potato salad to protein annotation**. In, *Proceedings of the iswc 2017 posters & demonstrations and industry tracks* (2017). <https://ceur-ws.org/Vol-1963/paper579.pdf>

</div>

<div id="ref-vukolov2024">

27\. A. Vukolov, E. Van Winkle, E. Schultes, L. C. Pouchard, S. Iman, P. Koellinger, & C. Hill (2024): **An overview of decentralized web technologies as a foundation for future IPFS-centric FDOs**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-10.7717/peerj-cs.1781">

28\. Stian Soiland-Reyes, Carole Goble, & Paul Groth (2024): Evaluating FAIR Digital Object and Linked Data as distributed object systems. *PeerJ Computer Science*, (2024). \<<https://doi.org/10.7717/peerj-cs.1781>\>

</div>

<div id="ref-lopez2024">

29\. J. Lopez Gordillo & S. Islam (2024): **FDO as an interoperability framework for the biodiversity digital twin project**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-grieb2024">

30\. J. Grieb, C. Weiland, A. Wolodkin, J. Lopez Gordillo, & S. Islam (2024): **Implementing FAIR semantic mappings leveraging on RO-Crate**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-10.2218/ijdc.v17i1.833">

31\. Ana Trisovic (2023): Cluster analysis of open research data: A case for replication metadata. *International Journal of Digital Curation*, **17** (2023). \<<https://doi.org/10.2218/ijdc.v17i1.833>\>

</div>

<div id="ref-10.31915/nws.2023.9">

32\. Zoltán Tóth (2023): **Az RO-Crate alapú kutatási objektum csomagolás keretrendszere az ELKH ARP platformban**. In, *Új technológiákkal, új tartalmakkal a jövő digitális transzformációja felé: 32. Networkshop: Országos konferencia: 2023. Április 12-14. Pannon egyetem, veszprém* (HUNGARNET Egyesület, 2023). \<<https://doi.org/10.31915/nws.2023.9>\>

</div>

<div id="ref-Macneil2024">

33\. R. Macneil & T. Mathes (2024): **Implementation of PIDs and plans for FDOs in the RSpace digital research platform**. In Peter Wittenburg, Larry Lannom, Sara El-Gebali, Claudia Biniossek, Dirk Betz, & Paolo Budroni,eds., *International fair digital objects implementation summit 2024* (TIB Open Publishing, 2024)

</div>

<div id="ref-10.5281/zenodo.10892090">

34\. Leyla Jael Castro, Stian Soiland-Reyes, Jonas Grieb, & Claus Weiland (2024): Practical web-based FDOs with RO-Crate and FAIR Signposting. (2024). \<<https://doi.org/10.5281/zenodo.10892090>\>

</div>

<div id="ref-10.5281/zenodo.10847062">

35\. Stian Soiland-Reyes & Herbert Van de Sompel (2024): Signposting and RO-Crate: experiences and lessons learned. (2024). \<<https://doi.org/10.5281/zenodo.10847062>\>

</div>

</div>




