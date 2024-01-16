---
title: "Discussion"
weight: 61
lang: en-GB
categories:
  - PhD
summary: > 
  Discussion of findings from this thesis, relating them to emerging related work and future directions. Conclusions for the research questions raised in introduciton.
---

In this section I summarise and discuss the findings from the previous chapters, relating them to emerging related work and future directions.

Making a predictable ecosystem of FAIR digital objects {#ecosystem}
------------------------------------------------------

The main advantage of scholarly researchers publishing *FAIR data* is to enable machine actionability \[[Wilkinson 2016]\], which again will accelerate further research, such as through computational workflows. In practice, data publishing is largely approached either by depositions in general and institutional repositories for Open Data such as Figshare and Zenodo \[[Dillen 2019a]\], or to specialised domain-specific repositories such as in biodiversity \[[GBIF 2021]\].

European research infrastructures supporting Open Science practices are coalescing their services to form the European Open Science Cloud (EOSC) \[[Ayris 2016]\], which are embracing FAIR principles \[[Mons 2017]\] and building a common framework for interoperability \[[Kurowski 2021]\].

While existing practices for implementing FAIR have relied on the Linked Data stack, that is just one possible technology to achieve the benefits of interoperable machine actionability \[[Mons 2017]\].

[Chapter 3](/2023/phd/fdo-and-linked-data/) explored the emerging concept of *FAIR Digital Objects* (FDO) \[[Schultes 2019]\] as a potential distributed object system for FAIR data, comparing its proposed principles and current practices with the established Linked Data approach. As detailed in section [fdo](ch3.html#fdo), FDO defines a handful of constraints and guides for a predictable way to organise complex machine actionable digital entities.

Conceptually FDO can clearly be useful for realizing FAIR principles with more active digital objects that can form a consistent ecosystem, but this opens many questions on actual FDO implementations with regards to protocols and standards.

### Linked Data need more constraints and consistency to be FAIR {#constraints}

Examined in section [ld](ch3.html#ld), the principles of *Linked Data* emerged from the Semantic Web as a data-centric view with a focus on navigation and cross-site interoperability, rather than say elaborate logical inferencing systems using ontologies. Yet the bewildering landscape of technology choices for using RDF in data platforms means that the developers suffer and still face a steep learning curve. For clients consuming Linked Data from multiple sources -- *Linked Data Mashup* \[[Tran 2014]\] -- the situation is still baffling in that relatively small differences in identifiers, vocabularies and usage patterns across deployment result in incompatibilities that may require platform-specific workarounds and mappings \[[Millard 2010]\].

The ecosystem of FAIR tooling is not currently mature enough to support Linked Data consumption in a user-friendly and efficient way \[[Thompson 2020]\], although recent metrics and tools for assessing *FAIRness* \[[Wilkinson 2018]\] can assist both data providers and consumers. Evaluations by EOSC has since found that FAIRness metrics can vary widely across the different assessment tools for the same data resource \[[Wilkinson 2022a]\], showing that further definitions of conventions and practices are needed for consistent Linked Data publishing and consumption.

Making the FAIR principles achieve practical benefits for researchers and platform developers thus requires more specific constraints and broader consistency.

### FDOs as a distributed object system on the Web {#distributed}

The framework-based comparisons in section [results](ch3.html#results) considered the implementation details of both FDO and Linked Data, and evaluated to what extent either can be considered a global distributed object system. The findings from this research show that FDO recommendations can benefit FAIR thinking to build machine actionable ecosystems and provide stronger promises of consistency and predictability across data platforms.

These comparisons highlighted that the Web on the other hand has a flexible, scalable and mature technology stack, which can form a solid basis for implementing FDO. However, if such implementation is to use Linked Data technologies, these must be constrained sufficiently in order to practically realize such an ecosystem within the FDO guidelines and without degrading the developer experience.

### FDOs can be implemented on the Web using Signposting {#signposting}

Section [meeting-fdo-principles-using-linked-data-standards](ch2.html#meeting-fdo-principles-using-linked-data-standards) explored how the FDO principles can be achieved for Linked Data as further constraints on existing standards. As [Chapter 3](/2023/phd/fdo-and-linked-data/) has highlighted throughout, there are many technical details remaining to be specified for FDO it to be consistently implemented according to its own principles.

If such conventions need to be evolved and specified no matter the protocol basis for FDO, this chapter argued, then it would be intuitive to build FDO on the mature Web stack, unless there was an compelling argument for alternative protocol stacks having other advantages.[^1]

Section [discussion](ch2.html#discussion) found that the basis of Web-based FDOs can be built using only Signposting \[[Van de Sompel 2015], [Van de Sompel 2022]\], adding a couple of non-intrusive HTTP headers that are agnostic to metadata standards and serializations. An implementation of such Web-based FDOs was shown in section [lightweight-fdo](ch4.html#lightweight-fdo).

The Signposting approach has also been highlighted both by EOSC \[[Wilkinson 2022a], [Wilkinson 2024]\] and as a possible FDO configuration type \[[Lannom 2022a]\]. The FAIR-IMPACT project launched an [open call](https://fair-impact.eu/1st-open-call-support-closed) where 14 participating institutions participated to build support for Signposting \[[Soiland-Reyes 2023b]\] in their data repositories and platforms.

RO-Crate as a developer-friendly approach {#crate}
-----------------------------------------

As pointed out in section [ld-web](ch3.html#ld-web), while Linked Data is a powerful and flexible approach to publishing structured data on the Web, the developer experience of using Semantic Web technology still needs simplifications, like reducing number of choices for vocabularies and serialization formats.

[Chapter 4](/2023/phd/ro-crate/) introduced *RO-Crate* as a practical implementation of the FAIR principles for the purpose of packaging data alongside structured metadata. The approach builds on best practices for Linked Data, however RO-Crate specifications are example-driven with simple interrelated JSON structures, and primarily use a single, general purpose vocabulary.

This way of "Linked Data by stealth" means that developers don't need to be concerned about RDF implementation details, although they can at their option take advantage of RDF knowledge graph technologies like SPARQL (section [linkeddata](ch5.html#linkeddata)). Extension points are well defined, and although extending RO-Crate do require some RDF knowledge like defining namespaces, reasonable examples and vocabulary repositories are provided by RO-Crate -- developers do not for instance need to learn about ontologies nor need to deploy a web service serving multiple RDF serialisations for every described entity.

### Just enough Linked Data {#justenough}

An important lesson from this work then is to use "just enough" Linked Data for the desired level of interoperability and knowledge representation. While previous efforts to 'FAIRify' largely have been concerned about representing the data values using an RDF data model, this can lead to significant effort needed in developing ontologies and vocabularies.

RO-Crate is using \[[schema.org]\] as its base vocabulary, and tries to follow its philosophy of building a lightweight semantic structure by associating many free text attributes to the same node, rather than making elaborate interconnected semantic objects. For instance, while a `Person`'s `affiliation` ideally goes to a `Organization` with it's own URL and other attributes, in some cases, a free text string is all information available, and this can be used cirectly as the `affiliation`.

With retrospect we can say that this reduction in semantic rigidity compared to use in OWL ontologies is a move back to the simplicity of early RDF as an open-ended model (see section [semweb](ch3.html#semweb)), where a property can be used to point to almost anything, and RDF authors are free to use almost any term.

Another aspect that is not highlighted well in ontologies is where to stop in the formal knowledge representation of an object. In schema.org, many properties like <http://schema.org/license> are defined as having the *range*[^2] of either [`CreativeWork`](http://schema.org/CreativeWork) or [`URL`](http://schema.org/URL), hinting that the licence is not required to be explained as another entity with further properties, but that the attribute's primary purpose is navigation or identification.

This would be a key aspect of Linked Data, which traditionally have had the rather undefined convention of "follow your nose" navigation -- a client may attempt to request any node identifier (if it is a URL), and if, with content-negotiation, it returns some RDF, then that could be integrated into a joint knowlege graph, hopefully adding more description of that node, although possibly using other vocabularies. Signposting on the URL helps to make such navigation and expected profiles explicit.

However, ontologies used in Linked Data have not commonly indicated navigation waypoints as done in Schema.org, simply defining a property's range as a given class leaves it undefined if documents were expected to explain that node or link to its explanation. One notable exception is the Data Catalog Vocabulary (DCAT)[^3] \[[Albertoni 2020]\] which have navigational properties like `dcat:landingPage` (to a `foaf:Document`) and `dcat:downloadURL` (to any `rdfs:Resource`).

### Embedding contextual information reduces need for navigation {#contextual}

A divergence from common Linked Data practices is that our RO-Crate approach is making a self-described container. Rather than assume that information will always be available from the referenced URIs, and requiring clients to crawl their way through the many identifiers to see which ones contain more information, the RO-Crate contains a minimal description of each referenced contextual entity (section [contextualentities](ch5.html#contextualentities)).

This has multiple purposes:

-   Simplify user interfaces, e.g. show a human-readable label and type before the user chooses to click the link.

-   Vocabulary adaptation, for instance describing with schema.org in the crate, what was expressed in FOAF vocabulary at the URI.

-   Unify descriptions of semantic artefacts and web pages. Making "ad-hoc" semantic artefacts within the crate where none exited beforehand.

-   Embed "as of at time of writing" descriptions for longevity. An RO-Crate is self-contained and can be archived independently, and embedding contextual information reduces cross-organizational service dependencies (at the risk of outdated information).

Several of these reasons are also organizational in nature, reflecting back on the EOSC Interoperability Framework (section [eosc-interoperability-framework](ch3.html#eosc-interoperability-framework)) -- rather than requiring for instance the Research Organization Registry [(ROR)](https://ror.org/) to add Linked Data representations of organizations, one can be made ad-hoc by the RO-Crate's author, and contained by the crate as a contextual entity.

This ability to describe a referenced entity locally is also a workaround for the chicken-and-egg problem of creating and linking Linked Data resources that vocabulary-wise are cross-related both ways. For instance orcid.org recently added schema.org content negotiation, but *after* RO-Crate started describing people using the <http://schema.org/Person> type and ORCID identifiers.[^4]

### FDO ecosystems need to permit flexible references {#references}

When reflecting on the above contextualization from the propositions of FAIR Digital Objects as covered back in [Chapter 3](/2023/phd/fdo-and-linked-data/), we can predict a problem if every reference from an FDO must go to another pre-existing FDO (or at least a registered PID), in that there must then be a linear order of FDO creation within an ecosystem of compatible FDO types. A strict reading of the FDO principles means implementations cannot utilise the established human-readable Web for bootstrapping. This risks large cross-organizational delays with a stronger need for collaboration and coordination, or alternatively, starting with a smaller FDO data models that can gradually evolve to add more navigation, when and if registries appear with FDO interfaces.

The emphasis on strong typing in FDOs also means that seemingly incompatible types (for instance developed by the biodiversity community vs. those from genomics communities) lead to a split of the PID space of referenceable objects from a given type of FDOs. Counter to this, the current FDO recommendations for attributes and types \[[Blanchi 2023]\] do not require specification of the *range* of an attribute to be a PID of an FDO, and as current FDO type declarations have been relatively lightweight (textual descriptions only), they are flexible enough to permit URLs to any Web resource or existing Linked Data concepts.

There is a concern, however, that some FDO serializations using the Handle system and key-value attributes cannot distinguish between string literals and object references. Combined with the use of PID references expressed as handles rather than as a URIs (e.g. `21.14100/2fcf49d3-0608-3373-a47f-0e721b7eaa87` instead of <https://hdl.handle.net/21.14100/2fcf49d3-0608-3373-a47f-0e721b7eaa87>), this means that machine actionability suffers, in that the string value is not typed to what kind of reference it may or may not be, or in what PID system. Compare this with listing [triples](ch3.html#triples) where the RDF syntax distinguishes literal strings from object references -- in Handle-based FDOs, machine-actionable navigation is only possible by understanding the attributes of the FDO type, yet as highlighted in the previous paragraph these type definitions are not directly machine-actionable themselves.

In schema.org we find a similar challenge with properties permitting both string values and object references. <http://schema.org/keywords> is perhaps the most ambiguous, as it permits `Text`[^5], but also `URL` or `DefinedTerm`. The two latter cases are both intended for referencing controlled vocabularies, with the distinction that a `DefinedTerm` is defined explicitly within the referenced object, while the defined term is implied if only the URL is provided. JSON-LD contexts have the possibility of enforcing object references (`"@type: "@id"`), but this cannot be used in this case as freetext strings are also permitted. The result is that a freetext keyword that just looks like a URL cannot be distinguished from an intended URL reference, similar to the FDO Handle example in the previous paragraph.

In order to reduce such ambiguity and multiple developer choices, in RO-Crate all object references are in JSON-LD object form (as we saw in Listing [lis1](ch5.html#lis1)), and the RO-Crate context do not have any `@type` shortcuts for implicit references. RO-Crate 1.2 will also recommend that [all entities](https://www.researchobject.org/ro-crate/1.2-DRAFT/metadata.html#common-principles-for-ro-crate-entities) have a type, identifier and human-readable name.

### Profiles restrict general flexibility to gain specific predictability {#profiles}

Section [inuse](ch5.html#inuse) showed how RO-Crate is adopted by different scientific domains. Since the publication of the corresponding manuscripts in [Chapter 4](/2023/phd/ro-crate/), RO-Crate has also been used by the [Language Data Commons of Australia](https://www.researchobject.org/ro-crate/in-use/LDaCA.html) \[[Smith 2022]\] building language corpa, [Survey Ontology](https://www.researchobject.org/ro-crate/in-use/survey-ontology.html) \[[Scrocca 2021]\] describing surveys, [DataPlant](https://nfdi4plants.org/content/learn-more/annotated-research-context.html) for plant experiments, [distributed provenance](https://w3id.org/cpm/ro-crate) of biological specimens \[[Wittner 2020], [Wittner 2023a], [Wittner 2023b]\], [COVID-19 causal inferences](https://w3id.org/ro/doi/10.5281/zenodo.6913045) to compare public health interventions internationally \[[Meurisse 2023]\], and [Trusted Research Environments](https://w3id.org/5s-crate/0.4) for controlled workflow computation on sensitive health data. Several of these use cases have also expanded RO-Crate with additional terms from schema.org or defined in corresponding RO-Crate profiles. The span of these domains shows that RO-Crate is flexible for a range of use cases and can be adopted by developers not familiar with Semantic Web technologies.

The discussion of strictness vs flexibility in section [strictness-vs-flexibility](ch5.html#strictness-vs-flexibility) highlighted the tension between a flexible open-ended model and the predictability needed to consistently create and consume content expressed by the model. While RO-Crate itself can be seen as a restriction of the more open-ended JSON-LD and schema.org, its extensibility points still allow different use cases to expand on those conventions.

Section [profiles](ch5.html#profiles) detailed how semi-formalised profiles can be gradually formed to at first *duck-type* a class of RO-Crates that have similar properties. Later work has formalised this as [Profile Crate](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles) to capture the profile itself as a separate crate. This have now evolved to use the W3C Profiles Vocabulary \[[Atkinson 2019]\] to explicitly link to vocabularies, mappings and importantly constraints expressed as RDF Shapes \[[Soiland-Reyes 2023d]\]. This turns RO-Crate profiles into machine-actionable type definitions, from which existing RDF tooling can do for instance validation. Figure [profilecrate](fig.html#profilecrate) shows how the usage of *roles* within the profile crate indicates the purpose of the constituent parts. Roles are here particularly important as many of these Semantic Web resources are expressed in the same file format (e.g. `text/turtle`) and may be used for different purposes (e.g. SKOS is used to represent either a *mapping* or a *vocabulary* \[[Isaac 2009]\]).

{{< figure src="profile-crate.svg" link="profile-crate.svg" id="figure1" 
  width="100%" title="Example of Profile Crate for Workflow Run Crate"
  caption="" >}}

![**Example of Profile Crate for Workflow Run Crate**. An RO-Crate *WFRun Crate* declares conformance with a given RO-Crate profile. Resolving the profile URI retrieves the *Profile Crate*, which parts include an *RDF Shape*, an *SKOS mapping* and a *DefinedTermSet*. By using the indirection of *ResourceDescriptor* from the Profiles Vocabulary \[[Atkinson 2019]\], the roles of each of these artefacts are defined, e.g. *constraints*. The embedded *vocabulary* as a *DefinedTermSet* defines ad-hoc terms like *sourceParameter* used by the Workflow Run Crate  profile \[[Leo 2023b]\]. ](figures/ch09/profile-crate.pdf){#fig:profilecrate width="\\textwidth"}

While profiles are at first lightweight indicators of common conventions for a class of crates (which may be implicit or explicit), they can be gradually formalised in a *eat own dogfood* way through another RO-Crate, optionally taking advantage of existing Semantic Web technology that enable for instance strict validation of domain-specific RO-Crates.

### One vocabulary is not enough, but one profile may suffice {#oneprofile}

RO-Crate relies heavily on \[[schema.org]\] as its main vocabulary, but as highlighted in section [futurework](ch5.html#futurework) and [profiles](ch61.html#profiles), domain-specific usage will eventually need to define their own terms in order to be specific enough for their use cases. However, we have found it is important to ensure a developer-friendly approach when specifying such profiles for RO-Crate -- earlier work on [ad-hoc terms](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#adding-new-or-ad-hoc-vocabulary-terms) in RO-Crate used a simple CSV approach to be added to the [ro-terms](https://github.com/ResearchObject/ro-terms) namespace.

As with other aspects of RO-Crate, there is a gradual approach towards Linked Data practices. While conventional wisdom in Semantic Web would be to sit down and make your own ontology following design patterns \[[Blomquist 2009], [Poveda 2010]\] and best practices for deployment \[[Matentzoglu 2022]\], in RO-Crate philosophy that would be more of a last resort. The middle of the ground is therefore adding the ad-hoc vocabulary directly to the profile crate, as shown in figure [profilecrate](fig.html#profilecrate). In this approach a single profile URI can, through Linked Data and Signposting, play the role of:

-   Human-readable documentation of conventions (negotiated to HTML preview).
-   List of software and repositories the profile is intended for.
-   List of additional schema.org types and properties utillised by the profile.
-   Indication of which content is expected in the crate (e.g. a Workflow).
-   Validation of a manifest conforming to the profile.
-   Vocabulary definitions of additional terms.
-   JSON-LD context which namespaces the additional terms (as any JSON-LD document can also be a JSON-LD context \[[Sporny 2020]\]).

It should be reasonable to expect developers able to make RO-Crates with their own additional terms to also be able to make a lightweight Profile Crate once those terms have stabilised. Developers with deeper familiarity with Semantic Web technologies can expand the profile capabilities to use existing ontology methodologies, in which case it would be preferrable to aggregate separate semantic artefacts from the Profile Crate rather than embedding them in the RO-Crate Metadata File.

In the FAIR-IMPACT project we are evaluating if the Profile Crate approach is also suitable for FAIR publishing of semantic artefacts themselves, e.g. ontologies and mappings. This is an attractive proposal because such artefacts are also becoming multifaceted, with multiple formats and profiles (e.g. an ontology expressed with OWL2 RL in RDF Turtle syntax), documentation and similar attribution and provenance challenges which RO-Crate is built to handle.

Future RO-Crate directions {#rocratefuture}
--------------------------

In this section we consider future directions for RO-Crate and ongoing RO-Crate adaptations not covered by section [packaging-research-artefacts-with-ro-crate](ch5.html#packaging-research-artefacts-with-ro-crate).

### User applications are needed for researchers to generate FAIR Research Objects {#applications}

RO-Crate and its best practices can be considered a type of *middleware* used by application developers to capture and transmit metadata and relate data files that together form some tangible unit (a *Research Object* \[[Bechhofer 2013]\]). While RO-Crate have already been implemented by several repositories and applications such as workflow systems, it is important to also consider the role of user applications in order to increase adoptation of FAIR research objects by scholars in general.

#### Template-based crates with ya2ro

Futher work by the RO-Crate community has created more user-fronting tools such as [Pavel 2023,](https://github.com/oeg-upm/ya2ro) which given metadata and identifier in a YAML[^6] file can retrieve contextual metadata from ORCID, GitHub and DOI registries and build and publish a completed RO-Crate \[[Pavel 2023]\]. While this technology still requires some understanding of editing, it is intended to be more approachable to data scientists and for use with simple Web publishing platforms like [GitHub Pages.](https://pages.github.com/) The GitHub Action [ro-crate-preview](https://github.com/marketplace/actions/ro-crate-preview) also automate HTML preview generation of crates on GitHub Pages.

#### Editing and publishing RO-Crate in ROHub

The repository [ROHub](https://www.rohub.org/) \[[Garcia-Silva 2019]\] has recently added RO-Crate import and export \[[Fouilloux 2023]\], and provides both a browseable repository for publishing crates, but also interactive and collaborative editing of its metadata. In this use case, RO-Crate plays the role as an exchange and archiving format, as the hub stores the crates in general-purpose repositories Zenodo and B2Share which do not have the facility to keep the granular metadata expressed within the RO-Crate metadata file. As detailed in \[[Fouilloux 2023]\], a series of templates assist users in creating research objects with particular content and annotations.

#### Making ad-hoc vocabularies in Crate-O {#crate-o}

The [Crate-O](https://language-research-technology.github.io/crate-o/) tool has been developed by Language Data Commons of Australia [(LDaCA)](https://ldaca.edu.au/) as a general-purpose RO-Crate editor and successor to Describo \[[La Rosa 2021d]\] and Describo Online \[[La Rosa 2021c]\]. This tool can describe any folder and resources from the Web as an RO-Crate, supporting any schema.org type and property, pluggable with any rdfs vocabularies \[[Guha 2014]\]. Notably this tool is also intended for creation of such vocabularies, and is thus a lightweight user interface for building a Profile Crate (section [profiles](ch61.html#profiles)) using Schema.org style Schemas[^7] [(SoSS)](https://schema.org/docs/schemas.html).

#### Executable papers can fully represent their computation using RO-Crate {#livepublication}

[LivePublication](https://livepublication.github.io/LP_Pub_LID/) \[[Ellerm 2023]\] is a proof of concept of an *executable paper*, which interactive visualization and statistical calculations can be regenerated on the fly taking into consideration data sources updated after the paper's publication date. A [corresponding RO-Crate](https://livepublication.github.io/LP_Pub_OrchestrationCrate/) is the mechanism to enable this execution on the Globus infrastructure through an innovative use of individual RO-Crates and containers for each computable element of the paper, nested within a top-level Crate for the paper.

This novel approach shows how it is possible to use RO-Crate as an machine-actionable object, which do not rely on bundling an underlying workflow representation in an existing workflow language.

### Web-based FDOs can use RO-Crate for its metadata {#webfdo}

Section [lightweight-fdo](ch4.html#lightweight-fdo) argues that many of the FDO requirements \[[Anders 2023]\] for metadata can be implemented as *RO-Crate FDOs* (section [fair-packaging-of-researchworkflow-objects-with-ro-crate](ch8.html#fair-packaging-of-researchworkflow-objects-with-ro-crate)), with FAIR Signposting \[[Van de Sompel 2015], [Van de Sompel 2022]\] assisting navigation from persistent identifiers, and the RO-Crate containing the metadata.

This approach was first implemented in the repository WorkflowHub \[[Goble 2021], [Wittenburg 2022]\], and in the FDO Forum \[[Van de Sompel 2023]\] suggests RO-Crate with Signposting as a modern update to his OAI-ORE[^8] approach from 2008 \[[Lagoze 2008]\]. RO-Crate FDOs are being further developed within the Horizon Europe projects [EuroScienceGateway](https://eurosciencegateway.eu/) \[[Soiland-Reyes 2022f]\] and [FAIR-IMPACT](https://fair-impact.eu/) \[[Goble 2022]\].

RO-Crate FDOs complements the findings of section [signposting](ch61.html#signposting), in that RO-Crate provides FDO with a generic metadata framework and a serialization that can work both for FDOs on the Web and with legacy Handle/DOIP approaches -- this metadata role for RO-Crate in the FDO ecosystem is also highlighted by \[[Wittenburg 2023b]\].

Some extra considerations is rightly needed on identifiers to reduce relative paths challenges with RO-Crate FDOs -- for this purpose, the next specification \[[RO-Crate 1.2]\] introduce a distinction between an [attached RO-Crate](https://www.researchobject.org/ro-crate/1.2-DRAFT/structure.html#attached-ro-crate) (*has some root directory containing other files referenced by relative paths, possibly archived in a ZIP or exposed on the Web*) and a [detached RO-Crate](https://www.researchobject.org/ro-crate/1.2-DRAFT/structure.html#detached-ro-crate) (*no defined root directory, all references are absolute*). This *detached* style is suitable for an FDO architecture, even for use within APIs which do not lend themselves to relative path references (such as DOIP-over-HTTP \[[CNRI 2023a]\]). RO-Crate 1.2 also define methods for [converting between attached/detached](https://www.researchobject.org/ro-crate/1.2-DRAFT/appendix/relative-uris.html) crates using standard JSON-LD tooling, showing another advantage of using Linked Data as basis for RO-Crate.

### How FAIR are RO-Crates? {#fair-crates}

FAIROs \[[González 2022]\] is a framework for calculating a "FAIRness" score for research objects. For RO-Crate evaluation this puts additional requirements on the use of persistent identifier for the RO-Crate, and that the core metadata of the crate (e.g. licensing) is provided. These aspects are important for ensuring FDO machine actionability of RO-Crates.

Another aspect of FAIRness for RO-Crate is if extensions are themselves following FAIR principles (RDA-I2-01M *Metadata uses FAIR-compliant vocabularies*). The Profile Crate specifications for [extension vocabularies](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles#extension-vocabularies) recommends the use of `DefinedTerm` or `DefinedTermSet` as a mechanism to "import" an existing term or vocabulary to the profile, allowing a neutral way to define these terms independent of their ontology technology. There is some tension with Crate-O's "Schema.org style Schemas" (see section [crate-o](ch61.html#crate-o)) which desired compatibility with `rdfs:Class` and `rdfs:Property` and wide-spread RDFS tooling -- the RO-Crate community consensus is to use the rdfs types when the term is *defined* by the profile rather than imported and to avoid the RDFS-like <http://schema.org/Class> and <http://schema.org/Property> overall.

The use of profiles, and particularly nested profiles as in figure [profile\_venn](ch54:fig.html#profile_venn), makes validation of RO-Crates more complex. An initial approach of [ShEx validation in runcrate](https://github.com/ResearchObject/runcrate/pull/17) extended the [ro-crate-validator-py](https://github.com/ResearchObject/ro-crate-validator-py) library to use ShEx based validation \[[Baker 2019]\] depending on declared WRROC profiles. [Future work](https://s11.no/2023/comp66090/profiles/) is planned to further investigate this using a combination of Semantic Web and RDF Shapes technologies, possibly using hierarchical profile validation with [Cheka](https://github.com/surroundaustralia/cheka) but based on the crate's declared `conformsTo` statements.

### RO-Crate can build collections of digital objects {#collections}

RO-Crate has also been proposed as a generic mechanism for FDO Collections \[[Soiland-Reyes 2023d]\], as an aggregator of FDOs by their PIDs. Such collections add a similar challenge in FDO as in Linked Data, in that clients may need to resolve an excessive number of persistent identifiers (see section [avoid-lots-of-requests](ch20.html#avoid-lots-of-requests)) to FDOs which may be of different semantic types. Using a detached RO-Crate for such collections, the bibliographic metadata of each PID can be directly embedded and normalised to a single vocabulary, reducing client needs for recursive queries and type mappings.

Work on building large data citations as a "reliquary" -- a *container of persistent identifiers (PIDs)* \[[Buck 2022]\] -- started from the earth science domain with AGU's [Data Citation Community of Practice](https://data.agu.org/DataCitationCoP/) and continues in RDA's [Complex Citation Working Group](https://www.rd-alliance.org/groups/complex-citations-working-group). In this approach RO-Crate is being considered as a promising implementation to capture large number of citations along with minimal metadata, including licensing and attribution. Here a main motivation is to avoid excessive lists of data citations for scholarly publications following processing of aggregated datasets from repositories such as GBIF \[[GBIF 2021]\], while still propagating each dataset's FAIR metadata (as required by the Creative Commons Attribution licence) through the indirection of a collection. There is a potential overlap with workflow run provenance, although a workflow is not required by reliquaries.

### Mutable FDOs can be captured in knowledge graphs using RO-Crate {#datalakes}

Knowledge Enhanced Digital Objects [(KEOD)](https://github.com/luoyu357/KEDODataLake) \[[Luo 2022]\] is an experimental approach of building a data lake using a combination of knowledge graphs, RO-Crate and PID records \[[Luo 2023]\]. This is effectively an FDO implementation: A KEDO PID is a Handle that identifies a KEDO Object, described using a KEDO RO-Crate. This crate again has *internal RO-Crate*s as parts, which records a combination of *Features* and *Insights*. The distinction is that features are mainly fixed at digital object creation and considered directly describing the object's nature, while insights can be discovered later from further processing and linkage. This approach solves a mutability problem in FDOs, as the KEOD system only allows insights to be added along with provenance that connect PIDs when KEDOs evolve. Files in a KEDO RO-Crate are stored locally, and each recorded with a Handle PID within the crate.

This KEOD setup of multiple graphs forming a single knowledge unit can be considered analoguous to nanopublications \[[Kuhn 2021]\] but for FDOs. Indeed using nanopublication to capture FDOs of digital twins has also been proposed \[[Schultes 2022]\], however, that use a different distributed architecture where the PIDs for nanopublications are generated by cryptographically hashing their content \[[Kuhn 2021]\].

### Distributed architectures for FAIR Digital Objects can use detached crates {#dpid}

The [DeSci Nodes](https://docs.desci.com/) system has been developed by the [DeSci foundation](https://www.descifoundation.org/), where [dPID](https://www.dpid.org/) (distibuted Persistent Identifier) act as an overlay of the Interplanetary File System (IPFS) \[[Trautwein 2022]\]. Users can interact with the DeSci platform for building and publishing Research Objects, and the [DeSci metadata](https://docs.desci.com/learn/open-state-repository/metadata) are exposed as a [detached RO-Crate](https://www.researchobject.org/ro-crate/1.2-DRAFT/structure.html#detached-ro-crate) with IPFS references (see [example dPID](https://beta.dpid.org/46?jsonld)). DeSci Nodes have documented a [FAIR Implementation Profile](https://docs.desci.com/learn/fair-data/fair-compliance/desci-nodes-fip) (FIP) \[[Schultes 2020]\] documenting compliance with FAIR principles.

This is a novel FAIR Digital Object implementation that challenges both the traditional centralised FDO approach using the Handle system, as well as the mostly Web-based RO-Crate ecosystem covered in section [packaging-research-artefacts-with-ro-crate](ch5.html#packaging-research-artefacts-with-ro-crate). It remains to be independently verified if the decentralisation of IPFS is effectively constrained by access through a centralised API, or if dPIDs can be retrieved from multiple independent resolvers.

The use of detached crates has also been utilised by the [Language Data Commons of Australia Program](https://www.researchobject.org/ro-crate/in-use/LDaCA.html), where RO-Crate is part of navigating centralised API resources, rather than a standalone publication on the Web. In both of these approaches, additional FDO measures such as using persistent identifiers and validation against profiles become important.

Workflows capture computational methods {#workflow}
---------------------------------------

[Chapter 5](/2023/phd/workflows/) explored in depth different ways in which FAIR Digital Objects and RO-Crate are applied to computational workflows, in effect capturing the computational methods in a FAIR Research Object.

### Workflows can be constructed of FAIR digital objects {#workflowfdo}

As introduced in section [rq3](intro.html#rq3), we have previously proposed the concept of *FAIR Computational Workflows* \[[Goble 2020]\]. That work expands on the well-established motivations for using scientific workflow systems \[[Möller 2017], [Atkinson 2017]\], such as supporting Automation, Scalable execution, Abstraction, and Provenance \[[Ludäscher 2016]\], and highlights that workflows themselves benefit from and contribute to FAIR data, for instance providing metadata for describing workflow outputs. In addition workflow themselves can be considered digital objects that should be shared as a reproducible computational method.

Applying the FAIR principles for workflows in practice has however revealed additional challenges, such as lack of clarify of what constitutes a *workflow* as opposed to FAIR Research Software in general \[[Katz 2021b]\], or reduced reusability when the workflow requires unwritten, human-centric operations between computational steps (e.g. trivial file column manipulations) \[[Wilkinson 2022b]\].

In developing the repository [WorkflowHub](https://workflowhub.eu/) \[[Goble 2021]\] we emphasised the importance of preserving and publishing not just executable workflow definitions, but their structured descriptions independent of workflow formats as well as further references to external sources, software required (including the workflow engine). For this we developed the Workflow RO-Crate Profile \[[Bacall 2022]\], which became a foundational format for more specific workflow execution profiles (section [wrroc](ch54.html#wrroc)).

One aspect that makes workflow management systems different from research software in general, is that the they frequently encourage modularization, in that the composition of steps also can reflect the analytical process that is intended by the scientists. Mature workflow systems like Galaxy \[[Galaxy 2022]\] provide a large collection of re-usable components that wrap underlying command line tools and make them interoperable without manual adjustments. In CWL \[[Crusoe 2022]\], tool definitions include not just execution details, but also structured input/output definitions, allowing them to be reused and combined in multiple workflows.

Section [making-canonical-workflow-building-blocks-interoperable-across-workflow-languages](ch6.html#making-canonical-workflow-building-blocks-interoperable-across-workflow-languages) explored how such building blocks can themselves be considered FAIR digital objects. These assist workflow systems in propagating rich metadata about tools and their analytical purpose, but also allows building blocks to be reused across workflow systems. This in effect means that a *canonical workflow* *Wittenburg 2021* can be implemented in different workflow languages, each executing the same *canonical steps* in the same way. Given that FAIR Digital Objects emphasize machine-actionability, and we can consider workflows as FDOs, it is important to have the ability not just to reliably re-execute a workflow, but even re-use its constituent steps.

### Building FDOs incrementally challenges typing constraints {#buildingfdo}

Sections [the-specimen-data-refinery](ch8.html#the-specimen-data-refinery) and [incrementally-building-fair-digital-objects-with-specimen-data-refinery-workflows](ch7.html#incrementally-building-fair-digital-objects-with-specimen-data-refinery-workflows) showed another aspect of using such building blocks, where FDOs are the unit of communication between steps in the workflow. This approach is pushing the envelope of FAIR Digital Objects concept, by having the FDO built incrementally by different stages of the specimen digitization pipeline, and exchanged only within the workflow system before it is ready to be published. This scenario, where we experimented with strict validation with JSON Schema for every step, highlighted limitations of having larger composite FDO object types, as intermediate FDOs would not validate without significantly softening the schema. In effect the Specimen Data Refinery (SDR) workflow can be considered as a variant of the classic *Builder pattern* [@Gamma; @1995 pp. 97--106], which gradually constructs an object through a series of operations on an intermediate object (the builder). However, as highlighted by section [fdo-lessons](ch7.html#fdo-lessons), ducktyping-like profiles/interfaces are needed for typing incremental FDOs, to ensure that a later workflow step receives a partial FDO with the expected fragments populated, otherwise workflow users would be able to compose steps with the FDO in an invalid state.

The later section [the-workflow-run-ro-crate-profiles](ch54.html#the-workflow-run-ro-crate-profiles) showed how RO-Crate profiles for workflow provenance FDOs can be staggered for different granularity levels, but that is more akin to a class hierarchy, as each level builds on previous complete levels. The Five Safes Crate profile (section [trusted-workflow-run-crate](ch54.html#trusted-workflow-run-crate)) however, has a similar incremental pattern as the SDR FDOs, and the different review states should be performed in a particular order. Enforcing this for typing purposes may require explicit rule-based abstract state machines (ASM) \[[Gurevich 1995]\], as has been demonstrated for Linked Data with ASM4LD \[[Käfer 2018a], [Käfer 2018b]\].

### Flexible profiles increase adaptability of interoperable provenance {#provenance}

Section [wrroc](ch54.html#wrroc) introduced the Workflow Run Crate (WRROC) profiles for capturing workflow provenance. It was highlighted that the multiple levels were designed to ease adoptability -- indeed the different WRROC implementations (section [implementations](ch54.html#implementations)) have chosen profiles depending on the provenance available to that particular engine. In addition, some implementations had to utilise optionality of some attributes, for instance to handle dynamic workflows.

In addition the *Process Run Crate* profile was shown to be suitable also for "manual workflows" where processes are executed by hand, as illustrated by figure [baseline-usecase](fig.html#baseline-usecase). In this example, the process run is only a small part of the crate, namely to generate the synthetic dataset, but of bigger importance in this crate is the causal model that explains to humans the relationships that led to the synthetic dataset. There is no overall computational workflow as the individual computational steps are performed with human interaction; however, this also means the RO-Crate metadata must be created by human interaction.

{{< figure src="baseline-usecase.svg" link="baseline-usecase.svg" id="figure1" 
  width="100%" title="Example of RO-Crate using the Process Run Crate profile"
  caption="" >}}

![**Example of RO-Crate using the Process Run Crate profile** to describe a BY-COVID use case for modelling vaccine effectiveness \[[Meurisse 2023]\]. The crate *hasPart* multiple data entities, and *mentions* several process runs according to the profile. The use case is further described with extra schema.org attributes like *temporalCoverage*. Screenshot of RO-Crate preview HTML, modified for print from <https://w3id.org/ro/doi/10.5281/zenodo.6913045> ](figures/ch09/baseline-usecase.pdf){#fig:baseline-usecase height="\\textheight"}

The community making WRROC involved multiple developers from different backgrounds and a variety of workflow systems. A lesson to learn from that experience is that even though RO-Crate profiles give additional rigidity (as discussed in section [profiles](ch61.html#profiles)) that enable interoperability like the *runcrate run* reproducibility in section [runcrate](ch54.html#runcrate), profiles need to also ensure sufficient flexibility for individual implementations of different capabilities and purposes. Profiles are therefore different from stricter type systems and bounded schemas as otherwise used by FDO implementations and Linked Data ontologies.

An interoperability challenge remains on how much flexibility to permit, as discussed in [profiles](ch61.html#profiles). However it is arguably more interoperable to have optional features defined by the community when needed, rather than individual vendor extensions -- giving common ground and graceful fallback. This practice is in line with FDO principle FDO-FDOR4 (*can include other community defined and registered attributes*) \[[Anders 2023]\] and FAIR principle RDA-R1.3-01M (*Metadata complies with a community standard*) \[[FAIR Maturity 2020]\].

### Profiles should not need to define subclasses

Part of RO-Crate's philosophy is to use Semantic Web technology while avoiding many of its pitfalls discussed in section [semweb](ch3.html#semweb) and [simplicity](ch5.html#simplicity). An unusual consequence of this is that extension profiles like WRROC end up reusing multiple types for the same entity. For instance, the *CreateAction* representing a [process run](https://w3id.org/ro/wfrun/process/0.4) has an *instrument* to either a `SoftwareApplication`, `SoftwareCourceCode` or `ComputationalWorkflow`. In the specialising profile for [workflow run](https://w3id.org/ro/wfrun/workflow/0.4) the actual type of the instrument is however a combination: `["File", "SoftwareSourceCode", "ComputationalWorkflow"]`

Traditional ontology thinking such as with OWL and RDFS would be to create a class hierarchy, indeed both <http://schema.org/SoftwareSourceCode> and <http://schema.org/MediaObject> (aliased as `File` in RO-Crate's JSON-LD) are subtypes of <http://schema.org/CreativeWork> which has most of the useful properties like *author* and *license*. It would however not be RO-Crate's job to modify the existing schema.org class hierarchy to inject artificial superclasses like *ApplicationOrSourceCodeOrWorkflow*, neither would it be desirable to create a subproperty of *instrument* with the intended *domainIncludes*, as that means using custom terms that diverge from schema.org.

It is an important part of the simplification of the Semantic Web in RO-Crate that consumers should not need to do any ontology retrieval or reasoning. For RO-Crate users it is therefore natural to occassionally combine types, enabling properties from both. schema.org is not a strict ontology with disjoint classes, so this usually do not cause any problem. It is however not desirable to re-iterate supertypes already defined within schema.org such as *CreativeWork*.

RO-Crate profiles like WRROC live are doing a combination of *restrictions* (requiring the crate to have a particular entity) and *extensions* (suggesting additional terms to use). By following the RO-Crate philosophy the profiles also reuse existing schema.org types as much as possible, adding a filtered overlay of their many properties, just like RO-Crate itself, and only adding terms where no appropiate alternative exist.

Listing [wrroc-in-owl](ch61.html#wrroc-in-owl) shows an attempt to declare the partial WRROC requirements from the top of this section in OWL. In doing so it was necessary to introduce additional types for the profile and the action, in addition to anonymous union classes and inverse properties. It is clear that expressing a full RO-Crate profile in this matter would require a deep understanding of OWL ontologies and would require its own set of unit tests, and would not be inline with the RO-Crate philosophy of *just enough Linked Data*.

However, that is not to say that such OWL rules cannot be generated from simpler definitions of RO-Crate profile requirements. Of future consideration is that the tool Crate-O's [Editor profiles](https://github.com/Language-Research-Technology/ro-crate-editor-profiles) (mainly for driving the UI form generations), and [LinkML](https://linkml.io/linkml/) which can generate ShEx, SHACL, OWL and JSON-LD context from a concise YAML definition -- in coordination with validation as discussed in section [fair-crates](ch61.html#fair-crates).

### Linked data provenance models can be made approachable

As dicussed in sections [rq3](intro.html#rq3) and [introduction](ch54.html#introduction), the subject of capturing provenance from computational workflow executions is both diverse and mature, with most of the implementations coalescing on the W3C PROV data model \[[Moreau 2013]\], and in particular specializations of the OWL ontology serialization PROV-O \[[Lebo 2013a]\]. Yet even with earlier approaches like Research Objects wfprov \[[Belhajjame 2015]\], D-PROV \[[Missier 2013]\] and CWLProv \[[Khan 2019]\], the uptake of these technologies by scientific workflow systems is fragmented at best.

Given these approaches rely on Semantic Web technology and hierarchies of ontologies, it is not a far stretch to hypothesie that some of the challenges on uptake of Linked Data we discussed in section [ld](ch3.html#ld) and [simplicity](ch5.html#simplicity) also apply to the use of PROV-O by workflow systems developers.

A core concern for workflow users is to get hold of and distribute their result data -- the exact computational structure is often of less concern as it is taken for given from the workflow definition. A change of focus from process-oriented to data-oriented will therefore also be beneficial for workflow provenance.

Targeted workflow provenance models like Biocompute Objects (BCO) \[[IEEE 2791-2020], [Alterovitz 2018]\], discussed in sections [regulatorysciences](ch5.html#regulatorysciences) and [bco-crate](ch54.html#bco-crate), emphasise the *context* of the workflow -- what is the purpose? What are possible inputs? What data sources are referenced? BCO is being implemented by workflow management systems in Life Science domain including Nextflow and Galaxy, but is perhaps not deemed generic enough for other domains like earth sciences or astronomy. While extensions are possible in BCO (e.g. [FHIR](https://wiki.biocomputeobject.org/index.php?title=Extension-fhir)) they are separate from the rest of the descriptions and do not natively support Linked Data principles.

The aspect of documenting the context and human processing is also emphasised by Five Safes Crate \[[Soiland-Reyes 2023f]\] as discussed in section [trusted-workflow-run-crate](ch54.html#trusted-workflow-run-crate). Here the \[[schema actions]\] are used to record the review process in a restricted environment for sensitive data, while also progressing the crate towards becoming a Workflow Run Crate. This model has built interest beyond workflow computations in the health data research area, amongst implementers who are not native speakers of FAIR principles or Linked Data technologies.

Section [implementations](ch54.html#implementations) presented the range of workflow systems that have implemented WRROC, and section [exemplary-use-cases](ch54.html#exemplary-use-cases) illustrated usage in the biomedical domain. While it is too early to tell to what extent WRROC is an approachable lightweight provenance model that can be implemented for many different research domains, the reception from those approaching it so far has been overwhelmingly positive. At the same time, new members of the WRROC community tend to contribute new requirements or adjustments that means the model is both maturing and evolving.

### Combining provenance and metadata models gives the best of both worlds

The intention of Workflow Run Crate, and indeed RO-Crate overall, is not to replace all existing Linked Data descriptions of research data and workflows. Even if the format of RO-Crate is JSON-LD, and in theory can support any RDF vocabulary, that does not mean that doing so is the right design decision. The engineering principle of *separation of concern* applies just as well to Linked Data formats which seem possible to integrate -- in other words, just because it is *possible* to merge two knowledge graphs that does not mean they should be!

The FAIR community has a long history of developing metadata standards, ontologies and provenance models. Research domains have also developed specific vocabularies and formats for repository submissions (often CSV-based), and likewise domain-specific models for making their registered data available as FAIR resources (often RDF-based, now more frequently JSON).

If we consider the lessons of evaluating FAIR Digital Objects and Linked Data in [Chapter 3](/2023/phd/fdo-and-linked-data/), and the philosophy of RO-Crate from [Chapter 4](/2023/phd/ro-crate/), then it would seem important to facilitate proliferation of existing community standards, but also make their content more generally Findable and Accessible using a common overlay.

An approach that we have found useful with RO-Crate is therefore to propagate the existing provenance and metadata serializations, but also annotate their format and profiles in the RO-Crate metadata as not all formats are self-describing or well-known. General metadata (e.g. authors, license, subject) can then be extracted and replicated in the RO-Crate, increasing its coverage of the domain and making the metadata available to a wider set of technologies.

One approach for this covered by section section [process-run-crate-and-cpm-ro-crate-for-cancer-detection](ch54.html#process-run-crate-and-cpm-ro-crate-for-cancer-detection) describes how the PROV-based Common Provenance Model \[[Wittner 2023a]\] is used together with RO-Crate, both as a container of identified PROV bundles and by replicating the overall computation structure in the WRROC profiles. The full details are left in the PROV serialization that is carried along within the crate, and can be combined with distributed provenance of real-life processes such as transferring a biosample between a hospital and a lab.

Likewise interoperability with existing models is important, and section [prov](ch54.html#prov) showed how WRROC provenance can be mapped back to PROV. Note that some of the workflow details could be lost or muddled in a generic mapping if they don't have a corresponding pattern in PROV -- for instance the expression of the workflow engine execution does not explicitly type it as such, that would require a particular PROV extension such as OPMW-PROV \[[Garijo 2011]\].

### A strong community trumps semantically correctness

The development of Workflow Run Crate was done as a community activity (section [conclusion](ch54.html#conclusion)), following the same pattern as RO-Crate itself (section [community](ch5.html#community)) and many activities within the ELIXIR Europe life science network \[[Harrow 2022]\].

When collectively building semantic models, particularly using ontology design patterns \[[Hitzler 2016]\], it can often take much longer to figure out what is the *meaning* of a term (e.g. its semantics) rather than how it should be formalised in an ontology language. In research domains this often comes down to considering redefining core concepts of the field itself, which in life sciences for instance easily turn into philosophical dialectic arguments \[[Falk 2010]\].

The recently started Workflows Community Initiative has a working group for [FAIR computational workflows](https://workflows.community/groups/fair/), but before it is able to formalise the FAIR principles for workflows (building on \[[Goble 2020]\]), the group had to discuss to length what is or is not a *workflow*, and what makes it different from other research software.

While such fundamentals are important to get right, they should not become blockers for community progress. In the pragmatic take by the WRROC community for instance, a reverse argument was made that it is not so important if a workflow engine exist or not, but rather that we wanted to capture \"workflowy\" provenance. The principle of "I know it when I see it" does not just apply to censorship of obscene material \[[Gewirtz 1996]\], but also to semantic design. In designing WRROC and RO-Crate it was useful to be constrained by the \[[schema.org]\] vocabulary, for instance the type <http://schema.org/HowTo> -- with current examples showing how to change tires on a car -- was also found adequate for describing a computational workflow and its steps in the Provenance Crate Profile (section [provenance-run-crate](ch54.html#provenance-run-crate)).

This forced generalization may also have helped to make the model general enough for the different forms of workflow systems who implemented it, as each would have to "squint" slightly to map the WRROC concepts to their much more specific engine concepts. This also leads to fruitful community discussions and allowing reinterpretions of existing assumptions, placing the "just enough Linked Data" idea (section [justenough](ch61.html#justenough)) into practice.

[^1]: For instance, a de-centralised, resiliant architecture and long term preservation was the motivation for the design of the Interplanetary File System (IPFS) as a *Decentralized Web* \[[Trautwein 2022]\].

[^2]: Expected type of object \[[Guha 2014]\], however note that schema.org uses <http://schema.org/rangeIncludes> instead of `rdfs:range`, to permit multiple alternatives without the need for a union class.

[^3]: Although the <http://schema.org/Dataset> type used by RO-Crate's root entity is derived from DCAT, RO-Crate does not assume a corresponding data catalogue on the Web.

[^4]: One of my earlier code contributions to ORCID already established content-negotiation to RDF -- but using the classical FOAF vocabulary \[[Brickley 2014]\]. Slightly inconsistent with Semantic Web principles, the registry is currently returning *Person* descriptions in different semantic models depending on the requested serialization.\
    <https://github.com/ORCID/ORCID-Source/blob/main/CONTENT_NEGOTIATION.md>

[^5]: To conflate matters, the `keywords` property can be repeated, but also allows multiple keywords within a single comma-separated string.

[^6]: YAML is a file format with the same data model as JSON, but with a more readable syntax, e.g. using indentation instead of quoted strings. <https://yaml.org/>

[^7]: It is notable that schema.org's own vocabulary definition use rdfs directly for Linked Data interoperability, rather than its own <http://schema.org/Class>, <http://schema.org/Property>, or the SKOS-like <http://schema.org/DefinedTerm>. On property definitions, SoSS use <http://schema.org/domainIncludes> and <http://schema.org/rangeIncludes> to avoid union classes for alternative domain/range types, which can clutter OWL/RDFS equivalent properties.

[^8]: OAI-ORE was also used by earlier Research Object approaches \[[Belhajjame 2015], [Soiland-Reyes 2014]\] to capture the aggregation aspect of ROs.



## References

See chapter [references](../../2023/references/).

[van der Aalst 2014]: https://doi.org/10.1007/978-3-319-04948-9_2 "Data Scientist: The Engineer of the Future"
[Addink 2019]: https://doi.org/10.3897/biss.3.37502 "DiSSCo as a New Regional Model for Scientific Collections in Europe"
[Afgan 2018]: https://doi.org/10.1093/nar/gky379 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2018 update"
[Afgan 2023]: https://github.com/galaxyproject/galaxy/releases/tag/v23.1.1 "galaxyproject/galaxy"
[Agarwal 2021]: https://data.agu.org/DataCitationCoP/2nd-workshop-data-citation "Data Citation Community of Practice -- 8 June 2021 Workshop"
[Albertoni 2020]: https://www.w3.org/TR/2020/REC-vocab-dcat-2-20200204/ "Data Catalog Vocabulary (DCAT) -- Version 2"
[Albertoni 2023]: https://www.w3.org/TR/2023/WD-vocab-dcat-3-20230307/ "Data Catalog Vocabulary (DCAT)- Version 3"
[Allan 2019]: https://doi.org/10.3897/BDJ.7.e32342 "A Novel Automated Mass Digitisation Workflow for Natural History Microscope Slides"
[Allcock 2005]: https://doi.org/10.1109/sc.2005.72 "The Globus Striped GridFTP Framework and Server"
[Almeida 2019]: https://doi.org/10.1038/s41586-019-0965-1 "A new genomic blueprint of the human gut microbiota"
[Alterovitz 2018]: https://doi.org/10.1371/journal.pbio.3000099 "Enabling precision medicine via standard communication of HTS provenance, analysis, and results"
[Alves 2021]: https://doi.org/10.37044/osf.io/k8znb "ELIXIR Software Management Plan for Life Sciences"
[Amorim 2016]: https://doi.org/10.1007/s10209-016-0475-y "A comparison of research data management platforms: Architecture, flexible metadata and interoperability"
[Amstutz 2021]: https://s.apache.org/existing-workflow-systems "Existing Workflow systems"
[Amstutz 2023]: https://doi.org/10.5281/zenodo.7575947 "common-workflow-language/cwltool: 3.1.20230127121939"
[Anders 2022]: https://doi.org/10.5281/zenodo.7825630 "FDO PID profiles & attributes"
[Anders 2023]: https://doi.org/10.5281/zenodo.7782262 "FAIR Digital Objects Forum FDO requirement specifications"
[Andrio 2019]: https://doi.org/10.1038/s41597-019-0177-4 "BioExcel Building Blocks, a software library for interoperable biomolecular simulation workflows"
[ANSI/NISO Z39.99-2017]: https://doi.org/10.3789/ansi.niso.z39.99-2017 "ANSI/NISO Z39.99-2017, ResourceSync Framework Specification"
[Arend 2022]: https://doi.org/10.37044/osf.io/c724r "BioHackEU22 Project 22: Plant data exchange and standard interoperability"
[Arfaoui 2020]: https://github.com/GhaithArf/ro-crate-rda-madmp-mapper "RO-Crate RDA maDMP Mapper"
[Arkisto 2022]: https://arkisto-platform.github.io/tools/portal/ "Tools: Data Portal & Discovery"
[Atkinson 2017]: https://doi.org/10.1016/j.future.2017.05.041 "Scientific workflows: Past, present and future"
[Atkinson 2019]: https://www.w3.org/TR/2019/NOTE-dx-prof-20191218/ "The Profiles Vocabulary"
[Ayris 2016]: https://doi.org/10.2777/940154 "Realising the European Open Science Cloud"
[Azeroual 2022]: https://hdl.handle.net/11366/2243 "Putting FAIR Principles in the Context of Research Information: FAIRness for CRIS and CRIS for FAIRness"
[Bacall 2019]: https://esciencelab.org.uk/projects/ro-composer/ "eScienceLab: RO-Composer"
[Bacall 2022]: https://w3id.org/workflowhub/workflow-ro-crate/1.0 "Workflow RO-Crate Profile 1.0"
[Bacall 2022b]: https://github.com/ResearchObject/ro-crate-ruby "GitHub -- ResearchObject/ro-crate-ruby: A Ruby gem for creating, manipulating and reading RO-Crates"
[Bahra 2011]: https://doi.org/10.21957/nr843dob "Managing work flows with ecFlow"
[Bahui 2020]: https://doi.org/10.5334/dsj-2020-041 "The FAIR data maturity model: An approach to harmonise FAIR assessments"
[Baker 2013]: https://doi.org/10.1016/j.websem.2013.05.001 "Key choices in the design of Simple Knowledge Organization System (SKOS)"
[Baker 2019]: http://shex.io/shex-primer/ "Shape Expressions (ShEx) 2.1 Primer"
[Baker 2020]: https://doi.org/10.1371/journal.ppat.1008643 "No more business as usual: Agile and effective responses to emerging pathogen threats require open data and open analytics"
[Barker 2019]: https://doi.org/10.5334/dsj-2019-044 "The Australian Research Data Commons"
[Barker 2022]: https://doi.org/10.1038/s41597-022-01710-x "Introducing the FAIR Principles for research software"
[Batista 2022]: https://doi.org/10.1038/s41597-022-01707-6 "Machine actionable metadata models"
[Baxter 2012]: https://www.research.ed.ac.uk/en/publications/e8416ad7-750f-442f-9b17-d812b9bb414d "The Research Software Engineer"
[Bayarri 2021a]: https://doi.org/10.48546/workflowhub.workflow.29.3 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in CWL"
[Bayarri 2021b]: https://doi.org/10.48546/workflowhub.workflow.120.2 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in Jupyter Notebook"
[Bayarri 2022]: https://doi.org/10.48546/workflowhub.workflow.255.1 "CWL GMX Automatic Ligand Parameterization tutorial"
[Bechhofer 2013]: https://doi.org/10.1016/j.future.2011.08.004 "Why Linked Data is not enough for scientists"
[Beg 2021]: https://doi.org/10.1109/MCSE.2021.3052101 "Using Jupyter for Reproducible Scientific Workflows"
[Beier 2024]: https://doi.org/10.37044/osf.io/7y2jh "Enabling continuous RDM using Annotated Research Contexts with RO-Crate profiles for ISA"
[Belchev 2021]: https://github.com/KockataEPich/CheckMyCrate "KockataEPich/CheckMyCrate: A command line application for validating a RO-Crate object against a JSON profile"
[Belhajjame 2015]: https://doi.org/10.1016/j.websem.2015.01.003 "Using a suite of ontologies for preserving workflow-centric research objects"
[Belshe 2022]: https://doi.org/10.17487/rfc7540 "Hypertext Transfer Protocol Version 2 (HTTP/2)"
[Beltrán 2023]: https://doi.org/10.5281/zenodo.10199020 "Autosubmit v4.0.100"
[Benureau 2017]: https://doi.org/10.3389/fninf.2017.00069 "Re-run, repeat, reproduce, reuse, replicate: Transforming code into scientific contributions"
[Berman 2007]: https://doi.org/10.1093/nar/gkl971 "The worldwide Protein Data Bank (wwPDB): Ensuring a single, uniform archive of PDB data"
[Berners-Lee 1998]: https://www.w3.org/Provider/Style/URI "Cool URIs don't change"
[Berners-Lee 1999]: https://identifiers.org/isbn/9780062515865 "Weaving the Web: The original design and ultimate destiny of the World Wide Web by its inventor"
[Berners-Lee 2000]: https://www.w3.org/2000/Talks/1206-xml2k-tbl/slide10-0.html "Semantic Web on XML"
[Berners-Lee 2005]: https://doi.org/10.17487/rfc3986 "Uniform Resource Identifier (URI): Generic Syntax"
[Berners-Lee 2006]: https://www.w3.org/DesignIssues/LinkedData.html "Linked Data"
[Bernstein 2016]: https://doi.org/10.1145/2890489 "A new look at the semantic web"
[Bietrix 2021]: https://doi.org/10.5281/zenodo.4705078 "EOSC-Life methodology framework to enhance reproducibility within EOSC Life"
[BioMoby 2008]: https://doi.org/10.1093/bib/bbn003 "Interoperability with Moby 1.0---It's better than sharing your toothbrush!"
[Bishop 2022]: https://doi.org/10.17487/rfc9114 "HTTP/3"
[Bizer 2009]: https://doi.org/10.4018/jswis.2009081901 "Linked Data - The Story So Far"
[Bizer 2011]: https://doi.org/10.4018/978-1-60960-593-3.ch008 "Linked data: The story so far"
[Blanchi 2022]: https://doi.org/10.5281/zenodo.7825549 "FDO -- upload of FDO"
[Blanchi 2023]: https://doi.org/10.5281/zenodo.7825572 "Implementation of attributes, types, profiles and registries"
[Blankenberg 2014]: https://doi.org/10.1186/gb4161 "Dissemination of scientific software with Galaxy ToolShed"
[Blomquist 2009]: https://doi.org/10.1145/1597735.1597743 "Experiments on pattern-based ontology design"
[Bonino 2016]: https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability "FAIR Data points supporting big data interoperability"
[Bonino 2019]: https://github.com/GEDE-RDA-Europe/GEDE/blob/master/FAIR\%20Digital\%20Objects/FDOF/FAIR\%20Digital\%20Object\%20Framework-v1-02.docx "FAIR digital object framework v1.02"
[Bonino 2020]: https://fairdigitalobjectframework.org/ "FAIR Digital Object Framework Documentation"
[Bouyssié 2023]: https://doi.org/10.1101/2023.10.02.560412 "WOMBAT-P: Benchmarking Label-Free Proteomics Data Analysis Workflows"
[Brack 2022a]: https://doi.org/10.1371/journal.pcbi.1009823 "Ten Simple Rules for making a software tool workflow-ready"
[Brack 2022b]: https://doi.org/10.48546/workflowhub.workflow.373.1 "De novo digitisation."
[Brand 2015]: https://doi.org/10.1087/20150211 "Beyond authorship: Attribution, contribution, collaboration, and credit"
[Bray 2017]: https://doi.org/10.17487/rfc8259 "The JavaScript Object Notation (JSON) Data Interchange Format"
[Brenner 2020]: https://github.com/BrennerG/Ro-Crate_2_ma-DMP "BrennerG/Ro-Crate\_2\_ma-DMP: v1.0.0"
[Brickley 2014]: http://xmlns.com/foaf/spec/ "FOAF Vocabulary Specification"
[Broeder 2022]: https://drive.google.com/file/d/1KJ9l0p96naKi_2HPJ_MPqPTwS_zlP92G "FDO glossary november 2022"
[Buck 2022]: https://doi.org/10.1002/essoar.10509966.1 "AGU data citation community of practice - Credit for creators of data within collections using the concept of a reliquary"
[Capadisli 2017]: https://www.w3.org/TR/2017/REC-ldn-20170502/ "Linked Data Notifications"
[Cardoso 2020a]: https://doi.org/10.1007/978-3-030-45442-5_15 "Machine-actionable data management plans: A knowledge retrieval approach to automate the assessment of funders' requirements"
[Cardoso 2020b]: https://repository.publisso.de/resource/frl:6423289 "Towards Semantic Representation of Machine-Actionable Data Management Plans"
[Carranza-Rojas 2017]: https://doi.org/10.1186/s12862-017-1014-z "Going deeper in the automated identification of Herbarium specimens"
[Carriero 2010]: https://doi.org/10.3233/ssw200033 "The landscape of ontology reuse approaches"
[Carrothers 2014]: http://www.w3.org/TR/2014/REC-n-triples-20140225/ "RDF 1.1 N-Triples"
[Chard 2014]: https://doi.org/10.1109/MCC.2014.52 "Efficient and secure transfer, synchronization, and sharing of big data"
[Chard 2016]: https://static.aminer.org/pdf/fa/bigdata2016/BigD418.pdf "I'll take that to go: Big data bags and minimal identifiers for exchange of large, complex datasets"
[Chard 2019]: https://zenodo.org/record/3381754 "Application of BagIt-serialized research object bundles for packaging and re-execution of computational analyses"
[Chard 2020]: https://doi.org/10.3233/APC200107 "Toward enabling reproducibility for data-intensive research using the Whole Tale platform"
[Ciccarese 2013]: https://doi.org/10.1186/2041-1480-4-37 "PAV ontology: Provenance, authoring and versioning"
[Ciccarese 2017]: https://www.w3.org/TR/2017/REC-annotation-model-20170223/ "Web Annotation Data Model"
[Claerbout 1992]: http://sep.stanford.edu/oldsep/matt/join/redoc/web/seg92.html "Electronic documents give reproducible research a new meaning"
[Clemm 2002]: https://doi.org/10.17487/rfc3253 "Versioning Extensions to WebDAV"
[CNRI 2023a]: https://www.cordra.org/documentation/api/doip-api-for-http-clients.html "DOIP API for HTTP Clients"
[CNRI 2023b]: https://www.cordra.org/documentation/api/doip.html "DOIP and Examples"
[Cohen 2020]: https://doi.org/10.1109/MS.2020.2973362 "The Four Pillars of Research Software Engineering"
[Cohen-Boulakia 2017]: https://hal.archives-ouvertes.fr/hal-01516082 "Scientific workflows for computational reproducibility in the life sciences: Status, challenges and opportunities"
[Colonnelli 2021]: https://doi.org/10.1109/TETC.2020.3019202 "StreamFlow: cross-breeding Cloud with HPC"
[Colonnelli 2023a]: https://doi.org/10.5281/zenodo.7911906 "StreamFlow run of digital pathology tissue/tumor prediction workflow"
[Colonnelli 2023b]: https://github.com/alpha-unito/streamflow/releases/tag/0.2.0.dev10 "alpha-unito/streamflow"
[Corcho 2021]: https://doi.org/10.5281/zenodo.4913285 "D5.1 RO Model Adapted to EOSC"
[Corcho 2023]: https://doi.org/10.48550/arXiv.2305.06746 "A maturity model for catalogues of semantic artefacts"
[Cossu 2018]: https://github.com/duraspace/pcdm/wiki "Portland Common Data Model"
[Costa 2013]: https://doi.org/10.1145/2457317.2457365 "Capturing and querying workflow runtime provenance with PROV"
[Crosas 2011]: https://doi.org/10.1045/january2011-crosas "The DataVerse Network: An open-source application for sharing, discovering and preserving data"
[Crosas 2020]: https://doi.org/10.7557/5.5422 "Harvard Data Commons"
[Crosswell 2012]: https://doi.org/10.1016/j.tibtech.2012.02.002 "ELIXIR: A distributed infrastructure for European biological data"
[CRS4 2022]: https://about.lifemonitor.eu/ "LifeMonitor, a testing and monitoring service for scientific workflows"
[Crusoe 2022]: https://doi.org/10.1145/3486897 "Methods Included: Standardizing Computational Reuse and Portability with the Common Workflow Language"
[Cruz 2009]: https://doi.org/10.1109/SERVICES-I.2009.18 "Towards a Taxonomy of Provenance in Scientific Workflow Management Systems"
[Cuevas-Vicenttín 2016]: https://purl.dataone.org/provone-v1-dev "ProvONE: A PROV Extension Data Model for Scientific Workflow Provenance"
[CWFR 2021]: https://osf.io/3rekv/ "Canonical Workflow Frameworks for Research"
[da Veiga Leprevost 2017]: https://doi.org/10.1093/bioinformatics/btx192 "BioContainers: An open-source and community-driven framework for software standardization"
[DCMI 2020]: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/2020-01-20/ "DCMI Metadata Terms"
[De Geest 2022]: https://doi.org/10.3897/rio.8.e95164 "Enhancing RDM in Galaxy by integrating RO-Crate"
[De Geest 2023a]: https://github.com/researchobject/ro-crate-py "GitHub -- ResearchObject/ro-crate-py: Python library for RO-Crate"
[De Geest 2023b]: https://doi.org/10.5281/zenodo.7785861 "Run of an example Galaxy collection workflow"
[De Giovanni 2016]: https://doi.org/10.1111/ecog.01552 "ENM Components: a new set of web service‐based workflow components for ecological niche modelling"
[De Roure 2010]: https://web.archive.org/web/20140828142306/http://journal.webscience.org/325/ "Anchors in shifting sand: the primacy of method in the web of data"
[De Smedt 2020]: https://doi.org/10.3390/publications8020021 "FAIR Digital Objects for Science: From Data Pieces to Actionable Knowledge Units"
[Del Rio 2022]: https://doi.org/10.1007/978-3-031-13321-3_48 "AI Support for Accelerating Histopathological Slide Examinations of Prostate Cancer in Clinical Studies"
[Delgado 2016]: https://doi.org/10.1007/978-3-319-31861-5_1 "An Interoperability Framework and Distributed Platform for Fast Data Applications"
[Desai 2016]: https://econpapers.repec.org/RePEc:uwe:wpaper:20161601 "Five Safes: designing data access for research"
[Devaraju 2021]: https://doi.org/10.5334/dsj-2021-004 "From conceptualization to implementation: FAIR assessment of research data objects"
[Dillen 2019a]: https://doi.org/10.3897/biss.3.37080 "Zenodo, an archive and publishing repository: A tale of two herbarium specimen pilot projects"
[Dillen 2019b]: https://doi.org/10.3897/BDJ.7.e31817 "A benchmark dataset of herbarium specimen imagfes with label data"
[Di Tommaso 2017]: https://doi.org/10.1038/nbt.3820 "Nextflow enables reproducible computational workflows"
[DOI 2019]: https://doi.org/10.1000/182 "DOI Handbook - Resolution"
[DONA 2018]: https://hdl.handle.net/0.DOIP/DOIPV2.0 "Digital Object Interface Protocol specification, version 2.0"
[DONA 2021]: https://www.dona.net/node/88 "Digital Object Architecture"
[Drummond 2006]: https://www.cs.man.ac.uk/~drummond/presentations/OWA.pdf "The Open World Assumption"
[Dürst 2005]: https://doi.org/10.17487/rfc3987 "Internationalized resource identifiers (IRIs)"
[Dusseault 2007]: https://doi.org/10.17487/rfc4918 "HTTP Extensions for Web Distributed Authoring and Versioning"
[Eguinoa 2020]: https://github.com/workflowhub-eu/galaxy2cwl "GitHub workflowhub-eu/galaxy2cwl"
[Eguinoa 2023]: https://doi.org/10.37044/osf.io/24jst "BioHackEU22 Report: Enhancing Research Data Management in Galaxy and Data Stewardship Wizard by utilising RO-Crates"
[Ejarque 2023]: https://doi.org/10.5281/zenodo.7975340 "COMPSs"
[Ekuan 2023]: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design "Web API design best practices"
[Ellerm 2023]: https://doi.org/10.1109/e-Science58273.2023.10254857 "LivePublication: The Science Workflow Creates and Updates the Publication"
[Ellis 2007]: https://doi.org/10.1109/ICSE.2007.85 "The Factory Pattern in API Design: A Usability Evaluation"
[EMBL-EBI 2019]: http://ftp.ebi.ac.uk/pub/databases/metagenomics/umgs_analyses/ "FTP index of /pub/databases/metagenomics/umgs\_analyses/"
[EMBL-EBI 2020]: https://github.com/Finn-Lab/MGS-gut "GitHub -- Finn-Lab/MGS-gut: Analysing Metagenomic Species (MGS)"
[EU 2016]: https://ec.europa.eu/research/participants/data/ref/h2020/grants_manual/hi/oa_pilot/h2020-hi-oa-data-mgt_en.pdf "Guidelines on FAIR Data Management in Horizon 2020"
[Ewels 2020]: https://doi.org/10.1038/s41587-020-0439-x "The nf-core framework for community-curated bioinformatics pipelines"
[FAIR Maturity 2020]: https://doi.org/10.15497/rda00050 "FAIR data maturity model: Specification and guidelines"
[Falk 2010]: https://doi.org/10.1016/j.shpsc.2010.10.014 "What is a gene?—Revisited"
[Farnel 2014]: https://dcpapers.dublincore.org/pubs/article/view/3714 "Metadata for research data: Current practices and trends"

[FDO]: https://fairdo.org/ "FAIR Digital Object Forum"
[FDO Specs]: https://hdl.handle.net/20.500.14132/fdo-spec-docs "FDO Specification Documents - November 2022"
[Feng 2007]: https://doi.org/10.1145/1254882.1254906 "PBS: a unified priority-based scheduler"
[Fenner 2019]: https://doi.org/10.5438/jwvf-8a66 "Introducing the PID graph"
[Fensel 2011]: https://doi.org/10.1007/978-3-642-19193-0 "Semantic Web Services"
[Fernández 2023a]: https://doi.org/10.5281/zenodo.10068956 "inab/WfExS-backend"
[Fernández 2023b]: https://doi.org/10.5281/zenodo.10091550 "RO-Crate from staged WfExS working directory"
[Ferreira da Silva 2021]: https://doi.org/10.48550/arXiv.2110.02168 "A Community Roadmap for Scientific Workflows Research and Development"
[Ferreira da Silva]: https://doi.org/10.48550/arXiv.2304.00019 "Workflows Community Summit 2022"
[Fielding 1999]: https://doi.org/10.17487/rfc2616 "Hypertext Transfer Protocol -- HTTP/1.1"
[Fielding 2000]: https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm "Architectural styles and the design of network-based software architectures"
[Fielding 2014a]: https://doi.org/10.17487/rfc7230 "Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing"
[Fielding 2014b]: https://doi.org/10.17487/rfc7231 "Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content"
[Fielding 2017]: https://doi.org/10.1145/3106237.3121282 "Reflections on the REST architectural style and \"principled design of the modern web architecture\" (impact paper award)"
[Fielding 2022]: https://doi.org/10.17487/rfc9110 "HTTP Semantics"
[Fillbrunn 2017]: https://doi.org/10.1016/j.jbiotec.2017.07.028 "KNIME for reproducible cross-domain analysis of life science data"
[Fouilloux 2023]: https://doi.org/10.3897/rio.9.e108765 "FAIR Research Objects for realizing Open Science with RELIANCE EOSC project"
[Freire 2008]: https://doi.org/10.1109/MCSE.2008.79 "Provenance for Computational Tasks: A Survey"
[Galaxy 2022]: https://doi.org/10.1093/nar/gkac247 "The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update"
[Gamma 1995]: https://identifiers.org/isbn/9780201633610 "Design Patterns"
[Garcia 2020]: https://doi.org/10.1371/journal.pcbi.1007808 "Ten simple rules to run a successful BioHackathon"
[Garcia-Silva 2019]: https://doi.org/10.48550/arXiv.1809.10617 "Enabling FAIR research in Earth science through research objects"
[Garijo 2011]: https://doi.org/10.1145/2110497.2110504 "A New Approach for Publishing Workflows"
[Garijo 2012]: https://ceur-ws.org/Vol-951/paper6.pdf "Augmenting PROV with Plans in P-PLAN: Scientific Processes as Linked Data"
[Garijo 2014a]: https://doi.org/10.1016/j.future.2013.09.018 "Common Motifs in Scientific Workflows: An Empirical Analysis"
[Garijo 2014b]: https://doi.org/10.1109/works.2014.13 "Towards Workflow Ecosystems through Semantic and Standard Representations"
[Gauthier 2019]: https://doi.org/10.1093/bib/bby063 "A brief history of bioinformatics"
[GBIF 2021]: https://doi.org/10.35035/bezp-jj23 "GBIF Science Review 2020"
[Gewirtz 1996]: https://heinonline.org/HOL/P?h=hein.journals/ylr105&i=1057 "On I Know It When I See It"
[Gil 2011]: https://doi.org/10.1109/MIS.2010.9 "Wings: Intelligent Workflow-Based Design of Computational Experiments"
[Giles 2023]: https://doi.org/10.5281/zenodo.10055354 "TRE-FX: Delivering a federated network of trusted research environments to enable safe data analytics"
[GitHub 2021]: https://docs.github.com/en/repositories/working-with-files/managing-large-files "Managing large files -- GitHub Docs"
[Goble 2008]: https://doi.org/10.1016/j.jbi.2008.01.008 "State of the nation in data integration for bioinformatics"
[Goble 2010]: https://doi.org/10.1093/nar/gkq429 "myExperiment: A repository and social network for the sharing of bioinformatics workflows"
[Goble 2016]: http://repscience2016.research-infrastructures.eu/img/CaroleGoble-ReproScience2016v2.pdf "What Is Reproducibility? The R* Brouhaha"
[Goble 2018]: https://doi.org/10.5281/zenodo.1313066 "Research Object Community Update"
[Goble 2020]: https://doi.org/10.1162/dint_a_00033 "FAIR Computational Workflows"
[Goble 2021]: https://doi.org/10.5281/zenodo.4605654 "Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory"
[Goble 2022]: https://doi.org/10.5281/zenodo.7157647 "FAIR-IMPACT: T3.2.1 PIDs in data production workflows"
[González 2022]: https://dgarijo.com/papers/TPDL2022_gonzalez.pdf "FAIROs: Towards FAIR Assessment in Research Objects"
[Gray 2017]: https://iswc2017.semanticweb.org/paper-579/ "Bioschemas: From Potato Salad to Protein Annotation"
[Gregorio 2007]: https://doi.org/10.17487/rfc5023 "The Atom Publishing Protocol"
[Gregorio 2012]: https://doi.org/10.17487/rfc6570 "URI Template"
[Groom 2020]: https://doi.org/10.1093/database/baaa072 "People are essential to linking biodiversity data"
[Grossman 2016]: https://doi.org/10.1109/MCSE.2016.92 "A case for data commons: Toward data science as a service"
[Groth 2014]: https://doi.org/10.1016/j.websem.2014.03.003 "API-centric Linked Data integration: The Open PHACTS Discovery Platform case study"
[Grüning 2018a]: https://doi.org/10.1038/s41592-018-0046-7 "Bioconda: Sustainable and Comprehensive Software Distribution for the Life Sciences"
[Grüning 2018b]: https://doi.org/10.1016/j.cels.2018.03.014 "Practical Computational Reproducibility in the Life Sciences"
[Guha 2014]: http://www.w3.org/TR/rdf-schema/ "RDF Schema 1.1"
[Guha 2015]: https://doi.org/10.1145/2857274.2857276 "Schema.org: Evolution of Structured Data on the Web: Big data makes common schemas even more necessary"
[Guha 2016]: https://doi.org/10.1145/2844544 "Schema.org: evolution of structured data on the web"
[Gurevich 1995]: https://identifiers.org/isbn/9780198538547 "Evolving Algebras 1993: Lipari Guide"
[Handle]: https://www.handle.net/download_hnr.html "Handle.Net Software"
[Hardisty 2016]: https://doi.org/10.1186/s12898-016-0103-y "BioVeL: a virtual laboratory for data analysis and modelling in biodiversity science and ecology"
[Hardisty 2019a]: https://doi.org/10.3897/biss.3.37033 "`openDS' -- A New Standard for Digital Specimens and Other Natural Science Digital Object Types"
[Hardisty 2019b]: https://doi.org/10.5281/zenodo.3532937 "Provisional Data Management Plan for DiSSCo infrastructure"
[Hardisty 2020]: https://doi.org/10.3897/rio.6.e54280 "Conceptual design blueprint for the DiSSCo digitization infrastructure - DELIVERABLE D8.1"
[Hardisty 2022]: https://doi.org/10.1162/dint_a_00134 "The Specimen Data Refinery"
[Harrow 2021]: https://doi.org/10.15252/embj.2020107409 "ELIXIR-EXCELERATE: establishing Europe's data infrastructure for the life science research of the future"
[Harrow 2022]: https://doi.org/10.1093/bioinformatics/btab481 "ELIXIR: providing a sustainable infrastructure for life science data at European scale"
[Hasnain 2018]: https://doi.org/10.1007/978-3-319-98192-5_60 "Assessing FAIR Data Principles Against the 5-Star Open Data Principles"
[Hausenblas 2012]: http://5stardata.info/ "5-star Open Data"
[Heath 2011]: https://doi.org/10.2200/S00334ED1V01Y201102WBE001 "Linked Data: Evolving the Web into a Global Data Space"
[Heberling 2019]: https://doi.org/10.1093/biosci/biz094 "The Changing Uses of Herbarium Data in an Era of Global Change: An Overview Using Automated Content Analysis"
[Heberling 2021]: https://doi.org/10.1073/pnas.2018093118 "Data integration enables global biodiversity synthesis"
[Hellström 2022]: https://doi.org/10.5281/zenodo.7825686 "FDO -- granularity, versioning, mutability"
[Hereld 2019]: https://doi.org/10.3897/biss.3.37228 "LightningBug ONE: An experiment in high-throughput digitization of pinned insects"
[Herschel 2017]: https://doi.org/10.1007/s00778-017-0486-1 "A survey on provenance: What for? What form? What from?"
[Himanen 2019]: https://doi.org/10.1002/advs.201900808 "Data-Driven Materials Science: Status, Challenges, and Perspectives"
[Hitzler 2016]: https://identifiers.org/isbn/9781614996767 "Ontology engineering with ontology design patterns"
[Holland 2014]: http://blog.schema.org/2014/06/introducing-role.html "Introducing 'Role'"
[Horrocks 2022]: https://doi.org/10.1007/3-540-48005-6 "The Semantic Web --- ISWC 2002"
[Hospital 2020]: https://doi.org/10.5281/zenodo.4540432 "BioExcel-2 Deliverable 2.3 -- First release of demonstration workflows"
[Hospital 2021a]: https://doi.org/10.48546/workflowhub.workflow.200.1 "Protein MD Setup HPC tutorial using BioExcel Building Blocks (biobb) in PyCOMPSs"
[Hospital 2021b]: https://doi.org/10.48546/workflowhub.workflow.201.1 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in KNIME"
[Hu 2011]: https://identifiers.org/isbn/9783642210334 "How matchable are four thousand ontologies on the semantic web"
[Hui 2012]: https://doi.org/10.1111/j.1467-9973.2012.01761.x "What is a Digital Object?"
[Huntingford 2019]: https://doi.org/10.1088/1748-9326/ab4e55 "Machine learning and artificial intelligence to aid climate change research and preparedness"
[Hussein 2021]: https://doi.org/10.48550/arXiv.2104.08732 "Application of Computer Vision and Machine Learning for Digitized Herbarium Specimens: A Systematic Literature Review"
[IEEE 2791-2020]: https://research.manchester.ac.uk/en/publications/936de52b-ac53-4f0e-9927-77fd7073e88d "IEEE Standard for Bioinformatics Analyses Generated by High-Throughput Sequencing (HTS) to Facilitate Communication"
[Isaac 2009]: https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/ "SKOS Simple Knowledge Organization System Primer"
[Islam 2020]: https://doi.org/10.5334/dsj-2020-050 "Incorporating RDA Outputs in the Design of a European Research Infrastructure for natural history Collections"
[Islam 2023]: https://doi.org/10.3233/FC-230001 "FAIR digital objects, persistent identifiers and machine actionability"
[ISO 16684]: https://www.iso.org/standard/75163.html "ISO 16684-1:2019 --- graphic technology --- extensible metadata platform (XMP)"
[ISO 23009-1]: https://www.iso.org/standard/83314.html "ISO/IEC 23009-1:2022 --- information technology --- dynamic adaptive streaming over HTTP (DASH)"
[Ison 2013]: https://doi.org/10.1093/bioinformatics/btt113 "EDAM: an ontology of bioinformatics operations, types of data and identifiers, topics and formats"
[Ison 2021]: https://doi.org/10.1093/gigascience/giaa157 "biotoolsSchema: a formalized schema for bioinformatics software description"
[ITU-T X.1255]: https://www.itu.int/rec/T-REC-X.1255-201309-I "X.1255 : Framework for Discovery of Identity Management Information"
[Ivonne 2023]: https://doi.org/10.5281/zenodo.7824714 "FAIR digital object technical overview"
[Iyengar 2021]: https://doi.org/10.17487/rfc9000 "QUIC: A UDP-Based Multiplexed and Secure Transport"
[Jacobsen 2020]: https://doi.org/10.1162/dint_r_00024 "FAIR Principles: Interpretations and Implementation Considerations"
[Jaradeh 2019]: https://doi.org/10.1007/978-3-030-30760-8_31 "Open research knowledge graph: A system walkthrough"
[Jensen 2017]: https://doi.org/10.1182/blood-2017-03-735654 "The NCI Genomic Data Commons as an engine for precision medicine"
[Jones 2021]: https://doi.org/10.5281/zenodo.4477164 "Science-on-Schema.org v1.2.0"
[Jones 2022]: https://swordapp.github.io/swordv3/swordv3.html "SWORD 3.0 Specification"
[Joras 2020]: https://engineering.fb.com/2020/10/21/networking-traffic/how-facebook-is-bringing-quic-to-billions "How Facebook is bringing QUIC to billions"
[JSONPath 2023]: https://datatracker.ietf.org/doc/id/draft-ietf-jsonpath-base-10 "JSONPath: Query Expressions for JSON"
[Jupyter 2018]: https://doi.org/10.25080/majora-4af1f417-011 "Binder 2.0 - Reproducible, Interactive, Sharable Environments for Science at Scale"
[Juty 2011]: https://doi.org/10.1093/nar/gkr1097 "Identifiers.org and MIRIAM Registry: Community resources to provide persistent identification"
[Juty 2020]: https://doi.org/10.1162/dint_a_00025 "Unique, Persistent, Resolvable: Identifiers as the foundation of FAIR"
[Kahn 1995]: http://www.cnri.reston.va.us/k-w.html "A framework for distributed digital object services"
[Kahn 2006]: https://doi.org/10.1007/s00799-005-0128-x "A framework for distributed digital object services"
[Kallinikos 2013]: https://www.jstor.org/stable/43825913 "The ambivalent ontology of digital artifacts"
[Kamdar 2017]: https://doi.org/10.3233/sw-160238 "A systematic analysis of term reuse and term overlap across biomedical ontologies"
[Katsumi 2016]: https://doi.org/10.3233/978-1-61499-660-6-9 "What is ontology reuse?"
[Katz 2021a]: https://doi.org/10.48550/arXiv.2101.10883 "A Fresh Look at FAIR for Research Software"
[Katz 2021b]: https://doi.org/10.1016/j.patter.2021.100222 "A Fresh Look at FAIR for Research Software"
[Kelly 2016]: https://datatracker.ietf.org/doc/draft-kelly-json-hal/08/ "JSON Hypertext Application Language"
[Khan 2019]: https://doi.org/10.1093/gigascience/giz095 "Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv"
[Khare 2000]: https://doi.org/10.17487/rfc2817 "Upgrading to TLS Within HTTP/1.1"
[Kharouba 2019]: https://doi.org/10.1098/rstb.2017.0405 "Using insect natural history collections to study global change impacts: challenges and opportunities"
[Kim 2008]: https://doi.org/10.1002/cpe.1228 "Provenance trails in the Wings/Pegasus system"
[Kinoshita 2023]: https://doi.org/10.5281/zenodo.8144612 "RO-Crate created using Autosubmit version 4.0.100 workflow running kinow/auto-mhm-test-domains"
[Klein 2014]: https://doi.org/10.1371/journal.pone.0115253 "Scholarly Context Not Found: One in Five Articles Suffers from Reference Rot"
[Klímek 2019]: https://doi.org/10.3233/SW-180316 "Survey of tools for linked data consumption"
[Kluyver 2016]: https://doi.org/10.3233/978-1-61499-649-1-87 "Jupyter Notebooks – a publishing format for reproducible computational workflows"
[Knyshov 2021]: https://doi.org/10.1093/isd/ixab004 "Pretrained Convolutional Neural Networks Perform Well in a Challenging Test Case: Identification of Plant Bugs (Hemiptera: Miridae) Using a Small Number of Training Images"
[Koesten 2020]: https://doi.org/10.1016/j.patter.2020.100136 "Dataset reuse: Toward translating principles to practice"
[Koesten 2021]: https://doi.org/10.1016/j.ijhcs.2020.102562 "Talking datasets -- understanding data sensemaking behaviours"
[Kontokostas 2017]: https://www.w3.org/TR/shacl/ "Shapes Constraint Language (SHACL)"
[Köster 2012]: https://doi.org/10.1093/bioinformatics/bts480 "Snakemake—a scalable bioinformatics workflow engine"
[Kuhn 2021]: https://doi.org/10.7717/peerj-cs.387 "Semantic micro-contributions with decentralized nanopublication services"
[Kumar 2013]: https://doi.org/10.1029/2012WR012195 "Implications of distributed hydrologic model parameterization on water fluxes at multiple scales and locations"
[Kunze 2018]: https://doi.org/10.17487/rfc8493 "The BagIt File Packaging Format"
[Kunze 2022]: https://datatracker.ietf.org/doc/draft-kunze-ark/36/ "The ARK Identifier Scheme"
[Kurowski 2021]: https://doi.org/10.2777/620649 "EOSC Interoperability Framework"
[Käfer 2018a]: http://events.linkeddata.org/ldow2018/papers/LDOW2018_paper_7.pdf "Rule-based Programming of User Agents for Linked Data"
[Käfer 2018b]: https://doi.org/10.1007/978-3-030-00671-6_25 "Specifying, Monitoring, and Executing Workflows in Linked Data Environments"
[La Rosa 2021a]: https://github.com/CoEDL/modpdsc/ "GitHub -- CoEDL/modpdsc"
[La Rosa 2021b]: https://github.com/CoEDL/ocfl-tools "GitHub -- CoEDL/ocfl-tools: Tools to process and manipulate an OCFL tree"
[La Rosa 2021c]: https://arkisto-platform.github.io/describo-online/ "Arkisto Platform: Describo Online"
[La Rosa 2021d]: https://arkisto-platform.github.io/describo/ "Arkisto Platform: Describo"
[Labra Gayo 2017]: https://doi.org/10.2200/s00786ed1v01y201707wbe016 "Validating RDF Data"
[Lagoze 2008]: http://www.openarchives.org/ore/1.0/datamodel#Proxies "ORE Specification - Abstract Data Model"
[Lammey 2020]: https://doi.org/10.6087/kcse.192 "Solutions for identification problems: A look at the research organization registry"
[Lamprecht 2019]: https://doi.org/10.3233/DS-190026 "Towards FAIR principles for research software"
[Lamprecht 2021]: https://doi.org/10.12688/f1000research.54159.1 "Perspectives on automated composition of workflows in the life sciences"
[Lannom 2020]: https://doi.org/10.1162/dint_a_00034 "FAIR Data and Services in Biodiversity Science and Geoscience"
[Lannom 2022a]: https://doi.org/10.5281/zenodo.7825703 "FDO configuration types"
[Lannom 2022b]: https://doi.org/10.5281/zenodo.7824673 "FAIR digital objects roadmap. Version 5 november 2022"
[Lannom 2022c]: https://doi.org/10.5281/zenodo.7825599 "Typing FAIR digital objects"
[Lanthaler 2021]: http://www.hydra-cg.com/spec/latest/core/ "Hydra Core Vocabulary"
[Lassila 1999]: https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/ "Resource Description Framework (RDF) Model and Syntax Specification"
[Lebo 2013a]: https://www.w3.org/TR/2013/REC-prov-o-20130430/ "PROV-O: The PROV Ontology"
[Lebo 2013b]: https://www.w3.org/TR/2013/NOTE-prov-links-20130430/ "Linking Across Provenance Bundles"
[Lee 2018]: https://doi.org/10.1371/journal.pcbi.1006561 "Ten simple rules for documenting scientific software"
[Leipzig 2021]: https://doi.org/10.1016/j.patter.2021.100322 "The role of metadata in reproducible computational research"
[Leo 2023a]: https://github.com/ResearchObject/runcrate "runcrate"
[Leo 2023b]: https://doi.org/10.48550/arXiv.2312.07852 "Recording provenance of workflow runs with RO-Crate"
[Leo 2023c]: https://w3id.org/ro/doi/10.5281/zenodo.10368989 "Recording provenance of workflow runs with RO-Crate"
[Leo 2023]: https://doi.org/10.5281/zenodo.7774351 "Run of digital pathology tissue/tumor prediction workflow"
[Little 2020]: https://doi.org/10.1002/aps3.11365 "An algorithm competition for automatic species identification from herbarium specimens"
[Liu 2007]: https://www.w3.org/TR/2007/REC-wsdl20-primer-20070626/ "Web Services Description Language"
[Livermore 2022a]: https://doi.org/10.48546/workflowhub.workflow.374.1 "DLA-Collections-test."
[Livermore 2022b]: https://doi.org/10.48546/workflowhub.workflow.375.1 "HTR-Collections-test"
[Lohonya 2020]: https://doi.org/10.3897/BDJ.8.e50503 "Georeferencing the Natural History Museum's Chinese type collection: of plateaus, pagodas and plants"
[Loo 2022]: https://doi.org/10.3897/rio.coll.190 "First International Conference on FAIR Digital Objects"
[Lordan 2014]: https://doi.org/10.1007/s10723-013-9272-5 "ServiceSs: An interoperable programming framework for the cloud"
[Lowe 2021a]: https://doi.org/10.48546/workflowhub.workflow.194.1 "Protein MD Setup tutorial using BioExcel Building Blocks (biobb) in Galaxy"
[Lowe 2021b]: https://doi.org/10.48546/workflowhub.workflow.56.1 "Protein Ligand Complex MD Setup tutorial using BioExcel Building Blocks (biobb) (jupyter notebook)"
[Ludäscher 2016]: https://doi.org/10.1007/978-3-319-40226-0_7 "A Brief Tour Through Provenance in Scientific Workflows and Databases"
[Lughadha 2019]: https://doi.org/10.1111/cobi.13289 "Harnessing the potential of integrated systematics for conservation of taxonomically complex, megadiverse plant groups"
[Luo 2022]: https://www.proquest.com/docview/2763290077 "Knowledge enhanced digital objects"
[Luo 2023]: https://doi.org/10.1109/CCGridW59191.2023.00064 "Knowledge Enhanced Digital Objects: a Data Lake Approach"
[Lynch 2022]: https://www.npmjs.com/package/ro-crate-excel "npm: ro-crate-excel"
[Mai Chan 1995]: https://identifiers.org/isbn/9781563081910 "Library of Congress Subject Headings: Principles and Application"
[Manubens-Gil 2016]: https://doi.org/10.1109/HPCSim.2016.7568429 "Seamless management of ensemble climate prediction experiments on HPC platforms"
[Marinescu 2023]: https://identifiers.org/isbn/9780323852777 "Cloud Computing: Theory and Practice"
[Matentzoglu 2022]: https://doi.org/10.1093/database/baac087 "Ontology Development Kit: a toolkit for building, maintaining and standardizing biomedical ontologies"
[McMurry 2017]: https://doi.org/10.1371/journal.pbio.2001414 "Identifiers for the 21st century: How to design, provision, and reuse identifiers to maximize utility and impact of life science data"
[MDN 2023]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation "HTTP Content negotiation"
[de Mello 2022]: https://doi.org/10.1007/s12553-022-00639-w "Semantic interoperability in health records standards: a systematic literature review"
[Meroño-Peñuela 2021a]: https://doi.org/10.1007/978-3-031-01917-3_7 "Conclusion and future challenges"
[Meroño-Peñuela 2021b]: https://doi.org/10.1007/978-3-031-01917-3_3 "Web data APIs over SPARQL"
[Meurisse 2023]: https://s11.no/2023/phd/federated-causal-inference/ "Federated causal inference based on real-world observational data sources"
[Miksa 2019a]: https://doi.org/10.15497/rda00039 "RDA DMP Common Standard for Machine-Actionable Data Management Plans"
[Miksa 2019b]: https://doi.org/10.1371/journal.pcbi.1006750 "Ten principles for machine-actionable data management plans"
[Miksa 2020]: https://doi.org/10.4126/frl01-006423291 "Research Object Crates and Machine-actionable Data Management Plans"
[Millard 2010]: https://ceur-ws.org/Vol-665/MillardEtAl_COLD2010.pdf "Consuming multiple linked data sources: Challenges and Experiences"
[Miller 2021]: https://spec.openapis.org/oas/v3.1.0.html "OpenAPI Specification"
[Missier 2010]: https://doi.org/10.1109/WORKS.2010.5671861 "Linking multiple workflow provenance traces for interoperable collaborative science"
[Missier 2013]: https://doi.org/10.5555/2482949.2482961 "D-PROV: extending the PROV provenance model with workflow structure"
[Möller 2010]: https://doi.org/10.1186/1471-2105-11-S12-S5 "Community-driven computational biology with Debian Linux"
[Möller 2017]: https://doi.org/10.1007/s41019-017-0050-4 "Robust cross-platform workflows: How technical and scientific communities collaborate to develop, test and share best practices for data analysis"
[Mons 2017]: https://doi.org/10.3233/ISU-170824 "Cloudy, increasingly FAIR; revisiting the FAIR Data guiding principles for the European Open Science Cloud"
[Mons 2018]: https://identifiers.org/isbn/9781315351148 "Data Stewardship for Open Science"
[Moreau 2013]: https://www.w3.org/TR/2013/REC-prov-dm-20130430/ "PROV-DM: The PROV Data Model"
[myExperiment 2009]: https://web.archive.org/web/20091115080336/http%3a%2f%2frdf.myexperiment.org/ontologies "myExperiment Ontology Modules"
[Nature 2019]: https://doi.org/10.1038/s41592-019-0350-x "Giving software its due"
[NCBO]: https://bioportal.bioontology.org/ontologies "NCBO BioPortal"
[Nelson 2019a]: https://doi.org/10.1098/rstb.2017.0391 "The history and impact of digitization and digital data mobilization on biodiversity research"
[Nelson 2019b]: https://doi.org/10.3897/biss.3.37896 "DiSSCo, iDigBio and the Future of Global Collaboration"
[Neumann 2021]: https://doi.org/10.1109/TSC.2018.2847344 "An analysis of public REST web service apis"
[Newman 2009]: http://ceur-ws.org/Vol-523/Newman.pdf "myExperiment: An ontology for e-Research"
[Neylon 2017]: https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/ "As a researcher \ldots I'm a bit bloody fed up with Data Management"
[Nieva de la Hidalga 2021]: https://doi.org/10.1007/s00138-022-01276-z "Cross-validation of a semantic segmentation network for natural history collection specimens"
[Niewielska 2020]: https://doi.org/10.5281/zenodo.4916060 "BioExcel-2 Deliverable 2.5 - Provision of a Workflow Environment at BioExcel portal"
[Norris 2021]: https://doi.org/10.1186/s13326-021-00240-6 "Why and how to engage expert stakeholders in ontology development: Insights from social and behavioural sciences"
[Nottingham 2017]: https://doi.org/10.17487/rfc8288 "Web Linking"
[Nurdiati 2008]: https://purl.utwente.nl/publications/64931 "25 years development of knowledge graph theory: the results and the challenge"
[Ó Carragáin 2019a]: https://doi.org/10.5281/zenodo.3250687 "A lightweight approach to research object data packaging"
[Ó Carragáin 2019b]: https://s11.no/2019/phd/ro-crate/ "RO-Crate: A lightweight approach to research object data packaging"
[OCFL 2020]: https://ocfl.io/1.0/spec/ "OCFL, Oxford Common File Layout Specification"
[OCLC 2010]: http://info-uri.info/ "Info URI Registry (Frozen)"
[Ohta 2023]: https://doi.org/10.5281/zenodo.10134581 "Example of Workflow Run RO-Crate Output in Sapporo"
[Oliver 2019]: https://doi.org/10.1109/MCSE.2019.2906593 "Workflow Automation for Cycling Systems"
[Open Graph]: https://ogp.me/ "The Open Graph protocol"
[openDS 2021]: https://github.com/DiSSCo/openDS "Draft specification for open Digital Specimens (openDS)"
[OpenStand 2017]: https://open-stand.org/about-us/principles/ "The Modern Standards Paradigm"
[OSI 022]: https://opensource.org/licenses "Licenses & Standards"
[Owen 2020]: https://doi.org/10.3897/rio.6.e58030 "Towards a scientific workflow featuring Natural Language Processing for the digitisation of natural history collections"
[Page 2011]: https://doi.org/10.1145/1967428.1967435 "REST and Linked Data"
[Pantos 2017]: https://doi.org/10.17487/rfc8216 "HTTP Live Streaming"
[Parecki 2017]: https://www.w3.org/TR/2017/REC-micropub-20170523/ "Micropub"
[Pavel 2023]: https://doi.org/10.4126/frl01-006444984 "Ya2ro: A tool for creating Research Objects from minimum metadata"
[Pérez 2018]: https://doi.org/10.1007/s10115-018-1164-3 "A systematic review of provenance systems"
[Pergl 2019]: https://doi.org/10.5334/dsj-2019-059 "``Data Stewardship Wizard'': A Tool Bringing Together Researchers, Data Stewards, and Data Experts around Data Management Planning"
[Piper 2020]: https://doi.org/10.1080/14490854.2020.1796500 "Digital crowdsourcing and public understandings of the past: Citizen historians meet criminal characters"
[Poiata 2016]: https://doi.org/10.1093/gji/ggw071 "Multiband array detection and location of seismic sources recorded by dense seismic networks"
[Poiata 2023]: https://doi.org/10.5281/zenodo.7788030 "BackTrackBB: Multi-band array detection and location of seismic sources (PyCOMPSs implementation)"
[Polleres 2020]: https://doi.org/10.3233/SW-190380 "A more decentralized vision for linked data"
[Poveda 2010]: https://doi.org/10.1007/978-3-642-14264-2_10 "Common Pitfalls in Ontology Development"
[Price 2018]: https://doi.org/10.31219/osf.io/s2p73 "ALICE: Angled Label Image Capture and Extraction for high throughput insect specimen digitisation"
[Prlić 2012]: https://doi.org/10.1371/journal.pcbi.1002802 "Ten Simple Rules for the Open Development of Scientific Software"
[Pryer 2022]: https://doi.org/10.1002/aps3.11372 "Using computer vision on herbarium specimen images to discriminate among closely related horsetails (Equisetum)"
[RDF 1.1 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
[Rehm 2021]: https://doi.org/10.1016/j.xgen.2021.100029 "GA4GH: International policies and standards for data sharing across genomic research and healthcare"
[Reilly 2009]: https://www.dona.net/doipv1doc "Digital Object Interface Protocol Version 1.0"
[Reis 2022]: https://doi.org/10.1109/ACCESS.2021.3137671 "Developing Docker and Docker-Compose Specifications"
[Rescorla 2000]: https://doi.org/10.17487/rfc2818 "HTTP Over TLS"
[Rettberg 2015]: https://doi.org/10.5860/crln.76.6.9326 "OpenAIRE: Supporting a European open access mandate"
[Riccardi 2022]: https://doi.org/10.1002/jcc.26842 "Towards improved FAIRness of the ThermoML Archive"
[Rice 2022]: https://websockets.spec.whatwg.org/ "WebSockets Standard"
[RO-Crate 1.0]: https://doi.org/10.5281/zenodo.3541888 "RO-Crate Metadata Specification 1.0"
[RO-Crate 1.1]: https://w3id.org/ro/crate/1.1 "RO-Crate Metadata Specification 1.1"
[RO-Crate 1.1.3]: https://w3id.org/ro/crate/1.1 "RO-Crate Metadata Specification 1.1.3"
[RO-Crate 1.2]: https://www.researchobject.org/ro-crate/1.2-DRAFT/ "RO-Crate Metadata Specification 1.2.0"
[ro-crate-html-js]: https://www.npmjs.com/package/ro-crate-html-js "ro-crate-html-js"
[Robinson 2017]: https://doi.org/10.7490/f1000research.1114375.1 "CWL Viewer: The Common Workflow Language viewer"
[Robinson 2023]: https://github.com/common-workflow-language/cwlviewer "common-workflow-language/cwlviewer: v1.4.7"
[Rocca-Serra 2023]: https://doi.org/10.1038/s41597-023-02166-3 "The FAIR cookbook - the essential resource for and by FAIR doers"
[Saltz 2006]: https://doi.org/10.1093/bioinformatics/btl272 "caGrid: design and implementation of the core architecture of the cancer biomedical informatics grid"
[Samaniego 2010]: https://doi.org/10.1029/2008WR007327 "Multiscale parameter regionalization of a grid-based hydrologic model at the mesoscale"
[Samuel 2022]: https://doi.org/10.1186/s13326-021-00253-1 "End-to-End provenance representation for the understandability and reproducibility of scientific experiments using a semantic approach"
[Sandve 2013]: https://doi.org/10.1371/journal.pcbi.1003285 "Ten simple rules for reproducible computational research"
[Sandvine 2022]: https://www.sandvine.com/global-internet-phenomena-report-2022 "Global Internet Phenomena Report"
[Sauermann 2008]: http://www.w3.org/TR/cooluris/ "Cool URIs for the semantic web"
[Scheidegger 2008]: https://doi.org/10.1145/1376616.1376747 "Querying and re-using workflows with VsTrails"
[schema.org]: https://schema.org/ "Schema.org - Schema.org"
[schema actions]: https://schema.org/docs/actions.html "Schema.org Actions"
[Schreiber 2014]: http://www.w3.org/TR/2014/NOTE-rdf11-primer-20140624 "RDF 1.1 Primer"
[Schriml 2020]: https://doi.org/10.1038/s41597-020-0524-5 "COVID-19 pandemic reveals the peril of ignoring metadata standards"
[Schröder 2022]: https://doi.org/10.1186/s13326-021-00257-x "Structure-based knowledge acquisition from electronic lab notebooks for research data provenance documentation"
[Schultes 2019]: https://doi.org/10.23728/B2SHARE.166A074BFF614A31B05E9DF5BFD9809D "FAIR principles and digital objects: Accelerating convergence on a data infrastructure"
[Schultes 2020]: https://doi.org/10.1007/978-3-030-65847-2_13 "Reusable FAIR implementation profiles as accelerators of FAIR convergence"
[Schultes 2022]: https://doi.org/10.3389/data.2022.883341 "FAIR Digital Twins for Data-Intensive Research"
[Schwardmann 2022a]: https://doi.org/10.5281/zenodo.7824796 "DOIP endorsement request"
[Schwardmann 2022b]: https://doi.org/10.3897/rio.8.e96014 "Two Examples on How FDO Types can Support Machine and Human Readability"
[Scrocca 2021]: https://doi.org/10.4126/frl01-006429412 "The Survey Ontology: Packaging Survey Research as Research Objects"
[Sefton 2018]: https://doi.org/10.5281/zenodo.1445817 "DataCrate: a method of packaging, distributing, displaying and archiving Research Objects"
[Sefton 2021b]: https://github.com/UTS-eResearch/ro-crate-js "GitHub -- UTS-eResearch/ro-crate-js"
[Sefton 2021a]: http://ptsefton.com/2021/04/07/rdmpic/ "FAIR Data Management; It's a lifestyle not a lifecycle"
[Semmler 2022]: https://www.wdc-climate.de/ui/entry?acronym=C6CMAWAWMhi "IPCC DDC: AWI AWI-CM1.1MR model output prepared for CMIP6 CMIP historical"
[Singhal 2012]: https://blog.google/products/search/introducing-knowledge-graph-things-not/ "Introducing the knowledge graph: Things, not strings"
[Sirvent 2022]: https://hdl.handle.net/2117/384589 "Automatic, Efficient, and Scalable Provenance Registration for FAIR HPC Workflows"
[Smith 2007]: https://doi.org/10.1038/nbt1346 "The OBO Foundry"
[Smith 2016]: https://doi.org/10.7717/peerj-cs.86 "Software citation principles"
[Smith 2022]: https://aclanthology.org/2022.signlang-1.28 "Integrating Auslan Resources into the Language Data Commons of Australia"
[Snowley 2023]: https://www.hdruk.ac.uk/wp-content/uploads/2023/10/Integrating-Our-Community_v1-Oct-2023-compressed.pdf "Integrating Our Community"
[Soiland-Reyes 2014]: https://w3id.org/bundle/2014-11-05/ "Research Object Bundle 1.0"
[Soiland-Reyes 2016]: https://s11.no/2016/provweek-tavernaprov/ "Tracking Workflow Execution With TavernaPROV"
[Soiland-Reyes 2018]: https://doi.org/10.5281/zenodo.1471585 "common-workflow-language/cwlprov: CWLProv 0.6.0"
[Soiland-Reyes 2020a]: https://twitter.com/soilandreyes/status/1250721245622079488 "I am looking for which bioinformatics journals encourage authors to submit their code/pipeline/workflow supporting data analysis"
[Soiland-Reyes 2021]: https://doi.org/10.5281/zenodo.4633732 "Describing and packaging workflows using RO-Crate and BioCompute Objects"
[Soiland-Reyes 2022a]: https://s11.no/2022/phd/ro-crate/ "Packaging research artefacts with RO-Crate"
[Soiland-Reyes 2022b]: https://s11.no/2022/phd/canonical-workflow-building-blocks/ "Making Canonical Workflow Building Blocks interoperable across workflow languages"
[Soiland-Reyes 2022c]: https://s11.no/2022/phd/fdo-with-ro-crate/ "Creating lightweight FAIR digital objects with RO-Crate"
[Soiland-Reyes 2022d]: https://s11.no/2022/phd/updating-ld-for-fdo/ "Updating Linked Data practices for FAIR Digital Object principles"
[Soiland-Reyes 2022e]: https://doi.org/10.5281/zenodo.7256713 "stain/signposting: Signposting v0.9.0"
[Soiland-Reyes 2022f]: https://doi.org/10.5281/zenodo.7152762 "EuroScienceGateway: WP2 introduction"
[Soiland-Reyes 2022g]: https://w3id.org/ro/doi/10.5281/zenodo.5146227 "Packaging research artefacts with RO-Crate"
[Soiland-Reyes 2023a]: https://w3id.org/ro/doi/10.5281/zenodo.8075229 "Comparison tables for evaluating FAIR Digital Object and Linked Data"
[Soiland-Reyes 2023b]: https://doi.org/10.5281/zenodo.7774582 "Enabling FAIR Signposting and RO-Crate for content/metadata discovery and consumption"
[Soiland-Reyes 2023c]: https://s11.no/2023/phd/evaluating-fdo/ "Evaluating FAIR Digital Object and Linked Data as distributed object systems"
[Soiland-Reyes 2023d]: https://doi.org/10.5281/zenodo.7828632 "Building diverse FDO Collections using RO-Crate"
[Soiland-Reyes 2023e]: https://w3id.org/5s-crate/0.4 "Five Safes RO-Crate profile"
[Soiland-Reyes 2023f]: https://doi.org/10.5281/zenodo.10376350 "TRE-FX Technical Documentation - Five Safes RO-crate"
[Soiland-Reyes 2024]: https://doi.org/10.37044/osf.io/gmk2h "Enabling FAIR Digital Objects with RO-Crate, Signposting and Bioschemas"
[Speicher 2015]: http://www.w3.org/TR/2015/REC-ldp-20150226/ "Linked Data Platform 1.0"
[Sporny 2014]: https://www.w3.org/TR/2014/REC-json-ld-20140116/ "JSON-LD 1.0: A JSON-based Serialization for Linked Data"
[Sporny 2015]: https://www.w3.org/TR/2015/NOTE-rdfa-primer-20150317/ "RDFa 1.1 Primer"
[Sporny 2020]: https://www.w3.org/TR/2020/REC-json-ld11-20200716/ "JSON-LD 1.1: A JSON-based Serialization for Linked Data"
[Sporny 2023]: https://datatracker.ietf.org/doc/draft-ietf-mediaman-suffixes/03/ "Media Types with Multiple Suffixes"
 
[Stallings 1990]: https://identifiers.org/isbn/9780672226977 "Handbook of computer-communications standards: The open systems (OSI) model and OSI-related standards"
 
[Stanczyk 1987]: https://doi.org/10.21954/ou.ro.0000f821 "Process modelling for information system description"
[Stefi 2015a]: http://doi.org/10.1007/978-3-319-19593-3_18 "To develop or to reuse? Two perspectives on external reuse in software projects"
[Stefi 2015b]: https://doi.org/10.18151/7217489 "Do Developers Make Unbiased Decisions? - The Effect of Mindfulness and Not-Invented-Here Bias on the Adoption of Software Components"
[Stodden 2016]: https://doi.org/10.1126/science.aah6168 "Enhancing reproducibility for computational methods"
[Suetake 2022]: https://doi.org/10.12688/f1000research.122924.1 "Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics"
[Suetake 2023a]: https://doi.org/10.1093/gigascience/giad031 "A workflow reproducibility scale for automatic validation of biological interpretation results"
[Suetake 2023b]: https://doi.org/10.5281/zenodo.10134452 "sapporo-wes/sapporo-service"
[Sun 2003a]: https://doi.org/10.17487/rfc3650 "Handle System Overview"
[Sun 2003b]: https://doi.org/10.17487/rfc3652 "Handle System Protocol (ver 2.1) Specification"
[Sweeney 2018]: https://doi.org/10.12705/671.10 "Large-scale digitization of herbarium specimens: Development and usage of an automated, high-throughput conveyor system"
[Taschuk 2017]: https://doi.org/10.1371/journal.pcbi.1005412 "Ten simple rules for making research software more robust"
[Taivalsaari 2021]: https://doi.org/10.1007/978-3-030-74296-6_28 "Full Stack Is Not What It Used to Be"
[Tegelberg 2017]: https://doi.org/10.1109/eScience.2017.85 "Mass Digitization of Individual Pinned Insects Using Conveyor-Driven Imaging"
[Tejedor 2017]: https://doi.org/10.1177/1094342015594678 "PyCOMPSs: Parallel computational workflows in Python"
[Thieberger 2012]: https://hdl.handle.net/10125/4567 "Keeping records of language diversity in melanesia: The Pacific and regional archive for digital sources in endangered cultures (PARADISEC)"
[Thiers 2016]: https://doi.org/10.1007/s12228-016-9423-7 "Digitization of the New York Botanical Garden herbarium"
[Thompson 2012]: https://www.w3.org/TR/2012/REC-xmlschema11-1-20120405/ "W3C XML Schema Definition Language (XSD) 1.1 Part 1"
[Thompson 2020]: https://doi.org/10.1162/dint_a_00031 "Making FAIR Easy with FAIR Tools: From Creolization to Convergence"
[Thornton 2019]: https://doi.org/10.1007/978-3-030-21348-0_39 "Using shape expressions (ShEx) to share RDF data models and to guide curation with rigorous validation"
[Tirmizi 2011]: https://doi.org/10.1186/2041-1480-2-s1-s3 "Mapping between the OBO and OWL ontology languages"
[Tran 2014]: https://doi.org/10.1007/978-3-319-05458-2_27 "Linked Data Mashups: A Review on Technologies, Applications and Challenges"
[Trautwein 2022]: https://doi.org/10.48550/arXiv.2208.05877 "Design and Evaluation of IPFS: A Storage Layer for the Decentralized Web"
[Triki 2020]: https://doi.org/10.5220/0009170005230529 "Objects Detection from Digitized Herbarium Specimen based on Improved YOLO V3"
[Troncy 2010]: https://www.persistent-identifier.nl/urn:nbn:nl:ui:18-14511 "VAMP: A service for validating MPEG-7 descriptions w.r.t. to formal profile definitions"
[Tudorache 2020]: https://doi.org/10.3233/SW-190382 "Ontology engineering: Current state, challenges, and future directions"
[Tupelo-Scheck 2022]: https://www.rd-alliance.org/sites/default/files/Cordra.2022.pdf "Brief Introduction to Cordra & DOIP"
[Turcoane 2014]: https://doi.org/10.55630/dipp.2014.4.11 "Linked data, JSON-LD and the semantics of cultural and scientific heritage"
[Unger 2016]: https://doi.org/10.1186/s12862-016-0827-5 "Computer vision applied to herbarium specimens of German trees"
[Van de Sompel 2007]: http://icl.utk.edu/ctwatch/quarterly/articles/2007/08/interoperability-for-the-discovery-use-and-re-use-of-units-of-scholarly-communication/ "Interoperability for the discovery, use, and re-use of units of scholarly communication"
[Van de Sompel 2013]: https://doi.org/10.17487/rfc7089 "HTTP Framework for Time-Based Access to Resource States --Memento"
[Van de Sompel 2015]: https://doi.org/10.1045/november2015-vandesompel "Reminiscing About 15 Years of Interoperability Efforts"
[Van de Sompel 2022]: https://signposting.org/FAIR/ "FAIR Signposting Profile"
[Van de Sompel 2023]: https://doi.org/10.5281/zenodo.7977333 "FAIR Digital Objects and FAIR Signposting"
[Verborgh 2018]: https://ruben.verborgh.org/blog/2018/12/28/designing-a-linked-data-developer-experience/ "Designing a Linked Data developer experience"
[Verborgh 2020]: https://doi.org/10.3233/SW-190372 "The semantic web identity crisis: In search of the trivialities that never were"
[Verburg 2023]: https://doi.org/10.5281/zenodo.7848102 "FAIR-IMPACT project response to \"FAIR Assessment Tools: Towards an \"Apples to Apples\" Comparisons\""
[Vergoulis 2021]: https://doi.org/10.5281/zenodo.4671709 "Use of RO-Crates in SCHeMa"
[Vergoulis 2022]: https://doi.org/10.48550/arXiv.2103.13138 "SCHeMa: Scheduling Scientific Containers on a Cluster of Heterogeneous Machines"
[de Visser 2023]: https://doi.org/10.1371/journal.pcbi.1011369 "Ten quick tips for building FAIR workflows"
[Vivian 2017]: https://doi.org/10.1038/nbt.3772 "Toil enables reproducible, open source, big biomedical data analyses"
[Volk 2014]: https://doi.org/10.1007/s00267-014-0258-2 "Why is data sharing in collaborative natural resource efforts so hard and what can we do to improve it?"
[W3C 2007]: https://www.w3.org/2001/tag/doc/httpRange-14/2007-08-31/HttpRange-14.html "Dereferencing HTTP URIs"
[W3C 2012]: https://www.w3.org/TR/2012/REC-owl2-overview-20121211 "OWL 2 Web Ontology Language Document Overview"
[W3C 2013]: https://www.w3.org/TR/2013/REC-sparql11-overview-20130321/ "SPARQL 1.1 Overview"
[W3C 2015]: https://www.w3.org/standards/semanticweb/data "Linked Data"
[W3Techs 2023]: https://w3techs.com/technologies/details/da-jsonld "Usage Statistics of JSON-LD for Websites"
[Walton 2020a]: https://doi.org/10.3897/rio.6.e57602 "Landscape Analysis for the Specimen Data Refinery"
[Walton 2020b]: https://doi.org/10.3897/rio.6.e56211 "A cost analysis of transcription systems"
[Watanabe 2019]: https://doi.org/10.1093/biosci/biy163 "The Evolution of Natural History Collections: New research tools move specimens, data to center stage"
[WHATWG 2023]: https://html.spec.whatwg.org/multipage/microdata.html "Microdata"
[Weigel 2018]: https://doi.org/10.15497/rda00031 "RDA Recommendation on PID Kernel Information"
[Weigel 2022]: https://doi.org/10.5281/zenodo.7825693 "FDO -- kernel attributes & metadata"
[Weiland 2022a]: https://drive.google.com/file/d/1lPNBBROjEoZ6fTfrtdqcMa3Q2G27PoC_ "FAIR Digital Objects Forum Document Standards"
[Weiland 2022b]: https://doi.org/10.5281/zenodo.7825650 "FDO machine actionability"
[de Wit 2022]: https://doi.org/10.5281/zenodo.7113250 "A Non-Intimidating Approach to Workflow Reproducibility in Bioinformatics"
[de Wit 2023]: https://doi.org/10.5281/zenodo.10251812 "Analysis of runcrate"
[Wieczorek 2012]: https://doi.org/10.1371/journal.pone.0029715 "Darwin Core: An Evolving Community-Developed Biodiversity Data Standard"
[Wilde 2013]: https://doi.org/10.17487/rfc6906 "The 'profile' Link Relation Type"
[Wilde 2020]: https://doi.org/10.17487/rfc9264 "Linkset: Media Types and a Link Relation Type for Link Sets"
[Wilkinson 2016]: https://doi.org/10.1038/sdata.2016.18 "The FAIR Guiding Principles for scientific data management and stewardship"
[Wilkinson 2018]: https://doi.org/10.1038/sdata.2018.118 "A design framework and exemplar metrics for FAIRness"
[Wilkinson 2022a]: https://doi.org/10.5281/zenodo.7463421 "FAIR Assessment Tools: Towards an “Apples to Apples” Comparisons"
[Wilkinson 2022b]: https://doi.org/10.48550/arxiv.2209.09022 "F*** workflows: When parts of FAIR are missing"
[Wilkinson 2023a]: https://doi.org/10.12688/openreseurope.15364.2 "Community-driven governance of FAIRness assessment"
[Wilkinson 2024]: https://doi.org/10.5281/zenodo.10490289 "Report on FAIR Signposting and its uptake by the community"
[Williams 2012]: https://doi.org/10.1016/j.drudis.2012.05.016 "Open PHACTS: Semantic interoperability for drug discovery"
[Wittenburg 2019]: https://doi.org/10.23728/b2share.b605d85809ca45679b110719b6c6cb11 "Digital objects as drivers towards convergence in data infrastructures"
[Wittenburg 2021]: https://doi.org/10.1162/dint_a_00132 "Canonical Workflows to Make Data FAIR"
[Wittenburg 2022]: https://doi.org/10.5281/zenodo.5872645 "FAIR digital object demonstrators 2021"
[Wittenburg 2023a]: https://doi.org/10.52825/cordi.v1i.263 "FDOs to Enable Cross-Silo Work"
[Wittenburg 2023b]: https://doi.org/10.52825/cordi.v1i.374 "FDO to Structure the Domain of Knowledge"
[Wittner 2020]: https://s11.no/2021/phd/iso-23494-provenance/ "ISO 23494: Biotechnology - Provenance Information Model for Biological Specimen and Data"
[Wittner 2022]: https://doi.org/10.1038/s41597-022-01537-6 "Lightweight Distributed Provenance Model for Complex Real--world Environments"
[Wittner 2023a]: https://doi.org/10.1002/lrh2.10365 "Toward a common standard for data and specimen provenance in life sciences"
[Wittner 2023b]: https://s11.no/2023/phd/linking-provenance/ "Linking provenance and its metadata in multi-organizational environments of life sciences"
[Wittner 2023c]: https://doi.org/10.5281/zenodo.8095888 "Packing provenance using CPM RO-Crate profile"
[Wolstencroft 2011]: https://doi.org/10.1093/bioinformatics/btr312 "RightField: Embedding ontology annotation in spreadsheets"
[Wolstencroft 2013]: https://doi.org/10.1093/nar/gkt328 "The Taverna workflow suite"
[Wood 2014]: https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/ "RDF 1.1 Concepts and Abstract Syntax"
[Woolland 2022]: https://doi.org/10.3897/rio.8.e94349 "Incrementally building FAIR Digital Objects with Specimen Data Refinery workflows"
[WorkflowHub 2023]: https://w3id.org/workflowhub/ "WorkflowHub project: Project pages for developing and running the WorkflowHub, a registry of scientific workflows"
[Wright 2022]: https://datatracker.ietf.org/doc/draft-bhutton-json-schema/01/ "JSON schema: A media type for describing JSON documents"
[WRROC 2023a]: https://w3id.org/ro/wfrun/process/0.4 "Process Run Crate specification"
[WRROC 2023b]: https://w3id.org/ro/wfrun/workflow/0.4 "Workflow Run Crate specification"
[WRROC 2023c]: https://w3id.org/ro/wfrun/provenance/0.4 "Provenance Run Crate specification"
[Yoo 2003]: https://doi.org/10.1007/10968987_3 "SLURM: Simple Linux Utility for Resource Management"
[Yuen 2021]: https://doi.org/10.1093/nar/gkab346 "The Dockstore: enhancing a community platform for sharing reproducible and accessible computational protocols"
[Zarras 2004]: https://doi.org/10.5381/jot.2004.3.5.a2 "A Comparison Framework for Middleware Infrastructures"
[Zerouali 2023]: https://doi.org/10.1109/MSR59073.2023.00078 "Helm Charts for Kubernetes Applications: Evolution, Outdatedness and Security Risks"
[Zhao 2012]: https://research.manchester.ac.uk/en/publications/cba81ca4-e92c-408e-8442-383d1f15fcdf "Why workflows break -- understanding and combating decay in taverna workflows"
[Zoubek 2021]: https://github.com/e11938258/RO-Crates-and-Excel "RO Crates and Excel"
[Žumer 2009]: https://doi.org/10.1515/9783598441844 "National Bibliographies in the Digital Age: Guidance and New Directions"

