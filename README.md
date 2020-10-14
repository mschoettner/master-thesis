# Master thesis

Code for my Master thesis "Psychopathic Traits and Social Cognition: Effective Connectivity in Theory of Mind and Empathy Networks". 

## How to run

This section will explain how to reproduce the analyses from quality control and preprocessing, over first and second level analysis, DCM, through to statistical analysis of behavioral data.

### Quality Control

Quality control was done using [MRIQC](https://mriqc.readthedocs.io/en/latest/) in a [Docker](https://www.docker.com/) container. To run it, follow the installation procedure described [here](https://mriqc.readthedocs.io/en/latest/docker.html) and run the following command:

`docker run -it --rm -v /path/to/data:/data:ro -v /path/to/data/derivatives/mriqc/out:/out poldracklab/mriqc /data /out participant`

followed by

`docker run -it --rm -v /path/to/data:/data:ro -v /path/to/data/derivatives/mriqc/out:/out poldracklab/mriqc /data /out group`

where `/path/to/data` is replaced with the path to where you stored that data set. Depending on your installation, you might need to include `sudo` to run the command as root.

### Preprocessing

Pull the docker image of [fMRIprep](https://fmriprep.org/en/stable/) and run the following command:

`docker run --rm -it -v /path/to/data:/data:ro -v /path/to/data/derivatives:/fmriprep poldracklab/fmriprep /data /fmriprep participant --fs-license-file /data/code/license.txt --write-graph --fs-no-reconall`

This preprocesses the data without running [Freesurfers](https://surfer.nmr.mgh.harvard.edu/) surface reconstruction. Again, replace `/path/to/data` with the path to the data set. Additionally, you might want to use the flag `--nprocs` to change the number of cpu cores to enable parallel processing.
