# fmriprep_acompcor_lesionfix
Re-run the [FMRIPREP](https://github.com/nipreps/fmriprep) aCompCor workflow while excluding voxels within a lesion mask.

aCompCor relies on accurate tissue type classificaiton of voxels, which can be difficult for brains with gross patholgy. The code in this repository is a kludgy hack to re-run the FMRIPREP aCompCor workflow after subtracting a voxels within a lesion mask provided to FMRIPREP during preprocessing. The workflow is designed to be run after an initial run of FMRIPREP, and depends on intermediate files contained in the FMRIPREP working directory. It will output updated aCompCor time series for each FMRIPREP-ed BOLD scan.

This workflow was developed for and tested with FMRIPREP [version 1.3.2](https://github.com/nipreps/fmriprep/tree/1.3.2) and may (probably) won't work with newer versions without edits. 

## Usage
This workflow is designed to be run from within the FMRIPREP docker/singularity container. It expects two positional arguments:
1) The subject ID
2) The FMRIPREP output directory.

Below is an example shell script to loop through subjects:

```
for sub_id in `cat /mnt/data/patient_list.txt`; do
    python /mnt/code/patients-03-acompcor_lesionfix/acompcor_lesionfix_workflow.py $sub_id /mnt/data/derivatives
done
```

