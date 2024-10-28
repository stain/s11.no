---
title: "RO-Crate, a lightweight approach to Research Object data packaging"
lang: en-GB
date-meta: '2019-07-16'
categories:
 - Conference
summary: > 
  Conference abstract presented at _Workshop on Research Objects 2019 (RO2019)_
description: > 
    A Research Object (RO) provides a machine-readable mechanism to communicate the diverse set of digital and real-world resources that contribute to an item of research. The aim of an RO is to replace traditional academic publications of static PDFs, to rather provide a complete and structured archive of the items (such as people, organisations, funding, equipment, software etc) that contributed to the research outcome, including their identifiers, provenance, relations and annotations.

    This is increasingly important as researchers now rely heavily on computational analysis, yet we are facing a reproducibility crisis as key components are often not sufficiently tracked, archived or reported.

    We are developing Research Object Crate (or RO-Crate for short), a lightweight approach to package research data with their structured metadata, based on schema.org annotations in a formalized JSON-LD format that can be used independent of infrastructure to encourage FAIR sharing of reproducible datasets and analytical methods.
authors:
  - name: Eoghan Ó Carragáin
    orcid: https://orcid.org/0000-0001-8131-2150
  - name: Peter Sefton
    orcid: https://orcid.org/0000-0002-3545-944X
  - name: Carole Goble
    orcid: https://orcid.org/0000-0003-1219-2137
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
---


<h2>Cite as</h2>

Eoghan Ó Carragáin, Carole Goble, Peter Sefton, Stian Soiland-Reyes (2019):  
**RO-Crate: A lightweight approach to research object data packaging**.  
RO-15 at _Workshop on Research Objects_ ([RO 2019](http://www.researchobject.org/ro2019/proceedings)), IEEE eScience 2019, 2019-09-24, San Diego, CA, USA.  
<https://doi.org/10.5281/zenodo.3337883>


# RO-Crate, a lightweight approach to Research Object data packaging

_Eoghan Ó Carragáin¹, Carole Goble², Peter Sefton³, Stian Soiland-Reyes²⁴_

<div class="affiliations">

¹ University College Cork, Ireland  
² The University of Manchester, UK  
³ University of Technology Sydney, Australia  
⁴ University of Amsterdam, Amsterdam, Netherlands  

</div>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown; reference in s11 house style; reference author lists completed; Gigascience citation updated. 

## Abstract


A **Research Object** (RO) provides a machine-readable mechanism to communicate the diverse set of digital and real-world resources that contribute to an item of research. The aim of an RO is to replace traditional academic publications of static PDFs, to rather provide a complete and structured archive of the items (such as people, organisations, funding, equipment, software etc) that contributed to the research outcome, including their identifiers, provenance, relations and annotations. This is increasingly important as researchers now rely heavily on computational analysis, yet we are facing a _reproducibility crisis_ [[1]] as key components are often not sufficiently tracked, archived or reported.

We are developing _Research Object Crate_ (or **RO-Crate** for short), a lightweight approach to package research data with their structured metadata, based on schema.org annotations in a formalized JSON-LD format that can be used independent of infrastructure to encourage FAIR sharing of reproducible datasets and analytical methods.


## Background

Earlier work introduced the notion of _Research Objects_ [[2]]. Their formalization combines existing _Linked Data_ standards: W3C RDF, JSON-LD, OAI-ORE, W3C Web Annotations, PROV, Dublin Core Terms, ORCID. The [RO ontologies](https://w3id.org/ro/2016-01-28/) [[3]] combined these to describe ROs, but do not themselves formalize how ROs are saved or transmitted. Multiple formats have since been realized: the portal [RO Hub](http://www.rohub.org/) [[4]] use RDF REST resources; while workflow provenance make [RO Bundle](https://w3id.org/bundle/) ZIP files [[5]] or Big Data [BagIt](https://tools.ietf.org/html/rfc8493) archives (_BDBag_) [[6]] [[7]]. Each of these require RO support in the packaging infrastructure.

Multiple _data packaging_ initiatives have recently emerged, within [Research Data Alliance](https://rd-alliance.org/), [Force11](https://www.force11.org/),  [DataOne](https://www.dataone.org/) and elsewhere; like [Frictionless data](https://frictionlessdata.io/specs/) [[8]] for table-like files, [BioCompute Objects](https://github.com/biocompute-objects/BCO_Specification) for regulatory science [[9]], [CodeMeta](https://codemeta.github.io/) for software, [Psych-DS](https://psych-ds.github.io/) for psychology studies, and [DataCrate](https://github.com/UTS-eResearch/datacrate) [[10]] for datasets. RDA has surveyed a large variety of [data packaging formats](https://docs.google.com/document/d/155lA2BcixTl-zwJHGfLkxsmg7WmQbBK00QWyP8QggkE/edit?usp=sharing) across different domains. 

Common among these is _structured metadata_, e.g. with a single JSON file that refer to neighbouring data files and scripts maintained and published together, e.g. in GitHub. Many of these initiatives use [schema.org](https://schema.org/) [[11]] as basis for common metadata. With [JSON-LD](https://json-ld.org/) this offers a developer-friendly experience and interoperability with web conventions outside of the research domain.


## Data packaging principles

At an [RDA meeting on data packaging](https://rd-alliance.org/approaches-research-data-packaging-rda-11th-plenary-bof-meeting) we concluded that many initiatives arrive at similar principles: simple folder structure; JSON-LD manifest; schema.org for core metadata; BagIt for fixity; OAI-ORE for aggregation. This points to: a) appetite for general package/folder-oriented approach in different contexts; b) a generic solution won’t work for all and needs to be domain-extensible; c) a tendency to re-invent the wheel, leading to sub-optimal interoperability and duplication of effort.

We have identified a gap for a solid base format for data packaging that also allow communities to build domain-specific solutions. [Frictionless data](https://frictionlessdata.io/specs/) [[8]] could arguably fill this gap, with mature specifications and a strong design philosophy, however as an independent JSON format it does not fully apply Linked Data principles, and would be harder to use in FAIR integrations and extensions.

Our proposal is to build on [DataCrate](https://github.com/UTS-eResearch/datacrate) [[10]] to evolve **[RO-Crate](http://www.researchobject.org/ro-crate/)**, based around these principles: a) metadata as Linked Data, using schema.org as much as possible; b) extensible for different domains; c) retain the core [Research Object principles](http://www.researchobject.org/overview/) _Identity, Aggregation, Annotation_; d) inferred metadata rather than repetition; e) “just-enough” provenance; f) layered validation; g) archivable with BagIt; h) hooks to reuse existing domain formats; i) lightweight programmatic generation and consumption. 

Similar to the approach of [BioSchemas](https://bioschemas.org/), rather than building new specifications from scratch, we aim to build best-practice guides and validatable profiles for building rich research data packages with existing standards, without requiring expert knowledge for developing producers and consumers.


## Challenges

In the desire to make a lightweight approach that is also generally applicable we have focused primarily on RO-Crate as a way to capture and describe a [dataset](http://schema.org/Dataset) of neighbouring files, for instance maintained in a GitHub repository, while also describing external resources and provenance. 

A goal of RO-Crate is to simplify the creation and maintenance of metadata, supporting both a manual or programmatic manner, with a set of opinionated profiles for describing common resource types such as tables, organizations, equipment, software, workflows, places. One design challenge is the pressure between explicit and implicit. For instance, should the creator be repeated for every file they also made, or can the creator of the research object be a reasonable default? Do all files in a directory need to be listed in the RO-Crate metadata, or is it sufficient to describe the directory or a filename glob pattern? 

Recognising this challenge, our vision is a separation of concern between _packaging_ and _description_. By letting `ro-crate-metadata.jsonld` be used in any file-or web-based approach at a root directory, we can rely on [BDBag](https://github.com/fair-research/bdbag) [[7]] when the RO-Crate needs to be shipped, archived or deposited. At this point the Research Object would be “completed” to generate a full “classical” Research Object manifest, integrating the BagIt checksums and file list with metadata implied from the RO-Crate metadata. We are developing this tooling for this completion step, which should also perform _validation_ against the declared profile, might include snapshotting remote resources and minting of RO identifiers using [MinId](http://minid.bd2k.org/) [[7]]. Although an RO-Crate is in a sense a recipe for making full Research Objects, RO-Crate metadata can also be consumed “as-is” as JSON-LD if discovered in the wild, or updated programmatically based on the profile and other schema.org markup.


## Building community consensus

RO-Crate is a fresh initiative, bringing together data archive and repository maintainers with existing Research Object, workflow and provenance communities.  Starting as a small cross-domain group, organically formed to build the core principles and first sketches of their use, we are now expanding to collect use cases and reaching out to other packaging initiatives to build common ground.

One emerging use of RO-Crate is for capturing workflows and tools in a federated _workflow repository_ being built in [EOSC-Life](http://www.eosc-life.eu/), a large European Open Science Cloud project across 13 research infrastructures in the life science domain. However RO-Crate is also aiming to be usable by individual scientists with no particular infrastructure beyond [Jupyter notebook](https://jupyter.org/), who may not have the time or motivation to use a cascade of metadata vocabularies and research data management tools [[12]].

RO-Crate development and discussion is done openly in a [GitHub repository](https://github.com/ResearchObject/ro-crate) by volunteers, with monthly telcons to synchronize the effort. Anyone can [join](https://github.com/ResearchObject/ro-crate/issues/1) to help form the RO-Crate approach.


## References

[1]: https://doi.org/10.1038/533452a
\[1\] Monya Baker (2016):  
**1,500 scientists lift the lid on reproducibility**.  
_Nature **533**(7604)_  
<https://doi.org/10.1038/533452a>

[2]: https://research.manchester.ac.uk/en/publications/why-linked-data-is-not-enough-for-scientists-2
\[2\] Sean Bechhofer, Iain Buchan, David De Roure, Paolo Missier, John Ainsworth, Jiten Bhagat, Philip Couch, Don Cruickshank, Mark Delderfield, Ian Dunlop, Matthew Gamble, Danius Michaelides, Stuart Owen, David Newman, Shoaib Sufi, Carole Goble (2013):  
**Why Linked Data is Not Enough for Scientists**.  
_Future Generation Computer Systems_ **29**(2)  
<https://doi.org/10.1016/j.future.2011.08.004> [[preprint](https://research.manchester.ac.uk/en/publications/why-linked-data-is-not-enough-for-scientists-2)]

[3]: https://doi.org/10.1016/j.websem.2015.01.003
\[3\] Khalid Belhajjame, Jun Zhao, Daniel Garijo, Matthew Gamble, Kristina Hettne, Raul Palma, Eleni Mina, Oscar Corcho, José Manuel Gómez-Pérez, Sean Bechhofer, Graham Klyne, Carole Goble (2015):  
**Using a suite of ontologies for preserving workflow-centric research objects**.  
_Journal of Web Semantics_ **32**  
<https://doi.org/10.1016/j.websem.2015.01.003>

[4]: http://sandbox.rohub.org/rodl/ROs/experiences-escience-2017/preprint.pdf
\[4\]	Jose Manuel Gomez-Perez, Raul Palma, Andres Garcia-Silva (2017):  
**Towards a Human-Machine Scientific Partnership Based on Semantically Rich Research Objects**.  
_IEEE 13th International Conference on e-Science_ ([e-Science 2017](http://escience2017.org.nz/programme/)).  
<https://doi.org/10.1109/eScience.2017.40> [[preprint](http://sandbox.rohub.org/rodl/ROs/experiences-escience-2017/preprint.pdf)]

[5]: /2016/provweek-tavernaprov/
\[5\]	Stian Soiland-Reyes, Pinar Alper, Carole Goble (2016):  
[**Tracking workflow execution with TavernaProv**](/2016/provweek-tavernaprov/).  
_ProvenanceWeek 2016; PROV: Three Years Later._  6 Jun 2016, Washington DC, US.  
<https://doi.org/10.5281/zenodo.51314>

[6]: https://doi.org/10.1371/journal.pone.0213013
\[6\]	Ravi Madduri, Kyle Chard, Mike D’Arcy, Segun C. Jung, Alexis Rodriguez, Dinanath Sulakhe, Eric Deutsch, Cory Funk, Ben Heavner, Matthew Richards, Paul Shannon, Gustavo Glusman, Nathan Price, Carl Kesselman, Ian Foster (2019):  
**Reproducible big data science: A case study in continuous FAIRness**.  
_PLoS ONE_ **14**(4)  
<https://doi.org/10.1371/journal.pone.0213013>

[7]: https://doi.org/10.1093/gigascience/giz095
\[7\]	Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):   
**Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv**.  
*GigaScience* **8**(11)  
<https://doi.org/10.1093/gigascience/giz095>

[8]: https://doi.org/10.5281/zenodo.1301152
\[8\] Jo Barratt, Serah Rono (2018):  
**Frictionless Data and Data Packages**.  
_Workshop on Research Objects ([RO 2018](https://www.researchobject.org/ro2018/ro2018-proceedings/))_, 29 Oct 2018, Amsterdam, Netherlands.  
<https://doi.org/10.5281/zenodo.1301152>

[9]: https://doi.org/10.1371/journal.pbio.3000099
\[9\] Gil Alterovitz, Dennis A Dean II, Carole Goble, Michael R Crusoe, Stian
Soiland-Reyes, Amanda Bell, Anais Hayes, Anita Suresh, Charles Hadley S
King IV, Dan Taylor, KanakaDurga Addepalli, Elaine Johanson, Elaine E
Thompson, Eric Donaldson, Hiroki Morizono, Hsinyi Tsang, Jeet K Vora,
Jeremy Goecks, Jianchao Yao, Jonas S Almeida, Jonathon Keeney,
KanakaDurga Addepalli, Konstantinos Krampis, Krista Smith, Lydia Guo,
Mark Walderhaug, Marco Schito, Matthew Ezewudo, Nuria Guimera, Paul
Walsh, Robel Kahsay, Srikanth Gottipati, Timothy C Rodwell, Toby Bloom,
Yuching Lai, Vahan Simonyan, Raja Mazumder (2018):  
**Enabling precision medicine via standard communication of HTS provenance, analysis, and results**.  
*PLOS Biology* **16**(12):e3000099  
<https://doi.org/10.1371/journal.pbio.3000099>

[10]: https://doi.org/10.5281/zenodo.1445817
\[10\] Peter Sefton, Gerard Devine, Christian Evenhuis, Michael Lynch, Sharyn Wise, Michael Lake, Duncan Loxton (2018):  
**[DataCrate: a method of packaging, distributing, displaying and archiving Research Objects](https://data.research.uts.edu.au/examples/v1.0/datacrate-RO-2018/data/paper.html)**.  
_Workshop on Research Objects ([RO 2018](https://www.researchobject.org/ro2018/ro2018-proceedings/))_, 29 Oct 2018, Amsterdam, Netherlands.  
<https://doi.org/10.5281/zenodo.1445817>

[11]: https://doi.org/10.1145/2844544
\[11\] R. V. Guha, Dan Brickley, Steve Macbeth (2016):  
**Schema.org: evolution of structured data on the web**.  
_Communications of the ACM_ **59** (2)  
<https://doi.org/10.1145/2844544>

[12]: http://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/
\[12\] Cameron Neylon (2017):  
[**As a researcher…I’m a bit bloody fed up with Data Management**](http://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management).  
_Science in the Open_  (blog)  
<http://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/> [[archived](http://web.archive.org/web/20190412013849/http://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/) 2019-04-12]


_An earlier version of this abstract was accepted for BOSC 2019, see <https://doi.org/10.5281/zenodo.3250687>._
