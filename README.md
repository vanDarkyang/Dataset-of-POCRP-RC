# POCRP-RC Benchmark Datasets

Research data accompanying **Optimization of partially ordered container relocation problem with rolled containers**, by Ning Wang, Xinyu Ma, Ruobing Yang, and Jingjing Hu, *Computers & Operations Research*, 191 (2026), 107434.

**Paper:** https://doi.org/10.1016/j.cor.2026.107434

The partially ordered container relocation problem with rolled containers (POCRP-RC) considers ordinary containers with partial retrieval precedence and rolled containers (RCs) that remain in the yard.

## Download the data

| Archive | Nominal RC proportion | Available instances | Purpose |
| --- | --- | ---: | --- |
| [rc_00.zip](rc_00.zip) | 0% | 1,560 | RC proportion comparison, Section 6.6 |
| [rc_10.zip](rc_10.zip) | 10% | 1,560 | RC proportion comparison, Section 6.6 |
| [rc_20.zip](rc_20.zip) | 20% | 1,560 | Main benchmark, Sections 6.1-6.5; comparison in Section 6.6 |
| [rc_30.zip](rc_30.zip) | 30% | 1,560 | RC proportion comparison, Section 6.6 |
| [rc_20_tuning_195.zip](rc_20_tuning_195.zip) | 20% | 195 | First five instances from each of the 39 subsets; parameter tuning in Section 6.3.2 |

Download and extract the ZIP archive for the desired proportion. Each archive contains an English-named folder of plain-text `.pro` instance files. Original instance filenames and nonempty file contents are preserved byte for byte.

## Important data availability note

The 20% RC benchmark was stored separately from the original archive containing the 0%, 10%, and 30% variants. This release adds the available 20% benchmark and provides English archive names and documentation.

The paper describes 39 subsets of 40 instances, totaling 1,560 instances. The initially inspected copy contained one empty file, `Bay-15-8-5-79-63-16-17.pro`. Its nonempty counterpart was recovered from the separate data-generation archive with distinct RC identifiers (Z_100, Z_101, ...). The recovered file contains 79 containers (63 ordinary and 16 rolled) in 15 yard stacks, and its bytes are preserved unchanged.

To verify provenance, all 1,559 other benchmark instances were compared against that archive: 1,520 matched byte for byte; the remaining 39 matched the first instance record in the corresponding source files, which contained additional appended records. Only the missing instance was recovered; the other distributed benchmark files were not replaced. The 20% archive now contains all **1,560 instances**. The 195-instance tuning subset is unchanged and complete.

## Experimental settings

The benchmark is adapted from the ordinary-container instances of Jovanovic et al. (2019), as described in Section 6 of the paper. Containers were selected as RCs to construct the proportion variants.

- Sections 6.1-6.5 use the nominal 20% RC setting, with the subsets specified in each experiment.
- Section 6.6 compares the nominal 0%, 10%, 20%, and 30% RC settings using GRASP.
- Instance sizes range from 10 to 390 containers: small (10-50), medium (54-150), and large (170-390).
- In the available 20% data, `OC = floor(0.8 * C)` and `RC = C - OC`. Integer rounding means the realized proportion can exceed 20% for small instances; for example, 16 containers include 4 RCs. Read the counts in each file rather than assuming an exact fractional count.

## Instance format

The header records total containers, yard stacks, maximum yard tiers, vessel stacks (groups), ordinary/export containers, and rolled/shutout containers. The `Yard Bay` section then lists the contents of each stack.

The legacy header **Number Of Shutout Containers** denotes the RC count. RC tokens use the `Z_` prefix. Header wording and instance data are retained for compatibility with existing readers.

Filenames follow `Bay-S-T-G-C-OC-RC-instance.pro`, where `S` is the number of yard stacks, `T` the maximum yard tiers, `G` the number of vessel stacks/groups, and `C`, `OC`, and `RC` the total, ordinary, and rolled container counts. Instance-number padding may vary across the original proportion variants.

## Validation and reproducibility

[instance_manifest.csv](instance_manifest.csv) lists every distributed instance, its header counts, and its SHA-256 checksum. [validation_summary.json](validation_summary.json) records available files and empty source files excluded from the archives. [SHA256SUMS.txt](SHA256SUMS.txt) provides download checksums.

Validation checks include archive integrity, total yard-container counts, RC token counts, consistency of `C = OC + RC`, and byte-for-byte agreement between the 195 tuning files and their counterparts in the 20% benchmark. These checks validate the distributed files; they do not rerun or independently reproduce the optimization experiments.

## Citation

If you use these datasets, please cite:

```bibtex
@article{Wang2026POCRPRC,
  title   = {Optimization of partially ordered container relocation problem with rolled containers},
  author  = {Wang, Ning and Ma, Xinyu and Yang, Ruobing and Hu, Jingjing},
  journal = {Computers & Operations Research},
  volume  = {191},
  pages   = {107434},
  year    = {2026},
  doi     = {10.1016/j.cor.2026.107434}
}
```

## Questions and corrections

Please open a GitHub issue with the archive name and instance filename if you encounter a problem or need clarification about the data.
