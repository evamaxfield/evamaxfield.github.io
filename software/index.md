---
layout: layouts/base.njk
title: Software
templateClass: tmpl-post
eleventyNavigation:
  key: Software
  order: 5
---

Please see my [GitHub Profile](https://github.com/evamaxfield) for a complete list of the software I am working on.

##### Subject Matter

1. [Science of Scientific Software](#science-of-scientific-software)
1. [Public Interest Technology](#public-interest-technology)
1. [Computational Biology](#computational-biology)

#### Science of Scientific Software

##### Research Software Graph (rs-graph)

_Development Status :: 4 - Beta_
[https://github.com/evamaxfield/rs-graph](https://github.com/evamaxfield/rs-graph)

_RS-Graph is an open-source project which enables the collection, processing, and standardization of metadata, bibliometric information, and computed statistics for scientific publications and their associated research software/code repositories. The data produced from the current version of rs-graph includes document information (DOI, title, publication date, cited-by-count, topics/fields/domains), researcher details (name, works count, h-index), document-contributors (author position, corresponding author status), repositories (owner, name, description, stargazers count, created datetime, README content), developer accounts (username, name, email), repository-contributors (links between repositories and developer accounts), document-repository-links (links between documents and their associated source-code repositories), and researcher-developer-account-links (links between researchers and their associated developer accounts)._

##### Scientific Software Models (sci-soft-models)

_Development Status :: 4 - Beta_
[https://github.com/evamaxfield/sci-soft-models](https://github.com/evamaxfield/sci-soft-models)

_Sci-Soft-Models is an open-source project which provides simple access to computational predictive models relevant to scientists interested in large-scale examinations of scientific software production. Currently the library includes modules for using the "Author-Developer Account Matching Model" described and used in [Code Contribution and Credit in Science](https://doi.org/10.48550/arXiv.2510.16242) and an updated and greatly improved version of the "Soft-Search" model which predicts software production from NSF award information originally described in [Soft-Search: Two Datasets to Study the Identification and Production of Research Software](https://doi.org/10.1109/JCDL57899.2023.00040)._

##### AWS-GROBID

[https://github.com/evamaxfield/aws-grobid](https://github.com/evamaxfield/aws-grobid)

_Development Status :: 4 - Beta_
_AWS-GROBID is a small open-source project which provides simple utilities for quickly creating and destroying GROBID servers on AWS compute. [GROBID servers](https://grobid.readthedocs.io/en/latest/) enable large-scale processing of scientific publication PDFs, and, relevant to scientific software, enable the large-scale extraction of [software mentions from scientific publication PDFs](https://github.com/softcite/software-mentions)._

#### Public Interest Technology

##### Council Data Project

Eva Maxfield Brown, To Huynh, Isaac Na, Hawk Ticehurst, Katlyn M.F. Greene, Emily Gilles, Madeleine Farrer, Brian Ledbetter, Nic Weber
_Development Status :: 5 - Production/Stable_
[https://councildataproject.org](https://councildataproject.org)

_Council Data Project is an open-source project dedicated to providing journalists, activists, researchers, and all members of each community we serve with the tools they need to stay informed and hold their councilmembers accountable. By combining and simplifying sources of information on council meetings and actions, CDP ensures that everyone is empowered to participate in local government. For members of the community looking to stay up-to-date, we aim to make finding relevant meetings as easy as possible. For journalists and activists, our tools enable tracking legislation through the council process, transcript search with timestamped transcripts for review and sharing, full voting records querying, and more. And, for civic technology organizations and municipal government offices, we make all of our tools easy to deploy for your own council._

#### Computational Biology

##### AICSImageIO / BioIO

Eva Maxfield Brown, et al.
_Development Status :: 5 - Production/Stable_
[https://github.com/AllenCellModeling/aicsimageio](https://github.com/AllenCellModeling/aicsimageio) / [https://github.com/bioio-devs/bioio](https://github.com/bioio-devs/bioio)

_AICSImageIO aims to provide a consistent intuitive API for reading in or out-of-memory image pixel data and metadata for the many existing proprietary microscopy file formats, and, an easy-to-use API for converting from proprietary file formats to an open, common, standard – all using either language agnostic or pure Python tooling._