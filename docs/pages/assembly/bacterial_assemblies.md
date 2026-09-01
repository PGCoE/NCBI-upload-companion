---
title: "Bacterial Assemblies"
layout: page
parent: "Assembly Uploads"
nav_order: 1
---

# Bacterial Assembly Submission
{: .no_toc }

- **Table of Contents**
{:toc}

<!---
Sections start here
-->


## Annotating Bacterial Genomes

Annotation of bacterial genomes before submission to NCBI is optional, and in most cases unnecessary. Bacterial genomes submitted to NCBI without an annotation will be annotated by NCBI's [PGAP](https://www.ncbi.nlm.nih.gov/refseq/annotation_prok/) tool shortly after submission and made available on NCBI in addition to the submitted genome.

In cases where NCBI's automatic annotation is not desired, [Bakta](https://github.com/oschwengers/bakta) is a great tool for bacterial annotation. If run with the `--compliant` argument, the GFF3 files produced by Bakta can be fed directly into NCBI's [table2asn](https://www.ncbi.nlm.nih.gov/genbank/table2asn/) software to create .sqn files needed to submit genome annotations to NCBI. The Bakta documentation has [a quick overview](https://github.com/oschwengers/bakta?tab=readme-ov-file#genome-submission) of the procedure to generate the compatible GFF3 files here. NCBI provides a guide to running table2asn with GFF3 files [here](https://www.ncbi.nlm.nih.gov/genbank/genomes_gff/).

There are many other tools for genome annotation and methods of submitting bacterial genomes to NCBI available, but the options above are suitable for most public health use cases.

## Bacterial Submission Mechanics

The primary method of submitting bacterial genomes to NCBI is through the [NCBI Submission Portal "Genome" page](https://submit.ncbi.nlm.nih.gov/subs/genome/). This user-friendly web interface allows submission of single genomes or batches of up to 400 genomes. Sample metadata is provided either by filling in a series of forms (for single sample submissions) or by filling out and uploading structured spreadsheet/CSV files with sample metadata.

{: .important }
>All samples in a batch submission must share a common set of features: BioProject, release date, assembly type, file type (FASTA or .sqn), gap/Ns details, publication information, and PGAP request status.

Genome and annotation data files can be uploaded through several mechanisms:

1. An upload button in the submission processes (Best option for low volumes or beginners)
2. File Transfer Protocol (FTP) (Good for large datasets or many files)
   1. This method can be used with GUI FTP clients (ex. WinSCP, Filezilla)or via the FTP command line tool.
3. Aspera protocol (Good for large datasets or many files)
   1. This method can be used via the Aspera browser plugin, or the Aspera command line tool.

{: .note }
> Options 2 and 3 above require configuring your FTP/Aspera client with [credentials provided on the NCBI Genome website](https://submit.ncbi.nlm.nih.gov/subs/genome/) . These credentials only appear when logged into NCBI.
