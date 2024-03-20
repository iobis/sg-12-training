# Introduction to Darwin Core

## What is Darwin Core (DwC)?

If you're not already familiar with Darwin Core (DwC), you should know that it:

* Is a body of standards including identifiers, labels, and definitions to facilitate sharing biodiversity information
* Provides stable terms and vocabularies related to biological objects, data, and their collection
* Is maintained by [TDWG](https://www.tdwg.org/) (Biodiversity Information Standards, formerly The International Working Group on Taxonomic Databases)

It's important to use stable terms and vocabularies to ensure that datasets in OBIS have consistently interpretable fields. By following Darwin Core standards, both data providers and users know *exactly* the definition of various fields and can interpret quality of data easier.

A key resource to bookmark is the [Darwin Core Quick Reference Guide](https://dwc.tdwg.org/terms/), which contains a list with definitions of all current Darwin Core vocabularies. We'll return to this later.

## Data files and the Darwin Core Archive (DwC-A)

Datasets can come in many different formats and file arrangements for all the different types of data - one spreadsheet, multiple sheets, many files, etc. This can of course make interpreting different datasets difficult because data might be in different places. Fortunately Darwin Core includes guidelines for dataset structure!

The basic structure includes at minimum one core data file, with the possibility for additional "extension" files. For datasets published to OBIS there are two options for a core file: 1) Occurrence core or 2) Event core. Ocurrence core datasets tend to be simpler compared to Event core, and describe observations and/or specimen records. They are used when there is **no** information on how the data was sampled and any measurements are related to a single observation/occurrence. Occurrence core is also used for datasets with DNA data.

Conversely, Event core is used when there *is* information on how a sample or observation was taken and/or processed.

Then for extension tables, the most relevant options include: 1) Occurrence core (only when Event core is used), 2) extendedMeasurementOrFact table, 3) DNA derived data extension. For all possible extensions see [here](https://rs.gbif.org/extensions.html).

The flow chart below can be used to help decide what dataset structure (core + extensions) suits a particular dataset.

![](/images/Dataset-structure-decisionTree.png)

For the purposes of this training we will focus on Occurrence core + the extendedMeasurementOrFact and the DNA derived data extension tables. See the [OBIS Manual](https://manual.obis.org/formatting.html#dataset-structure) for more details on dataset structure.

## EXERCISE

Use the flow chart above to determine what kind dataset structure is best suited for each example:

[in development]
