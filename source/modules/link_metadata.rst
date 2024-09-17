Link Datasets
=============

Overview:
^^^^^^^^^

The **Link Datasets Module** enables users to merge two datasets (data
and metadata) by linking them based on shared columns (``plate``,
``filename``, and ``well``). Users can select metadata combinations from
the second dataset and apply them to unique combinations of ``plate``
and ``filename`` in the first dataset. This module is particularly
useful when merging experimental data with corresponding metadata,
ensuring that information is aligned across datasets.

Purpose:
^^^^^^^^

This module allows users to merge two datasets based on matching
metadata while providing flexibility in selecting which metadata to
include. It is ideal for workflows where experimental data needs to be
linked to corresponding metadata to provide context for further
analysis.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **Data DataFrame Selection**:

   -  **Selectbox**: The user selects a primary dataset (referred to as
      the “Data DataFrame”). This dataset will be the one to which
      metadata will be linked.
   -  **Use Case**: Useful for selecting the core experimental data that
      needs to be enriched with metadata.

2. **Metadata DataFrame Selection**:

   -  **Selectbox**: The user selects a secondary dataset (referred to
      as the “Metadata DataFrame”) from which metadata will be linked to
      the Data DataFrame.
   -  **Use Case**: This dataset typically contains metadata or
      additional information that provides context for the data (e.g.,
      experimental conditions, treatments).

3. **Metadata Combination Selection**:

   -  **Multiselect**: For each unique combination of ``plate`` and
      ``filename`` in the Data DataFrame, the user selects one or more
      corresponding combinations from the Metadata DataFrame.
   -  **Use Case**: This allows users to specify which metadata should
      be linked to specific experimental data, enabling selective and
      flexible merging.

4. **Button: Merge DataFrames**:

   -  **Functionality**: Clicking this button merges the two selected
      datasets based on the user-defined metadata combinations. The
      resulting DataFrame includes both the experimental data and the
      linked metadata.
   -  **Use Case**: Once the user defines how the datasets should be
      linked, this button processes the merge and outputs the final
      dataset.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Unique Combination Matching**:

   -  The module first identifies unique combinations of ``plate`` and
      ``filename`` in both the Data DataFrame and the Metadata
      DataFrame. These combinations are then used as the basis for
      linking the two datasets.

2. **Metadata Selection**:

   -  For each unique combination in the Data DataFrame, the user
      selects corresponding combinations from the Metadata DataFrame.
      The selections are made using a **multiselect** input, allowing
      users to choose multiple metadata combinations.

3. **Merging DataFrames**:

   -  The selected data and metadata are merged on the ``well`` column.
      The resulting merged DataFrame contains data from both the primary
      and metadata datasets, with a distinction between the source
      columns.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Merging Experimental Data with Treatment Metadata**: A biologist has
experimental data collected from multiple plates (``plate``,
``filename``, ``well``) and metadata describing the treatments applied
to those plates. Using this module, the biologist can link the
experimental data with the treatment metadata by selecting the
appropriate combinations from the metadata dataset for each experimental
dataset. The result is a merged DataFrame that includes both the
experimental data and the treatment information.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Link Multiple Metadata Combinations**: Users can select multiple
   combinations of metadata to link to specific combinations in the Data
   DataFrame, providing flexibility in how metadata is applied to the
   experimental data.
-  **Flexible Merging**: The module allows users to define how data from
   the two datasets should be linked, giving them control over the
   merging process and the resulting dataset structure.

--------------

Notes:
~~~~~~

-  **Column Requirements**: Both the Data DataFrame and Metadata
   DataFrame must contain the columns ``plate``, ``filename``, and
   ``well`` for the merging process to work properly.
-  **Multiple Selections**: Users can link multiple metadata
   combinations to a single combination of ``plate`` and ``filename`` in
   the Data DataFrame, allowing for complex merging scenarios.
