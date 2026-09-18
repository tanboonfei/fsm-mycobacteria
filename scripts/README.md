# Analysis code

The code behind the reported analyses, with the inputs it reads. This is a reduced
set: exploratory work, the annotation pipeline drivers, the data-preparation and
export utilities, the quality-control checkers and the figure-drawing code are not
included. Annotation commands are recorded per genome in Table S28.

Run everything from this directory.

| Script | Produces |
|---|---|
| `paths.py` | shared paths and the Table S1 loader; not run directly |
| `binning_artefact_control.py` | Table S4, the isolate-versus-MAG binning control |
| `bakta_isolates_analyse.py` | Tables S5 and S6, pseudogene load under one annotator |
| `s8_ingroup_models.R` | Table S8, phylogenetically corrected trait models |
| `s8_gls_corpagel_crosscheck.R` | the GLS cross-check quoted in Table S8 |
| `genome_size_bm_null.R` | the Brownian-motion null for ancestral genome size |
| `opsin_simulation_null.R` | Table S3b, the Mk simulation null for opsin presence |

Rerun results are written to `run_output/`, which is created on first use, so that
they can be compared against the workbook without overwriting it.

## Inputs

`inputs/` holds what the scripts read that is not in Additional file 2.

| Input | Read by |
|---|---|
| `tsv/` | all scripts; a per-table text export of `Additional_file_2.xlsx`, one file per table |
| `myco_bac120.rooted.treefile` | the four R scripts |

`bakta_isolates_analyse.py` additionally reads the 260 Bakta output directories and
`analysis_gaps/assembly_stats.tsv` from the project tree, which are too large to
bundle. Its results are in Tables S5 and S6.

## Reproduction notes

- The R scripts and `binning_artefact_control.py` reproduce their tables exactly.
  `bakta_isolates_analyse.py` differs from the workbook only in row order and in
  displayed precision.
- HyPhy RELAX optimisation is stochastic; see `ENVIRONMENT.md`.
- `Additional_file_2.xlsx` is the authority. Where a script default, an exported
  table or a note disagrees with it, the workbook is correct.

## Environment

`ENVIRONMENT.md` lists interpreter, library and tool versions, and records four
reproduction pitfalls worth reading before a rerun. `environment.yml` and
`requirements.txt` are alongside it.
