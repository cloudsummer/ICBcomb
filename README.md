# ICBcomb bulk-RNAseq workflow
We utilized NEXTFLOW for the processing pipeline of bulk RNA-seq raw data, and the software used has been encapsulated within the Docker image: xynicoo/rnaseq:n3-fastpMqc.
1. To download, simply run the following code on a server with Docker (Docker version we used is 20.10.21, build 20.10.21-0ubuntu1~22.04.3) and NextFlow (the version we used is 20.07.1 build 5412) installed:

docker pull xynicoo/rnaseq:n3-fastpMqc

2. All software parameters are preconfigured in the "bulk RNA-seq workflow of NEXTFLOW" file. If you need to modify the runtime parameters of the software, you can make changes to this file.

3. Modify the file "nextflow.config": To run a Nextflow configuration file and specify parameters such as the path to the fastq files, reference genome path, user UID, and other relevant settings.

4. Running the following code will initiate background processing, and save the log in "NF.log.":

nohup nextflow ./bulk_RNAseq_work_flow_of_NEXTFLOW -with-docker xynicoo/rnaseq:n3-fastpMqc -c nextflow.config >> NF.log 2>&1 &


