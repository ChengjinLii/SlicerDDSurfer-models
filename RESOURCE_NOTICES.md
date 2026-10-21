# Optional Resource Notices

These resources are unmodified third-party inference/reference files, not
project-owned models or clinical validation data. Preserve this notice and the
indicated license with copies. The resource catalog is not legal certification.

## PNL CNN

Upstream: https://github.com/pnlbwh/CNN-Diffusion-MRIBrain-Segmentation/releases/tag/v0.3

All or portions of this licensed product (such portions are the "Software")
have been obtained under license from The Brigham and Women's Hospital, Inc.
and are subject to the following terms and conditions:
[complete PNL/BWH agreement](brain_mask/pnl_cnn/LICENSE.txt).

Architecture and three weight files are copied without modification. Cite
Palanivelu, Cetin Karayumak, Billah, Zurrin, Bouix and Rathi, CNN based diffusion
MRI brain segmentation tool, doi:10.5281/zenodo.3665739, and the upstream requested
method citations. This notice does not cover the third-party IIT template.

## IIT Template: Not Mirrored

https://www.nitrc.org/projects/iit/ states that electronic reposting requires
express written IIT permission. The ignored, authorized local copy is for
local use/verification only. It must not be uploaded with the PNL weights.
Acquire the template from the author-designated upstream source and follow
the IIT research-use, attribution and other restrictions.

## TractCloud

Upstream: https://github.com/SlicerDMRI/TractCloud/releases/tag/v1.0.0

All or portions of this licensed product (such portions are the "Software")
have been obtained under license from The Brigham and Women's Hospital, Inc.
and are subject to the following terms and conditions:
[complete upstream Slicer agreement](bundles/tractcloud/LICENSE.txt).

The model, CLI argument record and small atlas reference are an unmodified
inference subset. Training logs, example subject data and the training/test
archives are excluded. Cite Xue et al., TractCloud, MICCAI 2023, and the
underlying ORG atlas. No author endorsement is implied.

## SynthStrip

Andrew Hoopes, Jocelyn S. Mora, Adrian V. Dalca, Bruce Fischl, Malte Hoffmann.
SynthStrip: Skull-Stripping for Any Brain Image. NeuroImage 260:119474 (2022).
doi:10.1016/j.neuroimage.2022.119474.

The unmodified main model version 1 uses the author's CC BY 4.0 option:
https://creativecommons.org/licenses/by/4.0/.
Source and license options: https://surfer.nmr.mgh.harvard.edu/docs/synthstrip/.
No model changes, endorsement or clinical approval are asserted.

## ORG White Matter Atlas

Fan Zhang, Ye Wu, Isaiah Norton, Laura Rigolo, Yogesh Rathi, Nikos Makris,
Lauren O'Donnell. ORG Fiber Clustering White Matter Atlas.
doi:10.5281/zenodo.2648292; https://zenodo.org/records/2648292.

The pinned Zenodo distribution states CC BY 4.0:
https://creativecommons.org/licenses/by/4.0/.
Registration/clustering ZIPs are unchanged; the local extraction omits only
macOS resource-fork metadata. Retain the upstream agreement as well:

All or portions of this licensed product (such portions are the "Software")
have been obtained under license from The Brigham and Women's Hospital, Inc.
and are subject to the following terms and conditions:
[upstream Slicer agreement](bundles/wma/LICENSE.txt).

Cite Zhang et al., An anatomically curated fiber clustering white matter atlas
for consistent white matter tract parcellation across the lifespan,
NeuroImage 179:429-447 (2018), plus the atlas DOI and applicable upstream
citations. No individual subject DWI dataset is included.
