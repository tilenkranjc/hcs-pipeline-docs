Modify Combination of Column Values
===================================

Overview:
^^^^^^^^^

The **Modify Combination of Column Values Module** allows users to
modify specific rows in a dataset based on unique combinations of values
across multiple columns. The user can select combinations of column
values and update a portion of the rows that match these combinations
with new values. This is useful when needing to adjust specific subsets
of data, such as updating metadata labels or correcting groupings.

Purpose:
^^^^^^^^

This module provides flexibility to adjust specific combinations of
values within a dataset, allowing users to modify selected groups of
rows while preserving other parts of the dataset. It’s particularly
helpful for adjusting metadata or experimental conditions in cases where
only part of the data needs to be updated.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Functionality**: The user selects one dataset from the available
      datasets. The selected dataset is used for modification based on
      the combinations of values within its columns.

2. **Select Columns to Combine**:

   -  **Multiselect**: The user selects one or more columns to define
      combinations of values that will be targeted for modification.
   -  **Use Case**: Typically used for selecting metadata columns such
      as ``Treatment``, ``Plate``, or ``Timepoint`` to identify unique
      combinations of experimental conditions.

3. **Select Combination of Values**:

   -  **Selectbox**: After selecting columns, the user is presented with
      a list of unique combinations of values from the selected columns.
      The user selects a specific combination of values to target the
      corresponding rows.

4. **Specify Fraction of Rows to Modify**:

   -  **Slider**: The user selects what fraction of the rows that match
      the chosen combination should be modified (from 1% to 100%).

5. **New Values for Selected Columns**:

   -  **Text Input**: The user enters new values for each of the
      selected columns, which will replace the existing values in the
      selected rows. The current value for each column is used as the
      default in the input field.

6. **Button: Modify Data**:

   -  **Functionality**: After setting the desired options, the user
      clicks this button to apply the modifications to the selected rows
      in the dataset. The changes are then saved for future use.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Modifying Negative Control Wells for Normalization**: A biologist is
preparing to normalize experimental data using negative control wells.
Before performing normalization, they decide to exclude 20% of the
negative control wells to avoid biasing the normalization process. Using
this module, they select the ``Plate`` and ``Well`` columns, choose the
combination that corresponds to the negative control wells, and modify
the labels for 20% of those wells. This ensures that only the
appropriate control wells are used in the subsequent normalization
steps.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Dynamic Column and Value Selection**: Users can select and modify
   any combination of columns in the dataset, giving them control over
   how specific groups of rows are updated.
-  **Random Fractional Modification**: The ability to modify a fraction
   of the matching rows adds flexibility when only a subset of the data
   needs to be adjusted.
-  **Column Value Updates**: The module allows users to input new values
   for selected columns, making it adaptable for tasks such as
   relabeling or updating metadata.
