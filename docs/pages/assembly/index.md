---
title: "Assembly Uploads"
layout: page
nav_order: 6
---

# Assembly Uploads
{: .no_toc }

- **Table of Contents**
{:toc}

<!---
Sections start here
-->

## How do I submit my genome assembly to NCBI?

This process varies depending on the organism being submitted. 
- [Submitting bacterial assemblies](/NCBI-upload-companion/docs/pages/assembly/bacterial_assemblies.html)
- [Submitting viral assemblies](/NCBI-upload-companion/docs/pages/assembly/viral_assemblies.html)

## How Can I Annotate my Genome?

Genome annotation is the process of tagging genes, structural elements, and other features within a genome. This is a complex process, with many approaches that vary based on organism type and the desired level of detail.

NCBI has different annotation requirements based on the type of organism being submitted. See the table below to determine whether an annotation is required for your organism:

| **Organism** | **Submitter Provides Annotation** | **Files Required** | **Note** |
| --- | --- | --- | --- |
| Bacteria | Optional | Genome FASTA  OR  Genome FASTA + .sqn file | Genomes submitted without an annotation will be annotated with [PGAP](https://www.ncbi.nlm.nih.gov/refseq/annotation_prok/) by NCBI. |
| Eukaryotes | Optional | Genome FASTA  OR  Genome FASTA + .sqn file | Genomes submitted without an annotation will be stored in NCBI unannotated. |
| SARS-CoV-2 | No | Genome FASTA | SARS-CoV-2 genomes will be annotated with [VADR](https://github.com/ncbi/vadr) by NCBI. |
| Influenza | No | Genome FASTA | Influenza genomes will be annotated with [FLAN](https://pmc.ncbi.nlm.nih.gov/articles/PMC1933127/) by NCBI. However, NCBI intends to update to VADR in the future and will accept any genomes that fail FLAN but pass VADR if you ask them. |
| Other viruses | Yes | Zipped .sqn file |  |

## Genome Naming and Species Differentiations

There are multiple international bodies that exist to aid in the naming of species and to help create structure around species naming conventions and submission to international repositories. These international bodies are distinct for the different taxonomic classes of organisms. There are three main taxonomic separations included in NCBI: 
- Prokaryotes fall under the [International Code of Nomenclature of Prokaryotes](https://the-icsp.org/code-of-nomenclatur) (curated by [ICSP](http://www.the-icsp.org/))
- Animals fall under the [International Code of Zoological Nomenclature](https://www.iczn.org/the-code/the-code-online/) (curated by [ICZN](https://www.iczn.org/))
- Plants, algae, and fungi fall under the [International Code of Nomenclature For Algae, Fungi, and Plants](https://www.iaptglobal.org/_functions/code/madrid) (curated by [IAPT](https://www.iaptglobal.org/)). 
- Viruses, do not have a code of nomenclature, but instead fall under the recommendations from the [International Committee on Taxonomy of Viruses](https://ictv.global/).

When submitting samples to NCBI, there are multiple guidelines on what information should be included in a submission based on specific recommendations for that particular species. Well characterized and popularly submitted viruses, such as influenza and SARS-CoV-2, have well established schemas that are recommended by multiple bodies. 

{: .example }
> In the case of SARS-CoV-2 ICTV released the following naming convention for individual isolates: SARS-CoV-2/host/location/isolate/date. Further recommendations by the CDC proposed simplifying naming conventions to include country/state-lab-sample/year information when submitting to public repositories like GISAID and NCBI. In certain instances, these simplifications are aimed at reducing personally identifiable information (PII), subsequently reducing the likelihood that a sample will not be uploaded to avoid being identified by it's name. 

It is generally suggested that submitters look to [ICTV](https://ictv.global/) to see if there is a naming schema available for their virus of interest. If none is available, consider looking to other closely related viruses for guidance.
