<div align="center">

# SlicerDDSurfer Resources

[Code](https://github.com/ChengjinLii/SlicerDDSurfer) | [Layout](#layout) | [Optional Resources](#optional-resources) | [Notices](RESOURCE_NOTICES.md) | [中文](README.zh-CN.md)

</div>

---

This repository stores model weights, atlases, templates and other large non-code runtime resources used by
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
brain_mask/pnl_cnn/
brain_mask/synthstrip/
bundles/tractcloud/
bundles/wma/archives/
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

---

## Optional Resources

The historical repository name is retained for compatibility; this is not a
weights-only store. Optional resources are separate from the 31-file default
core profile. Merely cloning the code must not download every optional atlas.

| Group | Contents | Distribution |
| --- | --- | --- |
| PNL CNN | Three original HDF5 weights, architecture JSON, full upstream agreement | Mirrorable subset with notices |
| IIT b0 template | Required by PNL; kept only in an authorized local working copy | **Not committed or mirrored**; written IIT permission is required for electronic redistribution |
| TractCloud | Model, inference arguments, 308-byte atlas reference and upstream agreement | Minimal inference subset, not training/test datasets |
| SynthStrip | Main version-1 model | Author's CC BY 4.0 option, attributed and unmodified |
| WMA / ORG | Official registration and clustering ZIPs, upstream agreement | Separate opt-in archive profile; preserve ORG citation and CC BY 4.0 attribution |

`optional_assets_mirror_manifest.json` and `optional_assets_mirror_index.tsv`
describe the prepared optional mirror separately from the original core index.
The code repository's `models/external_assets_manifest.json` is its download,
integrity and redistribution-policy catalog. The 14-file optional resource set
was pushed in `11167a5`, including eight LFS binary objects. The public mirror
supports anonymous URL downloads; the code repository can remain private.
Anonymous TractCloud acquisition into a clean directory passed all four hashes.
WMA's extracted local trees are ignored by Git and can be reproduced from the
two pinned ZIPs and verified against the 849-file index. IIT is not in Git.
Independent fresh-checkout readback verified all 14 optional file sizes and
SHA256 values. Selected files contain no unresolved LFS pointers.

Use the code repository to verify local resources:

```bash
python3 scripts/download_model_assets.py \
  --manifest models/external_assets_manifest.json \
  --profile mirrorable-inference --asset-root /path/to/SlicerDDSurfer-models \
  --verify-only
```

PNL's complete local verification uses `--profile pnl-cnn`; that profile includes
the restricted IIT template and is deliberately refused by the mirror exporter.
An upstream-only download cannot be redirected to arbitrary mirror URLs.

Conda environments, Python/CUDA libraries, external executables, installer
caches, raw subject data and analysis outputs do not belong in this repository.
See [resource notices](RESOURCE_NOTICES.md) before distributing any optional files.

---

## Download From SlicerDDSurfer

Users can download the core profile from the code repository with:

```bash
python3 scripts/download_model_assets.py \
  --profile core \
  --source url \
  --source-id slicerdsurfer_models_git
```

Download only selected optional resources (no Git/Git LFS client required):

```bash
python3 scripts/setup_optional_assets.py --profiles tractcloud wma \
  --asset-root /path/to/resources --execute --accept-terms
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
