# Purpose:
Subworkflow for if you just want to: 
- Run the round A/B primer and contaminant removal steps of Hecatomb without any of the other preprocessing steps
- Get the statistics (which Hecatomb doesn't currently output) for what was removed from each sample


# How to run:
- Git clone this repository
- Run from an environment with Snakemake version 8+, [mamba](https://anaconda.org/conda-forge/mamba), and [snakemake-executor-plugin-slurm](https://snakemake.github.io/snakemake-plugin-catalog/plugins/executor/slurm.html)

```
source /ref/sahlab/software/miniforge3/bin/activate
conda activate snakemake_v8.20.3
```

```
cd workflow
snakemake --profile ../profile/slurm/ --config [options]
```

## Note:

If your fastq files have any suffixes other than _R1.fastq.gz and _R2.fastq.gz, need to specify this on the command line using the fastq_names_1 and fastq_names_2 options

# Options:

 - reads: specify path to directory where paired-end fastq reads are

 - output: specify path to directory where all outputs will be created

 - fastq_names_1: default is "{sample}_R1.fastq.gz"

 - fastq_names_2: default is "{sample}_R2.fastq.gz"


### Example command:

```
snakemake --profile ../profile/slurm/ --config reads=/scratch/sahlab/Megan/test_reads output=/scratch/sahlab/Megan/pipeline_test.out
```
