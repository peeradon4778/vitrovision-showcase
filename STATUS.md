# STATUS — VitroVision

Last updated: **2026-11-22**
Owner: project author. This file records the state that can be checked against
repository artifacts, not promotional claims.

> **Public showcase note:** data files, source code, submitted deliverables and
> internal logs are not included in this public repository. Evidence paths refer
> to the private archive.

## 1. What is verified

| Item | Evidence | Status |
|---|---|---|
| 100-bottle expert labels | `data/processed/ground_truth.csv` | 60 ready / 38 not ready / 2 review |
| SAM3 pilot height correlation | `data/processed/trait_benchmark/` | `r = 0.6382` (preliminary) |
| SAM3 pilot height rule | same CSV, threshold `0.275` | accuracy `0.7551`, sensitivity `0.9167` (n=98, preliminary) |
| Preliminary height kappa | derived from the same pilot | about `0.4468`, below the 0.70 target |
| Current U-Net checkpoint | `space/README.md` and the private training archive | trained on public greenhouse data; not fine-tuned on bottle images |
| Human ground-truth masks | `data/processed/ground_truth_masks/` | 0/30 at last check |
| New 60-bottle collection | `data/raw/newrun_202611/` | manifest and split only; images pending |
| Repository size | `git count-objects -vH` | about 8 MB pack; no files above 1.2 MB in history |

## 2. Claims that are not verified in this repository

- `val_dice 0.9817` for the current checkpoint: no evaluation CSV or reproducible
  command is attached; the number appears in older docs.
- "Distilled from SAM3": the public app README says the checkpoint was trained on
  a public greenhouse dataset (not SAM3-pseudo, not bottle labels). The
  distillation claim is therefore not supported.
- `U-Net accuracy 0.653 / sensitivity 0.717 / specificity 0.579`: no CSV is
  attached in this repository.
- Any statement that the system is "validated" or ready for production.

See [`docs/CLAIMS_AND_EVIDENCE.md`](docs/CLAIMS_AND_EVIDENCE.md) for the mapping.
For corrections to claims in submitted or historical documents, see
[`ERRATA.md`](ERRATA.md).

## 3. Known blockers

1. No human-annotated masks for Level A (Dice/mIoU).
2. U-Net domain gap on bottle images; threshold `0.20` has not been revalidated.
3. New collection incomplete; cross-species evidence is not available.
4. The private research archive has no LICENSE; this public repository uses MIT
   for code (`LICENSE`) and CC BY 4.0 for documentation (`LICENSE-docs`).
5. `v1-final` is a June 2026 archive tag in the private repository and does not
   match the current code. It is not part of this public repository.
6. `data/processed/verdict_confusion_full.csv` is a deprecated artifact and must
   not be cited as a current result.

## 4. Next actions

- Annotate at least 30 human masks, then run the mask metrics script in the
  private archive.
- Fix the `height_proxy` axis swap in the private training script and handle
  EXIF orientation before any new evaluation.
- Re-run evaluation on a frozen test split and attach the CSV to the repository.
- Decide the license and the public-data policy.
- Keep the private archive separate; publish only reviewed files from the public
  allowlist.
