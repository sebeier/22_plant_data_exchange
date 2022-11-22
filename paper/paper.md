---
title: 'BioHackEU22 Project 22: Plant data exchange and standard interoperability'
title_short: 'BioHackEU22 #22: Plants'
tags:
  - MIAPPE
  - ISA
  - RO-Crate
  - ARC
  - Bioschemas
  - BrAPI
  - Plants
  - SWATE
authors:
  - name: Daniel Arend
    orcid: 0000-0002-2455-5938
    affiliation: 1
  - name: Sebastian Beier
    orcid: 0000-0002-2177-8781
    affiliation: 2
  - name: Erwan Le Floch
    orcid: 0000-0002-1010-6859
    affiliation: 3
  - name: Laurent Bouri
    orcid: 0000-0002-2297-1559
    affiliation: 3
  - name: Marco Brandizi
    orcid: 0000-0002-5427-2496
    affiliation: 4
  - name: Cyril Pommier
    orcid: 0000-0002-9040-8733
    affiliation: 3
  - name: Timo Mühlhaus
    orcid: 0000-0003-3925-6778
    affiliation: 5
  - name: Philippe Rocca-Serra
    orcid: 0000-0001-9853-5668
    affiliation: 6
affiliations:
  - name: Leibniz Institute for Plant Genetics and Crop Plant Research (IPK) Gatersleben, Germany
    index: 1
  - name: Forschungszentrum Jülich GmbH, Germany
    index: 2
  - name: Université Paris-Saclay, INRAE, URGI, France
    index: 3
  - name: Rothamsted Research, Harpenden, UK
    index: 4
  - name: Technical University Kaiserslautern, Germany
    index: 5
  - name: University of Oxford, UK
    index: 6
date: 10 November 2022
cito-bibliography: paper.bib
event: BH22EU
biohackathon_name: "BioHackathon Europe 2022"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Paris, France, 2022"
group: Project 22
git_url: https://github.com/sebeier/22_plant_data_exchange
authors_short: Daniel Arend \emph{et al.}
---


# Introduction

The overall goal of this year's BioHackathon Europe project, initiated by the ELIXIR Plant Sciences Community, was to improve shared plant data standards in terms of their interoperability. Several technologies and data formats for plant science have already been created in the past. These include the metadata standard [MIAPPE](https://www.miappe.org/) (Minimal Information on a Plant Phenotyping Experiment), which can define a phenotyping experiment in its completeness [@citesAsAuthority:Papoutsoglou2020]. A particularly noteworthy part of MIAPPE is the way biological samples are described. Not only is the exact taxonomic name recorded here, but also information about the lineage, passport data, the developmental stage and the anatomical entity from which the sample was obtained. The representation in file form for MIAPPE can vary, but a common way is via tables. One often used solution is the [ISA framework](https://isa-tools.org/format/specification.html/) (Investigation-Study-Assay), either as ISA-tab or ISA JSON [@citesAsAuthority:Rocca_Serra2010]. For web resources, such as data warehouses and databases, the Breeding API [BrAPI](https://www.brapi.org/) has been created, which is fully MIAPPE-compliant [@citesAsAuthority:Selby2019]. This allows data to be retrieved and transferred programmatically via RESTful services. In order to make plant experimental datasets findable, websites in which such datasets are described can be annotated using Schema.org. Unfortunately, Schema.org does not provide domain-specific keywords, but there are several projects that extend Schema.org. For the life sciences this is [Bioschemas](https://www.bioschemas.org/) [@citesAsAuthority:gray2017]. MIAPPE is still not yet fully supported by Bioschemas. All these different options provide a broad basis for representing phenomics datasets and the possibility to store them. When it comes to linking phenomics with other data domains, e.g. omics-based data, there are still significant shortcomings and hardly any methods to integrate data from these data domains.

During the ELIXIR BioHackathon Europe 2021 first groundwork had been established to fully map Bioschemas to MIAPPE. Certain fields were still under discussion because it was not possible to unambiously map every field. A desired outcome of the BioHackathon 2022 was the completed and finalised mapping between MIAPPE and Bioschemas.

# ISA

The open source ISA framework helps plant science to manage an increasingly diverse range of experiments using one or a combination of multiple technologies. The framework is centered around the three entities Investigation (the project), Study (the experimental setup) and Assay (the description of analytical measurements or transformation of data). The idea is that data models and serialisations (tabular, JSON and RDF) help experimentalists to provide a comprehensive description of the entire experimental metadata (sample characteristics, technology and protocols used, measurement types and data transformation, relationships between samples and data) so that the results and findings produced are reproducible and reusable by other scientists.

During the Hackathon it became apparent that an extension of ISA to support analytic or measurement results within the data model was urgently needed to support the MIAPPE use case. Assays usually only describe the process on how results were obtained and not the actual result values. Therefore, discussions led to two possible solutions which were added as pull request to the ISA github repository: 
1. Extend the assay tables to include measurement values. This should be avoided for larger number of results [(git)](https://github.com/ISA-tools/isa-api/issues/473).
2. Keep results in a separate file linked in the assay table [(git)](https://github.com/ISA-tools/isa-api/issues/475).


Within the DataPLANT consortium (https://www.nfdi4plants.de), which is part of the German [NFDI](https://www.nfdi.de/?lang=en) (National Research Data Infrastructure), the ISA model has been used extensively to describe all types of plant experiments. They propose a data structure that they call [ARC](https://nfdi4plants.org/nfdi4plants.knowledgebase/docs/implementation/AnnotatedResearchContext.html/) (annotated research context), which builds on the ISA structure and combines it with [git](https://git-scm.com/) and [CWL](https://www.commonwl.org/). This allows version control, long term reproducible workflows and complete user access and provenance. To store the experimental metadata, they have developed a tool based on MS Excel, which is available as a plug-in and is called [SWATE](https://nfdi4plants.org/nfdi4plants.knowledgebase/docs/implementation/Swate.html). The metadata is thus stored in Excel spreadsheets (.xlsx) and during the hackathon there was discussion about [formalising this representation of ISA](https://github.com/ISA-tools/isa-api/issues/474).

# RO-Crate

For simple and lightweight archiving and packaging, the scientific community has created the [RO-Crate](https://www.researchobject.org/ro-crate/) data standard. It is based on [Schema.org](https://www.schema.org/) markup annotations in [JSON-LD](https://json-ld.org/) and aims to make best practices for formal metadata description accessible and workable. In this context, an RO-Crate is a structured archive of all elements that have contributed to a research result, including their identifiers and origins.

RO-Crates based on ISA (either ISA JSON, ISA-Tab or ISA.xlsx) and have been intensively discussed for the data exchange of MIAPPE datasets during this BioHackathon. We recommend to create four RO-Crate profiles with a flat and disentangled ISA structure. This avoids nested data structures and grants direct access, which is necessary for tools, which can process the exposed metadata such as GALAXY or KnowledgeGraphs. 

As a rule of thumb the annotation schema used for the description of the dataset is more general at the top of the hierarchy, when possible more general terms should be preferred when describing fields or parameters.

**1. ISA-Investigation Profile:**
Description on the Investigation of the ISA only relying on Schema.org for type definitions. This enables to find and harvet the datasets, e.g. via Google Dataset Search. 

**2. ISA-Study Profile:**
Description on an individual Study of the ISA in question relying on [Bioschemas](https://bioschemas.org/) for type definitions (where possible).

**3. ISA-Assay Profile:** 
Description on an Assay of the ISA in question relying on ISA terminology.

**4. MIAPPE Profile:** 
Description of special MIAPPE related fields, not directly describable in Schema.org, Bioschemas, or ISA terms.

# Bioschemas

placeholder

# FAIR Cookbook Recipe "MIAPPE -> ISA"

During the discussions, we realised that several challenges related to the mapping of MIAPPE-compliant phenomic datasets to the ISA model have often caused confusion in their implementation in the past. In addition, some of the previously described mappings need to be formalised and concretised to help data producers and data curators ensure a consistent representation of the data. Therefore, we decided to write a FAIR cookbook recipe explaining how to describe common phenotypic studies in a MIAPPE-compliant way as an ISA dataset [@citesAsAuthority:rocca_serra_philippe_2022_6783564]. This can probably be a subsection or a mature variant of an "ISA" recipe. The basis for this recipe could be the existing description from the https://github.com/MIAPPE/ISA-Tab-for-plant-phenotyping repository. It already contains various sections for the different ISA components and needs only minor additions.

<!--
# Citation Typing Ontology annotation

You can use CiTO annotations, as explained in [this BioHackathon Europe 2021 write up](https://raw.githubusercontent.com/biohackrxiv/bhxiv-metadata/main/doc/elixir_biohackathon2021/paper.md) and [this CiTO Pilot](https://www.biomedcentral.com/collections/cito).
Using this template, you can cite an article and indicate why you cite that article, for instance DisGeNET-RDF [@citesAsAuthority:Queralt2016].

Possible CiTO typing annotation include:

* citesAsDataSource: when you point the reader to a source of data which may explain a claim
* usesDataFrom: when you reuse somehow (and elaborate on) the data in the cited entity
* usesMethodIn
* citesAsAuthority
* discusses
* extends
* agreesWith
* disagreesWith
-->
# Results
* Suggestion for ISA extention for full compatible MIAPPE mapping (validate & approve during BH Germany)
* &#8594; Implementation of extention in Q1 2023
* Suggestion for integration of ISA into RO-Crate by developing 4 corresponding profiles
* Plan to draft FAIR cookbook recipe for MIAPPE to ISA mapping
* &#8594; referenced on RDMKit and miappe.org

# Discussion

...

## Acknowledgements

This work was funded by ELIXIR, the research infrastructure for life-science data. Discussions and work were conducted during the ELIXIR BioHackathon 2022 in Paris, France.

## References
