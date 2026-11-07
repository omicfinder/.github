# OmicFinder

Official website: https://project.inria.fr/omicfinder/

![Microbiome illustration](https://project.inria.fr/omicfinder/files/2023/12/antoine-dore-editorial-microbiome-illustration-gut-scientist.jpg-1024x629.jpg)

*Illustration © [Antoine Doré](https://www.antoinedore.com/)*

## Overview

Genomic data enable critical advances in medicine, ecology, ocean monitoring, and agronomy. Sequencing data accumulate exponentially in public genomic data banks such as the [ENA](https://www.ebi.ac.uk/ena/browser/about/statistics). A major limitation is that these data (petabytes of sequences) cannot be queried in their entirety.

**OmicFinder** is an [Inria challenge](https://www.inria.fr/en/list-of-inria-challenges), a four-year project that started in late 2023. Its aim is to provide a global search engine for querying nucleotide sequences against the vast amount of publicly available genomic data. The central algorithmic idea of a genomic search engine is to index and query small exact words (hundreds of billions across millions of datasets), together with their associated metadata.

## Teams

- [GenScale](https://team.inria.fr/genscale/): fundamental algorithms and data structures.
- [Dyliss](https://www-dyliss.irisa.fr/): query experience and answer enrichment through Semantic Web technologies.
- [Iroko](https://team.inria.fr/iroko/): index distribution at scale.
- [Taran](https://team.inria.fr/taran/): specialized hardware, to minimize the environmental impact of large-scale use of the tools.

## External partners

Partners participate in algorithmic developments and provide validations and use cases.

- [CEA-Genoscope](https://jacob.cea.fr/drf/ifrancoisjacob/Pages/Departements/Genoscope.aspx)
- [ELIXIR](https://elixir-europe.org)
- [Institut Pasteur](https://research.pasteur.fr/en/team/sequence-bioinformatics/)
- [Inria Challenge OceanIA](https://www.inria.fr/en/oceania)
- [CEA-CNRGH](https://jacob.cea.fr/drf/ifrancoisjacob/Pages/Departements/CNRGH.aspx)
- [Mediterranean Institute of Oceanography](https://www.mio.osupytheas.fr/en)

## Tools and results

### [Logan Search](http://logan-search.org)

Developed with [Téo Lemane](https://tlemane.github.io/) (CEA [Genoscope](https://jacob.cea.fr/drf/ifrancoisjacob/Pages/Departements/Genoscope.aspx)), [Rayan Chikhi](https://research.pasteur.fr/en/member/rayan-chikhi/) ([Sequence Bioinformatics](https://research.pasteur.fr/en/team/sequence-bioinformatics/) team, Institut Pasteur), and [Artem Babaian](https://rrna.ca/)'s group [1].

- Searches any DNA sequence against all 27 million sequencing datasets in the SRA (up to December 2023) in minutes, backed by a 1 PB k-mer index.
- Queries are decomposed into k-mers (k=31); every dataset containing them is returned.
- Results can be explored with custom plots over harmonized query and SRA metadata (sequencing technology, molecule type, geographic distribution, sample origin).
- Returns SRA accessions, not alignments. A companion microservice retrieves the Logan contigs matching a search.

### [Kaminari](https://github.com/yhhshb/kaminari)

A resource-frugal index for approximate colored k-mer queries, based on minimizers and integer compression. A careful implementation of this design outperforms previous Bloom filter-based solutions by a wide margin [2].

### [Back to sequences](https://github.com/pierrepeterlongo/back_to_sequences)

A simple tool to find the origin of k-mers in large genomic datasets [3].

### [The backpack quotient filter](https://github.com/vicLeva/bqf)

A dynamic and space-efficient data structure for querying k-mers with abundance [4].

### [kmcomp](https://www.biorxiv.org/content/10.64898/2026.07.03.736306v1.abstract)

Lossless compression of k-mer matrices enabling random row access, used to compress [kmindex](https://github.com/tlemane/kmindex) indexes [5].

### [kmhelpers](https://sebllns.github.io/kmhelpers/)

A Python toolkit for managing, compressing, and querying [kmindex](https://github.com/tlemane/kmindex) indexes [6].

### [Node counts in colored compacted de Bruijn graphs](https://journals.sagepub.com/doi/abs/10.1177/15578666261486474)

A method for comparing pangenomes by their node counts, addressing two challenges: the variability of node counts across graphs built from different numbers of genomes, and the strong influence of rare genomic sequences [7].

## Publications

1. Chikhi, R., Lemane, T., Loll-Krippleber, R., Montoliu-Nerin, M., Raffestin, B., Camargo, A. P., ... & Babaian, A. (2024). Logan: planetary-scale genome assembly surveys life's diversity. *bioRxiv*, 2024-07.
2. Levallois, V., Shibuya, Y., Le Gal, B., Patro, R., Peterlongo, P., & Pibiri, G. E. (2025). Kaminari: a resource-frugal index for approximate colored k-mer queries. *bioRxiv*, 2025-05.
3. Baire, A., Marijon, P., Andreace, F., & Peterlongo, P. (2024). Back to sequences: Find the origin of k-mers. *Journal of Open Source Software*, 9(101), 7066. https://doi.org/10.21105/joss.07066
4. Levallois, V., Andreace, F., Le Gal, B., Dufresne, Y., & Peterlongo, P. (2024). The backpack quotient filter: A dynamic and space-efficient data structure for querying k-mers with abundance. *iScience*, 27(12).
5. Regnier, A., Lemane, T., Bellenous, S., Chikhi, R., & Peterlongo, P. (2026). Lossless compression of k-mer matrices enabling random row access. *bioRxiv*, 2026-07.
6. Bellenous, S., Jaron, K., & Peterlongo, P. (2026). kmhelpers: A Python toolkit for automated management of genomic indexes. Submitted to [JOSS](https://joss.theoj.org/).
7. Parmigiani, L., & Peterlongo, P. (2026). Interpolating and Extrapolating Node Counts in Colored Compacted de Bruijn Graphs for Pangenome Diversity. *Journal of Computational Biology*, 15578666261486474.
