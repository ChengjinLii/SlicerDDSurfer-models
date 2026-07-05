# SlicerDDSurfer Models

This repository stores large model weights and template assets used by
SlicerDDSurfer. The code repository is:

https://github.com/ChengjinLii/SlicerDDSurfer

## Layout

Files keep the same repository-relative paths expected by SlicerDDSurfer, for
example:

```text
Resources/Data/ckpts/hcp/
Resources/Data/template/
surface/template/
segmentation/weights/
parcellation/weights/
```

This allows the downloader in the code repository to restore assets without
rewriting runtime paths.

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
