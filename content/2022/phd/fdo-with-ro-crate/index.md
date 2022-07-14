---
title: "Chapter 4: Creating lightweight FAIR Digital Objects with RO-Crate"
weight: 40
lang: en-GB
categories:
  - PhD
date-meta: '2022-07-10'
summary: >
  Poster abstract submitted to FAIR Digital Objects conference (FDO2022)
description: >
  RO-Crate is a lightweight method to package research outputs along with their metadata, based on Linked Data principles and W3C standards. RO-Crate provides a flexible mechanism for researchers archiving and publishing rich data packages (or any other research outcome) by capturing their dependencies and context. However, additional measures should be taken to ensure that a crate is also following the FAIR principles, including consistent use of persistent identifiers, provenance, community standards, clear machine/human-readable licensing for metadata and data, and Web publication of RO-Crates.

  The FAIR Digital Object (FDO) approach gives a set of recommendations that aims to improve findability, accessibility, interoperability and reproducibility for any digital object, allowing implementation through different protocols or standards.
  
  Here we present how we have followed the FDO recommendations and turned research outcomes into FDOs by publishing RO-Crates on the Web using HTTP, following best practices for Linked Data. We highlight challenges and advantages of the FDO approach, and reflect on what is required for an FDO profile to achieve FAIR RO-Crates.
---

<h2>Cite as</h2>

Stian Soiland-Reyes, Peter Sefton, Leyla Jael Castro, Frederik Coppens, Daniel Garijo, Simone Leo, Marc Portier, Paul Groth (2022):  
**Creating lightweight FAIR Digital Objects with RO-Crate**.  
_Research Ideas and Outcomes_, [1st International Conference on FAIR Digital Objects](https://www.fdo2022.org/) (submitted)


# Creating lightweight FAIR Digital Objects with RO-Crate

_Stian Soiland-Reyes¹², Peter Sefton³, Leyla Jael Castro⁴, Frederik Coppens⁵, Daniel Garijo⁶, Simone Leo⁷, Marc Portier⁸, Paul Groth²_

<div class="affiliations">

¹ The University of Manchester, Manchester, United Kingdom  
² Informatics Institute, Faculty of Science, University of Amsterdam, Amsterdam, Netherlands  
³ The University of Queensland School of Languages and Cultures, The University of Queensland, Brisbane, Queensland, Australia  
⁴ ZB Med, Cologne, Germany  
⁵ VIB-UGent Center for Plant Systems Biology, Ghent, Belgium  
⁶ Ontology Engineering Group, Universidad Politécnica de Madrid, Madrid, Spain  
⁷ Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Pula (CA), Italy
⁸ Vlaams Instituut voor de Zee (VLIZ), Oostende, Belgium  

</div>

## Abstract

RO-Crate [[Soiland-Reyes 2022](https://doi.org/10.3233/DS-210053)] is a lightweight method to package research outputs along with their metadata, based on Linked Data principles [[Bizer 2009](https://doi.org/10.4018/jswis.2009081901)] and W3C standards. RO-Crate provides a flexible mechanism for researchers archiving and publishing rich data packages (or any other research outcome) by capturing their dependencies and context. 

However, additional measures should be taken to ensure that a crate is also following the FAIR principles [[Wilkinson 2016](https://doi.org/10.1038/sdata.2016.18)], including consistent use of persistent identifiers, provenance, community standards, clear machine/human-readable licensing for metadata and data, and Web publication of RO-Crates.

The FAIR Digital Object (FDO) approach [[De Smedt 2020](https://doi.org/10.3390/publications8020021)] gives a set of recommendations that aims to improve findability, accessibility, interoperability and reproducibility for any digital object, allowing implementation through different protocols or standards.

Here we present how we have followed the FDO recommendations and turned research outcomes into FDOs by publishing RO-Crates on the Web using HTTP, following best practices for Linked Data. We highlight challenges and advantages of the FDO approach, and reflect on what is required for an FDO profile to achieve FAIR RO-Crates.

The implementation allows for a broad range of use cases, across scientific domains. A minimal RO-Crate may be represented as a persistent URI resolving to a summary website describing the outputs in a scientific investigation (e.g. <https://w3id.org/dgarijo/ro/sepln2022> with links to the used datasets along with software). 

One of the advantages of RO-Crates is flexibility, particularly regarding the metadata accompanying the actual research outcome. RO-Crate extends [schema.org](https://schema.org/), a popular vocabulary for describing resources on the Web [[Guha 2016](https://doi.org/10.1145/2844544)]. A generic RO-Crate is not required to be typed beyond `Dataset`[^1] In practice, RO-Crates declare conformance to particular [profiles](https://www.researchobject.org/ro-crate/profiles.html), allowing processing based on the specific needs and assumptions of a community or usage scenario. This, effectively, makes RO-Crates typed and thus machine-actionable. RO-Crate profiles serve as metadata templates, making it easier for communities to agree and build upon their own metadata needs.

[^1]: [Resources described](https://www.researchobject.org/ro-crate/1.1/contextual-entities.html) by an RO-Crate are also typed, e.g. `Person`, `Organization`, `ScholarlyArticle`, `ImageObject`


RO-Crates have been combined with _machine-actionable Data Management Plans_ (maDMPs) to automate and facilitate management of research data [[Miksa 2020](https://doi.org/10.4126/frl01-006423291)]. This mapping allows RO-Crates to be generated out of maDMPs and vice versa. The ELIXIR Software Management Plans [[Alves 2021](https://doi.org/10.37044/osf.io/k8znb)] is planning to move their questionnaire to a machine-actionable format with RO-Crate. ELIXIR [Biohackathon](https://biohackathon-europe.org/) 2022 will [explore](https://github.com/elixir-europe/biohackathon-projects-2022/tree/main/10) integration of RO-Crate and the [Data Stewardship Wizard](https://ds-wizard.org/) [[Pergl 2019](https://doi.org/10.5334/dsj-2019-059)] with Galaxy, which can automate FDO creation that also follows data management plans.

A tailored RO-Crate profile has been defined to represent Electronic Lab Notebooks (ELN) protocols bundled together with metadata and related datasets. [[Schröder 2022](https://doi.org/10.1186/s13326-021-00257-x)] uses RO-Crates to encode provenance information at different levels, including researchers, manufacturers, biological and chemical resources, activities, measurements, and resulting research data. The use of RO-Crates makes it easier to programmatically question-answer information related to the protocols, for instance activities, resources and equipment used to create data. 

Another example is [WorkflowHub](https://workflowhub.eu/) [[Goble 2021](https://doi.org/10.5281/zenodo.4605654)] which defines the [Workflow RO-Crate](https://w3id.org/workflowhub/workflow-ro-crate/1.0) profile [[Bacall 2022](https://w3id.org/workflowhub/workflow-ro-crate/1.0)], imposing additional constraints such as the presence of a main workflow and a license. It also specifies which entity types and properties must be used to provide such information, implicitly defining a set of operations (e.g., get the main workflow and its language) that are valid on all complying crates. The workflow system Galaxy [[Galaxy 2022](https://doi.org/10.1093/nar/gkac247)] retrieves such Workflow Crates using [GA4GH TRS API](https://about.workflowhub.eu/developer/trs/).

The workflow profile has been further extended (with OOP-like inheritance) in [Workflow Testing RO-Crate](https://crs4.github.io/life_monitor/workflow_testing_ro_crate), adding formal workflow testing components: this adds operations such as getting remote test instances and test definitions, used by the [LifeMonitor](https://www.lifemonitor.eu/) service to keep track of the health status of multiple published workflows. 

While RO-Crates use Web technologies, they are also _self-contained_, moving data along with their metadata. This is a powerful construct for interoperability across FAIR repositories, but this raises some challenges with regards to mutability and persistence of crates.

To illustrate how such challenges can be handled, we detail how the WorkflowHub repository follows several FDO principles:


1. Workflow entries must be _frozen_ for editing and have complete kernel metadata (title, authors, license, description) \[FDOF4] before they can be assigned a persistent identifier, e.g. <https://doi.org/10.48546/workflowhub.workflow.255.1> \[FDOF1]
2. Computational workflows can be composed of multiple files used as a whole, e.g. CWL files in a GitHub repository. These are snapshotted as a single RO-Crate ZIP, indicating the main workflow. \[FDF11]
3. PID resolution can content-negotiate to Datacite’s PID metadata \[FDOF2] or use [FAIR Signposting](https://signposting.org/FAIR/) to find an RO-Crate containing the workflow \[FDOF3] and richer JSON-LD metadata resources \[FDOF5,FDOF8], see [Figure 1](#fig:signposting)
4. Metadata uses schema.org \[FDOF7] following the community-developed Bioschemas [ComputationalWorkflow](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) profile \[FDOF10].
5. Workflows are discovered using the[ GA4GH TRS API](https://about.workflowhub.eu/developer/trs/) [FDOF5,FDOF6,FDOF11] and created/modified using [CRUD operations](https://workflowhub.eu/api) [FDOF6]
6. The RO-Crate profile, effectively the FDO Type \[FDOF7], is declared as <https://w3id.org/workflowhub/workflow-ro-crate/1.0>; the workflow language (e.g. <https://w3id.org/workflowhub/workflow-ro-crate#galaxy> is defined in metadata of the main workflow. 


{{< figure src="signposting.svg" id="fig:signposting" 
  width="100%" title="FAIR Signposting"
  caption="[FAIR Signposting](https://signposting.org/FAIR/) on a workflow PID [[Bayarri 2022](https://doi.org/10.48546/workflowhub.workflow.255.1)] discovered from HTTP `Link:` headers using the [Signposting tool](https://pypi.org/project/signposting/) shows machine-actionable navigation to content-negotiate for the metadata FDOs, as well as download bit sequence [FDOF3] as an RO-Crate zip. [JSON-LD from workflowhub.eu](https://workflowhub.eu/workflows/255.jsonld) follows the BioSchemas [ComputationalWorkflow profile](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE) to give workflow details not included in DataCite’s [general JSON-LD](https://data.crosscite.org/application/ld+json/10.48546/workflowhub.workflow.255.1)." >}}


Further work on RO-Crate profiles include to formalise links to the API operations and repositories \[FDOF5,FDOF7], to include PIDs of profiles and types in the FAIR Signposting, and HTTP navigation to individual resources within the RO-Crate.

RO-Crate has shown a broad adoption by communities across many scientific disciplines, providing a lightweight, and therefore easy to adopt, approach to generating FAIR Digital Objects. It is rapidly becoming an integral part of the interoperability fabric between the different components as demonstrated here for WorkflowHub, contributing to building the European Open Science Cloud.


## Presenting author

Stian Soiland-Reyes


## Submitted to present at

First International Conference on FAIR Digital Objects, poster


## Acknowledgements

We would like to acknowledge the [RO-Crate community](https://www.researchobject.org/ro-crate/community.html) and the [WorkflowHub Club](https://about.workflowhub.eu/project/acknowledgements/).


## Funding

European Commission Horizon 2020 (BioExcel-2 [823830](https://cordis.europa.eu/project/id/823830), EOSC-Life [824087](https://cordis.europa.eu/project/id/824087)), Horizon Europe (BY-COVID [101046203](https://cordis.europa.eu/project/id/101046203), FAIR-IMPACT [101057344](https://cordis.europa.eu/project/id/101057344)). 

Daniel Garijo is supported by the Madrid Government (Comunidad de Madrid-Spain) under the Multiannual Agreement with Universidad Politécnica de Madrid in the line Support for R&D projects for Beatriz Galindo researchers, in the context of the V PRICIT (Regional Programme of Research and Technological Innovation). 

Leyla Jael Castro is supported by a German Research Foundation DFG grant for NFDI4DataScience. 

Frederik Coppens is supported by Research Foundation - Flanders (FWO) for ELIXIR Belgium (I002819N).


## Contributions

Author contributions to this article according to the Contributor Roles Taxonomy [CASRAI CrEDiT](https://casrai.org/credit/):

Stian Soiland-Reyes
: Conceptualization, Funding acquisition, Project administration, Software, Writing – original draft, Writing – review & editing

Peter Sefton
: Funding acquisition, Project administration, Software

Leyla Jael Castro
: Writing – original draft, Writing – review & editing

Frederik Coppens
: Funding acquisition, Supervision, Writing – review & editing

Daniel Garijo
: Software, Writing – review and editing

Simone Leo
: Conceptualization, Project administration, Software, Writing – original draft

Marc Portier
: Writing – review & editing

Paul Groth
: Supervision


## References

[Alves 2022] Renato Alves, Dimitrios Bampalikis, Leyla Jael Castro, José María Fernández, Jennifer Harrow, Mateusz Kuzak, Eva Martin, Fotis E. Psomopoulos, Allegra Via (2022):  
**ELIXIR Software Management Plan for Life Sciences**.  
_BioHackrXiv_  
<https://doi.org/10.37044/osf.io/k8znb>

[Bacall 2022] Finn Bacall, Alan R. Williams, Stuart Owen, Stian Soiland-Reyes (2022):  
**Workflow RO-Crate Profile 1.0.**  
<https://w3id.org/workflowhub/workflow-ro-crate/1.0>

[Bayarri 2022] Genís Bayarri, Adam Hospital (2022): 
**CWL GMX Automatic Ligand Parameterization tutorial**.  
_Workflow Hub_ (Common Workflow Language)  
<https://doi.org/10.48546/workflowhub.workflow.255.1>

[Bizer 2009] C Bizer, Tom Heath, Tim Berners-Lee (2009):  
**Linked Data - The Story So Far**.  
_International Journal on Semantic Web and Information Systems_ **5**(3)  
<https://doi.org/10.4018/jswis.2009081901>

[De Smedt 2020] Koenraad De Smedt, Dimitris Koureas, Peter Wittenburg (2020):   
**FAIR Digital Objects for Science: From Data Pieces to Actionable Knowledge Units**.  
_Publications)_ **8**(2):21   
<https://doi.org/10.3390/publications8020021>

[Galaxy 2022] The Galaxy Community (<small>E. Afgan, A. Nekrutenko, B. A. Grüning, D. Blankenberg, J. Goecks, M. C. Schatz, A. E. Ostrovsky, A. Mahmoud, A. J. Lonie, A. Syme, A. Fouilloux, A. Bretaudeau, A. Nekrutenko, A. Kumar, A. C. Eschenlauer, A. D. DeSanto, A. Guerler, B. Serrano-Solano, B. Batut, B. A. Grüning, B. W. Langhorst, B. Carr, B. A. Raubenolt, C. J. Hyde, C. J. Bromhead, C. B. Barnett, C. Royaux, C. Gallardo, D. Blankenberg, D. J. Fornika, D. Baker, D. Bouvier, D. Clements, D. A. de Lima Morais, D. L. Tabernero, D. Lariviere, E. Nasr, E. Afgan, F. Zambelli, F. Heyl, F. Psomopoulos, F. Coppens, G. R. Price, G. Cuccuru, G. L. Corguillé, G. Von Kuster, G. G. Akbulut, H. Rasche, H. Hans-Rudolf, I. Eguinoa, I. Makunin, I. J. Ranawaka, J. P. Taylor, J. Joshi, J. Hillman-Jackson, J. Goecks, J. M. Chilton, K. Kamali, K. Suderman, K. Poterlowicz, L. B. Yvan, L. Lopez-Delisle, L. Sargent, M. E. Bassetti, M. A. Tangaro, M. van den Beek, M. Čech, M. Bernt, M. Fahrner, M. Tekman, M. C. Föll, M. C. Schatz, M. R. Crusoe, M. Roncoroni, N. Kucher, N. Coraor, N. Stoler, N. Rhodes, N. Soranzo, N. Pinter, N. A. Goonasekera, P. A. Moreno, P. Videm, P. Melanie, P. Mandreoli, P. D. Jagtap, Q. Gu, R. J. M. Weber, R. Lazarus, R. H. P. Vorderman, S. Hiltemann, S. Golitsynskiy, S. Garg, S. A. Bray, S. L. Gladman, S. Leo, S. P. Mehta, T. J. Griffin, V. Jalili, V. Yves, V. Wen, V. K. Nagampalli, W. A. Bacon, W. de Koning, W. Maier, P. J. Briggs</small>) (2022):  
**The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update**.  
_Nucleic Acids Research_ **50**  
<https://doi.org/10.1093/nar/gkac247>

[Goble 2021] Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, José Mª Fernández, Salvador Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano, Philip Ewels, Frederik Coppens (2021):  
**Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory**.  
_Zenodo_  
<https://doi.org/10.5281/zenodo.4605654>

[Guha 2016] R. V. Guha, Dan Brickley, Steve Macbeth (2016):  
**Schema.org: evolution of structured data on the web**.  
_Communications of the ACM_ **59**(2)  
<https://doi.org/10.1145/2844544>

[Miksa 2020] Tomasz Miksa, Maroua Jaoua, Ghaith Arfaoui (2020):  
**Research Object Crates and Machine-actionable Data Management Plans**.  
_First Workshop on Data and Research Objects Management for Linked Open Science (DaMaLOS)_ at The 19th International Semantic Web Conference (ISWC 2020).  
<https://doi.org/10.4126/frl01-006423291>

[Pergl 2019] Robert Pergl, Rob Hooft, Marek Suchánek, Vojtěch Knaisl, Jan Slifka (2019):  
**“Data Stewardship Wizard”: A Tool Bringing Together Researchers, Data Stewards, and Data Experts around Data Management Planning**.  
_Data Science Journal_ **18**(1)  
<https://doi.org/10.5334/dsj-2019-059>

[Schröder 2022] Max Schröder, Susanne Staehlke, Paul Groth, J. Barbara Nebe, Sascha Spors, Frank Krüger (2022):  
**Structure-based knowledge acquisition from electronic lab notebooks for research data provenance documentation**.  
_Journal of Biomedical Semantics_ **13**:4  
<https://doi.org/10.1186/s13326-021-00257-x>

[Soiland-Reyes 2022] Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):  
[**Packaging research artefacts with RO-Crate**](../ro-crate/).  
_Data Science_ (pre-press)  
<https://doi.org/10.3233/DS-210053>

[Wilkinson 2016] Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas Blomberg, Jan-Willem Boiten, Luiz Bonino da Silva Santos, Philip E. Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas, Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard Finkers, Alejandra Gonzalez-Beltran, Alasdair J.G. Gray, Paul Groth, Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A.C ’t Hoen, Rob Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E. Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe Rocca-Serra, Marco Roos, Rene van Schaik, Susanna-Assunta Sansone, Erik Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz, Mark Thompson, Johan van der Lei, Erik van Mulligen, Jan Velterop, Andra Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, Barend Mons (2016):  
**The FAIR Guiding Principles for scientific data management and stewardship**.   
_Nature Scientific Data_ **3**:160018   
<https://doi.org/10.1038/sdata.2016.18>
