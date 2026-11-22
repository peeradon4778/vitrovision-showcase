# VitroVision

Non-destructive computer-vision research prototype for assessing the
acclimatization readiness of tissue-cultured plants from bottle photographs.

Project: **29YCSE00054T** (YSC 2027) — research prototype, not a validated
production grading system.

> **Public showcase scope:** this repository contains demo code and status
> documents only. Raw images, expert labels, submitted deliverables, source
> archive and internal logs are not included.

## What it does

The pipeline segments a plant inside a transparent culture bottle and derives
measurements such as projected height, coverage, color fractions and image
quality. A decision layer turns those measurements into a readiness verdict
with a confidence value and a short explanation.

```
photo -> quality gate -> segmentation -> measurements -> verdict -> explanation
```

The final product is intended to run in the browser: camera capture, ONNX
inference and the decision layer can all run locally, without uploading images
to a server.

## Current model status

- Public checkpoint: **U-Net + MobileNetV3-Small** (`segmentation-models-pytorch`),
  about **3.59M parameters**, ONNX about **14.45 MB**.
- It was trained on a public greenhouse dataset (about 1,200 image/mask pairs).
- It has **not** been fine-tuned on the 100-bottle in-domain set.
- Older internal documents describe the checkpoint as "distilled from SAM3" and
  report `val_dice 0.9817`. Those claims are **not currently supported by an
  evaluation artifact in this repository**. Treat them as unverified until a
  reproducible evaluation is attached. See
  [`docs/CLAIMS_AND_EVIDENCE.md`](docs/CLAIMS_AND_EVIDENCE.md).

## Preliminary evidence

Pilot work with SAM3 zero-shot segmentation on 100 bottle images produced
preliminary measurements. This is pilot evidence, not a validated result:

- Height correlation with manual measurements: `r = 0.6382`.
- A height threshold of `0.275` produced accuracy `0.7551` and sensitivity
  `0.9167` on 98 labelled images.
- No human-annotated pixel masks were available for a Level A Dice/mIoU
  evaluation at that time.

Raw images, processed CSVs, expert labels and model weights are not included in
this public showcase; they remain in the private research archive.

## Known limitations

- No human ground-truth masks for the current Level A evaluation (0/30 at the
  last check).
- The current U-Net checkpoint has a domain gap on bottle images.
- The 100-image pilot contains one species; cross-species performance is not
  established.
- The new 60-bottle, 3-species collection run is not complete (images pending).
- The decision threshold and height-to-cm calibration have not been revalidated
  for the current pipeline.


## Repository layout

| Path | Purpose |
|---|---|
| `space/` | Gradio demo application |
| `docs/` | Claims, errata and selected diagrams |

## Quick start

Read [`STATUS.md`](STATUS.md) first for the current verified state and blockers.
Then see [`docs/CLAIMS_AND_EVIDENCE.md`](docs/CLAIMS_AND_EVIDENCE.md) and
[`ERRATA.md`](ERRATA.md). The app in `space/` can be run locally with its own
dependencies; see `space/README.md`.

## Documentation

- [`STATUS.md`](STATUS.md) — verified state, open blockers and next actions
- [`ERRATA.md`](ERRATA.md) — corrections to unverified claims in submitted or
  historical documents
- [`docs/CLAIMS_AND_EVIDENCE.md`](docs/CLAIMS_AND_EVIDENCE.md) — which claims are
  supported, unverified or historical

## License

- Code: MIT — see [`LICENSE`](LICENSE).
- Documentation and diagrams: CC BY 4.0 — see [`LICENSE-docs`](LICENSE-docs).

Third-party dependencies and model weights keep their own licenses.
