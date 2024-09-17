Add Metadata Columns
====================

Overview:
^^^^^^^^^

The **Add Metadata Columns Module** allows users to add new metadata
columns to an existing dataset. Users can dynamically create new
columns, edit their values, and apply them to specific data entries
based on identifiers such as ``plate`` and ``filename``. These key
columns remain uneditable to ensure that important data identifiers
remain intact.

Purpose:
^^^^^^^^

This module enables users to enrich their dataset with additional
metadata, which might be necessary for further data processing or
analysis. It provides flexibility to create and modify metadata while
keeping key identifiers (such as plate and filename) protected from
accidental changes.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Functionality**: The user selects an existing dataset from the
      available data. This dataset will be used as the base to add and
      modify metadata columns.
   -  **Validation**: The selected dataset must contain ``plate`` and
      ``filename`` columns, which are required for identifying
      individual data entries across multiple plates or files.

2. **New Column Input**:

   -  **Text Input**: The user can define the name of a new metadata
      column they wish to add to the dataset.
   -  **Validation**: The module checks that the new column name does
      not already exist in the dataset or among previously added
      columns. Duplicate column names are not allowed, and a message
      will notify the user if an invalid or duplicate column name is
      entered.

3. **Add Column Button**:

   -  **Functionality**: Clicking this button adds the new column to the
      dataset. Each new column starts with empty values, allowing the
      user to populate it with relevant metadata.

4. **Column Deletion**:

   -  **Functionality**: The user can delete any dynamically added
      column by clicking the delete button next to the column name. The
      column is removed from the dataset along with any values that had
      been added.

5. **Editable Table**:

   -  **Editable Columns**: The user can edit the values of dynamically
      added columns within the table. This allows users to input new
      metadata or update existing metadata for each combination of
      ``plate`` and ``filename``.
   -  **Non-Editable Columns**: The ``plate`` and ``filename`` columns
      are locked and cannot be edited to ensure that data integrity is
      maintained across plates and files.

6. **Dataset Name Input**:

   -  **Functionality**: The user can give the dataset a custom name,
      which is used to save the updated dataset. This name helps
      identify the dataset for future use in subsequent analysis steps.

7. **Update DataFrame Button**:

   -  **Functionality**: Once the user finishes editing the metadata,
      clicking this button applies the changes to the dataset. The new
      metadata columns are merged with the original dataset, with values
      assigned to the appropriate rows based on ``plate`` and
      ``filename`` matches.

--------------

Data Handling and Computation:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Managing Columns**:

   -  When a new column is added, it is stored along with the dataset
      and remains available for editing until removed. This ensures that
      users can manage their columns dynamically throughout their
      session.
   -  Deleted columns are immediately removed from the dataset, ensuring
      that only the active columns are displayed and editable.

2. **DataFrame Updates**:

   -  When the table is edited, the module applies the changes to the
      original dataset by finding the rows that match the specified
      ``plate`` and ``filename`` values. The newly added metadata is
      then integrated into the corresponding rows of the dataset.

--------------

Example Usage Scenarios:
~~~~~~~~~~~~~~~~~~~~~~~~

**Scenario 1: Adding Timepoint Information for Different Plates**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In a longitudinal experiment, a biologist collects data from multiple
plates, each representing a different timepoint (e.g., 0 hours, 12
hours, 24 hours, etc.). The plates contain the same layout of cells or
samples, but the biologist needs to differentiate between the timepoints
in the analysis.

1. The biologist uploads the data from each plate.
2. Using the **Add Metadata Columns Module**, they create a new column
   named ``Timepoint`` to store the time information for each plate.
3. They assign the appropriate timepoint (e.g., ``0h``, ``12h``,
   ``24h``) to the relevant plates using the editable table interface.
4. The module ensures that the metadata (timepoints) is correctly
   associated with each ``plate`` and ``filename`` combination.
5. The biologist saves the dataset, and now the experiment’s timepoint
   information is available for use in downstream analyses (e.g.,
   tracking changes over time).

**Benefit**: This approach allows the biologist to seamlessly
incorporate temporal metadata into the dataset, ensuring that the
correct timepoints are associated with each plate without needing to
modify the raw data manually.

--------------

**Scenario 2: Adding Treatment Information for a Single Plate Layout**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A biologist is performing an experiment using the same plate layout for
two different conditions—one with a specific drug treatment and one
without. Each plate contains the same arrangement of wells and samples,
but the treatment condition varies between plates.

1. The biologist uploads the data from the plates with and without the
   treatment.
2. In the **Add Metadata Columns Module**, they create a new column
   called ``Treatment``.
3. Using the table interface, they assign the value ``Drug`` for the
   plates that received the drug treatment, and ``No Drug`` for the
   control plates.
4. The new ``Treatment`` column is automatically mapped to the correct
   ``plate`` and ``filename`` entries, ensuring that the treatment
   condition is recorded alongside the experimental data.
5. The biologist updates the dataset with this new metadata, enabling
   them to analyze the effects of the treatment in downstream analysis.

**Benefit**: The module allows the biologist to easily annotate
experimental conditions (such as drug treatment) across identical plate
layouts, ensuring that all relevant metadata is tracked accurately
without altering the structure of the underlying data.

--------------

These usage scenarios demonstrate how the **Add Metadata Columns
Module** enables biologists to efficiently manage metadata associated
with multi-plate experiments, ensuring that key experimental details
(like timepoints or treatment conditions) are correctly linked to the
data for subsequent analyses.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Dynamic Column Creation**: Users can create and manage metadata
   columns as needed, without having to reload or reset the dataset.
-  **Editable Table**: Provides a clear interface for editing metadata,
   allowing users to input values for each column in a structured
   manner.
-  **Non-Editable Key Columns**: Protects critical columns (``plate``
   and ``filename``) to ensure that data remains correctly associated
   with its origin.
-  **DataFrame Update**: The edited data is applied directly to the
   dataset, ensuring that new metadata is saved and used in subsequent
   analyses.

--------------

Notes:
~~~~~~

-  **Column Name Validation**: Ensure that each new column name is
   unique to avoid conflicts with existing columns or previously added
   metadata.
-  **Column Deletion**: Once a column is deleted, its associated values
   are removed from the dataset, so be certain before removing columns.
