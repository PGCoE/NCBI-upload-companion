---
title: "Read Uploads"
layout: page
nav_order: 5
---

# Read Uploads
{: .no_toc }

- **Table of Contents**
{:toc}

<!---
Sections start here
-->

## Data Upload Methods

There are several ways to upload data to the NCBI Sequence Read Archive (SRA). The most user-friendly method is the [Submission Portal Wizard](https://submit.ncbi.nlm.nih.gov/subs/sra/), which guides users through metadata entry and file upload. For transferring large files, NCBI supports [File Transfer Protocol](https://www.ncbi.nlm.nih.gov/datasets/docs/v2/data-processing/policies-annotation/genomeftp/) (FTP), [Aspera Connect](https://www.ncbi.nlm.nih.gov/sra/docs/submitfiles/#aspera-connect) (a high-speed transfer tool), and [cloud storage options](https://www.ncbi.nlm.nih.gov/sra/docs/sra-cloud/#:~:text=Overview,compute%20through%20these%20cloud%20providers.) (AWS or Google Cloud). Additionally, users can automate or streamline submissions using pipelines like [SeqSender](https://github.com/CDCgov/seqsender), [TOSTADAS](https://github.com/CDCgov/tostadas), and [Terra\_2\_NCBI\_PHB](https://dockstore.org/workflows/github.com/theiagen/public_health_bioinformatics/Terra_2_NCBI_PHB%3Av3.1.0?tab=info), which integrate metadata handling and data transfer into reproducible workflows.

## Limits on Batch Submission

Submitting sequencing data to NCBI databases in batches can greatly improve the efficiency and ease of uploading to public repositories, but there are a few limitations to be aware of. Namely, batch submissions using the web Submission Portal (either SRA or BioSample) can include only up to [1000 samples,](https://www.ncbi.nlm.nih.gov/sra/docs/submitportal/) however this limitation does not exist when submitting via FTP/XML. For both submission pathways each FASTQ file must be less than 100GB and the total data in a submission must be less than 5TB.

Additionally, all data submitted within a batch submission must be submitted to only one BioProject. 

{: .important }
> All samples in a batch BioSample submission must use the same BioSample package. If your samples use more than one BioSample package they should be split into two submissions.
> 
> {: .example }
> Eukaryotic genome submissions must be separate from bacterial submissions. Influenza A submissions must be separate from Influenza B, which must also be separate from general non-special viral submissions.

## Human Read Scrubbing

Human read scrubbing is the process of screening and removing human reads from raw read files. This should be done on any sequence data that may contain human reads prior to uploading to SRA. Typically, this means any sequencing data originating from a human-derived specimen that did not go through a culture step. The Human Read Removal Tool (HRRT) was developed by NCBI for this purpose. HRRT identifies human reads in FASTQ files using a comprehensive human kmer database and masks those reads with `N`. HRRT can be run locally and is [available on GitHub](https://github.com/ncbi/sra-human-scrubber). You may also request that NCBI applies the HRRT automatically to all SRA submissions made under a specific BioProject by emailing sra@ncbi.nlm.nih.gov and requesting HRRT activation for that BioProject. Alternatively, some labs independently scrub the reads with HRRT or other software solutions, such as [Hostile](https://github.com/bede/hostile), and then submit the data to NCBI clean of human reads.

{: .tip }
> For more information on human read removal, this paper is a good place to start.
> 
> > [🔗 Forbes, Matthew et al. “Benchmarking of human read removal strategies for viral and microbial metagenomics.” Cell reports methods vol. 5,11 (2025): 101218. doi:10.1016/j.crmeth.2025.101218](https://pmc.ncbi.nlm.nih.gov/articles/PMC12664888/)
