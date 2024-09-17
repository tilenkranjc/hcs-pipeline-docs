Data Quality Filtering
======================

Overview:
^^^^^^^^^

The **Data Quality Filtering Module** allows users to filter their
dataset based on the presence of missing values (NaNs) and zero values.
It enables users to set thresholds for the acceptable percentage of NaNs
and zeros in both rows and columns, and automatically removes rows or
columns that exceed those thresholds. This module ensures the quality of
the data before further analysis, particularly for datasets that may
have missing or invalid data.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects a DataFrame from the available
      datasets to filter.
   -  **Use Case**: This input allows users to select which dataset they
      want to clean based on data quality.

2. **Metadata Column Selection**:

   -  **Multiselect**: Users can select metadata columns, which will be
      excluded from data quality filtering. These columns are considered
      reference information and will not be affected by the filtering
      process.
   -  **Use Case**: Useful when metadata columns (such as treatment,
      sample IDs, or timepoints) should remain unchanged, even if they
      contain missing or zero values.

3. **Thresholds for NaNs and Zeros**:

   -  **Threshold for NaNs in Columns**: The percentage of NaN values
      allowed in each column. Columns with more NaNs than the specified
      threshold will be removed.
   -  **Threshold for NaNs in Rows**: The percentage of NaN values
      allowed in each row. Rows with more NaNs than the specified
      threshold will be removed.
   -  **Threshold for Zeros in Columns**: The percentage of zero values
      allowed in each column. Columns with more zeros than the specified
      threshold will be removed.
   -  **Threshold for Zeros in Rows**: The percentage of zero values
      allowed in each row. Rows with more zeros than the specified
      threshold will be removed.
   -  **Use Case**: These inputs allow the user to fine-tune the data
      quality by specifying acceptable levels of missing or zero values.
      This helps ensure that only high-quality data is retained for
      further analysis.

4. **Button: Run Data Quality Filtering**:

   -  **Functionality**: Clicking this button filters the selected
      DataFrame based on the NaN and zero value thresholds specified by
      the user. The filtered DataFrame is then displayed and saved for
      further use.
   -  **Use Case**: This button finalizes the user’s choices and applies
      the filtering process to the dataset.

--------------

Data Handling and Computation:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Filtering Columns Based on NaN Percentage**:

   -  For each data column, the module calculates the percentage of NaN
      values. If the percentage exceeds the user-defined threshold, that
      column is removed from the DataFrame.

   Example: If the user sets the threshold for NaNs in columns to 5%,
   columns with more than 5% missing values will be excluded from the
   dataset.

2. **Filtering Rows Based on NaN Percentage**:

   -  Similar to columns, the module calculates the percentage of NaN
      values in each row. Rows that exceed the threshold are removed.

   Example: A threshold of 10% NaNs in rows means that any row with more
   than 10% missing values will be deleted.

3. **Filtering Columns Based on Zero Percentage**:

   -  The module calculates the percentage of zero values in each data
      column. Columns with more than the specified percentage of zeros
      are removed.

   Example: Setting a threshold of 1% zeros in columns ensures that
   columns containing more than 1% zero values will be removed.

4. **Filtering Rows Based on Zero Percentage**:

   -  Similarly, the module calculates the percentage of zeros in each
      row and removes rows that exceed the threshold.

5. **Resulting DataFrame**:

   -  After applying the specified thresholds, the remaining DataFrame
      is displayed, showing the cleaned data. The filtered dataset is
      saved for further analysis or processing.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Cleaning a Dataset with High Missing Values and Zeros**: A biologist
is working with a large dataset where some features (columns) have a
high percentage of missing values and zero values. Before proceeding
with further analysis, they want to ensure that only high-quality data
is retained. Using this module, the biologist sets a threshold of 5% for
NaNs in columns and 10% for rows, and similarly for zero values. The
module then removes columns and rows that exceed these thresholds,
resulting in a cleaned dataset with fewer missing and zero values, ready
for further analysis.

--------------

Recommendations:
~~~~~~~~~~~~~~~~

-  **When to Use**: Use this module when preparing a dataset for
   analysis where missing or zero values may affect the accuracy or
   validity of the results.
-  **Threshold Settings**: Consider setting more lenient thresholds
   (e.g., 10-20%) for exploratory analysis, but stricter thresholds
   (e.g., 1-5%) for final analysis to ensure data quality.
-  **Metadata Columns**: Always exclude metadata columns (like sample
   IDs, timepoints, or experimental conditions) from the filtering
   process to preserve important reference information.

--------------

Notes:
~~~~~~

-  **Impact of Filtering**: Removing too many rows or columns may result
   in loss of valuable data, so it’s important to choose thresholds
   carefully based on the specific needs of the analysis.
-  **Data Structure**: Ensure that the selected DataFrame is structured
   properly, with metadata columns clearly defined, to avoid unintended
   removal of important information.
