---
layout: layouts/base.njk
title: Papers
templateClass: tmpl-post
eleventyNavigation:
  key: Papers
  order: 3
---

##### Subject Matter

1. [Public Interest Technology](#public-interest-technology)
1. [Data Archival](#data-archival)
1. [Computational Biology](#computational-biology)

#### Public Interest Technology

- **Packaging Municipal Legislative Event Data for Reuse and Exchange**
  _Workshop on Research Objects - published: 28 August 2019_

  Jackson Brown and Nic Weber
  [https://doi.org/10.5281/zenodo.3380592](https://doi.org/10.5281/zenodo.3380592)

  _Municipal governments in the USA are often divided between a legislative (city council) and executive (mayoral) branch. These two branches not only differ in their power to govern a municipality, but also in the way their governing activities are organized: executive activities are periodic and random in occurrence, legislative activities are regularly occurring and organized around key events (e.g. committee and subcommittee meetings, expert testimony, public comment, introduction and debate of new legislation, and voting). Further, legislative events are subject to Open Meetings laws at both the State and Federal level - so that citizens can have a transparent record of how officials are performing their elected duties. This openness mandate further requires that the events of any municipal legislature are recorded and published to the web in an openly accessible format. However, many municipal governments lack the time, money, and expertise to provide citizens with well described data beyond a simple audio or video file of a legislative event. The Council Data Project (CDP) is our attempt to provide a platform for adding needed context to event based legislative data. In particular we provide open-source tools for transcribing, indexing, modeling, and publishing legislative event data to the web. Our on-going research is focused on how to package a bundle of event-based digital objects (audio-files, videos, transcripts, votes, etc) along with relevant metadata parameters to facilitate meaningful reuse by researchers._

#### Data Archival

- **Managing Manifests and Distributing Datasets**
  _Workshop on Research Objects - published: 30 August 2019_

  Jackson Brown
  [https://doi.org/10.5281/zenodo.3382258](https://doi.org/10.5281/zenodo.3382258)

  _A core principal of research is the affordability and ease of reproducing the results found by an experiment and to minimize the challenge of experimental reproducibility, it is common for researchers to share the dataset used to produce the results of an experiment. Methods for managing and distributing these datasets however, are ill-suited for imaging datasets, or more generally: large object datasets, because they commonly resemble a manifest and require additional packaging and organization than their feature set counterparts. Quilt3Distribute (Q3D) is a software application that enables the distribution of manifest style datasets which can be made of up thousands of individual files._

- **DSDB: Reproducible Computational Modeling**
  _Workshop on Research Objects - published: 16 July 2019_

  Jackson Brown and Nic Weber
  [https://doi.org/10.5281/zenodo.3337374](https://doi.org/10.5281/zenodo.3337374)

  _In the following abstract we describe Dataset-Database (DSDB), an open-source system for handling the provenance, versioning, de-duplication, history, and query of dynamic databases used at the Allen Institute for Cell Science. We present our initial design and deployment of DSDB, the results of this work for computational modeling, and conclude with a discussion of the future work necessary for provisioning data discovery and sharing tools that facilitate transparent reproducible research through provenance aware features._

#### Computational Biology

- **A deep generative model of 3D single-cell organization**
  _preprint -- published: 9 June 2021_

  Rory Donovan-Maiye, Jackson Brown, Caleb Chan, Liya Ding, Calysta Yan, Nathalie Gaudreault, Julie Theriot, Mary Maleckar, Theo Knijnenburg, Gregory Johnson
  [https://doi.org/10.1101/2021.06.09.447725](https://doi.org/10.1101/2021.06.09.447725)

  _We introduce a framework for end-to-end integrative modeling of 3D single-cell multi-channel fluorescent image data of diverse subcellular structures. We employ stacked conditional β-variational autoencoders to first learn a latent representation of cell morphology, and then learn a latent representation of subcellular structure localization which is conditioned on the learned cell morphology. Our model is flexible and can be trained on images of arbitrary subcellular structures and at varying degrees of sparsity and reconstruction fidelity. We train our full model on 3D cell image data and explore design trade-offs in the 2D setting. Once trained, our model can be used to impute structures in cells where they were not imaged and to quantify the variation in the location of all subcellular structures by generating plausible instantiations of each structure in arbitrary cell geometries. We apply our trained model to a small drug perturbation screen to demonstrate its applicability to new data. We show how the latent representations of drugged cells differ from unperturbed cells as expected by on-target effects of the drugs._

- **Cell states beyond transcriptomics: integrating structural organization and gene expression in hiPSC-derived cardiomyocytes**
  _Cell - published: 26 May 2021_

  Gerbin, Grancharova, Donovan-Maiye, Hendershott, et al.
  [https://doi.org/10.1016/j.cels.2021.05.001](https://doi.org/10.1016/j.cels.2021.05.001)

  _Although some cell types may be defined anatomically or by physiological function, a rigorous definition of cell state remains elusive. Here, we develop a quantitative, imaging-based platform for the systematic and automated classification of subcellular organization in single cells. We use this platform to quantify subcellular organization and gene expression in >30,000 individual human induced pluripotent stem cell-derived cardiomyocytes, producing a publicly available dataset that describes the population distributions of local and global sarcomere organization, mRNA abundance, and correlations between these traits. While the mRNA abundance of some phenotypically important genes correlates with subcellular organization (e.g., the beta-myosin heavy chain, MYH7), these two cellular metrics are heterogeneous and often uncorrelated, which suggests that gene expression alone is not sufficient to classify cell states. Instead, we posit that cell state should be defined by observing full distributions of quantitative, multidimensional traits in single cells that also account for space, time, and function._

- **Robust integrated intracellular organization of the human iPS cell: where, how much, and how variable?**
  _preprint -- published: 10 December 2020_

  Viana, et al.
  [https://doi.org/10.1101/2020.12.08.415562](https://doi.org/10.1101/2020.12.08.415562)

  _Despite the intimate link between cell organization and function, the principles underlying intracellular organization and the relation between organization, gene expression and phenotype are not well understood. We address this by creating a benchmark for mean cell organization and the natural range of cell-to-cell variation. This benchmark can be used for comparison to other normal or abnormal cell states. To do this, we developed a reproducible microscope imaging pipeline to generate a high quality dataset of 3D, high-resolution images of over 200,000 live cells from 25 isogenic human induced pluripotent stem cell (hiPSC) lines from the Allen Cell Collection. Each line contains one fluorescently tagged protein, created via endogenous CRISPR/Cas9 gene editing, representing a key cellular structure or organelle. We used these images to develop a new multi-part generalizable analysis approach of the locations, amounts, and variation of the 25 cellular structures. Taking an integrated approach, we found that both the extent to which a structure’s individual location varied (“stereotypy”) and the extent to which the structure localized relative to all the other cellular structures (“concordance”) were robust to a wide range of cell shape variation, from flatter to taller, smaller to larger, or less to more polarized cells. We also found that these cellular structures varied greatly in how their volumes scaled with cell and nuclear size. These analyses create a data-driven set of quantitative rules for the locations, amounts, and variation of 25 cellular structures within the hiPSC as a normal baseline for cell organization._
