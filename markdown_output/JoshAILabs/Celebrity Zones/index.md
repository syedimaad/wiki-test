# Pipeline Architecture (LLD)

[](https://viewer.diagrams.net/?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1#G1ThTi_RdQBPbBg6kiP-xybg7mwPiiAB_U)

LLD of CZ Pipeline

# Codebase

<https://gitlab.dailyhunt.in/josh-ai-labs/blip-azure-service/-/tree/prod/api/celebrity_zones>

# Pipeline Breakdown

### Frame Extraction

- If required frames are not provided, 1 frame per second will be
  extracted from the target video

  - Currently in PROD, 1 frame per second in the first 2 seconds of the
    video are used

### Face Detection

- Above frames will be batched and then faces are detected per frame
  using an `MTCNN Face Detector Model`

- All the detected faces are pre-processed and then batched to a single
  tensor

### Face Identification/Recognition

- Above computed faces tensor will be paased to `ADAFACE Model` to get
  respective embeddings

- These embeddings will be queryed on a `SCANN Index` to get the
  relevant zone-id\'s and respective cosine similarity scores

- All identified zones and their respective score are aggregated and
  then filtered out to get the final set of identified zones and their
  respective scores as a single dictionary

# Touch Points

- Root folder :
  <https://joshprodaimlsa.blob.core.windows.net/projects/celebrity-zones/>

- Models :

  - ADAFACE :
    <https://joshprodaimlsa.blob.core.windows.net/projects/celebrity-zones/models/adaface/adaface_ir50_ms1mv2.ckpt>

  - SCANN :
    <https://joshprodaimlsa.blob.core.windows.net/projects/celebrity-zones/archives/scann_models.zip>
