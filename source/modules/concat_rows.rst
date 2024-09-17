Concatenate Rows of DataFrames
==============================

Overview:
^^^^^^^^^

The **Concatenate Rows of DataFrames Module** allows users to combine
multiple datasets by concatenating them row-wise. The module also
provides an option to add a new column with distinct values for each
dataset, which helps in tracking the origin of each row. This feature is
particularly useful for managing datasets that share a common structure
but represent different conditions, treatments, or timepoints.

Purpose:
^^^^^^^^

This module simplifies the process of merging multiple datasets into one
by stacking their rows. It is ideal for combining data from different
experiments, plates, or treatments that need to be analyzed together.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Multiselect**: Users select one or more DataFrames from the
      available datasets to concatenate.
   -  **Use Case**: Helpful when combining datasets representing
      different experimental conditions, treatments, or timepoints.

2. **Add a New Column with Different Values for Each DataFrame**:

   -  **Checkbox**: If checked, this option adds a new column to the
      concatenated DataFrame. Each dataset will have a unique value in
      this column.
   -  **Use Case**: Useful for tracking which dataset each row came from
      once the data is merged.

3. **New Column Name**:

   -  **Text Input**: The user specifies the name of the new column that
      will store labels for each dataset (e.g., ``Dataset``, ``Plate``,
      ``Condition``).
   -  **Use Case**: Helps identify the origin of each row after the
      DataFrames are combined.

4. **Column Values for Each DataFrame**:

   -  **Text Input**: The user provides a unique value for each selected
      DataFrame to store in the new column.
   -  **Use Case**: This value could represent different conditions
      (e.g., ``Treatment A``, ``Plate 1``) to keep track of data
      sources.

5. **Button: Process DataFrames**:

   -  **Functionality**: Clicking this button processes the selected
      DataFrames and concatenates them row-wise. If the option to add a
      new column is enabled, the new column and its respective values
      are included.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Combining Data from Multiple Plates**: A biologist has data from three
plates, each representing different experimental treatments. To prepare
the data for analysis, they use this module to concatenate the three
datasets into a single DataFrame. They also enable the option to add a
new column, naming it ``Plate``, and input distinct values (``Plate 1``,
``Plate 2``, ``Plate 3``) for each dataset. After processing, the final
DataFrame includes all the data with an additional column indicating
which plate each row came from.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Combine Multiple Datasets**: Users can select and combine as many
   DataFrames as needed, making it convenient to handle large-scale
   experiments with multiple datasets.
-  **Custom Column for Data Origin**: The option to add a new column
   provides a clear way to track the source of each row in the
   concatenated dataset, which is useful for identifying conditions or
   plates in downstream analysis.
-  **Flexible Data Handling**: The user can customize both the column
   name and the values used to label each dataset, providing full
   control over how the data is organized and interpreted.

--------------

Notes:
~~~~~~

-  **Ensure Consistent Column Names**: All selected DataFrames should
   have the same column structure to ensure a smooth concatenation.
-  **Tracking Data Origin**: The ability to add a custom column with
   labels for each dataset is key to maintaining clarity when combining
   datasets from different experimental conditions or plates.
