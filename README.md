# Master thesis

Code for my Master thesis "Psychopathic Traits and Social Cognition: Effective Connectivity in Theory of Mind and Empathy Networks". 

## How to run

This section will explain how to reproduce the analyses from quality control and preprocessing, over first and second level analysis, DCM, through to statistical analysis of behavioral data.

### Quality Control

Quality control was done using [MRIQC](https://mriqc.readthedocs.io/en/latest/) in a [Docker](https://www.docker.com/) container. To run it, follow the installation procedure described [here](https://mriqc.readthedocs.io/en/latest/docker.html) and run the following command:

`sudo docker run -it --rm -v /path/to/data:/data:ro -v /path/to/data/derivatives/mriqc/out:/out poldracklab/mriqc /data /out participant`

followed by

`sudo docker run -it --rm -v /path/to/data:/data:ro -v /path/to/data/derivatives/mriqc/out:/out poldracklab/mriqc /data /out group`

where `/path/to/data` is replaced with the path to where you stored that data set.
