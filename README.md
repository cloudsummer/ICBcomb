# Bulk-RNAseq workflow of ICBcomb 
We utilized NEXTFLOW for the processing pipeline of bulk RNA-seq raw data of the datasets in ICBcomb, and the software used has been encapsulated within the Docker image: xynicoo/rnaseq:n3-fastpMqc.
1. To download, simply run the following code on a server with Docker (Docker version we used is 20.10.21, build 20.10.21-0ubuntu1~22.04.3) and NextFlow (the version we used is 20.07.1 build 5412) installed:

docker pull xynicoo/rnaseq:n3-fastpMqc

2. All software parameters are preconfigured in the "bulk RNA-seq workflow of NEXTFLOW" file. If you need to modify the runtime parameters of the software, you can make changes to this file.
 software detail:
 FastQC (version 0.11.9) was used for data quality control (QC).

 Fastp (version 0.23.1) was employed for adapter sequence removal and trimming to obtain high-quality clean reads. Clean reads were mapped to the human reference genome 
 GRCh38 or the mouse reference genome GRCm39 by HISAT2 (version 2.2.1).
 
 SAMtools (version 1.16) was used to convert the “.sam” file into a “.bam” file.
 
 StringTie (version 2.2.1) was used to estimate the abundance of transcripts for each sample.
 
 FeatureCounts (version 2.0.3) was used to calculate gene expression and get the raw counts (reads matrix).

4. Modify the file "nextflow.config": To run a Nextflow configuration file and specify parameters such as the path to the fastq files, reference genome path, user UID, and other relevant settings.

5. Running the following code will initiate background processing, and save the log in "NF.log.":

nohup nextflow ./bulk_RNAseq_work_flow_of_NEXTFLOW -with-docker xynicoo/rnaseq:n3-fastpMqc -c nextflow.config >> NF.log 2>&1 &


