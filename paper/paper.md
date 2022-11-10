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
  - SWATE
authors:
  - name: First Author
    affiliation: 1
  - name: Last Author
    orcid: 0000-0000-0000-0000
    affiliation: 2
affiliations:
  - name: First Affiliation
    index: 1
  - name: Second Affiliation
    index: 2
date: 10 November 2022
cito-bibliography: paper.bib
event: BH22EU
biohackathon_name: "BioHackathon Europe 2022"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Paris, France, 2022"
group: Project 22
# URL to project git repo --- should contain the actual paper.md:
git_url: [https://github.com/biohackrxiv/publication-template](https://github.com/sebeier/22_plant_data_exchange)
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: First Author \emph{et al.}
---


# Introduction

This project will improve the integration of Plant data standards with important interoperability technologies. Indeed, some interoperability technologies have already been established with BrAPI, MIAPPE and ISA (Tab/JSON) for Phenotyping data, but the link between phenotype and omics data needs to be improved. The latter can rather be well described using bioschemas and therefore it will be useful for plant researchers to build a graph dataset embedding both MIAPPE and Bioschemas annotated data. We will enable plant researchers' friendly data archive by embedding the main plant standards (MIAPPE, BrAPI, ISA) in RO Crate. To link with the current activities of the plant communities, and to ease the integration of more diverse data types, a bridge with Bioschemas will be set up by finalizing the MIAPPE Bioschemas mapping initiated during the 2021 biohackathon. To demonstrate the interest of this, real data will be converted from existing sources (BrAPI, ISA Tab, MIAPPE databases) to RO Crate and Bioschemas to sketch some proof-of-concept use case (eg, showing phenotyping network on a map, showing the link between expression and phenotype data, …).

# Formatting

This document use Markdown and you can look at [this tutorial](https://www.markdowntutorial.com/).

## Subsection level 2

Please keep sections to a maximum of only two levels.

## Tables and figures

Tables can be added in the following way, though alternatives are possible:

| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |

Table: Note that table caption is automatically numbered.

A figure is added with:

![Caption for BioHackrXiv logo figure](./biohackrxiv.png)

# Other main section on your manuscript level 1

Lists can be added with:

1. Item 1
2. Item 2

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
