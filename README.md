## Bulk-RNAseq workflow of ICBcomb 

- [Download the docker image](#Download the docker image.)
- [Download the docker image](#Download the docker image.)
- [1. Download the docker image.](#1. Download the docker image.)
- [2. Modify the file "parameters_of_RNAseq_workflow".]
- [3. Modify the file "nextflow.config".]
- [4.Running the workflow.]
    
![github_RNAseq_workflow](https://github.com/cloudsummer/ICBcomb/assets/24847317/1a84bded-588b-48e1-878a-8c3640fc8541)



We utilized NEXTFLOW for the processing pipeline of bulk RNA-seq raw data of the datasets in ICBcomb, and the software used has been encapsulated within the Docker image: xynicoo/rnaseq:n3-fastpMqc.

### 1. Download the docker image. 
Just simply run the following code on a server with Docker and NextFlow installed:

(Docker version we used is 20.10.21, build 20.10.21-0ubuntu1~22.04.3; the NextFlow version we used is 20.07.1 build 5412) 

```
#the docker image was made by me (the author of ICBcomb)
docker pull xynicoo/rnaseq:n3-fastpMqc
```

### 2. Modify the file "parameters_of_RNAseq_workflow".

All software parameters are preconfigured in the "parameters_of_RNAseq_workflow" file. If you need to modify the runtime parameters of the software, you can make changes to this file.

Software detail in the docker image "xynicoo/rnaseq:n3-fastpMqc":

- FastQC (version 0.11.9) was used for data quality control (QC).

- Fastp (version 0.23.1) was employed for adapter sequence removal and trimming to obtain high-quality clean reads. 
 
- Clean reads were mapped to the human reference genome GRCh38 or the mouse reference genome GRCm39 by HISAT2 (version 2.2.1).
 
- SAMtools (version 1.16) was used to convert the “.sam” file into a “.bam” file.
 
- StringTie (version 2.2.1) was used to estimate the abundance of transcripts for each sample.
 
- FeatureCounts (version 2.0.3) was used to calculate gene expression and get the raw counts (reads matrix).

### 3. Modify the file "nextflow.config".

To run a Nextflow configuration file and specify parameters such as the path to the fastq files, reference genome path, user UID, and other relevant settings.

### 4. Running the workflow.

Running the following code will initiate background processing, and save the log in "NF.log":

```nohup nextflow ./parameters_of_RNAseq_workflow -with-docker xynicoo/rnaseq:n3-fastpMqc -c nextflow.config >> NF.log 2>&1 &```


