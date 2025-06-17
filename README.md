# fmriprep_acompcor_lesionfix
Re-run the FMRIPREP aCompCor workflow while excluding voxels within a lesion mask.

aCompCor relies on accurate tissue type classificaiton of voxels, which can be difficult for brains with gross patholgy. The code in this repository is a kludgy hack to re-run the FMRIPREP aCompCor workflow after subtracting a voxels within a lesion mask provided to FMRIPREP during preprocessing. This workflow was developed for and tested with FMRIPREP version 1.3.2 and may (probably) won't work with newer versions without edits.
