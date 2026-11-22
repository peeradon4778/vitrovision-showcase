# Errata — VitroVision

Date: **2026-11-22**

This file records corrections to claims that appear in submitted deliverables or
historical documents but are not supported by a reproducible artifact in this
repository. The original submitted documents are left unchanged as historical
snapshots. Use this errata when citing or presenting the project.

> **Public showcase note:** submitted deliverables and data files are not
> included in this public repository. They remain in the private archive.

## E1 — "U-Net was distilled from SAM3"

**Status: corrected.** There is no reproducible evidence in this repository
that the public U-Net checkpoint was trained from SAM3 pseudo-labels. The public
app documentation and `src/train_greenhouse.py` describe training on a public
greenhouse dataset (about 1,200 image/mask pairs), not SAM3 pseudo-labels and not
the 100-bottle labels.

Correct description:

> The public U-Net + MobileNetV3-Small checkpoint is a greenhouse-trained
> baseline. It has not been fine-tuned on the 100-bottle in-domain set.

Do not describe it as a distilled SAM3 model unless a training script,
config, pseudo-label manifest and evaluation artifact are attached.

## E2 — `val_dice 0.9817`

**Status: unverified.** No evaluation CSV, prediction set, model hash or
reproducible command is attached in this repository. The number appears in
historical documents but cannot be reproduced from the repository as-is.

Action: do not cite `0.9817` as a verified result. Recompute on a frozen test
split, save the CSV and command, then update this errata.

## E3 — U-Net verdict `acc 0.653 / sens 0.717 / spec 0.579`

**Status: unverified.** No per-image prediction CSV is attached. The number
also depends on a height threshold (`0.20`) that has not been revalidated for
the current pipeline.

Action: recompute with saved predictions and report the exact threshold,
test split and model hash. Until then, label it `unverified`.

## E4 — SAM3 pilot numbers

**Status: preliminary.** The following are pilot results from the 100-bottle
dataset, not a validated system:

- height correlation `r = 0.6382`
- height-rule accuracy `0.7551`
- height-rule sensitivity `0.9167`
- height-rule kappa about `0.4468`, below the 0.70 target

Source: `data/processed/plant_growth_summary.csv` and
`data/processed/trait_benchmark/trait_benchmark_summary.csv`.

Always label these as **pilot/preliminary**.

## E5 — "Validated" or "production-ready"

**Status: false.** Human ground-truth masks are not complete (0/30 at the last
audit). No Level A Dice/mIoU evaluation has been run against human masks. The
system is a research prototype.

## E6 — "Human masks are complete / 30 masks available"

**Status: not done.** `data/processed/ground_truth_masks/` is empty at the last
audit. Do not claim a completed pixel-level ground truth until the masks are
committed or archived with a checksum.

## How to cite

| Use case | Wording |
|---|---|
| Public README/slides | "research prototype; not validated" |
| Pilot numbers | "preliminary pilot result (n=98)" |
| Unverified numbers | do not cite, or cite with `[unverified]` |
| Submitted deliverables | cite the document, then point to this errata |

## Change control

This errata does not alter submitted deliverables. If an official erratum is
required, submit a separate correction document through the same channel and
reference this file.
