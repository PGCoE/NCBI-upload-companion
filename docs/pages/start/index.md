---
title: "Getting Started"
layout: page
nav_order: 2
---

# Getting Started
{: .no_toc }

- **Table of Contents**
{:toc}


<!---
Sections start here
-->

This site aims to aid public health workers who want to share their pathogen sequence data on NCBI. It is not intended as a replacement for NCBI's own documentation, but as a guide with additional information tailored to public health infectious disease scientists who want to publicly share their data. Public data repositories, such as the ones hosted by NCBI, represent the collection of knowledge, both known and yet to be discovered, whose value is incalculable. By contributing your own data, you not only share your discoveries but also aid the wider public health and scientific communities.

## NCBI Structure

NCBI contains a wealth of biomedical and genomic information. Submitting sequence data to NCBI involves using and understanding the relationship between several resources:

- GenBank/RefSeq - These resources primarily store assembled sequence data and metadata about how a sequence was assembled.
  {: .note } 
  > In some cases, limited metadata about the biological sample that was used to generate the sequence may also be included.
- Sequence Read Archive (SRA) - A database of raw sequencing reads and metadata about sequencing methods.
- BioSample - Data about the biological specimen which was the starting point for sequencing.
- BioProject - An organizational structure that links data for a single research or surveillance project stored in other NCBI databases.
  {: .note } 
  > Umbrella BioProjects are a special BioProject type that only contain other BioProjects.

These resources are linked into a hierarchy:

- **Umbrella BioProjects** contain multiple **BioProjects** that are related in some way.
- **BioProjects** contain **BioSamples** (and other NCBI database entries) that were created as a part of a specific research/surveillance effort.
- **BioSamples** contain data about a biological sample and are linked to **SRA** and/or **GenBank**/**RefSeq** entries.
- **SRA** entries contain raw sequence data and sequencing procedure metadata.
- **GenBank**/**RefSeq** entries contain assembled sequences and assembly procedure metadata.

{: .note } 
RefSeq is a collection of high quality non-redundant sequences curated by NCBI. Users are not permitted to submit directly to RefSeq. For additional information see the [NCBI RefSeq About Page](https://www.ncbi.nlm.nih.gov/refseq/about/)

The figure below from [Timme et al. (2023)](https://doi.org/10.1099/mgen.0.001145) shows the relationship between these resources graphically (excluding umbrella BioProjects):

> ![Fig. 1.](../../media/Pathogen_DOM.png)
> [Putting everything in its place: using the INSDC compliant Pathogen Data Object Model to better structure genomic data submitted for public health applications]( https://pubmed.ncbi.nlm.nih.gov/38085797/)

Timme RE, Karsch-Mizrachi I, Waheed Z, et al. Putting everything in its place: using the INSDC compliant Pathogen Data Object Model to better structure genomic data submitted for public health applications. Microb Genom. 2023;9(12):001145. doi:[10.1099/mgen.0.001145](https://doi.org/10.1099/mgen.0.001145)

{: .tip }
In a perfect world, each sample you sequence would be submitted to NCBI with a new BioSample under a relavent BioProject. Raw sequence data would be deposited in SRA, and an assembly submitted to GenBank. However, depending on the scope are requirements of your project, it may not always be possible or make sense to use all of these resources.

## Should you submit your data to NCBI?

Submitting your genomic data to NCBI plays a crucial role in advancing scientific research and public health initiatives. By making this valuable data accessible to researchers and health officials worldwide, you contribute to collaborative efforts that can lead to significant breakthroughs in understanding genetic factors related to diseases and health outcomes. This open-access model not only fosters collaboration and innovation but also helps create a comprehensive resource for biomedical research, enabling scientists to explore genetic variations and their implications for clinical diagnostics, drug discovery, vaccine development, and public health surveillance. Critically, having a body of data from many jurisdictions to compare against enables genomic epidemiologists to find contextual samples necessary for proper investigation of outbreaks and transmission relationships.

Public data submission can also directly benefit and inform the submitter; certain BioProjects automatically assemble, characterize, and identify clusters of genomes via [NCBI's Pathogen Detection system](https://www.ncbi.nlm.nih.gov/pathogens/), allowing the submitter to identify putatively linked samples sequenced by other institutions. 


Furthermore, data stored in NCBI can enhance the visibility of your research or data contributions, allowing it to be easily cited and referenced, which promotes responsible use and interpretation of genomic information in the context of public health.

{: .note}
Submitting your data may be a requirement for funding agencies, necessary for manuscript or other publication submissions, or mandated by your organization's policies. 

Despite the many reasons to submit data to NCBI, researchers and public health officials may have valid concerns or hesitations about sharing their pathogen sequence data, particularly regarding privacy and confidentiality issues with potential Personally Identifiable Information (PII) or Protected Health Information (PHI) that could be revealed through pathogen-specific data and corresponding metadata. One alternative to consider is submitting genomic data that has been scrubbed of human reads (when sequencing directly from human specimens where there is a risk of generating non-target data), along with limited metadata, to minimize the risk of disclosing identifiable information that could raise legal or ethical concerns. Additionally, institutional policies or funding agency requirements may impose restrictions or delays on data sharing, and intellectual property concerns could impact proprietary research. Therefore, researchers and public health officials must carefully assess the ethical, legal, and logistical factors involved in submitting genomic data, ensuring compliance with regulations while safeguarding personal and clinical information and contributing effectively to public health initiatives.

## INSDC Federation: What if NCBI disappears?

Genomic data submitted to NCBI is not completely dependent on US government support for its continued survival. [The International Nucleotide Sequence Database Collaboration (INSDC)](https://www.insdc.org/) is a partnership between three major global sequence databases: [NCBI](https://www.ncbi.nlm.nih.gov/) (United States), the [European Nucleotide Archive (ENA)](https://www.ebi.ac.uk/ena/) at the European Bioinformatics Institute (United Kingdom), and the [DNA Data Bank of Japan (DDBJ)](https://www.ddbj.nig.ac.jp/index-e.html). These databases automatically synchronize and mirror each other's data daily, creating a robust international federated ecosystem for genomic information. This means that every sequence you submit to NCBI is also stored at ENA and DDBJ, and vice versa. In the event that any single database becomes unavailable due to funding changes, policy changes, technical issues, or other disruptions, your submitted data remains accessible through the other partner databases. This system has operated successfully for decades and ensures that the scientific record and public health data you've worked hard to generate, and share will persist regardless of changes in any single country's research infrastructure.

## Institutional Submission Frequency Considerations

Data submissions to NCBI can be a tedious and time-consuming process. Laboratories must not only compile the data but also gather and standardize the associated metadata. Additionally, it is often necessary to further process the data to remove human or host reads before submission. Various tools are available to assist with these tasks, for example: NCBI's [sra-human-scrubber](https://github.com/ncbi/sra-human-scrubber), [deacon](https://github.com/bede/deacon), and [nohuman](https://github.com/mbhall88/nohuman). Despite these resources, the submission process requires a considerable investment of time to ensure that all data are accurately submitted, and that accessions and submissions are effectively managed. To enhance efficiency, many laboratories may opt for batch submissions at regular intervals, such as weekly or according to a schedule that aligns with their operational needs. However, it is crucial not to delay submissions for extended periods, as timely data sharing is essential for supporting ongoing public health initiatives, particularly during outbreaks or pandemics.

## NCBI Submission Groups vs Individual Accounts

By default, NCBI associates submitted data with the NCBI account of the individual who submitted the data. This approach is less than ideal for groups and institutions where the best long-term steward for the submitted data is the institution which generated the data rather than the individual who uploaded it. To address this, NCBI allows the creation of submission groups. Submission groups provide a method for NCBI users to submit data under an organization rather than their individual account. Users can be added or removed from submission groups as needed, with the data remaining tied to the submission group regardless of staff turnover.

The GenomeTrakr protocol ["NCBI submission protocol for microbial pathogen surveillance"](https://www.protocols.io/view/ncbi-submission-protocol-for-microbial-pathogen-su-4r3l284pql1y/v11?step=1.2) contains detailed step-by-step instructions for creating and administering an NCBI submission group.

The steps detailed above can only be done once per NCBI account (i.e. each NCBI user account can only create one submission group). If a user needs to create additional submission groups, they can request assistance by emailing [info@ncbi.nlm.nih.gov](mailto:info@ncbi.nlm.nih.gov).

## Submission options: Web Portal vs FTP API

NCBI offers two primary pathways for submitting genomic data, each suited to different laboratory workflows and submission volumes. The NCBI [Submission Portal](https://submit.ncbi.nlm.nih.gov/) provides a user-friendly web interface that guides users through the submission process step-by-step with forms, wizards, and interactive validation. This approach is ideal for laboratories that are new to NCBI submission, submit data infrequently, or work with smaller batches of samples. The web portal allows users to upload files directly through their browser and provides immediate feedback on metadata formatting and submission status.

For laboratories with high-throughput sequencing operations, frequent submission schedules, or established bioinformatics pipelines, NCBI also supports programmatic submission via File Transfer Protocol (FTP) and Secure FTP (SFTP). These methods enable automated workflows where metadata and sequence files can be prepared in standardized formats and submitted without human intervention, making it particularly attractive for high volume sequencing labs. Generally, the same set of submission files are required for FTP/SFTP and the web portal but the files need to be packaged in a specific way before uploading.

Utilizing an FTP/SFTP-based pathway requires a one-time setup of a "Center Account" which functions like a Submission Group in the web portal but also provides credentials for accessing NCBI's FTP/SFTP servers. NCBI's instructions for setting up a center account can be found [here.](https://submit.ncbi.nlm.nih.gov/about/sra/#faq6)

The choice between methods often depends on your laboratory's submission frequency and technical capacity. It is advised to start with the web portal to become familiar with NCBI's requirements and workflows, then to consider transitioning to FTP-based methods as your submission volume and automation needs grow. 

{: .note }
 Not all pathogens are accepted over FTP for GenBank submission. Some documentation and examples of XML/ZIP payloads and server responses for FTP submission are available in NCBI's [documentation](https://github.com/ncbi/submission-schema).
