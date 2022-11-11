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
    affiliation: 2
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
  - name: TODO
    index: 6
date: 10 November 2022
cito-bibliography: paper.bib
event: BH22EU
biohackathon_name: "BioHackathon Europe 2022"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Paris, France, 2022"
group: Project 22

git_url: https://github.com/sebeier/22_plant_data_exchange

<!-- This is the short authors description that is used at the bottom of the generated paper (typically the first two authors): -->

authors_short: First Author \emph{et al.}

---


# Introduction

The overall goal of this years project initiated by the ELIXIR plant community was the improvement of common plant data standards according to their interoperability. Several technologies have been already established in the past within BrAPI, MIAPPE and ISA for phenomics data. Nevertheless the linkage between phenomics and other omics data is still lacking.


<!-- This project will improve the integration of Plant data standards with important interoperability technologies. Indeed, some interoperability technologies have already been established with BrAPI, MIAPPE and ISA (Tab/JSON) for Phenotyping data, but the link between phenotype and omics data needs to be improved. The latter can rather be well described using bioschemas and therefore it will be useful for plant researchers to build a graph dataset embedding both MIAPPE and Bioschemas annotated data. We will enable plant researchers' friendly data archive by embedding the main plant standards (MIAPPE, BrAPI, ISA) in RO Crate. To link with the current activities of the plant communities, and to ease the integration of more diverse data types, a bridge with Bioschemas will be set up by finalizing the MIAPPE Bioschemas mapping initiated during the 2021 biohackathon. To demonstrate the interest of this, real data will be converted from existing sources (BrAPI, ISA Tab, MIAPPE databases) to RO Crate and Bioschemas to sketch some proof-of-concept use case (eg, showing phenotyping network on a map, showing the link between expression and phenotype data, …).--> 

<!--
# Formatting

This document use Markdown and you can look at [this tutorial](https://www.markdowntutorial.com/).

## Tables and figures

Tables can be added in the following way, though alternatives are possible:

| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |

Table: Note that table caption is automatically numbered.

A figure is added with:

![Caption for BioHackrXiv logo figure](./biohackrxiv.png) -->

# ISA

During the Hackathon it became apparent that an extension of ISA to support analytic or measurement results within the data model was urgently needed to support the MIAPPE use case. Assays usually only describe the process on how results were obtained and not the actual result values. Therefore, discussions led to two possible solutions: 
1. Extend the assay tables to include measurement values. This should be avoided for larger number of results.
2. Keep results in a separate file linked in the assay table.


# RO-Crate

For data exchange of MIAPPE datasets RO-Crates build on top of ISA (either ISA JSON or ISA-Tab) have been intensively discussed. We recommend four RO-Crate profiles with a flat and disentangled ISA structure. This avoid nested data structures and direct access, which is necessary for tools that can process the metadata such as GALAXY or KnowledgeGraphs. 

As a rule of thumb the annotation schema used for the description of the dataset is more general at the top of the hierarchy, when possible more general terms should be preferred when describing fields / parameters.

**1. ISA-Investigation Profile:**
Description on the Investigation of the ISA only relying on Schema.org for type definitions. This enables to find and harvet the datasets, e.g. via Google Dataset Search. 

**2. ISA-Study Profile:**
Description on an individual Study of the ISA in question relying on Bioschemas for type definitions (where possible).

**3. ISA-Assay Profile:** 
Description on an Assay of the ISA in question relying on ISA terminology.

**4. MIAPPE Profile:** 
Description of special MIAPPE related fields, not directly describable in Schema.org, Bioschemas, or ISA terms.

# Bioschemas

placeholder

# FAIR Cookbook Recipe "MIAPPE -> ISA"

During the discussions we realized, that several challenges according to the mapping of MIAPPE compliant phenomic data to ISA were already discussed in the past. In addition, some of the previously described mappings need to be somehow formalised to help the data producers as well data curators. Therefore we decided to draft a FAIRCookbook recipe explaining how to describe common phenotypic studies in a MIAPPE compliant way as ISA. This can be probably a subsection or mature variant of an "ISA" recipe and potentially help data producers as well as data curators.

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

# Results


# Discussion

...

## Acknowledgements

...

## References
