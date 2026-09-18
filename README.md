# Analysis code and phylogenetic data

Supporting repository for:

> **A diverse uncultured freshwater clade with reduced genomes in the *Mycobacteriaceae***

This repository holds the items named in the manuscript's Availability of data and
materials statement: the bac120 species phylogeny, the multiple-sequence alignments,
the branch-labelled Newick trees, the unmodified HyPhy RELAX output, and the
analysis code.

The genomes themselves are not redistributed here. MAGs come from the SPIRE
database (https://spire.embl.de) and reference assemblies from NCBI, under the
accessions listed in Table S1 of the manuscript's Additional file 2.

| Directory | Contents |
|---|---|
| `scripts/` | the analysis code, with the inputs it reads; see `scripts/README.md` |
| `phylogeny/` | bac120 alignment, IQ-TREE output and the rooted species tree |
| `relax/` | RELAX alignments, branch-labelled trees, command records and unmodified JSON output; see `relax/README.txt` |

`scripts/inputs/myco_bac120.rooted.treefile` is the same tree as
`phylogeny/myco_bac120.rooted.treefile`, kept alongside the code so the scripts run
from `scripts/` without a path outside it.

## Reported values

`Additional_file_2.xlsx` in the submission (Supplementary Tables S1–S28) is the
authority for every reported value, and Table S27 traces each principal statistic to
its source table and filter. `scripts/inputs/tsv/` is a per-table text export of that
workbook, which is what the scripts read.

## Environment

`ENVIRONMENT.md` lists interpreter, library and tool versions, and records four
reproduction pitfalls worth reading before a rerun. `environment.yml` and
`requirements.txt` are alongside it.
