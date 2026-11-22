# Claims and Evidence

Last updated: **2026-11-22**

This document separates claims that are supported by repository artifacts from
claims that are preliminary, unverified or historical. It exists because several
documents written before the current checkpoint and data audit made stronger
claims than the repository can currently support.

For corrections that apply to submitted or historical documents, see
[`../ERRATA.md`](../ERRATA.md).

> **Public showcase note:** data files, submitted deliverables and internal
> documents referenced below are not included in this public repository. Paths
> refer to the private research archive.

## Evidence map

| Claim | Current evidence | Verdict | Action |
|---|---|---|---|
| The repository contains 100 expert-labelled bottle images | `data/processed/ground_truth.csv` | Supported | Use with caveat: 60 ready / 38 not ready / 2 review |
| SAM3 pilot height correlation `r = 0.6382` | `data/processed/trait_benchmark/trait_benchmark_summary.csv` | Supported, preliminary | Always label as pilot |
| SAM3 height rule accuracy `0.7551`, sensitivity `0.9167` | pilot CSV, threshold `0.275` | Supported, preliminary | Do not present as a validated system result |
| Height-rule kappa about `0.4468` | derived from the pilot | Supported, below target | Report honestly; do not hide |
| Current U-Net was distilled from SAM3 | no reproducible evidence; README and app docstring corrected in this public copy | **Unverified** | Do not reintroduce the claim |
| Current U-Net `val_dice 0.9817` | no evaluation artifact | **Unverified** | Do not cite until CSV/command is attached |
| U-Net verdict `acc 0.653` | no evaluation artifact in this repository | **Unverified** | Recompute and attach evidence |
| Human masks are complete for 30 images | `data/processed/ground_truth_masks/` is empty | **Not done (0/30)** | Annotate before claiming Level A |
| The system is validated or production-ready | no human-mask evaluation, no frozen test protocol | **False** | Keep the word "prototype" |

## Historical documents

The following files pre-date the 2026-11 audit and may contain the unverified
claims above. They are retained for project history and should not be used as
current evidence without checking this document:

- `docs/METHODOLOGY_DATA.md`
- `docs/ARCHITECTURE_PARAGRAPH.md`
- `docs/ARCHITECTURE_RATIONALE.md`
- `docs/FIGS_MASTER_PLAN.md`
- `docs/SOFTWARE_INVENTORY.md`
- `docs/planning/_backlog.md`
- `docs/deliverables/` (submitted snapshots; do not edit historical submissions)

## Rule for new writing

Any new README, report, slide or poster must use one of these labels:

- **Verified** — reproducible from a file or command in this repository.
- **Preliminary** — pilot result with the source named.
- **Unverified** — do not cite, or cite only with an explicit warning.
- **Historical** — kept for context, not current evidence.

When in doubt, use the weaker label.
