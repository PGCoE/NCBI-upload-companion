---
title: "Viral Assemblies"
layout: page
parent: "Assembly Uploads"
nav_order: 2
---

# Viral Assembly Submission
{: .no_toc }

- **Table of Contents**
{:toc}

<!---
Sections start here
-->

## Annotating Viral Genomes

Often, the hardest part of uploading viral assemblies to NCBI is the requirement to include gene annotations with genomes. You should seek out an automated gene annotation tool appropriate for your organism. A gene annotation tool would generally take as input 1) your bare unannotated genome FASTA and 2) some external reference data and produce a `.tbl` file that contains the gene names and locations in a coordinate space relative to your provided genome. The .tbl file would then be input to [table2asn](https://www.ncbi.nlm.nih.gov/genbank/table2asn/), a tool which formats sequence data an annotations which is required for submission to GenBank. Instructions for running table2asn to generate a .sqn file are [available on NCBI's website](https://www.ncbi.nlm.nih.gov/genbank/eukaryotic_genome_submission/). Running table2asn in batch mode may also require a Source table format (.src) file containing per-sequence metadata. For additional details see [the table2asn documentation](https://www.ncbi.nlm.nih.gov/genbank/table2asn/#:~:text=Source%20table%20format).

If a closely-related (no major inversions or transpositions) reference genome is already in GenBank, a simple annotation approach is to take the `.tbl` file of the reference genome (the GenBank web interface lets you download any accession as a "Feature Table", which is a .tbl file) and convert the gene coordinates in the reference genome to the corresponding coordinates in the genome being submitted, utilizing a pairwise alignment between the two. This is the conceptual approach used by many publicly available gene annotation tools/scripts.

[VADR](https://github.com/ncbi/vadr) is a command line tool maintained by NCBI that can annotate bare viral genomes for species that have a previously built model. Although VADR was originally designed to support only a handful of viral taxa, the list of viral species with pre-built models is [increasing regularly](https://github.com/broadinstitute/viral-references/blob/main/annotation/vadr/vadr-by-taxid.tsv). [The VADR documentation for building models](https://github.com/ncbi/vadr/blob/master/documentation/build.md) for new taxa can be used with some effort.

## Submission Mechanics: Most Viruses

To submit a genome for a virus that is not part of the "special virus" group [(see below)](#submission-mechanics-special-viruses-sars-cov-2-influenza-abc-norovirus-dengue-virus), email [mgb-sub@ncbi.nlm.nih.gov](mailto:mgb-sub@ncbi.nlm.nih.gov) and attach a zipped .sqn file (the output of [table2asn](https://www.ncbi.nlm.nih.gov/genbank/table2asn/)). Typically, NCBI staff will reply within a business day for any clarifications or curation issues after a submission email is sent. Currently there is no FTP/XML submission option available and the normal NCBI submission web portal cannot be used. A separate, web portal called [BankIt](https://www.ncbi.nlm.nih.gov/WebSub/) can be used as an alternative to email. However, email is generally the easier process. Viral genome submissions cannot be linked to NCBI submission groups currently, they are only associated with the submitter's personal NCBI account.

## Submission mechanics: Special Viruses (SARS-CoV-2, Influenza A/B/C, Norovirus, Dengue Virus)

SARS-CoV-2, Influenza A/B/C, Norovirus and Dengue Virus (referred to hereafter as special viruses) cannot be submitted via [the path described for other viruses above](#submission-mechanics-most-viruses). Instead, these special viruses are submitted via the [web-based GenBank section](https://submit.ncbi.nlm.nih.gov/subs/genbank/) of NCBI's Submission Portal or via FTP.

### Submission via NCBI's GenBank Submission Portal

NCBI's GenBank Submission Portal is a straightforward web-based interface for submitting assembled special virus sequences to NCBI. Submission requires a FASTA of your sequence and a TSV file containing metadata about the sequence. At minimum, submissions must include the collection date, genotype, geographic location where the sample was collected, host, isolation source, assembly method, and a name for the isolate. These metadata can be provided either using a TSV file (a template is provided during the submission process) or by filling in an interactive form on the website. While it is best to provide as much metadata as possible about your sequence, it is acceptable to use `unknown` for many of these fields. In some cases, it may be necessary to submit with less specific metadata due to privacy concerns, for more information see [this page](../biosample/index.html#reducing-identifiability-of-sequence-data).

### Submission of special viruses via FTP

Large batches of Influenza A/B/C and SARS-CoV-2 can also be submitted via FTP [(see the bacterial submission mechanics section for more info on setting up FTP submissions)](#submission-mechanics-bacteria), but Norovirus and Dengue must go through the [GenBank Submission Portal](https://submit.ncbi.nlm.nih.gov/subs/genbank/). FTP submissions must include a FASTA containing sequence data, an .src file containing sequence metadata, and a .sbt file containing the author list (See [NCBI's documentation on table2asn](https://www.ncbi.nlm.nih.gov/genbank/table2asn/) for more info on these files). Optionally, structured comment file (.cmt) may be included containing information about sequencing coverage per segment/sample.

Special virus submissions must be separated by species/subtype. 

{: .example }
> SARS-CoV-2 and Influenza cannot be uploaded in the same submission. This also applies to strains of the same virus such as Influenza A and B.

{: .note }
> Influenza D is not a special virus and must be submitted [via table2asn/BankIt like most other viruses](#submission-mechanics-most-viruses).

## Virus-Specific Considerations

In addition to the various submission pathways, some viruses have specific metadata requirements or conventions. Below are considerations for Influenza, SARS-CoV-2, and Dengue, special considerations for other less common viruses may exist which are not documented here.

### Influenza-Specific Considerations

Influenza A requires a source modifier column called `serotype` and it must be set to the flu A subtype (e.g. H1N1, H3N2, etc). Flu B and C do not require this column.

The isolate name in the source modifier table *must* be simple and cannot contain structured metadata! For example, you cannot submit `Influenza A/Massachusetts/MASPHL-123/2024(H1N1)` Instead, submit only `MASPHL-123`. GenBank will then reconstruct a new isolate name for each flu genome by pre-pending and appending metadata from the source modifier table, leading to the standardized names that can be observed for flu genomes in GenBank.

For FTP/XML submissions of Influenza (but not web portal submissions), the source table must contain a column called `strain`, which is essentially most of the genome name that will be displayed in GenBank. The web portal submissions automatically construct this from submitted metadata: `isolate`, `collection_date`, `geo_loc_name`, `host`, etc. But FTP submissions require the submitter to perform this work and submit strain names in the following format: `A/Massachusetts/MASPHL-123/2024`. Do not append a flu A subtype in parentheses to the end of this name, this process will happen following upload.

For Influenza, NCBI will also pull additional metadata from the associated BioSample record in the background (if a BioSample accession is specified in the source modifier table). Remember to include a BioSample accession number, if available.

As of mid-2024, NCBI will automatically group Influenza GenBank accessions for each gene segment of a genome together into NCBI Assembly entries. These entries consist of eight GenBank accessions for each Assembly accession to allow for easier data management and discovery on [NCBI Virus](https://www.ncbi.nlm.nih.gov/labs/virus/vssi/#/).

Currently, influenza sequences are annotated and error checked at NCBI using a tool called [FLAN](https://pubmed.ncbi.nlm.nih.gov/17545199/). In the future, NCBI plans to switch over to [VADR](https://github.com/ncbi/vadr), but that has not transpired as of late 2025. Influenza virus genome submissions can be pre-screened with VADR to ensure that they will pass NCBI's quality checks. 

{: .tip }
> Some genomes pre-screened with VADR may fail FLAN validation upon submission. If this happens, the submitter can reply to the automated email from NCBI for that submission and request that the failing sequences be permitted based on the passing VADR results. NCBI will then upload them manually. This process will need to be followed for every submission.

### SARS-CoV-2 Specific Considerations

SARS-CoV-2 sequences are annotated and error checked at NCBI via [VADR](https://github.com/ncbi/vadr) after submission. If submissions have been pre-screened with VADR prior to submission and only passing (no alerts) sequences uploaded, all sequences should pass NCBI upload.

{: .note }
>When submitting a batch of SARS-CoV-2 assemblies through the web portal, users are given the option whether they want NCBI's systems to reject the whole batch when a sample fails VADR, or to allow the passing samples to be accepted and have the failing samples rejected.

The community has a specific naming convention for SARS-CoV-2 genomes including the host (e.g. human), country, state, year, etc. (ex. SARS-CoV-2/human/USA/CA-CDPH-001/2020). For additional details and other SARS-CoV-2-specific metadata standards see the [PHA4GE SARS-CoV-2 Contextual Data Specification](https://github.com/pha4ge/sars-cov-2-contextual-data-specification).

### Dengue Specific Considerations

Dengue source modifier tables must contain a column called `genotype` and it must be set to one of the following: 1/2/3/4/5.


