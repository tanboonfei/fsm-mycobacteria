# Environment specification

Software used for the analyses reported in the manuscript. Versions in the first two
sections were captured from the machine the analyses were run on. Versions in the third
section are as recorded in the Methods and in the tool outputs themselves (Bakta writes its
version and database into every annotation summary; the per-isolate provenance is in
Table S28); they were not reinstalled to re-verify.

Companion files: `environment.yml` (conda) and `requirements.txt` (pip) alongside this file.

## Interpreters and libraries

| Component | Version |
|---|---|
| Python | 3.13.7 |
| pandas | 2.2.3 |
| numpy | 2.4.3 |
| scipy | 1.16.2 |
| statsmodels | 0.14.6 |
| openpyxl | 3.1.5 |
| biopython | 1.83 |
| R | 4.5.2 |
| ape | 5.8.1 |
| phytools | 2.5.2 |
| phylolm | 2.6.5 |
| nlme | 3.1.169 |
| geiger | 2.0.11 |
| castor | 1.8.4 |
| picante | 1.8.2 |

## Command-line tools verified on this machine

| Tool | Version |
|---|---|
| HyPhy | 2.5.59(MP), AVX build; RELAX analysis version 3.1.1 |
| IQ-TREE | 2.0.7 |
| MAFFT | 7.526 |
| BLAST+ | 2.16.0+ |
| Prodigal | 2.6.3 |
| pandoc | 3.1.3 (document rendering only) |

## Tools recorded in the Methods and tool outputs

| Tool | Version |
|---|---|
| Bakta | 1.11.4, database 6.0 (per-genome provenance in Table S28) |
| GTDB-Tk | 2.6.1, release R226 |
| CheckM2 | 0.1.3 (as applied by SPIRE) |
| GUNC | 1.0.1 (as applied by SPIRE) |
| OrthoFinder | 2.5.5 |
| gapseq | 1.4.0 |
| MMseqs2 | 18.8cc5c |
| eggNOG-mapper | 2.1.12, eggNOG database 5.0.2 |
| DIAMOND | 2.1.13 |
| HMMER | 3.4 |
| fastANI | 1.34 |
| SingleM | 0.21.3, metapackage S6.5.0 on GTDB R232 |

## Tools invoked inside Bakta 1.11.4

Recorded in every run log; they determine the annotation and are not separately installed.

| Tool | Version |
|---|---|
| Pyrodigal | 3.6.3 |
| tRNAscan-SE | 2.0.12 |
| Aragorn | 1.2.41 |
| Infernal cmscan | 1.1.5 |
| PilerCR | 1.6.0 |
| AMRFinderPlus | 4.0.23 |
| Pyhmmer | 0.11.1 |
| DIAMOND | 2.1.13 |
| blastn | 2.17.0 |

## Notes on reproduction

- `/usr/bin/hyphy` on this system is a `simd-dispatch` wrapper that collapses `"$@"` into a
  single argument and so cannot pass options through. Call the architecture binary directly:
  `/usr/lib/hyphy/bin/hyphy-avx LIBPATH=/usr/share/hyphy relax --alignment ... --tree ...`
- HyPhy RELAX optimisation is stochastic. Rerunning the identical FSM analysis gave
  K = 1.041 against 1.043 and LRT 13.0 against 12.6, so differences below about 0.5 in LRT
  carry no meaning.
- R's `read.delim` returns `""` rather than `NA` for empty cells. Metadata columns must be
  read with `na.strings = c("NA", "", "NaN", "None")` or missing biome and salinity calls
  enter analyses as absences.
- `castor::asr_mk_model` states must not be thresholded at p > 0.5; about 9% of families are
  genuinely unresolved and a 0.5 split assigns all of them to one side.
