# SlicerDDSurfer Models

This repository stores large model weights and template assets used by
SlicerDDSurfer. The code repository is:

https://github.com/ChengjinLii/SlicerDDSurfer

## Layout

Files keep the same repository-relative paths expected by SlicerDDSurfer, for
example:

```text
surface/weights/
surface/template/
segmentation/weights/
parcellation/weights/
Resources/Data/100HCP-population-mean-T2.nii.gz
```

This allows the downloader in the code repository to restore assets without
rewriting runtime paths.

## DDSurfer Update (2026-10-04)

The current surface profile mirrors DDSurfer revision
`c3fa631b340c3e06eb75ab4f0f9ac9a288a25488`: four `ddsurfer_*.pt` checkpoints,
`manifest.json`, `SHA256SUMS`, two transformed OBJ templates and the
`100HCP-population-mean-T2-1mm.nii.gz` atlas. These nine resources must be used
with the matching updated SlicerDDSurfer backend.

Old `Resources/Data/ckpts/hcp/` and template assets are retained for historical
checkouts, but the current surface profile does not select them. DDSeg and
DDParcel weights are unchanged; DDParcel retains its separate registration
atlas. `release-manifests/ddsurfer-sync-20261004.json` records the verified
31-file core profile.

## Manifest

- `asset_mirror_manifest.json`: exported asset manifest with SHA256 checksums,
  sizes, profile metadata and source commit.
- `asset_mirror_index.tsv`: compact table of paths, sizes and checksums.

The source code repository also keeps `models/assets_manifest.json`, which is
the canonical downloader manifest.

## Download From SlicerDDSurfer

After this repository is published, users can download the core profile from the
code repository with:

```bash
python3 scripts/download_model_assets.py \
  --profile core \
  --source url \
  --source-id slicerdsurfer_models_release
```

If using a direct mirror URL:

```bash
python3 scripts/download_model_assets.py \
  --profile core \
  --source url \
  --base-url https://example.org/SlicerDDSurfer-models/v0.1.0
```

## Release Policy

Large binary files should be stored with Git LFS or attached to GitHub Releases.
For a public DOI archive, confirm redistribution and archive terms for every
asset group before publishing.
