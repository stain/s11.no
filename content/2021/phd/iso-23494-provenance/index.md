---
title: "ISO 23494: Biotechnology – Provenance Information Model for Biological Specimen and Data"
categories:
  - Conferences
keywords:
  - provenance
  - biotechnology
  - standardization
authors:
  - name: Rudolf Wittner
    orcid: 0000-0002-0003-2024
  - name: Petr Holub
    orcid: 0000-0002-5358-616X
  - name: Heimo Müller
    orcid: 0000-0002-9691-4872
  - name: Joerg Geiger
    orcid: 0000-0002-7689-531X
  - name: Carole Goble
    orcid: 0000-0003-1219-2137
  - name: Stian Soiland-Reyes
    orcid: 0000-0001-9842-9718
  - name: Luca Pireddu
    orcid: 0000-0002-4663-5613
  - name: Francesca Frexia
    orcid: 0000-0003-1007-1286
  - name: Cecilia Mascia
    orcid: 0000-0002-8952-725X
  - name: Elliot Fairweather
    orcid: 0000-0003-0880-0785
  - name: Jason R. Swedlow
    orcid: 0000-0002-2198-1958
  - name: Josh Moore
    orcid: 0000-0003-4028-811X
  - name: Caterina Strambio
    orcid: 0000-0002-1069-1816
  - name: David Grunwald
    orcid: 0000-0001-9067-804X
  - name: Hiroki Nakae
    orcid: 0000-0002-5064-8468

summary: >
  Poster abstract accepted for Provenance Week 2020
description: >
  Exchange of research data and samples in biomedical research has become a common phenomenon demanding for their effective quality assessment. At the same time, several reports address reproducibility of research, where history of biological samples (acquisition, processing, transportation, storage, and retrieval) and data history (data generation and processing) defines their fitness for purpose, and hence their quality. The project aims at developing a comprehensive W3C PROV based provenance information standard intended for the biomedical research domain. The standard is being developed by the working group 5 ("data processing and integration") of the ISO (International Standardisation Organisation) technical committee 276 "biotechnology". The outcome of the project  will be published in parts as international standards or technical specifications. The poster informs about the  goals of the standardisation activity, presents the proposed structure of the standards, briefly describes its current state and outlines its future development and open issues.
---

<h2>Cite as</h2>

Rudolf Wittner, Petr Holub, Heimo Müller, Joerg Geiger, Carole Goble, Stian Soiland-Reyes, Luca Pireddu, Francesca Frexia, Cecilia Mascia, Elliot Fairweather, Jason R. Swedlow, Josh Moore, Caterina Strambio, David Grunwald, Hiroki Nakae (2021):  
**ISO 23494: Biotechnology – Provenance Information Model for Biological Specimen and Data**.  
In: Glavic B., Braganholo V., Koop D. (eds)
_Provenance and Annotation of Data and Processes_ (IPAW 2020/2021).  
_Lecture Notes in Computer Science_ **12839**.  
<https://doi.org/10.1007/978-3-030-80960-7_16>


# ISO 23494: Biotechnology -- Provenance Information Model for Biological Specimen and Data

_[Rudolf Wittner](https://orcid.org/0000-0002-0003-2024)<sup>1,2</sup>, 
[Petr Holub](https://orcid.org/0000-0002-5358-616X)<sup>1,2</sup>, 
[Heimo Müller](https://orcid.org/0000-0002-9691-4872)<sup>3</sup>, 
[Joerg Geiger](https://orcid.org/0000-0002-7689-531X)<sup>4</sup>, 
[Carole Goble](https://orcid.org/0000-0003-1219-2137)<sup>5</sup>, 
[Stian Soiland-Reyes](https://orcid.org/0000-0001-9842-9718)<sup>5,11</sup>, 
[Luca Pireddu](https://orcid.org/0000-0002-4663-5613)<sup>6</sup>, 
[Francesca Frexia](https://orcid.org/0000-0003-1007-1286)<sup>6</sup>, 
[Cecilia Mascia](https://orcid.org/0000-0002-8952-725X)<sup>6</sup>, 
[Elliot Fairweather](https://orcid.org/0000-0003-0880-0785)<sup>7</sup>, 
[Jason R. Swedlow](https://orcid.org/0000-0002-2198-1958)<sup>8</sup>, 
[Josh Moore](https://orcid.org/0000-0003-4028-811X)<sup>8</sup>, 
[Caterina Strambio](https://orcid.org/0000-0002-1069-1816)<sup>9</sup>, 
[David Grunwald](https://orcid.org/0000-0001-9067-804X)<sup>9</sup>, 
[Hiroki Nakae](https://orcid.org/0000-0002-5064-8468)<sup>10</sup>_

<div class="affiliations">

<sup>1</sup> BBMRI-ERIC, AUT  
<sup>2</sup> Institute of Computer Science & Faculty of Informatics, Masaryk University, CZ  
<sup>3</sup> Medical University Graz, AUT  
<sup>4</sup> Interdisciplinary Bank of Biomaterials and Data Würzburg (ibdw), Würzburg, DE  
<sup>5</sup> Department of Computer Science, The University of Manchester, UK  
<sup>6</sup> CRS4 -- Center for Advanced Studies, Research and Development in Sardinia, IT  
<sup>7</sup> King's College London, UK  
<sup>8</sup> School of Life Sciences, University of Dundee, Dundee, UK  
<sup>9</sup> University of Massachusetts, US  
<sup>10</sup> Japan bio- Measurement and Analysis Consortium, JPN  
<sup>11</sup> Informatics Institute, University of Amsterdam, NL

</div>

* **Is based on**: <https://doi.org/10.5281/zenodo.5004842>
* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)).
* **Modifications**: Formatting as Markdown from preprint; references in s11 house style; figure 1 re-created in SVG, figure 2 converted to SVG; additional paragraph breaks for readability; added footnote for mentioned preprint; re-added funding acknowledgement w/ DOI & hyperlinks.


## Introduction

Research in life sciences has undergone significant changes during
recent years, evolving away from individual projects confined to small
research groups to transnational consortia covering a wide range of
techniques and expertise. At the same time, several reports addressing
the quality of research papers in life sciences have uncovered an
alarming number of ill-founded claims. 

The reasons for the deficiencies
are diverse, with insufficient quality and documentation of the
biological material used being the major issue [[1]] [[2]] [[3]]. 
Hence there is urgent need for standardized and comprehensive documentation of the
whole workflow from the collection, generation, processing and analysis
of the biological material to data analysis and integration.

The PROV [[4]] family of documents serves as a current standard for
provenance information used to describe the history of an object. On the
other hand, as discussed in the results from EHR4CR and TRANSFoRm
projects [[5]] [[6]], its implementation for the biotechnology domain and
the field of biomedical research in particular is still a pending issue.

To address this, the International Standardisation Organisation (ISO)
initiated the development of a *Provenance Information Model for
Biological Specimen and Data* standard defining the requirements for
interoperable, machine-actionable documentation intended to describe the
complete process chain from the source of biological material through
its processing, analysis, and all steps of data generation and data
processing to final data analysis.

The standard is intended for implementers and suppliers of HW/SW tools
used in biomedical research (e.g. lab automation devices or analytical
devices used for research purposes) and also for organisations adopting
generated provenance (e.g. to require or use standardised tools).

## Goals of the Standard and Its Structure

The main goals of the standard are to

- enable effective assessment of quality and fitness for purpose of the
objects provided, such as biological material and data;
- support reproducible research by exacting the capture of all relevant
information;
- track error propagation within scientific results;
- track the source of biological material in order to prevent fabrication
of data and enabling notification of subjects in case of relevant
incidental findings;
- propagate withdrawal of or changes to an informed consent along the
process chain.

The proposed structure of the standard reflects the intention to
interconnect and integrate distributed provenance information furnished
by all kinds of organisations involved in biotechnology research.
Examples of such organisations are hospitals, biobanks, research
centers, universities, data centers or pharmaceutical companies, where
each of them is participating in research, thus generating provenance
information describing particular activities or contributions. In its
current the standard is composed of the following 6 parts:

**Part 1**
: stipulates common requirements for provenance information
  management in biotechnology to effectuate compatibility of
  provenance management at all stages of research and defines the
  design concept of this standard

**Part 2**
: defines a common provenance model which will serve as an
  overarching principle interconnecting provenance parts generated by
  all kinds of contributing organisations and enable access to
  provenance information in a distributed environment

**Part 3, 4 and 5**
: are meant to complement the *horizontal*
  standards (1) and (2) as *vertical* standards defining domain
  specific provenance models describing diverse stages or areas of
  research in biotechnology (e.g. sample acquisition and handling,
  analytical techniques, data management, cleansing and processing;
  database validation)

**Part 6**
: will contain optional data security extensions especially
  to address non-repudiation of provenance

The proposed structure is also depicted in [Figure 1](#figure1). Parts
indicated by red boxes are considered as *horizontal* standards, i.e.
providing a common basis for provenance information at all stages of
research. The blue boxes indicate domain specific *vertical* standards
build on top of the *horizontal* standards.

{{< figure src="figure1.svg" link="figure1.svg" id="figure1"
width="100%" title="Overall structure of the standard"
caption="" >}}


## Current Status and Future Development

The standard is currently at an early stage of development. The PROV
model has been already used to define new types of provenance
structures, called *connectors*, that are used to interconnect
provenance generated by different organizations. The concept of the
connectors and a common mechanism for bundles versioning has been
published as an EOSC-Life project provenance deliverable [[7]].
A publication describing use of the connectors at a specific use case
is under development at the moment and its pre-print will be published
in summer 2021[^2]. 

Continuously, the model will be enriched by new types of
structures (e.g. relations, entities, etc.) to capture common objects.
These structures will be subsequently used to design provenance
templates [^1] to define a common representation of usual scenarios in
life sciences. 

Further aspects will be also targeted. The major focus
areas are: opaque provenance components; privacy preservation and
non-repudiation of provenance information; full syntactic and semantic
interoperability of provenance information captured; rigorous formal
verification process of provenance instance validity (provable
compliance with the proposed model).

[^1]: The templates can be considered as synonyms for named graphs or
    graph patterns. These concepts are used to abstract from actual
    instances of provenance and to describe repeating occurrences of
    components of provenance

[^2]: See [Toward a common standard for data and specimen provenance in life sciences](https://doi.org/10.1002/lrh2.10365) and [Linking provenance and its metadata in multi-organizational environments of life sciences](https://s11.no/2023/phd/linking-provenance/); s11 ed. 2023-09-19

Another publication describing the standardization process in a more
detailed way is under development. The publication will contain more
detailed explanation of our motivation and the standardization activity
itself, more detailed description of the standard structure, and
finally, an important discussion on openness of the standard and related
issues.


{{< figure src="ISO23494.svg" link="ISO23494.svg" id="figure2"
width="100%" title="ISO 23494 Poster"
caption="Presented at Provenance Week 2021" >}}

## Acknowledgements

Supported by European Union’s Horizon 2020 research and innovation programme under grant agreement No. [654248](https://doi.org/10.3030/654248), project [CORBEL](https://www.corbel-project.eu/); grant agreement No. [824087]((https://doi.org/10.3030/824087)), project [EOSC-Life](https://www.eosc-life.eu/); and grant agreement No. [823830]((https://doi.org/10.3030/823830)), project [BioExcel-2](https://bioexcel.eu/).


## References

[1]: https://doi.org/10.1371/journal.pbio.1002165 "The economics of reproducibility in preclinical research"
\[1\] Leonard P. Freedman, Iain M. Cockburn, Timothy S. Simcoe (2015):  
**The economics of reproducibility in preclinical research**.  
*PLOS Biology* **13**(6):e1002165  
<https://doi.org/10.1371/journal.pbio.1002165>

[2]: https://doi.org/10.1161/CIRCRESAHA.114.303819 "Reproducibility in science"
\[2\] C. Glenn Begley, John P. A. Ioannidis (2015):  
**Reproducibility in science**: Improving the Standard for Basic and Preclinical Research.  
*Circulation Research* **116**  
<https://doi.org/10.1161/CIRCRESAHA.114.303819>

[3]: https://doi.org/10.1158/0008-5472.CAN-14-0925 "The increasing urgency for standards in basic biologic research"
\[3\] Leonard P. Freedman, James Inglese (2014):  
**The increasing urgency for standards in basic biologic research**.  
*Cancer Research* **74**(15)  
<https://doi.org/10.1158/0008-5472.CAN-14-0925>

[4]: https://www.w3.org/TR/2013/NOTE-prov-overview-20130430/ "PROV-overview**. An overview of the prov family of documents"
\[4\] Paul Groth, Luc Moreau (2013):  
**PROV-overview**. An overview of the PROV family of documents.  
_W3C Working Group Note_ 2013-04-30  
<https://www.w3.org/TR/2013/NOTE-prov-overview-20130430/>

[5]: https://doi.org/10.1016/j.future.2013.12.001 "Implementing interoperable provenance in biomedical research"
\[5\] Vasa Curcin, Simon Miles, R. Danger, Y. Chen, Richard Bache, Adel Taweel (2014):  
**Implementing interoperable provenance in biomedical research**.  
*Future Generation Computer Systems* **34**  
<https://doi.org/10.1016/j.future.2013.12.001>

[6]: https://doi.org/10.1109/HPCSim.2014.6903742 "An automated infrastructure to support high-throughput bioinformatics"
\[6\] Gianmauro Cuccuru, Simone Leo, Luca Lianas, Michele Muggiri, Andrea Pinna, Luca Pireddu, Paolo Uva, Alessio Angius, Giorgio Fotia, Gianluigi Zanetti (2014):  
**An automated infrastructure to support high-throughput bioinformatics**.  
*2014 international conference on High performance computing & simulation* (HPCS)   
<https://doi.org/10.1109/HPCSim.2014.6903742>

[7]: https://doi.org/10.5281/zenodo.4705074 "EOSC-life common provenance model"
\[7\] Rudolf Wittner, Cecilia Mascia, Francesca Frexia, Heimo Müller, Jörg Geiger, Katrina Exter, Petr Holub (2021):  
**EOSC-life common provenance model**.  
*Zenodo*  
<https://doi.org/10.5281/zenodo.4705074>

