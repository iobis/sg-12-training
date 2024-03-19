# The DNADerivedData extension

The [DNADerivedData extension](https://rs.gbif.org/extension/gbif/1.0/dna_derived_data_2022-02-23.xml) was created to extend occurrence data with sequencing related metadata, mostly consisting of terms from the GGBN Data Standard, GSC MIxS (Minimum Information about any (X) Sequence), and MIQE (The Minimum Information for Publication of Quantitative Real-Time PCR Experiments).

Guidelines for using the extension and publishing DNA-derived data in general are available at [Publishing DNA-derived data through biodiversity data platforms](https://docs.gbif.org/publishing-dna-derived-data/en/). The guide handles metabarcoding and metagenomis, which are sequence derived, and qPCR/ddPCR data which are not sequence derived.

## Processing workflow

![](https://docs.gbif.org/publishing-dna-derived-data/img/web/outline-of-bioinformatic-processing.en.svg)
From https://docs.gbif.org/publishing-dna-derived-data/en/

## Dataset categories

![](https://docs.gbif.org/publishing-dna-derived-data/img/web/ct/eDNA-categories.en.svg)
From https://docs.gbif.org/publishing-dna-derived-data/en/

## Data mapping

See [Mapping (meta)barcoding data](https://docs.gbif.org/publishing-dna-derived-data/en/#mapping-metabarcoding-edna-and-barcoding-data) and [Mapping qPCR/ddPCR data](https://docs.gbif.org/publishing-dna-derived-data/en/#mapping-ddpcr-qpcr-data).

## OBIS specificities
### Unclassified sequences

For OBIS we recommend that unclassified sequences are annotated as `scientificName` = `incertae sedis` and `scientificNameID` = `urn:lsid:marinespecies.org:taxname:12`.  This will ensure correct interpretation by both GBIF and OBIS.

Additionally, it is recommended that sequence identifiers from the used reference databases (e.g. Barcode index numbers: BINs from BOLD) be added in the taxonConceptID field of the occurrence core table. In this way OBIS will retain its taxonomic backbone based on WoRMS, while enabling linking to disparate reference sequence databases. Names from reference databases which are not strictly scientific names, can be added as verbatimIdentification.

Examples: [TODO]