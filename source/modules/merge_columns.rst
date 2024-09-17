Concatenate or Merge DataFrames
===============================

Overview:
^^^^^^^^^

The **Concatenate or Merge DataFrames Module** allows users to either
concatenate or merge multiple datasets (DataFrames). This module offers
flexibility by letting users add prefixes to column names, and in the
case of merging, users can specify which columns to merge on. It is
especially useful for combining datasets that either share similar
structures or contain complementary information.

Purpose:
^^^^^^^^

This module helps users combine data from different sources by
concatenating datasets (stacking columns side by side) or merging them
based on shared columns. By providing options for column prefixes and
merging strategies, the module makes it easy to organize and integrate
data from multiple datasets.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Multiselect**: The user selects one or more DataFrames from the
      available datasets to concatenate or merge.
   -  **Use Case**: This input allows users to select the datasets they
      want to work with, ensuring that only relevant data is combined.

2. **Merge Option**:

   -  **Checkbox**: The user can choose whether to merge the DataFrames
      instead of concatenating them.
   -  **Use Case**: If the user wants to combine datasets based on
      shared values in specific columns (e.g., merging datasets on
      ``ID`` or ``Well``), this option provides the flexibility to do
      so.

3. **Column Selection for Merging**:

   -  **Multiselect**: If the merge option is selected, the user can
      choose one or more common columns on which to merge the
      DataFrames.
   -  **Use Case**: This allows users to specify the keys for merging,
      ensuring that data from different datasets aligns correctly.

4. **Prefix for Columns**:

   -  **Text Inputs**: Users can provide a prefix for each selected
      DataFrame. This prefix will be added to the column names, helping
      distinguish between datasets once they are combined.
   -  **Use Case**: This is useful when multiple DataFrames contain
      columns with the same names, allowing users to prevent name
      conflicts or track which dataset each column came from.

5. **Apply Prefix Only to Duplicated Columns**:

   -  **Checkbox**: If checked, the prefix is only applied to columns
      that have duplicates across DataFrames, leaving unique column
      names unchanged.
   -  **Use Case**: This option reduces unnecessary renaming, only
      applying prefixes where needed to avoid conflicts.

6. **Button: Process DataFrames**:

   -  **Functionality**: Clicking this button processes the selected
      DataFrames by either concatenating or merging them, based on the
      user’s input. The resulting DataFrame is then displayed and saved.
   -  **Use Case**: This option finalizes the user’s selections and
      processes the DataFrames accordingly.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Renaming Columns**:

   -  For each DataFrame, the module allows the user to add a prefix to
      its column names. This helps avoid conflicts when DataFrames with
      similar or identical column names are concatenated or merged.

2. **Merging DataFrames**:

   -  If the user chooses to merge the DataFrames, the module merges
      them based on the selected common columns using an outer merge,
      ensuring that all data is retained, even if some values are
      missing.

3. **Concatenating DataFrames**:

   -  If concatenation is chosen, the DataFrames are combined by
      stacking columns from each dataset side by side. This operation is
      performed along the column axis (``axis=1``), keeping the rows
      intact.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Merging Multiple Datasets with Shared Keys**: A biologist has two
datasets: one containing experimental results and another containing
metadata such as sample IDs and treatment conditions. Using this module,
the biologist selects both datasets, chooses to merge them on the
``Sample ID`` column, and applies different prefixes to the columns to
easily differentiate between the two datasets. The resulting merged
DataFrame contains all the experimental results along with the
associated metadata.

**Concatenating Data from Different Plates**: In another scenario, the
user may have multiple datasets from different plates but wants to
concatenate the columns from each plate. The module allows the user to
apply a prefix to the columns for each plate, ensuring that the final
concatenated DataFrame is easy to interpret.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Concatenate or Merge**: Users can either concatenate columns or
   merge datasets based on shared values, providing flexibility
   depending on the structure of their data.
-  **Custom Prefixes**: The ability to add prefixes ensures that column
   names remain unique and distinguishable after the DataFrames are
   combined, making it easier to track the origin of each column.
-  **Selective Prefixing**: The option to apply prefixes only to
   duplicated columns prevents unnecessary renaming of columns that are
   already unique across the DataFrames.
-  **Merging on Specific Columns**: Users can select which columns to
   use for merging, ensuring that the data is aligned correctly and
   merged in a meaningful way.

--------------

Notes:
~~~~~~

-  **Column Compatibility**: When merging DataFrames, make sure the
   selected columns (merge keys) are present in all DataFrames and
   contain values that will enable meaningful merging.
-  **DataFrame Structure**: The resulting DataFrame after concatenation
   or merging retains the original structure of the data, with added
   prefixes for clarity if needed. This helps maintain the integrity of
   the data during processing.
