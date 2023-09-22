# ICBcomb bulk-RNAseq workflow
We utilized NEXTFLOW for the processing pipeline of bulk RNA-seq raw data, and the software used has been encapsulated within the Docker image: xynicoo/rnaseq:n3-fastpMqc.
1. To download, simply run the following code on a server with Docker and NextFlow installed:

docker pull xynicoo/rnaseq:n3-fastpMqc

2. All software parameters are preconfigured in the "bulk RNA-seq workflow of NEXTFLOW" file. If you need to modify the runtime parameters of the software, you can make changes to this file.

3. Modify the file "nextflow.config": To run a Nextflow configuration file and specify parameters such as the path to the fastq files, reference genome path, user UID, and other relevant settings.

4.

nohup nextflow ./3_xy_tuxedo_trim.nf.fastpMqc -with-docker xynicoo/rnaseq:n3-fastpMqc -c m.nextflow.config.txt >> NF.log 2>&1 &


