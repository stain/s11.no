---
title: "WorkflowHub: a registry for computational workflows"
categories:
  - Publication
summary: >
  arXiv preprint 
description: >
  The rising popularity of computational workflows is driven by the need for repetitive and scalable data processing, sharing of processing know-how, and transparent methods. As both combined records of analysis and descriptions of processing steps, workflows should be reproducible, reusable, adaptable, and available. Workflow sharing presents opportunities to reduce unnecessary reinvention, promote reuse, increase access to best practice analyses for non-experts, and increase productivity. In reality, workflows are scattered and difficult to find, in part due to the diversity of available workflow engines and ecosystems, and because workflow sharing is not yet part of research practice.
  
  WorkflowHub provides a unified registry for all computational workflows that links to community repositories, and supports both the workflow lifecycle and making workflows findable, accessible, interoperable, and reusable (FAIR). By interoperating with diverse platforms, services, and external registries, WorkflowHub adds value by supporting workflow sharing, explicitly assigning credit, enhancing FAIRness, and promoting workflows as scholarly artefacts. The registry has a global reach, with hundreds of research organisations involved, and more than 700 workflows registered.
tags:
  - FAIR
  - Workflow  
authors:
  - name: Ove Johan Ragnar Gustafsson
    orcid: https://orcid.org/0000-0002-2977-5032
  - name: Sean Wilkinson
    orcid: https://orcid.org/0000-0002-1443-7479
  - name: Finn Bacall
    orcid: https://orcid.org/0000-0002-0048-3300
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
  - name: Simone Leo
    orcid: https://orcid.org/0000-0001-8271-5429
  - name: Luca Pireddu
    orcid: https://orcid.org/0000-0002-4663-5613
  - name: Stuart Owen
    orcid: https://orcid.org/0000-0003-2130-0865
  - name: Nick Juty
    orcid: https://orcid.org/0000-0002-2036-8350
  - name: José Mª Fernández
    orcid: https://orcid.org/0000-0002-4806-5140    
  - name: Tom Brown
    orcid: https://orcid.org/0000-0001-8293-4816
  - name: Hervé Ménager
    orcid: https://orcid.org/0000-0002-7552-1009
  - name: Björn Grüning
    orcid: https://orcid.org/0000-0002-3079-6586
  - name: Salvador Capella-Gutierrez
    orcid: https://orcid.org/0000-0002-0309-604X
  - name: Frederik Coppens
    orcid: https://orcid.org/0000-0001-6565-5145
  - name: Carole Goble
    orcid: https://orcid.org/0000-0003-1219-2137
---

**Note**: This preprint has not yet been fully adapted for the Web.

<h2>Cite as</h2>

Ove Johan Ragnar Gustafsson, Sean R. Wilkinson, Finn Bacall, Stian Soiland-Reyes, Simone Leo, Luca Pireddu, Stuart Owen, Nick Juty, José Mª Fernández, Tom Brown, Hervé Ménager, Björn Grüning, Salvador Capella-Gutierrez, Frederik Coppens, Carole Goble (2024):  
**WorkflowHub: a registry for computational workflows**.  
_arXiv_:2410.06941 [cs.DL]  
<https://doi.org/10.48550/arXiv.2410.06941>


# WorkflowHub: a registry for computational workflows

_Ove Johan Ragnar Gustafsson<sup>1</sup>, Sean R. Wilkinson<sup>2</sup>, Finn Bacall<sup>3</sup>, Stian Soiland-Reyes<sup>3</sup>, Simone Leo<sup>4</sup>, Luca Pireddu<sup>4</sup>, Stuart Owen<sup>3</sup>, Nick Juty<sup>3</sup>, José Mª Fernández<sup>5,6</sup>, Tom Brown<sup>7</sup>, Hervé Ménager<sup>8,9</sup>, Björn Grüning<sup>10</sup>, Salvador Capella-Gutierrez<sup>6,11</sup>, Frederik Coppens<sup>12</sup>, Carole Goble<sup>3</sup>_


<div class="affiliations">

<sup>1</sup> Australian BioCommons, University of Melbourne, Melbourne, Victoria, Australia   
<sup>2</sup> Oak Ridge National Laboratory, Oak Ridge, TN, USA   
<sup>3</sup> The University of Manchester, Manchester, UK   
<sup>4</sup> Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Pula (CA), Italy  
<sup>5</sup> Barcelona Supercomputing Center (BSC), Spain  
<sup>6</sup> Spanish National Bioinformatics Institute (INB), Spain  
<sup>7</sup> Leibniz Institute for Zoo- and Wildlife Research, Berlin, Germany  
<sup>8</sup> Institut Pasteur, Université Paris Cité, Bioinformatics and Biostatistics Hub, 75015, Paris, France  
<sup>9</sup> CNRS, UMS 3601, Institut Français de Bioinformatique, IFB-core, 2 rue Gaston Crémieux, F-91000 Evry, France  
<sup>10</sup> Albert-Ludwigs-Universität Freiburg, Freiburg, Germany  
<sup>11</sup> Barcelona Supercomputing Center (BSC), Spain  
<sup>12</sup> VIB Data Core, VIB Technologies, Ghent, Belgium

</div>

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Reformatting as Markdown; references in s11 house style; inline citation hyperlinks; inline hyperlinks. 



## Abstract

The rising popularity of computational workflows is driven by the need for repetitive and scalable data processing, sharing of processing know-how, and transparent methods. As both combined records of analysis and descriptions of processing steps, workflows should be reproducible, reusable, adaptable, and available. Workflow sharing presents opportunities to reduce unnecessary reinvention, promote reuse, increase access to best practice analyses for non-experts, and increase productivity. In reality, workflows are scattered and difficult to find, in part due to the diversity of available workflow engines and ecosystems, and because workflow sharing is not yet part of research practice.

WorkflowHub provides a unified registry for all computational workflows that links to community repositories, and supports both the workflow lifecycle and making workflows findable, accessible, interoperable, and reusable (FAIR). By interoperating with diverse platforms, services, and external registries, WorkflowHub adds value by supporting workflow sharing, explicitly assigning credit, enhancing FAIRness, and promoting workflows as scholarly artefacts. The registry has a global reach, with hundreds of research organisations involved, and more than 700 workflows registered. 

## Introduction

In an era of Big Data and data-driven science, the need for repetitive, scalable, reproducible and quality-assured data processing and analysis methods has contributed to a surge in popularity for computational workflows [[da Silva 2023]]. The past two decades have seen a handful of workflow management systems (WfMS) expand to hundreds [[Amstutz 2024]], and workflows applied across a growing number of domains, including biosciences [[Maier 2021]], astronomy [[Freudling 2023]] and the physical sciences [[McClure 2020]].

In brief, computational workflows are a special kind of software for handling multi-step, multi-code data pipelines, analysis, and simulations, and are intended to automate data-handling processes. They come in many forms, but typically share certain features: a high-level language executed by a dedicated WfMS, which manages data flow and code execution; a composition of modular code or workflow building blocks that can be remixed; and a tendency to be closely associated, even intertwined with the data on which they will operate [[Gil 2007]]. Important scientific goals like repeatability, replicability, and reproducibility become more realistic when scientists specify their experiment’s analysis processes as a computational workflow [[Cohen-Boulakia 2017]]. 

For example, computational workflows have become central to major international science missions that require systematic, reproducible, and shared data analysis. Recent examples include the global response to the COVID-19 pandemic and the analyses of SARS-CoV-2 [[Maier 2021]], and the large-scale sequencing efforts currently in-flight for the Vertebrate Genomes Project (VGP) [[Larivière 2024]]. While these large consortia with defined collaborative research programs are key drivers for computational workflow creation and deployment, workflows are also being adopted across scientific disciplines as their computational requirements increase, and the emphasis on reproducibility and portability increases [[ICGC/TCGA 2020], [[Reiter 2021]], [[Wratten 2021]], [[Patel 2022]], [[Goble 2023]]].

Increasingly, scientists are also being asked to share their data and associated research objects (i.e. software), in ways others can reuse (e.g. the [Nelson Memo](https://www.whitehouse.gov/wp-content/uploads/2022/08/08-2022-OSTP-Public-Access-Memo.pdf), [NASA SPD-41a](https://smd-cms.nasa.gov/wp-content/uploads/2023/08/smd-information-policy-spd-41a.pdf)). 
The idea is to accelerate scientific progress and spur innovation by enabling scientists to avoid reinventing each others’ work, and to explicitly support confidence in published results by removing ambiguity surrounding the approach taken to create research outcomes. 

In addition, scientific activity often includes the exploration of analysis variance; modifying workflows to understand effects and changes on data products is simpler when those workflows are clearly described and available. To this end, Wilkinson et al. published guiding principles for scientific data management and stewardship, providing guidelines for making data and other research objects Findable, Accessible, Interoperable, and Reusable (FAIR) by others [[Wilkinson 2016]]. The FAIR principles have sparked an entire movement in the international community towards adopting FAIR practices, and further work has been undertaken to extend the principles to research software [[Barker 2022]], AI models [[Huerta 2023]], and computational workflows [[Wilkinson 2024]]. A fundamental step towards supporting FAIR workflows [[Goble 2020]] is to enable the sharing of workflows and their descriptions [[Gil 2009]] and make them findable

Researchers find software by searching: the web (i.e. search engines), public software project repositories (e.g. GitHub), the literature, mailing lists, discussion groups (e.g. StackOverflow), dependencies in the software itself, relevant registries (e.g. [CRAN](https://cran.r-project.org/), communities of practice like nf-core [[Ewels 2020], [[Tommaso 2017]]]), and even social media [[Stevens 2022]]. High-quality machine-processable metadata markup is needed to make workflows more findable and understandable in such a “search context”: in other words, the descriptors for workflows must be themselves standardised, accessible, and discoverable. 

Current mechanisms for sharing workflows do not achieve this outcome for the entire workflow ecosystem. Sharing source code includes options such as version control platforms (e.g. [GitHub](https://github.com/) or [GitLab](https://about.gitlab.com/), and WfMS-specific curated git repositories (e.g. Intergalactic Workflow Commission ([IWC](https://github.com/galaxyproject/iwc)) [[Community 2024]], nf-core, [Snakemake catalogue](https://snakemake.github.io/snakemake-workflow-catalog/) [[Mölder 2021]]). Creators can also publish their workflows, either in public generalist repositories (e.g. [Zenodo](https://zenodo.org/), [DataVerse](https://dataverse.org/)), conventional journals (e.g. [GigaScience](https://academic.oup.com/gigascience)) or software journals (e.g. the Journal of Open Source Software, [JOSS](https://joss.theoj.org/)). Finally, a creator can register the workflow using either a platform-specific (e.g. [Knime Community Hub](https://hub.knime.com/), [BinderHub](https://binderhub.readthedocs.io/en/latest/), [nf-core](https://nf-co.re/)) or platform-agnostic solution. The latter includes [Dockstore](https://dockstore.org/), a registry that supports the sharing and running of containerised tools, workflows and notebooks across diverse cloud computing environments [[Yuen 2021]].

While critical for software, discovery of these many resources and platforms can be impeded by non-standardised descriptors that are not necessarily visible to search. Even once a workflow has been found, a divergent ecosystem does not lend itself to better integration of services, adoption of standards, or achieving FAIR outcomes for workflows. A registry that serves as a hub for these various mechanisms, and their specific benefits, would begin to address these challenges. It could support workflow developers to share and gain credit for their work, integrate with the platforms, services and infrastructures that developers and users rely on to both create and use workflows, and support making workflows FAIR. 

Structurally, a registry should be flexible, extensible, and use internationally recognised standards that accommodate rich metadata. To capture and present the breadth of the global computational workflow ecosystem back to the research community, a registry should be agnostic to domains and WfMS, and embrace community standards. Finally, it should provide mechanisms that can link workflows to other digital objects that provide context for a research project, including documents, standard operating procedures (SOPs) and publications.

Here, we present a public and inclusive registry dedicated specifically to the sharing of computational workflows: [WorkflowHub](https://workflowhub.org) [[Goble 2021], [[Goble 2022]], [[Goble 2023]]]. WorkflowHub is designed to allow any scientist, regardless of expertise level, to contribute and share computational workflows. It indexes workflows from any scientific domain, in any format, in any workflow language, regardless of whether it uses a WfMS. Here, we describe in detail how WorkflowHub’s structure, design, standards, community engagement, and continued evolution support: 

1) Collaboration, sharing and credit for workflow developers, projects, and consortia 
2) Integration with added-value services, platforms, and capabilities that support the workflow life cycle (i.e. creation, version control, execution, maintenance, reuse and citation) 
3) Wizards and inbuilt features that ease the process of sharing workflows alongside the constellation of associated digital artefacts that give a workflow its scientific context


## Results

### A registry for computational workflows

The WorkflowHub is a registry for describing, sharing and publishing scientific computational workflows, irrespective of their type, development and maintenance location, or discipline. On the landing page for WorkflowHub, a new user is presented with a description of the platform and its purpose, the latest workflow additions, what content is discoverable, and how to join the WorkflowHub community. 

Underpinning WorkflowHub is the implementation of open tools and standards, which are further described herein. Collaborating Teams are supported by registry features that support workflow reuse, and include integration with native workflow repositories, assignment of credit, import and export, and the creation of curated Collections of workflows that are enriched by other digital objects (e.g. publications, SOPs). 

[Figure 1](#wfhub) provides a conceptual view of the WorkflowHub’s capabilities and its relationship to the workflow development and publishing ecosystem outlined above and discussed later in more depth.

{{< figure src="figure1.png" link="figure1.png" id="wfhub" 
  width="100%" title="WorkflowHub in the workflow life cycle"
  caption=" WorkflowHub connects to platforms, services, and resources that support a workflow’s life cycle [[Courbebaisse 2023]]. A researcher initially needs to **Plan & Find**, where they either plan for a particular analysis and find existing workflows (i.e. using a registry), or **Develop** a new workflow. WorkflowHub integrates with Git repositories (e.g. GitHub, GitLab), and Git-supported communities (e.g. nf-core), to support development. A workflow requires **Test & Review** to **Run & Deploy**, and here WorkflowHub connects to support services (e.g. LifeMonitor, bio.tools, Sapporo WES, WfExS) and welcomes diverse workflow platforms that aid deployment (e.g. CWL, Snakemake, Galaxy, Jupyter, Python, BASH, WDL, Nextflow). A creator needs to Share a workflow and can benefit from WorkflowHub’s use of citation infrastructures and standards (i.e CITATION.cff, Zenodo, DataCite, DOI and ORCID). In the **Maintain & Learn** stage, maintenance, and also understanding of a workflow by other researchers, becomes critical as it impacts workflow **Reuse & Rework**, where a workflow is either reused, or adapted, by other researchers to suit their requirements. WorkflowHub supports these stages through registration of digital objects that enrich a workflow (e.g. documents, publications, SOPs), the ability to create Collections and workflow citations based on DOIs, and ultimately through the connections created to knowledge graphs. WorkflowHub also enables communities of practice to benefit from all its integrations and connections, ensuring that they can reuse or rework workflows from across the globe. The entire support framework is enabled by the implementation of standards that allow WorkflowHub to interact with the ecosystem and truly act as a “Hub”: EDAM, Research Object Crates (RO-Crates), GA4GH APIs, abstract Common Workflow Language (CWL), FAIR Signposting, and Bioschemas." >}}
 
The registry is agnostic to domain, discipline and workflow type, supporting its adoption by a wide spectrum of researchers and other stakeholders. As a result, at the time of writing (October 2024), the registry already indexes workflows ranging from biodiversity, to astronomy and particle physics (see [workflows list on WorkflowHub](https://workflowhub.eu/workflows), with 764 workflows registered for an array of [workflow types](https://workflowhub.eu/workflow_classes) and 840 registered users from 236 Organisations across 35 countries.

{{< figure src="figure2.png" link="figure2.png" id="workflowtypes" 
  width="100%" title="Workflow types"
  caption="registered with WorkflowHub" >}}

WorkflowHub was launched in 2020, as part of the EOSC-Life Workflow Collaboratory [[Goble 2023]], to support the registration of workflows required for the response to the COVID pandemic. WorkflowHub now houses [66 COVID-related workflows](https://workflowhub.eu/search?utf8=%E2%9C%93&q=covid#workflows), including those that support the ongoing global analysis of intra-host variation as new samples become available [[Maier 2021]] [[Baker 2020]]. This outcome demonstrates a central ambition of WorkflowHub: to be of practical use in advancing the application of computational workflows in research science by _supporting the needs of the communities that it serves_.

WorkflowHub meets community requirements and supports the workflow life cycle in three key ways. Firstly, the registry provides structures that directly support collaboration, sharing knowledge and distributing credit. Secondly, woven into this structure are multiple integrations with other elements of the global research ecosystem that support the workflow life cycle: creation, development, discovery, reuse, and citation of workflows. Finally, WorkflowHub provides a registration wizard that guides users in leveraging these structures and integrations. 

This approach is deliberate and will continue to evolve in lock step with the requirements of the community. In the following sections, we will first describe how the data model and metadata framework of WorkflowHub support the registry’s core functions - namely registering, finding, and launching workflows and associated digital data objects. In turn we highlight how the registry design, including the use of wizards to guide best practice, allows it to act as an integrating hub across the workflows ecosystem and to support each stage of the workflow life cycle. Finally, we will describe how the WorkflowHub engages with the workflow community and highlight some key use cases for the registry.


### A data model that reflects real-world collaborations that create workflows


Science is a collaborative enterprise, and infrastructure platforms should reflect this quality to be of practical use in accelerating science missions. Research programs and projects are also intertwined with diverse computational approaches and ways of sharing research outcomes, and these are subject to the same requirements for findability, credit and impact assessment [[Gil 2007]]. As a result, WorkflowHub is structured to reflect real-world collaboration and assign complex credit well. 

The data model of WorkflowHub provides access to three elements for every registered user: Organisations, Teams, and Spaces. A user can specify one or more Organisations (i.e. affiliations) as part of their user profile. They also must belong to at least one Team, which must also belong to an administrative Space. If existing Teams are not suitable or appropriate, a user can create a new Team. A member of a Team can specify Organisations for each Team they join, which allows users to be related to different Organisations for different Teams. Multiple creators and Teams can be specified for a single workflow, additional credit can be assigned to contributors, and a distinction can be made between creators and submitters.

In effect, users belong to Teams, which belong to Spaces, and in this way credit is able to cascade as required from a workflow to creators, contributors, submitters, the Teams and Spaces to which they belong, the consortia and Organisations that these represent, and even new workflows which are derived from the original (see [Figure 3](#structures). 

This nested structure is capable of addressing sharing and credit for a diverse set of workflow contributors, including, but not limited to, individuals (e.g. workflow developers), research groups, institutions (e.g. universities), communities of practice (e.g. nf-core), and major research consortia (e.g. Biodiversity Genomics Europe ([BGE](https://biodiversitygenomics.eu/) [EC \#101059492](https://doi.org/10.3030/101059492)). 

For example, single users or research groups may only require a single Team to represent their workflow(s), and in this case they would add their Team to the default “Independent Teams” Space. However, a consortium representing multiple research groups or institutes may create a distinct Team for each one of its collaborating entities, and add the Teams to either the Independent Teams Space, or create a new Space to administer all these Teams. An individual, group, or consortium can thus establish a presence on WorkflowHub that reflects their real world structure, and which WorkflowHub then uses to assign credit.


{{< figure src="figure3.png" link="figure3.png" id="structures" 
  width="100%" title="A guide to the structures in WorkflowHub"
  caption="You, the user, belong to one or more Organisations (i.e. affiliations). You can also belong to one or more Teams, each of which also needs to belong to a single Space **(top)**. You can nominate which Organisations you wish to use for the different Teams that you have created or joined, and you can belong to multiple Teams in the same Space, as well as multiple Teams in other Spaces **(bottom)**. Image reused with permission from [WorkflowHub documentation](https://about.workflowhub.eu/docs/join-create-teams-spaces/)." >}}

The structure of WorkflowHub can also support an entire community of practice, whereby Spaces and Teams are used to organise contributors, share workflows, and support the sharing of knowledge within that community. This is achieved by registering workflows and linking them to other research outputs, including events, presentations, documents, publications, data files and SOPs - these assets can either be hosted by WorkflowHub or added by reference. 

A workflow developer can even nominate relevant community channels where they can connect with users, and curated “Collections” of workflows can be constructed to help a community manage specific sets of relevant workflows, and other outputs, that may span many scientific applications, workflow languages and research programs (e.g. Threatened Species [Initiative](https://threatenedspeciesinitiative.com/about-tsi/) annotation [workflows](https://workflowhub.eu/collections/23)). 

To streamline the onboarding process for consortia and larger projects, a generic set up guide [[Soiland-Reyes 2024b]], and multiple guides for specific consortia [[Soiland-Reyes 2024c], [[Soiland-Reyes 2024d]], [[Goble 2024b]]], have been created. These guides describe the steps required to get set up on WorkflowHub and use the platform effectively.

### A Hub for workflows

As the name of the registry suggests, the underlying aim of WorkflowHub is to act as a “Hub”, and specifically a Hub that helps to connect the workflows ecosystem and ease the interoperation of its constituent platforms and services. To realise this, WorkflowHub relies on a web-friendly metadata framework that simultaneously supports data representation within the registry itself, while also acting as a foundation for exchange of data and metadata between the platforms and services that are described in [Figure 1](#wfhub). Here, we provide more details for three core areas that underpin this “Hub” functionality [[Goble 2023]]. 

WorkflowHub participates in the EOSC federated Authentication and Authorization Infrastructure through LS-Login and the OAuth2 protocol, in addition to also supporting authentication via GitHub. This feature allows systems interacting with WorkflowHub to identify users as the same individual across different systems – even with their identity provided by their participating institutional accounts – enabling single-sign on and smart authorization decisions on accessing and operating on workflows, their metadata and other resources across the ecosystem forming around WorkflowHub.

To help describe workflows and their components, the registry uses three profiles from bioschemas [[Gray 2017]]: [Computational Tool](https://bioschemas.org/profiles/ComputationalTool/1.0-RELEASE), [Computational Workflow](https://bioschemas.org/profiles/ComputationalWorkflow/1.0-RELEASE), and [Formal Parameter](https://bioschemas.org/profiles/FormalParameter/1.0-RELEASE). 

Even though these are a part of the bioschemas effort, the profiles support a discipline independent and standardised way of describing workflows and their components. In addition, and owing to close collaboration with the Common Workflow Language (CWL) [[Crusoe 2022] [[Amstutz 2016]]] community, the CWL workflow specification is encouraged as a workflow language independent way of describing a WorkflowHub entry. This is the so-called “Abstract CWL”. This format can even hold semantic annotations, which WorkflowHub leverages to extract the typing of workflow inputs and outputs, as well as EDAM ontology concepts for Topics and Operations [[Ison 2013]]. 

[RO-Crate](https://www.researchobject.org/ro-crate/) [[Soiland-Reyes 2022]] is a standard for FAIR Research Objects. It was developed by the community to package a workflow with the components required to understand and execute that workflow. The additional packaged components may include test data, Abstract CWL, diagrams, publications, and SOPs, as well as the flat metadata file that provides the context for all these assets [[Soiland-Reyes 2022]]. The implementation of RO-Crate is central to the ability of WorkflowHub to interoperate and exchange [Workflow-RO-Crate](https://w3id.org/workflowhub/workflow-ro-crate/1.0) data with the ecosystem in [Figure 1](#wfhub) (e.g. Zenodo archiving) and for exposing workflows as FAIR Digital Objects [[Soiland-Reyes 2024a], [[De Smedt 2020]]].

WorkflowHub can also interoperate with workflow execution platforms that are part of the ecosystem (see [Figure 1](#wfhub)) through its implementation of the GA4GH Tools Registry Service ([TRS](https://www.ga4gh.org/product/tool-registry-service-trs/)) [API](https://ga4gh.github.io/tool-registry-service-schemas/). This means that a user of a TRS enabled analysis platform, like Galaxy, is able to search for and retrieve workflows, without leaving the platform. It also means that WorkflowHub can send workflows to these platforms, ready for execution. 

Ultimately, the impact of these features is threefold. Firstly, WorkflowHub is able to support machine actionability, as described by the FAIR principles [[Wilkinson 2016]]. This underpins the registry’s ability to connect to services and platforms that are in use day-to-day by workflow users and developers. Finally, these same users are able to access this ecosystem “Hub” using multiple authentication mechanisms and leverage multiple standards when contributing workflows.


### Using WorkflowHub to register, find and launch workflows

The primary purpose of WorkflowHub is to allow researchers to register and share workflows. Existing public workflows can therefore be viewed, downloaded and launched without needing to register with WorkflowHub. By extension, the contribution of open access and publicly accessible workflows is also encouraged. 

However, workflows may be registered privately, or be embargoed. This functionality supports creators of workflows in cases where they would like to (i.e. a workflow is still being developed), or need to, limit access to a specific group of users. 

User authentication (i.e. login) is required to register content with WorkflowHub, and enables the registry to assign credit and enable citation.

To contribute content an individual user needs to:

1.  **Register** and indicate the Organisations to which they are affiliated. A user can add the following to their profile: a description, their [ORCID](https://orcid.org/), contact details (visible to those in shared Teams and Spaces), as well as knowledge and expertise. More advance configurations are also available via a user profile, including the management of OAuth sessions, authorised applications, API applications, and API tokens.
2.  **Decide which Space on WorkflowHub to use:** a Space is a user-administered section of WorkflowHub that can be used to manage the Teams required for consortia, institutes, or other large research activities. WorkflowHub administers a single default Space called “Independent Teams”. This Space can be used when users do not need to create and manage many Teams, but simply need to create a single Team. All other Spaces are created upon request and administered by those who requested the Space.
3. **Create or join at least one Team:** 
  Teams are one or more people working on a particular research activity involving workflows. Every workflow in WorkflowHub is owned by at least one Team. WorkflowHub users must therefore belong to at least one Team, and this Team must belong to a Space (e.g. Independent Teams). 
  
  In addition to supporting the correct assignment of credit to workflow developers, contributors, and submitters, the Team also enables its members to further describe the context for their workflow development (i.e. background, project description), and serves to promote their contributions to other WorkflowHub users.

Once these steps are complete, a user has the option to register:

  - **Core resources** such as workflows and Collections. As workflows do not exist in a vacuum, Collections allow a WorkflowHub user to bring together workflows with any of their other resources and activities (see below) to create a visible and holistic resource that can support workflow reuse.

  - **Other resources**, including publications, documents, data files, and SOPs.
  
  - **Activities**, including presentations and events.

Registration of workflows can be carried out by manually uploading a workflow file, importing either a RO-Crate or Git repository, and by submission through a [REST](https://about.workflowhub.eu/docs/adding-files/) [API](https://about.workflowhub.eu/developer/ro-crate-api/). As a registry, WorkflowHub is designed to link to workflows held in their native repositories. However, because manual uploading and storage of files is also supported, it can also act as a repository. RO-Crate is used by WorkflowHub as a fundamental unit that underpins upload, download, import and export. Importantly, a user does not need to know how to create or work with RO-Crates, as the registry automatically builds a crate when a workflow is registered using one of the other available mechanisms.

To streamline the above processes, each stage is guided by inbuilt wizards and users are prompted to carry out the next step. For example, after user registration with WorkflowHub, a user is prompted to join or create a new Team. After registration of a workflow file or workflow repository, the user is prompted to complete the set of metadata suggested to create a well described and FAIR workflow entry.

[Figure 4](#examples) illustrates two example WorkflowHub entries: the *dna-seq-varlociraptor* Snakemake [workflow](https://workflowhub.eu/workflows/686) [[Köster 2023]], and the *Find transcripts - TSI* Galaxy [workflow](https://workflowhub.eu/workflows/877) [[Syme 2024]]. The top of the entry emphasises the workflow name (Figure 4.B) and workflow management system (Figure 4.A), along with quick links to the development repository, requesting contact with the authors, subscribing to notifications about changes to the workflow, downloading a workflow RO-Crate, and adding the workflow to a collection. In addition, the workflow creator also has access to administrative options for the workflow entry in this section, which include adding new documents or presentations connected to the workflow, and workflow actions such as adding new versions, requesting a DOI for a specific workflow version, editing the workflow metadata, managing workflow contributors and visibility, and deleting the workflow entry (Figure 4.C). The main panel for the entry has three tabs (Figure 4.D) that provide a workflow overview (including descriptions, version information, metadata, critical annotations, and activity analytics), access and view capability for the files that were registered, and links to related items (e.g. people, Spaces, Teams, Collections, other workflows).


{{< figure src="figure4.png" link="figure4.png" id="examples" 
  width="100%" title="Two example entries in WorkflowHub "
  caption="Workflows (left: [[Köster 2023]], right: [[Syme 2024]]) with sections of the user interface annotated and each entry using the flexible features of WorkflowHub in distinct ways. Entry features include **A)** workflow type, **B)** title, **C)** access panel with links to the source repository (e.g. GitHub), requests to contact the creators, subscribe / unsubscribe, download research object crate (RO-crate), add to a Collection, and in the right hand example access to administrative menus such as Add new (e.g. document, SOP) and Actions (e.g. edit or manage the workflow, including versions and minting DOIs), **D)** tabs for navigation between the entry overview, the list of files in the entry, and lists of items related to the workflow, including people, Teams, Spaces, Organisations, and other digital objects (e.g. publications, documents, SOPs, other workflows), **E)** description, which can be imported from Git, if available, **F)** version history, including Git commits, if available, **G)** creator and submitter information, **H)** links to more information about tools that comprise the workflow (i.e. bio.tools registry entries), **I)** license information, **J)** activity metrics (i.e. downloads and views), **K)** ontology concept annotations (e.g. EDAM in the left example entry), **L)** workflow diagram, **M)** parsed workflow inputs, outputs and steps for specific WfMS (e.g. Galaxy in the right example entry), **N)** buttons for launching workflows on execution platforms (e.g. Galaxy for right example entry), **O)** citation for the workflow (i.e. either using information from a minted DOI or a custom citation (e.g. workflow publication), **P)** custom tags, and **Q)** Collections that include the current workflow entry." >}}


The examples use many of the key features of WorkflowHub, including those enabled by the WorkflowHub registration wizard, which prompts inclusion of critical metadata: these include title (Figure 4.B), workflow management system (Figure 4.A), creators (Figure 4.G), component tools (Figure 4.H), license information (Figure 4.I) and ontology annotations (Figure 4.K). In addition, the *dna-seq-varlociraptor* workflow made use of the WorkflowHub Git integration to ingest the repository README file (complete with badges), as well as providing the link to the development repository (Figure 4.C), the ability to access and view the repository file list natively in WorkflowHub (Figure 4.D), and an annotated version history (including commit IDs, Figure 4.F). 

To find these workflows within the registry, a user can start by applying a text-based search, or by visiting the complete workflow listing where they can filter by type (e.g. Galaxy, Nextflow), tools used (i.e. using bio.tools identifiers [[Ison 2019]], creators, Organisations, Teams, Spaces, and more. Researchers can also refine their searches by making use of faceted browsing and filtering on tags and other annotations, and are able to sort by titles, dates, views and downloads. 

Galaxy’s integration with WorkflowHub leverages the GA4GH TRS API, enabling seamless workflow exchange. Researchers can discover, import, and run workflows from WorkflowHub directly within Galaxy. From the WorkflowHub interface users can utilise the “Run in Galaxy” button (see Figure 4.N), which redirects them to a Galaxy instance and a workflow run form. This interoperability facilitates immediate application and further development of workflows. The use of RO-Crate specification ensures that workflow metadata and components remain accessible and interoperable, aligning with FAIR principles.

### Design that supports the workflow life cycle

To support the workflow life cycle [[Gil 2007]] [[Courbebaisse 2023]] [[Gil 2006]], WorkflowHub integrates with services that workflow creators use for development, execution, maintenance, testing, citation, and ultimately archiving. These integrations initially form part of the workflow registration wizard, which guides a workflow creator through the process of registering their workflow for the first time. However, they are also accessible during a workflow’s maintenance phase, when the workflow may be updated to modify, improve, or repair its function.

#### Ease of access

A user of WorkflowHub begins by accessing the service via LS-Login. This enables researchers to use credentials from their specific institutions or even other identity-providing platforms (e.g. Google, Apple, ORCID). Authentication via GitHub or a local WorkflowHub account is also supported. This feature also enables WorkflowHub administrators to manage user access rights, and to create a custom combination of access levels that are suitable for specific user groups (e.g. research groups, consortia, international projects). 

For example, a contributor may simply want to register a single workflow to make it findable and the contributor may be the only user that requires edit access to the workflow, or to the Team to which the workflow belongs, and access rights can be set accordingly. Conversely, a community of practice (e.g. nf-core), or consortium (e.g. BGE) may have multiple contributors, from multiple institutes, that also belong to multiple WorkflowHub Teams. In this case, granular permissions for edit rights can be set at the workflow, Team and Space levels.

#### Development and versioning 

Integration with the Git version control system is a key aspect of WorkflowHub that supports workflow creation, development and maintenance. If the workflow registration wizard is provided with a Git repository URL, WorkflowHub will automatically import and parse its metadata. In this case, a workflow creator only needs to review, and potentially update, metadata fields prior to completing the registration process. WorkflowHub’s Git integration supports workflows to remain in their native creation and development environment (i.e. a version control system), avoiding any impact of registration on the workflow’s development and management process. 

Moreover, it allows for automation of tasks like updating workflow entries in the registry when workflows are versioned (e.g., by using the LifeMonitor GitHub [app](https://lifemonitor.eu/lm_wft_best_practices_github_app) [[Goble 2023]]). For use cases like Galaxy, where workflows can be created via graphical user interface, rather than scripting, WorkflowHub provides the option to manually upload a workflow file, and step through the wizard manually to enter metadata.

#### WorkflowHub welcomes all workflows

Workflows come in all shapes and sizes, and may even be composed of multiple subworkflows. They may start off as a set of scripts and evolve into a heavily standardised and portable workflow [[Wratten 2021]]. They may use one of the many known WfMS [[Amstutz 2024]]. And, of course, workflows can span virtually every field in the sciences and beyond. In short, the workflow and WfMS ecosystems are diverse. 

One role of WorkflowHub is to make these ecosystems transparent, and it does this by being agnostic to workflow language, maturity, source, structure, and even scientific quality. 
Contributions of every workflow type are [encouraged](https://workflowhub.eu/workflow_classes). Workflows at any development stage (i.e. work-in-progress) are encouraged, not just those workflows considered to be completed and stable. As such, an indication of the maturity of a workflow can be assigned by the creators, and naturally, this metadata is presented to potential workflow consumers in the registry entry to readily identify workflows that may not be ready for reuse. 

#### Annotating workflow purpose (i.e. adding metadata)

The WorkflowHub registration wizard guides users in provision of metadata. Although Bioschemas metadata profiles are used, the only mandatory metadata fields are the workflow Title and the contributing Team(s). In addition to describing the workflow itself, the metadata wizard can be used to associate a workflow to relevant other workflows, presentations, publications, documents, SOPs and data files.

Two key metadata integrations are in place that allow users to search for and add standard identifiers when editing workflow metadata. This functionality is available for bio.tools software [identifiers](https://bio.tools/) and the EDAM ontology concept identifiers for both Topics (e.g. genomics) and data transformation Operations (e.g. genome assembly) [[Ison 2013]]. 

A user can therefore annotate their workflow with persistent links to registry metadata about software that the workflow contains, and standardised shorthand terms that describe its application area and function. In the case of Galaxy, the standard structure of the workflow file is used to extract software tool identifiers and map these automatically to bio.tools [[Lamothe 2023]]. A user can also build on these integrations by manually including custom tags and keywords.

#### Discovery and understanding

When a workflow is ready to be shared and reused, a creator can update their workflow maturity from “work-in-progress” to “stable” in the WorkflowHub entry metadata. It is at this point that a workflow needs to be discoverable in multiple ways, and remain accessible in its original location. The reason for this is that not all researchers will necessarily seek to discover workflows in the same way. As a result, WorkflowHub is flexible in its approach. 

As mentioned earlier, within the registry itself a user can start by applying direct search and filtering to find workflows. External to the registry, the machine-readable, standardised format of WorkflowHub (i.e. Bioschemas) increases the search engine visibility of the rich metadata in a workflow entry. You can interactively explore the impact of workflow registration using evaluator tools such as FAIR-checker [[Rosnet 2024]] and FAIRsoft [[Pico 2022]].

Finding a workflow is step one for a potential user. Once found, the WorkflowHub entry metadata supports a user to understand the workflow, including its design, content, and purpose [[Cohen-Boulakia 2017]]. For example, _“this is a Galaxy type workflow, containing these tools (i.e. links to bio.tools), which are capable of these types of data transformations (i.e. EDAM annotations)”_. 

From a workflow entry that has been annotated with tools, a user can access links to navigate directly to the referenced bio.tools entries to explore and  further understand the components that comprise the workflow. Users can also view the files in the source Git repository (if the workflow was imported from Git), and with a single click visit the repository. It is even possible to subscribe and be notified of changes to entries, removing the need for constant monitoring. 

#### Execution / reuse

WorkflowHub actively supports and develops integrations with workflow execution platforms and services. A key example is the GA4GH TRS [API](https://github.com/ga4gh/tool-registry-service-schemas). If an execution platform or system adopts the TRS standard, it can search WorkflowHub for suitable workflows, retrieve those workflows, and execute them, without the need to develop custom integrations with the workflow’s native repository. Examples include, Galaxy, Sapporo [[Suetake 2022]] (DNA Data Bank of Japan [(DDBJ](https://ddbj.nig.ac.jp/)), and the Workflow Execution Service [(WfExS)](https://github.com/inab/WfExS-backend) [[Fernández 2022]], all of which implement the TRS API, either as providers or consumers. As execution platforms (e.g. Galaxy) can make use of the TRS, they are also able to provide inbuilt search interfaces that connect to WorkflowHub and support platform users to find and import a specific workflow. 

The connection of WorkflowHub to the [LifeMonitor service](https://www.lifemonitor.eu/), through the LifeMonitor GitHub app, allows workflow function and status to be reported to maintainers and users through regular automated tests driven by continuous integration (CI) based monitoring (e.g. Planemo automated workflow testing using Galaxy [[Bray 2023]]). In these cases, WorkflowHub will also include a badge that shows if the tests are passing or failing. An embedded link in the badge takes a user to the LifeMonitor page for the workflow, providing information on the reliability of the workflow over time and the timeliness of the workflow maintainers in solving issues as they arise. In addition, the app can automatically suggest changes to the workflow Git repository that will bring its metadata and structure in line with best practices. 

Finally, to streamline the inclusion of reuse conditions, licensing information is included in the metadata for workflows registered with WorkflowHub, default sharing and license conditions can be specified for Teams, and these rules can be updated by Team administrators.

#### Attribution and citation

It is important to properly attribute contributions to workflows, and this includes provenance of the entire workflow development process. 

The RO-Crate format used by WorkflowHub allows for provenance tracking of metadata, ensuring that workflow creators are given the credit they deserve, while also adding accountability. Workflows can be linked to each other using WorkflowHub metadata (i.e. the "attribution" metadata can be used to indicate that a workflow is based on another workflow). 

The Git integrations described above also support the citation standard [CITATION.cff](https://citation-file-format.github.io/) [[Druskat 2021]], so that WorkflowHub can import this file and use its contents to populate workflow entry metadata for creators, including their ORCID. This approach simplifies citing a workflow according to the wishes of the workflow developer. 

Once a workflow is registered and credit is established within the metadata framework of WorkflowHub, the registry can also, at the push of a button, use [DataCite](https://datacite.org/) to mint persistent digital object identifiers (DOIs) for workflows and to contribute to the DataCite [PID Graph](https://support.datacite.org/docs/datacite-graphql-api-guide). This is the first step to ensuring that workflows can be cited effectively, increasing their visibility and potential impact, and supporting inclusion in the scholarly knowledge graph. 

### User engagement and training

WorkflowHub engages and supports a broad set of use cases, including numerous projects and consortia of global significance. Major projects are supported so that their members are able to use WorkflowHub in a way that aligns with the expectations of their project and its funders. Workflow communities (e.g. nf-core, CWL, Snakemake) are directly engaged by the WorkflowHub team, and supported to make their best practice workflows available in the registry.

The main mechanism through which engagement happens is the fortnightly open format [WorkflowHub Club meeting](https://about.workflowhub.eu/#community), where anyone can join the conversation, learn more about the registry, ask questions, and even contribute to the on-going development and evolution of the registry. There are also indirect ways through which workflow creators and users interact with WorkflowHub and its resources. 

The WorkflowHub Club team creates and presents content for the registry at conferences, in webinars and workshops, and as part of [Ask-Me-Anything forum events](https://about.workflowhub.eu/project/outreach/). Registered users of WorkflowHub are also able to ask questions and provide direct feedback via the registry interface. These communications are sent directly to the administrators of WorkflowHub for review and response. 

Finally, WorkflowHub operates a [documentation site](https://about.workflowhub.eu/docs/) where users can access information on how to use the registry.

Clear and practical guidelines are required to support users of WorkflowHub. For example, some annotations are consistently missing from workflow entries, and useful features are sometimes overlooked (e.g. Git integration, parsing of CITATION.cff files, linking data to workflows, and linking workflows to each other). 

This highlights that the rich feature set of WorkflowHub is not necessarily immediately clear, and that guidance in leveraging these features is absolutely critical to support users in achieving best practice. It is important that the provided guidelines also extend to recommendations for how to organise a workflow development repository (i.e. Git repositories). 

This will enable WorkflowHub to extend the process currently in place for Galaxy IWC to more community repositories: integrating with these repositories in a more standard way to automatically manage the update of workflow versions in WorkflowHub, such that they are in sync with Git releases. 

As a result, and as highlighted earlier, a general onboarding and set up guide for projects and consortia has been developed [[Soiland-Reyes 2024b]], as have multiple consortia specific guides [[Soiland-Reyes 2024c]] [[Goble 2024b]]. Workflow resources have also been developed for the Galaxy Training Network (GTN [[Hiltemann 2023]]) [Smörgåsbord events](https://gallantries.github.io/video-library/modules/ro-crate) and specific GTN [tutorial sets](https://training.galaxyproject.org/training-material/topics/fair/).

Finally, the WorkflowHub team actively identifies opportunities to engage with peer infrastructures to grow the user base of the registry, investigate and create integrations that are of enduring value, and further improve the function of the registry. For example, WorkflowHub is actively fostering a conversation with publishers and journals focused on how to make workflows citable objects in the literature [[Goble 2024a]]. 

WorkflowHub is also being further developed to fully align with the best practice guidelines of the SciCodes Consortium [[Garijo 2022]], implement the FAIR Principles for Research Software (FAIR4RS) [[Barker 2022]] and contribute to the CodeMeta specification for software [[Jones 2024]]. As described earlier, a registry like WorkflowHub enables the creation of workflows that follow the FAIR principles, from the perspective of data [[Wilkinson 2016]], software [[Barker 2022]], and the unique features of workflows (e.g. abstraction, composition). 

WorkflowHub is central to discussions in the FAIR Computational Workflows working group for the Workflows Community Initiative [(WCI](https://workflows.community/groups/fair/)). This working group engages broadly across the global workflows ecosystem (i.e. workflow developers, communities, platforms and services) to develop FAIR principles for workflows [[Wilkinson 2024]]. The ultimate aim is to use the outcomes of these engagements to guide the evolution of WorkflowHub as a FAIR registry for workflows.

### Use Cases

To effectively support the sharing of workflows, WorkflowHub supports collaborations and communities of practice within the sciences. WorkflowHub contributions span domains such as cancer, COVID, genomics, rare diseases, geosciences, climate, physics, and more. WorkflowHub users span the globe and 35 countries are represented in the registered user [list](https://workflowhub.eu/people).

#### Research consortia & infrastructures

WorkflowHub is an integral platform for consortia and projects. Here we provide details for three specific use cases, EOSC-Life, BGE, and Australian BioCommons.

EOSC-Life was a key use case driver, as it supported the implementation of FAIR computational workflows in the EU by seeking to develop a cloud-based Workflow Collaboratory [[Goble 2021]] that ultimately resulted in the creation of WorkflowHub. The aim was to create a platform that would support community collaboration on the development, use, and reuse of FAIR computational workflows [[Goble 2020]], and to do so in a way that bridges research domains and infrastructures [[Goble 2023]] [[Goble 2021]]. WorkflowHub accommodates the diversity of EOSC-Life and ensures the visibility of workflows applied across its many established research infrastructures as they are created and registered [[Goble 2021]].

The BGE project is a coming together of two communities of researchers with a common goal of cataloguing biodiversity through genomic resources: the European Reference Genome Atlas [[Mazzoni 2023]] and the European node of the International Barcode of Life consortium (iBOL [Europe](https://iboleurope.org/)). Providing reference-quality genomes to the community (ERGA) and monitoring biodiversity through DNA barcoding (iBOL Europe) requires the management and processing of vast amounts of data, in an accessible and distributed fashion, relying on input from multiple individuals and institutes. The combination of BGE WorkflowHub [Spaces](https://workflowhub.eu/programmes/25), [Teams](https://workflowhub.eu/projects/163) and [Collections](https://workflowhub.eu/collections/10) allows individuals to contribute as needed to the projects across the consortium. As workflows have been collected and curated by the community, they in effect also come with a “seal of approval” for external users that wish to replicate the work of ERGA or iBOL Europe. All together, such a structure of publishing and maintaining workflows facilitates BGE in achieving their ambitious goals of cataloguing biodiversity in Europe and bringing together researchers from the biodiversity genomics community.

Australian [BioCommons](https://www.biocommons.org.au/) is a national infrastructure project that actively supports life science research communities with community scale digital infrastructure [[Christiansen 2024]]. Rather than building anew, BioCommons aims to adopt fit-for-purpose international platforms and services that, in the case of workflows, can assist with the provision of sophisticated software, analysis capabilities, and digital asset stewardship. WorkflowHub is the primary workflow registry for [BioCommons](https://workflowhub.eu/programmes/8), and it is the focal point for sharing the collaborative workflow efforts of BioCommons and its infrastructure partners together with Australian life science [researchers](https://workflowhub.eu/collections/6).

#### Workflow management systems

WorkflowHub accepts all workflow types, and includes Galaxy [[Community 2024]], Snakemake [[Mölder 2021]], Nextflow [[Tommaso 2017]], job schedulers (e.g. PyCOMPS [[Tejedor 2017]], application-specific types like SCIPION [[Rosa-Trevín 2016]], notebooks (e.g. [Jupyter](https://jupyter.org/)), and even scripting languages (e.g. R [[R 2024]] and [Python](https://www.python.org/) [[Boer 1991]] (see also [Figure 2](#workflowtypes)). WorkflowHub provides customised support for WfMS that are critical for specific domain communities (e.g. bioinformatics). 

This is currently the case for Galaxy, CWL and Nextflow, and additional significant and popular WfMS may be supported with relevant features, when appropriate. As an example, the registry development team, together with Galaxy, have created functionalities for WorkflowHub that include:

1) semi-automated registration of new and updated Galaxy IWC workflows
2) integration with LifeMonitor to further support semi-automated registration but also Planemo workflow test monitoring
3) automatic mapping of tool identifiers to the bio.tools registry [[Goble 2023]]. 

As the CWL community has been closely involved in registry development, WorkflowHub also has in-built functions for parsing CWL, and makes use of Abstract CWL. Most recently, engagement between nf-core and the WorkflowHub team resulted in the creation of automatic registration and metadata parsing functions for this community’s [Nextflow workflows](https://elixiruknode.org/news/2024/workflowhub-nf-core-workflow-accessibility/). [These workflows](https://workflowhub.eu/workflows?filter[project]=15) can now be found in WorkflowHub. 

#### Individual workflow developers

WorkflowHub supports large international science missions and consortia. However, the registry welcomes and encourages contributions from any workflow developer, regardless of their research domain, application areas, or the size of their research group. In fact, the largest Space on WorkflowHub is currently Independent Teams, which covers 287 people, 185 Teams, 180 Organisations and 279 workflows.

## Discussion

We have presented WorkflowHub, a registry that enriches the scientific workflows ecosystem by being a hub for discovery and sharing of workflows from across multiple languages, communities, consortia, and scientific domains. The registry connects this community of users and contributors to workflow development, support, and scholarly services that support the requirement for workflows to be shared and credited, as well as the various requirements developers encounter during the workflow life cycle (see [Figure 1](#wfhub)). 

Workflows continually evolve to keep pace with changing research questions, data types and practices. Similarly, it is intended for WorkflowHub to evolve in lock step with the changing requirements of both the developers and users of computational workflows.

The roadmap for WorkflowHub over the next few years can be broadly broken down into four aspects: improving the support and resources available to users of the registry, onboarding new communities and domains, contributing thought leadership for workflow best practices that directly impact aspects such as workflow visibility and quality, and aligning to FAIR principles for computational workflows.

### Improving support

As WorkflowHub and its integrated services intend to support the workflow life cycle, and not simply the registration and publication of workflows, the registry will aim to improve processes that align to supporting this life cycle. This includes improving search and the inbuilt wizards that assist with onboarding and resource registration, but also improving overall ease-of-use and guidance. Additions and improvements for the UI will continue, adding those features that are required by end users. Particular attention will be paid to tracking workflow cloning, as well as supporting workflow collections, sub-workflows, and nested workflows. 

Continued work on the onboarding guidelines created for WorkflowHub will improve the quality of workflow organisation for contributing groups (i.e. big projects and consortia), in part by including guides that cover best practice instructions for the structure and content of workflow repositories as well as how to make the most impact with LifeMonitor, but also by contributing to training. 

To date, WorkflowHub has been included in existing training, such as the GTN [Smörgåsbords](https://training.galaxyproject.org/) and workflow registration workshops [[Samaha 2023]]. As a next step, this effort should be extended to include WorkflowHub lessons in Software Carpentry developed by the Data Science training programme for Health and Biosciences [(Ed-DASH](https://edcarp.github.io/Ed-DaSH/)) for [Nextflow](https://carpentries-incubator.github.io/workflows-nextflow/) and [Snakemake](https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/). 

As the number of contributors and workflow assets grow, it will be critical to also explore the use of automated mechanisms that allow scaling of support. This could include streamlined metadata annotation approaches that use Large Language Models (LLMs) to populate metadata fields for review by a workflow creator, automatic reporting of issues to workflow creators and their Teams, or integration with additional added value services like APICURON [[Hatos 2021]]. 

Reflecting their importance to the operation of WorkflowHub, integrations with platforms and services that support the workflow life cycle will be added, improved, and updated. The RO-Crate format used by WorkflowHub will be central to this effort. 

Planned updates include the ability to natively configure automated synchronisation between Git repositories and WorkflowHub. Setting this up to match the expectations of the community of WorkflowHub users will be essential, and will depend on registry and community co-development, in particular for those case where work involves the repositories used by WfMS communities. In addition, the ability to “launch” workflows on additional instances that implement TRS will be explored (e.g. Seqera [Platform](https://seqera.io/platform/)), and benchmarking service integrations for workflow entries will be added through collaboration with [OpenEBench](https://openebench.bsc.es/) [[Capella-Gutierrez 2017]].

### Onboarding

WorkflowHub has already supported the onboarding of WfMS communities, including Galaxy’s IWC and Nextflow’s nf-core. A similar integration is currently being finalised for the GTN. These community-centric engagements have resulted in the addition of hundreds of workflows to the registry and, given that WorkflowHub is now integrated with the source repositories where new workflows are developed, this number will only grow.

Identifying and engaging workflow communities to onboard, in particular those that converge on specific WfMS, will be critical to increasing the number of workflows in the registry and the visibility of the workflows ecosystem overall, as well as to ensure that further requirements for WorkflowHub are being collected from a diverse set of stakeholders. 

Support provided to new communities may entail:
1) tailored integrations with community repositories, facilitating semi-automated ingestion of workflows to WorkflowHub and synchronised registration of new workflow releases
2) supporting WfMS communities to make the best use of WorkflowHub, including how to implement high quality workflow repository structures and effectively adopt both standards (e.g. RO-Crate, Abstract CWL, TRS) and services (e.g. LifeMonitor).

This level of support is now being explored for Snakemake workflows, and will involve close collaboration with the Snakemake community.

### Workflow visibility and recognition

WorkflowHub already has the capacity to import citation, author and contributor credit metadata from CITATION.cff files. In future, this could be extended to other popular standards, including codemeta.json [[Jones 2024]]. Through DataCite, WorkflowHub has the means to mint DOIs, and incorporate workflows with DOIs into [OpenAIRE](https://www.openaire.eu/). WorkflowHub has thus actively worked to increase the visibility of workflows in a standardised and streamlined fashion. This approach is already bearing fruit, with examples of WorkflowHub formatted citations appearing in the published literature [[Coin 2024]] [[Roach 2024]].

In addition, there are now examples of journals making computational workflows the focus of published works. A critical outcome here is to ensure that WorkflowHub becomes a recommended registry for journals and publishers. This includes providing workflow creators and users with a set of best practice recommendations for how to properly document and ultimately cite workflows in published research.

A forum has already been established with multiple publishers and journals, and these continuing conversations will aim to address the challenges (i.e. citation formats, complexity of workflow citations, impact on publishing system, recommended practices for peer review of workflows) and opportunities (i.e. developer recognition, tracking, reproducibility) presented by formal citation of computational workflows.


### Hand-holding for FAIR principles

As frequently alluded to in other sections, WorkflowHub is strongly connected to the FAIR principles at numerous levels. One of these levels that is of particular importance for users is the way that it “holds users’ hands” during the process of sharing workflows and related research artefacts. The FAIR principles are only guidelines, and even the most well-intentioned attempts to follow them can go awry in unexpected ways [[Wilkinson 2022]]. WorkflowHub aims to help the user to follow best practices, including following the FAIR principles, by making them convenient, but not imposing them as requirements.

For example, WorkflowHub helps users make their workflows Findable – easy to find for both humans and machines – by assigning globally unique and persistent identifiers for the workflows and their different versions (i.e. WorkflowHub identifiers and DOIs). WorkflowHub also guides users to describe their workflows with rich metadata, including the identifier for the workflow, and these metadata are automatically exposed for indexing through WorkflowHub’s use of Bioschemas.

WorkflowHub similarly helps users make their workflows Accessible – available to humans and machines over open protocols that provide optional access control – by providing multiple APIs over HTTPS. These APIs include the JSON-based  [FAIRDOM-SEEK API](https://workflowhub.eu/api), an [RO-Crate Submission API](https://about.workflowhub.eu/developer/ro-crate-api/), and the TRS API. Workflow DOIs can also be minted, which means the workflow and its metadata will be accessible even if the workflow itself is no longer available or if the workflow itself cannot be shared openly.

Workflows, after being found and accessed, should ideally be Interoperable – able to be used by humans and machines as part of a wider computational ecosystem. Interoperability often requires a lot of “plumbing” that WorkflowHub provides for users automatically through the use of open-source standards (i.e. RO-Crate as the primary data exchange format) and domain- and tool-specific integrations (i.e. Galaxy IWC and Nextflow nf-core). By guiding users through the process of inputting metadata, WorkflowHub reduces complexity and tedium, making it significantly easier to create interoperable workflows.

Finally, WorkflowHub helps users ensure their workflows are Reusable – allowed to be used in part or in entirety by other humans and machines. In particular, it does this by providing opportunities to specify a clear and accessible license, qualified references to other software, and detailed provenance. WorkflowHub also collaborates closely with prominent communities in the computational workflows space (see Use Cases section) so that the registry can accommodate and incorporate domain-relevant community standards.

## Methods

### Governance

WorkflowHub is an ELIXIR service supported by the UK and Belgium ELIXIR [Nodes](https://elixir-europe.org/) [[ELIXIR 2024]] as well as Australian [BioCommons](https://www.biocommons.org.au/) [[Christiansen 2024]]. The registry is part of both the ELIXIR  [Tools Platform](https://elixir-europe.org/platforms/tools) and  [Research Software Ecosystem](https://research-software-ecosystem.github.io/), and forms part of both [EuroScienceGateway](https://esciencelab.org.uk/projects/eurosciencegateway/) and DARE-UK [TRE-FX](https://esciencelab.org.uk/projects/tre-fx/). 

Governance is coordinated and managed by the [WorkflowHub Club](https://about.workflowhub.eu/project/community/): an inclusive community that meets biweekly online and consists of workflow developers/creators and workflow users, as well as WorkflowHub developers and product owners. The minutes for these meetings are [open](https://docs.google.com/document/d/1U2KAlbKviCu-fCX-znncKIBUIUUOeEnuRGdAg-fNd4Q/edit) and a GitHub organisation is used to manage [documentation](https://github.com/workflowhub-eu/about). Club members include representatives from ELIXIR, WCI, Australian BioCommons, and more. Over 60 people are listed as [contributors](https://about.workflowhub.eu/project/acknowledgements/#workflowhub-club), and any new contributors are invited to join. WorkflowHub has secured funding for sustainability through Horizon Europe projects, ELIXIR Europe and national UK funds. 

### Technical infrastructure

WorkflowHub is developed openly, and largely virtually, using open software development practices, hackathons, and virtual communication channels. It has both a [roadmap](https://about.workflowhub.eu/project/roadmap/) and regular release cycle (i.e SEEK release [cycle](https://github.com/seek4science/seek/). WorkflowHub requests for Team registration are supported for the American and Asia Pacific time zones by Oak Ridge National [Laboratory](https://www.ornl.gov/) and Australian BioCommons, respectively. 

WorkflowHub is built on the FAIRDOM-SEEK software [[Wolstencroft 2017]]. FAIRDOM-SEEK was originally developed as a data-management platform for the systems biology community, but has been generalised over time to support a wide variety of use cases, and now has numerous deployments across the world supporting many different communities. Development of FAIRDOM-SEEK is a collaborative activity with contributors from institutions in the UK, Germany, Belgium, Sweden and elsewhere. WorkflowHub is currently hosted on the University of Manchester’s Research IT cloud. 

WorkflowHub makes use of Git to store workflows as repositories. This enables the addition, modification and deletion of files for workflows that are uploaded directly to the registry by a user, as well as the ability to freeze “snapshots” of specific workflow versions. If a workflow has been added either via Git import or through submission of an RO-Crate, it then needs to be explicitly versioned and uploaded again. Curation of registered workflows is the responsibility of the workflow creators and / or submitters.

## Data Availability

WorkflowHub will ensure data and metadata availability and access up to 2027, with plans to extend this availability further. Further availability of data and metadata from WorkflowHub falls under two categories. For workflows with minted DOIs, the archiving of data and metadata is managed via DataCite. 

For all workflows, and associated digital assets, WorkflowHub has an [End-of-Life policy](https://about.workflowhub.eu/project/#retention-and-end-of-life-policy). 
The policy states that <q>If and when the WorkflowHub reaches its end of service after that (i.e. 2027), the published contributions and metadata will be archived as RO-Crates and made available through a public repository, such as Zenodo, Figshare or another appropriate resource at that time. DOI registrations will in this case be updated to link to the archived deposits.</q>. 

A knowledge graph of registered Workflow RO-Crates as of 2024-08 is published on Zenodo [[Hambley 2024]].


## Code Availability

WorkflowHub code is available as part of the [FAIRDOM-SEEK project](https://github.com/seek4science/seek) [[Owen 2024]].


## Acknowledgments

The authors are grateful to Sehrish Kanwal of the University of Melbourne for feedback and suggestions about the draft.

### Funding

workflowhub.eu was founded as part of EOSC-Life (WP2 Tools Collaboratory), funded by the European Union’s Horizon 2020 programme under grant agreement H2020-INFRAEOSC-2018-2 824087\. This work was further supported by funding from European Commission’s Horizon Europe programme and UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee: EuroScienceGateway (HORIZON-INFRA-2021-EOSC-01-04 101057388, UKRI 10038963), BY-COVID (HORIZON-INFRA-2021-EMERGENCY-01 101046203), FAIR-IMPACT (HORIZON-INFRA-2021-EOSC-01-05 101057344, UKRI 10038992), BioDT (HORIZON-INFRA-2021-TECH-01-01 101057437, UKRI 10038930), PREP-IBISBA (H2020-INFRADEV-2019-2 871118), AgroServ (HORIZON-INFRA-2021-SERV-01-02 101058020, UKRI 10038927), BIOINDUSTRY 4.0 (HORIZON-INFRA-2022-TECH-01 101094287, UKRI 10048146). 

This work is supported by Australian BioCommons which is enabled by NCRIS via Bioplatforms Australia funding, by the Sardinian Regional Government through the XData Project, and by the LIFEMAP project (Italian Ministry of Health, POS T3).

The work supported by the ELIXIR-DE node was supported by the German Federal Ministry of Education and Research BMBF grant 031 A538A de.NBI-RBC and the Ministry of Science, Research and the Arts Baden-Württemberg (MWK) within the framework of LIBIS/de.NBI Freiburg.

This research used resources of the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. Department of Energy under Contract No. DE-AC05-00OR22725.

## Author Contributions

Here, we follow the Contributor Role Taxonomy [(CRediT)](https://credit.niso.org). OJRG contributed through: Writing – original draft, Writing – review & editing, Project administration, Data curation, and Supervision. SRW contributed through: Writing – original draft, Writing – review & editing, and Project administration. FB contributed through: Conceptualization, Data curation, Investigation, Project administration, Software, Methodology, and Resources. SSR contributed through: Conceptualization, Funding acquisition, Investigation, Supervision, and Writing – review & editing. SO contributed through: Conceptualization, Investigation, Project administration, Software, and Methodology. NJ contributed through: Data curation and Writing – review & editing. FC contributed through: Conceptualization, Funding acquisition, Methodology, Project administration, Resources, and Supervision. CG contributed through: Conceptualization, Funding acquisition, Methodology, Project administration, Resources, Supervision, Visualization, Writing – original draft, and Writing – review & editing. All other authors contributed to the manuscript through: Writing – review & editing.

The authors declare no competing interests.

## References


\[Amstutz 2016\]
Peter Amstutz, Michael R. Crusoe, Nebojša Tijanić, Brad Chapman, John Chilton, Michael Heuer, Andrey Kartashov, Dan Leehr, Hervé Ménager, Maya Nedeljkovich, Matt Scales, Stian Soiland-Reyes, Luka Stojanovic (2016):  
**Common Workflow Language, v1.0**  
<https://doi.org/10.6084/M9.FIGSHARE.3115156.V2>

\[Amstutz 2024\]
Peter Amstutz, Maxim Mikheev, Michael R. Crusoe, Nebojša Tijanić, Samuel Lampa (2024):  
**Existing Workflow systems.**  
Common Workflow Language wiki.  
*GitHub*  
<https://s.apache.org/existing-workflow-systems> (accessed 8 July 2024)

\[Baker 2020\]
Dannon Baker, Marius Van Den Beek, Daniel Blankenberg, Dave Bouvier, John Chilton, Nate Coraor, Frederik Coppens, Ignacio Eguinoa, Simon Gladman, Björn Grüning, Nicholas Keener, Delphine Larivière, Andrew Lonie, Sergei Kosakovsky Pond, Wolfgang Maier, Anton Nekrutenko, James Taylor, Steven Weaver (2020):  
**No more business as usual: Agile and effective responses to emerging pathogen threats require open data and open analytics**.  
*PLOS Pathogens* **16**(8)  
<https://doi.org/10.1371/journal.ppat.1008643>

\[Barker 2022\]
Michelle Barker, Neil P. Chue Hong, Daniel S. Katz, Anna-Lena Lamprecht, Carlos Martinez-Ortiz, Fotis Psomopoulos, Jennifer Harrow, Leyla Jael Castro, Morane Gruenpeter, Paula Andrea Martinez, Tom Honeyman (2022):  
**Introducing the FAIR Principles for research software**.  
*Scientific Data* **9**(1)  
<https://doi.org/10.1038/s41597-022-01710-x>

\[Boer 1991\]
Guido Van Rossum & Jelke De Boer (1991):  
**Interactively testing remote servers using the Python programming language**.  
*CWI quarterly* **4**(4)  
<https://ir.cwi.nl/pub/18204>

\[Bray 2023\]
Simon Bray, John Chilton, Matthias Bernt, Nicola Soranzo, Marius van den Beek, Bérénice Batut, Helena Rasche, Martin Čech, Peter J. A. Cock, Björn Grüning, Anton Nekrutenko (2023):  
**The Planemo toolkit for developing, deploying, and executing scientific data analyses in Galaxy and beyond**.  
*Genome Research* **33**(2)  
<https://doi.org/10.1101/gr.276963.122>

\[Capella-Gutierrez 2017\]
Salvador Capella-Gutierrez, Diana De La Iglesia, Juergen Haas, Analia Lourenco, José María Fernández, Dmitry Repchevsky, Christophe Dessimoz, Torsten Schwede, Cedric Notredame, Josep Ll Gelpi, Alfonso Valencia (2017):  
**Lessons Learned: Recommendations for Establishing Critical Periodic Scientific Benchmarking**  
<https://doi.org/10.1101/181677>

\[Christiansen 2024\]
Rhys Francis & Jeffrey H. Christiansen (2024):  
**Australian BioCommons Strategic Plan 2023 - 2028**  
<https://doi.org/10.5281/zenodo.13626350>

\[Cohen-Boulakia 2017\]
Sarah Cohen-Boulakia, Khalid Belhajjame, Olivier Collin, Jérôme Chopard, Christine Froidevaux, Alban Gaignard, Konrad Hinsen, Pierre Larmande, Yvan Le Bras, Frédéric Lemoine, Fabien Mareuil, Hervé Ménager, Christophe Pradal, Christophe Blanchet (2017):  
**Scientific workflows for computational reproducibility in the life sciences**: Status, challenges and opportunities.   
*Future Generation Computer Systems* **75** 
<https://doi.org/10.1016/j.future.2017.01.012>

\[Coin 2024\]
Michael B. Hall & Lachlan J. M. Coin (2024):  
**Pangenome databases improve host removal and mycobacteria classification from clinical metagenomic data**.  
*GigaScience* **13** 
<https://doi.org/10.1093/gigascience/giae010>

\[Community 2024\]
The Galaxy Community, <small>Linelle Ann L. Abueg, Enis Afgan, Olivier Allart, Ahmed H. Awan, Wendi A. Bacon, Dannon Baker, Madeline Bassetti, Bérénice Batut, Matthias Bernt, Daniel Blankenberg, Aureliano Bombarely, Anthony Bretaudeau, Catherine J. Bromhead, Melissa L. Burke, Patrick K. Capon, Martin Čech, María Chavero-Díez, John M. Chilton, Tyler J. Collins, Frederik Coppens, Nate Coraor, Gianmauro Cuccuru, Fabio Cumbo, John Davis, Paul F. De Geest, Willem De Koning, Martin Demko, Assunta DeSanto, José Manuel Domínguez Begines, Maria A. Doyle, Bert Droesbeke, Anika Erxleben-Eggenhofer, Melanie C. Föll, Giulio Formenti, Anne Fouilloux, Rendani Gangazhe, Tanguy Genthon, Jeremy Goecks, Alejandra N. Gonzalez Beltran, Nuwan A. Goonasekera, Nadia Goué, Timothy J. Griffin, Björn A. Grüning, Aysam Guerler, Sveinung Gundersen, Ove Johan Ragnar Gustafsson, Christina Hall, Thomas W. Harrop, Helge Hecht, Alireza Heidari, Tillman Heisner, Florian Heyl, Saskia Hiltemann, Hans-Rudolf Hotz, Cameron J. Hyde, Pratik D. Jagtap, Julia Jakiela, James E. Johnson, Jayadev Joshi, Marie Jossé, Khaled Jum’ah, Matúš Kalaš, Katarzyna Kamieniecka, Tunc Kayikcioglu, Markus Konkol, Leonid Kostrykin, Natalie Kucher, Anup Kumar, Mira Kuntz, Delphine Lariviere, Ross Lazarus, Yvan Le Bras, Gildas Le Corguillé, Justin Lee, Simone Leo, Leandro Liborio, Romane Libouban, David López Tabernero, Lucille Lopez-Delisle, Laila S. Los, Alexandru Mahmoud, Igor Makunin, Pierre Marin, Subina Mehta, Winnie Mok, Pablo A. Moreno, François Morier-Genoud, Stephen Mosher, Teresa Müller, Engy Nasr, Anton Nekrutenko, Tiffanie M. Nelson, Asime J. Oba, Alexander Ostrovsky, Polina V. Polunina, Krzysztof Poterlowicz, Elliott J. Price, Gareth R. Price, Helena Rasche, Bryan Raubenolt, Coline Royaux, Luke Sargent, Michelle T. Savage, Volodymyr Savchenko, Denys Savchenko, Michael C. Schatz, Pauline Seguineau, Beatriz Serrano-Solano, Nicola Soranzo, Sanjay Kumar Srikakulam, Keith Suderman, Anna E. Syme, Marco Antonio Tangaro, Jonathan A. Tedds, Mehmet Tekman, Wai Cheng (Mike) Thang, Anil S. Thanki, Michael Uhl, Marius Van Den Beek, Deepti Varshney, Jenn Vessio, Pavankumar Videm, Greg Von Kuster, Gregory R. Watson, Natalie Whitaker-Allen, Uwe Winter, Martin Wolstencroft, Federico Zambelli, Paul Zierep, Rand Zoabi</small> (2024):  
**The Galaxy platform for accessible, reproducible, and collaborative data analyses**: 2024 update.  
*Nucleic Acids Research*  
<https://doi.org/10.1093/nar/gkae410>

\[Courbebaisse 2023\]
Guy Courbebaisse, Bernd Flemisch, Kay Graf, Uwe Konrad, Jason Maassen, Raphael Ritz (2023):  
**Research Software Lifecycle**  
<https://doi.org/10.5281/zenodo.8324828>

\[Crusoe 2022\]
Michael R. Crusoe, Sanne Abeln, Alexandru Iosup, Peter Amstutz, John Chilton, Nebojša Tijanić, Hervé Ménager, Stian Soiland-Reyes, Bogdan Gavrilović, Carole Goble, The Cwl Community (2022):  
**Methods included: Standardizing computational reuse and portability with the Common Workflow Language**.  
*Communications of the ACM* **65**(6)  
<https://doi.org/10.1145/3486897>

\[da Silva 2023\]
<small>Rafael Ferreira da Silva, Rosa M. Badia, Venkat Bala, Debbie Bard, Peer-Timo Bremer, Ian Buckley, Silvina Caino-Lores, Kyle Chard, Carole Goble, Shantenu Jha, Daniel S. Katz, Daniel Laney, Manish Parashar, Frederic Suter, Nick Tyler, Thomas Uram, Ilkay Altintas, Stefan Andersson, William Arndt, Juan Aznar, Jonathan Bader, Bartosz Balis, Chris Blanton, Kelly Rosa Braghetto, Aharon Brodutch, Paul Brunk, Henri Casanova, Alba Cervera Lierta, Justin Chigu, Taina Coleman, Nick Collier, Iacopo Colonnelli, Frederik Coppens, Michael Crusoe, Will Cunningham, Bruno De Paula Kinoshita, Paolo Di Tommaso, Charles Doutriaux, Matthew Downton, Wael Elwasif, Bjoern Enders, Chris Erdmann, Thomas Fahringer, Ludmilla Figueiredo, Rosa Filgueira, Martin Foltin, Anne Fouilloux, Luiz Gadelha, Andy Gallo, Artur Garcia Saez, Daniel Garijo, Roman Gerlach, Ryan Grant, Samuel Grayson, Patricia Grubel, Johan Gustafsson, Valerie Hayot-Sasson, Oscar Hernandez, Marcus Hilbrich, AnnMary Justine, Ian Laflotte, Fabian Lehmann, Andre Luckow, Jakob Luettgau, Ketan Maheshwari, Motohiko Matsuda, Doriana Medic, Pete Mendygral, Marek Michalewicz, Jorji Nonaka, Maciej Pawlik, Loic Pottier, Line Pouchard, Mathias Putz, Santosh Kumar Radha, Lavanya Ramakrishnan, Sashko Ristov, Paul Romano, Daniel Rosendo, Martin Ruefenacht, Katarzyna Rycerz, Nishant Saurabh, Volodymyr Savchenko, Martin Schulz, Christine Simpson, Raul Sirvent, Tyler Skluzacek, Stian Soiland-Reyes, Renan Souza, Sreenivas Rangan Sukumar, Ziheng Sun, Alan Sussman, Douglas Thain, Mikhail Titov, Benjamin Tovar, Aalap Tripathy, Matteo Turilli, Bartosz Tuznik, Hubertus Van Dam, Aurelio Vivas, Logan Ward, Patrick Widener, Sean Wilkinson, Justyna Zawalska, Mahnoor Zulfiqar</small> (2023):  
**Workflows Community Summit 2022: A Roadmap Revolution**  
<https://doi.org/10.5281/zenodo.7750670>

\[De Smedt 2020\]
Koenraad De Smedt, Dimitris Koureas, Peter Wittenburg (2020):  
**FAIR Digital Objects for Science: From Data Pieces to Actionable Knowledge Units**.  
*Publications* **8**(2)  
<https://doi.org/10.3390/publications8020021>

\[Druskat 2021\]
Stephan Druskat, Jurriaan H. Spaaks, Neil Chue Hong, Robert Haines, James Baker, Spencer Bliven, Egon Willighagen, David Pérez-Suárez, Alexander Konovalov (2021):  
**Citation File Format**  
<https://doi.org/10.5281/zenodo.5171937>

\[ELIXIR 2024\]
ELIXIR (2024):  
**ELIXIR Annual Report 2023**  
_F1000Research_ **13**(ELIXIR):779  
<https://doi.org/10.7490/F1000RESEARCH.1119751.1>

\[Ewels 2020\]
Philip A. Ewels, Alexander Peltzer, Sven Fillinger, Harshil Patel, Johannes Alneberg, Andreas Wilm, Maxime Ulysse Garcia, Paolo Di Tommaso, Sven Nahnsen (2020):  
**The nf-core framework for community-curated bioinformatics pipelines**.  
*Nature Biotechnology* **38**(3)  
<https://doi.org/10.1038/s41587-020-0439-x>

\[Fernández 2022\]
José M. Fernández, Laura Rodríguez-Navas, Salvador Capella-Gutiérrez (2022):  
**Secured and annotated execution of workflows with WfExS-backend**  
<https://doi.org/10.7490/F1000RESEARCH.1119198.1>

\[Freudling 2023\]
Wolfram Freudling, Stefano Zampieri, Lodovico Coccato, Stanislaw Podgorski, Martino Romaniello, Andrea Modigliani, John Pritchard (2023):  
**Adaptive Data Reduction Workflows for Astronomy – The ESO Data Processing System (EDPS)**  
<https://doi.org/10.48550/ARXIV.2311.03822>

\[Garijo 2022\]
Daniel Garijo, Hervé Ménager, Lorraine Hwang, Ana Trisovic, Michael Hucka, Thomas Morrell, Alice Allen, Task Force on Best Practices for Software Registries, SciCodes Consortium (2022):  
**Nine best practices for research software registries and repositories**.  
*PeerJ Computer Science* **8** 
<https://doi.org/10.7717/peerj-cs.1023>

\[Gil 2006\]
Ewa Deelman & Yolanda Gil (2006):  
**Managing Large-Scale Scientific Workflows in Distributed Environments**: Experiences and Challenges.  
*2006 Second IEEE International Conference on e-Science and Grid Computing (e-Science’06)*    
<https://doi.org/10.1109/E-SCIENCE.2006.261077>

\[Gil 2007\]
Yolanda Gil, Ewa Deelman, Mark Ellisman, Thomas Fahringer, Geoffrey Fox, Dennis Gannon, Carole Goble, Miron Livny, Luc Moreau, Jim Myers (2007):  
**Examining the Challenges of Scientific Workflows**.  
*Computer* **40**(12)  
<https://doi.org/10.1109/MC.2007.421>

\[Gil 2009\]
Yolanda Gil (2009):  
**From data to knowledge to discoveries: Artificial intelligence and scientific workflows**.  
*Scientific Programming* **17**(3)  
<https://doi.org/https://doi.org/10.3233/SPR-2009-0261>

\[Goble 2020\]
Carole Goble, Sarah Cohen-Boulakia, Stian Soiland-Reyes, Daniel Garijo, Yolanda Gil, Michael R. Crusoe, Kristian Peters, Daniel Schober (2020):  
**FAIR Computational Workflows**.  
*Data Intelligence* **2**(1-2)  
<https://doi.org/10.1162/dint_a_00033>

\[Goble 2021\]
Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Simone Leo, Luca Pireddu, Laura Rodríguez-Navas, José Mª Fernández, Salvador Capella-Gutierrez, Hervé Ménager, Björn Grüning, Beatriz Serrano-Solano, Philip Ewels, Frederik Coppens (2021):  
**Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory**  
<https://doi.org/10.5281/zenodo.4605654>

\[Goble 2022\]
Carole Goble, Finn Bacall, Stian Soiland-Reyes, Stuart Owen, Alan Williams, Ignacio Eguinoa, Bert Droesbeke, Hervé Ménager, Laura Rodríguez Navas, José María Fernández, Salvador Capella-Gutierrez, Michael R. Crusoe, Björn Grüning, Simone Leo, Luca Pireddu, Johan Gustafsson, Phil Ewels, WorkflowHub Community, Frederik Coppens (2022):  
**WorkflowHub – a FAIR registry for workflows**  
<https://doi.org/10.7490/F1000RESEARCH.1118984.1>

\[Goble 2023\]
Carole Goble, Stian Soiland-Reyes, Finn Bacall, Stuart Owen, Luca Pireddu, Simone Leo (2023):  
**EOSC-Life Implementation of a mechanism for publishing and sharing workflows across instances of the environment**  
<https://doi.org/10.5281/zenodo.7886545>

\[Goble 2024a\]
Carole Goble (2024):  
**WorkflowHub Publishers and Journal Forum**  
<https://galaxyproject.org/news/2024-08-03-workflow-publisher-forum/> (accessed 12 August 2024)

\[Goble 2024b\]
Carole Goble, Finn Bacall, Stian Soiland-Reyes (2024):  
**The BY-COVID Guide to using WorkflowHub**  
<https://doi.org/10.48546/WORKFLOWHUB.SOP.10.1> (accessed 11 June 2024)

\[Gray 2017\]
Alasdair J G Gray, Carole Goble, Rafael C. Jimenez (2017):  
**Bioschemas: From potato salad to protein annotation**.  
*ISWC 2017 posters & demonstrations and industry tracks*  urn:nbn:de:0074-1963-7, (RWTH Aachen University)  
<https://iswc2017.semanticweb.org/paper-579/>

\[Hambley 2024\]
Alexander Hambley, Eli Chadwick, Oliver Woolland, Stian Soiland-Reyes, Volodymyr Savchenko (2024):  
**WorkflowHub Knowledge Graph**  
_Zenodo_
<https://doi.org/10.5281/zenodo.13362051>

\[Hatos 2021\]
András Hatos, Federica Quaglia, Damiano Piovesan, Silvio C. E. Tosatto (2021):  
**APICURON: A database to credit and acknowledge the work of biocurators**.  
*Database* **2021** 
<https://doi.org/10.1093/database/baab019>

\[Hiltemann 2023\]
Saskia Hiltemann, Helena Rasche, Simon Gladman, Hans-Rudolf Hotz, Delphine Larivière, Daniel Blankenberg, Pratik D. Jagtap, Thomas Wollmann, Anthony Bretaudeau, Nadia Goué, Timothy J. Griffin, Coline Royaux, Yvan Le Bras, Subina Mehta, Anna Syme, Frederik Coppens, Bert Droesbeke, Nicola Soranzo, Wendi Bacon, Fotis Psomopoulos, Cristóbal Gallardo-Alba, John Davis, Melanie Christine Föll, Matthias Fahrner, Maria A. Doyle, Beatriz Serrano-Solano, Anne Claire Fouilloux, Peter Van Heusden, Wolfgang Maier, Dave Clements, Florian Heyl, Galaxy Training Network, Björn Grüning, Bérénice Batut (2023):  
**Galaxy Training**: A powerful framework for teaching\!  
*PLOS Computational Biology* **19**(1)  
<https://doi.org/10.1371/journal.pcbi.1010752>

\[Huerta 2023\]
E. A. Huerta, Ben Blaiszik, L. Catherine Brinson, Kristofer E. Bouchard, Daniel Diaz, Caterina Doglioni, Javier M. Duarte, Murali Emani, Ian Foster, Geoffrey Fox, Philip Harris, Lukas Heinrich, Shantenu Jha, Daniel S. Katz, Volodymyr Kindratenko, Christine R. Kirkpatrick, Kati Lassila-Perini, Ravi K. Madduri, Mark S. Neubauer, Fotis E. Psomopoulos, Avik Roy, Oliver Rübel, Zhizhen Zhao, Ruike Zhu (2023):  
**FAIR for AI: An interdisciplinary and international community building perspective**.  
*Scientific Data* **10**(1)  
<https://doi.org/10.1038/s41597-023-02298-6>

\[ICGC/TCGA 2020\]
<small>
The ICGC/TCGA Pan-Cancer Analysis of Whole Genomes Consortium,
Lauri A. Aaltonen, Federico Abascal, Adam Abeshouse, Hiroyuki Aburatani, David J. Adams, Nishant Agrawal, Keun Soo Ahn, Sung-Min Ahn, Hiroshi Aikata, Rehan Akbani, Kadir C. Akdemir, Hikmat Al-Ahmadie, Sultan T. Al-Sedairy, Fatima Al-Shahrour, Malik Alawi, Monique Albert, Kenneth Aldape, Ludmil B. Alexandrov, Adrian Ally, Kathryn Alsop, Eva G. Alvarez, Fernanda Amary, Samirkumar B. Amin, Brice Aminou, Ole Ammerpohl, Matthew J. Anderson, Yeng Ang, Davide Antonello, Pavana Anur, Samuel Aparicio, Elizabeth L. Appelbaum, Yasuhito Arai, Axel Aretz, Koji Arihiro, Shun-ichi Ariizumi, Joshua Armenia, Laurent Arnould, Sylvia Asa, Yassen Assenov, Gurnit Atwal, Sietse Aukema, J. Todd Auman, Miriam R. R. Aure, Philip Awadalla, Marta Aymerich, 
Gary D. Bader, Adrian Baez-Ortega, Matthew H. Bailey, Peter J. Bailey, Miruna Balasundaram, Saianand Balu, Pratiti Bandopadhayay, Rosamonde E. Banks, Stefano Barbi, Andrew P. Barbour, Jonathan Barenboim, Jill Barnholtz-Sloan, Hugh Barr, Elisabet Barrera, John Bartlett, Javier Bartolome, Claudio Bassi, Oliver F. Bathe, Daniel Baumhoer, Prashant Bavi, Stephen B. Baylin, Wojciech Bazant, Duncan Beardsmore, Timothy A. Beck, Sam Behjati, Andreas Behren, Beifang Niu, Cindy Bell, Sergi Beltran, Christopher Benz, Andrew Berchuck, Anke K. Bergmann, Erik N. Bergstrom, Benjamin P. Berman, Daniel M. Berney, Stephan H. Bernhart, Rameen Beroukhim, Mario Berrios, Samantha Bersani, Johanna Bertl, Miguel Betancourt, Vinayak Bhandari, Shriram G. Bhosle, Andrew V. Biankin, Matthias Bieg, Darell Bigner, Hans Binder, Ewan Birney, Michael Birrer, Nidhan K. Biswas, Bodil Bjerkehagen, Tom Bodenheimer, Lori Boice, Giada Bonizzato, Johann S. De Bono, Arnoud Boot, Moiz S. Bootwalla, Ake Borg, Arndt Borkhardt, Keith A. Boroevich, Ivan Borozan, Christoph Borst, Marcus Bosenberg, Mattia Bosio, Jacqueline Boultwood, Guillaume Bourque, Paul C. Boutros, G. Steven Bova, David T. Bowen, Reanne Bowlby, David D. L. Bowtell, Sandrine Boyault, Rich Boyce, Jeffrey Boyd, Alvis Brazma, Paul Brennan, Daniel S. Brewer, Arie B. Brinkman, Robert G. Bristow, Russell R. Broaddus, Jane E. Brock, Malcolm Brock, Annegien Broeks, Angela N. Brooks, Denise Brooks, Benedikt Brors, Søren Brunak, Timothy J. C. Bruxner, Alicia L. Bruzos, Alex Buchanan, Ivo Buchhalter, Christiane Buchholz, Susan Bullman, Hazel Burke, Birgit Burkhardt, Kathleen H. Burns, John Busanovich, Carlos D. Bustamante, Adam P. Butler, Atul J. Butte, Niall J. Byrne, Anne-Lise Børresen-Dale, 
Samantha J. Caesar-Johnson, Andy Cafferkey, Declan Cahill, Claudia Calabrese, Carlos Caldas, Fabien Calvo, Niedzica Camacho, Peter J. Campbell, Elias Campo, Cinzia Cantù, Shaolong Cao, Thomas E. Carey, Joana Carlevaro-Fita, Rebecca Carlsen, Ivana Cataldo, Mario Cazzola, Jonathan Cebon, Robert Cerfolio, Dianne E. Chadwick, Dimple Chakravarty, Don Chalmers, Calvin Wing Yiu Chan, Kin Chan, Michelle Chan-Seng-Yue, Vishal S. Chandan, David K. Chang, Stephen J. Chanock, Lorraine A. Chantrill, Aurélien Chateigner, Nilanjan Chatterjee, Kazuaki Chayama, Hsiao-Wei Chen, Jieming Chen, Ken Chen, Yiwen Chen, Zhaohong Chen, Andrew D. Cherniack, Jeremy Chien, Yoke-Eng Chiew, Suet-Feung Chin, Juok Cho, Sunghoon Cho, Jung Kyoon Choi, Wan Choi, Christine Chomienne, Zechen Chong, Su Pin Choo, Angela Chou, Angelika N. Christ, Elizabeth L. Christie, Eric Chuah, Carrie Cibulskis, Kristian Cibulskis, Sara Cingarlini, Peter Clapham, Alexander Claviez, Sean Cleary, Nicole Cloonan, Marek Cmero, Colin C. Collins, Ashton A. Connor, Susanna L. Cooke, Colin S. Cooper, Leslie Cope, Vincenzo Corbo, Matthew G. Cordes, Stephen M. Cordner, Isidro Cortés-Ciriano, Kyle Covington, Prue A. Cowin, Brian Craft, David Craft, Chad J. Creighton, Yupeng Cun, Erin Curley, Ioana Cutcutache, Karolina Czajka, Bogdan Czerniak, 
Rebecca A. Dagg, Ludmila Danilova, Maria Vittoria Davi, Natalie R. Davidson, Helen Davies, Ian J. Davis, Brandi N. Davis-Dusenbery, Kevin J. Dawson, Francisco M. De La Vega, Ricardo De Paoli-Iseppi, Timothy Defreitas, Angelo P. Dei Tos, Olivier Delaneau, John A. Demchok, Jonas Demeulemeester, German M. Demidov, Deniz Demircioğlu, Nening M. Dennis, Robert E. Denroche, Stefan C. Dentro, Nikita Desai, Vikram Deshpande, Amit G. Deshwar, Christine Desmedt, Jordi Deu-Pons, Noreen Dhalla, Neesha C. Dhani, Priyanka Dhingra, Rajiv Dhir, Anthony DiBiase, Klev Diamanti, Li Ding, Shuai Ding, Huy Q. Dinh, Luc Dirix, HarshaVardhan Doddapaneni, Nilgun Donmez, Michelle T. Dow, Ronny Drapkin, Oliver Drechsel, Ruben M. Drews, Serge Serge, Tim Dudderidge, Ana Dueso-Barroso, Andrew J. Dunford, Michael Dunn, Lewis Jonathan Dursi, Fraser R. Duthie, Ken Dutton-Regester, 
Jenna Eagles, Douglas F. Easton, Stuart Edmonds, Paul A. Edwards, Sandra E. Edwards, Rosalind A. Eeles, Anna Ehinger, Juergen Eils, Roland Eils, Adel El-Naggar, Matthew Eldridge, Kyle Ellrott, Serap Erkek, Georgia Escaramis, Shadrielle M. G. Espiritu, Xavier Estivill, Dariush Etemadmoghadam, Jorunn E. Eyfjord, 
Bishoy M. Faltas, Daiming Fan, Yu Fan, William C. Faquin, Claudiu Farcas, Matteo Fassan, Aquila Fatima, Francesco Favero, Nodirjon Fayzullaev, Ina Felau, Sian Fereday, Martin L. Ferguson, Vincent Ferretti, Lars Feuerbach, Matthew A. Field, J. Lynn Fink, Gaetano Finocchiaro, Cyril Fisher, Matthew W. Fittall, Anna Fitzgerald, Rebecca C. Fitzgerald, Adrienne M. Flanagan, Neil E. Fleshner, Paul Flicek, John A. Foekens, Kwun M. Fong, Nuno A. Fonseca, Christopher S. Foster, Natalie S. Fox, Michael Fraser, Scott Frazer, Milana Frenkel-Morgenstern, William Friedman, Joan Frigola, Catrina C. Fronick, Akihiro Fujimoto, Masashi Fujita, Masashi Fukayama, Lucinda A. Fulton, Robert S. Fulton, Mayuko Furuta, P. Andrew Futreal, Anja Füllgrabe, 
Stacey B. Gabriel, Steven Gallinger, Carlo Gambacorti-Passerini, Jianjiong Gao, Shengjie Gao, Levi Garraway, Øystein Garred, Erik Garrison, Dale W. Garsed, Nils Gehlenborg, Josep L. L. Gelpi, Joshy George, Daniela S. Gerhard, Clarissa Gerhauser, Jeffrey E. Gershenwald, Mark Gerstein, Moritz Gerstung, Gad Getz, Mohammed Ghori, Ronald Ghossein, Nasra H. Giama, Richard A. Gibbs, Bob Gibson, Anthony J. Gill, Pelvender Gill, Dilip D. Giri, Dominik Glodzik, Vincent J. Gnanapragasam, Maria Elisabeth Goebler, Mary J. Goldman, Carmen Gomez, Santiago Gonzalez, Abel Gonzalez-Perez, Dmitry A. Gordenin, James Gossage, Kunihito Gotoh, Ramaswamy Govindan, Dorthe Grabau, Janet S. Graham, Robert C. Grant, Anthony R. Green, Eric Green, Liliana Greger, Nicola Grehan, Sonia Grimaldi, Sean M. Grimmond, Robert L. Grossman, Adam Grundhoff, Gunes Gundem, Qianyun Guo, Manaswi Gupta, Shailja Gupta, Ivo G. Gut, Marta Gut, Jonathan Göke, 
Gavin Ha, Andrea Haake, David Haan, Siegfried Haas, Kerstin Haase, James E. Haber, Nina Habermann, Faraz Hach, Syed Haider, Natsuko Hama, Freddie C. Hamdy, Anne Hamilton, Mark P. Hamilton, Leng Han, George B. Hanna, Martin Hansmann, Nicholas J. Haradhvala, Olivier Harismendy, Ivon Harliwong, Arif O. Harmanci, Eoghan Harrington, Takanori Hasegawa, David Haussler, Steve Hawkins, Shinya Hayami, Shuto Hayashi, D. Neil Hayes, Stephen J. Hayes, Nicholas K. Hayward, Steven Hazell, Yao He, Allison P. Heath, Simon C. Heath, David Hedley, Apurva M. Hegde, David I. Heiman, Michael C. Heinold, Zachary Heins, Lawrence E. Heisler, Eva Hellstrom-Lindberg, Mohamed Helmy, Seong Gu Heo, Austin J. Hepperla, José María Heredia-Genestar, Carl Herrmann, Peter Hersey, Julian M. Hess, Holmfridur Hilmarsdottir, Jonathan Hinton, Satoshi Hirano, Nobuyoshi Hiraoka, Katherine A. Hoadley, Asger Hobolth, Ermin Hodzic, Jessica I. Hoell, Steve Hoffmann, Oliver Hofmann, Andrea Holbrook, Aliaksei Z. Holik, Michael A. Hollingsworth, Oliver Holmes, Robert A. Holt, Chen Hong, Eun Pyo Hong, Jongwhi H. Hong, Gerrit K. Hooijer, Henrik Hornshøj, Fumie Hosoda, Yong Hou, Volker Hovestadt, William Howat, Alan P. Hoyle, Ralph H. Hruban, Jianhong Hu, Taobo Hu, Xing Hua, Kuan-lin Huang, Mei Huang, Mi Ni Huang, Vincent Huang, Yi Huang, Wolfgang Huber, Thomas J. Hudson, Michael Hummel, Jillian A. Hung, David Huntsman, Ted R. Hupp, Jason Huse, Matthew R. Huska, Barbara Hutter, Carolyn M. Hutter, Daniel Hübschmann, 
Christine A. Iacobuzio-Donahue, Charles David Imbusch, Marcin Imielinski, Seiya Imoto, William B. Isaacs, Keren Isaev, Shumpei Ishikawa, Murat Iskar, S. M. Ashiqul Islam, Michael Ittmann, Sinisa Ivkovic, Jose M. G. Izarzugaza, Jocelyne Jacquemier, Valerie Jakrot, Nigel B. Jamieson, Gun Ho Jang, Se Jin Jang, Joy C. Jayaseelan, Reyka Jayasinghe, Stuart R. Jefferys, Karine Jegalian, Jennifer L. Jennings, Seung-Hyup Jeon, Lara Jerman, Yuan Ji, Wei Jiao, Peter A. Johansson, Amber L. Johns, Jeremy Johns, Rory Johnson, Todd A. Johnson, Clemency Jolly, Yann Joly, Jon G. Jonasson, Corbin D. Jones, David R. Jones, David T. W. Jones, Nic Jones, Steven J. M. Jones, Jos Jonkers, Young Seok Ju, Hartmut Juhl, Jongsun Jung, Malene Juul, Randi Istrup Juul, Sissel Juul, Natalie Jäger, 
Rolf Kabbe, Andre Kahles, Abdullah Kahraman, Vera B. Kaiser, Hojabr Kakavand, Sangeetha Kalimuthu, Christof Von Kalle, Koo Jeong Kang, Katalin Karaszi, Beth Karlan, Rosa Karlić, Dennis Karsch, Katayoon Kasaian, Karin S. Kassahn, Hitoshi Katai, Mamoru Kato, Hiroto Katoh, Yoshiiku Kawakami, Jonathan D. Kay, Stephen H. Kazakoff, Marat D. Kazanov, Maria Keays, Electron Kebebew, Richard F. Kefford, Manolis Kellis, James G. Kench, Catherine J. Kennedy, Jules N. A. Kerssemakers, David Khoo, Vincent Khoo, Narong Khuntikeo, Ekta Khurana, Helena Kilpinen, Hark Kyun Kim, Hyung-Lae Kim, Hyung-Yong Kim, Hyunghwan Kim, Jaegil Kim, Jihoon Kim, Jong K. Kim, Youngwook Kim, Tari A. King, Wolfram Klapper, Kortine Kleinheinz, Leszek J. Klimczak, Stian Knappskog, Michael Kneba, Bartha M. Knoppers, Youngil Koh, Jan Komorowski, Daisuke Komura, Mitsuhiro Komura, Gu Kong, Marcel Kool, Jan O. Korbel, Viktoriya Korchina, Andrey Korshunov, Michael Koscher, Roelof Koster, Zsofia Kote-Jarai, Antonios Koures, Milena Kovacevic, Barbara Kremeyer, Helene Kretzmer, Markus Kreuz, Savitri Krishnamurthy, Dieter Kube, Kiran Kumar, Pardeep Kumar, Sushant Kumar, Yogesh Kumar, Ritika Kundra, Kirsten Kübler, Ralf Küppers, 
Jesper Lagergren, Phillip H. Lai, Peter W. Laird, Sunil R. Lakhani, Christopher M. Lalansingh, Emilie Lalonde, Fabien C. Lamaze, Adam Lambert, Eric Lander, Pablo Landgraf, Luca Landoni, Anita Langerød, Andrés Lanzós, Denis Larsimont, Erik Larsson, Mark Lathrop, Loretta M. S. Lau, Chris Lawerenz, Rita T. Lawlor, Michael S. Lawrence, Alexander J. Lazar, Ana Mijalkovic Lazic, Xuan Le, Darlene Lee, Donghoon Lee, Eunjung Alice Lee, Hee Jin Lee, Jake June-Koo Lee, Jeong-Yeon Lee, Juhee Lee, Ming Ta Michael Lee, Henry Lee-Six, Kjong-Van Lehmann, Hans Lehrach, Dido Lenze, Conrad R. Leonard, Daniel A. Leongamornlert, Ignaty Leshchiner, Louis Letourneau, Ivica Letunic, Douglas A. Levine, Lora Lewis, Tim Ley, Chang Li, Constance H. Li, Haiyan Irene Li, Jun Li, Lin Li, Shantao Li, Siliang Li, Xiaobo Li, Xiaotong Li, Xinyue Li, Yilong Li, Han Liang, Sheng-Ben Liang, Peter Lichter, Pei Lin, Ziao Lin, W. M. Linehan, Ole Christian Lingjærde, Dongbing Liu, Eric Minwei Liu, Fei-Fei Fei Liu, Fenglin Liu, Jia Liu, Xingmin Liu, Julie Livingstone, Dimitri Livitz, Naomi Livni, Lucas Lochovsky, Markus Loeffler, Georgina V. Long, Armando Lopez-Guillermo, Shaoke Lou, David N. Louis, Laurence B. Lovat, Yiling Lu, Yong-Jie Lu, Youyong Lu, Claudio Luchini, Ilinca Lungu, Xuemei Luo, Hayley J. Luxton, Andy G. Lynch, Lisa Lype, Cristina López, Carlos López-Otín, 
Eric Z. Ma, Yussanne Ma, Gaetan MacGrogan, Shona MacRae, Geoff Macintyre, Tobias Madsen, Kazuhiro Maejima, Andrea Mafficini, Dennis T. Maglinte, Arindam Maitra, Partha P. Majumder, Luca Malcovati, Salem Malikic, Giuseppe Malleo, Graham J. Mann, Luisa Mantovani-Löffler, Kathleen Marchal, Giovanni Marchegiani, Elaine R. Mardis, Adam A. Margolin, Maximillian G. Marin, Florian Markowetz, Julia Markowski, Jeffrey Marks, Tomas Marques-Bonet, Marco A. Marra, Luke Marsden, John W. M. Martens, Sancha Martin, Jose I. Martin-Subero, Iñigo Martincorena, Alexander Martinez-Fundichely, Yosef E. Maruvka, R. Jay Mashl, Charlie E. Massie, Thomas J. Matthew, Lucy Matthews, Erik Mayer, Simon Mayes, Michael Mayo, Faridah Mbabaali, Karen McCune, Ultan McDermott, Patrick D. McGillivray, Michael D. McLellan, John D. McPherson, John R. McPherson, Treasa A. McPherson, Samuel R. Meier, Alice Meng, Shaowu Meng, Andrew Menzies, Neil D. Merrett, Sue Merson, Matthew Meyerson, William Meyerson, Piotr A. Mieczkowski, George L. Mihaiescu, Sanja Mijalkovic, Tom Mikkelsen, Michele Milella, Linda Mileshkin, Christopher A. Miller, David K. Miller, Jessica K. Miller, Gordon B. Mills, Ana Milovanovic, Sarah Minner, Marco Miotto, Gisela Mir Arnau, Lisa Mirabello, Chris Mitchell, Thomas J. Mitchell, Satoru Miyano, Naoki Miyoshi, Shinichi Mizuno, Fruzsina Molnár-Gábor, Malcolm J. Moore, Richard A. Moore, Sandro Morganella, Quaid D. Morris, Carl Morrison, Lisle E. Mose, Catherine D. Moser, Ferran Muiños, Loris Mularoni, Andrew J. Mungall, Karen Mungall, Elizabeth A. Musgrove, Ville Mustonen, David Mutch, Francesc Muyas, Donna M. Muzny, Alfonso Muñoz, Jerome Myers, Ola Myklebost, Peter Möller, 
Genta Nagae, Adnan M. Nagrial, Hardeep K. Nahal-Bose, Hitoshi Nakagama, Hidewaki Nakagawa, Hiromi Nakamura, Toru Nakamura, Kaoru Nakano, Tannistha Nandi, Jyoti Nangalia, Mia Nastic, Arcadi Navarro, Fabio C. P. Navarro, David E. Neal, Gerd Nettekoven, Felicity Newell, Steven J. Newhouse, Yulia Newton, Alvin Wei Tian Ng, Anthony Ng, Jonathan Nicholson, David Nicol, Yongzhan Nie, G. Petur Nielsen, Morten Muhlig Nielsen, Serena Nik-Zainal, Michael S. Noble, Katia Nones, Paul A. Northcott, Faiyaz Notta, Brian D. O’Connor, Peter O’Donnell, Maria O’Donovan, Sarah O’Meara, Brian Patrick O’Neill, J. Robert O’Neill, David Ocana, Angelica Ochoa, Layla Oesper, Christopher Ogden, Hideki Ohdan, Kazuhiro Ohi, Lucila Ohno-Machado, Karin A. Oien, Akinyemi I. Ojesina, Hidenori Ojima, Takuji Okusaka, Larsson Omberg, Choon Kiat Ong, Stephan Ossowski, German Ott, B. F. Francis Ouellette, 
Christine P’ng, Marta Paczkowska, Salvatore Paiella, Chawalit Pairojkul, Marina Pajic, Qiang Pan-Hammarström, Elli Papaemmanuil, Irene Papatheodorou, Nagarajan Paramasivam, Ji Wan Park, Joong-Won Park, Keunchil Park, Kiejung Park, Peter J. Park, Joel S. Parker, Simon L. Parsons, Harvey Pass, Danielle Pasternack, Alessandro Pastore, Ann-Marie Patch, Iris Pauporté, Antonio Pea, John V. Pearson, Chandra Sekhar Pedamallu, Jakob Skou Pedersen, Paolo Pederzoli, Martin Peifer, Nathan A. Pennell, Charles M. Perou, Marc D. Perry, Gloria M. Petersen, Myron Peto, Nicholas Petrelli, Robert Petryszak, Stefan M. Pfister, Mark Phillips, Oriol Pich, Hilda A. Pickett, Todd D. Pihl, Nischalan Pillay, Sarah Pinder, Mark Pinese, Andreia V. Pinho, Esa Pitkänen, Xavier Pivot, Elena Piñeiro-Yáñez, Laura Planko, Christoph Plass, Paz Polak, Tirso Pons, Irinel Popescu, Olga Potapova, Aparna Prasad, Shaun R. Preston, Manuel Prinz, Antonia L. Pritchard, Stephenie D. Prokopec, Elena Provenzano, Xose S. Puente, Sonia Puig, Montserrat Puiggròs, Sergio Pulido-Tamayo, Gulietta M. Pupo, Colin A. Purdie, Michael C. Quinn, 
Raquel Rabionet, Janet S. Rader, Bernhard Radlwimmer, Petar Radovic, Benjamin Raeder, Keiran M. Raine, Manasa Ramakrishna, Kamna Ramakrishnan, Suresh Ramalingam, Benjamin J. Raphael, W. Kimryn Rathmell, Tobias Rausch, Guido Reifenberger, Jüri Reimand, Jorge Reis-Filho, Victor Reuter, Iker Reyes-Salazar, Matthew A. Reyna, Sheila M. Reynolds, Esther Rheinbay, Yasser Riazalhosseini, Andrea L. Richardson, Julia Richter, Matthew Ringel, Markus Ringnér, Yasushi Rino, Karsten Rippe, Jeffrey Roach, Lewis R. Roberts, Nicola D. Roberts, Steven A. Roberts, A. Gordon Robertson, Alan J. Robertson, Javier Bartolomé Rodriguez, Bernardo Rodriguez-Martin, F. Germán Rodríguez-González, Michael H. A. Roehrl, Marius Rohde, Hirofumi Rokutan, Gilles Romieu, Ilse Rooman, Tom Roques, Daniel Rosebrock, Mara Rosenberg, Philip C. Rosenstiel, Andreas Rosenwald, Edward W. Rowe, Romina Royo, Steven G. Rozen, Yulia Rubanova, Mark A. Rubin, Carlota Rubio-Perez, Vasilisa A. Rudneva, Borislav C. Rusev, Andrea Ruzzenente, Gunnar Rätsch, 
Radhakrishnan Sabarinathan, Veronica Y. Sabelnykova, Sara Sadeghi, S. Cenk Sahinalp, Natalie Saini, Mihoko Saito-Adachi, Gordon Saksena, Adriana Salcedo, Roberto Salgado, Leonidas Salichos, Richard Sallari, Charles Saller, Roberto Salvia, Michelle Sam, Jaswinder S. Samra, Francisco Sanchez-Vega, Chris Sander, Grant Sanders, Rajiv Sarin, Iman Sarrafi, Aya Sasaki-Oku, Torill Sauer, Guido Sauter, Robyn P. M. Saw, Maria Scardoni, Christopher J. Scarlett, Aldo Scarpa, Ghislaine Scelo, Dirk Schadendorf, Jacqueline E. Schein, Markus B. Schilhabel, Matthias Schlesner, Thorsten Schlomm, Heather K. Schmidt, Sarah-Jane Schramm, Stefan Schreiber, Nikolaus Schultz, Steven E. Schumacher, Roland F. Schwarz, Richard A. Scolyer, David Scott, Ralph Scully, Raja Seethala, Ayellet V. Segre, Iris Selander, Colin A. Semple, Yasin Senbabaoglu, Subhajit Sengupta, Elisabetta Sereni, Stefano Serra, Dennis C. Sgroi, Mark Shackleton, Nimish C. Shah, Sagedeh Shahabi, Catherine A. Shang, Ping Shang, Ofer Shapira, Troy Shelton, Ciyue Shen, Hui Shen, Rebecca Shepherd, Ruian Shi, Yan Shi, Yu-Jia Shiah, Tatsuhiro Shibata, Juliann Shih, Eigo Shimizu, Kiyo Shimizu, Seung Jun Shin, Yuichi Shiraishi, Tal Shmaya, Ilya Shmulevich, Solomon I. Shorser, Charles Short, Raunak Shrestha, Suyash S. Shringarpure, Craig Shriver, Shimin Shuai, Nikos Sidiropoulos, Reiner Siebert, Anieta M. Sieuwerts, Lina Sieverling, Sabina Signoretti, Katarzyna O. Sikora, Michele Simbolo, Ronald Simon, Janae V. Simons, Jared T. Simpson, Peter T. Simpson, Samuel Singer, Nasa Sinnott-Armstrong, Payal Sipahimalani, Tara J. Skelly, Marcel Smid, Jaclyn Smith, Karen Smith-McCune, Nicholas D. Socci, Heidi J. Sofia, Matthew G. Soloway, Lei Song, Anil K. Sood, Sharmila Sothi, Christos Sotiriou, Cameron M. Soulette, Paul N. Span, Paul T. Spellman, Nicola Sperandio, Andrew J. Spillane, Oliver Spiro, Jonathan Spring, Johan Staaf, Peter F. Stadler, Peter Staib, Stefan G. Stark, Lucy Stebbings, Ólafur Andri Stefánsson, Oliver Stegle, Lincoln D. Stein, Alasdair Stenhouse, Chip Stewart, Stephan Stilgenbauer, Miranda D. Stobbe, Michael R. Stratton, Jonathan R. Stretch, Adam J. Struck, Joshua M. Stuart, Henk G. Stunnenberg, Hong Su, Xiaoping Su, Ren X. Sun, Stephanie Sungalee, Hana Susak, Akihiro Suzuki, Fred Sweep, Monika Szczepanowski, Holger Sültmann, 
Takashi Yugawa, Angela Tam, David Tamborero, Benita Kiat Tee Tan, Donghui Tan, Patrick Tan, Hiroko Tanaka, Hirokazu Taniguchi, Tomas J. Tanskanen, Maxime Tarabichi, Roy Tarnuzzer, Patrick Tarpey, Morgan L. Taschuk, Kenji Tatsuno, Simon Tavaré, Darrin F. Taylor, Amaro Taylor-Weiner, Jon W. Teague, Bin Tean Teh, Varsha Tembe, Javier Temes, Kevin Thai, Sarah P. Thayer, Nina Thiessen, Gilles Thomas, Sarah Thomas, Alan Thompson, Alastair M. Thompson, John F. F. Thompson, R. Houston Thompson, Heather Thorne, Leigh B. Thorne, Adrian Thorogood, Grace Tiao, Nebojsa Tijanic, Lee E. Timms, Roberto Tirabosco, Marta Tojo, Stefania Tommasi, Christopher W. Toon, Umut H. Toprak, David Torrents, Giampaolo Tortora, Jörg Tost, Yasushi Totoki, David Townend, Nadia Traficante, Isabelle Treilleux, Jean-Rémi Trotta, Lorenz H. P. Trümper, Ming Tsao, Tatsuhiko Tsunoda, Jose M. C. Tubio, Olga Tucker, Richard Turkington, Daniel J. Turner, Andrew Tutt, Masaki Ueno, Naoto T. Ueno, 
Christopher Umbricht, Husen M. Umer, Timothy J. Underwood, Lara Urban, Tomoko Urushidate, Tetsuo Ushiku, Liis Uusküla-Reimand, Alfonso Valencia, David J. Van Den Berg, Steven Van Laere, Peter Van Loo, Erwin G. Van Meir, Gert G. Van Den Eynden, Theodorus Van Der Kwast, Naveen Vasudev, Miguel Vazquez, Ravikiran Vedururu, Umadevi Veluvolu, Shankar Vembu, Lieven P. C. Verbeke, Peter Vermeulen, Clare Verrill, Alain Viari, David Vicente, Caterina Vicentini, K. VijayRaghavan, Juris Viksna, Ricardo E. Vilain, Izar Villasante, Anne Vincent-Salomon, Tapio Visakorpi, Douglas Voet, Paresh Vyas, Ignacio Vázquez-García, Nick M. Waddell, Nicola Waddell, Claes Wadelius, Lina Wadi, Rabea Wagener, Jeremiah A. Wala, Jian Wang, Jiayin Wang, Linghua Wang, Qi Wang, Wenyi Wang, Yumeng Wang, Zhining Wang, Paul M. Waring, Hans-Jörg Warnatz, Jonathan Warrell, Anne Y. Warren, Sebastian M. Waszak, David C. Wedge, Dieter Weichenhan, Paul Weinberger, John N. Weinstein, Joachim Weischenfeldt, Daniel J. Weisenberger, Ian Welch, Michael C. Wendl, Johannes Werner, Justin P. Whalley, David A. Wheeler, Hayley C. Whitaker, Dennis Wigle, 
Matthew D. Wilkerson, Ashley Williams, James S. Wilmott, Gavin W. Wilson, Julie M. Wilson, Richard K. Wilson, Boris Winterhoff, Jeffrey A. Wintersinger, Maciej Wiznerowicz, Stephan Wolf, Bernice H. Wong, Tina Wong, Winghing Wong, Youngchoon Woo, Scott Wood, Bradly G. Wouters, Adam J. Wright, Derek W. Wright, Mark H. Wright, Chin-Lee Wu, Dai-Ying Wu, Guanming Wu, Jianmin Wu, Kui Wu, Yang Wu, Zhenggang Wu, Liu Xi, Tian Xia, Qian Xiang, Xiao Xiao, Rui Xing, Heng Xiong, Qinying Xu, Yanxun Xu, Hong Xue, Shinichi Yachida, Sergei Yakneen, Rui Yamaguchi, Takafumi N. Yamaguchi, Masakazu Yamamoto, Shogo Yamamoto, Hiroki Yamaue, Fan Yang, Huanming Yang, Jean Y. Yang, Liming Yang, Lixing Yang, Shanlin Yang, Tsun-Po Yang, Yang Yang, Xiaotong Yao, Marie-Laure Yaspo, Lucy Yates, Christina Yau, Chen Ye, Kai Ye, Venkata D. Yellapantula, Christopher J. Yoon, Sung-Soo Yoon, Fouad Yousif, Jun Yu, Kaixian Yu, Willie Yu, Yingyan Yu, Ke Yuan, Yuan Yuan, Denis Yuen, Christina K. Yung, Olga Zaikova, 
Jorge Zamora, Marc Zapatka, Jean C. Zenklusen, Thorsten Zenz, Nikolajs Zeps, Cheng-Zhong Zhang, Fan Zhang, Hailei Zhang, Hongwei Zhang, Hongxin Zhang, Jiashan Zhang, Jing Zhang, Junjun Zhang, Xiuqing Zhang, Xuanping Zhang, Yan Zhang, Zemin Zhang, Zhongming Zhao, Liangtao Zheng, Xiuqing Zheng, Wanding Zhou, Yong Zhou, Bin Zhu, Hongtu Zhu, Jingchun Zhu, Shida Zhu, Lihua Zou, Xueqing Zou, Anna deFazio, Nicholas Van As, Carolien H. M. Van Deurzen, Marc J. Van De Vijver, L. Van’T Veer, Christian Von Mering</small> (2020):  
**Pan-cancer analysis of whole genomes**.  
*Nature*  **578**(7793)  
<https://doi.org/10.1038/s41586-020-1969-6>

\[Ison 2013\]
Jon Ison, Matúš Kalaš, Inge Jonassen, Dan Bolser, Mahmut Uludag, Hamish McWilliam, James Malone, Rodrigo Lopez, Steve Pettifer, Peter Rice (2013):  
**EDAM: An ontology of bioinformatics operations, types of data and identifiers, topics and formats**.  
*Bioinformatics* **29**(10)  
<https://doi.org/10.1093/bioinformatics/btt113>

\[Ison 2019\]
Jon Ison, Hans Ienasescu, Piotr Chmura, Emil Rydza, Hervé Ménager, Matúš Kalaš, Veit Schwämmle, Björn Grüning, Niall Beard, Rodrigo Lopez, Severine Duvaud, Heinz Stockinger, Bengt Persson, Radka Svobodová Vařeková, Tomáš Raček, Jiří Vondrášek, Hedi Peterson, Ahto Salumets, Inge Jonassen, Rob Hooft, Tommi Nyrönen, Alfonso Valencia, Salvador Capella, Josep Gelpí, Federico Zambelli, Babis Savakis, Brane Leskošek, Kristoffer Rapacki, Christophe Blanchet, Rafael Jimenez, Arlindo Oliveira, Gert Vriend, Olivier Collin, Jacques Van Helden, Peter Løngreen, Søren Brunak (2019):  
**The bio.tools registry of software tools and data resources for the life sciences**.  
*Genome Biology* **20**(1)  
<https://doi.org/10.1186/s13059-019-1772-6>

\[Jones 2024\]
Matthew B. Jones, Carl Boettiger, Abby Cabunoc Mayes, Arfon Smith, Morane Gruenpeter, Valentin Lorentz, Thomas Morrell, Daniel Garijo, Peter Slaughter, Kyle Niemeyer, Yolanda Gil, Martin Fenner, Krzysztof Nowak, Mark Hahnel, Luke Coy, Alice Allen, Mercè Crosas, Ashley Sands, Neil Chue Hong, Patricia Cruse, Daniel S. Katz, Carole Goble, Bryce Mecum, Alejandra Gonzalez-Beltran, Noam Ross (2024):  
**CodeMeta: An exchange schema for software metadata**  
<https://w3id.org/codemeta/v3.0> (accessed 7 August 2024)

\[Köster 2023\]
Johannes Köster, Felix Mölder, David Laehnemann, Christopher Schröder, Till Hartmann, Jan Forster, User-Tq (2023):  
**Snakemake-workflows/dna-seq-varlociraptor: V5.0.2**  
<https://doi.org/10.5281/zenodo.8421328>

\[Lamothe 2023\]
Lucie Lamothe, Jennifer Rugaard Bregndahl Jensen, Hans Ienasescu, Ove Johan Ragnar Gustafsson, Alban Gaignard, Dmitry Repchevsky, Radka Svobodová, Tomáš Raček, Matej Antol, Magnus Palmblad, Matúš Kalaš, Hervé Menager (2023):  
**An evaluation of EDAM coverage in the Tools Ecosystem and prototype integration of Galaxy and WorkflowHub systems**.    
_BioHackrXiv_  
<https://doi.org/10.37044/osf.io/79kje>

\[Larivière 2024\]
Delphine Larivière, Linelle Abueg, Nadolina Brajuka, Cristóbal Gallardo-Alba, Bjorn Grüning, Byung June Ko, Alex Ostrovsky, Marc Palmada-Flores, Brandon D. Pickett, Keon Rabbani, Agostinho Antunes, Jennifer R. Balacco, Mark J. P. Chaisson, Haoyu Cheng, Joanna Collins, Melanie Couture, Alexandra Denisova, Olivier Fedrigo, Guido Roberto Gallo, Alice Maria Giani, Grenville MacDonald Gooder, Kathleen Horan, Nivesh Jain, Cassidy Johnson, Heebal Kim, Chul Lee, Tomas Marques-Bonet, Brian O’Toole, Arang Rhie, Simona Secomandi, Marcella Sozzoni, Tatiana Tilley, Marcela Uliano-Silva, Marius Van Den Beek, Robert W. Williams, Robert M. Waterhouse, Adam M. Phillippy, Erich D. Jarvis, Michael C. Schatz, Anton Nekrutenko, Giulio Formenti (2024):  
**Scalable, accessible and reproducible reference genome assembly and evaluation in Galaxy**.  
*Nature Biotechnology* **42**(3)  
<https://doi.org/10.1038/s41587-023-02100-3>

\[Maier 2021\]
Wolfgang Maier, Simon Bray, Marius Van Den Beek, Dave Bouvier, Nathan Coraor, Milad Miladi, Babita Singh, Jordi Rambla De Argila, Dannon Baker, Nathan Roach, Simon Gladman, Frederik Coppens, Darren P. Martin, Andrew Lonie, Björn Grüning, Sergei L. Kosakovsky Pond, Anton Nekrutenko (2021):  
**Ready-to-use public infrastructure for global SARS-CoV-2 monitoring**.  
*Nature Biotechnology* **39**(10)  
<https://doi.org/10.1038/s41587-021-01069-1>

\[Mazzoni 2023\]
Camila J. Mazzoni, Claudio Ciofi, Robert M. Waterhouse (2023):  
**Biodiversity: An atlas of European reference genomes**.  
*Nature* **619**(7969)  
<https://doi.org/10.1038/d41586-023-02229-w>

\[McClure 2020\]
James E. McClure, Junqi Yin, Ryan T. Armstrong, Ketan C. Maheshwari, Sean Wilkinson, Lucas Vlcek, Ying Da Wang, Mark A. Berrill, Mark Rivers (2020):  
**Toward Real-Time Analysis of Synchrotron Micro-Tomography Data**: Accelerating Experimental Workflows with AI and HPC.  
*Driving Scientific and Engineering Discoveries Through the Convergence of HPC, Big Data and AI*  
<https://doi.org/10.1007/978-3-030-63393-6_15>

\[Mölder 2021\]
Felix Mölder, Kim Philipp Jablonski, Brice Letcher, Michael B. Hall, Christopher H. Tomkins-Tinch, Vanessa Sochat, Jan Forster, Soohyun Lee, Sven O. Twardziok, Alexander Kanitz, Andreas Wilm, Manuel Holtgrewe, Sven Rahmann, Sven Nahnsen, Johannes Köster (2021):  
**Sustainable data analysis with Snakemake**.  
*F1000Research* **10** 
<https://doi.org/10.12688/f1000research.29032.2>

\[Owen 2024\]
Stuart Owen, Finn Bacall, Lihua, maggy128, Vahid Kiani, Alan R. Williams, Xiaoming Hu, Kevin De Pelseneer, hleonov, Francisco Herrerías-Azcué, Alain Becam, Aitor Apaolaza, Tomasz Zielinski, Niall Beard, Robert Haines, Sonja Mathias, Vahid Kiani, Jeremy, Stian Soiland-Reyes, Quyen Nguyen, Christoph Beger, Eilidh Troup, Katrin Leinweber, Wolfgang Müller, Anthony Bretaudeau, Benjamin Mulelid, Arthur Rosendahl, Josh Kalderimis, susca (2024):  
**Seek4science/seek: FAIRDOM-SEEK v1.15.0**  
_Zenodo_
<https://doi.org/10.5281/zenodo.11209855>

\[Patel 2022\]
Ria Patel, Brandan Roachell, Silvina Caino-Lores, Ross Ketron, Jacob Leonard, Nigel Tan, Duncan Brown, Ewa Deelman, Michela Taufer (2022):  
**Reproducibility of the First Image of a Black Hole in the Galaxy M87 from the Event Horizon Telescope (EHT) Collaboration**  
<https://doi.org/10.48550/ARXIV.2205.10267>

\[Pico 2022\]
Eva Martı́n del Pico, Josep Lluis Gelpi, Salvador Capella-Gutiérrez (2022):  
**FAIRsoft - a practical implementation of fair principles for research software**.  
*bioRxiv*  
<https://doi.org/10.1101/2022.05.04.490563>

\[R 2024\]
R. Core Team (2024):  
**R: A Language and Environment for Statistical Computing**.    
<https://www.r-project.org/> (accessed 12 June 2024)

\[Reiter 2021\]
Taylor Reiter, Phillip T. Brooks, Luiz Irber, Shannon E. K. Joslin, Charles M. Reid, Camille Scott, C. Titus Brown, N. Tessa Pierce-Ward (2021):  
**Streamlining data-intensive biology with workflow systems**.  
*GigaScience* **10**(1)  
<https://doi.org/10.1093/gigascience/giaa140>

\[Roach 2024\]
Michael J. Roach, Sarah J. Beecroft, Kathie A. Mihindukulasuriya, Leran Wang, Anne Paredes, Luis Alberto Chica Cárdenas, Kara Henry-Cocks, Lais Farias Oliveira Lima, Elizabeth A. Dinsdale, Robert A. Edwards, Scott A. Handley (2024):  
**Hecatomb: An integrated software platform for viral metagenomics**.  
*GigaScience* **13** 
<https://doi.org/10.1093/gigascience/giae020>

\[Rosa-Trevín 2016\]
J. M. De La Rosa-Trevín, A. Quintana, L. Del Cano, A. Zaldívar, I. Foche, J. Gutiérrez, J. Gómez-Blanco, J. Burguet-Castell, J. Cuenca-Alba, V. Abrishami, J. Vargas, J. Otón, G. Sharov, J. L. Vilas, J. Navas, P. Conesa, M. Kazemi, R. Marabini, C. O. S. Sorzano, J. M. Carazo (2016):  
**Scipion: A software framework toward integration, reproducibility and validation in 3D electron microscopy**.  
*Journal of Structural Biology* **195**(1)  
<https://doi.org/10.1016/j.jsb.2016.04.010>

\[Rosnet 2024\]
Thomas Rosnet, Alban Gaignard, Marie-Dominique Devignes, Sahar Frikha (2024):  
**FAIR-checker**  
<https://github.com/IFB-ElixirFr/fair-checker>

\[Samaha 2023\]
Johan Gustafsson & Georgina Samaha (2023):  
**WORKSHOP: Make your bioinformatics workflows findable and citable**  
<https://doi.org/10.5281/zenodo.7787488>

\[Soiland-Reyes 2022\]
Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble (2022):  
**Packaging research artefacts with RO-Crate**.  
*Data Science* **5**(2)  
<https://doi.org/10.3233/DS-210053>

\[Soiland-Reyes 2024a\]
Stian Soiland-Reyes, Eli Chadwick, Finn Bacall, José M. Fernández, Björn Grüning, Hakan Bayındır (2024):  
**EuroScienceGateway D2.1: Reproducible FAIR Digital Objects for Workflows**  
<https://doi.org/10.5281/zenodo.13225792>

\[Soiland-Reyes 2024b\]
Stian Soiland-Reyes, Carole Goble, Finn Bacall, Johan Gustafsson, Rafael Andrade Buono (2024):  
**A guide to using WorkflowHub**  
<https://doi.org/10.48546/WORKFLOWHUB.SOP.13.4> (accessed 11 June 2024)

\[Soiland-Reyes 2024c\]
Stian Soiland-Reyes (2024):  
**BioDT Guide to using WorkflowHub**  
<https://doi.org/10.48546/WORKFLOWHUB.SOP.14.1> (accessed 8 July 2024)

\[Soiland-Reyes 2024d\]
Stian Soiland-Reyes (2024):  
**The BGE guide to using WorkflowHub**  
<https://doi.org/10.48546/WORKFLOWHUB.SOP.15.1> (accessed 8 July 2024)

\[Stevens 2022\]
Frankie Stevens (2022):  
**Understanding how researchers find research software for research practice**.   
_Zenodo_  
<https://doi.org/10.5281/zenodo.7340034>

\[Suetake 2022\]
Hirotaka Suetake, Tomoya Tanjo, Manabu Ishii, Bruno P. Kinoshita, Takeshi Fujino, Tsuyoshi Hachiya, Yuichi Kodama, Takatomo Fujisawa, Osamu Ogasawara, Atsushi Shimizu, Masanori Arita, Tsukasa Fukusato, Takeo Igarashi, Tazro Ohta (2022):  
**Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics**.  
*F1000Research* **11** 
<https://doi.org/10.12688/f1000research.122924.1>

\[Syme 2024\]
Luke Silver & Anna Syme (2024):  
**Find transcripts - TSI**  
<https://doi.org/10.48546/WORKFLOWHUB.WORKFLOW.877.1>

\[Tejedor 2017\]
Enric Tejedor, Yolanda Becerra, Guillem Alomar, Anna Queralt, Rosa M. Badia, Jordi Torres, Toni Cortes, Jesús Labarta (2017):  
**PyCOMPSs: Parallel computational workflows in Python**.  
*The International Journal of High Performance Computing Applications* **31**(1)  
<https://doi.org/10.1177/1094342015594678>

\[Tommaso 2017\]
Paolo Di Tommaso, Maria Chatzou, Evan W. Floden, Pablo Prieto Barja, Emilio Palumbo, Cedric Notredame (2017):  
**Nextflow enables reproducible computational workflows**.  
*Nature Biotechnology* **35**(4)  
<https://doi.org/10.1038/nbt.3820>

\[Wilkinson 2016\]
Mark D. Wilkinson, Michel Dumontier, IJsbrand Jan Aalbersberg, Gabrielle Appleton, Myles Axton, Arie Baak, Niklas Blomberg, Jan-Willem Boiten, Luiz Bonino Da Silva Santos, Philip E. Bourne, Jildau Bouwman, Anthony J. Brookes, Tim Clark, Mercè Crosas, Ingrid Dillo, Olivier Dumon, Scott Edmunds, Chris T. Evelo, Richard Finkers, Alejandra Gonzalez-Beltran, Alasdair J. G. Gray, Paul Groth, Carole Goble, Jeffrey S. Grethe, Jaap Heringa, Peter A. C. ’T Hoen, Rob Hooft, Tobias Kuhn, Ruben Kok, Joost Kok, Scott J. Lusher, Maryann E. Martone, Albert Mons, Abel L. Packer, Bengt Persson, Philippe Rocca-Serra, Marco Roos, Rene Van Schaik, Susanna-Assunta Sansone, Erik Schultes, Thierry Sengstag, Ted Slater, George Strawn, Morris A. Swertz, Mark Thompson, Johan Van Der Lei, Erik Van Mulligen, Jan Velterop, Andra Waagmeester, Peter Wittenburg, Katherine Wolstencroft, Jun Zhao, Barend Mons (2016):  
**The FAIR Guiding Principles for scientific data management and stewardship**.  
*Scientific Data* **3**(1)  
<https://doi.org/10.1038/sdata.2016.18>

\[Wilkinson 2022\]
Sean R. Wilkinson, Greg Eisenhauer, Anuj J. Kapadia, Kathryn Knight, Jeremy Logan, Patrick Widener, Matthew Wolf (2022):  
**F\*\*\* workflows: When parts of FAIR are missing**.  
*2022 IEEE 18th International Conference on e-Science (e-Science)*   
<https://doi.org/10.1109/eScience55777.2022.00090>

\[Wilkinson 2024\]
Sean R. Wilkinson, Meznah Aloqalaa, Khalid Belhajjame, Michael R. Crusoe, Bruno de Paula Kinoshita, Luiz Gadelha, Daniel Garijo, Ove Johan Ragnar Gustafsson, Nick Juty, Sehrish Kanwal, Farah Zaib Khan, Johannes Köster, Karsten Peters-von Gehlen, Line Pouchard, Randy K. Rannow, Stian Soiland-Reyes, Nicola Soranzo, Shoaib Sufi, Ziheng Sun, Baiba Vilne, Merridee A. Wouters, Denis Yuen, Carole Goble (2024):  
**Applying the FAIR Principles to Computational Workflows**  
<https://doi.org/10.48550/arXiv.2410.03490>

\[Wolstencroft 2017\]
Katherine Wolstencroft, Olga Krebs, Jacky L. Snoep, Natalie J. Stanford, Finn Bacall, Martin Golebiewski, Rostyk Kuzyakiv, Quyen Nguyen, Stuart Owen, Stian Soiland-Reyes, Jakub Straszewski, David D. van Niekerk, Alan R. Williams, Lars Malmström, Bernd Rinn, Wolfgang Müller, Carole Goble (2017):  
**FAIRDOMHub: A repository and collaboration environment for sharing systems biology research**.    
*Nucleic Acids Research* **45**(D1)  
<https://doi.org/10.1093/nar/gkw1032>

\[Wratten 2021\]
Laura Wratten, Andreas Wilm, Jonathan Göke (2021):  
**Reproducible, scalable, and shareable analysis pipelines with bioinformatics workflow managers**.  
*Nature Methods* **18**(10)  
<https://doi.org/10.1038/s41592-021-01254-9>

\[Yuen 2021\]
Denis Yuen, Louise Cabansay, Andrew Duncan, Gary Luu, Gregory Hogue, Charles Overbeck, Natalie Perez, Walt Shands, David Steinberg, Chaz Reid, Nneka Olunwa, Richard Hansen, Elizabeth Sheets, Ash O’Farrell, Kim Cullion, Brian D. O’Connor, Benedict Paten, Lincoln Stein (2021):  
**The Dockstore: Enhancing a community platform for sharing reproducible and accessible computational protocols**.  
*Nucleic Acids Research* **49**(W1)  
<https://doi.org/10.1093/nar/gkab346>



[Amstutz 2016]: https://doi.org/10.6084/M9.FIGSHARE.3115156.V2 "Common Workflow Language, v1.0"
[Amstutz 2024]: https://s.apache.org/existing-workflow-systems "Existing Workflow systems."
[Baker 2020]: https://doi.org/10.1371/journal.ppat.1008643 "No more business as usual: Agile and effective responses to emerging pathogen threats require open data and open analytics"
[Barker 2022]: https://doi.org/10.1038/s41597-022-01710-x "Introducing the FAIR Principles for research software"
[Boer 1991]: https://ir.cwi.nl/pub/18204 "Interactively testing remote servers using the Python programming language"
[Bray 2023]: https://doi.org/10.1101/gr.276963.122 "The Planemo toolkit for developing, deploying, and executing scientific data analyses in Galaxy and beyond"
[Capella-Gutierrez 2017]: https://doi.org/10.1101/181677 "Lessons Learned: Recommendations for Establishing Critical Periodic Scientific Benchmarking"
[Christiansen 2024]: https://doi.org/10.5281/zenodo.13626350 "Australian BioCommons Strategic Plan 2023 - 2028"
[Cohen-Boulakia 2017]: https://doi.org/10.1016/j.future.2017.01.012 "Scientific workflows for computational reproducibility in the life sciences"
[Coin 2024]: https://doi.org/10.1093/gigascience/giae010 "Pangenome databases improve host removal and mycobacteria classification from clinical metagenomic data"
[Community 2024]: https://doi.org/10.1093/nar/gkae410 "The Galaxy platform for accessible, reproducible, and collaborative data analyses"
[Courbebaisse 2023]: https://doi.org/10.5281/zenodo.8324828 "Research Software Lifecycle"
[Crusoe 2022]: https://doi.org/10.1145/3486897 "Methods included: Standardizing computational reuse and portability with the Common Workflow Language"
[da Silva 2023]: https://doi.org/10.5281/zenodo.7750670 "Workflows Community Summit 2022: A Roadmap Revolution"
[Druskat 2021]: https://doi.org/10.5281/zenodo.5171937 "Citation File Format"
[ELIXIR 2024]: https://doi.org/10.7490/F1000RESEARCH.1119751.1 "ELIXIR Annual Report 2023"
[Ewels 2020]: https://doi.org/10.1038/s41587-020-0439-x "The nf-core framework for community-curated bioinformatics pipelines"
[Fernández 2022]: https://doi.org/10.7490/F1000RESEARCH.1119198.1 "Secured and annotated execution of workflows with WfExS-backend"
[Freudling 2023]: https://doi.org/10.48550/ARXIV.2311.03822 "Adaptive Data Reduction Workflows for Astronomy – The ESO Data Processing System (EDPS)"
[Garijo 2022]: https://doi.org/10.7717/peerj-cs.1023 "Nine best practices for research software registries and repositories"
[Gil 2006]: https://doi.org/10.1109/E-SCIENCE.2006.261077 "Managing Large-Scale Scientific Workflows in Distributed Environments"
[Gil 2007]: https://doi.org/10.1109/MC.2007.421 "Examining the Challenges of Scientific Workflows"
[Gil 2009]: https://doi.org/https://doi.org/10.3233/SPR-2009-0261 "From data to knowledge to discoveries: Artificial intelligence and scientific workflows"
[Goble 2020]: https://doi.org/10.1162/dint_a_00033 "FAIR Computational Workflows"
[Goble 2021]: https://doi.org/10.5281/zenodo.4605654 "Implementing FAIR Digital Objects in the EOSC-Life Workflow Collaboratory"
[Goble 2022]: https://doi.org/10.7490/F1000RESEARCH.1118984.1 "WorkflowHub – a FAIR registry for workflows"
[Goble 2023]: https://doi.org/10.5281/zenodo.7886545 "EOSC-Life Implementation of a mechanism for publishing and sharing workflows across instances of the environment"
[Goble 2024a]: https://galaxyproject.org/news/2024-08-03-workflow-publisher-forum/ "WorkflowHub Publishers and Journal Forum"
[Goble 2024b]: https://doi.org/10.48546/WORKFLOWHUB.SOP.10.1 "The BY-COVID Guide to using WorkflowHub"
[Gray 2017]: https://iswc2017.semanticweb.org/paper-579/ "Bioschemas: From potato salad to protein annotation"
[Hambley 2024]: https://doi.org/10.5281/zenodo.13362051 "WorkflowHub Knowledge Graph"
[Hatos 2021]: https://doi.org/10.1093/database/baab019 "APICURON: A database to credit and acknowledge the work of biocurators"
[Hiltemann 2023]: https://doi.org/10.1371/journal.pcbi.1010752 "Galaxy Training"
[Huerta 2023]: https://doi.org/10.1038/s41597-023-02298-6 "FAIR for AI: An interdisciplinary and international community building perspective"
[ICGC/TCGA 2020]: https://doi.org/10.1038/s41586-020-1969-6 "Pan-cancer analysis of whole genomes"
[Ison 2013]: https://doi.org/10.1093/bioinformatics/btt113 "EDAM: An ontology of bioinformatics operations, types of data and identifiers, topics and formats"
[Ison 2019]: https://doi.org/10.1186/s13059-019-1772-6 "The bio.tools registry of software tools and data resources for the life sciences"
[Jones 2024]: https://w3id.org/codemeta/v3.0 "CodeMeta: An exchange schema for software metadata"
[Köster 2023]: https://doi.org/10.5281/zenodo.8421328 "Snakemake-workflows/dna-seq-varlociraptor: V5.0.2"
[Lamothe 2023]: https://doi.org/10.37044/osf.io/79kje "An evaluation of EDAM coverage in the Tools Ecosystem and prototype integration of Galaxy and WorkflowHub systems"
[Larivière 2024]: https://doi.org/10.1038/s41587-023-02100-3 "Scalable, accessible and reproducible reference genome assembly and evaluation in Galaxy"
[Maier 2021]: https://doi.org/10.1038/s41587-021-01069-1 "Ready-to-use public infrastructure for global SARS-CoV-2 monitoring"
[Mazzoni 2023]: https://doi.org/10.1038/d41586-023-02229-w "Biodiversity: An atlas of European reference genomes"
[McClure 2020]: https://doi.org/10.1007/978-3-030-63393-6_15 "Toward Real-Time Analysis of Synchrotron Micro-Tomography Data"
[Mölder 2021]: https://doi.org/10.12688/f1000research.29032.2 "Sustainable data analysis with Snakemake"
[Owen 2024]: https://doi.org/10.5281/zenodo.11209855 "Seek4science/seek: FAIRDOM-SEEK v1.15.0"
[Patel 2022]: https://doi.org/10.48550/ARXIV.2205.10267 "Reproducibility of the First Image of a Black Hole in the Galaxy M87 from the Event Horizon Telescope (EHT) Collaboration"
[Pico 2022]: https://doi.org/10.1101/2022.05.04.490563 "FAIRsoft - a practical implementation of fair principles for research software"
[R 2024]: https://www.r-project.org/ "R: A Language and Environment for Statistical Computing"
[Reiter 2021]: https://doi.org/10.1093/gigascience/giaa140 "Streamlining data-intensive biology with workflow systems"
[Roach 2024]: https://doi.org/10.1093/gigascience/giae020 "Hecatomb: An integrated software platform for viral metagenomics"
[Rosa-Trevín 2016]: https://doi.org/10.1016/j.jsb.2016.04.010 "Scipion: A software framework toward integration, reproducibility and validation in 3D electron microscopy"
[Rosnet 2024]: https://github.com/IFB-ElixirFr/fair-checker "FAIR-checker"
[Samaha 2023]: https://doi.org/10.5281/zenodo.7787488 "WORKSHOP: Make your bioinformatics workflows findable and citable"
[Smedt 2020]: https://doi.org/10.3390/publications8020021 "FAIR Digital Objects for Science: From Data Pieces to Actionable Knowledge Units"
[Soiland-Reyes 2022]: https://doi.org/10.3233/DS-210053 "Packaging research artefacts with RO-Crate"
[Soiland-Reyes 2024a]: https://doi.org/10.5281/zenodo.13225792 "EuroScienceGateway D2.1: Reproducible FAIR Digital Objects for Workflows"
[Soiland-Reyes 2024b]: https://doi.org/10.48546/WORKFLOWHUB.SOP.13.4 "A guide to using WorkflowHub"
[Soiland-Reyes 2024c]: https://doi.org/10.48546/WORKFLOWHUB.SOP.14.1 "BioDT Guide to using WorkflowHub"
[Soiland-Reyes 2024d]: https://doi.org/10.48546/WORKFLOWHUB.SOP.15.1 "The BGE guide to using WorkflowHub"
[Stevens 2022]: <https://doi.org/10.5281/zenodo.7340034> "Understanding how researchers find research software for research practice"
[Suetake 2022]: https://doi.org/10.12688/f1000research.122924.1 "Sapporo: A workflow execution service that encourages the reuse of workflows in various languages in bioinformatics"
[Syme 2024]: https://doi.org/10.48546/WORKFLOWHUB.WORKFLOW.877.1 "Find transcripts - TSI"
[Tejedor 2017]: https://doi.org/10.1177/1094342015594678 "PyCOMPSs: Parallel computational workflows in Python"
[Tommaso 2017]: https://doi.org/10.1038/nbt.3820 "Nextflow enables reproducible computational workflows"
[Wilkinson 2016]: https://doi.org/10.1038/sdata.2016.18 "The FAIR Guiding Principles for scientific data management and stewardship"
[Wilkinson 2022]: https://doi.org/10.1109/eScience55777.2022.00090 "" F*** workflows"
[Wilkinson 2024]: https://doi.org/10.48550/arXiv.2410.03490 "Applying the FAIR Principles to Computational Workflows"
[Wolstencroft 2017]: https://doi.org/10.1093/nar/gkw1032 "FAIRDOMHub: A repository and collaboration environment for sharing systems biology research"
[Wratten 2021]: https://doi.org/10.1038/s41592-021-01254-9 "Reproducible, scalable, and shareable analysis pipelines with bioinformatics workflow managers"
[Yuen 2021]: https://doi.org/10.1093/nar/gkab346 "The Dockstore: Enhancing a community platform for sharing reproducible and accessible computational protocols"
